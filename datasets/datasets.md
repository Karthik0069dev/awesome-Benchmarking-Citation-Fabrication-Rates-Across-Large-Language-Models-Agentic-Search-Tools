# Datasets

| Dataset | Source | Description | Application | Link |
|---|---|---|---|---|
| **RAGTruth** | Niu et al., ACL 2024 | ~18,000 LLM responses across QA, data-to-text, and summarization, with word-level human hallucination annotations | Training/evaluating span-level hallucination and citation-faithfulness detectors | [GitHub](https://github.com/ParticleMedia/RAGTruth) |
| **HaluEval** | Li et al., EMNLP 2023 | Sampled + human-annotated hallucinated QA, dialogue, and summarization samples | Benchmarking an LLM's own ability to *recognize* hallucinated content | [GitHub](https://github.com/RUCAIBox/HaluEval) |
| **LePhantomCite** | Who Checks the Citations?, 2026 | 4,499 legal-citation instances (real appellate briefs + systematic hallucination injection + Dahl et al. LLM outputs) | Benchmarking legal citation-hallucination detectors | [Paper](https://arxiv.org/abs/2606.21155) |
| **AuthorityBench** | Authority, Truth, and Citation Bias, 2026 | Multi-domain QA set evaluating how citation presence (real vs. fabricated) shifts hallucination rates | Studying epistemic susceptibility / citation-bias effects | [GitHub](https://github.com/floating-reeds/AuthorityBench) |
| **CiteME benchmark** | Press et al., NeurIPS 2024 | 130 manually-curated excerpts from ML papers, each unambiguously citing one paper | Benchmarking citation-attribution accuracy of LMs and agents | [Paper](https://arxiv.org/abs/2407.12861) |
