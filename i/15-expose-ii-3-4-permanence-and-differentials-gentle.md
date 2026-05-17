# Exposé II, sections 3–4: permanence and differential properties (gentle)

## What this file is about

If you have a good algebraic version of a submersion, two questions follow almost automatically. Does it preserve the
properties that mattered for ordinary covering maps? And does it admit a workable derivative test, so that you can check
the property by computing something concrete on the defining equations?

This file answers both. The local algebraic properties that survived crossing a covering — being free of certain
singularities, being well-dimensioned, and so on — also survive crossing a submersion, with one extra term tracking the
extra dimensions the submersion adds. The derivative test, in turn, is exactly the test that an engineer or physicist
would write down for the standard example: an elliptic curve cut out of the plane by a cubic equation in two variables
is smooth precisely when the partial derivatives of the cubic do not simultaneously vanish. The classical computation
that a calculus student would do becomes the algebraic theorem of the chapter.

File 14 set up smooth morphisms — étale modulo polynomial coordinates — and gave two intrinsic criteria (flat + smooth
fiber; under normality, equidimensional + smooth fiber). This file does two things. First (II.3): permanence — every
classical local-ring property survives a smooth extension, exactly as it survived an étale one in file 12, with one
extra clause for the relative dimension. Second (II.4): differentials — the relative cotangent sequence splits under
smoothness, `Ω¹_{X/Y}` is locally free of rank `dim_x f`, and the **Jacobian criterion** identifies smooth
sub-preschemes by a rank computation on differentials.

The differential half is the centerpiece. By the end of this file the elliptic-curve example
`Spec ℤ[x, y] / (y² − x³ − ax − b) → Spec ℤ` becomes a one-line check.

Standing assumption: locally noetherian preschemes throughout.

## II.3 Permanence properties

<!-- source: II.3 -->

### What smooth preserves

<!-- source: II.3.1 -->

_This result says: under a smooth morphism, regular / reduced / normal pass between source and target in both
directions. The proofs are inherited from the étale case (file 12) and the polynomial-extension case._

**Proposition II.3.1.** Let `f : X → Y` be smooth at `x ∈ X`, and let `y = f(x)`. Then `𝒪_x` is regular (resp. reduced,
resp. normal) iff `𝒪_y` is.

### Proof

The case `X = Y[t₁, …, tₙ]` is the standard "polynomial extension preserves regular / reduced / normal." The case `X`
étale over `Y` was Theorem I.9.5 (file 12). By definition smoothness combines these two: an étale morphism
`U → Y[t₁, …, tₙ]` followed by the polynomial projection. Apply each preservation step in turn.

### Dimension and depth formulas

Quasi-finite flatness (file 12 opening) preserves Krull dimension and depth. Smoothness adds the polynomial layer. The
combined formulas are:

```text
dim 𝒪_x = dim 𝒪_y + n − d,
depth 𝒪_x = depth 𝒪_y + n − d,
```

where `n` is the relative dimension of `f` at `x` and `d` is the transcendence degree of `κ(x)` over `κ(y)`. (See EGA IV
§6.1, §6.3 for the proofs.) Subtracting:

```text
codepth 𝒪_x = codepth 𝒪_y,    where codepth = dim − depth.
```

So **codepth is invariant under smooth morphisms**. In particular `𝒪_x` is Cohen-Macaulay (codepth `0`) iff `𝒪_y` is,
and `𝒪_x` has no embedded components iff `𝒪_y` does not.

Most of this is "Cohen-Macaulay over `Y`" — flat plus smooth fiber — and was implicit at the opening of section I.9 in
the gentle treatment of Exposé I (file 12).

## II.4 Differential properties of smooth morphisms

<!-- source: II.4 -->

The differential machinery of file 03 — the diagonal, the ideal sheaf `𝓘_X`, the sheaf of relative Kähler differentials
`Ω¹_{X/Y} = 𝓘_X / 𝓘_X²`, and the [conormal](glossary.md#conormal-sheaf) and
[cotangent](glossary.md#relative-differentials) exact sequences — applies to any morphism. Under smoothness, the
cotangent sequence **splits**, `Ω¹_{X/Y}` is **locally free** of the right rank, and the conormal sequence becomes the
engine of the **Jacobian criterion**. We collect the four foundational lemmas, then climb to the criterion.

### Recall: the relative cotangent sequence

For an `S`-morphism `f : X → Y` the cotangent sequence (file 03, "Two exact sequences for `Ω¹`") reads

```text
f*(Ω¹_{Y/S}) → Ω¹_{X/S} → Ω¹_{X/Y} → 0
```

and is exact at the right two terms in general. It is exact on the left exactly when `f` is formally smooth (one of the
EGA characterizations of formal smoothness; cf.
[`formally-etale-lifting`](appendix-black-boxes.md#formally-etale-lifting)). We will see immediately that smooth ⟹ split
exact.

### Unramified vs. étale, in differentials

<!-- source: II.4.1 -->

_This result says: at the differential level, unramified is "surjective on differentials," étale is "isomorphic on
differentials."_

**Lemma II.4.1.** Let `f : X → Y` be a morphism of `S`-preschemes.

- If `f` is **unramified**, then `f*(Ω¹_{Y/S}) → Ω¹_{X/S}` is surjective.
- If `f` is **étale**, then `f*(Ω¹_{Y/S}) → Ω¹_{X/S}` is an isomorphism.
- The converse for unramified holds when `f` is locally of finite type.

### Proof

The unramified case follows from the cotangent sequence above and `Ω¹_{X/Y} = 0` (file 04, form (ii) of unramified). For
the étale direction, consider the diagram

```text
X  →  X ×_Y X  →  X ×_S X
↓                  ↓
Y  →             Y ×_S Y.
```

`X ×_Y X` is the fibered product of `Y` and `X ×_S X` over `Y ×_S Y`. Since `f` is unramified, `Δ_{X/Y} : X → X ×_Y X`
is an open immersion (file 04 form (iii)). Hence the conormal sheaf of the composite immersion `X → X ×_Y X → X ×_S X`
is the pullback to `X` of the conormal sheaf of `X ×_Y X → X ×_S X`. Since `f` is also flat (étale), `X ×_S X → Y ×_S Y`
is flat, so this last conormal sheaf is the pullback of the conormal sheaf of `Y → Y ×_S Y`, which is `Ω¹_{Y/S}`. Pulled
back to `X`, that is `f*(Ω¹_{Y/S})`. On the other hand, the conormal sheaf of `X → X ×_S X` is `Ω¹_{X/S}`. The chain of
identifications gives the isomorphism.

### The polynomial case

<!-- source: II.4.2 -->

_This result says: for the relative polynomial scheme `X = Y[t₁, …, tₙ]`, the cotangent sequence is split exact and
`Ω¹_{X/Y}` is free on the differentials of the coordinates._

**Lemma II.4.2.** Let `X = Y[t₁, …, tₙ]` over an `S`-prescheme `Y`. Then the canonical sequence

```text
0 → f*(Ω¹_{Y/S}) → Ω¹_{X/S} → Ω¹_{X/Y} → 0
```

is exact, and `Ω¹_{X/Y}` is **free** with basis `dt₁, …, dt_n`.

### Proof

Affine and computational. For `B = A[t₁, …, t_n]`, `Ω¹_{B/A} = ⊕ B · dt_i` is free by direct construction (file 03). The
exactness on the left follows from the explicit splitting "set the `dt_i` to zero and identify the rest with
`f*(Ω¹_{Y/S})`."

### The differential structure of smooth morphisms

<!-- source: II.4.3 -->

_This result says: under smoothness, the relative cotangent sequence is split exact and `Ω¹_{X/Y}` is locally free of
rank equal to the relative dimension. This is the differential-geometric heart of smoothness._

**Theorem II.4.3.** Let `f : X → Y` be a smooth morphism of `S`-preschemes. Then:

1. The canonical sequence

```text
0 → f*(Ω¹_{Y/S}) → Ω¹_{X/S} → Ω¹_{X/Y} → 0
```

is **exact**.

1. `Ω¹_{X/Y}` is **locally free**, and its rank at `x` equals the relative dimension of `f` at `x`.

### Proof

By Definition II.1.1, locally `f` factors as étale `g : U → Y[t₁, …, t_n]` followed by the polynomial projection. Lemma
II.4.2 gives the conclusion for the polynomial projection. Lemma II.4.1 gives isomorphisms `g*(Ω¹_{Y[t]/S}) ≃ Ω¹_{U/S}`
and `g*(Ω¹_{Y[t]/Y}) ≃ Ω¹_{U/Y}`. Composing the two reductions gives the conclusion for `f` near the chosen point. Local
freeness with rank `n = dim_x f` follows from `Ω¹_{X/Y} ≃ g*(Ω¹_{Y[t]/Y})` and `Ω¹_{Y[t]/Y}` free of rank `n` (Lemma
II.4.2).

### A direct corollary

<!-- source: II.4.4 -->

*This result says: under smoothness, the pullback `f*(Ω¹_{Y/S})`sits inside`Ω¹_{X/S}` as a locally direct factor.*

**Corollary II.4.4.** Let `f : X → Y` be smooth. The map `f*(Ω¹_{Y/S}) → Ω¹_{X/S}` is **injective**, and its image is
**locally a direct factor** of `Ω¹_{X/S}`.

### Universally injective homomorphisms

A homomorphism `u : F → G` of `𝒪_X`-modules is **universally injective** at `x ∈ X` if `F_x → G_x` is injective and
remains so after tensoring with every `𝒪_x`-module. When `F` and `G` are free of finite type near `x`, the following are
equivalent:

1. `u` is injective at `x` and `Coker u` is free at `x`.
1. There is a neighborhood `U` of `x` on which `u` realizes `F|U` as a direct factor of `G|U`.
1. `u` is universally injective at `x`.
1. The induced map on fibers `F_x ⊗ κ(x) → G_x ⊗ κ(x)` is injective.
1. The transposed map `Ǧ → F̌` is surjective at `x`.

The proof is a circular round trip: (iv) ⟹ (v) by Nakayama, and (v) ⟹ (i) because a locally free quotient sheaf is
automatically a direct factor. Geometrically, "universally injective" says `u` realizes the vector bundle of `F` as a
sub-bundle of the vector bundle of `G`.

### Smoothness via universal injectivity

<!-- source: II.4.5 -->

_This result says: if the target `Y` is already smooth, then `f` itself is smooth iff the source is smooth and the
differential pullback is universally injective._

**Corollary II.4.5.** Let `f : X → Y` be locally of finite type, `x ∈ X`, `y = f(x)`, with `Y` smooth at `y` over `S`.
The following are equivalent:

1. `f` is smooth at `x`.
1. `X` is smooth over `S` at `x`, and `f*(Ω¹_{Y/S}) → Ω¹_{X/S}` is universally injective at `x` — equivalently,
    injective with free cokernel `Ω¹_{X/Y}` at `x`.

### Étale criterion in differentials

<!-- source: II.4.6 -->

_This result says: between two smooth `S`-preschemes, `f` is étale iff it pulls differentials back isomorphically._

**Corollary II.4.6.** Let `f : X → Y` be a morphism of smooth `S`-preschemes. Then `f` is étale at `x` iff
`f*(Ω¹_{Y/S}) → Ω¹_{X/S}` is an isomorphism at `x`.

### Proof sketch

Necessity is II.4.1. For sufficiency: II.4.1 shows `f` is unramified at `x`. By II.2.2 reduce to `S = Spec(k)`.
Smoothness of `Y` over `k` forces `Y` regular hence normal; injectivity of `𝒪_y → 𝒪_x` then follows by I.9.5(ii) (file
12\) once we check dimensions agree — and the dimensions are the ranks of `Ω¹_{Y/k}` and `Ω¹_{X/k}` at `y` and `x`
(Theorem II.4.3(ii)), hence equal by hypothesis.

### Tangent map: a familiar form

<!-- source: II.4.7 -->

When `X` and `Y` are both smooth over `S`, the smoothness criterion II.4.5(ii) for `f : X → Y` can be rephrased: at
every `x ∈ X`, the **tangent map** `T_x f` of `f` at `x` (the transpose of the fiber map of `f*(Ω¹_{Y/S}) → Ω¹_{X/S}`)
is **surjective**.

This is the algebraic-geometric analog of the differential-geometric "submersion = surjective tangent map" condition,
familiar from analytic geometry. The "nonsingularity" hypothesis usually imposed in analytic geometry is the same as
smoothness over `Spec ℂ`.

### Étale via differentials of generators

<!-- source: II.4.8 -->

_This result says: at a smooth point, an `S`-morphism to the affine `n`-space defined by sections `g_i` is étale iff the
`dg_i` form a basis of `Ω¹_{X/S}`._

**Corollary II.4.8.** Let `X` be an `S`-prescheme, `g : X → S[t₁, …, t_n]` an `S`-morphism defined by sections
`g_i ∈ 𝒪_X`, and `x ∈ X` such that `X` is smooth over `S` at `x`. Then `g` is étale at `x` iff the `dg_i`, `1 ≤ i ≤ n`,
form a **basis** of `Ω¹_{X/S}` at `x`. Equivalently, the `dg_i(x)` form a basis of the fiber `Ω¹_{X/S}(x)` over `κ(x)`.

This is the differential test for "the chosen coordinates are local étale coordinates."

### The conormal sheaf

For a closed sub-prescheme `Y ↪ X` defined by a coherent ideal sheaf `𝒥`, the **conormal sheaf** of `Y` in `X` is

```text
𝒩_{Y/X} := 𝒥 / 𝒥²,
```

a coherent sheaf on `Y`. It records the first-order behavior of `X` along `Y`.

If `X` is an `S`-prescheme, the **conormal exact sequence** on `Y` reads

```text
𝒥/𝒥²  --d→  Ω¹_{X/S} ⊗_{𝒪_X} 𝒪_Y  →  Ω¹_{Y/S}  →  0,
```

or in the affine version (`B → C = B/J`):

```text
J/J²  →  Ω¹_{B/A} ⊗_B C  →  Ω¹_{C/A}  →  0.
```

The right two terms are the cotangent sequence of `Y → X → S` with `Ω¹_{Y/X} = 0`; the first map sends a function
`g ∈ 𝒥` to its differential `dg`, restricted to `Y` (modulo `𝒥²`). The exactness is classical (file 03 derived this from
the diagonal computation for differentials).

This was the engine behind I.7.2 in file 11 (the different ideal of `B = A[t]/F` is `(F'(u))`).

### Smooth in `X` smooth over `S`: four equivalent forms

<!-- source: II.4.9 -->

_This result says: when `X` is smooth and `Y ⊂ X` is a closed sub-prescheme, four conditions are equivalent
characterizations of "`Y` arises by an étale base change of a coordinate hyperplane in some affine `n`-space.""_

**Proposition II.4.9.** Let `X` be an `S`-prescheme smooth at `x ∈ X`, let `Y ↪ X` be defined by an ideal sheaf `𝒥`, and
let `g_i ∈ 𝒪_X`, `1 ≤ i ≤ n`, define an `S`-morphism `g : X → X' = S[t₁, …, t_n]`. Fix `0 ≤ p ≤ n`. The following are
equivalent:

1. There is a neighborhood `X₁` of `x` in `X` such that `g|X₁` is étale and `Y ∩ X₁` is the inverse image of the
    coordinate sub-prescheme `Y' = S[t_{p+1}, …, t_n] ⊂ X'`. Equivalently, the `g_i`, `1 ≤ i ≤ p`, generate `𝒥|X₁`.
1. `Y` is smooth over `S` at `x`, the `g_i` for `1 ≤ i ≤ p` lie in `𝒥_x`, the `dg_i(x)` for `1 ≤ i ≤ n` form a basis of
    `Ω¹_{X/S}(x)`, and the `dg'_i(x)` for `p + 1 ≤ i ≤ n` form a basis of `Ω¹_{Y/S}(x)` (where `g'_i` is the
    restriction of `g_i` to `Y`).
1. The `g_i`, `1 ≤ i ≤ p`, generate `𝒥_x`, and the `dg_i(x)`, `1 ≤ i ≤ n`, form a basis of `Ω¹_{X/S}(x)`.
1. `Y` is smooth over `S` at `x`, the `g_i` for `1 ≤ i ≤ p` form a minimal system of generators of `𝒥_x`, and the
    `dg'_i(x)` for `p + 1 ≤ i ≤ n` form a basis of `Ω¹_{Y/S}(x)`.

Under any of these conditions, `𝒩_{Y/X} = 𝒥/𝒥²` is free at `x` with basis the classes of the `g_i`, `1 ≤ i ≤ p`, and the
conormal homomorphism `𝒥/𝒥² → Ω¹_{X/S} ⊗ 𝒪_Y` is universally injective at `x`.

### Proof outline

(i) ⟹ all others: `Y₁` is étale over `Y'` by the corollary "étale + étale-target = étale" (I.4.6, file 10), hence smooth
of relative dimension `n − p`. Then II.4.8 gives the basis statements on `Ω¹`. The conormal sequence forces the `g_i`
modulo `𝒥²` to form a basis of `𝒥/𝒥²`.

(iii) ⟹ (i): II.4.8 says `g` is étale near `x`; the `g_i`, `1 ≤ i ≤ p`, generate `𝒥` locally, so `Y ∩ X₁ = g⁻¹(Y')`.

(ii) ⟹ (i): the differential conditions plus II.4.8 say `g` is étale at `x` and the restriction `h : Y → Y'` is étale at
`x`. Let `Y" = g⁻¹(Y')`. Then `Y ⊂ Y"`, both étale over `Y'` at `x`. By I.4.8 (file 10), the inclusion `Y → Y"` is
étale, hence (radicial) an open immersion (I.5.1 / I.5.2, file 11). Restrict.

(iv) ⟹ (ii): pure unwinding once one knows `𝒥/𝒥²` is free under the smoothness of `Y` (which is the next theorem).

### The Jacobian criterion

<!-- source: II.4.10 -->

_This result says: given a smooth ambient `X`, a closed sub-prescheme `Y` is smooth at `x` iff the defining ideal `𝒥`
admits, at `x`, generators whose differentials are linearly independent in the fiber of `Ω¹_{X/S}`. This is the
**Jacobian criterion for smoothness**._

**Theorem II.4.10.** Let `X` be a smooth `S`-prescheme, `Y ↪ X` a closed sub-prescheme defined by `𝒥`, and `x ∈ X`. The
following are equivalent:

1. `Y` is smooth over `S` at `x`.
1. There is a neighborhood `X₁ ∋ x` and an étale `S`-morphism `g : X₁ → X' = S[t₁, …, t_n]` such that `Y ∩ X₁` is the
    inverse image of the coordinate sub-prescheme `Y' = S[t_{p+1}, …, t_n]` for some `p`.
1. There are generators `g_i`, `1 ≤ i ≤ p`, of `𝒥_x` such that the `dg_i` are part of a basis of `Ω¹_{X/S}` at `x`.
    Equivalently, the `dg_i(x)` are linearly independent in `Ω¹_{X/S}(x)` over `κ(x)`.
1. The conormal sheaf `𝒩_{Y/X} = 𝒥/𝒥²` is free on `Y` at `x`, the conormal map `𝒥/𝒥² → Ω¹_{X/S} ⊗ 𝒪_Y` is universally
    injective at `x`, and `Ω¹_{Y/S}` is locally free at `x` — equivalently, the conormal sequence

```text
   0 → 𝒥/𝒥² → Ω¹_{X/S} ⊗ 𝒪_Y → Ω¹_{Y/S} → 0
```

is exact and split at `x`.

### Why this is the right criterion

In differential geometry, a smooth submanifold `Y ⊂ X` is cut out locally by functions whose differentials span the
conormal directions. The Jacobian criterion is the algebraic transcription: generators of `𝒥` whose differentials are
linearly independent in `Ω¹_{X/S}(x)` cut out a smooth sub-prescheme.

### Proof outline

(ii) ⟹ (i), (iii), (iv) was established in II.4.9. The implication (i) ⟹ (ii) is the new content. By Theorem II.4.3(ii)
the right two terms of the conormal sequence are free `𝒪_Y`-modules at `x`. The map `Ω¹_{X/S} ⊗ 𝒪_Y → Ω¹_{Y/S}` is
surjective; choose `g_i` for `p + 1 ≤ i ≤ n` whose differentials map to a basis of `Ω¹_{Y/S}`, and complete to a basis
of `Ω¹_{X/S} ⊗ 𝒪_Y` by `g_i ∈ 𝒥_x` for `1 ≤ i ≤ p`. This puts us under the hypothesis of II.4.9(ii), which gives
II.4.9(i) — i.e. II.4.10(ii).

(iii) ⟹ (ii) is II.4.9(iii) ⟹ II.4.9(i). (iv) is trivially equivalent: if `𝒥/𝒥²` is free of rank `p` at `x` and the
conormal map is universally injective, choose generators whose classes are a basis of `𝒥/𝒥²`; by Nakayama they generate
`𝒥_x`, and (iii) follows.

### A useful refinement

<!-- source: II.4.11 -->

_This result says: when both `X` and `Y` are smooth, four conditions on a candidate generating set `(g_i)` of `𝒥`
coincide, including being a minimal generating set and being part of an étale-coordinate system._

**Corollary II.4.11.** Let `X` be an `S`-prescheme, `Y ⊂ X` defined by `𝒥`, `x ∈ Y` with both `X` and `Y` smooth over
`S` at `x`. Let `g_i`, `1 ≤ i ≤ p`, be sections of `𝒥`. The following are equivalent:

1. The `g_i` generate `𝒥_x` and the `dg_i(x)` are linearly independent in `Ω¹_{X/S}(x)` over `κ(x)`.
1. The `g_i` modulo `𝒥²` form a basis of `𝒥/𝒥²` at `x`.
1. The `g_i` form a minimal system of generators of `𝒥_x`.
1. There exist `g_i`, `p + 1 ≤ i ≤ n`, such that the full collection defines an étale morphism `X₁ → X' = S[t₁, …, t_n]`
    on a neighborhood `X₁ ∋ x`, with `Y₁ = Y ∩ X₁` the inverse image of `Y' = S[t_{p+1}, …, t_n]`.

### The hypersurface case

<!-- source: II.4.12 -->

_This result says: a hypersurface `{F = 0}` in a smooth ambient is smooth at `x` iff `F` vanishes in a neighborhood of
`x` (trivial case) or `dF(x) ≠ 0` (transverse case)._

**Corollary II.4.12.** Let `X` be an `S`-prescheme smooth at `x`, let `F ∈ 𝒪_X`, and let `Y` be the closed sub-prescheme
defined by `F · 𝒪_X`. Then `Y` is smooth over `S` at `x` iff one of the following holds:

- `F` is zero in a neighborhood of `x` (so `Y` agrees with `X` there), or
- `dF(x) ≠ 0` in `Ω¹_{X/S}(x)`.

### Application: the elliptic-curve example

For `S = Spec ℤ`, `X = Spec ℤ[x, y] = 𝔸²_ℤ`, smooth over `ℤ` of relative dimension `2`. Take `F = y² − x³ − ax − b` for
fixed `a, b ∈ ℤ`. Then `Y = Spec ℤ[x, y] / (F)` is a closed sub-prescheme of `𝔸²_ℤ`. Compute:

```text
dF = 2y · dy − (3x² + a) · dx ∈ Ω¹_{X/ℤ} = ℤ[x, y] · dx ⊕ ℤ[x, y] · dy.
```

By Corollary II.4.12, `Y` is smooth over `ℤ` at a point `(x₀, y₀) ∈ Y` iff `dF(x₀, y₀) ≠ 0` in `Ω¹_{X/ℤ}(x₀, y₀)`. That
is:

```text
(2y₀, −(3x₀² + a)) ≠ (0, 0)    in κ(x₀, y₀)².
```

Equivalently, `2y₀ ≠ 0` or `3x₀² + a ≠ 0`. The locus where both vanish is `y₀ = 0`, `3x₀² + a = 0`, with the additional
constraint `F(x₀, y₀) = 0` (i.e. `(x₀, y₀) ∈ Y`). Substituting `y₀ = 0`: `0 = x₀³ + a x₀ + b`. Substituting
`3x₀² + a = 0`: `a = −3x₀²`. Then `0 = x₀³ − 3x₀³ + b = −2x₀³ + b`, so `x₀³ = b/2`. Multiplying out, the condition for
non-smoothness at some characteristic-`p` fiber pins down a specific divisibility involving the **discriminant**
`Δ = −16(4a³ + 27b²)`.

In particular, **`Y` is smooth over `ℤ[1/Δ]`**: away from the primes dividing the discriminant, the elliptic curve has
nowhere non-vanishing `dF`, hence is smooth at every point. This is the classical elliptic-curve discriminant story; the
Jacobian criterion of II.4.10 / II.4.12 is what lets us read it off `dF` alone, with no further analysis.

### Smoothness descends along faithfully flat extensions

<!-- source: II.4.13 -->

_This result says: smoothness can be checked after a faithfully flat base change._

**Corollary II.4.13.** Let `Y` be an `S`-prescheme locally of finite type, `S' → S` a flat morphism, `Y' = Y ×_S S'`,
`x' ∈ Y'` mapping to `x ∈ Y`. Then `Y` is smooth over `S` at `x` iff `Y'` is smooth over `S'` at `x'`. If `S' → S` is
flat and surjective, `Y` is smooth over `S` iff `Y'` is smooth over `S'`.

### Proof

Necessity by II.1.3(ii). For sufficiency: reduce to `Y` affine, embed `Y` as a closed sub-prescheme of `S[t₁, …, t_n]`.
Apply the Jacobian criterion II.4.10(iv): the conormal sequence is exact on the source iff it is on the base change;
this transfers smoothness.

### Regular ideals and regular immersions

<!-- source: II.4.14 -->

The Jacobian criterion deserves the name. Grothendieck's formulation in terms of relative differentials (rather than
absolute differentials over `ℤ`) is the form that travels well to the noetherian setting.

The full II.4.14 introduces a packaging:

**Definition.** A sequence `x₁, …, x_n ∈ A` (`A` noetherian) generates an ideal `J` **regularly** if the canonical
surjection

```text
(A/J)[t₁, …, t_n] → gr^J(A)
```

is an isomorphism. Equivalently:

- the canonical map `S_{A/J}(J/J²) → gr^J(A)` from the symmetric algebra is an isomorphism;
- `J/J²` is free with basis the classes of the `x_i` modulo `J²`.

If `J ≠ A`, the `x_i` are then a minimal system of generators of `J`, and every other minimal system of generators is
also regular. Localization preserves regularity. For a noetherian local `(A, 𝔪)` with `x_i ∈ 𝔪`, the `x_i` form a
regular system of generators iff they form an **`A`-regular sequence in Serre's sense**: each `x_i` is a
non-zero-divisor in `A / (x₁, …, x_{i−1})`.

(The `A`-regular sequence formulation appears in Serre's course on commutative algebra written up by Gabriel.)

In sheaf form: an ideal sheaf `𝒥` on `X` is a **regular ideal** if for every `x ∈ X`, `𝒥_x` admits a regular system of
generators. Equivalently:

1. `S_{𝒪_X / 𝒥}(𝒥/𝒥²) → gr^𝒥(𝒪_X)` is an isomorphism.
1. `𝒥/𝒥²` is locally free as an `(𝒪_X / 𝒥)`-module.

The closed sub-prescheme `Y ⊂ X` defined by a regular ideal is **regularly immersed** in `X`. A morphism that locally
identifies its source with such a closed sub-prescheme is a **regular immersion**, regular at `x` if the local
identification works on a neighborhood of `x`.

### Terminology warning (Grothendieck)

> The terminology _regular immersion_, _regular ideal_, etc. introduced in this number met with rather lively and
> general opposition from Chevalley and Serre. _Cohen-Macaulay ideal_, or _Macaulayan ideal_, was proposed, which would
> morally oblige one also to adopt _Cohen-Macaulay immersion_. This conflicts with another usage already in the
> multiplodocus, where a morphism of finite type is _Cohen-Macaulay_ at a point if it is flat there and its fiber has a
> Cohen-Macaulay local ring. Pending a satisfactory solution, we shall keep, with every reservation, the terminology
> introduced in this number.

EGA 0_IV §15.1.7 settles on this terminology (regular ideal, regular immersion).

### Smooth ambient via regular immersion

<!-- source: II.4.15 -->

_This result says: if `Y ↪ X` is a closed immersion with `Y` smooth over `S` at `x`, then `X` is smooth over `S` at `x`
iff the immersion is regular at `x`._

**Theorem II.4.15.** Let `X` be an `S`-prescheme locally of finite type, `Y ↪ X` a closed sub-prescheme defined by `𝒥`,
`x ∈ Y`. Suppose **`Y` is smooth over `S` at `x`** (no hypothesis on `X`). Then:

```text
X smooth over S at x  ⟺  𝒥_x is a regular ideal of 𝒪_x.
```

### Why the regular-immersion form is natural

When `Y` is smooth, regularity of the immersion is equivalent to "`X` looks locally like a free polynomial extension of
`Y`." That is exactly the local form of smoothness: `X` smooth over `S` near `Y` iff `X` is, near `Y`, a
normal-crossings-free thickening of `Y` by polynomial coordinates.

### Corollary on global regular embedding

<!-- source: II.4.16 -->

_This result says: when `Y` is smooth, smoothness of `X` along `Y` is the same as `Y` being regularly embedded._

**Corollary II.4.16.** Suppose `Y` is smooth over `S`. Then `X` is smooth over `S` in a neighborhood of `Y` iff `Y` is
regularly embedded in `X`.

### Proof of II.4.16 (sketch)

(i) ⟹ (ii): apply criterion (ii) of II.4.10. The witness `g : X₁ → X'` is flat, hence regularity descends from the
standard inclusion `Y' ⊂ X'` to `Y ⊂ X` along `g`.

(ii) ⟹ (i): take a regular system `(g_i)`, `1 ≤ i ≤ p`, of generators of `𝒥_x`, and `g_i`, `p + 1 ≤ i ≤ n`, lifts of an
étale-coordinate system on `Y₁`. The combined `g_i` define `g : X₁ → X' = S[t₁, …, t_n]`. Show `g` is étale at `x`: it
is unramified by the fiber computation, and a graded-ring argument (using a flatness criterion on `gr^𝒥`) gives
flatness.

### The section case

<!-- source: II.4.17 -->

_This result says: for `X` over `Y` and a section `i : Y → X`, four local properties at `x = i(y)` coincide, including
`X → Y` smooth at `x`, the immersion regular, and the formal completion of `𝒪_x` along `𝒥` being a power-series
algebra._

**Corollary II.4.17.** Let `X` be locally of finite type over `Y`, `i : Y → X` a section, `y ∈ Y`, `x = i(y)`, `𝒥` the
ideal sheaf of `i(Y)` (assume closed). The following are equivalent:

1. `X` is smooth over `Y` at `x`.
1. `i` is a regular immersion at `y`.
1. The completion `𝒪̂_x` of `𝒪_x` for the `𝒥_x`-adic topology is isomorphic over `𝒪_y` to a formal power-series algebra
    `𝒪_y[[t₁, …, t_n]]`.
1. There is an `S`-morphism `g : V → U[t₁, …, t_n]` (with `U ∋ y`, `V ∋ x`) such that `g` is étale, the section `i` of
    `X` over `Y` corresponds via `g` to the zero section of `U[t₁, …, t_n]`.

### Differential smoothness

<!-- source: II.4.18 -->

_This result says: a smooth `X` over `S` has the property that the diagonal `X → X ×_S X` is a regular immersion. We
call this "differentially smooth," and it is exactly the half of smoothness not detected by flatness._

**Corollary II.4.18.** Let `X` be smooth over `S`. Then the diagonal morphism `Δ_{X/S} : X → X ×_S X` is a **regular
immersion**.

We call `X` **differentially smooth over `S`** if its diagonal is regularly immersed.

### Proof

`X` and `X ×_S X` are both smooth over `S`. Apply Corollary II.4.16 to the closed embedding `Δ_{X/S} : X ↪ X ×_S X`.

### Principal parts sheaves

For `X` over `S` (locally of finite type, hence `𝒫ⁿ_{X/S}` coherent), recall (file 03) the **principal parts sheaves**

```text
𝒫ⁿ_{X/S} := 𝒪_{X ×_S X} / 𝓘_X^{n+1},    n ≥ 0,
```

regarded as a sheaf of `𝒪_X`-algebras through the first projection `pr₁ : X ×_S X → X`. The projective limit
`𝒫^∞_{X/S} = lim_n 𝒫ⁿ_{X/S}` is the structure sheaf of the formal completion of `X ×_S X` along the diagonal.

Under differential smoothness (Corollary II.4.18), `𝒫^∞_{X/S}` is _regular as a sheaf of augmented algebras over `𝒪_X`_,
equivalently:

- `Ω¹_{X/S}` is locally free, and
- the canonical surjection `S_{𝒪_X}(Ω¹_{X/S}) → gr_*(𝒫^∞_{X/S})` from the symmetric algebra is an isomorphism.

Equivalently: every point of `X` has an open neighborhood on which `𝒫^∞_{X/S}` is isomorphic to `𝒪_X[[t₁, …, t_n]]`.

### Smooth ⟺ flat + differentially smooth

A consequence of II.4.17 + II.4.18 (and II.4.13): for `X` of finite type over `S`,

```text
X smooth over S  ⟺  X flat over S  +  X differentially smooth over S.
```

Flatness is the new clause; without it differential smoothness already follows for closed sub-preschemes (e.g. `X ⊂ S`),
but flatness fails. So flatness is the genuinely separate piece.

### Differential operators

The principal parts sheaves are the universal carriers of **differential operators** on `𝒪_X` relative to `S`: a
homomorphism `D : 𝒪_X → F` of `𝒪_X`-modules is a _differential operator of order `≤ n`_ iff it factors through
`dⁿ : 𝒪_X → 𝒫ⁿ_{X/S}` followed by an `𝒪_X`-linear map `u : 𝒫ⁿ_{X/S} → F`. This recovers the recursive definition: `D` is
order `≤ n` iff for every `g ∈ 𝒪_X(U)`, the map `f ↦ D(fg) − g D(f)` is order `≤ n − 1`.

Under differential smoothness, the sheaf of all-orders differential operators has the familiar structure from manifold
calculus: locally generated by **divided powers** in commuting operators `∂/∂x_i`, `1 ≤ i ≤ n`. In characteristic `0`
(or whenever `S` is a sheaf of `ℚ`-algebras) the divided powers reduce to ordinary polynomials in the `∂/∂x_i`.

(Full details: EGA IV §16.8–16.12.)

### Terminology revisited

<!-- source: II.4.19 -->

The terminological compromise — "regular immersion" rather than "Cohen-Macaulay immersion" — is recorded in EGA 0_IV
§15.1.7. The gentle reading follows it.

## What to remember

The four pieces of file 15:

- **Permanence (II.3.1, codepth-invariance).** Every classical local-ring property — regular, reduced, normal,
    Cohen-Macaulay — survives a smooth extension in both directions, exactly as it did under étale (file 12) with the
    relative dimension as the only numerical adjustment.
- **The structure of `Ω¹` under smoothness (II.4.3).** The cotangent sequence is split exact, and `Ω¹_{X/Y}` is locally
    free of rank `dim_x f`. This is the differential-geometric heart of smoothness.
- **The Jacobian criterion (II.4.10).** A closed sub-prescheme of a smooth ambient is smooth at `x` iff its defining
    ideal admits generators with linearly independent differentials at `x`. Tested on the elliptic-curve example, this
    gives the classical discriminant story for free.
- **Regular immersions and the diagonal (II.4.15–II.4.18).** Smooth morphisms have regularly immersed diagonals;
    equivalently, the formal completion of `X ×_S X` along the diagonal is a power-series algebra over `𝒪_X`. Smooth =
    flat + differentially smooth, the cleanest decomposition of the definition.

The next file (16) closes the picture by working over a base field: smooth ⟺ regular under separability conditions, the
Mac Lane criterion via separating transcendence bases, and the bridge back to the étale theory of file 12 (étale =
smooth of relative dimension `0`).
