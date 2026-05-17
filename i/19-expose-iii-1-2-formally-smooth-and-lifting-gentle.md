# Exposé III, sections 1–2: formally smooth morphisms and the lifting characterization (gentle)

## What this file is about

An earlier batch of files said what it means for an algebraic shape to vary smoothly over a base, in the sense of having
no kinks or pinch points. The definition there required a finiteness restriction. Some of the most useful objects break
it: power series in several variables, the local ring at a point of a complex analytic shape, and the rings used in
arithmetic over the integers all behave like smooth families everywhere it matters, but the older definition does not
see them.

This file widens the notion to take them in. The wider definition is a lifting question. Given a map into the shape from
a smaller piece sitting inside a slightly thicker piece, does the map extend to the thicker piece? The right answer is
yes, always. The file proves that this lifting condition agrees with the earlier definition wherever the earlier one
applied.

Exposé II (files 14–16) developed smooth morphisms under a **finite-type** hypothesis: smooth = locally étale over a
polynomial scheme `Y[t₁, …, t_n]`. The current exposé widens the lens. Some of the rings most relevant to formal and
analytic geometry — the formal-power-series ring `A[[t₁, …, t_n]]`, the local ring of a point in a complex-analytic
product `Y × ℂⁿ` — are not localizations of finite-type algebras over a base. They behave like smooth algebras in every
respect we care about, but the finite-type definition does not see them.

The exposé fixes this in two stages. **Section III.1** introduces **formally smooth homomorphisms**, defined directly in
terms of the formal completions of `A → B`. These are the objects of formal geometry. Their characterization on
finite-type morphisms recovers ordinary smoothness (III.1.9). **Section III.2** proves the deep characterization:
formally smooth is equivalent to a **lifting property** for homomorphisms into artinian quotients. This is the form
later authors take as the definition (EGA 0_IV §19.3.1); the SGA decision to start with the formal-power-series form is
one of presentation, and the source acknowledges this in the footnote to III.1.2.

The slogan that runs through:

> **Formally smooth = lifts along nilpotent thickenings.** A local ring map `A → B` is formally smooth iff every algebra
> map from `B` into a quotient `C / J` of an artinian `A`-algebra by a nilpotent ideal lifts to an algebra map into `C`.
> For finite-type morphisms this matches Exposé II's smoothness verbatim (III.1.9). The lifting property is the
> characterization that makes formal smoothness portable across formal, analytic, and arithmetic settings.

The new running examples come from formal geometry:

- **`A → A[[t₁, …, t_n]]`** — the formal power series ring is formally smooth of relative dimension `n` over `A`. It is
    the prototypical formally smooth algebra. (For `A` a noetherian local ring, `A[[t₁, …, t_n]]` has the local ring `A`
    with `n` more "formal directions" attached.)
- **The completion of a smooth `A`-algebra** at a point — also formally smooth, by III.1.9 once we have it. The
    completion identifies smooth Exposé-II-style with the formal geometry of this exposé.

## III.1 Formally smooth homomorphisms

<!-- source: III.1 -->

### Setup: completions and finite residual extensions

The setup throughout §III.1 is a **local homomorphism of noetherian local rings** `u : A → B`. We write `𝔪 ⊂ A` and
`𝔫 ⊂ B` for the maximal ideals, `k = A / 𝔪` and `L = B / 𝔫` for the residue fields. The key hypothesis — present in
every numbered statement of §III.1 — is that the **residual extension `L / k` is finite**. Without this hypothesis the
formal-power-series form of the definition becomes inadequate; the right framework then is the EGA 0_IV §19
lifting-property setup, which §III.2 will recover.

The completions `Â` and `B̂` (file 04) play a starring role. Definition III.1.1 is phrased on the completions, and
Remark III.1.2 immediately observes that the property depends only on the homomorphism `Â → B̂` deduced from `u`.

### Definition

<!-- source: III.1.1 -->

_This definition says: a local map `A → B` of noetherian local rings is formally smooth if, after completing both sides
and extending scalars by a suitable finite free local algebra, the extended ring is a formal-power-series ring over the
extended base._

**Definition III.1.1.** _Let `u : A → B` be a local homomorphism of noetherian local rings. Suppose `κ(B)` is finite
over `κ(A)`. We say `u` is **formally smooth**, or that the algebra `B` is **formally smooth over `A`**, if there exists
a local finite `Â`-algebra `A'`, free over `Â`, such that the local components of the semi-local ring_

```text
B' := B̂ ⊗_{Â} A'
```

_are `A'`-isomorphic to formal-power-series algebras over `A'`._

Three things to observe.

- `B' = B̂ ⊗_{Â} A'` is finite and free over `B̂`, hence semi-local (a finite product of complete local rings). The
    condition is that **each local component**, viewed as an `A'`-algebra, is isomorphic to `A'[[t₁, …, t_d]]` for some
    `d` (the number of variables).
- The number `d` of variables is the same for every local component: by faithful flatness of completion and tensor
    product, `d = dim B̂ − dim Â = dim B − dim A`. So `d` is an intrinsic invariant of the local map `u`.
- The number `d` also equals the dimension of the **fiber ring** `B / 𝔪B = B ⊗_A k`. We call it the **relative dimension
    of `B` over `A`** and write `d = dim_u B`.

**Footnote echoed from the source.** The general "right" definition of formally smooth, motivated by the lifting
characterization (III.2.1 below), drops the finite-residual-extension assumption and replaces the formal-power-series
form by the lifting property. That definition lives in EGA 0_IV §19.3.1 (appendix row `formally-smooth-ega`) and is the
one most modern authors take. The SGA definition is equivalent to it under the finite-residual hypothesis (which is the
case of almost all applications), and is what we will work with in the rest of this file.

### Renaming: formally étale, formally unramified

<!-- source: III.1.2 -->

_This remark says: the SGA terminology "formally étale" and "formally unramified" replaces what Exposé I called
"essentially étale" and "essentially unramified." The reader will verify that "formally étale" = "formally smooth and
quasi-finite."_

**Remark III.1.2.** Definition III.1.1 depends only on the homomorphism on completions `Â → B̂` deduced from `A → B`.
The SGA repents of Definitions I.3.2(b) and I.4.1(b) (file 04 covers these) and prefers, in the formal setting:

- **formally smooth**: `B` is formally smooth over `A` in the sense of III.1.1.
- **formally étale**: `B` is formally smooth and the residual extension `L / k` is **trivial** (so `d = 0` in Definition
    III.1.1; the formal-power-series component is just `A'`).
- **formally unramified**: the lifting property of III.2.1 holds but `B` need not be flat (i.e., the unramified analogue
    of formally smooth in §III.2).

The reader will immediately verify that "formally étale" is equivalent to "formally smooth and quasi-finite."

A reasonable definition exists that drops the finite-residual hypothesis — it is the EGA 0_IV §19.3.1 definition we have
already mentioned. For example, a Cohen `p`-ring (file 22) is formally smooth over the ring of `p`-adic integers in this
more general sense. In what follows, "formally smooth" always means "with finite residual extension."

### Formally smooth implies flat

<!-- source: III.1.3 -->

_This lemma says: a formally smooth local map is automatically flat — flatness is built into the formal-power-series
structure on local components._

**Lemma III.1.3.** _If `B` is formally smooth over `A`, then `B` is flat over `A`._

**Proof sketch.** Flatness is invariant under completion (the appendix `completion-test-for-flatness`), so we may
suppose `A` and `B` complete. Flatness is also invariant under faithfully flat extension of the base, so by Definition
III.1.1 we reduce to the case `B = A[[t₁, …, t_d]]`. As an `A`-module, `B` is the product of free rank-one `A`-modules
`A · t₁^{i₁} ⋯ t_d^{i_d}` over all `i = (i₁, …, i_d) ∈ ℕ^d`. Since `A` is noetherian, an arbitrary product of flat
`A`-modules is flat (this is the key noetherian input); so `B` is flat over `A`. ∎

This is the formal-smooth analogue of Exposé II.2.1's "smooth = flat + smooth fibers" — half of it. The full
characterization for formally smooth comes in III.1.7 below.

### Behavior under finite local extensions

<!-- source: III.1.4 -->

_This proposition says: formal smoothness behaves well under base change to a finite local algebra. Both directions
hold; the converse needs the extension to be free over the base._

**Proposition III.1.4.** _Let `A → B` be a local homomorphism of local rings with finite residual extension, and let
`A'` be a finite local `A`-algebra, so that `B' := B ⊗_A A'` is finite over `B` and is a semi-local noetherian ring._

1. _If `B` is formally smooth over `A`, then the localizations of `B'` at its maximal ideals are formally smooth over
    `A'`._
1. _The converse is true if `A'` is free over `A`._

**Proof sketch.** By passing to completions, we may assume `A` and `B` complete. For (i), let `A''` be a finite free
local `A`-extension witnessing the formal smoothness of `B`. Extend scalars to `A'' ⊗_A A' → A'''`, where `A'''` is a
local component. The local components of `B ⊗_A A'''` are formal-power series over `A'''` (by tracking through the
construction). Since `A''` is free over `A`, `A'' ⊗_A A'` is free over `A'`, hence so is its local component `A'''`, and
`B'` over `A'` inherits formal smoothness.

For (ii), if `A''` is a finite free local `A'`-algebra such that `B' ⊗_{A'} A''` is a formal-power-series algebra over
`A''`, then since `A'` is free over `A`, so is `A''`; and `B' ⊗_{A'} A'' = B ⊗_A A''` is a formal-power-series algebra
over `A''`. So `B` is formally smooth over `A`. ∎

### The trivial-residual-extension case

<!-- source: III.1.5 -->

_This proposition says: when the residual extension is trivial, formal smoothness reduces to the cleanest possible form
— `B̂` is literally a formal-power-series algebra over `Â`._

**Proposition III.1.5.** _Let `A → B` be a local homomorphism of local rings with **trivial** residual extension. Then
`B` is formally smooth over `A` if and only if `B̂` is isomorphic to a formal-power-series algebra over `Â`._

**Proof sketch.** Necessity needs proof; sufficiency is in the definition. Assume `A` and `B` complete. Let
`t₁, …, t_n ∈ 𝔫` project to a basis of the vector space

```text
(𝔫 / 𝔫²) / Im(𝔪 / 𝔪²) = 𝔫 / (𝔫² + 𝔪B).
```

These elements define a homomorphism of local `A`-algebras `B₁ := A[[t₁, …, t_n]] → B`. It suffices to prove this is an
isomorphism. By passing to associated graded rings for the `𝔪`-adic filtration (using flatness from III.1.3 to commute
the graded-ring construction with tensor product), one reduces to the case `A = k` a field. With `A = k`,
`B = k[[t₁, …, t_n]]` after the witness extension `A'`, and the map of formal power series rings induced by mapping each
`t_i` of `B₁` to the corresponding `t_i` of `B` is an isomorphism (a standard graded-ring argument). ∎

### Existence of a trivializing extension

<!-- source: III.1.6 -->

_This corollary says: even when the residual extension is not trivial, one can always make it trivial by passing to a
suitable finite free local extension of `A`._

**Corollary III.1.6.** _If `B` is formally smooth over `A`, then there exists a finite local `A`-algebra `A'` such that
the local components of_

```text
B̂ ⊗_{Â} Â' = completion of (B ⊗_A A')
```

_are isomorphic to formal-power-series algebras over `Â'`._

**Proof sketch.** Choose a finite extension `k' / k` of residue fields making `L ⊗_k k'` have only trivial residual
extensions over `k'`. Lift to a finite free local `A`-algebra `A'` with `A' / 𝔪 A' = k'` (this is possible by lifting
minimal polynomial coefficients step by step from `k` to `A`, after reducing to the monogenic case). The local
components of `B ⊗_A A'` then have trivial residual extensions over `k'`, and by III.1.5 are formal-power-series
algebras over the corresponding components of `A'`. ∎

This is the operational version of formal smoothness: **after extending the base finitely and freely, the situation is
literally formal-power-series.** Most arguments using formal smoothness pass through this reduction.

### Flat plus formally smooth on the residue field

<!-- source: III.1.7 -->

_This corollary says: formal smoothness factorizes — `B` is formally smooth over `A` iff `B` is flat over `A` and the
fiber `B / 𝔪B` is formally smooth over the residue field `k = A / 𝔪`. The flatness condition is the III.1.3 half; the
fiber condition is formal smoothness over a field, which by III.1.5 just means the completed fiber is a
formal-power-series algebra._

**Corollary III.1.7.** _Let `A → B` be a local homomorphism of local rings. Then `B` is formally smooth over `A` if and
only if_

1. _`B` is flat over `A`, and_
1. _`B / 𝔪B` is formally smooth over `k = A / 𝔪`._

**Proof sketch.** "Only if" is III.1.3 + III.1.4(i). "If": after III.1.4(ii), we may take a free local extension `A'` so
that the residual extension of `B'` over `A'` is trivial, and reduce to proving that `B' = (B' / 𝔪B')` is a
formal-power-series algebra over `Â'` given that `B' / 𝔪B'` is a formal-power-series algebra over `A' / 𝔪A' = k'`. The
proof of III.1.5 carries this through. ∎

This is the **formal-smooth analogue of II.2.1**: smooth = flat + smooth-on-fibers. In the formal setting one passes to
the completed fiber `B̂ / 𝔪B̂` and asks for it to be a formal-power-series algebra over `k`.

### Differential properties (remark)

<!-- source: III.1.8 -->

_This remark says: formally smooth morphisms admit a differential theory analogous to Exposé II's, but it requires
modifying the Kähler differentials to use completed tensor products. The exposé gestures at this without developing it._

**Remark III.1.8.** It is not difficult to develop, for formally smooth homomorphisms, the analogue of all the
properties of smooth morphisms studied in Exposé II. For the differential properties, this requires a modification of
the usual definition of Kähler differentials (file 03): completed tensor products replace ordinary tensor products. The
analogue of `Ω¹_{B/A}` for formally smooth becomes the **module of continuous Kähler differentials** `Ω̂¹_{B/A}` — the
inverse limit of the ordinary `Ω¹` on the artinian thickenings.

We content ourselves with evoking these abysses here. The reader who wants the full development should consult EGA 0_IV
§22 (after §19 for formal smoothness itself); the modern textbook treatment is in Bourbaki, *Algèbre Commutative*
Chapter X.

### Bridge: smooth ⟺ formally smooth for finite type

<!-- source: III.1.9 -->

_This proposition says: when `B` is a localization of an `A`-algebra of finite type — i.e. when we are in the setting of
Exposé II — formal smoothness coincides with smoothness. The two notions disagree only outside the finite-type world._

**Proposition III.1.9.** _Let `A → B` be a local homomorphism with `B` a localization of an `A`-algebra of finite type.
Then `B` is **smooth** over `A` (in the sense of Exposé II.2.1, file 14) if and only if `B` is **formally smooth** over
`A`._

**Proof sketch.** Using III.1.7 and II.2.1 (smooth = flat + smooth fibers, file 14), we reduce to the case where `A = k`
is a field. By III.1.4(ii) and II.4.13 (the field-case differential setup, file 16), a suitable extension `k'` of `k`
reduces us to the case where the residual extension is trivial. By III.1.5 and II.5.2:

- `B` is **smooth** over `k` iff `B` is a regular local ring (Exposé II.5.5, file 16).
- `B` is **formally smooth** over `k` iff `B̂` is a formal-power-series algebra over `k` (III.1.5).

When the residual extension is trivial, these two conditions are equivalent — every regular local ring with trivial
residual extension has formal-power-series completion, and conversely every ring with formal-power-series completion is
regular. ∎

This is the bridge between Exposé II and Exposé III. Every finite-type smooth algebra of Exposé II is formally smooth in
the sense of this exposé, and vice versa. The new content of Exposé III lives in the **non-finite-type cases**:
formal-power-series rings themselves, the local rings of formal preschemes, and (in the analytic setting) the local
rings of complex-analytic varieties.

## III.2 The lifting characterization

<!-- source: III.2 -->

We now come to the deep characterization: formally smooth is equivalent to a **lifting property**. The lifting property
is what later authors take as the definition (EGA 0_IV §19.3.1, where it is the modern conceptual starting point); the
SGA decision to start with the formal-power-series form was one of presentation. For the rest of the exposé it is the
lifting property that does the work, not the formal-power-series form.

### Theorem: five equivalent conditions

<!-- source: III.2.1 -->

_This theorem says: formal smoothness is equivalent to the property that algebra maps from `B` to artinian `A`-algebras
lift along nilpotent thickenings. The exposé gives five forms, ranging from "every complete local C" to "every artinian
local C with square-zero ideal." The equivalence among them is the bookkeeping; the substance is the lifting itself._

**Theorem III.2.1.** _Let `A → B` be a local homomorphism of local rings defining a finite residual extension. The
following are equivalent:_

1. _`B` is formally smooth over `A`._
1. _For every local homomorphism `A → C` with `C` a complete local ring, every ideal `J` of `C` contained in the radical
    `𝔯(C)`, and every local `A`-homomorphism `B → C / J`, there exists an `A`-homomorphism `B → C` lifting it._
1. _For every `A`-algebra `C` (not necessarily noetherian), every nilpotent ideal `J` of `C`, and every continuous
    `A`-homomorphism `B → C / J` (i.e., one vanishing on a power of `𝔯(B)`), there exists a (necessarily continuous)
    `A`-homomorphism `B → C` lifting it._
1. _The same statement as (ii) and (iii), but with `C` a local artinian ring finite over `A`._
1. _As in (iv), but with `J` square-zero._

**Remark.** For the rest of the exposé, **only the implications `(iv) ⇒ (i)` and `(iv bis) ⇒ (i)` will actually be
used**. The other directions are conceptually important but bookkeeping. We sketch the cycle.

**Proof sketch.** We prove `(i) ⇒ (iii) ⇒ (ii)` and `(iv) ⇒ (i)`. The implication `(ii) ⇒ (iv)` is trivial; the
equivalence of `(iv)` and `(iv bis)` follows by induction on `n` such that `J^n = 0`.

**`(i) ⇒ (iii)`.** An immediate induction reduces us to `J² = 0`. Since `C` is finite over `A` (in (iii) `C` is just an
`A`-algebra, not necessarily finite — but the special case to lift to (iii) for formally smooth homomorphisms reduces to
a finiteness claim), some power `𝔪^q` annihilates `C`. Reducing modulo `𝔪^q` makes `A` artinian; then by III.1.3, `B` is
flat hence free over the artinian `A`. Choose an `A`-module homomorphism `w : B → C` lifting the given `u : B → C / J`.
The defect `f(x, y) := w(xy) − w(x) w(y)` lies in `J` and is `A`-bilinear. We seek an `A`-module map `g : B → J` with
`v := w + g` an algebra map; this is an inhomogeneous linear system in `Hom_A(B, J)` with right-hand sides in `J`. By
faithful flatness, such a system has a solution iff its extension to a faithfully flat `A'` does. Choose `A'` finite
free local with `B' = B ⊗_A A'` a formal-power-series algebra. The extended system is then exactly the system
determining algebra extensions `B' → C ⊗_A A'`, lifting `u' : B' → C' / J'`. Since `B'` is a formal-power-series algebra
`A'[[t₁, …, t_n]]`, lifting `u'` is concrete: lift the images of the `t_i` arbitrarily to elements `z_i ∈ C'`. The `z_i`
are nilpotent (because their images modulo `J'` are nilpotent and `J'` is nilpotent), so they define a continuous
algebra homomorphism `A'[[t₁, …, t_n]] → C'` extending `u'`. This produces the required lift.

**`(iii) ⇒ (ii)`.** Standard step-by-step argument: write `J_q := (J + 𝔫^q) / 𝔫^q`, build lifts `v_q : B → C / 𝔫^q`
extending `u_q : B → C / (J + 𝔫^q)` by inductively applying (iii) (each intermediate ideal is nilpotent in the relevant
quotient ring), and pass to the inverse limit since `C` is complete and `J` is closed.

**`(iv) ⇒ (i)`.** First, if (iv) holds for `B → A`, it also holds for the local components of `B ⊗_A A'` over `A'` for
any finite local `A'`. Choosing `A'` free over `A` so that the residual extensions of `B' = B ⊗_A A'` over `A'` are
trivial, by III.1.4(ii) we reduce to the case where `B / A` has trivial residual extension. The substance is in III.2.2
below, which constructs a homomorphism `u : B → A[[t₁, …, t_n]]` inducing an isomorphism on `𝔫 / (𝔫² + 𝔪B)`; one checks
that `u` is necessarily an isomorphism (III.2.3), recovering the formal-power-series form. ∎

### Trivial residual extension case

<!-- source: III.2.2 -->

_This corollary says: in the trivial residual extension case, the lifting property (iv) of III.2.1 produces a canonical
homomorphism `u : B → A[[t₁, …, t_n]]` that is an isomorphism on the cotangent spaces. By III.2.3 below, this `u` is
itself an isomorphism._

**Corollary III.2.2.** _Under the conditions of III.2.1, suppose moreover that the residual extension of `B / A` is
trivial. Then the equivalent conditions of III.2.1 are also equivalent to:_

(v) _Setting `n = dim 𝔫 / (𝔫² + 𝔪B)`, there exists a local `A`-homomorphism_

```text
u : B → B₁ := A[[t₁, …, t_n]]
```

_inducing an isomorphism `𝔫 / (𝔫² + 𝔪B) → 𝔫₁ / (𝔫₁² + 𝔪 B₁)`, where `𝔫₁` is the maximal ideal of `B₁`._

**Proof sketch.** From (iv) (or its square-zero strengthening (iv bis)), choose a basis `a₁, …, a_n` of `𝔫 / (𝔫² + 𝔪B)`.
This defines a map `B → B₁ / (𝔫₁² + 𝔪 B₁) = k[t₁, …, t_n] / (t₁, …, t_n)²`. Lift step by step using (iv ter) — the
square-zero ideal version — to maps `B → B₁ / 𝔫₁^q` for increasing `q`; passing to the projective limit gives the
desired `u`. ∎

### `u` is necessarily an isomorphism

<!-- source: III.2.3 -->

_This corollary says: the homomorphism `u` of III.2.2 is in fact an isomorphism, recovering the formal-power-series form
of formal smoothness from the lifting property._

**Corollary III.2.3.** _Under the conditions of III.2.2(v), the homomorphism `u` is necessarily an isomorphism._

**Proof sketch.** Consider the commutative diagram

```text
𝔪/𝔪²  →  𝔫/𝔫²        →  𝔫/(𝔫² + 𝔪B)        →  0
↓        ↓               ↓
𝔪/𝔪²  →  𝔫₁/𝔫₁²   →  𝔫₁/(𝔫₁² + 𝔪 B₁)  →  0
```

with exact rows. The two extreme vertical maps are surjective (the left is the identity; the right is the isomorphism
postulated in (v)), so the middle vertical is also surjective. Since `B` is complete, the surjection on cotangent spaces
lifts to a surjection `B → B₁`. Lifting the `t_i` of `B₁` to elements `x_i ∈ B` defines a map `B₁ → B` whose composite
with `u` is the identity (by construction). So `u` is also injective, and is therefore an isomorphism. ∎

This finishes the proof that `(iv) ⇒ (i)`, hence III.2.1. As an aside, we have **recovered III.1.5**: a formally smooth
`B̂ / Â` with trivial residual extension is a formal-power-series algebra. "There is little merit in that," says the
source — III.1.5 was the proof input. The point of III.2.3 is the categorical role: the formal-power-series structure is
forced by the lifting property plus the cotangent-space isomorphism.

## What to remember

- **Formal smoothness** (III.1.1) extends Exposé II's smoothness beyond the finite-type setting. The definition uses
    formal-power-series local components after a free local extension of the base; the relative dimension
    `d = dim B − dim A` is the number of variables.
- **Renaming** (III.1.2): "essentially étale / unramified" of Exposé I becomes "formally étale / formally unramified" in
    the formal setting. Formally étale = formally smooth with trivial residual extension (so `d = 0`).
- **Permanence** (III.1.3, III.1.4, III.1.7): formally smooth implies flat; behavior under base change to finite local
    algebras; `B` formally smooth over `A` iff `B` is flat over `A` and `B / 𝔪B` is formally smooth over `k`.
- **Bridge to Exposé II** (III.1.9): for finite-type local morphisms, formally smooth = smooth.
- **Lifting characterization** (III.2.1): formally smooth iff every algebra map `B → C / J` lifts to `B → C` for `C`
    artinian and `J` nilpotent (or any of the equivalent forms). This is the modern conceptual definition (EGA 0_IV
    §19.3.1).
- **Recovery** (III.2.2, III.2.3): the lifting property combined with a cotangent-space isomorphism forces the
    formal-power-series structure of III.1.5. The two definitions are honestly equivalent.
- The **only implications used in the rest of the exposé** are `(iv) ⇒ (i)` and the equivalent forms; the cycle through
    `(iii)` is conceptually important but logically auxiliary.

The next file (file 20) globalizes these to schemes: §III.3 turns the lifting characterization into a property of
morphisms of finite type into a smooth scheme, and §III.4 inverts the direction to ask when smooth schemes themselves
lift along thickenings.
