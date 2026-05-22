# Exposé II, sections 3–4: permanence and differential properties (gentle)

## What this file is about

If you have a good algebraic version of a submersion, two questions follow almost automatically. Does it preserve the
properties that mattered for ordinary covering maps? And does it admit a workable derivative test, so that you can check
the property by computing something concrete on the defining equations?

This file answers both. The local algebraic properties that survived crossing a covering — being free of certain
singularities, being well-dimensioned, and so on — also survive crossing a submersion, with one extra term tracking the
extra dimensions the submersion adds. The derivative test, in turn, is exactly the test that an engineer or physicist
would write down for the standard example: an elliptic curve cut out of the plane by a cubic equation in two variables
is smooth precisely when the partial derivatives of the cubic do not simultaneously vanish. The classical computation
that a calculus student would do becomes the algebraic theorem of the chapter.

File 14 set up smooth morphisms — étale modulo polynomial coordinates — and gave two intrinsic criteria (flat + smooth
fiber; under normality, equidimensional + smooth fiber). This file does two things. First (II.3): permanence — every
classical local-ring property survives a smooth extension, exactly as it survived an étale one in file 12, with one
extra clause for the relative dimension. Second (II.4): differentials — the relative cotangent sequence splits under
smoothness, $\Omega^{1}_{X/Y}$ is locally free of rank $\dim_{x} f$, and the **Jacobian criterion** identifies smooth
sub-preschemes by a rank computation on differentials.

The differential half is the centerpiece. By the end of this file the elliptic-curve example
$\operatorname{Spec} \mathbb{Z}[x, y] / (y^{2} - x^{3} - ax - b) \to \operatorname{Spec} \mathbb{Z}$ becomes a one-line
check.

Standing assumption: locally noetherian preschemes throughout.

## II.3 Permanence properties

<!-- source: II.3 -->

### What smooth preserves

<!-- source: II.3.1 -->

_This result says: under a smooth morphism, regular / reduced / normal pass between source and target in both
directions. The proofs are inherited from the étale case (file 12) and the polynomial-extension case._

**Proposition II.3.1.** Let $f : X \to Y$ be smooth at $x \in X$, and let $y = f(x)$. Then $\mathcal{O}_{x}$ is regular
(resp. reduced, resp. normal) iff $\mathcal{O}_{y}$ is.

### Proof

The case $X = Y[t_{1}, \cdots, t_{n}]$ is the standard "polynomial extension preserves regular / reduced / normal." The
case $X$ étale over $Y$ was Theorem I.9.5 (file 12). By definition smoothness combines these two: an étale morphism
$U \to Y[t_{1}, \cdots, t_{n}]$ followed by the polynomial projection. Apply each preservation step in turn.

### Dimension and depth formulas

Quasi-finite flatness (file 12 opening) preserves Krull dimension and depth. Smoothness adds the polynomial layer. The
combined formulas are:

```text
dim 𝒪_x = dim 𝒪_y + n − d,
depth 𝒪_x = depth 𝒪_y + n − d,
```

where $n$ is the relative dimension of $f$ at $x$ and $d$ is the transcendence degree of $\kappa(x)$ over $\kappa(y)$.
(See EGA IV §6.1, §6.3 for the proofs.) Subtracting:

```text
codepth 𝒪_x = codepth 𝒪_y,    where codepth = dim − depth.
```

So **codepth is invariant under smooth morphisms**. In particular $\mathcal{O}_{x}$ is Cohen-Macaulay (codepth `0`) iff
$\mathcal{O}_{y}$ is, and $\mathcal{O}_{x}$ has no embedded components iff $\mathcal{O}_{y}$ does not.

Most of this is "Cohen-Macaulay over $Y$" — flat plus smooth fiber — and was implicit at the opening of section I.9 in
the gentle treatment of Exposé I (file 12).

## II.4 Differential properties of smooth morphisms

<!-- source: II.4 -->

The differential machinery of file 03 — the diagonal, the ideal sheaf $\mathcal{I}_{X}$, the sheaf of relative Kähler
differentials $\Omega^{1}_{X/Y} = \mathcal{I}_{X} / \mathcal{I}^{2}_{X}$, and the [conormal](glossary.md#conormal-sheaf)
and [cotangent](glossary.md#relative-differentials) exact sequences — applies to any morphism. Under smoothness, the
cotangent sequence **splits**, $\Omega^{1}_{X/Y}$ is **locally free** of the right rank, and the conormal sequence
becomes the engine of the **Jacobian criterion**. We collect the four foundational lemmas, then climb to the criterion.

### Recall: the relative cotangent sequence

For an $S$-morphism $f : X \to Y$ the cotangent sequence (file 03, "Two exact sequences for $\Omega^{1}$") reads

$$
f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S} \to \Omega^{1}_{X/Y} \to 0
$$

and is exact at the right two terms in general. It is exact on the left exactly when $f$ is formally smooth (one of the
EGA characterizations of formal smoothness; cf.
[`formally-etale-lifting`](appendix-black-boxes.md#formally-etale-lifting)). We will see immediately that smooth ⟹ split
exact.

### Unramified vs. étale, in differentials

<!-- source: II.4.1 -->

_This result says: at the differential level, unramified is "surjective on differentials," étale is "isomorphic on
differentials."_

**Lemma II.4.1.** Let $f : X \to Y$ be a morphism of $S$-preschemes.

- If $f$ is **unramified**, then $f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$ is surjective.
- If $f$ is **étale**, then $f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$ is an isomorphism.
- The converse for unramified holds when $f$ is locally of finite type.

### Proof

The unramified case follows from the cotangent sequence above and $\Omega^{1}_{X/Y} = 0$ (file 04, form (ii) of
unramified). For the étale direction, consider the diagram

```text
X  →  X ×_Y X  →  X ×_S X
↓                  ↓
Y  →             Y ×_S Y.
```

$X \times_{Y} X$ is the fibered product of $Y$ and $X \times_{S} X$ over $Y \times_{S} Y$. Since $f$ is unramified,
$\Delta_{X/Y} : X \to X \times_{Y} X$ is an open immersion (file 04 form (iii)). Hence the conormal sheaf of the
composite immersion $X \to X \times_{Y} X \to X \times_{S} X$ is the pullback to $X$ of the conormal sheaf of
$X \times_{Y} X \to X \times_{S} X$. Since $f$ is also flat (étale), $X \times_{S} X \to Y \times_{S} Y$ is flat, so
this last conormal sheaf is the pullback of the conormal sheaf of $Y \to Y \times_{S} Y$, which is $\Omega^{1}_{Y/S}$.
Pulled back to $X$, that is $f*(\Omega^{1}_{Y/S})$. On the other hand, the conormal sheaf of $X \to X \times_{S} X$ is
$\Omega^{1}_{X/S}$. The chain of identifications gives the isomorphism.

### The polynomial case

<!-- source: II.4.2 -->

_This result says: for the relative polynomial scheme $X = Y[t_{1}, \cdots, t_{n}]$, the cotangent sequence is split
exact and $\Omega^{1}_{X/Y}$ is free on the differentials of the coordinates._

**Lemma II.4.2.** Let $X = Y[t_{1}, \cdots, t_{n}]$ over an $S$-prescheme $Y$. Then the canonical sequence

$$
0 \to f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S} \to \Omega^{1}_{X/Y} \to 0
$$

is exact, and $\Omega^{1}_{X/Y}$ is **free** with basis $dt_{1}, \cdots, dt_{n}$.

### Proof

Affine and computational. For $B = A[t_{1}, \cdots, t_{n}]$, $\Omega^{1}_{B/A} = \oplus B \cdot dt_{i}$ is free by
direct construction (file 03). The exactness on the left follows from the explicit splitting "set the $dt_{i}$ to zero
and identify the rest with $f*(\Omega^{1}_{Y/S})$."

### The differential structure of smooth morphisms

<!-- source: II.4.3 -->

_This result says: under smoothness, the relative cotangent sequence is split exact and $\Omega^{1}_{X/Y}$ is locally
free of rank equal to the relative dimension. This is the differential-geometric heart of smoothness._

**Theorem II.4.3.** Let $f : X \to Y$ be a smooth morphism of $S$-preschemes. Then:

1. The canonical sequence

$$
0 \to f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S} \to \Omega^{1}_{X/Y} \to 0
$$

is **exact**.

1. $\Omega^{1}_{X/Y}$ is **locally free**, and its rank at $x$ equals the relative dimension of $f$ at $x$.

### Proof

By Definition II.1.1, locally $f$ factors as étale $g : U \to Y[t_{1}, \cdots, t_{n}]$ followed by the polynomial
projection. Lemma II.4.2 gives the conclusion for the polynomial projection. Lemma II.4.1 gives isomorphisms
$g*(\Omega^{1}_{Y[t]/S}) \simeq \Omega^{1}_{U/S}$ and $g*(\Omega^{1}_{Y[t]/Y}) \simeq \Omega^{1}_{U/Y}$. Composing the
two reductions gives the conclusion for $f$ near the chosen point. Local freeness with rank $n = \dim_{x} f$ follows
from $\Omega^{1}_{X/Y} \simeq g*(\Omega^{1}_{Y[t]/Y})$ and $\Omega^{1}_{Y[t]/Y}$ free of rank $n$ (Lemma II.4.2).

### A direct corollary

<!-- source: II.4.4 -->

*This result says: under smoothness, the pullback $f*(\Omega^{1}_{Y/S})$sits inside$\Omega^{1}_{X/S}$ as a locally
direct factor.*

**Corollary II.4.4.** Let $f : X \to Y$ be smooth. The map $f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$ is **injective**,
and its image is **locally a direct factor** of $\Omega^{1}_{X/S}$.

### Universally injective homomorphisms

A homomorphism $u : F \to G$ of $\mathcal{O}_{X}$-modules is **universally injective** at $x \in X$ if $F_{x} \to G_{x}$
is injective and remains so after tensoring with every $\mathcal{O}_{x}$-module. When $F$ and $G$ are free of finite
type near $x$, the following are equivalent:

1. $u$ is injective at $x$ and `Coker u` is free at $x$.
1. There is a neighborhood $U$ of $x$ on which $u$ realizes $F|U$ as a direct factor of $G|U$.
1. $u$ is universally injective at $x$.
1. The induced map on fibers $F_{x} \otimes \kappa(x) \to G_{x} \otimes \kappa(x)$ is injective.
1. The transposed map $\check{G} \to \check{F}$ is surjective at $x$.

The proof is a circular round trip: (iv) ⟹ (v) by Nakayama, and (v) ⟹ (i) because a locally free quotient sheaf is
automatically a direct factor. Geometrically, "universally injective" says $u$ realizes the vector bundle of $F$ as a
sub-bundle of the vector bundle of $G$.

### Smoothness via universal injectivity

<!-- source: II.4.5 -->

_This result says: if the target $Y$ is already smooth, then $f$ itself is smooth iff the source is smooth and the
differential pullback is universally injective._

**Corollary II.4.5.** Let $f : X \to Y$ be locally of finite type, $x \in X$, $y = f(x)$, with $Y$ smooth at $y$ over
$S$. The following are equivalent:

1. $f$ is smooth at $x$.
1. $X$ is smooth over $S$ at $x$, and $f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$ is universally injective at $x$ —
   equivalently, injective with free cokernel $\Omega^{1}_{X/Y}$ at $x$.

### Étale criterion in differentials

<!-- source: II.4.6 -->

_This result says: between two smooth $S$-preschemes, $f$ is étale iff it pulls differentials back isomorphically._

**Corollary II.4.6.** Let $f : X \to Y$ be a morphism of smooth $S$-preschemes. Then $f$ is étale at $x$ iff
$f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$ is an isomorphism at $x$.

### Proof sketch

Necessity is II.4.1. For sufficiency: II.4.1 shows $f$ is unramified at $x$. By II.2.2 reduce to
$S = \operatorname{Spec}(k)$. Smoothness of $Y$ over $k$ forces $Y$ regular hence normal; injectivity of
$\mathcal{O}_{y} \to \mathcal{O}_{x}$ then follows by I.9.5(ii) (file 12\) once we check dimensions agree — and the
dimensions are the ranks of $\Omega^{1}_{Y/k}$ and $\Omega^{1}_{X/k}$ at $y$ and $x$ (Theorem II.4.3(ii)), hence equal
by hypothesis.

### Tangent map: a familiar form

<!-- source: II.4.7 -->

When $X$ and $Y$ are both smooth over $S$, the smoothness criterion II.4.5(ii) for $f : X \to Y$ can be rephrased: at
every $x \in X$, the **tangent map** $T_{x} f$ of $f$ at $x$ (the transpose of the fiber map of
$f*(\Omega^{1}_{Y/S}) \to \Omega^{1}_{X/S}$) is **surjective**.

This is the algebraic-geometric analog of the differential-geometric "submersion = surjective tangent map" condition,
familiar from analytic geometry. The "nonsingularity" hypothesis usually imposed in analytic geometry is the same as
smoothness over $\operatorname{Spec} \mathbb{C}$.

### Étale via differentials of generators

<!-- source: II.4.8 -->

_This result says: at a smooth point, an $S$-morphism to the affine $n$-space defined by sections $g_{i}$ is étale iff
the $dg_{i}$ form a basis of $\Omega^{1}_{X/S}$._

**Corollary II.4.8.** Let $X$ be an $S$-prescheme, $g : X \to S[t_{1}, \cdots, t_{n}]$ an $S$-morphism defined by
sections $g_{i} \in \mathcal{O}_{X}$, and $x \in X$ such that $X$ is smooth over $S$ at $x$. Then $g$ is étale at $x$
iff the $dg_{i}$, $1 \leq i \leq n$, form a **basis** of $\Omega^{1}_{X/S}$ at $x$. Equivalently, the $dg_{i}(x)$ form a
basis of the fiber $\Omega^{1}_{X/S}(x)$ over $\kappa(x)$.

This is the differential test for "the chosen coordinates are local étale coordinates."

### The conormal sheaf

For a closed sub-prescheme $Y \hookrightarrow X$ defined by a coherent ideal sheaf $\mathcal{J}$, the **conormal sheaf**
of $Y$ in $X$ is

$$
\mathcal{N}_{Y/X} := \mathcal{J} / \mathcal{J}^{2},
$$

a coherent sheaf on $Y$. It records the first-order behavior of $X$ along $Y$.

If $X$ is an $S$-prescheme, the **conormal exact sequence** on $Y$ reads

```text
𝒥/𝒥²  --d→  Ω¹_{X/S} ⊗_{𝒪_X} 𝒪_Y  →  Ω¹_{Y/S}  →  0,
```

or in the affine version ($B \to C = B/J$):

```text
J/J²  →  Ω¹_{B/A} ⊗_B C  →  Ω¹_{C/A}  →  0.
```

The right two terms are the cotangent sequence of $Y \to X \to S$ with $\Omega^{1}_{Y/X} = 0$; the first map sends a
function $g \in \mathcal{J}$ to its differential `dg`, restricted to $Y$ (modulo $\mathcal{J}^{2}$). The exactness is
classical (file 03 derived this from the diagonal computation for differentials).

This was the engine behind I.7.2 in file 11 (the different ideal of $B = A[t]/F$ is `(F'(u))`).

### Smooth in $X$ smooth over $S$: four equivalent forms

<!-- source: II.4.9 -->

_This result says: when $X$ is smooth and $Y \subset X$ is a closed sub-prescheme, four conditions are equivalent
characterizations of "$Y$ arises by an étale base change of a coordinate hyperplane in some affine $n$-space.""_

**Proposition II.4.9.** Let $X$ be an $S$-prescheme smooth at $x \in X$, let $Y \hookrightarrow X$ be defined by an
ideal sheaf $\mathcal{J}$, and let $g_{i} \in \mathcal{O}_{X}$, $1 \leq i \leq n$, define an $S$-morphism
$g : X \to X' = S[t_{1}, \cdots, t_{n}]$. Fix $0 \leq p \leq n$. The following are equivalent:

1. There is a neighborhood $X_{1}$ of $x$ in $X$ such that $g|X_{1}$ is étale and $Y \cap X_{1}$ is the inverse image of
   the coordinate sub-prescheme $Y' = S[t_{p+1}, \cdots, t_{n}] \subset X'$. Equivalently, the $g_{i}$,
   $1 \leq i \leq p$, generate $\mathcal{J}|X_{1}$.
1. $Y$ is smooth over $S$ at $x$, the $g_{i}$ for $1 \leq i \leq p$ lie in $\mathcal{J}_{x}$, the $dg_{i}(x)$ for
   $1 \leq i \leq n$ form a basis of $\Omega^{1}_{X/S}(x)$, and the $dg'_{i}(x)$ for $p + 1 \leq i \leq n$ form a basis
   of $\Omega^{1}_{Y/S}(x)$ (where $g'_{i}$ is the restriction of $g_{i}$ to $Y$).
1. The $g_{i}$, $1 \leq i \leq p$, generate $\mathcal{J}_{x}$, and the $dg_{i}(x)$, $1 \leq i \leq n$, form a basis of
   $\Omega^{1}_{X/S}(x)$.
1. $Y$ is smooth over $S$ at $x$, the $g_{i}$ for $1 \leq i \leq p$ form a minimal system of generators of
   $\mathcal{J}_{x}$, and the $dg'_{i}(x)$ for $p + 1 \leq i \leq n$ form a basis of $\Omega^{1}_{Y/S}(x)$.

Under any of these conditions, $\mathcal{N}_{Y/X} = \mathcal{J}/\mathcal{J}^{2}$ is free at $x$ with basis the classes
of the $g_{i}$, $1 \leq i \leq p$, and the conormal homomorphism
$\mathcal{J}/\mathcal{J}^{2} \to \Omega^{1}_{X/S} \otimes \mathcal{O}_{Y}$ is universally injective at $x$.

### Proof outline

(i) ⟹ all others: $Y_{1}$ is étale over $Y'$ by the corollary "étale + étale-target = étale" (I.4.6, file 10), hence
smooth of relative dimension $n - p$. Then II.4.8 gives the basis statements on $\Omega^{1}$. The conormal sequence
forces the $g_{i}$ modulo $\mathcal{J}^{2}$ to form a basis of $\mathcal{J}/\mathcal{J}^{2}$.

(iii) ⟹ (i): II.4.8 says $g$ is étale near $x$; the $g_{i}$, $1 \leq i \leq p$, generate $\mathcal{J}$ locally, so
$Y \cap X_{1} = g^{-1}(Y')$.

(ii) ⟹ (i): the differential conditions plus II.4.8 say $g$ is étale at $x$ and the restriction $h : Y \to Y'$ is étale
at $x$. Let $Y" = g^{-1}(Y')$. Then $Y \subset Y"$, both étale over $Y'$ at $x$. By I.4.8 (file 10), the inclusion
$Y \to Y"$ is étale, hence (radicial) an open immersion (I.5.1 / I.5.2, file 11). Restrict.

(iv) ⟹ (ii): pure unwinding once one knows $\mathcal{J}/\mathcal{J}^{2}$ is free under the smoothness of $Y$ (which is
the next theorem).

### The Jacobian criterion

<!-- source: II.4.10 -->

_This result says: given a smooth ambient $X$, a closed sub-prescheme $Y$ is smooth at $x$ iff the defining ideal
$\mathcal{J}$ admits, at $x$, generators whose differentials are linearly independent in the fiber of
$\Omega^{1}_{X/S}$. This is the **Jacobian criterion for smoothness**._

**Theorem II.4.10.** Let $X$ be a smooth $S$-prescheme, $Y \hookrightarrow X$ a closed sub-prescheme defined by
$\mathcal{J}$, and $x \in X$. The following are equivalent:

1. $Y$ is smooth over $S$ at $x$.
1. There is a neighborhood $X_{1} \ni x$ and an étale $S$-morphism $g : X_{1} \to X' = S[t_{1}, \cdots, t_{n}]$ such
   that $Y \cap X_{1}$ is the inverse image of the coordinate sub-prescheme $Y' = S[t_{p+1}, \cdots, t_{n}]$ for some
   $p$.
1. There are generators $g_{i}$, $1 \leq i \leq p$, of $\mathcal{J}_{x}$ such that the $dg_{i}$ are part of a basis of
   $\Omega^{1}_{X/S}$ at $x$. Equivalently, the $dg_{i}(x)$ are linearly independent in $\Omega^{1}_{X/S}(x)$ over
   $\kappa(x)$.
1. The conormal sheaf $\mathcal{N}_{Y/X} = \mathcal{J}/\mathcal{J}^{2}$ is free on $Y$ at $x$, the conormal map
   $\mathcal{J}/\mathcal{J}^{2} \to \Omega^{1}_{X/S} \otimes \mathcal{O}_{Y}$ is universally injective at $x$, and
   $\Omega^{1}_{Y/S}$ is locally free at $x$ — equivalently, the conormal sequence

```text
   0 → 𝒥/𝒥² → Ω¹_{X/S} ⊗ 𝒪_Y → Ω¹_{Y/S} → 0
```

is exact and split at $x$.

### Why this is the right criterion

In differential geometry, a smooth submanifold $Y \subset X$ is cut out locally by functions whose differentials span
the conormal directions. The Jacobian criterion is the algebraic transcription: generators of $\mathcal{J}$ whose
differentials are linearly independent in $\Omega^{1}_{X/S}(x)$ cut out a smooth sub-prescheme.

### Proof outline

(ii) ⟹ (i), (iii), (iv) was established in II.4.9. The implication (i) ⟹ (ii) is the new content. By Theorem II.4.3(ii)
the right two terms of the conormal sequence are free $\mathcal{O}_{Y}$-modules at $x$. The map
$\Omega^{1}_{X/S} \otimes \mathcal{O}_{Y} \to \Omega^{1}_{Y/S}$ is surjective; choose $g_{i}$ for $p + 1 \leq i \leq n$
whose differentials map to a basis of $\Omega^{1}_{Y/S}$, and complete to a basis of
$\Omega^{1}_{X/S} \otimes \mathcal{O}_{Y}$ by $g_{i} \in \mathcal{J}_{x}$ for $1 \leq i \leq p$. This puts us under the
hypothesis of II.4.9(ii), which gives II.4.9(i) — i.e. II.4.10(ii).

(iii) ⟹ (ii) is II.4.9(iii) ⟹ II.4.9(i). (iv) is trivially equivalent: if $\mathcal{J}/\mathcal{J}^{2}$ is free of rank
$p$ at $x$ and the conormal map is universally injective, choose generators whose classes are a basis of
$\mathcal{J}/\mathcal{J}^{2}$; by Nakayama they generate $\mathcal{J}_{x}$, and (iii) follows.

### A useful refinement

<!-- source: II.4.11 -->

_This result says: when both $X$ and $Y$ are smooth, four conditions on a candidate generating set $(g_{i})$ of
$\mathcal{J}$ coincide, including being a minimal generating set and being part of an étale-coordinate system._

**Corollary II.4.11.** Let $X$ be an $S$-prescheme, $Y \subset X$ defined by $\mathcal{J}$, $x \in Y$ with both $X$ and
$Y$ smooth over $S$ at $x$. Let $g_{i}$, $1 \leq i \leq p$, be sections of $\mathcal{J}$. The following are equivalent:

1. The $g_{i}$ generate $\mathcal{J}_{x}$ and the $dg_{i}(x)$ are linearly independent in $\Omega^{1}_{X/S}(x)$ over
   $\kappa(x)$.
1. The $g_{i}$ modulo $\mathcal{J}^{2}$ form a basis of $\mathcal{J}/\mathcal{J}^{2}$ at $x$.
1. The $g_{i}$ form a minimal system of generators of $\mathcal{J}_{x}$.
1. There exist $g_{i}$, $p + 1 \leq i \leq n$, such that the full collection defines an étale morphism
   $X_{1} \to X' = S[t_{1}, \cdots, t_{n}]$ on a neighborhood $X_{1} \ni x$, with $Y_{1} = Y \cap X_{1}$ the inverse
   image of $Y' = S[t_{p+1}, \cdots, t_{n}]$.

### The hypersurface case

<!-- source: II.4.12 -->

_This result says: a hypersurface ${F = 0}$ in a smooth ambient is smooth at $x$ iff $F$ vanishes in a neighborhood of
$x$ (trivial case) or $dF(x) \neq 0$ (transverse case)._

**Corollary II.4.12.** Let $X$ be an $S$-prescheme smooth at $x$, let $F \in \mathcal{O}_{X}$, and let $Y$ be the closed
sub-prescheme defined by $F \cdot \mathcal{O}_{X}$. Then $Y$ is smooth over $S$ at $x$ iff one of the following holds:

- $F$ is zero in a neighborhood of $x$ (so $Y$ agrees with $X$ there), or
- $dF(x) \neq 0$ in $\Omega^{1}_{X/S}(x)$.

### Application: the elliptic-curve example

For $S = \operatorname{Spec} \mathbb{Z}$, $X = \operatorname{Spec} \mathbb{Z}[x, y] = \mathbb{A}^{2}_{\mathbb{Z}}$,
smooth over $\mathbb{Z}$ of relative dimension `2`. Take $F = y^{2} - x^{3} - ax - b$ for fixed $a, b \in \mathbb{Z}$.
Then $Y = \operatorname{Spec} \mathbb{Z}[x, y] / (F)$ is a closed sub-prescheme of $\mathbb{A}^{2}_{\mathbb{Z}}$.
Compute:

```text
dF = 2y · dy − (3x² + a) · dx ∈ Ω¹_{X/ℤ} = ℤ[x, y] · dx ⊕ ℤ[x, y] · dy.
```

By Corollary II.4.12, $Y$ is smooth over $\mathbb{Z}$ at a point $(x_{0}, y_{0}) \in Y$ iff $dF(x_{0}, y_{0}) \neq 0$ in
$\Omega^{1}_{X/\mathbb{Z}}(x_{0}, y_{0})$. That is:

```text
(2y₀, −(3x₀² + a)) ≠ (0, 0)    in κ(x₀, y₀)².
```

Equivalently, $2y_{0} \neq 0$ or $3x^{2}_{0} + a \neq 0$. The locus where both vanish is $y_{0} = 0$,
$3x^{2}_{0} + a = 0$, with the additional constraint $F(x_{0}, y_{0}) = 0$ (i.e. $(x_{0}, y_{0}) \in Y$). Substituting
$y_{0} = 0$: $0 = x^{3}_{0} + a x_{0} + b$. Substituting $3x^{2}_{0} + a = 0$: $a = -3x^{2}_{0}$. Then
$0 = x^{3}_{0} - 3x^{3}_{0} + b = -2x^{3}_{0} + b$, so $x^{3}_{0} = b/2$. Multiplying out, the condition for
non-smoothness at some characteristic-$p$ fiber pins down a specific divisibility involving the **discriminant**
$\Delta = -16(4a^{3} + 27b^{2})$.

In particular, **$Y$ is smooth over $\mathbb{Z}[1/\Delta]$**: away from the primes dividing the discriminant, the
elliptic curve has nowhere non-vanishing `dF`, hence is smooth at every point. This is the classical elliptic-curve
discriminant story; the Jacobian criterion of II.4.10 / II.4.12 is what lets us read it off `dF` alone, with no further
analysis.

### Smoothness descends along faithfully flat extensions

<!-- source: II.4.13 -->

_This result says: smoothness can be checked after a faithfully flat base change._

**Corollary II.4.13.** Let $Y$ be an $S$-prescheme locally of finite type, $S' \to S$ a flat morphism,
$Y' = Y \times_{S} S'$, $x' \in Y'$ mapping to $x \in Y$. Then $Y$ is smooth over $S$ at $x$ iff $Y'$ is smooth over
$S'$ at $x'$. If $S' \to S$ is flat and surjective, $Y$ is smooth over $S$ iff $Y'$ is smooth over $S'$.

### Proof

Necessity by II.1.3(ii). For sufficiency: reduce to $Y$ affine, embed $Y$ as a closed sub-prescheme of
$S[t_{1}, \cdots, t_{n}]$. Apply the Jacobian criterion II.4.10(iv): the conormal sequence is exact on the source iff it
is on the base change; this transfers smoothness.

### Regular ideals and regular immersions

<!-- source: II.4.14 -->

The Jacobian criterion deserves the name. Grothendieck's formulation in terms of relative differentials (rather than
absolute differentials over $\mathbb{Z}$) is the form that travels well to the noetherian setting.

The full II.4.14 introduces a packaging:

**Definition.** A sequence $x_{1}, \cdots, x_{n} \in A$ ($A$ noetherian) generates an ideal $J$ **regularly** if the
canonical surjection

$$
(A/J)[t_{1}, \cdots, t_{n}] \to gr^{J}(A)
$$

is an isomorphism. Equivalently:

- the canonical map $S_{A/J}(J/J^{2}) \to gr^{J}(A)$ from the symmetric algebra is an isomorphism;
- $J/J^{2}$ is free with basis the classes of the $x_{i}$ modulo $J^{2}$.

If $J \neq A$, the $x_{i}$ are then a minimal system of generators of $J$, and every other minimal system of generators
is also regular. Localization preserves regularity. For a noetherian local $(A, \mathfrak{m})$ with
$x_{i} \in \mathfrak{m}$, the $x_{i}$ form a regular system of generators iff they form an **$A$-regular sequence in
Serre's sense**: each $x_{i}$ is a non-zero-divisor in $A / (x_{1}, \cdots, x_{i-1})$.

(The $A$-regular sequence formulation appears in Serre's course on commutative algebra written up by Gabriel.)

In sheaf form: an ideal sheaf $\mathcal{J}$ on $X$ is a **regular ideal** if for every $x \in X$, $\mathcal{J}_{x}$
admits a regular system of generators. Equivalently:

1. $S_{\mathcal{O}_{X} / \mathcal{J}}(\mathcal{J}/\mathcal{J}^{2}) \to gr^{\mathcal{J}}(\mathcal{O}_{X})$ is an
   isomorphism.
1. $\mathcal{J}/\mathcal{J}^{2}$ is locally free as an $(\mathcal{O}_{X} / \mathcal{J})$-module.

The closed sub-prescheme $Y \subset X$ defined by a regular ideal is **regularly immersed** in $X$. A morphism that
locally identifies its source with such a closed sub-prescheme is a **regular immersion**, regular at $x$ if the local
identification works on a neighborhood of $x$.

### Terminology warning (Grothendieck)

> The terminology _regular immersion_, _regular ideal_, etc. introduced in this number met with rather lively and
> general opposition from Chevalley and Serre. _Cohen-Macaulay ideal_, or _Macaulayan ideal_, was proposed, which would
> morally oblige one also to adopt _Cohen-Macaulay immersion_. This conflicts with another usage already in the
> multiplodocus, where a morphism of finite type is _Cohen-Macaulay_ at a point if it is flat there and its fiber has a
> Cohen-Macaulay local ring. Pending a satisfactory solution, we shall keep, with every reservation, the terminology
> introduced in this number.

EGA 0_IV §15.1.7 settles on this terminology (regular ideal, regular immersion).

### Smooth ambient via regular immersion

<!-- source: II.4.15 -->

_This result says: if $Y \hookrightarrow X$ is a closed immersion with $Y$ smooth over $S$ at $x$, then $X$ is smooth
over $S$ at $x$ iff the immersion is regular at $x$._

**Theorem II.4.15.** Let $X$ be an $S$-prescheme locally of finite type, $Y \hookrightarrow X$ a closed sub-prescheme
defined by $\mathcal{J}$, $x \in Y$. Suppose **$Y$ is smooth over $S$ at $x$** (no hypothesis on $X$). Then:

```text
X smooth over S at x  ⟺  𝒥_x is a regular ideal of 𝒪_x.
```

### Why the regular-immersion form is natural

When $Y$ is smooth, regularity of the immersion is equivalent to "$X$ looks locally like a free polynomial extension of
$Y$." That is exactly the local form of smoothness: $X$ smooth over $S$ near $Y$ iff $X$ is, near $Y$, a
normal-crossings-free thickening of $Y$ by polynomial coordinates.

### Corollary on global regular embedding

<!-- source: II.4.16 -->

_This result says: when $Y$ is smooth, smoothness of $X$ along $Y$ is the same as $Y$ being regularly embedded._

**Corollary II.4.16.** Suppose $Y$ is smooth over $S$. Then $X$ is smooth over $S$ in a neighborhood of $Y$ iff $Y$ is
regularly embedded in $X$.

### Proof of II.4.16 (sketch)

(i) ⟹ (ii): apply criterion (ii) of II.4.10. The witness $g : X_{1} \to X'$ is flat, hence regularity descends from the
standard inclusion $Y' \subset X'$ to $Y \subset X$ along $g$.

(ii) ⟹ (i): take a regular system $(g_{i})$, $1 \leq i \leq p$, of generators of $\mathcal{J}_{x}$, and $g_{i}$,
$p + 1 \leq i \leq n$, lifts of an étale-coordinate system on $Y_{1}$. The combined $g_{i}$ define
$g : X_{1} \to X' = S[t_{1}, \cdots, t_{n}]$. Show $g$ is étale at $x$: it is unramified by the fiber computation, and a
graded-ring argument (using a flatness criterion on $gr^{\mathcal{J}}$) gives flatness.

### The section case

<!-- source: II.4.17 -->

_This result says: for $X$ over $Y$ and a section $i : Y \to X$, four local properties at $x = i(y)$ coincide, including
$X \to Y$ smooth at $x$, the immersion regular, and the formal completion of $\mathcal{O}_{x}$ along $\mathcal{J}$ being
a power-series algebra._

**Corollary II.4.17.** Let $X$ be locally of finite type over $Y$, $i : Y \to X$ a section, $y \in Y$, $x = i(y)$,
$\mathcal{J}$ the ideal sheaf of $i(Y)$ (assume closed). The following are equivalent:

1. $X$ is smooth over $Y$ at $x$.
1. $i$ is a regular immersion at $y$.
1. The completion $\hat{\mathcal{O}}_{x}$ of $\mathcal{O}_{x}$ for the $\mathcal{J}_{x}$-adic topology is isomorphic
   over $\mathcal{O}_{y}$ to a formal power-series algebra $\mathcal{O}_{y}[[t_{1}, \cdots, t_{n}]]$.
1. There is an $S$-morphism $g : V \to U[t_{1}, \cdots, t_{n}]$ (with $U \ni y$, $V \ni x$) such that $g$ is étale, the
   section $i$ of $X$ over $Y$ corresponds via $g$ to the zero section of $U[t_{1}, \cdots, t_{n}]$.

### Differential smoothness

<!-- source: II.4.18 -->

_This result says: a smooth $X$ over $S$ has the property that the diagonal $X \to X \times_{S} X$ is a regular
immersion. We call this "differentially smooth," and it is exactly the half of smoothness not detected by flatness._

**Corollary II.4.18.** Let $X$ be smooth over $S$. Then the diagonal morphism $\Delta_{X/S} : X \to X \times_{S} X$ is a
**regular immersion**.

We call $X$ **differentially smooth over $S$** if its diagonal is regularly immersed.

### Proof

$X$ and $X \times_{S} X$ are both smooth over $S$. Apply Corollary II.4.16 to the closed embedding
$\Delta_{X/S} : X \hookrightarrow X \times_{S} X$.

### Principal parts sheaves

For $X$ over $S$ (locally of finite type, hence $\mathcal{P}^{n}_{X/S}$ coherent), recall (file 03) the **principal
parts sheaves**

```text
𝒫ⁿ_{X/S} := 𝒪_{X ×_S X} / 𝓘_X^{n+1},    n ≥ 0,
```

regarded as a sheaf of $\mathcal{O}_{X}$-algebras through the first projection $pr_{1} : X \times_{S} X \to X$. The
projective limit $\mathcal{P}^{\infty}_{X/S} = \lim_{n} \mathcal{P}^{n}_{X/S}$ is the structure sheaf of the formal
completion of $X \times_{S} X$ along the diagonal.

Under differential smoothness (Corollary II.4.18), $\mathcal{P}^{\infty}_{X/S}$ is _regular as a sheaf of augmented
algebras over $\mathcal{O}_{X}$_, equivalently:

- $\Omega^{1}_{X/S}$ is locally free, and
- the canonical surjection $S_{\mathcal{O}_{X}}(\Omega^{1}_{X/S}) \to gr_{*}(\mathcal{P}^{\infty}_{X/S})$ from the
  symmetric algebra is an isomorphism.

Equivalently: every point of $X$ has an open neighborhood on which $\mathcal{P}^{\infty}_{X/S}$ is isomorphic to
$\mathcal{O}_{X}[[t_{1}, \cdots, t_{n}]]$.

### Smooth ⟺ flat + differentially smooth

A consequence of II.4.17 + II.4.18 (and II.4.13): for $X$ of finite type over $S$,

```text
X smooth over S  ⟺  X flat over S  +  X differentially smooth over S.
```

Flatness is the new clause; without it differential smoothness already follows for closed sub-preschemes (e.g.
$X \subset S$), but flatness fails. So flatness is the genuinely separate piece.

### Differential operators

The principal parts sheaves are the universal carriers of **differential operators** on $\mathcal{O}_{X}$ relative to
$S$: a homomorphism $D : \mathcal{O}_{X} \to F$ of $\mathcal{O}_{X}$-modules is a _differential operator of order
$\leq n$_ iff it factors through $d^{n} : \mathcal{O}_{X} \to \mathcal{P}^{n}_{X/S}$ followed by an
$\mathcal{O}_{X}$-linear map $u : \mathcal{P}^{n}_{X/S} \to F$. This recovers the recursive definition: $D$ is order
$\leq n$ iff for every $g \in \mathcal{O}_{X}(U)$, the map $f \mapsto D(fg) - g D(f)$ is order $\leq n - 1$.

Under differential smoothness, the sheaf of all-orders differential operators has the familiar structure from manifold
calculus: locally generated by **divided powers** in commuting operators $\partial/\partial x_{i}$, $1 \leq i \leq n$.
In characteristic `0` (or whenever $S$ is a sheaf of $\mathbb{Q}$-algebras) the divided powers reduce to ordinary
polynomials in the $\partial/\partial x_{i}$.

(Full details: EGA IV §16.8–16.12.)

### Terminology revisited

<!-- source: II.4.19 -->

The terminological compromise — "regular immersion" rather than "Cohen-Macaulay immersion" — is recorded in EGA 0_IV
§15.1.7. The gentle reading follows it.

## What to remember

The four pieces of file 15:

- **Permanence (II.3.1, codepth-invariance).** Every classical local-ring property — regular, reduced, normal,
  Cohen-Macaulay — survives a smooth extension in both directions, exactly as it did under étale (file 12) with the
  relative dimension as the only numerical adjustment.
- **The structure of $\Omega^{1}$ under smoothness (II.4.3).** The cotangent sequence is split exact, and
  $\Omega^{1}_{X/Y}$ is locally free of rank $\dim_{x} f$. This is the differential-geometric heart of smoothness.
- **The Jacobian criterion (II.4.10).** A closed sub-prescheme of a smooth ambient is smooth at $x$ iff its defining
  ideal admits generators with linearly independent differentials at $x$. Tested on the elliptic-curve example, this
  gives the classical discriminant story for free.
- **Regular immersions and the diagonal (II.4.15–II.4.18).** Smooth morphisms have regularly immersed diagonals;
  equivalently, the formal completion of $X \times_{S} X$ along the diagonal is a power-series algebra over
  $\mathcal{O}_{X}$. Smooth = flat + differentially smooth, the cleanest decomposition of the definition.

The next file (16) closes the picture by working over a base field: smooth ⟺ regular under separability conditions, the
Mac Lane criterion via separating transcendence bases, and the bridge back to the étale theory of file 12 (étale =
smooth of relative dimension `0`).
