# Exposé VIII §§VIII.5–6 (gentle): descent of morphisms and finite-fibre applications

## What this file is about

Gluing has so far been about objects: take pieces with overlap data and assemble one global thing. The next question is
about the maps between such things. Given two assembled objects and a candidate map between them defined piece by piece,
when does it actually fit together as a single global map? The answer is what closes the previous two files' machinery
into something usable for working geometers.

The file also includes a small finite-fibre application. When a family is well-behaved and only ever hits finitely many
points above each base point, the family is forced into an especially rigid shape — close to the most classical kind of
covering one meets in undergraduate algebra. A clean theorem captures exactly when this happens.

## Opening: from modules-and-topology to morphisms in `Sch`

File 40 (§VIII.1) descended *quasi-coherent modules*. File 41 (§§VIII.2–4) descended *properties* of morphisms
(surjectivity, finite type, quasi-compactness, openness, separation, properness) — but always *property* descent, not
descent of morphisms themselves. The present file (§§VIII.5–6) closes that gap.

**§VIII.5.** Faithfully flat quasi-compact morphisms are themselves *descent morphisms* for the arrow fibration of
`Sch`: a morphism $f : X \to Y$ of $S$-schemes is the same data as its base change $f' : X' \to Y'$ plus a descent
condition on the two pull-backs to $S''$. This is Theorem VIII.5.2. It is the corollary of two things already in hand —
descent of sections of quasi-coherent modules (file 40, VIII.1.7) and the quotient-topology fact (file 41, VIII.4.3) —
assembled by an effective-epimorphism argument (VIII.5.1). Once VIII.5.2 is proved, immersions, affine morphisms,
integral / finite / locally free morphisms, ampleness, and quasi-affineness all descend.

**§VIII.6.** Two Zariski-Main-Theorem-flavoured statements: **proper with finite fibres ⇒ finite** (VIII.6.1) and
**quasi-finite + separated ⇒ quasi-affine** (VIII.6.2). Both are about locally noetherian $Y$ and are proved together by
noetherian induction on $\dim Y$. The argument decomposes $X = X' \amalg X''$ into a finite piece $X'$ and a remainder
$X''$ whose fibre at the closed point of $Y$ is empty; the proper case forces $X'' = \emptyset$, the quasi-finite case
reduces $X''$ to lower dimension. The proofs do *not* use the theorem on formal functions; they come "for free"
alongside the descent machinery, hence Grothendieck's "as a bonus to the reader".

The slogan for this file: **morphisms descend, and descent plus noetherian induction give Grothendieck's algebraic
Zariski Main Theorem.**

## §VIII.5 Descent of morphisms of preschemes

<!-- source: VIII.5 -->

### VIII.5.1 — Effective epimorphism in ringed spaces

<!-- source: VIII.5.1 -->

_This result says: under mild surjectivity-and-injectivity hypotheses on the structure sheaf map, $g : S' \to S$ is
already an **epimorphism** of ringed spaces; under the further sheaf-equaliser condition that the descent diagram is
exact, $g$ is an **effective epimorphism**. This is the topological + sheaf-theoretic core that lifts the descent of
sections (VIII.1.7) to descent of morphisms (VIII.5.2)._

**Proposition.** Let $g : S' \to S$ be a morphism of preschemes.

(a) Suppose $g$ is surjective and the homomorphism $g^{*} : \mathcal{O}_{S} \to g_{*}(\mathcal{O}_{S'})$ of sheaves of
rings on $S$ is injective. Then $g$ is an epimorphism in the category of preschemes, and even in the category of ringed
spaces.

(b) Suppose moreover that $g$ makes $S$ a *quotient topological space* of $S'$. Let $S'' = S' \times_{S} S'$ with
structural morphism $h : S'' \to S$, and consider the canonical diagram of homomorphisms

```text
𝒪_S  ⟶  g_*(𝒪_{S′})  ⇉  h_*(𝒪_{S″}).
```

Suppose this diagram is *exact* (i.e. $\mathcal{O}_{S}$ is the equaliser). Then $g$ is an **effective epimorphism** in
the category of preschemes (and in the category of ringed spaces). Equivalently: for every prescheme (resp. ringed
space) $Z$, the diagram

```text
Hom(S, Z)  ⟶  Hom(S′, Z)  ⇉  Hom(S″, Z)
```

is exact.

**Proof.** (a) We must show that a morphism of ringed spaces $f : S \to Z$ is determined by its composition `f g`. Since
$g$ is surjective, the underlying map $f_{0} : S \to Z$ is determined by $f_{0} g_{0}$. The remaining datum is a map of
sheaves $u : f^{-1}_{0}(\mathcal{O}_{Z}) \to \mathcal{O}_{S}$. From `f g` we know the analogous map
$(f g)^{-1}_{0}(\mathcal{O}_{Z}) = g^{-1}_{0}(f^{-1}_{0}(\mathcal{O}_{Z})) \to \mathcal{O}_{S'}$, equivalently a map
$f^{-1}_{0}(\mathcal{O}_{Z}) \to g_{*}(\mathcal{O}_{S'})$. One checks this is the composite of
$g^{*} : \mathcal{O}_{S} \to g_{*}(\mathcal{O}_{S'})$ with $u$. Since $g^{*}$ is injective by hypothesis, $u$ is
determined by $g^{*} u$. Hence $u$ is determined by `f g`.

(b) Surjectivity gives $f_{0} = f_{0} g_{0} / R(g)$ as set maps; the quotient-topology hypothesis says $f_{0}$ is
continuous (if `f g` is). We need to construct $f$ from $f_{0}$ and from the homomorphism
$(f g)^{*} : (f_{0} g_{0})^{-1}(\mathcal{O}_{Z}) \to \mathcal{O}_{S'}$ that comes packaged with $f_{0} g_{0}$.

That homomorphism is equivalent, via the adjunction $(g_{0})_{*}  \dashv (g_{0})^{-1}$ and using that
$f_{0} = f_{0} g_{0} / R(g)$, to a map $f^{-1}_{0}(\mathcal{O}_{Z}) \to g_{*}(\mathcal{O}_{S'})$. The descent-equation
$f' p_{1} = f' p_{2}$ on $S''$ says that this map equalises the two arrows `g_*(𝒪_{S′}) ⇉ h_*(𝒪_{S″})`. By the equaliser
hypothesis (b), the map factors uniquely through $\mathcal{O}_{S}$. This gives the map
$f^{-1}_{0}(\mathcal{O}_{Z}) \to \mathcal{O}_{S}$ we need, hence a morphism of ringed spaces $f : S \to Z$ with
$f g = f'$. ∎

_N.B._ The proposition holds for arbitrary ringed spaces and for spaces ringed by local rings (one verifies that the
descended $f$ is a morphism of *locally* ringed spaces by surjectivity of $g$). This is the abstraction we apply for
preschemes below.

### VIII.5.2 — The main descent theorem for morphisms

<!-- source: VIII.5.2 -->

_This result says: faithfully flat quasi-compact morphisms $g : S' \to S$ are morphisms of `Sch`-descent: morphisms
between two $S$-schemes are the same data as their base-change morphisms with a descent condition. **Not** every descent
datum on a prescheme $X' \to S'$ is effective — see §VIII.7 for the delicate question of effectivity._

**Theorem.** Let $\mathcal{F}$ be the fibred category $Ar(Sch) \to Sch$ of arrows in `Sch` (file 35, VI.11.a). Every
faithfully flat quasi-compact morphism $g : S' \to S$ is a morphism of $\mathcal{F}$-descent. Equivalently: for every
pair `X, Y` of $S$-preschemes with base changes $X', Y'$ over $S'$ and $X'', Y''$ over $S''$, the diagram

```text
Hom_S(X, Y)  ⟶  Hom_{S′}(X′, Y′)  ⇉  Hom_{S″}(X″, Y″)
```

is exact.

**Proof.** This is VIII.5.1(b) applied to the prescheme $g : S' \to S$ and to the target $Z = Y$ (the target prescheme),
*after* one reduces the morphism statement to a structure-sheaf statement.

Specifically: in `Sch`, the hypothesis (b) of VIII.5.1 — that `𝒪_S → g_*(𝒪_{S′}) ⇉ h_*(𝒪_{S″})` is exact — is exactly
the content of VIII.1.7 (descent of sections) applied to the structure sheaf $\mathcal{O}_{S}$. And the
quotient-topology hypothesis of (b) is VIII.4.3 (file 41). So (b) applies, and the morphism statement above is its
conclusion. ∎

The slogan: **morphisms of $S$-schemes descend along faithfully flat quasi-compact covers.**

### VIII.5.3 — Universal effective epimorphism

<!-- source: VIII.5.3 -->

**Corollary.** A faithfully flat quasi-compact morphism of preschemes is a *universal effective epimorphism* (an
effective epimorphism in `Sch` that remains so after every base change).

**Proof.** The class of faithfully flat quasi-compact morphisms is stable under base change. By VIII.5.2 every such
morphism is an effective epimorphism; the universal version is the same statement after pull-back. ∎

### VIII.5.4 — Isomorphisms descend

<!-- source: VIII.5.4 -->

_This result says: an $S'$-morphism is an isomorphism iff its image after the base change $g$ is. The most-used
corollary of VIII.5.2 in practice._

**Corollary.** Let $g : S' \to S$ be faithfully flat quasi-compact, $f : X \to Y$ an $S$-morphism, and $f' : X' \to Y'$
its base change. Then $f$ is an isomorphism iff $f'$ is.

**Proof.** If $f'$ is an isomorphism, its inverse $f'^{-1}$ is an $S'$-morphism between schemes with descent data. By
VIII.5.2 (full faithfulness) it comes from a unique $S$-morphism $e : Y \to X$. The two compositions $e f = id_{X}$ and
$f e = id_{Y}$ follow from the corresponding identities for $f'$ and $f'^{-1}$ after pull-back to $S'$. ∎

### VIII.5.5 — Descent of immersions

<!-- source: VIII.5.5 -->

_This result says: closed, open, and quasi-compact immersions descend along faithfully flat quasi-compact base change.
Each variant reduces to a different descent statement we already have._

**Corollary.** Under the conditions of VIII.5.4, $f$ is a closed immersion (resp. open immersion, resp. quasi- compact
immersion) iff $f'$ is.

**Proof.** Reduce to $Y = S$ (since $Y' \to Y$ is itself faithfully flat quasi-compact). Only "if" needs proof. Notice
that the immersion $f'$ being a *monomorphism* implies that the two pull-backs of $X'$ to $S''$ are the same subobject
of $Y''$, so any "subobject of $Y'$" interpretation of $X'$ automatically has its descent datum on the diagonal.

*Closed immersion.* $f' : X' \to Y'$ is a closed immersion, so corresponds to a quasi-coherent ideal of
$\mathcal{O}_{Y'}$. By VIII.1.9 (descent of closed subpreschemes), this ideal descends to a quasi-coherent ideal of
$\mathcal{O}_{Y}$, i.e. to a closed subprescheme $X_{1} \subset Y$ with $g^{*}(X_{1}) = X'$. By VIII.5.2, `X_1` is
$Y$-isomorphic to $X$, hence $f : X \to Y$ is a closed immersion.

*Open immersion.* $f' : X' \to Y'$ is an open immersion, so $f'(X')$ is open in $Y'$. By VIII.4.4 (descent of opens),
$f'(X')$ descends to an open $U \subset Y$. The inclusion $U \to Y$ and the morphism $f : X \to Y$ then agree (by
VIII.5.2), so $f$ is an open immersion.

*Quasi-compact immersion.* By VIII.3.3 $f$ is quasi-compact; by VIII.4.5 the subset $f(X) \subset Y$ is locally closed.
Restricting $Y$ to an open neighbourhood of $f(X)$ in which it is closed reduces to the closed-immersion case. ∎

### VIII.5.6 — Affine morphisms descend

<!-- source: VIII.5.6 -->

**Corollary.** Under the conditions of VIII.5.4, $f$ is affine iff $f'$ is.

**Proof.** Specialisation of VIII.2.1 to the $f : X \to Y$ situation (replacing the base $S$ of VIII.2.1 by $Y$).
Alternatively, one can apply Serre's cohomological criterion for affineness (EGA II 5.2) without using descent at all.
Either route gives the conclusion. ∎

### VIII.5.7 — Integral, finite, and finite locally free morphisms descend

<!-- source: VIII.5.7 -->

_This result says: each of "integral", "finite", "finite locally free" descends through faithfully flat quasi-compact
base change. The mechanism is the colimit-of-finite-type argument of VIII.3.4 combined with VIII.5.6._

**Corollary.** Under the conditions of VIII.5.4, $f$ is integral (resp. finite, resp. finite locally free) iff $f'$ is.

**Proof.** "If" only. Reduce to $Y = S$ and to $Y, Y'$ affine. By VIII.5.6, $f$ is affine, so $X, X'$ are affine.

Let $A, A', B, B' = B \otimes_{A} A'$ be the rings of $Y, Y', X, X'$. Write $B = colim_{i} B_{i}$ over its finite-type
$A$-subalgebras. Then $B' = colim_{i} B_{i} \otimes_{A} A'$.

*Integral.* If $B'$ is integral over $A'$, each $B_{i} \otimes_{A} A'$ is a finite-type $A'$-module (its generators are
integral). By faithful flatness of $A' / A$ (VIII.1.10), each $B_{i}$ is then a finite-type $A$-module, hence $B$ is
integral over $A$.

*Finite.* If $B'$ is finite over $A'$, the same argument with finitely many generators of $B'$ gives a single $B_{i}$
with $B_{i} \otimes_{A} A' = B'$. By faithful flatness, $B_{i} = B$. So $B$ is finite over $A$.

*Finite locally free.* "Locally free of finite type" is "finite presentation + flat" (file 26 IV.5). Both descend by
VIII.1.11 (finite presentation) and by faithful flatness reflecting the flatness criterion (file 26). ∎

### Vocabulary: ample invertible sheaves and quasi-projective morphisms

_Inline mini-introduction; cited from [`ega-ii-proj-and-ample`](appendix-black-boxes.md#ega-ii-proj-and-ample)._

An **invertible sheaf** $\mathcal{L}$ on a prescheme $X$ is a locally free $\mathcal{O}_{X}$-module of rank 1.
Equivalently, a line bundle on $X$.

For a quasi-compact morphism $f : X \to S$ of preschemes, an invertible sheaf $\mathcal{L}$ on $X$ is **ample relative
to $f$** when the canonical map

```text
j : X  ⟶  Proj_S\bigl( \oplus_{n ≥ 0} f_*(𝓛^{⊗ n}) \bigr)
```

is an (open) immersion. Equivalently (EGA II 4.6): every point of $X$ has an affine open neighbourhood of the form
$X_{s}$ for some $s \in \Gamma(X, \mathcal{L}^{\otimes n})$ and some $n \geq 1$, and these affine opens cover $X$. The
sheaf $\mathcal{L}$ is **very ample relative to $f$** when $\mathcal{L} = j^{*} \mathcal{O}(1)$ for some closed
immersion $j : X \to \mathcal{P}(\mathcal{S}_{1}) = \mathbb{P}(f_{*}(\mathcal{L}))$.

A morphism $f : X \to S$ is **quasi-projective** when it is quasi-compact and $X$ admits an ample invertible sheaf
relative to $f$; **projective** when there is a *very* ample one.

These notions are *not* developed elsewhere in the gentle SGA series (the ample-sheaf machinery belongs to EGA II); we
use them only to state and apply VIII.5.8 and VIII.5.9 below, and one more time in §VIII.7.6 and §VIII.7.8.

### VIII.5.8 — Ampleness descends (with descent datum)

<!-- source: VIII.5.8 -->

_This result says: ampleness of an invertible sheaf descends through faithfully flat quasi-compact base change,
**provided** the invertible sheaf itself is equipped with a descent datum. VIII.5.10 below explains why "descent datum
on the sheaf" is necessary (and not "descent datum only on $X$")._

**Corollary.** Under the conditions of VIII.5.4, suppose $f$ is quasi-compact, and let $\mathcal{L}$ be an invertible
module on $X$ with inverse image $\mathcal{L}'$ on $X'$. Then $\mathcal{L}$ is ample (resp. very ample) relative to $f$
iff $\mathcal{L}'$ is ample (resp. very ample) relative to $f'$.

**Proof.** "If" only. The hypothesis "$\mathcal{L}'$ is ample relative to $f'$" already implies that $f'$ is separated;
by VIII.4.8, $f$ is separated. Since $f$ is quasi-compact and $g : Y' \to Y$ is flat, computation of direct images via
affine coverings gives, for every $n$,

```text
g^*\bigl( f_*(𝓛^{⊗ n}) \bigr)  ≃  f′_*\bigl( 𝓛′^{⊗ n} \bigr),
```

so the graded $\mathcal{O}_{Y}$-algebra $\mathcal{S} = \oplus_{n} f_{*}(\mathcal{L}^{\otimes n})$ has inverse image
$\mathcal{S}' = g^{*} \mathcal{S} = \oplus_{n} f'_{*}(\mathcal{L}'^{\otimes n})$.

The cokernel of the canonical map $f^{*}(\mathcal{S}_{n}) \to \mathcal{L}^{\otimes n}$ is a quasi-coherent module on $X$
whose pull-back to $X'$ is the cokernel of $f'^{*}(\mathcal{S}'_{n}) \to \mathcal{L}'^{\otimes n}$. The support $Z_{n}$
of the former on $X$ pulls back to the support $Z'_{n}$ of the latter on $X'$. By ampleness of $\mathcal{L}'$, the
intersection $\cap_{n} Z'_{n} = \emptyset$; surjectivity of $X' \to X$ then gives $\cap_{n} Z_{n} = \emptyset$. So the
canonical morphism

$$
j : X  \longrightarrow  \operatorname{Proj}_{S}(\mathcal{S})
$$

is well-defined (its target is the relative `Proj` of $\mathcal{S}$; EGA II §3). The corresponding morphism
$j' : X' \to \operatorname{Proj}_{S'}(\mathcal{S}') = \operatorname{Proj}_{S}(\mathcal{S}) \times_{S} S'$ is the base
change of $j$. The ampleness of $\mathcal{L}'$ says that $j'$ is an immersion, necessarily quasi-compact since $f'$ is.
By VIII.5.5, $j$ is an immersion; hence $\mathcal{L}$ is ample relative to $f$.

The "very ample" case is the same with $n = 1$ and `Proj` replaced by $\mathbb{P}(\mathcal{S}_{1})$. ∎

### VIII.5.9 — Quasi-affine morphisms descend

<!-- source: VIII.5.9 -->

_Recall (EGA II 5.1.1): a quasi-compact $f : X \to S$ is **quasi-affine** when, for every affine open $U \subset S$,
$f^{-1}(U)$ is isomorphic to an open subscheme of an affine scheme. Equivalently: $\mathcal{O}_{X}$ is ample (or very
ample) relative to $f$. The statement of VIII.5.8 with $\mathcal{L} = \mathcal{O}_{X}$ gives:_

**Corollary.** Under the conditions of VIII.5.4, with $f$ quasi-compact, $f$ is quasi-affine iff $f'$ is.

### VIII.5.10 — Remark: Hironaka's example and the projectivity caveat

<!-- source: VIII.5.10 -->

**Remarks.** Hironaka's example of a non-projective smooth proper variety shows: there exists a proper morphism
$f : X \to Y$ of non-singular varieties (with $Y$ projective) such that $Y = Y_{1} \cup Y_{2}$ for two opens with each
$X_{i} = X \times_{Y} Y_{i}$ projective over $Y_{i}$, but $f$ itself not projective. Setting $Y' = Y_{1} \amalg Y_{2}$,
the morphism $Y' \to Y$ is faithfully flat quasi-compact (even quasi-finite), and $f' : X' \to Y'$ is projective, while
$f$ is not.

*Lesson.* Projectivity does *not* descend automatically. To apply VIII.5.8 — i.e. to deduce projectivity of $f$ from
projectivity of $f'$ — one must have an *ample invertible sheaf $\mathcal{L}'$ on $X'$ equipped with a descent datum*
relative to $g$. Then $\mathcal{L}'$ is the inverse image of an invertible sheaf $\mathcal{L}$ on $X$, which is ample
relative to $f$ by VIII.5.8, hence $f$ is quasi-projective (and projective when $\mathcal{L}'$ is very ample). In
Hironaka's example, the projective embedding on each piece $X_{i}$ does *not* assemble into a descent-compatible line
bundle on $X'$; that obstruction is precisely what stops $f$ from being projective.

When $g : S' \to S$ is *finite locally free*, there is a finer story: the norm construction (file 43 §VIII.7.6 and
VIII.7.7) lets one build the requisite descent-compatible ample sheaf, and quasi-projective descent becomes automatic.
We pick this thread up in §VIII.7.

The slogan: **descent of morphisms in `Sch` is the joint application of section-descent (VIII.1.7) and quotient-
topology (VIII.4.3); for projectivity, one also needs descent on the *invertible sheaf*, which is a separate datum.**

## §VIII.6 Application to finite and quasi-finite morphisms

<!-- source: VIII.6 -->

_(Source footnote: "Cf. EGA IV 18.12 for generalizations to preschemes not necessarily locally noetherian.")_

This section proves two theorems that are not, strictly speaking, about descent — but whose proof Grothendieck packages
into Exposé VIII because the natural reduction to the local-noetherian-complete case goes through descent (the
completion `Â` of a noetherian local ring $A$ is faithfully flat over $A$, hence the descent statements of §VIII.5 let
us pass between $A$ and `Â` freely).

**Theorem (VIII.6.1).** Let $f : X \to Y$ be proper with finite fibres, with $Y$ locally noetherian. Then $f$ is finite.

**Theorem (VIII.6.2).** Let $f : X \to Y$ be quasi-finite and separated, with $Y$ locally noetherian. Then $f$ is
quasi-affine (hence quasi-projective).

We prove both at once by a common induction on $n = \dim Y$ after a common reduction to the local complete case.

### VIII.6.3 — Remarks (Chevalley and the Main Theorem)

<!-- source: VIII.6.3 -->

**Remarks.** Theorem VIII.6.1 is classical for algebraic varieties (Chevalley); the modern *EGA* proof uses the theorem
on formal functions (EGA III §4). The present proof avoids that machinery — we get VIII.6.1 free with the proof of
VIII.6.2, which is the substantive new statement.

Recall the *global* form of Zariski's Main Theorem ([EGA III §4] or [VIII.1]): if $f : X \to Y$ is quasi-finite and
*quasi-projective* with $Y$ noetherian, then $X$ is $Y$-isomorphic to an open subprescheme of a *finite* $Y$-prescheme
$Z$. Combining the Main Theorem with VIII.6.2 gives:

### VIII.6.4 — Global Zariski Main Theorem

<!-- source: VIII.6.4 -->

**Corollary.** Let $f : X \to Y$ be quasi-finite and separated with $Y$ noetherian. Then $X$ is $Y$-isomorphic to an
open subprescheme of a finite $Y$-prescheme $Z$.

**Proof.** By VIII.6.2, $f$ is quasi-projective. Apply the Main Theorem. ∎

A further descent-theoretic application of VIII.6.2 is VIII.7.9 (file 43): every descent datum on a quasi-finite
separated prescheme over a locally noetherian base is effective. We say more in file 43.

### VIII.6.5 — Local reduction lemma

<!-- source: VIII.6.5 -->

_Black box; we use it without proof. See \[`ega-iv-constructibility-via-finite-presentation`\](appendix-black-
boxes.md#ega-iv-constructibility-via-finite-presentation) for the noetherian-reduction machinery; the lemma itself is in
EGA IV §8._

**Lemma.** Let $X$ be a prescheme of finite type over a locally noetherian $Y$, and let $y \in Y$. There exists an open
neighbourhood $U \ni y$ such that $X|U$ is finite (resp. quasi-affine, resp. …) over $U$ iff
$X \times_{Y} \operatorname{Spec}(\mathcal{O}_{y})$ is finite (resp. quasi-affine, resp. …) over
$\operatorname{Spec}(\mathcal{O}_{y})$.

In other words: each of these conditions is checkable on the local rings of $Y$. We use this to localise the proofs of
VIII.6.1 and VIII.6.2 to the case where $Y$ is the spectrum of a noetherian local ring.

### Proof of VIII.6.1 and VIII.6.2 (joint)

<!-- source: VIII.6 main proof -->

The proofs share a setup, a reduction, and an induction step. We present them together.

*Reduction to local Y.* Both "finite" and "quasi-affine" are local on $Y$. By VIII.6.5, we may suppose
$Y = \operatorname{Spec} A$ for $A$ a noetherian local ring, and then prove the conclusion over the closed point and
conclude.

*Reduction to complete A.* The completion map $A \to \hat{A}$ is faithfully flat and quasi-compact (file 25, IV.3.4).
The hypotheses of VIII.6.1 and VIII.6.2 — proper + finite fibres, resp. quasi-finite + separated — are stable under base
change. The conclusions — finite, resp. quasi-affine — descend along faithfully flat quasi-compact morphisms by VIII.5.7
(finite) and VIII.5.9 (quasi-affine). So we may suppose $A$ is *complete*.

*Decomposition $X = X' \amalg X''$.* Suppose $A$ is a complete noetherian local ring of dimension $n$. The closed point
of $Y$ is $y$. Let $y_{0} \in X$ lie over $y$. We claim: there is a decomposition

$$
X  =  X'  \amalg  X'',
$$

where $X' \to Y$ is **finite** and the fibre of $X''$ at $y$ is **empty**. To produce it, use that $f$ is separated and
$X$ quasi-finite over $Y$ (in both theorem statements; VIII.6.1's "proper with finite fibres" is *a fortiori*
quasi-finite + separated): the fibre $X_{y}$ is a finite disjoint union of points, and over the *complete* local base
$A$, each isolated point $x \in X_{y}$ corresponds to a *finite* local ring $\mathcal{O}_{X, x}$ over $A$ (by Hensel's
lemma; cf. file 12 I.6.1 or EGA IV §18.5.13). Together these $\operatorname{Spec}(\mathcal{O}_{X, x})$ form a finite
$Y$-prescheme $X'$. The complement $X'' = X \ X'$ lies entirely over `Y \ {y}`.

*Induction.* We do noetherian induction on $n = \dim Y$.

For $n < 0$ (i.e. $Y = \emptyset$) the claim is trivial.

Suppose $n \geq 0$ and the corresponding theorem holds in dimensions $< n$.

*Proof of VIII.6.1 (proper case).* If $f$ is proper, then $X'' \to Y$ is proper (proper is preserved by restriction to
closed subschemes). So $f(X'')$ is closed in $Y$. But $f(X'')$ does not contain $y$ (the fibre of $X''$ at $y$ is
empty). So $f(X'') \subset Y \ {y}$. Since $Y = \operatorname{Spec} A$ with $A$ local and $y$ the closed point,
`Y \ {y}` is not closed in $Y$ *unless* $f(X'') = \emptyset$. Since $f(X'')$ is closed, $f(X'') = \emptyset$, hence
$X'' = \emptyset$. So $X = X'$ is finite. ∎

*Proof of VIII.6.2 (quasi-finite separated case).* Now $f$ is quasi-finite and separated. $X''$ is also quasi-finite and
separated, lying over `Y \ {y}`. Since $\dim(Y \ {y}) < n$ (as $A$ is local of dimension $n$ and removing the closed
point removes one dimension), the induction hypothesis applies: $X''$ is quasi-affine over `Y \ {y}`, hence over $Y$.
The "finite" piece $X'$ is *affine* (finite ⇒ affine), hence quasi-affine. The disjoint union of two quasi-affine
$Y$-preschemes is quasi-affine. So $X = X' \amalg X''$ is quasi-affine over $Y$. ∎

The slogan: **descent + noetherian induction proves the algebraic Zariski Main Theorem variants. Proper kills $X''$
directly; quasi-finite induces $X''$ down to a lower dimension.**

### VIII.6.6 — Remark: dropping noetherian

<!-- source: VIII.6.6 -->

**Remark.** Theorems VIII.6.1 and VIII.6.2 remain valid when $Y$ is *not* assumed locally noetherian, *provided* $f$ is
assumed to be of finite presentation (cf. VIII.3.6). The proof: reduce to $Y$ affine, then use the noetherian- reduction
lemma \[`ega-iv-constructibility-via-finite-presentation`\](appendix-black-boxes.md#ega-iv-constructibility-
via-finite-presentation) to find a noetherian `Y_0` and a finite-type `Y_0`-scheme `X_0` with the same hypotheses
satisfying $f : X \to Y$ deduced from $f_{0} : X_{0} \to Y_{0}$ by base change. By VIII.6.1 (resp. VIII.6.2) for
$f_{0}$, $f_{0}$ is finite (resp. quasi-affine), hence so is $f$. The pattern — "use finite presentation to drop
noetherian" — is ubiquitous in EGA IV.

## Closing

This file proves two distinct things:

1. **Faithfully flat quasi-compact morphisms are descent morphisms in `Sch`** (VIII.5.2), with corollaries descending
   isomorphisms, immersions of every flavour, affineness, integral / finite / finite-locally-free morphisms, ampleness
   (with sheaf-level descent datum), and quasi-affineness.
1. **The local-noetherian Zariski-Main-Theorem variants** (VIII.6.1, VIII.6.2): proper with finite fibres ⇒ finite, and
   quasi-finite + separated ⇒ quasi-affine. The proofs avoid the theorem on formal functions: the descent statement
   VIII.5.7/9 lets us reduce to the complete-local case, and induction on $\dim Y$ plus the decomposition
   $X = X' \amalg X''$ does the rest.

VIII.6.4 then packages VIII.6.2 with the global Main Theorem (EGA III §4, the Stein-factorisation form of Zariski's Main
Theorem for proper morphisms) to produce the global ZMT statement: quasi-finite + separated ⇒ open in a finite scheme.

The next file (§VIII.7) circles back to the effectivity question deferred at the end of VIII.5.2: when *can* a descent
datum on a prescheme $X'$ over $S'$ be made effective? The most important cases are radicial bases (always effective;
VIII.7.5), finite locally free bases (effective when fibres of the equivalence relation lie in affine opens; VIII.7.6),
and ample-invertible-sheaf data (always effective for quasi-projective $X'$; VIII.7.8).

#### Aside (modern perspective).

_Skip if Vistoli or Poonen's chapter is not part of your background._

Vistoli §4.3 gives the modern statement: the fibred category $(Sch / S_{0})$ of preschemes over a fixed base is *not* a
stack in the fpqc topology — descent of morphisms (VIII.5.2) holds, but descent of objects (effectivity) fails in
general (Hironaka's example). The full picture: the *quasi-affine* sub-fibration is a stack (this is VIII.7.9), the
*affine* sub-fibration is a stack (VIII.2.1), and effectivity criteria like VIII.7.6 (finite locally free + affine
neighbourhoods) and VIII.7.8 (ample invertible with descent datum) carve out sub-stacks. The general lesson is that "a
category is fibred + sheaf condition + effectivity" is the stack data, and Exposé VIII catalogues exactly which
sub-fibrations of `Sch` are stacks under fpqc descent.

______________________________________________________________________

This closes §§VIII.5–6 in the gentle reading. Morphisms descend; immersions and structural conditions descend along with
them; and the local-noetherian Zariski-Main-Theorem variants come for free. The final piece — effectivity criteria — is
the topic of file 43.
