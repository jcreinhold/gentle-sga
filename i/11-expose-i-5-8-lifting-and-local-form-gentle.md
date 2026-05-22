# Exposé I, sections 5–8: lifting and local form (gentle)

## What this file is about

When you bend a steel rod, every short stretch of it bends with the rest; the rod has no slack. The algebraic notion of
a covering map turns out to have the same flavour, and this file is where the rigidity is measured. Four separate
statements, taken in sequence, say how little information is enough to pin down a covering completely. A small condition
on points pins one down; a small infinitesimal thickening of the base fails to change the catalogue; a covering of a
sufficiently complete local target is determined by what it does on the residue field alone; and locally, every covering
is built from a single polynomial in one variable.

Each statement narrows the notion from a different side. The previous file gave the proofs in sketch. Here they are
proved in the source's full detail.

File 10 named the class. File 11 measures its rigidity. Across the four sections I.5–I.8 the source proves, in order,
that an étale morphism is determined by very little data: by one extra condition on the points (I.5.1), by its
restriction to a closed subscheme with the same underlying space (I.5.5 and I.8.3), by its residue data over a complete
local ring (I.6.1), and by a single monic polynomial up to localization (I.7.6). Each result tightens the slogan "étale
= local isomorphism" by another notch. Together they make the slogan a working theorem.

The four landmarks of the chapter:

1. **I.5.1**: étale + radicial = open immersion. With consequences for sections, lifting, and uniqueness.
1. **I.5.5**: étale schemes do not see nilpotent thickenings. Sections lift uniquely across $Y_{0} \to Y$.
1. **I.6.1**: finite étale extensions of a complete local ring correspond bijectively to finite separable algebras over
   the residue field.
1. **I.7.6**: every étale local algebra has a standard local form $(A[t]/F)_{(F')}$ with $F$ monic. The global existence
   theorem **I.8.3** — étale $Y_{0}$-schemes lift uniquely to étale $Y$- schemes for nilpotent thickenings — falls out
   of this.

Standing assumption: all preschemes are locally noetherian. [Zariski's Main Theorem](appendix-black-boxes.md#zmt),
[Chevalley's theorem on proper morphisms](appendix-black-boxes.md#chevalley-proper),
[Hensel's lemma](appendix-black-boxes.md#hensel), and the [flatness sorites](appendix-black-boxes.md#flatness-sorites)
enter as black boxes; the appendix collects statements and sources.

## I.5 The fundamental property of étale morphisms

<!-- source: I.5 -->

The chapter opener named the four landmarks. The first is here. An étale morphism, plus injectivity on points with
purely inseparable residue extensions (radicial), is an open immersion. The source of an étale morphism is then
identified with an open subscheme of the target.

That is theorem I.5.1. The rest of the section unpacks it. Sections of an étale morphism are open immersions onto
connected components. Morphisms into étale schemes lift uniquely across nilpotent thickenings.

### Theorem

<!-- source: I.5.1 -->

_This result says: an étale morphism that is also radicial (set-theoretically injective with purely inseparable residue
extensions) is exactly an open immersion._

**Theorem I.5.1.** Let $f : X \to Y$ be a morphism of finite type. The following are equivalent.

1. $f$ is an **open immersion**.
1. $f$ is **étale and radicial**.

### Proof

**Necessity (i) ⟹ (ii)** is immediate: an open immersion is étale and is set-theoretically injective with identity
residue extensions (hence radicial).

**Sufficiency (ii) ⟹ (i)**. We give two proofs, following the source. The first is shorter; the second more elementary.

#### First proof of sufficiency

A flat morphism is open. So we may replace $Y$ by $f(X)$ and assume $f$ is a homeomorphism onto $Y$. After **any base
extension**, the morphism remains flat, radicial, and surjective, hence remains a homeomorphism, hence is **closed**. So
$f$ is **proper** (separated

- universally closed + finite type).

Now apply [Chevalley's theorem](appendix-black-boxes.md#chevalley-proper): a proper morphism is finite iff it is
quasi-finite. Net implies quasi-finite (file 04), so $f$ is finite. Hence $f$ is defined by a coherent sheaf
$\mathcal{B}$ of algebras. Since $f$ is flat and finite, $\mathcal{B}$ is locally free. Since $f$ is radicial and
surjective, $\mathcal{B}$ has rank 1 everywhere. Therefore $\mathcal{B} = \mathcal{O}_{Y}$, and $X = Y$.

#### Second proof of sufficiency (more elementary)

Reduce to $Y$ and $X$ affine. Then to the local case: assume $Y = \operatorname{Spec} A$ with $A$ local,
$X = \operatorname{Spec} B$, and $f^{-1}(y) \neq \emptyset$ where $y$ is the closed point of $Y$. We must show $B = A$.

This implication propagates: every $y \in f(X)$ then has a neighborhood $U$ such that $X|U = U$, exhibiting $f$ as an
open immersion onto $f(X)$.

Reduce further by passing to the completion `Â`: replace $A$ by `Â` and $B$ by $B \otimes_{A} \hat{A}$. The map
$A \to \hat{A}$ is [faithfully flat](appendix-black-boxes.md#completion-flat), so the desired conclusion $A = B$
propagates.

So assume $A$ complete. Let $x$ be the (unique) point of $X$ over $y$. By corollary I.2.2, $\mathcal{O}_{x}$ is
**finite** over $A$. Being also **flat** (étale ⊃ flat) and **radicial** (étale + radicial hypothesis), the local ring
$\mathcal{O}_{x}$ is identified with $A$.

Then $X = Y \amalg X'$ as a disjoint union (since $\mathcal{O}_{x} = A$ provides a section of $f$). Since $X$ is
radicial over $Y$, no extra points remain, so $X' = \emptyset$ and $X = Y$. Done.

### Why two proofs

The first proof is conceptually short — proper + quasi-finite = finite, rank-one locally free = identity — but it uses
[Chevalley's theorem](appendix-black-boxes.md#chevalley-proper). The second is more elementary but longer. Each shows
why "étale + radicial" forces a local isomorphism.

### Corollary

<!-- source: I.5.2 -->

_This result says: a connected closed immersion that is also étale is the inclusion of a connected component._

**Corollary I.5.2.** Let $f : X \to Y$ be a closed immersion that is also étale. If $X$ is connected, then $f$ is an
isomorphism from $X$ onto a connected component of $Y$.

### Proof

A closed immersion is radicial. By I.5.1, $f$ is also an open immersion. A clopen connected piece is a connected
component.

### Corollary

<!-- source: I.5.3 -->

_This result says: sections of a net $Y$-scheme (with $Y$ connected) are in bijection with the components projecting
isomorphically; a section is determined by its value at one point._

**Corollary I.5.3.** Let $X$ be a net $Y$-scheme with $Y$ connected. Then every section $s : Y \to X$ of $X$ over $Y$ is
an isomorphism from $Y$ onto a connected component of $X$.

In particular, sections are in **bijection** with connected components $X_{i} \subseteq X$ whose projection
$X_{i} \to Y$ is surjective and radicial, equivalently (by I.5.1) is an isomorphism. A section is determined by its
value at any one point.

### Proof

A section is a closed immersion (because $X$ is separated over $Y$). A section is also étale (because $X \to Y$ is net
and $Y \to Y$ is the identity, étale; apply I.4.8). By I.5.2, the section is an isomorphism onto a connected component.

### Corollary

<!-- source: I.5.4 -->

_This result says: two $S$-morphisms into a net separated $S$-scheme that agree geometrically at one point are equal._

**Corollary I.5.4.** Let $X$, $Y$ be $S$-preschemes, with $X$ net and separated over $S$ and $Y$ connected. Let
$f, g : Y \to X$ be two $S$-morphisms. Suppose there is a point $y \in Y$ such that

```text
f(y) = g(y) = x,    and    f, g induce the same residue
                              homomorphism κ(x) → κ(y).
```

Then $f = g$.

### Proof

Apply I.5.3 to the situation reduced to $Y = S$, replacing $X$ by $X \times_{S} Y$. Two sections of $X \times_{S} Y$
over $Y$ agreeing at one geometric point agree.

### Theorem

<!-- source: I.5.5 -->

_This result says: morphisms into an étale $S$-scheme are in bijection with morphisms into its restriction to any closed
subprescheme with the same underlying space — the étale category does not see nilpotent thickenings._

**Theorem I.5.5.** Let $S$ be a prescheme, $S_{0} \subseteq S$ a closed subprescheme with the same underlying
topological space (a "nilpotent thickening"). Let `X, Y` be $S$-preschemes, and let $X_{0} = X \times_{S} S_{0}$,
$Y_{0} = Y \times_{S} S_{0}$.

If $X$ is **étale** over $S$, then the natural map

```text
Hom_S(Y, X) → Hom_{S₀}(Y₀, X₀)
```

is **bijective**.

### Proof

Reduce to $Y = S$ and $Y_{0} = S_{0}$ by replacing $X$ with $X \times_{S} Y$. Now we are looking at sections of
$X \to S$ versus sections of $X_{0} \to S_{0}$. By I.5.3, sections correspond to connected components of $X$ (resp.
$X_{0}$) projecting isomorphically. Since $X$ and $X_{0}$ have the **same underlying topological space** (the closed
subprescheme $S_{0}$ has the same space as $S$, and $X_{0} \subseteq X$ likewise has the same space as $X$), connected
components of $X$ correspond to connected components of $X_{0}$. The bijection follows.

### Scholium

The result asserts both **uniqueness** and **existence** of morphisms. When $Y$ is also étale over $S$, it says the
functor $X \mapsto X_{0}$ from étale $S$-schemes to étale $S_{0}$-schemes is **fully faithful**. Section I.8 upgrades
this to an **equivalence of categories**; existence of lifts is theorem I.8.3.

### Corollary (extension theorem for liftings)

<!-- source: I.5.6 -->

_This result says: a partial lift of a morphism from a closed subscheme $Y_{0}$ extends uniquely to all of $Y$ when the
target is étale._

**Corollary I.5.6.** Consider a commutative diagram

$$
Y_{0} \to X
\downarrow    \downarrow
Y  \to S
$$

where $X \to S$ is étale and $Y_{0} \to Y$ is a **bijective closed immersion** (a closed immersion that is a
homeomorphism, equivalently a nilpotent thickening). Then there is a **unique** morphism $Y \to X$ making both triangles
commute.

### Proof

Reduce to the case $Y = S$, $X$ replaced by $X \times_{S} Y$, then apply I.5.5 to $Y = S$.

### Proposition

<!-- source: I.5.7 -->

_This result says: for a $Y$-morphism between flat finite-type $Y$-schemes, "open immersion" and "isomorphism" can be
checked on each fiber._

**Proposition I.5.7.** Let $X$ and $X'$ be of finite type and flat over $Y$, and let $g : X \to X'$ be a $Y$-morphism.
Then $g$ is an **open immersion**, respectively an **isomorphism**, iff for every $y \in Y$ the induced morphism on
fibers

```text
g ⊗_Y κ(y) : X ⊗_Y κ(y) → X′ ⊗_Y κ(y)
```

is an open immersion, respectively an isomorphism.

### Proof

Sufficiency is what needs proof. The surjective case is standard (surjective on every fiber implies surjective). Reduce
to the case of an open immersion. By I.5.1, we must verify $g$ is radicial (immediate from injectivity on each fiber)
and étale (uses I.5.9 below).

### Corollary

<!-- source: I.5.8 -->

_This result says: quasi-finite and net at a point can be checked on the fiber._

**Corollary I.5.8.** Let $X, X'$ be $Y$-preschemes, and $g : X \to X'$ a $Y$-morphism. Let $x \in X$ with $y$ its
projection to $Y$. Then $g$ is **quasi-finite**, respectively **net**, at $x$ iff the same is true of
$g \otimes_{Y} \kappa(y)$ at the corresponding point.

### Proof

The two algebras over $\kappa(g(x))$ to be considered are the same for $g$ and for the fiber morphism.

### Corollary

<!-- source: I.5.9 -->

_This result says: when source and target are flat and of finite type, flat and étale at a point can be checked
fiberwise._

**Corollary I.5.9.** With the notation of I.5.8, suppose $X$ and $X'$ are flat and of finite type over $Y$. Then $g$ is
**flat**, respectively **étale**, at $x$ iff $g \otimes_{Y} \kappa(y)$ is so.

### Proof

The flat statement is one of the fundamental criteria for flatness of a morphism in fibers, treated as a black box (cf.
EGA IV 5.9). The étale statement combines this with corollary I.5.8.

### What to remember

The key statements are I.5.1 (étale + radicial = open immersion), I.5.5 (sections lift uniquely across nilpotent
thickenings), and I.5.6 (the explicit "extension theorem for liftings"). These give the full uniqueness side of the
equivalence of étale categories under nilpotent thickening.

## I.6 Étale extensions of complete local rings

<!-- source: I.6 -->

I.5.5 gave uniqueness of lifting across a nilpotent thickening. Section I.6 turns it into a classification. Over a
**complete** noetherian local ring $A$ with residue field $k$, finite étale $A$-algebras are classified by finite
separable $k$-algebras. The classifying functor is reduction modulo $\mathfrak{m}$.

This is a special case of the formal-scheme theory of section I.8. But it admits a direct proof, short, and free of
Zariski's Main Theorem (which I.7 will need).

### Theorem

<!-- source: I.6.1 -->

_This result says: over a complete noetherian local ring, the category of finite étale extensions is the same data as
the category of finite separable algebras over the residue field._

**Theorem I.6.1.** Let $A$ be a complete noetherian local ring with residue field $k$. The functor

```text
R : { finite étale A-algebras } → { finite separable k-algebras },
   B ↦ B ⊗_A k
```

is an **equivalence of categories**.

### Proof

We must show $R$ is **fully faithful** and **essentially surjective**.

#### Fully faithful

The full faithfulness is the following corollary, true for any pair of $A$-algebras.

#### Corollary

<!-- source: I.6.2 -->

_This result says: Hom out of a finite étale $A$-algebra is determined by Hom out of its residue algebra._

**Corollary I.6.2.** Let $B, B'$ be finite $A$-algebras with $B$ **étale** over $A$. Then the canonical map

```text
Hom_{A-alg}(B, B′) → Hom_{k-alg}(R(B), R(B′))
```

is **bijective**.

#### Proof of I.6.2

By passing to $A/\mathfrak{m}^{n}$ and taking limits, reduce to $A$ artinian. Then $A$ is a nilpotent thickening of
$k = A/\mathfrak{m}$, and the result follows from theorem I.5.5 applied with $S = \operatorname{Spec} A$,
$S_{0} = \operatorname{Spec} k$, $X = \operatorname{Spec} B$, $Y = \operatorname{Spec} B'$.

#### Essentially surjective

Given a finite separable $k$-algebra $L$, we must produce an étale $A$-algebra $B$ with $B \otimes_{A} k = L$.

We may assume $L$ is a single separable extension (the general case is a finite product of these). So $L = k[t]/\bar{F}$
for some monic separable polynomial $\bar{F} \in k[t]$.

Lift $\bar{F}$ to a monic polynomial $F \in A[t]$ (possible because $A \twoheadrightarrow k$). Set $B = A[t]/F$.

Then $B \otimes_{A} k = k[t]/\bar{F} = L$. We must show $B$ is étale over $A$.

$B = A[t]/F$ is finite of rank `deg F` over $A$. Because $F$ is monic, $B$ is **free** of rank `deg F` over $A$ with
basis $1, t, \cdots, t^{deg F - 1}$. Free modules are flat, so $B$ is flat over $A$.

To check unramifiedness, use the computation $\Omega^{1}_{B/A} = B / F'(t) \cdot B$. Modulo $\mathfrak{m}$, this becomes
$L / \bar{F}'(t) \cdot L$. Since $\bar{F}$ is separable, $\bar{F}'(t)$ is a unit in $L$, so
$\Omega^{1}_{B/A} \otimes k = 0$. By [Nakayama](appendix-black-boxes.md#nakayama), $\Omega^{1}_{B/A} = 0$. So $B$ is
unramified over $A$.

Étale = flat + unramified. So $B$ is étale over $A$. This completes the proof.

### Why this works

Three ingredients. First, lifting across nilpotent thickenings (I.5.5) gives full faithfulness in the artinian case.
Second, completion: an étale algebra over $A$ is determined by its restrictions to $A/\mathfrak{m}^{n}$. Third, the
explicit construction $B = A[t]/F$ for a separable $\bar{F}$.

Section I.7 expands the third.

### What to remember

Over a complete local ring, the étale theory reduces entirely to the residue field. Every finite separable extension
$L/k$ lifts uniquely to a finite étale $B/A$, and morphisms also lift uniquely.

## I.7 Local construction of unramified and étale morphisms

<!-- source: I.7 -->

I.6.1 classified the complete-local case by reduction to the residue field. Section I.7 drops completeness and replaces
it with an explicit local model. Every étale local algebra is, up to localization, of the form $A[t]/F$ with $F$ monic
and $F'$ nonzero in the residue field.

That is theorem I.7.6. Its proof uses [Zariski's Main Theorem](appendix-black-boxes.md#zmt) as a black box.

### Proposition

<!-- source: I.7.1 -->

_This result says: localizing a polynomial-presented finite $A$-algebra away from the derivative `F'(u)` makes the
morphism net._

**Proposition I.7.1.** Let $A$ be noetherian, $B$ a finite $A$-algebra generated by a single element $u \in B$. Let
$F \in A[t]$ be such that $F(u) = 0$ ($F$ not assumed monic). Set $u' = F'(u) \in B$. Let $\mathfrak{q}$ be a prime
ideal of $B$ not containing $u'$, and let $\mathfrak{p} = \mathfrak{q} \cap A$ be its trace on $A$. Then
$B_{\mathfrak{q}}$ is **net** over $A_{\mathfrak{p}}$.

### Geometric reading

$Y = \operatorname{Spec} A$, $X = \operatorname{Spec} B$, $X_{u'} = \operatorname{Spec} B[1/u']$. Then $X_{u'}$ is
**unramified** over $Y$. The reason is the more precise statement:

### Corollary

<!-- source: I.7.2 -->

_This result says: the different ideal of $B/A$ contains the principal ideal `u'B` generated by `F'(u)`, with equality
when the polynomial presentation $A[t]/F \to B$ is an isomorphism._

**Corollary I.7.2.** The different ideal $\mathfrak{d}_{B/A}$ of $B/A$ contains $u' B$. It **equals** $u' B$ if the
natural homomorphism $A[t]/FA[t] \to B$, sending $t \mapsto u$, is an isomorphism.

### Proof

Let $J = \ker(A[t] \to B, t \mapsto u)$. Then $J \supseteq FA[t]$, with equality in the second case. Compute:

```text
Ω¹_{B/A} = Ω¹_{A[t]/A} ⊗ B  /  ⟨ J · Ω¹, dJ ⟩.
```

The polynomial ring has $\Omega^{1}_{A[t]/A} = A[t] \cdot dt$, free of rank one, so tensoring with $B$ gives
$B \cdot dt$. Then:

```text
Ω¹_{B/A} = B · dt / ⟨ images of dG for G ∈ J ⟩.
```

For $G \in J$, $dG = G'(u) \cdot dt$. The set of such $G'(u)$ for $G$ ranging over generators of $J$ generates the
relations.

When $J = (F)$, the only relation is $F'(u) \cdot dt = u' \cdot dt$. So $\Omega^{1}_{B/A} = B / u' B$. The annihilator
$\mathfrak{d}_{B/A}$ is then exactly $u' B$.

When $J \supsetneq (F)$, there are additional relations, so $\mathfrak{d}_{B/A}$ is larger. In any case
$u' B \subseteq \mathfrak{d}_{B/A}$. The proposition follows.

### Comment on order

The source notes that "I.7.2 should be made the proposition and I.7.1 the corollary." We follow that logic in spirit.

### Corollary

<!-- source: I.7.3 -->

_This result says: for $B = A[t]/F$ with $F$ monic, étaleness at a prime is exactly nonvanishing of `F'(u)` there._

**Corollary I.7.3.** Under the hypotheses of I.7.1, suppose $F$ is **monic** and $A[t]/FA[t] \to B$ is an
**isomorphism**. Then $B_{\mathfrak{q}}$ is **étale** over $A_{\mathfrak{p}}$ iff $\mathfrak{q} \nsupseteq u'$.

### Proof

$B = A[t]/F$ is free of rank `deg F` over $A$ (monic polynomial), hence flat. Étale = flat + net; the net condition is
just "$u'$ is a unit at $\mathfrak{q}$," which is $\mathfrak{q} \nsupseteq u'$.

### Corollary

<!-- source: I.7.4 -->

_This result says: $B = A[t]/F$ is étale over $A$ iff $F$ and $F'$ generate the unit ideal in `A[t]`._

**Corollary I.7.4.** Under the hypotheses of I.7.3, $B$ is **étale** over $A$ iff $u'$ is **invertible** in $B$,
equivalently iff the ideal $(F, F')$ in `A[t]` is the **unit ideal**.

### Proof

The first criterion is just I.7.3 globally. For the second: if $(F, F') = A[t]$, write $1 = aF + bF'$ in `A[t]`;
reducing mod $F$ gives $1 \equiv b F' mod F$ in $B$, so $F'(u)$ is a unit. The reverse implication is by Nakayama in
$B$.

### Definition (separable polynomial)

A monic polynomial $F \in A[t]$ is called **separable** if $(F, F') = A[t]$. Equivalently, $F$ is monic and $A[t]/F$ is
étale over $A$.

For a non-monic polynomial, one would also need the leading coefficient to be invertible. Over a field, this matches the
usual definition of a separable polynomial.

### Corollary

<!-- source: I.7.5 -->

_This result says: under an infinite-residue-field or local-fiber hypothesis, every net (étale) finite $A$-algebra is a
quotient of, respectively isomorphic to, $A[t]/F$ for a monic separable $F$._

**Corollary I.7.5.** Let $B$ be a finite $A$-algebra over a local ring $A$. Suppose either:

- $K(A) = A/\mathfrak{m}$ is infinite, or
- $B$ is local.

Let $n = rk_{K}(A)(B \otimes_{A} K(A))$ = rank of the fiber. Then $B$ is **net**, respectively **étale**, over $A$ iff
$B$ is isomorphic to a quotient of, respectively isomorphic to, $A[t]/FA[t]$ for a monic separable polynomial $F$ (which
may be taken, respectively must be, of degree $n$).

### Proof of necessity

Net ⟹ $B/\mathfrak{m}B = L$ is a finite separable algebra over $k = A/\mathfrak{m}$. By the hypothesis ($k$ infinite or
$L$ local), there is a generator $\xi \in L$, so the powers $\xi^{i}$ for $0 \leq i < n$ form a basis of $L$ over $k$.
Lift $\xi$ to $u \in B$. By Nakayama, $u^{i}$ for $0 \leq i < n$ generate $B$ as an $A$-module (and form a basis when
$B$ is étale, since $B$ is then free of rank $n$).

So there exists a monic $F \in A[t]$ of degree $n$ with $F(u) = 0$, and $B$ is a quotient of $A[t]/FA[t]$ (or equal, for
the étale case). Apply I.7.4 to $L = k[t]/\bar{F}$: $(\bar{F}, \bar{F}')$ generates `k[t]`, so by Nakayama in
$A[t]/FA[t]$, $(F, F')$ generates `A[t]`. Hence $F$ is separable.

### Theorem

<!-- source: I.7.6 -->

*This result says: every essentially-of-finite-type net local algebra over $A$ is, up to localization, of the standard
form $(A[t]/F)*\mathfrak{n}$for a monic$F$with$F'(u) \notin \mathfrak{n}$.*

**Theorem I.7.6.** Let $A$ be a noetherian local ring, and let $A \to \mathcal{O}$ be a local homomorphism with
$\mathcal{O}$ a localization of an $A$-algebra of finite type. Suppose $\mathcal{O}$ is **net** over $A$. Then there
exist:

- a finite $A$-algebra $B$,
- a maximal ideal $\mathfrak{n} \subset B$,
- a generator $u \in B$ of $B$ over $A$,
- a monic polynomial $F \in A[t]$ with $F(u) = 0$,

such that $\mathfrak{n} \nsupseteq F'(u)$ and $\mathcal{O} \simeq B_{\mathfrak{n}}$ as $A$-algebras.

If additionally $\mathcal{O}$ is **étale** over $A$, one can take $B = A[t]/FA[t]$.

### Proof

We use [Zariski's Main Theorem](appendix-black-boxes.md#zmt): a quasi-finite morphism of finite type is locally an open
immersion into a finite cover. Net implies quasi-finite, so we may write $\mathcal{O} = B_{\mathfrak{n}}$ with $B$
finite over $A$ and $\mathfrak{n}$ a maximal ideal of $B$.

Now $B/\mathfrak{n} = \kappa(\mathcal{O})$ is a separable extension of $k = A/\mathfrak{m}$, hence generated by a single
element. Choose a generator $u \in B$ whose class in $B/\mathfrak{n}$ is a generator and which lies in every other
maximal ideal of $B$.

Two lemmas finish the argument.

#### Lemma

<!-- source: I.7.9 -->

*This result says: an algebraic step in the proof of I.7.6 — the canonical map $B'_{\mathfrak{n}'} \to B*\mathfrak{n}$is
an isomorphism for a suitably chosen generator$u$.*

**Lemma I.7.9.** With $u \in B$ as above, set $B' = A[u] \subseteq B$ and $\mathfrak{n}' = \mathfrak{n} \cap B'$. Then
$B'_{\mathfrak{n}'} \to B_{\mathfrak{n}}$ is an **isomorphism**.

#### Proof of I.7.9

Let $S = B - \mathfrak{n}$, $S' = B' - \mathfrak{n}'$. The localization $B_{\mathfrak{n}} = BS^{-1}$ is finite over
$B'_{\mathfrak{n}'} = B' S'^{-1}$ (since $B$ is finite over $B' = A[u]$). We must show every element of $S$ is
invertible in $B_{S'^{-1}}$, or equivalently every prime of $B_{S'^{-1}}$ lies above $\mathfrak{n}$.

Let $\mathfrak{p} \subset B_{S'^{-1}}$ be a prime. Its contraction to $B'_{\mathfrak{n}'}$ is the unique maximal ideal
$\mathfrak{n}' B'_{\mathfrak{n}'}$, so its contraction to $B'$ is $\mathfrak{n}'$. Its contraction to $B$ is a prime
above $\mathfrak{n}'$. Among maximal ideals of $B$ above $\mathfrak{n}'$, $\mathfrak{n}$ is the only one that does not
contain $u$ (by our choice of $u$). So the contraction is $\mathfrak{n}$.

This shows $B_{S'^{-1}} = B_{\mathfrak{n}} = B'_{\mathfrak{n}'}$. (One last sublemma uses Nakayama in
$B_{\mathfrak{n}} / \mathfrak{n}' \cdot B_{\mathfrak{n}}$, which is generated over $k$ by $u$, to confirm
$B_{\mathfrak{n}} \subseteq B'_{\mathfrak{n}'}$.) Done.

#### Lemma

<!-- source: I.7.10 -->

_This result says: under the unramified hypothesis, one can always find a monic polynomial annihilating $u$ with
$F'(u) \notin \mathfrak{n}$._

**Lemma I.7.10.** Let $B$ be a finite $A$-algebra generated by $u$, and let $\mathfrak{n}$ be a maximal ideal of $B$
such that $B_{\mathfrak{n}}$ is unramified over $A$. Then there exists a monic polynomial $F \in A[t]$ with $F(u) = 0$
and $F'(u) \notin \mathfrak{n}$.

#### Proof of I.7.10

Let $n = rk_{k}(B \otimes_{A} k)$. By Nakayama, there is a monic $F \in A[t]$ of degree $n$ with $F(u) = 0$. Reduce:
$f = F mod \mathfrak{m} \in k[t]$. Then $L = B \otimes_{A} k = k[t]/f$. By I.7.3 applied to $L/k$, the residue condition
$\mathfrak{n}_{L} \nsupseteq f'(\xi)$ (where $\xi = t mod f$) becomes $f'(\xi) \notin \mathfrak{n}_{L}$. Since $f'(\xi)$
is the image of $F'(u)$ in $L$, we have $F'(u) \notin \mathfrak{n}$. Done.

#### Combining

Combining I.7.9 and I.7.10 gives I.7.6 in the net case. The étale case requires $B = A[t]/FA[t]$ (not merely a
quotient): apply I.7.7 below to upgrade.

### Corollary

<!-- source: I.7.7 -->

_This result says: net = quotient of an étale local algebra._

**Corollary I.7.7.** $\mathcal{O}$ is **net** over $A$ iff $\mathcal{O}$ is a **quotient** of an étale local algebra
over $A$.

### Proof

$\mathcal{O} = B_{\mathfrak{n}}$ with the data of I.7.6. Set $\mathcal{O}' = B'_{\mathfrak{n}'}$ where $B' = A[t]/FA[t]$
and $\mathfrak{n}' = \mathfrak{n} \cap B'$. By the rules above, $\mathcal{O}'$ is étale over $A$, and the natural
surjection $\mathcal{O}' \twoheadrightarrow \mathcal{O}$ does the job.

### Corollary

<!-- source: I.7.8 -->

_This result says: geometrically, net = closed immersion into étale, locally._

**Corollary I.7.8.** Let $f : X \to Y$ be a morphism of finite type, and $x \in X$. Then $f$ is **net** at $x$ iff there
exist:

- an open neighborhood $U$ of $x$,
- a factorization $U \to X' \to Y$,

where $U \to X'$ is a **closed immersion** and $X' \to Y$ is **étale**.

### Proof

This is the geometric form of I.7.7. A net morphism factors locally through an étale one, by closed immersion.

### Comment on the étale case

The source then notes: in the étale case of I.7.6, the surjection $\mathcal{O}' \to \mathcal{O}$ of I.7.7 between two
étale $A$-algebras is **étale** by I.4.8 (étale + net = étale), and étale + surjective is an **isomorphism**. So
$\mathcal{O} = \mathcal{O}' = (A[t]/F)_{(F')}$.

### Remark

The source closes section I.7 with a pointer toward generalizing Theorem I.7.6 to **semilocal** rings. We do not need
this generalization.

### What to remember

Every étale local algebra essentially of finite type (= a localization of an $A$-algebra of finite type; see glossary)
over a noetherian local ring $A$ is, up to localization, of the form $A[t]/F$ with $F$ monic and $F'$ a unit in the
localization. This is the algebraic inverse function theorem.

The criterion for $B = A[t]/F$ to be étale over $A$ is $(F, F') = A[t]$. The proof uses
[Zariski's Main Theorem](appendix-black-boxes.md#zmt).

## I.8 Infinitesimal lifting and formal schemes

<!-- source: I.8 -->

I.7.6 gave the local model. Section I.8 turns it into existence. Given a nilpotent thickening $Y_{0} \hookrightarrow Y$
and an étale $Y_{0}$-scheme $X_{0}$, we **construct** an étale $Y$-scheme $X$ lifting $X_{0}$. Combined with the
uniqueness of I.5.5, this is the **equivalence of categories** between étale $Y$-schemes and étale $Y_{0}$-schemes.

Proposition I.8.1 is the local construction. Theorem I.8.3 glues it into a global one. Corollary I.8.4 is the
formal-scheme version.

### Proposition

<!-- source: I.8.1 -->

_This result says: an étale $Y_{0}$-scheme lifts locally to an étale $Y$-scheme._

**Proposition I.8.1.** Let $Y$ be a prescheme, $Y_{0} \subseteq Y$ a closed subprescheme with the same underlying space,
and let $X_{0}$ be an étale $Y_{0}$-scheme. Let $x \in X_{0}$. Then there exist:

- an étale $Y$-scheme $X$,
- a neighborhood $U_{0}$ of $x$ in $X_{0}$,
- a $Y_{0}$-isomorphism $U_{0} \simeq X \times_{Y} Y_{0}$.

### Proof

Let $y \in Y_{0}$ be the image of $x$, and let $A_{0} \to B_{0}$ be the local homomorphism
$\mathcal{O}_{Y_{0}, y} \to \mathcal{O}_{X_{0}, x}$. By theorem I.7.6 applied to the étale local homomorphism
$A_{0} \to B_{0}$, write

```text
B₀ = (C₀)_{𝔫₀},    C₀ = A₀[t]/F₀ A₀[t],
```

with $F_{0} \in A_{0}[t]$ monic and $\mathfrak{n}_{0} \subseteq C_{0}$ a maximal ideal not containing $F_{0}'(t)$ mod
$C_{0}$.

Now lift to $Y$. Let $A = \mathcal{O}_{Y, y}$. Lift $F_{0}$ to a monic $F \in A[t]$ (possible because $A \to A_{0}$ is
surjective and $F_{0}$ is monic). Set $C = A[t]/FA[t]$, and let $\mathfrak{n} \subset C$ be the inverse image of
$\mathfrak{n}_{0}$ under the surjection $C \to C \otimes_{A} A_{0} = C_{0}$. Set $B = C_{\mathfrak{n}}$.

By construction and proposition I.7.1 (alternatively the étale criterion I.7.4), $B$ is étale over $A$. By construction,
$B \otimes_{A} A_{0} \simeq B_{0}$.

Globalize: there exists a $Y$-scheme $X$ of finite type and a point $z \in X$ over $y$ with $\mathcal{O}_{z} \simeq B$
as $A$-algebras (this uses the gluing of EGA Chapter I). Shrinking $X$, we may assume $X$ is étale over $Y$. Then
$X'_{0} := X \times_{Y} Y_{0}$ has local ring at $z$ equal to $B \otimes_{A} A_{0} = B_{0}$, isomorphic to
$\mathcal{O}_{X_{0}, x}$. The isomorphism extends to a neighborhood $U_{0}$ of $x$ in $X_{0}$ mapping isomorphically to
a neighborhood of $z$ in $X'_{0}$. Shrinking again, we may assume the neighborhood is all of $X'_{0}$. Done.

### Corollary

<!-- source: I.8.2 -->

_This result says: the same lifting holds for étale coverings, under the additional hypothesis that the residue field is
infinite._

**Corollary I.8.2.** The analogous statement for **étale coverings** holds, with the additional hypothesis that the
residue field $\kappa(y)$ is **infinite**.

### Proof

The proof is the same, with corollary I.7.5 replacing theorem I.7.6. The infinite-residue-field hypothesis is what
allows I.7.5 to give a single generator.

### Theorem

<!-- source: I.8.3 -->

_This result says: the restriction functor from étale $Y$-schemes to étale $Y_{0}$-schemes is an equivalence of
categories — étale geometry is completely insensitive to nilpotent thickenings._

**Theorem I.8.3.** The functor

```text
{ étale Y-schemes } → { étale Y₀-schemes },    X ↦ X ×_Y Y₀
```

is an **equivalence of categories**.

### Proof

By theorem I.5.5, the functor is fully faithful. We must show essential surjectivity: every étale $Y_{0}$-scheme $X_{0}$
is of the form $X \times_{Y} Y_{0}$ for some étale $Y$-scheme $X$.

The underlying topological space of $X$ must equal that of $X_{0}$ (since $Y_{0}$ and $Y$ have the same underlying
space). So we are seeking a sheaf of $\mathcal{O}_{Y}$-algebras on $|X_{0}|$ extending the structure sheaf of $X_{0}$.

Equivalently, we want, on $|X_{0}|$, a sheaf of algebras $\mathcal{O}_{X}$ over `f₀⁎(𝒪_Y)`, where
$f_{0} : X_{0} \to Y_{0}$ is the projection regarded as a continuous map of underlying spaces, together with a
homomorphism $\mathcal{O}_{X} \to \mathcal{O}_{X_{0}}$ compatible with `f₀⁎(𝒪_Y) → f₀⁎(𝒪_{Y₀})` and inducing an
isomorphism

```text
𝒪_X ⊗_{f₀⁎(𝒪_Y)} f₀⁎(𝒪_{Y₀}) ≃ 𝒪_{X₀}.
```

Now the existence is **local**: by proposition I.8.1, around any point of $X_{0}$ we can find a local solution.

The local solutions glue. The gluing data on overlaps is unique by theorem I.5.5 (the uniqueness of liftings in the
étale category). So the local sheaves of algebras patch into a global sheaf, giving the desired étale $Y$-scheme $X$
with $X \times_{Y} Y_{0} = X_{0}$.

$X$ is **separated** over $Y$ because $X_{0}$ is separated over $Y_{0}$ and separation lifts. Done.

### Corollary

<!-- source: I.8.4 -->

_This result says: same equivalence on the formal-scheme level — étale coverings of a formal prescheme are the same data
as étale coverings of its underlying ordinary prescheme._

**Corollary I.8.4.** Let $S$ be a locally noetherian formal prescheme, with ideal of definition $\mathcal{J}$, and let
$S_{0} = (|S|, \mathcal{O}_{S} / \mathcal{J})$ be the underlying ordinary prescheme. Then the functor

```text
𝔛 ↦ 𝔛 ×_S S₀
```

from étale coverings of $S$ to étale coverings of $S_{0}$ is an **equivalence of categories**.

### What is a formal scheme?

A **formal prescheme** with ideal of definition $\mathcal{J}$ is, intuitively, an "infinite nilpotent thickening": the
structure sheaf is the inverse limit of the structure sheaves modulo $\mathcal{J}^{n+1}$.

For us, the relevant statement is:

```text
𝓑 on S = compatible system of 𝓑_n on S_n,
```

where $S_{n} = (|S|, \mathcal{O}_{S} / \mathcal{J}^{n+1})$. The 𝓑_n are linked by

```text
𝓑_m ⊗_{𝒪_{S_m}} 𝒪_{S_n} ≃ 𝓑_n,    m ≥ n.
```

$\mathcal{B}$ is **étale** over $S$ iff every $\mathcal{B}_{n}$ is étale over $S_{n}$. In particular, the étale
condition is determined by the residue level $\mathcal{B}_{0}$.

### Proof of I.8.4

Each step "go from $S_{n}$ to $S_{n+1}$" is a nilpotent thickening, so theorem I.8.3 applies. Compatibility lets us
assemble the sequence into a formal-scheme datum. Done.

### Remark

The source observes that the restriction to **coverings** in I.8.4 is not necessary; the full equivalence of étale
categories holds for general étale $Y$-schemes. We follow the source's restraint.

### What to remember

I.8.3 says étale geometry is **completely insensitive** to nilpotent thickenings. Combined with I.5.5, the two
categories of étale schemes are equivalent. So étale $Y$-schemes are determined by their data on any closed subprescheme
$Y_{0} \subseteq Y$ with the same underlying space — the foundation of the étale-cohomology theory in later exposés,
where étale cohomology of $Y$ and $Y_{red}$ agree.

The rigidity is now proved. The remaining question is what rigidity is _for_. File 12 answers it, in two steps. Section
I.9 shows that étale extensions transfer essentially every classical local property of rings, so the theory keeps the
hypotheses you started with. Sections I.10–I.11 specialize to a normal connected base and identify finite étale covers
with the unramified-over-$Y$ finite separable extensions of the function field — étale geometry over a normal base
becomes the Galois theory of fields.
