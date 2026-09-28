# Deep Technical Briefs: LangChain smithtune & Xiaomi HySparse2

## Brief 1: LangChain "smithtune" — agent trajectories → SFT models

### What it is
**smithtune** is an open-source CLI (MIT license) built by LangChain that turns agent trajectories recorded in LangSmith into supervised fine-tuning (SFT) datasets and trained/deployed models, end to end. It is the tool behind "LangSmith Fine-Tuning," announced at LangChain's **Interrupt 26 conference in New York on September 24, 2026**, currently in **public beta**. The GitHub repo (github.com/langchain-ai/smithtune) was created 2026-09-10, first tag v0.1.0, and is explicitly labeled an early-beta project whose commands may change. The announcement post was authored by Ankush Gola, Jake Broekhuizen, and Vivek Trivedy; launch partners are **Fireworks AI** (Pranav Jain, product lead) and **Baseten** (Aaron Ellis-Bloor, applied researcher). It ships with a coding-agent skill (`npx skills add langchain-ai/smithtune`) so a coding agent (Claude Code, Cursor, Codex) can run the whole pipeline.

### How it works (mechanism step-by-step)
1. **Capture.** Works off existing LangSmith traces — no new instrumentation. Reads trajectories from a tracing project or an existing LangSmith trajectory dataset. Trajectory sources include LangChain/LangGraph/Deep Agents, OpenAI and Claude agent kits, and coding agents (Codex, Claude Code, Cursor).
2. **Filter.** You write a LangSmith filter expression over **root runs** (each match brings in its whole thread), e.g. `and(eq(feedback_key, "correctness"), gte(feedback_score, 0.9))`, and test it with the LangSmith CLI before pulling. `smithtune dataset pull` downloads trajectories locally **without model calls**; `--target-count` (default 100) sets the desired count, `--max-candidates` caps candidates (default 1,000, max 2,000). A time window is mandatory (default: last 24h).
3. **Curate (optional council).** `smithtune dataset triage` runs an "agent council": a set of judge LLMs evaluates each whole trajectory against a user-written `rubric.md` (there is no default rubric; you must describe the task, what to keep/drop, with examples) and keeps trajectories on strict majority vote. Default judges are **DeepSeek V4.1 Flash and GLM-5.3-Flash on Baseten Model APIs** (Fireworks-hosted judges, e.g. `deepseek-v4p1-flash`, also supported). Decisions are saved to `labels.jsonl` + `report.md` for human review; up to 3 review rounds. Skippable with `--no-triage` when you already filter on trusted quality signals (feedback scores, human labels). README warns: "Council review helps assess quality; it does not guarantee good training data."
4. **Push.** `smithtune dataset push` previews, then `--confirm` uploads the curated set to a LangSmith dataset.
5. **Prepare → SFT pairs.** `smithtune prepare` validates each trajectory and the tools available at each assistant turn, then converts it into SFT examples: recorded **system messages are preserved; reasoning is omitted by default**; unsupported or overlong trajectories are **excluded without truncation** (listed in `rejected.json`); **each assistant answer becomes one training target**, paired with its preceding context and the tools available at that call. Tokenizer/formatting are selected per target model. Splits are ~**80% train / 10% val / 10% test**, with each source trajectory kept within a single split (no cross-split leakage); memberships are published back to the LangSmith dataset.
6. **Plan & train.** `smithtune plan` previews the job; `smithtune train` fine-tunes on **Fireworks** or **Baseten Loops** and selects the checkpoint with the **lowest validation loss**. With `--evaluate`, it also runs a replay evaluation on held-out test trajectories: provider samplers generate base-model and tuned-model responses from recorded contexts, a judge model scores agreement, plus judge calibration calls; `--max-points-per-trajectory` caps eval points per trajectory.
7. **Evaluate.** Results publish to LangSmith as a base-vs-tuned comparison experiment (single comparison URL). Metrics: `teacher_agreement` (did the assistant action pass the judge, with explanation) and `trajectory_teacher_agreement` (trajectory average). **Replay does not execute tool calls; scores measure how closely the model matches recorded behavior, not end-to-end task completion, and do not affect checkpoint selection.**
8. **Deploy (optional).** `smithtune deploy` promotes the checkpoint to an endpoint — Fireworks (via `firectl`) or Baseten (e.g. `--accelerator H200:1 --max-seq-len 32768`); `undeploy` stops charges.
Safety/cost rails: a first-use interactive acknowledgment of data rights/permitted use; `--confirm` is required before any paid compute; `doctor` checks local prerequisites.

### Key numbers (LangChain internal benchmarks from the announcement; not independently verified)
- **IssueBench subset** (LangChain's internal issue-finding/grouping benchmark): fine-tuned **Kimi K3 = 96.0** vs base Kimi K3 = 90.0 vs **GPT-5.6 Sol = 87.0**. Post notes base Kimi was already strong and further harness work had stopped moving it or GPT-5.6 Sol.
- **Internal code-review-agent PR set**, Qwen-3.8-27B: **F1 48.9% → 53.7%**; precision **62.9% → 81.5%**; recall **unchanged at 40.0%**; model calls per review **55.9 → 39.2 (−29.8%)**; tool requests per review **65.8 → 46.5 (−29.4%)**.
- The announcement itself reports that **an earlier, less selective training set reduced F1** — i.e., data selection (the filtering/triage stage) is the main driver of gains.

### Models & agent frameworks targeted
- **Trained models:** open-weight models fine-tunable on Fireworks serverless training or Baseten Loops (dedicated GPUs in your own workspace). Example in README: `qwen3p8-27b` works with both providers; `smithtune models list --provider` enumerates what's enabled for your account. Internal results used **Kimi K3** and **Qwen-3.8-27B**.
- **Judge models:** DeepSeek V4.1 Flash, GLM-5.3-Flash (Baseten), deepseek-v4p1-flash (Fireworks).
- **Input side:** any agent whose traces land in LangSmith — LangChain, LangGraph, Deep Agents, OpenAI/Claude agent kits, Codex, Claude Code, Cursor.
- **Related context:** LangChain's own applied-research team trains the models behind LangSmith Engine on Baseten Loops by fine-tuning open models on LangSmith agent traces — the internal workflow smithtune productizes.

### Relation to RLHF / post-training data pipelines
- smithtune is explicitly **SFT-only**: the announcement says it "currently supports supervised fine-tuning (SFT) which trains a model using examples of good behavior." No DPO/RLHF/RLVR/online-RL stage exists in the tool today.
- Position in the pipeline: it automates the classic first stage of post-training — demonstration/imitation data (curated trajectories → SFT pairs) — plus eval-driven checkpoint selection. The LangSmith eval-judge loop and feedback signals could feed preference data later, but that is not part of the current product.

### Pricing / licensing
- **CLI itself: MIT open-source, free**; the fine-tuning feature is in public beta (no separate LangSmith SKU named for it in the announcement).
- **All compute is pass-through:** you bring your own Fireworks and/or Baseten API keys; training, evaluation samplers, judge calls, and serving endpoints **bill to your own provider accounts**. `--confirm` gates paid steps; running endpoints keep accruing until undeployed. Baseten Loops is in **early access** (may need to request enablement). Data-rights/permitted-use acknowledgment is required before first use.

### Criticism / limitations
- **Eval is behavioral cloning, not task success:** replay scores agreement with recorded behavior; tool calls are never executed; scores don't affect checkpoint selection. A tuned model can score well by mimicking a mediocre-but-consistent teacher.
- **Benchmarks are vendor-internal:** the 96.0/F1 numbers are LangChain's own tests on internal datasets; no independent replication. Third-party coverage (badsignal.ai) flagged inconsistencies in the surrounding announcement package (60M vs 70M trace counts across posts).
- **Data quality is the fragile link:** filtering by agent name or error flags alone "does not establish training quality"; an unselective training set hurt F1; council triage doesn't guarantee good data.
- **Provider lock-in:** only Fireworks and Baseten training backends; no self-training path.
- **Early beta churn:** commands and saved-directory formats may change.
- **Data movement:** trajectories are pulled out of LangSmith to local disk during preparation — relevant for sensitive production data (hence the data-rights acknowledgment).

### Status & source links
- Announced: **Sept 24, 2026**, Interrupt 26, NYC; Public Beta. Repo created Sept 10, 2026 (v0.1.0).
- Repo: https://github.com/langchain-ai/smithtune (MIT) — verified live 2026-09-28.
- Docs: https://docs.langchain.com/langsmith/smithtune — verified live.
- Announcement overview: https://www.langchain.com/blog/langsmith-engine-agents-fine-tuning-trajectories (Sept 25, 2026) — verified live. Detail post "Introducing LangSmith Fine-Tuning" (A. Gola, J. Broekhuizen, V. Trivedy, Sept 24, 2026) on https://www.langchain.com/blog.
- Baseten launch blog: https://www.baseten.co/blog/fine-tune-on-your-langsmith-traces-with-baseten-loops/ — verified live.
- Press reprint of release: https://mediarelease.co/us/mr01022-langchain-introduces-langsmith-fine-tuning-24092026.html — index only.

### Open questions
- Is DPO/RLHF/RLVR on the roadmap (the repo is named a "Post-Training CLI," suggesting more than SFT)?
- Exact Fireworks vs Baseten Loops training price points for typical runs.
- How `prepare` treats reasoning-model traces (reasoning omitted by default) and multi-modal/tool-schema-heavy trajectories.
- Whether judge calibration details and eval prompts are inspectable/reproducible by users.

---

## Brief 2: Xiaomi "HySparse2" — halving prefill compute

### What it is
**HySparse2: Hybrid Sparse Attention with Two-Level KV Sharing** — a Transformer architecture from Xiaomi's **LLM-Core team** (lead authors Jianyu Wei* and Yizhao Gao*; corresponding authors Shijie Cao and team lead Fuli Luo), posted to arXiv as **arXiv:2609.26368 on September 22, 2026**. It is designed for the defining asymmetry of long-horizon, multi-turn agents: enormous tool outputs/environment observations are read (prefill), then very short actions are emitted (decode). The architecture splits the model so **prefill exits after roughly the first half of the network**, cutting prefill FLOPs ~5× and KV-cache storage ~4.5× versus a Hybrid SWA baseline at 1M tokens, while improving long-context retrieval. Xiaomi MiMo lead **Fuli Luo** announced that the upcoming **MiMo-V3** will adopt HySparse2 as its core architecture (~Sept 24, 2026).

### How it works (mechanism step-by-step)
Two-level KV sharing across a split decoder:
1. **Split.** The 49-layer backbone is divided into a 25-layer **self-decoder** (hybrid full attention + sliding-window attention for local modeling) and a 24-layer **cross-decoder** (hybrid full attention + sparse attention for global retrieval). This borrows the overall structure from **YOCO** (Sun et al., Microsoft Research, 2024), which introduced self-decoder/cross-decoder with cross-layer KV sharing.
2. **Outer level — KV Bridging.** The KV caches for the cross-decoder's **full-attention layers only** are not computed by running the cross-decoder. Instead, learned projections generate them from the corresponding self-decoder full-attention layer's hidden states: `K_j^cross = Proj_j^K(H_i^self)`, `V_j^cross = Proj_j^V(H_i^self)` (each cross-decoder layer keeps its own K/V projections, so distinct KV representations arise even when sharing a source; queries still use the cross-decoder's own hidden states). Bridging only full-attention layers is deliberate: YOCO shared all layers, but a separate SWA branch in the cross-decoder would create a dependency on the cross-decoder's own hidden states that grows with depth and can't be skipped — so HySparse2 **removes the SWA branch from the cross-decoder entirely**.
3. **Early exit.** Because every cross-decoder KV cache can be constructed from self-decoder hidden states, **prefill runs only the first 25 layers + bridging projections** (reportedly just one full-attention layer sits on that path) and skips all 24 cross-decoder layers. Decode still runs the full network, preserving retrieval/generation capacity. In prefill–decode disaggregated serving, the **prefill node hosts only the self-decoder — nearly half the weights — cutting prefill-node memory nearly in half**.
4. **Inner level — KV Reuse + token-level sparsity.** Inside each hybrid block, a full-attention layer computes attention scores and emits both its KV cache and token-selection indices; subsequent sparse layers reuse those indices (no separately trained selector). Two refinements over HySparse1: (a) **block-level → token-level selection**: 1,024 individually selected tokens replace 64-token blocks (block selection dragged in 63 irrelevant neighbors with each relevant token — costly for scattered agent evidence); (b) the removed SWA branch is replaced by a **forced local window: the 128 most recent tokens are always in the selection**, read from the existing full-attention KV cache — no extra KV state or projection parameters.

### Key numbers
All on an **80B-A3B MoE** (80B total, ~3B active), 49 layers, identical data/training recipes; baselines: Hybrid SWA (9 full-attention layers), HySparse1 (5), HySparse2 (5, plus more compact MQA). KV cache measured with **FP8**:
- **At 1M tokens:** prefill FLOPs **5.02× lower than Hybrid SWA, 2.92× lower than HySparse1** ("halving" headlines understate it — it's an ~80% cut vs Hybrid SWA). KV cache: **12.09 GB (Hybrid SWA) → 6.72 GB (HySparse1) → 2.69 GB (HySparse2)**, i.e. ~4.5× smaller than Hybrid SWA, ~2.5× smaller than HySparse1.
- **Pretraining long-context:** RULER **90.77 vs 84.89 vs 88.71**; NoLiMa **49.76 vs 40.27 vs 30.13**; Repo Code PPL 1.1570 vs 1.1588 vs 1.1578 (lower better).
- **After ~100B tokens light post-training, evals up to 256k:** mean **MRCR-v2 +11.30 pp** over HySparse1 (+6.44 pp over Hybrid SWA); mean **RULER-v2 +19.81 pp** over HySparse1 (+18.65 pp over Hybrid SWA); at 256k, RULER-v2 **58.45 vs 32.61 vs 35.74**; AgentPPL and LongPPL lower (better) than both baselines at every tested length.
- **Ablations:** token-level selection (same budget, 32k): RULER-v2 **+6.57**, two-needle MRCR-v2 **+8.14**, GraphWalks **+5.55**. KV Bridging at 290B-A8B / 1.8T tokens: MMLU/TriviaQA slightly up, RULER −0.31, Repo PPL flat, LongPPL 3.6053→3.4202, BBH/GSM8K ~−1 pt, **DROP 71.37→68.17**. Forced-SWA vs gated-SWA branch: GSM8K **−5.08**, MRCR-v2 −4.99 — the price of enabling early exit.
- **General capability (mixed, as expected):** BBH 64.29 vs 61.93 and MMLU-Pro 37.56 vs 35.74 improve; DROP 58.99 vs 63.78 and GSM8K 61.94 vs 64.14 regress vs HySparse1.
- **How "halved" is measured:** theoretical prefill FLOPs and KV-cache bytes at 1M context on same-recipe models — **not wall-clock latency on named hardware**; kernel implementations for token-level sparse attention are not described (paper cites Wang et al. 2025 sparse-kernel advances).

### Models & chips targeted
- **Target model:** Xiaomi **MiMo-V3** (upcoming; no release date announced) will use HySparse2 as its core architecture. Paper experiments: 80B-A3B MoE and 290B-A8B ablation.
- **Chips:** no GPU/accelerator named for the experiments. Context: Xiaomi has a track record of day-0 chip adaptation — MiMo-V2.5 launched with day-0 support across 7 vendors (Alibaba T-Head Zhenwu 810E, AWS Trainium2 + vLLM, AMD ROCm, Baidu Kunlun, Enflame L600, Muxi XiYun, Iluvatar CoreX) plus day-0 SGLang/vLLM support — but no such announcement exists yet for HySparse2/MiMo-V3.

### Relation to prior sparse-attention work
- **HySparse1 (arXiv:2602.03560, Feb 2026, same Xiaomi team):** hybrid sparse attention with "oracle token selection" and KV cache sharing. Sparse layers had **two branches** — block sparse attention (64-token blocks, indices + KV derived from the preceding full-attention layer) and an SWA branch with its own KV cache, fused by a sigmoid gate. Prefill still ran every layer. HySparse2's changes: token-level selection, SWA branch removed (forced 128-token local window), and the new outer KV-Bridging/early-exit level.
- **YOCO (MSR, 2024):** the self-decoder/cross-decoder split and "You Only Cache Once" idea; HySparse2 applies it selectively — bridging **only full-attention layers** — and pairs it with hybrid sparse attention in the cross-decoder.
- **Field context:** NSA/DSA/MoBA-class sparsity and DeepSeek-V4's DSA scheme are the 2026 mainstream; industry notes stress these must be **trained into the model** (not retrofitted) — consistent with HySparse2 requiring training from scratch.

### Status & source links
- **Status:** research preprint; **no production checkpoint, code release, or inference-runtime support announced** as of 2026-09-28. MiMo-V3 adoption announced (~Sept 24, 2026) but MiMo-V3 itself has no release date; no HySparse2 repo found (Xiaomi's open-source org is XiaomiMiMo, e.g. MiMo-Code).
- Paper: https://arxiv.org/pdf/2609.26368 (arXiv:2609.26368, Sept 22, 2026) — verified live.
- Analysis: https://originshq.com/blog/hysparse2-hybrid-sparse-attention-agents/ (Origins AI, deep technical read) — verified live.
- News: https://technode.com/2026/09/24/xiaomis-mimo-v3-to-adopt-new-architecture-as-hysparse2-cuts-long-context-costs/ — verified live.
- Secondary detail (index only): https://toolnavs.com/article/2080-xiaomi-unveils-hysparse2-the-core-architecture-of-mimo-v3-prefill-compute-cut-to; https://www.kucoin.com/news/flash/xiaomi-s-mimo-v3-architecture-cuts-prefill-compute-by-80.

### Open questions
- Wall-clock prefill latency on real GPUs (H100/H200/B200-class) and which custom sparse kernels will be used.
- MiMo-V3 release date; whether weights will be open (Xiaomi open-sourced MiMo-V2.5 and MiMo-Code under MIT).
- Whether SGLang/vLLM will add native HySparse2 support (token-level sparse selection + KV bridging) and when.
- Whether token-level selection will be back-ported as an independent improvement to other hybrid models.

---

## Sources (all read 2026-09-28 unless noted)
1. https://github.com/langchain-ai/smithtune — smithtune README, repo metadata — verified live.
2. https://docs.langchain.com/langsmith/smithtune — official docs — verified live.
3. https://www.langchain.com/blog/langsmith-engine-agents-fine-tuning-trajectories — official announcement overview — verified live.
4. https://www.baseten.co/blog/fine-tune-on-your-langsmith-traces-with-baseten-loops/ — Baseten launch blog — verified live.
5. https://badsignal.ai/stories/langsmith-engine-v2 — third-party coverage incl. internal benchmark tables — verified live.
6. https://originshq.com/blog/hysparse2-hybrid-sparse-attention-agents/ — technical deep dive on HySparse2 — verified live.
7. https://arxiv.org/pdf/2609.26368 — HySparse2 paper PDF — verified live.
8. https://technode.com/2026/09/24/xiaomis-mimo-v3-to-adopt-new-architecture-as-hysparse2-cuts-long-context-costs/ — MiMo-V3 adoption news — verified live.
9. https://mediarelease.co/us/mr01022-langchain-introduces-langsmith-fine-tuning-24092026.html — press reprint — index only.
10. https://toolnavs.com/article/2080-xiaomi-unveils-hysparse2-the-core-architecture-of-mimo-v3-prefill-compute-cut-to — index (search snippet) only.

## Could not verify
- smithtune: Fireworks/Baseten per-run pricing; roadmap for DPO/RLHF; inspectability of judge prompts.
- HySparse2: named hardware for experiments; wall-clock latency; kernel availability; MiMo-V3 release date/open-weight status; official code repo (none found).
- The dedicated "Introducing LangSmith Fine-Tuning" blog post URL (confirmed to exist on langchain.com/blog, dated Sept 24, 2026, but direct URL not captured verbatim; its content was verified via the official overview and the press reprint).
