# Rewritten Exposé XII, section XII.4 — cohomological GAGA

<!-- source: XII.4 -->

## What this file is about

A coherent sheaf is a bundle of linear data spread across a geometric object — a small vector space at each point,
varying under controlled rules. Its natural invariants are cohomology groups, which measure how badly local pieces of
the data fail to glue into a global object. Over the complex numbers every coherent sheaf has two parallel lives,
algebraic and analytic, and the question is whether the cohomology groups agree.

They agree whenever the underlying object is compact in the right algebraic sense. The result generalises in two
directions: from a single space to a family, and from compact spaces inside a fixed ambient space to a more flexible
class. The categories of coherent sheaves match on the two sides, maps between two such objects correspond, and
finite covers of one match finite covers of the other. The last consequence feeds the Riemann existence theorem of
the next file.

Files 57 and 58 built the analytification functor `Φ : X ↦ X^an`, its functoriality, the inverse-image functor
`F ↦ F^an = φ^* F` on coherent sheaves (exact, faithful, conservative), and the two property dictionaries between
`X` and `X^an` and between `f` and `f^an`. Together these results say: locally and globally, the analytic and
algebraic categories carry the same property data over `ℂ`.

This file (§XII.4) handles the *cohomological* side of the comparison. The cleanest form: for a *proper* morphism
`f : X → Y` of `ℂ`-schemes locally of finite type and a coherent sheaf `F` on `X`, the canonical comparison map

```text
θ_p : (R^p f_* F)^an → R^p f_*^an(F^an)
```

is an isomorphism for every `p ≥ 0` (XII.4.2). Specialised to `Y = Spec ℂ` (so `f` is the structure morphism of a
proper `ℂ`-scheme), this gives `H^p(X, F) ≃ H^p(X^an, F^an)` (XII.4.3). Globalised, it gives an *equivalence of
categories* `Coh(X) ≃ Coh(X^an)` for `X` proper (XII.4.4), full faithfulness of the analytification functor
on the category of proper `ℂ`-schemes (XII.4.5), and an equivalence on finite (resp. finite étale) schemes
(XII.4.6) — which prepares the ground for the Riemann existence theorem of file 60.

The proof of XII.4.2 has the standard two-stage shape: handle the *projective* case directly via a standard
Stein cover of `ℙ^r_𝒴` and Cartan's Theorem B, then reduce the *proper* case to the projective case via Chow's
lemma and EGA III §3.1.2 dévissage. This is the form Serre 1956 found for the absolute projective GAGA; XII.4.2
is the relative-and-proper extension.

The slogan that emerges by the end of this file: **on a proper `ℂ`-scheme, coherent algebraic geometry and
coherent analytic geometry agree, including at the level of cohomology, higher direct images, and morphism sets.**

______________________________________________________________________

## §XII.4.0 — Bridge: what comparison map we want

<!-- source: XII.4 -->

On a proper complex variety, an algebraic coherent sheaf and its analytic counterpart have the same cohomology. That
is GAGA. Serre proved it in 1956 for the projective case; XII.4 extends both sides — projective to proper, single
spaces to families — so the comparison runs at the level of higher direct images. The formula version:
for a *projective* `ℂ`-scheme `X` and a coherent `𝒪_X`-module `F` (Serre 1956, `gaga-serre-original`),

```text
H^p(X, F) ≃ H^p(X^an, F^an)    for every  p ≥ 0,
```

and the analytification functor `F ↦ F^an` is an equivalence of categories `Coh(X) ≃ Coh(X^an)`. Serre's proof
proceeds by:

1. Computing `H^p(ℙ^r_ℂ, 𝒪(d))` on both sides (algebraic and analytic) via Čech cohomology on a standard cover,
    and showing the two computations match.
2. Deriving the general projective case by twisting and resolving.

XII.4 generalises this in two directions at once. **First**, the base `Spec ℂ` is replaced by an arbitrary
`ℂ`-scheme `Y` locally of finite type, and the absolute cohomology groups are replaced by relative higher direct
images `R^p f_*`. **Second**, the projective hypothesis is replaced by the weaker hypothesis that `f : X → Y` is
proper. The first generalisation is essentially formal — we just need to be careful about how `R^p f_*` is
constructed in the relative setting and where the analytification map enters. The second is the substantive
step, and it uses Chow's lemma.

Once the comparison map `θ_p` is built (XII.4.1) and `θ_p` is shown to be an isomorphism (XII.4.2), the other
four results (XII.4.3, XII.4.4, XII.4.5, XII.4.6) follow by specialisation: take `Y = Spec ℂ` for XII.4.3;
combine XII.4.3 with the `Ext` long exact sequence and noetherian induction for XII.4.4; characterise morphisms
as graphs and apply XII.4.4 for XII.4.5; recognise finite morphisms as coherent algebras for XII.4.6.

The full payoff of file 59 is therefore concentrated in XII.4.1 and XII.4.2. Everything else is a corollary.

______________________________________________________________________

## §XII.4.1 — The canonical comparison map `θ_p`

<!-- source: XII.4.1 -->

### Construction of `θ_p`

<!-- source: XII.4.1 -->

Let `f : X → Y` be a morphism of `ℂ`-schemes locally of finite type. Consider the analytification square

```text
X^an --φ→ X
 |        |
f^an    f
 |        |
Y^an --ψ→ Y.
```

Both `φ` and `ψ` are flat (XII.1.1 (3)) and `f^an` is the analytification of `f` (XII.1.2). For an `𝒪_X`-module
`F`, we want to compare two sheaves on `Y^an`:

- The **analytification of `R^p f_* F`**, which is `ψ^* (R^p f_* F) = (R^p f_* F)^an`.
- The **`p`-th derived direct image of `F^an = φ^* F`**, which is `R^p f_*^an(F^an)`.

To construct a canonical map `θ_p` between these, we use the Leray spectral sequences for the two compositions
`X^an → X → Y` and `X^an → Y^an → Y`. Since both compositions equal the single morphism `X^an → Y`, the abutments
of the two spectral sequences agree, and we can extract a comparison map from the edge homomorphisms.

Concretely: for any `𝒪_X`-module `F`, the canonical map `F → φ_* φ^* F = φ_* F^an` is the unit of the
`(φ^*, φ_*)` adjunction. Applying `R^p f_*`, we get

```text
R^p f_* F  --i→  R^p f_*(φ_* F^an).
```

Now apply the Leray spectral sequence for the composition `X^an → X → Y` (acting on `F^an`):

```text
E_2^{p, q} = R^p f_*(R^q φ_* F^an)  ⇒  R^{p+q}(f ∘ φ)_* F^an.
```

Edge homomorphisms give

```text
R^p f_*(φ_* F^an) = R^p f_*(R^0 φ_* F^an)  --j→  R^p(f ∘ φ)_* F^an.
```

Apply the Leray spectral sequence for the composition `X^an → Y^an → Y` (acting on `F^an`):

```text
E_2^{p, q} = R^p ψ_*(R^q f_*^an F^an)  ⇒  R^{p+q}(ψ ∘ f^an)_* F^an = R^{p+q}(f ∘ φ)_* F^an.
```

Edge homomorphisms give

```text
R^p(f ∘ φ)_* F^an  --k→  ψ_*(R^p f_*^an F^an).
```

Combining `i`, `j`, `k`:

```text
R^p f_* F  --i→  R^p f_*(φ_* F^an)  --j→  R^p(f ∘ φ)_* F^an  --k→  ψ_*(R^p f_*^an F^an).
```

The composition `k ∘ j ∘ i : R^p f_* F → ψ_*(R^p f_*^an F^an)` is an `𝒪_Y`-linear map. By the
`(ψ^*, ψ_*)` adjunction, this corresponds to a map

<!-- label: eq:XII.4.1.1 -->

```text
(4.1.1)   θ_p : (R^p f_* F)^an = ψ^*(R^p f_* F)  →  R^p f_*^an(F^an).
```

This is the **canonical comparison map** of degree `p`.

> **Slogan.** *`θ_p` is the comparison datum.* It is constructed once and for all from the Leray spectral
> sequences of the analytification square. The next subsection (XII.4.2) is the claim that, for `f` proper and
> `F` coherent, every `θ_p` is an isomorphism.

#### Aside (naturality of `θ_p`).

The construction of `θ_p` is functorial in `F` (because each of `i, j, k` is) and contravariant in `f` (the
edge maps reverse direction). In particular, `θ_p` is compatible with composition of morphisms: for `f : X → Y`
and `g : Y → Z`, the comparison map `θ_p` for `g ∘ f` factors through `θ_p` for `f` and `θ_p` for `g` in a
Leray-spectral-sequence sense. This compatibility will be used implicitly in the dévissage argument of XII.4.2
Stage 2.

______________________________________________________________________

## §XII.4.2 — The GAGA theorem (proper case)

<!-- source: XII.4.2 -->

### Theorem XII.4.2 — `θ_p` is an isomorphism for proper `f` and coherent `F`

<!-- source: XII.4.2 -->

**Theorem XII.4.2.** Let `f : X → Y` be a *proper* morphism of `ℂ`-schemes locally of finite type, and let `F`
be a coherent `𝒪_X`-module. Then for every integer `p ≥ 0`, the canonical map

```text
θ_p : (R^p f_* F)^an  →  R^p f_*^an(F^an)
```

(constructed in XII.4.1) is an isomorphism.

*This result says:* the higher-direct-image functors `R^p f_*` for proper `f` and coherent `F` are preserved by
analytification. In particular (taking `Y = Spec ℂ` and `F = 𝒪_X`), the algebraic and analytic cohomology
groups of a proper `ℂ`-scheme agree.

#### Proof structure.

The proof has two stages. **Stage 1** handles the case where `f` is projective. We reduce to `f = pr_2 : ℙ^r_Y →
Y` (the relative projective space) and `F = 𝒪`, then `F = 𝒪(d)`, by twisting and standard
projective-cohomology computations. The Stein-cover analytic-side computation matches the algebraic-side
computation. **Stage 2** handles the general proper case by dévissage (EGA III §3.1.2): a class `𝓚` of coherent
sheaves satisfying the conclusion of XII.4.2 that is closed under extensions and direct factors and contains a
generator at every point coincides with all coherent sheaves. We build a generator using Chow's lemma and EGA
III §2.2.1.

#### Stage 1 — the projective case.

<!-- source: XII.4.2 -->

Suppose `f : X → Y` is *projective*. We may further reduce to the case `X = ℙ^r_Y`, `f = pr_2`. (Indeed, every
projective morphism factors through a closed immersion into some relative projective space; the closed
immersion has trivial higher direct images, and the comparison reduces to the projective-space case via the
adjunction `i_* i^* = id` on coherent sheaves of the closed subscheme.)

So let `𝒴 := Y^an` and `𝓟 := ℙ^r_𝒴 = (ℙ^r_Y)^an`. We claim

```text
f_*^an 𝒪_𝓟  =  𝒪_𝒴,         R^p f_*^an(𝒪_𝓟)  =  0    for  p > 0.
```

To verify these relations, we may localise on `𝒴`. Hence we may assume `𝒴 = 𝓑` is an open ball in some `ℂⁿ` —
in particular `𝒴` is a Stein analytic space and so is every product `𝓑 × 𝓔^r`.

Consider the **standard cover** of `𝓟 = ℙ^r_𝓑` by `r + 1` open subsets `𝓤_0, …, 𝓤_r`:

```text
𝓤_i  =  𝓑 × { [x_0 : … : x_r] : x_i ≠ 0 }  ≃  𝓑 × 𝓔^r.
```

Each `𝓤_i` is isomorphic to `𝓑 × 𝓔^r` (an open polydisc-cylinder), hence is Stein. Moreover, every finite
intersection `𝓤_{i_0} ∩ … ∩ 𝓤_{i_p}` is also Stein (an open polydisc-cylinder times a fixed open subset of
`(ℂ^*)^p`). By Cartan's Theorem B (`cartan-faisceaux-analytiques`), for every coherent analytic sheaf `𝓕` on
`𝓟` and every finite intersection `𝓤_{i_0} ∩ … ∩ 𝓤_{i_p}`,

```text
H^q(𝓤_{i_0} ∩ … ∩ 𝓤_{i_p}, 𝓕)  =  0    for  q ≥ 1.
```

This is Leray's acyclic-cover condition. Consequently, for every coherent analytic `𝓕`, the canonical map

```text
Ȟ^p({𝓤_i}, 𝓕)  →  H^p(𝓟, 𝓕)
```

is an isomorphism for every `p ≥ 0`.

Apply this to `𝓕 = 𝒪_𝓟`. The Čech complex of `𝒪_𝓟` over the cover `{𝓤_i}` can be computed explicitly. On each
`𝓤_i ≃ 𝓑 × 𝓔^r`, sections of `𝒪_𝓟` are holomorphic functions in coordinates `(b, u_1, …, u_r)` with
`u_j = x_j / x_i` for `j ≠ i`. On a higher intersection `𝓤_{i_0} ∩ … ∩ 𝓤_{i_p}`, sections of `𝒪_𝓟` are *Laurent
series* in `(u_j)_{j ∈ I}` (where `I` is the index set), with the coefficient series convergent on `𝓑`.

A computation in Laurent series — completely parallel to Serre's lemma 5 of `[XII.10, no. 12]` (cf.
`gaga-serre-original`) — gives

```text
H^0(𝓟, 𝒪_𝓟)  =  Γ(𝓑, 𝒪_𝓑) · 1  ≃  H^0(𝓑, 𝒪_𝓑),         H^p(𝓟, 𝒪_𝓟)  =  0   for  p > 0.
```

The same computation on the algebraic side (Serre 1956 lemma 5) gives the same answer. The two computations
*match term-by-term*: each Laurent series in `(u_j)` matches an algebraic polynomial in `(u_j)` after passage
through Čech cohomology, because the Stein cohomology of `𝒪` on `𝓤_{i_0} ∩ … ∩ 𝓤_{i_p}` is exactly the
convergent series of the algebraic-side `H^0(U_{i_0} ∩ … ∩ U_{i_p}, 𝒪) = Γ(U_{i_0} ∩ … ∩ U_{i_p}, 𝒪)`.

This proves `θ_p` is an iso for `F = 𝒪_𝓟`.

For `F = 𝒪(d)` an arbitrary line bundle on `𝓟`, the same Čech / Laurent-series computation works, with the
Laurent series weighted by degree `d`. The result matches the algebraic-side computation Serre 1956 of
`H^p(ℙ^r_Y, 𝒪(d))`.

For a general coherent sheaf `F` on `ℙ^r_Y`, present `F` as a quotient `⊕ 𝒪(d_i) ↠ F`, take a resolution

```text
…  →  ⊕ 𝒪(d_i^{(2)})  →  ⊕ 𝒪(d_i^{(1)})  →  ⊕ 𝒪(d_i^{(0)})  →  F  →  0
```

(every coherent sheaf on `ℙ^r_Y` admits such a resolution), and combine: each `⊕ 𝒪(d_i^{(p)})` has `θ_p`-iso for
its analytification, so a five-lemma argument applied to the long exact sequence in Čech cohomology yields
`θ_p`-iso for `F`. Spelling out the details requires bookkeeping — the resolution is finite (Hilbert syzygy
theorem on `ℙ^r`) and the five-lemma applies hereditarily — but the conceptual argument is the same as Serre
1956's lemma 5.

This completes Stage 1 of the proof. For projective `f`, `θ_p` is an iso for every coherent `F` and every
`p ≥ 0`. ∎_{stage 1}

#### Stage 2 — the proper case via Chow + dévissage.

<!-- source: XII.4.2 -->

Let `f : X → Y` be *proper* (but not necessarily projective). We use Chow's lemma to reduce to the projective
case via dévissage.

Define the class `𝓚` of coherent `𝒪_X`-modules satisfying the conclusion of XII.4.2:

```text
𝓚  :=  { F ∈ Coh(X)  :  θ_p (F)  is an iso for every  p ≥ 0 }.
```

We will verify three properties of `𝓚`:

1. **`𝓚` is closed under short exact sequences**: if `0 → F' → F → F'' → 0` is a short exact sequence in
    `Coh(X)` with `F', F'' ∈ 𝓚`, then `F ∈ 𝓚`.
2. **`𝓚` is closed under direct factors**: if `F ⊕ G ∈ 𝓚`, then `F ∈ 𝓚`.
3. **`𝓚` contains a generator**: for every point `x ∈ X`, there exists `F ∈ 𝓚` with `F_x ≠ 0`.

By the EGA III §3.1.2 dévissage theorem (`ega-iii-3-1-2-devissage`), these three conditions imply
`𝓚 = Coh(X)`, completing the proof of XII.4.2.

**Verification of (1).** Apply analytification to `0 → F' → F → F'' → 0` (this preserves exactness, by
XII.1.3.1) to get `0 → F'^an → F^an → F''^an → 0`. Take higher direct images on both the scheme and the
analytic side:

```text
…  → R^p f_* F'      → R^p f_* F      → R^p f_* F''      → R^{p+1} f_* F'      → …
                                       ↓                                       ↓
…  → R^p f_*^an F'^an → R^p f_*^an F^an → R^p f_*^an F''^an → R^{p+1} f_*^an F'^an → …
```

After analytifying the top row and identifying `(R^p f_* F)^an` with `R^p f_*^an F^an` via `θ_p`, the diagram
becomes a morphism of long exact sequences. If `F', F'' ∈ 𝓚`, the columns at positions `F', F''` and
`F', F''` are isos. The five-lemma applied at the central column gives `F ∈ 𝓚`.

**Verification of (2).** If `F ⊕ G ∈ 𝓚`, then for every `p`, `θ_p(F ⊕ G) = θ_p(F) ⊕ θ_p(G)` is an iso. The
direct sum of two maps is an iso iff each summand is. Hence `θ_p(F)` is an iso for every `p`, i.e. `F ∈ 𝓚`.

**Verification of (3).** Fix `x ∈ X`; we construct `F ∈ 𝓚` with `F_x ≠ 0`.

We may restrict to the case `X` irreducible with generic point `x` (by replacing `X` with the closure of `{x}`
in `X` and adjusting). Since `f` is proper and `X` is irreducible, the image `f(X)` is a closed irreducible
subset of `Y`. We may further assume `Y` is noetherian (by writing `Y` as a union of noetherian affine opens
and working locally on `Y`).

Apply **Chow's lemma** (EGA II §5.6.1; `chow-lemma`) to `f : X → Y`: there exist a *projective* `Y`-scheme `X'`
and a *projective surjective* morphism `g : X' → X`. The composition `f ∘ g : X' → Y` is projective.

By EGA III §2.2.1 (`ega-iii-2-2-1-cohomology-vanishing`), there exists an integer `n` such that
`R^p g_*(𝒪_{X'}(n)) = 0` for every `p > 0`, and such that the canonical map `g^* g_*(𝒪_{X'}(n)) → 𝒪_{X'}(n)` is
surjective (here `𝒪_{X'}(n)` denotes the `n`-th twist of the very ample line bundle along `g`).

Define `F := g_*(𝒪_{X'}(n))`. We claim `F ∈ 𝓚` and `F_x ≠ 0`.

For `F_x ≠ 0`: the map `g^* F → 𝒪_{X'}(n)` is surjective on `X'`, which sits above the generic point `x` of
`X`. Taking stalks at `x` gives `F_x ⊗ k(x) ≠ 0`, hence `F_x ≠ 0`.

For `F ∈ 𝓚`: compute `R^p f_* F` using the **Leray spectral sequence**

```text
R^p f_*(R^q g_*(𝒪_{X'}(n)))  ⇒  R^{p+q}(f ∘ g)_*(𝒪_{X'}(n)).
```

The `E_2` page degenerates because `R^q g_*(𝒪_{X'}(n)) = 0` for `q > 0` (by our choice of `n`). Hence

```text
R^p f_* F  =  R^p f_*(g_* 𝒪_{X'}(n))  ≃  R^p(f ∘ g)_*(𝒪_{X'}(n)).
```

The same calculation holds on the analytic side, by the analytic Leray spectral sequence and the analytic
analogue of EGA III §2.2.1 (Cartan's Theorem A on Stein covers, plus the analytic higher-direct-image
vanishing). So

```text
R^p f_*^an(F^an)  ≃  R^p(f ∘ g)_*^an(𝒪_{X'}(n)^an).
```

These two iso identifications fit into a commutative diagram with the comparison maps `θ_p` for `F` (on `X`)
and for `𝒪_{X'}(n)` (on `X'`):

```text
(R^p f_* F)^an           ≃  (R^p (f ∘ g)_*(𝒪_{X'}(n)))^an
      ↓ θ_p (F)                       ↓ θ_p (𝒪_{X'}(n))
R^p f_*^an(F^an)        ≃  R^p (f ∘ g)_*^an(𝒪_{X'}(n)^an).
```

The right-hand vertical arrow is the comparison map `θ_p` for `𝒪_{X'}(n)` along the *projective* morphism
`f ∘ g`. By Stage 1, this is an isomorphism. So the left-hand vertical arrow `θ_p(F)` is also an isomorphism,
i.e. `F ∈ 𝓚`.

This verifies (3) and completes the proof of XII.4.2. ∎

> **Slogan.** *Chow's lemma + projective GAGA + EGA III dévissage = relative proper GAGA.* The projective case
> is Serre 1956's standard Stein-cover computation; the proper case is one Chow projection away.

#### Aside (where the proof would break for non-proper `f`).

The dévissage argument fails for non-proper `f` because EGA III §2.2.1 — the existence of high enough `n` making
`g^* g_*(𝒪_{X'}(n)) → 𝒪_{X'}(n)` surjective — requires the *projective* family `g : X' → X` to be proper over
the *projective* base coming from Chow's lemma. Without properness of `f`, Chow's lemma does not produce a
*proper* `X'`, and the cohomological vanishing of `R^q g_*` fails.

This is the structural reason why XII.4.2 demands properness, and why the *full* analytic-comparison statement
for *non-proper* `f` is much weaker (sometimes much stronger; see Serre's "Géométrie algébrique et géométrie
analytique" for the *quasi-projective* case, where one gets a comparison up to **étale** locally-trivial
modifications — beyond the scope of this gentle SGA).

______________________________________________________________________

## §XII.4.3 — Corollary: cohomology agrees on proper `ℂ`-schemes

<!-- source: XII.4.3 -->

### Corollary XII.4.3 — `H^p(X, F) ≃ H^p(X^an, F^an)` for `X` proper

<!-- source: XII.4.3 -->

**Corollary XII.4.3.** Let `X` be a proper `ℂ`-scheme, and let `F` be a coherent `𝒪_X`-module. Then for every
integer `p ≥ 0`, the canonical morphism

```text
H^p(X, F)  →  H^p(X^an, F^an)
```

is an isomorphism.

*This result says:* coherent-sheaf cohomology of a proper `ℂ`-scheme is the same whether computed algebraically
or analytically. This is the absolute GAGA principle in its sharpest form.

**Proof.** Apply XII.4.2 to the structure morphism `f : X → Y = Spec ℂ`. Then `R^p f_* F = H^p(X, F)` (as
`ℂ`-vector spaces, viewed as `𝒪_Y`-modules on the one-point base `Y`), and similarly `R^p f_*^an F^an =
H^p(X^an, F^an)`. The analytification of a `ℂ`-vector space at a single point is just the `ℂ`-vector space
itself. So `θ_p` becomes the canonical map `H^p(X, F) → H^p(X^an, F^an)`, which by XII.4.2 is an iso. ∎

> **Slogan.** *Coherent-sheaf cohomology agrees on proper `ℂ`-schemes.* This is the absolute version of XII.4.2.

______________________________________________________________________

## §XII.4.4 — Equivalence of coherent-sheaf categories

<!-- source: XII.4.4 -->

### Theorem XII.4.4 — `Coh(X) ≃ Coh(X^an)` for `X` proper

<!-- source: XII.4.4 -->

**Theorem XII.4.4.** Let `X` be a proper `ℂ`-scheme. The functor `F ↦ F^an` which sends every coherent
`𝒪_X`-module to its analytification on `X^an` is an *equivalence of categories*

```text
Coh(X)  ≃  Coh(X^an).
```

*This result says:* on a proper `ℂ`-scheme, every coherent analytic sheaf comes from a coherent algebraic
sheaf, uniquely up to isomorphism. The analytic and algebraic categories of coherent sheaves are identical.

**Proof.** We verify the two clauses: fully faithful and essentially surjective.

#### Block (1): the functor is fully faithful.

Let `F, G ∈ Coh(X)`. The Hom-set comparison is

```text
Hom_{𝒪_X}(F, G)  →  Hom_{𝒪_{X^an}}(F^an, G^an).
```

Both sides are global sections of internal Hom-sheaves: `Hom_{𝒪_X}(F, G) = H^0(X, SheafHom_{𝒪_X}(F, G))` and
`Hom_{𝒪_{X^an}}(F^an, G^an) = H^0(X^an, SheafHom_{𝒪_{X^an}}(F^an, G^an))` (EGA `0_I` 6.7.6 and analytic analogue
of same).

Now `SheafHom_{𝒪_X}(F, G)` is a coherent `𝒪_X`-module (because `F` is coherent and `G` is coherent — kernels of
the standard short exact sequences are then coherent). By XII.4.3 applied to this coherent sheaf,

```text
H^0(X, SheafHom_{𝒪_X}(F, G))  ≃  H^0(X^an, SheafHom_{𝒪_X}(F, G)^an).
```

And by basic functoriality of pullback, `SheafHom_{𝒪_X}(F, G)^an ≃ SheafHom_{𝒪_{X^an}}(F^an, G^an)` (we are
using that `F`, `G` are coherent, so the pullback of the SheafHom is the SheafHom of the pullbacks).

Combining: `Hom_{𝒪_X}(F, G) ≃ Hom_{𝒪_{X^an}}(F^an, G^an)`. The functor is fully faithful.

#### Block (2): the functor is essentially surjective.

This is the substantive part. Let `𝓕` be a coherent analytic sheaf on `X^an`. We must produce a coherent
algebraic sheaf `F` on `X` with `F^an ≃ 𝓕`.

**Reduction to projective.** When `X` is projective, this is Serre 1956's original projective GAGA
(`gaga-serre-original`, theorem 3 of `[XII.10, no. 12]`). Take this as the base case.

**Noetherian induction.** Reduce the proper case to the projective case by **Chow's lemma** + noetherian
induction on `X`.

Let `X'` be a *projective* `ℂ`-scheme, let `f : X' → X` be a projective surjective morphism (Chow's lemma), and
let `U ⊂ X` be a dense open such that `f` induces an isomorphism `f^{-1}(U) ≃ U`. We argue by noetherian
induction on `X`: assume that for every coherent analytic `𝓖` on `X^an` whose support is contained in `Y^an` for
some proper closed subscheme `Y ⊊ X`, there exists a coherent algebraic sheaf `G` on `X` with `G^an ≃ 𝓖`.

Given our coherent analytic `𝓕` on `X^an`, define coherent analytic sheaves `𝓚` and `𝓛` on `X^an` by the exact
sequence

```text
0  →  𝓚  →  𝓕  →  f_*^an f^{an*} 𝓕  →  𝓛  →  0.
```

(The map `𝓕 → f_*^an f^{an*} 𝓕` is the unit of the `(f^{an*}, f_*^an)` adjunction. Its kernel is `𝓚` and its
cokernel is `𝓛`.)

Since `X'` is projective, by the projective case of the theorem there exists a coherent algebraic sheaf `F'` on
`X'` with `F'^an ≃ f^{an*} 𝓕`. By XII.4.2 applied to the proper morphism `f : X' → X`,

```text
(f_* F')^an  ≃  f_*^an F'^an  =  f_*^an f^{an*} 𝓕.
```

So `f_* F'` is a coherent algebraic sheaf on `X` whose analytification matches the analytic middle term of our
sequence.

Now `𝓚|_{U^an} = 𝓛|_{U^an} = 0` because `f` restricts to an iso over `U`, so the unit map `𝓕 → f_*^an f^{an*} 𝓕`
is an iso on `U^an`. By the noetherian inductive hypothesis applied to `𝓚` and `𝓛` (their supports are contained
in `(X − U)^an = Y^an` for `Y = X − U ⊊ X`), there exist coherent algebraic sheaves `K, L` on `X` with
`K^an ≃ 𝓚` and `L^an ≃ 𝓛`.

By block (1) — full faithfulness — the analytic morphism `f_*^an f^{an*} 𝓕 → 𝓛` comes from a unique algebraic
morphism `f_* F' → L`. Define `I := Ker(f_* F' → L)`.

We have an exact sequence on `X^an`:

```text
0  →  𝓚  →  𝓕  →  I^an  →  0
```

(here `I^an` is the kernel of `(f_* F')^an → L^an = 𝓛`, which by exactness of analytification (XII.1.3.1) is
the same as `(Ker(f_* F' → L))^an = I^an`). So `𝓕` is an extension of `I^an` by `𝓚 = K^an`.

It remains to show that this extension comes by inverse image from an extension of `I` by `K` on `X`. The
extension `0 → 𝓚 → 𝓕 → I^an → 0` is classified by an element of `Ext^1_{𝒪_{X^an}}(I^an, K^an)`. We need to show
this element lifts to `Ext^1_{𝒪_X}(I, K)`.

That is, we need:

<!-- label: eq:XII.4.* -->

```text
(*)   Ext^1_{𝒪_X}(I, K)^an  ≃  Ext^1_{𝒪_{X^an}}(I^an, K^an).
```

(The source prints `q ≠ 1` here, but the argument needs the case `q = 1`. We follow the corrected source.)

For (*), we use the **`ExtSheaf` comparison + Grothendieck spectral sequence**. Step 1: the analytification of
`ExtSheaf` agrees with the analytic `ExtSheaf` of the analytifications:

```text
ExtSheaf^q_{𝒪_X}(I, K)^an  ≃  ExtSheaf^q_{𝒪_{X^an}}(I^an, K^an)    for every  q ≥ 0.
```

This is `ega-0-12-3-5-sheaf-ext` (EGA `0_III` §12.3.5) — the sheaf-Ext is local on `X`, so it agrees with its
analytification on coherent sheaves, with the iso coming from the local-ring iso (XII.1.1 (2)) at each point.

Step 2: there is a Grothendieck spectral sequence on each side relating `Hᵖ(X, ExtSheaf^q)` to global `Ext^{p+q}`
(EGA `0_III` §12.3.5):

```text
H^p(X, ExtSheaf^q_{𝒪_X}(I, K))      ⇒  Ext^{p+q}_{𝒪_X}(I, K),
H^p(X^an, ExtSheaf^q_{𝒪_{X^an}}(I^an, K^an))  ⇒  Ext^{p+q}_{𝒪_{X^an}}(I^an, K^an).
```

By XII.4.3 + Step 1, the `E_2^{p, q}` pages agree under analytification. Hence the abutments agree, giving
(*) for every `q ≥ 0`, in particular for `q = 1`. This is what we needed.

Hence the analytic extension `0 → 𝓚 → 𝓕 → I^an → 0` comes by analytification from an algebraic extension
`0 → K → F → I → 0` on `X`. Then `F^an ≃ 𝓕`, completing the essentially-surjective step.

This proves XII.4.4. ∎

> **Slogan.** *On a proper `ℂ`-scheme, the analytification functor `F ↦ F^an` is an equivalence of categories
> `Coh(X) ≃ Coh(X^an)`.*

#### Aside (the `q = 1` correction).

The source prints `q ≠ 1` in equation `(*)`. The argument in the surrounding text actually needs the case
`q = 1` (to lift the `Ext^1`-class classifying the extension). The translator's correction is a *mathematical*
correction, not a stylistic one. The need for `q = 1` is the substantive content of the essential-surjectivity
proof: it is where the comparison of `Ext^1` groups enters, and where the Grothendieck spectral sequence in
`ExtSheaf` becomes essential.

This is one of three or four such mathematical corrections preserved in the English translation of SGA 1
Exposé XII.

______________________________________________________________________

## §XII.4.5 — Hom comparison for proper `ℂ`-schemes

<!-- source: XII.4.5 -->

### Corollary XII.4.5 — `Hom_ℂ(X, Y) ≃ Hom(X^an, Y^an)` for `X, Y` proper

<!-- source: XII.4.5 -->

**Corollary XII.4.5.** Let `X, Y` be proper `ℂ`-schemes. The canonical map

```text
Hom_ℂ(X, Y)  →  Hom_{AnSp/ℂ}(X^an, Y^an)
```

is a bijection. Equivalently, the analytification functor `Φ : Sch_{proper}/ℂ → AnSp/ℂ` is fully faithful.

*This result says:* there is no analytic morphism between proper `ℂ`-schemes that is not the analytification of
an algebraic morphism.

**Proof.** To give a morphism `X → Y` is equivalent to giving its **graph**, that is, a closed subscheme `Z ⊂
X × Y` such that the restriction of the first projection `X × Y → X` to `Z` is an isomorphism.

To give an analytic morphism `X^an → Y^an` is equivalent to giving its **analytic graph**, that is, a closed
analytic subspace `𝓩 ⊂ X^an × Y^an = (X × Y)^an` such that the restriction of the first projection to `𝓩` is
an analytic isomorphism.

A closed subscheme of `X × Y` (resp. a closed analytic subspace of `(X × Y)^an`) is the zero locus of a coherent
sheaf of ideals on `𝒪_{X × Y}` (resp. `𝒪_{(X × Y)^an}`). By XII.4.4 applied to the *proper* `ℂ`-scheme `X × Y`,
coherent sheaves of ideals on the algebraic and analytic sides are in bijection.

The "first projection is iso" condition transfers between algebraic and analytic by XII.3.2 (ix) and XII.3.2
(v), using properness of `X × Y → X`. So algebraic graphs correspond bijectively to analytic graphs, and
morphisms agree. ∎

> **Slogan.** *Analytification is fully faithful on proper `ℂ`-schemes.* No analytic information at the level
> of morphism sets is created or lost.

______________________________________________________________________

## §XII.4.6 — Corollary: finite / finite étale categories

<!-- source: XII.4.6 -->

### Corollary XII.4.6 — analytification is an equivalence on finite and on finite étale categories

<!-- source: XII.4.6 -->

**Corollary XII.4.6.** Let `X` be a proper `ℂ`-scheme. The functor `X' ↦ X'^an` is an equivalence of categories
from the category of *finite* `X`-schemes (resp. *finite étale* `X`-schemes) to the category of *finite*
analytic `X^an`-spaces (resp. *finite étale* analytic `X^an`-spaces).

*This result says:* finite (resp. finite étale) coverings of a proper `ℂ`-scheme are the same algebraically and
analytically. This is the *proper-case* version of the Riemann existence theorem; XII.5.1 of file 60 removes the
properness hypothesis.

**Proof.** A finite `X`-scheme `X' → X` is the same datum as a *coherent sheaf of `𝒪_X`-algebras*. Similarly, a
finite analytic `X^an`-space `𝓧' → X^an` is the same datum as a coherent sheaf of analytic `𝒪_{X^an}`-algebras
(`[XII.4, no. 19, §5, th. 2]`).

By XII.4.4, the categories of coherent sheaves (with their multiplicative algebra structure preserved) on `X`
and on `X^an` are equivalent. Hence the categories of coherent sheaves of algebras agree, and so do the
categories of finite `X`-schemes / finite analytic `X^an`-spaces.

The étale layer: a finite morphism is *étale* iff its analytification is étale (XII.3.1 (iii)). Restricting the
equivalence to the étale subcategory gives the finite étale equivalence. ∎

> **Slogan.** *For proper `X`, finite (resp. finite étale) coverings agree on the algebraic and analytic
> sides.* This is the Riemann existence theorem for proper `X`; the non-proper case is XII.5.1 of file 60.

______________________________________________________________________

## §XII.4.7 — Closing of file 59

<!-- source: XII.4 -->

By the end of this file we have the **cohomological GAGA** between `Sch_{lft}/ℂ` and `AnSp/ℂ`:

- (XII.4.1) The canonical comparison map `θ_p : (R^p f_* F)^an → R^p f_*^an(F^an)` is constructed from the two
    Leray spectral sequences of the analytification square.
- (XII.4.2) For `f : X → Y` proper and `F` coherent, `θ_p` is an isomorphism for every `p ≥ 0`. Two-stage
    proof: Stage 1 (projective via Stein-cover Čech cohomology) + Stage 2 (proper via Chow's lemma + EGA III
    §3.1.2 dévissage).
- (XII.4.3) Specialised to `Y = Spec ℂ`: `H^p(X, F) ≃ H^p(X^an, F^an)` for `X` proper.
- (XII.4.4) `Coh(X) ≃ Coh(X^an)` is an equivalence of categories for `X` proper. The fully-faithful direction
    is by XII.4.3 + SheafHom. The essentially-surjective direction is by Chow + noetherian induction + the
    `Ext^1` comparison via the Grothendieck spectral sequence.
- (XII.4.5) Analytification is fully faithful on proper `ℂ`-schemes (`Hom_ℂ(X, Y) ≃ Hom(X^an, Y^an)`).
- (XII.4.6) For `X` proper, the categories of finite (resp. finite étale) `X`-schemes and finite (resp. finite
    étale) analytic `X^an`-spaces are equivalent.

The full **Riemann existence theorem** — removing the properness hypothesis on `X` in XII.4.6 — and the
**`π_1`-comparison** `π_1^ét(X) ≃ π̂_1^top(X^an)` are the substance of **file 60 (§XII.5)**. The proper case of
the Riemann existence theorem is already in XII.4.6; what file 60 adds is the descent step that handles
non-proper `X` via Hironaka resolution and the Grauert–Remmert theorem.

> **Final slogan for file 59.** *On a proper `ℂ`-scheme, algebraic and analytic coherent geometry coincide,
> including higher direct images, cohomology groups, morphism sets, and finite (étale) coverings.* The
> comparison map `θ_p` is built from the Leray spectral sequences of the analytification square; the
> isomorphism statement (XII.4.2) factors through Chow's lemma and the projective-case Stein-cover
> computation.
