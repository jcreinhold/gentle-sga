# Exposé IV, section 5: the local flatness criterion (gentle)

## What this file is about

The well-behaved-family condition introduced two files back is hard to check directly. The definition asks for
compatibility with every possible auxiliary piece of data, and the test is not local in any obvious sense. In
practice one wants to know whether a family is well behaved by inspecting it only at a single fixed locus.

This file gives the theorem that makes the inspection legitimate. Under mild hypotheses, a family is well behaved
over its full base if and only if its restriction to the first infinitesimal layer at the locus is well behaved
there and a single auxiliary obstruction vanishes. Every earlier file in the seminar that argued well-behavedness by
checking the special fibre was implicitly using this theorem. It is the engine of the local theory of smooth and
étale maps and underlies almost every later flatness argument.

§4 (file 25) gave the flatness ⟺ freeness story over local rings under the standard hypotheses (`I` nilpotent, or `A`
noetherian with `I` in the radical and `M` finite). The criterion was "`M ⊗ A/I` free plus `Tor^A₁(M, A/I) = 0`," and
the proof was a single Nakayama lift.

§5 globalizes this from the residue level to the entire `I`-adic filtration. The substantive question: given a
finite-type `B`-module `M` and a homomorphism `A → B` with `IB` in the radical of `B`, what does it take to verify that
`M` is **`A`-flat** (not just free over `A/I`)? The answer is a four-part equivalence (IV.5.6, the **local flatness
criterion**) that says: it suffices to check flatness of the **first thickening** `M ⊗_A A/I`, and the absence of any
Tor obstruction along the way.

The criterion is the workhorse of EGA's smoothness, étaleness, and lifting verifications. Every time the étale theory
(file 11) or the smooth theory (files 14–15) said "and now we check flatness on the special fiber, then conclude
flatness over the base," it was IV.5.6 doing the work — implicitly, until now.

The slogan:

> **IV.5.6 (local flatness criterion).** Let `A → B` be a map of noetherian rings, `I ⊂ A` an ideal with `IB` in the
> radical of `B`, `M` a finite-type `B`-module. Then:
>
> _M is `A`-flat ⟺ `M ⊗_A A/I` is `A/I`-flat and `Tor^A₁(M, A/I) = 0` ⟺ (gr form) `M ⊗_A A/I` is `A/I`-flat and the
> canonical `gr` map is an iso ⟺ (filtration form) `M ⊗_A A/I^n` is `A/I^n`-flat for every `n`._
>
> When `A/I` is a field (the most common case), the `M ⊗_A A/I` flat hypothesis is automatic, and the criterion reduces
> to "Tor-vanishing on the residue field."

Throughout this file we use the Tor language of
[file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md) and the IV.4.2 `gr` criterion of
[file 25](25-expose-iv-3-4-completion-and-free-modules-gentle.md). The single non-routine input is the **spectral
sequence for composite functors** (file 23, §2), which IV.5.2 invokes once.

## IV.5 Local flatness criteria

<!-- source: IV.5 -->

### Proposition: Tor vanishing along `I^n` and the `gr` isomorphism

<!-- source: IV.5.1 -->

_This proposition says: Tor-vanishing along the entire `I`-adic filtration implies the `gr` isomorphism. Conversely,
when `I` is nilpotent, the `gr` isomorphism implies Tor-vanishing along the filtration. So in the nilpotent case the two
are equivalent._

**Proposition IV.5.1.** _Let `A` be a ring, `I ⊂ A` an ideal, `M` an `A`-module. If_

```text
Tor^A₁(M, A/I^n) = 0  for every n ≥ 1,
```

_then the canonical surjective map_

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

_is an isomorphism. Conversely, if the `gr` isomorphism holds and `I` is nilpotent, then `Tor^A₁(M, A/I^n) = 0` for
every `n ≥ 1`._

**Proof.** **Forward direction.** The Tor-vanishing along `A/I^n` for all `n` says (by the same argument as in §IV.1,
applied to the inclusion `I^n ⊂ A`) that the natural maps

```text
I^n ⊗_A M → I^n M
```

are isomorphisms for every `n ≥ 0`. Quotienting (`I^n / I^{n+1}`): the maps

```text
(I^n / I^{n+1}) ⊗_A M → I^n M / I^{n+1} M
```

are isomorphisms for every `n`. Summing over `n` and identifying
`(I^n / I^{n+1}) ⊗_A M = (I^n / I^{n+1}) ⊗_{A/I} (M / IM)` (using that `I` acts as zero on `I^n / I^{n+1}` from one
side): the canonical map of the displayed equation is an isomorphism in each graded degree, hence an iso of graded
`A/I`-modules.

**Converse (when `I` is nilpotent).** Use descending induction on `n`: pick `n₀` with `I^{n₀} = 0`; for `n ≥ n₀ - 1`,
the ideal `I^n = 0`, so the `Tor^A₁(M, A/I^n) = Tor^A₁(M, A) = 0` trivially.

For the inductive step, suppose `Tor^A₁(M, A/I^{n+1}) = 0`. Use the diagram

```text
       M ⊗ I^{n+1}  →  M ⊗ I^n  →  M ⊗ (I^n / I^{n+1})  →  0
              ↓              ↓                 ↓
0  →       I^{n+1}M  →      I^nM  →     I^nM / I^{n+1}M    → 0
```

with exact rows (the bottom is exact by the iso in the right column at the next step; the top is right-exact, with the
left piece of the row coming from the long exact sequence in Tor).

By the gr-isomorphism hypothesis the right vertical arrow is an isomorphism (this is exactly the assertion). By the
inductive hypothesis on `n + 1`, the left vertical arrow is an isomorphism: from `Tor^A₁(M, A/I^{n+1}) = 0` we conclude
`I^{n+1} ⊗_A M → I^{n+1} M` is an iso. Five lemma: the middle arrow `M ⊗ I^n → I^n M` is an iso. So
`Tor^A₁(M, A/I^n) = 0`, completing the induction. ∎

The first half is a clean unwinding of "Tor vanishing on every quotient `A/I^n` controls the graded structure." The
second half is the converse-via-descending-induction that fails when `I` is not nilpotent — the descending induction has
no base case because `I^n` does not eventually vanish.

> **Concrete special case.** For `A = k[t]_{(t)}` and `I = (t)`, the inclusion `I = (t) → A` is multiplication by `t`.
> The Tor-vanishing `Tor^A₁(M, A/I) = 0` says "multiplication by `t` on `M` is injective," i.e. `M` is `t`-torsion-free.
> Iterating: `Tor^A₁(M, A/I^n) = 0` for every `n` says `M` is torsion-free for every `t^n`. The `gr` isomorphism then
> identifies `gr(M) ≅ M/tM ⊗ k[T]`, which is the algebraic version of "the Taylor expansion of `M` at the origin is
> structureless from the data of `M / tM` plus the polynomial ring `k[T]` of derivatives."

### Proposition: Serre's lemma (composite functors)

<!-- source: IV.5.2 -->

_This proposition says: tensoring is local in a strong sense for flatness purposes. Vanishing of `Tor^A₁(M, N)` for
**all** `B`-modules `N` (where `B` sits between `A` and the situation) is equivalent to two pieces: vanishing of
`Tor^A₁(M, B)` itself, plus `B`-flatness of the base-change `M ⊗_A B`. This is the algebraic input that lets the next
two corollaries reduce flatness verifications across `A → B`._

**Proposition IV.5.2** (Serre)**.** _Let `A → B` be a homomorphism of rings, and let `M` be an `A`-module. The following
are equivalent:_

1. _For every `B`-module `N`, `Tor^A₁(M, N) = 0`._
1. _`Tor^A₁(M, B) = 0`, and `M ⊗_A B` is `B`-flat._

**Proof.** Apply the spectral sequence for composite functors (file 23, §2) with `F = − ⊗_A B : A`-Mod `→ B`-Mod and
`G = − ⊗_B N : B`-Mod `→ Ab`. The composition is `G ∘ F = − ⊗_A N`. The spectral sequence has the form

```text
E²_{p, q} = Tor^B_p(Tor^A_q(M, B), N) ⇒ Tor^A_{p + q}(M, N).
```

The five-term exact sequence in low degrees (file 23) reads

```text
Tor^B₁(M ⊗_A B, N) ← Tor^A₁(M, N) ← Tor^A₁(M, B) ⊗_A N.
```

(Right-to-left direction; the spectral sequence is a left-derived homological sequence.)

**(i) ⟹ (ii).** Suppose `Tor^A₁(M, N) = 0` for every `N`. From the displayed sequence, both surrounding terms are zero
(the left because `Tor^A₁(M, B) = 0`, applying (i) with `N = B`; the right because `Tor^A₁(M, N) = 0` is the central
term). So `Tor^B₁(M ⊗_A B, N) = 0` for every `B`-module `N`. By the Tor characterization (file 23), `M ⊗_A B` is
`B`-flat.

**(ii) ⟹ (i).** Suppose `Tor^A₁(M, B) = 0` and `M ⊗_A B` is `B`-flat. From the displayed sequence: the right term
`Tor^A₁(M, B) ⊗_A N = 0` (by hypothesis); the left term `Tor^B₁(M ⊗_A B, N) = 0` (by `B`-flatness of `M ⊗_A B`). So the
central term `Tor^A₁(M, N) = 0`. ∎

This is the lemma Serre isolated to simplify the proof of IV.5.6. The key insight: instead of verifying Tor-vanishing of
`M` on every `A`-module `N` (a possibly large family), one verifies Tor-vanishing of `M` on the single `A`-module `B`,
plus `B`-flatness of the (often smaller) base-change `M ⊗_A B`.

### Corollary: extending to `N` annihilated by a power of `I`

<!-- source: IV.5.3 -->

_This corollary says: when `B = A/I` (the special case most relevant to applications), the Tor-vanishing of IV.5.2 (i)
extends from `B` itself to every `A`-module annihilated by a power of `I` — even though the IV.5.2 statement is *for
every `B`-module*._

**Corollary IV.5.3.** _Suppose `B = A/I` in IV.5.2. The equivalent conditions of IV.5.2 are then also equivalent to:_

1. _`Tor^A₁(M, N) = 0` for every `A`-module `N` annihilated by some power of `I`._

**Proof.** (i) of IV.5.3 says: `Tor^A₁(M, N) = 0` for every `A/I^k`-module `N` (for all `k ≥ 1`).

That implies (i) of IV.5.2: take `k = 1`, then `N` is an `A/I = B`-module.

For the converse, use the filtration `N ⊃ IN ⊃ I²N ⊃ … ⊃ I^k N = 0` of `N` (the `k`-th piece is zero by hypothesis). The
quotients `I^j N / I^{j+1} N` are annihilated by `I`, so are `A/I = B`-modules. By IV.5.2 (i),
`Tor^A₁(M, I^j N / I^{j+1} N) = 0`. Inductively (using the long exact Tor sequence on each
`0 → I^{j+1} N → I^j N → I^j N / I^{j+1} N → 0`), one propagates the vanishing up to `Tor^A₁(M, N) = 0`. ∎

This corollary is the form that connects IV.5.2 (a tensor- algebraic statement about all `B`-modules) to the `I`-adic
content of §IV.4 (a graded statement about the filtration).

### Corollary: the `gr` criterion holds and `M ⊗ A/I` is flat

<!-- source: IV.5.4 -->

_This corollary says: when the IV.5.2 / IV.5.3 conditions hold (with `B = A/I`), one automatically has the IV.4.2 `gr`
isomorphism for the `I`-adic filtration of `M`, plus flatness of the residue `M ⊗_A A/I` over `A/I`. This is the bridge
from "Tor-vanishing along the filtration" to "the `gr` form of the criterion."_

**Corollary IV.5.4.** _Under the conditions of IV.5.3, the canonical functorial map_

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

_is an isomorphism, and `M ⊗_A A/I` is `A/I`-flat._

**Proof.** The Tor-vanishing of (i) of IV.5.3 gives in particular `Tor^A₁(M, A/I^n) = 0` for every `n ≥ 1`. By IV.5.1
(forward direction), the `gr` map is an iso.

For `A/I`-flatness of `M ⊗_A A/I`: this is just the second half of (ii) of IV.5.2 transcribed (`M ⊗_A B = M ⊗_A A/I` is
`B = A/I`-flat). ∎

So the equivalent (i)–(ii) of IV.5.2 and (i) of IV.5.3 propagate to **two extra conditions** that look identical to
those of IV.4.2 / IV.4.3.

### Corollary: the nilpotent-`I` form

<!-- source: IV.5.5 -->

_This corollary says: when `I` is nilpotent, the equivalences collapse to a clean three-condition equivalence — flatness
over `A`, flatness over `A/I` plus Tor-vanishing, and flatness over `A/I` plus the `gr` iso. The nilpotent-`I` form is
the regime in which the entire criterion is symmetric._

**Corollary IV.5.5.** _Let `A` be a ring with a nilpotent ideal `I`, and let `M` be an `A`-module. The following are
equivalent:_

1. _`M` is `A`-flat._
1. _`M ⊗_A A/I` is `A/I`-flat, and `Tor^A₁(M, A/I) = 0`._
1. *`M ⊗_A A/I` is `A/I`-flat, and the canonical map `gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)` is an iso.*

**Proof.** **(i) ⟹ (ii).** `M` flat ⟹ `Tor^A₁(M, −) = 0` ⟹ in particular `Tor^A₁(M, A/I) = 0`. Also `M ⊗_A A/I` is
`(A/I)`-flat by base change (file 24, IV.1's closure properties).

**(ii) ⟹ (i).** Suppose (ii). We want `M` to be `A`-flat. By the criterion of IV.5.2 with `B = A/I`: it suffices to have
`Tor^A₁(M, A/I) = 0` (one half of (ii)) and `M ⊗_A A/I` is `A/I`-flat (the other half). Combined with IV.5.3, we get
`Tor^A₁(M, N) = 0` for every `N` annihilated by a power of `I`. **Since `I` is nilpotent**, every `A`-module is
annihilated by a power of `I` (specifically, by the power `I^{n₀}` with `I^{n₀} = 0`). So `Tor^A₁(M, N) = 0` for every
`A`-module `N`. By the Tor characterization, `M` is flat.

**(ii) ⟺ (iii).** This is IV.5.1 (both directions, since `I` is nilpotent), applied to the `M ⊗_A A/I`-flat hypothesis.
The `Tor^A₁(M, A/I) = 0` half of (ii) and the `gr` iso of (iii) are equivalent given the second clause `M ⊗_A A/I` flat
(which makes the `Tor` and `gr` reductions of §IV.4 valid). ∎

The nilpotent-`I` form (IV.5.5) is the "if and only if" of the local flatness criterion in the artinian / infinitesimal
regime — exactly the regime that recurs throughout §III.5–§III.6 (file 21). When the gentle reader encountered the H¹
obstruction story of file 21, the underlying flatness lifts were governed by IV.5.5 implicitly.

### Theorem: the local flatness criterion (IV.5.6)

<!-- source: IV.5.6 -->

_This theorem says: the equivalences of IV.5.5 extend to the non-nilpotent case under a finiteness / radical hypothesis.
For `A → B` of noetherian rings, `IB` in the radical of `B`, and `M` a finite-type `B`-module, the same four conditions
are equivalent (plus a fourth: flatness of every thickening `M ⊗_A A/I^n`)._

**Theorem IV.5.6.** _Let `A → B` be a homomorphism of noetherian rings, let `I` be an ideal of `A` such that `IB` is
contained in the radical of `B`, and let `M` be a `B`-module of finite type. Then the following are equivalent:_

1. _`M` is `A`-flat._
1. _`M ⊗_A A/I` is `A/I`-flat and `Tor^A₁(M, A/I) = 0`._
1. *`M ⊗_A A/I` is `A/I`-flat and the canonical map `gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)` is an iso.*
1. _For every integer `n`, `M ⊗_A A/I^n` is flat over `A/I^n`._

**Proof outline.** **(i) ⟹ (ii)** is base change. **(ii) ⟺ (iii)** is IV.5.1 (the converse direction needs Krull's
intersection theorem in lieu of the nilpotency previously assumed; this is where the hypotheses noetherian + `IB` in
radical + `M` finite enter, ensuring that intersections `∩_n I^n M ⊂ (separated topology)` vanish). **(ii) ⟹ (iv)**:
apply IV.5.5 to the system `(A, A/I^n, I/I^n, M ⊗_A A/I^n)` to get flatness of `M ⊗_A A/I^n` over `A/I^n` from
(ii)-style data on the smaller filtration. **(iv) ⟹ (i)**: this is the substantive direction; it is where the noetherian
\+ finite + radical-`IB` hypothesis is essential, in the form of the "`M ⊗_A N` is `I`-adically separated for `N` of
finite type" condition the source isolates. The argument from there (lines 408–432 of the source) is a careful diagram
chase that identifies the kernel of `M ⊗_A N' → M ⊗_A N` for an arbitrary inclusion `N' → N` of finite-type `A`-modules
with the intersection of the `I^n M ⊗_A N'`, then uses Krull-separation to make that intersection vanish.

The full proof is in lines 295–432 of the source. We do not reproduce the diagram chase (its essence is a careful
application of Krull plus the (iv)-style flatness hypothesis at each thickening); the reader who wants the line-by-line
should consult Bourbaki AC III §5.4 or the source's own argument. ∎

The hypothesis "`IB` is in the radical of `B`" is automatic in the most arithmetic-relevant case where `B` is local and
`I` is contained in the maximal ideal of `A` (then `IB` is in the maximal ideal of `B`). The finite-type-`M`-over-`B`
hypothesis then becomes "finite-type `B`-module" with `B` local noetherian.

> **The case `A/I` a field.** This is the deformation-theoretic regime: `(A, 𝔪)` local noetherian, `I = 𝔪`, `A/𝔪 = k`
> the residue field. The condition "`M ⊗_A A/I` is `A/I`-flat" becomes "`M ⊗_A k` is `k`-flat," automatic for any
> `k`-vector space. The criterion collapses to:
>
> _For `(A, 𝔪)` noetherian local, `B` noetherian local with `𝔪 B ⊂ 𝔫_B`, and `M` finite over `B`: `M` is `A`-flat ⟺
> `Tor^A₁(M, k) = 0` ⟺ the `gr` map is an iso ⟺ each `M ⊗_A A/𝔪^n` is `A/𝔪^n`-free._
>
> The "`M ⊗_A A/𝔪^n` is `A/𝔪^n`-free" form is the one most often invoked in deformation theory: to verify flatness of a
> deformation, lift the special-fiber structure to each infinitesimal thickening freely. This is the form used in file
> 19 / file 21 implicitly.

The theorem IV.5.6 is the centerpiece of the exposé. The remaining propositions IV.5.7–IV.5.9 are corollaries.

### Corollary: relative criterion for `u : M' → M`

<!-- source: IV.5.7 -->

_This corollary says: a homomorphism of finite-type `B`-modules that is `A`-flat-on-the-target is `A`-flat-injective
(with flat cokernel) iff its tensor product with the residue field is injective. This is the form used in deformation
theory: to lift a homomorphism along a thickening with flatness preserved, it suffices to check injectivity at the
residue field._

**Corollary IV.5.7.** _Let `A → B` be a local homomorphism of noetherian local rings, and let `u : M' → M` be a
homomorphism of finite-type `B`-modules. Suppose `M` is flat over `A`. Let `k` be the residue field of `A`. The
following are equivalent:_

1. _`u` is injective and `Coker\ u` is flat over `A`._
1. _`u ⊗_A k : M' ⊗_A k → M ⊗_A k` is injective._

**Proof.** **(i) ⟹ (ii).** `u` injective ⟹ the short exact sequence `0 → M' → M → Coker\ u → 0` exists. By IV.1.1 (file
24\) with flat right term (the cokernel), the sequence remains exact after tensoring with `k`. So `u ⊗_A k` is injective.

**(ii) ⟹ (i).** First, we show `u` is injective. Pass to associated graded modules along the `𝔪_A`-filtration: the
condition `u ⊗_A k = u ⊗_A A/𝔪_A` injective gives `gr_{𝔪_A}⁰(u)` injective. By the `gr` iso (IV.5.6 (iii) for `M`, which
is `A`-flat by hypothesis), `gr_{𝔪_A}(u) : gr(M') → gr(M)` is determined in each degree by `gr⁰`, which is injective. So
`gr(u)` is injective in every degree. The kernel of `u` then lives in the intersection of the `𝔪_A^n M'` (no graded
contribution survives), which by Krull is zero. So `u` is injective.

Second, we show `Coker\ u` is `A`-flat. The short exact sequence `0 → M' → M → Coker\ u → 0` and the long exact Tor
sequence give

```text
Tor^A₁(M, k) → Tor^A₁(Coker\ u, k) → M' ⊗_A k → M ⊗_A k.
```

By `M`-flat, the leftmost term is zero. By hypothesis (ii), the rightmost arrow is injective, so the connecting term
`Tor^A₁(Coker\ u, k) = 0`. By IV.5.6 applied to `Coker\ u` (a finite-type `B`-module), `Coker\ u` is `A`-flat. ∎

This is the criterion that supplied "lift `u` to a thickened deformation injectively with flatness preserved" in file
21's H¹ obstruction calculations. The gentle reader can now see that the underlying lift was governed by IV.5.7 as a
black box.

### Corollary: completion-invariance of flatness

<!-- source: IV.5.8 -->

_This corollary says: under the IV.5.6 hypotheses, flatness of `M` over `A` is equivalent to flatness of `M` over the
`I`-adic completion `Â`. Completing the base does not change flatness — the algebraic microscope of completion preserves
flat / non-flat distinctions._

**Corollary IV.5.8.** _Under the hypotheses of IV.5.6, let `J` be an ideal of `B` containing `IB` and contained in the
radical of `B`. Let `Â`, `B̂`, `M̂` be the `J`-adic completions of `A`, `B`, `M` respectively (with `Â` the `I`-adic
completion). Then `M` is `A`-flat ⟺ `M` is `Â`-flat._

**Proof.** The forward direction (`M` flat over `A` ⟹ flat over `Â`) is immediate by base change along `A → Â` (and
`Â`-flat for `M̂`-style modules follows because completion preserves flatness for finite-type modules over noetherian
rings).

The reverse direction uses the `gr`-form criterion (iii) of IV.5.6 and IV.3.2 (file 25). The `gr` of the situation
`(A, B, I, M)` is identified with the `gr` of the situation `(Â, B̂, IÂ, M̂)` because completion preserves graded
structure along ideals contained in the radical. So the (iii) condition of IV.5.6 for `M / A` is equivalent to the (iii)
condition for `M̂ / Â`. By IV.3.2 (faithful flatness of `Â / A` under the radical hypothesis) plus base change, both
conditions translate across. So flatness of `M` over `A` is equivalent to flatness of `M̂` over `Â`. The remaining
identification "flat over `Â` for `M` versus for `M̂`" uses the appendix row `completion-test-for-flatness`. ∎

This corollary is the proof of the appendix row `completion-test-for-flatness`, which has been treated as a black box
since file 04. The black box is now opened.

### Corollary: three-tier criterion `A → B → C`

<!-- source: IV.5.9 -->

_This corollary says: when there are three rings stacked `A → B → C` with `B` flat over `A`, flatness of a `C`-module
`M` over `B` decomposes into two independent pieces: flatness of `M` over `A`, and flatness of the residue `M ⊗_A k`
over `B ⊗_A k`. This is the criterion for "checking flatness over the middle ring after a base change."_

**Corollary IV.5.9.** _Let `A → B → C` be local homomorphisms of noetherian local rings, `M` a finite-type `C`-module,
and suppose `B` is flat over `A`. Let `k` be the residue field of `A`. The following are equivalent:_

1. _`M` is `B`-flat._
1. _`M` is `A`-flat, and `M ⊗_A k` is flat over `B ⊗_A k`._

**Proof.** **(i) ⟹ (ii).** `M` flat over `B` and `B` flat over `A` ⟹ `M` flat over `A` by transitive composition. For
the second part: tensoring with `k` over `A` is the base change `A → k`, and `M ⊗_A k` becomes `M ⊗_B (B ⊗_A k)`
(associativity), which is flat over `B ⊗_A k` by `M` flat over `B` and base change.

**(ii) ⟹ (i).** Apply IV.5.6 (iii) to `(B, C, 𝔪_B = I, M)` where `𝔪_B` is the maximal ideal of `B`. The condition for
flatness of `M / B` is: `M ⊗_B (B / 𝔪_B) = M ⊗_B (B ⊗_A k) = M ⊗_A k` is flat over `B / 𝔪_B = B ⊗_A k`, AND the second
condition of IV.5.6 (iii) holds for the `gr_{𝔪_B}` of `M`. The first half of this is given by hypothesis (ii). The
second half holds because `M` is `A`-flat (hypothesis (ii)) and `B` is `A`-flat, by an associativity argument for tensor
products (`M ⊗_B B / 𝔪_B^n = M ⊗_A (B / 𝔪_B^n)` etc., where flatness of `M / A` and of `B / A` together secure each
thickening's flatness via the same `gr` route). ∎

The remark from the source: when `𝔪_A` is nilpotent (instead of maximal but not nilpotent), the same statement holds via
IV.5.5 in place of IV.5.6. Conceptually: the "field at the bottom keeping things rigid" can be replaced by an artinian
local ring, and the criterion still works.

> **Note on the maximal-ideal-vs-nilpotent dichotomy.** The source comments parenthetically that maximality of `𝔪` "did
> not enter" the proof — the criterion works for any `I` either nilpotent or in the radical with finite-type `M` over
> noetherian `B`. The maximal case is "the best possible" in the sense that `A/𝔪` is a field, making flatness over `A/𝔪`
> automatic, and so the criterion collapses to the single condition `Tor^A₁(M, k) = 0`. This is the form most often
> invoked.

## Worked example: the elliptic curve over `ℤ_p`

Continuing the running example from file 24 (and from files 14, 15, 21 going back). Take

```text
A = ℤ_{(p)},   I = (p),   k = A/I = 𝔽_p
```

and let `B = ℤ_{(p)}[x, y] / (y² − x³ − ax − b)` for a Weierstrass equation with `a, b ∈ ℤ_{(p)}` and discriminant
`Δ = 4a³ + 27b² ≠ 0` in `ℤ_{(p)}` (we'll discuss the case `p ∤ Δ` first). The morphism `Spec B → Spec A` is the elliptic
curve `ℰ` over `Spec ℤ_{(p)}`.

**Goal: verify flatness of `B` over `A` using IV.5.6.** Take `M = B` (a finite-type `B`-module, trivially). Hypothesis
check: `A, B` noetherian; `I = (p)`, `IB = (p) B`. Is `IB` in the radical of `B`? We need `(p)` to lie in the Jacobson
radical of `B`. For `B` semilocal (it is — its maximal ideals are the closed points of the special fiber `ℰ_p`, all
containing `p`), the Jacobson radical contains `p`, so yes.

**Apply IV.5.6 (ii).** We need:

1. `M ⊗_A A/I = B ⊗_{ℤ_{(p)}} 𝔽_p = 𝔽_p[x, y] / (y² − x³ − ax − b)` is `𝔽_p`-flat. As a vector space over a field, this
    is automatic.
1. `Tor^A₁(M, A/I) = Tor^{ℤ_{(p)}}₁(B, 𝔽_p) = 0`.

For the second point: take a free resolution of `𝔽_p` over `ℤ_{(p)}`:

```text
0 → ℤ_{(p)} → ℤ_{(p)} → 𝔽_p → 0.
```

This is a free resolution of length 1. Tensoring with `B`:

```text
0 → B → B → B/pB → 0.
```

The kernel of `B → B` is the `p`-torsion of `B`. So `Tor^{ℤ_{(p)}}₁(B, 𝔽_p) = B[p]` (the `p`-torsion). For
`B = ℤ_{(p)}[x, y] / (y² − x³ − ax − b)` integral, the `p`-torsion is zero (`ℤ_{(p)}` is integral and torsion-free, and
`B` is a quotient of `ℤ_{(p)}[x, y]` by a polynomial that is irreducible over `Frac(ℤ_{(p)})[x, y]` for generic
`(a, b)`, hence integral). So `Tor^{ℤ_{(p)}}₁(B, 𝔽_p) = 0`.

By IV.5.6, `B` is `ℤ_{(p)}`-flat. The morphism `ℰ → Spec ℤ_{(p)}` is flat. ∎

When `p | Δ`, the special fiber `ℰ_p` is singular (a node or a cusp), but `B` is still `ℤ_{(p)}`-flat — the same Tor
calculation goes through. The lesson: **flatness ≠ smoothness**. The elliptic curve is flat over `ℤ_{(p)}` for every
prime `p`, but smooth only over `Spec ℤ_{(p)}[1/Δ]`. The flat locus contains the smooth locus and, in fact, equals all
of `ℰ`; the smooth locus is the strict subset `ℰ \ V(Δ)`.

In file 27 we will revisit this example to verify the open-image theorem (IV.6.6) and the openness of the flat locus
(IV.6.10) on `ℰ`. The flat locus is `ℰ` itself, the maximal possible; generic flatness (IV.6.11) is automatic.

## Worked example: a non-flat foil

Take `A = ℤ_{(p)}`, `B = A[t]/(p t)`. Verify `B` is not flat over `A` using the failure of IV.5.6 (ii). Take `M = B`.

`Tor^A₁(B, 𝔽_p)` is computed as before: the `p`-torsion in `B`. In `B = ℤ_{(p)}[t]/(pt)`, the element `t` satisfies
`pt = 0`. So `t ≠ 0` in `B` (it is the image of the generator), and `p · t = 0` in `B`. So `t` is in the `p`-torsion of
`B`. Hence `Tor^A₁(B, 𝔽_p) ≠ 0`. By IV.5.6 (ii) failing, `B` is not flat over `A`.

Geometrically: the map `Spec(ℤ_{(p)}[t]/(pt)) → Spec ℤ_{(p)}` has fibers that algebraically jump. Over the generic point
`(0)`, the fiber is `Frac(ℤ_{(p)})[t]/(0) = Frac(ℤ_{(p)})[t]`, the affine line. Over `(p)`, the fiber is
`𝔽_p[t]/(0 · t) = 𝔽_p[t]`, the affine line again — but the map `t ↦ t` from the special fiber to `B` no longer factors
through the special fiber consistently; the embedded component along `t = 0` (where `t` is `p`-torsion) is missing at
the generic point. The `Tor` computation captures exactly this jump.

## Closing remark

Theorem IV.5.6 is the algebraic content of "flatness is the right condition for a family to vary continuously without
algebraic jumps." All the gentle-SGA appeals to flatness up through file 22 — the ones that quietly cite the appendix
rows `flatness-sorites`, `local-flatness-criterion`, `completion-flat`, `completion-test-for-flatness` — are
applications or special cases of IV.5.6 plus the IV.1, IV.2, IV.3 sorites of files 24–25.

The geometric payoff comes in §6 (file 27): combined with constructibility (Chevalley) and the open-set characterization
via generizations, IV.5.6 implies that the flat locus `U = { x ∈ X : F_x  flat over  𝒪_{f(x)} }` is **open** in `X`
(IV.6.10), and that for `Y` integral, the flat locus is non-empty (IV.6.11 — generic flatness, the spread-out theorem).

Read on into [file 27](27-expose-iv-6-constructibility-openness-and-generic-flatness-gentle.md) for the geometric
consequences and the closing of the project.
