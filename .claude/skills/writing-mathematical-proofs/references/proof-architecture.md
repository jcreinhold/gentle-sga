# Proof Architecture

Use this file for theorem-scale arguments that are not already short and linear.

If the work has its own filesystem workspace, treat `rapid-prototype.md` as the scratch document and this file as the
cleaned-up scaffold that survives after the first decomposition pass.

The goal is not to start writing the main proof sooner. The goal is to turn a hard theorem into a small dependency
scaffold that can actually be proved.

This workflow distills practical advice from Halmos, Tao, Hammack, and Gowers. See the source list at the end.

## The Process

### 1. Write a rapid prototype

Before writing full proofs, write a bare-bones skeleton containing:

- the main theorem
- any load-bearing definitions
- candidate milestone propositions
- candidate local lemmas
- very short notes to self about why each item should be true

Do not optimize statements yet. The point is to expose the big picture and leave yourself free to move pieces around.

If the theorem has its own workspace, this first pass belongs in `rapid-prototype.md`.

### 2. Distill the proof architecture

After the prototype exposes the shape of the argument, rewrite the stable part into `proof-architecture.md`.

This cleaned-up scaffold should contain:

- the current theorem statement;
- the milestone propositions;
- the local technical lemmas;
- the dependency order;
- the current gaps, blocking lemmas, and stop rules.

Keep disposable scratch work, abandoned branches, and rough trial statements in `rapid-prototype.md`, not here.

### 3. Draw the dependency graph

Make the logical order explicit.

At minimum, record:

- which results feed directly into the main theorem
- which technical facts are used only inside one proof
- which clusters of results naturally belong together

Use a bullet DAG, a tiny table, or box-arrow notes. The format does not matter; visibility does.

Questions to ask:

- what are the genuine milestones, without which the theorem cannot move?
- which technical facts are only there to discharge one local obstacle?
- which result is conceptually important enough to deserve section-level prominence?

### 4. Run a level audit before deeper factoring

Before adding more lemmas, check whether the current theorem is being asked on the right object.

Ask:

- is the statement substantive on the exact object, or only on a shadow?
- does a trivial mediator or surrogate choice make the claim immediate?
- does the live content sit in data omitted by the current formulation?

A shadow is a quotient, classifier, invariant, or summary that forgets some datum. If the theorem has collapsed onto a
shadow, stop adding lemmas on that same level. Classify the result as false at this level, tautological at this level,
or substantive only at a richer level. Then either restate the theorem at that richer level, record a stop rule that the
present level is only bookkeeping, or switch to `mathematical-theory-design` or `mathematical-conjecture-design`.

### 5. Project to a simpler paper when stuck

If the dependency graph is still murky, do not keep attacking the full theorem.

Instead, project to a simpler version by removing roughly half the difficulty:

- a simpler special case
- one dimension instead of many
- the main term without the error terms
- a model example
- a near-counterexample that shows where the theorem is tight

Then ask: what are the real subproblems in the simplified setting? Those often reveal the right milestone propositions
for the full proof.

### 6. Use backward scratch work

For the main theorem, or for one milestone proposition, work backward from the desired conclusion to something obviously
true or already known.

Typical use:

- start from the target conclusion
- algebraically or categorically transform it until a recognizable intermediate claim appears
- stop when you reach a fact that should be isolated as its own lemma or proposition

Then reverse the direction for the final proof.

Backward work is scratch work, not finished prose. Its job is to discover the next enabling claim.

### 7. Choose the right kind of subclaim

Once a candidate subclaim appears, classify it correctly.

- Use a **milestone proposition** when the subclaim is a conceptual turning point, is cited later, or makes the main
  theorem mostly formal.
- Use a **local lemma** when the subclaim removes one technical obstacle and can be forgotten after use.
- Use a **sublemma inside a proof** when the intermediate claim only matters inside that proof.
- Merge two technical lemmas if the intermediate bridge statement is only verified once and only used once.

Good decomposition removes one source of difficulty per lemma. Bad decomposition mixes unrelated jobs or creates labels
the reader must remember for no payoff.

### 8. State lemmas for use, not for proof

When you keep a lemma, state it in the form that is easiest to apply:

- natural hypotheses
- manifestly useful conclusion
- only the notation the reader really needs

Push disposable notation, local calculations, and purely internal bridge claims into the proof when possible.

### 9. Prove in dependency order

A practical order is:

1. prove the enabling local lemmas;
1. prove the milestone propositions;
1. assemble the main theorem from them;
1. move orthogonal or dull technical material later or to an appendix.

If the top-level proof still looks like a heroic direct attack after this, the architecture is not finished.

### 10. Escalate only after architecture fails

Do not jump too quickly from “this proof is hard” to “the definitions are wrong.”

First try:

- prototype
- dependency graph
- simpler-model projection
- backward scratch work
- lemma / proposition reclassification

If the proof still feels ad hoc after that, then the issue may really be definitional; use `mathematical-theory-design`.

## Source Notes

This workflow is based mainly on:

- Paul Halmos, _How to Write Mathematics_: outline first, organization as graph/tree, find a shared lemma when proofs
  start repeating, and avoid both unbroken long proofs and boring lemma parades.
- Terence Tao, “Write a rapid prototype first,” “Organise the paper,” “Create lemmas,” and “On compilation errors in
  mathematical reading”: skeleton first, explicit dependency diagrams, milestones early, localize technical work, merge
  one-use technical bridges, and project to a simpler paper when the full one is too hard to see.
- Richard Hammack, _Book of Proof_: use backward scratch work to discover a route from the target to an obvious fact,
  then reverse it in the final proof.
- Timothy Gowers, “examples first”: when the abstract structure is slippery, get a concrete model in mind before trying
  to carry the full theorem.
