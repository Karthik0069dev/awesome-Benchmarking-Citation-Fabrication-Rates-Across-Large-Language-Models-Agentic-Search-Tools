## Datasets

| Dataset | Source | Description | Application | Link |
| --- | --- | --- | --- | --- |
| **RAGTruth** | Niu et al., ACL 2024 | ~18,000 LLM responses across QA, data-to-text, and summarisation, annotated at word level for hallucination and intensity | Training and evaluating span-level hallucination and citation-faithfulness detectors | [GitHub](https://github.com/ParticleMedia/RAGTruth) |
| **HaluEval** | Li et al., EMNLP 2023 | Sampled and human-annotated hallucinated QA, dialogue, and summarisation samples | Benchmarking whether an LLM can *recognise* hallucinated content | [GitHub](https://github.com/RUCAIBox/HaluEval) |
| **AuthorityBench** | Khurana et al., 2026 | 220,564 prompts, balanced 2×2 over claim veracity × citation veracity, across general knowledge, science, law, and medicine | Studying epistemic susceptibility and citation-bias effects | [GitHub](https://github.com/floating-reeds/AuthorityBench) |
| **CiteME** | Press et al., NeurIPS 2024 | Manually curated excerpts from ML papers, each unambiguously citing exactly one paper | Benchmarking citation-attribution accuracy of LMs and agents | [Paper](https://arxiv.org/abs/2407.12861) |
| **MCiteBench** | Hu et al., 2025 | Multimodal citation-generation set built from academic papers and review–rebuttal interactions | Evaluating citation grounding in multimodal LLMs | [GitHub](https://github.com/caiyuhu/MCiteBench) |
| **Legal citation-hallucination set** | Liu, Stammbach & Henderson, 2026 | 1,300 legal brief excerpts with systematically injected citation errors, taxonomy grounded in real court filings | Benchmarking legal citation-hallucination detectors | [Paper](https://arxiv.org/abs/2606.21155) |
