# First measurements (October 2026)

Process-extraction quality vs. a hand-made reference list of processes, on two public normative acts.

- **Act A** – 10 reference processes
- **Act B** – 14 reference processes (9 required)

| Variant | Act A found | Act A F1 | Act B found | Act B F1 | Input tokens |
|---|---|---|---|---|---|
| Baseline | 2 / 10 | 0.250 | 4 / 14 | 0.222 | 1x |
| Relaxed decomposition rules | – | 0.421 | – | 0.320 | 2.4–3x |
| Qwen "thinking" mode (vLLM) | empty JSON | – | empty JSON | – | – |

Notes:
- Relaxed decomposition improves F1 substantially but costs 2.4–3x more input tokens.
- Thinking mode returned empty JSON under vLLM; this is an open issue.
