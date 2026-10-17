# Roadmap and milestone evidence

## Phase 0 — Environment

**Goal:** Reproducible Apple Silicon development environment.

**Deliverables:** tool versions, setup notes, secure Git configuration, Python virtual environment, basic tests, storage layout.

**Evidence:** terminal outputs and successful smoke tests, with private information redacted.

## Phase 1 — Local LLM inference and gateway

**Goal:** Run a quantized model locally, expose a minimal API, and measure performance.

**Deliverables:** FastAPI service, model configuration, benchmark script, latency / throughput / memory measurements.

**Evidence:** commands, hardware, model version, quantization, context length, and raw measurements.

## Phase 2 — Document intelligence

**Goal:** Compare basic vector RAG against an improved retrieval system and optionally GraphRAG.

**Deliverables:** document ingestion, retrieval, citations, evaluation questions, baseline comparison.

**Evidence:** retrieval quality, groundedness, latency, and failure cases.

## Phase 3 — Evaluation

**Goal:** Build repeatable evaluation workflows.

**Deliverables:** rubric, human-labeled examples, LLM-as-judge comparisons, regression tests.

**Evidence:** agreement and error analysis; disclose limitations.

## Phase 4 — Agent orchestration

**Goal:** Build an assistant with bounded tools and traceable execution.

**Deliverables:** workflows, state handling, retry policy, tool safety, structured outputs.

**Evidence:** successful and failed task traces, costs and latency.

## Phase 5 — Security and reliability

**Goal:** Evaluate our own applications under controlled tests.

**Deliverables:** prompt-injection test cases, guardrails, gateway failure tests, observability.

**Evidence:** before-and-after tests and unresolved risks.

## Phase 6 — Model adaptation and MLOps

**Goal:** Test small-scale fine-tuning and deployment lifecycle.

**Deliverables:** training data provenance, small LoRA experiment where feasible, model registry, deployment notes.

**Evidence:** quality / speed / memory comparison to baseline.

## Publishing workflow

For each meaningful milestone:
1. Implement and test.
2. Commit code and docs to GitHub.
3. Record real results and limitations.
4. Draft a concise English LinkedIn post linking to the repository.
5. Publish only after reviewing the wording and evidence.
