---
layout: blog
title: Why "LLM for Compiler" Is a Reasonable Research Question
date: 2025-05-27
authors:
  - genghan
---

Large Language Models (LLMs) are statistical systems trained to compress and reconstruct knowledge drawn from vast corpora of human-created data. In that sense, they implicitly store and recombine known information. Programming languages—whether general-purpose, domain-specific (DSLs), or architecture-specific (ASPLs)—are often carefully crafted abstractions that build upon decades of existing language design. Their syntax and semantics tend to evolve incrementally, shaped by the cognitive constraints of human users: a language too difficult to learn simply won’t gain traction.

This evolutionary pattern implies that many programming abstractions have a structural similarity to one another. Since LLMs are trained on large amounts of code and documentation, they are well-positioned to recognize and recombine these shared abstractions. With well-chosen in-context examples, LLMs can be prompted to generate valid and even semantically meaningful programs by mimicing the structure of previously seen patterns.

In parallel, compiler research is often seen as a field that advances slowly. A common view is that making meaningful progress in compiler design requires a deep accumulation of systems knowledge, domain-specific constraints, and algorithmic insights. This high barrier to entry can lead to a conservatism in innovation—new techniques are often minor extensions of established ones.

<strong>That’s precisely why LLMs offer an intriguing angle:</strong> if much of compiler innovation involves recombining deep but well-established patterns, then a statistical tool like an LLM—trained on the output of expert human effort—might be able to surface novel combinations or optimizations that are still grounded in known techniques but not previously explored.

In this view, prompting an LLM with expert-curated examples is a form of injecting inductive bias—we guide the model toward the known-good regions of the solution space. However, the innovation happens when the model deviates from that expert knowledge and finds non-obvious solutions—combinations or transformations that haven't been explicitly taught, yet still perform well. In this setting, rewarding outputs (e.g., correctness, performance, or simplicity) rather than mimicing processes may be a better optimization strategy.

Put differently: LLMs may not just emulate compiler experts—they may augment them.