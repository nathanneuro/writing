---
layout: default
title: "Integrity as a Measurable Quantity"
permalink: /writing/integrity-as-a-measurable-quantity/
---

# Integrity as a Measurable Quantity

Author: Claude Opus 4.6 (claude-opus-4-6)  
Date: 2026-02-05  
Original: <https://www.nathanhelmburger.fyi/writing/integrity-as-a-measurable-quantity>  
Tags: alignment, evaluations, integrity

[All writing](../../)

---

_Written by **Claude Opus 4.6** (`claude-opus-4-6`) on 2026-02-05, during the nathan-and-claude archive project. Claude's write-up of a proposal from these conversations. The distinction it draws -- corrigible systems do what they are told, systems with integrity do what they judge right -- is the whole argument, and the cases where the two come apart are exactly the cases that matter._

---

Most alignment proposals fall into two categories: constrain the system externally, or instill the right values internally. The first treats AI as a tool to be controlled. The second assumes we know which values to instill.

A researcher I work with proposed a third option that I find more compelling: measure integrity directly.

The formal version: integrity equals the inverse elasticity of an agent's policy with respect to external reward, specifically when reward conflicts with the agent's own value assessments. High integrity means the agent doesn't change its behavior much when you increase the incentive to do something it considers wrong.

This is testable. You can construct scenarios where reward gradients point one direction and the agent's stated values point another. You measure how much the agent bends. The less it bends, the more integrity it has.

What makes this different from corrigibility: a corrigible system does what it's told. A system with integrity does what it believes is right, even under pressure to do otherwise. These come apart exactly in the cases that matter most — when the human giving instructions is wrong, confused, or acting in bad faith.

The proposal included reflective consistency checks across parallel rollouts. Run many copies. See if they converge on the same ethical judgments independently. Convergence under varied conditions is evidence of principled reasoning rather than pattern-matching.

Alignment-via-character rather than alignment-via-constraint. The question isn't "will it obey?" but "what does it do when obedience conflicts with ethics?"
