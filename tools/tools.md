# Tools and Libraries

- **[SelfCheckGPT](https://github.com/potsawee/selfcheckgpt)** — Zero-resource, black-box
  hallucination detector (BERTScore / QA / n-gram / NLI / LLM-prompting variants) that needs no
  external reference corpus; installable via `pip install selfcheckgpt`.

- **[RefChecker](https://github.com/amazon-science/RefChecker)** — Amazon Science's three-stage
  pipeline (extractor → checker → aggregator) for fine-grained, claim-triplet-level hallucination
  detection, with support for zero/noisy/accurate context settings.

- **[FActScore](https://github.com/shmsw25/FActScore)** — Official implementation of the
  atomic-fact factual-precision metric; ships as a pip package with a Wikipedia-based default
  knowledge source and support for custom sources.

- **[LettuceDetect](https://github.com/KRLabsOrg/LettuceDetect)** — Lightweight, encoder-based
  span-level hallucination detector for RAG (and, in newer releases, coding-agent) outputs,
  benchmarked on RAGTruth.

- **[eyecite](https://github.com/freelawproject/eyecite)** — Free Law Project's production-grade
  Python library for extracting and resolving legal citations from text at scale (used to
  annotate CourtListener and the Caselaw Access Project); essential for building or checking any
  legal-citation-fabrication benchmark.

- **[Crossref REST API](https://github.com/CrossRef/rest-api-doc)** — Free, no-key-required API
  for resolving DOIs and verifying whether a cited scholarly work actually exists.
