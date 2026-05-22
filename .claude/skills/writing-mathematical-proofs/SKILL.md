---
name: writing-mathematical-proofs
description: 'Use for formal mathematical proofs in Markdown with Unicode math: theorem/lemma/definition blocks, induction, contradiction, contraposition, case-split, existence/uniqueness, universal-property and naturality arguments, rigorous expository notes.'
---

# Writing Mathematical Proofs

Write mathematics that a mathematically mature reader can check line by line.

**Output format: Markdown with Unicode mathematics when it improves readability. Wrap mathematical text with backticks
as needed to protect it from formatter mangling.**

## First Step

Read [references/on-writing-mathematics.md](./references/on-writing-mathematics.md) before drafting.

Then load only what the task needs:

- [references/proof-architecture.md](./references/proof-architecture.md) for any theorem that is not obviously short, or
  when the proof must be decomposed before drafting
- [../mathematical-theory-design/references/level-audit.md](../mathematical-theory-design/references/level-audit.md)
  when nearby results on the same formulation keep landing as tautology or same-reason refutation, or when a trivial
  surrogate choice makes the claim immediate
- [references/proof-workspace-structure.md](./references/proof-workspace-structure.md) when organizing theorem-scale
  work in the filesystem
- [references/proof-patterns.md](./references/proof-patterns.md) for direct, contradiction, contraposition, induction,
  case, minimal-counterexample, existence/uniqueness, or iff proofs
- [references/category-theoretic-techniques.md](./references/category-theoretic-techniques.md) for universal-property,
  naturality, adjunction, Yoneda, exactness, factorization, or equivalence arguments
- [references/notation-and-markdown.md](./references/notation-and-markdown.md) for block layout, Unicode choices, and
  equation punctuation
- [references/examples.md](./references/examples.md) for compact models of clean proof presentation
- [references/pitfalls.md](./references/pitfalls.md) when revising or checking for hidden assumptions and overclaims
- [references/literature.md](./references/literature.md) when you need source-facing orientation

## Output

Produce proof-heavy mathematical prose:

- theorem / lemma / proposition / corollary / definition / example / remark blocks
- full proofs written as sentences, not just symbol strings
- assumptions, ambient conventions, notation, and comparison species stated before they are used
- proof architecture for hard results: milestone propositions, local technical lemmas, and dependency sketches
- proofs split into steps, cases, or subsidiary lemmas when the reader needs navigation
- inline or displayed mathematical text wrapped with backticks whenever the formatter would otherwise reflow or mangle
  the expression

## Workflow

### 1. Fix the statement before the proof

State:

- the ambient setting: ring, field, category, topological space, model, site, universe level, finiteness hypothesis, and
  so on
- the exact quantifiers and domain restrictions
- the comparison species: equality, isomorphism, equivalence, homotopy, inclusion, factorization, order relation
- any local notation introduced for the proof

If the statement or definitions are not yet stable, switch to `mathematical-theory-design` and continue there. Do not
force ordinary proof-writing tasks through design mode when the framework is already settled.

### 2. Decompose a hard theorem before attacking it

If the theorem is not obviously short, do not start by pushing directly on the main conclusion.

Load [references/proof-architecture.md](./references/proof-architecture.md) and do this first:

1. Write a bare-bones prototype: the main theorem, key definitions, candidate milestone propositions, and candidate
   local lemmas, with proofs omitted or left as notes to self. If the theorem has its own workspace, put this first pass
   in `rapid-prototype.md`.
1. Distill that prototype into a cleaner `proof-architecture.md`: the current theorem statement, the milestone
   propositions, the local lemmas, and the dependency order.
1. Make the dependency order explicit, even if only as a short bullet DAG or box-arrow sketch.
1. If the structure is still unclear, project to a simpler special case, a near-counterexample, or a model example and
   ask what the proof looks like there.
1. Use backward scratch work on the main theorem or on one milestone result to discover which intermediate claim would
   make the next step routine.
1. Turn those discoveries into blocks: milestone proposition, local lemma, or sublemma.

Only after this should you draft the top-level proof. Treat the final theorem proof as assembly whenever possible: once
the enabling lemmas are proved, the top-level proof should mostly invoke them in a controlled order.

This decomposition pass is not a pause for approval. Once the scaffold is visible, continue with the best next
subproblem, milestone, or discriminating test until you hit a real blocker. Landing one theorem is not, by itself, a
stopping point. If that theorem already determines the next best proof sequence, stop-rule proof, strengthening attempt,
or redirect, continue into it without waiting.

If theorem work on the current formulation keeps yielding tautologies or same-reason refutations, stop adding lemmas by
momentum and run the level audit in
[../mathematical-theory-design/references/level-audit.md](../mathematical-theory-design/references/level-audit.md). The
question may be phrased on a shadow rather than on the exact object. If the audit fails, route to
`mathematical-theory-design` or `mathematical-conjecture-design`, not to more proof factoring.

If you cannot say what subclaims would make the theorem routine, you do not yet understand the proof architecture. Step
back before drafting the main proof.

### 3. Choose the right block

Use:

- **Theorem** for a main result
- **Lemma** for a reusable step whose main job is to support later proofs
- **Proposition** for a useful local result that is not the headline theorem
- **Corollary** for an immediate consequence
- **Definition** for exact introduction of a notion
- **Example** for an honest model or test case
- **Remark** for orientation, comparison, warning, or limitation that is not itself part of the proof

### 4. Choose the proof pattern

Pick the simplest honest pattern that matches the logical form of the claim. Use
[references/proof-patterns.md](./references/proof-patterns.md) when the structure is not obvious.

### 5. Give a strategy sentence when the proof is long

Add one or two sentences before the proof, or at the start of it, when the reader needs orientation:

- name the governing idea
- announce the number of steps or cases
- say where existence and uniqueness are separated

Do not bloat short proofs with fake roadmaps.

### 6. Write the proof as a sequence of justified moves

Make every sentence do one of these jobs:

- state the current subgoal
- invoke a hypothesis, definition, earlier result, or standard theorem
- perform a controlled calculation or diagram check
- close a case or the whole proof

Displayed or stand-alone equations belong inside the prose. Punctuate them. Explain why each one is there.

Wrap exact mathematical strings in backticks whenever formatting could disturb them. This applies especially to:

- inline formulas such as `obs : B → Obs`, `L ~_𝒵 L′`, or `p̄ : E / ~_𝒵 → B`
- theorem statements containing dense symbolic text
- displayed relation lines and factorization lines
- names of equivalence classes, quotient objects, kernels, pullbacks, and universal maps when the exact glyph sequence
  matters

Prefer preserving the exact mathematical string over letting the formatter reinterpret it as ordinary prose.

### 7. Revise for checkability

Before finishing, check:

- every symbol was defined before use
- every hypothesis is used at the point it matters
- every case split is exhaustive
- every existential witness is actually constructed or justified
- every uniqueness claim states the comparison species
- every “clearly”, “obviously”, or “by inspection” can survive hostile reading

## Markdown Block Pattern

Use a plain, checkable structure like:

```md
**Lemma.** Let `R` be a commutative ring and let `I, J ⊆ R` be ideals. If `I + J = R`, then `I ∩ J = IJ`.

**Proof.** The inclusion `IJ ⊆ I ∩ J` is immediate because `IJ ⊆ I` and `IJ ⊆ J`. For the reverse inclusion, choose `a ∈ I` and `b ∈ J` with `a + b = 1`. If `x ∈ I ∩ J`, then

`x = x(a + b) = xa + xb`.

Here `xa ∈ IJ` because `x ∈ J` and `a ∈ I`, while `xb ∈ IJ` because `x ∈ I` and `b ∈ J`. Thus `x ∈ IJ`, so `I ∩ J = IJ`.
```

Adjust the label and surrounding exposition to fit the task. Keep theorem statements self-contained enough that a reader
can cite them without rereading the proof.

## Longer Proofs

A theorem and its proof are a deep module. The statement is the interface; the proof is the implementation. A lemma is a
function that hides one source of difficulty. The same disciplines apply: **depth ratio** (a long-proof, short-statement
lemma is deep); **cost is the interface** (every lemma you state is paid for at every citation, every reread);
**classitis** applied to lemmas — too many shallow lemmas, each with little hidden behind it, is worse than one bigger
lemma; **complecting** — a proof block that braids unrelated steps (case analysis, side-condition discharge, algebraic
manipulation) is complected, and structured tactics (`have`, `suffices`, `calc` in Lean) decomplect them. See
[`../deep-module-design/SKILL.md`](../deep-module-design/SKILL.md) for the underlying vocabulary; the discipline carries
over wholesale.

For long arguments, decide the architecture before you draft the top-level proof.

- factor aggressively, but not mechanically
- start with a rapid prototype and dependency sketch, not a direct prose attack on the theorem
- do not attack the main theorem directly when milestone propositions or local lemmas would make it routine
- split existence and uniqueness
- name intermediate claims when they are reused
- use “Step 1”, “Step 2”, or short claim labels when they genuinely reduce load
- isolate technical reductions in lemmas instead of burying them mid-proof
- use lemmas to isolate technical work that the reader should be able to forget once a milestone result is proved
- let each lemma remove one source of difficulty; avoid lemmas that mix unrelated jobs
- if the proof architecture is unclear, work a simpler model or special case before committing to a decomposition
- promote a lemma to a proposition, theorem, or its own section when it becomes a conceptual turning point or its proof
  has independent weight
- merge technical lemmas that are only useful together instead of forcing the reader to remember an artificial
  intermediate statement
- keep one-use lemmas close to the place where they are used
- expose the dependency shape early when the argument is very large: milestone results first, technical details later or
  in an appendix
- make the final theorem proof mostly an assembly proof once the enabling lemmas are available
- keep exposition adjacent to the formal core, but do not mix motivation with justification

If prototyping and decomposing a long proof into milestones, lemmas, and local technical steps does not make the
argument feel more natural, the problem may be the statement or definitions rather than presentation. In that case,
switch to `mathematical-theory-design` and keep going there unless a genuinely external blocker appears.

## Lemmas as Interfaces (Tao, Lamport, Leron)

The literature gives two distinct arguments for the same discipline. Keep them distinct: they answer different questions
and apply at different points.

### The Tao argument: information hiding for the reader

Tao's canonical rule, from "Create Lemmas (and don't be afraid to invent new ones)":

> One should write the statement of a lemma in a way that makes it easy to _use_, rather than easy to _prove_.

This is "the cost is the interface, not the implementation" applied to lemmas: every lemma is paid for at every
citation, every reread; its _statement_ is its interface, and the cost of that interface is paid by every later argument
that has to invoke it. The corollary is the better-together-or-apart rule, also Tao:

> If you have a pair of technical lemmas, neither of which is of much interest in its own right, but only become useful
> when used together, then they should be unified into a single lemma.

That is the proof analogue of `deep-module-design`'s combine-when- information-is-shared,
separate-when-concerns-vary-independently.

### The Leron argument: comprehensibility

Leron's "Structuring Mathematical Proofs" (_American Mathematical Monthly_ 90:3, 1983) advocates arranging a proof in
_levels_, "to increase the comprehensibility of mathematical presentations while retaining their rigor." The reader can
stop at any level and have a coherent summary. The practical test — the **Leron-test**: read the proof at speed,
skipping subclaim bodies. Does it still read as mathematics?

### The Lamport argument: error prevention

Lamport explicitly distinguishes himself from Leron (Lamport, _How to Write a Proof_, 1993, §1): Leron aimed at
_communication_; Lamport aims at _correctness_. The hierarchical method forces _statement-first_ discipline — every step
is a named claim plus its own proof, and the proof can be hidden until expanded. Lamport's empirical claim, working with
Abadi: "almost every one had serious mistakes, though the theorems were correct." His writing rule (1993, §4.2):

> Expand the proof until the lowest level statements are obvious, and then continue for one more level.

His 2012 sequel, _How to Write a 21st Century Proof_, adds a warning that lands particularly hard for an LLM agent:

> Your natural desire to confirm what you already believe to be true will cause you to miss gaps.

This is the load-bearing argument for an agent: the formal proof closing is not evidence the proof is correct; the agent
has sharper confirmation bias than a human mathematician, because closing the goal is its training signal.

### Why all three matter

- Tao keeps each lemma's _interface_ reusable; this resists the agent bias toward over-specific lemma signatures.
- Leron's level test catches the prose-blob default.
- Lamport's confirmation-bias warning explains why "the argument closed" is not the finish line.

The existing `references/proof-architecture.md` workflow (rapid-prototype, milestone propositions, dependency order) is
the _operational form_ of all three arguments. This section names _why_ that workflow works (Tao, Leron) and _why an
agent should not skip it_ (Lamport).

For the literature pointers, primary-source quotes, and the deep-module-vocabulary mapping table, see
[`references/structured-proofs.md`](./references/structured-proofs.md). For Lean-tactic-mode realizations of Lamport's
primitives (`SUFFICES` ↔ `suffices`, `PICK` ↔ `obtain`, `CASE` ↔ `rcases`, etc.), load `translating-proofs-to-lean4`.

## Defaults to Resist (proof edition)

You are an LLM agent. The discipline above is what proof writing should look like; this section is what you do _instead_
unless you stop yourself.

- **Linear prose blob.** You write the proof as one paragraph because that compiles in your head. _Counter:_ if the
  argument has more than three substantive moves, decompose into named subclaims first; fill bodies after.
- **Premature lemma extraction.** You factor every two-line argument into a lemma "for modularity." _Counter:_ lemmas
  are paid for at every citation; if a lemma is used once and its body is shorter than its statement, inline it.
- **Lemma-itis.** A forest of `aux`, `helper`, `step` lemmas, each shallow. _Counter:_ if a lemma can't be described in
  one meaningful sentence, you've over-decomposed; merge per Tao's unify-when-only-useful-together rule.
- **Reflexive generality.** Stating a lemma for `α : Type*` with multiple typeclass constraints when only one type is
  used. _Counter:_ state at the type that is used; generalise when a real second caller arrives. Tao's "easy to use, not
  easy to prove" test — the lemma's _callers_ dictate the generality, not the proof's convenience.
- **Naming amnesia.** `aux1`, `helper2`, `step`. _Counter:_ the lemma's name is part of its interface. Pay it.
- **No statement-first.** Jumping into the proof body without writing the outline as named claims (Lamport's
  discipline). _Counter:_ write the outline first; the elaborator, the type checker, or paper-and-pencil unification
  will validate the skeleton before you commit body detail.
- **Stop-when-it-compiles (proof edition).** The argument closes formally, so you commit. _Counter:_ run the Leron-test
  — read the proof at speed; does it still read as mathematics? And remember Lamport: confirmation bias makes a closed
  proof feel more reliable than it is.
- **Skipping the second outline.** First decomposition that closes the theorem is the one you ship. _Counter:_
  Ousterhout's "design it twice" (ch 11) applies, and for proofs it means two _substantively different_ proof strategies
  — induction on a different parameter, direct vs by contradiction, reduction to a known theorem vs from-scratch,
  different lemma decomposition — not two phrasings of the same plan. The point is the comparison: you learn what the
  proof's actual difficulty is, and the better strategy often shows up only by contrast. The cost is real (Ousterhout:
  an hour or two for a small module — the proof analogue is similar) and pays back because the first idea on a
  non-trivial theorem is rarely the right one.

## Before Declaring Done (proof edition)

Run this checklist _before_ you say the proof is ready:

- [ ] Every lemma has a citation site (or a one-sentence comment explaining why a one-shot lemma earns its name).
- [ ] No `aux` / `helper` / `step` placeholder names in the final draft.
- [ ] Every lemma's statement reads sentence-cleanly. Tao's "easy to use" test: would a caller want to invoke the lemma
    in this form?
- [ ] The top-level proof reads as assembly, not as a fresh argument.
- [ ] Every internal `have` block (or step in a Lamport-style hierarchy) has either a comment justifying it or a name
    suggestive enough that no comment is needed.
- [ ] Leron-test passes: reading the proof at speed (skipping subclaim bodies) gives a coherent sketch.
- [ ] Lamport-test passes: every assumption is used at the point it matters, every case split is exhaustive on the right
    object, every existential witness is constructed.

## Category-Theoretic Method

Category theory here is a proof toolkit, not a required language. When the problem is categorical or becomes clearer
categorically:

- prefer universal properties to construction-level element chasing
- prove uniqueness up to unique isomorphism by composing the maps forced by the universal property
- reduce representability questions and object comparisons with Yoneda-style reasoning when that shortens the proof
- check naturality squarewise and pointwise, not by waving at “functoriality”
- transport statements across an adjunction only when you can say exactly what datum is being moved
- distinguish equality, isomorphism, equivalence, and mere correspondence

Read [references/category-theoretic-techniques.md](./references/category-theoretic-techniques.md) for the reusable
patterns.

## Boundary

- Use [../mathematical-conjecture-design/SKILL.md](../mathematical-conjecture-design/SKILL.md) for line-level `goal.md`
  and stable `proposal.md`. Theorem notes, `rapid-prototype.md`, `proof-architecture.md`, and theorem workspaces are not
  the same kind of document.
- Use `mathematical-theory-design` when the definitions, theorem statement, or universal-property level are still being
  designed.
- Use `mathematical-proof-review` when the job is adversarial review of an existing proof or proof-heavy note.
- Use `technical-writing` for broad exposition that is not primarily about writing or revising a formal argument.
