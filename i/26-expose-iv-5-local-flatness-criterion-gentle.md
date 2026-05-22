# Exposé IV, section 5: the local flatness criterion (gentle)

## What this file is about

The well-behaved-family condition introduced two files back is hard to check directly. The definition asks for
compatibility with every possible auxiliary piece of data, and the test is not local in any obvious sense. In practice
one wants to know whether a family is well behaved by inspecting it only at a single fixed locus.

This file gives the theorem that makes the inspection legitimate. Under mild hypotheses, a family is well behaved over
its full base if and only if its restriction to the first infinitesimal layer at the locus is well behaved there and a
single auxiliary obstruction vanishes. Every earlier file in the seminar that argued well-behavedness by checking the
special fibre was implicitly using this theorem. It is the engine of the local theory of smooth and étale maps and
underlies almost every later flatness argument.

§4 (file 25) gave the flatness ⟺ freeness story over local rings under the standard hypotheses ($I$ nilpotent, or $A$
noetherian with $I$ in the radical and $M$ finite). The criterion was "$M \otimes A/I$ free plus
$Tor^{A}_{1}(M, A/I) = 0$," and the proof was a single Nakayama lift.

§5 globalizes this from the residue level to the entire $I$-adic filtration. The substantive question: given a
finite-type $B$-module $M$ and a homomorphism $A \to B$ with `IB` in the radical of $B$, what does it take to verify
that $M$ is **$A$-flat** (not just free over $A/I$)? The answer is a four-part equivalence (IV.5.6, the **local flatness
criterion**) that says: it suffices to check flatness of the **first thickening** $M \otimes_{A} A/I$, and the absence
of any Tor obstruction along the way.

The criterion is the workhorse of EGA's smoothness, étaleness, and lifting verifications. Every time the étale theory
(file 11) or the smooth theory (files 14–15) said "and now we check flatness on the special fiber, then conclude
flatness over the base," it was IV.5.6 doing the work — implicitly, until now.

The slogan:

> **IV.5.6 (local flatness criterion).** Let $A \to B$ be a map of noetherian rings, $I \subset A$ an ideal with `IB` in
> the radical of $B$, $M$ a finite-type $B$-module. Then:
>
> _M is $A$-flat ⟺ $M \otimes_{A} A/I$ is $A/I$-flat and $Tor^{A}_{1}(M, A/I) = 0$ ⟺ (gr form) $M \otimes_{A} A/I$ is
> $A/I$-flat and the canonical `gr` map is an iso ⟺ (filtration form) $M \otimes_{A} A/I^{n}$ is $A/I^{n}$-flat for
> every $n$._
>
> When $A/I$ is a field (the most common case), the $M \otimes_{A} A/I$ flat hypothesis is automatic, and the criterion
> reduces to "Tor-vanishing on the residue field."

Throughout this file we use the Tor language of
[file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md) and the IV.4.2 `gr` criterion of
[file 25](25-expose-iv-3-4-completion-and-free-modules-gentle.md). The single non-routine input is the **spectral
sequence for composite functors** (file 23, §2), which IV.5.2 invokes once.

## IV.5 Local flatness criteria

<!-- source: IV.5 -->

### Proposition: Tor vanishing along $I^{n}$ and the `gr` isomorphism

<!-- source: IV.5.1 -->

_This proposition says: Tor-vanishing along the entire $I$-adic filtration implies the `gr` isomorphism. Conversely,
when $I$ is nilpotent, the `gr` isomorphism implies Tor-vanishing along the filtration. So in the nilpotent case the two
are equivalent._

**Proposition IV.5.1.** _Let $A$ be a ring, $I \subset A$ an ideal, $M$ an $A$-module. If_

```text
Tor^A₁(M, A/I^n) = 0  for every n ≥ 1,
```

_then the canonical surjective map_

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

_is an isomorphism. Conversely, if the `gr` isomorphism holds and $I$ is nilpotent, then $Tor^{A}_{1}(M, A/I^{n}) = 0$
for every $n \geq 1$._

**Proof.** **Forward direction.** The Tor-vanishing along $A/I^{n}$ for all $n$ says (by the same argument as in §IV.1,
applied to the inclusion $I^{n} \subset A$) that the natural maps

```text
I^n ⊗_A M → I^n M
```

are isomorphisms for every $n \geq 0$. Quotienting ($I^{n} / I^{n+1}$): the maps

```text
(I^n / I^{n+1}) ⊗_A M → I^n M / I^{n+1} M
```

are isomorphisms for every $n$. Summing over $n$ and identifying
$(I^{n} / I^{n+1}) \otimes_{A} M = (I^{n} / I^{n+1}) \otimes_{A/I} (M / IM)$ (using that $I$ acts as zero on
$I^{n} / I^{n+1}$ from one side): the canonical map of the displayed equation is an isomorphism in each graded degree,
hence an iso of graded $A/I$-modules.

**Converse (when $I$ is nilpotent).** Use descending induction on $n$: pick $n_{0}$ with $I^{n_{0}} = 0$; for
$n \geq n_{0} - 1$, the ideal $I^{n} = 0$, so the $Tor^{A}_{1}(M, A/I^{n}) = Tor^{A}_{1}(M, A) = 0$ trivially.

For the inductive step, suppose $Tor^{A}_{1}(M, A/I^{n+1}) = 0$. Use the diagram

```text
       M ⊗ I^{n+1}  →  M ⊗ I^n  →  M ⊗ (I^n / I^{n+1})  →  0
              ↓              ↓                 ↓
0  →       I^{n+1}M  →      I^nM  →     I^nM / I^{n+1}M    → 0
```

with exact rows (the bottom is exact by the iso in the right column at the next step; the top is right-exact, with the
left piece of the row coming from the long exact sequence in Tor).

By the gr-isomorphism hypothesis the right vertical arrow is an isomorphism (this is exactly the assertion). By the
inductive hypothesis on $n + 1$, the left vertical arrow is an isomorphism: from $Tor^{A}_{1}(M, A/I^{n+1}) = 0$ we
conclude $I^{n+1} \otimes_{A} M \to I^{n+1} M$ is an iso. Five lemma: the middle arrow $M \otimes I^{n} \to I^{n} M$ is
an iso. So $Tor^{A}_{1}(M, A/I^{n}) = 0$, completing the induction. ∎

The first half is a clean unwinding of "Tor vanishing on every quotient $A/I^{n}$ controls the graded structure." The
second half is the converse-via-descending-induction that fails when $I$ is not nilpotent — the descending induction has
no base case because $I^{n}$ does not eventually vanish.

> **Concrete special case.** For $A = k[t]_{(t)}$ and $I = (t)$, the inclusion $I = (t) \to A$ is multiplication by $t$.
> The Tor-vanishing $Tor^{A}_{1}(M, A/I) = 0$ says "multiplication by $t$ on $M$ is injective," i.e. $M$ is
> $t$-torsion-free. Iterating: $Tor^{A}_{1}(M, A/I^{n}) = 0$ for every $n$ says $M$ is torsion-free for every $t^{n}$.
> The `gr` isomorphism then identifies $gr(M) \cong M/tM \otimes k[T]$, which is the algebraic version of "the Taylor
> expansion of $M$ at the origin is structureless from the data of $M / tM$ plus the polynomial ring `k[T]` of
> derivatives."

### Proposition: Serre's lemma (composite functors)

<!-- source: IV.5.2 -->

_This proposition says: tensoring is local in a strong sense for flatness purposes. Vanishing of $Tor^{A}_{1}(M, N)$ for
**all** $B$-modules $N$ (where $B$ sits between $A$ and the situation) is equivalent to two pieces: vanishing of
$Tor^{A}_{1}(M, B)$ itself, plus $B$-flatness of the base-change $M \otimes_{A} B$. This is the algebraic input that
lets the next two corollaries reduce flatness verifications across $A \to B$._

**Proposition IV.5.2** (Serre)**.** _Let $A \to B$ be a homomorphism of rings, and let $M$ be an $A$-module. The
following are equivalent:_

1. _For every $B$-module $N$, $Tor^{A}_{1}(M, N) = 0$._
1. _$Tor^{A}_{1}(M, B) = 0$, and $M \otimes_{A} B$ is $B$-flat._

**Proof.** Apply the spectral sequence for composite functors (file 23, §2) with $F = - \otimes_{A} B : A$-Mod
$\to B$-Mod and $G = - \otimes_{B} N : B$-Mod $\to Ab$. The composition is $G \circ F = - \otimes_{A} N$. The spectral
sequence has the form

```text
E²_{p, q} = Tor^B_p(Tor^A_q(M, B), N) ⇒ Tor^A_{p + q}(M, N).
```

The five-term exact sequence in low degrees (file 23) reads

```text
Tor^B₁(M ⊗_A B, N) ← Tor^A₁(M, N) ← Tor^A₁(M, B) ⊗_A N.
```

(Right-to-left direction; the spectral sequence is a left-derived homological sequence.)

**(i) ⟹ (ii).** Suppose $Tor^{A}_{1}(M, N) = 0$ for every $N$. From the displayed sequence, both surrounding terms are
zero (the left because $Tor^{A}_{1}(M, B) = 0$, applying (i) with $N = B$; the right because $Tor^{A}_{1}(M, N) = 0$ is
the central term). So $Tor^{B}_{1}(M \otimes_{A} B, N) = 0$ for every $B$-module $N$. By the Tor characterization (file
23), $M \otimes_{A} B$ is $B$-flat.

**(ii) ⟹ (i).** Suppose $Tor^{A}_{1}(M, B) = 0$ and $M \otimes_{A} B$ is $B$-flat. From the displayed sequence: the
right term $Tor^{A}_{1}(M, B) \otimes_{A} N = 0$ (by hypothesis); the left term $Tor^{B}_{1}(M \otimes_{A} B, N) = 0$
(by $B$-flatness of $M \otimes_{A} B$). So the central term $Tor^{A}_{1}(M, N) = 0$. ∎

This is the lemma Serre isolated to simplify the proof of IV.5.6. The key insight: instead of verifying Tor-vanishing of
$M$ on every $A$-module $N$ (a possibly large family), one verifies Tor-vanishing of $M$ on the single $A$-module $B$,
plus $B$-flatness of the (often smaller) base-change $M \otimes_{A} B$.

### Corollary: extending to $N$ annihilated by a power of $I$

<!-- source: IV.5.3 -->

_This corollary says: when $B = A/I$ (the special case most relevant to applications), the Tor-vanishing of IV.5.2 (i)
extends from $B$ itself to every $A$-module annihilated by a power of $I$ — even though the IV.5.2 statement is *for
every $B$-module*._

**Corollary IV.5.3.** _Suppose $B = A/I$ in IV.5.2. The equivalent conditions of IV.5.2 are then also equivalent to:_

1. _$Tor^{A}_{1}(M, N) = 0$ for every $A$-module $N$ annihilated by some power of $I$._

**Proof.** (i) of IV.5.3 says: $Tor^{A}_{1}(M, N) = 0$ for every $A/I^{k}$-module $N$ (for all $k \geq 1$).

That implies (i) of IV.5.2: take $k = 1$, then $N$ is an $A/I = B$-module.

For the converse, use the filtration $N \supset IN \supset I^{2}N \supset \cdots \supset I^{k} N = 0$ of $N$ (the $k$-th
piece is zero by hypothesis). The quotients $I^{j} N / I^{j+1} N$ are annihilated by $I$, so are $A/I = B$-modules. By
IV.5.2 (i), $Tor^{A}_{1}(M, I^{j} N / I^{j+1} N) = 0$. Inductively (using the long exact Tor sequence on each
$0 \to I^{j+1} N \to I^{j} N \to I^{j} N / I^{j+1} N \to 0$), one propagates the vanishing up to
$Tor^{A}_{1}(M, N) = 0$. ∎

This corollary is the form that connects IV.5.2 (a tensor- algebraic statement about all $B$-modules) to the $I$-adic
content of §IV.4 (a graded statement about the filtration).

### Corollary: the `gr` criterion holds and $M \otimes A/I$ is flat

<!-- source: IV.5.4 -->

_This corollary says: when the IV.5.2 / IV.5.3 conditions hold (with $B = A/I$), one automatically has the IV.4.2 `gr`
isomorphism for the $I$-adic filtration of $M$, plus flatness of the residue $M \otimes_{A} A/I$ over $A/I$. This is the
bridge from "Tor-vanishing along the filtration" to "the `gr` form of the criterion."_

**Corollary IV.5.4.** _Under the conditions of IV.5.3, the canonical functorial map_

```text
gr_I⁰(M) ⊗_{A/I} gr_I(A) → gr_I(M)
```

_is an isomorphism, and $M \otimes_{A} A/I$ is $A/I$-flat._

**Proof.** The Tor-vanishing of (i) of IV.5.3 gives in particular $Tor^{A}_{1}(M, A/I^{n}) = 0$ for every $n \geq 1$. By
IV.5.1 (forward direction), the `gr` map is an iso.

For $A/I$-flatness of $M \otimes_{A} A/I$: this is just the second half of (ii) of IV.5.2 transcribed
($M \otimes_{A} B = M \otimes_{A} A/I$ is $B = A/I$-flat). ∎

So the equivalent (i)–(ii) of IV.5.2 and (i) of IV.5.3 propagate to **two extra conditions** that look identical to
those of IV.4.2 / IV.4.3.

### Corollary: the nilpotent-$I$ form

<!-- source: IV.5.5 -->

_This corollary says: when $I$ is nilpotent, the equivalences collapse to a clean three-condition equivalence — flatness
over $A$, flatness over $A/I$ plus Tor-vanishing, and flatness over $A/I$ plus the `gr` iso. The nilpotent-$I$ form is
the regime in which the entire criterion is symmetric._

**Corollary IV.5.5.** _Let $A$ be a ring with a nilpotent ideal $I$, and let $M$ be an $A$-module. The following are
equivalent:_

1. _$M$ is $A$-flat._
1. _$M \otimes_{A} A/I$ is $A/I$-flat, and $Tor^{A}_{1}(M, A/I) = 0$._
1. *$M \otimes_{A} A/I$ is $A/I$-flat, and the canonical map $gr^{0}_{I}(M) \otimes_{A/I} gr_{I}(A) \to gr_{I}(M)$ is an
   iso.*

**Proof.** **(i) ⟹ (ii).** $M$ flat ⟹ $Tor^{A}_{1}(M, -) = 0$ ⟹ in particular $Tor^{A}_{1}(M, A/I) = 0$. Also
$M \otimes_{A} A/I$ is $(A/I)$-flat by base change (file 24, IV.1's closure properties).

**(ii) ⟹ (i).** Suppose (ii). We want $M$ to be $A$-flat. By the criterion of IV.5.2 with $B = A/I$: it suffices to have
$Tor^{A}_{1}(M, A/I) = 0$ (one half of (ii)) and $M \otimes_{A} A/I$ is $A/I$-flat (the other half). Combined with
IV.5.3, we get $Tor^{A}_{1}(M, N) = 0$ for every $N$ annihilated by a power of $I$. **Since $I$ is nilpotent**, every
$A$-module is annihilated by a power of $I$ (specifically, by the power $I^{n_{0}}$ with $I^{n_{0}} = 0$). So
$Tor^{A}_{1}(M, N) = 0$ for every $A$-module $N$. By the Tor characterization, $M$ is flat.

**(ii) ⟺ (iii).** This is IV.5.1 (both directions, since $I$ is nilpotent), applied to the $M \otimes_{A} A/I$-flat
hypothesis. The $Tor^{A}_{1}(M, A/I) = 0$ half of (ii) and the `gr` iso of (iii) are equivalent given the second clause
$M \otimes_{A} A/I$ flat (which makes the `Tor` and `gr` reductions of §IV.4 valid). ∎

The nilpotent-$I$ form (IV.5.5) is the "if and only if" of the local flatness criterion in the artinian / infinitesimal
regime — exactly the regime that recurs throughout §III.5–§III.6 (file 21). When the gentle reader encountered the H¹
obstruction story of file 21, the underlying flatness lifts were governed by IV.5.5 implicitly.

### Theorem: the local flatness criterion (IV.5.6)

<!-- source: IV.5.6 -->

_This theorem says: the equivalences of IV.5.5 extend to the non-nilpotent case under a finiteness / radical hypothesis.
For $A \to B$ of noetherian rings, `IB` in the radical of $B$, and $M$ a finite-type $B$-module, the same four
conditions are equivalent (plus a fourth: flatness of every thickening $M \otimes_{A} A/I^{n}$)._

**Theorem IV.5.6.** _Let $A \to B$ be a homomorphism of noetherian rings, let $I$ be an ideal of $A$ such that `IB` is
contained in the radical of $B$, and let $M$ be a $B$-module of finite type. Then the following are equivalent:_

1. _$M$ is $A$-flat._
1. _$M \otimes_{A} A/I$ is $A/I$-flat and $Tor^{A}_{1}(M, A/I) = 0$._
1. *$M \otimes_{A} A/I$ is $A/I$-flat and the canonical map $gr^{0}_{I}(M) \otimes_{A/I} gr_{I}(A) \to gr_{I}(M)$ is an
   iso.*
1. _For every integer $n$, $M \otimes_{A} A/I^{n}$ is flat over $A/I^{n}$._

**Proof outline.** **(i) ⟹ (ii)** is base change. **(ii) ⟺ (iii)** is IV.5.1 (the converse direction needs Krull's
intersection theorem in lieu of the nilpotency previously assumed; this is where the hypotheses noetherian + `IB` in
radical + $M$ finite enter, ensuring that intersections $\cap_{n} I^{n} M \subset (separated topology)$ vanish). **(ii)
⟹ (iv)**: apply IV.5.5 to the system $(A, A/I^{n}, I/I^{n}, M \otimes_{A} A/I^{n})$ to get flatness of
$M \otimes_{A} A/I^{n}$ over $A/I^{n}$ from (ii)-style data on the smaller filtration. **(iv) ⟹ (i)**: this is the
substantive direction; it is where the noetherian \+ finite + radical-`IB` hypothesis is essential, in the form of the
"$M \otimes_{A} N$ is $I$-adically separated for $N$ of finite type" condition the source isolates. The argument from
there (lines 408–432 of the source) is a careful diagram chase that identifies the kernel of
$M \otimes_{A} N' \to M \otimes_{A} N$ for an arbitrary inclusion $N' \to N$ of finite-type $A$-modules with the
intersection of the $I^{n} M \otimes_{A} N'$, then uses Krull-separation to make that intersection vanish.

The full proof is in lines 295–432 of the source. We do not reproduce the diagram chase (its essence is a careful
application of Krull plus the (iv)-style flatness hypothesis at each thickening); the reader who wants the line-by-line
should consult Bourbaki AC III §5.4 or the source's own argument. ∎

The hypothesis "`IB` is in the radical of $B$" is automatic in the most arithmetic-relevant case where $B$ is local and
$I$ is contained in the maximal ideal of $A$ (then `IB` is in the maximal ideal of $B$). The finite-type-$M$-over-$B$
hypothesis then becomes "finite-type $B$-module" with $B$ local noetherian.

> **The case $A/I$ a field.** This is the deformation-theoretic regime: $(A, \mathfrak{m})$ local noetherian,
> $I = \mathfrak{m}$, $A/\mathfrak{m} = k$ the residue field. The condition "$M \otimes_{A} A/I$ is $A/I$-flat" becomes
> "$M \otimes_{A} k$ is $k$-flat," automatic for any $k$-vector space. The criterion collapses to:
>
> _For $(A, \mathfrak{m})$ noetherian local, $B$ noetherian local with $\mathfrak{m} B \subset \mathfrak{n}_{B}$, and
> $M$ finite over $B$: $M$ is $A$-flat ⟺ $Tor^{A}_{1}(M, k) = 0$ ⟺ the `gr` map is an iso ⟺ each
> $M \otimes_{A} A/\mathfrak{m}^{n}$ is $A/\mathfrak{m}^{n}$-free._
>
> The "$M \otimes_{A} A/\mathfrak{m}^{n}$ is $A/\mathfrak{m}^{n}$-free" form is the one most often invoked in
> deformation theory: to verify flatness of a deformation, lift the special-fiber structure to each infinitesimal
> thickening freely. This is the form used in file 19 / file 21 implicitly.

The theorem IV.5.6 is the centerpiece of the exposé. The remaining propositions IV.5.7–IV.5.9 are corollaries.

### Corollary: relative criterion for $u : M' \to M$

<!-- source: IV.5.7 -->

_This corollary says: a homomorphism of finite-type $B$-modules that is $A$-flat-on-the-target is $A$-flat-injective
(with flat cokernel) iff its tensor product with the residue field is injective. This is the form used in deformation
theory: to lift a homomorphism along a thickening with flatness preserved, it suffices to check injectivity at the
residue field._

**Corollary IV.5.7.** _Let $A \to B$ be a local homomorphism of noetherian local rings, and let $u : M' \to M$ be a
homomorphism of finite-type $B$-modules. Suppose $M$ is flat over $A$. Let $k$ be the residue field of $A$. The
following are equivalent:_

1. _$u$ is injective and `Coker\ u` is flat over $A$._
1. _$u \otimes_{A} k : M' \otimes_{A} k \to M \otimes_{A} k$ is injective._

**Proof.** **(i) ⟹ (ii).** $u$ injective ⟹ the short exact sequence $0 \to M' \to M \to Coker\ u \to 0$ exists. By
IV.1.1 (file 24\) with flat right term (the cokernel), the sequence remains exact after tensoring with $k$. So
$u \otimes_{A} k$ is injective.

**(ii) ⟹ (i).** First, we show $u$ is injective. Pass to associated graded modules along the
$\mathfrak{m}_{A}$-filtration: the condition $u \otimes_{A} k = u \otimes_{A} A/\mathfrak{m}_{A}$ injective gives
$gr^{0}_{\mathfrak{m}_{A}}(u)$ injective. By the `gr` iso (IV.5.6 (iii) for $M$, which is $A$-flat by hypothesis),
$gr_{\mathfrak{m}_{A}}(u) : gr(M') \to gr(M)$ is determined in each degree by $gr^{0}$, which is injective. So $gr(u)$
is injective in every degree. The kernel of $u$ then lives in the intersection of the $\mathfrak{m}^{n}_{A} M'$ (no
graded contribution survives), which by Krull is zero. So $u$ is injective.

Second, we show `Coker\ u` is $A$-flat. The short exact sequence $0 \to M' \to M \to Coker\ u \to 0$ and the long exact
Tor sequence give

```text
Tor^A₁(M, k) → Tor^A₁(Coker\ u, k) → M' ⊗_A k → M ⊗_A k.
```

By $M$-flat, the leftmost term is zero. By hypothesis (ii), the rightmost arrow is injective, so the connecting term
$Tor^{A}_{1}(Coker\ u, k) = 0$. By IV.5.6 applied to `Coker\ u` (a finite-type $B$-module), `Coker\ u` is $A$-flat. ∎

This is the criterion that supplied "lift $u$ to a thickened deformation injectively with flatness preserved" in file
21's H¹ obstruction calculations. The gentle reader can now see that the underlying lift was governed by IV.5.7 as a
black box.

### Corollary: completion-invariance of flatness

<!-- source: IV.5.8 -->

_This corollary says: under the IV.5.6 hypotheses, flatness of $M$ over $A$ is equivalent to flatness of $M$ over the
$I$-adic completion `Â`. Completing the base does not change flatness — the algebraic microscope of completion preserves
flat / non-flat distinctions._

**Corollary IV.5.8.** _Under the hypotheses of IV.5.6, let $J$ be an ideal of $B$ containing `IB` and contained in the
radical of $B$. Let `Â`, $\hat{B}$, $\hat{M}$ be the $J$-adic completions of $A$, $B$, $M$ respectively (with `Â` the
$I$-adic completion). Then $M$ is $A$-flat ⟺ $M$ is `Â`-flat._

**Proof.** The forward direction ($M$ flat over $A$ ⟹ flat over `Â`) is immediate by base change along $A \to \hat{A}$
(and `Â`-flat for $\hat{M}$-style modules follows because completion preserves flatness for finite-type modules over
noetherian rings).

The reverse direction uses the `gr`-form criterion (iii) of IV.5.6 and IV.3.2 (file 25). The `gr` of the situation
$(A, B, I, M)$ is identified with the `gr` of the situation $(\hat{A}, \hat{B}, I\hat{A}, \hat{M})$ because completion
preserves graded structure along ideals contained in the radical. So the (iii) condition of IV.5.6 for $M / A$ is
equivalent to the (iii) condition for $\hat{M} / \hat{A}$. By IV.3.2 (faithful flatness of $\hat{A} / A$ under the
radical hypothesis) plus base change, both conditions translate across. So flatness of $M$ over $A$ is equivalent to
flatness of $\hat{M}$ over `Â`. The remaining identification "flat over `Â` for $M$ versus for $\hat{M}$" uses the
appendix row `completion-test-for-flatness`. ∎

This corollary is the proof of the appendix row `completion-test-for-flatness`, which has been treated as a black box
since file 04. The black box is now opened.

### Corollary: three-tier criterion $A \to B \to C$

<!-- source: IV.5.9 -->

_This corollary says: when there are three rings stacked $A \to B \to C$ with $B$ flat over $A$, flatness of a
$C$-module $M$ over $B$ decomposes into two independent pieces: flatness of $M$ over $A$, and flatness of the residue
$M \otimes_{A} k$ over $B \otimes_{A} k$. This is the criterion for "checking flatness over the middle ring after a base
change."_

**Corollary IV.5.9.** _Let $A \to B \to C$ be local homomorphisms of noetherian local rings, $M$ a finite-type
$C$-module, and suppose $B$ is flat over $A$. Let $k$ be the residue field of $A$. The following are equivalent:_

1. _$M$ is $B$-flat._
1. _$M$ is $A$-flat, and $M \otimes_{A} k$ is flat over $B \otimes_{A} k$._

**Proof.** **(i) ⟹ (ii).** $M$ flat over $B$ and $B$ flat over $A$ ⟹ $M$ flat over $A$ by transitive composition. For
the second part: tensoring with $k$ over $A$ is the base change $A \to k$, and $M \otimes_{A} k$ becomes
$M \otimes_{B} (B \otimes_{A} k)$ (associativity), which is flat over $B \otimes_{A} k$ by $M$ flat over $B$ and base
change.

**(ii) ⟹ (i).** Apply IV.5.6 (iii) to $(B, C, \mathfrak{m}_{B} = I, M)$ where $\mathfrak{m}_{B}$ is the maximal ideal of
$B$. The condition for flatness of $M / B$ is:
$M \otimes_{B} (B / \mathfrak{m}_{B}) = M \otimes_{B} (B \otimes_{A} k) = M \otimes_{A} k$ is flat over
$B / \mathfrak{m}_{B} = B \otimes_{A} k$, AND the second condition of IV.5.6 (iii) holds for the $gr_{\mathfrak{m}_{B}}$
of $M$. The first half of this is given by hypothesis (ii). The second half holds because $M$ is $A$-flat (hypothesis
(ii)) and $B$ is $A$-flat, by an associativity argument for tensor products
($M \otimes_{B} B / \mathfrak{m}^{n}_{B} = M \otimes_{A} (B / \mathfrak{m}^{n}_{B})$ etc., where flatness of $M / A$ and
of $B / A$ together secure each thickening's flatness via the same `gr` route). ∎

The remark from the source: when $\mathfrak{m}_{A}$ is nilpotent (instead of maximal but not nilpotent), the same
statement holds via IV.5.5 in place of IV.5.6. Conceptually: the "field at the bottom keeping things rigid" can be
replaced by an artinian local ring, and the criterion still works.

> **Note on the maximal-ideal-vs-nilpotent dichotomy.** The source comments parenthetically that maximality of
> $\mathfrak{m}$ "did not enter" the proof — the criterion works for any $I$ either nilpotent or in the radical with
> finite-type $M$ over noetherian $B$. The maximal case is "the best possible" in the sense that $A/\mathfrak{m}$ is a
> field, making flatness over $A/\mathfrak{m}$ automatic, and so the criterion collapses to the single condition
> $Tor^{A}_{1}(M, k) = 0$. This is the form most often invoked.

## Worked example: the elliptic curve over $\mathbb{Z}_{p}$

Continuing the running example from file 24 (and from files 14, 15, 21 going back). Take

```text
A = ℤ_{(p)},   I = (p),   k = A/I = 𝔽_p
```

and let $B = \mathbb{Z}_{(p)}[x, y] / (y^{2} - x^{3} - ax - b)$ for a Weierstrass equation with
$a, b \in \mathbb{Z}_{(p)}$ and discriminant $\Delta = 4a^{3} + 27b^{2} \neq 0$ in $\mathbb{Z}_{(p)}$ (we'll discuss the
case `p ∤ Δ` first). The morphism $\operatorname{Spec} B \to \operatorname{Spec} A$ is the elliptic curve $\mathcal{E}$
over $\operatorname{Spec} \mathbb{Z}_{(p)}$.

**Goal: verify flatness of $B$ over $A$ using IV.5.6.** Take $M = B$ (a finite-type $B$-module, trivially). Hypothesis
check: `A, B` noetherian; $I = (p)$, $IB = (p) B$. Is `IB` in the radical of $B$? We need `(p)` to lie in the Jacobson
radical of $B$. For $B$ semilocal (it is — its maximal ideals are the closed points of the special fiber
$\mathcal{E}_{p}$, all containing $p$), the Jacobson radical contains $p$, so yes.

**Apply IV.5.6 (ii).** We need:

1. $M \otimes_{A} A/I = B \otimes_{\mathbb{Z}_{(p)}} \mathbb{F}_{p} = \mathbb{F}_{p}[x, y] / (y^{2} - x^{3} - ax - b)$
   is $\mathbb{F}_{p}$-flat. As a vector space over a field, this is automatic.
1. $Tor^{A}_{1}(M, A/I) = Tor^{\mathbb{Z}_{(p)}}_{1}(B, \mathbb{F}_{p}) = 0$.

For the second point: take a free resolution of $\mathbb{F}_{p}$ over $\mathbb{Z}_{(p)}$:

$$
0 \to \mathbb{Z}_{(p)} \to \mathbb{Z}_{(p)} \to \mathbb{F}_{p} \to 0.
$$

This is a free resolution of length 1. Tensoring with $B$:

$$
0 \to B \to B \to B/pB \to 0.
$$

The kernel of $B \to B$ is the $p$-torsion of $B$. So $Tor^{\mathbb{Z}_{(p)}}_{1}(B, \mathbb{F}_{p}) = B[p]$ (the
$p$-torsion). For $B = \mathbb{Z}_{(p)}[x, y] / (y^{2} - x^{3} - ax - b)$ integral, the $p$-torsion is zero
($\mathbb{Z}_{(p)}$ is integral and torsion-free, and $B$ is a quotient of $\mathbb{Z}_{(p)}[x, y]$ by a polynomial that
is irreducible over $Frac(\mathbb{Z}_{(p)})[x, y]$ for generic $(a, b)$, hence integral). So
$Tor^{\mathbb{Z}_{(p)}}_{1}(B, \mathbb{F}_{p}) = 0$.

By IV.5.6, $B$ is $\mathbb{Z}_{(p)}$-flat. The morphism $\mathcal{E} \to \operatorname{Spec} \mathbb{Z}_{(p)}$ is flat.
∎

When $p | \Delta$, the special fiber $\mathcal{E}_{p}$ is singular (a node or a cusp), but $B$ is still
$\mathbb{Z}_{(p)}$-flat — the same Tor calculation goes through. The lesson: **flatness ≠ smoothness**. The elliptic
curve is flat over $\mathbb{Z}_{(p)}$ for every prime $p$, but smooth only over
$\operatorname{Spec} \mathbb{Z}_{(p)}[1/\Delta]$. The flat locus contains the smooth locus and, in fact, equals all of
$\mathcal{E}$; the smooth locus is the strict subset $\mathcal{E} \ V(\Delta)$.

In file 27 we will revisit this example to verify the open-image theorem (IV.6.6) and the openness of the flat locus
(IV.6.10) on $\mathcal{E}$. The flat locus is $\mathcal{E}$ itself, the maximal possible; generic flatness (IV.6.11) is
automatic.

## Worked example: a non-flat foil

Take $A = \mathbb{Z}_{(p)}$, $B = A[t]/(p t)$. Verify $B$ is not flat over $A$ using the failure of IV.5.6 (ii). Take
$M = B$.

$Tor^{A}_{1}(B, \mathbb{F}_{p})$ is computed as before: the $p$-torsion in $B$. In $B = \mathbb{Z}_{(p)}[t]/(pt)$, the
element $t$ satisfies $pt = 0$. So $t \neq 0$ in $B$ (it is the image of the generator), and $p \cdot t = 0$ in $B$. So
$t$ is in the $p$-torsion of $B$. Hence $Tor^{A}_{1}(B, \mathbb{F}_{p}) \neq 0$. By IV.5.6 (ii) failing, $B$ is not flat
over $A$.

Geometrically: the map $\operatorname{Spec}(\mathbb{Z}_{(p)}[t]/(pt)) \to \operatorname{Spec} \mathbb{Z}_{(p)}$ has
fibers that algebraically jump. Over the generic point `(0)`, the fiber is
$Frac(\mathbb{Z}_{(p)})[t]/(0) = Frac(\mathbb{Z}_{(p)})[t]$, the affine line. Over `(p)`, the fiber is
$\mathbb{F}_{p}[t]/(0 \cdot t) = \mathbb{F}_{p}[t]$, the affine line again — but the map $t \mapsto t$ from the special
fiber to $B$ no longer factors through the special fiber consistently; the embedded component along $t = 0$ (where $t$
is $p$-torsion) is missing at the generic point. The `Tor` computation captures exactly this jump.

## Closing remark

Theorem IV.5.6 is the algebraic content of "flatness is the right condition for a family to vary continuously without
algebraic jumps." All the gentle-SGA appeals to flatness up through file 22 — the ones that quietly cite the appendix
rows `flatness-sorites`, `local-flatness-criterion`, `completion-flat`, `completion-test-for-flatness` — are
applications or special cases of IV.5.6 plus the IV.1, IV.2, IV.3 sorites of files 24–25.

The geometric payoff comes in §6 (file 27): combined with constructibility (Chevalley) and the open-set characterization
via generizations, IV.5.6 implies that the flat locus $U = { x \in X : F_{x}  flat over  \mathcal{O}_{f(x)}}$ is
**open** in $X$ (IV.6.10), and that for $Y$ integral, the flat locus is non-empty (IV.6.11 — generic flatness, the
spread-out theorem).

Read on into [file 27](27-expose-iv-6-constructibility-openness-and-generic-flatness-gentle.md) for the geometric
consequences and the closing of the project.
