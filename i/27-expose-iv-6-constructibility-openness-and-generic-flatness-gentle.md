# Exposé IV, section 6: constructibility, open morphisms, and generic flatness (gentle)

## What this file is about

The previous file said when a family is well behaved at a single point. The follow-up question is how the well-behaved
points sit inside the base. Are they an open region, with each one in a fat neighbourhood of its peers? A thin scatter
of isolated points? Is the well-behaved region even non-empty?

This file gives three answers. A well-behaved family with full support produces an open map on the base. The points at
which an arbitrary family of coherent data is well behaved form an open subset of the source. Over a base with no
internal partitions, the well-behaved region contains a non-empty open piece. The third answer, called generic flatness,
is the technical reason why a piece of data over the generic point of an arithmetic base spreads out automatically to a
Zariski-open neighbourhood. It is invoked all over arithmetic geometry.

The local flatness criterion of §5 (file 26) lives at a single point. Globalizing it requires topology: how do flatness
loci sit inside `Spec(B)`? The answer rests on **constructibility** (Chevalley) and the open-set characterization via
generizations. Combined with the local criterion, these geometric ingredients give:

- The **open-image theorem** (IV.6.6): a finite-type morphism `f : X → Y` carrying a coherent flat sheaf with full
    support is open.
- **Openness of the flat locus** (IV.6.10): for any coherent sheaf `F` on a finite-type morphism `X → Y`, the set of
    points where `F` is flat over the base is open in `X`.
- **Generic flatness** (IV.6.11): when `Y` is integral, every coherent sheaf on a finite-type morphism `X → Y` is flat
    over a non-empty open `V ⊂ Y` along its preimage. This is the **spread-out** theorem used freely in arithmetic
    geometry: deformations from generic-fiber data to neighboring fibers exist over a Zariski open.

The slogan:

> **Flat morphisms are open. The flat locus is open. Over an integral base, the flat locus is non-empty.** Each
> statement is a translation of the local flatness criterion (IV.5.6) by a topological criterion (IV.6.4).

The first three subsections develop the topological infrastructure (IV.6.1–IV.6.5: Chevalley constructibility and the
open-set characterization via generizations). The middle two prove the open-image theorem (IV.6.6) and isolate the
generic-freeness lemma (IV.6.7) — the algebraic input. The final two combine these into the openness-of-the-flat-locus
theorem (IV.6.10) and generic flatness (IV.6.11).

The constructibility infrastructure is from circulating notes of the Dieudonné-Rosenlicht seminar, recorded in EGA 0_III
§9 and EGA IV §1.8–§1.10. We treat Chevalley's theorem (IV.6.2) as a black box (appendix row
`chevalley-constructibility`); the combinatorial criteria (IV.6.1, IV.6.3, IV.6.4) we develop in full.

## IV.6 Flat morphisms and open sets

<!-- source: IV.6 -->

### Setup: constructibility, generizations, specializations

A subset `Z` of a topological space `X` is **locally closed** if it is the intersection of an open and a closed set. A
subset is **constructible** if it is a finite union of locally closed subsets. (Equivalently: a finite union of
intersections `U ∩ Z` with `U` open and `Z` closed.) The constructible subsets of a noetherian topological space form a
Boolean algebra: closed under finite union, finite intersection, and complement.

A point `y` of a topological space is a **generization** of a point `x` if `x ∈ closure({y})` (the closure of the
singleton `{y}`). Symmetrically, `x` is a **specialization** of `y`. In a scheme `Spec A`, generization corresponds to
inclusion of prime ideals: `y` is a generization of `x` ⟺ `𝔭_y ⊂ 𝔭_x` (where the subscript names the corresponding
prime). The generic point of an irreducible closed subset is the unique generization of every point of that subset.

Throughout this section the topological space `X` will be a **noetherian** scheme (or its underlying topological space).
In this setting every irreducible closed subset has a unique generic point — a fact we use repeatedly without further
comment.

### Lemma: combinatorial criterion for constructibility

<!-- source: IV.6.1 -->

_This lemma says: in a noetherian topological space, a subset is constructible iff for every irreducible closed subset,
the intersection is either nondense or contains a non-empty open of the irreducible. The criterion picks out subsets
that "behave like polynomial-relations on each irreducible component"._

**Lemma IV.6.1.** _Let `X` be a noetherian topological space, and let `Z ⊂ X`. Then `Z` is constructible if and only if
for every irreducible closed subset `Y ⊂ X`, the intersection `Z ∩ Y` is either nondense in `Y` or contains a non-empty
open subset of `Y`._

**Proof.** **Necessity.** Constructible `Z` is a finite union of locally closed subsets. Pulling back to an irreducible
closed `Y`, `Z ∩ Y` is a finite union of locally closed subsets of `Y`. In an irreducible space, each non-trivial
locally closed subset is either contained in a proper closed subset (nondense) or contains a non-empty open subset. The
finite union must then either be nondense (if all components are nondense) or contain a non-empty open (if some
component does).

**Sufficiency.** By noetherian induction on `X`. Suppose every irreducible closed `Y ⊂ X` satisfies the criterion for
`Z ∩ Y`. Let `Y₁, …, Y_r` be the irreducible components of `X` (finite because `X` is noetherian). For each `Y_i`,
`Z ∩ Y_i` is either nondense or contains a non-empty open of `Y_i`. In the second case, write `Z ∩ Y_i = U_i ∪ F_i` with
`U_i` open in `Y_i` and `F_i` nondense. Now `Z = ⋃_i (Z ∩ Y_i)`, a finite union; each piece is itself a union of an open
in `Y_i` and a nondense piece. The nondense piece, again by the criterion, is itself constructible (by induction on the
dimension); so the whole `Z` is a finite union of locally closed sets. ∎

### Lemma: Chevalley — image of a finite-type morphism is constructible

<!-- source: IV.6.2 -->

_This lemma says: the image of a finite-type morphism between noetherian schemes is a constructible set. This is the
fundamental constructibility theorem of algebraic geometry._

**Lemma IV.6.2** (Chevalley)**.** _Let `f : X → Y` be a morphism of finite type of preschemes, with `Y` noetherian. Then
`f(X)` is constructible in `Y`._

The proof reduces to the affine case `f : Spec B → Spec A` with `B` finite-type over `A` and `A` noetherian. The key
step is the Chevalley constructibility theorem, which we treat as a black box (appendix row
`chevalley-constructibility`). The full proof is in EGA 0_III §9.2 / EGA IV §1.8.4 / Stacks tag 054K.

> **Sketch.** By noetherian induction on `Y`, reduce to `Y` integral. By Noether normalization (file 23), `B ⊗_A K` is
> finite over a polynomial subring `K[t₁, …, t_n]`. The image of `Spec(B) → Spec(A)` then contains the generic point of
> `Spec A` (because `B ⊗_A K ≠ 0`), and the rest of the image is described inductively by quotienting `A` by a small
> ideal. The full bookkeeping is the Chevalley argument.

The point for us: when we apply IV.6.5 below to a finite-type `f`, the image-set `f(X)` is constructible by Chevalley,
and the test "is `f(X)` a neighborhood of `y`?" can be answered using the generization criterion IV.6.3.

### Lemma: constructible neighborhoods via generizations

<!-- source: IV.6.3 -->

_This lemma says: in a noetherian topological space whose irreducible closed subsets have generic points, a
constructible subset `U` is a neighborhood of a point `x` iff `U` contains every generization of `x`. This is the key
"geometric form" of constructibility._

**Lemma IV.6.3.** _Let `X` be a noetherian topological space in which every irreducible closed subset admits a generic
point. Let `U` be a constructible subset of `X`, and let `x ∈ X`. Then `U` is a neighborhood of `x` if and only if every
generization `y` of `x` belongs to `U`._

**Proof.** **Necessity.** If `U` is a neighborhood of `x`, then `U` contains an open set `V ∋ x`. Every generization `y`
of `x` satisfies `x ∈ closure({y})`, so `closure({y}) ∩ V ≠ ∅`, so `y ∈ V` (because `y` is the unique generic point of
`closure({y})`, and the closure intersects the open). So `y ∈ V ⊂ U`.

**Sufficiency.** Suppose every generization of `x` belongs to `U`. By the criterion of IV.6.1 applied to the irreducible
closed subset `closure({x})`: the intersection `U ∩ closure({x})` is either nondense or contains a non-empty open of
`closure({x})`. The unique generic point of `closure({x})` is `x` itself, which is in `U` by hypothesis. So
`U ∩ closure({x})` contains the generic point, hence is dense. So by the dichotomy, `U ∩ closure({x})` contains a
non-empty open subset of `closure({x})`. That non-empty open contains `x` (because every non-empty open of an
irreducible space contains the generic point), so `U` is a neighborhood of `x` inside `closure({x})`, hence in `X`. ∎

### Corollary: open-set criterion via generizations

<!-- source: IV.6.4 -->

_This corollary says: in a noetherian topological space with generic points, a subset `U` is open iff (a) it contains
every generization of each of its points, and (b) for each point `x ∈ U`, the intersection `U ∩ closure({x})` contains a
non-empty open of `closure({x})`._

**Corollary IV.6.4.** _Let `X` be a noetherian topological space in which every irreducible closed subset admits a
generic point, and let `U ⊂ X`. Then `U` is open if and only if both:_

1. _`U` contains every generization of each of its points._
1. _For every `x ∈ U`, the intersection `U ∩ closure({x})` contains a non-empty open subset of `closure({x})`._

**Proof.** Necessity of (a) and (b) is immediate from the definitions. For sufficiency: by (a) and (b), `U` is
constructible (by IV.6.1: every irreducible closed `Y ⊂ X` has its intersection `U ∩ Y` either nondense or containing a
non-empty open). And by IV.6.3 (using (a)), `U` is a neighborhood of every point `x ∈ U`. So `U` is open. ∎

### Corollary: geometric form for finite-type morphisms

<!-- source: IV.6.5 -->

_This corollary says: for `f : X → Y` of finite type with `Y` locally noetherian, `f` carries neighborhoods of `x` to
neighborhoods of `y = f(x)` iff every generization `y'` of `y` is hit by some generization `x'` of `x` with
`f(x') = y'`. This is the "lifting of generizations" form of "open at `x`"._

**Corollary IV.6.5.** _Let `f : X → Y` be a morphism of finite type with `Y` locally noetherian. Let `x ∈ X` and
`y = f(x)`. The following are equivalent:_

1. _`f` carries every neighborhood of `x` to a neighborhood of `y`._
1. _For every generization `y'` of `y`, there exists a generization `x'` of `x` with `f(x') = y'`._

**Proof.** Reduce to `X, Y` affine, hence noetherian. We test the question "is `f(X)` a neighborhood of `y`?" by the
criterion of IV.6.3 (applied to the constructible set `f(X)`, which is constructible by Chevalley IV.6.2): `f(X)` is a
neighborhood of `y` ⟺ every generization `y'` of `y` lies in `f(X)` ⟺ every generization `y'` is the image of some
`x' ∈ X`. We need the lifted point `x'` to be a generization of `x`. The "necessity" direction of the corollary forces
`x'` to be a generization (otherwise the closure of `{x'}` does not contain `x`, and the neighborhood
`X \ closure({x'})` of `x` would have an image not containing `y'`). The "sufficiency" direction is direct. ∎

The geometric reading: the topological condition "`f` is open at `x`" lifts to the algebraic condition "every
generization (= specialization, in primes) of `f(x)` is realized by a generization of `x`."

### Theorem: flat ⟹ open (IV.6.6)

<!-- source: IV.6.6 -->

_This theorem says: a morphism `f : X → Y` locally of finite type to a locally noetherian base, carrying a coherent
sheaf with full support that is flat over the base, is open. The flat hypothesis ("the family varies without algebraic
jump") forces the geometric conclusion ("the image is a neighborhood of every target point")._

**Theorem IV.6.6.** _Let `f : X → Y` be a morphism locally of finite type, with `Y` locally noetherian. Let `F` be a
coherent sheaf on `X` with `Supp(F) = X` (full support), flat relative to `Y`. Then `f` is an open morphism._

**Proof.** It suffices to verify (ii) of IV.6.5 at every point `x ∈ X`. The generizations `x'` of `x` correspond to
prime ideals `𝔭_{x'} ⊂ 𝒪_{X, x}`; the generizations `y'` of `y = f(x)` correspond to prime ideals `𝔭_{y'} ⊂ 𝒪_{Y, y}`.
So we need to verify: every prime of `𝒪_{Y, y}` is induced by a prime of `𝒪_{X, x}`.

Now `F_x` is a non-zero `𝒪_{X, x}`-module (full support hypothesis), flat over `𝒪_{Y, y}` (flatness of `F` relative to
`Y`). By IV.2.2 (file 24): `F_x` is **faithfully flat** over `𝒪_{Y, y}`. By IV.2.3: every prime of `𝒪_{Y, y}` is induced
by a prime of `Supp(F_x) ⊂ 𝒪_{X, x}` (the support condition selects from the spectrum of `𝒪_{X, x}` exactly those primes
where `F_x ≠ 0`; faithful flatness then ensures these primes exist over each prime of `𝒪_{Y, y}`).

So (ii) of IV.6.5 holds at every `x`. By IV.6.5 itself, `f` is open at every `x ∈ X`. ∎

The remark from the source: since flatness is preserved under base change (IV.1's closure properties), `f` is moreover
**universally open** — open after every base change. This is the strongest possible "open" conclusion.

> **Grumpy footnote (preserved verbatim from the source).** "I do not know, however, when `Y` is integral and `X` is of
> finite type over `Y`, whether `f` induces on every component `X_i` of `X` an open morphism, or even only an
> equidimensional one, i.e. one whose fiber components all have the same dimension; one only knows that `X_i`
> **dominates** `Y`. The question is related to the following one: let `A → B` be a local homomorphism of noetherian
> local rings, such that `B` is flat over `A` and `𝔪 B` is an ideal of definition of `B`, which implies moreover
> `dim B = dim A`. Is it true that for every minimal prime ideal `𝔭_i` of `B` one has `dim B/𝔭_i = dim B`? Let us only
> point out that the answer to the first question is negative if one replaces the flatness hypothesis of IV.6.5 by the
> sole hypothesis that `f` is universally open."
>
> **Editorial follow-up.** The answer to the second (local dimension) question is affirmative; the answer to the first
> (open on each component) is negative even for `f` étale. See EGA IV 12.1.1.5 for the dimension equality on irreducible
> components of a flat fibre, and EGA Err_IV 33 for the counterexample to "open on each component." The gentle reader
> can absorb the spirit: "flat is open" is good news; "flat with extra structure" is more subtle than the bare
> topological openness suggests.

### Lemma: generic freeness (IV.6.7)

<!-- source: IV.6.7 -->

_This lemma says: for `A` noetherian integral and `B` finite- type over `A`, every finite-type `B`-module `M` becomes a
free `A`-module after inverting some non-zero element of `A`. This is the **generic freeness** lemma — the algebraic
input that controls the geometry over the generic point of `Y`._

**Lemma IV.6.7.** _Let `A` be a noetherian integral ring, let `B` be an `A`-algebra of finite type, and let `M` be a
`B`-module of finite type. Then there exists a non-zero element `f ∈ A` such that `M_f` is a free `A_f`-module (a
fortiori `A_f`-flat)._

**Proof.** Let `K = Frac(A)`. Then `B ⊗_A K` is a finite-type algebra over the field `K`, and `M ⊗_A K` is a finite-type
module over `B ⊗_A K`. Let `n = dim_K Supp(M ⊗_A K)`. We argue by induction on `n`.

**Base case `n = -1`** (i.e., `M ⊗_A K = 0`). Take a finite set of generators of `M` over `B`. Each generator is
annihilated by some non-zero element of `A` (because tensoring with `K` kills the generator). The product of those
non-zero elements is a non-zero `f ∈ A` such that `M_f = 0`, hence trivially free.

**Inductive step `n ≥ 0`.** The `B`-module `M` admits a composition series whose successive quotients are `B / 𝔭_i` for
prime ideals `𝔭_i ⊂ B`. An extension of free modules is free; inducting on the length of the series, we reduce to the
case `M = B / 𝔭` for a prime `𝔭` of `B`, equivalently `M = B` with `B` an integral `A`-algebra.

Apply Noether's normalization lemma (file 23) to the `K`-algebra `B ⊗_A K`: there exist algebraically independent
`t₁, …, t_n ∈ B ⊗_A K` such that `B ⊗_A K` is finite over `K[t₁, …, t_n]`. The `t_i` can be chosen in `B` after clearing
denominators by an element `f ∈ A`; localize to make this happen. So we may assume `B` is finite over the polynomial
subring `C := A[t₁, …, t_n] ⊂ B` with the `t_i` algebraically independent. Since `B` is integral and finite over `C`,
and `C` is integral, `B` is a finite torsion-free `C`-module. Let `m` be its `C`-rank.

There is then an exact sequence of `C`-modules

```text
0 → C^m → B → M' → 0
```

where `M'` is a torsion `C`-module. The Krull dimension of `M' ⊗_A K` over `C ⊗_A K = K[t₁, …, t_n]` is strictly less
than `n` (because `M'` has positive `t`-adic codimension as a torsion `C`-module). By the inductive hypothesis (applied
to `(A, C, M')`), there is a non-zero `f ∈ A` such that `M'_f` is free over `A_f`.

On the other hand, `C^m = (A[t₁, …, t_n])^m` is a free `A`-module — its underlying `A`-module structure has a basis
indexed by `{t₁^{a₁} ⋯ t_n^{a_n} : a_i ≥ 0}^m`, which is infinite but free.

So both `C^m` and `M'_f` (after replacing `f` by a suitable power product if needed) are free over `A_f`. Their
extension `B_f` in the displayed short exact sequence is also free over `A_f` (extensions of free modules over a ring
are free in the "free as `A`-module" sense, by elementary linear algebra over `A_f`). So `B_f = M_f` is `A_f`-free. ∎

The induction step is the substance of the lemma: Noether normalization realizes `B` as a finite extension of a
polynomial algebra `C`, and the polynomial algebra is `A`-free for free.

> **Corollary already in hand.** IV.6.7 immediately implies the **weak generic flatness**: for `Y = Spec A` integral
> noetherian, `X = Spec B` of finite type over `Y`, and `M = F` a coherent sheaf on `X`, there is a non-zero `f ∈ A`
> such that `F_f` is `A_f`-free, hence `A`-flat at every point of `Spec(B_f) ⊂ X`. The full openness IV.6.10 needs more
> machinery; the weak form needs only IV.6.7.

### Lemma: passage from generically flat to flat on a Zariski open

<!-- source: IV.6.8 -->

_This lemma says: if a finite-type module is flat at a single prime, then it is flat in a Zariski open neighborhood of
that prime, after the appropriate localization in `B`._

**Lemma IV.6.8.** *Let `A` be a noetherian ring, `B` a finite- type `A`-algebra, `M` a finite-type `B`-module, `𝔭` a
prime ideal of `B`, and `𝔮 = 𝔭 ∩ A` the prime it induces in `A`. Suppose `M*𝔭`is flat over`A*𝔮`(equivalently over`A`).
Then there exists `g ∈ B − 𝔭` such that:*

1. _`(M / 𝔮 M)_g` is flat over `A / 𝔮`._
1. _`Tor^A₁(M, A / 𝔮)_g = 0`._

**Proof.** Apply IV.6.7 to the system `(A / 𝔮, B / 𝔮 B, M / 𝔮 M)`: there exists `f ∈ A − 𝔮` such that `(M / 𝔮 M)_f` is
free over `(A / 𝔮)_f`, hence flat over `A / 𝔮`. So (a) is achieved on the localization `(M / 𝔮 M)_f`.

For (b): since `M_𝔭` is flat over `A`, `Tor^A₁(M, A / 𝔮)_𝔭 = Tor^A₁(M_𝔭, A / 𝔮) = 0`. Now `Tor^A₁(M, A / 𝔮)` is a
finite-type `B`-module (it is computed from a finite resolution of `A / 𝔮` over `A` and finite-type `M`), and the
localization at `𝔭` is zero, so some `g ∈ B − 𝔭` annihilates `Tor^A₁(M, A / 𝔮)`, i.e. `Tor^A₁(M, A / 𝔮)_g = 0`.

Replacing `g` by `g · f` (and using `f ∈ A ⊂ B − 𝔭` since `𝔭` does not contain `f`), both (a) and (b) hold
simultaneously. ∎

### Corollary: extension to nearby primes

<!-- source: IV.6.9 -->

*This corollary says: under the conclusion of IV.6.8, for every prime `𝔭'` of `B` containing `𝔭` and not containing `g`,
the localization `M_{𝔭'}`is flat over`A`(and over the corresponding prime`A_{𝔮'}`).*

**Corollary IV.6.9.** *With the notation of IV.6.8, for every prime `𝔭'` of `B` containing `𝔭` and not containing `g`,
`M_{𝔭'}`is flat over`A`, equivalently over `A_{𝔮'}`where`𝔮' = 𝔭' ∩ A`.*

**Proof.** Apply the local flatness criterion IV.5.6 (file 26) in the form (ii) to the system `(A, B_{𝔮'}, 𝔮, M_{𝔮'})`:
the flatness of `M_{𝔮'}` over `A` is equivalent to flatness of `(M / 𝔮 M)_{𝔮'}` over `A / 𝔮` plus vanishing of
`Tor^A₁(M, A / 𝔮)_{𝔮'}`. Both pieces are now consequences of (a) and (b) of IV.6.8, localized at `𝔮'` and using `g ∉ 𝔭'`
(so `𝔭' ∩ B_g ≠ B_g`, allowing the localization to remain non-trivial). ∎

### Theorem: openness of the flat locus (IV.6.10)

<!-- source: IV.6.10 -->

_This theorem says: for any finite-type morphism `f : X → Y` to a locally noetherian base, and any coherent sheaf `F` on
`X`, the **flat locus** `U = { x ∈ X : F_x  flat over  𝒪_{f(x)} }`is open in`X`. So flatness is a Zariski-local
condition on the source._

**Theorem IV.6.10.** _Let `f : X → Y` be a morphism of finite type with `Y` locally noetherian, and let `F` be a
coherent sheaf on `X`. Let `U = { x ∈ X : F_x  flat over  𝒪_{f(x)} }`. Then `U`is open in`X`._

**Proof.** Reduce to `X` and `Y` affine, with rings `B` and `A` respectively, and `F` corresponds to a finite-type
`B`-module `M`. We apply the open-set criterion IV.6.4 to the subset `U ⊂ X = Spec B`.

**Condition (a) of IV.6.4** (`U` contains every generization of each of its points): if `𝔭 ∈ U` (i.e., `M_𝔭` is
`A`-flat), and `𝔭'` is a generization of `𝔭` (i.e., `𝔭' ⊂ 𝔭`), then `M_{𝔭'} = (M_𝔭)_{𝔭'}` is a localization of the flat
`A`-module `M_𝔭`, hence flat over `A` (file 24, IV.1.2 (i)).

**Condition (b) of IV.6.4** (for each `𝔭 ∈ U`, the intersection `U ∩ closure({𝔭})` contains a non-empty open of
`closure({𝔭})`): Lemma IV.6.8 gives `g ∈ B − 𝔭` such that the conditions (a)–(b) hold; Corollary IV.6.9 then says every
`𝔭' ⊃ 𝔭` not containing `g` is in `U`. The set `closure({𝔭}) ∩ D(g) = {𝔭' ⊃ 𝔭 : g ∉ 𝔭'}` is a non-empty open of
`closure({𝔭})` (open because `D(g)` is open in `Spec B`; non-empty because `𝔭` itself is in it, i.e., `g ∉ 𝔭`). And
every point of this open is in `U`.

So both conditions of IV.6.4 hold, and `U` is open. ∎

The flat locus `U` is the algebraic content of "where the family `F` varies without jumps." Theorem IV.6.10 says this
locus is a Zariski open subset of the source — the place where flatness "sets in" cannot have a complicated topology.

### Corollary: generic flatness (IV.6.11)

<!-- source: IV.6.11 -->

_This corollary says: for `Y` integral and `X` of finite type over `Y`, the flat locus is non-empty over `Y`.
Concretely: there exists a non-empty open `V ⊂ Y` such that `F` is flat over `Y` at every point of `f⁻¹(V)`. This is
**generic flatness**, the spread-out theorem._

**Corollary IV.6.11.** _Under the conditions of IV.6.10, suppose `Y` is integral. Then there exists a non-empty open
`V ⊂ Y` such that `F` is flat over `Y` at every point of `f⁻¹(V)`._

**Proof.** Let `η ∈ Y` be the generic point. The local ring `𝒪_{Y, η} = Frac(A)` (when `Y = Spec A` integral) is a
field. So every `𝒪_{Y, η}`-module is flat. So every point of the fiber `f⁻¹(η)` is in the flat locus `U` of IV.6.10. By
IV.6.10, `U` is open in `X`. Since `f⁻¹(η) ⊂ U`, and `f⁻¹(η)` is the fiber over the generic point (the geometrically
dense subset of `X` over the generic `η`), the open `U` contains a set of the form `f⁻¹(V)` for some non-empty open
`V ⊂ Y`. (This uses that `f` is of finite type, so the image-of-fiber properties play out as expected.) ∎

The remark from the source:

> **In many questions, the following weaker form of Theorem IV.6.10 is sufficient; it already follows from Lemma IV.6.7,
> and therefore requires neither the technique of constructible sets nor Theorem IV.5.6.**

This is the gentle reader's heads-up that **IV.6.11 alone** needs much less machinery than IV.6.10. The shortcut: by
IV.6.7, `M_f` is `A_f`-free for some non-zero `f ∈ A`; then `Spec(B_f)` is contained in the flat locus, and `D(f) ⊂ Y`
is the desired open `V`. No constructibility or local flatness criterion needed.

In practice, generic flatness is the form most often invoked in arithmetic geometry — when you "spread out" a result
from a generic fiber to neighboring fibers, you are using IV.6.11 (or the IV.6.7 shortcut to it).

The closing remark from the source: when `Y` is noetherian but not integral, IV.6.11 gives a partition of `Y` into
locally closed subsets `Y_i` (one for each irreducible component of `Y`, with the induced reduced structure) such that
`F` is flat over each `Y_i` at every point of `X_i = X ×_Y Y_i`. This is the most general form of "flatness eventually
sets in."

## Worked example: openness of the flat locus on the elliptic curve

Continuing the elliptic-curve example from file 26. Take `A = ℤ`, `Y = Spec ℤ`, `B = ℤ[x, y] / (y² − x³ − ax − b)`,
`X = Spec B = ℰ`, `F = 𝒪_X` (the structure sheaf, a coherent sheaf with full support on `X`). Discriminant
`Δ = 4a³ + 27b² ∈ ℤ`.

**By the Tor calculation in file 26**, `B` is `ℤ`-flat at every point of `X`. So the flat locus `U` of IV.6.10 is **all
of `X`**. By IV.6.6, the morphism `ℰ → Spec ℤ` is open. By IV.6.11 (or trivially since `U = X`), `ℰ → Spec ℤ` is
generically flat — every point of `ℰ` lies over a point of `Spec ℤ` in the open `Spec ℤ` (i.e., everywhere; here
`Y = V`).

The interesting subtlety: although the flat locus is all of `X`, the **smooth** locus is the strict subset
`ℰ ∩ {Δ ≠ 0}_X = ℰ ×_{Spec ℤ} Spec\  ℤ[1/Δ]`. At a prime `p | Δ`, the special fiber `ℰ_p` has a singular point (a node
or cusp), so `ℰ` is not smooth at the singular point of the special fiber. But `ℰ` is still flat there — the family does
not have an embedded component or a sudden algebraic jump, only a singular special-fiber.

This is the canonical illustration of the **flat ⊃ smooth** distinction: smoothness requires regular fibers (in addition
to flatness), and the flat locus is generally larger than the smooth locus.

## Worked example: a non-flat foil revisited

`A = ℤ`, `B = ℤ[t]/(pt)`, `X = Spec B`, `F = 𝒪_X`. As verified in file 26, `B` is **not** flat over `ℤ` at every point:
the `p`-torsion in `B` makes `Tor^A₁(B, 𝔽_p) ≠ 0`.

What is the flat locus? At a prime `𝔭 ⊂ B` not containing `p`, the localization `B_𝔭` inverts `p`, so
`B_𝔭 = ℤ[t]_𝔭 / (pt)` becomes `ℤ[1/p][t]_𝔭`, with the relation `pt = 0` becoming `t = 0` (since `p` is invertible). So
`B_𝔭 = ℤ[1/p]_𝔭`, which is `ℤ`-flat (it is a localization of `ℤ[1/p]`, a localization of `ℤ`). So every prime not
containing `p` is in the flat locus.

At a prime `𝔭 ⊃ (p)` of `B`, the situation depends. The maximal ideal of the special fiber is `(p, t) ⊂ B`, and at this
maximal ideal the `p`-torsion in `B` (specifically, the element `t`) survives. So `B_{(p, t)}` has `p`-torsion, hence is
not `ℤ`-flat. The point `(p, t)` is in `X ∖ U`.

By IV.6.4 (a) applied to `U`, every generization of a flat point is flat. The points `𝔭 ∈ X` not containing `p` are open
in `X` (they form `D(p) = X ∩ {p ≠ 0}`); the points `𝔭 ⊃ (p, t)` are a closed subset of the special fiber; in between,
primes containing `(p)` but not `(t)` (i.e., generic primes of the special fiber) are open in the special fiber.

The flat locus `U` is consequently the open subset of `X` that **excludes** the irreducible closed component along
`t = 0` of the special fiber. The non-flat behavior is concentrated on the embedded `t = 0` component — the algebraic
jump of the family.

This illustrates IV.6.10 in its sharp form: the flat locus is open, and its complement (the non-flat locus) is the
closed set where the family algebraically jumps.

## Continuing on

The gentle reading continues with **Exposé V** — _The fundamental group: generalities_ — in files 28–33. The étale
fundamental group `π₁^ét(X, x̄)` that has been forward-referenced since file 05 (Galois group sidebar), file 06 (closing
note on the `π₁^ét` of normal schemes), file 22 (transcendental computation of `π₁^ét` of curves), and the four-exposé
arc above gets its full construction there.

Files 28–29 are extra preparation. File 28 develops topological covering spaces and the topological fundamental group
`π₁^top` — the geometric analogy that the algebraic story generalises. File 29 develops profinite groups, pro-objects of
a category, strict epimorphisms / monomorphisms, and connected objects in a category — the categorical and
topological-algebra toolkit used throughout the §§4–6 axiomatic theory.

Files 30–33 rewrite §§1–9 of Exposé V: quotients, inertia groups, and principal coverings (file 30, V.1–V.2); étale
automorphisms and the axiomatic Galois theorem V.4.1 (file 31, V.3–V.4); Galois categories and exact functors (file 32,
V.5–V.6); and the **étale fundamental group `π₁(S, a)`** of a connected locally noetherian scheme (file 33, V.7), with
the case-of-a-field identification `π₁(Spec k, ā) = Gal(k̄ / k)` (V.8.1) and the normal-base surjection `π₁(η) ↠ π₁(S)`
whose kernel is generated by ramification (V.8.2). The closing of the project sits at the end of file 33.
