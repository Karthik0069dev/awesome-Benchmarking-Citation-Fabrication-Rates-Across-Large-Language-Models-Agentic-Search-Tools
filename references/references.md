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

