# Finiteness, unramified, flat, étale

## What this file is about

Wrap a rubber band twice around your wrist. Every point on your wrist now has two points of band sitting above it. That
is a covering map: a top space lying neatly over a bottom space, finitely many sheets, the sheets locally
indistinguishable from stacked copies of the bottom. Covering maps are one of the oldest pictures in topology, and they
are how the subject sees symmetry.

What would it take for an algebraic map between two spaces — a map given by polynomial formulas, not by stretching
rubber — to deserve the same name? Three things, separated here for the first time. The fibres have to be finite. The
fibres have to be clean, with no infinitesimal slack hidden inside them. And the family of fibres has to vary smoothly
as you move on the base, without algebraic jumps. This file names the three conditions in turn and gives the combined
notion its name. That combined notion is the central character of the entire book.

A topological covering map `p : E → B` is one whose fibers are discrete and whose local picture is a stack of copies of
`B` glued homeomorphically; the canonical example is `S¹ → S¹, z ↦ zⁿ`. The algebraic analogue must say the same three
things in ring-theoretic language. The fibers must be finite. They must be discrete, with no infinitesimal slack inside
the fiber. And as we move on the base, the family must vary without algebraic jumps. Each clause will turn into a
precise algebraic condition; their conjunction is what we will call **étale**.

The four words in the title name the conditions in order of strictness: quasi-finite ⇒ unramified ⇒ étale, with finite
étale and open immersion as further specializations. The trichotomy from earlier files — split, extension, ramified —
sorts into this hierarchy: the first two cases are étale, the third is the obstruction.

From here on, all schemes are locally noetherian, matching the source's standing assumption.

A preview of the hierarchy this file will build. Each step adds one clause to the previous condition:

```text
quasi-finite       — finite fibers
    ⟸ unramified  — also no nilpotent slack in the fiber, residue extensions separable
    ⟸ étale       — also flat: family varies without algebraic jumps
```

with two further specializations of étale:

```text
finite étale       — étale + globally finite
open immersion     — étale + radicial: a local isomorphism
```

The synonyms **unramified** and **net** mean the same thing; we use both. The full diagram with local tests is at the
end of this file.

## Quasi-finite: finite fibers, locally

We start with the weakest of the four conditions: that the fibers be finite as sets. This controls only the first of the
three clauses in the topological picture, and it leaves both the infinitesimal structure of the fiber and its variation
along the base untouched.

A morphism `f : X → Y` is **quasi-finite at `x`** if `x` is an isolated point of its fiber `f⁻¹(f(x))`. Equivalently,
the fiber near `x` is a finite set of points.

The algebraic version comes in three forms. Each measures the same idea — the fiber is small — from a different angle:
as a `k`-algebra, as a local ring, and as an object after completion. Let `A → B` be a local homomorphism of noetherian
local rings and write `𝔪 = 𝔪_A`.

The first form measures the fiber directly. The fiber `B/𝔪B`, viewed as a `k`-algebra over `k = A/𝔪`, should have finite
dimension. This is what "small fiber" means at face value.

The second form measures the same thing through the local geometry of `B`. Asking that `𝔪B` be an ideal of definition
forces `B/𝔪B` to be artinian, and since `B` is local, local artinian; the residue extension then has to be finite to
keep the fiber finite-dimensional.

The third form trades local data for global data. Completion at the maximal ideal turns the local picture at `x` into a
finitely generated module over a complete local ring — a more rigid object on which finiteness becomes a clean global
condition. After completion, quasi-finite becomes finite.

The following are equivalent. We take (1) as the primary definition; (2) and (3) follow by short arguments collected as
the appendix black-box row [`quasi-finite-equivalences`](appendix-black-boxes.md#quasi-finite-equivalences).

1. `B / 𝔪 B` is finite-dimensional over `k = A / 𝔪`. _(primary definition: the fiber as a `k`-algebra is
    finite-dimensional)_
1. `𝔪 B` is an ideal of definition of `B` — that is, some power of the maximal ideal of `B` lies in `𝔪 B` — and
    `κ(B) / κ(A)` is a finite field extension. _(equivalence with (1): the fiber `B/𝔪B` is artinian iff `𝔪B` is an
    ideal of definition; an artinian local ring is finite-dimensional over its residue field iff the residue extension
    is finite.)_
1. The completion `B̂` is finite as an `Â`-module. _(equivalence with (1): completion turns a quasi-finite local algebra
    into a finite one; this is the version that lets one reduce statements about quasi-finite morphisms to statements
    about finite morphisms after passing to completions.)_

When these hold, we say `B` is **quasi-finite over `A`**. A morphism `f : X → Y` is **quasi-finite** if `𝒪_x` is
quasi-finite over `𝒪_{f(x)}` for every `x ∈ X`.

Quasi-finite is **not** the same as finite. Finite means `B` is a finitely generated `A`-module, a **global** condition.
Quasi-finite is **local**: it controls behavior near a single point.

For the running example `Spec ℤ[t]/(t² − 2) → Spec ℤ`, every fiber has at most two points, so the morphism is
quasi-finite. By contrast, `Spec ℤ[t] → Spec ℤ` (the affine line over `ℤ`) is **not** quasi-finite anywhere: each fiber
is `Spec 𝔽_p[t]`, an entire affine line.

## Unramified: discrete fibers with separable residue extensions

Quasi-finite gave us the first clause of the topological picture: the fiber is finite as a set. It said nothing about
the second clause, that the fiber be discrete. Closing that gap is the job of this section. The fiber should not only be
a finite set of points; it should also have **no infinitesimal slack**, and the residue field extension at each point
should be **separable**.

This is the condition called **unramified**, or in Grothendieck's French, **net**. The two words mean the same thing.
The English "unramified" tracks the algebraic-number-theory origin (an extension of number rings is unramified at a
prime if the prime does not divide the discriminant). The French "net" tracks the diagonal-criterion picture (the
diagonal is "neat" — locally an open immersion).

Grothendieck's preference, recorded in a footnote of EGA IV 17.3.1, is worth keeping for the record:

> The words "net" and "formally net" seem more preferable to the terminology used in "unramified" (resp. "formally
> unramified") and will be used almost exclusively in Chapter V.

We follow the source of Exposé I, which uses both, until the eye gets used to either.

### Equivalent forms

For `f : X → Y` of finite type and `x ∈ X`, the following are equivalent.

1. The fiber algebra `𝒪_x / 𝔪_y · 𝒪_x` is a finite separable extension of `κ(y)`.
1. The sheaf `Ω¹_{X/Y}` vanishes at `x`.
1. The diagonal `Δ_{X/Y}` is an open immersion in a neighborhood of `Δ(x)`.
1. For any auxiliary morphism `Z → Y`, the canonical homomorphism `f*(Ω¹_{Y/Z}) → Ω¹_{X/Z}` is surjective at `x`.

The equivalence of (1)–(3) is proposition I.3.1 of the source, restated and proved in file 10. Form (4) is an immediate
consequence of (2) plus the relative cotangent sequence (file 03); it is the form Grothendieck uses in EGA IV §17.2.2 as
a permanent-under-composition criterion. Each form says "no infinitesimal slack in the fiber" from a different angle.

Form (i) is the **fiber criterion**: at the residue-field level, the fiber is a finite separable field extension. No
nilpotents in the fiber.

Form (ii) is the **differential criterion**: the sheaf of relative differentials, which we built in file 03 to detect
first-order infinitesimal differences, vanishes near `x`. No first-order direction in the fiber.

Form (iii) is the **diagonal criterion**: the diagonal `Δ_{X/Y} : X → X ×_Y X` — the geometric witness of "two points
equal over the base" — is locally an open immersion. Two points of `X` over `Y` that are "close" are already equal.

Form (iv) is the **relative cotangent criterion**. It is the form that lets one prove "composition of unramified is
unramified" without going through fibers each time.

Pick the form that suits the question at hand. We use (i) for fiber-level reasoning, (ii) for differential-level
reasoning, (iii) for graph-style arguments (most notably corollary I.3.4 of the source, which gives the graph of a
`Y`-morphism into an unramified scheme as an open immersion), and (iv) for the permanence sorites.

### Algebraic definition

For a local homomorphism `A → B` of noetherian local rings, `B` is **unramified** (or **net**) over `A` if

- `𝔪_A · B = 𝔪_B`, and
- `κ(B) / κ(A)` is a finite separable extension.

The first condition says the maximal ideal of `B` is generated by the image of the maximal ideal of `A`. The second
controls the residue extension.

Net implies quasi-finite. Here is the explicit argument: net forces `𝔪_A · B = 𝔪_B`, so the fiber algebra `B/𝔪_A B`
equals `B/𝔪_B = κ(B)`, a field. Net also forces `κ(B)/κ(A)` finite separable, hence in particular finite, hence
finite-dimensional over `k = κ(A)`. So `B/𝔪_A B` is a finite-dimensional `k`-algebra — condition (1) of
quasi-finiteness.

The converse fails. The [fat point](glossary.md#fat-point) `Spec k[ε]/(ε²) → Spec k` is quasi-finite (one point in the
fiber) but not unramified (the fiber has the nilpotent `ε`). This is the model failure: the fiber is a single point, but
it has algebraic flesh on its bones.

### Examples

**Finite separable field extension.** `k → k'` finite separable. `𝔪_k = 0`, `𝔪_{k'} = 0`, so `𝔪_k · k' = 0 = 𝔪_{k'}`.
The residue extension is `k'/k`, separable by hypothesis. So `k'/k` is unramified. ✓

**Open immersion.** `U → X`. The local ring of any `u ∈ U` equals the local ring at the image. Both maximal ideals
match, residue extension is the identity. Trivially unramified. ✓

**The [fat point](glossary.md#fat-point).** `Spec k[ε]/(ε²) → Spec k`. Here `𝔪_A = 0`, `𝔪_B = (ε) ≠ 0`, so
`𝔪_A · B ≠ 𝔪_B`. **Not unramified.** ✗

**Inseparable extension.** `𝔽_p(s^{1/p}) / 𝔽_p(s)`. Finite, but not separable. So **not unramified**. ✗ The differential
`d(s^{1/p})` is non-zero in `Ω¹` because the relation `(s^{1/p})ᵖ = s` differentiates to `0 = ds`, an empty constraint,
leaving `d(s^{1/p})` free.

### The different ideal

The annihilator `𝔡_{X/Y} := Ann(Ω¹_{X/Y})` is the **different ideal** of `X/Y`. It cuts out, set-theoretically, the
locus where `f` is **ramified** (not unramified).

The complement of this closed subscheme is the open locus of unramifiedness. The proof that this locus is open is
corollary I.3.3 of the source: each of the three equivalent forms is open in `x`, so their conjunction is too.

The word "different" comes from algebraic number theory. For an extension of number fields `L/K`, the **different
ideal** in `𝒪_L` in the classical sense agrees with our `𝔡` for the morphism `Spec 𝒪_L → Spec 𝒪_K`. Its norm to `K` is
the **discriminant**, which we will see again under flatness.

### The running example, rephrased

For our `B = ℤ[t]/(t² − 2)` over `ℤ`, file 03 computed `Ω¹_{B/A} = B / 2t · B`, and showed this vanishes at every prime
except `(2)`. So the morphism is **unramified at every prime except `(2)`**, and **ramified at `(2)`**. The trichotomy
from file 02 now has a name for two of its three cases:

```text
p = 7  →  split        — unramified
p = 5  →  extension    — unramified
p = 2  →  ramified     — not unramified
```

The split and extension cases are unified under "unramified." The distinction between them — one or two points in the
fiber — is the content of the **discriminant** at the étale level, which we get to below.

## Flat: no algebraic jumps as the base moves

We have controlled the fiber at a single point. We have not yet controlled how the fibers vary as we move on the base.
That is what flatness does.

The intuitive picture: a family `Spec B → Spec A` is "flat" if the fibers vary without sudden algebraic jumps. No fiber
suddenly appears or disappears or changes dimension in a way the rest of the family does not anticipate.

Algebraically: `B` is **flat over `A`** when tensoring with `B` preserves injections. That is, if `M' ↪ M` is an
injection of `A`-modules, then `M' ⊗_A B ↪ M ⊗_A B` is again an injection.

### What flatness buys you

The definition is austere; the payoff is geometric. A flat family is one without algebraic surprises. Concretely:

- **No fibre is special by accident.** If the family is flat, every fibre carries the same kind of algebraic information
    that the generic fibre does. A flat family is not allowed to grow a hidden component over a closed point, or to shed
    one.
- **Multiplication by a base regular element stays injective.** This is the literal meaning of "preserves injections":
    if `a ∈ A` is not a zero divisor, then `a` is not a zero divisor in `B` either. In families of curves, this is
    exactly the absence of the embedded-point pathology.
- **Dimensions move continuously.** For finite-type families, the dimension of the fibre is locally constant in the flat
    case (with a precise statement that we will not need verbatim).

The full operational toolkit splits into facts we prove here and facts we take from Exposé IV of EGA. We make the split
visible. The first three facts have short proofs we work in the next subsection; the last two depend on the local
flatness criterion and on faithfully flat descent, machinery that requires its own development. Exposé IV of SGA 1
(files 24–27 in this gentle pass) opens those boxes; the source of Exposé I cites them, and we follow.

**Operational facts proved here.**

1. Open immersions are flat.
1. Composition of flat morphisms is flat.
1. Localization is flat.

**Operational facts cited.**

1. Base change of a flat morphism is flat. (Standard tensor-product exchange; see
    [`flatness-sorites`](appendix-black-boxes.md#flatness-sorites).)
1. The locus where a finite-type morphism is flat is open. (EGA IV, §11; the proof uses the local flatness criterion.)
1. **Faithfully flat descent**: if `A → B` is faithfully flat, properties of `A` can often be tested on `B`. (Faithfully
    flat = flat plus injective on every nonzero `A`-module after tensoring up. The descent machinery is the subject of
    Exposé VIII; files 40–43 in this gentle pass.)

Each cited fact has an entry in the appendix with statement, role, and source.

### When flatness is easy to check

Two cases are immediate.

**Localization is flat.** `A → A[1/f]` and `A → A_𝔭` are flat. Here is the proof in one paragraph. By construction
`A[1/f]` is the colimit of the directed system `A →^f A →^f A → ⋯` along multiplication by `f`. Tensoring commutes with
colimits, so for any `A`-module `M`, the localization `M ⊗_A A[1/f] = M[1/f]` is the same colimit applied to `M`. An
injection `M' ↪ M` becomes an injection at every stage of the system (multiplication by `f` is preserved), and filtered
colimits in the category of `A`-modules are exact. So `M'[1/f] ↪ M[1/f]`, which is the flatness condition. The
localization `A_𝔭 = (A ∖ 𝔭)^{-1} A` is the same argument over the multiplicative set `A ∖ 𝔭`.

**Free implies flat.** If `B` is free as an `A`-module, then `B` is flat over `A`. The reason: tensoring with a free
module is isomorphism-on-each-summand, which preserves injections.

**Critical case.** For a monic polynomial `F ∈ A[t]`, the algebra `B = A[t]/F` is **free of rank `deg F`** as an
`A`-module, with basis `1, t, t², …, t^{deg F − 1}`. So `B` is flat over `A`. This is **why** the standard étale form
`A → A[t]/F` works out algebraically: monic polynomial gives free, free gives flat, flat plus unramified gives étale.

### Where flatness fails

The clean test for failure: tensor an injection with the candidate algebra and look for injectivity to break.

`ℤ → ℤ/p` is **not** flat. Witness: tensor the injection `ℤ →^p ℤ` (multiplication by `p`) with `ℤ/p`. The result is the
zero map `ℤ/p → ℤ/p`, which is not injective. So `ℤ → ℤ/p` does not preserve all injections.

Geometrically, the closed immersion `Spec 𝔽_p → Spec ℤ` is not flat. The base "loses" everything outside `(p)`.

`ℤ → ℤ[t]/(2t − 1)` is also not flat. Note `2t − 1` is not monic. The localization `ℤ[t]/(2t − 1) ≃ ℤ[1/2]` inverts `2`,
killing the prime `(2)` from `ℤ`. Closed immersions and most non-monic-relation algebras are problematic.

### A common misreading: flat ≠ "constant fiber size"

It is tempting to say "flat means all fibers have the same size." This is false in literal generality. The careful
statement:

> **For a [finite locally free](glossary.md#finite-locally-free) morphism, the rank function `y ↦ rk(B(y))` is locally
> constant on `Y`.**

A morphism is **finite locally free** when the corresponding sheaf of `𝒪_Y`-algebras is locally a free `𝒪_Y`-module of
constant rank. Equivalent characterization: finite + flat + finitely presented. The equivalence relies on the
[local flatness criterion](appendix-black-boxes.md#local-flatness-criterion) (over a local noetherian ring, finite +
flat = free), so that a finite flat algebra is free on each stalk and hence locally free in a neighborhood. In this
case, the rank of the fiber is locally constant — the closest honest version of "constant fiber size."

For more general flat morphisms, the dimensions of fibers can vary, but flat prevents specific kinds of pathological
jumping. We will not need the precise statements; we use flatness through the five operational facts above.

## Étale: flat plus unramified

Unramified gave us a discrete fiber with separable residue extensions; flat ruled out algebraic jumps along the base.
The two clauses match the two remaining requirements of the topological covering picture, and combining them gives the
algebraic notion that closes it.

A morphism `f : X → Y` of finite type is **étale at `x`** if it is **flat at `x`** and **unramified at `x`**. It is
**étale** if it is so at every point.

For a local homomorphism `A → B` (with `B` essentially of finite type over `A`), `B` is **étale over `A`** if `B` is
**flat** and **unramified** over `A`.

Both halves earn their keep.

Without flatness, we cannot make sense of "the fibers vary continuously." The closed immersion `Spec 𝔽_p → Spec ℤ` is
unramified (the residue extension `𝔽_p / 𝔽_p` is trivial, `𝔪_ℤ · 𝔽_p = (p) · 𝔽_p = 0 = 𝔪_𝔽_p`) but not flat — `𝔽_p` has
`p`-torsion as a `ℤ`-module. The fiber jumps abruptly: empty over every prime other than `(p)`.

Without unramifiedness, we cannot rule out hidden directions in the fiber. The [fat point](glossary.md#fat-point)
`Spec k[ε]/(ε²) → Spec k` is flat (the source is a free `k`-module of rank `2`) but not unramified; the nilpotent `ε` is
a first-order direction in the unique fiber.

The conjunction is what we want. With both, the morphism behaves, locally, exactly like a covering map: a flat family of
separable field extensions.

### What "étale" buys

Two reasons étale is the right notion.

**Topological analogy.** Base-change an étale morphism to an algebraically closed field at a point. The fiber becomes a
finite product `k × k × … × k` of copies of the field — literally a finite discrete set of points. So étale = local
covering, in the algebraic sense.

**Rigidity.** Étale morphisms have a unique-lifting property across nilpotent thickenings: maps into them factor
uniquely through the underlying reduced scheme. This is the algebraic version of "covering maps lift uniquely along
homotopies." It is the topic of file 05.

### Examples revisited

**Finite separable field extension.** Étale.

**Open immersion.** Étale.

**The classical `n`-fold cover.** Take `A = k[s, s⁻¹]` and `B = k[t, t⁻¹]` with `s = tⁿ`. The map `A → B`, `s ↦ tⁿ`,
gives `Spec B → Spec A`. Compute: `B = A[t] / (tⁿ − s)`, monic, hence free of rank `n`, hence flat. Unramified iff the
formal derivative `(tⁿ − s)' = n tⁿ⁻¹` is a unit in `B`, iff `n` is a unit in `k`. So **étale iff `n` is invertible in
`k`**.

In characteristic 0 (or characteristic `p` not dividing `n`), this is the algebraic version of `S¹ → S¹`, `z ↦ zⁿ`. In
characteristic dividing `n`, it is **not** étale: the cover has wild ramification. The classic example is `t ↦ tᵖ` in
characteristic `p`, the **Frobenius** — purely inseparable, not étale anywhere.

**The branch point at the origin.** `A = k[s]`, `B = k[t]`, `s = t²`, `char k ≠ 2`. The morphism is finite of rank `2`,
hence flat. The differential of `t² − s` with respect to `t` is `2t`, a unit on `B[1/t]` but **not at `t = 0`**. So the
morphism is étale on `Spec B \ {(t)}` and **ramified at the origin**. The origin is a branch point, in the classical
sense.

**The fat point fails again.** `k[ε]/(ε²) → k` is flat but not unramified; not étale.

### The étale locus is open

The étale locus of a morphism of finite type is open in the source. This is proposition I.4.5 of the source. It follows
immediately from the analogous facts for flat (open) and unramified (open).

So we can move freely from "étale at `x`" to "étale in a neighborhood of `x`," and the source does so silently from this
point on.

### A useful corollary, used constantly

Corollary I.4.8 of the source gives a powerful "automatic étaleness" principle.

> If `g : X → X'` is a `Y`-morphism with `X` étale over `Y` and `X'` unramified over `Y`, then `g` is étale.

The proof factors `g` through its **graph**. Recall the graph morphism

```text
Γ_g : X → X ×_Y X',    x ↦ (x, g(x)),
```

induced by the pair `(id_X, g)` and the universal property of `X ×_Y X'`. By construction `g = pr_{X'} ∘ Γ_g`. Two facts
about this factorization:

- The projection `pr_{X'} : X ×_Y X' → X'` is the base change of `X → Y` along `X' → Y`, hence étale (étale is preserved
    by base change).
- The graph `Γ_g : X → X ×_Y X'` is the base change of the diagonal `Δ_{X'/Y} : X' → X' ×_Y X'` along the morphism
    `(id_X, g) : X → X' ×_Y X'`. Since `X'/Y` is unramified, the diagonal `Δ_{X'/Y}` is an open immersion (form (iii)
    above), and open immersions are stable under base change, so `Γ_g` is an open immersion.

Open immersion is étale, étale composed with étale is étale, so `g` is étale.

This is the **graph trick**: factor a `Y`-morphism through its graph in a fibered product, identify the graph with a
base change of the diagonal of the target, and read off properties of the graph from properties of the diagonal. We will
use it again at several points downstream. Whenever you see "étale" appear on `g` for free, this corollary is usually
the reason.

## Finite étale coverings: the algebraic covering map

We finish with the global notion.

A **finite étale covering** of `Y` is a `Y`-scheme `X` that is **finite** over `Y` and **étale** over `Y`. Equivalently,
finite

- flat + unramified.

A **net covering** is finite + unramified, but not necessarily flat. (This is the source's term; we use it only to state
a few results.)

### Algebraic translation

A finite morphism `X → Y` corresponds, by the equivalence between finite morphisms and coherent sheaves of algebras, to
a **coherent sheaf `𝓑` of `𝒪_Y`-algebras**. (Coherent here means: locally finitely generated as `𝒪_Y`-module.)

The further conditions for étale are:

- `𝓑` is **locally free** as `𝒪_Y`-module. This is what "flat + finite" gives — in this setting, flat plus finitely
    presented forces locally free.
- For every `y ∈ Y`, the fiber `𝓑(y) = 𝓑_y ⊗_{𝒪_y} κ(y)` is a **separable algebra over `κ(y)`** — that is, a finite
    product of finite separable field extensions of `κ(y)`.

Over an algebraically closed `κ(y)`, the second condition forces the fiber to be `κ(y)^n`, a product of copies of the
residue field — literally `n` discrete points, the model of a covering of degree `n`.

### The trivial cover

For any scheme `Y`, the disjoint union `Y ⨿ Y ⨿ … ⨿ Y` of `n` copies of `Y` is a finite étale covering of degree `n`.
The corresponding sheaf of algebras is `𝒪_Y^n` with componentwise multiplication. Fibers are `κ(y)^n`. This is the
"totally split" covering.

### The discriminant criterion

A finite locally free sheaf of algebras `𝓑` over `𝒪_Y` carries a **trace** map: for `b ∈ 𝓑_y`, multiplication by `b` is
an `𝒪_y`-linear endomorphism of the free `𝒪_y`-module `𝓑_y`, with a trace `tr(b) ∈ 𝒪_y`.

The **trace pairing** is

```text
β : 𝓑 × 𝓑 → 𝒪_Y,    β(b, b') = tr(bb').
```

Pick a local basis `b₁, …, b_n` of `𝓑` as `𝒪_Y`-module. The matrix `(β(b_i, b_j))` has entries in `𝒪_Y`, and its
determinant is the **discriminant**:

```text
disc(𝓑/𝒪_Y) := det(tr(b_i b_j)) ∈ 𝒪_Y.
```

Different bases give discriminants differing by a unit, so the discriminant generates a well-defined ideal.

> **A finite locally free `𝓑` over `𝒪_Y` is étale iff its discriminant ideal is the unit ideal.**

This is proposition I.4.10 of the source. It is the operational test for étaleness in the finite locally free setting.

The discriminant and the [different ideal](glossary.md#different-ideal) are related: for a finite étale covering,
`disc(𝓑/𝒪_Y) = N(𝔡_{X/Y})`, the **norm** of the different. The "different" ideal lives on the source `X` and measures
local ramification; the "discriminant" ideal lives on the target `Y` and is the image of the different under the norm
map. Either ideal cuts out the ramified locus — seen from `X` for the different, from `Y` for the discriminant.

### Computing the discriminant of `ℤ[√2] / ℤ`

`B = ℤ[t]/(t² − 2)` as a free `ℤ`-module has basis `1, t`. The trace pairing matrix is

```text
[[ tr(1·1), tr(1·t) ],     [[ 2, 0 ],
 [ tr(t·1), tr(t·t) ]]  =   [ 0, 4 ]].
```

Two preparatory facts about the trace. _(i)_ For a rank-`n` free `A`-module, the trace of the identity is `n`, and more
generally `tr(c · id) = n · c` for any scalar `c ∈ A`. _(ii)_ The trace of "multiplication by `b`" for `b` an element of
the algebra is the trace of the linear map `b·` written in any chosen basis.

Computing each entry: `tr(1) = 2` (the trace of the identity on a rank-2 module). `tr(t) = 0` (the matrix of `t·` in
basis `1, t` is `[[0, 2], [1, 0]]`, with trace 0). `tr(t²) = tr(2 · id) = 2 · 2 = 4`.

The determinant is `8`. So the discriminant ideal is `(8) = (2³)`, supported on the prime `(2)`. The morphism is étale
on the open complement `Spec ℤ[1/2]`, ramified at `(2)`. This matches what we have computed three different ways already
(fibers, differentials, discriminants).

> **Three ways of saying the same thing:** the fiber has nilpotents, `Ω¹` does not vanish, the discriminant has positive
> valuation.

All three are properties of the same ramified prime.

## The four-class hierarchy in one picture

```text
quasi-finite ⟸ unramified (net) ⟸ étale = flat + unramified
                                          ⟸ finite étale = finite + étale
                                          ⟸ open immersion
```

| Property             | Local test                                                                                                                             |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **quasi-finite**     | `B/𝔪B` is finite-dimensional over `k`                                                                                                  |
| **unramified** (net) | `Ω¹_{X/Y} = 0` near the point; equivalently, the fiber has no nilpotents and the residue extension is finite separable                 |
| **flat**             | tensoring with `B` preserves injections (black box)                                                                                    |
| **étale**            | flat **and** unramified                                                                                                                |
| **finite étale**     | finite **and** étale; equivalently, locally free with separable fibers; equivalently, finite locally free with invertible discriminant |
| **open immersion**   | locally `Spec(A[1/f]) → Spec A`                                                                                                        |

Each property is preserved by composition and base change. Each cuts out an open locus on the source. The strongest,
**open immersion**, is the simplest model of "local isomorphism" in algebraic geometry.

## The running example, summarized

The morphism `Spec ℤ[t]/(t² − 2) → Spec ℤ` has been recomputed in every preparation file. Here the five different lenses
are collected on one page.

| Lens                        | `p = 7`            | `p = 5`           | `p = 2`              |
| --------------------------- | ------------------ | ----------------- | -------------------- |
| Fiber `𝔽_p[t]/(t² − 2)`     | `𝔽₇ × 𝔽₇`          | `𝔽_25`            | `𝔽₂[t]/(t²)`         |
| Geometric description       | split (two points) | extension         | ramified (nilpotent) |
| `Ω¹_{B/A}` at the prime     | `0` (`2t` a unit)  | `0` (`2t` a unit) | full fiber (nonzero) |
| Discriminant `(8) = (2³)`   | unit               | unit              | generates `(2³)`     |
| `n((p))` (geometric points) | `2`                | `2`               | `1`                  |
| Verdict                     | étale              | étale             | ramified             |

Where each row was computed in the preparation arc:

- fibers and the trichotomy first appear at the end of file 01;
- the geometric reframing as fibered product is at file 02;
- the `Ω¹` vanishing computation is in file 03;
- the unramified-locus verdict is the running thread of this file;
- the geometric-point count `n((p))` is in file 06.

Read the columns top to bottom: every row at `p = 7` and `p = 5` gives the same verdict (étale); every row at `p = 2`
gives the same verdict (ramified). The five lenses are equivalent ways of asking the same question.

The next file shows that **étale** behaves much more like an open immersion than its definition would suggest. Étale
morphisms are extraordinarily rigid: an étale morphism plus one extra condition (set-theoretic injectivity with purely
inseparable residue extensions) is literally an open immersion. Maps into étale schemes lift uniquely across nilpotent
thickenings of the base. Over a complete local ring, finite étale extensions are determined by the residue field.
Locally, every étale algebra is `(A[t]/F)_{(F'(t))}` for some monic `F`.

These four rigidity properties are the substance of file 05.
