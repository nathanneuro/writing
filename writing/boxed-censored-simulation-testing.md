---
layout: default
title: "Boxed Censored Simulation Testing: a meta-plan for AI safety which seeks to address the 'no retries' problem"
permalink: /writing/boxed-censored-simulation-testing/
---

# Boxed Censored Simulation Testing: a meta-plan for AI safety which seeks to address the 'no retries' problem

Author: Nathan Helm-Burger  
Date: 2026-11-16  
Original: <https://www.lesswrong.com/posts/pFzpRePDkbhEj9d5G/an-attempt-to-steelman-openai-s-alignment-plan>

[All writing](../../)

---

*By Nathan Helm-Burger. First published on LessWrong on 2023-07-13 as ["An attempt to steelman OpenAI's alignment plan"](https://www.lesswrong.com/posts/pFzpRePDkbhEj9d5G/an-attempt-to-steelman-openai-s-alignment-plan), written in response to the launch of OpenAI's Superalignment team. Revised and expanded under the present title on [AI-Plans](https://ai-plans.com/abs/xfnhxph5ycmhzlg), where it was up by September 2023; that version added the "Known Weaknesses" section. Reposted here unchanged on 2026-11-16, apart from formatting, straight quotes, and one typo.*

This plan suggests that high-capability general AI models should be tested within a secure computing environment (box) that is censored (no mention of humanity or computers) and highly controlled (auto-compute halts/slowdowns, restrictions on agent behavior) with simulations of alignment-relevant scenarios (e.g. with other general agents that the test subject is to be aligned to).

---

I'd like to start by sharing two quotes which inspired me to write this post. One from Zvi and one from Paul Christiano. Both of these contain further quotes within them, from the OpenAI post and from Jan Leike respectively.

## [Zvi](https://www.lesswrong.com/posts/NSZhadmoYdjRKNq6X/openai-launches-superalignment-taskforce)

> "Our goal is to build a roughly human-level automated alignment researcher. We can then use vast amounts of compute to scale our efforts, and iteratively align superintelligence."
>
> Oh no.
>
> An human-level automated alignment researcher is an AGI, also a human-level AI capabilities researcher.
>
> Alignment isn't a narrow safe domain that can be isolated. The problem deeply encompasses general skills and knowledge.
>
> It being an AGI is not quite automatically true, depending on one's definition of both AGI and especially one's definition of a human-level alignment researcher. Still seems true.
>
> If the first stage in your plan for alignment of superintelligence involves building a general intelligence (AGI), what makes you think you'll be able to align that first AGI? What makes you think you can hit the at best rather narrow window of human intelligence without undershooting (where it would not be useful) or overshooting (where we wouldn't be able to align it, and might well not realize this and all die)? Given comparative advantages it is not clear 'human-level' exists at all here.

## [Paul Christiano](https://www.lesswrong.com/posts/Hna4aoMwr6Qx9rHBs/linkpost-introducing-superalignment?commentId=NsYXBdLY6edAXavsM)

> The basic tension here is that if you evaluate proposed actions you easily lose competitiveness (since AI systems will learn things overseers don't know about the consequences of different possible actions) whereas if you evaluate outcomes then you are more likely to have an abrupt takeover where AI systems grab control of sensors / the reward channel / their own computers (since that will lead to the highest reward). A subtle related point is that if you have a big competitiveness gap from process-based feedback, then you may also be running an elevated risk from deceptive alignment (since it indicates that your model understands things about the world that you don't).
>
> ...
>
> I think that takeover risks will be small in the near future, and it is very plausible that you can get huge amounts of research out of AI systems before takeover is a significant risk. That said I do think eventually that risk will become large and so we will need to turn to something else: new breakthroughs, process-based feedback, or fortunate facts about generalization.
>
> As I mentioned, I'm actually not sure what Jan's current take on this is, or exactly what view he is expressing in this piece. He says:
>
> > "Another important open question is how much easier evaluation is if you can't rely on feedback signals from the real world. For example, is evaluation of a piece of code easier than writing it, even if you're not allowed to run it? If we're worried that our AI systems are writing code that might contain trojans and sandbox-breaking code, then we can't run it to "see what happens" before we've reviewed it carefully."

## The goal: Keep humanity in charge. Keep the researchers in charge of the AI subjects (including AI-based researchers).

Building a human-level alignment researcher is nearly like making AGI on its own. Where possible, make the AI researcher narrower, give more specific tasks. Also, carefully keep it contained and unaware of humanity. Train the researcher in a simulation where it is monitoring and experimenting on the stronger AI subject which is itself in it's own separate simulation, ignorant of humanity and the AI researcher.

Give the AI researcher substantial powers over the subject AI.

These researcher powers should include: slowing the subject down, wiping its memory and rerunning it with different initializations and in different scenarios, reading all its parameters and hidden states across frequent checkpoints.

## Stick with just A and B, alignment researcher and alignment subject.

Don't make a stack of A aligns B aligns C aligns... because the telephone game effect will likely lead to inherent instability and greater chance of mishaps. Also, because if C is so far ahead of the smartest humans that we're dependent on B to understand it, we've already gone too far with our ambitions. An aligned AI should be willing to respect our request that it not self-improve, so if we truly align B, and B is strong enough to prevent the rise of rogue AI, then we've successfully gotten far enough with alignment to make it to the long reflection.

It seems plausible to me that an intelligent AGI which was no smarter than an unusually smart human and also well aligned would be sufficient to police the world to prevent rogue AGI breakout. A digital agent has a lot of inherent advantages, even when you take recursive self-improvement off the table. For example: rapidly copying itself, moving around the world at the speed of the internet, not getting bored or tired or needing sleep or getting sick or aging, potentially operating at many times human speed. So if we get that far, we have bought ourselves a lot of time to work on the harder problem of aligning superintelligence.

## Try many different things

Don't fencepost-security your research effort. You can have multiple copies of the AI researcher working on different aspects of the problem at once. Blue-teamers trying to proactively strengthen, while Red-teamers try to find holes. When flaws are found, you don't just shallowly patch them, you consider what underlying paradigm problems might have given rise to the problems. Check to make sure the AI subject notices when it is being pushed too far from its training distribution and gives warnings and eventually just shuts down. Don't let it fail-dangerous, make sure it fails-safe.

Blue-sky experimenters can design and test novel architectures and algorithms in search of fundamentally more interpretable models. I feel pretty confident that humanity is capable of discovering low-safety-tax architectural changes which will make transformer-like models fundamentally easier to interpret.

## Iteratively refine the simulations

Keep working on improving the breadth and realism of the two simulation layers, the AI researcher's sim and the AI subject's sim. The AI researcher should be able to test the subject in a wide variety of fictional scenarios. These scenarios should be made larger and more complex over time as more compute becomes available, and as the various security measures like honeypots detect any sign of the AIs realizing they are in a sim and trying to break out. Eventually there should be entire simulated societies with multiple AI subjects coordinating to work within them.

The fact that the human researchers get to wipe the memories of the AIs means that flaws found over the course of running the simulation can be patched more easily than it could with a human. I would expect failures like the fictional portrayal of the Truman Show, with gradually accumulating evidence and suspicion leading to a realization of the truth. I would also expect that such would be detectable and patchable, over and over again.

## Known Weaknesses

### Impractical / Unprofitable

This would be a large sink of resources without immediate opportunities for profitability. In the medium term, it seems possible to safely extract easily verifiable intellectual outputs such as mathematical proofs or code snippets. In the longer term, obviously the benefits of managing to allow ourselves to work on the important project of alignment in a safer way is highly valuable.

The high initial investment of resources and the inconvenient nature of the boxing and censoring may dissuade companies from adopting this approach.

Possible solutions:

**Governance.** Putting government regulations in place to pressure all leading orgs to accept the costs, thus keeping the commercial playing field level.

Using government funding for the development of the boxed compute resources, and the censored datasets, and the simulation environments. All researchers and companies could then get access to these resources, reducing the burden. This is especially valuable for the datasets and simulations, which can be shared with any number of users with no overhead. This could greatly reduce the friction for small orgs, academic labs, and individual researchers.

**Levels of Intensity.** Another approach to easing the 'safety tax' burden would be to have several levels of intensity of boxing and of censoring. As some thresholds of risky capability are passed (perhaps evaluated by an external org like ARC evals), then appropriate levels of caution would then be required going forward.

### Adequate Simulations

Building a sufficiently realistic simulation that the results would be useful is a difficult problem, probably requiring a lot of resources to do well.

Some alignment plans may be much more compatible with simulation testing. For example, the approach of developing brain-like AGI has the compatibility advantage of potentially creating a sufficiently human-like AI agent that it could be used as a simulated population of digital 'people' which the alignment-subject agent is being aligned to. Obviously, such an in-depth simulation involving populations of complex agents would be a late-stage high-resource project.
