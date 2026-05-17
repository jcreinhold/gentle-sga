# Exposé III, sections 3–4: local infinitesimal extension (gentle)

## What this file is about

Imagine an algebraic shape sitting over a single point and a slightly thicker point next to it, the thicker point being
the original with an infinitesimal extra layer added. Two questions come up. First, given a map from the slightly
thicker point into another smooth shape, where only the inner part of the map has been specified, can the specification
be extended over the whole thicker point? Second, given the smooth shape itself, but only over the inner point, can the
shape itself be thickened to live over the thicker point and still be smooth?

This file answers both questions locally, meaning on a small enough patch. In each case the answer is yes, and in each
case the answer is not unique. The next two files measure the failure of uniqueness and ask whether the local answers
paste together into a single answer over the whole space.

Section III.1 defined **formally smooth** as a property of local ring maps. Section III.2 gave the equivalent **lifting
characterization**: every algebra map `B → C / J` to a quotient by a nilpotent ideal lifts to an algebra map `B → C`. We
now globalize both pieces to schemes.

The first half of this file (§III.3) turns the lifting characterization into a property of morphisms of finite type. For
a finite-type morphism `f : X → Y`, smoothness of `f` is equivalent to the property that **morphisms into `X` from
infinitesimally thickened sources extend**. In the source's notation: given `Y' ⊃ Y'₀` a closed sub-prescheme with the
same underlying space, every `Y`-morphism `g₀ : Y'₀ → X` extends, locally, to a `Y`-morphism `Y' → X`.

The second half (§III.4) inverts the question. Given a smooth `Y₀`-scheme `X₀`, can it be **lifted** to a smooth
`Y`-scheme over a base `Y₀ ↪ Y` with the same underlying space? Locally, yes — Theorem III.4.1. Globally, the lift is
**not canonical**; files 21–22 will show that this non-canonicity is exactly the cohomological obstruction `H¹` and
`H²`.

The slogan that runs through:

> **Smoothness = sections of an infinitesimal thickening always extend.** A finite-type morphism `f : X → Y` is smooth
> iff sections of `f` (or, equivalently, morphisms into `X`) extend from any closed sub-prescheme to the ambient
> prescheme, at least locally on the source. The étale case is the same with uniqueness added.

The new running examples:

- **The affine line `Spec ℤ[t] → Spec ℤ`**, lifted along the closed immersion `Spec ℤ → Spec ℤ → Spec ℤ` (trivial; just
    to fix vocabulary). Then lifted along `Spec ℤ / p² → Spec ℤ`: the affine line `𝔸¹_{ℤ/p²}` is the unique smooth lift
    of `𝔸¹_{𝔽_p}`.
- **An elliptic curve over `𝔽_p` lifted to `ℤ / p²ℤ`** — represented by a Weierstrass equation `y² − x³ − ax − b` for
    `(a, b) ∈ 𝔽_p²` with `4a³ + 27b² ≠ 0`. The lift exists by III.4.1 once we lift `(a, b)` arbitrarily to
    `(ã, b̃) ∈ (ℤ/p²)²` and check the discriminant remains a unit; smoothness is preserved by the Jacobian criterion
    (file 15, II.4.10). The non-canonicity (III.4.3) is the freedom in choosing the lifts `(ã, b̃)`.

## III.3 Local infinitesimal extension of morphisms into a smooth `S`-scheme

<!-- source: III.3 -->

### Theorem: five equivalent conditions for smoothness

<!-- source: III.3.1 -->

_This theorem says: for a finite-type morphism `f : X → Y`, smoothness is equivalent to the property that any
`Y`-morphism from a closed subprescheme of a test scheme `Y'` extends, locally, to a `Y`-morphism from `Y'` itself. The
five equivalent forms range over choices of test scheme and global vs. local extension._

**Theorem III.3.1.** _Let `f : X → Y` be a morphism locally of finite type. The following are equivalent:_

1. _`f` is smooth._
1. _For every prescheme `Y'` over `Y`, every closed sub-prescheme `Y'₀` of `Y'` having the same underlying space as
    `Y'`, every `Y`-morphism `g₀ : Y'₀ → X`, and every `z ∈ Y'₀`, there exists an open neighborhood `U` of `z` in `Y'`
    and an extension `g` of `g₀|_{Y'₀ ∩ U}`to a`Y`-morphism `U → X`._
1. _For `Y', Y'₀, z` as in (ii), set `X' := X ×_Y Y'` and `X'₀ := X ×_Y Y'₀`; every section of `X'₀` over `Y'₀` extends
    to a section of `X'` over an open neighborhood `U` of `z`._
1. _For every `Y`-scheme `Y'` that is the spectrum of a local artinian ring finite over some `𝒪_y` (with `y ∈ Y`), every
    nonempty closed sub-prescheme `Y'₀` of `Y'`, and every `Y`-morphism `g₀ : Y'₀ → X`, there exists a `Y`-morphism
    `g : Y' → X` extending `g₀`._
1. _As (iii), with `Y'` and `Y'₀` as in (iv) — i.e. with the test scheme being an artinian spectrum — every section
    extends to a section of `X'` over `Y'`._

**Proof sketch.** The equivalence of (ii) and (ii bis), and of (iii) and (iii bis), is trivial. The implication (ii) ⇒
(iii) is also formal. So we prove (i) ⇒ (ii) and (iii) ⇒ (i).

**`(i) ⇒ (ii)`.** Let `x = g₀(z)`. By replacing `X` by an open neighborhood of `x` and `Y'` by the prescheme on the open
inverse image, we may suppose `X` is **étale** over the relative polynomial scheme `Y[t₁, …, t_n]` (the Exposé II
definition of smooth = locally étale over `Y[t₁, …, t_n]`, file 14). Consider the composite `Y'₀ → X → Y[t₁, …, t_n]`.
This composite is determined by `n` sections of `𝒪_{Y'₀}` (the images of the `t_i`). Each can be extended in a
neighborhood of `z` to a section of `𝒪_{Y'}`, since `Y'₀` and `Y'` share their underlying space: `𝒪_{Y'₀} = 𝒪_{Y'} / 𝒥`
for some sheaf of ideals `𝒥` of square zero (or at least nilpotent) — and a section over `Y'₀` is a local section of
`𝒪_{Y'}` modulo `𝒥`, which lifts trivially.

We have extended the morphism to `Y' → Y[t₁, …, t_n]`. Now apply the lifting property for **étale** morphisms (file 11,
I.5.6): since `X → Y[t₁, …, t_n]` is étale, the morphism `Y'₀ → X` lifts **uniquely** to `Y' → X` once
`Y'₀ → Y[t₁, …, t_n]` extends to `Y' → Y[t₁, …, t_n]`. This produces the desired `g`.

**`(iii) ⇒ (i)`.** The set of points where `f` is smooth is open (file 14, II.1.4); so it suffices to show smoothness at
every `x ∈ X` closed in its fiber. Let `y = f(x)`. The local ring `𝒪_x` is an algebra over `𝒪_y`, a localization of an
algebra of finite type, with finite residual extension (since `x` is closed in its fiber).

Hypothesis (iii) — applied with `Y' = Spec(C)` for `C` a local artinian algebra finite over `𝒪_y`, `Y'₀ = Spec(C / J)`
for `J` contained in the radical, and `g₀ : Y'₀ → X` corresponding to the natural local map `𝒪_x → C / J` — implies that
every such local ring map lifts to a local ring map `𝒪_x → C`. (We are using that a morphism `Spec B → X` for `B` local
is determined bijectively by a local map from some `𝒪_x` into `B`.)

This is exactly condition (iv) of Theorem III.2.1 (file 19) for the local map `𝒪_y → 𝒪_x`. So `𝒪_x` is **formally
smooth** over `𝒪_y`. Since `𝒪_x / 𝒪_y` is a localization of a finite-type algebra, by III.1.9 (file 19) `𝒪_x` is
**smooth** over `𝒪_y` — i.e., `f` is smooth at `x`. ∎

This is the geometric form of the lifting characterization. **All of the rest of Exposé III is built on top of it.**

### Étale via uniqueness of extensions

<!-- source: III.3.2 -->

_This corollary says: the étale case of III.3.1 is recovered by demanding that the extension `g` of `g₀` is **unique**.
Smoothness gives existence; étaleness adds uniqueness._

**Corollary III.3.2.** _Let `f : X → Y` be as in III.3.1. The following are equivalent:_

1. _`f` is étale._
1. _Condition (ii) of III.3.1 holds with **uniqueness** of the extension `g` of `g₀` to `U`._
1. _Condition (iii) of III.3.1 holds with **uniqueness** of `g`._

**Proof sketch.** In the proof of (i) ⇒ (ii) of III.3.1, we factored through `Y[t₁, …, t_n]` and used the **uniqueness**
part of the étale lifting property. The unique lift of the image of `Y'₀` in `Y[t₁, …, t_n]` to `Y'` is unique only if
the lift of `Y'₀ → Y[t₁, …, t_n]` to `Y' → Y[t₁, …, t_n]` is unique. But extending sections of `𝒪_{Y'₀}` to `𝒪_{Y'}` is
not unique in general — except when `n = 0`, in which case there is nothing to extend and uniqueness is automatic. So
uniqueness of the extension `g` of `g₀` happens exactly when `n = 0` — i.e. when `f` is **smooth of relative dimension
`0`**, which is **étale** (file 14, II.1.4). ∎

This is the second proof, by lifting, that **étale = smooth of relative dimension `0`**. The first was by counting
Kähler differentials in file 14.

### Rational sections over a complete local ring

<!-- source: III.3.3 -->

_This corollary says: when the base is a complete local ring `A` and `X / A` is smooth, every rational point of the
closed fiber `X ⊗_A k` lifts to a section of `X` over `A`. The proper case (say, `A` a DVR and `X` proper) becomes the
classical statement about extending generic-fiber points to integral models._

**Corollary III.3.3.** _Let `X → Y = Spec(A)` be a prescheme locally of finite type over a **complete** local ring `A`,
with `y ∈ Y` the closed point. Let `x ∈ f⁻¹(y)` be **rational over `κ(y)`**. If `X` is **smooth over `A` at `x`**, then
there exists a section `s : Y → X` of `f` "passing through `x`", i.e. with `s(y) = x`._

_In particular, if `X` is smooth over `A`, then the natural map_

```text
Γ(X / Y) ⟶ Γ(X ⊗_A k / k)
```

_from sections of `X` over `Y` to rational points of the closed fiber over `k = A / 𝔪` is **surjective**._

**Proof sketch.** The rational point `x ∈ f⁻¹(y)` is a section of `f⁻¹(y) = X ⊗_A k → Spec(k)`, i.e. a section of `X`
over the closed sub-prescheme `Spec(k) ⊂ Spec(A)`. By Theorem III.3.1 condition (iii) (or rather a step-by-step
application of it through the artinian thickenings `A / 𝔪^{n+1}`), this section extends to a section over each
thickening. Passing to the limit (using the completeness of `A`), the section extends to all of `Y = Spec(A)`. ∎

**The discrete-valuation-ring application.** Suppose `A` is a discrete valuation ring with field of fractions `K`, and
`X` is proper (in fact projective) over `A`. Then sections of `X` over `Y = Spec(A)` are the same as **points of `X`
with values in `A`**. By the valuative criterion for properness (file 02, §V4 of the algebraic-geometry skill, or Liu
§3.3.4), these identify with the **points of `X_K = X ⊗_A K` with values in `K`** — i.e. the `K`-rational points of the
generic fiber `X_K`. Combining with III.3.3:

> _For `A` a complete DVR, `X` smooth and proper over `A`: every rational point of the closed fiber `X ⊗_A k` extends
> uniquely to a `K`-rational point of the generic fiber `X_K`._

This is the classical "specialization map" for `K`-rational points. It is the foundation for studying integral models of
varieties over local fields — the arithmetic-geometry use of Exposé III's lifting theory.

## III.4 Local infinitesimal extension of smooth `S`-schemes

<!-- source: III.4 -->

We now invert the direction of §III.3. Instead of asking whether a morphism into a smooth scheme extends, we ask whether
a smooth scheme **itself** extends along a thickening of the base.

### Theorem: smooth schemes lift smoothly, locally

<!-- source: III.4.1 -->

_This theorem says: a smooth scheme over a closed sub-prescheme `Y₀` always lifts, locally, to a smooth scheme over the
ambient `Y`. The local lift exists; the next two results clarify what "local" and "unique up to isomorphism" mean._

**Theorem III.4.1.** _Let `Y` be a locally noetherian prescheme, let `Y₀` be a closed sub-prescheme with the same
underlying space, let `X₀` be a smooth `Y₀`-prescheme, and let `x ∈ X₀`. Then there exist:_

- _an open neighborhood `U₀` of `x` in `X₀`,_
- _a prescheme `X` smooth over `Y`,_
- _a `Y₀`-isomorphism `h : U₀ → X ×_Y Y₀`._

_Moreover, if `(U'₀, X', h')` is another solution, then it is isomorphic to the first in a neighborhood of `x` (in a
sense made precise in the source)._

**Reformulation in terms of sheaves.** For `U₀` given, a solution of the problem amounts to giving on `U₀` a sheaf of
algebras `ℬ` over `f₀⁻¹(𝒪_Y)`, where `f₀` is the continuous map underlying the structural morphism `U₀ → Y₀`, together
with a homomorphism of rings `ℬ → 𝒪_{U₀}` compatible with the homomorphism `f⁻¹(𝒪_Y) → f⁻¹(𝒪_{Y₀})`, satisfying:

1. The induced map `ℬ ⊗_{f⁻¹(𝒪_Y)} f⁻¹(𝒪_{Y₀}) → 𝒪_{U₀}` is an isomorphism (the sheaf of algebras `ℬ` recovers `𝒪_{U₀}`
    after reduction modulo the ideal of `Y₀` in `Y`).
1. `U₀` equipped with `ℬ` becomes a smooth `Y`-prescheme.

In this form the precise meaning of local uniqueness becomes particularly evident.

**Proof sketch.** Since `X₀` is smooth over `Y₀`, by file 14 (II.1.1) we may suppose, at the chosen `x`, that `X₀` is
étale over a relative polynomial scheme `Y₀[t₁, …, t_n] := Y'₀`. The relative polynomial scheme `Y'₀` is itself a closed
sub-prescheme of `Y' := Y[t₁, …, t_n]`, with the same underlying space. By file 11 (I.8.3, the étale lifting theorem),
there exists a prescheme `X → Y'` étale over `Y'` and a `Y'₀`-isomorphism `X ×_{Y'} Y'₀ → X₀`. This `X` is then smooth
over `Y` (étale over `Y[t₁, …, t_n]` ⟹ smooth over `Y` by file 14, II.1.1). This gives the existence.

For uniqueness, we use Lemma III.4.2 (below). Two local solutions `(X, h)` and `(X', h')` agree modulo the ideal of `Y₀`
in `Y`, and the lemma promotes this agreement to an isomorphism of `X` and `X'` in a neighborhood of `x`. ∎

**Comment on canonicity.** The local isomorphism is **not unique**: two local solutions admit isomorphisms between them,
but the isomorphism is determined only up to a section of the **automorphism sheaf** of the local lift. This is the
engine of the cohomological obstruction theory in file 21 (III.6).

### Lemma: isomorphism via reduction modulo a locally nilpotent ideal

<!-- source: III.4.2 -->

_This lemma says: a flat `Y`-morphism `u : X → X'` is an isomorphism iff its reduction `u₀ : X ×_Y Y₀ → X' ×_Y Y₀` is an
isomorphism, when `Y₀` is the closed sub-prescheme defined by a locally nilpotent sheaf of ideals on `Y`._

**Lemma III.4.2.** _Let `Y` be a prescheme, let `Y₀` be a closed sub-prescheme defined by a locally nilpotent sheaf of
ideals `𝒥`, let `X` and `X'` be `Y`-preschemes, and let `u : X → X'` be a `Y`-morphism. Suppose `X` is **flat** over
`Y`. Then `u` is an isomorphism if and only if_

```text
u₀ : X ×_Y Y₀ ⟶ X' ×_Y Y₀
```

_is an isomorphism._

**Proof sketch.** Easy by passing to the affine case and looking at associated graded rings for the `𝒥`-adic filtration.
Flatness of `X` over `Y` means tensoring `M ⊗_𝒪_Y 𝒪_X` is exact, so an isomorphism after reducing modulo `𝒥` propagates
to an isomorphism on each graded piece, hence on the inverse limit, hence on `X` itself.

**Variant.** The analogous statement obtained by replacing "isomorphism" with **"closed immersion"** is also valid, and
**without** the flatness hypothesis. (This is occasionally useful and we will use it implicitly in file 21.)

### Remark: the lift is **not** canonical

<!-- source: III.4.3 -->

_This remark says: the local extension `X` of `X₀` produced by III.4.1 is not unique up to canonical isomorphism — there
exist nontrivial `Y`-automorphisms of `X` inducing the identity on `X₀`. This non-canonicity is precisely what makes the
**global** extension obstructed by cohomology (in file 21)._

**Remark III.4.3.** It is essential to note that the local extension `X` obtained in III.4.1 **is not canonical**: in
other words, the local isomorphism between two solutions is not unique. Equivalently, in general there exist nontrivial
`Y`-automorphisms of `X` inducing the identity on the closed sub-prescheme `X₀ = X ×_Y Y₀`.

This is why, for the construction of **global** infinitesimal extensions of smooth preschemes, one must expect the
existence of an obstruction of **cohomological nature**. We make this obstruction precise in file 21 (III.6.3): the
obstruction lives in `H²(X₀, 𝒢)` for the appropriate sheaf `𝒢` built from the **tangent sheaf** `𝔤_{X₀/Y₀}` of `X₀` over
`Y₀`.

> _The connection to file 17._ The non-canonicity of the local lift is exactly the data that gives the automorphism
> sheaf of the local lift. The 2-cocycle of automorphisms on triple overlaps is the obstruction class. The reader who
> has digested file 17 already sees the shape of file 21's argument; III.6 is the application of the H²-as-obstruction
> picture to the lifting problem opened here.

## Running example: lifting `Spec ℤ[t]` and the elliptic curve

We give two concrete instances of III.4.1 to anchor the abstract discussion.

**The affine line.** Take `Y = Spec ℤ`, `Y₀ = Spec(ℤ / pℤ) = Spec 𝔽_p`. The closed sub-prescheme `Y₀` is cut out by the
square-zero ideal `(p) ⊂ ℤ` (well, square-zero as an ideal in `ℤ / p²ℤ`, not in `ℤ` itself; we work over `Spec ℤ / p²ℤ`
for square-zero). Let `X₀ = 𝔸¹_{𝔽_p} = Spec 𝔽_p[t]`. Then `X = 𝔸¹_{ℤ/p²} = Spec(ℤ/p²)[t]` is a smooth lift of `X₀` over
`Spec(ℤ/p²)`, and any other lift is `Spec(ℤ/p²)[t']` for some indeterminate `t'`. The freedom is in the **choice of
coordinate** `t' = t + p · ε(t)` for `ε(t) ∈ 𝔽_p[t]` — exactly an element of the tangent sheaf `𝔤_{𝔸¹_{𝔽_p}/𝔽_p}`
tensored with the square-zero ideal `(p)`. In file 21, this is the H¹ classification of lifts of the affine line; in
this case, since `H¹(𝔸¹_{𝔽_p}, 𝔤) = 0` (Serre vanishing on the affine), there is essentially one lift up to isomorphism.

**The elliptic curve.** Take `Y = Spec(ℤ/p²)`, `Y₀ = Spec 𝔽_p`, and `X₀ = E₀ := V(y² − x³ − ax₀ − b₀) ⊂ 𝔸²_{𝔽_p}` for
some `a₀, b₀ ∈ 𝔽_p` with `4 a₀³ + 27 b₀² ≠ 0` (so `E₀` is smooth by the file 15 Jacobian criterion). To lift: choose any
`ã, b̃ ∈ ℤ/p²` projecting to `a₀, b₀`, and set

```text
E := V(y² − x³ − ã x − b̃) ⊂ 𝔸²_{ℤ/p²}.
```

Smoothness of `E` over `Spec(ℤ/p²)` requires the discriminant `−16(4ã³ + 27 b̃²)` to be a unit in `ℤ/p²`. Since the
reduction mod `p` of this discriminant is `−16(4 a₀³ + 27 b₀²)`, which is a unit in `𝔽_p`, the lifted discriminant is a
unit in `ℤ/p²`. So `E` is a smooth lift.

The freedom in choosing `(ã, b̃) ∈ (ℤ/p²)²` projecting to `(a₀, b₀)` is a **`(p)·(ℤ/p²)²` orbit** of lifts — concretely
`p · (ℤ/p²)² ≃ 𝔽_p²`, two `𝔽_p`-degrees of freedom. This is the H¹ classification: `H¹(E₀, 𝔤_{E₀/𝔽_p}) ≃ 𝔽_p²` (by Serre
duality on the elliptic curve, this is `H⁰(E₀, ω_{E₀/𝔽_p}) ⊗ 𝔽_p² ≃ 𝔽_p`, which times the Lie-algebra dual is `𝔽_p²` —
but the explicit computation belongs to file 21). The two lifts of `(a₀, b₀)` give the same lifted elliptic curve up to
isomorphism if and only if the corresponding 1-cocycle is a coboundary, which here happens always since the lift of `a`
and `b` is unique up to coboundary.

## What to remember

- **§III.3.1** is the geometric form of the lifting characterization (file 19, III.2.1): smoothness of a finite-type
    morphism `f : X → Y` is equivalent to extending morphisms into `X` from closed subpreschemes of test schemes. Five
    equivalent forms, ranging over local vs global and arbitrary vs artinian test scheme.
- **§III.3.2** recovers étale = smooth + uniqueness of extensions = smooth of relative dimension `0`.
- **§III.3.3** specializes to a complete local base: every rational point of the closed fiber lifts to a section over
    the base. The DVR + proper case is the classical specialization map for rational points.
- **§III.4.1** inverts: every smooth `Y₀`-scheme lifts smoothly to a `Y`-scheme **locally**, where `Y₀ ↪ Y` is a
    square-zero thickening (or, more generally, a thickening by a locally nilpotent ideal).
- **§III.4.2** is the lemma that promotes "isomorphism after reduction" to "isomorphism", under flatness.
- **§III.4.3** is the crucial preview: the local lift is **not canonical**. The non-canonicity is exactly the
    cohomological obstruction theory of files 21 and 22.

The next file (file 21) globalizes: §III.5 handles the obstruction to extending a morphism (in `H¹`); §III.6 handles the
obstruction to extending a smooth scheme (in `H²`). Both use the cohomological machinery of file 17.
