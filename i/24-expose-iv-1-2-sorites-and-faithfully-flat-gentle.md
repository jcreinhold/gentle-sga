# Exposé IV, sections 1–2: sorites on flat modules, faithfully flat modules (gentle)

## What this file is about

Imagine an algebraic family of shapes parametrised by a base. As the parameter moves, the shape over each value
changes. The cleanest families are the ones with no surprises: nothing jumps up in dimension at a special value,
nothing collapses, nothing disappears. The technical word for this kind of well-behaved variation, used as a black
box in almost every file so far, is flatness.

This file opens the box. The first section collects the closure properties: flatness is preserved under composition,
under base change, and under combinations of these. The second section sharpens flatness into a stronger condition
called faithful flatness, which corresponds to the geometric notion of a covering map that reaches every point of
the base. This is the algebraic backbone of descent, treated much later in the seminar.

Files 04, 05, 11, 12, and 14–22 have used flatness as a black box. Whenever the étale or smooth theory needed "flat is
preserved under base change," "the flat locus is open," or "flat plus finite over a local ring is free," we cited the
appendix rows `flatness-sorites`, `local-flatness-criterion`, `completion-flat`, or `completion-test-for-flatness` and
moved on. This is the file that opens those boxes.

The view from inside is plain. **Flatness is exactness of the functor `M ⊗_A −`.** Everything else in this exposé
follows from that one definition by careful bookkeeping with `Tor` (file 23). The sorites of §IV.1 — composition, base
change, transitive combination, behavior under localization — are the closure properties one would guess from the
definition, and they are proven by chasing the relevant Tor terms through long exact sequences. The single non-routine
fact in §IV.1 is **IV.1.1**, the "as good as split" lemma: a short exact sequence with a flat quotient stays exact under
any tensor product, and `M` and `M'` are flat together.

Section §IV.2 introduces the strengthening of flatness most relevant to descent: **faithful flatness**. A faithfully
flat `A`-module `M` is one for which `M ⊗_A −` _reflects_ exactness, not just preserves it — the tensor product detects
whether a sequence of `A`-modules was already exact. Geometrically: if `M = B` is a faithfully flat `A`-algebra, then
`Spec B → Spec A` is **surjective** (IV.2.3), and conversely flatness plus surjectivity implies faithful flatness
(IV.2.6). The right mnemonic: faithful flatness is the algebraic content of "covering map" in the geometric sense that
every prime of the base is hit.

The slogan that runs through:

> **Flat = `M ⊗_A −` is exact. Faithfully flat = `M ⊗_A −` is exact and reflects exactness, equivalently
> `M ⊗ N = 0 ⟹ N = 0`, equivalently `Spec(B) → Spec(A)` is surjective in the algebra case.** Flatness underwrites the
> closure properties used everywhere in EGA; faithful flatness is the descent hypothesis Grothendieck's school built
> around.

Throughout this file we write `Tor^A_i(M, N)` for the left-derived functor of `M ⊗_A −`. The reader should consult
[file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md) for the definition, the long exact
sequence, the symmetry, and the vanishing characterization of flatness.

A long-form sequel to this exposé exists in EGA IV §§11–12, where the systematic study of fiber dimension, cohomological
dimension, and depth for `X → Y` of finite type with coherent `F` flat over `Y` is carried out. We do not reproduce it;
the appendix row `ega-fibers-systematic` records the pointer. The Bourbaki _Algèbre Commutative_ I (Modules plats)
presentation of these sorites covers the case of a non-commutative base ring; we work in the commutative setting
throughout, and refer to the appendix row `bourbaki-flat-modules` for the alternative.

## IV.1 Sorites on flat modules

<!-- source: IV.1 -->

### Setup: the definition

An `A`-module `M` is **flat**, or `A`-flat, if the functor

```text
T_M : N ↦ M ⊗_A N
```

— which is in any case right exact — is **exact**, i.e. carries monomorphisms to monomorphisms. Equivalently (file 23):

> `M` is flat ⟺ `Tor^A₁(M, N) = 0` for every `A`-module `N` ⟺ `Tor^A_i(M, N) = 0` for every `N` and every `i ≥ 1`.

Two reductions are useful and we will use them often.

- Since `Tor` commutes with directed colimits, it is enough to verify these vanishings for `N` of finite type.
- A finitely generated `N` admits a composition series whose successive quotients are monogenic, i.e. of the form `A/I`
    for an ideal `I`. So it is enough to verify `Tor^A₁(M, A/I) = 0` for ideals `I` of finite type.

For `N = A/I`, the long exact sequence applied to `0 → I → A → A/I → 0` reads

```text
0 = Tor^A₁(M, A) → Tor^A₁(M, A/I) → I ⊗_A M → A ⊗_A M → A/I ⊗ M → 0,
```

so `Tor^A₁(M, A/I) = 0` if and only if the natural map

```text
I ⊗_A M → IM
```

is **injective**. Combined with the always-surjective map of the same shape, this says

> `M` is flat ⟺ `I ⊗_A M → IM` is an isomorphism for every ideal `I` (and it suffices to consider `I` of finite type).

This is a working criterion in concrete situations: to verify flatness, check that tensoring with `M` does not introduce
relations among elements of an ideal that were independent in `A`.

### Closure properties

The closure properties below all follow from the exactness characterization. We list them and indicate the proof.

- **Direct sums and direct factors.** If `(M_α)` is a family of flat `A`-modules, then `⊕ M_α` is flat (tensor product
    commutes with direct sums; direct sums of exact functors are exact). A direct factor of a flat module is flat (a
    retract of an exact functor is exact).
- **Free, projective ⟹ flat.** `A` is `A`-flat (the identity functor is exact). So a free `A`-module is flat. A
    projective `A`-module is a direct factor of a free one, hence flat.
- **Tensor product.** If `M₁, M₂` are `A`-flat, then `M₁ ⊗_A M₂` is `A`-flat: tensoring with `M₁ ⊗_A M₂` is the
    composition of tensoring with `M₂` and then with `M₁`, both exact.
- **Base change.** If `M` is `A`-flat and `A → B` is any ring map, then `M ⊗_A B` is `B`-flat: for any `B`-module `N`,
    `(M ⊗_A B) ⊗_B N = M ⊗_A N` (associativity), and the right side is exact in `N` because `M ⊗_A −` is exact and the
    underlying `A`-module functor is exact.
- **Transitive composition.** If `M` is `B`-flat and `B` is `A`-flat, then `M` is `A`-flat: tensoring with `M` over `A`
    is the composition of tensoring with `B` over `A` (exact) and then with `M` over `B` (exact).
- **Localization is flat.** For `S ⊂ A` a multiplicative set, `S⁻¹A` is `A`-flat because `S⁻¹A ⊗_A N = S⁻¹N` is an exact
    functor in `N` (the universal property of localization preserves exactness). Consequently, if `M` is `A`-flat then
    `S⁻¹M = S⁻¹A ⊗_A M` is `S⁻¹A`-flat by base change, and (more strongly) is `A`-flat by transitive composition.

The reader who wants the subobject-bookkeeping consequences — that for an exact functor `T` and submodules
`N', N'' ⊂ N`, `T(N' ∩ N'') = T(N') ∩ T(N'')` and `T(N' + N'') = T(N') + T(N'')` — can extract them from the same
exactness of `M ⊗_A −`. We will not need them in displayed form.

### Proposition: short exact sequence with flat quotient

<!-- source: IV.1.1 -->

_This proposition says: in a short exact sequence whose right-hand term is flat, the sequence behaves under tensor
product as if it were split — it remains exact after tensoring with anything, and the middle term is flat exactly when
the left term is._

**Proposition IV.1.1.** _Let_

```text
0 → M' → M → M'' → 0
```

_be an exact sequence of `A`-modules with `M''` flat. Then:_

1. _The sequence remains exact after tensoring with any `A`-module `N`._
1. _`M` is flat if and only if `M'` is flat._

**Proof.** (1) Apply `− ⊗_A N` to the short exact sequence. The long exact sequence in `Tor` reads

```text
… → Tor^A₁(M'', N) → M' ⊗_A N → M ⊗_A N → M'' ⊗_A N → 0.
```

Since `M''` is flat, `Tor^A₁(M'', N) = 0` (file 23, vanishing characterization), so the displayed three-term sequence on
the right is exact and the connecting map vanishes. So `0 → M' ⊗ N → M ⊗ N → M'' ⊗ N → 0` is exact.

(2) Apply `− ⊗_A N` to the same sequence and look further left in the long exact sequence:

```text
Tor^A₂(M'', N) → Tor^A₁(M', N) → Tor^A₁(M, N) → Tor^A₁(M'', N).
```

By flatness of `M''`, the outer two terms vanish. So `Tor^A₁(M', N) ≅ Tor^A₁(M, N)` for every `N`. The vanishing
characterization gives `M'` flat ⟺ `M` flat. ∎

The slogan in the source is:

> "From the point of view of behavior under tensor products, flat modules are 'as good' as free or projective modules;
> the exact sequence of IV.1.1 is 'as good' as if it split."

### Proposition: flatness is local on the second ring

<!-- source: IV.1.2 -->

_This proposition says: when an `A`-module structure is built on top of a `B`-module by way of a ring map `A → B`, the
flatness question is local on `B` — it can be checked at the maximal ideals of `B`. The first half of the proposition
records the trivial direction (localization is flat), and the second half is the substantive local-to-global._

**Proposition IV.1.2.** _Let `A → B` be a ring homomorphism, let `M` be a `B`-module, and let `T` be a multiplicative
set in `B`._

1. _If `M` is `A`-flat, then `T⁻¹M` is `A`-flat (and hence `S⁻¹A`-flat for every multiplicative set `S` of `A` mapping
    into `T`)._
1. *Conversely, if `M*𝔫`is flat over`A*𝔫`for every maximal ideal`𝔫`of`B`(equivalently over`A*𝔪`where`𝔪`is the inverse
    image of`𝔫`in`A`), then `M`is`A`-flat.*

**Proof.** Both halves use the functorial isomorphism

```text
T⁻¹M ⊗_A N = T⁻¹(M ⊗_A N),
```

natural in the `A`-module `N`. (Both sides identify with `T⁻¹B ⊗_B M ⊗_B N_{(B)}` where `N_{(B)} = N ⊗_A B`, by
associativity of tensor product and the universal property of localization.)

(1) If `M ⊗_A N` is exact in `N`, then composing with the exact functor `T⁻¹(−)` gives that `T⁻¹M ⊗_A N` is exact in
`N`.

(2) An equality of `B`-modules (or of `A`-modules underlying `B`-modules) holds iff it holds after localizing at every
maximal ideal of `B`. So a sequence `0 → P' → P → P'' → 0` of `A`-modules tensored with `M` is exact iff the
localizations at every maximal `𝔫` are exact, iff (by the displayed isomorphism)
`(P' ⊗_A M)_𝔫 → (P ⊗_A M)_𝔫 → (P'' ⊗_A M)_𝔫` is exact, iff (by part (1) applied to `M_𝔫` over `A`, equivalently over
`A_𝔪`) the original sequence tensored with `M_𝔫` over `A_𝔪` is exact — which holds by hypothesis. So `M ⊗_A −` is exact,
i.e. `M` is `A`-flat. ∎

This is the practical local criterion for flatness. To check flatness of a `B`-module over `A`, it suffices to check
flatness of each `B_𝔫`-module `M_𝔫` over the corresponding local ring `A_𝔪`. Combined with
[file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md)'s Tor characterization, this
reduces flatness of `M / A` to a local Tor computation.

### Proposition: flat over integral, flat over Dedekind

<!-- source: IV.1.3 -->

_This proposition says: over an integral ring, flat modules are torsion-free, and over a principal ideal domain (e.g. a
Dedekind ring like `ℤ` or the integers of a number field), torsion-free is the whole story._

**Proposition IV.1.3.** _Let `A` be a ring._

1. _Let `M` be a flat `A`-module. If `x ∈ A` is not a zero- divisor in `A`, then `x` is not a zero-divisor in `M`. In
    particular, if `A` is integral, `M` is torsion-free._
1. *Suppose `A` is integral and `A*𝔪`is a principal ideal domain for every maximal ideal`𝔪`(e.g.`A`Dedekind, or`A`itself
    a PID). Then an`A`-module `M` is flat if and only if it is torsion-free.*

**Proof.** (1) Multiplication by `x` on `A` is injective by hypothesis. Tensoring this injection with `M` gives an
injection `x · : A ⊗_A M = M → A ⊗_A M = M`, which is multiplication by `x` on `M`. Tensoring preserves injections
because `M` is flat.

(2) By IV.1.2 (ii), flatness over `A` may be checked at each maximal ideal of `A`, so we may assume `A` is a principal
ideal domain. We need to show that for every ideal `I`, the inclusion `I → A` tensored with `M` is injective. Since `A`
is a PID, `I = (x)` for some non-zero-divisor `x ∈ A`. The inclusion `I → A` becomes "multiplication by `x` from `A` to
`A`," and tensoring gives "multiplication by `x` from `M` to `M`," which is injective by torsion-freeness of `M`. ∎

The geometric reading: over `Spec ℤ`, a flat `ℤ`-module is the algebraic content of "no fiber suddenly drops rank as you
move to a different prime `p`." Torsion-free `ℤ`-modules are exactly those for which no prime annihilates a non-zero
element; over a PID, this single condition certifies flatness.

The arithmetic running examples will use this constantly. For `ℤ[t]` viewed as a `ℤ`-module, the underlying additive
group is free (as `ℤ`-module): a basis is `{t^n : n ≥ 0}`. Free implies flat. So `Spec ℤ[t] → Spec ℤ` is flat; the
flat-ness of this map is the substance of "the polynomial scheme over `ℤ` has no arithmetic jumps."

For `ℤ[t]/(pt) → ℤ` with `p ∈ ℤ` prime, the module `ℤ[t]/(pt)` viewed over `ℤ` is **not** torsion-free: the element `t`
is annihilated by `p`. So `ℤ[t]/(pt)` is not `ℤ`-flat, by IV.1.3 (i). Geometrically, the fiber of
`Spec ℤ[t]/(pt) → Spec ℤ` over `(p)` has an embedded component along `t = 0` that is not present at the generic point —
the family jumps algebraically.

## IV.2 Faithfully flat modules

<!-- source: IV.2 -->

### Setup: faithful, faithful exact

A functor `F : 𝓒 → 𝓓` is **faithful** if for every pair of objects `X, Y ∈ 𝓒`, the induced map

```text
Hom_𝓒(X, Y) → Hom_𝓓(F(X), F(Y))
```

is **injective**. For an additive functor between additive categories, faithfulness is equivalent to "`F(u) = 0` implies
`u = 0`," which in particular implies "`F(X) = 0` implies `X = 0`" (apply to `u = id_X`).

A functor `F` between abelian categories is **faithful and exact** iff for every sequence `M' → M → M''` of morphisms in
`𝓒`, the transformed sequence `F(M') → F(M) → F(M'')` is exact **if and only if** the original is exact. Equivalently,
`F` is exact and `F(X) = 0 ⟹ X = 0`.

A useful reformulation. Suppose `(M_i)` is a family of non-zero objects of `𝓒` such that every non-zero object of `𝓒`
has a subobject admitting a quotient isomorphic to some `M_i`. Then a functor `F` is faithful and exact iff `F` is exact
and `F(M_i) ≠ 0` for every `i`. For `𝓒 = A`-Mod, one may take the family `(A/𝔪)` indexed by the maximal ideals `𝔪` of
`A`: every non-zero `A`-module admits a non-zero monogenic submodule isomorphic to `A/I` for some proper ideal `I`, and
Krull's theorem gives a maximal ideal `𝔪 ⊃ I`, hence a quotient `A/𝔪`.

### Proposition: equivalent conditions for faithful flatness

<!-- source: IV.2.1 -->

_This proposition says: faithful flatness — flatness plus the property that the tensor functor reflects, not just
preserves, exactness — is equivalent to flatness plus any of three "detection" conditions. The condition most useful in
practice is "tensoring with `M` does not annihilate any non-zero module," or equivalently "`M ⊗ A/𝔪 ≠ 0` for every
maximal ideal `𝔪`."_

**Proposition IV.2.1.** _Let `M` be an `A`-module. The following are equivalent:_

1. _The functor `M ⊗_A −` is faithful and exact._
1. _`M` is flat, and `M ⊗_A N = 0` implies `N = 0`._
1. _`M` is flat, and `M ⊗_A A/𝔪 ≠ 0` for every maximal ideal `𝔪` of `A`._
1. _For every sequence of homomorphisms `N' → N → N''`, the sequence tensored with `M` is exact if and only if the
    original is exact._

**Proof.** The pattern is the same in each direction. (i) ⟺ (ii) by definition of "faithful" + "exact" applied to
`M ⊗_A −` (a functor between `A`-Mod and itself is faithful iff `F(N) = 0 ⟹ N = 0`, given exactness).

(ii) ⟹ (iii). The `A`-module `A/𝔪` is non-zero, so `M ⊗ A/𝔪 ≠ 0` is the (ii)-condition applied with `N = A/𝔪`.

(iii) ⟹ (ii). Suppose `M ⊗_A N = 0` for some `N ≠ 0`. Then `N` admits a non-zero monogenic submodule, hence a quotient
`A/𝔪` for some maximal `𝔪`. Tensoring the surjection `N → A/𝔪 → 0` with `M` (`M`-flat, so right-exact suffices), get
`M ⊗ N → M ⊗ A/𝔪 → 0`. The left side is zero, so `M ⊗ A/𝔪 = 0`, contradicting (iii).

(i) ⟺ (iv). This is just the categorical equivalent formulation of "`F` is faithful and exact" in an abelian category,
applied to `F = M ⊗_A −`. ∎

The conditions (ii), (iii) of IV.2.1 are usually called **conditions (i bis), (i ter)** in the SGA-IV-EGA tradition,
following Grothendieck's labeling. We use the modernized roman numerals.

We say `M` is a **faithfully flat** `A`-module when these conditions hold. The familiar consequence: tensoring with `M`
not only preserves but **reflects** monomorphisms, epimorphisms, and isomorphisms.

The same closure properties as in §IV.1 propagate: tensor product of faithfully flat modules is faithfully flat (use
(iii) and tensor of "non-zero on `A/𝔪`"); base change `M ⊗_A B` is faithfully flat over `B` if `M` is faithfully flat
over `A`; transitive composition along `A → B → C` lifts faithful flatness along the way.

### Corollary: local-to-local case

<!-- source: IV.2.2 -->

_This corollary says: in the most arithmetically common setting — a local map of local rings, with a finite-type module
— the distinction between flat and faithfully flat collapses, and is detected by whether the module is non-zero._

**Corollary IV.2.2.** _Let `A → B` be a local homomorphism of local rings, and let `M` be a finite-type `B`-module. Then
`M` is faithfully flat over `A` if and only if `M` is flat over `A` and `M ≠ 0`._

In particular, when `M = B` itself is a finite-type `B`-module of the trivial sort: **`B` is `A`-flat iff `B` is
`A`-faithfully flat**.

**Proof.** "Only if" is trivial: `M ⊗_A A/𝔪 ≠ 0` (with `𝔪` the maximal ideal of `A`) certainly forces `M ≠ 0`.

"If" uses condition (iii) of IV.2.1. We need `M ⊗_A A/𝔪 ≠ 0`. By Nakayama (appendix row `nakayama`) applied to the
finite-type `B`-module `M` and to the maximal ideal `𝔫` of `B`: since `M ≠ 0`, `M / 𝔫 M ≠ 0`. Now
`M ⊗_A A/𝔪 = M / 𝔪 M ⊃ M / 𝔫 M` (as quotients of `M`, using that `𝔪 B ⊂ 𝔫` because `A → B` is local). The quotient
`M / 𝔫 M ≠ 0`, so `M / 𝔪 M ≠ 0`, so `M ⊗_A A/𝔪 ≠ 0`. ∎

### Proposition: surjectivity on Spec

<!-- source: IV.2.3 -->

_This proposition says: faithful flatness of `B` over `A` implies that the map of spectra `Spec B → Spec A` is
surjective. Geometrically, faithful flatness is the algebraic content of "surjective covering"._

**Proposition IV.2.3.** _Let `A → B` be a ring homomorphism, and let `M` be a `B`-module faithfully flat over `A`. For
every prime ideal `𝔭` of `A`, there exists a prime ideal `𝔮` of `B` inducing it (i.e., `𝔮 ∩ A = 𝔭`)._

**Proof.** Fix `𝔭`. Reduce modulo `𝔭`: replace `(A, B, M)` by `(A/𝔭, B/𝔭B, M/𝔭M)`. Now `A` is integral, and we want a
prime of `B` inducing the zero prime of `A`.

Localize at the zero prime `(0)` of `A` (i.e., invert all non-zero elements): replace `(A, B, M)` by
`(K, B ⊗_A K, M ⊗_A K)` where `K = Frac(A)`. Now `A = K` is a field. The faithful flatness of `M` over `A` survives base
change. By the characterization (iii) of IV.2.1: `M ⊗_A A/𝔪 = M ⊗_K K/(0) = M ≠ 0` (faithful flatness, with `K` the only
field-on-itself field having maximal ideal `(0)`). So `M ≠ 0`, hence `B ≠ 0` (otherwise `M = M ⊗_B B = 0`), so `B` has a
prime ideal `𝔮`, which is forced by `A = K` to induce `(0)`. ∎

In algebra terms: `Spec(B) → Spec(A)` is **surjective**.

### Corollary: minimal primes lift

<!-- source: IV.2.4 -->

_This corollary says: under flatness plus a support hypothesis, not just any prime of the base lifts — the minimal
primes of the fiber over `𝔭` induce precisely `𝔭`._

**Corollary IV.2.4.** *Suppose `M` is `A`-flat, finite-type over `B`, and `Supp M = Spec(B)` (i.e., `M*𝔮 ≠ 0`for every
prime`𝔮 ∈ Spec B`). Then for every prime `𝔭`of`A`, the prime ideals `𝔮`of`B`containing`𝔭B`and minimal among such ideals
induce`𝔭`.*

**Proof.** Reduce to the case `𝔭 = 0`, which preserves all hypotheses. Then `A` is integral. The reduction is to the
following corollary, which we state and prove independently.

### Corollary: minimal primes induce minimal primes

<!-- source: IV.2.5 -->

_This corollary says: when `M` is flat, finite-type, with full support, every minimal prime of `B` lies over a minimal
prime of `A`. Geometrically: every irreducible component of `Spec(B)` dominates an irreducible component of `Spec(A)`._

**Corollary IV.2.5.** _With `M` as in IV.2.4, every minimal prime `𝔮` of `B` induces a prime `𝔭 = 𝔮 ∩ A` of `A` that is
minimal._

**Proof.** Localize at `𝔮` and `𝔭`. The hypotheses are preserved: `A → B` becomes a local map of local rings, `M = M_𝔮`
is non-zero (full-support hypothesis) and flat over `A_𝔭`, and `B = B_𝔮` has dimension zero (since `𝔮` was minimal). We
must show `A` has dimension zero, i.e. that `𝔭` was minimal.

By IV.2.2, `M_𝔮` is faithfully flat over `A_𝔭`. By IV.2.3, every prime of `A_𝔭` is induced by a prime of `B_𝔮`. The only
primes of `B_𝔮` are subsets of the maximal ideal (because `dim B_𝔮 = 0` means there is just one prime — the maximal
one); so the only prime of `A_𝔭` induced from `B_𝔮` is the maximal ideal of `A_𝔭`. So every prime of `A_𝔭` equals its
maximal ideal, i.e. `dim A_𝔭 = 0`. So `𝔭` was minimal. ∎

Geometrically: every irreducible component of `X = Spec B` dominates some irreducible component of `Y = Spec A`,
provided there exists a quasi-coherent sheaf of finite type on `X`, with support all of `X`, and flat over `Y`.

The remark at the end of the source: in IV.2.4, we did not need `M` faithfully flat over `A`. But without that
hypothesis, nothing guarantees a prime of `B` containing `𝔭 B` exists. Faithful flatness gives existence (IV.2.3);
IV.2.4 then gives the more refined conclusion that **minimal** primes containing `𝔭B` actually induce `𝔭`.

### Proposition: six equivalent conditions for `B` faithfully flat over `A`

<!-- source: IV.2.6 -->

_This proposition says: when `M = B` is a ring map (not just an abstract module), faithful flatness has six equivalent
forms. The most useful for descent are (ii) "flat plus surjective on Spec" and (iv) "injective with flat cokernel"; the
most useful for ideal-theoretic verification is (vi) "tensor product gives isomorphism `I ⊗_A B → IB` and the inverse
image of `IB` is `I`"._

**Proposition IV.2.6.** _Let `i : A → B` be a ring homomorphism. The following are equivalent:_

1. _`B` is a faithfully flat `A`-module._
1. _`B` is `A`-flat and `Spec(B) → Spec(A)` is surjective._
1. _`B` is `A`-flat and every maximal ideal of `A` is induced by an ideal of `B`._
1. _`i` is injective and `Coker i` is a flat `A`-module._
1. _The functor `M ↦ M_{(B)} = M ⊗*A B`on`A`-modules is exact, and the canonical map `M → M_{(B)}`is injective for
    every`M`._
1. _For every ideal `I` of `A`, the canonical map `I ⊗_A B → IB` is an isomorphism, and the inverse image of `IB` in `A`
    equals `I`._

**Proof.** (i) ⟹ (ii) is IV.2.3. (ii) ⟹ (iii) is trivial: maximal ideals are special cases of primes.

(iii) ⟹ (i). By the criterion (iii) of IV.2.1, we need `B ⊗_A A/𝔪 ≠ 0` for every maximal `𝔪` of `A`. By hypothesis there
is an ideal `J` of `B` with `J ∩ A = 𝔪`. Pick a maximal ideal `𝔫 ⊃ J`; then `𝔫 ∩ A ⊃ 𝔪` is a proper ideal of `A`, so
`𝔫 ∩ A = 𝔪`. So `𝔪 B ⊂ 𝔫`, hence `B / 𝔪 B ≠ 0` (it surjects onto `B/𝔫 ≠ 0`). So `B ⊗_A A/𝔪 = B/𝔪B ≠ 0`.

(iii) ⟹ (iv). Apply IV.1.1 (the "as good as split" lemma) to

```text
0 → A → B → Coker i → 0
```

(once we know `i` is injective). Injectivity of `i`: suppose `a ∈ A` with `i(a) = 0`. Tensor `0 → (a) → A` with `B`: the
left becomes `(a) ⊗_A B`, the right becomes `B`, and the map sends `a ⊗ 1` to `i(a) = 0`. By IV.2.1 (i) (which is "(i) ⟺
(ii)" plus exactness of `B ⊗_A −`, which holds by `B` flat), the map `(a) ⊗_A B → B` is injective; so `a ⊗ 1 = 0` in
`(a) ⊗_A B`. Since `(a) ≅ A / Ann(a)` is a quotient of `A`, the tensor `(a) ⊗_A B = B / Ann(a) B`. Vanishing of `a ⊗ 1`
means `1 ∈ Ann(a) B`, equivalently `Ann(a) B = B`, so `Ann(a) ⊃ A` (no proper ideal of `A` extends to `B` in this case
by (iii)), so `a · 1 = 0`, so `a = 0`. Now `i` is injective, and IV.1.1 (ii) applied to the sequence with flat quotient
`B`: `A` is flat (always); so `Coker i` flat ⟺ `B` flat. By hypothesis `B` is flat, so `Coker i` is flat.

(iv) ⟹ (v). Take the second part of (v): for any `M`, apply `− ⊗_A M` to `0 → A → B → Coker i → 0`. By IV.1.1 (i) (Coker
i flat): the sequence stays exact, so `0 → M → M ⊗_A B → M ⊗_A (Coker i) → 0` is exact. So `M → M ⊗_A B` is injective.
For the first part: `B` is flat (it embeds in a flat extension with flat cokernel; equivalently, IV.1.1 (ii) on the same
sequence with `M' = A` flat).

(v) ⟹ (i). Exactness of `M ⊗_A B` says `B` is flat. The injectivity of `M → M ⊗_A B` for every `M`: suppose
`B ⊗_A N = 0` for some `N ≠ 0`. Then in particular the map `N → N ⊗_A B = 0` is the zero map; injectivity forces
`N = 0`, contradiction. So `B ⊗_A N = 0 ⟹ N = 0`, the condition (ii) of IV.2.1.

(iv) ⟹ (vi). For any ideal `I` of `A`, apply `− ⊗_A B` to `0 → I → A → A/I → 0`: by `Coker i` flat plus `B` flat
(equivalent in this setting), `0 → I ⊗_A B → A ⊗_A B → (A/I) ⊗_A B → 0` is exact, and the arrows identify with
`I ⊗_A B → B → B/IB → 0`. So `I ⊗_A B → IB` is an isomorphism. For the second part of (vi): take `M = A/I` in (v). The
injection `A/I → A/I ⊗_A B = B/IB` forces `i⁻¹(IB) = I`.

(vi) ⟹ (i). The first part of (vi) is the flatness criterion "`I ⊗_A B → IB` iso for all `I`" we developed at the start
of §IV.1. The second part `i⁻¹(IB) = I` for every ideal `I` implies in particular `i⁻¹(𝔪 B) = 𝔪` for every maximal ideal
`𝔪`, which contains `𝔪 B ≠ B`, so `B / 𝔪 B ≠ 0`, which is (iii) of IV.2.1.

The cycle is complete. ∎

The pieces of IV.2.6 are individually used everywhere in descent theory.

> **Concrete special case.** For `A → B = Â` the `𝔪`-adic completion of a noetherian local ring (file 25, IV.3.2): the
> map is faithfully flat. By IV.2.6 (iv): the natural map `A → Â` is injective and `Â / A` is `A`-flat. By IV.2.6 (vi):
> `I Â ∩ A = I` for every ideal `I` of `A` — the **Krull intersection** style fact that completion preserves ideal
> structure. These two facts together are why the gentle SGA has been treating `completion-flat` as a universally
> available black box since file 04.

### Closing remark

The five-page workout above is the substance of "flat = exactness of `M ⊗_A −` and faithfully flat = exactness plus
reflection of exactness." Everything else in Exposé IV is downstream:

- **§3** (file 25) applies IV.2 to completion: `Â` is flat over `A` (IV.3.1), and faithfully flat exactly when `I` is in
    the radical (IV.3.2). The proof is one line each, using IV.2.1.
- **§4** (file 25) uses IV.1.1 to lift bases through `gr` and Nakayama (IV.4.1), giving the "free iff `Tor₁ = 0`"
    criterion.
- **§5** (file 26) uses IV.5.2 (Serre's lemma, via the spectral sequence of file 23) to globalize the Tor criterion
    across a base change `A → B`, culminating in the local flatness criterion IV.5.6.
- **§6** (file 27) uses IV.2.2 + IV.2.3 in the proof of IV.6.6 (open-image theorem for flat morphisms), and uses Noether
    normalization (file 23) in the proof of IV.6.7 (generic freeness).

Read on into [file 25](25-expose-iv-3-4-completion-and-free-modules-gentle.md) for the completion and free-module
corollaries; into [file 26](26-expose-iv-5-local-flatness-criterion-gentle.md) for the local flatness criterion; and
into [file 27](27-expose-iv-6-constructibility-openness-and-generic-flatness-gentle.md) for the geometric payoff and the
closing of the project.
