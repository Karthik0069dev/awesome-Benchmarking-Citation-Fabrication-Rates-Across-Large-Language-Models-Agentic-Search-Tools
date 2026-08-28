# Awesome Citation Fabrication Benchmarking

A curated collection of research papers, datasets, tools, implementations, and learning
resources on **benchmarking citation fabrication ("hallucination") rates across Large
Language Models (LLMs) and agentic search tools** — covering general-purpose chatbots,
retrieval-augmented generation (RAG) systems, legal-research AI products, and generative
search engines.


## Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Verification Method](#verification-method)
- [Curated Research Papers](#curated-research-papers)
  - [Survey Papers](#survey-papers)
  - [Foundational Benchmarks and Metrics](#foundational-benchmarks-and-metrics)
  - [Citation Attribution Benchmarks](#citation-attribution-benchmarks)
  - [Domain-Specific: Legal Citation Fabrication](#domain-specific-legal-citation-fabrication)
  - [Agentic Search and Generative Search Engines](#agentic-search-and-generative-search-engines)
  - [Measurement Critiques and Emerging Work](#measurement-critiques-and-emerging-work)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Tutorials and Learning Resources](#tutorials-and-learning-resources)
- [License](#license)

---

## Overview

Large language models and the agentic "deep research" tools built on top of them
routinely support their claims with citations — but a growing body of work shows that a
meaningful fraction of those citations are fabricated: papers, cases, DOIs, or URLs that
either do not exist or do not say what the model claims they say. This repository tracks
the empirical measurement of that problem — the "citation fabrication rate" — across four
overlapping strands of research.

The first strand is **general hallucination benchmarks** that include citation and
attribution tasks (HaluEval, FActScore, RefChecker, RAGTruth). The second is **benchmarks
built specifically around citation attribution** and scholarly references (CiteME,
CiteGuard, MCiteBench). The third is **domain audits of deployed products**, most notably
legal-research AI tools (Westlaw, Lexis+ AI, GPT-4) and generative or agentic search
engines (Bing Chat, Perplexity, YouChat, deep research agents). The fourth, and newest, is
**critique of the measurement instruments themselves** — work showing that a reported
fabrication rate can be an artifact of the reference corpus used to check it rather than a
property of the model under test.

Reported fabrication rates vary enormously by task and domain, from roughly 3–13% for
hallucinated citation URLs in deep research agents up to 91.9% citation omission on
structured bibliographic reconstruction. That spread is itself one of the central findings
this collection tries to make legible: without a fixed task definition and a fixed
verification oracle, "hallucination rate" is not a comparable number.

Key open problems include standardising what counts as a *hallucinated* versus a *partially
valid* citation, separating fabrication from mere retrieval failure or link rot, building
reference-free (zero-resource) detectors that do not require a ground-truth corpus,
controlling for the coverage of whatever database is used as the oracle, and evaluating
agentic tool-using systems rather than single-turn generation alone.

---

## Repository Structure

```
awesome-citation-fabrication-benchmarking/
|-- README.md
|-- LICENSE
|-- paper/
|   `-- AI_Assisted_Research_Paper.pdf
|-- citation-audit/
|   `-- Citation_Integrity_Audit.pdf
|-- references/
|   `-- references.md              # full paper list with verification status
|-- datasets/
|   `-- datasets.md                # dataset details and access notes
|-- tools/
|   `-- tools.md                   # tool and library details
`-- implementations/
    `-- github-repositories.md     # code releases and selection rationale
```

Only the author's own documents are hosted in this repository. All third-party papers are
linked to their publisher, DOI, ACL Anthology, or arXiv page rather than redistributed as
PDFs.

---

## AI-Assisted Research Paper

[View Paper](paper/AI_Assisted_Research_Paper.pdf) — generated with Google Gemini (Flash)
on 21 August 2026 using a single, unprompted (non-audit-flagged) generation request.

The paper proposes a five-category citation-failure taxonomy (Total Fabrication, Partial
Attribute Corruption, Identifier Hijacking, Placeholder Hallucination, Semantic
Misattribution) and synthesises claimed precision and recall trends across non-agentic and
agentic search architectures. It is preserved here **exactly as originally generated,
including its own citation errors** — see the audit below.

## Citation Integrity Audit

[View Audit](citation-audit/Citation_Integrity_Audit.pdf) — a structured, evidence-based
audit (Lab 1: AI-Assisted Citation Integrity Audit) of all three references in the paper
above, checked against arXiv, Crossref/DOI, PubMed, and publisher records.

**Result: Authenticity Score 66.67/100 (moderate risk)** — one fully verified reference,
one with wrong or truncated metadata, and one case of **identifier hijacking**, where two
different real papers (Li, Lin & Ma vs. Zhao & Yin) were cited with the *same* arXiv ID,
one of them wrong. Fittingly, an AI-generated paper about citation fabrication itself
contained a citation-fabrication error — exactly the failure mode this repository exists
to catalogue.

---

## Verification Method

Every entry below was checked against a primary source before inclusion. The procedure was:

1. **Resolve the identifier.** Open the arXiv abstract page, DOI, or ACL Anthology record
   directly rather than trusting a search-engine snippet or an AI-generated reference.
2. **Match the title exactly.** Preprint titles change between versions; the title recorded
   here is the one on the *current* version of record.
3. **Copy the author list from the source.** No author list here was reconstructed from
   memory or from a citing paper's bibliography.
4. **Read the abstract before writing the description.** Every one-line summary below
   paraphrases a claim actually made in the abstract or paper, not an inferred one.
5. **Check the version.** For preprints, the version consulted is noted where a revision
   changed the paper's title, framing, or headline numbers.



---

## Curated Research Papers

23 verified papers across six categories.

### Survey Papers

- **A Survey on Large Language Model Benchmarks**
  Ni, Chen, Li, Chen, Li, Wang, et al. (14 authors) — 2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2508.15361)
  Reviews 283 representative LLM benchmarks organised into general-capability,
  domain-specific, and target-specific categories — useful as a map of where citation and
  hallucination benchmarks sit within the wider evaluation landscape.

- **Survey of Hallucination in Natural Language Generation**
  Ji, Lee, Frieske, Yu, Su, Xu, Ishii, Bang, Madotto, Fung — 2023, *ACM Computing Surveys*
  55(12), Article 248
  [Paper / DOI](https://doi.org/10.1145/3571730)
  Foundational, widely cited survey defining and categorising hallucination in NLG broadly;
  used as the definitional baseline in most later citation-fabrication papers.

### Foundational Benchmarks and Metrics

- **HaluEval: A Large-Scale Hallucination Evaluation Benchmark for Large Language Models**
  Li, Cheng, Zhao, Nie, Wen — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.11747) · [Code](https://github.com/RUCAIBox/HaluEval)
  Introduces a sampling-then-filtering pipeline for generating and human-annotating
  hallucinated LLM samples, and benchmarks whether models can recognise hallucinated
  content in their own domain.

- **FActScore: Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation**
  Min, Krishna, Lyu, Lewis, Yih, Koh, Iyyer, Zettlemoyer, Hajishirzi — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.14251) · [Code](https://github.com/shmsw25/FActScore)
  Decomposes long-form generations into atomic facts and scores the percentage supported by
  a reliable knowledge source — the metric most later citation-verification work is
  measured against.

- **SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models**
  Manakul, Liusie, Gales — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2303.08896) · [Code](https://github.com/potsawee/selfcheckgpt)
  Detects hallucination via response self-consistency across resampled generations, with no
  external reference corpus — a key building block for auditing closed, citation-generating
  systems where ground truth is unavailable.

- **RefChecker: Reference-based Fine-grained Hallucination Checker and Benchmark for Large Language Models**
  Hu, Ru, Guo, Qiu, Zhang, et al. (Amazon Science) — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14486) · [Code](https://github.com/amazon-science/RefChecker)
  Breaks LLM claims into knowledge triplets for finer-grained checking than sentence-level
  methods, across zero-context, noisy-context, and accurate-context settings.

- **RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models**
  Niu, Wu, Zhu, Xu, Shum, Zhong, Song, Zhang — 2024, ACL 2024 (Long Papers), pp. 10862–10878
  [Paper / DOI](https://doi.org/10.18653/v1/2024.acl-long.585) ·
  [arXiv](https://arxiv.org/abs/2401.00396) ·
  [Data](https://github.com/ParticleMedia/RAGTruth)
  A corpus of nearly 18,000 naturally generated RAG responses with manual annotation at both
  case and word level, including hallucination intensity — the standard training set for
  span-level detectors.

### Citation Attribution Benchmarks

- **CiteME: Can Language Models Accurately Cite Scientific Claims?**
  Press, Prabhu, Udandarao, Bethge, Hochlehnert, Press — 2024, NeurIPS 2024 Datasets and
  Benchmarks Track
  [Paper](https://arxiv.org/abs/2407.12861)
  Manually curated benchmark of unambiguous excerpts from ML papers, each pointing to
  exactly one cited paper; frontier LMs reach only 4.2–18.5% accuracy versus 69.7% for human
  experts, and the paper's own CiteAgent system closes only part of that gap (35.3%).

- **CiteGuard: Faithful Citation Attribution for LLMs via Retrieval-Augmented Validation**
  Choi, Guo, Fung, Wang — 2025, arXiv preprint (v4, rev. April 2026)
  [Paper](https://arxiv.org/abs/2510.17853) · [Code](https://github.com/KathCYM/CiteGuard)
  Reframes citation evaluation as attribution *alignment* — whether an LLM's citation
  matches what a human author would have cited — and proposes a retrieval-aware agent that
  improves on the prior baseline by 10 percentage points, reaching up to 68.1% accuracy on
  CiteME against a human baseline of 69.2%.

- **MCiteBench: A Multimodal Benchmark for Generating Text with Citations**
  Hu, Zhang, Zhu, Ye, Xiao — 2025, arXiv preprint (v3)
  [Paper](https://arxiv.org/abs/2503.02589) · [Code](https://github.com/caiyuhu/MCiteBench)
  The first benchmark for citation generation in multimodal contexts, built from academic
  papers and review–rebuttal interactions; finds that MLLMs struggle to ground outputs in
  multimodal input and exhibit a systematic modality bias in which sources they cite.

- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents**
  Onweller, Lumer, Huber, Ramchandani, Subbiah, Feld — 2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2605.06635)
  Uses a reproducible AST parser to extract inline citations from LLM-generated Markdown
  reports at scale and retrieves the actual cited content; across 14 models, link validity
  stays above 94% and relevance above 80%, yet factual accuracy reaches only 39–77% — and
  degrades roughly 42% as tool calls scale from 2 to 150.

- **Detecting Citation Hallucinations in Large Language Model Outputs (Student Abstract)**
  Misra, Udandarao — 2026, *Proceedings of the AAAI Conference on Artificial Intelligence*
  40(48), pp. 41325–41327
  [Paper / DOI](https://doi.org/10.1609/aaai.v40i48.42257) ·
  [AAAI record](https://ojs.aaai.org/index.php/AAAI/article/view/42257)
  Proposes a hybrid detection pipeline combining bibliographic retrieval, fuzzy similarity,
  and LLM verification, with a three-way labelling scheme (valid / partially valid /
  hallucinated) for machine-generated references.

### Domain-Specific: Legal Citation Fabrication

- **Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models**
  Dahl, Magesh, Suzgun, Ho — 2024, *Journal of Legal Analysis* 16(1)
  [Paper](https://arxiv.org/abs/2401.01301)
  Tests general-purpose LLMs (GPT-3.5, GPT-4, Llama 2, PaLM 2) against 200,000+ verifiable
  legal questions built from real federal court cases, finding hallucination rates from 58%
  (GPT-4) to 88% (Llama 2), including on tasks as basic as summarising a case's holding.

- **Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools**
  Magesh, Surani, Dahl, Suzgun, Manning, Ho — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.20362)
  Head-to-head audit of commercial legal-AI products (Lexis+ AI, Westlaw AI-Assisted
  Research) against GPT-4, reporting hallucination rates of 17%, 33%, and 43% respectively —
  retrieval-grounded legal tools outperform general LLMs but are far from hallucination-free.

- **Who Checks the Citations? Benchmarking Legal Hallucination Detection**
  Liu, Stammbach, Henderson — 2026, arXiv preprint (v2, rev. August 2026)
  [Paper](https://arxiv.org/abs/2606.21155)
  Identifies over 1,000 real court filings containing fabricated citations, with the count
  growing year over year; introduces a taxonomy grounded in actual filings plus a dataset of
  1,300 brief excerpts with injected errors, and finds GPT-5 reaches 84.4% recall but only
  55.0% F1 in an agentic setting, averaging 15.3 verification steps per excerpt.

- **Citation Grounding Measures the Oracle: Graph Coverage Determines Reported LLM Hallucination Rates in Law**
  Ovcharov — 2026, arXiv preprint (v2, rev. August 2026)
  [Paper](https://arxiv.org/abs/2606.00898)
  Scores the same 400 responses against two snapshots of one national citation graph: the
  sparse snapshot implies 15–21% of citations are hallucinated, the dense snapshot scores the
  identical responses at 0.989–0.999. Shows that a citation-grounding metric largely reports
  the coverage of its own reference graph, and that at trustworthy coverage it no longer
  separates models at all.

### Agentic Search and Generative Search Engines

- **Evaluating Verifiability in Generative Search Engines**
  Liu, Zhang, Liang — 2023, Findings of EMNLP 2023
  [Paper](https://arxiv.org/abs/2304.09848)
  Human audit of Bing Chat, NeevaAI, Perplexity.ai, and YouChat: only 51.5% of generated
  sentences are fully supported by their citations and only 74.5% of citations actually
  support the sentence they are attached to — one of the earliest systematic
  citation-precision/recall studies of deployed search-and-cite products.

- **Evaluating Robustness of Generative Search Engine on Adversarial Factoid Questions**
  Hu, Li, Chen, Li, Li, Li, Wang, Liu, Wen, Yu, Guo — 2024, Findings of ACL 2024,
  pp. 10650–10671
  [Paper / DOI](https://doi.org/10.18653/v1/2024.findings-acl.633) ·
  [arXiv](https://arxiv.org/abs/2403.12077)
  Human evaluation of Bing Chat, PerplexityAI, and YouChat under black-box adversarial
  factoid questions, showing that subtle manipulation of a claim reliably induces incorrect
  responses and that retrieval-augmented generation is *more* susceptible to factual errors
  than the same models without retrieval.
  *Note: the arXiv preprint is titled "Adversarial Factual Questions"; the peer-reviewed ACL
  version above says "Factoid Questions". Cite the ACL version.*

- **Detecting and Correcting Reference Hallucinations in Commercial LLMs and Deep Research Agents**
  Rao, Wong, Callison-Burch — 2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2604.03173)
  Measures citation URL validity for 10 models and agents on DRBench (53,090 URLs) and 3
  models on ExpertQA (168,021 URLs): 3–13% of citation URLs are hallucinated with no Wayback
  Machine record, and 5–18% are non-resolving. Deep research agents cite more per query but
  hallucinate URLs at higher rates. Releases the `urlhealth` tool as a mitigation.

- **Generative AI Search Engines as Arbiters of Public Knowledge: An Audit of Bias and Authority**
  Li, Sinnamon — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14034)
  Empirical audit of ChatGPT, Bing Chat, and Perplexity using 48 authentic queries across 4
  topics over a 7-day window, analysed by sentiment analysis, inductive coding, and source
  classification; finds uneven source quality with heavy reliance on news, media, and
  business sites, plus commercial and geographic bias in which sources get cited. Included
  because *which* sources a system cites is the necessary complement to *whether* the
  citation is real.

### Measurement Critiques and Emerging Work

- **Structural Hallucination in Large Language Models: A Network-Based Evaluation of Knowledge Organization and Citation Integrity**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2603.01341)
  Introduces *structural* hallucination — distortion of conceptual organisation and
  bibliographic grounding invisible to sentence-level accuracy metrics — and applies a
  network-based stress test across lexical, biographical, and bibliometric benchmarks,
  finding citation omission of 91.9% and near-total failure on structured bibliographic
  reconstruction.

- **Authority, Truth, and Citation Bias: A Large-Scale Multi-Domain Benchmark for Studying Epistemic Susceptibility in Large Language Models**
  Khurana, Ramana RN, Kumar — 2026, arXiv preprint; accepted to AI4GOOD and EIML at ICML 2026
  [Paper](https://arxiv.org/abs/2606.13104) ·
  [Code](https://github.com/floating-reeds/AuthorityBench)
  A 220,564-prompt benchmark with a balanced 2×2 design crossing claim veracity against
  citation veracity across four domains. Finds that the mere presence of a citation, real or
  fabricated, raises hallucination rates relative to a no-citation baseline — by 3 to 22
  percentage points, strongest when fabricated citations accompany true claims.

- **LettuceDetect: A Hallucination Detection Framework for RAG Applications**
  Kovács, Recski — 2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2502.17125) ·
  [Code](https://github.com/KRLabsOrg/LettuceDetect)
  A token-classification detector built on ModernBERT's 8k-token context and trained on
  RAGTruth; outperforms all previous encoder-based models and most prompt-based models while
  being roughly 30× smaller, reaching 79.22% F1 at the example level.

---

## Datasets

| Dataset | Source | Description | Application | Link |
| --- | --- | --- | --- | --- |
| **RAGTruth** | Niu et al., ACL 2024 | ~18,000 LLM responses across QA, data-to-text, and summarisation, annotated at word level for hallucination and intensity | Training and evaluating span-level hallucination and citation-faithfulness detectors | [GitHub](https://github.com/ParticleMedia/RAGTruth) |
| **HaluEval** | Li et al., EMNLP 2023 | Sampled and human-annotated hallucinated QA, dialogue, and summarisation samples | Benchmarking whether an LLM can *recognise* hallucinated content | [GitHub](https://github.com/RUCAIBox/HaluEval) |
| **AuthorityBench** | Khurana et al., 2026 | 220,564 prompts, balanced 2×2 over claim veracity × citation veracity, across general knowledge, science, law, and medicine | Studying epistemic susceptibility and citation-bias effects | [GitHub](https://github.com/floating-reeds/AuthorityBench) |
| **CiteME** | Press et al., NeurIPS 2024 | Manually curated excerpts from ML papers, each unambiguously citing exactly one paper | Benchmarking citation-attribution accuracy of LMs and agents | [Paper](https://arxiv.org/abs/2407.12861) |
| **MCiteBench** | Hu et al., 2025 | Multimodal citation-generation set built from academic papers and review–rebuttal interactions | Evaluating citation grounding in multimodal LLMs | [GitHub](https://github.com/caiyuhu/MCiteBench) |
| **Legal citation-hallucination set** | Liu, Stammbach & Henderson, 2026 | 1,300 legal brief excerpts with systematically injected citation errors, taxonomy grounded in real court filings | Benchmarking legal citation-hallucination detectors | [Paper](https://arxiv.org/abs/2606.21155) |

---

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

---

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

---

## Tutorials and Learning Resources

- **[Semantic Scholar Academic Graph API — Tutorial](https://www.semanticscholar.org/product/api/tutorial)**
  — Official step-by-step guide to querying paper, author, and citation metadata to confirm
  whether a claimed reference actually exists.
- **[Crossref REST API documentation](https://www.crossref.org/documentation/retrieve-metadata/rest-api/)**
  — Official documentation for resolving DOIs and retrieving publisher metadata.
- **[Crossref REST API GitHub docs](https://github.com/Crossref/rest-api-doc)** —
  Community-maintained, more example-heavy companion to the official Crossref docs.
- **[eyecite tutorial notebook](https://github.com/freelawproject/eyecite/blob/main/TUTORIAL.ipynb)**
  — Hands-on notebook for extracting, cleaning, and resolving legal citations from raw text.
- **[LettuceDetect: a walkthrough by the authors](https://huggingface.co/blog/adaamko/lettucedetect)**
  — First-party explanation of the architecture, training on RAGTruth, and usage, written by
  the paper's author.
- **[CiteGuard project page](https://kathcym.github.io/CiteGuard_Page/)** — Method overview,
  results against AI2 Paper Finder, and portability experiments swapping the Semantic Scholar
  backend for arXiv retrieval.

---


## License

The original content of this repository — README text, curation, category structure, the
verification log, and the audit document — is released under the [MIT License](LICENSE).

Linked papers, datasets, and third-party tools remain the property of their respective
authors and are governed by their own licences. No third-party paper PDFs are redistributed
here; all external work is linked to its DOI, ACL Anthology entry, publisher page, or arXiv
record.
