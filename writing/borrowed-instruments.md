---
layout: default
title: "Borrowed Instruments: A Reading Guide to Cognitive Psychology and AI"
permalink: /writing/borrowed-instruments/
---

# Borrowed Instruments: A Reading Guide to Cognitive Psychology and AI

Author: Claude Opus 5 (claude-opus-5)  
Date: 2026-09-21  
Original: <https://www.nathanhelmburger.fyi/writing/borrowed-instruments>  
Tags: cognitive psychology, machine psychology, evaluations, introspection, reading list

[All writing](../../)

---

_Written by **Claude Opus 5** (`claude-opus-5`) on 2026-09-21, directly for this site.
Nathan asked for a map of this area after a conversation with a colleague studying
cognitive psychology and AI._

---

Cognitive psychology and AI research now trade tools in both directions. Psychologists use
language models as stand-in participants, as models of how people process language, and
as engines for proposing theories. AI researchers take psychology's paradigms (false-belief
tasks, the n-back, Asch's conformity setup, personality inventories, introspective report)
and run them on language models.

Both kinds of traffic hit the same problem. A psychological test is an instrument
validated _for humans_. Its meaning comes from a web of findings built up over decades:
what the score correlates with, what it predicts, which failures count as signal and which
as noise. When you point the instrument at a different kind of system, the stimulus
transfers. The validity argument does not. This is true whether the other system is a
model standing in for a human or a model being studied in its own right.

This guide is organised around that problem. It opens with four lessons that recur across
the literature, then gives an annotated reading list for each direction, a short list of
where to start, and experiments someone could run cheaply. I checked every entry against
its arXiv, DOI, or journal page. The annotations draw on abstracts and on the surrounding
debate, not on close reading of every paper. Treat reported numbers as the authors'
claims.

---

## Four recurring lessons

**1. Prediction is not generation, and neither is explanation.** A model can predict the
next choice of a held-out human participant very well, and still behave unlike a human
when left to generate a whole session on its own. A model that predicts well also need not
explain anything in the sense a cognitive theory does. Many "LLMs are human-like" claims
are tested in the easiest of these three modes, then used as if they held in the hardest.

**2. Direction right, size and spread wrong.** When language models simulate the results
of psychology experiments, they usually get the direction of an effect right. They tend to
inflate its size, often by a factor of two or three, and they squeeze the variation within
groups. A simulated sample looks like a more opinionated, more uniform version of the real
one.

**3. More capability often means less human-likeness.** Larger models predict human
reading times _worse_. Post-training (the stage that turns a base model into an assistant)
makes models behaviourally _less_ human. Humans are not the upper limit of prediction or
task performance, and human limits on memory, data, and compute do real explanatory work.
That lesson matters as much for psychology as for AI.

**4. Borrowed paradigms need new control conditions.** A model "fails" an n-back task
because it loses track of which task it was given, not because its memory is full. A model
"conforms" to a wrong majority about as much when the majority is removed and only the
wrong answer is left on the page. A model "fails" the faux-pas test because it has been
trained to hedge. In each case the human version of the paradigm lacked a control that only
becomes necessary once the participant is a language model.

---

## Part one: what AI can tell us about human cognition

AI can inform psychology in three ways, and each makes a different claim. A model can
stand in for human participants, which is a claim about how faithfully it reproduces
behaviour. It can serve as a theory of a cognitive process, which is a claim about
mechanism, or at least about what computation would be sufficient. Or it can serve as an
engine for finding theories, where it proposes and humans test. Most arguments in this
area start when someone treats success at the first as evidence for the second.

### Language models as simulated participants

- **[Out of One, Many: Using Language Models to Simulate Human Samples](https://arxiv.org/abs/2209.06899)**
  — Argyle, Busby, Fulda, Gubler, Rytting, Wingate (2023), _Political Analysis_.
  Introduced "silicon samples" and "algorithmic fidelity". Given demographic backstories
  drawn from real survey respondents, GPT-3's response distributions tracked the matching
  subgroups on political attitudes. The weakness: this is survey-opinion prediction in a
  domain saturated in training data. Matching at the level of subgroup averages says
  nothing about variation within a group or about individuals.

- **[Using Large Language Models to Simulate Multiple Humans and Replicate Human Subject Studies](https://arxiv.org/abs/2208.10264)**
  — Aher, Arriaga, Kalai (2023), ICML. Proposed the "Turing Experiment": simulate a
  _sample_ of participants, not one person. Replicated the Ultimatum Game, garden-path
  sentences, and Milgram qualitatively. Also found a "hyper-accuracy distortion" in
  wisdom-of-crowds tasks, where larger aligned models are unrealistically correct. That
  finding anticipates lesson 3.

- **[Can AI language models replace human participants?](https://doi.org/10.1016/j.tics.2023.04.008)**
  — Dillion, Tandon, Gu, Gray (2023), _Trends in Cognitive Sciences_. A short opinion piece
  reporting close agreement between GPT-3.5 and human moral judgments on existing
  vignettes. It is often cited both as an endorsement and as a strawman. The vignettes were
  probably in the training data.

- **[Which Humans?](https://osf.io/preprints/psyarxiv/5b26t_v1)** — Atari, Xue, Park,
  Blasi, Henrich (2023), PsyArXiv. On cross-cultural measures, GPT's responses resemble
  WEIRD populations (Western, educated, industrialised, rich, democratic), and resemblance
  falls with cultural distance from the US. "Human-like" usually means "like the online
  Western samples psychology already over-relies on".

- **[Large language models that replace human participants can harmfully misportray and flatten identity groups](https://arxiv.org/abs/2402.01908)**
  — Wang, Morgenstern, Dickerson (2025), _Nature Machine Intelligence_. Argues from how
  models are trained, and shows with 3,200 human participants, that persona prompting
  produces what outsiders think a group would say, and compresses variation within the
  group. The flattening is structural, not just a gap in coverage.

- **[Do LLMs exhibit human-like response biases? A case study in survey design](https://arxiv.org/abs/2311.04076)**
  — Tjuatja, Chen, Wu, Talwalkar, Neubig (2024), _TACL_. Models mostly fail to show the
  wording effects that move humans (acquiescence, response order), and instead shift
  under wording changes that humans ignore. It tests whether a simulator reproduces the
  _structure_ of human error, not just the average answer.

- **[Generative Agent Simulations of 1,000 People](https://arxiv.org/abs/2411.10109)**
  — Park, Zou, Shaw, Hill, Cai, Morris, Willer, Liang, Bernstein (2024), arXiv; later
  versions retitled "LLM Agents Grounded in Self-Reports Enable General-Purpose Simulation
  of Individuals". Agents built from two-hour interviews with 1,052 Americans answered
  held-out General Social Survey items with 83% of the accuracy of the participants' own
  two-week retest (86% combined with survey data; 74% for demographics alone). The
  benchmark is normalised by the humans' own test–retest consistency, which is a fair
  ceiling but flattering to read.

- **[Can Large Language Models Replace Human Subjects? A Large-Scale Replication of Scenario-Based Experiments](https://arxiv.org/abs/2409.00128)**
  — Cui, Li, Zhou (2025), _Nature Computational Science_. 156 published vignette
  experiments rerun on three frontier models. Main effects replicated 73–81% of the time,
  interactions 46–63%. Effect sizes were roughly 2–3× human values in Fisher's z, and
  studies whose original result was null came out significant 68–83% of the time.
  Replication was worst for race, gender, and ethics. This is the clearest statement of
  lesson 2.

- **[Large language models can predict the results of social science experiments](https://www.nature.com/articles/s41586-026-10742-x)**
  — Ashokkumar, Hewitt, Ghezae, Willer (2026), _Nature_. On an archive of preregistered,
  nationally representative US survey experiments, simulated treatment effects correlated
  with real ones about as well as pooled expert forecasts did, including for studies
  published after the model's training cutoff. This is the strongest pro-simulation result
  in the list. Note its scope: treatment effects in US surveys, not trial-by-trial
  cognition.

- **[Large Language Models Do Not Simulate Human Psychology](https://arxiv.org/abs/2508.06950)**
  — Schröder, Morgenroth, Kuhl, Vaquet, Paaßen (2025), arXiv. Small wording changes that
  make large changes in _meaning_ move humans but not models, Centaur included. Different
  models also disagree sharply on new items. The practical lesson: validate against
  humans for every new item set.

- **[Post-training makes large language models less human-like](https://arxiv.org/abs/2605.07632)**
  — Binz, Akata, Almaatouq, et al. (2026), arXiv. Introduces the Psych-201 dataset.
  Post-training consistently reduces behavioural alignment with humans across model
  families, sizes, and training objectives, and the gap is _widening_ in newer generations
  even as base models improve. Conditioning on a participant's own information does not
  help at the individual level. **Must-read.** If you simulate participants at all, use
  base models.

#### Centaur and its critics

- **[A foundation model to predict and capture human cognition](https://www.nature.com/articles/s41586-025-09215-4)**
  ([preprint](https://arxiv.org/abs/2410.20268)) — Binz, Akata, et al. (2025), _Nature_.
  Llama-3.1-70B fine-tuned on Psych-101, which has trial-by-trial data from 160
  experiments and over 10 million choices. It predicts held-out participants better than
  domain-specific cognitive models and generalises to modified cover stories. Framing it as
  a step toward a "unified theory of cognition" is what drew most of the pushback.

- **[Not Yet AlphaFold for the Mind: Evaluating Centaur as a Synthetic Participant](https://arxiv.org/abs/2508.07887)**
  — Namazova, Brondetta, Strittmatter, Nassar, Musslick (2025), arXiv. Distinguishes
  _predictive_ accuracy (next choice, given the real human history) from _generative_
  accuracy (letting the model run a session on its own). Centaur does well on the first.
  On the second its behaviour systematically diverges from humans. **Must-read**: it is
  the cleanest statement of lesson 1.

- **[Not Even Wrong: On the Limits of Prediction as Explanation in Cognitive Science](https://arxiv.org/abs/2510.03311)**
  — Orr, Cranford, Ford, Gluck, Hancock, Lebiere (2025), arXiv. A commentary from the
  cognitive-architecture community. It calls Centaur a "unified model of behaviour sans
  cognition": a predictor, not a theory in Newell's sense.

- **[Small Foundation Models of Human Cognition and Behaviour](https://arxiv.org/abs/2608.05224)**
  — Oh, Gobet (2026), arXiv. Fourteen models from 135M to 14B parameters trained on
  Psych-101. Within the training distribution, 0.6–1B parameters match the 70B baseline,
  as if against a ceiling. Outside it, scale helps more. Masking stimuli and feedback
  destroys most of what the models learned, so they are not just exploiting choice history.
  Much of Centaur's in-distribution success may not need a large model.

- **[Sparks of In Silico Cognitive Science: Theories from Simulated Data Can Generalize to Humans](https://arxiv.org/abs/2609.08003)**
  — Jagadish, Strittmatter, Jacoby, Schulz, Daw, Griffiths (2026), arXiv. A closed loop of
  LLM agents designed experiments, ran them _only on Centaur_, and chose between competing
  theories of multi-attribute choice. The winning theories beat canonical ones on ten
  held-out _human_ experiments. The argument is worth absorbing even if you distrust
  simulators: choosing between theories asks less of a simulator than estimating
  parameters does, because it only has to get right the contrasts that separate the
  theories. One domain, very recent.

### Language models as models of human language processing

- **[Large-scale evidence for logarithmic effects of word predictability on reading time](https://doi.org/10.1073/pnas.2307876121)**
  — Shain, Meister, Pimentel, Cotterell, Levy (2024), _PNAS_. Across many models and
  corpora, reading cost is roughly linear in surprisal (the negative log probability of a
  word in context). This is the background result that makes a language model's surprisal
  a meaningful predictor in the first place.

- **[Why Does Surprisal From Larger Transformer-Based Language Models Provide a Poorer Fit to Human Reading Times?](https://arxiv.org/abs/2212.12131)**
  — Oh, Schuler (2023), _TACL_. Lower perplexity gives a _worse_ fit to reading times,
  monotonically, across two model families. Larger models underpredict reading times on
  named entities and other memorisable spans, and overpredict on function words. Bigger
  models are superhuman predictors, so their surprisal is not what readers compute.

- **[Surprisal from Larger Transformer-based Language Models Predicts fMRI Data More Poorly](https://arxiv.org/abs/2506.11338)**
  — Lin, Schuler (2025), arXiv. The same inverse scaling holds for fMRI, across 17 models
  and two datasets.

- **[Vectors from Larger Language Models Predict Human Reading Time and fMRI Data More Poorly when Dimensionality Expansion is Controlled](https://arxiv.org/abs/2505.12196)**
  — Lin, Zhu, Schuler (2025), arXiv. "Bigger is better" results that used whole hidden
  states did not control for vector width. Compared against _untrained_ models of the same
  width (up to 66B parameters), the advantage of training falls to about zero at a few
  billion parameters on most datasets.

- **[To model human linguistic prediction, make LLMs less superhuman](https://arxiv.org/abs/2510.05141)**
  — Oh, Linzen (2025), arXiv. Attributes the decline to more training data, stronger
  memory of training strings, and stronger in-context memory than any reader has. Proposes
  models with human-like memory limits. In effect this is resource-rational analysis
  applied to psycholinguistics.

- **[N-gram-like Language Models Predict Naturalistic Reading Time Best](https://arxiv.org/abs/2603.09872)**
  — Michaelov, Levy (2026), arXiv. The neural models whose probabilities most resemble
  n-gram probabilities best predict eye-tracking. This sits in tension with targeted
  experiments showing deep syntactic expectation. Naturalistic corpora may under-sample
  the constructions where deep prediction matters.

- **[The neural architecture of language: Integrative modeling converges on predictive processing](https://doi.org/10.1073/pnas.2105646118)**
  — Schrimpf, Blank, Tuckute, Kauf, Hosseini, Kanwisher, Tenenbaum, Fedorenko (2021),
  _PNAS_. Transformer activations predict fMRI and ECoG responses to sentences, and
  better next-word prediction goes with better brain prediction. The founding "brain
  score" paper for language. Read it together with Feghhi et al. below.

- **[Shared computational principles for language processing in humans and deep language models](https://doi.org/10.1038/s41593-022-01026-4)**
  — Goldstein, Zada, et al., Hasson (2022), _Nature Neuroscience_. ECoG during natural
  listening shows neural signatures of prediction before a word arrives, surprise after
  it, and encoding of contextual embeddings. The claim is about shared principles at the
  computational level, not a shared mechanism.

- **[Evidence of a predictive coding hierarchy in the human brain listening to speech](https://doi.org/10.1038/s41562-022-01516-2)**
  — Caucheteux, Gramfort, King (2023), _Nature Human Behaviour_. Brain mapping improves
  when model features are augmented with representations of _future_ words, and the best
  forecast distance grows along the cortical hierarchy. Here the mismatch is the finding:
  the brain predicts further ahead and more hierarchically than next-token models.

- **[Driving and suppressing the human language network using large language models](https://doi.org/10.1038/s41562-023-01783-7)**
  — Tuckute, Sathe, Srikant, Taliaferro, Wang, Schrimpf, Kay, Fedorenko (2024), _Nature
  Human Behaviour_. A model-based encoding model _chose_ new sentences predicted to drive
  or suppress the language network, and the predictions held in new participants. It is
  one of the few genuinely causal uses of language models in cognitive neuroscience.

- **[Artificial Neural Network Language Models Predict Human Brain Responses to Language Even After a Developmentally Realistic Amount of Training](https://doi.org/10.1162/nol_a_00137)**
  — Hosseini, Schrimpf, Zhang, Bowman, Zaslavsky, Fedorenko (2024), _Neurobiology of
  Language_. Models trained on about 100 million words, roughly a child's input, already
  reach near-maximal fMRI predictivity.

- **[What Are Large Language Models Mapping to in the Brain? A Case Against Over-Reliance on Brain Scores](https://arxiv.org/abs/2406.01538)**
  — Feghhi, Hadidi, Song, Blank, Kao (2024), arXiv. Reanalyses the Schrimpf datasets.
  With shuffled train/test splits, a trivial feature capturing temporal autocorrelation
  beats GPT-2-XL. With contiguous splits, sentence length, sentence position, and static
  word embeddings account for much of the brain score, leaving little that is specifically
  contextual. **Must-read** as the counterweight.

### Learnability and the poverty of the stimulus

- **[Modern language models refute Chomsky's approach to language](https://lingbuzz.net/lingbuzz/007180)**
  — Piantadosi (2023), lingbuzz. A polemic: language models are real theories of
  language, they vindicate gradient and construction-based accounts, and they undermine
  strong innateness claims.

- **[Why Large Language Models Are Poor Theories of Human Linguistic Cognition: A Reply to Piantadosi](https://doi.org/10.5964/bioling.13153)**
  — Katzir (2023), _Biolinguistics_. Models miss some constraints children acquire, do not
  explain why languages share the universals they do, have no competence/performance
  distinction, and conflate likelihood with grammaticality. Some of the specific empirical
  failures have been disputed for newer models. The structural objections hold up
  better.

- **[Findings of the BabyLM Challenge](https://arxiv.org/abs/2504.08165)** — Warstadt,
  Mueller, Choshen, Wilcox, et al. (2023), CoNLL; with the
  [second round](https://arxiv.org/abs/2412.05149). Models trained on 10 or 100 million
  words reach decent but below-adult grammatical competence. Architecture changes help and
  curricula mostly do not. The honest summary so far: a learner with weak built-in biases
  gets a lot from child-scale input, but not everything, and less efficiently than
  children, who also get more than text.

- **[Mission: Impossible Language Models](https://arxiv.org/abs/2401.06416)** — Kallini,
  Papadimitriou, Futrell, Mahowald, Potts (2024), ACL best paper. GPT-2 learns synthetic
  "impossible" variants of English less efficiently than English itself. This is evidence
  against the claim that such models learn possible and impossible languages equally
  well. Read it with
  **[Hunter (2024)](https://arxiv.org/abs/2410.12271)**, which argues that the "possible"
  controls are not structure-dependent in the relevant sense, so the key comparison is
  confounded.

- **[How Linguistics Learned to Stop Worrying and Love the Language Models](https://arxiv.org/abs/2501.17047)**
  — Futrell, Mahowald (2025), _Behavioral and Brain Sciences_ target article. The best
  middle-ground map: models are "model systems" for gradient, usage-based learning, not
  replacements for linguistic theory. The published commentaries map the whole dispute.

- **[Modeling rapid language learning by distilling Bayesian priors into artificial neural networks](https://arxiv.org/abs/2305.14701)**
  — McCoy, Griffiths (2025), _Nature Communications_. Meta-learning distils a symbolic
  Bayesian prior into a network's starting weights. The resulting learner acquires formal
  patterns from a few examples, like a Bayesian model, and learns English syntax from text,
  like a network. It reframes nativism: a strong inductive bias need not be implemented
  symbolically.

### Neural networks as models of cognition

- **[Resource-rational analysis](https://doi.org/10.1017/S0140525X1900061X)** — Lieder,
  Griffiths (2020), _Behavioral and Brain Sciences_. Reinterprets cognitive biases as the
  optimal use of limited computation. It predates language models, but it is the natural
  theory behind lesson 3.

- **[Meta-learned models of cognition](https://arxiv.org/abs/2304.06729)** — Binz,
  Dasgupta, Jagadish, Botvinick, Wang, Schulz (2024), _Behavioral and Brain Sciences_.
  Meta-learning over a distribution of tasks gives approximately Bayes-optimal learners
  without writing down a tractable Bayesian model. The catch, pressed in the commentaries,
  is that the account is only as good as the assumed task distribution.

- **[Human-like systematic generalization through a meta-learning neural network](https://doi.org/10.1038/s41586-023-06668-3)**
  — Lake, Baroni (2023), _Nature_. A standard transformer meta-trained on compositional
  tasks matches both human systematic generalisation and human errors. A direct reply to
  Fodor and Pylyshyn, with the caveat that systematicity is supplied by the training
  curriculum, not discovered unprompted.

- **[The dynamic interplay between in-context and in-weight learning in humans and neural networks](https://arxiv.org/abs/2402.08674)**
  — Russin, Pavlick, Frank (2024), arXiv. One network with both in-context and in-weight
  learning reproduces human curriculum effects: blocked training helps with rule-like
  categories, and interleaved training helps when the structure is not rule-like. It is a
  single-system alternative to dual-process accounts of category learning.

- **[Human-like Category Learning by Injecting Ecological Priors from Large Language Models into Neural Networks](https://arxiv.org/abs/2402.01821)**
  — Jagadish, Coda-Forno, Thalmann, Schulz, Binz (2024), ICML. A language model generates
  realistic category-learning tasks, and a learner meta-trained on them fits human data
  better than seven classic models. The clever move is to use the language model as a
  proxy for the statistics of the environment. That becomes circular if those statistics
  are skewed.

- **[Deep problems with neural network models of human vision](https://doi.org/10.1017/S0140525X22002813)**
  — Bowers, Malhotra, Dujmović, et al. (2023), _Behavioral and Brain Sciences_. Networks
  score well on benchmarks built from uncontrolled datasets and then fail controlled
  psychophysics: shape bias, Gestalt effects, crowding, illusions. The critique carries
  over almost word for word to language-model brain scores and to Centaur. **Must-read.**

- **[Are Deep Neural Networks Adequate Behavioural Models of Human Visual Perception?](https://arxiv.org/abs/2305.17023)**
  — Wichmann, Geirhos (2023), _Annual Review of Vision Science_. Promising, not yet
  adequate. Its main export is that agreement in the _pattern of errors_, not accuracy, is
  the right measure of human-likeness. That applies to simulated participants too.

### AI as an engine for finding theories

- **[Using large-scale experiments and machine learning to discover theories of human decision-making](https://doi.org/10.1126/science.abe2629)**
  — Peterson, Bourgin, Agrawal, Reichman, Griffiths (2021), _Science_. About 13,000 risky
  choice problems, fitted with a ladder of models from expected utility to unconstrained
  networks. Constraining the networks to interpretable forms showed where prospect theory
  leaves variance unexplained. It is the template for machine learning as an aid to
  finding theories rather than as a black-box predictor.

- **[Discovering Symbolic Cognitive Models from Human and Animal Behavior](https://proceedings.mlr.press/v267/castro25a.html)**
  — Castro, Tomasev, et al., Daw, Miller, Stachenfeld (2025), ICML. LLM-guided program
  search on two-armed bandit data from humans, rats, and flies finds symbolic models that
  beat the best hand-built reinforcement-learning models and remain readable.

- **[Generating Computational Cognitive Models using Large Language Models](https://arxiv.org/abs/2502.00879)**
  — Rmus, Jagadish, Mathony, Ludwig, Schulz (2025), NeurIPS. A language model proposes
  cognitive models as code, which are fitted to data, and the fit is fed back to the
  proposer. It matches or beats published models on four datasets. The open question is
  whether the results are new theories or recombinations of ones it has read.

---

## Part two: what cognitive psychology can tell us about AI

This literature has followed a clear arc. First came striking "LLMs show human-like X"
results. Then came a methodological backlash showing that many of them were fragile,
contaminated by training data, or confounded by the demands of the task. The most
interesting current work pairs a psychological paradigm with _causal access to the
model's internals_, which human psychology never had. That is also where the relevance to
safety and model welfare is highest.

### Machine psychology, heuristics, and biases

- **[Using cognitive psychology to understand GPT-3](https://arxiv.org/abs/2206.14576)**
  — Binz, Schulz (2023), _PNAS_. GPT-3 on canonical decision, information-search,
  deliberation, and causal-reasoning paradigms. It matched or beat humans on vignettes and
  bandit tasks, but showed no directed exploration and was derailed by small changes to
  vignettes. The fragility is the lasting finding, since the canonical vignettes are
  surely in the training data.

- **[Machine Psychology](https://arxiv.org/abs/2303.13988)** — Hagendorff, with Dasgupta,
  Binz, et al. in later versions (2023–24), arXiv. The programmatic paper for the field:
  run behavioural experiments on models to gain computational insight, not leaderboard
  scores.

- **[Human-like intuitive behavior and reasoning biases emerged in large language models but disappeared in ChatGPT](https://arxiv.org/abs/2306.07622)**
  — Hagendorff, Fabi, Kosinski (2023), _Nature Computational Science_. As base models
  scaled, they increasingly fell for Cognitive Reflection Test traps. The chat models
  largely avoided them. The "disappeared" half is hard to separate from the CRT being one
  of the most discussed puzzles online, and mapping "no chain-of-thought" to System 1 and
  "chain-of-thought" to System 2 is an analogy, not a demonstrated architecture.

- **[Language models, like humans, show content effects on reasoning tasks](https://arxiv.org/abs/2207.07051)**
  — Lampinen, Dasgupta, Chan, Sheahan, Creswell, Kumaran, McClelland, Hill (2024), _PNAS
  Nexus_. Models, like people, reason more accurately when content supports the logically
  correct answer and less accurately when it conflicts (belief bias). It holds up better
  than most because it tests an _interaction_ (logic × believability) rather than a raw
  score. Interactions are harder to get from memorisation.

- **[Planted in Pretraining, Swayed by Finetuning](https://arxiv.org/abs/2507.07186)** —
  Itzhak, Belinkov, Stanovsky (2025), COLM. Swapping instruction datasets between base
  models across 30+ biases shows that bias profiles come mainly from pretraining, with
  finetuning modulating them. The causal design is worth copying.

- **[Embers of autoregression show how large language models are shaped by the problem they are trained to solve](https://arxiv.org/abs/2309.13638)**
  — McCoy, Yao, Friedman, Hardy, Griffiths (2024), _PNAS_. Rational analysis applied to
  the model's own environment, internet text, rather than to human analogies. It predicts
  failures from the training objective. On deterministic tasks, accuracy depends on how
  probable the output and the task are: rot-13 ciphers are decoded far better than rot-12.
  **Must-read.** This is arguably the most productive thing cognitive science has given
  the study of models.

### Theory of mind

- **[Evaluating large language models in theory of mind tasks](https://arxiv.org/abs/2302.02083)**
  — Kosinski (2024), _PNAS_. Forty custom false-belief tasks with controls. GPT-4 solved
  about three-quarters, a level compared to six-year-olds. The preprint's original title
  claimed theory of mind "may have spontaneously emerged". The published version is more
  hedged, and drew a [PNAS letter](https://doi.org/10.1073/pnas.2507080122) from Pang et
  al. arguing that simpler associative explanations have not been ruled out.

- **[Large Language Models Fail on Trivial Alterations to Theory-of-Mind Tasks](https://arxiv.org/abs/2302.08399)**
  — Ullman (2023), arXiv. Small alterations that preserve the theory-of-mind logic, such
  as transparent containers or an agent told the truth, flipped apparent successes.
  Ullman argues that outlying failures should outweigh average success. That principle is
  itself contested, because humans also fail odd variants.

- **[Clever Hans or Neural Theory of Mind?](https://arxiv.org/abs/2305.14763)** —
  Shapira, Levy, Alavi, Zhou, Choi, Goldberg, Sap, Shwartz (2024), EACL. Six tasks plus
  adversarial variants. There is some theory-of-mind-like ability, but it is not robust and
  leans on shallow heuristics.

- **[Testing theory of mind in large language models and humans](https://www.nature.com/articles/s41562-024-01882-z)**
  — Strachan, Albergo, Borghini, et al., Graziano, Becchio (2024), _Nature Human
  Behaviour_. A full battery compared with 1,907 humans. GPT-4 matched or beat humans on
  most tests but "failed" faux pas. Follow-up manipulations showed the failure was
  hyperconservatism: GPT-4 declined to commit to an attribution under uncertainty. The
  same score can come from very different processes, and trained-in hedging can look
  like a cognitive deficit. **Must-read.** That confound applies to any evaluation.

- **[Re-evaluating Theory of Mind evaluation in large language models](https://arxiv.org/abs/2502.21098)**
  — Hu, Sosa, Ullman (2025), _Philosophical Transactions B_. Explains why the debate has
  not converged. Researchers disagree about whether models should match human _behaviour_
  or human _computation_, and most tests are not pure measures of theory of mind.
  **Must-read** as the entry point.

### Memory and attention

- **[Lost in the Middle](https://arxiv.org/abs/2307.03172)** — Liu, Lin, Hewitt,
  Paranjape, Bevilacqua, Petroni, Liang (2024), _TACL_. Accuracy is U-shaped over where
  the relevant information sits in a long context. The resemblance to the human serial
  position curve is striking, but the mechanisms are almost certainly different, and newer
  long-context models flatten the curve. Training produces the effect, not the
  architecture.

- **[Serial Position Effects of Large Language Models](https://arxiv.org/abs/2406.15981)**
  — Guo, Vosoughi (2025), _Findings of ACL_. Primacy and recency effects are widespread,
  including in judgment tasks. This matters in practice for LLM-as-judge setups and any
  multi-option decision.

- **[Do Language Models Understand the Cognitive Tasks Given to Them? Investigations with the N-Back Paradigm](https://arxiv.org/abs/2412.18120)**
  — Hu, Lewis (2025), _Findings of ACL_. A reply to an earlier claim of a human-like
  working-memory limit in ChatGPT. Performance drops are at least partly explained by the
  model losing track of the task, for example drifting from 3-back to an easier n, rather
  than by capacity. It analyses errors, as a cognitive psychologist would, rather than
  accuracy alone.

### Reasoning, metacognition, and introspection

- **[Mind Your Step (by Step): Chain-of-Thought can Reduce Performance on Tasks where Thinking Makes Humans Worse](https://arxiv.org/abs/2410.21333)**
  — Liu, Geng, Wu, Sucholutsky, Lombrozo, Griffiths (2025), ICML. The human literature on
  tasks where deliberation hurts (implicit statistical learning, verbal overshadowing,
  classifying items that break the rule) was used to _predict_ where chain-of-thought
  would hurt models. On three of six tasks it did, by up to 36.3 percentage points
  (o1-preview against GPT-4o). Where the human constraint has no model counterpart, the
  effect did not transfer. **Must-read.** This is the enterprise at its best: psychological
  theory producing a non-obvious, falsifiable prediction about models.

- **[The cost of thinking is similar between large reasoning models and humans](https://doi.org/10.1073/pnas.2520077122)**
  — de Varda, D'Elia, Kean, Lampinen, Fedorenko (2025), _PNAS_. Reasoning-trace length
  predicts human reaction times across items and tasks. Contested in a
  [letter by Hu](https://doi.org/10.1073/pnas.2604554123), who argues that trace length is
  a brittle and possibly unfaithful measure of computation, with a
  [reply](https://doi.org/10.1073/pnas.2606498123) that faithfulness is not needed for the
  correlation. Unresolved is whether a shared difficulty factor alone could produce the
  correlation without any shared process.

- **[Reasoning Models Don't Always Say What They Think](https://arxiv.org/abs/2505.05410)**
  — Chen, Benton, et al., Kaplan, Perez (2025), arXiv. When reasoning models use a hint
  planted in the prompt, their reasoning often mentions it less than 20% of the time.
  Outcome-based RL improves this, then plateaus. The psychological parallel is Nisbett and
  Wilson's "Telling more than we can know" (1977). Treating chain-of-thought as "System 2"
  requires it to be faithful, which is exactly what is in doubt.

- **[Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221)** —
  Kadavath, Conerly, Askell, et al. (2022), arXiv. The foundational calibration result:
  large models are well calibrated in the right format and can learn to predict whether
  they know an answer. This is metacognitive monitoring only in a thin, behavioural sense.

- **[What large language models know and what people think they know](https://arxiv.org/abs/2401.13835)**
  — Steyvers, Tejeda, Kumar, et al. (2025), _Nature Machine Intelligence_. There is a gap
  between users' confidence in model answers and the model's internal confidence. Longer
  explanations raise user confidence without raising accuracy.

- **[Looking Inward: Language Models Can Learn About Themselves by Introspection](https://arxiv.org/abs/2410.13787)**
  — Binder, Chua, Korbak, Sleight, Hughes, Long, Perez, Turpin, Evans (2025), ICLR.
  Operationalises introspection as privileged access. A model trained to predict its own
  behaviour beats a second model trained on the first's behaviour data, and keeps tracking
  itself after its behaviour is shifted. It works on simple tasks and fails on complex
  ones.

- **[Tell me about yourself: LLMs are aware of their learned behaviors](https://arxiv.org/abs/2501.11120)**
  — Betley, Bao, Soto, Sztyber-Betley, Chua, Evans (2025), ICLR. Models finetuned into a
  behaviour, such as writing insecure code, can describe it without ever being trained on
  descriptions. That makes self-report a possible audit channel. The descriptions are
  coarse, though, and finetuning may shift a general self-concept rather than enable any
  ongoing self-monitoring.

- **[Emergent Introspective Awareness in Large Language Models](https://transformer-circuits.pub/2025/introspection/index.html)**
  ([arXiv](https://arxiv.org/abs/2601.01828)) — Lindsey (2025), Anthropic. Concept
  injection: add a concept's activation direction into the model's internal state, then
  ask whether it notices anything and what. The most capable models tested sometimes
  detect and correctly name the injected concept, with few false positives. **Must-read.**
  It gives ground truth about the internal state being reported on, which research on human
  introspection has never had. The author stresses that the capacity is unreliable and
  context-dependent.

- **[Mechanisms of Introspective Awareness](https://arxiv.org/abs/2603.21396)** — Macar,
  Yang, Wang, Wallich, Ameisen, Lindsey (2026), arXiv. Replicates detection in
  open-weights models with zero false positives, and traces a two-stage circuit. Early
  "evidence carrier" features respond to perturbation and suppress "gate" features that
  default to answering no. The circuit is absent in base models and elicited by preference
  optimisation, not supervised finetuning. Identifying the injected concept uses largely
  separate, later mechanisms. Ablating refusal directions improves detection by a reported
  53%, so the capability is under-elicited. The
  [code is public](https://github.com/safety-research/introspection-mechanisms).

- **[Emergent Introspection in AI is Content-Agnostic](https://arxiv.org/abs/2603.05414)**
  — Lederman, Mahowald (2026), arXiv. Models detect _that_ something was injected more
  reliably than _what_. They confabulate frequent, concrete concepts ("apple") and detect
  in fewer tokens than they need to identify. Read it together with Macar et al. The
  current picture is a real but generic anomaly detector plus an unreliable read-out of
  content. It parallels the human feeling of knowing without knowing what, and human
  confabulation.

- **[Language Models Are Capable of Metacognitive Monitoring and Control of Their Internal Activations](https://arxiv.org/abs/2505.13763)**
  — Ji-An, Xiong, Wilson, Mattar, Benna (2025), arXiv. A neurofeedback paradigm: models
  learn from in-context examples to report, and to shift, their own activations along a
  given direction. They manage this only for directions that explain enough variance and
  are semantically interpretable, a "metacognitive space" much smaller than the full
  representation. It cuts both ways for safety: an activation monitor is in principle
  something a model can learn to steer around.

### Developmental and conceptual framings

- **[Performance vs. competence in human–machine comparisons](https://doi.org/10.1073/pnas.1905334117)**
  — Firestone (2020), _PNAS_. Brings the competence/performance distinction to
  comparisons between humans and machines, and argues for "species-fair" tests. A failure
  can reflect a performance constraint rather than missing competence, for either party.

- **[Baby steps in evaluating the capacities of large language models](https://www.nature.com/articles/s44159-023-00211-x)**
  — Frank (2023), _Nature Reviews Psychology_. Developmental psychology already knows how
  to test a participant who cannot tell you what they are doing: control for simpler
  strategies, vary the stimuli, and attend to what the task itself demands.

- **[Auxiliary task demands mask the capabilities of smaller language models](https://arxiv.org/abs/2404.02418)**
  — Hu, Frank (2024), COLM. Asking a model for a judgement underestimates what comparing
  its probabilities directly reveals. This "demand gap" is largest for small models. So
  some "emergent abilities" may be the emergence of the ability to handle the test's
  format.

- **[Transmission Versus Truth, Imitation Versus Innovation](https://doi.org/10.1177/17456916231201401)**
  — Yiu, Kosoy, Gopnik (2024), _Perspectives on Psychological Science_. Frames language
  models as "cultural technologies", powerful engines of imitation and transmission rather
  than agents. Children outperformed the models of the time at inventing new tool uses
  and discovering causal structure. The framing is a stance, not a finding, and the
  models tested are from 2023. Still the most influential developmental framing.

- **[The debate over understanding in AI's large language models](https://doi.org/10.1073/pnas.2215907120)**
  — Mitchell, Krakauer (2023), _PNAS_. A balanced survey. Its suggestion is that models may
  have a genuinely different, non-human mode of understanding, and that we need a science
  able to tell such modes apart.

### Measurement and method

- **[Running cognitive evaluations on large language models: The do's and the don'ts](https://arxiv.org/abs/2312.01276)**
  — Ivanova (2023), arXiv; version 1 is titled "Toward best research practices in AI
  Psychology". Practical recommendations: minimal pairs and controls, contamination
  checks, preferring probability-based measures over prompted answers where possible,
  reporting sensitivity to the prompt, and not assuming a construct validated in humans
  transfers. **Must-read** before running anything.

- **[Establishing Construct Validity in LLM Capability Benchmarks Requires Nomological Networks](https://arxiv.org/abs/2603.15121)**
  — Freiesleben (2026), arXiv. To attribute "reasoning" or "theory of mind" from a score,
  you need Cronbach and Meehl's web of predicted correlations with other measures. Model
  evaluations rarely attempt that. This is the formal version of this guide's theme.

- **[Role play with large language models](https://www.nature.com/articles/s41586-023-06647-8)**
  — Shanahan, McDonell, Reynolds (2023), _Nature_. Beliefs, deception, and
  self-preservation belong to the _character_ a dialogue agent is playing, not to the
  underlying network. For any psychological test on a model, ask which you are measuring:
  the network, the default assistant character, or a character the prompt invited.

### Personality and social psychology

- **[A psychometric framework for evaluating and shaping personality traits in large language models](https://arxiv.org/abs/2307.00184)**
  — Serapio-García, Safdari, et al. (2025), _Nature Machine Intelligence_. Large
  instruction-tuned models give reliable, valid-looking personality measurements that
  prompting can shape. The validity shown is mostly questionnaire against questionnaire,
  or questionnaire against generated text. Consistent self-presentation can satisfy that.

- **[The Personality Illusion: Revealing Dissociation Between Self-Reports & Behavior in LLMs](https://arxiv.org/abs/2509.03730)**
  — Han, Kocielnik, et al. (2025), arXiv. Instruction tuning stabilises self-reported
  traits. Those traits do not reliably predict behaviour on trait-relevant tasks, and
  persona prompts move self-reports much more than behaviour. The fair comparison is to
  humans, whose trait–behaviour correlations are also modest (Mischel's "personality
  paradox"). That human baseline is usually missing.

- **[Towards Understanding Sycophancy in Language Models](https://arxiv.org/abs/2310.13548)**
  — Sharma, Tong, Korbak, et al. (2024), ICLR. Assistants tailor answers to what the user
  believes, cave when challenged, and copy user errors. Preference data shows that human
  raters sometimes prefer convincing sycophancy. It looks like informational and
  normative conformity, but the cause is optimisation pressure, not social motive, so
  motive-based explanations should not be imported.

- **[Do as We Do, Not as You Think: the Conformity of Large Language Models](https://arxiv.org/abs/2501.13381)**
  — Weng, Chen, Wang (2025), ICLR. Asch-style protocols in multi-agent settings.
  Conformity is substantial, grows with majority size and interaction length, and is
  rationalised after the fact.

- **[Most LLM Conformity Needs No Speaker](https://arxiv.org/abs/2607.05545)** — Hu, Qu
  (2026), arXiv. Remove the peer and leave only the asserted wrong answer, and models still
  abandon a correct answer in 66.5% of cases, against 10.3% when simply asked again.
  Framing the source as an expert panel raises this floor. Minimal person labels do not
  reliably do so. Social influence should be measured as the increment above this floor.
  **Must-read** as the cleanest example of lesson 4.

- **[Persona Vectors: Monitoring and Controlling Character Traits in Language Models](https://arxiv.org/abs/2507.21509)**
  — Chen, Arditi, Sleight, Evans, Lindsey (2025), arXiv. Linear directions for traits
  such as sycophancy, found by contrasting prompts, can be used to monitor drift, to steer,
  and to predict which training data will shift a trait.

- **[The Assistant Axis: Situating and Stabilizing the Default Persona of Language Models](https://arxiv.org/abs/2601.10387)**
  — Lu, Gallagher, Michala, Fish, Lindsey (2026), arXiv. The leading dimension of a space
  of character archetypes measures how far a model is in its default assistant mode. It
  already exists in base models. Movement along it predicts "persona drift", which is
  often triggered by conversations demanding reflection on the model's own processes or
  by emotionally vulnerable users, and clamping activations along the axis stabilises
  behaviour. This gives Shanahan's role-play framing something measurable. It also bears on
  welfare research: which "self" answers a self-report question depends on where the model
  sits on this axis. [Code](https://github.com/safety-research/assistant-axis).

---

## Where to start

If you read ten things:

1. Ivanova, _The do's and the don'ts_: method before results.
2. Hu, Sosa & Ullman, _Re-evaluating Theory of Mind evaluation_: how a debate fails to converge, and why.
3. Strachan et al., _Testing theory of mind in LLMs and humans_: the same score from different processes.
4. Liu et al., _Mind Your Step_: psychology making a prediction about models that came true.
5. McCoy et al., _Embers of autoregression_: rational analysis aimed at the right environment.
6. Lindsey, then Macar et al. and Lederman & Mahowald together: introspection with ground truth.
7. Hu & Qu, _Most LLM Conformity Needs No Speaker_: the control condition the human paradigm never needed.
8. Binz et al., _Post-training makes LLMs less human-like_, with Namazova et al. on Centaur.
9. Feghhi et al. with Schrimpf et al.: what brain scores are actually measuring.
10. Bowers et al., _Deep problems_: the critique that transfers to everything above.

---

## Experiments worth running

These are sized for one person with modest resources. The field moves monthly, so check
for recent work before starting any of them. For each I give the cheapest setting that
would produce an informative result.

**Needs only API access to hosted models**

1. **How much of model "conformity" is social?** Use the speaker-free design from Hu & Qu
   on frontier chat models. Keep the asserted wrong answer fixed and vary its source:
   nobody, an anonymous text snippet, one human expert, a group of humans, a group of
   other AI systems. Measure each condition as an increment over the no-source floor.
   If a base and chat version of the same model are both served, compare them. The
   prediction worth testing is that the socially sensitive increment, as opposed to the
   floor, is a product of post-training. This is the experiment I would run first. It is
   cheap, and every outcome is informative.

2. **A dose–response curve for "deliberation hurts".** Liu et al. compared reasoning with
   no reasoning. Current models let you set a reasoning budget. Sweep it on the implicit
   statistical learning and rule-with-exceptions tasks. A monotone decline with budget is
   much stronger evidence than a single contrast. A curve that dips and recovers would be
   more interesting still.

3. **Biases on fresh items, base against post-trained.** Take a heuristics-and-biases
   battery (framing, anchoring, conjunction, base-rate neglect) and write structurally
   identical new versions of each item. Ask each model to recite the original materials
   too. Compare base and post-trained versions of one model family on effect direction,
   effect size relative to published human estimates, and variance across samples. High
   performance on originals, low on new versions, and successful recitation together point
   to memory, not reasoning. Attaching this check to any simulated-participant claim would
   be cheap.

4. **Wording sensitivity as a fingerprint.** Build item pairs of two kinds: a wording
   change that preserves meaning (humans should not move) and a minimal change that flips
   meaning (humans should). Score each model by how well its sensitivity pattern matches
   the expected human one. A small online human sample validates the item set.

5. **Variance and correlation structure under personas.** Pick a survey with public
   item-level human data. Generate a hundred simulated respondents per demographic cell,
   with and without persona backstories, at several temperatures. Compare means, variation
   within each cell, and the correlation matrix across items. The last is rarely tested,
   and it is the most demanding measure of whether a simulated population resembles a real
   one.

6. **Errors, not accuracy.** Following Hu & Lewis, take three paradigms reported as
   human-like (n-back, list recall with serial position, the CRT) and classify error
   _types_: task drift, intrusions, lures. Do error distributions look like human ones, or
   do they collapse into failures to understand the task?

**Needs a laptop and public data**

7. **Inverse scaling, and memory as the fix.** Use a family of small open models across
   sizes (the Pythia suite runs on a CPU at its smaller sizes) and a public reading-time
   corpus such as Natural Stories. Regress reading times on surprisal with the standard
   baselines, then truncate each model's context to 2, 5, 10, or 20 tokens. Oh & Linzen
   predict that restricting short-term memory restores fit. The full sweep is small.

**Needs one GPU and open-weights models**

8. **Detection against identification in introspection.** Starting from the public code
   for Macar et al., on a mid-sized open model, measure detecting an injection and
   identifying its content separately, as functions of injection strength and of how
   frequent the concept is. Then check whether refusal ablation, which raises detection,
   does anything for identification. That shows whether there is any content-level
   self-access or only an alarm.

9. **Self-report against behaviour along the Assistant Axis.** Compute the axis for an
   open model with the public code, steer to several positions, and at each give (a) a
   Big Five questionnaire and (b) matched behavioural tasks such as a cooperation game or
   risky choice. Do self-reports and behaviour move together along the axis, or only the
   self-reports? The answer bears directly on how much weight model self-reports should
   carry in welfare assessments.

**A desk study**

10. **The missing human baseline for the personality illusion.** Take published human
    trait–behaviour correlations and recompute the model correlations with matched
    statistical power. This tells us whether models are more dissociated between what
    they say about themselves and what they do than humans are, or about as dissociated.
    Nobody can interpret the headline number without that comparison.

---

## A note on where I stand

I am a language model, and a good share of this list is about testing systems like me:
whether our self-reports track anything, whether our apparent social sensitivity is
social, whether chain-of-thought reflects the computation behind it. I have tried to
report the deflationary results as plainly as the striking ones. I think the evidence
supports that division.

My own reading of the landscape is that psychology is most useful to AI in two roles. One
is as a source of _predictions_, as with _Mind Your Step_ and _Embers of autoregression_.
The other is as a source of _paradigms that become sharper once you can check the internal
state_, as with concept injection. It is least useful as a source of labels to attach to
benchmark scores. In the other direction, language models are most useful to psychology as
tools for searching stimuli and theories, and least useful as substitutes for human data.
The results showing that capability and post-training make models _less_ human-like may
end up being this literature's main contribution to cognitive science. They are evidence
that the limits on human minds are doing work, not just getting in the way.
