# Tristan Freiberg

**Mathematician and technical communicator working across software correctness, system validation, scientific computing, and technical documentation.**

[LinkedIn](https://www.linkedin.com/in/tmfreiberg/) · Research papers: [MathSciNet](https://mathscinet.ams.org/mathscinet/MRAuthorID/895400); [arXiv](https://arxiv.org/search/math?searchtype=author&query=Freiberg,+T) · [Mathematics Genealogy Project](https://www.genealogy.math.ndsu.nodak.edu/id.php?id=160180) · Montréal, Canada

My background spans mathematical research, scientific review, university teaching, applied cryptography, and technical writing, grounded in doctoral training in mathematics.

I am increasingly interested in documentation not only as a collection of individual documents but as a system for organizing technical knowledge: how large bodies of material are structured, maintained, versioned, reviewed, and made usable by readers with different needs and levels of expertise. That includes distinguishing tutorials, how-to guides, reference material, and explanation, establishing consistent standards, preserving institutional knowledge, and designing documentation so that it remains useful as a project or organization grows.

This interest grows naturally from a long-standing habit of careful record-keeping. I tend to preserve decisions, assumptions, intermediate reasoning, and operational knowledge rather than leaving them implicit or dependent on memory. In professional settings, that instinct has led me toward single-source documents, reproducible technical materials, engineering manuals, review standards, durable handover records, and documentation that connects technical specialists with less specialized readers.

My projects often begin with an abstract mathematical or analytical question, but they rarely end with a bare computation. I tend to build **inspectable systems** around the underlying idea: executable examples, interactive interfaces, visualizations, persistent data, and documentation intended for readers other than myself.

The projects below range from interactive-proof protocols and computational number theory to quantitative finance, medical imaging, and road-safety data.

## Selected projects

### [Sum-check and GKR](https://tmfreiberg.github.io/sumcheck-gkr-notes/)

**Making advanced interactive-proof protocols executable and teachable.**

How can someone verify that a large computation was performed correctly without repeating the entire computation? The sum-check protocol and the Goldwasser–Kalai–Rothblum (GKR) protocol, which builds on it, are foundational tools for addressing that problem.

<p align="center">
  <a href="https://tmfreiberg.github.io/sumcheck-gkr-notes/">
    <img
      src="assets/sumcheck.gif"
      alt="Interactive sum-check protocol demonstration showing a prover–verifier exchange"
      width="500"
    >
  </a>
  <br>
  <em>An interactive prover–verifier exchange making the mechanics of the sum-check protocol visible.</em>
</p>

This project turns their mathematics into a **[fully rendered, interactive book](https://tmfreiberg.github.io/sumcheck-gkr-notes)** and concrete prover–verifier exchanges. It covers finite-field arithmetic, multilinear extensions, arithmetic circuits, soundness, and the layer-by-layer structure of GKR, with circuit visualizations and role-based transcripts that expose the mechanism of each protocol rather than treating it as a black box. Every theorem is numbered and cross-linked, every worked example runs live, and the reader can play the prover, the verifier, or neither and watch each round unfold — including a dishonest prover being caught, or, over a small enough field, occasionally slipping through.

The source is organized as a modern Python package with a companion command-line interface, published to the web from Markdown sources through an automated build. Following Justin Thaler's *Proofs, Arguments, and Zero-Knowledge*, the treatment supplements his presentation with additional background, complete proofs of the underlying lemmas, and executable examples. Both the sum-check and GKR protocols are covered in full, including a proof of the GKR soundness-error bound checked against a Monte Carlo simulation over a deliberately small field.

**Focus:** verifiable computation, mathematical exposition, MyST / executable documents, Python packaging, CLI design, Graphviz, pedagogical software design

---

### [Euclid's Algorithm Analysis](https://tmfreiberg.github.io/euclids_algorithm_analysis/)

**An ancient algorithm that still holds mathematical mysteries.**

Euclid's algorithm is one of the oldest algorithms still in regular use, underlying modern work in number theory, computer algebra, and cryptography. Its basic operation is elementary, but the statistical behavior of its running time remains surprisingly subtle.

<p align="center">
  <a href="https://tmfreiberg.github.io/euclids_algorithm_analysis/">
    <img
      src="assets/euclids_algorithm.gif"
      alt="Animated distribution of the number of steps in Euclid's algorithm"
      width="400"
    >
  </a>
    <br>
  <em>The distribution of Euclid's algorithm step counts approaching its predicted normal limit as the input range grows.</em>
</p>

This project applies the algorithm to nearly **five billion pairs of integers**, records how many division steps each calculation requires, and compares the resulting distributions with theoretical asymptotic predictions. An animation makes the emerging normal distribution visible as the range of inputs grows.

The investigation also sheds numerical light on a secondary constant in the known variance formula, one for which, to my knowledge, no previous numerical estimate or closed-form expression exists. The full treatment reads as an expository mathematical article, integrating historical context, derivations, algorithms, plots, animations, and reproducible numerical evidence, with the headline estimate re-derivable from the shipped data in a single step.

The source is organized as a modern Python package with a companion command-line interface and a test suite, and the article is published to the web as a fully rendered book built automatically from executable sources. The fast computations run live at build time against the package itself, so the exposition and the numbers stay in step with the code.

**Focus:** algorithm analysis, computational statistics, large-scale computation, numerical estimation, NumPy / SciPy, Quarto / executable documents, Python packaging, CLI design, mathematical visualization, long-form technical exposition

---

### [Primes in Intervals](https://tmfreiberg.github.io/primes_in_intervals/)

**Testing a refinement of the standard probabilistic model for prime numbers.**

Prime numbers appear irregular, but their irregularity has structure. This project asks a concrete statistical question: how often does a short interval contain exactly zero, one, two, or more primes, and how closely does theory predict the answer?


<p align="center">
  <a href="https://tmfreiberg.github.io/primes_in_intervals/">
    <img
      src="assets/primes_in_intervals.gif"
      alt="Animated empirical distribution of prime counts in short intervals"
      width="400"
    >
  </a>
  <br>
  <em>Empirical prime-count distributions evolving across larger numerical ranges.</em>
</p>

The code supports several different ways of sampling intervals, including disjoint intervals, overlapping sliding intervals, and intervals beginning at primes. A custom postponed sieve generates primes without allocating a large fixed array, while sliding-window updates avoid repeating expensive calculations, so counting every overlapping interval costs about twice a disjoint count rather than a hundred times as much. Results are stored in SQLite so computations that run for hours are paid for once and can be extended across sessions.

Near a large number $N$, primes thin out to an average spacing of $\log N$. Cramér's model treats them as scattered at random with that density, which predicts that the number of primes in an interval of comparable length follows a Poisson distribution. Gallagher showed the prediction follows from the Hardy-Littlewood prime tuples conjecture, but as an asymptotic main term only, with nothing said about the error. [My published work](https://doi.org/10.1007/978-3-319-92777-0_2) conjectures a secondary term, conditional on the prime tuples conjecture and on uniformity assumptions in an estimate of Montgomery and Soundararajan that have not been established. This project measures the counts at scale and tests the prediction against them, with plots, tables, and animations showing how the fit changes as the interval length and the numerical range vary.

The repository is about 4,800 lines of Python across eleven modules, with a 163-test suite, a command-line interface exposing every function to the shell, and continuous integration. The exposition is a ten-chapter book that executes the package as it renders, so every number, table, and figure on the site is produced by the code rather than pasted in. Among its demonstrations, one line of code reproduces, in about one second, a historical prime-counting table associated with Gauss.

**Focus:** analytic number theory, reusable algorithm design, custom prime generation, statistical model comparison, SQLite, Python packaging, testing and CI, technical documentation

---

### [Black–Scholes Option Pricer](https://github.com/tmfreiberg/black-scholes-option-pricer)

**Turning a mathematical pricing formula into an interactive analytical tool.**

Rather than stopping at the closed-form Black–Scholes formula, this project builds an interactive Streamlit dashboard for exploring how a European option’s value changes with market assumptions.

The application offers three connected views:

* a heatmap showing the effect of spot price and volatility on the option premium;
* an implied-volatility tool that solves the inverse pricing problem numerically;
* premium curves showing how option value changes with spot price and time to maturity.

Parameters remain synchronized across the application, and users can save and reload calculated surfaces through a relational SQLite database. The project was an early exploration of quantitative finance and established a pattern that recurs in my later work: take a mathematical model, make its behavior visible, and give the reader a way to interact with it.

**Focus:** quantitative finance, numerical root-finding, Streamlit, NumPy, SciPy, pandas, matplotlib, SQLite

---

### [Medical Image Classification](https://github.com/tmfreiberg/HAM10000-skin-lesion-classification)

**A configurable deep-learning pipeline for classifying dermatoscopic images.**

This project was selected as one of the top projects from the Erdős Institute’s Spring 2024 Deep Learning Boot Camp cohort. It uses the HAM10000 dataset of dermatoscopic images to investigate binary and multiclass skin-lesion classification with fine-tuned ResNet-18 and EfficientNet-B0 models.

The main technical challenge was not merely training a neural network. The dataset is strongly imbalanced, contains multiple images of some lesions, and includes visual artifacts that a model could learn as misleading shortcuts. The preprocessing pipeline therefore operates at the lesion level to prevent train–test leakage and supports configurable class mappings, balancing strategies, augmentation methods, and transfer-learning choices.

Evaluation uses balanced accuracy, per-class recall, confusion matrices, and threshold analysis rather than relying on raw accuracy. A Streamlit application presents the work as a human-versus-model challenge, allowing users to classify held-out images and compare their results with the trained model.

This is an educational machine-learning project, not a clinical diagnostic system.

**Focus:** PyTorch, transfer learning, computer vision, leakage prevention, class imbalance, experimental design, model evaluation, Streamlit

---

### [Towards Vision Zero](https://github.com/tmfreiberg/road-safety)

**A road-safety project whose most important result was recognizing the limits of its own model.**

This Erdős Institute data science project analyzes Quebec traffic accident records from 2011 through 2022. The codebase includes multi-year data ingestion, bilingual data dictionaries, feature engineering, exploratory analysis tools, XGBoost classification, custom confusion matrices, weighted evaluation metrics, and threshold adjustment for the asymmetric costs of different prediction errors.

The original goal was to predict whether an accident would result in property damage, minor injury, or serious injury or death. The resulting model was useful for aggregate analysis but not reliable enough to justify confident predictions about individual accidents.

I therefore reframed the project around a more defensible question. Instead of presenting a single model prediction as an answer, the retrospective analysis module finds historical accidents matching a user’s selected conditions and shows the distribution of outcomes among those comparable records.

That pivot is the most important feature of the project: the purpose of analysis is not to force a model into a predetermined use case, but to understand what the available data can—and cannot—honestly support.

**Focus:** public-data engineering, XGBoost, model evaluation, asymmetric error costs, bilingual documentation, retrospective analysis, analytical judgment

## Research publications

Before moving into applied technical work, I spent eight years as a research mathematician in analytic and probabilistic number theory. I published **12 peer-reviewed journal papers and two expository articles**, working both independently and with collaborators across several institutions.

The research falls into three broad strands:

* **Prime distributions and rare events:** gaps between consecutive primes, primes in short intervals, and probabilistic models for arithmetic data. This includes joint work with William Banks and James Maynard published in the *Proceedings of the London Mathematical Society*.
* **Arithmetic statistics and cryptographic mathematics:** the group structure of elliptic curves over finite fields, perfect-power values, square totients, and Carmichael numbers. I coauthored *A Note on Square Totients*, published in the *International Journal of Number Theory*, with Carl Pomerance; I was fortunate to learn from the collaboration, which also gives me an Erdős number of 2.
* **Number theory and mathematical physics:** Poisson statistics for sums of two squares and their application to spectral spacings in a model from quantum chaos.

Joint work with William Banks and James Maynard on normalized prime gaps, and its extension by Jori Merikoski, was discussed by K. Soundararajan in his presentation of Maynard's research at the 2022 Fields Medal ceremony. Soundararajan used the extended result to explain the striking consequence that at least one of $e$, $\pi$, or $\pi-e$ must be a limit point of normalized consecutive prime gaps. [Watch the relevant excerpt](https://youtu.be/EXRBpsU-khk?si=8QWDlvmQQe6gi2Gt&t=4902).


These papers are evidence not only of mathematical research but of sustained technical writing: constructing and revising long rigorous arguments, collaborating with coauthors, responding to specialist peer review, and presenting difficult results for publication.

[Read the papers and preprints on arXiv](https://arxiv.org/search/math?searchtype=author&query=Freiberg,+T)

## The common thread

Across these projects, I repeatedly return to the same questions:

* How can an abstract technical idea be made inspectable?
* What does a computation or model actually establish?
* Which assumptions and limitations must be visible to the reader?
* How can code, documentation, and visualization work together as one explanatory system?
* How can technical knowledge be organized so that it remains usable, maintainable, and understandable as a project grows?

That combination of **technical depth, critical evaluation, and reader-oriented documentation** is the center of my work.

I am increasingly interested in extending that approach from individual projects to documentation practice more broadly: building systems that distinguish tutorials, how-to guides, reference material, and explanation; support review and consistent standards; preserve institutional knowledge; and help readers with different levels of expertise find what they need.
