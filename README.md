# kz-legal-bpmn-bench

An open pipeline that turns Kazakhstan legal acts (public regulations, ministry orders; Russian and Kazakh) into BPMN process diagrams using **local LLMs** (Qwen served with vLLM). The goal: let teams map public-service processes without sending documents to external APIs.

## Pipeline

1. **Document extraction** – text from PDF/DOCX.
2. **Chunking** – split the act into overlapping sections.
3. **Parallel chunk readers** – each reader extracts candidate processes from its chunk.
4. **Merger / decomposition** – deduplicate, merge and split candidates into a clean process list.
5. **BPMN generation** – produce BPMN 2.0 diagrams for each process.

## Planned experiments

- **Many small readers vs. few large ones:** small fast models (e.g. LiquidAI LFM3-1.7B) reading 10–20 chunks in parallel vs. a large model reading ~4 chunks.
- **Fine-tuning a reader** on Russian/Kazakh legal text to improve process recall.
- **Thinking-mode reasoning** under vLLM (currently returns empty JSON – open issue).

**Compute needs:** A100 80GB (large-model runs, fine-tuning) and RTX 4090/5090 (parallel small-model readers).

## Evaluation

Process-extraction recall / precision / F1 against hand-made reference process lists for public normative acts. First results: [results/baseline.md](results/baseline.md).

## Roadmap

- [x] End-to-end prototype pipeline and first measurements (Oct 2026)
- [ ] Publish evaluation harness and reference process lists for public acts
- [ ] Small-vs-large reader experiments on GPU
- [ ] Fix structured output with thinking mode under vLLM
- [ ] Fine-tune a Russian/Kazakh legal reader model
- [ ] BPMN quality metrics (structure validity, step coverage)
- [ ] Expand benchmark to more acts and Kazakh-language documents

## License

MIT
