# Awesome Citation Fabrication Benchmarking

A curated collection of research papers, datasets, tools, implementations, and learning
resources on **benchmarking citation fabrication ("hallucination") rates across Large
Language Models (LLMs) and agentic search tools** — covering general-purpose chatbots,
retrieval-augmented generation (RAG) systems, legal-research AI products, and generative
search engines.



## Contents

- [Overview](#overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Curated Research Papers](#curated-research-papers)
  - [Survey Papers](#survey-papers)
  - [Foundational Benchmarks and Metrics](#foundational-benchmarks-and-metrics)
  - [Citation Attribution Benchmarks](#citation-attribution-benchmarks)
  - [Domain-Specific: Legal Citation Fabrication](#domain-specific-legal-citation-fabrication)
  - [Agentic Search / Generative Search Engines](#agentic-search--generative-search-engines)
  - [Recent / Emerging Work](#recent--emerging-work)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Tutorials and Learning Resources](#tutorials-and-learning-resources)
- [License](#license)

## Overview

Large language models and the agentic "deep research" tools built on top of them
routinely support their claims with citations — but a growing body of work shows that a
meaningful fraction of those citations are fabricated: papers, cases, DOIs, or URLs that
either do not exist or do not say what the model claims they say. This repository tracks
the empirical measurement of that problem — "citation fabrication rate" — across three
overlapping strands of research: (1) general hallucination benchmarks that include
citation/attribution tasks (e.g., HaluEval, FActScore, RefChecker), (2) benchmarks built
specifically around citation attribution and scholarly references (e.g., CiteME,
RAGTruth), and (3) domain audits of deployed products, most notably legal-research AI
tools (Westlaw, Lexis+ AI, GPT-4) and generative/agentic search engines (Bing Chat,
Perplexity, YouChat). Reported fabrication rates vary enormously by task and domain —
from single digits for tool-augmented citation attribution up to 80–90% for some
structured bibliographic fields — which is itself one of the central empirical findings
this collection tries to make legible. Key open problems include: standardizing what
counts as a "hallucinated" vs. "partially valid" citation, separating fabrication from
mere retrieval failure, building reference-free (zero-resource) detectors that don't
require a ground-truth corpus, and evaluating agentic/tool-using systems rather than
single-turn generation alone.

## AI-Assisted Research Paper

[View Paper](paper/AI_Assisted_Research_Paper.pdf) — generated with Google Gemini
(Flash) on 21/08/2026 using a single, unprompted (non-audit-flagged) generation request.
The paper proposes a five-category citation-failure taxonomy (Total Fabrication, Partial
Attribute Corruption, Identifier Hijacking, Placeholder Hallucination, Semantic
Misattribution) and synthesizes claimed precision/recall trends across non-agentic and
agentic search architectures. It is preserved here **exactly as originally generated,
including its own citation errors** — see the audit below.

## Citation Integrity Audit

[View Audit](citation-audit/Citation_Integrity_Audit.pdf) — a structured, evidence-based
audit (Lab 1: AI-Assisted Citation Integrity Audit) of all 3 references in the paper above,
checked against arXiv, Crossref/DOI, PubMed, and publisher records. Result: **Authenticity
Score 66.67/100 (moderate risk)** — 1 fully verified reference, 1 with wrong/truncated
metadata, and 1 case of **identifier hijacking**, where two different real papers (Li, Lin &
Ma vs. Zhao & Yin) were cited with the *same* arXiv ID, one of them wrong. Fittingly, the
AI-generated paper about citation fabrication itself contains a citation-fabrication error —
which is exactly the kind of failure this repository exists to catalog.

## Curated Research Papers

Verification note: every entry below was checked for a real, resolvable arXiv / ACL /
publisher / DOI link at the time of writing. Because this is a fast-moving area, re-verify
links before your submission deadline (see [Tutorials](#tutorials-and-learning-resources)).

### Survey Papers

- **A Survey on Large Language Model Benchmarks**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2508.15361)
  Broad survey of LLM benchmark categories that devotes a dedicated section to
  hallucination taxonomy (factual vs. faithfulness hallucination) and its causes across
  the model lifecycle — useful as a map of where citation fabrication sits within the
  wider hallucination literature.

- **Survey of Hallucination in Natural Language Generation**
  Ji, Lee, Frieske, Yu, Su, Xu, Ishii, Bang, Madotto, Fung — 2023, *ACM Computing Surveys*, 55(12)
  [Paper](https://doi.org/10.1145/3571730)
  Foundational, widely-cited survey defining and categorizing hallucination in NLG
  broadly; frequently used as the definitional baseline in later citation-fabrication
  papers.

### Foundational Benchmarks and Metrics

- **HaluEval: A Large-Scale Hallucination Evaluation Benchmark for Large Language Models**
  Li, Cheng, Zhao, Nie, Wen — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.11747) · [Code](https://github.com/RUCAIBox/HaluEval)
  Introduces a large sampling-then-filtering pipeline for generating and
  human-annotating hallucinated LLM samples; finds ChatGPT fabricates unverifiable
  information in roughly 19.5% of responses on the targeted topics tested.

- **FActScore: Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation**
  Min, Krishna, Lyu, Lewis, Yih, Koh, Iyyer, Zettlemoyer, Hajishirzi — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.14251) · [Code](https://github.com/shmsw25/FActScore)
  Decomposes long-form generations (biographies) into atomic facts and scores the
  percentage supported by a reliable knowledge source; finds ChatGPT achieves only ~58%
  factual precision, and introduces an automated FActScore estimator with under 2% error.

- **SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models**
  Manakul, Liusie, Gales — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2303.08896) · [Code](https://github.com/potsawee/selfcheckgpt)
  Proposes detecting hallucination via response self-consistency across resampled
  generations, without needing an external reference corpus — a key building block for
  auditing closed, citation-generating systems where ground truth isn't available.

- **RefChecker: Reference-based Fine-grained Hallucination Checker and Benchmark for Large Language Models**
  Hu, Ru, Guo, Qiu, Zhang, et al. (Amazon Science) — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14486) · [Code](https://github.com/amazon-science/RefChecker)
  Breaks LLM claims into knowledge triplets for finer-grained hallucination checking
  than sentence-level methods, across zero-context, noisy-context, and accurate-context
  settings; releases 11k annotated claim-triplets from seven LLMs.

- **RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models**
  Niu, Wu, Zhang, Zhao, et al. — 2024, ACL 2024
  [Paper](https://arxiv.org/abs/2401.00396) · [Data](https://github.com/ParticleMedia/RAGTruth)
  The first large-scale, word-level-annotated hallucination benchmark specifically for
  RAG settings; ~18,000 LLM responses across QA, data-to-text, and summarization tasks,
  labeled for hallucination intensity and type.

### Citation Attribution Benchmarks

- **CiteME: Can Language Models Accurately Cite Scientific Claims?**
  Press, Prabhu, Udandarao, Bethge, Hochlehnert, Press — 2024, NeurIPS 2024 Datasets and Benchmarks Track
  [Paper](https://arxiv.org/abs/2407.12861)
  Manually-curated benchmark of unambiguous text excerpts from ML papers, each pointing
  to exactly one cited paper; frontier LMs achieve only 4.2–18.5% accuracy at identifying
  the correct reference versus 69.7% for human experts, and the paper's own CiteAgent
  system closes only part of that gap (35.3%).

- **CiteGuard: Faithful Citation Attribution for LLMs via Retrieval-Augmented Validation**
  Choi, et al. — 2025, arXiv preprint / ACL 2026
  [Paper](https://arxiv.org/abs/2510.17853)
  Reframes citation evaluation as attribution-alignment and proposes a retrieval-aware
  agent that reaches 68.1% accuracy on CiteME, approaching the human baseline, and
  generalizes to biomedical and cross-domain excerpt sets.

- **MCiteBench: A Multimodal Benchmark for Generating Text with Citations**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2503.02589)
  Extends citation-generation evaluation to multimodal LLMs that must ground statements
  in both text and non-text sources, addressing a gap in citation research that is
  otherwise almost entirely text-only.

- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2605.06635)
  Introduces a reproducible AST-based parser to extract and evaluate inline citations
  from LLM-generated Markdown research reports at scale, closing the loop by retrieving
  the actual cited content rather than checking claims in isolation.

- **Detecting Citation Hallucinations in Large Language Model Outputs**
  2026, AAAI Student Abstract
  [Paper](https://ojs.aaai.org/index.php/AAAI/article/view/42257)
  Proposes a hybrid detection pipeline (bibliographic retrieval + fuzzy similarity +
  LLM verification) and a three-way labeling scheme (valid / partially valid /
  hallucinated) for machine-generated references.

### Domain-Specific: Legal Citation Fabrication

- **Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models**
  Dahl, Magesh, Suzgun, Ho — 2024, *Journal of Legal Analysis*, 16(1)
  [Paper](https://arxiv.org/abs/2401.01301)
  Tests general-purpose LLMs (GPT-3.5, GPT-4, Llama 2, PaLM 2) against 200,000+
  verifiable legal questions built from real federal court cases; finds hallucination
  rates from 58% (GPT-4) to 88% (Llama 2), including on tasks as basic as summarizing a
  case's holding.

- **Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools**
  Magesh, Surani, Dahl, Suzgun, Manning, Ho — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.20362)
  Head-to-head audit of commercial legal-AI products (Lexis+ AI, Westlaw AI-Assisted
  Research) against GPT-4; finds hallucination rates of 17%, 33%, and 43% respectively,
  showing retrieval-grounded legal-specific tools substantially outperform general LLMs
  but are still far from hallucination-free.

- **Citation Grounding: Detecting and Reducing LLM Citation Hallucinations via Legal Citation Graphs**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.00898)
  Builds on the Dahl et al. and Magesh et al. findings to propose a legal-citation-graph
  grounding method, explicitly positioning itself against FActScore- and
  RefChecker-style approaches that don't handle structured legal citations well.

- **Who Checks the Citations? Benchmarking Legal Hallucination Detection**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.21155)
  Introduces the LePhantomCite dataset (4,499 citation instances, ~1,100 hallucinated)
  combining real appellate-brief excerpts with systematically injected hallucinations
  across five hallucination types, plus real LLM-generated holdings from Dahl et al.

### Agentic Search / Generative Search Engines

- **Evaluating Verifiability in Generative Search Engines**
  Liu, Zhang, Liang — 2023, Findings of EMNLP 2023
  [Paper](https://arxiv.org/abs/2304.09848)
  Human audit of Bing Chat, NeevaAI, Perplexity.ai, and YouChat; finds only 51.5% of
  generated sentences are fully supported by their citations and only 74.5% of
  citations actually support the sentence they're attached to — one of the earliest
  systematic citation-precision/recall studies of deployed search-and-cite products.

- **Evaluating Robustness of Generative Search Engine on Adversarial Factual Questions**
  2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2403.12077)
  Stress-tests Bing, Perplexity, YouChat, and comparison LLMs with adversarial factual
  questions, reporting citation precision/recall alongside factuality and attack
  success rate, showing citation reliability degrades under adversarial pressure.

- **Detecting and Correcting Reference Hallucinations in Commercial LLMs and Deep Research Agents**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2604.03173)
  Systematically measures citation URL validity for 10 models/agents on DRBench
  (53,090 URLs) and 3 models on ExpertQA (168,021 URLs); finds 3–13% of citation URLs
  are outright hallucinated (no Wayback Machine record) while 5–18% are non-resolving.

- **Generative AI Search Engines as Arbiters of Public Knowledge: An Audit of Bias and Authority**
  2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14034)
  Broader audit-methodology survey covering citation verifiability, source diversity,
  and bias in generative search engines; contextualizes citation-fabrication findings
  within wider concerns about these systems as information gatekeepers.

### Recent / Emerging Work

- **Structural Hallucination in Large Language Models: A Network-Based Evaluation of Knowledge Organization and Citation Integrity**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2603.01341)
  Evaluates hallucination across lexical, biographical, and bibliometric benchmarks
  using network-based analysis; finds citation omission around 91.9% and near-total
  failure on fields like DOI and citation-count reconstruction.

- **Authority, Truth, and Citation Bias: A Large-Scale Multi-Domain Benchmark for Studying Epistemic Susceptibility in Large Language Models**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.13104) · [Code](https://github.com/floating-reeds/AuthorityBench)
  Shows that the mere presence of a citation — real or fabricated — increases downstream
  hallucination rates relative to a no-citation baseline, especially when fabricated
  citations are attached to true claims (a 3–22 percentage point increase). Note: an
  unrelated paper also uses the name "AuthorityBench" for a different RAG-authority
  benchmark (`Trustworthy-Information-Access/AuthorityBench`) — the link above is the
  correct one for this entry.

- **LettuceDetect: A Hallucination Detection Framework for RAG Applications**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2502.17125) · [Code](https://github.com/KRLabsOrg/LettuceDetect)
  Lightweight encoder-based span-level hallucination detector trained and evaluated on
  RAGTruth, outperforming other encoder- and prompt-based baselines while being
  significantly smaller and faster.

## Datasets

| Dataset | Source | Description | Application | Link |
|---|---|---|---|---|
| **RAGTruth** | Niu et al., ACL 2024 | ~18,000 LLM responses across QA, data-to-text, and summarization, with word-level human hallucination annotations | Training/evaluating span-level hallucination and citation-faithfulness detectors | [GitHub](https://github.com/ParticleMedia/RAGTruth) |
| **HaluEval** | Li et al., EMNLP 2023 | Sampled + human-annotated hallucinated QA, dialogue, and summarization samples | Benchmarking an LLM's own ability to *recognize* hallucinated content | [GitHub](https://github.com/RUCAIBox/HaluEval) |
| **LePhantomCite** | Who Checks the Citations?, 2026 | 4,499 legal-citation instances (real appellate briefs + systematic hallucination injection + Dahl et al. LLM outputs) | Benchmarking legal citation-hallucination detectors | [Paper](https://arxiv.org/abs/2606.21155) |
| **AuthorityBench** | Authority, Truth, and Citation Bias, 2026 | Multi-domain QA set evaluating how citation presence (real vs. fabricated) shifts hallucination rates | Studying epistemic susceptibility / citation-bias effects | [GitHub](https://github.com/floating-reeds/AuthorityBench) |
| **CiteME benchmark** | Press et al., NeurIPS 2024 | 130 manually-curated excerpts from ML papers, each unambiguously citing one paper | Benchmarking citation-attribution accuracy of LMs and agents | [Paper](https://arxiv.org/abs/2407.12861) |

## Tools and Libraries

- **[SelfCheckGPT](https://github.com/potsawee/selfcheckgpt)** — Zero-resource, black-box
  hallucination detector (BERTScore / QA / n-gram / NLI / LLM-prompting variants) that
  needs no external reference corpus; installable via `pip install selfcheckgpt`.
- **[RefChecker](https://github.com/amazon-science/RefChecker)** — Amazon Science's
  three-stage pipeline (extractor → checker → aggregator) for fine-grained,
  claim-triplet-level hallucination detection, with support for zero/noisy/accurate
  context settings.
- **[FActScore](https://github.com/shmsw25/FActScore)** — Official implementation of the
  atomic-fact factual-precision metric; ships as a pip package with a Wikipedia-based
  default knowledge source and support for custom sources.
- **[LettuceDetect](https://github.com/KRLabsOrg/LettuceDetect)** — Lightweight,
  encoder-based span-level hallucination detector for RAG (and, in newer releases,
  coding-agent) outputs, benchmarked on RAGTruth.
- **[eyecite](https://github.com/freelawproject/eyecite)** — Free Law Project's
  production-grade Python library for extracting and resolving legal citations from
  text at scale (used to annotate CourtListener and the Caselaw Access Project);
  essential for building or checking any legal-citation-fabrication benchmark.
- **[Crossref REST API](https://github.com/CrossRef/rest-api-doc)** — Free, no-key-required
  API for resolving DOIs and verifying whether a cited scholarly work actually exists.

## GitHub Implementations

- **[amazon-science/RefChecker](https://github.com/amazon-science/RefChecker)** —
  Reference implementation of the RefChecker paper's triplet extraction and checking
  pipeline; relevant because it is a directly reusable hallucination-checking backend
  rather than a one-off experiment script.
- **[shmsw25/FActScore](https://github.com/shmsw25/FActScore)** — Official FActScore
  release accompanying the EMNLP 2023 paper; well-documented CLI flags
  (`--use_atomic_facts`, `--cache_dir`, `--gamma`) make it straightforward to reproduce
  published numbers.
- **[potsawee/selfcheckgpt](https://github.com/potsawee/selfcheckgpt)** — Official
  SelfCheckGPT release with a runnable demo notebook
  (`demo/SelfCheck_demo1.ipynb`), useful as a template for auditing your own model outputs.
- **[KRLabsOrg/LettuceDetect](https://github.com/KRLabsOrg/LettuceDetect)** — Actively
  maintained (models released for span-level detection across RAG, code, and tool
  output), demonstrating how RAGTruth-trained detectors extend beyond prose.
- **[lflage/OpenFActScore](https://github.com/lflage/OpenFActScore)** — Reimplementation
  of FActScore using fully open models (e.g., OLMo-2, Gemma-3) instead of proprietary
  APIs, relevant for reproducing factual-precision scores without paid API access.
- **[freelawproject/eyecite](https://github.com/freelawproject/eyecite)** — Production
  legal-citation parser maintained by a nonprofit (Free Law Project) with an active
  issue tracker and a JOSS-published methodology paper, relevant to anyone building a
  legal-domain citation-fabrication benchmark.

## Tutorials and Learning Resources

- **[Semantic Scholar Academic Graph API — Tutorial](https://www.semanticscholar.org/product/api/tutorial)** —
  Official step-by-step tutorial for querying paper, author, and citation metadata to
  verify whether a claimed reference actually exists.
- **[Crossref REST API documentation](https://www.crossref.org/documentation/retrieve-metadata/rest-api/)** —
  Official docs for resolving DOIs and metadata; the standard first stop for checking
  whether a cited DOI is real.
- **[Crossref REST API GitHub docs](https://github.com/Crossref/rest-api-doc)** —
  Community-maintained, more example-heavy companion to the official Crossref docs.
- **[eyecite tutorial notebook](https://github.com/freelawproject/eyecite/blob/main/TUTORIAL.ipynb)** —
  Hands-on notebook for extracting, cleaning, and resolving legal citations from raw text.
- **["Understanding and Mitigating LLM Hallucinations" — Towards Data Science](https://towardsdatascience.com/understanding-and-mitigating-llm-hallucinations-be88d31c4200/)** —
  Accessible walkthrough of the SelfCheckGPT family of methods (BERTScore, QA, n-gram,
  NLI, LLM-prompting) with worked examples.

## License

The original content of this repository (README text, curation, and the audit document)
is released under the [MIT License](LICENSE). Linked papers, datasets, and third-party
tools remain the property of their respective authors and are governed by their own
licenses — see each entry above for the source.
