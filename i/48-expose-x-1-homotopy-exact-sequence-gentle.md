# Rewritten Exposé X, section X.1 — the homotopy exact sequence for a proper separable morphism

<!-- source: X.1 -->

## What this file is about

The previous file proved a three-term sequence connecting the fundamental groups of a fibre, of the total space, and of
the base — but only under a strong hypothesis: the base had to be local and small in a specific sense. Real families of
geometric objects live over bases that are typically larger and more global.

This file removes the hypothesis, at the price of identifying the right replacement: a separability condition on the
family, demanding that fibres remain reduced under any further extension of scalars. With that condition the three-term
sequence holds over any reasonable base. Three early consequences follow: a product formula, invariance under enlarging
an algebraically closed ground field, and a slogan that families of coverings over a compact-like base are rigid.

File 47 closed Exposé IX with the **fundamental exact sequence**

```text
1 → π₁(X̄_0, ā) → π₁(X, a) → π₁(S, b) → 1
```

valid for $X \to S$ proper surjective with geometrically connected fibres over an **artinian** base $S$ (file 47,
IX.6.1). The artinian hypothesis was load-bearing: it made the Stein factorisation $X \to S' \to S$ *trivially* a single
point in each fibre, so that one could read off "$f_{*}\mathcal{O}_{X} = \mathcal{O}_{S}$ = $S'$ connected" directly.
Exposé X opens by asking what happens when the base is allowed to be any locally noetherian prescheme. The first step is
to identify the right hypothesis to put in the place of "artinian." It is not "noetherian local" — at least not by
itself — and it is not "geometrically connected fibres" alone. The right hypothesis is **separability** of the morphism:
$f$ flat with geometrically reduced fibres, plus the residue extensions of generic fibre points are separable. With
separability in hand, the technical content of Exposé IX *and* the Stein-factorisation upgrade of EGA III §7.8 combine
to deliver the **homotopy exact sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

for any proper separable $f : X \to Y$ with geometrically connected fibres, with $Y$ locally noetherian.

Two qualifiers are important. The arrow at the left is **not** asserted to be injective; the algebraic analogue of the
topological $\pi_{2}(Y, b)$ is unavailable in the algebraic-geometric setting at the level of SGA 1. And the right-hand
"$e$" is mandatory: surjectivity at $\pi_{1}(Y, b)$ is the content of IX.3.4 (file 45) made *geometric* via Stein
factorisation, and there is no further term beyond it for our purposes here. The price of dropping the artinian-base
hypothesis is the loss of left-exactness; the gain is that the sequence holds over *any* base, with separability the
controlling hypothesis.

The rest of this file unpacks the proof and three early consequences: the **product formula**
$\pi_{1}(X \times_{k} Y) \simeq \pi_{1}(X) \times \pi_{1}(Y)$ (X.1.7) — which was foreshadowed in file 46 IX.5.4
(pinching) and file 46 IX.5.8 (symmetric powers); the **algebraic-closure invariance**
$\pi_{1}(X) = \pi_{1}(X \otimes_{k} k')$ for $X$ proper connected over an algebraically closed $k$ and $k' \supseteq k$
algebraically closed (X.1.8); and the slogan that **families of étale coverings of a proper scheme are constant**
(X.1.9). The exposé closes with the Lang–Serre counterexample: dropping properness in characteristic $p$ is fatal — the
Artin–Schreier family $x^{p} - x = st$ over the affine plane gives a non-constant family of étale coverings of
$\mathbb{A}^{1}$ parametrised by another $\mathbb{A}^{1}$ (X.1.10).

## §X.1.1 — Separable morphisms

<!-- source: X.1.1 -->

### Definition X.1.1 — separable morphism

<!-- source: X.1.1 -->

**Definition X.1.1.** A prescheme $X$ over a field $k$ is called **separable**, or **separable over $k$**, if for every
field extension $K / k$, the base change $X \otimes_{k} K$ is **reduced**. A morphism of preschemes $f : X \to Y$ is
called **separable**, or $X$ is said to be **separable over $Y$**, if (i) $f$ is **flat**, and (ii) for every $y \in Y$,
the fibre $X_{y} = X \otimes_{Y} \kappa(y)$ is separable over $\kappa(y)$ in the sense just defined.

*This definition says:* a morphism is separable when it is flat and its geometric fibres remain reduced after any
further extension of the residue field. The vocabulary echoes the field-theoretic word "separable" — and not by
accident: when $X$ is a $k$-scheme of finite type, separability of $X$ over $k$ is equivalent to the residue fields
$\kappa(x)$ at generic points of irreducible components being **separable extensions** of $k$, which is the usual
field-theoretic condition.

#### Aside (perfect base fields).

*Skip if the equivalence "separable = reduced" over a perfect field is already familiar.*

If $k$ is **perfect** — that is, every algebraic extension of $k$ is separable — then $X / k$ is separable if and only
if $X / k$ is reduced. This is because in a perfect field there is no inseparability to detect after base extension: the
residue-field extensions $\kappa(x) / k$ at generic points are automatically separable. In particular, over
characteristic zero or over the algebraic closure of any field, "separable" reduces to "reduced." Over an imperfect
field of characteristic $p$ — for instance $\mathbb{F}_{p}(t)$ — the gap between "reduced" and "separable" is real: the
inseparable curve $\operatorname{Spec}(\mathbb{F}_{p}(t)[x] / (x^{p} - t))$ is reduced (the polynomial is irreducible)
but becomes non-reduced after base change to $\mathbb{F}_{p}(t^{1/p})$, where it acquires a $p$-th-power factor.

______________________________________________________________________

### Sorites X.1.1.1 — base change preserves separability

<!-- source: X.1.1 -->

**Sorites.** Let $f : X \to Y$ be separable. For any base change $Y' \to Y$, the pullback $f' : X \times_{Y} Y' \to Y'$
is again separable. Indeed, flatness is preserved by base change, and a fibre $(X \times_{Y} Y')_{y'}$ at $y' \in Y'$ is
canonically isomorphic to the fibre $X_{f'(y')}$ of $f$ base-changed to $\kappa(y')$, which remains separable over
$\kappa(y')$ by the field-theoretic stability of separability.

The composition statement is more delicate; under suitable finiteness hypotheses, the composite of two separable
morphisms is separable. We shall need only the following form, which is an immediate consequence of the definitions
together with (file 12) I.9.2 (étale base change preserves separability of fibres):

**Sorites (étale composition).** If $X$ is separable over $Y$ and $X' \to X$ is étale, then $X'$ is separable over $Y$.

This is exactly what we shall use repeatedly: separability "lives upstairs" under any further étale base change. The
proof is the one-sentence one: étale morphisms are flat, so the composite is flat; and étale base change preserves
reducedness of fibres (file 12, I.9.2).

> **Slogan.** *Separable = flat + geometrically reduced fibres. The hypothesis behaves well under base change and
> further étale extension; it is the right vocabulary for "a morphism whose fibres are honest geometric pieces, with no
> inseparable hidden structure."*

## §X.1.2 — Stein factorisation upgrade

<!-- source: X.1.2 -->

### Proposition X.1.2 — the Stein factorisation of a proper separable morphism is finite étale

<!-- source: X.1.2 -->

**Proposition X.1.2.** Let $f : X \to Y$ be a **proper** and **separable** morphism with $Y$ locally noetherian.
Consider its **Stein factorisation** $X \to Y' \to Y$, where $Y' = \operatorname{Spec}_{Y}(f_{*}\mathcal{O}_{X})$ is the
relative spectrum of the structure direct image; the canonical map $X \to Y'$ is proper with geometrically connected
fibres satisfying $(X \to Y')_{*}\mathcal{O}_{X} = \mathcal{O}_{Y'}$, and $Y' \to Y$ is **finite**. Then $Y' \to Y$ is
**étale**: the Stein factorisation is finite étale.

*This result says:* under proper-separable hypotheses, the "factor out the connected-fibre content" decomposition
$X \to Y' \to Y$ from EGA III §4.3 (file 47's
[`ega-iii-stein-factorisation`](appendix-black-boxes.md#ega-iii-stein-factorisation)) is upgraded: the residual finite
morphism $Y' \to Y$ is no longer merely finite, it is finite **étale** — exactly the class of "covering" morphisms whose
theory we developed in Exposé V (files 30–33).

*Sketch.* The proof appears as the **EGA III 7.8.10(i) corollary**; the gentle outline along the SGA-source lines is the
following. One reduces to the case where $Y = \operatorname{Spec}(A)$ is the spectrum of a complete noetherian local
ring. After a suitable finite faithfully flat extension $A \to A'$ corresponding to a residue-field extension, one
arranges that the connected components of the fibre $X_{y} = X \otimes_{A} \kappa(A)$ over the closed point are
**geometrically** connected. This is equivalent to saying that

```text
H⁰(X_y, 𝒪_{X_y}) = ∏_i k_i,
```

a product of fields equal to $k = \kappa(A)$. Supposing $X$ is connected (one may, by working component by component),
one gets $H^{0}(X_{y}, \mathcal{O}_{X_{y}}) = k$, and the homomorphism $A \to H^{0}(X_{y}, \mathcal{O}_{X_{y}})$ is
**surjective**. The Künneth-type proper-base-change formula EGA III §7 then says that $f_{*}\mathcal{O}_{X}$ is a free
$A$-module $B$ with $B / \mathfrak{m}B \simeq H^{0}(X_{y}, \mathcal{O}_{X_{y}}) = k$. Thus $B$ is a noetherian local
$A$-algebra, free over $A$, with residue extension $k \to k$ the identity — that is, $B$ is **finite locally free** of
rank `1`, and étale-ness reduces to checking the discriminant. Separability of $X / Y$ is what guarantees that the
discriminant is nonzero — that the residue extension is the identity, not a non-trivial inseparable thickening.
Combining: $B$ is finite étale over $A$, hence $Y' = \operatorname{Spec}(B) \to Y$ is finite étale.

The full proof appears in **EGA III §7.8.10(i)**, which we record as a new black-box row
[`ega-iii-7-stein-finite-etale`](appendix-black-boxes.md#ega-iii-7-stein-finite-etale).

> **Slogan.** *The Stein factorisation of a proper separable morphism is finite étale. The general Stein factorisation
> only gives a finite morphism with connected fibres; separability upgrades "finite" to "finite étale."*

This proposition is the workhorse of §X.1. It says that *separability* converts the "Stein factor" $Y'$ from a vague
non-étale finite cover into an honest étale $Y$-cover, which we can think of in the categorical language of (file 33)
Galois categories without modification.

## §X.1.3 — Descent of étale coverings to the base

<!-- source: X.1.3 -->

### Theorem X.1.3 — descent of an étale $X$-covering to an étale $Y$-covering

<!-- source: X.1.3 -->

**Theorem X.1.3.** Let $f : X \to Y$ be **proper** and **separable** with $Y$ locally noetherian and **connected**, and
suppose $f_{*}\mathcal{O}_{X} = \mathcal{O}_{Y}$. (By X.1.2, this is equivalent to saying that the fibres of $f$ are
geometrically connected.) Let $y \in Y$, let $\kappa\bar{y}$ be an algebraic closure of $\kappa(y)$, and let
$\bar{X}_{y} = X_{y} \otimes_{\kappa(y)} \kappa\bar{y}$ be the geometric fibre at $y$.

Let $X'$ be a **connected** étale covering of $X$, and let $\bar{X}'_{y} = X' \times_{X} \bar{X}_{y}$ be the induced
étale covering of $\bar{X}_{y}$. Then the following are equivalent:

1. There exists an étale covering $Y' \to Y$ and an $X$-isomorphism $X' \simeq X \times_{Y} Y'$;
1. $\bar{X}'_{y} \to \bar{X}_{y}$ admits a **section**.

*This result says:* descent of a connected étale covering $X' \to X$ to an étale covering $Y' \to Y$ is controlled by a
single discrete piece of data — whether the geometric fibre $\bar{X}'_{y}$ of the upstairs covering at any chosen
$y \in Y$ admits a section. If yes, then $X'$ does descend to $Y$ (so $\pi_{1}(X) \to \pi_{1}(Y)$ factors through
$\pi_{1}(\bar{X}_{y})$); if no, then $X'$ is "genuinely new on $X$," and contributes to the kernel of
$\pi_{1}(X) \to \pi_{1}(Y)$.

*Proof.* (1) ⟹ (2): if $X' \simeq X \times_{Y} Y'$ for some étale $Y' \to Y$, then
$\bar{X}'_{y} = \bar{X}_{y} \times_{Y} Y'_{y}$. The geometric fibre $Y'_{y} = Y' \otimes_{Y} \kappa\bar{y}$ is a finite
disjoint union $\amalg_{i} \operatorname{Spec}(L_{i})$ of separable extensions of $\kappa\bar{y}$. Since $\kappa\bar{y}$
is algebraically closed, each $L_{i} = \kappa\bar{y}$, so $Y'_{y}$ is a finite disjoint union of copies of
$\operatorname{Spec}(\kappa\bar{y})$. Choose any one of these copies; the corresponding
$\operatorname{Spec}(\kappa\bar{y}) \to Y'_{y}$ pulls back to a section $\bar{X}_{y} \to \bar{X}'_{y}$.

(2) ⟹ (1): suppose a section $\sigma : \bar{X}_{y} \to \bar{X}'_{y}$ is given. We construct $Y'$ as the Stein
factorisation of the composite $X' \to X \to Y$. Concretely, set

```text
h : X′ → Y,    h = f ∘ (X′ → X),    Y′ := Spec_Y(h_*𝒪_{X′}).
```

The composite $X' \to Y' \to Y$ is the Stein factorisation of $h$; the morphism $X' \to Y'$ is proper with geometrically
connected fibres, and $Y' \to Y$ is finite. Since $X'$ is connected and $h_{*}\mathcal{O}_{X'}$ is therefore a
local-on-$Y$ algebra with one connected component over each point, $Y' \to Y$ is the **étale covering** of $Y$
controlled by $f$ and $X'$. That $Y' \to Y$ is *étale* follows from X.1.2 applied to $h = f \circ (X' \to X)$: this
morphism is proper (composite of proper) and separable (composite of proper separable with étale, by the X.1.1 sorites).
Hence the Stein factor $Y' \to Y$ is étale by X.1.2.

It remains to identify $X'$ with $X \times_{Y} Y'$. The canonical comparison map $X' \to X \times_{Y} Y'$ is a morphism
of étale $X$-coverings (étale because both $X \to Y$ and $Y' \to Y$ are, by file 12, I.4.8), so it is étale. It is
between **connected** schemes: $X'$ is connected by hypothesis; $X \times_{Y} Y'$ is connected because $Y' \to Y$ has
connected fibres ($Y'$ is connected as the image of the connected $X'$) and $X \to Y$ has connected fibres ((file 45)
IX.3.4 + the strict-epimorphism (file 33) V.6.9(iii)). So the comparison $X' \to X \times_{Y} Y'$ is an étale morphism
between connected schemes, and to show it is an isomorphism it suffices to show that the projection degree at *one*
point of $X \times_{Y} Y'$ equals 1.

This is where the section $\sigma$ comes in. The hypothesis gives a point $\bar{x} \in \bar{X}_{y}$ over which
$\bar{X}'_{y} \to \bar{X}_{y}$ has a distinguished section, hence has projection degree exactly 1 at $\bar{x}$. The
geometric fibre $(X \times_{Y} Y')_{y} \to \bar{X}_{y}$, after extension to $\kappa\bar{y}$, picks out the chosen
$Y'$-component of $Y'_{y}$, so the projection degree of $\bar{X}'_{y} \to (X \times_{Y} Y')_{y}$ at $\bar{x}$ is again 1
— and projection degree is constant in connected components, so it is 1 everywhere. This proves $X' \to X \times_{Y} Y'$
is an isomorphism.

> **Slogan.** *Descent of a connected étale covering of $X$ to the base $Y$ is detected by a single section over the
> geometric fibre. The descended $Y'$ is the Stein factorisation of $X' \to Y$; X.1.2 is what makes it étale.*

The proof made critical use of X.1.2 (Stein factor is étale), of IX.3.4 (file 45; geometrically connected fibres ⇒ fully
faithful descent on `Sch`), and of the V.6.9 dictionary (file 33; surjective on objects = epi on $\pi_{1}$). The proof
also used a fact about étale morphisms between connected schemes: an étale morphism $\phi : A \to B$ of connected
schemes is an isomorphism iff its projection degree at one (any) point of $B$ is 1 (file 11, I.5.5 corollary). This is
the "covering-space" rigidity that the étale machinery was built to detect.

## §X.1.4 — The homotopy exact sequence

<!-- source: X.1.4 -->

### Corollary X.1.4 — the homotopy exact sequence on $\pi_{1}$

<!-- source: X.1.4 -->

With $f : X \to Y$ proper and separable, $Y$ locally noetherian and connected, $f_{*}\mathcal{O}_{X} = \mathcal{O}_{Y}$
(equivalently, the geometric fibres are connected), choose a point $y \in Y$, an algebraic closure $\kappa\bar{y}$, and
a geometric point $\bar{a} \in \bar{X}_{y}$. Let $a$ and $b$ be its images in $X$ and $Y$.

**Corollary X.1.4.** The sequence of group homomorphisms

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

is **exact** at $\pi_{1}(X, a)$ and at $\pi_{1}(Y, b)$.

*This result says:* under proper-separable + geometrically-connected-fibres, the canonical map
$\pi_{1}(X) \to \pi_{1}(Y)$ is **surjective**, and the inverse image (in $\pi_{1}(X)$) of the trivial subgroup of
$\pi_{1}(Y)$ is the closed normal subgroup generated by the image of $\pi_{1}(\bar{X}_{y}) \to \pi_{1}(X)$.
Categorically: the finite étale coverings of $Y$ are exactly the finite étale coverings of $X$ that become trivial after
base change to a geometric fibre.

*Proof.* This is the rewrite of X.1.3 into the language of fundamental groups, via the V.6 dictionary (file 33). By
(file 33) V.6.9(iii) and V.6.11, a continuous homomorphism $\phi : \pi_{1}(X) \to \pi_{1}(Y)$ is **surjective** if and
only if the corresponding pullback functor on finite étale categories $\mathcal{C}(Y) \to \mathcal{C}(X)$ (taking
$Y' \mapsto X \times_{Y} Y'$) is **fully faithful with image closed under disjoint union and connected quotients**. By
IX.3.4 (file 45), this pullback functor *is* fully faithful under our hypotheses (geometrically connected fibres). The
image is closed under disjoint union and quotients trivially. So $\pi_{1}(X, a) \to \pi_{1}(Y, b)$ is surjective; this
gives exactness at $\pi_{1}(Y, b)$ and the final $e$.

For exactness at $\pi_{1}(X, a)$: this is the V.6.9(ii)-type statement that the kernel of $\pi_{1}(X) \to \pi_{1}(Y)$ (a
closed normal subgroup) is the closed normal subgroup generated by the image of $\pi_{1}(\bar{X}_{y}) \to \pi_{1}(X)$.
Translated through the dictionary, this says: a connected étale cover $X' \to X$ becomes trivial after base change to
$Y$ — i.e. comes from an étale cover $Y' \to Y$ — iff its geometric fibre $\bar{X}'_{y}$ admits a section. That is
exactly X.1.3.

> **Slogan.** *Proper separable + geometrically connected fibres ⇒ $\pi_{1}(X) \to \pi_{1}(Y)$ is surjective with kernel
> the closed normal subgroup generated by $\pi_{1}(\bar{X}_{y})$.*

The exact sequence has no left term $1 \to \pi_{1}(\bar{X}_{y}) \to \cdots$; the leftmost arrow is **not** asserted to
be injective. The algebraic-topology analogue would assert that the kernel of $\pi_{1}(\bar{X}_{y}) \to \pi_{1}(X)$ is
the image of $\pi_{2}(Y, b)$, but $\pi_{2}$ of a scheme is not (in any standard way) part of SGA 1's vocabulary.

## §X.1.5 — Why the proof works: the role of formal geometry

<!-- source: X.1.5 -->

### Remark X.1.5 — IX.1.10 is the load-bearing input

<!-- source: X.1.5 -->

The proof of X.1.3 — and hence of X.1.4 — uses X.1.2 in an essential way. X.1.2, in turn, uses the **first comparison
theorem in algebraic-formal geometry** (i.e. (file 44) IX.1.10, which we cite via
[`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence) and the proper-base-change formula of EGA III
§7.8). This is what we record as the new appendix row
[`ega-iii-7-formal-functions`](appendix-black-boxes.md#ega-iii-7-formal-functions). Without it, separability of $f$
would not suffice to upgrade the Stein factorisation to étale.

By contrast, the descent theory of Exposé IX is used only via **IX.3.4** (file 45) — the assertion that geometrically
connected fibres of $f$ imply the descent functor `g^* : \mathrm{ét}(Y) → \mathrm{ét}(X)` is fully faithful. In the
*proper* case under consideration, IX.3.4 admits a particularly simple direct proof, which we record here for
completeness.

#### Aside (direct proof of IX.3.4 in the proper case).

*Skip if you are comfortable with the file 45 derivation; this is a one-paragraph alternative.*

Let $Y' \to Y$ be étale and suppose $X' = X \times_{Y} Y'$ is the disjoint union of two non-empty open subsets $X'_{1}$
and $X'_{2}$. We show the same is true of $Y'$. Locally on $Y$ we have $Y' = \operatorname{Spec}(\mathcal{A})$ for a
quasi-coherent $\mathcal{O}_{Y}$-algebra $\mathcal{A}$, hence
$X' = \operatorname{Spec}(\mathcal{A} \otimes_{\mathcal{O}_{Y}} \mathcal{O}_{X}) = \operatorname{Spec}(\mathcal{A} \otimes_{\mathcal{O}} \mathcal{O}_{X})$.
The decomposition $X' = X'_{1} \amalg X'_{2}$ corresponds to a decomposition of $\mathcal{A} \otimes \mathcal{O}_{X}$
into two non-zero $\mathcal{O}_{X}$-algebras
$\mathcal{A} \otimes \mathcal{O}_{X} = \mathcal{B}_{1} \times \mathcal{B}_{2}$. Applying $f_{*}$, since
$f_{*}\mathcal{O}_{X} = \mathcal{O}_{Y}$, we get $\mathcal{A} = f_{*}(\mathcal{B}_{1}) \times f_{*}(\mathcal{B}_{2})$ —
a decomposition of $\mathcal{A}$ into two $\mathcal{O}_{Y}$-algebras. To conclude that these are *non-zero*, note that
their unit sections are non-zero (they are the unit sections of the original $\mathcal{B}_{i}$, which are non-zero by
hypothesis). So `Y′ = Spec(𝒜) = Spec(f_*𝓑_1) ⨿ Spec(f_*𝓑_2)` is a non-trivial decomposition. This proves IX.3.4 in the
proper case directly. □

______________________________________________________________________

## §X.1.6 — Extension to the seven-term sequence on $\pi_{0}$

<!-- source: X.1.6 -->

### Remark X.1.6 — the seven-term homotopy sequence

<!-- source: X.I.6 -->

Suppose $f : X \to Y$ is proper and separable as in X.1.4, but now drop the hypothesis
$f_{*}\mathcal{O}_{X} = \mathcal{O}_{Y}$. The Stein factorisation $f : X \to Y' \to Y$ then has $Y' \to Y$ an étale (in
general non-trivial) covering of $Y$, pointed above $b$ by the image $b' \in Y'$ of the geometric point $a \in X$.
Applying X.1.4 to the canonical morphism $X \to Y'$ and supposing $f$ surjective, the exact sequence X.1.4 extends to
the **seven-term sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → π₀(X̄_y, ā) → π₀(X, a) → π₀(Y, b) → e,
```

analogous to the **long exact sequence of homotopy groups of a fibration** in algebraic topology. Here $\pi_{0}(Z, z)$
denotes the pointed set of connected components of $Z$ at $z$ — the "discrete homotopy `0`-th group."

*This result says:* even when $f_{*}\mathcal{O}_{X} \neq \mathcal{O}_{Y}$, the failure is recorded by the
connected-component structure of the geometric fibre via the Stein factorisation, and the resulting seven-term sequence
is the analogue of the topological homotopy LES (low-degree) of a fibration.

The honest qualifier: in topology, the kernel of `π₁(\mathrm{fibre}) → π₁(\mathrm{total})` is the image of
$\pi_{2}(\mathrm{base})$. In algebraic geometry, the analogue of $\pi_{2}$ is not (in any received way) part of SGA 1's
vocabulary; results in this direction would require a "higher homotopy" theory of schemes, which Grothendieck flags as
desirable but unavailable at the time of writing. (Modern work via étale homotopy theory — Artin–Mazur, Friedlander —
addresses this; we do not pursue it here.)

> **Slogan.** *The proper-separable π₁ exact sequence extends to a seven-term
> $\pi_{1} \to \pi_{1} \to \pi_{1} \to \pi_{0} \to \pi_{0} \to \pi_{0} \to e$ sequence analogous to the homotopy LES of
> a fibration. Higher terms would require a higher-homotopy theory of schemes, which is not part of SGA 1.*

## §X.1.7 — The product formula

<!-- source: X.1.7 -->

### Corollary X.1.7 — $\pi_{1}$ of a product

<!-- source: X.1.7 -->

**Corollary X.1.7.** Let $k$ be an algebraically closed field, and let $X$ and $Y$ be two connected preschemes over $k$,
with $X$ **proper** over $k$ and $Y$ locally noetherian. Let $a$ be a geometric point of $X$ and $b$ a geometric point
of $Y$, both with values in the same algebraically closed extension $K / k$. Consider the geometric point $c = (a, b)$
of $X \times_{k} Y$. Then the canonical homomorphism

```text
π₁(X ×_k Y, c) → π₁(X, a) × π₁(Y, b),
```

induced by the two projections, is an **isomorphism**.

*This result says:* over an algebraically closed $k$, the étale fundamental group is **multiplicative under products
with a proper factor**: $\pi_{1}$ of $X \times_{k} Y$ is the direct product of the individual $\pi_{1}$'s, exactly as in
topology for the analogous topological case $\pi_{1}(X \times Y) = \pi_{1}(X) \times \pi_{1}(Y)$.

This formula was foreshadowed in file 46 (IX.5.4 pinching, IX.5.5 nodal-cubic, IX.5.8 symmetric powers); it is the
formal underpinning of computations like $\pi_{1}(Sym^{n} X) = \pi_{1}(X)^{ab}$ (file 46, IX.5.8).

*Proof.* First suppose $K = k$ (i.e. $a$ and $b$ are $k$-rational). Set $Z = X \times_{k} Y$. Apply X.1.4 to the
projection $f : Z \to Y$ and the geometric point $b \in Y$. Two preliminary observations:

- After replacing $X$ by $X_{red}$ (which does not change $\pi_{1}(X, a)$, since the reduction is a universal
  homeomorphism and étale coverings are invariant under such by IX.4.10 (file 45)), we may assume $X$ is **reduced**,
  hence **separable** over $k$ (recall: over an algebraically closed $k$, separable = reduced). Therefore the projection
  $Z = X \times_{k} Y \to Y$ is separable: it is the base change of the separable $X \to \mathrm{Spec}(k)$ along
  $Y \to \mathrm{Spec}(k)$.
- The geometric fibre $Z_{b}$ of $Z \to Y$ over the algebraically closed $b \in Y$ is canonically
  $X \otimes_{k} \kappa(b) = X$ (the hypothesis $K = k$ gives $\kappa(b) = k$). So
  $\pi_{1}(\bar{Z}_{b}) = \pi_{1}(X, a)$.

Hence X.1.4 applied to $Z \to Y$ yields the exact sequence

```text
π₁(X, a) → π₁(Z, c) → π₁(Y, b) → e.
```

The composite $X \to Z \to X$ is the identity (where the first arrow is $id_{X} \times b : X \to X \times_{k} Y = Z$ and
the second is the projection to $X$). This shows that $\pi_{1}(X, a) \to \pi_{1}(Z, c)$ is **injective**: any element of
its kernel must come from an element of $\pi_{1}(Z, c)$ that is killed by the projection to $X$, but the composite is
the identity, so the kernel is trivial.

Together: we have an exact sequence

```text
e → π₁(X, a) → π₁(Z, c) → π₁(Y, b) → e.
```

On the other hand, there is the canonical exact sequence

```text
e → π₁(X, a) → π₁(X, a) × π₁(Y, b) → π₁(Y, b) → e
```

with the canonical inclusion and projection. The canonical homomorphism
$\pi_{1}(Z, c) \to \pi_{1}(X, a) \times \pi_{1}(Y, b)$ is a homomorphism of short exact sequences with identity maps on
the two end terms. Commutativity of the diagram is immediate. By the five lemma, the middle map is an isomorphism. This
proves X.1.7 in the case $K = k$.

When $K \neq k$, we have only an isomorphism $\pi_{1}(Z, c) \to \pi_{1}(X \otimes_{k} K, a) \times \pi_{1}(Y, b)$.
Reducing to the previous case requires the next corollary:

> **Slogan.** *Over an algebraically closed $k$, $\pi_{1}$ is multiplicative under products with a proper factor:
> $\pi_{1}(X \times_{k} Y) = \pi_{1}(X) \times \pi_{1}(Y)$. The "with a proper factor" qualifier is sharp; X.1.10 shows
> that dropping it leads to non-product behaviour.*

## §X.1.8 — Algebraic-closure invariance for $\pi_{1}$

<!-- source: X.1.8 -->

### Corollary X.1.8 — $\pi_{1}$ of a proper scheme over an algebraically closed field is invariant under further algebraically closed extension

<!-- source: X.1.8 -->

**Corollary X.1.8.** Let $X$ be a **proper connected** scheme over an algebraically closed field $k$, let $k' / k$ be an
extension with $k'$ again algebraically closed, let $a'$ be a geometric point of $X \otimes_{k} k'$, and let $a$ be its
image in $X$. Then the canonical homomorphism

```text
π₁(X ⊗_k k′, a′) → π₁(X, a)
```

is an **isomorphism**.

*This result says:* the étale fundamental group of a proper scheme over an algebraically closed field does not change
under further extension of the algebraically closed base field. In particular, computing $\pi_{1}(X)$ is "absolute" —
once $k$ is algebraically closed, no further base extension can refine the answer.

*Proof.* **Surjectivity.** Saying $\pi_{1}(X \otimes_{k} k', a') \to \pi_{1}(X, a)$ is surjective is the assertion: for
every connected étale covering $X' \to X$, the pullback $X' \otimes_{k} k' \to X \otimes_{k} k'$ is again connected.
This follows from $k$ algebraically closed: a connected algebraic extension of an algebraically closed field is the
algebraically closed field itself. Equivalently, this is a special case of (file 45) IX.3.4 with
$g : X \otimes_{k} k' \to X$ (note: properness is not used yet).

**Injectivity.** This is the substantive content. It says: **every étale covering of $X \otimes_{k} k'$ is isomorphic to
the pullback of an étale covering of $X$**.

Let $X'' \to X \otimes_{k} k'$ be an étale covering. By a standard "sorital" finiteness argument (étale coverings are
finite type over the base), one can find a finite-type sub-$k$-algebra $A \subset k'$ and an étale covering
$X'_{A} \to X \otimes_{k} A$ whose pullback to $X \otimes_{k} k'$ is $X'$. Let $Y = \mathrm{Spec}(A)$ — an integral
$k$-scheme of finite type, hence having $k$-rational points (since $k$ is algebraically closed and finite-type integral
implies non-empty $k$-points by Hilbert's Nullstellensatz). Applying X.1.7 to $\pi_{1}(X \times Y)$ at a $k$-rational
point $(a, b) \in X \times Y$: every connected étale covering of $X \times Y$ is the quotient of
$\tilde{X} \times \tilde{Y}$ by a subgroup of $G \times G'$, where $\tilde{X} \to X$ is a Galois étale cover with group
$G$, $\tilde{Y} \to Y$ is Galois with group $G'$, and the quotient subgroup is some $H \subset G \times G'$.

Following the same reasoning on $X \times Y'$, where $Y' = \mathrm{Spec}(L)$ for $L$ the function field of $Y$ (a finite
separable extension of which contains $k'$-algebraically-closed-data), one finds that the original
$X' \to X \otimes_{k} L$ becomes isomorphic to a pullback $X_{1}' \otimes_{k} L'$ (for some finite separable extension
$L' \supset L$ and $X_{1}' \to X$ étale) — and this $L'$ may be taken in $k'$ since $k'$ is algebraically closed.
Pulling back along $L' \to k'$, we conclude $X' \simeq X_{1}' \otimes_{k} k'$. Injectivity proved. □

> **Slogan.** *$\pi_{1}$ of a proper connected scheme over an algebraically closed field is invariant under further
> algebraically closed extension. The proof reduces "extend the base field" to "find a $k$-rational point in the
> parameter space" via Hilbert's Nullstellensatz and the X.1.7 product formula.*

The cycle X.1.7 ⟹ X.1.8 (and X.1.8 closes the proof of X.1.7 by reducing $K = k$ ⟹ general $K$) closes off the
product/base-change story for $\pi_{1}$ of a proper scheme.

## §X.1.9 — Families of étale coverings of a proper scheme are constant

<!-- source: X.1.9 -->

### Corollary X.1.9 — constant families

<!-- source: X.1.9 -->

**Corollary X.1.9.** Let $k$ be an algebraically closed field, let $X$ and $Y$ be two locally noetherian preschemes over
$k$, and let $Z = X \times_{k} Y$. Let $Z' \to Z$ be an étale covering. For every $k$-rational point $y \in Y(k)$, let
$i_{y} : \mathrm{Spec}(k) \to Y$ be the associated point and let $j_{y} = id_{X} \times_{k} i_{y} : X \to Z$ be the
inclusion of the fibre. Let $X_{y}' = X \times_{Z} Z' = (j_{y})^{*} Z'$ be the induced étale covering of $X$ from
$j_{y}$.

Assume $Y$ is **connected** and that **one** of $X$, $Y$ is **proper** over $k$. Then the coverings $X_{y}'$ of $X$ are
**all isomorphic**.

*This result says:* a family of étale coverings of $X$ parametrised by a connected $Y$ — i.e. a single étale covering of
$X \times Y$ whose fibre at each $y$ is the corresponding member of the family — is **constant** when one of $X$, $Y$ is
proper over $k$. The "constant family" intuition is: there are no continuous variations in étale-covering topology over
a proper base.

*Proof.* By X.1.7, every connected étale covering of $X \times_{k} Y$ is a quotient of $\tilde{X} \times_{k} \tilde{Y}$
by a subgroup of $G \times G'$, where $\tilde{X} \to X$ and $\tilde{Y} \to Y$ are Galois étale coverings with groups $G$
and $G'$. The fibre at a $k$-rational $y \in Y(k)$ is then a quotient of $\tilde{X} \times_{k} \mathrm{Spec}(k)$ by a
subgroup of $G \times G'_{y}$, where $G'_{y}$ is the stabiliser of $y$ in $G'$. But since $Y$ is connected, the action
of $G'$ on $Y(k)$ is transitive (assuming $\tilde{Y} \to Y$ is Galois étale connected and Galois acts transitively on
geometric fibres), so all stabilisers $G'_{y}$ are conjugate in $G'$. Hence all quotients
$(\tilde{X} \times \mathrm{Spec}(k)) / (G \times G'_{y})$ are isomorphic as étale $X$-coverings. This is X.1.9. □

> **Slogan.** *Étale coverings of $X$, parametrised by a connected proper $Y$ (or with $X$ proper itself), are constant:
> they don't move with $y$. This is the algebraic counterpart of "constancy of monodromy along a proper-base
> deformation" in classical algebraic geometry.*

## §X.1.10 — The Lang–Serre counterexample

<!-- source: X.1.10 -->

### Remarks X.1.10 — properness cannot be dropped

<!-- source: X.1.10 -->

**Remark X.1.10.** Corollaries X.1.7, X.1.8, and X.1.9 are due to **Lang and Serre** (\[X.2\]: S. Lang and J.-P. Serre,
"Sur les revêtements non ramifiés des variétés algébriques," *Amer. J. Math.* **79** (1957), 319–330) in the case of
normal algebraic schemes. Their work was the **initial motivation** for Grothendieck's theory of the étale fundamental
group developed in SGA 1.

These results become **false** if the properness hypothesis is dropped, at least in characteristic $p > 0$. The
canonical counterexample is the **Artin–Schreier family**.

**Example.** Take $k$ algebraically closed of characteristic $p > 0$. Let $X = \mathrm{Spec}(k[t])$ be the affine line
and $Y = \mathrm{Spec}(k[s])$ another affine line. Consider the family of `k[t, s]`-algebras

```text
B_s = k[t, s][x] / (x^p − x − s t).
```

For each fixed value of $s$ (regarded as a parameter), the family member $B_{s}|_{s = s_{0}}$ for $s_{0} \in k$,
$s_{0} \neq 0$, defines an étale covering $X_{s_{0}}' \to X$: it is a non-trivial Artin–Schreier $\mathbb{Z}/p$-cover of
$\mathbb{A}^{1}_{k}$ ramified only at $\infty$. Two such coverings $X_{s_{0}}'$ and $X_{s_{1}}'$, for $s_{0} \neq s_{1}$
(both non-zero), are **non-isomorphic** as étale $X$-coverings — this is the classical fact that Artin–Schreier
extensions of `k[t]` corresponding to different choices of $s \in k^{\times}$ give non-isomorphic ramified extensions of
$k(t)$ at $\infty$.

Hence: the étale $(X \times Y)$-covering `\mathrm{Spec}(B) → \mathrm{Spec}(k[t, s])` (where
$B = k[t, s][x] / (x^{p} - x - st)$) has all-non-trivial fibres over `Y$, and pairwise distinct fibres over distinct`s₀ ∈
Y(k)$. This contradicts X.1.9, so *a fortiori* X.1.7 fails over $X \times Y$ here.

Similarly, treating `s$ as a transcendental element in an algebraically closed extension`K / k$, one obtains an étale
covering $X' \to X \otimes_{k} K$ that does **not** come from any étale covering of $X$ — contradicting X.1.8.

> **Slogan.** *In characteristic `p$, the affine line over`k$ admits a non-constant family of étale coverings of itself
> parametrised by another affine line — the Artin–Schreier family $x^{p} - x - st$. Properness is the hypothesis that
> rules out such families and makes X.1.7–9 hold.*

The Artin–Schreier family illustrates the **structural** reason why properness matters here: in characteristic \`p$,
inseparable phenomena give rise to non-trivial étale coverings of affine schemes that don't extend to coverings of the
projective compactification. Properness "boxes in" the inseparability by forcing the cover to extend over the boundary,
which then forces constancy in the family.

This counterexample also closes the loop on X.2.5 (file 49): dropping the *separability* hypothesis on
`f$ in X.1.4 or X.2.4 produces families where the specialisation`π₁` morphism fails to be surjective. The Lang–Serre Artin–Schreier phenomenon is the same "wild" inseparable behaviour that makes characteristic-`p$
algebraic geometry strictly richer than characteristic-0 algebraic geometry.

______________________________________________________________________

## Closing pointer: X.1 in context

This file gave the **homotopy exact sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

for $X \to Y$ proper separable with geometrically connected fibres (X.1.4), the **product formula**
$\pi_{1}(X \times_{k} Y) \simeq \pi_{1}(X) \times \pi_{1}(Y)$ for $X$ proper connected over algebraically closed
`k$ (X.1.7), and the **algebraic-closure invariance** of`π₁(X)$ under further algebraically closed extension (X.1.8). The qualifier "the leftmost map is not asserted to be
injective" is structural: the algebraic-geometric analogue of `π₂$ of the base is not in our vocabulary at the level of
SGA 1.

File 49 continues with X.2.1–X.2.5: under a **complete-local** base hypothesis the leftmost map *is* in fact injective
((file 47) IX.6.1 supplies this), and the exact sequence becomes left-exact too — yielding the canonical
**specialisation morphism** $\mathrm{sp} : \pi_{1}(\bar{X}_{y_{1}}) \to \pi_{1}(\bar{X}_{y_{0}})$ for a specialisation
`y_0 ⤳ y_1` in
`Y$. The specialisation map is **surjective** under proper separable hypotheses (upper semicontinuity of fibre`π₁$), but
it can drop strictly along a non-trivial specialisation — even in characteristic 0, even for proper *separable* families
— and the canonical counterexamples (degenerate elliptic curves, M. Artin's unpublished obstruction to fibre `π₁$ as a
local system) are recorded faithfully there.

File 50 carries the story through to the **transcendental method**: in characteristic 0 (and lifted to characteristic
$p$ via Witt vectors plus the X.2.3 surjectivity), the fundamental group of a proper smooth curve of genus
`g$ has a clean topological presentation, with`2g$ generators and one commutator relation. File 51 closes Exposé X by proving
the **continuity theorem** for proper smooth morphisms: the specialisation map is an isomorphism on prime-to-`p$
quotients, with **Abhyankar's lemma** as the technical input.
