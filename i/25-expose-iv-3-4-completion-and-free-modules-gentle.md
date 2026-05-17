# Exposé IV, sections 3–4: completion and free modules (gentle)

## What this file is about

The previous file gave the rules of behaviour for well-varying algebraic families. This file applies them in two
situations that appear constantly in practice.

The first is the relationship between a ring and its completion at an ideal, the algebraic analogue of zooming in on a
fixed locus and remembering every infinitesimal layer around it. The completion always varies as well as the original
ring, and sometimes more so. The second is local. Near a single point of a base, a finitely generated package of data
may or may not be as simple as possible, meaning a finite stack of free copies of the base ring. The file gives a clean
criterion for being a free stack, phrased in terms of behaviour along a single infinitesimal layer. The criterion is a
skeleton version of the deeper one in the next file.

Two themes carried in two short sections. **§3** says completion is flat (and faithfully flat under a radical hypothesis
on the defining ideal). This is where the appendix rows `completion-flat` and `completion-test-for-flatness`, used
freely since file 04, get their proofs. **§4** connects flatness to freeness over local rings via Nakayama and the
**`gr` criterion**, the algebraic precursor to the local flatness theorem of §5 (file 26). Both sections are short —
together they take about 30 lines of source text — but their content is load-bearing for the rest of the exposé.

The slogans:

> **§3.** Completion `Â` is `A`-flat (IV.3.1). It is faithfully flat exactly when the defining ideal `I` lies in the
> radical of `A` (IV.3.2). For a noetherian local ring with `I = 𝔪`, faithful flatness always holds.

> **§4.** Over a local ring with `I` either nilpotent or in the radical with `M` finite, `M` is **free** iff `M ⊗ A/I`
> is free and `Tor^A₁(M, A/I) = 0`. Replace the Tor-vanishing by the **`gr` isomorphism** condition and the equivalence
> still holds (IV.4.2). When `A/I` is a field, "free" coincides with "projective," "flat," and the Tor / `gr` conditions
> (IV.4.3) — the local flatness criterion in skeleton form.

Both sections carry forward the framework of [file 24](24-expose-iv-1-2-sorites-and-faithfully-flat-gentle.md): flatness
is exactness of `M ⊗_A −`, faithful flatness is exactness with reflection. The new ingredient is the **`I`-adic
filtration** of an `A`-module: the descending chain `M ⊃ IM ⊃ I²M ⊃ …`, with associated graded module
`gr_I(M) := ⊕_{n ≥ 0} I^n M / I^{n+1} M`. This is the algebraic shape of "Taylor expansion at the closed subscheme
`Spec(A/I)`."

## IV.3 Relations with completion

<!-- source: IV.3 -->

### Setup: `I`-adic completion of modules

Let `A` be a noetherian ring, let `I ⊂ A` be an ideal, and let `M` be an `A`-module. The **`I`-adic completion** of `M`
is

```text
M̂ := lim_n M / I^n M,
```

an `Â`-module where `Â = lim_n A/I^n` is the `I`-adic completion of `A`. (See
[file 18](18-formal-schemes-and-i-adic-completion-gentle.md) for the full development; the original case `M = 𝔪`-adic
completion of a noetherian local ring is in [file 04](04-finiteness-unramified-flat-etale.md).) There is a canonical
`Â`-linear map

```text
M ⊗_A Â → M̂,
```

natural in `M`. We will see in a moment that for `M` finitely generated and `A` noetherian, this map is an isomorphism.

The key fact we will use is **Krull's intersection theorem**: for `N ⊂ M` a submodule of a finite-type module over
noetherian `A`, the `I`-adic topology of `N` agrees with the topology induced from `M`. Equivalently, for every `n`
there exists `m ≥ n` such that `I^m M ∩ N ⊂ I^n N`. Source: appendix row `krull-intersection`.

A standard consequence: when `M` ranges over **finitely generated `A`-modules**, the functor `M ↦ M̂` is **exact**. The
proof is short. Take a short exact sequence `0 → N → M → P → 0` of finite-type modules. The induced sequence
`0 → N̂ → M̂ → P̂ → 0` of completions: surjectivity on the right is clear (by passing to the limit of the surjections
`M / I^n M → P / I^n P`); the content is exactness on the left, which is exactly what Krull gives — `N̂ → M̂` is
injective because the topology of `N` matches the induced topology from `M`, so the `I`-adic Cauchy sequences of `N` are
detected inside `M`.

For the full proof, see Atiyah-Macdonald §10.10 or Liu §1.3
(`papers/books/algebraic-geometry-arithmetic-curves/01-03-formal-completion.md`).

### Proposition: completion is flat

<!-- source: IV.3.1 -->

_This proposition says: for any noetherian ring `A` and ideal `I`, the `I`-adic completion `Â` is flat over `A`. The
flatness holds without any local or radical hypothesis._

**Proposition IV.3.1.** _Let `A` be a noetherian ring and `I ⊂ A` an ideal. The separated `I`-adic completion `Â` is
flat over `A`._

**Proof.** We need `Â ⊗_A −` to be exact on `A`-modules. By the standard reductions
([file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md) plus the IV.1 reductions): it
suffices that `Â ⊗_A N` is exact in `N` for `N` of finite type. For finite-type `N`, `Â ⊗_A N = N̂` (the canonical map
is an iso, by resolving `N` by `L₁ → L₀ → N → 0` with `L₀, L₁` free of finite rank, applying `Â ⊗_A −`, and noting that
both `Â ⊗_A −` and the completion functor `̂` agree on free modules of finite rank and are right exact). The functor
`N ↦ N̂` is exact on finite-type modules by Krull's theorem (above). So `Â ⊗_A −` is exact on finite-type modules, hence
on all modules. ∎

This proves the first half of the appendix row `completion-flat`.

### Corollary: faithfully flat ⟺ `I` in radical

<!-- source: IV.3.2 -->

_This corollary says: `A → Â` is faithfully flat iff the defining ideal `I` lies in the radical of `A`. For a local ring
with `I = 𝔪` (the most common case), this always holds._

**Corollary IV.3.2.** _Under the hypotheses of IV.3.1, the following are equivalent:_

1. _`Â` is faithfully flat over `A`._
1. _`I` is contained in the radical of `A`._

**Proof.** By IV.2.1 (iii), `Â` is faithfully flat ⟺ `Â ⊗_A A/𝔪 ≠ 0` for every maximal ideal `𝔪`. Compute:
`Â ⊗_A A/𝔪 = (A/𝔪)^{̂} = lim_n (A/𝔪) / I^n (A/𝔪)`. If `I ⊂ 𝔪`, then `I (A/𝔪) = 0` and the inverse limit is `A/𝔪 ≠ 0`. If
`I ⊄ 𝔪`, then `I (A/𝔪) = A/𝔪` (the image of `I` in `A/𝔪` is the unit ideal), so `(A/𝔪) / I^n (A/𝔪) = 0` for all `n ≥ 1`,
hence the inverse limit is `0`.

So `Â ⊗_A A/𝔪 ≠ 0` ⟺ `I ⊂ 𝔪`. The condition "for every maximal `𝔪`" then says `I` is in the intersection of all maximal
ideals of `A`, i.e. `I` is in the radical. ∎

This proves the rest of `completion-flat` and is one direction of `completion-test-for-flatness`. The other direction —
that flatness over `Â` lifts to flatness over `A` for finite- type modules — comes out of the local flatness criterion
(IV.5.8, file 26).

The most-used special case: for `(A, 𝔪)` a noetherian local ring and `I = 𝔪`, `A → Â` is faithfully flat. Combined with
IV.2.6 (iv): the natural map `A → Â` is injective, and `Â / A` is `A`-flat. Combined with IV.2.6 (vi): `I Â ∩ A = I` for
every ideal `I`, the ideal-preservation form of Krull.

These two corollaries also explain the **completion as algebraic microscope** picture often invoked in deformation
theory: completing at `𝔪` does not lose information (faithful flatness), preserves all ideals (Krull), and intertwines
tensor product correctly (flatness). It is the algebraic embodiment of "zoom in to a closed point without distorting the
picture."

## IV.4 Relations with free modules

<!-- source: IV.4 -->

### Setup: the `gr` of an `I`-adic filtration

The **associated graded** of `A` along `I` is the graded ring

```text
gr_I(A) := ⊕_{n ≥ 0} I^n / I^{n+1},
```

with multiplication induced by the multiplication in `A`. The zeroth piece is `gr_I⁰(A) = A/I`. (See
[notation.md](notation.md) for the symbol distinction between `gr_I^n(R)` of a single graded piece and `gr_I(R)` of the
full ring.)

For an `A`-module `M`, the **associated graded** along the `I`-adic filtration is the `gr_I(A)`-module

```text
gr_I(M) := ⊕_{n ≥ 0} I^n M / I^{n+1} M,
```

with the natural action. The zeroth piece is `gr_I⁰(M) = M/IM`, which is naturally an `A/I`-module.

There is always a canonical `gr_I(A)`-linear surjection

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

— the map sending `(m mod IM) ⊗ (a mod I^{n+1})` to `am mod I^{n+1}M`. This map is the central object of §IV.4: when it
is an **isomorphism**, the `I`-adic structure of `M` is "freely generated" by `M/IM` over `gr_I(A)`. This is a strong
condition; it is the lifting condition for "free over `A/I` ⟹ free over `A`," in the precise sense developed below.

### Proposition: `M` free iff `M ⊗ A/I` free and `Tor₁ = 0`

<!-- source: IV.4.1 -->

_This proposition says: under one of two standard local hypotheses (`I` nilpotent, or `A` noetherian with `I` in the
radical and `M` finite), one can lift "free over `A/I`" to "free over `A`" provided `Tor^A₁(M, A/I) = 0`. The
Tor-vanishing is the obstruction to lifting._

**Proposition IV.4.1.** _Let `A` be a ring, `I ⊂ A` an ideal, `M` an `A`-module. Suppose at least one of the following:_

1. _`I` is nilpotent;_
1. _`A` is noetherian, `I` is contained in the radical of `A`, and `M` is finitely generated._

_Then `M` is free over `A` if and only if `M ⊗ A/I` is free over `A/I` and `Tor^A₁(M, A/I) = 0`._

**Proof.** Necessity is clear: if `M` is free, then `M ⊗ A/I` is free of the same rank, and `Tor^A₁(M, −) = 0` for all
arguments.

For sufficiency, choose elements `(e_i)_{i ∈ J}` of `M` whose images in `M ⊗ A/I = M / IM` form a free basis over `A/I`.
(In case (b), `J` is finite by Nakayama applied to the finite-type quotient `M/IM`.) Form the free `A`-module `L := A^J`
on the same index set, and the unique `A`-linear map `L → M` sending the standard basis to `(e_i)`. Tensoring with `A/I`
gives a map `L ⊗ A/I → M ⊗ A/I`, which by construction is the identity on the chosen bases — hence an isomorphism.

We claim `L → M` is **surjective**. Let `Q := Coker(L → M)`. Tensoring `L → M → Q → 0` with `A/I`: since
`L ⊗ A/I → M ⊗ A/I` is an isomorphism, `Q ⊗ A/I = 0`. By Nakayama (appendix row `nakayama`) — valid in case (a) because
`I` is nilpotent and in case (b) because `Q` is a finite-type quotient of finite- type `M` and `I` is in the radical —
`Q = 0`.

We claim `L → M` is **injective**. Let `R := Ker(L → M)`. The short exact sequence `0 → R → L → M → 0` gives the long
exact sequence (in `Tor`)

```text
… → Tor^A₁(M, A/I) → R ⊗ A/I → L ⊗ A/I → M ⊗ A/I → 0.
```

By hypothesis `Tor^A₁(M, A/I) = 0`. The map `L ⊗ A/I → M ⊗ A/I` is an iso. So `R ⊗ A/I = 0`. Apply Nakayama again —
valid in case (a) directly, and in case (b) because `R` is finite-type as a submodule of a finite-type free `L` over
noetherian `A` — to conclude `R = 0`.

So `L → M` is an isomorphism, and `M` is free. ∎

The proof has the shape: lift a basis on the quotient, use Nakayama (twice) to clear the cokernel and the kernel. The
Tor-vanishing hypothesis is exactly what makes the second Nakayama applicable. This is the "Nakayama for flatness"
pattern that the rest of §§4–5 will refine.

### Corollary: the `gr` form

<!-- source: IV.4.2 -->

*This corollary says: the Tor-vanishing in IV.4.1 can be replaced by the more geometric condition "the canonical map
`gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)` is an isomorphism," and the equivalence still holds.*

**Corollary IV.4.2.** _Under the hypotheses of IV.4.1, one may replace `Tor^A₁(M, A/I) = 0` by the condition that the
canonical surjective map_

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

_is an isomorphism. That is, `M` is free over `A` iff `M ⊗ A/I` is free and the displayed map is an isomorphism._

**Proof.** Necessity: if `M` is free, the displayed map is clearly an iso (a free module has the "Taylor-expansion-free"
property at every order).

Sufficiency: redo the proof of IV.4.1, but check injectivity of `L → M` using the `gr`-isomorphism instead of
Tor-vanishing. The `gr` form gives that the induced map of associated graded modules `gr_I(L) → gr_I(M)` is an
isomorphism (computed degree by degree from the iso on `gr⁰` plus the freeness of `gr_I(A)` over its own zeroth piece).
The kernel of `L → M` then has zero image in every `gr` piece, hence lives in the intersection of the `I^n L`. In case
(a) (nilpotent `I`), this intersection is zero. In case (b) (noetherian, `I` in radical, finite), the intersection is
zero by Krull's intersection theorem. ∎

The `gr` form is the form that **inducts** well: in §IV.5 we will iterate this criterion across an `I`-adic filtration,
and the `gr` formulation makes the induction step a clean graded-module statement.

### Corollary: when `A/I` is a field, five equivalent conditions

<!-- source: IV.4.3 -->

_This corollary says: when the quotient `A/I` is a field, all of the following are equivalent: free, projective, flat,
Tor- vanishing, and `gr`-isomorphism. This is the single most practically useful instance of the Tor / `gr` criteria._

**Corollary IV.4.3.** _Suppose `A/I` is a field. Then for an `A`-module `M`, the following are equivalent:_

1. _`M` is free over `A`._
1. _`M` is projective over `A`._
1. _`M` is flat over `A`._
1. _`Tor^A₁(M, A/I) = 0`._
1. *The canonical map `gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)` is an isomorphism.*

**Proof.** Free ⟹ projective ⟹ flat is general. Flat ⟹ (iv) is the `Tor` characterization (file 23). (iv) ⟹ (i) by
IV.4.1 (taking `M ⊗ A/I` free over the field `A/I`, which is automatic), and similarly (v) ⟹ (i) by IV.4.2. So (iv) and
(v) each imply (i), and (i) implies (iv) and (v). All five are equivalent. ∎

The hypothesis "`A/I` is a field" makes "`M ⊗ A/I` is free over `A/I`" automatic (every vector space is free), which is
why the criterion collapses cleanly.

This corollary applies in two regimes the gentle reader will revisit constantly:

- **`A` artinian local with maximal ideal `I` nilpotent.** Then `A/I` is the residue field, and IV.4.3 says: every flat
    `A`-module (over an artinian local ring) is free. This is the statement used in file 04 to underwrite "finite + flat
    over a local ring = free."
- **`A` noetherian local, `I = 𝔪`, `M` of finite type.** Same conclusion: flat ⟺ free.

The first regime is part (a) of the IV.4.1 hypothesis; the second is part (b). Both are routinely invoked in the étale
and smooth theory.

### Corollary: noetherian local integral form

<!-- source: IV.4.4 -->

_This corollary says: in the noetherian local integral case, the five equivalent conditions of IV.4.3 are also
equivalent to "the rank at the generic point equals the rank at the closed point," which is the most concrete and
arithmetically intuitive form of the criterion._

**Corollary IV.4.4.** _Let `A` be a noetherian local integral ring with maximal ideal `𝔪 = I`, residue field `k = A/I`,
and field of fractions `K = Frac(A)`. Let `M` be a finite-type `A`-module. Then the equivalent conditions (i)–(v) of
IV.4.3 are also equivalent to:_

1. _`M ⊗_A K` and `M ⊗_A k` are vector spaces of the same dimension._

_Equivalently: the rank of `M` at the generic point equals the minimum number of generators of `M`._

**Proof.** Necessity: if `M` is free of rank `n`, then `M ⊗_A K = K^n` and `M ⊗_A k = k^n`, both of dimension `n`.

Sufficiency: let `n = dim_k M ⊗_A k`. Choose `n` elements of `M` whose images in `M / 𝔪 M` form a `k`-basis. The free
`A`- module `L = A^n` maps to `M`, and `L ⊗_A k → M ⊗_A k` is an iso. By Nakayama (`L → M → Coker → 0`, then tensor with
`k`, get cokernel zero, conclude surjective), `L → M` is surjective. Tensoring with `K`: `L ⊗_A K → M ⊗_A K` is a
surjection of `K`-vector spaces of the same dimension `n`, so an iso. The kernel of `L → M`, after tensoring with `K`,
is zero; but the kernel is finite-type over `A` (submodule of free `L` of rank `n` over noetherian `A`), and a
finite-type `A`-module with `(−) ⊗_A K = 0` is torsion. Now use that `A` is integral and the kernel embeds in `L` which
is `A`-flat (free), hence torsion-free. So the kernel is both torsion and torsion-free, hence zero. So `L → M` is iso,
and `M` is free. ∎

The exercise the source flags: generalize to the case where `A` has no nilpotents (i.e., reduced) — here one requires
that the ranks of `M` at the **minimal** primes of `A` all equal `dim_k M ⊗_A k`. We do not pursue this; it appears
occasionally in the EGA literature.

### Two regimes where IV.4.3 applies

The source records, after IV.4.4, the standard summary:

> The preceding result (IV.4.3) is valid in the following two cases:
>
> - `M` is an arbitrary module over a local ring `A` whose maximal ideal `I` is nilpotent (e.g. an artinian local ring).
> - `M` is a module of finite type over a noetherian local ring.

These are exactly the two regimes the étale and smooth theories have used in files 04, 05, 11, 14, 15. The black box
`local-flatness-criterion` of the appendix is the second of these regimes; the artinian special case is the deformation-
theoretic regime that recurs in [file 19](19-expose-iii-1-2-formally-smooth-and-lifting-gentle.md) and
[file 20](20-expose-iii-3-4-local-infinitesimal-extension-gentle.md).

### Worked example: the `gr` criterion in action

Take `A = k[t]_{(t)}` the local ring at the origin of the affine line over a field `k`, with maximal ideal `I = (t)`.
The associated graded ring is

```text
gr_I(A) = ⊕_{n ≥ 0} (t^n) / (t^{n+1}) ≅ k[T],
```

a polynomial ring in one variable (set `T = closure(t)`). The zeroth piece is `gr_I⁰(A) = A/I = k`.

Take a finite-type `A`-module `M = A`. Trivially free. The `gr` condition:
`gr_I⁰(M) ⊗_k gr_I(A) = k ⊗_k k[T] = k[T] = gr_I(M)`, isomorphism.

Take `M' = A / (t²)`. This is the artinian quotient — and now the
`gr_I^n(M') = (t^n M') / (t^{n+1} M') = (t^n / t^{n+2})` which equals `k` for `n = 0, 1` and `0` for `n ≥ 2`. So
`gr_I(M') = k ⊕ k T`, with `T² = 0` in `gr_I(M')` because `t² M' = 0`. The right side
`gr_I⁰(M') ⊗_k gr_I(A) = k ⊗_k k[T] = k[T]` has `T² ≠ 0`. The canonical map `k[T] → gr_I(M')` sends `T^n` to
`t^n mod (t^{n+1})M'`, and becomes zero for `n ≥ 2`. Not an isomorphism.

So `M'` fails the `gr` criterion, and IV.4.2 then says `M'` is not `A`-free — which is independently obvious (`A`-rank
of `M'` is `0`, but `M' ≠ 0`). The `gr` failure encodes the algebraic nature of the failure: the relation `t² = 0` in
`M'` is not present in `A`, so `M'` cannot be free.

A second, arithmetic, instance. Take `A = ℤ_{(p)}` (the localization of `ℤ` at a prime `p`) with `I = (p)`. The
associated graded ring is `gr_I(A) = ⊕_{n ≥ 0} (p^n) / (p^{n+1}) ≅ 𝔽_p[T]` (graded by the powers of `p`, with
`T = closure(p)` of degree 1). For `M = ℤ_{(p)}` (free of rank 1), the `gr` map is an iso. For
`M' = ℤ_{(p)} / (p) = 𝔽_p` (the residue module), one has `gr_I⁰(M') = 𝔽_p` and `gr_I^n(M') = 0` for `n ≥ 1` because
`p · 𝔽_p = 0`. The right side `gr_I⁰(M') ⊗_{𝔽_p} gr_I(A) = 𝔽_p ⊗_{𝔽_p} 𝔽_p[T] = 𝔽_p[T]` carries `T^n ≠ 0` for all `n`.
So the canonical map `𝔽_p[T] → gr_I(M')` is non-zero in degree `0` and zero in higher degree — not an iso. And
`M' = 𝔽_p` is not `A = ℤ_{(p)}`-free (it has `p`-torsion), so IV.4.2 confirms the failure.

The take-away: the `gr` criterion is **strict** as a freeness test under the IV.4.1 (a)–(b) hypotheses. When it holds
plus `M ⊗ A/I` is `A/I`-free, the module is `A`-free; when it fails, the module is not `A`-free.

### Closing remark

This file's two propositions IV.3.1 and IV.4.1 are the algebraic backbone of the deformation-theoretic story. IV.3.1
says "completion is a flat (and faithfully flat, under mild hypotheses) microscope on a local ring." IV.4.1–IV.4.3 say
"over local rings of the regimes you actually encounter, flat is free." Together they justify the universal use of these
facts in files 04–22.

In §5 (file 26), we will iterate the `gr` form of IV.4.2 across an `I`-adic filtration: instead of "free given
Tor-vanishing on `A/I`," we will get "flat given conditions on every thickening `A/I^n`." That iteration is the local
flatness criterion (IV.5.6), the centerpiece of the exposé.

Read on into [file 26](26-expose-iv-5-local-flatness-criterion-gentle.md) for the local flatness criterion.
