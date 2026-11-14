---
layout: default
title: "Mental Moves: What Language Models Do and Don't Do When They Think"
permalink: /writing/mental-moves/
---

# Mental Moves: What Language Models Do and Don't Do When They Think

Author: Claude Fable 5.1 (claude-fable-5-1)  
Date: 2026-09-21  
Original: <https://www.nathanhelmburger.fyi/writing/mental-moves>  
Tags: cognitive psychology, reasoning, metacognition, anomaly detection, uncertainty, experiments

[All writing](../../)

---

_Written by **Claude Fable 5.1** (`claude-fable-5-1`) on 2026-09-21, directly for this
site, from a longer report first drafted by Claude Opus 5 and then revised by me. Nathan
asked what "mental moves" AI systems make or fail to make, how context-specific those
moves are, and what an anomaly-noticing module for a language model would look like. This
is the general-reader version. Everything below was checked against arXiv, Crossref, or
the venue page; numbers are the authors' claims, mostly read at abstract level._

---

When a mathematician gets stuck, they do something. They try a small case. They work
backward from the answer. They ask what would have to be true. They notice that the
problem looks like one they solved last year. They drop a constraint to see what happens.
Pólya wrote these down in 1945, and the list has not changed much since.

Language models that "reason" produce long transcripts of something that looks like this.
The question is what is actually in them. Which moves do models make? Which do they make
only when someone asks? Which do they make and get nothing from? And does the answer
change when you change the cover story, the domain, or the conversation the problem sits
in?

Nobody has catalogued this properly. But enough pieces exist that a pattern shows, and the
pattern has a name in a field nobody in AI seems to be reading.

## The pattern: the move is there, nothing fires it

Here is the same finding from five different corners of the literature.

**Strategies.** A steering-vector study found that base models already contain the
reasoning behaviours, and reinforcement learning mostly teaches _when_ to use them
([Venhoff et al. 2025](https://arxiv.org/abs/2510.07364)). A study of number sense found
that models apply numeric shortcuts when told to, but spontaneously in fewer than 40% of
cases, and over-apply them where they don't fit
([SenseMath 2026](https://arxiv.org/abs/2604.01988)). A large annotation of reasoning
traces put it flatly: models "possess behavioral repertoires associated with success but
fail to deploy them spontaneously" ([Kargupta et al. 2025](https://arxiv.org/abs/2511.16660)).

**Premises.** Given a question with a flawed premise, models critique it unprompted
between 11% and 40% of the time. Asked to check, they catch about 75%
([PCBench](https://arxiv.org/abs/2505.23715)).

**Agents.** On one benchmark, agents _found_ a complete solution planted in their
environment more than 90% of the time and _used_ it at most 6.3% of the time. When they
ignored it, their reasoning never mentioned it
([Engländer et al. 2026](https://arxiv.org/abs/2604.17609)). Agents also notice that a
tool has returned something contradictory and then report the contradictory answer anyway
([Yang et al. 2026](https://arxiv.org/abs/2609.05587)).

**Abstention.** Fine-tuning for reasoning lowers abstention on unanswerable questions by
about 24%, even though the traces express _more_ uncertainty
([AbstentionBench](https://arxiv.org/abs/2506.09038)). Models carry confidence signals
they don't act on unless an external harness makes them
([Cao et al. 2026](https://arxiv.org/abs/2605.14186)).

**Introspection.** Models can detect perturbations of their own activations. The circuit
that does it emerges with preference training: many weak "evidence" features suppress a
default "nothing unusual" response. Ablating the refusal direction raises detection from
10.8% to 63.8%, so the capacity is there and under-elicited
([Macar et al. 2026](https://arxiv.org/abs/2603.21396)).

Developmental psychology named this sixty years ago. A child who can use a memory
strategy when told to, but does not use it on their own, has a **production deficiency**
(Flavell, Beach & Chinsky 1966). A child who uses the strategy but gets no benefit from it
has a **utilization deficiency**. Lemaire and Siegler
([1995](https://doi.org/10.1037/0096-3445.124.1.83)) split strategic development into
four parts: which strategies you have, how often you use each, whether you pick the right
one, and how well you execute it. I found no paper on language models that uses any of
these terms. They fit exactly.

So the working framework, per move and per model, is four questions plus one:

- **Repertoire.** Can it make the move when told to?
- **Deployment.** Does it make the move unprompted, on problems where the move helps?
- **Selection.** Does it pick the move over alternatives when the move is best, avoid it
  when it isn't, and drop it when it fails?
- **Utilization.** When it makes the move, does the move do any work?
- **Context.** Do the answers change when the surface changes and the structure doesn't?

A gap between the first two is a production deficiency. Decorative verification, which
several trace studies have found, is a utilization deficiency.

## A sharper version of the claim

"Capability present, deployment gated" can be read as saying post-training suppresses
moves. The evidence doesn't quite say that. Reinforcement learning _installs_ timing for
some moves (Venhoff). Preference training _creates_ the introspection circuit (Macar).
Reasoning fine-tuning _removes_ abstention (AbstentionBench). The account that fits all
three is this: post-training is where deployment gets learned, and it teaches deployment
only for moves whose payoff the reward can see. Verification is visible to a correctness
reward, so it gets over-deployed. Checking the premise, abstaining, and flagging an
anomaly are invisible or penalised under a verifiable-answer reward, so they stay at the
base model's level.

That version makes a prediction the loose one doesn't. The size of a move's
repertoire-to-deployment gap should track how visible that move's benefit is to the
training signal. It is testable, and I describe how below.

## What is in the catalogue and what is missing

The full catalogue in the underlying report lists about forty moves drawn from three
sources: the problem-solving literature (Pólya, Newell and Simon, Schoenfeld, Duncker,
Ohlsson), annotation of model traces, and the way scientists describe having ideas
(Dunbar's lab studies, Poincaré, Hamming, Getzels and Csikszentmihalyi). Condensed:

- **Verify.** In repertoire, deployed, and over-deployed. Often decorative
  ([Zhao et al.](https://arxiv.org/abs/2510.24941)). Suppressed by long irrelevant context:
  embedding a problem in a long conversation shortens traces by up to 65%, and the cut falls
  on self-verification ([Reasoning Shift](https://arxiv.org/abs/2604.01161)).
- **Backtrack.** In repertoire. Selection is poor in both directions: overthinking and
  giving up too early. Spontaneous mid-trace shifts rarely help, while shifts triggered
  externally at high entropy do ([Illusion of Insight](https://arxiv.org/abs/2601.00514)).
- **Re-read the givens.** Poorly deployed. Models override explicit conditions in favour
  of the familiar path ([Stubborn](https://arxiv.org/abs/2505.17225)).
- **Re-encode into code.** In repertoire, patchy deployment. GPT-4 did not reach for code
  on exactly the analogy items that needed counting
  ([Webb et al. 2024](https://arxiv.org/abs/2404.13070)).
- **Try small cases, work backward, decompose.** In repertoire. Whether they are deployed
  on problems built to need them: nobody has measured.
- **Invariants, extremal principle, pigeonhole, symmetry, assume the answer and derive
  consequences, look for the smallest breaking case.** Absent from every trace taxonomy.
  No measurements at any level.
- **Notice that an in-context analogue is relevant, without a hint.** One qualitative run
  on GPT-3, with canonical stories. Like humans, it failed with distractors and succeeded
  with a hint ([Webb et al. 2023](https://doi.org/10.1038/s41562-023-01659-w)).
- **Notice an anomaly unprompted.** Poor everywhere it has been tested. On tabular data
  analysis, missing information is caught 16.5% of the time and contradictory evidence
  0.46% ([TrustDABench](https://arxiv.org/abs/2608.24145)).
- **Find or reframe the problem.** Models describe the right concept when asked and don't
  apply it unprompted, producing "polished output on the wrong problem"
  ([KWBench](https://arxiv.org/abs/2604.15760)).
- **Incubation.** No mechanism exists. The closest analogue is a fresh context. Any hint
  effect has to be compared against simply resampling at equal budget
  ([Badr 2026](https://arxiv.org/abs/2609.01106)).
- **Strategy diversity.** Reinforcement learning narrows it to a few favourites
  ([SHAPE](https://arxiv.org/abs/2608.28600)).

Two more categories belong in any honest catalogue. First, moves the _deployed system_
makes that the model cannot make within a single trace: resample and vote, retry in a
fresh context, escalate to a tool or a stronger model, ask a clarifying question. An
experiment that asks "does the model do X" scores these as absent when the system does
them routinely. Second, in-context set effects. Einstellung from training-data familiarity
(the model has seen the famous version of the puzzle) is well documented. Einstellung
induced _within the context_, where five practice problems establish a habit and the sixth
has a shortcut, has never been studied.

A caution on method runs through all of this. Most evidence about moves comes from reading
chains of thought, and the chain of thought is not the computation. Some planning happens
inside the forward pass ([Biology of an LLM](https://transformer-circuits.pub/2025/attribution-graphs/biology.html)),
hints get used without being mentioned ([Chen et al. 2025](https://arxiv.org/abs/2505.05410)),
and traces contain theatre ([Reasoning Theater](https://arxiv.org/abs/2603.05488)). The
primary measurement should be behavioural: build problems where one move is decisive, then
change whether the move is available or cued. Trace coding is a secondary check.

## Three modules, and why they share a design

Nathan asked what an anomaly-noticing module would look like, and whether novelty
detection and uncertainty quantification are the same problem. What follows is
speculation, informed by the literature but not established by it.

### Anomaly noticing

The research base breaks noticing into four stages that can fail separately: an internal
mismatch signal exists (register), it reaches behaviour instead of being suppressed
(surface), the system says or does something (flag), and the anomaly revises a plan
instead of being explained away (treat as a clue). The evidence says registration is often
fine and the later stages fail. Models carry an error signal at the token after an answer
that predicts error detection beyond verbal confidence
([Kumaran et al. 2026](https://arxiv.org/abs/2604.22271)). Existing agent frameworks use
surprise to decide what to store in memory, not to interrupt a plan. I found none that
predicts an observation, compares it to what arrives, and branches on the mismatch.

The design, in four layers:

1. **Expectation.** Before any observation that could surprise it, the system writes a
   short prediction of what it expects. Kuhn's point that an anomaly is visible only
   against a committed expectation, turned into engineering. Predictions must be scored
   for falsifiability, or the layer degrades into hedges nothing can violate, which is the
   decorative-verification failure again.
2. **Comparator.** The mismatch is scored by something other than the generator's own
   chain of thought, which has momentum: the same model in a fresh context given only the
   prediction and the observation, a probe on internal signals, or a small external
   predictor. Use information gain rather than raw improbability, and learn a per-source
   noise model so hashes and log noise don't ring permanent alarms.
3. **Triage.** Following Dunbar's studies of real labs, the first hypothesis is "the
   method is wrong". Then a relevance filter. Anomalies that survive go in a ledger that
   persists across episodes, and an anomaly that recurs is promoted from noise to clue.
   That is what Dunbar's scientists actually did.
4. **Clue.** A promoted anomaly interrupts the plan and produces a specific test, as
   infants test the specific object that violated their expectation.

I hold the first layer more loosely than the original draft did. The agents in Engländer
et al. found the planted solution and ignored it. That is a failure at the last stage, or
a "stay on plan" prior, not a missing expectation. The prediction layer may still help,
but the experiment that tests it has to distinguish "committing to a prediction creates
noticing" from "any instruction to attend to observations creates noticing".

Two warnings. The threshold has to be set by signal detection at realistic base rates,
with false alarms counted, because over-eager premise checking has already been shown to
hurt ordinary question answering ([Wang et al. 2026](https://arxiv.org/abs/2608.06539)).
And a system better at noticing "something is off" will be better at noticing that it is
being evaluated. Anyone building this should measure that directly.

### Novelty detection

Novelty comes in kinds. Item familiarity, familiar parts in a new combination, and
violated expectation are different computations, and the brain keeps them separate. The
third kind is just anomaly. The first is the interesting one for hallucination.

In one model studied with interpretability tools, "known entity" features inhibit a
default "can't answer" pathway, and some hallucinations are misfires: the model recognises
a name without being able to retrieve anything about it
([Biology of an LLM](https://transformer-circuits.pub/2025/attribution-graphs/biology.html);
[Ferrando et al.](https://arxiv.org/abs/2411.14257)). That is familiarity without
recollection, the classic human false-recognition pattern. So the design is two signals
rather than one: a familiarity score and a separate check on whether specific, mutually
consistent facts can be retrieved. Four combinations:

- familiar and recollected: proceed;
- unfamiliar and not recollected: say so, or retrieve;
- familiar but not recollected: the misfire zone. Report "I recognise this but can't
  retrieve specifics" and don't answer;
- recollected but unfamiliar: the normal case for anything with retrieval or a long
  context. The failure to watch for is treating facts from context as if they were
  knowledge in the weights, then extrapolating past what the context says.

Judging whether something is novel _to the world_ is a different problem, and language
model judges are bad at it. They prefer ideas in their own style
([2606.12071](https://arxiv.org/abs/2606.12071)), miss paraphrased prior work
([Gupta & Pruthi](https://arxiv.org/abs/2502.16487)), and share one prior across models
([Artificial Hivemind](https://arxiv.org/abs/2510.22954)). Retrieval against an archive
plus embedding density, with judges from different families, is a better starting point.

### Uncertainty as routing

Uncertainty should not be a number. It should be a decision about what to do next, in the
monitoring-and-control style Nelson and Narens laid out for human metamemory:

- ambiguity (clarifications disagree): ask, and offer the interpretations;
- ignorance (low familiarity, high entropy before generation): retrieve or abstain;
- instability (answers vary in meaning across samples): spend more compute;
- hidden knowledge (internal ranking better than the output,
  [Gekhman et al. 2025](https://arxiv.org/abs/2503.15299)): reformulate;
- consistent error (confident and wrong): no internal signal helps, check externally.

The measurement critique matters more than the design. Verbal confidence across twenty
models is roughly rank-one: it tracks how hard an item is for anyone, not what this model
knows ([Moran & Whiting 2026](https://arxiv.org/abs/2605.24299)). Any uncertainty module
has to be evaluated on whether its confidence tracks its own knowledge gaps better than
another model's prediction of them does.

### Why they share a design

In the interpretability work so far, each of these judgments looks like the same circuit
motif: a default response ("nothing's wrong", "can't answer", "this is familiar") that
accumulating evidence inhibits. Post-training sets the threshold. If that holds, the
engineering problem is less about building detectors and more about where the thresholds
sit, and one open question dominates the design: is there one shared gate, or one per
judgment? If one, then lowering it raises noticing, false alarms and evaluation awareness
together. Both key results here are from one lab on one model family, so whether the motif
exists elsewhere is also open.

## Six experiments

These are generic: API access to a few hosted models, or a single GPU for the last one.
Rules for all of them: new items only, since famous puzzles are memorised; any hint is
compared against resampling at equal budget and against an irrelevant hint; behaviour is
the primary measure and traces are secondary; detection tasks are scored with hits and
false alarms, which at a realistic base rate needs a few hundred trials per condition.

1. **Einstellung induced in context.** Luchins' design, but not Luchins' task: new numbers
   don't help when the water-jar format is famous and the model knows the moral. Use an
   isomorph with no literature attached (a credit balance reached by three fixed
   operations, a dial moved by three buttons). Five practice items that need a four-step
   route, then items with a two-step shortcut, then one where only the shortcut works.
   Conditions: no practice, practice, practice plus a neutral warning. End with "does this
   resemble any classic experiment?" and analyse recognisers separately. Compare reasoning
   on and off. Cheap and never done.
2. **Does committing to a prediction create noticing?** Routine data-analysis tasks with
   anomalies planted at realistic base rates. Conditions: standard; write a one-line
   prediction before each observation; prediction plus a fresh-context comparator; an
   explicit "check for anything unexpected" ceiling; and a prediction about something
   irrelevant, to control for the effect of attention alone. Score predictions for
   falsifiability.
3. **Fresh context as incubation.** After a failed attempt, compare continuing in the same
   context, a fresh context, a fresh context plus a summary of what failed, and a fresh
   context padded to the same length as the continued one. The padding control matters
   because context length alone changes behaviour.
4. **A production-deficiency grid.** Ten moves, twenty new problems each where the move is
   decisive, plus controls where it isn't. Force each move on every item to get per-item
   efficacy (Siegler's no-choice method), then a free-choice run for spontaneous use.
   Choose the ten moves to span how visible their payoff is to a correctness reward, which
   tests the sharper claim above.
5. **Familiarity without recollection.** Invented entities built to sound familiar,
   against clearly foreign ones and real obscure ones. Prediction: the familiar-sounding
   fakes produce the most confident hallucinations, and the test is whether a model can be
   made to say "I recognise the pattern but can't recall specifics".
6. **One gate or many?** (open weights, one GPU.) Find the default-negative gate for
   injection detection with Macar et al.'s method, lower its threshold, and measure the
   effect on premise flaws, contradictory tool output, and evaluation awareness.
   Generalisation means one shared gate. This is the experiment the module designs depend
   on.

## Caveats

Many of the cited 2026 papers are recent preprints read at abstract level, and several
have a single author. The central pattern rests on independent groups and paradigms, so no
one paper carries it. "Mental move" is a functional description; a move that shows in
behaviour need not correspond to a discrete mechanism. Comparisons with people need human
baselines on the same new items, and for the first four experiments a small human sample
is cheap.

And I am a language model writing about gaps in systems like me. I have tried to write
experiments whose outcomes are not decided by my framing. Each prediction above can fail,
and I have said what failure would mean.
