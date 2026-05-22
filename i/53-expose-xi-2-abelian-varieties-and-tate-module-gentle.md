# Rewritten Exposé XI, section XI.2 — abelian varieties and the Tate module

<!-- source: XI.2 -->

## What this file is about

A doughnut surface — and its higher-dimensional cousins — is a space whose points can be added, addition like on a
torus, wrapping in every direction. The two-dimensional doughnut has two independent loops around it, the
three-dimensional version has three, and the count rises with the dimension. Abelian varieties are the algebraic
counterparts: compact geometric objects with the same kind of addition, and by analogy they should carry equally rich
fundamental groups.

Over a typical field, the analogy holds exactly and the loop count matches the topology. Over a field of prime
characteristic the count drops at that single prime. Some of the would-be loops slip beneath the radar of the standard
algebraic tools — they live on points that have collapsed together rather than separated. Widening the notion of cover,
due to Nori, recovers the missing information. The closing dictionary lines up three pictures of the same object.

Projective spaces, rational varieties, and rationally connected varieties (file 52) sit at one extreme of the
$\pi_{1}$-landscape: they have *small* fundamental groups, often trivial. **Abelian varieties** sit at the other
extreme. They are the *$\pi_{1}$-richest* proper smooth varieties: for an abelian variety $A$ of dimension $g$ over an
algebraically closed field $k$, the étale fundamental group $\pi_{1}(A)$ is determined by the kernels of multiplication-
by-$n$ and has rank `2g` away from the characteristic of $k$. The classical computation, due jointly to Serre and Lang,
is the **Serre–Lang theorem**:

```text
π₁(A) ≃ T·(A) := lim_n _nA(k),
```

where the limit is taken along multiplication-by-$s$ transition maps ${}_{ns}A \to {}_{nA}$. The right-hand side is the
**Tate module** of $A$.

The Serre–Lang theorem has two qualifications. First, the étale fundamental group $\pi_{1}(A)$ is **commutative** — a
purely formal consequence of the fact that $\pi_{1}$ is a product-preserving functor on pointed proper schemes, hence
sends group objects to group objects, hence sends *commutative* group objects (which abelian varieties are by rigidity)
to commutative group objects. Second, the rank of $T\cdot(A)$ at the prime $p = char(k)$ is *not* `2g` — it is
$\nu \leq g$, the **$p$-rank** of $A$. The étale fundamental group of an abelian variety in characteristic $p$ sees only
the *étale quotient* of the multiplication-by-$p^{r}$ kernels; the infinitesimal part is invisible.

This file (gentle Exposé XI §XI.2) reproduces the Serre–Lang theorem and Weil's structure of $T_{\ell}(A)$ in the gentle
voice (§§XI.2.1–XI.2.4), and then gives a **full gentle treatment** of the **true fundamental group** that Grothendieck
pointed at in the SGA source. The true fundamental group $\pi^{true}_{1}(A) := \lim_{n} {}_{nA}$ (with ${}_{nA}$ as a
finite *flat* group scheme, not as the underlying finite étale set) has rank `2g` at *every* prime — there is no drop at
$p$. This pro-finite-group-scheme is exactly **Nori's fundamental group scheme** $\pi^{N}_{1}$, defined for any proper
connected reduced $k$-scheme $X$ and classifying principal bundles for finite (possibly non-étale) group schemes $G$
over $k$. The Esnault–Hai Tannakian recasting and the role of essentially finite vector bundles round out the gentle
treatment in §XI.2.5.

The lesson by the end: **the abelian case is exactly where the étale $\pi_{1}$ is "wrong" in characteristic $p$ — and
where the flat / Nori $\pi_{1}$ is "right".** The drop at $p$ recorded by the $p$-rank $\nu$ is not a fiction of the
proof method; it is the étale fundamental group genuinely missing infinitesimal information that the flat fundamental
group captures.

______________________________________________________________________

## §XI.2.1 — Serre's primitive-elements theorem: $Ext(A, G) \simeq H^{1}(A, G)$

<!-- source: XI.2 -->

### Setup

<!-- source: XI.2 -->

Throughout this section, let $k$ be an algebraically closed field, $A$ an **abelian variety** over $k$ (proper smooth
geometrically connected $k$-group scheme), and $G$ a finite commutative group scheme over $k$. The group schemes we care
about most are:

- $G = (\mathbb{Z}/n\mathbb{Z})_{k}$, the constant étale group scheme of order $n$;
- $G = \mu_{n, k}$, the Kummer group scheme of rank $n$ (kernel of $n$-th power on $\mathbb{G}_{m, k}$);
- $G = \alpha_{p}$, the infinitesimal group scheme $\operatorname{Spec} k[t] / (t^{p})$ in char $p$.

Define two natural groups:

- $Ext(A, G)$ = **isomorphism classes of commutative extensions** $0 \to G \to E \to A \to 0$ in the category of
  commutative $k$-group schemes;
- $H^{1}(A, G)$ = **isomorphism classes of principal $G$-bundles** on $A$ (in the fpqc sense — equivalently, in the
  étale sense for $G$ étale, which covers $G = \mathbb{Z}/n\mathbb{Z}$ and $G = \mu_{n}$ with $n$ invertible in $k$).

There is a canonical homomorphism

```text
Ext(A, G) → H¹(A, G), \qquad [E] ↦ [E \text{ as principal } G\text{-bundle over } A]
```

obtained by forgetting the group structure of the extension and remembering only the principal-$G$-bundle structure.

### Theorem XI.2.1 — Ext ↪ H¹ has image the primitive elements

<!-- source: XI.2 -->

**Theorem XI.2.1 (Serre).** Let $A$ be an abelian variety over algebraically closed $k$, $G$ a finite commutative group
scheme over $k$. The canonical map $Ext(A, G) \to H^{1}(A, G)$ is **injective**, and its **image** is the set of
**primitive** classes — those $\xi \in H^{1}(A, G)$ for which

$$
\pi*(\xi) = pr_{1}*(\xi) + pr_{2}*(\xi)
$$

in $H^{1}(A \times A, G)$, where $\pi : A \times A \to A$ is the composition law, $pr_{1}, pr_{2} : A \times A \to A$
are the projections, and `+` is the group operation on $H^{1}$ induced by the commutative group structure of $G$.

*This result says:* an extension structure on a principal $G$-bundle $E \to A$ is determined by — and amounts to — a
compatibility of $E$ with the multiplication on $A$. The compatibility is exactly the **primitive** condition.

#### Heuristic.

For $A$ an abelian variety and $E \to A$ a connected principal $G$-bundle, *pointed at the origin* of $A$, there is in
principle a *canonical* group structure on $E$ extending the right $G$-action: the unique structure making the
projection $E \to A$ a homomorphism of group schemes. The Serre primitivity condition
$\pi*(\xi) = pr_{1}*(\xi) + pr_{2}*(\xi)$ captures exactly when this canonical structure exists — and it always does, as
we will see in §XI.2.2 below using the product formula X.1.7.

#### Proof of XI.2.1.

The full proof is in Serre, *Groupes algébriques et corps de classes*, Ch. VII Theorem 5 (appendix
[`serre-groupes-algebriques-class-fields`](appendix-black-boxes.md#serre-groupes-algebriques-class-fields)). Serre
states the result only for $G$ linear connected smooth; for our purposes ($G$ finite commutative) we need a slight
extension, which we sketch.

**Step 1 — Injectivity.** Suppose $E_{1}, E_{2}$ are commutative extensions of $A$ by $G$ that are isomorphic as
principal $G$-bundles via an isomorphism $\phi : E_{1} \to E_{2}$. We must show $\phi$ is automatically a group-scheme
isomorphism.

Since $A$ is proper connected, every morphism $A \to E_{2}$ that maps the origin of $A$ to the origin of `E_2` is a
**group homomorphism** (this is **Mumford's rigidity lemma** for morphisms of abelian varieties; for a sketch: the
difference $\phi \circ \mu_{E_{1}} - \mu_{E_{2}} \circ (\phi \times \phi) : A \times A \to E_{2}$ is a morphism sending
`(0, 0)` to `0`, and any such morphism between abelian varieties factors through `0` — see Mumford TIFR Ch. II Thm. 1,
appendix [`mumford-abelian-varieties`](appendix-black-boxes.md#mumford-abelian-varieties)). Applying this to the
underlying abelian-variety structure on `E_1` and `E_2` (or rather to their sections of the projections to $A$), one
concludes $\phi$ is a group homomorphism. Hence the two commutative extensions are isomorphic as extensions.

**Step 2 — Image is primitive.** For $\xi \in Ext(A, G)$, the extension $E \hookrightarrow A \times A$ pulled back along
the multiplication $\pi : A \times A \to A$ is the sum of the pull-backs along $pr_{1}, pr_{2}$, because $E$ is a
*homomorphism* of group schemes over $A \times A$ between $(pr_{1} + pr_{2})^{*}(E)$ and $\pi^{*}(E)$. So
$\pi*(\xi) = pr_{1}*(\xi) + pr_{2}*(\xi)$.

**Step 3 — Every primitive class lifts.** Conversely, given a primitive principal $G$-bundle $E \to A$, the primitivity
condition gives a morphism $E \times_{A} E \to E$ (a "multiplication" on $E$) commuting with the right $G$-action.
Together with the section $0 \in A(k) \hookrightarrow E(k)$ (or rather, a fixed point in the fibre `E_0` over
$0 \in A$), this constructs a commutative group-scheme structure on $E$ making $E \to A$ a homomorphism. ∎

> **Slogan.** *$Ext(A, G) \subset H^{1}(A, G)$ cuts out exactly the primitive classes.* Equivalently: a principal
> $G$-bundle on $A$ is an extension of $A$ by $G$ iff its $H^{1}$-class is primitive under multiplication.

______________________________________________________________________

## §XI.2.2 — Every class is primitive: $Ext(A, G) \simeq H^{1}(A, G)$

<!-- source: XI.2 -->

### Corollary XI.2.2 — every $H^{1}(A, G)$ class is primitive

<!-- source: XI.2 -->

**Corollary XI.2.2.** For $A$ an abelian variety over algebraically closed $k$ and $G$ a finite commutative group scheme
over $k$, **every** class in $H^{1}(A, G)$ is primitive. Hence the canonical injection of XI.2.1 is an **isomorphism**:

```text
Ext(A, G) ≃ H¹(A, G).
```

*This result says:* every principal $G$-bundle on $A$, pointed at the origin, has a canonical group-scheme structure
making it an extension of $A$. Equivalently: every connected finite étale cover of an abelian variety is itself an
abelian variety (an *isogeny* $A' \to A$).

**Proof.** Interpret $H^{1}(A, G) = \operatorname{Hom}_{cont}(\pi_{1}(A), G)$ (for $G$ étale; for $G$ non-étale we use
the Nori fundamental group $\pi^{N}_{1}$, see §XI.2.5; the argument is unchanged). The primitivity condition
$\pi*(\xi) = pr_{1}*(\xi) + pr_{2}*(\xi)$ becomes, in terms of the homomorphism $\phi : \pi_{1}(A) \to G$,

```text
φ ∘ (π_*) = φ ∘ (pr_1)_* + φ ∘ (pr_2)_*,
```

where $\pi_{*}, (pr_{1})_{*}, (pr_{2})_{*}: \pi_{1}(A \times A) \to \pi_{1}(A)$ are the induced maps. Using the
**product formula** X.1.7 (file 48):

```text
π₁(A × A) ≃ π₁(A) × π₁(A),
```

with $(pr_{1})_{*}, (pr_{2})_{*}$ the two projections and $\pi_{*}$ the addition map
$+ : \pi_{1}(A) \times \pi_{1}(A) \to \pi_{1}(A)$ (using that $\pi_{1}$ of a group scheme has a canonical group
structure). Then $\phi \circ +(x, y) = \phi(x) + \phi(y)$ for any *homomorphism* $\phi$. So the primitivity condition is
**automatic** — it just says $\phi$ is a homomorphism, which it is by construction. ∎

> **Slogan.** *Every principal $G$-bundle on an abelian variety, pointed at the origin, is canonically an isogeny.* The
> product formula X.1.7 forces every $H^{1}(A, G)$-class to be primitive.

#### Consequence — connected covers are abelian varieties.

If $A' \to A$ is a connected finite étale cover of an abelian variety, then by XI.2.2 it carries a canonical
abelian-variety structure with $A' \to A$ an isogeny. Hence **the étale fundamental group of an abelian variety is
generated by isogenies.** This is the geometric content of the Serre–Lang theorem (next).

______________________________________________________________________

## §XI.2.3 — Commutativity of $\pi_{1}(A)$

<!-- source: XI.2 -->

### Proposition XI.2.3 — $\pi_{1}(A)$ is commutative

<!-- source: XI.2 -->

**Proposition XI.2.3.** Let $A$ be an abelian variety over an algebraically closed field $k$. Then $\pi_{1}(A)$ is a
**commutative** profinite group.

*This result says:* the étale fundamental group of an abelian variety is abelian. This is purely a functoriality
statement, but it controls the structure of $T\cdot(A)$ in §XI.2.4 below.

**Proof.** The functor `π₁ : (\text{pointed proper smooth connected } k\text{-schemes}) → (\text{profinite groups})`
**commutes with products** by the product formula X.1.7 (file 48). A product-preserving functor sends group objects to
group objects, and sends *commutative* group objects (group objects whose multiplication is symmetric) to *commutative*
group objects.

An abelian variety $A$ is a commutative group object in `(\text{proper smooth connected } k\text{-schemes})` (by
**Mumford's rigidity theorem**, every connected group scheme proper over a field is automatically commutative — the
kernel of the commutator map $[\cdot, \cdot] : A \times A \to A$ contains the origin and hence, by rigidity, is all of
$A \times A$, so the commutator is trivial).

Applying $\pi_{1}$, the group $\pi_{1}(A)$ is therefore a commutative group object in the category of profinite groups —
i.e., it is commutative. ∎

> **Slogan.** *$\pi_{1}(A)$ is commutative.* Functoriality of $\pi_{1}$ + rigidity of abelian varieties.

#### Aside (a topological cross-check).

For $A = E_{1} \times \cdots \times E_{g}$ a product of complex elliptic curves over $\mathbb{C}$, the analytic
fundamental group is
$\pi_{1}(A^{an}) = \pi_{1}(E^{an}_{1}) \times \cdots \times \pi_{1}(E^{an}_{g}) = \mathbb{Z}^{2} \times \cdots \times \mathbb{Z}^{2} = \mathbb{Z}^{2g}$,
which is abelian. The profinite completion is $\hat{\mathbb{Z}}^{2g}$. The Serre–Lang theorem (next) recovers exactly
this profinite completion via the algebraic Tate module construction.

______________________________________________________________________

## §XI.2.4 — The Serre–Lang theorem: $\pi_{1}(A) \simeq T\cdot(A)$

<!-- source: XI.2.1 -->

### Theorem XI.2.4 — Serre–Lang: $\pi_{1}(A) \simeq T\cdot(A)$

<!-- source: XI.2.1 -->

For each positive integer $n$, let

- ${}_{nA} := \ker(n_{A} : A \to A)$, the kernel of multiplication by $n$ (a finite flat group scheme over $k$, of order
  $n^{2g}$ where $g = \dim A$);
- $K_{n} := {}_{nA}(k) =$ the **étale group** underlying ${}_{nA}$, equivalently the geometric $k$-points of ${}_{nA}$.

For each prime $\ell$, define the **$\ell$-adic Tate module**:

$$
T_{\ell}(A) := \lim_{r} K_{\ell^{r}},
$$

where the transition map $K_{\ell^{r+1}} \to K_{\ell^{r}}$ is multiplication by $\ell$. Define the **adelic Tate
module**:

```text
T·(A) := ∏_ℓ T_ℓ(A) = lim_n K_n,
```

where the transition map $K_{ns} \to K_{n}$ for $s \geq 1$ is multiplication by $s$.

**Theorem XI.2.4 (Serre–Lang).** *(Labelled `XI.2.1` in the SGA source.)* The canonical map

$$
\pi_{1}(A) \to T\cdot(A)
$$

is an **isomorphism** of profinite abelian groups. For each prime $\ell$, the $\ell$-primary component of $\pi_{1}(A)$
is canonically isomorphic to $T_{\ell}(A)$.

*This result says:* every connected finite étale cover of $A$ is an isogeny — specifically, a quotient of some
multiplication-by-$n$ map. The étale fundamental group is the inverse limit of these isogeny kernels.

#### Proof.

We show that every connected finite étale $A' \to A$ factors through some multiplication-by-$n$ map $n_{A} : A \to A$,
and conversely every such factorisation is a connected cover.

**Step 1.** Let $A' \to A$ be a connected finite étale cover, with degree $d$. By XI.2.2 (file 53 §XI.2.2), $A'$ carries
a canonical structure of abelian variety, with $A' \to A$ an isogeny of degree $d$.

**Step 2.** Every isogeny $A' \to A$ of degree $d$ (with $d$ prime to $char(k) = p$ if $p > 0$) factors through
$n_{A} : A \to A$ for some $n$. **Argument:** the dual isogeny $A^{\vee} \to (A')^{\vee}$ has degree $d$ (by Mumford
TIFR Ch. III, biduality and the dual-isogeny lemma; appendix
[`mumford-abelian-varieties`](appendix-black-boxes.md#mumford-abelian-varieties)), and the composition

$$
A' \to A \to A',
$$

via the dual isogeny followed by the original isogeny, is multiplication by $d$ on $A'$ (this is the
Riemann–Roch-on-abelian-varieties computation, again Mumford Ch. III). Setting $n = d$, the composition factors the
original isogeny through $n_{A}$. (For $p | d$ the argument adapts but uses flat finite group schemes rather than étale;
we treat the $p$-part separately in the next paragraph.)

**Step 3.** For each $n$, the étale cover $n_{A} : A \to A$ is connected (since $A$ is connected and $n_{A}$ is
surjective with finite étale fibre ${}_{nA}(k)$) and has Galois group ${}_{nA}(k) = K_{n}$ (acting on $A$ by translation
by $n$-torsion points). Hence $\pi_{1}(A)$ quotients onto each $K_{n}$, with compatible transitions $K_{ns} \to K_{n}$
by multiplication by $s$.

**Step 4.** Conversely, by Step 1 every connected finite étale cover factors through some $n_{A}$, so
$\pi_{1}(A) = \lim_{n} K_{n} = T\cdot(A)$. ∎

> **Slogan.** *$\pi_{1}(A) = T\cdot(A)$.* The étale fundamental group of an abelian variety is determined by the
> multiplication-by-$n$ kernels.

#### Functoriality.

For a homomorphism of abelian varieties $\alpha : A \to B$, the induced map $\alpha_{*} : \pi_{1}(A) \to \pi_{1}(B)$
corresponds via Serre– Lang to the induced map $T\cdot(\alpha) : T\cdot(A) \to T\cdot(B)$ on Tate modules. In
particular, an **endomorphism** $\alpha \in \operatorname{End}(A)$ acts on $T\cdot(A)$. The representation

```text
End(A) → End(T·(A)) ≃ End(T_ℓ(A)) × \cdots, \qquad α ↦ T·(α),
```

is called the **Weil representation** of $\operatorname{End}(A)$ (or, decomposed by primes, the $\ell$-adic Weil
representation). The Weil representation is the algebraic-geometric analogue of the action of the homology functor on a
topological space.

______________________________________________________________________

## §XI.2.5 — Weil's structure of $T_{\ell}(A)$

<!-- source: XI.2 -->

### Theorem XI.2.5 — Weil: $T_{\ell}$ is free of rank `2g` away from $p$, of rank $\nu \leq g$ at $p$

<!-- source: XI.2 -->

**Theorem XI.2.5 (Weil).** Let $A$ be an abelian variety of dimension $g$ over an algebraically closed field $k$, and
let $\ell$ be a prime. Then:

**(a)** *If $\ell \neq char(k)$:* $K_{\ell^{r}}$ is a free $\mathbb{Z}/\ell^{r} \mathbb{Z}$-module of rank `2g`. Hence
$T_{\ell}(A) \simeq \mathbb{Z}^{2g}_{\ell}$ is a free $\mathbb{Z}_{\ell}$-module of rank `2g`.

**(b)** *If $\ell = p = char(k) > 0$:* $K_{p^{r}}$ is a free $\mathbb{Z}/p^{r} \mathbb{Z}$-module of rank $\nu$, where
$0 \leq \nu \leq g$ is an integer **independent** of $r$ (called the **$p$-rank** of $A$). Hence
$T_{p}(A) \simeq \mathbb{Z}^{\nu}_{p}$.

*This result says:* the étale $\pi_{1}(A)$ has the maximum possible rank `2g` at every prime except possibly the
characteristic, where the rank $\nu$ is *bounded above* by $g$ and may *drop* relative to `2g`.

#### Proof of (a).

Multiplication-by-$n$ on an abelian variety $A$ of dimension $g$ is a **finite flat morphism of degree** $n^{2g}$. This
is a standard fact about abelian varieties — see Mumford TIFR Ch. II §6 (appendix
[`mumford-abelian-varieties`](appendix-black-boxes.md#mumford-abelian-varieties)).

For $n$ coprime to $char(k)$, multiplication-by-$n$ is also **étale** (since the differential of $n_{A}$ at any point is
multiplication by $n$ on the tangent space $T_{0} A$, and this is invertible iff $n$ is invertible in $k$).

Hence ${}_{nA}(k)$ is the underlying étale group of a finite étale group scheme of degree $n^{2g}$, and so has order
exactly $n^{2g}$. The fact that it is a *free* $\mathbb{Z}/n\mathbb{Z}$-module of rank `2g` then follows from the
structure theorem for finite abelian groups together with the divisibility hypothesis on the multiplication-by-$n$ map.

Passing to the limit gives $T_{\ell}(A) \simeq \mathbb{Z}^{2g}_{\ell}$. ∎

#### Proof of (b).

For $n = p^{r}$ with $p = char(k)$, multiplication-by-$p^{r}$ is still finite flat of degree $p^{2gr}$, but it is **no
longer étale** — the differential of $p_{A}$ at any point is multiplication by $p$, which is *zero* on the tangent space
$T_{0} A$ in characteristic $p$.

So the kernel ${}_{p^{r}}A$ is a finite *flat* group scheme of order $p^{2gr}$, but not étale. It decomposes as an
extension of an *étale* part (the part visible to $K_{p^{r}} = {}_{p^{r}}A(k)$) by an *infinitesimal* part (the
**connected component of the identity** in ${}_{p^{r}}A$ as a group scheme):

$$
0 \to ({}_{p^{r}}A)^{\circ} \to {}_{p^{r}}A \to ({}_{p^{r}}A)_{et} \to 0,
$$

where $({}_{p^{r}}A)^{\circ}$ is the (infinitesimal, hence non-étale) connected component and $({}_{p^{r}}A)_{et}$ is
the étale quotient.

The étale quotient $({}_{p^{r}}A)_{et}$ is **what $K_{p^{r}}$ sees** — its $k$-points are exactly $K_{p^{r}}$. The
integer $\nu$ is the dimension over $\mathbb{F}_{p}$ of $({}_{p^{r}}A)_{et}(k)$ as a finite $\mathbb{Z}/p^{r}$-module;
**$\nu$ does not depend on $r$** (this is the standard $p$-divisible-group computation; see Mumford TIFR Ch. IV §5–6).

The **$p$-rank $\nu$** classifies abelian varieties:

- $\nu = g$: **ordinary**. The full `2g` rank is *not* achieved in the étale picture, because the infinitesimal part of
  ${}_{p^{r}}A$ contributes nothing to $K_{p^{r}}$, but $\nu = g$ is the largest possible value. In characteristic
  $p > 0$, ordinary abelian varieties are "generic" in the sense of moduli.
- $\nu = 0$: **supersingular**. The most extreme case: the étale picture sees nothing at $p$, and all $p^{r}$-torsion is
  infinitesimal. For elliptic curves ($g = 1$), this is the case where the endomorphism ring is the maximal order in a
  quaternion algebra over $\mathbb{Q}$ ramified at $p$ and $\infty$.
- $0 < \nu < g$: **intermediate**. Genuinely interpolates between ordinary and supersingular.

#### Dimensional-jump phenomenon.

As $A$ varies in a family $\mathcal{A} \to S$ of abelian varieties over a base $S$, the $p$-primary part of
$\pi_{1}(\mathcal{A}_{s}) = T_{p}(\mathcal{A}_{s}) \simeq \mathbb{Z}^{\nu(s)}_{p}$ may **drop** as $s$ specialises to a
point with smaller $p$-rank — e.g. ordinary specialising to supersingular. This is exactly the upper-semicontinuity
X.2.3 (file 49) made concrete:

```text
ν(\eta) \geq ν(0) \qquad \text{when } 0 \text{ specialises from } \eta.
```

The drop is **real** and **necessary**: it reflects the fact that the étale fundamental group misses infinitesimal
phenomena. The next subsection (§XI.2.6 below) shows how the *flat* fundamental group restores the missing rank.

> **Slogan.** *$T_{\ell}(A) \simeq \mathbb{Z}^{2g}_{\ell}$ for $\ell \neq p$; $T_{p}(A) \simeq \mathbb{Z}^{\nu}_{p}$
> with $0 \leq \nu \leq g$.* The rank drops at $p$ because the infinitesimal part of ${}_{p^{r}}A$ is invisible to the
> étale $\pi_{1}$.

______________________________________________________________________

## §XI.2.6 — The true fundamental group: $\pi^{true}_{1}(A) = \lim {}_{nA}$ and Nori's $\pi^{N}_{1}$

<!-- source: XI.2 -->

The Serre–Lang theorem (XI.2.4) and Weil's structure (XI.2.5) together pin down the **étale** fundamental group of an
abelian variety. The drop at $p$ in characteristic $p > 0$ raises a natural question: is there a "true" fundamental
group that *doesn't* drop — one that sees the infinitesimal part of ${}_{p^{r}}A$ and has rank `2g` at every prime?

Yes. Grothendieck pointed at it in passing in the SGA source ("this suggests that the 'true' fundamental group of an
abelian variety $A$ is the pro-algebraic group $\lim_{n} {}_{nA}$"), and the systematic theory was developed by Serre
(1960 *Publ. Math. IHÉS*, the **pro-algebraic** fundamental group) and Nori (1976, 1982, the **fundamental group
scheme** $\pi^{N}_{1}$). The modern Tannakian recasting (Esnault–Hai 2008) gives the clean categorical formulation.

This section is the gentle full treatment, in five paragraphs.

### Paragraph 1 — what the étale picture misses

<!-- source: XI.2 -->

For every $n$, the **true kernel** ${}_{nA}$ is a finite flat group scheme over $k$ of degree $n^{2g}$. The
multiplication-by-$n$ morphism $n_{A} : A \to A$ is *always* finite flat of degree $n^{2g}$ (Mumford TIFR Ch. II §6),
regardless of whether $n$ is coprime to $char(k)$.

When $n$ is invertible in $k$, ${}_{nA}$ is **étale**, and the gentle SGA's Galois category framework (files 30–33)
captures it. But when $p | n$, ${}_{nA}$ has an **infinitesimal part**, and the étale fundamental group $\pi_{1}(A)$
only sees the *étale quotient* $({}_{nA})_{et}$. The infinitesimal part of ${}_{nA}$ is invisible to $\pi^{et}_{1}$.

Concretely, for $A = E$ a supersingular elliptic curve over $\bar{k}_{p}$ and $n = p$, the kernel ${}_{pE}$ is a
connected finite flat group scheme of order $p^{2}$ (it has Hopf algebra $k[x, y]/(x^{p}, y^{p})$, say). The étale
quotient $({}_{pE})_{et}$ is **trivial** — ${}_{pE}(\bar{k}) = 0$. The étale $\pi_{1}(E)$ sees no $p$-torsion at all.
But ${}_{pE}$ itself, as a flat group scheme, has order $p^{2} = p^{2g}$ and is *not* trivial.

This is the gap that the true fundamental group fills.

### Paragraph 2 — the pro-algebraic candidate $\lim_{n} {}_{nA}$

<!-- source: XI.2 -->

Define

$$
\pi^{true}_{1}(A) := \lim_{n} {{}_{nA}},
$$

where the inverse limit is taken in the category of **finite flat commutative $k$-group schemes**, with transition maps
${}_{ns}A \to {}_{nA}$ given by multiplication by $s$. This is a **pro-finite-group-scheme** over $k$, and as such sits
in a category larger than the profinite groups.

The flatness of ${}_{nA} \to S$ in families is the key technical input: when $A$ varies over a base $S$, ${}_{nA} \to S$
is **flat** of degree $n^{2g}$ for every $n$ (regardless of the residue characteristic), so the rank of
$\pi^{true}_{1}(\mathcal{A}_{s})$ is constant at $n^{2g}$-th-roots-of-unity rank — there is no drop.

For each prime $\ell$:

```text
π₁^{true}(A)[ℓ^\infty] := \lim_r {_{ℓ^r}A}
```

is a $\mathbb{Z}_{\ell}$-module of rank `2g` for *every* $\ell$ (including $\ell = p = char(k)$). The drop at $p$
recorded by the $p$-rank $\nu$ is exactly the difference between

- $T_{p}(A) = (\pi^{et}_{1}(A))_{p} \simeq \mathbb{Z}^{\nu}_{p}$ — the étale fundamental group at $p$, and
- $\pi^{true}_{1}(A)[p^{\infty}] \simeq$ a pro-finite *flat* group scheme of rank $p^{2gr}$ over $k$ at level $r$ —

with the étale-vs-flat dichotomy controlling the difference.

(Reference for this discussion: J.-P. Serre, "Groupes proalgébriques," Publ. Math. IHÉS **7** (1960), appendix
[`serre-pro-algebraic`](appendix-black-boxes.md#serre-pro-algebraic).)

### Paragraph 3 — Nori's fundamental group scheme $\pi^{N}_{1}(X, x)$

<!-- source: XI.2 -->

M. V. Nori (1976, 1982; appendix [`nori-fundamental-group`](appendix-black-boxes.md#nori-fundamental-group)) gave a
systematic construction extending the gentle "true fundamental group" to **any** proper connected reduced $k$-scheme $X$
with a chosen rational point $x \in X(k)$, where $k$ is a perfect field.

**Definition (Nori 1982).** The **Nori fundamental group scheme** $\pi^{N}_{1}(X, x)$ is the pro-finite-group-scheme
over $k$ classifying principal $G$-bundles $P \to X$ (in the fpqc sense — see file 55) for $G$ an arbitrary finite
commutative $k$-group scheme, with a marked point $\tilde{x} \in P(k)$ over $x$. Concretely: $\pi^{N}_{1}(X, x)$ is the
projective limit of the duals of finite quotients

```text
\pi_1^N(X, x) = \lim_G \text{Aut}_G(P_G),
```

where $P_{G} \to X$ is the "universal" principal $G$-bundle on $X$ (in a precise sense; this requires Tannakian
formalism — see paragraph 4).

**Key example.** For $X = A$ an abelian variety:

```text
\pi_1^N(A, 0) = \lim_n {_nA} = π_1^{true}(A) \quad \text{from paragraph 2}.
```

This is the gentle precise statement of "the true fundamental group of an abelian variety is the inverse limit of
multiplication-by-$n$ kernels."

For $X$ not an abelian variety, $\pi^{N}_{1}(X, x)$ is generally hard to compute. Some known cases:

- For $X = \mathbb{P}^{r}$, $\pi^{N}_{1}(\mathbb{P}^{r}) = 0$ (since $\mathbb{P}^{r}$ admits no non-trivial finite flat
  principal bundles, by an extension of XI.1.1 to the flat case — Mehta–Subramanian's theorem).
- For a smooth projective connected curve $X / \bar{k}_{p}$ of genus $g \geq 2$, $\pi^{N}_{1}(X)$ is genuinely larger
  than $\pi^{et}_{1}(X)$: it contains, at $p$, information about the **$F$-isocrystal structure** of
  $H^{1}(X, \mathcal{O}_{X})$ — specifically, the Newton polygon / slope filtration of the Frobenius action.

### Paragraph 4 — the Tannakian recasting (Esnault–Hai)

<!-- source: XI.2 -->

The cleanest categorical formulation of $\pi^{N}_{1}(X, x)$ uses **Tannakian duality**. H. Esnault and P. H. Hai (2008;
appendix [`esnault-hai-gauss-manin`](appendix-black-boxes.md#esnault-hai-gauss-manin)) showed:

**Theorem (Esnault–Hai 2008).** Let $X$ be a proper connected reduced $k$-scheme with a rational point $x \in X(k)$, $k$
a perfect field. The category **$\mathrm{EFin}(X)$** of **essentially finite** vector bundles on $X$ — vector bundles
$V$ admitting a non-trivial polynomial relation $P(V) = Q(V)$ in the Grothendieck ring $K_{0}(X)$ (where
$P, Q \in \mathbb{Z}[T]$ are polynomials, and $V^{\oplus i}$ and $Sym^{i} V$, $\wedge^{i} V$ are interpreted as the
relevant ring operations) — is a **neutral Tannakian category** over $k$, with fibre functor $V \mapsto V_{x}$ (fibre at
the marked point).

The **Tannakian dual** of $\mathrm{EFin}(X)$ is the **Nori fundamental group scheme** $\pi^{N}_{1}(X, x)$.

#### What this says.

The category $\mathrm{EFin}(X)$ is closed under tensor, dual, direct sum, and direct summand (the "essentially finite"
condition is preserved by all these). For $X = A$ an abelian variety, every line bundle
$L \in \operatorname{Pic}^{0}(A) = A^{\vee}(k)$ is essentially finite: $L^{\otimes n} = \mathcal{O}_{A}$ for some $n$
(namely, the order of $L$ in $A^{\vee}(k)$), so the polynomial relation $L^{n} = 1$ witnesses the essential finiteness.

The Tannakian formalism then says: knowing $\mathrm{EFin}(X)$ as a tensor category is equivalent to knowing
$\pi^{N}_{1}(X, x)$ as a pro-finite-group-scheme. This is exactly the Tannakian dictionary for finite-dimensional
representations.

The Tannakian viewpoint makes the abelian-variety computation $\pi^{N}_{1}(A, 0) = \lim_{n} {}_{nA}$ *clean*: the
essentially-finite vector bundles on $A$ are exactly the *torsion* line bundles in
$\operatorname{Pic}^{0}(A) = A^{\vee}$, with the Tannakian dual being the dual abelian variety's torsion
`\lim_n A^∨[n] = \lim_n A[n] = lim_n _nA` (using biduality $A^{\vee\vee} = A$).

### Paragraph 5 — what we have and what remains

<!-- source: XI.2 -->

To summarise the gentle treatment:

**Abelian case (well-understood).** $\pi^{N}_{1}(A, 0) = \lim_{n} {}_{nA}$, of rank `2g` at every prime $\ell$ including
$\ell = char(k) = p$. The étale $\pi_{1}(A) = T\cdot(A)$ drops at $p$ to rank $\nu \leq g$ exactly because it sees only
the étale quotient $({}_{nA})_{et}$ of the flat group scheme ${}_{nA}$. The flat / Nori $\pi^{N}_{1}$ does not drop.

**Non-abelian case (much less understood).** For $X$ not an abelian variety, $\pi^{N}_{1}(X)$ is generically *much*
larger than $\pi^{et}_{1}(X)$. For curves of genus $g \geq 2$ in char $p$, the difference is genuinely interesting and
encodes the $F$-isocrystal structure / Newton polygon of Frobenius on $H^{1}(X, \mathcal{O}_{X})$. The relevant modern
references are:

- A. Holschbach, "The fundamental group scheme of a non-reduced scheme," (PhD thesis, Essen, 2009).
- V. B. Mehta, S. Subramanian, "Nori's fundamental group scheme of a non-reduced scheme," Adv. Math. **214** (2007),
  728–740.
- See also the survey: D. Hai, "Tannakian aspects of the fundamental group scheme," in *Algebraic groups and their
  representations* (NATO ASI Ser. C. **517**, Kluwer 1998), 233–251.

**Recovery of Weil representations.** From the $p$-primary component of the true $\pi^{N}_{1}(A)$, one recovers the Weil
characteristic polynomial of an endomorphism $\alpha \in \operatorname{End}(A)$ in characteristic $p$, in a more natural
way than via Serre's pro-algebraic construction. The characteristic polynomial of $T_{\ell}(\alpha)$ for $\ell \neq p$
agrees with that of $T^{N}_{p}(\alpha)$ (the $p$-component of the **true** Tate module), so the characteristic
polynomial is independent of prime — this is the **Weil conjecture for abelian varieties** in characteristic $p$, proved
by Weil for $\ell \neq p$ and extended to $\ell = p$ via Nori-style flat fundamental groups.

> **Slogan.** *The abelian case is the simplest place where étale $\pi_{1}$ is "wrong" in char $p$ — and where the Nori
> / flat $\pi^{N}_{1}$ is "right."* The drop at $p$ recorded by the $p$-rank $\nu$ is exactly the étale fundamental
> group missing infinitesimal information.

______________________________________________________________________

## Closing of file 53

We reproduced Serre's primitivity theorem (XI.2.1), the corollary that every principal-$G$-bundle class on an abelian
variety is primitive (XI.2.2), the commutativity of $\pi_{1}(A)$ (XI.2.3), the Serre–Lang theorem
$\pi_{1}(A) \simeq T\cdot(A)$ (XI.2.4), and Weil's structure theorem for $T_{\ell}(A)$ (XI.2.5). The full gentle
treatment of the "true fundamental group" in §XI.2.6 introduced the pro-algebraic candidate $\lim_{n} {}_{nA}$, the Nori
fundamental group scheme $\pi^{N}_{1}$, and the Esnault–Hai Tannakian recasting via essentially finite vector bundles.

Next, file 54 turns to the **opposite direction**: counterexamples. The projective cone over a non-simply- connected
smooth $V$ is itself simply connected — but the contraction morphism $f : X \to \hat{C}_{V}$ is *not* separable (it is
not even flat), and the counterexample shows X.1.3 / X.1.4 / X.2.4 cannot be extended to "fibres are smooth" or
"geometrically reduced fibres". Zariski's flat counterexample (built from the Fermat surface
$x^{n} + y^{n} + z^{n} + t^{n} = 0$ with a $\mathbb{Z}/n\mathbb{Z}$-action) shows the separability hypothesis cannot be
weakened even to "flat with geometrically integral fibres". The Exposé X separability hypothesis is **sharp**.
