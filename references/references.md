# References

Verified research papers on benchmarking citation fabrication rates across LLMs and agentic
search tools. Every entry was checked for a real, resolvable arXiv / ACL / publisher / DOI
link at time of writing (28 August 2026). Re-verify links before your submission deadline.

## Survey Papers

- **A Survey on Large Language Model Benchmarks**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2508.15361)
  Broad survey of LLM benchmark categories that devotes a dedicated section to hallucination
  taxonomy (factual vs. faithfulness hallucination) and its causes across the model lifecycle —
  useful as a map of where citation fabrication sits within the wider hallucination literature.

- **Survey of Hallucination in Natural Language Generation**
  Ji, Lee, Frieske, Yu, Su, Xu, Ishii, Bang, Madotto, Fung — 2023, *ACM Computing Surveys*, 55(12)
  [Paper](https://doi.org/10.1145/3571730)
  Foundational, widely-cited survey defining and categorizing hallucination in NLG broadly;
  frequently used as the definitional baseline in later citation-fabrication papers.

## Foundational Benchmarks and Metrics

- **HaluEval: A Large-Scale Hallucination Evaluation Benchmark for Large Language Models**
  Li, Cheng, Zhao, Nie, Wen — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.11747) · [Code](https://github.com/RUCAIBox/HaluEval)
  Introduces a large sampling-then-filtering pipeline for generating and human-annotating
  hallucinated LLM samples; finds ChatGPT fabricates unverifiable information in roughly 19.5%
  of responses on the targeted topics tested.

- **FActScore: Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation**
  Min, Krishna, Lyu, Lewis, Yih, Koh, Iyyer, Zettlemoyer, Hajishirzi — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2305.14251) · [Code](https://github.com/shmsw25/FActScore)
  Decomposes long-form generations (biographies) into atomic facts and scores the percentage
  supported by a reliable knowledge source; finds ChatGPT achieves only ~58% factual precision,
  and introduces an automated FActScore estimator with under 2% error.

- **SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models**
  Manakul, Liusie, Gales — 2023, EMNLP 2023
  [Paper](https://arxiv.org/abs/2303.08896) · [Code](https://github.com/potsawee/selfcheckgpt)
  Proposes detecting hallucination via response self-consistency across resampled generations,
  without needing an external reference corpus — a key building block for auditing closed,
  citation-generating systems where ground truth isn't available.

- **RefChecker: Reference-based Fine-grained Hallucination Checker and Benchmark for Large Language Models**
  Hu, Ru, Guo, Qiu, Zhang, et al. (Amazon Science) — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14486) · [Code](https://github.com/amazon-science/RefChecker)
  Breaks LLM claims into knowledge triplets for finer-grained hallucination checking than
  sentence-level methods, across zero-context, noisy-context, and accurate-context settings;
  releases 11k annotated claim-triplets from seven LLMs.

- **RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models**
  Niu, Wu, Zhang, Zhao, et al. — 2024, ACL 2024
  [Paper](https://arxiv.org/abs/2401.00396) · [Data](https://github.com/ParticleMedia/RAGTruth)
  The first large-scale, word-level-annotated hallucination benchmark specifically for RAG
  settings; ~18,000 LLM responses across QA, data-to-text, and summarization tasks, labeled for
  hallucination intensity and type.

## Citation Attribution Benchmarks

- **CiteME: Can Language Models Accurately Cite Scientific Claims?**
  Press, Prabhu, Udandarao, Bethge, Hochlehnert, Press — 2024, NeurIPS 2024 Datasets and
  Benchmarks Track
  [Paper](https://arxiv.org/abs/2407.12861)
  Manually-curated benchmark of unambiguous text excerpts from ML papers, each pointing to
  exactly one cited paper; frontier LMs achieve only 4.2–18.5% accuracy at identifying the
  correct reference versus 69.7% for human experts, and the paper's own CiteAgent system closes
  only part of that gap (35.3%).

- **CiteGuard: Faithful Citation Attribution for LLMs via Retrieval-Augmented Validation**
  Choi, et al. — 2025, arXiv preprint / ACL 2026
  [Paper](https://arxiv.org/abs/2510.17853)
  Reframes citation evaluation as attribution-alignment and proposes a retrieval-aware agent
  that reaches 68.1% accuracy on CiteME, approaching the human baseline, and generalizes to
  biomedical and cross-domain excerpt sets.

- **MCiteBench: A Multimodal Benchmark for Generating Text with Citations**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2503.02589)
  Extends citation-generation evaluation to multimodal LLMs that must ground statements in both
  text and non-text sources, addressing a gap in citation research that is otherwise almost
  entirely text-only.

- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2605.06635)
  Introduces a reproducible AST-based parser to extract and evaluate inline citations from
  LLM-generated Markdown research reports at scale, closing the loop by retrieving the actual
  cited content rather than checking claims in isolation.

- **Detecting Citation Hallucinations in Large Language Model Outputs**
  2026, AAAI Student Abstract
  [Paper](https://ojs.aaai.org/index.php/AAAI/article/view/42257)
  Proposes a hybrid detection pipeline (bibliographic retrieval + fuzzy similarity + LLM
  verification) and a three-way labeling scheme (valid / partially valid / hallucinated) for
  machine-generated references.

## Domain-Specific: Legal Citation Fabrication

- **Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models**
  Dahl, Magesh, Suzgun, Ho — 2024, *Journal of Legal Analysis*, 16(1)
  [Paper](https://arxiv.org/abs/2401.01301)
  Tests general-purpose LLMs (GPT-3.5, GPT-4, Llama 2, PaLM 2) against 200,000+ verifiable legal
  questions built from real federal court cases; finds hallucination rates from 58% (GPT-4) to
  88% (Llama 2), including on tasks as basic as summarizing a case's holding.

- **Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools**
  Magesh, Surani, Dahl, Suzgun, Manning, Ho — 2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.20362)
  Head-to-head audit of commercial legal-AI products (Lexis+ AI, Westlaw AI-Assisted Research)
  against GPT-4; finds hallucination rates of 17%, 33%, and 43% respectively, showing
  retrieval-grounded legal-specific tools substantially outperform general LLMs but are still
  far from hallucination-free.

- **Citation Grounding: Detecting and Reducing LLM Citation Hallucinations via Legal Citation Graphs**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.00898)
  Builds on the Dahl et al. and Magesh et al. findings to propose a legal-citation-graph
  grounding method, explicitly positioning itself against FActScore- and RefChecker-style
  approaches that don't handle structured legal citations well.

- **Who Checks the Citations? Benchmarking Legal Hallucination Detection**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.21155)
  Introduces the LePhantomCite dataset (4,499 citation instances, ~1,100 hallucinated) combining
  real appellate-brief excerpts with systematically injected hallucinations across five
  hallucination types, plus real LLM-generated holdings from Dahl et al.

## Agentic Search / Generative Search Engines

- **Evaluating Verifiability in Generative Search Engines**
  Liu, Zhang, Liang — 2023, Findings of EMNLP 2023
  [Paper](https://arxiv.org/abs/2304.09848)
  Human audit of Bing Chat, NeevaAI, Perplexity.ai, and YouChat; finds only 51.5% of generated
  sentences are fully supported by their citations and only 74.5% of citations actually support
  the sentence they're attached to — one of the earliest systematic citation-precision/recall
  studies of deployed search-and-cite products.

- **Evaluating Robustness of Generative Search Engine on Adversarial Factual Questions**
  2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2403.12077)
  Stress-tests Bing, Perplexity, YouChat, and comparison LLMs with adversarial factual
  questions, reporting citation precision/recall alongside factuality and attack success rate,
  showing citation reliability degrades under adversarial pressure.

- **Detecting and Correcting Reference Hallucinations in Commercial LLMs and Deep Research Agents**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2604.03173)
  Systematically measures citation URL validity for 10 models/agents on DRBench (53,090 URLs)
  and 3 models on ExpertQA (168,021 URLs); finds 3–13% of citation URLs are outright hallucinated
  (no Wayback Machine record) while 5–18% are non-resolving.

- **Generative AI Search Engines as Arbiters of Public Knowledge: An Audit of Bias and Authority**
  2024, arXiv preprint
  [Paper](https://arxiv.org/abs/2405.14034)
  Broader audit-methodology survey covering citation verifiability, source diversity, and bias
  in generative search engines; contextualizes citation-fabrication findings within wider
  concerns about these systems as information gatekeepers.

## Recent / Emerging Work

- **Structural Hallucination in Large Language Models: A Network-Based Evaluation of Knowledge Organization and Citation Integrity**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2603.01341)
  Evaluates hallucination across lexical, biographical, and bibliometric benchmarks using
  network-based analysis; finds citation omission around 91.9% and near-total failure on fields
  like DOI and citation-count reconstruction.

- **Authority, Truth, and Citation Bias: A Large-Scale Multi-Domain Benchmark for Studying Epistemic Susceptibility in Large Language Models**
  2026, arXiv preprint
  [Paper](https://arxiv.org/abs/2606.13104) · [Code](https://github.com/floating-reeds/AuthorityBench)
  Shows that the mere presence of a citation — real or fabricated — increases downstream
  hallucination rates relative to a no-citation baseline, especially when fabricated citations
  are attached to true claims (a 3–22 percentage point increase). Note: an unrelated paper also
  uses the name "AuthorityBench" for a different RAG-authority benchmark
  (`Trustworthy-Information-Access/AuthorityBench`) — the link above is the correct one for this
  entry.

- **LettuceDetect: A Hallucination Detection Framework for RAG Applications**
  2025, arXiv preprint
  [Paper](https://arxiv.org/abs/2502.17125) · [Code](https://github.com/KRLabsOrg/LettuceDetect)
  Lightweight encoder-based span-level hallucination detector trained and evaluated on RAGTruth,
  outperforming other encoder- and prompt-based baselines while being significantly smaller and
  faster.
