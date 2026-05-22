# Exposé I, sections 1–4: étale morphisms (gentle)

## What this file is about

The preceding files explained the algebraic notion of a covering map twice, in a friendly order chosen to keep the
reader oriented. Grothendieck did not write his original lectures in that order. He had a single instrument in mind — an
algebraic calculus of infinitesimal differences between two points lying above the same base point — and he wanted to
lay the instrument out first, all of it, before letting any of the geometry use it. The instrument and the geometry then
unfold together in a tighter, more efficient sequence than the one we used.

This file rewinds and walks through that original sequence at the source's pace. The mathematics is the same as in the
earlier files; the order, the proofs, and the technical bookkeeping are the source's. By the end the algebraic version
of a covering map has been built once, in full, from inside the calculus that made Grothendieck believe in it.

The preparation arc closed by promising that every term Grothendieck uses is on the page. This file cashes the promise.
We revisit the first four sections of Exposé I at the source's pace, with the same theorems and proofs, in the source's
order.

The arc of these four sections is a single argument carried out twice. Section I.1 builds the differential calculus on
which the whole exposé runs: the diagonal of a morphism, its defining ideal, the sheaf $\Omega^{1}_{X/Y}$ of relative
Kähler differentials, and the infinitesimal neighborhoods that record higher-order data. Sections I.2 through I.4 pick
out the morphism classes the differential calculus distinguishes — quasi-finite, unramified (net), flat, and finally
étale — and certify étaleness by an invertibility condition on the discriminant. By the end of the file, étale is a
theorem- proving tool and the discriminant is its testable invariant.

The standing assumption from the source ($I$): **all preschemes are locally noetherian**, at least from section I.2
onward. We also assume separation when the diagonal needs to be a closed immersion; the source mentions this in section
I.1 with the line "a hypothesis that would be farcical here." We take separation as the default and flag exceptions. See
file 03 for the definition.

## I.1 Differential calculus

<!-- source: I.1 -->

The preparation in file 03 staged the algebra of derivations and Kähler differentials; this section translates it into
geometry. The diagonal of a morphism, the ideal that defines it, the sheaf $\Omega^{1}_{X/Y}$ of relative Kähler
differentials, and the infinitesimal neighborhoods all give algebraic access to "first-order infinitesimal differences"
between two points of $X$ lying over the same point of $Y$.

For a morphism $f : X \to Y$, the diagonal $\Delta_{X/Y} : X \to X \times_{Y} X$ is induced by $(id_{X}, id_{X})$. As an
immersion, it identifies $X$ with a closed subscheme of an open subset $V \subset X \times_{Y} X$. The defining ideal
$\mathcal{I}_{X} \subseteq \mathcal{O}_{V}$ of this closed subscheme records "the difference between the two points."
Killing higher-order terms in $\mathcal{I}_{X}$ gives infinitesimal neighborhoods of the diagonal, the scheme-theoretic
carriers of derivative data for $f$.

### The ideal of the diagonal

Given $f : X \to Y$, choose $V \subset X \times_{Y} X$ open such that $\Delta_{X/Y}$ factors as a closed immersion
$X \to V$. Define $\mathcal{I}_{X}$ as the ideal sheaf of this closed subscheme.

The source remarks that if one objects to choosing $V$ (because $X$ is not assumed separated over $Y$), one can do this
intrinsically. Use the augmentation ideal in the inverse image $\Delta^{-1}(\mathcal{O}_{X\times_{Y} X})$. We will not
need this generality; for our standing setting, the choice of $V$ is harmless because two choices give canonically
isomorphic data on $X$.

### Sheaves of relative differentials

The sheaf

$$
\Omega^{1}_{X/Y} := \mathcal{I}_{X} / \mathcal{I}^{2}_{X}
$$

is a quasi-coherent sheaf on $X$. It is **of finite type** if the morphism $f : X \to Y$ is of finite type. It is
**stable under base change**: for $Y' \to Y$ and $X' = X \times_{Y} Y'$, the natural map
$\Omega^{1}_{X/Y} \otimes \mathcal{O}_{X'} \to \Omega^{1}_{X'/Y'}$ is an isomorphism.

The algebraic version (file 03): for $\operatorname{Spec} B \to \operatorname{Spec} A$,
$\Omega^{1}_{B/A} = \ker(\mu)/\ker(\mu)^{2}$ where $\mu : B \otimes_{A} B \to B$ is multiplication. It represents the
functor $M \mapsto \operatorname{Der}_{A}(B, M)$ on $B$-modules.

### Infinitesimal neighborhoods

For $n \geq 0$, define

```text
𝓟ⁿ_{X/Y} := 𝒪_{X ×_Y X} / 𝓘_X^{n+1}.
```

This is a sheaf of rings on $X$ (after pushing forward along the diagonal). It defines a prescheme structure on the
underlying space of $X$, denoted $\Delta^{n}_{X/Y}$ and called the **$n$-th infinitesimal neighborhood** of $X$ in
$X \times_{Y} X$.

For $n = 0$ we recover $X$ itself. For $n = 1$ we get the **first infinitesimal neighborhood**, which carries
$\Omega^{1}_{X/Y}$ as a quotient.

### Comment on style

The source describes the bookkeeping of these constructions as "of total triviality, although rather long" and indicates
that they are worth developing only when one has something useful to say. We agree. The actual use of $\Omega^{1}_{X/Y}$
in this exposé is in section I.3 (the differential criterion of unramifiedness). Higher neighborhoods do not return
until later in SGA, where smooth morphisms appear.

### What to remember

The diagonal $\Delta_{X/Y}$ measures "two points equal." Its defining ideal $\mathcal{I}_{X}$ and the quotient
$\Omega^{1}_{X/Y} = \mathcal{I}_{X} / \mathcal{I}^{2}_{X}$ carry the first-order infinitesimal data of $f : X \to Y$.
Algebraically, $\Omega^{1}_{X/Y}$ is the universal target of $A$-derivations of $B$. We will use it in section I.3 to
define unramifiedness.

## I.2 Quasi-finite morphisms

<!-- source: I.2 -->

The differential calculus of I.1 is in place; this section opens the morphism-class arc with the loosest finite-fiber
condition. Quasi-finiteness says that, near a chosen point of $X$, the fiber over the image point is finite as a
topological space. Algebraically, the local ring of $X$ at that point is finite over the local ring of $Y$ at the image
once we pass to completions.

### The proposition

<!-- source: I.2.1 -->

_This result says: three different finiteness conditions on the fiber — its dimension as a residue-field algebra, the
ideal-theoretic structure of $B$, and the size after completion — are equivalent._

**Proposition I.2.1.** Let $A \to B$ be a local homomorphism of noetherian local rings, with $\mathfrak{m} \subset A$
the maximal ideal. The following are equivalent.

1. $B/\mathfrak{m}B$ is finite-dimensional over $k = A/\mathfrak{m}$.
1. $\mathfrak{m}B$ is an ideal of definition of $B$, and $\kappa(B)/\kappa(A)$ is a field extension.
1. The completion $\hat{B}$ is finite over the completion `Â`.

When these hold, $B$ is **quasi-finite** over $A$.

### What it means

Condition (i) says: the fiber $B \otimes_{A} k = B/\mathfrak{m}B$, viewed as a $k$-algebra, has finite vector-space
dimension. This is the "finite fiber" condition.

Condition (ii) gives the same content in two pieces: a power of the maximal ideal $\mathfrak{n}$ of $B$ lies in
$\mathfrak{m}B$ (so $\mathfrak{m}B$ is $\mathfrak{n}$-primary), and the residue field is a single field extension (so
the zero-dimensional fiber is local).

Condition (iii) is the completion form: quasi-finite becomes finite after completing. Many later arguments pass to
completions for exactly this reason.

### Sketch of equivalence

(i) ⟹ (iii): A noetherian local ring $B/\mathfrak{m}B$ finite-dimensional over $k$ has only finitely many prime ideals
(artinian quotient of $B$), all of which lie above $\mathfrak{m}$. The completion $\hat{B}$ is finite over `Â` because,
modulo $\mathfrak{m}\hat{A}$, it is $B/\mathfrak{m}B$ and we can lift generators.

(iii) ⟹ (i): If $\hat{B}$ is finite over `Â`, then
$\hat{B}/\mathfrak{m}\hat{B} = \hat{B} \otimes_{\hat{A}} (\hat{A}/\mathfrak{m}\hat{A}) = (B/\mathfrak{m}B) \otimes_{k} k = B/\mathfrak{m}B$
is finite over $k$.

(i) ⟺ (ii): The fiber $B/\mathfrak{m}B$ is a noetherian ring of dimension zero (so $\mathfrak{m}B$ is
$\mathfrak{n}$-primary) and finite-dimensional over $k$. It is local iff its only maximal ideal is $\mathfrak{n}$, iff
$\kappa(B)/\kappa(A)$ is a single extension.

### Geometric definition

A morphism $f : X \to Y$ is **quasi-finite at $x$** if $\mathcal{O}_{x}$ is quasi-finite over $\mathcal{O}_{f(x)}$.
Equivalently, **$x$ is isolated in its fiber** $f^{-1}(f(x))$.

$f$ is **quasi-finite** if it is so at every point.

The source notes that EGA II 6.2.3 imposes the additional hypothesis that $f$ be of finite type. We follow the source's
looser convention here.

### Corollary

<!-- source: I.2.2 -->

_This result says: completeness of the base collapses quasi-finite to finite._

**Corollary I.2.2.** If $A$ is **complete**, then quasi-finite is equivalent to **finite**.

### Why this is true

If $A$ is complete and $B$ is quasi-finite over $A$, then $\hat{B}$ is finite over $A$. But $B \to \hat{B}$ need not be
a priori finite. The trick is that $A$ complete and $B$ quasi-finite force $B = \hat{B}$: any $b \in \hat{B}$ is a
finite $A$-linear combination of elements of $B/\mathfrak{m}B$, lifted; complete-faithfully-flat descent identifies
$\hat{B}$ with $B$. (More carefully: complete local ring + finite module gives a complete module, which equals $B$. We
treat this as a small black box.)

### Example

$A = \mathbb{Z}[t]/(t^{2} + 1)$ and $B = \mathbb{Z}[t]/(t^{2} + 1)$ localized at $(t + 1, 2)$. The map $A \to B$ is
local and quasi-finite over the maximal ideal `(2)`, but $B$ is not finite over $A$ (the localization is not finite).
After completing $A$ at `(2)`, however, the local homomorphism becomes finite.

### Comment

The source remarks that one could give the standard sorites for quasi-finite morphisms — composition, base change, etc.
— but that this seems unnecessary. We follow the same restraint.

### What to remember

Quasi-finite = isolated fiber = finite-dimensional fiber algebra. Becomes finite after completion. This is the loosest
finite-fiber condition; we strengthen it with "unramified" in the next section.

## I.3 Unramified or net morphisms

<!-- source: I.3 -->

Quasi-finite from I.2 controls the size of the fiber; this section controls its infinitesimal shape. Unramifiedness,
called **net** in the source, is the algebraic counterpart of "no first-order infinitesimal directions in the fibers."
Three formulations of the same condition appear: a fiber criterion, a differential criterion, and a diagonal criterion.
The proposition below states their equivalence.

### The proposition

<!-- source: I.3.1 -->

_This result says: "unramified" has three equivalent forms — a fiber criterion (separable residue extension), a
differential criterion ($\Omega^{1} = 0$), and a diagonal criterion (the diagonal is locally an open immersion)._

**Proposition I.3.1.** Let $f : X \to Y$ be a morphism of finite type, let $x \in X$, and let $y = f(x)$. The following
are equivalent.

1. $\mathcal{O}_{x} / \mathfrak{m}_{y} \cdot \mathcal{O}_{x}$ is a finite separable extension of $\kappa(y)$.
1. $\Omega^{1}_{X/Y}$ vanishes at $x$.
1. The diagonal $\Delta_{X/Y}$ is an open immersion in a neighborhood of $x$.

### Proof

**(i) ⟹ (ii)**. By Nakayama, we may pass to the fiber, reducing to the case $Y = \operatorname{Spec} k$ and
$X = \operatorname{Spec} k'$ for a finite separable extension $k'/k$. Then $\Omega^{1}_{k'/k} = 0$ follows from the
well-known fact that a finite separable extension has zero module of Kähler differentials. (Algebraic check:
$k' = k(\alpha)$ with minimal polynomial $F$, so
$\Omega^{1}_{k'/k} = k' \cdot d\alpha / F'(\alpha) \cdot k' \cdot d\alpha = 0$ since $F'(\alpha) \neq 0$ by
separability.)

**(ii) ⟹ (iii)**. We use a characterization of open immersions: a morphism of finite type is an open immersion if and
only if it is unramified, flat, and induces an isomorphism on residue fields, plus a Krull-style local check. The
vanishing of the relative differentials of the diagonal at $x$ means the second projection $X \times_{Y} X \to X$ is
unramified at $\Delta(x)$ over the first projection. A short argument with
[Krull's intersection theorem](appendix-black-boxes.md#krull-intersection) then upgrades this to: the diagonal is
locally an open immersion. The source calls this characterization "pleasant and easy."

**(iii) ⟹ (i)**. Reduce again to $Y = \operatorname{Spec} k$. Then the diagonal $X \to X \times_{k} X$ is everywhere an
open immersion. Pass to algebraic closure; we may assume $k$ algebraically closed. Every closed point of $X$ is then
isolated, since under the morphism $X \to X \times_{k} X$, $x \mapsto (x, x)$, the closed point $x$ is identified with
its inverse image of the diagonal. So $X$ is finite. Reducing further, suppose $X = \operatorname{Spec} A$ is one point.
The map $A \otimes_{k} A \to A$ is an isomorphism, which forces $A = k$. So $X$ is finite separable over $k$.

### Definition

<!-- source: I.3.2 -->

**Definition I.3.2.**

1. A morphism $f : X \to Y$ of finite type is **net at $x$**, or **unramified at $x$**, if conditions (i)–(iii) of
   proposition I.3.1 hold.
1. A local homomorphism $A \to B$ of noetherian local rings is **net** or **unramified** if
   $\mathfrak{r}(A) \cdot B = \mathfrak{r}(B)$ and $\kappa(B)/\kappa(A)$ is finite separable.

The notation $\mathfrak{r}(A)$ denotes the maximal ideal of a noetherian local ring $A$. We use $\mathfrak{m}_{A}$
interchangeably.

### Remarks

**Recognition on completions.** The source observes that "$B$ net over $A$" is detectable on completions: $B/A$ is net
iff $\hat{B}/\hat{A}$ is net. The proof: the conditions involve $\mathfrak{m}_{A} B$, the residue extension, and finite
separability — all of which descend to or reflect from completions.

**Net implies quasi-finite.** A separable field extension is finite, so $B/\mathfrak{m}_{A} B$ is finite-dimensional
over $\kappa(A)$, that is, quasi-finite.

### Corollary

<!-- source: I.3.3 -->

_This result says: unramifiedness is an open condition on the source._

**Corollary I.3.3.** The set of points where $f$ is net is open in $X$.

### Proof

Each of conditions (i), (ii), (iii) of proposition I.3.1 is open in $x$. For (ii), the support of $\Omega^{1}_{X/Y}$ is
closed, so its complement (where the sheaf vanishes) is open. The corollary follows.

### Corollary

<!-- source: I.3.4 -->

_This result says: the graph of any $Y$-morphism into an unramified $Y$-scheme is automatically an open immersion._

**Corollary I.3.4.** Let $X'$ and $X$ be of finite type over $Y$, and let $g : X' \to X$ be a $Y$-morphism. If $X$ is
net over $Y$, then the graph morphism

```text
Γ_g : X′ → X ×_Y X
```

is an open immersion.

### Proof

The graph $\Gamma_{g}$ is the inverse image of the diagonal $\Delta_{X/Y}$ under
$g \times_{Y} id_{X'} : X' \times_{Y} X \to X \times_{Y} X$. Since $X/Y$ is net, $\Delta_{X/Y}$ is locally an open
immersion (proposition I.3.1 (iii)). The pullback of an open immersion along any morphism is an open immersion. The
result follows.

### The different ideal

The source defines the **annihilator ideal**

$$
\mathfrak{d}_{X/Y} := Ann(\Omega^{1}_{X/Y}) \subset \mathcal{O}_{X}.
$$

This is the **different ideal** of $X/Y$. It defines a closed subscheme of $X$, set-theoretically equal to the locus
where $X/Y$ is **ramified** — that is, **not net**.

### Sorites

<!-- source: I.3.5 -->

_This result says: immersions are net, and netness is preserved by composition and base change._

**Proposition I.3.5.**

1. An immersion (open or closed) is net.
1. The composition of two net morphisms is net.
1. A base extension of a net morphism is net.

### Proof

For (i): for an immersion, $\mathcal{O}_{x} = \mathcal{O}_{y} / I$ and $\mathfrak{m}_{x} = \mathfrak{m}_{y} / I$, so
$\mathfrak{m}_{y} \cdot \mathcal{O}_{x} = \mathfrak{m}_{x}$ and the residue extension is the identity.

For (ii) and (iii): the diagonal criterion (iii) of proposition I.3.1 makes both immediate, by chasing pullback
diagrams.

The source remarks that one could be more precise pointwise; this is "only apparently more general" and tedious. We
agree.

### Corollaries

<!-- source: I.3.6 -->

_This result says: cartesian products, factor maps of a net composite, and reduction all preserve netness._

**Corollaries I.3.6.**

1. The cartesian product of two net morphisms is net.
1. If $g \circ f$ is net, then $f$ is net.
1. If $f$ is net, then `f_red : X_red → Y_red` is net.

These follow formally from proposition I.3.5 and standard sorites.

### Proposition

<!-- source: I.3.7 -->

_This result says: under a trivial-residue or algebraically-closed-residue hypothesis, netness is equivalent to
$\hat{B}$ being a quotient of `Â`._

**Proposition I.3.7.** Let $A \to B$ be a local homomorphism, and suppose either:

- the residue extension $\kappa(B)/\kappa(A)$ is trivial, or
- $\kappa(A)$ is algebraically closed.

Then $B/A$ is net iff $\hat{B}$ is, as an `Â`-algebra, a **quotient** of `Â`.

### Proof sketch

Net implies $\mathfrak{m}_{A} B = \mathfrak{m}_{B}$, and the residue extension is trivial or comes from algebraic
closure. Combining with completeness of `Â`, the structure map $\hat{A} \to \hat{B}$ is surjective: any element of
$\hat{B}$ is in the image plus higher-order error, and completeness lets us correct.

For the converse: if $\hat{B}$ is a quotient of `Â`, then $\hat{B}$ is local artinian or local noetherian quotient, and
the maximal ideal is generated by the image of $\mathfrak{m}_{A}$. Combined with the trivial residue extension, this
gives netness.

### Remarks

**Reduction to trivial residue extension.** When the residue extension is not trivial, one can reduce to that case by
making a suitable finite flat extension over $A$ that kills the residue extension.

**Counterexample.** The source offers an instructive example. Let $A$ be the local ring of an ordinary double point of a
curve, and $B$ the local ring of a point of the normalization above it. Then $A \subset B$, $B$ is net over $A$ with
trivial residue extension, and $\hat{A} \to \hat{B}$ is **surjective but not injective**. So the literal inclusion
$\hat{A} \subset \hat{B}$ is not preserved.

This is the kind of example that motivates section I.11.

### Strengthening

The source closes section I.3 by saying "we shall therefore strengthen the notion of netness." The strengthening is the
addition of **flatness**, giving étale.

### What to remember

Net = unramified = no first-order infinitesimal directions in the fibers. Three equivalent forms: fiber criterion
(separable extension), differential criterion ($\Omega^{1} = 0$), diagonal criterion (diagonal is open immersion). Net
implies quasi-finite. Net is preserved by composition, base change, products. Net is detected on completions. The locus
of netness is open. The annihilator of $\Omega^{1}_{X/Y}$ is the **different**, cutting out the ramified locus.

## I.4 Étale morphisms and étale coverings

<!-- source: I.4 -->

Unramified plus a flatness theory closes the early arc. Étale = flat + net. The combination is so well behaved under
base change, composition, products, and openness that it deserves its own name. This section also introduces **finite
étale coverings** as the algebraic analogue of finite covering spaces, and gives the **discriminant criterion** for a
finite locally free morphism to be étale.

The source admits all needed flatness facts — composition, base change, openness of the flat locus, faithful flatness of
completion — as black boxes, referring to Exposé IV. We do the same; see the
[flatness sorites](appendix-black-boxes.md#flatness-sorites) and
[faithful flatness of completion](appendix-black-boxes.md#completion-flat) in the appendix.

### Definition

<!-- source: I.4.1 -->

**Definition I.4.1.**

1. A morphism $f : X \to Y$ of finite type is **étale at $x$** if $f$ is **flat at $x$** and **net at $x$**. It is
   **étale** if it is so at every point.
1. A local homomorphism $A \to B$ is **étale**, or $B$ is **étale over $A$**, if $B$ is **flat** and **net** over $A$.

### Proposition

<!-- source: I.4.2 -->

_This result says: étaleness is preserved and reflected by passing to completions._

**Proposition I.4.2.** $B/A$ is étale iff $\hat{B}/\hat{A}$ is étale.

### Proof

Both flat and net descend to and from completions. The result follows.

### Corollary

<!-- source: I.4.3 -->

_This result says: étaleness at a point depends only on the induced local ring map, even only on its completion._

**Corollary I.4.3.** Let $f : X \to Y$ be of finite type. The condition that $f$ is étale at $x$ depends only on the
local homomorphism $\mathcal{O}_{y} \to \mathcal{O}_{x}$, and even only on the corresponding homomorphism of
completions.

### Corollary

<!-- source: I.4.4 -->

_This result says: under a trivial-residue or algebraically-closed-residue hypothesis, étaleness is equivalent to
$\hat{A} \to \hat{B}$ being an isomorphism._

**Corollary I.4.4.** Suppose the residue extension $\kappa(A) \to \kappa(B)$ is **trivial**, or that $\kappa(A)$ is
**algebraically closed**. Then $B/A$ is étale iff $\hat{A} \to \hat{B}$ is an **isomorphism**.

### Proof

Combine flatness with proposition I.3.7. Net under those hypotheses makes $\hat{A} \to \hat{B}$ surjective; flat (or
rather faithfully flat in this local setting) makes it injective. So it is an isomorphism.

### Proposition

<!-- source: I.4.5 -->

_This result says: the étale locus of a morphism of finite type is open in the source._

**Proposition I.4.5.** Let $f : X \to Y$ be of finite type. The set of points where $f$ is étale is open in $X$.

### Proof

The locus where $f$ is flat is open (a basic theorem about flat morphisms of finite type; see
[`flatness-sorites`](appendix-black-boxes.md#flatness-sorites)). The locus where $f$ is net is open (corollary I.3.3).
The intersection is open.

### Comment

So "étale at $x$" upgrades to "étale on a neighborhood of $x$." Pointwise language is unnecessary for finite-type
morphisms étale at some point.

### Sorites

<!-- source: I.4.6 -->

_This result says: open immersions are étale, and étaleness is preserved by composition and base change._

**Proposition I.4.6.**

1. An open immersion is étale.
1. The composition of two étale morphisms is étale.
1. The base change of an étale morphism is étale.

### Proof

(i) is trivial. For (ii) and (iii), each property — flat and net — satisfies the analogous statement.

The source notes that there are corresponding statements for local homomorphisms without the finiteness condition; these
"should appear in the multiplodocus, beginning with the net case." We do not need them.

### Corollary

<!-- source: I.4.7 -->

_This result says: cartesian products of étale morphisms are étale._

**Corollary I.4.7.** A cartesian product of two étale morphisms is étale.

### Corollary

<!-- source: I.4.8 -->

_This result says: a $Y$-morphism from an étale $Y$-scheme to an unramified $Y$-scheme is automatically étale._

**Corollary I.4.8.** Let $X$ and $X'$ be of finite type over $Y$, and let $g : X \to X'$ be a $Y$-morphism. If $X'$ is
**net** over $Y$ and $X$ is **étale** over $Y$, then $g$ is **étale**.

### Proof

By corollary I.3.4, the graph morphism $\Gamma_{g} : X \to X \times_{Y} X'$ is an open immersion (because $X'$ is net).
The composition $X \to X \times_{Y} X' \to X'$, where the second map is the projection, gives $g$. The projection
$X \times_{Y} X' \to X'$ is the base change of $X \to Y$ by $X' \to Y$, hence étale. The graph is an open immersion,
hence étale. Composition of étale morphisms is étale.

### Definition

<!-- source: I.4.9 -->

**Definition I.4.9.** An **étale covering**, respectively a **net covering**, of $Y$ is a $Y$-scheme $X$ that is
**finite** over $Y$ and **étale**, respectively **net**, over $Y$.

### What this means

Finite over $Y$ means: $X$ corresponds to a coherent sheaf $\mathcal{B}$ of $\mathcal{O}_{Y}$-algebras. Étale then
means: $\mathcal{B}$ is **locally free** as $\mathcal{O}_{Y}$-module (this is flat + finite + finitely presented), and
for every $y \in Y$, the fiber

```text
𝓑(y) = 𝓑_y ⊗_{𝒪_y} κ(y)
```

is a **separable algebra** over $\kappa(y)$ — that is, a finite product of finite separable field extensions of
$\kappa(y)$.

For "net" the local-freeness is replaced by no condition; the fiber-separability remains.

### Example: trivial covering

For any $Y$, the disjoint union $Y \amalg Y \amalg \cdots \amalg Y$ of $n$ copies of $Y$ is an étale covering of degree
$n$. The corresponding sheaf of algebras is $\mathcal{O}^{n}_{Y}$, the product of $n$ copies of $\mathcal{O}_{Y}$ with
componentwise multiplication. The fiber at every $y$ is $\kappa(y)^{n}$, the trivially split product.

### Example: $\mathbb{Z}[i]$ over $\mathbb{Z}[1/2]$

The morphism $\operatorname{Spec} \mathbb{Z}[i] \to \operatorname{Spec} \mathbb{Z}$, restricted to the open complement
of `(2)`, is a finite étale covering of $\operatorname{Spec} \mathbb{Z}[1/2]$ of degree `2`. Fiber at `(p)` for $p$ odd:
either $\mathbb{F}_{p} \times \mathbb{F}_{p}$ (when $p \equiv 1 mod 4$) or $\mathbb{F}_{p^{2}}$ (when
$p \equiv 3 mod 4$). In both cases a two-element separable algebra.

### Discriminant criterion

<!-- source: I.4.10 -->

_This result says: a flat covering is étale iff its trace pairing is nondegenerate — equivalently, iff its discriminant
ideal is the unit ideal._

**Proposition I.4.10.** Let $X$ be a flat covering of $Y$ of degree $n$, defined by a coherent locally free sheaf
$\mathcal{B}$ of algebras. The **trace** map

```text
tr_{𝓑/𝓐} : 𝓑 → 𝓐 = 𝒪_Y
```

is the homomorphism of $\mathcal{A}$-modules sending $b \in \mathcal{B}$ to the trace of multiplication-by-$b$ as an
$\mathcal{A}$-linear endomorphism of $\mathcal{B}$.

For $X$ to be **étale**, the following are equivalent.

1. The bilinear form $(b, b') \mapsto tr_{\mathcal{B}/\mathcal{A}}(bb')$ defines an isomorphism
   $\mathcal{B} \to \check{\mathcal{B}} := \operatorname{Hom}_{\mathcal{A}}(\mathcal{B}, \mathcal{A})$.

1. The **discriminant section**

    ```text
    d_{X/Y} = d_{𝓑/𝓐} ∈ Γ(Y, ∧ⁿ𝓑̌ ⊗_𝓐 ∧ⁿ𝓑̌)
    ```

    is invertible.

1. The **discriminant ideal** generated by this section is the unit ideal.

### Proof

Reduction to $Y = \operatorname{Spec} k$ for a field $k$: this is the well-known separability criterion. Pass to the
algebraic closure of $k$; over an algebraically closed field, a finite-dimensional commutative algebra is separable iff
it is a product of copies of the field iff the trace pairing is nondegenerate. The result follows.

### Comment

The source notes that there is a less-trivial statement available when $X$ is **not** assumed flat, but $Y$ is
**normal**. We treat this in section I.10.

### What to remember

Étale = flat + net. Open immersions are étale. Composition and base change preserve étale. The étale locus of a
finite-type morphism is open. Étale + net structure on $X'$ implies any $Y$-morphism $X \to X'$ (with $X$ étale over
$Y$) is itself étale.

A **finite étale covering** is a finite morphism whose sheaf of algebras is locally free with separable fibers. The
**discriminant** is invertible iff the covering is étale — the algebraic Galois-theoretic test for étaleness, in the
finite- locally-free setting.

I.1–I.4 closes here. The class of morphisms is named, certified, and stable. The next file asks what an étale morphism
_does_. The answer, across I.5–I.8, is rigidity: an étale morphism plus one extra condition is an open immersion; the
étale category over $Y$ is unchanged by nilpotent thickening of the base; over a complete local ring, finite étale
extensions are determined by the residue field; and every étale local algebra has a single explicit form.
