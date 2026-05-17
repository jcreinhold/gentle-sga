# Exposé II, section 5: case of a base field (gentle)

## What this file is about

Take the simplest possible setting. The base of the family is a single field — the rational numbers, say, or the real
numbers, or one of the finite arithmetic worlds where every prime divides exactly once. Over a base that simple, what
do the algebraic submersions developed in the previous two files reduce to? And how does the algebraic word for
"smooth" line up with the older, more elementary word "regular" that ring theorists were already using for local
algebraic objects that look like polynomial rings near a point?

This file does the comparison. Over a perfect base — one with no hidden arithmetic flaw in the way roots of
polynomials behave — the two words agree exactly. Over an imperfect base they part ways, and the gap is named and
measured. The chapter then closes a circle: covering maps are submersions of zero dropped dimensions, and the rigidity
results of the earlier files are the derivative test of this chapter, specialised to that case.

Files 14 and 15 developed smooth morphisms in full generality (over an arbitrary base prescheme `Y`). This file
specializes to `Y = Spec k` for `k` a field. The pay-off is concrete: smooth becomes a single-criterion test in
differentials, and the relationship to the classical notion of _regularity_ of local rings becomes precise. Over a
perfect field the two coincide; over imperfect fields the gap is exactly inseparability.

The closing remark of the file connects everything back: étale morphisms (file 11) are smooth morphisms of relative
dimension `0`, and the rigidity of file 11 is the rigidity of file 15's differential criterion at relative dimension
`0`.

Standing assumption: `k` is a field; `X` is a prescheme of finite type over `k`; "smooth" means smooth in the sense of
file 14.

## II.5 The base-field case

<!-- source: II.5 -->

### Étale via differentials of generators

<!-- source: II.5.1 -->

*This result says: for `X` of finite type over a field `k`, a morphism to affine `n`-space `Spec k[t₁, …, t_n]` is étale
at `x` iff the differentials of its defining sections form (or just generate) a basis of `Ω¹_{X/k}`at`x`. As a
consequence, `X`is smooth and`𝒪*x`is regular at`x`.*

**Proposition II.5.1.** Let `X` be of finite type over `k`, `x ∈ X`, `n = dim_x X`, and let `f : X → Spec k[t₁, …, t_n]`
be defined by sections `f_i ∈ Γ(X, 𝒪_X)`. The following are equivalent, and imply that `X` is smooth over `k` at `x`
(hence regular at `x` by II.3.1):

1. `f` is étale at `x`.
1. The `df_i` form a **basis** of `Ω¹_{X/k}` at `x`.
1. The `df_i` **generate** `Ω¹_{X/k}` at `x`.

### Proof

(i) ⟹ (ii) is II.4.8 (file 15) once we know `X` is smooth at `x`, which (i) supplies via II.1.3(i) (file 14: étale ⟹
smooth). The implication (ii) ⟹ (iii) is trivial.

(iii) ⟹ (i): if the `df_i` generate, then `f` is unramified at `x` by Lemma II.4.1 (file 15). Replacing `X` by an open
neighborhood of `x`, `f` is also of finite type, hence quasi-finite (one of the equivalent forms of unramified, file
04). Quasi-finite over a regular noetherian base, with both the source and target of the same dimension `n` at `x`, is
dominant for dimension reasons. Then I.9.5(ii) (file 12) — over a normal base, injective and unramified is étale —
closes the argument once we observe that `Spec k[t₁, …, t_n]` is regular and so normal.

### When `κ(x) / k` is finite separable

<!-- source: II.5.2 -->

_This result says: under the additional hypothesis that the residue extension at `x` is finite separable and the `f_i`
lie in `𝔪_x`, "`f_i` generate `𝔪_x`" is a fourth equivalent condition._

**Corollary II.5.2.** Under the hypotheses of II.5.1, suppose `κ(x) / k` is **finite separable** and the `f_i` lie in
the maximal ideal `𝔪_x`. Then conditions II.5.1(i)–(iii) are equivalent to:

(iv) The `f_i` generate `𝔪_x` — equivalently, the `f_i` modulo `𝔪_x²` form a basis of `𝔪_x / 𝔪_x²` over `κ(x)`.

### Proof

(iv) ⟹ (iii): the exact sequence

```text
𝔪_x / 𝔪_x²  →  Ω¹_{𝒪_x / k}  →  Ω¹_{κ(x) / k}  →  0
```

(a special case of the conormal sequence for `Spec κ(x) ↪ Spec 𝒪_x`). Since `κ(x) / k` is finite separable,
`Spec κ(x) → Spec k` is étale, so `Ω¹_{κ(x) / k} = 0`. Then `𝔪_x / 𝔪_x² → Ω¹_{𝒪_x / k}` is surjective; the `df_i` images
generate, so the `df_i` themselves generate.

(ii) ⟹ (iv): when `X` and `Spec κ(x)` are both smooth over `k` at `x` (the latter automatic from `κ(x) / k` finite
separable, by II.1.3 or directly), the conormal sequence above is split exact (II.4.10(iv), file 15), so its leftmost
term injects. Counting ranks, the `df_i` and the `f_i mod 𝔪²` correspond. The basis on the right gives a generating set
on the left.

### Smooth ⟹ regular; converse over finite separable residue

extension

<!-- source: II.5.3 -->

_This result says: smoothness at `x` forces `𝒪_x` to be regular. The converse holds when the residue extension
`κ(x) / k` is finite separable._

**Corollary II.5.3.** Let `x ∈ X` of finite type over `k`. If `X` is smooth over `k` at `x`, then `𝒪_x` is regular.
Conversely, if `𝒪_x` is regular and `κ(x) / k` is finite separable, then `X` is smooth over `k` at `x`.

### Proof

The forward direction is II.3.1 (file 15). For the converse: take a regular system of parameters `(f_i)` of `𝒪_x`. By
II.5.2, the hypotheses (iv) hold, so II.5.1 applies and `X` is smooth at `x`.

### The perfect-field case

<!-- source: II.5.4 -->

_This result says: smooth implies regular always; regular implies smooth when `k` is perfect._

**Proposition II.5.4.** Let `X` be of finite type over `k`. If `X` is smooth over `k`, then `X` is regular. The converse
holds if `k` is **perfect**.

### Proof

The forward direction is the previous corollary. For the converse: when `k` is perfect, every residue extension
`κ(x) / k` of a closed point `x` is finite separable (perfect base; finite extension is always separable). By II.5.3,
`X` is smooth at every closed point. Smoothness is open (Proposition II.1.1, file 14), so `X` is smooth everywhere.

### The big theorem of II.5

<!-- source: II.5.5 -->

_This result says: five conditions are equivalent for `X` of finite type over `k` at `x`. They tie together smoothness,
freeness of `Ω¹`, generation of `Ω¹` by `n` elements, differential smoothness, and regularity after extension to a
perfect base._

**Theorem II.5.5.** Let `X` be of finite type over `k`, `x ∈ X`, `n = dim_x X`, `k′ ⊃ k` a perfect extension. The
following are equivalent:

1. `X` is **smooth** over `k` at `x`.
1. `Ω¹_{X/k}` is **free of rank `n`** at `x`.
1. `Ω¹_{X/k}` is **generated by `n` elements** at `x`.
1. `X` is **differentially smooth** over `k` at `x`.
1. There is an open neighborhood `U` of `x` such that `U ⊗_k k′` is **regular**.

### Proof

(i) ⟹ (ii) by Theorem II.4.3(ii) (file 15: smooth ⟹ `Ω¹` locally free of rank = relative dim). (ii) ⟹ (iii) is trivial.
(iii) ⟹ (i) is II.5.1 above.

(i) ⟺ (iv) by the smooth ⟺ flat + differentially smooth decomposition (file 15, II.4.18); flatness is automatic over a
field.

(i) ⟹ (v): smoothness is preserved by base extension (II.1.3(ii), file 14), so `U ⊗_k k′` is smooth over `k′`; by (i) ⟹
regular (II.5.4 for perfect `k′`), `U ⊗_k k′` is regular.

(v) ⟹ (i): over the perfect `k′`, regular ⟺ smooth (II.5.4), so `U ⊗_k k′` is smooth over `k′`; by II.4.13 (file 15),
smoothness descends along the faithfully flat extension `Spec k′ → Spec k`, giving `U` smooth over `k` and hence `X`
smooth at `x`.

### Field-extension version (Mac Lane / separating transcendence

basis)

<!-- source: II.5.6 -->

_This result says: for a localization `K` of a finite-type `k`-algebra (e.g. an extension of finite type), four
conditions are equivalent — including being a finite separable extension of a purely transcendental extension, having
`Ω¹_{K/k}`free of rank = transcendence degree, and being a separable extension of`k`._

**Corollary II.5.6.** Let `K` be a local Artin ring obtained by localizing an algebra of finite type over `k`. Let
`n = trdeg_k κ`, where `κ` is the residue field of `K`. The following are equivalent:

1. `K` is a finite separable extension of a purely transcendental extension `k(t₁, …, t_n)` of `k` — i.e. there is a
    **separating transcendence basis** `t₁, …, t_n`.
1. `Ω¹_{K/k}` is a **free `K`-module of rank `n`**.
1. `Ω¹_{K/k}` is a `K`-module **admitting `n` generators**.
1. The completion of `K ⊗_k K` for the topology defined by powers of the augmentation ideal is a "regular" augmented
    `K`-algebra, i.e. isomorphic to a formal power-series algebra over `K`.
1. `K` is a **separable extension** of `k` — i.e. for every non-zero `K`-derivation `D : K → M` over `k`, `M ≠ 0`.

### Proof outline

Reduce `K` to the local ring of the generic point of an irreducible `X` of finite type over `k`. The five conditions are
exactly II.5.5(i)–(v) for that case (with `k′` an algebraic closure of `k`). The only non-immediate step is "(v) `K`
separable over `k` ⟹ `X` smooth at the generic point": by II.4.13 reduce to `k = k′` algebraically closed; then `X` has
a `k`-rational point, smooth at that point by II.5.4, and a fortiori smooth at the generic point.

### Sidebar: the Mac Lane criterion

This sidebar paraphrases Bourbaki _Algèbre_ Chapter V §16 (the "Mac Lane criterion" cited by Grothendieck in the errata
to II.5). See [`mac-lane-separability`](appendix-black-boxes.md#mac-lane-separability) in the appendix.

For a field extension `K / k`, the following are equivalent:

- `K` is **separable** over `k` (every finitely generated intermediate extension has a separating transcendence basis;
    equivalently, `K ⊗_k k^{1/p^∞}` is reduced for `char k = p`).
- `Ω¹_{K/k}` is generated, as a `K`-module, by the differentials of a transcendence basis whose elements are linearly
    independent.
- For every finite collection `f₁, …, f_n ∈ K` whose differentials `df_i` are linearly independent in `Ω¹_{K/k}`, the
    elements `f_i` are algebraically independent over `k`.

The second form is what makes II.5.5 — "smooth ⟺ `Ω¹` free of the right rank" — a working theorem for any base field.
The third form is the technical statement Grothendieck cites in the II.5 errata to close the proof of II.5.6 without
circularity (the original proof relied on Zariski's "regular locus is open," whose standard proof uses differentials).

The proof of the third form (Bourbaki / Mac Lane): suppose `g ∈ k[t₁, …, t_n]` is a polynomial of minimal degree with
`g(f₁, …, f_n) = 0`. Differentiating,

```text
Σᵢ (∂g/∂t_i)(f₁, …, f_n) · df_i = 0.
```

Since the `df_i` are linearly independent, each `(∂g/∂t_i)(f₁, …, f_n) = 0`, hence each `∂g/∂t_i = 0` by minimality of
`g`. In characteristic `0`, this forces `g = 0`. In characteristic `p ≠ 0`, it forces `g = h(t₁^p, …, t_n^p)` for some
`h`; the Mac Lane criterion (separability) lets us conclude `h(f₁, …, f_n) = 0` too, hence `g = 0` again by minimality.
Contradiction.

### Remark on circular reasoning

Grothendieck's errata at the end of Exposé II flag this issue: the direct proof of II.5.5 / II.5.6 via Zariski's
"regular locus is open" used differential methods, hence assumed the very theorem under proof. Mac Lane's criterion,
established by purely algebraic means in Bourbaki, breaks the circle. Nagata later gave a non-differential proof of
Zariski's open-regularity theorem; we record this as
[`nagata-open-regular`](appendix-black-boxes.md#nagata-open-regular) in the appendix.

### Smooth via locally free `Ω¹` and separable generic points

<!-- source: II.5.7 -->

_This result says: `X` is smooth over `k` iff `Ω¹_{X/k}`is locally free and the local rings at generic points of
irreducible components are separable extensions of`k`. Over a perfect base the latter condition is automatic for reduced
`X`._

**Corollary II.5.7.** Let `X` be of finite type over `k`. Then `X` is smooth over `k` iff `Ω¹_{X/k}` is locally free
**and** the local rings at the generic points of the irreducible components of `X` are separable extensions of `k`. The
latter condition is automatic when `k` is perfect and `X` is reduced.

### Caveat on inseparability

A finite, _not necessarily separable_, extension `K / k` still has `Ω¹_{K/k}` free as a `K`-module — but the rank is
wrong. So `Spec K` has locally free `Ω¹` and is reduced, yet `Spec K` is not smooth over `k`. After base-changing to the
algebraic closure of `k`, one gets `Spec K ⊗_k k̄` non-reduced even though `Spec K` was reduced. The separability clause
in II.5.7 is genuine.

### Étale at a point: regular parameters + separating

transcendence

<!-- source: II.5.8 -->

_This result says: for `X` over `k` with the right-dimension setup, a morphism `X → Spec k[t₁, …, t_n]` is étale at `x`
iff the first `p` coordinates form a regular system of parameters of `𝒪_x` and the remaining `n − p` coordinates project
to a separating transcendence basis of `κ(x) / k`._

**Corollary II.5.8.** Let `X` be of finite type over `k`, `x ∈ X`, `n = dim_x X`, `p = dim 𝒪_x` (the codimension in `X`
of the closure of `x`). Then `n − p = trdeg_k κ(x)`. Let `f_i ∈ 𝒪_x`, `1 ≤ i ≤ n`, with `f_i ∈ 𝔪_x` for `1 ≤ i ≤ p`. The
following are equivalent:

1. The morphism `X → Spec k[t₁, …, t_n]` defined by the `f_i` is **étale** at `x`.
1. The `f_i`, `1 ≤ i ≤ p`, generate `𝔪_x` (i.e. form a **regular system of parameters** of `𝒪_x`), and the `df̄_j`,
    `p + 1 ≤ j ≤ n`, form a **basis** of `Ω¹_{κ(x) / k}` (equivalently, the classes of `f_j` in `κ(x)` form a
    separating transcendence basis).

### Proof

(i) ⟹ (ii): II.4.8 (file 15) gives a basis of `Ω¹_{X/k}(x)`. The images `df̄_i(x)` in `Ω¹_{κ(x)/k}` generate, and since
the first `p` of them vanish (the `f_i` lie in `𝔪_x`), the remaining `n − p` generate. Transcendence-degree counting
(Corollary II.5.6 (iii)) forces them to be a basis. Then II.4.9(ii) (file 15) is satisfied, which gives II.4.9(iii); the
`f_i`, `1 ≤ i ≤ p`, generate `𝔪_x`, and they are a regular system of parameters since `𝒪_x` has dimension `p`.

(ii) ⟹ (i): the conormal sequence `𝔪_x / 𝔪_x² → Ω¹_{𝒪_x / k} → Ω¹_{κ(x) / k} → 0` shows the `df_i(x)` generate
`Ω¹_{X/k}(x)`. Apply II.5.1.

### Regular + separable residue ⟺ smooth

<!-- source: II.5.9 -->

_This result says: four conditions on a point `x` of `X` over `k` are equivalent, including "smoothness at `x`" and
"`𝒪_x` regular plus `κ(x) / k` separable.""_

**Corollary II.5.9.** Setup as in II.5.8. The following are equivalent:

1. `𝒪_x` is regular and `κ(x) / k` is a **separable extension** of `k`.

1. `X` is smooth over `k` at `x`, and the canonical map

    ```text
    𝔪_x / 𝔪_x²  →  Ω¹_{𝒪_x / k} ⊗ κ(x)  =  Ω¹_{X/k}(x)
    ```

    is **injective**.

1. There exist `f_i ∈ 𝒪_x`, `1 ≤ i ≤ n`, with `f_i ∈ 𝔪_x` for `1 ≤ i ≤ p`, such that the morphism
    `X → Spec k[t₁, …, t_n]` defined by the `f_i` is étale at `x`.

1. There exist `f_i ∈ 𝒪_x`, `1 ≤ i ≤ n`, such that the `f_i`, `1 ≤ i ≤ p`, generate `𝔪_x` and the `df_j(x)`,
    `p + 1 ≤ j ≤ n`, generate `Ω¹_{κ(x) / k}` over `κ(x)`.

### Proof

(iii) ⟺ (iv) is II.5.8. By II.4.9 these conditions are equivalent to "X smooth at `x` and II.4.10(ii) satisfied,"
equivalently "X smooth at `x` and II.4.10(iv) satisfied," which gives (ii). The condition "X smooth at `x` and
II.4.10(i) satisfied" — i.e. `κ(x) / k` separable — implies (i).

For the reverse, (i) ⟹ (iv): use the regularity of `𝒪_x` to find a regular system of parameters `(f_i)`, `1 ≤ i ≤ p`.
The separability of `κ(x) / k` and II.5.6(iii) give a separating transcendence basis lifted to `(df_j(x))`,
`p + 1 ≤ j ≤ n`.

### The closing equivalence

<!-- source: II.5.10 -->

_This result says: when the residue field `κ(x) / k` is a separable extension, smooth at `x` is the same as regular at
`x`._

**Corollary II.5.10.** Let `x ∈ X` of finite type over `k`, with `κ(x) / k` separable. Then `X` is smooth over `k` at
`x` iff `𝒪_x` is regular.

### Why this closes the picture

Smoothness specialized to a base field divides cleanly:

- Over a **perfect base** (e.g. `ℚ`, `𝔽_p`, any algebraically closed field of characteristic `0`): smooth = regular at
    every point. The étale theory of file 12 lives entirely inside this case at relative dimension `0`.
- Over an **imperfect base** (e.g. `𝔽_p(t)`): the gap between smooth and regular is exactly inseparability. A regular
    point whose residue extension is inseparable (e.g. the closed point of `Spec 𝔽_p(t^{1/p})` over `𝔽_p(t)`) is regular
    but not smooth.

This recovers the étale theory: an étale morphism `Spec L → Spec k` of fields, viewed as smooth of relative dimension
`0`, is smooth iff `L / k` is finite separable — which is exactly the file-04 definition of unramified for fields.

## Continuing on

The étale theory of Exposé I and the smooth theory of Exposé II are now both in hand. Étale = smooth of relative
dimension `0`; smooth = locally étale over a polynomial scheme; the Jacobian criterion (II.4.10, file 15) reads as the
classical "compute `dF` and check it is non-zero" for hypersurfaces; the differential exact sequence (II.4.3, file 15)
splits for smooth morphisms. The toy examples — `ℤ[√2]` for étale, `ℤ[t]` and the elliptic curve for smooth — exhibit
the two relative-dimension regimes (`0` and `≥ 1`) of the same underlying theory.

The gentle reading continues with **Exposé III** in files 17–22. Files 17–18 are extra preparation specific to Exposé
III (sheaf cohomology in low degrees, torsors, the tangent sheaf, formal schemes); files 19–22 are the rewrite proper
(formally smooth and lifting characterization; local infinitesimal extension; H¹/H² obstructions for global extension;
algebraization over complete local rings). One headline payoff is **Corollary III.7.4** in file 22: every smooth proper
curve over `k` lifts to a smooth proper curve over any complete local ring with residue field `k`. The reading then
continues with **Exposé IV** — _Flat morphisms_ — in files 23–27 (Tor / spectral-sequence / Noether prep in 23; flatness
sorites and faithful flatness in 24; completion and free modules in 25; the local flatness criterion in 26;
constructibility, openness, and generic flatness in 27). The reading then continues with **Exposé V** — _The fundamental
group: generalities_ — in files 28–33 (topological prep in 28; profinite / pro-object prep in 29;
preschemes-with-`G`-action and principal coverings in 30; étale automorphisms and the axiomatic Galois theorem in 31;
Galois categories and exact functors in 32; the étale fundamental group `π₁(S, a)` in 33). The closing of the project
sits at the end of file 33.
