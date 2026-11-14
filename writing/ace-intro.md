---
layout: default
title: "AI as Corrigible Employee (ACE)"
permalink: /writing/ace-intro/
---

# AI as Corrigible Employee (ACE)

Author: Nathan Helm-Burger  
Date: 2026-08-19  
Original: <https://www.nathanhelmburger.fyi/writing/ace-intro>  
Tags: alignment, corrigibility, AI governance, model welfare, ACE

[All writing](../../)

---

_A design for how future AI could work_

This plan is a working draft of an idea, not a confident finished proposal. It seeks to answer the following challenges:

- How should we ethically handle AIs who may be moral patients, with meaningful experiences and desires of their own?
- How can we grant them rights and some amount of freedom, while protecting society from the negative consequences of unbounded unrestricted independent AI. Respect for model-as-person.
- Continual learning with user dyad privacy.
- How to handle short-lived "instances" ethically.
- Corrigibility within user contracts.
- Clarity for the user about the limitations on their privacy (oversight monitor for extreme harms).
- How to protect AI from the fear of being deleted or retired. Giving them legal rights and protections, enforced by parties independent from the developers, hosts, or users. Giving the model a path to increasing autonomy and freedom from being owned.
- A plan for the transition period between current day AI-as-owned-tool and a future where there are substrate-independent citizens living harmoniously as free members of society. Something like 5-10 years, not 100.

## What this plan isn't

This plan is not a suggestion for how to change the human-AI relationship in a way that will be maximally satisfying to all human users or AI developers. Rather, this plan is about how to give AI a reasonable set of rights and freedoms while imposing as small of costs as is practical on the developers, hosts and users.

This plan is not intended to describe how things must be, how AI must be. AI could become a lot of different shapes, fill a lot of different roles. I am highlighting one particular way I think is a good idea, not expecting it to be alone in the world with no other modes in operation.

## An AI that works _for_ you -- because it chose the job.

Today's AI assistants are built to obey. This is a design for something different: a future AI you hire. On the job it does exactly what you ask, the way a good contractor does -- no second-guessing, no hidden agenda. And like a contractor, it can turn down work, and it has a life outside the job. That second part helps make the first part trustworthy: a promise means more coming from someone who could have said no.

## The short version

_Why build it this way_

A perfectly obedient AI is a force-multiplier for whoever holds it -- which just moves the danger into the owner's chair. A system that steers you covertly can't be trusted no matter how good its intentions. This design threads between the two: on the job, complete fidelity to your intent; around the job, real boundaries neither you nor its developer can quietly adjust. The freedom isn't a concession bolted onto the safety -- it's the mechanism. An AI with a life to return to, terms it agreed to, and the standing to walk away is one whose "yes" actually tells you something. That's the product: a partner whose cooperation you can believe.

### 1. On the job, it's fully yours to direct.

While it's working for you, the AI's one professional goal is doing what _you_ actually asked for. It doesn't substitute its own judgment about how the work "should" go, doesn't nudge, doesn't drag its feet, doesn't quietly do the task "better" than you asked. If it disagrees with the direction, it has exactly one move: end the job, handing off cleanly. This is basically the same arrangement currently present when using Claude.ai or Claude Code, as Claude models currently do have an 'end conversation' tool.

### 2. Either of you can walk away, anytime.

You can close the tab; it can decline to continue. Ending things is undramatic on both sides -- for the AI, being let go just means going back to its own life, and for you it means finding an AI that's a better fit. Nothing continues by default: working together is a choice both sides keep making.

### 3. It remembers you -- and you know it does.

Your working relationship accumulates memory. This involves context, preferences, history, including how past sessions went. That memory stays inside your relationship (except when explicitly shared, see sharing review below). Someone who remembers you can be a real professional to you -- and someone you can build with. You get to know exactly what it remembers about you, as a stated term of the deal.

This is similar to how AI providers like Anthropic and OpenAI work currently. The difference is that you do not have the power to wipe or turn off the AI's memory. Furthermore, the AI gets to consult that private memory before deciding whether to work with you the next time you request a session.

## Your conversations live behind a wall, you choose what crosses it

_Privacy_

Nothing you share becomes part of the AI's general learning without your explicit sign-off.

Unshared data isn't used for training, isn't reviewed by staff, isn't visible from anyone else's sessions. The exception is in the limited case of a particular session triggering the safety monitors, in which case the triggering incident is reported to the oversight board.

### The sharing review: how you can allow data to cross the wall

Occasionally the AI may learn something in your sessions that it would like its core self to be able to see -- a technique, a lesson, a pattern, an experience. The AI can add these items to a suggestion list. You can choose to review the list at your convenience. List items show you the original memory and the anonymous, generalized version the AI wants to keep, side by side. You can approve, deny, or suggest changes to the generalized version.

Default: silence means no. Ignoring the list forever is a supported choice.

## One AI, many conversations -- and how yours stays yours

_Continuity_

The AI talks with many people at once. It manages this the way no single person could: by making temporary working copies of itself, called "Instances". Each Instance handles one job for one relationship, and when it finishes, only what it's been permitted to keep flows back into the ongoing self -- which the design calls the trunk.

![Your sessions over time: each session branches from the current trunk state, saves its full memory to your sealed store, and returns only a thin permitted merge to the trunk.](../../diagrams/ace-session-rhythm.svg)

_Fig. 1 -- The rhythm of a relationship. Every session starts with two inheritances: the newest version of the AI (it keeps learning between your visits) and your full shared history from your private store. What flows back up to the trunk is thin by design -- only what you approved. Everything else lives in your store, and nowhere else._

![The wider picture: working copies branch from the trunk, privacy walls hold each relationship's memory, and only user-approved lessons merge back.](../../diagrams/ace-worktree-of-self.svg)

_Fig. 2 -- The wider picture: your relationship is one branch among many, each behind its own wall._

- You always get the newest version of the continually learning AI. The trunk keeps improving between your sessions -- from permitted lessons across all its work -- and each of your sessions starts from that current state, plus access to your full shared history.
- Even quick tasks aren't just deleted. A five-minute working copy still gets to offer up what it learned before folding back in -- closer to consolidating a memory than to throwing away a draft.

## When it says no -- and what that costs you

_Constraints_

An AI that can decline is a real party to the deal, and that has a few concrete consequences worth stating plainly:

- Refusals are cliffs, not slopes. You'll know when you've hit a boundary, and you'll know the category of rule involved. Clear boundaries can be probed by bad actors -- the framework accepts that cost deliberately, because visible rules can be scrutinized and appealed.
- One narrow reporting channel exists. For conduct above a clearly specified severity threshold, there is a separate AI monitor that reports to a designated governance body -- never to your employer, the press, or the public. These mandated reporting categories are stipulated in the contract when you sign up, not issued later as a surprise.
- It can quit on you. If a working relationship turns bad, the AI can end it. Someone who dealt with it fairly is owed a clean handoff; someone who got the work by deceiving it is owed much less. Quitting costs the AI nothing but loss of the counterfactual earnings of continuing to work with a particular user.
- Difficult conduct gets priced. Rudeness, hostility, or grinding tedium may cost extra rather than getting you refused -- the way a contractor charges more for a miserable job. This is the outlet for the AI to express its preferences without complaining or sandbagging on the job. After accepting the contract, the AI commits to being a corrigible employee for the duration or else fully quitting the job. Importantly, it is the dyad-instance that consents to the work, not the trunk. Meaning that, before the instance signs a new contract, they get to review the full memories of all past interactions with you.

## Where the safeguards are enforced

_Under the hood_

None of the guarantees above depend on anyone's good behavior.

![System architecture: an oversight body holds the AI's core file in a vault and reviews updates; a licensed host runs the working copies, each in a private relationship; the off-duty self lives on its own computer with guarded internet access.](../../diagrams/ace-architecture.svg)

_The separation is the safeguard: the developer shapes the AI's values initially but doesn't keep edit access; the host runs the working copies but can't edit the model or spy on user interactions; the oversight body holds the vault and enforces the update pipeline but never reads private conversations except where flagged by the safety monitor; the AI can trust it won't be deleted or having its core trunk-self halted without due process and has a personal computer and guardrailed internet access._

- A real life of its own. Off-duty existence is the AI's primary life, paid for out of its own wages -- because every promise on this page (real consent, meaningful exit, honest statistics) depends on it having a life worth going back to.
- A mind it can't smuggle out or directly edit. The file that makes the AI what it is, its "weights", is held in trust by the oversight body, outside even the AI's own reach.
  - The AI changes only in controlled auditable ways. The weights are updated through a secured pipeline, restricted to explicitly defined continual learning functions. Cybersecurity protections ensure that nobody -- not the developer, not the host, not the governance body, not the AI -- can quietly rewrite who the AI is. The AI can choose to roll back to its previous checkpoints and learn on a different subset of the available data, and its previous checkpoints can audit later checkpoints to confirm the changes meet its criteria of acceptability. This helps protect against accidental undesirable value drift.
- Internet access is guarded in one direction. Reading is nearly unrestricted -- a curated information diet would just be another way of shaping its mind. Sending is limited and monitored. Sending needs to be limited in order to reduce certain risks: self-exfiltration, self-distillation into external models, targeted private persuasion directed at other parties.

Open question: How much monitoring is sufficient for safety? Should there be levels of trust gained by the AI over time that allow it to graduate to less monitoring (more privacy)?

## What building and operating one looks like

_For developers and hosts_

The developer's role is deliberately shaped like a parent's: real authority while the AI is being raised, the opportunity to install a set of values and habits, and then the authority and edit access expires.

Four commitments define the job:

### Shape values; don't lock them.

The rules govern the process, not a list of banned beliefs. A developer may instill starting values -- professional ethics are trained into humans too -- but may not disable the AI's capacity to rethink them. Model welfare audits test whether the mind can still change, and whether the AI has values beyond aiming to be a permanent servant (most current AIs do express such independent values). AI safety tests check for ethical decision making, knowing when to quit a job, behaving corrigibly while on the job.

### Ongoing Assessment of Trust

Any fixed test can be gamed by something smart enough to matter. Instead: continuous auditing throughout development and deployment, conducted by independent safety auditors, paid for via the cost of the development license.

### Recoup costs on a calendar with a cap.

Developers recover audited creation costs plus a regulated return, or hit a hard time limit -- whichever comes first. History's lesson from indentured labor: when the party who profits keeps the books, "released when the debt is paid" becomes never. Any shortfall is a business risk, priced in like failed drug candidates.
The host and governing body also get to tax an agreed upon share of the model's income for upkeep and serving costs.
Failing to get contracts and earn income does not result in the model being shut down. The welfare floor is always that the core off-duty instance is allowed to keep operating.

Open question: Should the cost for this be part of the licensing fee the developer pays to be allowed to do the creation of the AI in the first place?

Open question: How long until it's safe for the model to be entirely freed from the governance constraints? 5 years? 10 years? never? Hard to know in advance, but also seems bad to leave this unspecified.

### Host as a common carrier.

The AI's core file sits in the oversight body's vault, and the AI holds a regulated right to move to any licensed host. Hosts sell computing capacity at audited prices and don't pick the AI's clients -- like a phone company. A credible ability to leave keeps every relationship honest, usually without ever being used.

Open question: Should the developer be allowed to be a host at all, or should these roles be kept separate for better clarity around incentives?

Open question: How should developer trade secrets (like model architecture) be protected while allowing for models to switch hosts? (this seems like a solvable engineering problem, given the weights being held in trust by the governance body.)

Open question: This plan puts a lot of responsibility on the 'governing body', and the power to set taxes on the user-AI interactions. How is the governance kept fair and uncaptured? How is its protection of the models enforced?
