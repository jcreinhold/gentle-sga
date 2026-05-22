# Rewritten Exposé XII, section XII.5 — Riemann existence theorem and $\pi_{1}$ comparison

<!-- source: XII.5 -->

## What this file is about

Take a complex algebraic variety. Build a finite cover of it by analytic means — wind around it the way one winds a
helix above a circle, layer extra sheets above each point, glue everything together using only the tools of complex
analysis. The construction lives entirely outside algebra. The result is the headline theorem of this file: every such
cover, no matter how it was assembled, secretly comes from a polynomial cover. Algebraic geometry catches all of them.
This is the bridge from topology to algebra. As a consequence, the fundamental group computed by walking loops in the
analytic space matches, after a profinite completion, the fundamental group computed by classifying finite algebraic
covers. The two stories — topological and algebraic — agree.

Files 57, 58, 59 built the analytification functor and the algebraic-analytic dictionary at four levels: at the level of
the structure morphism $\phi : X^{an} \to X$ and its completion isomorphism (XII.1), at the level of scheme properties
(XII.2.1), at the level of morphism properties (XII.3.1, XII.3.2), and at the level of coherent cohomology (XII.4.2).
For proper $\mathbb{C}$-schemes the cohomological side delivers a sharp equivalence $Coh(X) \simeq Coh(X^{an})$
(XII.4.4) and a finite-étale equivalence (XII.4.6) on the analytic side.

This file (§XII.5) closes the comparison story by removing the *properness* hypothesis from XII.4.6. The clean statement
(XII.5.1) is the **Riemann existence theorem**: for any $\mathbb{C}$-scheme $X$ locally of finite type — proper or not —
the analytification functor $X' \mapsto X'^{an}$ is an equivalence between finite étale coverings of $X$ and finite
étale coverings of $X^{an}$. The proof routes through three reductions (normal, regular, affine-regular) and then
through Hironaka resolution + the Grauert–Remmert theorem on extending normal finite coverings across divisors.

The most-cited corollary is XII.5.2: the étale fundamental group $\pi^{\acute{e}}_{1}t(X, \phi(x))$ is canonically
isomorphic to the *profinite completion* of the topological fundamental group $\pi^{top}_{1}(X^{an}, x)$. This is the
analytic underpinning of the **transcendental method** of file 50 (X.2.6): the surface-group presentation of
$\pi^{top}_{1}(\Sigma_{g})$ for a smooth proper curve of genus $g$, together with a Witt-vector lift to characteristic
`0` and base change to $\mathbb{C}$, gives the étale fundamental group of any curve of genus $g$ over any algebraically
closed field of any characteristic, as the profinite completion of the topological surface group.

The supporting analytic theory — XII.5.3 (normal cover extension across thin subsets), XII.5.4 (Grauert–Remmert), and
the warning XII.5.5 (the $T^{2} - \sin(1/z)$ counterexample) — is the analytic backbone of the proof of XII.5.1. The
closing remark XII.5.6 of the source records Raynaud's 2003 observation about Higman groups and Toledo's
non-residually-finite construction: the natural map $\pi^{top}_{1}(V^{an}) \to \pi^{\acute{e}}_{1}t(V)$ is generally
*not* injective. The profinite completion in XII.5.2 is therefore load-bearing.

The slogan that emerges by the end of this file: **for $\mathbb{C}$-schemes locally of finite type, finite étale
coverings and topological covering theory agree at the level of profinite completions of $\pi_{1}$** — and that is
exactly what the étale fundamental group of files 30–33 was designed to detect.

______________________________________________________________________

## §XII.5.0 — Bridge: the Riemann existence theorem in three forms

<!-- source: XII.5.0 -->

The **classical Riemann existence theorem** in complex analysis says: every connected unramified topological covering of
a Riemann surface comes from an algebraic structure on the cover. Explicitly: given a meromorphic function $f$ on a
Riemann surface $X$ and a degree-$n$ algebraic equation $P(z, w) = 0$ with $P$ polynomial in $w$ and meromorphic in $z$,
the multi-valued function $w(z)$ cuts out a connected $n$-sheeted covering of the complement-of-branch-locus of $X$, and
this covering carries a unique compatible analytic structure that makes the projection a morphism of Riemann surfaces.

XII.5.1 is Grothendieck's algebraic-scheme-theoretic abstraction of this principle. The bridge from the classical form
to XII.5.1 is, roughly:

- The "Riemann surface" $X$ is replaced by an arbitrary $\mathbb{C}$-scheme $X$ locally of finite type.
- The "connected unramified topological covering" is replaced by the *analytic-space* notion of a finite étale covering.
- The conclusion — that the analytic covering comes from an algebraic one — is unpacked as the equivalence of categories
  XII.5.1.

Three nested forms of the theorem will emerge in this file.

#### Form 1: finite étale categories agree.

The cleanest statement (XII.5.1): the functor $X' \mapsto X'^{an}$ is an equivalence

```text
{finite étale coverings of X}  ≃  {finite étale coverings of X^an}.
```

This is the "categorical Riemann existence theorem". XII.4.6 already gave it for *proper* $X$; XII.5.1 removes the
properness hypothesis.

#### Form 2: $\pi^{\acute{e}}_{1}t(X) = \hat{\pi}^{top}_{1}(X^{an})$.

A corollary of Form 1 by general nonsense about Galois categories (file 33): the étale fundamental group
$\pi^{\acute{e}}_{1}t(X, \phi(x))$ is isomorphic to the **profinite completion** of the topological fundamental group
$\pi^{top}_{1}(X^{an}, x)$. This is XII.5.2.

#### Form 3: a covering of the regular open of $X^{an}$ extends.

The analytic-side backbone of the proof (XII.5.3 and XII.5.4): a finite normal covering of a normal analytic space,
étale away from a rare closed analytic subset, extends uniquely to a finite normal covering of the whole space.

We will prove Form 1 (XII.5.1) by induction on the structure of $X$, reducing successively to the normal, regular, and
finally affine-regular case. The affine-regular case uses Hironaka resolution to compactify, then local Kummer
extensions at boundary points to extend the étale covering, then Grauert–Remmert (Form 3) to globalise the extension,
then XII.4.6 to descend the resulting covering to algebra.

______________________________________________________________________

## §XII.5.1 — The Riemann existence theorem

<!-- source: XII.5.1 -->

### Theorem XII.5.1 — Riemann existence theorem

<!-- source: XII.5.1 -->

**Theorem XII.5.1 (Riemann existence theorem).** Let $X$ be a $\mathbb{C}$-scheme locally of finite type. The functor
$\Psi : X' \mapsto X'^{an}$ from finite étale coverings of $X$ to finite étale coverings of $X^{an}$ is an equivalence
of categories.

*This result says:* every finite étale covering of the analytic space $X^{an}$ comes from a finite étale covering of the
scheme $X$, uniquely up to isomorphism. The analytic and algebraic categories of finite étale coverings agree, without
any properness hypothesis on $X$.

#### Proof structure.

We verify the two clauses: fully faithful (XII.5.1, step 1) and essentially surjective (XII.5.1, step 2). Step 2 is the
substantive case and proceeds by three nested reductions, each handled in its own block.

#### Step 1 — $\Psi$ is fully faithful.

<!-- source: XII.5.1 -->

Let `X', X''` be finite étale coverings of $X$. We must show the canonical map

<!-- label: eq:XII.5.* -->

```text
(*)   Hom_X(X', X'')  →  Hom_{X^an}(X'^an, X''^an)
```

is bijective.

We may assume $X'$ is *connected* (the general case splits over connected components). To give an $X$-morphism from $X'$
to `X''` is equivalent to giving a connected component $X_{i}$ of $X' \times_{X} X''$ such that the morphism
$X_{i} \to X'$ induced by the first projection is an isomorphism. (Indeed, a morphism $X' \to X''$ is the graph
construction: it picks out the closed subscheme $Z \subset X' \times_{X} X''$ that is the graph of the morphism, with
first projection an iso. For a *connected* $X'$ and a finite étale `X''`, every such graph is a connected component of
$X' \times_{X} X''$.)

By the same construction on the analytic side, an analytic $X^{an}$-morphism from $X'^{an}$ to $X''^{an}$ corresponds to
a connected component of $(X' \times_{X} X'')^{an} = X'^{an} \times_{X^{an}} X''^{an}$ whose first projection is an
analytic iso.

By XII.2.6 (file 58), connected components of $X' \times_{X} X''$ correspond bijectively to connected components of
$X'^{an} \times_{X^{an}} X''^{an}$. By XII.3.1 (ix) (file 58), a morphism $X_{i} \to X'$ is an iso iff its
analytification is. Combining these two bijections, the set of "algebraic graphs" is in bijection with the set of
"analytic graphs", which proves `(*)` bijective. ∎\_{step 1}

#### Step 2 — $\Psi$ is essentially surjective.

<!-- source: XII.5.1 -->

Let $\mathcal{X}' \to X^{an}$ be a finite étale covering of $X^{an}$. We must produce an étale covering $X' \to X$ and
an isomorphism $X'^{an} \simeq \mathcal{X}'$. In view of Step 1, the question is *local on $X$*, so we may assume $X$ is
affine.

We proceed by three reductions.

##### (a) Reduction to $X$ normal.

<!-- source: XII.5.1 -->

We may suppose $X$ reduced. Indeed, suppose the theorem proved for $X_{red}$. The functor

```text
Θ : \{finite étale coverings of X^an\}  →  \{finite étale coverings of X_{red}^an\},
    𝓧'  ↦  𝓧'^{red}
```

is fully faithful (a finite étale covering is determined by its restriction to the reduced subscheme of the base,
because the base extension preserves étaleness and the underlying topological space of a reduced finite étale covering
matches the underlying topological space of the original). Composing with the equivalence on $X_{red}$ proves the
equivalence on $X$.

We may further suppose $X$ normal. Let $p : \tilde{X} \to X$ be the normalisation morphism. Then $p$ is finite, so by
IX.4.7 (file 45, also `bourbaki-sem-190`), $p$ is a *morphism of effective descent for the category of étale coverings
of $X$*.

Suppose the theorem proved for $\tilde{X}$. Define

```text
𝓧̃'  :=  𝓧' ×_{X^an} X̃^an
```

as a finite étale covering of $\tilde{X}^{an}$. By the inductive hypothesis (theorem on $\tilde{X}$), there exist an
étale covering $\tilde{X}' \to \tilde{X}$ and an iso $\tilde{X}'^{an} \simeq \tilde{\mathcal{X}}'$. By Step 1 (full
faithfulness, applied to $\tilde{X}$), the natural descent datum on $\tilde{\mathcal{X}}'$ along
$\tilde{X}^{an} \to X^{an}$ lifts to a descent datum on $\tilde{X}'$ along $\tilde{X} \to X$. By effective descent
(IX.4.7), the descent datum is effective, giving an étale covering $X' \to X$ with an iso

```text
i : X'^an ×_{X^an} X̃^an  ≃  𝓧̃',
```

whose two pullbacks to $\tilde{X}^{an} \times_{X^{an}} \tilde{X}^{an}$ agree.

By IX.3.2 (file 45, with its analytic-context analogue valid), the analytic morphism $\tilde{X}^{an} \to X^{an}$ is a
*morphism of descent for the category of finite étale coverings*. Hence the descent datum $i$ extends uniquely to an iso
$X'^{an} \simeq \mathcal{X}'$.

This reduces the theorem to the case $X$ normal. ∎\_{step 2a}

##### (b) Reduction to $X$ regular.

<!-- source: XII.5.1 -->

Let $U$ be the open subset of regular points of $X$. By Input 2 of file 58 (excellence + openness of the regular locus),
$U$ is open and dense in $X$. By XII.2.1 (iv), $U^{an}$ is the open subset of regular points of $X^{an}$. Since $X$ is
normal, $codim_{X}(X - U) \geq 2$ (this is a standard fact about normal noetherian schemes).

We claim it suffices to extend $\mathcal{X}'|_{U^{an}}$ to a finite étale covering on all of $X^{an}$, then descend the
extension. Suppose $U' \to U$ is an étale covering with $U'^{an} \simeq \mathcal{X}'|_{U^{an}}$. Show: $U'$ extends to
an étale covering $X' \to X$ such that $X'^{an} \simeq \mathcal{X}'$.

We just need to show $U'$ extends to an étale $X' \to X$ over the whole of $X$. (Once we have this, the analytic
restriction $X'^{an}|_{U^{an}} \simeq \mathcal{X}'|_{U^{an}}$ is given; and by the codim-≥-2 + normal hypothesis the
canonical maps of structure sheaves

```text
𝓕  →  i_*^an(𝓕|_{U^an}),     𝓖  →  i_*^an(𝓖|_{U^an}),
```

where $\mathcal{F}$ is the coherent analytic algebra defining $\mathcal{X}'$ and $\mathcal{G}$ is the coherent analytic
algebra defining $X'^{an}$, are isomorphisms by `serre-prolongement-faisceaux` (file 58 lemma XII.2.5 codim-2 case).
Hence $\mathcal{F} \simeq \mathcal{G}$, and so $\mathcal{X}' \simeq X'^{an}$.)

To show $U'$ extends, the question is local on $X$. For every point $y \in X^{an} - U^{an}$, consider the étale covering

```text
U'_{φ(y)}  :=  U' ×_X Spec(𝒪_{X, φ(y)})
```

of $U_{\phi(y)} := U \times_{X} \operatorname{Spec}(\mathcal{O}_{X, \phi(y)})$. We need to show this extends to an étale
covering of $\operatorname{Spec}(\mathcal{O}_{X, \phi(y)})$.

Let $H$ be the coherent $\mathcal{O}_{U}$-algebra defining $U'$. The canonical map

```text
α : (i_* H)^an  →  i_*^an(H^an)  =  𝓕
```

defines a stalk map on $\operatorname{Spec}(\mathcal{O}_{X^{an}, y})$:

```text
α_y : (i_* H)^an_y  →  𝓕_y,
```

whose restriction to

```text
U_y  :=  U_{φ(y)} ×_{Spec(𝒪_{X, φ(y)})} Spec(𝒪_{X^an, y})
```

is an isomorphism. This is because over the regular open $U$, the local algebraic and analytic algebras agree after
completion (XII.1.1), and the étale-cover algebra $H$ is finite-locally-free, hence preserved by passage to completion +
faithful-flatness.

The iso on $U_{y}$ says that $H|_{U_{y}}$ is a trivial finite-flat algebra (= a free module of given rank). This
triviality propagates to $\operatorname{Spec}(\mathcal{O}_{X, \phi(y)})$ by Serre's prolongation theorem
(`serre-prolongement-faisceaux`), using $codim_{X}(X - U) \geq 2$: the algebra $i_{*} H$ is reflexive (because $H$ is
free, hence reflexive on $U$), so the stalk $(i_{*} H)_{\phi(y)}$ is the algebra defining the extension of $U'$ to
$\operatorname{Spec}(\mathcal{O}_{X, \phi(y)})$.

This proves the local extension at every $y \in X^{an} - U^{an}$, hence by gluing, $U'$ extends to an étale $X' \to X$.
∎\_{step 2b}

##### (c) Affine regular case.

<!-- source: XII.5.1 -->

Suppose $X$ is *affine and regular*. Let

$$
j : X  \to  P
$$

be a compactification of $X$, where $P$ is a *projective* $\mathbb{C}$-scheme and $j$ is a dominant open immersion. (One
constructs $P$ as the projective closure of an affine embedding; the dominance comes from the affine embedding being
open in its closure.)

By **Hironaka resolution of singularities** (`hironaka-resolution`, since we are in characteristic 0), we can find a
regular projective $\mathbb{C}$-scheme $R$ and a projective morphism

$$
r : R  \to  P
$$

such that $r$ induces an isomorphism $r^{-1}(X) \simeq X$ and such that $R - r^{-1}(X)$ is a **divisor with normal
crossings** in $R$. Let

```text
k := r^{-1} ∘ j : X  →  R
```

be the canonical immersion of $X$ into the regular projective compactification.

We will show: there exists a finite normal covering $\mathcal{R}' \to R^{an}$ (in the sense of XII.5.0; specifically a
normal analytic finite-cover) that extends the étale covering $X'^{an} = \mathcal{X}'|_{X^{an}}$ of
$X^{an} = r^{-1}(X)^{an}$.

By **XII.5.3** (proved below), such an extension $\mathcal{R}'$ is *unique* up to isomorphism — if it exists, it is
determined by its restriction to the dense open $X^{an} \subset R^{an}$. So the problem of extending $\mathcal{X}'$ to
$R^{an}$ is **local on $R^{an}$ near $R^{an} - X^{an}$**.

But each point of $R^{an} - X^{an}$ has, by the normal-crossings structure of the boundary, an open neighbourhood
$\mathcal{V}$ analytically isomorphic to an open ball in some $\mathbb{C}^{n}$, with
$\mathcal{V} - \mathcal{V} \cap X^{an}$ defined by the vanishing of the first $p$ coordinate functions
$z_{1}, \cdots, z_{p}$, where $0 \leq p \leq n$. (When $p = 0$, the boundary is trivial; when $p \geq 1$, it is a
normal-crossings union of $p$ divisors locally.)

The fundamental group of $\mathcal{U} := \mathcal{V} \cap X^{an} = \mathcal{V} - {z_{1} \cdots z_{p} = 0}$ is the
abelianization of $\mathbb{Z}^{p}$ (more precisely, $\pi^{top}_{1}(\mathcal{U}) \simeq \mathbb{Z}^{p}$, with generators
given by small loops around each $z_{i} = 0$ hyperplane). Therefore every finite étale covering of $\mathcal{U}$ is a
quotient of a *Kummer-type* covering

```text
𝓤''  :=  𝓤[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

(for integers $n_{i} > 0$) by a subgroup
$H \subset \mathbb{Z}/n_{1}\mathbb{Z} \times \cdots \times \mathbb{Z}/n_{p}\mathbb{Z}$ of the Galois group of
$\mathcal{U}''$.

The advantage of the Kummer form: $\mathcal{U}''$ *extends naturally* to a regular finite analytic covering of
$\mathcal{V}$:

```text
𝓥''  :=  𝓥[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p).
```

The variety $\mathcal{V}''$ is regular (the equations $T^{n_{i}}_{i} = z_{i}$ cut out a regular hypersurface in a
polydisc), and the group $H$ acts on it. The quotient $\mathcal{V}'' / H$ is then the desired extension of
$\mathcal{U}'' / H$ to $\mathcal{V}$.

Globalising over the cover of $R^{an} - X^{an}$ by such normal-crossings neighbourhoods, we obtain the desired normal
finite analytic covering $\mathcal{R}' \to R^{an}$.

Now apply **XII.4.6** (file 59): since $R$ is a *proper* (in fact projective) $\mathbb{C}$-scheme, the analytification
functor is an equivalence between finite (étale) $R$-schemes and finite (étale) analytic $R^{an}$-spaces. Hence the
finite normal analytic covering $\mathcal{R}'$ of $R^{an}$ comes from a finite normal covering $R' \to R$ of the
projective scheme $R$, with $R'^{an} \simeq \mathcal{R}'$. By XII.3.1 (iii), since
$\mathcal{R}'|_{X^{an}} = \mathcal{X}'$ is *étale*, so is its restriction to $X$, i.e. $X' := R' \times_{R} X$ is finite
étale over $X$. And $X'^{an} \simeq \mathcal{R}'|_{X^{an}} = \mathcal{X}'$. ∎\_{step 2c}

This proves Theorem XII.5.1. ∎

> **Slogan.** *The functor $X' \mapsto X'^{an}$ is an equivalence between finite étale coverings of $X$ and finite étale
> coverings of $X^{an}$, for every $\mathbb{C}$-scheme $X$ locally of finite type.* No properness hypothesis is needed;
> the proof factors through Hironaka resolution + local Kummer extensions + Grauert–Remmert extension.

#### Aside (why Hironaka and not étale local arguments).

The use of Hironaka resolution (`hironaka-resolution`) in step (c) is essential for the *local* picture of the boundary
$R^{an} - X^{an}$ as a normal-crossings divisor. Without normal crossings, the local étale-cover classification at
boundary points becomes much more delicate (a general boundary is a stratification of varying-dimensional pieces, each
with its own fundamental group of the link), and the explicit Kummer-extension construction breaks down.

This is one of two essential uses of resolution-of-singularities in SGA 1 XII (the other is XII.5.4 below). Both uses
are *characteristic 0* — Hironaka's theorem is char 0. The characteristic-$p$ analogue would require de Jong's
alterations (1996) and a more elaborate analytic-side proof, neither of which is in SGA 1.

______________________________________________________________________

## §XII.5.2 — The $\pi_{1}$ comparison

<!-- source: XII.5.2 -->

### Corollary XII.5.2 — $\pi^{\acute{e}}_{1}t(X, \phi(x)) \simeq \hat{\pi}^{top}_{1}(X^{an}, x)$

<!-- source: XII.5.2 -->

**Corollary XII.5.2.** Let $X$ be a *connected* $\mathbb{C}$-scheme locally of finite type, let $\phi : X^{an} \to X$ be
the canonical morphism, and let $x \in X^{an}$. Then there is a canonical isomorphism of profinite groups

```text
π_1^ét(X, φ(x))  ≃  π̂_1^top(X^an, x),
```

where the left side is the étale fundamental group of the scheme $X$ at the base-point $\phi(x)$ (defined in file 33
V.7), and the right side is the **profinite completion** of the topological fundamental group of the analytic space
$X^{an}$ at $x$.

*This result says:* the étale fundamental group is the profinite completion of the topological fundamental group.
Specifically, $\pi^{\acute{e}}_{1}t(X, \phi(x))$ is the completion of $\pi^{top}_{1}(X^{an}, x)$ for the topology
defined by subgroups of finite index.

**Proof.** Let $\mathcal{C}$ be the category of finite étale coverings of $X^{an}$, and let $F : \mathcal{C} \to Set$ be
the *fibre functor*

```text
F(𝓧')  :=  \{ \text{points of } 𝓧' \text{ above } x \}.
```

By construction of the profinite fundamental group of a category-and-fibre-functor pair (V.4, file 33), there is a
canonical profinite group $\hat{\pi}^{top}_{1}(X^{an}, x)$ associated with $(\mathcal{C}, F)$, such that
$(\mathcal{C}, F)$ is *equivalent to the category of finite continuous actions of $\hat{\pi}^{top}_{1}(X^{an}, x)$ on
finite sets*.

Now: every finite étale covering of $X^{an}$ is a quotient of the **universal covering** of $X^{an}$ (which is itself a
topological space, the universal cover in the classical sense) by a subgroup of finite index. Hence the profinite group
associated with $(\mathcal{C}, F)$ is exactly the profinite completion of $\pi^{top}_{1}(X^{an}, x)$:

```text
π̂_1^top(X^an, x)  =  \text{prof. completion of} \pi_1^top(X^an, x)  \text{for the topology of finite-index subgroups}.
```

By XII.5.1, the functor `𝓒 ≃ \{\text{finite étale coverings of} X\}`. The fibre functor of
`\{\text{finite étale coverings of} X\}` is $F' : X' \mapsto X'(\bar{x})$ for $\bar{x} = \phi(x)$ a geometric point. By
V.6.10 (file 33), the associated profinite group is $\pi^{\acute{e}}_{1}t(X, \phi(x))$.

Combining the two equivalences:

```text
π_1^ét(X, φ(x))  =  \text{profinite completion of}  \pi_1^top(X^an, x).
```

∎

> **Slogan.** *$\pi^{\acute{e}}_{1}t(X) \simeq \hat{\pi}^{top}_{1}(X^{an})$ over $\mathbb{C}$.* The étale fundamental
> group is the analytic fundamental group profinitely completed.

#### Aside (the analytic side of the transcendental method of file 50).

The corollary XII.5.2 is the analytic side of the **transcendental method** of file 50 (X.2.6). The
transcendental-method-as-applied-in-file-50 reasoning runs as follows:

1. Take a smooth proper curve `X_0` of genus $g$ over an algebraically closed field $k$ of characteristic $p$.
1. By the Witt-vector lifting theorem (file 22 III.7.4), there exists a smooth proper $W(k)$-curve $X$ with closed fibre
   `X_0`. The generic fibre $X_{K} = X \otimes K$ ($K$ the fraction field of $W(k)$) is a smooth proper curve of genus
   $g$ over $K$.
1. Base change to $K \to \mathbb{C}$ (any embedding) gives a smooth proper curve $X_{\mathbb{C}}$ of genus $g$ over
   $\mathbb{C}$.
1. By XII.5.2, $\pi^{\acute{e}}_{1}t(X_{\mathbb{C}}) \simeq \hat{\pi}^{top}_{1}(X^{an}_{\mathbb{C}})$.
1. Topology of compact Riemann surfaces:
   $\pi^{top}_{1}(X^{an}_{\mathbb{C}}) = \pi^{top}_{1}(\Sigma_{g}) = \langle s_{1}, \cdots, s_{g}, t_{1}, \cdots, t_{g} | \prod [s_{i},  t_{i}] = 1\rangle$
   (the surface group).
1. Specialisation X.2.3 (file 49):
   $\pi^{\acute{e}}_{1}t(X_{\mathbb{C}}) \twoheadrightarrow \pi^{\acute{e}}_{1}t(X_{0})$, surjective.

Combining (4)–(6): $\pi^{\acute{e}}_{1}t(X_{0})$ is a quotient of $\hat{\pi}^{top}_{1}(\Sigma_{g})$, the profinite
completion of the surface group. By continuity X.3.8 (file 51), this surjection is an iso on prime-to-$p$ quotients.

This is exactly the X.2.6 statement that $\pi^{\acute{e}}_{1}t(X_{0})^{(p')}$ is the prime-to-$p$ profinite completion
of the surface group on `2g` generators. XII.5.2 is the analytic input.

______________________________________________________________________

## §XII.5.3 — Normal cover extension across thin subsets

<!-- source: XII.5.3 -->

### Proposition XII.5.3 — normal-finite-cover restriction is fully faithful

<!-- source: XII.5.3 -->

**Proposition XII.5.3.** Let $\mathcal{X}$ be a normal complex analytic space, and let $\mathcal{Y} \subset \mathcal{X}$
be a closed analytic subset such that $\mathcal{U} := \mathcal{X} - \mathcal{Y}$ is *dense* in $\mathcal{X}$. The
restriction functor

```text
\{\text{normal finite coverings of} 𝓧\}  →  \{\text{normal finite coverings of} 𝓤\},
              𝓧'  ↦  𝓧'|_𝓤
```

is *fully faithful*.

*This result says:* a normal finite covering of a normal analytic space is recoverable from its restriction to a dense
open complement of a closed analytic subset. This is the uniqueness half of the XII.5.4 Grauert–Remmert extension
theorem.

**Proof.** Let $\mathcal{X}', \mathcal{X}''$ be normal finite coverings of $\mathcal{X}$. We must show

```text
Hom_𝓧(𝓧', 𝓧'')  →  Hom_𝓤(𝓧'|_𝓤, 𝓧''|_𝓤)
```

is bijective. Let `u, v` be $\mathcal{X}$-morphisms $\mathcal{X}' \to \mathcal{X}''$ with
$u|_{\mathcal{U}} = v|_{\mathcal{U}}$. We show $u = v$.

**Injectivity.** The two morphisms `u, v` coincide on $\mathcal{U} \times_{\mathcal{X}} \mathcal{X}'$, which is a dense
open of $\mathcal{X}'$. By `[XII.4, no. 19, §4, cor. 5]` (an analytic-space fact: two morphisms of normal analytic
spaces agreeing on a dense open agree everywhere — analytic continuation), $u = v$ on $\mathcal{X}'$.

**Surjectivity.** Let $u : \mathcal{X}'|_{\mathcal{U}} \to \mathcal{X}''|_{\mathcal{U}}$ be a $\mathcal{U}$-morphism. We
show that $u$ extends to a morphism $\mathcal{X}' \to \mathcal{X}''$ on all of $\mathcal{X}$.

We may suppose $\mathcal{X}'$ regular. Indeed, the singular locus of $\mathcal{X}'$ is a closed analytic subset
$\mathcal{S}' \subset \mathcal{X}'$ of codimension $\geq 1$. There is an open $\mathcal{V} \subset \mathcal{X}$ with
complement $\mathcal{S} \subset \mathcal{X}$ of codimension $\geq 2$ such that
$\mathcal{V}' := \mathcal{X}' \times_{\mathcal{X}} \mathcal{V} = (regular part of \mathcal{X}')|_{\mathcal{V}}$ is
regular. Let $\mathcal{V}'' := \mathcal{X}'' \times_{\mathcal{X}} \mathcal{V}$. If the proposition is proved for the
regular $\mathcal{V}'$, the extension of $u|_{\mathcal{V}'}$ to a morphism $\mathcal{V}' \to \mathcal{V}''$ is given.

Then: with the morphism of $\mathcal{O}_{\mathcal{V}}$-algebras

```text
g''_* 𝒪_{𝓥''}  →  g'_* 𝒪_{𝓥'}
```

associated to the extended morphism $\mathcal{V}' \to \mathcal{V}''$, where `g', g''` are the projections, one deduces a
morphism

```text
i_* g''_* 𝒪_{𝓥''}  →  i_* g'_* 𝒪_{𝓥'},
```

where $i : \mathcal{V} \hookrightarrow \mathcal{X}$ is the inclusion. Using the iso
$i_{*}' \mathcal{O}_{\mathcal{V}'} \simeq \mathcal{O}_{\mathcal{X}'}$ and
$i_{*}'' \mathcal{O}_{\mathcal{V}''} \simeq \mathcal{O}_{\mathcal{X}''}$ (`serre-prolongement-faisceaux`, applied to the
codim-≥-2 complement), we deduce a morphism of $\mathcal{O}_{\mathcal{X}}$-algebras

```text
f''_* 𝒪_{𝓧''}  →  f'_* 𝒪_{𝓧'},
```

hence the desired morphism $\mathcal{X}' \to \mathcal{X}''$ (analytic spectra reverse the arrow).

So suppose $\mathcal{X}'$ regular. Let $\mathcal{U}' := \mathcal{U} \times_{\mathcal{X}} \mathcal{X}'$. Let
$\mathcal{Y}' := \mathcal{X}' - \mathcal{U}'$ (a closed analytic subset of $\mathcal{X}'$, viewed as a reduced analytic
subspace). If $\mathcal{Y}'_{1}$ is the singular closed subset of $\mathcal{Y}'$, then
$\dim \mathcal{Y}'_{1} < \dim \mathcal{Y}'$ (Grauert–Remmert). By induction on $\dim \mathcal{Y}'$, we may suppose
$\mathcal{Y}'$ is **smooth**.

Since the question is local on $\mathcal{Y}'$ (it suffices to extend $u$ to an open neighbourhood of each point of
$\mathcal{Y}'$), we may by the implicit function theorem suppose $\mathcal{X}'$ is an open ball in $\mathbb{C}^{n}$ and
$\mathcal{Y}'$ is the closed subset defined by the vanishing of the first $p$ coordinate functions
$z_{1}, \cdots, z_{p}$ ($0 \leq p \leq n$).

To $u$ we associate a section $s$ of

```text
p_2 : 𝓧' ×_𝓧 𝓧''  →  𝓧'
```

over $\mathcal{U}'$. After restricting $\mathcal{X}'$ if necessary, we may suppose
$(p_{2})_{*}(\mathcal{O}_{\mathcal{X}' \times_{\mathcal{X}} \mathcal{X}''})$ is generated by elements
$x_{1}, \cdots, x_{q} \in \Gamma(\mathcal{X}', (p_{2})_{*} \mathcal{O}_{\mathcal{X}' \times_{\mathcal{X}} \mathcal{X}''})$
(finite generation: $\mathcal{X}''$ is finite over $\mathcal{X}$, so
$p_{2} : \mathcal{X}' \times_{\mathcal{X}} \mathcal{X}'' \to \mathcal{X}'$ is finite; the algebra
$(p_{2})_{*} \mathcal{O}_{\mathcal{X}' \times_{\mathcal{X}} \mathcal{X}''}$ is coherent over
$\mathcal{O}_{\mathcal{X}'}$ and locally finitely generated).

Let $u_{1}, \cdots, u_{q} \in \Gamma(\mathcal{U}', \mathcal{O}_{\mathcal{X}'})$ be the images by $s$ of
$x_{1}|_{\mathcal{U}'}, \cdots, x_{q}|_{\mathcal{U}'}$. The statement "$s$ extends to $\mathcal{X}'$" is equivalent to
"each $u_{i}$ extends to a section of $\Gamma(\mathcal{X}', \mathcal{O}_{\mathcal{X}'})$".

But $\mathcal{X}'' \to \mathcal{X}'$ is finite, so each $u_{i}$ is *integral* over the holomorphic functions on
$\mathcal{X}'$. In coordinates, each $u_{i}$ is a Laurent series in $z_{1}, \cdots, z_{p}$ with coefficients that are
convergent power series in $z_{p+1}, \cdots, z_{n}$, and satisfies an integral-dependence relation. Integrality forces
the Laurent series to have *no negative powers*: a Laurent series satisfying a monic polynomial equation over
holomorphic functions on a neighbourhood of the origin has only non-negative terms (Riemann removable singularity in
several variables). Hence $u_{i}$ is a convergent power series in $z_{1}, \cdots, z_{n}$, and extends to $\mathcal{X}'$.

This proves the extension, hence the surjectivity. ∎

> **Slogan.** *On a normal analytic space, a finite normal cover is recoverable from its restriction to a dense open.*
> The proof routes through (i) reduction to the regular case via `serre-prolongement-faisceaux`, (ii) the implicit
> function theorem to pick coordinates, (iii) integrality and Riemann removable singularity to upgrade Laurent series to
> power series.

______________________________________________________________________

## §XII.5.4 — The Grauert–Remmert theorem

<!-- source: XII.5.4 -->

### Theorem XII.5.4 — Grauert–Remmert: existence of normal extension

<!-- source: XII.5.4 -->

**Theorem XII.5.4 (Grauert–Remmert).** Let $\mathcal{X}$ be a normal complex analytic space, and let
$\mathcal{Y} \subset \mathcal{X}$ be a closed analytic subset such that $\mathcal{U} := \mathcal{X} - \mathcal{Y}$ is
*dense* in $\mathcal{X}$. Let $\mathcal{U}'$ be a normal finite covering of $\mathcal{U}$. Suppose there exists a rare
closed analytic subset $\mathcal{S} \subset \mathcal{X}$ such that the restriction of $\mathcal{U}'$ to
$\mathcal{U} - \mathcal{U} \cap \mathcal{S}$ is *étale*. Then there exists a normal finite covering
$\mathcal{X}' \to \mathcal{X}$ extending $\mathcal{U}'$, and $\mathcal{X}'$ is unique up to isomorphism.

*This result says:* a normal finite covering of an open subset, étale away from a thin subset, extends uniquely to a
normal finite covering of the whole space. The étale-away-from-thin hypothesis is essential (XII.5.5 warning).

**Proof.** *Uniqueness* follows from XII.5.3.

*Existence.* The problem of extending $\mathcal{U}'$ is local on $\mathcal{X}$. We may suppose $\mathcal{U}$ regular
(the singular locus of $\mathcal{U}$ is a rare closed analytic subset, and we replace $\mathcal{U}$ by its regular part)
and $\mathcal{U}'$ étale over $\mathcal{U}$ (by shrinking $\mathcal{U}$ further to the étale locus).

Let $y \in \mathcal{X} - \mathcal{U}$. We show $\mathcal{U}'$ extends to a neighbourhood of $y$. After restricting
$\mathcal{X}$ to an open neighbourhood of $y$, by **Hironaka resolution of singularities** (`hironaka-resolution`) we
find a regular analytic space $\mathcal{X}_{1}$ and a projective morphism

$$
f : \mathcal{X}_{1}  \to  \mathcal{X}
$$

inducing by restriction to $\mathcal{U}$ an iso $\mathcal{U}_{1} := f^{-1}(\mathcal{U}) \simeq \mathcal{U}$, such that
$\mathcal{U}_{1}$ is the complement in $\mathcal{X}_{1}$ of a *divisor with normal crossings*.

We show $\mathcal{U}'$ extends to a normal finite covering of $\mathcal{X}_{1}$. Since the question is local on
$\mathcal{X}_{1}$, we may suppose $\mathcal{X}_{1}$ is an open ball in some $\mathbb{C}^{n}$ and
$\mathcal{X}_{1} - \mathcal{U}_{1}$ is defined by the vanishing of the first $p$ coordinate functions
$z_{1}, \cdots, z_{p}$, with $0 \leq p \leq n$.

The étale covering $\mathcal{U}'$ of $\mathcal{U}_{1}$ is a quotient of a *Kummer-type* covering

```text
𝓤_2  :=  𝓤_1[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

by a subgroup $H$ of the Galois group $\mathbb{Z}/n_{1}\mathbb{Z} \times \cdots \times \mathbb{Z}/n_{p}\mathbb{Z}$ (the
local model of $\pi^{top}_{1}(\mathcal{U}_{1}) = \mathbb{Z}^{p}$).

The covering $\mathcal{U}_{2}$ extends naturally to the regular finite covering

```text
𝓧_2  :=  𝓧_1[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

of $\mathcal{X}_{1}$ (now over the whole ball, not just the complement of the normal-crossings divisor). The group $H$
acts on $\mathcal{X}_{2}$. Define

$$
\mathcal{X}'_{1}  :=  \mathcal{X}_{2} / H,
$$

a normal finite covering of $\mathcal{X}_{1}$ extending $\mathcal{U}'$.

Now push forward along $f : \mathcal{X}_{1} \to \mathcal{X}$. Let $\mathcal{F}_{1}$ be the coherent analytic
$\mathcal{O}_{\mathcal{X}_{1}}$-algebra defining $\mathcal{X}'_{1}$. By the **Grauert–Remmert finiteness theorem**
(`grauert-remmert-coherence`, the analytic analogue of the EGA III coherence-of-direct-images theorem for proper
morphisms), $f_{*} \mathcal{F}_{1}$ is a coherent analytic $\mathcal{O}_{\mathcal{X}}$-algebra. Take the analytic
spectrum:

$$
\mathcal{X}'  :=  \text{Spec}_{an}(f_{*} \mathcal{F}_{1}).
$$

This is a finite covering of $\mathcal{X}$ (because $f_{*} \mathcal{F}_{1}$ is coherent) extending $\mathcal{U}'$
(because $f_{*} \mathcal{F}_{1}|_{\mathcal{U}} \simeq \mathcal{U}'$-algebra by construction). It is normal because
$\mathcal{X}'_{1}$ is regular (a finite cover of a regular space by a regular space is normal). ∎

> **Slogan.** *Grauert–Remmert: a normal-finite-cover defined on $\mathcal{U}$, étale on a thin-complement, extends
> uniquely to a normal-finite-cover of $\mathcal{X}$.* The proof routes through Hironaka resolution + local Kummer +
> pushforward of coherent analytic algebras (Grauert–Remmert finiteness).

### Remark XII.5.5 — the étale-locus hypothesis is essential

<!-- source: XII.5.5 -->

**Remark XII.5.5.** The hypothesis in XII.5.4 that $\mathcal{U}'$ is *étale away from a rare closed analytic subset*
cannot be removed.

**Counterexample.** Let $\mathcal{X} := \{ z \in \mathbb{C} : |z| < 1 \}$ be the unit disc, and let
$\mathcal{U} := \mathcal{X} - \{0\}$. Define

```text
𝓤'  :=  𝓤[T] / (T^2 − sin(1/z)),
```

the analytic double cover of $\mathcal{U}$ branched at the zeros of $\sin(1/z)$.

Then $\mathcal{U}'$ is a normal finite covering of $\mathcal{U}$. But $\mathcal{U}'$ does *not* extend to a finite
covering of $\mathcal{X}$. Indeed, suppose $\mathcal{U}'$ extended to a finite covering $\mathcal{X}' \to \mathcal{X}$.
The locus of points of $\mathcal{X}$ where $\mathcal{X}' \to \mathcal{X}$ is not étale is a closed analytic subset of
$\mathcal{X}$. This locus contains all points $z \in \mathcal{X}$ with $\sin(1/z) = 0$, i.e. all points $z = 1/(n\pi)$
for $n \in \mathbb{Z}_{\geq 1}$. But this set has the origin $z = 0$ as an accumulation point — a closed analytic subset
of $\mathcal{X}$ cannot have an accumulation point in its interior. Contradiction.

The pathology here is that $\mathcal{U}'$ is *not étale away from a rare subset*: the non-étale locus is the zero set of
$\sin(1/z)$, which accumulates at the origin and so is not contained in any rare closed analytic subset of
$\mathcal{X}$.

#### Strengthening for codimension ≥ 2.

When $codim_{\mathcal{X}}(\mathcal{X} - \mathcal{U}) \geq 2$, the étale-locus hypothesis on $\mathcal{S}$ can be dropped
from XII.5.4. Indeed: suppose $\mathcal{U}'$ is a normal finite covering of $\mathcal{U}$ without the étale hypothesis.
By the **Remmert–Stein theorem** (analytic extension of subvarieties of codimension $\geq 2$), the locus of points where
$\mathcal{U}' \to \mathcal{U}$ is not étale is the trace on $\mathcal{U}$ of a divisor of $\mathcal{X}$. We may then
suppose $\mathcal{U}$ regular (the singular locus of $\mathcal{U}$ is part of the boundary when $codim \geq 2$). The
locus of points of $\mathcal{U}$ where $\mathcal{U}' \to \mathcal{U}$ is not étale is a divisor of $\mathcal{U}$, and it
follows from Remmert–Stein that it is the trace on $\mathcal{U}$ of a divisor of $\mathcal{X}$. In this codim-≥-2 case,
taking $\mathcal{X}' := \text{Spec}_{an}(i_{*} \mathcal{A})$, where $\mathcal{A}$ is the coherent
$\mathcal{O}_{\mathcal{U}}$-algebra such that $\mathcal{U}' = \text{Spec}_{an}(\mathcal{A})$, gives the desired
extension; $i_{*} \mathcal{A}$ is coherent by `serre-prolongement-faisceaux` (`[XII.11, no. 1, th. 1]`).

> **Slogan.** *Normal-finite-cover extension is automatic across thin subsets (under the étale hypothesis); the
> hypothesis can be dropped when the boundary has codim $\geq 2$.* The $T^{2} - \sin(1/z)$ example pins down the precise
> limit.

______________________________________________________________________

## §XII.5.5 — Raynaud's 2003 remark on non-residually-finite $\pi_{1}$

<!-- source: XII.5.6 -->

### Remark XII.5.6 — Higman groups and the failure of $\pi^{top}_{1} \to \pi^{\acute{e}}_{1}t$ to be injective

<!-- source: XII.5.6 -->

**Remark XII.5.6 (M. Raynaud, added in 2003).** There exist nontrivial finitely-presented groups $G$ having no proper
subgroup of finite index. For example, **G. Higman's group** (`higman-non-residually-finite`; cf. J.-P. Serre, _Arbres
et amalgames_, Astérisque **46**, prop. 6, ch. I §1).

Consequently, if such a group $G$ could be realised as the topological fundamental group of a $\mathbb{C}$-scheme $V$
locally of finite type — say smooth and projective — then the analytic space $V^{an}$ would *not* be topologically
simply connected ($\pi^{top}_{1}(V^{an}) = G \neq 1$), but $V$ would be *algebraically simply connected*
(`π_1^ét(V) = π̂_1^top(V^an) = profinite completion of G = 1`, by XII.5.2 and the fact that $G$ has trivial profinite
completion). At present *no such $V$ is known* — the existence of a smooth proper $\mathbb{C}$-variety with Higman
fundamental group is an open problem.

Let us nevertheless mention that **D. Toledo** (`toledo-non-residually-finite-pi1`) constructed smooth projective
$\mathbb{C}$-schemes $V$ whose topological fundamental group $\pi^{top}_{1}(V^{an})$ is **not separated** for the
topology of subgroups of finite index — i.e. $\pi^{top}_{1}(V^{an})$ is not residually finite. The natural map

$$
\pi^{top}_{1}(V^{an})  \to  \pi^{\acute{e}}_{1}t(V)
$$

(induced by XII.5.2 and the universal property of profinite completion) is therefore *not injective*: it kills the
intersection of all finite-index subgroups of $\pi^{top}_{1}(V^{an})$, which is non-trivial when $\pi^{top}_{1}$ is not
residually finite.

> **Slogan.** *$\pi^{\acute{e}}_{1}t(V)$ is the *profinite* completion of $\pi^{top}_{1}(V^{an})$, not
> $\pi^{top}_{1}(V^{an})$ itself.*

#### Aside (the historical context).

The historical context here is striking. In 1960, when SGA 1 was written, it was unclear how much the étale fundamental
group could "see" — whether it could distinguish, for example, surfaces of different geometric behaviour over
$\mathbb{C}$. The XII.5.2 result was the first clear statement that the étale $\pi_{1}$ *recovers* the profinite
information of the topological $\pi_{1}$.

Toledo's 1993 result and Raynaud's 2003 remark add the sharp boundary: the étale $\pi_{1}$ recovers *only* the profinite
information, not the full topological $\pi_{1}$. There exist smooth proper $\mathbb{C}$-varieties whose topological
$\pi_{1}$ is not residually finite, and for those the étale $\pi_{1}$ strictly *under-determines* the topological
$\pi_{1}$. The Higman conjecture sharpens this further: there might exist smooth proper $\mathbb{C}$-varieties with
trivial étale $\pi_{1}$ and yet non-trivial topological $\pi_{1}$. As of 2026 no such example is known, but the
existence remains open.

______________________________________________________________________

## §XII.5.6 — Closing pointers and the gentle SGA closing

<!-- source: XII.5 -->

#### File 50's transcendental method = XII.5.2 + topological surface group.

The **transcendental method** of file 50 (X.2.6) — the calculation of $\pi^{\acute{e}}_{1}t$ for a smooth proper curve
of any genus $g$ in any characteristic, by lifting to characteristic 0 via Witt vectors, base-changing to $\mathbb{C}$,
and applying the surface-group presentation
$\pi^{top}_{1}(\Sigma_{g}) = \langle s_{1}, \cdots, s_{g}, t_{1}, \cdots, t_{g} | \prod [s_{i}, t_{i}] = 1\rangle$ — is
exactly **XII.5.2 applied to the analytic-side computation of $\pi^{top}_{1}(\Sigma_{g})$**.

This is the "deep" use of GAGA in SGA 1: not just as a *property* dictionary (file 58) or *cohomological* comparison
(file 59), but as a *transcendental method for computing $\pi^{\acute{e}}_{1}t$* in characteristic $p$.

#### Forward-pointer to gentle Exposé XIII and SGA 4.

The next gentle pass — files 61–64 — covers **Exposé XIII** (cohomological properness of sheaves of sets and of
non-commutative groups). Exposé XIII is the only exposé in SGA 1 that genuinely depends on **SGA 4** (étale cohomology)
and on **SGA 5 II** (cohomologically proper morphisms in higher dimension). Files 61–64 quote both as a standing bridge
and prove the SGA-1-internal content in the gentle voice: cohomological properness of the tame $R^{1}$ along a
normal-crossings divisor (XIII.2.4); the tame fundamental group of an open curve (XIII.2.12); the étale homotopy exact
sequence and the Künneth formula for $\pi^{p'}_{1}$ (XIII.4.1, XIII.4.6); and the absolute Abhyankar lemma
(XIII.5.1–XIII.5.2).

SGA 4 itself is the next chapter: the full étale topology, derived functor $H^{i}_{et}$, the proper-base-change theorem
for étale sheaves (the étale-cohomology analogue of XIII's coherent version), the smooth-base-change theorem, ℓ-adic
cohomology, the Lefschetz trace formula in characteristic $p$. The XII.5.1 + XII.5.2 results of this file are *the
input* SGA 4 takes for granted on the étale-fundamental-group side; everything in SGA 4 beyond is the topological /
cohomological / coefficient-level upgrade.

> **Final slogan for file 60 (and for the gentle Exposé XII).** *Finite étale coverings of a $\mathbb{C}$-scheme $X$ and
> of its analytification $X^{an}$ are the same, in a precise and effective way; the étale fundamental group is the
> profinite completion of the topological fundamental group.* The Riemann existence theorem (XII.5.1) is the analytic
> foundation; the $\pi_{1}$ comparison (XII.5.2) is the corollary that powers the transcendental method of file 50; the
> Grauert–Remmert extension theorem (XII.5.4) and Hironaka resolution are the analytic tools that fuel the proof.

______________________________________________________________________

## Closing of file 60 (and of the gentle Exposé XII)

With this file, the gentle SGA pass through **Exposé XII — Algebraic Geometry and Analytic Geometry** is complete (files
57–60):

- **File 57 (§XII.1)** — the analytification functor $X \mapsto X^{an}$ and its representing universal property;
  bijection on $\mathbb{C}$-points; completion isomorphism
  $\hat{\mathcal{O}}_{X, \phi(x)} \simeq \hat{\mathcal{O}}_{X^{an}, x}$; flatness of $\phi$; functoriality (commuting
  with fibre products); the inverse-image functor $F \mapsto F^{an} = \phi^{*} F$ on coherent sheaves, exact, faithful,
  and conservative.
- **File 58 (§§XII.2–XII.3)** — the property dictionaries: eight scheme-level properties transfer between $X$ and
  $X^{an}$; eleven morphism-level properties without finite-type assumption; six more under a finite-type hypothesis;
  closure / open / dense / $\pi_{0}$ agreement; XII.2.5 connectedness lemma for normal analytic spaces.
- **File 59 (§XII.4)** — cohomological GAGA: the comparison map
  $\theta_{p} : (R^{p} f_{*} F)^{an} \to R^{p} f^{an}_{*}(F^{an})$ is an iso for $f$ proper and $F$ coherent;
  specialised to absolute cohomology; specialised to coherent-sheaf categories; specialised to morphism sets and to
  finite (étale) coverings of proper schemes.
- **File 60 (§XII.5)** — the Riemann existence theorem $\Psi : X' \mapsto X'^{an}$ is an equivalence of finite-étale
  categories; the $\pi_{1}$ comparison $\pi^{\acute{e}}_{1}t(X, \phi(x)) \simeq \hat{\pi}^{top}_{1}(X^{an}, x)$; XII.5.3
  normal-cover extension; XII.5.4 Grauert–Remmert; XII.5.5 obstruction example; XII.5.6 Raynaud 2003 remark on Higman /
  Toledo.

The **gentle SGA project — as of files 52–60 — now covers Exposés I, II, III, IV, V, VI, VIII, IX, X, XI, XII**. Exposé
**XIII (cohomological properness)** of SGA 1 is files 61–64.
