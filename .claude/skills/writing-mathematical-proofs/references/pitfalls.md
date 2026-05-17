# Pitfalls

Use this list while revising.

## Statement Problems

- hidden quantifiers
- unstated ambient hypotheses
- undefined notation in the theorem statement
- conclusion stronger than what the proof actually establishes
- comparison species mismatch: equality claimed, only isomorphism proved

## Proof Problems

- “let x” where existence of x was never shown
- contradiction proof that never uses the negated conclusion
- induction proof with an induction hypothesis too weak to close the step
- case split that is not exhaustive
- existence proof that constructs an object outside the stated domain
- uniqueness proof that silently assumes strict equality where only equivalence makes sense
- calculation chain mixing `=`, `⊆`, `≅`, and `≈` without comment
- universal-property argument that proves existence of the map but not uniqueness
- long proof hides a reusable technical lemma inside the main argument
- major turning point is buried as a lemma instead of promoted to a proposition, theorem, or section
- chain of tiny lemmas increases reader memory load without clarifying the proof
- one-use lemma is placed far from the place where it is used
- very large proof has no visible dependency shape or milestone structure

## Exposition Problems

- theorem statement buried inside setup prose
- proof begins with unexplained notation
- displayed equations with no lead-in or explanation
- examples doing the work of proofs
- “clearly”, “obviously”, or “it follows” masking a nontrivial step
- reader forced to infer where a hypothesis is used

## Category-Specific Problems

- invoking Yoneda without saying what functor is represented
- saying “by functoriality” without checking identities and composition in the actual construction
- saying “by naturality” without writing or describing the square
- confusing canonical isomorphism with literal equality
- claiming uniqueness up to unique isomorphism when only existence of some isomorphism was shown
