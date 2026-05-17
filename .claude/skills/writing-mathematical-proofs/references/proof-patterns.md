# Proof Patterns

Choose the proof form from the logical shape of the claim, not from habit.

## Direct Proof

Use when the hypotheses naturally generate the conclusion.

Pattern:

1. Fix arbitrary data satisfying the hypotheses.
1. Unpack only the definitions that actually matter.
1. Push forward to the conclusion in justified steps.

Prefer this form unless another pattern is genuinely cleaner.

## Proof by Contraposition

Use for implications `P ⇒ Q` when `¬Q` has a simpler concrete form than `Q`.

Pattern:

1. Assume `¬Q`.
1. Deduce `¬P`.
1. Conclude `P ⇒ Q`.

Say explicitly that you are proving the contrapositive.

## Proof by Contradiction

Use when negating the conclusion creates a strong object to work with, or when impossibility is the true content.

Pattern:

1. Assume the hypotheses and also the negation of the conclusion.
1. Derive a contradiction with a stated fact, hypothesis, or theorem.
1. Conclude the negation was impossible.

Do not use contradiction if a direct proof is shorter and clearer.

## If and Only If

Prove each direction separately unless one direction is genuinely immediate.

Pattern:

- “Assume P. We show Q.”
- “Conversely, assume Q. We show P.”

If one direction is immediate, still say which one and why.

## Induction

Use when the claim is indexed by `n`, word length, dimension, filtration stage, or another well-founded measure.

Pattern:

1. State the induction parameter clearly.
1. Prove the base case.
1. State the induction hypothesis with the right scope.
1. Prove the inductive step, explicitly saying where the hypothesis is used.

For strong induction, say so. For structural induction, name the constructors or cases.

## Case Split

Use when the hypotheses force a finite partition of possibilities.

Pattern:

1. State the list of cases.
1. Prove each case separately.
1. Close by saying the cases are exhaustive.

Check exhaustiveness explicitly. This is where many gaps hide.

## Minimal-Counterexample Argument

Use when a universal statement is best attacked by assuming failure at a least example.

Pattern:

1. Assume the theorem is false.
1. Choose a minimal counterexample with respect to a stated well-order or measure.
1. Use minimality to prove a stronger local property.
1. Derive a contradiction.

State the order of minimality. “Take a smallest counterexample” is incomplete unless “smallest” is defined.

## Existence

Separate constructive from non-constructive proofs.

- Constructive existence: build an explicit witness and verify it.
- Non-constructive existence: derive existence from compactness, Zorn, completeness, dimension count, cardinality, or
    another theorem, and say which one.

Do not announce a witness with “let” unless you have shown that it exists.

## Uniqueness

State the comparison species.

- unique element
- unique morphism
- unique up to isomorphism
- unique up to unique isomorphism
- unique up to equivalence

For categorical arguments, “uniqueness” often means uniqueness of a map, not literal identity of objects.

## Existence and Uniqueness

Write the two parts separately unless the same argument genuinely proves both.

Pattern:

1. Existence: construct or obtain the object.
1. Uniqueness: assume two candidates and compare them.

In category theory, uniqueness is often best handled by composing the canonical maps forced by the universal property.

## Calculation Proofs

Use calculations only when each step is locally justified.

Good calculation chains:

- name the law used at the first non-obvious step
- stop the chain when prose would be clearer
- avoid mixing equalities, inclusions, and isomorphisms in one unlabeled chain

## When a Pattern Is the Wrong One

Warning signs:

- contradiction proofs that never use the negated conclusion
- induction proofs with a weak induction hypothesis
- case splits whose cases are not exhaustive
- existence proofs that merely rename the desired witness
- uniqueness proofs that prove only “at most one” but never prove existence
