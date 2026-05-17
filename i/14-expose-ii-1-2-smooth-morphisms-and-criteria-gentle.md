# Exposé II, sections 1–2: smooth morphisms and criteria (gentle)

## What this file is about

In ordinary calculus, the cleanest kind of map between two surfaces is a submersion: at every point the map locally
looks like a flat projection, dropping some coordinates and keeping the rest. A submersion is what guarantees that the
preimage of a point is itself a smooth surface, and the dimension drops by a predictable amount. The notion runs
through every part of geometry where you want to slice an object into well-behaved families.

This file builds the algebraic version. The starting material is the notion of covering map from the earlier files,
which behaved like a submersion of zero dropped dimensions — the layers were discrete. Drop the discreteness. Allow the
fibres to be honest geometric pieces of positive dimension, but require everything else to keep behaving cleanly. The
result is the algebraic version of a submersion. Two intrinsic tests for the property follow, both saying the same
thing from different angles.

Exposé I built étale morphisms — flat plus unramified, the algebraic analogue of an unramified covering. Exposé II adds
one parameter: relative dimension. A **smooth** morphism is the algebraic analogue of a submersion, a covering "of
arbitrary positive relative dimension." The gentle reading of Exposé I (files 01–06, 10–12) already supplies every
algebraic prerequisite. Exposé II is then a short story.

The slogan that runs through it:

> **Smooth = étale modulo polynomial coordinates.** A morphism is smooth if, locally on the source, it factors through a
> relative polynomial scheme `Y[t₁, …, tₙ]` by an étale morphism. Étale is recovered as smooth of relative dimension
> `0`.

Two new running examples for the smooth story, both arithmetic:

- **`Spec ℤ[t] → Spec ℤ`** — the affine line over `ℤ`, the smallest smooth morphism of relative dimension `1`. `Ω¹` is
    the free `ℤ[t]`-module on `dt`.
- **An elliptic curve `Spec ℤ[x, y] / (y² − x³ − ax − b) → Spec ℤ`** for chosen integers `a, b` with discriminant
    `−16(4a³ + 27b²)` a unit at the primes we care about. Smoothness is detected by the Jacobian of the defining
    polynomial — the classical elliptic-curve smoothness test, which we will see is exactly the Jacobian criterion
    II.4.10.

The étale ℤ[√2] of Exposé I lives at relative dimension `0`; the two new examples live at relative dimension `1`. The
arithmetic universe is the same; only the relative dimension changes.

## II.1 Generalities

<!-- source: II.1 -->

### Setup: the relative polynomial scheme

For a prescheme `Y` and indeterminates `t₁, …, tₙ`, write

```text
Y[t₁, …, tₙ] := Y ×_{Spec ℤ} Spec ℤ[t₁, …, tₙ].
```

This is the prescheme of "polynomials in `n` variables with coefficients in `𝒪_Y`." Concretely: a `Y`-section of
`Y[t₁, …, tₙ]` is exactly an `n`-tuple of sections of `𝒪_Y` (the images of the `t_i`); base change replaces `Y` by any
`Y′` and gives `Y′[t₁, …, tₙ]`; and iterating composes polynomial-ring constructions algebraically. The morphism
`Y[t₁, …, tₙ] → Y` is finite-type, flat, and surjective.

This relative polynomial scheme is the universal "free relative dimension `n` step." Smoothness is the property of
looking, locally, like an étale cover of one of these.

### Definition

<!-- source: II.1.1 -->

**Definition II.1.1.** A morphism `f : X → Y` is **smooth at** `x ∈ X` if there exist an integer `n ≥ 0`, an open
neighborhood `U` of `x` in `X`, and an étale `Y`-morphism

```text
g : U → Y[t₁, …, tₙ].
```

The morphism `f` is **smooth** if it is smooth at every point of `X`. An algebra `B` over `A` is **smooth at a prime
`𝔭 ⊂ B`** if `Spec B` is smooth over `Spec A` at the point `𝔭`; smooth tout court means smooth at every prime. A local
homomorphism `A → B` of local rings is **smooth** if `B` is a localization of an `A`-algebra of finite type that is
smooth over `A`. (EGA IV 18.6.1 calls this latter notion _essentially smooth_ over `A`.)

### Why this is the right definition

The slogan _smooth = étale modulo polynomial coordinates_ says exactly that smoothness imposes no constraint beyond two:
that the fibers vary flatly along the base, and that, after stripping out the free polynomial directions, what remains
is étale. The étale cover `g : U → Y[t₁, …, tₙ]` provides the flat polynomial coordinates; the integer `n` is the
relative dimension at `x` (we will see this in II.1.5).

This is the algebraic counterpart of a **submersion** in differential geometry: a map of manifolds whose derivative is
surjective at every point, equivalently, a map that locally looks like the projection `ℝᵐ × ℝⁿ → ℝᵐ` from a product to
the first factor.

#### Aside (differential-geometry analogy).

_Skip this paragraph if differential topology is not part of your background; nothing later depends on it._

A submersion `M → N` of smooth manifolds is, locally, the projection `N × U → N` for some open `U ⊂ ℝⁿ`. The gentle
SGA's "étale to `Y[t₁, …, tₙ]`" is the algebraic shadow: locally on the source, the morphism factors through a free
`n`-dimensional family over the base by an étale step (the residue of "no slack"). The fibers are smooth `n`-folds in
the algebraic sense.

### Smoothness is open

<!-- source: prop:II.1.1 -->

_This result says: the locus where a morphism is smooth is open in the source._

**Proposition II.1.1.** The set of points `x ∈ X` at which `f` is smooth is open in `X`.

### Proof

Trivial from Definition II.1.1: smoothness at `x` is witnessed by an open neighborhood `U` of `x` and an étale morphism
on `U`. Every point of `U` then has the same witness.

### Specializations stay smooth

<!-- source: II.1.2 -->

_This result says: smoothness at a prime propagates to all primes contained in it._

**Corollary II.1.2.** If `B` is smooth over `A` at the prime `𝔭 ⊂ B`, then `B` is smooth over `A` at every prime `𝔮 ⊂ B`
contained in `𝔭`.

### Permanence

<!-- source: II.1.3 -->

_This result says: étale morphisms are smooth, base change preserves smoothness, and the composite of two smooth
morphisms is smooth._

**Proposition II.1.3.**

1. An étale morphism — in particular an open immersion or the identity — is smooth.
1. The base change of a smooth morphism is smooth.
1. The composite of two smooth morphisms is smooth.

### Proof

(i) is trivial: if `f` is étale, take `n = 0` in Definition II.1.1 (the étale `Y`-morphism `U → Y[ ] = Y` is `f` itself,
with `U = X`).

(ii) follows from the analogous fact for étale (file 10, I.4.6) and for the projections `Y[t₁, …, tₙ] → Y` (which
clearly base-change to `Y′[t₁, …, tₙ] → Y′`). Combine the two: an étale `g : U → Y[t₁, …, tₙ]` base-changes to an étale
`U′ → Y′[t₁, …, tₙ]`, which witnesses smoothness of `X′ → Y′` at `x′`.

(iii) Suppose `Y` is smooth over `Z` and `X` is smooth over `Y`. Locally we may assume `Y → Z[t₁, …, tₙ]` is étale and
`X → Y[s₁, …, sₘ]` is étale. Then `Y[s₁, …, sₘ] → Z[t₁, …, tₙ][s₁, …, sₘ] = Z[t₁, …, tₙ, s₁, …, sₘ]` is étale (by the
analogous fact for polynomial extensions of étale algebras). Composing, `X → Z[t₁, …, tₙ, s₁, …, sₘ]` is étale,
witnessing smoothness of `X → Z` at the relevant point.

### Étale = quasi-finite + smooth

<!-- source: II.1.4 -->

_This result says: étale morphisms are exactly the smooth morphisms with finite fibers._

**Corollary II.1.4.** A morphism is étale iff it is quasi-finite and smooth.

### Proof

Étale ⟹ quasi-finite (file 04) and étale ⟹ smooth by II.1.3(i). Conversely, suppose `f` is quasi-finite and smooth.
Choose an étale `g : U → Y[t₁, …, tₙ]` witnessing smoothness near `x`. The projection `Y[t₁, …, tₙ] → Y` has fiber
`Spec κ(y)[t₁, …, tₙ]`, the affine `n`-space. Composing with the étale `g` shows the fiber of `f` near `x` contains an
étale image of `κ(y)`-affine `n`-space. Quasi-finiteness forces the fiber to be a finite set of points; hence `n = 0`,
and `g : U → Y` is étale, so `f` is étale at `x`.

### Relative dimension

<!-- source: II.1.5 -->

_This result says: the integer `n` in Definition II.1.1 is well defined and additive under composition. It equals the
dimension of the local ring of `x` in its fiber._

**Remark II.1.5 (relative dimension).** The integer `n` in Definition II.1.1 depends only on `f` and `x`, not on the
choice of witness. Concretely:

```text
n = dim 𝒪_{f⁻¹(f(x)), x},
```

the dimension of the local ring of `x` in its fiber over `f(x)`. We call `n` the **relative dimension** of `f` at `x`,
and write

```text
dim_x f = n.
```

It is **additive under composition**: for `X → Y → Z` with both morphisms smooth,
`dim_x(g ∘ f) = dim_x f + dim_{f(x)} g`.

When the relative dimension is locally constant on `X` (e.g. when `X` is connected), we say `f` has **relative dimension
`n`**. The running affine line `Spec ℤ[t] → Spec ℤ` has relative dimension `1` everywhere; an étale morphism has
relative dimension `0`.

## II.2 Smoothness criteria

<!-- source: II.2 -->

The definition is asymmetric: smoothness is checked by exhibiting an étale morphism to an auxiliary polynomial scheme.
Section II.2 gives intrinsic criteria — fiber-by-fiber tests that do not require choosing such a witness.

### The flatness criterion

<!-- source: II.2.1 -->

_This result says: smooth at `x` is equivalent to flat at `x` plus smooth fiber at `x`. The two clauses split smoothness
into a "horizontal" condition (the family is flat) and a "vertical" one (each fiber is smooth)._

**Theorem II.2.1.** Let `f : X → Y` be a morphism locally of finite type, let `x ∈ X`, and let `y = f(x)`. The following
are equivalent:

1. `f` is smooth at `x`.
1. `f` is flat at `x` and the fiber `f⁻¹(y)` is smooth over `κ(y)` at `x`.

### Proof

**(i) ⟹ (ii).** Smoothness factors through `g : U → Y[t₁, …, tₙ]` étale and `Y[t₁, …, tₙ] → Y` flat. Composition of flat
is flat ([flatness sorites](appendix-black-boxes.md#flatness-sorites)), so `f` is flat at `x`. Base-changing to the
fiber preserves smoothness (II.1.3(ii)), so `f⁻¹(y) → Spec κ(y)` is smooth at `x`.

**(ii) ⟹ (i).** Let `V = Spec A` be an affine neighborhood of `y`, `U = Spec B` an affine neighborhood of `x` over `V`.
By the fiber-smoothness assumption, after shrinking `U` we have an étale `κ(y)`-morphism

```text
g_y : U|_{f⁻¹(y)} → Spec κ(y)[t₁, …, tₙ]
```

defined by `n` sections `g_i` of the structure sheaf of `f⁻¹(y)`. The sections `g_i` lift to sections of `𝒪_U` (after
possibly multiplying by a common nonzero element of `κ(y)`), defining a `Y`-morphism

```text
g : U → Y[t₁, …, tₙ].
```

By (ii), `U` is flat over `Y` at `x`; the projection `Y[t₁, …, tₙ] → Y` is also flat. The induced morphism on fibers
over `y` is the étale `g_y`. By the **fiber criterion for étaleness** (I.5.8 / I.5.9, file 11) — flat over the base plus
étale on a fiber forces étale at the corresponding point — `g` is étale at `x`. This is what witnesses smoothness of `f`
at `x`.

### Why the proof works

The fiber gives the étale witness in disguise; flatness lets us lift it from the fiber to a neighborhood. The two
clauses match the two clauses of étale (flat + unramified) one level higher: smooth = flat + (fiber is "0-flat plus
unramified," i.e. smooth-over-a-field).

### Relative form

<!-- source: II.2.2 -->

_This result says: a more flexible version of II.2.1, where the base of comparison is not the immediate target but a
deeper base `S`._

**Corollary II.2.2.** Let `S` be a prescheme, `f : X → Y` an `S`-morphism of finite type, with `Y` of finite type and
flat over `S`. Let `x ∈ X` and `s` its projection to `S`. Then `f` is smooth at `x` iff `X` is flat (equivalently,
smooth) over `S` at `x` and the fiber morphism `f_s : X_s → Y_s` is smooth at `x`.

### Proof

Combine II.2.1 with the fiber criterion for flatness ([flatness sorites](appendix-black-boxes.md#flatness-sorites); file
11, I.5.9).

### Equidimensional criterion (under normality)

<!-- source: II.2.3 -->

A morphism `f : X → Y` locally of finite type is **equidimensional at `x`** if, near `x`, every component of `X`
dominates a component of `Y`, and for every `y′ ∈ Y` near `y`, the irreducible components of `f⁻¹(y′)` near `x` all have
the same dimension, independent of `y′`. (Equivalently: the components of `f⁻¹(y)` near `x` have the "right" dimension
for the generic fiber.)

_This result says: when the base is normal, the flatness clause in II.2.1 can be replaced by equidimensionality._

**Proposition II.2.3.** Let `f : X → Y` be locally of finite type, `x ∈ X`, `y = f(x)`. Suppose `𝒪_y` is **normal**.
Then `f` is smooth at `x` iff:

1. `f` is equidimensional at `x`, and
1. `f⁻¹(y)` is smooth over `κ(y)` at `x`.

### Proof sketch

Smooth ⟹ equidimensional is immediate (the witness `Y[t₁, …, tₙ]` is equidimensional over `Y`). For the converse,
construct `g : X → Y[t₁, …, tₙ]` étale on the fiber as in II.2.1. By equidimensionality, the components of `X` dominate
components of the polynomial scheme; hence `𝒪_{g(x)} → 𝒪_x` is injective and unramified. Normality of `𝒪_y` (hence of
`𝒪_{g(x)}`, since it is a localization of `𝒪_y[t₁, …, tₙ]`) lets us upgrade injective + unramified to étale by I.9.5(ii)
(file 12). So `g` is étale at `x`, witnessing smoothness.

### A relaxation

<!-- source: II.2.4 -->

The normality hypothesis in II.2.3 can be relaxed to **geometrically unibranch** at `y` (file 06), since the version of
I.9.5 we use holds under that weaker hypothesis. For complete local rings with algebraically closed residue field,
"analytically integral" (`Â` integral) implies geometrically unibranch.

### Hironaka's criterion (multiplicity 1)

<!-- source: II.2.5 -->

A component `Z` of a fiber `f⁻¹(y)` has **multiplicity `1`** if its generic point `x` satisfies (i) `dim 𝒪_x = dim 𝒪_y`
(no excess component) and (ii) the maximal ideal `𝔪_{𝒪_x}` is generated by `𝔪_{𝒪_y}`. The second condition automatically
holds modulo passing to an ideal of definition; condition (i) excludes "fattened" components.

_This result says: under multiplicity-1 hypotheses on the fibers, reducedness is automatic and the morphism becomes
flat._

**Proposition II.2.5 (Hironaka).** Let `f : X → Y` be a dominant morphism of finite type of reduced preschemes, `y ∈ Y`
with `𝒪_y` regular. Suppose:

- every component of `f⁻¹(y)` has multiplicity `1`;
- `f⁻¹(y)_red` is normal.

Then `f⁻¹(y)` is reduced (hence normal), `X` is normal at all points of `f⁻¹(y)`, and `f` is flat over `Y` at all points
of `f⁻¹(y)`.

We treat this as a [black box](appendix-black-boxes.md#hironaka-multiplicity); the proof is in EGA IV §5.12.10.
Combining with II.2.1 / II.2.3:

### Hironaka's smoothness criterion

<!-- source: II.2.6 -->

_This result says: a smoothness test for dominant morphisms over a regular base, in terms of fiber multiplicities and
reducedness._

**Corollary II.2.6.** Let `f : X → Y` be a dominant morphism of finite type of reduced preschemes, `y ∈ Y` with `𝒪_y`
regular. The morphism `f` is smooth at every point of `X` above `y` iff every component of `f⁻¹(y)` has multiplicity `1`
and `f⁻¹(y)_red` is smooth over `κ(y)`.

### Historical note

Grothendieck remarks: this situation, with `Y = Spec A` for `A` a discrete valuation ring, was traditionally described
by phrases like "if the reduction of `X` modulo the given valuation is pretty …" The intrinsic role of "object defined
over `A`" rather than just over the fraction field `Frac A` was, before the language of schemes, hard to articulate.

## What to remember

The two intrinsic criteria for smoothness at a point:

- **Flat + smooth fiber** (II.2.1): the universal form, no extra hypothesis needed.
- **Equidimensional + smooth fiber** (II.2.3): trades flatness for equidimensionality, but requires the base to be
    normal (or unibranch).

The hierarchy that tracks Exposé I:

```text
quasi-finite ⟸ unramified ⟸ étale = smooth + relative dim 0
                            ⟸ smooth     (this exposé)
```

Smooth morphisms with constant relative dimension `n` are the algebraic submersions of relative dimension `n`. Étale is
the relative-dimension-`0` slice. The next two files (15, 16) develop the differential properties that make this picture
precise: the sequence `0 → f*Ω¹_Y → Ω¹_X → Ω¹_{X/Y} → 0` becomes split exact under smoothness, with `Ω¹_{X/Y}` locally
free of rank `dim_x f`, and the **Jacobian criterion** turns smoothness checks into rank computations on differentials.
