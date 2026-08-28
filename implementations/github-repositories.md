# GitHub Implementations

- **[amazon-science/RefChecker](https://github.com/amazon-science/RefChecker)** — Reference
  implementation of the RefChecker paper's triplet extraction and checking pipeline; relevant
  because it is a directly reusable hallucination-checking backend rather than a one-off
  experiment script.

- **[shmsw25/FActScore](https://github.com/shmsw25/FActScore)** — Official FActScore release
  accompanying the EMNLP 2023 paper; well-documented CLI flags (`--use_atomic_facts`,
  `--cache_dir`, `--gamma`) make it straightforward to reproduce published numbers.

- **[potsawee/selfcheckgpt](https://github.com/potsawee/selfcheckgpt)** — Official SelfCheckGPT
  release with a runnable demo notebook (`demo/SelfCheck_demo1.ipynb`), useful as a template for
  auditing your own model outputs.

- **[KRLabsOrg/LettuceDetect](https://github.com/KRLabsOrg/LettuceDetect)** — Actively maintained
  (models released for span-level detection across RAG, code, and tool output), demonstrating
  how RAGTruth-trained detectors extend beyond prose.

- **[lflage/OpenFActScore](https://github.com/lflage/OpenFActScore)** — Reimplementation of
  FActScore using fully open models (e.g., OLMo-2, Gemma-3) instead of proprietary APIs,
  relevant for reproducing factual-precision scores without paid API access.

- **[freelawproject/eyecite](https://github.com/freelawproject/eyecite)** — Production legal-citation
  parser maintained by a nonprofit (Free Law Project) with an active issue tracker and a
  JOSS-published methodology paper, relevant to anyone building a legal-domain
  citation-fabrication benchmark.
