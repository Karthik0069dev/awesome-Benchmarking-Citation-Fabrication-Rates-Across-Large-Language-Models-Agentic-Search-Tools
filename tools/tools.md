## Tools and Libraries

Runnable libraries and services for detecting or verifying citations. (Code accompanying a
specific paper is listed separately under [GitHub Implementations](#github-implementations).)

- **[SelfCheckGPT](https://github.com/potsawee/selfcheckgpt)** — Zero-resource, black-box
  hallucination detector (BERTScore / QA / n-gram / NLI / LLM-prompting variants) requiring
  no external reference corpus. Installable via `pip install selfcheckgpt`.
- **[RefChecker](https://github.com/amazon-science/RefChecker)** — Amazon Science's
  three-stage pipeline (extractor → checker → aggregator) for claim-triplet-level
  hallucination detection, with zero-, noisy-, and accurate-context modes.
- **[FActScore](https://github.com/shmsw25/FActScore)** — Official implementation of the
  atomic-fact factual-precision metric; pip-installable, with a Wikipedia-based default
  knowledge source and support for custom sources.
- **[LettuceDetect](https://github.com/KRLabsOrg/LettuceDetect)** — Lightweight
  encoder-based span-level hallucination detector for RAG output, using ModernBERT for
  English and EuroBERT for multilingual support. `pip install lettucedetect`.
- **[eyecite](https://github.com/freelawproject/eyecite)** — Free Law Project's
  production-grade Python library for extracting and resolving legal citations at scale,
  used to annotate CourtListener and the Caselaw Access Project. Essential for building or
  checking any legal citation-fabrication benchmark.
- **[Crossref REST API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/)**
  — Free, no-key-required API for resolving DOIs and confirming that a cited scholarly work
  actually exists. The first stop for any automated reference check.
- **`urlhealth`** — 83-line Python package released with
  [Rao, Wong & Callison-Burch (2026)](https://arxiv.org/abs/2604.03173) under MIT licence.
  Issues an HTTP HEAD request per URL and classifies the result as LIVE, DEAD (404 with a
  Wayback snapshot, i.e. link rot), LIKELY_HALLUCINATED (404 with no archived snapshot), or
  UNKNOWN. Distributed as a pip package and as an agent skill; in the paper's experiments it
  cut non-resolving citation URLs by 6–79× to under 1%.
