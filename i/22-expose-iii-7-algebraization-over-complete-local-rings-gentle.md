# Exposé III, section 7: algebraization over complete local rings (gentle)

## What this file is about

A central drama of modern number theory is the move between geometric shapes defined modulo a prime, where the
arithmetic is rigid and finite, and shapes defined over the integers themselves, where the methods of ordinary geometry
apply. Lifting from the small-prime world to the integer world is hard. The standard strategy climbs one infinitesimal
layer at a time, takes a limit, and then asks whether the limit really is an honest geometric object rather than a
purely formal tower.

The previous files built the layer-by-layer machinery and identified the obstruction at each step. This file finishes
the job. When two bookkeeping groups attached to the shape are both zero, every layer can be climbed and the limit comes
from an honest geometric object. The marquee consequence is that every smooth curve in the small-prime world lifts to
one over the integers, with no obstruction at all.

The cohomological obstruction theory of file 21 (§III.5–§III.6) says when a smooth scheme $X_{0} / k$ lifts to a smooth
scheme over an infinitesimal thickening of $\operatorname{Spec} k$. Stringing those lifts together gives a **formal
scheme** $\mathfrak{X} \to \hat{S}$ (Theorem III.6.10, file 21). The remaining question — and the payoff of the exposé —
is whether this formal scheme is in fact **algebraic**: whether it comes from an ordinary scheme over the base.

This is the point at which **Cohen rings** enter. Cohen's structure theorem gives every complete noetherian local ring
$(A, \mathfrak{m}, k)$ a **Cohen ring** $W$ with the same residue field, with $A$ a quotient of
$W[[T_{1}, \cdots, T_{n}]]$. In equicharacteristic $A$ contains a coefficient field; in mixed characteristic $W$ is the
role played by the Witt vectors $W(k)$. This pins the lifting story to characteristic-`0` arithmetic.

The headline is **Theorem III.7.3**: a smooth projective scheme $X_{0} / k$ with
$H^{2}(\mathfrak{g}_{X_{0}/k}) = H^{2}(\mathcal{O}_{X_{0}}) = 0$ lifts to a smooth projective scheme $X / A$. For curves
both $H^{2}$ vanish (dimension reasons), giving the corollary

> **Corollary III.7.4.** _Every smooth proper curve over $k$ lifts to a smooth proper curve over any complete local ring
> with residue field $k$._

This is the exposé's most concrete payoff and the foundation for the transcendental study of fundamental groups of
curves in the later exposés of SGA 1.

The slogan that runs through:

> **Lifting smooth schemes from characteristic $p$ to characteristic `0`: H²(𝔤) controls the formal lift; H²(𝒪) controls
> the algebraization.** When both vanish — and they always do for curves — there is no obstruction at all, and the
> smooth scheme lifts.

## Cohen rings and coefficient fields

A complete noetherian local ring $(A, \mathfrak{m}, k)$ carries a great deal of structure. Cohen's structure theorem
makes it explicit: there is a "minimal" complete local ring $W$ with the same residue field as $A$, and $A$ is built
from $W$ by adjoining formal-power-series variables and (perhaps) taking a quotient. This $W$ is the **Cohen ring of
$k$**.

Cohen rings are the stuff over which lifting from characteristic $p$ to characteristic `0` happens. The most important
examples:

- **Equicharacteristic.** If $char k = 0$, or more generally if $A$ contains a copy of its residue field, the Cohen ring
  $W$ is just $k$ itself, and $A$ is a quotient of $k[[T_{1}, \cdots, T_{n}]]$.
- **Mixed characteristic.** If $char k = p > 0$ but $A$ has characteristic `0` (so $p \neq 0$ in $A$, but
  $p \in \mathfrak{m}$), the Cohen ring $W$ is a complete discrete valuation ring with residue field $k$ and uniformizer
  $p$. For $k = \mathbb{F}_{p}$, $W = \mathbb{Z}_{p}$. For $k$ perfect of characteristic $p$, $W = W(k)$ is the **ring
  of Witt vectors** of $k$ (Serre, _Local Fields_ Ch. II).

### Definition: Cohen ring

**Definition.** _A **Cohen ring** is a complete noetherian local ring $W$ with maximal ideal `(p)` for some prime
$p > 0$ (or `(0)`, in which case $W$ is a field) and perfect residue field._

The Cohen ring of a perfect field $k$ of characteristic $p > 0$ is the unique (up to canonical isomorphism) complete DVR
with residue field $k$ and uniformizer $p$. For $k = \mathbb{F}_{q}$ the Cohen ring is the unramified extension of
$\mathbb{Z}_{p}$ of degree $[k : \mathbb{F}_{p}]$ — explicitly the **Witt vectors** $W(k)$. For $k$ not perfect, one can
still construct a Cohen ring (existence is part of the structure theorem) but it is not unique.

We treat Cohen rings as a **black box**, reading off the structure theorem we need from EGA 0_IV §19.8. Appendix row
`cohen-ring` records this; appendix row `coefficient-field` records the equicharacteristic version.

### Existence and structure

**Cohen's structure theorem (EGA 0_IV §19.8.6).** _Let $(A, \mathfrak{m}, k)$ be a complete noetherian local ring._

1. _There exists a Cohen ring $W$ with residue field $k$._
1. _There exists a surjective local ring map_

$$
W[[T_{1}, \cdots, T_{n}]] \twoheadrightarrow A
$$

_for some $n \geq 0$._

_If $A$ is itself regular of dimension $n$ (i.e. $\dim A = n$ and $\mathfrak{m}$ is generated by $n$ elements), the
surjection can be taken to be an isomorphism. In particular $A \simeq W[[T_{1}, \cdots, T_{n}]]$ as a formal power
series ring over the Cohen ring._

(Black box; appendix `cohen-ring`. The proof in EGA 0_IV §19.8.6 is several pages, building up from the existence of a
coefficient field in equicharacteristic, then the existence of a Cohen ring in mixed characteristic via
Witt-vector-style lifting.)

### Equicharacteristic case: coefficient field

If $A$ contains a field — equivalently, if $char A = char k$ — the **coefficient field theorem** says there is a copy of
$k$ sitting inside $A$.

**Coefficient field theorem (EGA 0_IV §19.6).** _Let $(A, \mathfrak{m}, k)$ be a complete noetherian local ring with
$char A = char k$. Then there exists a subfield $k' \subset A$ with $A \to k$ inducing an isomorphism $k' \simeq k$._

(Black box; appendix `coefficient-field`.)

In this case the Cohen ring $W = k'$ is just (a copy of) the residue field, and Cohen's theorem reads
$A \simeq k[[T_{1}, \cdots, T_{n}]]$ (or a quotient thereof).

### Mixed characteristic: Witt vectors

If $char A = 0$ but $char k = p > 0$, the situation is more delicate. The Cohen ring $W$ is no longer a field; it is a
complete DVR of mixed characteristic. The cleanest case is when $k$ is perfect: then $W = W(k)$ is the unique unramified
extension of $\mathbb{Z}_{p}$ with residue field $k$, the **ring of Witt vectors**.

For our purposes, the only fact we need is: **Cohen rings exist, and their formal-power-series rings recover all
complete local rings.** This means it suffices to study the lifting question **over Cohen rings as the universal base**;
if a smooth scheme lifts over a Cohen ring $W$, it lifts over every complete local $A$ with residue field $k$. The Cohen
ring is the **most characteristic-rigid** version of the lifting question.

In particular, for $k$ perfect of characteristic $p > 0$, the universal Cohen ring is $W(k)$. For $k = \mathbb{F}_{p}$
it is $\mathbb{Z}_{p}$. The exposé works mostly with $A$ complete local; the reader who wants to specialize should keep
these examples in mind.

## III.7 Application to construction of formal and ordinary smooth schemes

<!-- source: III.7 -->

We now apply the cohomological obstruction theory of file 21 to the central question: given a smooth scheme $X_{0}$ over
a field $k$, when does it lift to a smooth scheme over a Cohen ring $W$ with residue field $k$ (and hence, by descent,
over every complete local ring with residue field $k$)?

### Setup: equal vs unequal characteristic

We distinguish two cases.

**1. $A$ is "of equal characteristics".** This is the case in particular if $char k = 0$. Then by the coefficient-field
theorem, there exists a coefficient subfield $k' \subset A$. Then there even exists an **ordinary** smooth scheme over
$A$ reducing to $X_{0}$, namely

```text
X = X₀ ⊗_k A,
```

with $A$ regarded as an algebra over $k$ via $k \to k' \to A$. This is the simplest possible lift.

This construction is **not natural**, however. Already in the case $A = k[t]/(t^{2})$ (the dual numbers), another
lifting homomorphism $k \to A$ (defined by an absolute derivation of $k$ into itself) gives an $X' / A$ not isomorphic
to $X = X_{0} \otimes_{k} A$ in general, provided $H^{1}(X_{0}, \mathfrak{g}_{X_{0}/k}) \neq 0$. So the "trivial" lift
is sensitive to the choice of coefficient field — interesting in its own right but not the point of the obstruction
theory.

The existence of a coefficient field $k'$ does, however, imply that the **first obstruction** to lifting $X_{0}$, which
lies in $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/k}) \otimes_{k} \mathfrak{m}/\mathfrak{m}^{2}$, is necessarily zero. The
trivial lift exists at the first step. The **higher obstructions** to constructing $X_{2}, X_{3}, \cdots$ need not
vanish, and depend on a variable element in a principal homogeneous space under
$H^{1}(X_{0}, \mathcal{G}_{0}) \otimes \mathfrak{m}/\mathfrak{m}^{2}$. The detailed theory (Kodaira-Spencer brackets) is
studied in classical deformation theory; see Sernesi or Hartshorne.

**2. $A$ is of unequal characteristics.** Here we know much less. Even for $A = \mathbb{Z}/p^{2} \mathbb{Z}$ and $X_{0}$
an abelian scheme of dimension `2` over $\mathbb{F}_{p}$, the question of whether $X_{0}$ lifts to a smooth scheme over
$A$ was open at the time of the source's writing.

**(Footnote, from the source's later corrections.)** It is now known (Mumford, Oort) that abelian schemes do lift over
$\mathbb{Z}/p^{n}$ for every $n$, hence over the Cohen ring $W(k)$. Counterexamples in higher dimensions (non-abelian)
exist: Serre's example (_Proc. NAS USA_ 47 (1961), no. 1, pp. 108–109) of a smooth projective variety in characteristic
$p$ that does not lift to characteristic `0`; D. Mumford has an unpublished example with an algebraic surface
(referenced in the source).

In particular, the **first obstruction to lifting over a Cohen ring** lies in $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/k})$
(since $\mathfrak{m}/\mathfrak{m}^{2} = k$ for a Cohen ring with maximal ideal `(p)`); whether this can be **nonzero**
for some smooth $X_{0}$ was, at the time, open. It is now known to be nonzero in some cases (the source's footnote
indicates this).

These counterexamples are flagged here for completeness; the positive headline is **III.7.3** below: **everything works
for curves** because both $H^{2}(\mathfrak{g})$ and $H^{2}(\mathcal{O})$ vanish on a curve for dimension reasons.
**III.7.3** also gives a sufficient condition for higher-dimensional schemes (joint vanishing of $H^{2}(\mathfrak{g})$
and $H^{2}(\mathcal{O})$).

### Proposition: extending a locally free sheaf

<!-- source: III.7.1 -->

_This proposition says: extending a locally free sheaf along a thickening is a problem of the same shape as extending a
smooth scheme — H² is the obstruction, H¹ is the indeterminacy. The sheaf $\mathcal{G}$ is the endomorphism sheaf, not
the tangent sheaf, but the structure of the calculation is identical._

**Proposition III.7.1.** *Let $S$ be a prescheme with a quasi-coherent sheaf of ideals $\mathcal{I}$, let $X$ be a
prescheme over $S$, set $S_{n} := V(\mathcal{I}^{n+1})$ and $X_{n} := X \times_{S} S_{n}$. Let $\mathcal{E}_{n}$ be a
locally free sheaf on $X_{n}$, and seek to extend it to a locally free sheaf $\mathcal{E}_{n+1}$on$X_{n+1}$.*

_Then $\mathcal{E}_{n}$ defines a canonical **obstruction class in $H^{2}(X_{0}, \mathcal{G})$**, where_

```text
𝒢 := ℋ𝓂_{𝒪_{X₀}}(𝓔₀, 𝓔₀) ⊗ gr^{n+1}_𝓘(𝒪_X).
```

*Vanishing of this class is necessary and sufficient for the existence of $\mathcal{E}_{n+1}$. If the obstruction is
zero, the set of isomorphism classes (with isomorphisms inducing the identity on $\mathcal{E}*n$) of
$\mathcal{E}_{n+1}$is a torsor under$H^{1}(X*0, \mathcal{G})$.*

**Proof sketch.** Same argument as Theorem III.6.3 (file 21), mutatis mutandis. The sheaf of
$\mathcal{O}_{X_{n+1}}$-module automorphisms of $\mathcal{E}_{n+1}$ inducing the identity on $\mathcal{E}_{n}$ is
canonically isomorphic to
$\mathcal{Hm}(\mathcal{E}_{0}, \mathcal{E}_{0}) \otimes gr^{n+1}_{\mathcal{I}}(\mathcal{O}_{X}) = \mathcal{G}$. (This
identification is the analogue of III.6.1 for sheaves rather than schemes.) Two lifts of $\mathcal{E}_{n}$ are locally
isomorphic; the Čech 2-cocycle of triple-overlap composition failures gives the obstruction class in
$H^{2}(X_{0}, \mathcal{G})$. ∎

**Consequences.** If $X$ is **flat over $S$**, the sheaf $\mathcal{G}$ may be written

```text
𝒢 = ℋ𝓂_{𝒪_{X₀}}(𝓔₀, 𝓔₀) ⊗_{𝒪_{S₀}} gr^{n+1}_𝓘(𝒪_S).
```

If $S$ is affine and $gr^{n}(\mathcal{O}_{S})$ are locally free (the conditions of III.6.9), then for every $n$,

```text
H^i(X₀, 𝒢) = H^i(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A),
```

with $\mathcal{G}_{0} = \mathcal{Hm}_{\mathcal{O}_{X_{0}}}(\mathcal{E}_{0}, \mathcal{E}_{0})$. The single condition
$H^{2}(X_{0}, \mathcal{G}_{0}) = 0$ then makes all step obstructions vanish, and $\mathcal{E}_{n}$ extends to all $n$,
giving a coherent locally free sheaf on the formal completion $\hat{X}$.

### Algebraization criterion (EGA III §4.7.1, black box)

The obstruction theory of III.6.10 and III.7.1 produces a **formal smooth scheme** $\mathfrak{X} \to \hat{S}$ and a
**formal locally free sheaf** $\hat{\mathcal{E}}$ on $\mathfrak{X}$. To upgrade to ordinary algebraic schemes and
sheaves, we need an algebraization criterion.

**Theorem (EGA III §4.7.1).** *Let $\mathfrak{X} \to \hat{S}$ be a formal scheme proper over `Ŝ` (with
$S = \operatorname{Spec} A$ complete and noetherian). Suppose there exists a coherent formal sheaf $\hat{\mathcal{L}}$
on $\mathfrak{X}$ such that the restriction $\mathcal{L}_{0} := \hat{\mathcal{L}} |_{X*0}$is an **ample** line bundle on
the closed fiber$X_{0}$.*

_Then $\mathfrak{X}$ is **algebraizable**: there exists a projective scheme $X$ over $S$, equipped with an ample line
bundle $\mathcal{L}$ on $X$ such that the formal completion $(\hat{X}, \hat{\mathcal{L}})$ is isomorphic to
$(\mathfrak{X}, \hat{\mathcal{L}})$._

(Black box; appendix `algebraization-via-ample`. Combines with the Grothendieck existence theorem from file 18 —
coherent sheaves on $\hat{X}$ lift to $X$ — and the projectivity criterion that an ample line bundle exhibits $\hat{X}$
as Proj of a graded ring.)

In words: **a formal scheme proper over a complete base, equipped with a formal sheaf restricting to an ample line
bundle on the closed fiber, is the formal completion of an honest algebraic projective scheme.**

This is the algebraization step that promotes Theorem III.6.10 (formal lift exists) to **Theorem III.7.3** (algebraic
lift exists) — provided we can also lift an ample line bundle, which is the role of III.7.2 below.

### Proposition: algebraization under $H^{2}(\mathcal{O}) = 0$

<!-- source: III.7.2 -->

*This proposition says: when the formal scheme $\mathfrak{X}$ is proper, flat over a complete local $A$, with
$H^{2}(X_{0}, \mathcal{O}_{X*0}) = 0$, then the ample line bundle on $X_{0}$lifts to a formal line bundle
on$\mathfrak{X}$, which by the algebraization criterion EGA III §4.7.1 means $\mathfrak{X}$ is algebraic.*

**Proposition III.7.2.** *Let $A$ be a complete local ring, and let $\mathfrak{X}$ be a **formal scheme proper and flat
over $A$**, such that $X_{0} := \mathfrak{X} \otimes_{A} k$ is **projective** (over $k = A / \mathfrak{m}$) and
$H^{2}(X_{0}, \mathcal{O}_{X*0}) = 0$.*

_Then there exists a scheme $X$ projective over $A$ whose $\mathfrak{m}$-adic formal completion is isomorphic to
$\mathfrak{X}$._

**Proof sketch.** Apply III.7.1 to the structure sheaf $\mathcal{E}_{n} := \mathcal{O}_{X_{n}}$ (which is locally free
of rank `1`). The obstruction at step $n$ lies in $H^{2}(X_{0}, \mathcal{O}_{X_{0}}) \otimes_{A} gr^{n+1}_{I} (A)$
(using flatness and III.6.9 type computation). Since $H^{2}(X_{0}, \mathcal{O}_{X_{0}}) = 0$, all obstructions vanish,
and an ample line bundle $\mathcal{L}_{0}$ on $X_{0}$ lifts step by step to a formal line bundle $\hat{\mathcal{L}}$ on
$\mathfrak{X}$.

By the algebraization criterion (EGA III §4.7.1, above), $\mathfrak{X}$ is algebraizable: there exists a projective
$X / A$ with $\hat{X} = \mathfrak{X}$. ∎

### Theorem: the lifting theorem

<!-- source: III.7.3 -->

_This theorem says: combining the formal-lifting result III.6.10 with the algebraization result III.7.2, every smooth
projective scheme over $k$ with vanishing $H^{2}(\mathfrak{g})$ and $H^{2}(\mathcal{O})$ lifts to a smooth projective
scheme over any complete local $A$ with residue field $k$._

**Theorem III.7.3.** _Let $A$ be a complete local ring with residue field $k$, and let $X_{0}$ be a **smooth
projective** scheme over $k$ such that_

```text
H²(X₀, 𝔤_{X₀/k}) = H²(X₀, 𝒪_{X₀}) = 0.
```

_Then there exists a **smooth and projective** scheme $X$ over $A$ reducing to $X_{0}$._

_More generally, if one is given an $X_{n}$ smooth over $A_{n} = A / \mathfrak{m}^{n+1}$ reducing to $X_{0}$, then there
exists an $X$ smooth and proper over $A$ and an isomorphism $X \otimes_{A} A_{n} = X_{n}$._

**Proof.** By Corollary III.6.10 (file 21) applied to $S = \operatorname{Spec} A$ and $\mathcal{I} = \mathfrak{m}$,
vanishing of $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/k})$ gives a smooth formal scheme $\mathfrak{X} \to \hat{S}$ reducing to
$X_{0}$.

By Proposition III.7.2 above, vanishing of $H^{2}(X_{0}, \mathcal{O}_{X_{0}})$ together with projectivity of $X_{0}$
lifts an ample line bundle to a formal line bundle on $\mathfrak{X}$, and by the algebraization criterion EGA III §4.7.1
the formal scheme $\mathfrak{X}$ is algebraic — comes from a projective $X / A$.

Smoothness of $X$ over $A$ follows from smoothness of each $X_{n}$ over $A_{n}$. ∎

### Corollary: smooth proper curves lift

<!-- source: III.7.4 -->

_This corollary says: every smooth proper curve over $k$ lifts to a smooth proper curve over any complete local ring
with residue field $k$. This is the headline payoff: H²(𝔤) and H²(𝒪) both vanish on a curve for dimension reasons._

**Corollary III.7.4.** _Every smooth proper curve $X_{0}$ over $k$ is obtained by reduction from a smooth proper curve
$X$ over $A$ (any complete local $A$ with residue field $k$)._

**Proof.** Apply Theorem III.7.3. We need:

1. **$X_{0}$ is projective.** Every smooth proper curve over a field is projective (this is classical: a smooth proper
   curve has an ample line bundle — for instance, the canonical line bundle if $g \geq 2$, or any positive-degree line
   bundle in general).
1. **$H^{2}(X_{0}, \mathfrak{g}_{X_{0}/k}) = 0$.** By dimension: $X_{0}$ is one-dimensional, so
   $H^{i}(X_{0}, \mathcal{F}) = 0$ for $i \geq 2$ and any coherent sheaf $\mathcal{F}$ (Grothendieck vanishing for
   dimension reasons; cohomology in degree $> \dim X$ vanishes).
1. **$H^{2}(X_{0}, \mathcal{O}_{X_{0}}) = 0$.** Same dimension reason.

Both $H^{2}$ vanishings are dimensional. By III.7.3, $X_{0}$ lifts to a smooth projective $X / A$. ∎

This is the headline result Exposé III delivers. It is the **essential tool**, together with the existence theorem for
sheaves in formal geometry, **for studying the fundamental group of $X_{0}$ by transcendental means** in later exposés
of SGA 1 (particularly Exposés V and X). The strategy is:

- Lift $X_{0} / \mathbb{F}_{p}$ (or `/ k` for $k$ of characteristic $p > 0$) to a smooth proper curve $X / W(k)$ over
  the Witt vectors.
- The generic fiber $X \otimes_{W(k)} K$ (with $K = Frac W(k)$ of characteristic `0`) admits a complex-analytic
  embedding (after base change to $\mathbb{C}$).
- The transcendental fundamental group of the complex-analytic curve, computed by classical topology, equals the étale
  fundamental group of the original curve (after profinite completion).

This **specialization-to-characteristic-zero** technique — only possible because every smooth proper curve lifts — is
the bridge between algebraic and transcendental methods in arithmetic geometry.

## Counterexamples preserved as named pointers

The hypothesis "smooth projective with $H^{2}(\mathfrak{g}) = H^{2}(\mathcal{O}) = 0$" in III.7.3 is sufficient but not
necessary. Two famous facts:

### Serre's example

**Serre, _Proc. Nat. Acad. Sci. USA_ 47 (1961), pp. 108–109.**

There exists a smooth projective variety $X_{0}$ of characteristic $p > 0$ that does **not** lift to characteristic `0`.
Serre's construction uses a quotient of a Fermat-type variety by a finite group action; the obstruction is a nonzero
class in $H^{2}(\mathfrak{g})$ that the geometry forces. The example has dimension $\geq 3$.

### Mumford's surface

**D. Mumford** (unpublished; cited in the source's footnote).

There exists a smooth projective **surface** in characteristic $p$ that does not lift to characteristic `0`. Mumford's
example shows that the joint vanishing of $H^{2}(\mathfrak{g})$ and $H^{2}(\mathcal{O})$ in III.7.3 is not always
achievable — there are surfaces for which the obstruction is genuinely nonzero, and they do not lift.

Both examples are pointers, not constructions; the gentle reading does not reproduce them. The takeaway: **the lifting
theorem III.7.3 is sharp.** Curves always lift; some surfaces and higher-dimensional varieties do not.

## Continuing on

The gentle reading continues with **Exposé IV** — _Flat morphisms_ — in files 23–27. The flatness sorites that the étale
and smooth theories have leaned on throughout (the appendix rows
[`flatness-sorites`](appendix-black-boxes.md#flatness-sorites),
[`local-flatness-criterion`](appendix-black-boxes.md#local-flatness-criterion),
[`completion-flat`](appendix-black-boxes.md#completion-flat), and
[`completion-test-for-flatness`](appendix-black-boxes.md#completion-test-for-flatness)) get their full development
there. File 23 is extra preparation on the Tor functor, the spectral sequence for composite functors, and Noether's
normalization. Files 24–27 rewrite §§1–6 of Exposé IV: sorites and faithful flatness; completion and free modules; the
local flatness criterion (IV.5.6, the centerpiece); and the geometric package — open-image theorem (IV.6.6), openness of
the flat locus (IV.6.10), and generic flatness (IV.6.11). The reading then continues with **Exposé V** — _The
fundamental group: generalities_ — in files 28–33. Files 28–29 are extra preparation (topological covering theory in 28;
profinite groups, pro-objects, and the categorical toolkit in 29). Files 30–33 rewrite §§1–9 of Exposé V: quotients,
inertia groups, and principal coverings (V.1, V.2); étale automorphisms and the axiomatic Galois theorem V.4.1 (V.3,
V.4); Galois categories and exact functors (V.5, V.6); and the **étale fundamental group $\pi_{1}(S, a)$** (V.7), with
the case-of-a-field identification $\pi_{1}(\operatorname{Spec} k, \bar{a}) = \operatorname{Gal}(\bar{k}/k)$ (V.8.1) and
the normal-base surjection (V.8.2). The transcendental fundamental group of the complex-analytic curve cited in this
file's earlier "transcendental study of fundamental groups of curves" aside is the _topological_ $\pi_{1}$ of file 28;
its profinite completion is the algebraic $\pi^{\acute{e}}_{1}t$ of file 33. The closing of the project sits at the end
of file 33.
