# Formal schemes and 𝓘-adic completion (gentle prep for Exposé III)

## What this file is about

A function near a point is captured by its value, then its slope, then its curvature, and so on. Each new derivative
records a finer piece of behaviour near the point, and the whole tower together is the Taylor expansion. Geometry has an
analogue. Inside a larger space sits a smaller piece. Around the smaller piece there is a first-order neighbourhood,
then a second-order, then a third, each fatter than the last by an infinitesimal layer. The whole tower, taken at once,
is a richer object than any single layer.

This file gives the algebra that handles such towers. It builds the right notion of limit, the right notion of space the
limit lives in, and a theorem saying when a structure carried by the entire tower comes from an honest geometric object
on the larger space. The lifting questions in the next four files all depend on it.

Sections III.5–III.7 of Exposé III work over a base scheme $S$ equipped with a coherent sheaf of ideals $\mathcal{I}$.
They construct schemes one **infinitesimal thickening at a time**: starting from data over $S_{0} := V(\mathcal{I})$
(the closed subscheme cut out by $\mathcal{I}$), they extend to data over $S_{n} := V(\mathcal{I}^{n+1})$, and finally
pass to the limit to get data over the **formal completion** `Ŝ` of $S$ along $V(\mathcal{I})$. The limit object is no
longer a scheme in the ordinary sense; it is a **formal scheme**.

This file develops just enough of the formal-scheme apparatus (EGA I §10) to support those arguments. The contrast we
need to get straight is:

> **An ordinary scheme is the spectrum of a ring. A formal scheme is the spectrum of an adic ring.** The "adic" part — a
> fixed ideal of definition and an inverse-limit structure sheaf — is what allows the formal scheme to remember the
> entire tower of thickenings simultaneously.

A reader who already knows Vakil Chapter 28 (formal functions) or EGA I §10 may skim. We rely on the language of file 03
(sheaves) and the local-completion machinery of file 04 (the completion of a noetherian local ring at its maximal
ideal). The new content is the global construction, the inverse-limit description of coherent sheaves on a formal
scheme, and the Grothendieck existence theorem that lets one **algebraize** a formal scheme back to an ordinary one.

## Recap: completion of a noetherian local ring

File 04 introduced the completion `Â` of a noetherian local ring $(A, \mathfrak{m})$ at its maximal ideal: take the
inverse limit of the quotients $A / \mathfrak{m}^{n+1}$, equipped with its natural topology where the powers of the
maximal ideal go to zero. The completion is faithfully flat over $A$ (appendix `completion-flat`). It geometrizes
neighborhoods of the closed point: `Â` is "the limit of polynomial-truncation neighborhoods of the closed point of
$\operatorname{Spec} A$."

Two extensions are needed to handle Exposé III.

- The role of the maximal ideal $\mathfrak{m} \subset A$ is played by an arbitrary ideal $\mathcal{I} \subset R$, not
  necessarily maximal — and $R$ need not be local. We are no longer just **completing at a point**; we are completing
  along a **closed subscheme**.
- The construction has to be made **functorial in schemes**: applied to $\operatorname{Spec} R$ along
  $V(\mathcal{I}) \subset \operatorname{Spec} R$, then glued across Zariski covers for non-affine bases.

## 𝓘-adic completion of a noetherian ring

### Why this construction?

Before any formula, the picture. Pick a ring $R$ and an ideal $\mathcal{I}$. The quotient $R/\mathcal{I}$ knows the
values of functions modulo the ideal — geometrically, their values along the closed subscheme $V(\mathcal{I})$. The
quotient $R/\mathcal{I}^{2}$ adds one layer: it knows values plus first-order data, the way a derivative knows a
function plus its slope. $R/\mathcal{I}^{3}$ adds second-order data. The tower

$$
R/\mathcal{I}  \leftarrow  R/\mathcal{I}^{2}  \leftarrow  R/\mathcal{I}^{3}  \leftarrow  \cdots
$$

records what a function looks like to ever-higher infinitesimal order along $V(\mathcal{I})$. Functions in $R$ itself
sit at the top; each one projects to its image at every level.

The **completion** $\hat{R}$ is what you get when you let all those infinitesimal orders accumulate into single
elements. An element of $\hat{R}$ is a coherent choice of one element in each quotient — a value, a first-order
increment, a second-order increment, and so on, each compatible with the next. The result is what $R$ becomes when every
infinitesimal series along $V(\mathcal{I})$ is allowed to converge. In analytic language, $\hat{R}$ is to $R$ what the
ring of formal power series at a point is to the ring of polynomials.

The construction packages this as an inverse limit because every step kills slightly less of the data. The connection
backward is to file 03's first-order picture: the conormal sheaf there is $\mathcal{I}/\mathcal{I}^{2}$, the first
non-trivial layer of this tower. Everything that file 03 did at order one, this construction does at all orders at once.
The reason this matters for SGA III is that several extension problems we will study are unsolvable at any finite order
but solvable in the limit; the completion is where those solutions live.

Let $R$ be a noetherian ring and $\mathcal{I} \subset R$ an ideal. The **$\mathcal{I}$-adic topology** on $R$ declares
the powers $\mathcal{I}^{n+1}$ to be a fundamental system of open neighborhoods of zero. A sequence $(f_{k})_{k \geq 0}$
in $R$ is **$\mathcal{I}$-adically Cauchy** if for every $n \geq 0$ there exists $N$ with
$f_{j} - f_{k} \in \mathcal{I}^{n+1}$ whenever $j, k \geq N$. The **$\mathcal{I}$-adic completion** is

```text
R̂ := lim_{n ← ∞} R / 𝓘^{n+1}
```

with the inverse limit topology. A topological ring is **complete** when every Cauchy sequence in its topology has a
unique limit; for the $\mathcal{I}$-adic topology, completeness is equivalent to the natural map
$R \to \lim_{n} R/\mathcal{I}^{n+1}$ being an isomorphism. It is a topological ring; the natural map $R \to \hat{R}$ is
the universal $\mathcal{I}$-adically continuous map to a complete topological ring.

For $R$ noetherian and $\mathcal{I}$ finitely generated, $\hat{R}$ is also noetherian and the map $R \to \hat{R}$ is
**flat** (the appendix row `completion-flat` covers the local case; the proof for $\hat{R}$ non-local appears in EGA 0_I
§7.6.16). The map is **faithfully flat** when restricted to the localization of $R$ at primes containing $\mathcal{I}$ —
that is, around the closed subscheme $V(\mathcal{I})$.

### The thickenings $S_{n} = \operatorname{Spec}(R/\mathcal{I}^{n+1})$

Set $S = \operatorname{Spec} R$ and $S_{n} := \operatorname{Spec}(R / \mathcal{I}^{n+1})$ for each $n \geq 0$. Then:

- The underlying topological space $|S_{n}|$ of $S_{n}$ is the closed subset $V(\mathcal{I}) \subset |S|$. **All $S_{n}$
  share the same underlying space**. They differ only in their structure sheaf: $S_{0}$ has
  $\mathcal{O}_{S_{0}} = \mathcal{O}_{S} / \mathcal{I}$, the reduced structure on $V(\mathcal{I})$ (well, possibly
  non-reduced if $\mathcal{I}$ is not radical — call it the scheme-theoretic structure on $V(\mathcal{I})$); $S_{n}$
  adds in the higher jets $\mathcal{O}_{S} / \mathcal{I}^{n+1}$.
- The closed immersions $S_{0} \hookrightarrow S_{1} \hookrightarrow S_{2} \hookrightarrow \cdots \hookrightarrow S$
  form an ascending chain. Each $S_{n} \hookrightarrow S_{n+1}$ is a **square-zero thickening** of $S_{n}$ by the sheaf
  of ideals $\mathcal{I}^{n+1} / \mathcal{I}^{n+2}$ on $S_{0}$.
- $\lim_{n} \mathcal{O}_{S_{n}} = \hat{R}$ as a sheaf on $|V(\mathcal{I})|$.

The thickenings are how we will think about formal completions: **not as a single mysterious object, but as a coherent
system of ordinary schemes indexed by infinitesimal precision $n$.**

### The completed ring $\hat{R}$

Concretely, an element of $\hat{R}$ is a sequence $(f_{n})_{n \geq 0}$ with $f_{n} \in R / \mathcal{I}^{n+1}$ and
$f_{n+1} \mapsto f_{n}$ under the projection. Equivalently, when $R = A[t_{1}, \cdots, t_{d}]$ and
$\mathcal{I} = (t_{1}, \cdots, t_{d})$, the completion $\hat{R} = A[[t_{1}, \cdots, t_{d}]]$ is the
**formal-power-series ring**: each formal series is the inverse limit of its truncations.

This recovers the most important example.

### Faithfully flat completion

For $R$ noetherian and $\mathcal{I} \subset R$ proper, the completion $R \to \hat{R}$ is flat. After localizing at any
prime $\mathfrak{p} \supset \mathcal{I}$, the completion becomes faithfully flat: $M \otimes_{R} \hat{R} = 0$ implies
$M_{\mathfrak{p}} = 0$. This licenses an important technique: **prove statements after completing along
$V(\mathcal{I})$, then descend back**. The local form of this (file 04, completion of a local ring) is
`completion-flat`.

## Formal preschemes

We have all the ingredients to define formal preschemes affinely. The geometric step is to package the inverse system
$(S_{n})$ into a single object that remembers the topology, the structure sheaf, **and** the adic ideal $\mathcal{I}$.

### $Spf \hat{R}$ as a topologically ringed space

Given a noetherian ring $\hat{R}$ complete in the $\mathcal{I}$-adic topology (write $\mathcal{I} \subset \hat{R}$ for
the closure of the original ideal — for a complete ring this is the same $\mathcal{I}$), define the **formal spectrum**

```text
Spf R̂ := (V(𝓘), 𝒪_{Spf R̂})
```

as the topologically ringed space whose underlying space is the Zariski-closed subset
$V(\mathcal{I}) \subset \operatorname{Spec} \hat{R}$ (open subsets of $V(\mathcal{I})$ are intersections with open
subsets of $\operatorname{Spec} \hat{R}$), and whose structure sheaf is

```text
𝒪_{Spf R̂} := lim_n 𝒪_{Spec(R̂ / 𝓘^{n+1})}.
```

Each $\mathcal{O}_{\operatorname{Spec}(\hat{R}/\mathcal{I}^{n+1})}$ is an ordinary scheme structure sheaf on the same
underlying space; the inverse limit collects all the infinitesimal precision into a sheaf of topological rings. We do
not view $Spf \hat{R}$ as the spectrum of a ring in the ordinary sense.

### Globalizing: 𝓘-adic formal preschemes

A **formal prescheme** is a topologically ringed space that is **locally** isomorphic to $Spf \hat{R}$ for some
noetherian adic ring $(\hat{R}, \mathcal{I})$. The morphisms between formal preschemes are continuous maps of underlying
spaces with continuous maps of structure sheaves of topological rings. A morphism $f : \mathfrak{X} \to \mathfrak{Y}$ is
**adic** if the inverse image of an ideal of definition of $\mathfrak{Y}$ is an ideal of definition of $\mathfrak{X}$;
for the formal preschemes we will encounter, all morphisms are adic.

The formal preschemes that arise in Exposé III all have this shape: start with an ordinary noetherian scheme $S$ and a
coherent sheaf of ideals $\mathcal{I} \subset \mathcal{O}_{S}$. Take the closed subscheme $S_{0} := V(\mathcal{I})$ and
the thickenings $S_{n} := V(\mathcal{I}^{n+1})$. Then

```text
Ŝ := (|S₀|, lim_n 𝒪_{S_n})
```

is a formal prescheme — the **$\mathcal{I}$-adic formal completion of $S$**. For $S = \operatorname{Spec} R$ affine and
$\mathcal{I} \subset R$, $\hat{S} = Spf \hat{R}$.

### The thickenings $X_{n}$ of an ordinary scheme

Most often, instead of an $S$ with an ideal, we start with an ordinary scheme $X$ mapping to a fixed base $S$ with
$\mathcal{I} \subset \mathcal{O}_{S}$, and form the **base-change thickenings**

```text
X_n := X ×_S S_n.
```

Each $X_{n}$ is an ordinary scheme; the underlying space is independent of $n$ (the closed subset
$X \times_{S} S_{0} \subset |X|$); they form an ascending chain
$X_{0} \hookrightarrow X_{1} \hookrightarrow \cdots \hookrightarrow X$. The formal completion

$$
\hat{X} := \lim_{n} X_{n}
$$

(in the category of formal preschemes) is the formal completion of $X$ along $X_{0}$. The structure sheaf of $\hat{X}$
is the inverse limit of the $\mathcal{O}_{X_{n}}$.

## Coherent sheaves on a formal scheme

The category of coherent sheaves on a formal scheme is the deepest single piece of machinery we will need. Fortunately
it admits a clean inverse-limit description.

### Sheaves as inverse systems on the thickenings

A **coherent sheaf** $\hat{\mathcal{F}}$ on $\mathfrak{X} = \hat{X}$ is — equivalently — a coherent inverse system
$(\mathcal{F}_{n})_{n \geq 0}$ of sheaves on the thickenings:

- For each $n$, $\mathcal{F}_{n}$ is a coherent sheaf on $X_{n}$.
- For each $n$, the natural map
  $\mathcal{F}_{n+1} \otimes_{\mathcal{O}_{X_{n+1}}} \mathcal{O}_{X_{n}} \to \mathcal{F}_{n}$ is an isomorphism (the
  **inverse-system compatibility**).

The sheaf $\hat{\mathcal{F}}$ itself is then the inverse limit $\lim_{n} \mathcal{F}_{n}$ of the sheaves on the inverse
system. Tensor product, kernels, cokernels, and Hom in $Coh(\mathfrak{X})$ are computed level-by-level on the
thickenings.

This is the practical handle. Whenever file 21 or 22 says "a coherent sheaf on a formal scheme," we mean a compatible
system of coherent sheaves on the thickenings.

### Coherence

The compatibility condition forces the level-wise sheaves to be "of the same shape" at every level. Specifically: if
$\mathcal{F}_{n}$ is locally free of rank $r$ on every $X_{n}$ (which is the case in Exposé III when one is lifting a
locally free sheaf), then $\hat{\mathcal{F}}$ is **locally free of rank $r$** on $\mathfrak{X}$ in the appropriate
formal sense, and conversely every formal-locally-free $\hat{\mathcal{F}}$ arises this way.

### The category $Coh(\mathfrak{X})$

The takeaway: $Coh(\mathfrak{X})$ is a perfectly good abelian category, with the same kinds of constructions (kernels,
cokernels, tensor products, Hom-sheaves) as on an ordinary scheme. The cohomological machinery of file 17 —
$H^{q}(\mathfrak{X}, \hat{\mathcal{F}})$ for $\hat{\mathcal{F}}$ quasi-coherent — also makes sense and admits the same
Čech computation on an affine formal cover.

## Smooth, étale, and proper morphisms of formal schemes

We will need the formal versions of standard adjectives.

### Inheritance from the thickenings

A morphism of formal schemes $f : \mathfrak{X} \to \mathfrak{Y}$ (assumed adic, with matching ideals of definition) is:

- **smooth** (resp. **étale**, **proper**) if every level $f_{n} : X_{n} \to Y_{n}$ between the thickenings is smooth
  (resp. étale, proper) as an ordinary morphism of schemes.

This is the working definition; one can equivalently formulate it via lifting properties for thickening of test objects,
mirroring the lifting characterization in §III.2 (file 19). For our purposes the level-wise definition is adequate.

### Formal smoothness, formal properness

Sometimes "formally smooth" in the SGA sense (file 19) and "smooth as a morphism of formal schemes" line up; sometimes
they do not quite. The level-wise definition above is the correct notion for the algebraization arguments. The
lifting-property characterization is what makes it work — file 19 sets that up.

A **formal scheme proper over $S$** in the sense of Exposé III III.5.6 is a formal scheme $\mathfrak{X} \to \hat{S}$
whose every level $\mathfrak{X}_{n} \to S_{n}$ is proper. The classical example: $\mathfrak{X} = \hat{X}$ for $X \to S$
an ordinary proper scheme.

## Grothendieck's existence theorem

The pivot of the algebraization story is the following.

**Theorem (Grothendieck, EGA III §5.4.1).** _Let $R$ be a complete noetherian ring with ideal of definition
$\mathcal{I}$, and let $X \to \operatorname{Spec} R$ be a proper morphism. Write $\hat{X}$ for the $\mathcal{I}$-adic
formal completion of $X$. Then the functor_

```text
𝓕  ⟼  𝓕̂ := (𝓕 ⊗_{𝒪_X} 𝒪_{X_n})_n
```

_is an equivalence of categories between coherent sheaves on $X$ and coherent sheaves on $\hat{X}$._

(Black box; appendix row `grothendieck-existence`. The original proof is in EGA III §5.4 and is several pages long; the
modern exposition closest to our local corpus is Vakil's Theorem on Formal Functions, which is the cohomological half of
the existence theorem.)

What this buys: a coherent sheaf on the formal scheme $\hat{X}$ is the **same data** as a coherent sheaf on $X$.
Step-by-step extensions of coherent sheaves through the thickenings, when they succeed, **come from genuine global
coherent sheaves** on the algebraic $X$. There is no separate "formal vs. algebraic" gap to bridge once $X$ is proper
over a complete base.

### What "algebraizable" means

A formal scheme $\mathfrak{X}$ is **algebraizable** if it is isomorphic to $\hat{X}$ for some ordinary scheme $X$. The
Grothendieck existence theorem does not say every formal scheme is algebraizable — only that **coherent sheaves on a
formal scheme of the form $\hat{X}$ correspond to coherent sheaves on $X$**. The algebraization of formal schemes
themselves requires a stronger criterion, the **ample-sheaf criterion** of EGA III §4.7.1:

> _If $\mathfrak{X}$ is proper over `Ŝ` (with $S$ complete) and there exists a formal coherent sheaf $\hat{\mathcal{L}}$
> on $\mathfrak{X}$ whose restriction to $\mathfrak{X}_{0}$ is an ample line bundle, then there exists an ordinary
> projective scheme $X \to S$ with $\hat{X} \simeq \mathfrak{X}$, and $\hat{\mathcal{L}}$ comes from an ample line
> bundle on $X$._

(Black box; appendix row `algebraization-via-ample`. This is the algebraization criterion file 22 uses to upgrade
III.7.2 to III.7.3 — for projective $X_{0}$, the existence of a smooth proper formal lift implies the existence of an
ordinary smooth proper algebraic lift.)

## Worked example: the formal completion of $\mathbb{A}^{1}_{\mathbb{Z}_{p}}$ along the closed fiber

A concrete instance to anchor the picture. Let $R = \mathbb{Z}_{p}[t]$, the polynomial ring in one variable over the
$p$-adic integers. The ideal $\mathcal{I} := (p) \subset R$ cuts out the **closed fiber**

```text
S₀ = V(p) = Spec ℤ_p[t] / (p) = Spec 𝔽_p[t] = 𝔸¹_{𝔽_p}.
```

The thickenings are

```text
S_n = Spec(ℤ_p[t] / p^{n+1}) = Spec((ℤ / p^{n+1})[t]) = 𝔸¹_{ℤ/p^{n+1}}.
```

Each $S_{n}$ is the affine line over the truncated ring; their underlying space is the same
$\mathbb{A}^{1}_{\mathbb{F}_{p}}$, and they form an ascending chain.

The **`(p)`-adic formal completion** $\hat{S} = Spf \hat{R}$ has

```text
R̂ = lim_n ℤ_p[t] / p^{n+1}
   = { Σ_{i ≥ 0} a_i t^i  :  a_i ∈ ℤ_p,  a_i → 0 p-adically }.
```

This is the **Tate algebra** $\mathbb{Z}_{p}\langle t\rangle$ of restricted power series: formal series in $t$ with
$\mathbb{Z}_{p}$-coefficients converging $p$-adically to zero. Elements are not arbitrary formal series (those would be
$\mathbb{Z}_{p}[[t]]$, the $t$-adic completion); they are series whose tails go to zero in the $p$-adic topology, so
they converge on the **rigid-analytic unit disk** in the $p$-adic sense.

So:

> *The `(p)`-adic formal completion of $\mathbb{A}^{1}_{\mathbb{Z}*p}$along its closed
> fiber$\mathbb{A}^{1}_{\mathbb{F}*p}$is the formal scheme$Spf \mathbb{Z}_{p}\langle t\rangle$.*

Coherent sheaves on $Spf \mathbb{Z}_{p}\langle t\rangle$ correspond to compatible inverse systems of coherent sheaves on
the $\mathbb{A}^{1}_{\mathbb{Z}/p^{n+1}}$. By the Grothendieck existence theorem (since the base
$\operatorname{Spec} \mathbb{Z}_{p}$ is complete and we work with proper subschemes of $\mathbb{A}^{1}$, e.g. closed
points), coherent sheaves on $Spf \mathbb{Z}_{p}\langle t\rangle$ corresponding to coherent sheaves on a proper closed
subscheme of $\mathbb{A}^{1}_{\mathbb{Z}_{p}}$ lift to coherent sheaves on the algebraic
$\mathbb{A}^{1}_{\mathbb{Z}_{p}}$.

The role this example plays in file 21: it is the simplest case of "formal scheme algebraizable to an ordinary scheme
over a complete local base." When file 21 lifts a smooth $\mathbb{F}_{p}$-scheme $X_{0}$ along the thickenings
$\operatorname{Spec} \mathbb{Z}_{p} / p^{n+1}$, the resulting formal scheme $\mathfrak{X}$ is — when $H^{2}$ vanishes —
algebraic, hence comes from an honest $X / \operatorname{Spec} \mathbb{Z}_{p}$.

## What this prepares

We have:

- The notion of an **𝓘-adic formal scheme**, locally $Spf \hat{R}$ for $\hat{R}$ a noetherian adic ring; concretely, an
  inverse system of ordinary schemes $(S_{n})$ sharing an underlying space.
- The category of **coherent sheaves on a formal scheme**, captured as compatible inverse systems of coherent sheaves on
  the thickenings.
- **Smooth, étale, proper** for formal morphisms, defined level-wise.
- **Grothendieck's existence theorem**: for $X$ proper over a complete $R$, coherent sheaves on $\hat{X}$ and coherent
  sheaves on $X$ are equivalent.
- The **ample-sheaf algebraization criterion** (EGA III §4.7.1): a proper formal scheme over a complete base is
  algebraic whenever it carries a formal sheaf restricting to an ample line bundle on the closed fiber.

These are exactly the ingredients files 21 and 22 will use:

- **File 21 (§§5–6)** lifts smooth schemes one thickening at a time. The cohomological obstruction theory of file 17
  says when a single step $X_{n} \to X_{n+1}$ succeeds. Stringing together successful steps gives a **formal smooth
  scheme** $\mathfrak{X} \to \hat{S}$. The cohomological vanishing hypotheses are statements about coherent sheaves on
  the formal scheme, which by the inverse- system description reduce to statements on the $X_{n}$.
- **File 22 (§7)** algebraizes the formal scheme $\mathfrak{X}$. For $\mathfrak{X}$ formal-projective with an ample
  formal sheaf — guaranteed when $H^{2}(X_{0}, \mathcal{O}_{X_{0}}) = 0$ lets one lift an ample line bundle from $X_{0}$
  to $\mathfrak{X}$ — the algebraization criterion produces an ordinary smooth projective $X / \operatorname{Spec} R$.
  The headline application is to **smooth proper curves over $k$**, which always lift (their $H^{2}(\mathcal{O})$ and
  $H^{2}(\mathfrak{g})$ both vanish on dimension grounds).

## What to remember

- The **$\mathcal{I}$-adic completion** of a noetherian ring $R$ is $\hat{R} = \lim R/\mathcal{I}^{n+1}$. For
  $R = A[t_{1}, \cdots, t_{d}]$ and $\mathcal{I} = (t_{1}, \cdots, t_{d})$, this is the formal-power-series ring
  $A[[t_{1}, \cdots, t_{d}]]$.
- A **formal prescheme** is locally $Spf \hat{R}$ for $\hat{R}$ an adic ring; it is the limit of an inverse system of
  ordinary schemes $(S_{n})$ with common underlying space.
- The **completion of an ordinary scheme** $X \to S$ along a closed subscheme $X_{0} \subset X$ is the formal scheme
  $\hat{X} = \lim_{n} X_{n}$, where $X_{n}$ are the thickenings.
- **Coherent sheaves** on a formal scheme are compatible inverse systems of coherent sheaves on the thickenings.
- **Grothendieck's existence theorem** (EGA III §5.4.1): for $X$ proper over complete $R$, $Coh(X) \simeq Coh(\hat{X})$.
- **Algebraization of a formal scheme** requires more than the existence theorem for sheaves; the standard criterion
  (EGA III §4.7.1) is that $\mathfrak{X}$ is proper over the complete base and carries a formal sheaf restricting to an
  ample sheaf on the closed fiber.
- The worked example: the `(p)`-adic formal completion of $\mathbb{A}^{1}_{\mathbb{Z}_{p}}$ is
  $Spf \mathbb{Z}_{p}\langle t\rangle$, the Tate algebra of restricted power series. This is the prototype of a formal
  scheme over a complete base.
