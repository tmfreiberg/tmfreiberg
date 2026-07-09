# Tristan Freiberg

**Mathematician and technical communicator working across software correctness, system validation, scientific computing, and technical documentation.**

[LinkedIn](https://www.linkedin.com/in/tmfreiberg/) · Montréal, Canada

I have a PhD in mathematics and a professional background spanning mathematical research, scientific review, university teaching, applied cryptography, and technical writing.

I am increasingly interested in documentation not only as a collection of individual documents but as a system for organizing technical knowledge: how large bodies of material are structured, maintained, versioned, reviewed, and made usable by readers with different needs and levels of expertise. That includes distinguishing tutorials, how-to guides, reference material, and explanation, establishing consistent standards, preserving institutional knowledge, and designing documentation so that it remains useful as a project or organization grows.

This interest grows naturally from a long-standing habit of careful record-keeping. I tend to preserve decisions, assumptions, intermediate reasoning, and operational knowledge rather than leaving them implicit or dependent on memory. In professional settings, that instinct has led me toward single-source documents, reproducible technical materials, engineering manuals, review standards, durable handover records, and documentation that connects technical specialists with less specialized readers.

My projects often begin with an abstract mathematical or analytical question, but they rarely end with a bare computation. I tend to build **inspectable systems** around the underlying idea: executable examples, interactive interfaces, visualizations, persistent data, and documentation intended for readers other than myself.

The projects below range from interactive-proof protocols and computational number theory to quantitative finance, medical imaging, and road-safety data.

## Selected projects

### [Sum-check and GKR](https://github.com/tmfreiberg/sumcheck-gkr-notes)

**Making advanced interactive-proof protocols executable and teachable.**

How can someone verify that a large computation was performed correctly without repeating the entire computation? The sum-check protocol and the Goldwasser–Kalai–Rothblum (GKR) protocol, which builds on it, are foundational tools for addressing that problem.

This project turns their mathematics into interactive Python notebooks and concrete prover–verifier exchanges. It covers finite-field arithmetic, multilinear extensions, arithmetic circuits, soundness, and the layer-by-layer structure of GKR, with circuit visualizations and role-based transcripts that expose the mechanism of each protocol rather than treating it as a black box.

The repository is organized as a modern Python package with four Jupyter notebooks, platform-specific installation guidance, editable installation, optional dependencies, and cross-environment display support. The sum-check treatment is substantially complete; the corresponding pedagogical layer for GKR remains in development. 

**Focus:** verifiable computation, mathematical exposition, Python packaging, Jupyter, Graphviz, pedagogical software design

---

### [Euclid’s Algorithm Analysis](https://github.com/tmfreiberg/euclids_algorithm_analysis)

**An ancient algorithm that still holds mathematical mysteries.**

Euclid’s algorithm is one of the oldest algorithms still in regular use, underlying modern work in number theory, computer algebra, and cryptography. Its basic operation is elementary, but the statistical behavior of its running time remains surprisingly subtle.

<p align="center">
  <a href="https://github.com/tmfreiberg/euclids_algorithm_analysis">
    <img
      src="assets/euclids_algorithm.gif"
      alt="Animated distribution of the number of steps in Euclid's algorithm"
      width="400"
    >
  </a>
    <br>
  <em>The distribution of Euclid’s algorithm step counts approaching its predicted normal limit as the input range grows.</em>
</p>

This project applies the algorithm to nearly **five billion pairs of integers**, records how many division steps each calculation requires, and compares the resulting distributions with theoretical asymptotic predictions. An animation makes the emerging normal distribution visible as the range of inputs grows.

The investigation also sheds numerical light on a secondary constant in the known variance formula—for which, to my knowledge, no previous numerical estimate or closed-form expression is available. The extensive README functions as an expository mathematical article, integrating historical context, derivations, algorithms, plots, animations, and reproducible numerical evidence.

**Focus:** algorithm analysis, large-scale computation, computational statistics, SciPy, SQLite, mathematical visualization, long-form technical exposition

---

### [Primes in Intervals](https://github.com/tmfreiberg/primes_in_intervals)

**Testing competing theories about how prime numbers are distributed.**

Prime numbers appear irregular, but their irregularity has structure. This project asks a concrete statistical question: how often does a short interval contain exactly zero, one, two, or more primes—and which mathematical model best predicts the observed distribution?

<p align="center">
  <a href="https://github.com/tmfreiberg/primes_in_intervals">
    <img
      src="assets/primes_in_intervals.gif"
      alt="Animated empirical distribution of prime counts in short intervals"
      width="400"
    >
  </a>
  <br>
  <em>Empirical prime-count distributions evolving across larger numerical ranges.</em>
</p>

The code supports several different ways of sampling intervals, including disjoint intervals, overlapping sliding intervals, and intervals beginning at primes. A custom postponed sieve generates primes without allocating a large fixed array, while sliding-window updates avoid repeating expensive calculations. Results are stored in SQLite so long-running computations can be extended across sessions.

The empirical distributions are compared with predictions from the Cramér model, the Hardy–Littlewood prime $k$-tuples conjecture, and the more refined Montgomery–Soundararajan model. Plots, tables, and animations show how the distributions change as the interval length and numerical range vary.

The repository combines approximately 2,400 lines of Python with a substantial README and an extended examples guide that functions as a working textbook. Among its demonstrations, one line of code reproduces, in about one second, a historical prime-counting table associated with Gauss.

**Focus:** analytic number theory, reusable algorithm design, custom prime generation, statistical model comparison, SQLite, animation, technical documentation

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

## The common thread

Across these projects, I repeatedly return to the same questions:

* How can an abstract technical idea be made inspectable?
* What does a computation or model actually establish?
* Which assumptions and limitations must be visible to the reader?
* How can code, documentation, and visualization work together as one explanatory system?
* How can technical knowledge be organized so that it remains usable, maintainable, and understandable as a project grows?

That combination of **technical depth, critical evaluation, and reader-oriented documentation** is the center of my work.

I am increasingly interested in extending that approach from individual projects to documentation practice more broadly: building systems that distinguish tutorials, how-to guides, reference material, and explanation; support review and consistent standards; preserve institutional knowledge; and help readers with different levels of expertise find what they need.
