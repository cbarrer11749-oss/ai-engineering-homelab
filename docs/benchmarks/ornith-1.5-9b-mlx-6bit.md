# Ornith 1.5 9B — initial manual benchmarks

## Environment and source

- Hardware: Apple Mac mini with 32 GB unified memory.
- Model: Ornith 1.5 9B, 6-bit quantization.
- Runtime: MLX.
- Source: two real interactive terminal runs and metrics manually reported by the operator.
- These are historical observations, not new runs performed for this documentation. The execution date was not recorded.

## Reported results

| Metric | Test 1 | Test 2 |
|---|---:|---:|
| Generated tokens (reported) | 256 | 337 |
| Generation throughput | 21.1 tok/s | 21.3 tok/s |
| Prompt processing throughput | 14.4 tok/s | 108.7 tok/s |
| Reported peak memory | 7.49 GB | 7.47 GB |
| Response completion | Truncated | Complete |
| Instruction following | Not fully assessed from the retained evidence | Showed reasoning despite the instruction to omit it |

Retained metric lines:

```text
Test 1: 256 tokens · 21.1 tok/s · prompt 14.4 tok/s · peak 7.49 GB
Test 2: 337 tokens · 21.3 tok/s · prompt 108.7 tok/s · peak 7.47 GB
```

The conversation records a 256-token generation limit for the first experiment and a 1,024-token limit for the second. These settings were not captured in a saved command or machine-readable run log.

The retained prompt for test 2 was:

> Explain the difference between an AI model and an AI agent in exactly three sentences. Do not include your reasoning process.

Test 2 completed its final answer in three sentences, but also emitted reasoning text and a closing `</think>` marker. Completion therefore does not imply compliance with the full output-format instruction. The reported token count is not a count of final-answer-only tokens.

## Limited methodology and interpretation

These are two exploratory manual observations, not a controlled or reproducible benchmark suite. The exact model repository/revision, runtime and package versions, macOS version, full commands, sampling parameters, prompt token counts, context/history, warm-up procedure, cache state, background load, and full raw outputs were not retained. The exact first prompt is not available in this record. There were no repeated trials under identical conditions, so no statistical reliability or model ranking can be inferred.

Generation throughput was close in these two runs (21.1 and 21.3 tok/s). This is an initial baseline only. The large difference in prompt throughput does not establish an improvement: prompt length, context reuse, cache state, or other execution conditions may have differed, and their effects were not measured.

Peak memory is the value reported by the runtime, not a measurement of total system memory use or proof that a particular amount of RAM remains available. The first response was truncated at the reported generation cap; the precise runtime stop reason was not logged.

## Operating rule: one loaded model at a time

**Keep only one inference model loaded at a time across MLX, Ollama, and any other local model runtime.** Before loading a different model, stop the current inference session/server or unload its model, and verify it is no longer resident. Downloaded weights on disk do not count as a loaded model.

Apply this rule to future benchmark runs to reduce memory contention and interference. The retained evidence does not independently verify whether it was enforced during these two historical runs.

## Next experiment

Create a small Python benchmark runner that saves the exact model revision, environment, prompt, generation settings, completion/stop status, output, and runtime metrics to a structured file. Use a fixed prompt and repeatable warm-up/cache procedure, with repeated measured trials and only one model loaded.
