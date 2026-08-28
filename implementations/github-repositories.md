## GitHub Implementations

Code releases tied to a specific paper in this collection, selected for documentation
quality, reproducibility, licensing, and active maintenance rather than star count.

- **[KathCYM/CiteGuard](https://github.com/KathCYM/CiteGuard)** — Reference implementation
  of the CiteGuard retrieval-aware attribution agent. Builds directly on CiteME/CiteAgent,
  so it doubles as a worked example of extending an existing citation benchmark rather than
  starting from scratch.
- **[caiyuhu/MCiteBench](https://github.com/caiyuhu/MCiteBench)** — Benchmark construction
  and evaluation code for multimodal citation generation, with the dataset mirrored on
  Hugging Face. Relevant as the only multimodal citation-attribution pipeline in this
  collection.
- **[floating-reeds/AuthorityBench](https://github.com/floating-reeds/AuthorityBench)** —
  Full dataset and evaluation code for the 220,564-prompt citation-bias benchmark; the
  factorial prompt-construction code is reusable for designing controlled
  citation-manipulation experiments.
- **[ParticleMedia/RAGTruth](https://github.com/ParticleMedia/RAGTruth)** — Corpus,
  training, and evaluation code for the RAGTruth benchmark, with released model weights.
  Actively updated after publication (annotation revisions and an added `implicit_true`
  label), which is a good maintenance signal.
- **[RUCAIBox/HaluEval](https://github.com/RUCAIBox/HaluEval)** — Generation and evaluation
  code for the HaluEval benchmark, including the sampling-then-filtering pipeline, so the
  data-construction method can be reapplied to a new domain rather than only consumed.
- **[lflage/OpenFActScore](https://github.com/lflage/OpenFActScore)** — Reimplementation of
  FActScore supporting any Hugging Face model for both atomic fact generation and
  validation, evaluated with Llama 3.1, Gemma, Qwen, and OLMo. Reaches 0.99 Pearson
  correlation with the original FActScore results, making factual-precision scoring
  reproducible without paid API access.
  ([Paper](https://arxiv.org/abs/2507.05965))
