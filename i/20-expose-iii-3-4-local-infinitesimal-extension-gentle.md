# Exposé III, sections 3–4: local infinitesimal extension (gentle)

## What this file is about

Imagine an algebraic shape sitting over a single point and a slightly thicker point next to it, the thicker point being
the original with an infinitesimal extra layer added. Two questions come up. First, given a map from the slightly
thicker point into another smooth shape, where only the inner part of the map has been specified, can the specification
be extended over the whole thicker point? Second, given the smooth shape itself, but only over the inner point, can the
shape itself be thickened to live over the thicker point and still be smooth?

This file answers both questions locally, meaning on a small enough patch. In each case the answer is yes, and in each
case the answer is not unique. The next two files measure the failure of uniqueness and ask whether the local answers
paste together into a single answer over the whole space.

Section III.1 defined **formally smooth** as a property of local ring maps. Section III.2 gave the equivalent **lifting
characterization**: every algebra map $B \to C / J$ to a quotient by a nilpotent ideal lifts to an algebra map
$B \to C$. We now globalize both pieces to schemes.

The first half of this file (§III.3) turns the lifting characterization into a property of morphisms of finite type. For
a finite-type morphism $f : X \to Y$, smoothness of $f$ is equivalent to the property that **morphisms into $X$ from
infinitesimally thickened sources extend**. In the source's notation: given $Y' \supset Y'_{0}$ a closed sub-prescheme
with the same underlying space, every $Y$-morphism $g_{0} : Y'_{0} \to X$ extends, locally, to a $Y$-morphism
$Y' \to X$.

The second half (§III.4) inverts the question. Given a smooth $Y_{0}$-scheme $X_{0}$, can it be **lifted** to a smooth
$Y$-scheme over a base $Y_{0} \hookrightarrow Y$ with the same underlying space? Locally, yes — Theorem III.4.1.
Globally, the lift is **not canonical**; files 21–22 will show that this non-canonicity is exactly the cohomological
obstruction $H^{1}$ and $H^{2}$.

The slogan that runs through:

> **Smoothness = sections of an infinitesimal thickening always extend.** A finite-type morphism $f : X \to Y$ is smooth
> iff sections of $f$ (or, equivalently, morphisms into $X$) extend from any closed sub-prescheme to the ambient
> prescheme, at least locally on the source. The étale case is the same with uniqueness added.

The new running examples:

- **The affine line $\operatorname{Spec} \mathbb{Z}[t] \to \operatorname{Spec} \mathbb{Z}$**, lifted along the closed
  immersion `Spec ℤ → Spec ℤ → Spec ℤ` (trivial; just to fix vocabulary). Then lifted along
  $\operatorname{Spec} \mathbb{Z} / p^{2} \to \operatorname{Spec} \mathbb{Z}$: the affine line
  $\mathbb{A}^{1}_{\mathbb{Z}/p^{2}}$ is the unique smooth lift of $\mathbb{A}^{1}_{\mathbb{F}_{p}}$.
- **An elliptic curve over $\mathbb{F}_{p}$ lifted to $\mathbb{Z} / p^{2}\mathbb{Z}$** — represented by a Weierstrass
  equation $y^{2} - x^{3} - ax - b$ for $(a, b) \in \mathbb{F}^{2}_{p}$ with $4a^{3} + 27b^{2} \neq 0$. The lift exists
  by III.4.1 once we lift $(a, b)$ arbitrarily to $(\tilde{a}, \tilde{b}) \in (\mathbb{Z}/p^{2})^{2}$ and check the
  discriminant remains a unit; smoothness is preserved by the Jacobian criterion (file 15, II.4.10). The non-canonicity
  (III.4.3) is the freedom in choosing the lifts $(\tilde{a}, \tilde{b})$.

## III.3 Local infinitesimal extension of morphisms into a smooth $S$-scheme

<!-- source: III.3 -->

### Theorem: five equivalent conditions for smoothness

<!-- source: III.3.1 -->

_This theorem says: for a finite-type morphism $f : X \to Y$, smoothness is equivalent to the property that any
$Y$-morphism from a closed subprescheme of a test scheme $Y'$ extends, locally, to a $Y$-morphism from $Y'$ itself. The
five equivalent forms range over choices of test scheme and global vs. local extension._

**Theorem III.3.1.** _Let $f : X \to Y$ be a morphism locally of finite type. The following are equivalent:_

1. _$f$ is smooth._
1. _For every prescheme $Y'$ over $Y$, every closed sub-prescheme $Y'_{0}$ of $Y'$ having the same underlying space as
   $Y'$, every $Y$-morphism $g_{0} : Y'_{0} \to X$, and every $z \in Y'_{0}$, there exists an open neighborhood $U$ of
   $z$ in $Y'$ and an extension $g$ of $g_{0}|_{Y'_{0} \cap U}$to a$Y$-morphism $U \to X$._
1. _For $Y', Y'_{0}, z$ as in (ii), set $X' := X \times_{Y} Y'$ and $X'_{0} := X \times_{Y} Y'_{0}$; every section of
   $X'_{0}$ over $Y'_{0}$ extends to a section of $X'$ over an open neighborhood $U$ of $z$._
1. _For every $Y$-scheme $Y'$ that is the spectrum of a local artinian ring finite over some $\mathcal{O}_{y}$ (with
   $y \in Y$), every nonempty closed sub-prescheme $Y'_{0}$ of $Y'$, and every $Y$-morphism $g_{0} : Y'_{0} \to X$,
   there exists a $Y$-morphism $g : Y' \to X$ extending $g_{0}$._
1. _As (iii), with $Y'$ and $Y'_{0}$ as in (iv) — i.e. with the test scheme being an artinian spectrum — every section
   extends to a section of $X'$ over $Y'$._

**Proof sketch.** The equivalence of (ii) and (ii bis), and of (iii) and (iii bis), is trivial. The implication (ii) ⇒
(iii) is also formal. So we prove (i) ⇒ (ii) and (iii) ⇒ (i).

**$(i) \Rightarrow (ii)$.** Let $x = g_{0}(z)$. By replacing $X$ by an open neighborhood of $x$ and $Y'$ by the
prescheme on the open inverse image, we may suppose $X$ is **étale** over the relative polynomial scheme
$Y[t_{1}, \cdots, t_{n}]$ (the Exposé II definition of smooth = locally étale over $Y[t_{1}, \cdots, t_{n}]$, file 14).
Consider the composite $Y'_{0} \to X \to Y[t_{1}, \cdots, t_{n}]$. This composite is determined by $n$ sections of
$\mathcal{O}_{Y'_{0}}$ (the images of the $t_{i}$). Each can be extended in a neighborhood of $z$ to a section of
$\mathcal{O}_{Y'}$, since $Y'_{0}$ and $Y'$ share their underlying space:
$\mathcal{O}_{Y'_{0}} = \mathcal{O}_{Y'} / \mathcal{J}$ for some sheaf of ideals $\mathcal{J}$ of square zero (or at
least nilpotent) — and a section over $Y'_{0}$ is a local section of $\mathcal{O}_{Y'}$ modulo $\mathcal{J}$, which
lifts trivially.

We have extended the morphism to $Y' \to Y[t_{1}, \cdots, t_{n}]$. Now apply the lifting property for **étale**
morphisms (file 11, I.5.6): since $X \to Y[t_{1}, \cdots, t_{n}]$ is étale, the morphism $Y'_{0} \to X$ lifts
**uniquely** to $Y' \to X$ once $Y'_{0} \to Y[t_{1}, \cdots, t_{n}]$ extends to $Y' \to Y[t_{1}, \cdots, t_{n}]$. This
produces the desired $g$.

**$(iii) \Rightarrow (i)$.** The set of points where $f$ is smooth is open (file 14, II.1.4); so it suffices to show
smoothness at every $x \in X$ closed in its fiber. Let $y = f(x)$. The local ring $\mathcal{O}_{x}$ is an algebra over
$\mathcal{O}_{y}$, a localization of an algebra of finite type, with finite residual extension (since $x$ is closed in
its fiber).

Hypothesis (iii) — applied with $Y' = \operatorname{Spec}(C)$ for $C$ a local artinian algebra finite over
$\mathcal{O}_{y}$, $Y'_{0} = \operatorname{Spec}(C / J)$ for $J$ contained in the radical, and $g_{0} : Y'_{0} \to X$
corresponding to the natural local map $\mathcal{O}_{x} \to C / J$ — implies that every such local ring map lifts to a
local ring map $\mathcal{O}_{x} \to C$. (We are using that a morphism $\operatorname{Spec} B \to X$ for $B$ local is
determined bijectively by a local map from some $\mathcal{O}_{x}$ into $B$.)

This is exactly condition (iv) of Theorem III.2.1 (file 19) for the local map $\mathcal{O}_{y} \to \mathcal{O}_{x}$. So
$\mathcal{O}_{x}$ is **formally smooth** over $\mathcal{O}_{y}$. Since $\mathcal{O}_{x} / \mathcal{O}_{y}$ is a
localization of a finite-type algebra, by III.1.9 (file 19) $\mathcal{O}_{x}$ is **smooth** over $\mathcal{O}_{y}$ —
i.e., $f$ is smooth at $x$. ∎

This is the geometric form of the lifting characterization. **All of the rest of Exposé III is built on top of it.**

### Étale via uniqueness of extensions

<!-- source: III.3.2 -->

_This corollary says: the étale case of III.3.1 is recovered by demanding that the extension $g$ of $g_{0}$ is
**unique**. Smoothness gives existence; étaleness adds uniqueness._

**Corollary III.3.2.** _Let $f : X \to Y$ be as in III.3.1. The following are equivalent:_

1. _$f$ is étale._
1. _Condition (ii) of III.3.1 holds with **uniqueness** of the extension $g$ of $g_{0}$ to $U$._
1. _Condition (iii) of III.3.1 holds with **uniqueness** of $g$._

**Proof sketch.** In the proof of (i) ⇒ (ii) of III.3.1, we factored through $Y[t_{1}, \cdots, t_{n}]$ and used the
**uniqueness** part of the étale lifting property. The unique lift of the image of $Y'_{0}$ in $Y[t_{1}, \cdots, t_{n}]$
to $Y'$ is unique only if the lift of $Y'_{0} \to Y[t_{1}, \cdots, t_{n}]$ to $Y' \to Y[t_{1}, \cdots, t_{n}]$ is
unique. But extending sections of $\mathcal{O}_{Y'_{0}}$ to $\mathcal{O}_{Y'}$ is not unique in general — except when
$n = 0$, in which case there is nothing to extend and uniqueness is automatic. So uniqueness of the extension $g$ of
$g_{0}$ happens exactly when $n = 0$ — i.e. when $f$ is **smooth of relative dimension `0`**, which is **étale** (file
14, II.1.4). ∎

This is the second proof, by lifting, that **étale = smooth of relative dimension `0`**. The first was by counting
Kähler differentials in file 14.

### Rational sections over a complete local ring

<!-- source: III.3.3 -->

_This corollary says: when the base is a complete local ring $A$ and $X / A$ is smooth, every rational point of the
closed fiber $X \otimes_{A} k$ lifts to a section of $X$ over $A$. The proper case (say, $A$ a DVR and $X$ proper)
becomes the classical statement about extending generic-fiber points to integral models._

**Corollary III.3.3.** _Let $X \to Y = \operatorname{Spec}(A)$ be a prescheme locally of finite type over a **complete**
local ring $A$, with $y \in Y$ the closed point. Let $x \in f^{-1}(y)$ be **rational over $\kappa(y)$**. If $X$ is
**smooth over $A$ at $x$**, then there exists a section $s : Y \to X$ of $f$ "passing through $x$", i.e. with
$s(y) = x$._

_In particular, if $X$ is smooth over $A$, then the natural map_

```text
Γ(X / Y) ⟶ Γ(X ⊗_A k / k)
```

_from sections of $X$ over $Y$ to rational points of the closed fiber over $k = A / \mathfrak{m}$ is **surjective**._

**Proof sketch.** The rational point $x \in f^{-1}(y)$ is a section of
$f^{-1}(y) = X \otimes_{A} k \to \operatorname{Spec}(k)$, i.e. a section of $X$ over the closed sub-prescheme
$\operatorname{Spec}(k) \subset \operatorname{Spec}(A)$. By Theorem III.3.1 condition (iii) (or rather a step-by-step
application of it through the artinian thickenings $A / \mathfrak{m}^{n+1}$), this section extends to a section over
each thickening. Passing to the limit (using the completeness of $A$), the section extends to all of
$Y = \operatorname{Spec}(A)$. ∎

**The discrete-valuation-ring application.** Suppose $A$ is a discrete valuation ring with field of fractions $K$, and
$X$ is proper (in fact projective) over $A$. Then sections of $X$ over $Y = \operatorname{Spec}(A)$ are the same as
**points of $X$ with values in $A$**. By the valuative criterion for properness (file 02, §V4 of the algebraic-geometry
skill, or Liu §3.3.4), these identify with the **points of $X_{K} = X \otimes_{A} K$ with values in $K$** — i.e. the
$K$-rational points of the generic fiber `X_K`. Combining with III.3.3:

> _For $A$ a complete DVR, $X$ smooth and proper over $A$: every rational point of the closed fiber $X \otimes_{A} k$
> extends uniquely to a $K$-rational point of the generic fiber `X_K`._

This is the classical "specialization map" for $K$-rational points. It is the foundation for studying integral models of
varieties over local fields — the arithmetic-geometry use of Exposé III's lifting theory.

## III.4 Local infinitesimal extension of smooth $S$-schemes

<!-- source: III.4 -->

We now invert the direction of §III.3. Instead of asking whether a morphism into a smooth scheme extends, we ask whether
a smooth scheme **itself** extends along a thickening of the base.

### Theorem: smooth schemes lift smoothly, locally

<!-- source: III.4.1 -->

_This theorem says: a smooth scheme over a closed sub-prescheme $Y_{0}$ always lifts, locally, to a smooth scheme over
the ambient $Y$. The local lift exists; the next two results clarify what "local" and "unique up to isomorphism" mean._

**Theorem III.4.1.** _Let $Y$ be a locally noetherian prescheme, let $Y_{0}$ be a closed sub-prescheme with the same
underlying space, let $X_{0}$ be a smooth $Y_{0}$-prescheme, and let $x \in X_{0}$. Then there exist:_

- _an open neighborhood $U_{0}$ of $x$ in $X_{0}$,_
- _a prescheme $X$ smooth over $Y$,_
- _a $Y_{0}$-isomorphism $h : U_{0} \to X \times_{Y} Y_{0}$._

_Moreover, if $(U'_{0}, X', h')$ is another solution, then it is isomorphic to the first in a neighborhood of $x$ (in a
sense made precise in the source)._

**Reformulation in terms of sheaves.** For $U_{0}$ given, a solution of the problem amounts to giving on $U_{0}$ a sheaf
of algebras $\mathcal{B}$ over $f^{-1}_{0}(\mathcal{O}_{Y})$, where $f_{0}$ is the continuous map underlying the
structural morphism $U_{0} \to Y_{0}$, together with a homomorphism of rings $\mathcal{B} \to \mathcal{O}_{U_{0}}$
compatible with the homomorphism $f^{-1}(\mathcal{O}_{Y}) \to f^{-1}(\mathcal{O}_{Y_{0}})$, satisfying:

1. The induced map $\mathcal{B} \otimes_{f^{-1}(\mathcal{O}_{Y})} f^{-1}(\mathcal{O}_{Y_{0}}) \to \mathcal{O}_{U_{0}}$
   is an isomorphism (the sheaf of algebras $\mathcal{B}$ recovers $\mathcal{O}_{U_{0}}$ after reduction modulo the
   ideal of $Y_{0}$ in $Y$).
1. $U_{0}$ equipped with $\mathcal{B}$ becomes a smooth $Y$-prescheme.

In this form the precise meaning of local uniqueness becomes particularly evident.

**Proof sketch.** Since $X_{0}$ is smooth over $Y_{0}$, by file 14 (II.1.1) we may suppose, at the chosen $x$, that
$X_{0}$ is étale over a relative polynomial scheme $Y_{0}[t_{1}, \cdots, t_{n}] := Y'_{0}$. The relative polynomial
scheme $Y'_{0}$ is itself a closed sub-prescheme of $Y' := Y[t_{1}, \cdots, t_{n}]$, with the same underlying space. By
file 11 (I.8.3, the étale lifting theorem), there exists a prescheme $X \to Y'$ étale over $Y'$ and a
$Y'_{0}$-isomorphism $X \times_{Y'} Y'_{0} \to X_{0}$. This $X$ is then smooth over $Y$ (étale over
$Y[t_{1}, \cdots, t_{n}]$ ⟹ smooth over $Y$ by file 14, II.1.1). This gives the existence.

For uniqueness, we use Lemma III.4.2 (below). Two local solutions $(X, h)$ and `(X', h')` agree modulo the ideal of
$Y_{0}$ in $Y$, and the lemma promotes this agreement to an isomorphism of $X$ and $X'$ in a neighborhood of $x$. ∎

**Comment on canonicity.** The local isomorphism is **not unique**: two local solutions admit isomorphisms between them,
but the isomorphism is determined only up to a section of the **automorphism sheaf** of the local lift. This is the
engine of the cohomological obstruction theory in file 21 (III.6).

### Lemma: isomorphism via reduction modulo a locally nilpotent ideal

<!-- source: III.4.2 -->

_This lemma says: a flat $Y$-morphism $u : X \to X'$ is an isomorphism iff its reduction
$u_{0} : X \times_{Y} Y_{0} \to X' \times_{Y} Y_{0}$ is an isomorphism, when $Y_{0}$ is the closed sub-prescheme defined
by a locally nilpotent sheaf of ideals on $Y$._

**Lemma III.4.2.** _Let $Y$ be a prescheme, let $Y_{0}$ be a closed sub-prescheme defined by a locally nilpotent sheaf
of ideals $\mathcal{J}$, let $X$ and $X'$ be $Y$-preschemes, and let $u : X \to X'$ be a $Y$-morphism. Suppose $X$ is
**flat** over $Y$. Then $u$ is an isomorphism if and only if_

```text
u₀ : X ×_Y Y₀ ⟶ X' ×_Y Y₀
```

_is an isomorphism._

**Proof sketch.** Easy by passing to the affine case and looking at associated graded rings for the $\mathcal{J}$-adic
filtration. Flatness of $X$ over $Y$ means tensoring `M ⊗_𝒪_Y 𝒪_X` is exact, so an isomorphism after reducing modulo
$\mathcal{J}$ propagates to an isomorphism on each graded piece, hence on the inverse limit, hence on $X$ itself.

**Variant.** The analogous statement obtained by replacing "isomorphism" with **"closed immersion"** is also valid, and
**without** the flatness hypothesis. (This is occasionally useful and we will use it implicitly in file 21.)

### Remark: the lift is **not** canonical

<!-- source: III.4.3 -->

_This remark says: the local extension $X$ of $X_{0}$ produced by III.4.1 is not unique up to canonical isomorphism —
there exist nontrivial $Y$-automorphisms of $X$ inducing the identity on $X_{0}$. This non-canonicity is precisely what
makes the **global** extension obstructed by cohomology (in file 21)._

**Remark III.4.3.** It is essential to note that the local extension $X$ obtained in III.4.1 **is not canonical**: in
other words, the local isomorphism between two solutions is not unique. Equivalently, in general there exist nontrivial
$Y$-automorphisms of $X$ inducing the identity on the closed sub-prescheme $X_{0} = X \times_{Y} Y_{0}$.

This is why, for the construction of **global** infinitesimal extensions of smooth preschemes, one must expect the
existence of an obstruction of **cohomological nature**. We make this obstruction precise in file 21 (III.6.3): the
obstruction lives in $H^{2}(X_{0}, \mathcal{G})$ for the appropriate sheaf $\mathcal{G}$ built from the **tangent
sheaf** $\mathfrak{g}_{X_{0}/Y_{0}}$ of $X_{0}$ over $Y_{0}$.

> _The connection to file 17._ The non-canonicity of the local lift is exactly the data that gives the automorphism
> sheaf of the local lift. The 2-cocycle of automorphisms on triple overlaps is the obstruction class. The reader who
> has digested file 17 already sees the shape of file 21's argument; III.6 is the application of the H²-as-obstruction
> picture to the lifting problem opened here.

## Running example: lifting $\operatorname{Spec} \mathbb{Z}[t]$ and the elliptic curve

We give two concrete instances of III.4.1 to anchor the abstract discussion.

**The affine line.** Take $Y = \operatorname{Spec} \mathbb{Z}$,
$Y_{0} = \operatorname{Spec}(\mathbb{Z} / p\mathbb{Z}) = \operatorname{Spec} \mathbb{F}_{p}$. The closed sub-prescheme
$Y_{0}$ is cut out by the square-zero ideal $(p) \subset \mathbb{Z}$ (well, square-zero as an ideal in
$\mathbb{Z} / p^{2}\mathbb{Z}$, not in $\mathbb{Z}$ itself; we work over
$\operatorname{Spec} \mathbb{Z} / p^{2}\mathbb{Z}$ for square-zero). Let
$X_{0} = \mathbb{A}^{1}_{\mathbb{F}_{p}} = \operatorname{Spec} \mathbb{F}_{p}[t]$. Then
$X = \mathbb{A}^{1}_{\mathbb{Z}/p^{2}} = \operatorname{Spec}(\mathbb{Z}/p^{2})[t]$ is a smooth lift of $X_{0}$ over
$\operatorname{Spec}(\mathbb{Z}/p^{2})$, and any other lift is $\operatorname{Spec}(\mathbb{Z}/p^{2})[t']$ for some
indeterminate $t'$. The freedom is in the **choice of coordinate** $t' = t + p \cdot \epsilon(t)$ for
$\epsilon(t) \in \mathbb{F}_{p}[t]$ — exactly an element of the tangent sheaf
$\mathfrak{g}_{\mathbb{A}^{1}_{\mathbb{F}_{p}}/\mathbb{F}_{p}}$ tensored with the square-zero ideal `(p)`. In file 21,
this is the H¹ classification of lifts of the affine line; in this case, since
$H^{1}(\mathbb{A}^{1}_{\mathbb{F}_{p}}, \mathfrak{g}) = 0$ (Serre vanishing on the affine), there is essentially one
lift up to isomorphism.

**The elliptic curve.** Take $Y = \operatorname{Spec}(\mathbb{Z}/p^{2})$, $Y_{0} = \operatorname{Spec} \mathbb{F}_{p}$,
and $X_{0} = E_{0} := V(y^{2} - x^{3} - ax_{0} - b_{0}) \subset \mathbb{A}^{2}_{\mathbb{F}_{p}}$ for some
$a_{0}, b_{0} \in \mathbb{F}_{p}$ with $4 a^{3}_{0} + 27 b^{2}_{0} \neq 0$ (so $E_{0}$ is smooth by the file 15 Jacobian
criterion). To lift: choose any $\tilde{a}, \tilde{b} \in \mathbb{Z}/p^{2}$ projecting to $a_{0}, b_{0}$, and set

```text
E := V(y² − x³ − ã x − b̃) ⊂ 𝔸²_{ℤ/p²}.
```

Smoothness of $E$ over $\operatorname{Spec}(\mathbb{Z}/p^{2})$ requires the discriminant
$-16(4\tilde{a}^{3} + 27 \tilde{b}^{2})$ to be a unit in $\mathbb{Z}/p^{2}$. Since the reduction mod $p$ of this
discriminant is $-16(4 a^{3}_{0} + 27 b^{2}_{0})$, which is a unit in $\mathbb{F}_{p}$, the lifted discriminant is a
unit in $\mathbb{Z}/p^{2}$. So $E$ is a smooth lift.

The freedom in choosing $(\tilde{a}, \tilde{b}) \in (\mathbb{Z}/p^{2})^{2}$ projecting to $(a_{0}, b_{0})$ is a
**$(p)\cdot(\mathbb{Z}/p^{2})^{2}$ orbit** of lifts — concretely
$p \cdot (\mathbb{Z}/p^{2})^{2} \simeq \mathbb{F}^{2}_{p}$, two $\mathbb{F}_{p}$-degrees of freedom. This is the H¹
classification: $H^{1}(E_{0}, \mathfrak{g}_{E_{0}/\mathbb{F}_{p}}) \simeq \mathbb{F}^{2}_{p}$ (by Serre duality on the
elliptic curve, this is $H^{0}(E_{0}, \omega_{E_{0}/\mathbb{F}_{p}}) \otimes \mathbb{F}^{2}_{p} \simeq \mathbb{F}_{p}$,
which times the Lie-algebra dual is $\mathbb{F}^{2}_{p}$ — but the explicit computation belongs to file 21). The two
lifts of $(a_{0}, b_{0})$ give the same lifted elliptic curve up to isomorphism if and only if the corresponding
1-cocycle is a coboundary, which here happens always since the lift of $a$ and $b$ is unique up to coboundary.

## What to remember

- **§III.3.1** is the geometric form of the lifting characterization (file 19, III.2.1): smoothness of a finite-type
  morphism $f : X \to Y$ is equivalent to extending morphisms into $X$ from closed subpreschemes of test schemes. Five
  equivalent forms, ranging over local vs global and arbitrary vs artinian test scheme.
- **§III.3.2** recovers étale = smooth + uniqueness of extensions = smooth of relative dimension `0`.
- **§III.3.3** specializes to a complete local base: every rational point of the closed fiber lifts to a section over
  the base. The DVR + proper case is the classical specialization map for rational points.
- **§III.4.1** inverts: every smooth $Y_{0}$-scheme lifts smoothly to a $Y$-scheme **locally**, where
  $Y_{0} \hookrightarrow Y$ is a square-zero thickening (or, more generally, a thickening by a locally nilpotent ideal).
- **§III.4.2** is the lemma that promotes "isomorphism after reduction" to "isomorphism", under flatness.
- **§III.4.3** is the crucial preview: the local lift is **not canonical**. The non-canonicity is exactly the
  cohomological obstruction theory of files 21 and 22.

The next file (file 21) globalizes: §III.5 handles the obstruction to extending a morphism (in $H^{1}$); §III.6 handles
the obstruction to extending a smooth scheme (in $H^{2}$). Both use the cohomological machinery of file 17.
