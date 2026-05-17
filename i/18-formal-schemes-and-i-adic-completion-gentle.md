# Formal schemes and 𝓘-adic completion (gentle prep for Exposé III)

## What this file is about

A function near a point is captured by its value, then its slope, then its curvature, and so on. Each new derivative
records a finer piece of behaviour near the point, and the whole tower together is the Taylor expansion. Geometry has
an analogue. Inside a larger space sits a smaller piece. Around the smaller piece there is a first-order neighbourhood,
then a second-order, then a third, each fatter than the last by an infinitesimal layer. The whole tower, taken at once,
is a richer object than any single layer.

This file gives the algebra that handles such towers. It builds the right notion of limit, the right notion of space
the limit lives in, and a theorem saying when a structure carried by the entire tower comes from an honest geometric
object on the larger space. The lifting questions in the next four files all depend on it.

Sections III.5–III.7 of Exposé III work over a base scheme `S` equipped with a coherent sheaf of ideals `𝓘`. They
construct schemes one **infinitesimal thickening at a time**: starting from data over `S₀ := V(𝓘)` (the closed subscheme
cut out by `𝓘`), they extend to data over `S_n := V(𝓘^{n+1})`, and finally pass to the limit to get data over the
**formal completion** `Ŝ` of `S` along `V(𝓘)`. The limit object is no longer a scheme in the ordinary sense; it is a
**formal scheme**.

This file develops just enough of the formal-scheme apparatus (EGA I §10) to support those arguments. The contrast we
need to get straight is:

> **An ordinary scheme is the spectrum of a ring. A formal scheme is the spectrum of an adic ring.** The "adic" part — a
> fixed ideal of definition and an inverse-limit structure sheaf — is what allows the formal scheme to remember the
> entire tower of thickenings simultaneously.

A reader who already knows Vakil Chapter 28 (formal functions) or EGA I §10 may skim. We rely on the language of file 03
(sheaves) and the local-completion machinery of file 04 (the completion of a noetherian local ring at its maximal
ideal). The new content is the global construction, the inverse-limit description of coherent sheaves on a formal
scheme, and the Grothendieck existence theorem that lets one **algebraize** a formal scheme back to an ordinary one.

## Recap: completion of a noetherian local ring

File 04 introduced the completion `Â` of a noetherian local ring `(A, 𝔪)` at its maximal ideal: take the inverse limit
of the quotients `A / 𝔪^{n+1}`, equipped with its natural topology where the powers of the maximal ideal go to zero. The
completion is faithfully flat over `A` (appendix `completion-flat`). It geometrizes neighborhoods of the closed point:
`Â` is "the limit of polynomial-truncation neighborhoods of the closed point of `Spec A`."

Two extensions are needed to handle Exposé III.

- The role of the maximal ideal `𝔪 ⊂ A` is played by an arbitrary ideal `𝓘 ⊂ R`, not necessarily maximal — and `R` need
    not be local. We are no longer just **completing at a point**; we are completing along a **closed subscheme**.
- The construction has to be made **functorial in schemes**: applied to `Spec R` along `V(𝓘) ⊂ Spec R`, then glued
    across Zariski covers for non-affine bases.

## 𝓘-adic completion of a noetherian ring

### Why this construction?

Before any formula, the picture. Pick a ring `R` and an ideal `𝓘`. The quotient `R/𝓘` knows the values of functions
modulo the ideal — geometrically, their values along the closed subscheme `V(𝓘)`. The quotient `R/𝓘²` adds one
layer: it knows values plus first-order data, the way a derivative knows a function plus its slope. `R/𝓘³` adds
second-order data. The tower

```text
R/𝓘  ←  R/𝓘²  ←  R/𝓘³  ←  ⋯
```

records what a function looks like to ever-higher infinitesimal order along `V(𝓘)`. Functions in `R` itself sit at the
top; each one projects to its image at every level.

The **completion** `R̂` is what you get when you let all those infinitesimal orders accumulate into single elements.
An element of `R̂` is a coherent choice of one element in each quotient — a value, a first-order increment, a
second-order increment, and so on, each compatible with the next. The result is what `R` becomes when every
infinitesimal series along `V(𝓘)` is allowed to converge. In analytic language, `R̂` is to `R` what the ring of
formal power series at a point is to the ring of polynomials.

The construction packages this as an inverse limit because every step kills slightly less of the data. The connection
backward is to file 03's first-order picture: the conormal sheaf there is `𝓘/𝓘²`, the first non-trivial layer of this
tower. Everything that file 03 did at order one, this construction does at all orders at once. The reason this matters
for SGA III is that several extension problems we will study are unsolvable at any finite order but solvable in the
limit; the completion is where those solutions live.

Let `R` be a noetherian ring and `𝓘 ⊂ R` an ideal. The **`𝓘`-adic topology** on `R` declares the powers `𝓘^{n+1}` to be
a fundamental system of open neighborhoods of zero. A sequence `(f_k)_{k ≥ 0}` in `R` is **`𝓘`-adically Cauchy** if for
every `n ≥ 0` there exists `N` with `f_j − f_k ∈ 𝓘^{n+1}` whenever `j, k ≥ N`. The **`𝓘`-adic completion** is

```text
R̂ := lim_{n ← ∞} R / 𝓘^{n+1}
```

with the inverse limit topology. A topological ring is **complete** when every Cauchy sequence in its topology has a
unique limit; for the `𝓘`-adic topology, completeness is equivalent to the natural map `R → lim_n R/𝓘^{n+1}` being an
isomorphism. It is a topological ring; the natural map `R → R̂` is the universal `𝓘`-adically continuous map to a
complete topological ring.

For `R` noetherian and `𝓘` finitely generated, `R̂` is also noetherian and the map `R → R̂` is **flat** (the appendix
row `completion-flat` covers the local case; the proof for `R̂` non-local appears in EGA 0_I §7.6.16). The map is
**faithfully flat** when restricted to the localization of `R` at primes containing `𝓘` — that is, around the closed
subscheme `V(𝓘)`.

### The thickenings `S_n = Spec(R/𝓘^{n+1})`

Set `S = Spec R` and `S_n := Spec(R / 𝓘^{n+1})` for each `n ≥ 0`. Then:

- The underlying topological space `|S_n|` of `S_n` is the closed subset `V(𝓘) ⊂ |S|`. **All `S_n` share the same
    underlying space**. They differ only in their structure sheaf: `S₀` has `𝒪_{S₀} = 𝒪_S / 𝓘`, the reduced structure on
    `V(𝓘)` (well, possibly non-reduced if `𝓘` is not radical — call it the scheme-theoretic structure on `V(𝓘)`); `S_n`
    adds in the higher jets `𝒪_S / 𝓘^{n+1}`.
- The closed immersions `S₀ ↪ S₁ ↪ S₂ ↪ ⋯ ↪ S` form an ascending chain. Each `S_n ↪ S_{n+1}` is a **square-zero
    thickening** of `S_n` by the sheaf of ideals `𝓘^{n+1} / 𝓘^{n+2}` on `S₀`.
- `lim_n 𝒪_{S_n} = R̂` as a sheaf on `|V(𝓘)|`.

The thickenings are how we will think about formal completions: **not as a single mysterious object, but as a coherent
system of ordinary schemes indexed by infinitesimal precision `n`.**

### The completed ring `R̂`

Concretely, an element of `R̂` is a sequence `(f_n)_{n ≥ 0}` with `f_n ∈ R / 𝓘^{n+1}` and `f_{n+1} ↦ f_n` under the
projection. Equivalently, when `R = A[t₁, …, t_d]` and `𝓘 = (t₁, …, t_d)`, the completion `R̂ = A[[t₁, …, t_d]]` is the
**formal-power-series ring**: each formal series is the inverse limit of its truncations.

This recovers the most important example.

### Faithfully flat completion

For `R` noetherian and `𝓘 ⊂ R` proper, the completion `R → R̂` is flat. After localizing at any prime `𝔭 ⊃ 𝓘`, the
completion becomes faithfully flat: `M ⊗_R R̂ = 0` implies `M_𝔭 = 0`. This licenses an important technique: **prove
statements after completing along `V(𝓘)`, then descend back**. The local form of this (file 04, completion of a local
ring) is `completion-flat`.

## Formal preschemes

We have all the ingredients to define formal preschemes affinely. The geometric step is to package the inverse system
`(S_n)` into a single object that remembers the topology, the structure sheaf, **and** the adic ideal `𝓘`.

### `Spf R̂` as a topologically ringed space

Given a noetherian ring `R̂` complete in the `𝓘`-adic topology (write `𝓘 ⊂ R̂` for the closure of the original ideal —
for a complete ring this is the same `𝓘`), define the **formal spectrum**

```text
Spf R̂ := (V(𝓘), 𝒪_{Spf R̂})
```

as the topologically ringed space whose underlying space is the Zariski-closed subset `V(𝓘) ⊂ Spec R̂` (open subsets of
`V(𝓘)` are intersections with open subsets of `Spec R̂`), and whose structure sheaf is

```text
𝒪_{Spf R̂} := lim_n 𝒪_{Spec(R̂ / 𝓘^{n+1})}.
```

Each `𝒪_{Spec(R̂/𝓘^{n+1})}` is an ordinary scheme structure sheaf on the same underlying space; the inverse limit
collects all the infinitesimal precision into a sheaf of topological rings. We do not view `Spf R̂` as the spectrum of a
ring in the ordinary sense.

### Globalizing: 𝓘-adic formal preschemes

A **formal prescheme** is a topologically ringed space that is **locally** isomorphic to `Spf R̂` for some noetherian
adic ring `(R̂, 𝓘)`. The morphisms between formal preschemes are continuous maps of underlying spaces with continuous
maps of structure sheaves of topological rings. A morphism `f : 𝔛 → 𝔜` is **adic** if the inverse image of an ideal of
definition of `𝔜` is an ideal of definition of `𝔛`; for the formal preschemes we will encounter, all morphisms are adic.

The formal preschemes that arise in Exposé III all have this shape: start with an ordinary noetherian scheme `S` and a
coherent sheaf of ideals `𝓘 ⊂ 𝒪_S`. Take the closed subscheme `S₀ := V(𝓘)` and the thickenings `S_n := V(𝓘^{n+1})`. Then

```text
Ŝ := (|S₀|, lim_n 𝒪_{S_n})
```

is a formal prescheme — the **`𝓘`-adic formal completion of `S`**. For `S = Spec R` affine and `𝓘 ⊂ R`, `Ŝ = Spf R̂`.

### The thickenings `X_n` of an ordinary scheme

Most often, instead of an `S` with an ideal, we start with an ordinary scheme `X` mapping to a fixed base `S` with
`𝓘 ⊂ 𝒪_S`, and form the **base-change thickenings**

```text
X_n := X ×_S S_n.
```

Each `X_n` is an ordinary scheme; the underlying space is independent of `n` (the closed subset `X ×_S S₀ ⊂ |X|`); they
form an ascending chain `X₀ ↪ X₁ ↪ ⋯ ↪ X`. The formal completion

```text
X̂ := lim_n X_n
```

(in the category of formal preschemes) is the formal completion of `X` along `X₀`. The structure sheaf of `X̂` is the
inverse limit of the `𝒪_{X_n}`.

## Coherent sheaves on a formal scheme

The category of coherent sheaves on a formal scheme is the deepest single piece of machinery we will need. Fortunately
it admits a clean inverse-limit description.

### Sheaves as inverse systems on the thickenings

A **coherent sheaf** `𝓕̂` on `𝔛 = X̂` is — equivalently — a coherent inverse system `(𝓕_n)_{n ≥ 0}` of sheaves on the
thickenings:

- For each `n`, `𝓕_n` is a coherent sheaf on `X_n`.
- For each `n`, the natural map `𝓕_{n+1} ⊗_{𝒪_{X_{n+1}}} 𝒪_{X_n} → 𝓕_n` is an isomorphism (the **inverse-system
    compatibility**).

The sheaf `𝓕̂` itself is then the inverse limit `lim_n 𝓕_n` of the sheaves on the inverse system. Tensor product,
kernels, cokernels, and Hom in `Coh(𝔛)` are computed level-by-level on the thickenings.

This is the practical handle. Whenever file 21 or 22 says "a coherent sheaf on a formal scheme," we mean a compatible
system of coherent sheaves on the thickenings.

### Coherence

The compatibility condition forces the level-wise sheaves to be "of the same shape" at every level. Specifically: if
`𝓕_n` is locally free of rank `r` on every `X_n` (which is the case in Exposé III when one is lifting a locally free
sheaf), then `𝓕̂` is **locally free of rank `r`** on `𝔛` in the appropriate formal sense, and conversely every
formal-locally-free `𝓕̂` arises this way.

### The category `Coh(𝔛)`

The takeaway: `Coh(𝔛)` is a perfectly good abelian category, with the same kinds of constructions (kernels, cokernels,
tensor products, Hom-sheaves) as on an ordinary scheme. The cohomological machinery of file 17 — `H^q(𝔛, 𝓕̂)` for `𝓕̂`
quasi-coherent — also makes sense and admits the same Čech computation on an affine formal cover.

## Smooth, étale, and proper morphisms of formal schemes

We will need the formal versions of standard adjectives.

### Inheritance from the thickenings

A morphism of formal schemes `f : 𝔛 → 𝔜` (assumed adic, with matching ideals of definition) is:

- **smooth** (resp. **étale**, **proper**) if every level `f_n : X_n → Y_n` between the thickenings is smooth (resp.
    étale, proper) as an ordinary morphism of schemes.

This is the working definition; one can equivalently formulate it via lifting properties for thickening of test objects,
mirroring the lifting characterization in §III.2 (file 19). For our purposes the level-wise definition is adequate.

### Formal smoothness, formal properness

Sometimes "formally smooth" in the SGA sense (file 19) and "smooth as a morphism of formal schemes" line up; sometimes
they do not quite. The level-wise definition above is the correct notion for the algebraization arguments. The
lifting-property characterization is what makes it work — file 19 sets that up.

A **formal scheme proper over `S`** in the sense of Exposé III III.5.6 is a formal scheme `𝔛 → Ŝ` whose every level
`𝔛_n → S_n` is proper. The classical example: `𝔛 = X̂` for `X → S` an ordinary proper scheme.

## Grothendieck's existence theorem

The pivot of the algebraization story is the following.

**Theorem (Grothendieck, EGA III §5.4.1).** _Let `R` be a complete noetherian ring with ideal of definition `𝓘`, and let
`X → Spec R` be a proper morphism. Write `X̂` for the `𝓘`-adic formal completion of `X`. Then the functor_

```text
𝓕  ⟼  𝓕̂ := (𝓕 ⊗_{𝒪_X} 𝒪_{X_n})_n
```

_is an equivalence of categories between coherent sheaves on `X` and coherent sheaves on `X̂`._

(Black box; appendix row `grothendieck-existence`. The original proof is in EGA III §5.4 and is several pages long; the
modern exposition closest to our local corpus is Vakil's Theorem on Formal Functions, which is the cohomological half of
the existence theorem.)

What this buys: a coherent sheaf on the formal scheme `X̂` is the **same data** as a coherent sheaf on `X`. Step-by-step
extensions of coherent sheaves through the thickenings, when they succeed, **come from genuine global coherent sheaves**
on the algebraic `X`. There is no separate "formal vs. algebraic" gap to bridge once `X` is proper over a complete base.

### What "algebraizable" means

A formal scheme `𝔛` is **algebraizable** if it is isomorphic to `X̂` for some ordinary scheme `X`. The Grothendieck
existence theorem does not say every formal scheme is algebraizable — only that **coherent sheaves on a formal scheme of
the form `X̂` correspond to coherent sheaves on `X`**. The algebraization of formal schemes themselves requires a
stronger criterion, the **ample-sheaf criterion** of EGA III §4.7.1:

> _If `𝔛` is proper over `Ŝ` (with `S` complete) and there exists a formal coherent sheaf `ℒ̂` on `𝔛` whose restriction
> to `𝔛₀` is an ample line bundle, then there exists an ordinary projective scheme `X → S` with `X̂ ≃ 𝔛`, and `ℒ̂` comes
> from an ample line bundle on `X`._

(Black box; appendix row `algebraization-via-ample`. This is the algebraization criterion file 22 uses to upgrade
III.7.2 to III.7.3 — for projective `X₀`, the existence of a smooth proper formal lift implies the existence of an
ordinary smooth proper algebraic lift.)

## Worked example: the formal completion of `𝔸¹_{ℤ_p}` along the closed fiber

A concrete instance to anchor the picture. Let `R = ℤ_p[t]`, the polynomial ring in one variable over the `p`-adic
integers. The ideal `𝓘 := (p) ⊂ R` cuts out the **closed fiber**

```text
S₀ = V(p) = Spec ℤ_p[t] / (p) = Spec 𝔽_p[t] = 𝔸¹_{𝔽_p}.
```

The thickenings are

```text
S_n = Spec(ℤ_p[t] / p^{n+1}) = Spec((ℤ / p^{n+1})[t]) = 𝔸¹_{ℤ/p^{n+1}}.
```

Each `S_n` is the affine line over the truncated ring; their underlying space is the same `𝔸¹_{𝔽_p}`, and they form an
ascending chain.

The **`(p)`-adic formal completion** `Ŝ = Spf R̂` has

```text
R̂ = lim_n ℤ_p[t] / p^{n+1}
   = { Σ_{i ≥ 0} a_i t^i  :  a_i ∈ ℤ_p,  a_i → 0 p-adically }.
```

This is the **Tate algebra** `ℤ_p⟨t⟩` of restricted power series: formal series in `t` with `ℤ_p`-coefficients
converging `p`-adically to zero. Elements are not arbitrary formal series (those would be `ℤ_p[[t]]`, the `t`-adic
completion); they are series whose tails go to zero in the `p`-adic topology, so they converge on the **rigid-analytic
unit disk** in the `p`-adic sense.

So:

> *The `(p)`-adic formal completion of `𝔸¹_{ℤ*p}`along its closed fiber`𝔸¹_{𝔽*p}`is the formal scheme`Spf ℤ_p⟨t⟩`.*

Coherent sheaves on `Spf ℤ_p⟨t⟩` correspond to compatible inverse systems of coherent sheaves on the `𝔸¹_{ℤ/p^{n+1}}`.
By the Grothendieck existence theorem (since the base `Spec ℤ_p` is complete and we work with proper subschemes of `𝔸¹`,
e.g. closed points), coherent sheaves on `Spf ℤ_p⟨t⟩` corresponding to coherent sheaves on a proper closed subscheme of
`𝔸¹_{ℤ_p}` lift to coherent sheaves on the algebraic `𝔸¹_{ℤ_p}`.

The role this example plays in file 21: it is the simplest case of "formal scheme algebraizable to an ordinary scheme
over a complete local base." When file 21 lifts a smooth `𝔽_p`-scheme `X₀` along the thickenings `Spec ℤ_p / p^{n+1}`,
the resulting formal scheme `𝔛` is — when `H²` vanishes — algebraic, hence comes from an honest `X / Spec ℤ_p`.

## What this prepares

We have:

- The notion of an **𝓘-adic formal scheme**, locally `Spf R̂` for `R̂` a noetherian adic ring; concretely, an inverse
    system of ordinary schemes `(S_n)` sharing an underlying space.
- The category of **coherent sheaves on a formal scheme**, captured as compatible inverse systems of coherent sheaves on
    the thickenings.
- **Smooth, étale, proper** for formal morphisms, defined level-wise.
- **Grothendieck's existence theorem**: for `X` proper over a complete `R`, coherent sheaves on `X̂` and coherent
    sheaves on `X` are equivalent.
- The **ample-sheaf algebraization criterion** (EGA III §4.7.1): a proper formal scheme over a complete base is
    algebraic whenever it carries a formal sheaf restricting to an ample line bundle on the closed fiber.

These are exactly the ingredients files 21 and 22 will use:

- **File 21 (§§5–6)** lifts smooth schemes one thickening at a time. The cohomological obstruction theory of file 17
    says when a single step `X_n → X_{n+1}` succeeds. Stringing together successful steps gives a **formal smooth
    scheme** `𝔛 → Ŝ`. The cohomological vanishing hypotheses are statements about coherent sheaves on the formal scheme,
    which by the inverse- system description reduce to statements on the `X_n`.
- **File 22 (§7)** algebraizes the formal scheme `𝔛`. For `𝔛` formal-projective with an ample formal sheaf — guaranteed
    when `H²(X₀, 𝒪_{X₀}) = 0` lets one lift an ample line bundle from `X₀` to `𝔛` — the algebraization criterion
    produces an ordinary smooth projective `X / Spec R`. The headline application is to **smooth proper curves over
    `k`**, which always lift (their `H²(𝒪)` and `H²(𝔤)` both vanish on dimension grounds).

## What to remember

- The **`𝓘`-adic completion** of a noetherian ring `R` is `R̂ = lim R/𝓘^{n+1}`. For `R = A[t₁, …, t_d]` and
    `𝓘 = (t₁, …, t_d)`, this is the formal-power-series ring `A[[t₁, …, t_d]]`.
- A **formal prescheme** is locally `Spf R̂` for `R̂` an adic ring; it is the limit of an inverse system of ordinary
    schemes `(S_n)` with common underlying space.
- The **completion of an ordinary scheme** `X → S` along a closed subscheme `X₀ ⊂ X` is the formal scheme
    `X̂ = lim_n X_n`, where `X_n` are the thickenings.
- **Coherent sheaves** on a formal scheme are compatible inverse systems of coherent sheaves on the thickenings.
- **Grothendieck's existence theorem** (EGA III §5.4.1): for `X` proper over complete `R`, `Coh(X) ≃ Coh(X̂)`.
- **Algebraization of a formal scheme** requires more than the existence theorem for sheaves; the standard criterion
    (EGA III §4.7.1) is that `𝔛` is proper over the complete base and carries a formal sheaf restricting to an ample
    sheaf on the closed fiber.
- The worked example: the `(p)`-adic formal completion of `𝔸¹_{ℤ_p}` is `Spf ℤ_p⟨t⟩`, the Tate algebra of restricted
    power series. This is the prototype of a formal scheme over a complete base.
