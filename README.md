# AI Engineering Home Lab

Building a modular, production-oriented AI engineering platform on Apple Silicon. This repository documents the architecture, experiments, code, benchmarks, failures, and lessons learned along the way.

## Mission

Learn to design, build, evaluate, secure, and operate AI systems through reproducible, practical projects. Share verified results publicly as part of a transition into AI Engineering.

## Hardware

- Apple Mac mini M6, 32 GB unified memory
- 512 GB internal SSD
- UGREEN NVMe dock; 1 TB external SSD planned (not installed yet)

## Planned platform

```text
Applications / Demos
         |
  FastAPI LLM Gateway
         |
  Local Model Runtime (Ollama / MLX)
         |
+--------+----------+-------------+
|                   |             |
RAG / GraphRAG   Agents      Evaluation
|                   |             |
+-------------------+-------------+
         |
 Security / Observability / MLOps
```

## Project roadmap

1. **Infrastructure & development setup** — Git, Python, development environments, Docker, storage, and documentation.
2. **Local LLM gateway** — Serve and route local models; measure latency, memory, and throughput.
3. **Document intelligence / RAG / GraphRAG** — Retrieval grounded in documents, with source attribution.
4. **LLM evaluation** — Reproducible test sets, human review, and judge calibration.
5. **Research agents** — Tool use, orchestration, state, and safety boundaries.
6. **Security testing** — Authorized red-team tests for prompt injection and data leakage.
7. **Model adaptation & MLOps** — Small-scale LoRA experiments, tracking, and deployment.
8. **Computer vision (future)** — Explore industrial inspection and robotics applications.

The platform components above remain planned. Initial local MLX inference has been exercised manually; see the benchmark record below.

## Engineering principles

- Start with a working baseline before adding complexity.
- Record metrics and methodology; never invent benchmark results.
- Keep only one inference model loaded at a time across local runtimes; unload it before loading another.
- Document failures, trade-offs, and reproducible setup steps.
- Keep secrets, private datasets, model weights, and large artifacts out of Git.
- Favor modular services and testable interfaces.
- Publish short English-language LinkedIn updates when meaningful milestones are verified.

## Progress

- [x] Create public GitHub repository
- [x] Define initial architecture and roadmap
- [ ] Install Apple Command Line Tools
- [ ] Configure Git and Python development environment
- [ ] Set up external NVMe model storage
- [x] Run first local model and record benchmark (two manual Ornith MLX observations; methodology limitations documented)
- [ ] Publish first technical milestone

## Documentation

- [Roadmap](docs/ROADMAP.md)
- [Ornith 1.5 9B MLX 6-bit: initial manual benchmarks](docs/benchmarks/ornith-1.5-9b-mlx-6bit.md)

> This is a learning and engineering portfolio. Performance and reliability claims will be backed by reproducible experiments.
