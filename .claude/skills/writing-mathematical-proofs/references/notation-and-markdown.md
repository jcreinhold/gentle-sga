# Notation and Markdown

Use Markdown that stays readable in plain text and still looks like mathematics.

## Protect Math from the Formatter

Wrap mathematical text in backticks whenever exact presentation matters. Bare mathematical text is unstable under
formatting: symbols can be reflowed, relation lines can be split, and formulas can be treated as ordinary prose.

Use backticks for:

- inline formulas such as `f : X → Y`, `L ~_𝒵 L′`, `ker(p)`, `E / ~_𝒵`, or `ι : B → Obs × (M / ~_M)`
- dense symbolic theorem statements
- standalone displayed formula lines written in Markdown rather than true math blocks
- exact names of quotient classes, kernels, pullbacks, comparison maps, and equivalence relations

If a line would be damaged by reflow, prefer `` `...` `` over plain text.

## Block Layout

Prefer simple blocks:

```md
**Proposition.** Statement.

**Proof.** Argument.
```

For proofs with cases or steps:

```md
**Proof.** We argue in two cases.

**Case 1.** ...

**Case 2.** ...
```

Do not hide the theorem statement in a paragraph above the label.

## Assumptions and Notation

Put ambient assumptions before the first theorem that needs them.

Good:

```md
Assume throughout that R is a Noetherian ring.

**Lemma.** ...
```

Also good for local setup:

```md
Let `f : X → Y` be continuous. Write `Z = f⁻¹(A)`.

**Claim.** ...
```

## Unicode and Words

Use Unicode when it helps the reader scan the argument:

- `→`, `↠`, `⊂`, `⊆`, `∩`, `∪`, `∅`, `≤`, `≥`, `≅`, `≃`

Prefer words when the symbolic version becomes noisy:

- “for every”
- “there exists”
- “if and only if”
- “unique up to unique isomorphism”

Do not mix five visual conventions for the same relation in one note.

## Displayed Mathematics

Use display mode for:

- long formulas
- central identities
- commutative diagrams
- calculations that need visual separation

Keep short formulas inline when the sentence reads better that way.

When you keep formulas inline, fence them:

```md
The map `p̄ : E / ~_𝒵 → B` is well defined.
```

Punctuate displays as part of the sentence:

```md
Therefore

`f(x) = 0`,

so `x ∈ ker f`.
```

For relation definitions and factorization lines, fenced display-style lines are usually safer than bare prose:

```md
`L ~_𝒵 L′ ⟺ obs(p(L)) = obs(p(L′)) and struct(L) ~_M struct(L′).`
```

## Narrate Calculations

Introduce nontrivial displays with a short cue:

- “By exactness,”
- “Using naturality,”
- “Expanding the definition,”
- “Applying the induction hypothesis,”

Do not leave the reader to infer why a diagram or formula suddenly appeared.

## Comparison Species

Mark the relation you actually prove:

- equality `=`
- canonical isomorphism `≅`
- equivalence `≃`
- inclusion `⊆`
- factorization through `→`

If the object is defined only up to isomorphism, do not write literal equality unless the framework has already chosen a
strict representative.
