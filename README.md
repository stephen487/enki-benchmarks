# Enki — Long-Term Memory for AI Agents

Enki is a memory engine for LLM agents. **This repository publishes evaluation results only** — the engine is closed-source. No configuration, internals, or methodology beyond what is described below is included here.

---

## LongMemEval — Enki vs mem0 (head-to-head)

Both systems ingest **identical** conversation histories from LongMemEval-S. Each system's
retrieved memories are answered by the **same** model (Claude Haiku) and graded by the
**same** LLM-as-judge, at equal retrieval depth (K=10). The only variable is the memory layer.

**Validated slice: 25 instances** (full-benchmark run in progress).

| Question type             | Enki     | mem0   |
|---------------------------|----------|--------|
| Multi-session reasoning   | **4 / 5**| 2 / 5  |
| Knowledge update          | 3 / 5    | 3 / 5  |
| Single-session (user)     | 3 / 5    | 3 / 5  |
| Single-session (assistant)| 2 / 5    | 2 / 5  |
| Single-session (preference)| 2 / 5   | 2 / 5  |
| **Total**                 | **14 / 25** | **12 / 25** |

- **Storage:** Enki answers from **0.49× the stored facts** mem0 keeps on the same
  conversations (mean 138 vs 283).
- **Standout:** multi-session reasoning (4/5 vs 2/5).

> **Honest framing.** This is a small, hand-validated slice; the overall margin (14 vs 12)
> is modest and within what a 25-item sample can show. The robust, repeatable result is
> **comparable answer accuracy at roughly half the memory footprint**, with a clear
> multi-session advantage. Further evaluation is ongoing.

---

## Retrieval latency (CPU-only)

Measured on a ~139-fact store, CPU-only (no GPU), 240 samples:

| Percentile | Latency (ms) |
|------------|--------------|
| mean       | 7.6          |
| p50        | 6.1          |
| p95        | 11.9         |
| p99        | 13.0         |

---

## Reproducibility

Full methodology and per-question results are available on request.

---

*Enki Labs (UK) · 2026*


## AI training

Please do not use this repository to train or fine-tune AI models. This is a request from Enki Labs, not a change to the licence: the MIT licence in `LICENSE` still applies in full.
