# On Writing Mathematics

Use this file as the baseline style guide for proof writing.

It distills Halmos, Knuth-Larrabee-Roberts, Higham, Velleman, and adjacent lecture-note advice into rules that are cheap
to apply while drafting.

For theorem-scale decomposition, also read [proof-architecture.md](./proof-architecture.md).

## Keep Each Passage Single-Purpose

Give each block one job:

- **Definition**: introduce a notion exactly
- **Theorem / Lemma / Proposition / Corollary**: state a claim exactly
- **Proof**: justify the claim rigorously
- **Example**: show how the notion behaves
- **Remark**: orient the reader, compare formulations, or mark a limitation

Do not hide proof-only notation inside a theorem statement. Do not let examples stand in for proofs. Do not smuggle new
concepts into the middle of a proof unless the proof itself is about introducing them.

## State the Ambient Assumptions Early

Before the first formal statement that depends on them, say what world the reader is in:

- base category, site, ring, field, topological space, manifold, model, universe level, finiteness convention
- standing notation and comparison species
- whether maps are continuous, linear, smooth, exact, monoidal, and so on

Readers should not have to discover on page three that every space was compact Hausdorff all along.

## Write for a Strong Reader Who Does Not Share Your Local Context

Assume mathematical maturity. Do not assume your notation, conventions, or hidden abbreviations are already known.

Define symbols before use. Recall a hypothesis when it becomes active again. Prefer a cooperative voice:

- “We show…”
- “Fix…”
- “By the universal property…”
- “It remains to prove…”

## Use Words and Symbols Deliberately

Notation is a tool, not a decoration.

- Introduce the minimum notation that makes the argument easier to check.
- Use words instead of symbols when the sentence reads more cleanly that way.
- Keep one symbol for one role within a local argument.
- Distinguish equality from isomorphism, equivalence, inclusion, and factorization.

Write “for every”, “there exists”, and “if and only if” when the symbolic form would slow the reader down. Use symbols
when they materially shorten or clarify the proof.

## Make Displayed Mathematics Part of the Sentence

Displayed equations and diagrams do not replace prose. They need:

- a lead-in
- punctuation
- a reason for appearing exactly there

Bad:

```text
A=B=C=D
```

Better:

```text
Using associativity, rewrite A as B. Applying Lemma 2.4 gives

B = C.

Substituting the definition of D then yields C = D.
```

Chains of equalities or isomorphisms are acceptable only when every step is locally checkable or named in the
surrounding prose.

## Structure Proofs for Navigation

A proof is for a human reader, not just for truth preservation.

- Write forward when possible.
- Announce steps or cases if the proof is long.
- Extract reusable arguments into lemmas.
- Separate existence from uniqueness.
- Mark the end of a case before moving to the next one.

Useful strategy sentences:

- “We first reduce to the finite case.”
- “The proof has two parts: existence and uniqueness.”
- “We argue by induction on the length of the filtration.”

Do not add fake roadmaps to short proofs.

## Use Lemmas as Memory Management

For large arguments, factor aggressively, but not mechanically.

Do this before writing the main proof, not after it has already sprawled. A hard theorem should usually be approached by
asking which smaller claims would make the top-level argument mostly formal.

- Use lemmas to isolate technical work that the reader should be able to forget once a milestone result is established.
- Let each lemma remove one source of difficulty cleanly. If a lemma has several unrelated jobs, the architecture is
    probably still muddy.
- Promote a lemma to a proposition, theorem, or its own section when it becomes a conceptual hinge or its proof has
    independent weight.
- Merge technical lemmas that are only useful together instead of making the reader retain an artificial intermediate
    statement.
- Keep one-use lemmas close to where they are used.
- If an argument spans many moving parts, expose its dependency shape early: milestone results first, then technical
    reductions, with standard or orthogonal material moved later or to an appendix.

The point is not to maximize the number of lemmas. The point is to make the main theorem approachable, reduce reader
memory load, and turn the final proof into an assembly of already-understood moves rather than a heroic direct attack.

## State Theorems Cleanly

A theorem statement should be exact and citable on its own.

- include every hypothesis that the proof uses
- keep proof-only temporary notation out of the statement
- avoid “obvious” omissions in quantifiers or domains
- keep local setup outside the formal statement when possible

If a result needs explanation or motivation, place that just before or just after the statement, not inside it.

## Use Examples and Counterexamples Honestly

Examples teach the reader how to think with a definition or theorem. Counterexamples show why hypotheses and comparison
species matter.

Use examples to:

- preview an abstraction
- test whether a definition has the intended scope
- separate similar-looking notions

Use counterexamples to:

- show a converse fails
- show a hypothesis is necessary
- expose overclaims in a draft proof

Do not use an example as a substitute for a proof of a universal statement.

## Revise for Mathematical, Not Merely Grammatical, Clarity

After drafting, ask:

- is every quantifier visible?
- is every domain restriction stated?
- is every symbol defined before use?
- does each paragraph do one job?
- does each displayed formula have an explanation?
- can a hostile reader tell where each hypothesis enters?

Revision is part of the mathematics. A clearer statement often reveals a cleaner proof.

## Remember the Target

A good proof lets the reader answer, without strain:

1. What is the claim?
1. Under what hypotheses?
1. What kind of argument is being used?
1. Why is each step justified?
1. What is the actual conclusion: equality, isomorphism, equivalence, existence, uniqueness, or factorization?
