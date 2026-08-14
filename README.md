# Tristan Freiberg

**Mathematician and technical communicator working across software correctness, system validation, scientific computing, and technical documentation.**

[LinkedIn](https://www.linkedin.com/in/tmfreiberg/) · [Publications](https://mathscinet.ams.org/mathscinet/MRAuthorID/895400) · [Preprints](https://arxiv.org/search/math?searchtype=author&query=Freiberg,+T) · [Mathematics Genealogy Project](https://www.genealogy.math.ndsu.nodak.edu/id.php?id=160180)

My background spans mathematical research, scientific review, university teaching, applied cryptography, and technical writing, grounded in doctoral training in mathematics.

I am increasingly interested in documentation not only as a collection of individual documents but as a system for organizing technical knowledge: how large bodies of material are structured, maintained, versioned, reviewed, and made usable by readers with different needs and levels of expertise. That includes distinguishing tutorials, how-to guides, reference material, and explanation, establishing consistent standards, preserving institutional knowledge, and designing documentation so that it remains useful as a project or organization grows.

This interest grows naturally from a long-standing habit of careful record-keeping. I tend to preserve decisions, assumptions, intermediate reasoning, and operational knowledge rather than leaving them implicit or dependent on memory. In professional settings, that instinct has led me toward single-source documents, reproducible technical materials, engineering manuals, review standards, durable handover records, and documentation that connects technical specialists with less specialized readers.

My projects often begin with an abstract mathematical or analytical question, but they rarely end with a bare computation. I tend to build **inspectable systems** around the underlying idea: executable examples, interactive interfaces, visualizations, persistent data, and documentation intended for readers other than myself.

## Selected projects

**[Sum-check and GKR](#sum-check-and-gkr)** — Two foundational verifiable-computation protocols, made executable and teachable. An interactive book where you can play the prover or the verifier and watch a dishonest prover get caught.
*Verifiable computation · Python packaging · executable documents · pedagogical software*

**[Bash Odyssey](#bash-odyssey)** — A tutorial for the Unix command line in which the filesystem is the document. Thirteen episodes of the *Odyssey* as a directory tree: when the Cyclops asks Odysseus his name, you rename a file.
*Technical documentation · learning design · Unix/Linux · shell scripting · cross-platform verification*

**[Human Against Machine](#human-against-machine-skin-lesion-classification)** — A configurable deep-learning pipeline for skin-lesion classification, with a browser demo that runs the model client-side. The evaluation leads with what the model misses rather than what it gets right.
*PyTorch · ONNX · computer vision · leakage prevention · model evaluation · CI/CD*

**[Towards Vision Zero](#towards-vision-zero)** — 1.7 million Quebec collision records, and four independent arguments that no model could predict individual outcomes from them. Reframed around a question the data can actually answer.
*Public-data engineering · XGBoost · information theory · Bayes-error estimation · analytical judgment*

**[Primes in Intervals](#primes-in-intervals)** — Tests a conjectural refinement of the standard probabilistic model for primes at scale, including a secondary term from my own published work. A ten-chapter book that executes the package as it renders.
*Analytic number theory · custom prime generation · SQLite · testing and CI*

**[Euclid's Algorithm Analysis](#euclids-algorithm-analysis)** — Nearly five billion integer pairs, watching the step-count distribution converge to normal, plus a numerical estimate of a constant with no known closed form.
*Algorithm analysis · computational statistics · large-scale computation · NumPy / SciPy*

**[Black–Scholes Option Pricer](#blackscholes-option-pricer)** — A typed, tested option-pricing package whose published document runs the code in your browser. It closes by generating prices from a process the formula gets wrong and watching a volatility smile appear where the theory says there should be none.
*Quantitative finance · numerical methods · property-based testing · in-browser execution · PyPI*

---

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

### [Bash Odyssey](https://github.com/tmfreiberg/bash-odyssey)

**A tutorial for the Unix command line in which the filesystem is the document.**

Most command-line tutorials are a list of commands with example output. The reader types `rm file.txt`, sees that a file disappeared, and learns nothing they will remember a week later. The problem is not the explanation. It is that nothing was at stake.

This project is a thirteen-episode retelling of the *Odyssey* laid out as a directory tree, played entirely with real shell commands. There is no game engine, no runtime, no custom vocabulary to unlearn afterwards. A ninety-line shell script copies the story into a working directory; everything after that is the reader, a terminal, and the tools they are being taught.

<p align="center">
  <a href="https://github.com/tmfreiberg/bash-odyssey">
    <img
      src="assets/bash_odyssey.gif"
      alt="A terminal session: the player moves odysseus.txt out of the ship's crew directory and into the Cyclops cave under the name outis.txt, then later tries to read odysseus.txt and the shell replies: No such file or directory"
      width="500"
    >
  </a>
  <br>
  <em>In Homer, Odysseus escapes the Cyclops by giving his name as Nobody, then ruins it by shouting his real name from the ship as he sails away. Here the trick is a rename — and once it is done, the shell itself will not let you make his mistake.</em>
</p>

The design constraint throughout is that the command must *be* the action rather than illustrate it. When the Cyclops asks Odysseus his name, the reader renames a file, and the trick that saves him in Homer is the same `mv` that saves them. When six men die at Ismarus, the reader chooses which six from a roster of twenty and deletes them, having first read what little the file records about each — one detail apiece, because the narrator never bothered to learn more. `rm` has no undo, and the file says so at the moment it costs something. Eleven ships are lost in a single `rm -r`. The Sirens' song is six hundred lines long and the reader is tied to a mast, so it can only be searched, not read; the three lines that matter most are disguised as the refrain, so the filter that removes the noise removes them too.

Twenty-six commands are introduced across the thirteen episodes, one new tool per problem, each at the point where the story cannot proceed without it. Reference material is separated from narrative: the episodes never explain syntax, and the twenty-six reference documents never mention the plot. Choices persist as filesystem state, so a decision made in the first episode changes what is available in the third, and the closing move of the game is a recursive `diff` of the player's tree against the original — every file they destroyed, created, or altered, which is to say their particular version of the story, computed rather than asserted.

The engineering is small but the correctness requirements are not, since every instruction in the prose is a claim about what the reader's machine will do. Cross-platform behaviour was verified rather than assumed: `chmod` proved to enforce write permissions under Git Bash on Windows but not read permissions, so the reference document says exactly that and shows the reader how to test it themselves. Consistency across roughly two hundred files — paths, a crew roster that has to survive nine episodes of attrition, timestamps that a plain `cp` would silently flatten — is maintained by scripted audits rather than by rereading.

**Focus:** technical documentation, learning design, progressive disclosure, tutorial versus reference separation, Unix/Linux command line, shell scripting, cross-platform verification, Git Bash, editorial consistency at scale

---

### [Human Against Machine: Skin Lesion Classification](https://tmfreiberg.github.io/human-against-machine/)

**A configurable deep-learning pipeline for classifying dermatoscopic images, with a browser demo that runs the model client-side.**

This began as a team project at the Erdős Institute's Spring 2024 Deep Learning Boot Camp and has since been rebuilt from scratch as an installable Python package. It uses the HAM10000 dataset to investigate binary and multiclass skin-lesion classification with fine-tuned ResNet-18 models.

The interesting problems were not in training the network. The dataset is strongly imbalanced, photographs many lesions more than once, and carries acquisition artifacts a model can learn as shortcuts. Splitting therefore happens at the lesion level so that near-duplicate images cannot straddle the train/validation boundary, and the guarantee is asserted in tests rather than assumed. Experiments are defined in YAML and identified by a hash of the configuration, so a run directory names exactly one set of settings and records them alongside its artifacts.

Evaluation reports balanced accuracy against its chance level, per-class recall with support, confusion matrices, and two competing decision rules for melanoma, rather than leaning on raw accuracy. The seven-class model reaches 0.69 balanced accuracy where guessing scores 0.14, and the write-up leads with what that means clinically: it misses about two melanomas in five.

The accompanying book explains every design decision and its limitations, and the challenge page lets you attempt the same task against the model, with a quantised ONNX network running entirely in your browser.

This is an educational machine-learning project, not a clinical diagnostic system.

<p align="center">
  <a href="https://tmfreiberg.github.io/human-against-machine/">
    <img
      src="assets/human_against_machine.gif"
      alt="The challenge page: a dermatoscopic image from the HAM10000 dataset is shown, the user picks a diagnosis, and the page reveals the true label alongside the model's prediction and a running tally"
      width="500"
    >
  </a>
  <br>
  <em>The challenge page: dermatoscopic images from HAM10000, your guess against the model's, scored as you go. The network runs entirely in your browser.</em>
</p>

**Focus:** PyTorch, ONNX, transfer learning, computer vision, leakage prevention, class imbalance, experimental design, model evaluation, testing, CI/CD, Quarto

---

### [Towards Vision Zero](https://tmfreiberg.github.io/towards-vision-zero/)

**A road-safety project whose most important result was establishing what its data could not support.**

This project analyzes 1.7 million Quebec traffic collision records from 2011 through 2022. The codebase includes multi-year data ingestion, a bilingual machine-readable data dictionary, feature engineering, XGBoost and four other estimator families under identical conditions, per-class evaluation with Matthews correlation, information-theoretic bounds on achievable performance, permutation tests, an interactive explorer over the full dataset, and a Quarto book that regenerates every figure from source.

<p align="center">
  <a href="https://tmfreiberg.github.io/towards-vision-zero/">
    <img
      src="assets/towards_vision_zero.gif"
      alt="Interactive explorer filtering 1.7 million Quebec collision records by road and vehicle conditions, showing the distribution of actual outcomes among matching historical collisions"
      width="500"
    >
  </a>
  <br>
  <em>The retrospective explorer: choose a set of conditions and it reports how comparable historical collisions actually turned out — counts, not predictions.</em>
</p>

The original goal was to predict whether a collision would result in property damage, minor injury, or serious injury or death. The model reaches a Matthews correlation of 0.44 on held-out records, which in most settings would indicate something that worked. On the same records it predicted a serious collision seven times out of forty-one thousand, and was right once.

Rather than report the first number and omit the second, I set out to establish whether any model could do better. Four independent arguments say no: collisions recorded identically on all eighteen variables frequently turn out differently; the information the features carry puts a floor under the error rate; five estimator families land in the same place; and a learning curve that flattens says more records of the same kind would not help. The variables a city actually controls — road configuration, surface, lighting, posted speed — add almost nothing once you know who was involved.

I therefore reframed the project around a question the data can answer. The interactive explorer finds historical collisions matching a user's selected conditions and shows the distribution of outcomes among those comparable records. No model, no threshold, no prediction: it counts.

That pivot is the most important feature of the project. There is a difference between reporting that a model is not good enough and establishing that no model could be, and the second is checkable. Knowing which one you face is worth more than another round of tuning.

**Focus:** public-data engineering, XGBoost, model evaluation, information theory, Bayes-error estimation, permutation testing, held-out discipline, bilingual documentation, Quarto, analytical judgment

---

### [Primes in Intervals](https://tmfreiberg.github.io/primes-in-intervals/)

**Testing a refinement of the standard probabilistic model for prime numbers.**

Prime numbers appear irregular, but their irregularity has structure. This project asks a concrete statistical question: how often does a short interval contain exactly zero, one, two, or more primes, and how closely does theory predict the answer?


<p align="center">
  <a href="https://tmfreiberg.github.io/primes-in-intervals/">
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

### [Euclid's Algorithm Analysis](https://tmfreiberg.github.io/euclids-algorithm-analysis/)

**An ancient algorithm that still holds mathematical mysteries.**

Euclid's algorithm is one of the oldest algorithms still in regular use, underlying modern work in number theory, computer algebra, and cryptography. Its basic operation is elementary, but the statistical behavior of its running time remains surprisingly subtle.

<p align="center">
  <a href="https://tmfreiberg.github.io/euclids-algorithm-analysis/">
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

### [Black-Scholes Option Pricer](https://tmfreiberg.github.io/black-scholes-option-pricer/)

**Turning a pricing formula into an inspectable system, and then showing where the formula fails.**

Black-Scholes gives a closed-form value for a European option. This project builds the library around it, covering prices, the five Greeks, no-arbitrage bounds, implied volatility, and sensitivity surfaces, and then publishes a document whose code cells run that library in the reader's browser. Nothing is precomputed and nothing is sent to a server: the page installs the released package into a Python runtime compiled to WebAssembly, and the code shown is the code the tests run.

<p align="center">
  <a href="https://tmfreiberg.github.io/black-scholes-option-pricer/">
    <img
      src="assets/smile.png"
      alt="Black-Scholes implied volatility against strike for prices generated three ways"
      width="500"
    >
  </a>
  <br>
  <em>Implied volatility against strike. The flat line is the control: with no jumps, the generating model is Black–Scholes and the inversion returns the input exactly.</em>
</p>

The closing section is the reason the project exists in its current form. Implied volatility is *defined* by inverting Black-Scholes at an observed price, so if the model were correct, every option on one underlying at one expiry would imply the same volatility. Real markets disagree, and the document demonstrates the mechanism rather than asserting it: prices are generated under a jump-diffusion process, whose returns are not lognormal, then read back through Black-Scholes. The implied volatilities vary with strike, and the shape encodes *which way* the true distribution departs from the assumed one. The control case carries the argument, because with the jumps switched off the same pipeline returns a flat line, so a curve elsewhere cannot be an artifact of the solver.

That argument only works if the numbers are trustworthy, so the verification is the substance. The package carries no SciPy at runtime: the normal distribution function and the root-finder are implemented directly, which is what keeps the wheel small enough to load into a browser, and which creates the obligation to prove them right. They are checked against independent oracles, namely the standard library, SciPy, and a 50-digit reference implementation, at tolerances tighter than either library's own defaults. Every Greek is checked against a finite difference of the price function it claims to differentiate. Accuracy bounds are asserted to be *tight* rather than merely satisfied, so the stated error is a measurement rather than a comfortable margin.

Property-based testing and a multi-version test matrix found defects that example-based tests would not have: an overflow triggered only by subnormal volatility, two floating-point underflows in the root-finder that appear when inverting deep out-of-the-money prices, and a resource leak visible on one Python version and not another. The suite is 282 tests at 100% branch coverage, with every docstring example executed so that documentation cannot drift from behavior. The package is published to PyPI, released through an automated workflow that runs the full gate before uploading, and the document refuses to deploy if its pinned version is not actually available.

**Focus:** quantitative finance, numerical methods, property-based testing, floating-point correctness, Python packaging, PyPI release automation, Pyodide / WebAssembly, Quarto / executable documents, CI/CD, SQLite

---

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
