# Rewritten Exposé XII, section XII.1 — the analytification functor $X \mapsto X^{an}$

<!-- source: XII.1 -->

## What this file is about

A complex algebraic variety has two natures. From one side it is a system of polynomial equations and the geometry those
equations cut out, handled with rings and ideals. From the other side it is a complex-analytic space, locally like a
chunk of complex Euclidean space, with neighbourhoods and convergent power series and the usual tools of complex
analysis. The two natures describe the same underlying set of points but reach it through different machinery. The
question is how to set up a precise translation between them, so that any statement on one side has a counterpart on the
other. This file builds that translation, point by point, and shows that locally — after passing to the finest possible
neighbourhood of each point — the two descriptions carry exactly the same information.

Files 52–56 closed Exposé XI with the algebraic side of the étale $\pi_{1}$ story carried to its sharpest limits. We
computed $\pi_{1}(\mathbb{P}^{r}) = 0$ and threaded it out through the rational, unirational, and rationally connected
hierarchies (file 52). We computed $\pi_{1}(A) \simeq T\cdot(A)$ for abelian varieties and gave a gentle treatment of
Nori's true fundamental group scheme (file 53). We exhibited sharp counterexamples to the X.1.3 / X.2.4 separability
hypothesis through the projective-cone construction and Zariski's Fermat-surface example (file 54). We built the
descent-theoretic framework for principal homogeneous bundles in the fpqc sense and the six-term cohomology exact
sequence (file 55). And we fed the Kummer and Artin–Schreier sequences into that machine to extract the Cartier-duality
master formula $H^{1}(S, G) \simeq \operatorname{Hom}(D(G), \operatorname{Pic}_{S/k})$ (file 56).

Exposé XII now opens the second half of SGA 1's promised picture. The étale story we have been telling is purely
*algebraic*: schemes, ring maps, faithfully flat descent, no metric and no topology beyond Zariski. But for the most
important base field — $k = \mathbb{C}$ — there is a parallel *analytic* story. To every $\mathbb{C}$-scheme $X$ locally
of finite type we can attach a **complex analytic space** $X^{an}$, whose underlying set is $X(\mathbb{C})$ and whose
structure sheaf $\mathcal{O}_{X^{an}}$ is the sheaf of holomorphic functions. The pairing $X \mapsto X^{an}$ is a
functor; its first-named result, in this exposé, is the **GAGA principle** — algebraic and analytic geometry over
$\mathbb{C}$ agree at the cohomological and fundamental-group level for proper schemes. We split Exposé XII across four
gentle files: this one (§XII.1, the analytification functor itself), file 58 (§§XII.2–XII.3, the property dictionaries),
file 59 (§XII.4, the cohomological GAGA theorem), and file 60 (§XII.5, the **Riemann existence theorem** and the
analytic comparison of $\pi_{1}$).

This file (§XII.1) builds the functor $X \mapsto X^{an}$ from scratch. We give it the universal property that
characterises it (XII.1.1): $X^{an}$ represents the functor
$\mathcal{X} \mapsto \operatorname{Hom}_{\mathbb{C}}(\mathcal{X}, X)$ from complex analytic spaces to sets. The
representing object exists by gluing, with three building blocks — open subschemes, closed subschemes, and the affine
line $\mathbb{A}^{1}_{\mathbb{C}}$. We unpack the comparison morphism $\phi : X^{an} \to X$ and prove its key local
properties: it induces a bijection $|X^{an}| \simeq X(\mathbb{C})$, every local map
$\phi_{x} : \mathcal{O}_{X, \phi(x)} \to \mathcal{O}_{X^{an}, x}$ becomes an isomorphism after passage to completions,
and consequently $\phi$ is *flat*. We make $X \mapsto X^{an}$ and $f \mapsto f^{an}$ into a functor commuting with
finite projective limits (XII.1.2), and we lift it to a functor $F \mapsto F^{an} = \phi*F$ on $\mathcal{O}_{X}$-modules
whose restriction to coherent sheaves is exact, faithful, and conservative (XII.1.3, XII.1.3.1).

The slogan that emerges by the end of this file: **$X^{an}$ is the analytic shadow of $X$.** A **closed point** of a
scheme is a point that is closed as a subset; in the algebraic geometry of varieties these are the classical points, and
for a scheme $\operatorname{Spec} A$ they correspond to the maximal ideals of $A$. The slogan: $X^{an}$ carries the same
local data as $X$ at every closed point, after passage to completions; the comparison morphism $\phi$ is locally as flat
as one could ask. The content of files 58–60 is then to upgrade this slogan from a local statement about completions to
a global statement about properties, cohomology, and fundamental groups.

______________________________________________________________________

## §XII.0 — Bridge: analytic spaces over $\mathbb{C}$

<!-- source: XII.1 -->

Before we can state what $X^{an}$ is, we need a working definition of *complex analytic space*. The gentle SGA does not
develop the theory from scratch — that is the job of Gunning–Rossi or Grauert–Remmert. But we owe the reader a working
vocabulary for what we are about to do.

A **complex analytic space** is a locally-ringed space $(\mathcal{X}, \mathcal{O}_{\mathcal{X}})$ over $\mathbb{C}$ that
is locally isomorphic to a **closed analytic subspace** of an open subset $U \subset \mathbb{C}^{n}$. A closed analytic
subspace is the zero locus $Z(f_{1}, \cdots, f_{r}) \subset U$ of a finite collection of holomorphic functions
$f_{1}, \cdots, f_{r} \in \mathcal{O}(U)$, equipped with the sheaf of locally-defined holomorphic functions modulo the
ideal $(f_{1}, \cdots, f_{r})$. The structure sheaf $\mathcal{O}_{\mathcal{X}}$ is, in this local picture, the quotient
$\mathcal{O}_{U} / (f_{1}, \cdots, f_{r}) \cdot \mathcal{O}_{U}$ restricted to the closed subset
$Z(f_{1}, \cdots, f_{r})$.

Three things to keep in mind. First, complex analytic spaces are *locally-ringed* $\mathbb{C}$-spaces: each stalk
$\mathcal{O}_{\mathcal{X}, x}$ is a local $\mathbb{C}$-algebra whose residue field is $\mathbb{C}$, and morphisms
$(\mathcal{X}, \mathcal{O}_{\mathcal{X}}) \to (\mathcal{Y}, \mathcal{O}_{\mathcal{Y}})$ are continuous maps together
with sheaf maps $\mathcal{O}_{\mathcal{Y}} \to f_{*} \mathcal{O}_{\mathcal{X}}$ that respect localness. Second, the
local stalks are *not* polynomial rings — they are rings of convergent power series, henselian and complete in their
$\mathfrak{m}$-adic topology. The completion of $\mathcal{O}_{\mathcal{X}, x}$ at the maximal ideal is the formal power
series ring $\mathbb{C}[[T_{1}, \cdots, T_{n}]]$ modulo the formal completion of $(f_{1}, \cdots, f_{r})$. Third — and
this is the **Oka coherence theorem**, the foundational result that licenses every later coherence statement — the
structure sheaf $\mathcal{O}_{\mathcal{X}}$ is itself a coherent sheaf of rings (`oka-coherence`). Consequently the
category of coherent $\mathcal{O}_{\mathcal{X}}$-modules is closed under kernels, cokernels, finite direct sums, and
tensor products, and the standard sheaf-theoretic operations (pullback, pushforward along proper maps, `SheafHom`)
preserve coherence under reasonable hypotheses.

A **morphism of complex analytic spaces** $f : \mathcal{X} \to \mathcal{Y}$ is a morphism of locally-ringed
$\mathbb{C}$-spaces; equivalently, a continuous map $f_{top} : |\mathcal{X}| \to |\mathcal{Y}|$ plus a sheaf map
$f^{#} : \mathcal{O}_{\mathcal{Y}} \to f_{*} \mathcal{O}_{\mathcal{X}}$ such that the induced stalk maps are local
homomorphisms of local $\mathbb{C}$-algebras. We write $AnSp/\mathbb{C}$ for the category of complex analytic spaces and
$\mathbb{C}$-morphisms.

The fact that analytic spaces have fibre products in $AnSp/\mathbb{C}$ is non-trivial. We will need it only locally —
fibre products of *affine analytic spaces* — and we cite Gunning–Rossi for the general construction.

#### The picture before XII.1.1.

We have on one side $Sch_{lft}/\mathbb{C}$, the category of $\mathbb{C}$-schemes locally of finite type. On the other
side $AnSp/\mathbb{C}$, complex analytic spaces. The XII.1 theorem-definition produces a functor

```text
Φ : Sch_{lft}/ℂ → AnSp/ℂ
       X ↦ X^an
```

with a natural transformation $\phi : \Phi \Rightarrow id_{LocRing/\mathbb{C}}$ (where we view both categories as
subcategories of locally-ringed $\mathbb{C}$-spaces) — that is, a comparison morphism $\phi_{X} : X^{an} \to X$ for
every $X$. The functor $\Phi$ and the comparison morphism are constructed simultaneously by representing a single
functor, the **points functor**.

This is the moral content. The technical content is everything in §XII.1.1.

> *Working definition for the rest of the gentle SGA Exposé XII.* A complex analytic space is a locally-ringed
> $\mathbb{C}$-space locally modelled on $(Z(f_{1}, \cdots, f_{r}), \mathcal{O}_{U} / (f_{i}) \cdot \mathcal{O}_{U})$
> for some open $U \subset \mathbb{C}^{n}$ and holomorphic $f_{1}, \cdots, f_{r} \in \mathcal{O}(U)$. The structure
> sheaf is coherent (Oka). Morphisms are sheaf maps respecting localness. Cohomology means sheaf cohomology of
> $\mathcal{O}_{\mathcal{X}}$-modules in the usual sense (Cartan's Theorem B vanishes it on Stein opens). See
> Gunning–Rossi or Grauert–Remmert (`gunning-rossi-analytic`, `grauert-remmert-coverings`) for the formal foundations.

______________________________________________________________________

## §XII.1.1 — Representability of analytification

<!-- source: XII.1.1 -->

### Theorem-Definition XII.1.1 — the analytic space associated with a $\mathbb{C}$-scheme

<!-- source: XII.1.1 -->

Let $X$ be a $\mathbb{C}$-scheme locally of finite type. Define the **points functor**

```text
Φ_X : (AnSp/ℂ)^op → Set,         𝒳 ↦ Hom_{LocRing/ℂ}(𝒳, X),
```

where the right side is the set of morphisms of locally-ringed $\mathbb{C}$-spaces from $\mathcal{X}$ to $X$.

**Theorem-Definition XII.1.1.** The functor $\Phi_{X}$ is representable. That is, there exists a complex analytic space
$X^{an}$ and a morphism of locally-ringed $\mathbb{C}$-spaces

```text
φ = φ_X : X^an → X
```

such that for every analytic space $\mathcal{X}$, the canonical map

```text
Hom_{AnSp/ℂ}(𝒳, X^an) → Hom_{LocRing/ℂ}(𝒳, X),        ψ ↦ φ ∘ ψ,
```

is a bijection. The pair $(X^{an}, \phi_{X})$ is unique up to unique isomorphism.

Moreover, $(X^{an}, \phi_{X})$ has the following sharper local properties:

1. **Bijection on points.** The map $\phi : |X^{an}| \to |X|$ induces a bijection between the underlying set $|X^{an}|$
   of $X^{an}$ and the set $X(\mathbb{C}) \subset |X|$ of $\mathbb{C}$-valued points of $X$ (the closed points of $X$
   whose residue field is $\mathbb{C}$).
1. **Completion isomorphism.** For every point $x \in X^{an}$, the local map
   $\phi_{x} : \mathcal{O}_{X, \phi(x)} \to \mathcal{O}_{X^{an}, x}$ is a *local* homomorphism of local
   $\mathbb{C}$-algebras, and after passage to completions it becomes an isomorphism:

```text
φ̂_x : 𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}.
```

1. **Flatness.** Consequently $\phi : X^{an} \to X$ is flat (every $\phi_{x}$ is flat because faithfully flat after
   completion).

*This result says:* the analytification is built once-and-for-all, glues over affine opens, and matches $X$ exactly on
closed $\mathbb{C}$-points and after completion of every local ring. The data $(X^{an}, \phi_{X})$ extracts from $X$
precisely the analytic-geometric information that $X$ carries over $\mathbb{C}$.

#### Strategy of the proof.

We prove this in three building blocks. The first block (a) handles **subschemes**: if XII.1.1 holds for $Y$, then it
holds for every open subscheme and every closed subscheme of $Y$. The second block (b) handles **products**: if XII.1.1
holds for `X_1` and `X_2`, then it holds for $X_{1} \times X_{2}$. The third block (c) handles the **base case
$X = \mathbb{A}^{1}_{\mathbb{C}}$** explicitly: we exhibit $(\mathbb{A}^{1}_{\mathbb{C}})^{an}$ as the topological space
$\mathbb{C}$ with its sheaf of holomorphic functions. From (b) and (c) one deduces XII.1.1 for affine $n$-space
$\mathbb{A}^{n}_{\mathbb{C}}$. From (a) one deduces it for arbitrary affine $X$ (which is a closed subscheme of some
$\mathbb{A}^{n}_{\mathbb{C}}$). From (a) again — applied to *open* immersions and to the universal property — one then
deduces XII.1.1 for arbitrary $X$ by gluing affine charts.

The completion isomorphism (2) is preserved by each step because it is local at every point. Flatness (3) is then
formal.

#### Block (a): reduction to subschemes.

<!-- source: XII.1.1 -->

Suppose XII.1.1 holds for $Y$: there exist $(Y^{an}, \psi : Y^{an} \to Y)$ representing $\Phi_{Y}$, with bijection on
$\mathbb{C}$-points and completion isomorphism at every point. We must verify XII.1.1 for every subscheme $X \subset Y$.

**Sub-block (a1): open subscheme.** Let $X \subset Y$ be an open subscheme. Define
$X^{an} := \psi^{-1}(X) \subset Y^{an}$, an open subspace of $Y^{an}$ (with the induced analytic-space structure: open
subset, restricted structure sheaf). Let $\phi := \psi|_{\psi^{-1}(X)} : X^{an} \to X$.

We verify the universal property. Let $\mathcal{X}$ be an analytic space and let $\alpha : \mathcal{X} \to X$ be a
morphism of locally-ringed $\mathbb{C}$-spaces. The composition $\mathcal{X} \to X \hookrightarrow Y$ is then a morphism
of locally-ringed $\mathbb{C}$-spaces from $\mathcal{X}$ to $Y$, and the universal property of $Y^{an}$ yields a unique
lift $\tilde{\alpha} : \mathcal{X} \to Y^{an}$ with $\psi \circ \tilde{\alpha} = \alpha : \mathcal{X} \to Y$. Since the
image of $\tilde{\alpha}$ lies inside $\psi^{-1}(X) = X^{an}$ (a point $y \in \mathcal{X}$ maps to $\alpha(y) \in X$, so
$\psi(\tilde{\alpha}(y)) \in X$, hence $\tilde{\alpha}(y) \in \psi^{-1}(X)$), $\tilde{\alpha}$ factors uniquely through
$X^{an}$. This gives the bijection `Hom_{AnSp/ℂ}(𝒳, X^an) ≃ Hom_{LocRing/ℂ}(𝒳, X)`.

The bijection on $\mathbb{C}$-points and the completion isomorphism at every point are inherited from $Y^{an}$.

**Sub-block (a2): closed subscheme.** Let $X \subset Y$ be a closed subscheme, defined by a coherent ideal sheaf
$I \subset \mathcal{O}_{Y}$. Pull back along $\psi : Y^{an} \to Y$ to get the **analytic ideal sheaf**
$I \cdot \mathcal{O}_{Y^{an}} \subset \mathcal{O}_{Y^{an}}$. This is a coherent ideal of $\mathcal{O}_{Y^{an}}$ —
coherent because $I$ is coherent on $Y$ and $\mathcal{O}_{Y^{an}}$ is coherent (Oka, `oka-coherence`), so the pullback
$I \cdot \mathcal{O}_{Y^{an}}$ is coherent. Define $X^{an} \subset Y^{an}$ to be the closed analytic subspace cut out by
$I \cdot \mathcal{O}_{Y^{an}}$, with structure sheaf $\mathcal{O}_{Y^{an}} / I \cdot \mathcal{O}_{Y^{an}}$ restricted to
its support.

The morphism $\phi : X^{an} \to X$ is the restriction of $\psi$ to the closed analytic subspace, factored through
$X \subset Y$.

We verify the universal property. Let $\alpha : \mathcal{X} \to X$ be a morphism into the closed subscheme. Composing
with $X \hookrightarrow Y$ gives a morphism $\mathcal{X} \to Y$, which lifts uniquely to
$\tilde{\alpha} : \mathcal{X} \to Y^{an}$. The image of $\tilde{\alpha}$ lies in the closed analytic subspace defined by
$I \cdot \mathcal{O}_{Y^{an}}$ because $\alpha$ itself lands in the zero-locus of $I$. Hence $\tilde{\alpha}$ factors
uniquely through $X^{an}$.

The completion isomorphism at a point $x \in X^{an}$ is checked as follows. Let $y = \psi(x) \in X \subset Y$. The local
map $\phi_{x}$ is the composite

```text
𝒪_{X, y} = 𝒪_{Y, y} / I_y    →    𝒪_{X^an, x} = 𝒪_{Y^an, x} / I_y · 𝒪_{Y^an, x}.
```

After passage to completions this becomes

```text
𝒪̂_{Y, y} / I_y · 𝒪̂_{Y, y}    →    𝒪̂_{Y^an, x} / I_y · 𝒪̂_{Y^an, x},
```

an isomorphism because the underlying map $\hat{\mathcal{O}}_{Y, y} \to \hat{\mathcal{O}}_{Y^{an}, x}$ is the iso
$\hat{\psi}_{x}$. The bijection on $\mathbb{C}$-points is inherited.

> **Lemma (block a).** *If XII.1.1 holds for $Y$, it holds for every open and every closed subscheme of $Y$. Hence it
> holds for every subscheme of $Y$.*

#### Block (b): stability under products.

<!-- source: XII.1.1 -->

Suppose XII.1.1 holds for `X_1` and `X_2`. Let $\phi_{i} : X^{an}_{i} \to X_{i}$ be the comparison morphisms. We claim
that the analytic-space product $X^{an}_{1} \times X^{an}_{2}$ (which exists in $AnSp/\mathbb{C}$ by general nonsense +
a local construction in coordinate charts) together with the morphism

```text
φ := (φ_1 ∘ p_1, φ_2 ∘ p_2) : X_1^an × X_2^an → X_1 × X_2,
```

represents the functor $\mathcal{X} \mapsto \operatorname{Hom}_{LocRing/\mathbb{C}}(\mathcal{X}, X_{1} \times X_{2})$.

The proof is formal once we know that the scheme-theoretic product $X_{1} \times X_{2}$ is also the product *in the
larger category of locally-ringed $\mathbb{C}$-spaces*. This fact is exactly **EGA I §1.8.1**: the fibre product of
schemes in `LocRing` (the category of locally-ringed spaces) coincides with the fibre product computed in `Sch`.
Equivalently: the inclusion `Sch_{lft}/ℂ ↪ LocRing/ℂ` preserves finite limits.

Granting EGA I §1.8.1, a morphism $\alpha : \mathcal{X} \to X_{1} \times X_{2}$ in $LocRing/\mathbb{C}$ is the same
datum as a pair $(\alpha_{1}, \alpha_{2}) : \mathcal{X} \to X_{1}, \mathcal{X} \to X_{2}$. By the universal property of
$X^{an}_{i}$, each $\alpha_{i}$ lifts uniquely to $\tilde{\alpha}_{i} : \mathcal{X} \to X^{an}_{i}$. The pair
$(\tilde{\alpha}_{1}, \tilde{\alpha}_{2})$ defines a unique morphism
$\tilde{\alpha} : \mathcal{X} \to X^{an}_{1} \times X^{an}_{2}$ in $AnSp/\mathbb{C}$ (via the universal property of the
analytic-space product). This gives the bijection `Hom_{AnSp/ℂ}(𝒳, X_1^an × X_2^an) ≃ Hom_{LocRing/ℂ}(𝒳, X_1 × X_2)`.

The bijection on $\mathbb{C}$-points: $(X_{1} \times X_{2})(\mathbb{C}) = X_{1}(\mathbb{C}) \times X_{2}(\mathbb{C})$,
and similarly for analytic spaces, so
$|X^{an}_{1} \times X^{an}_{2}| \simeq X_{1}(\mathbb{C}) \times X_{2}(\mathbb{C}) \simeq (X_{1} \times X_{2})(\mathbb{C})$.
The completion isomorphism at a point $(x_{1}, x_{2}) \in X^{an}_{1} \times X^{an}_{2}$ is the tensor product of the
completion isomorphisms at $x_{1}$ and $x_{2}$.

> **Lemma (block b).** *If XII.1.1 holds for `X_1` and `X_2`, then it holds for $X_{1} \times X_{2}$.*

#### Block (c): the base case $X = \mathbb{A}^{1}_{\mathbb{C}}$.

<!-- source: XII.1.1 -->

Let $X = \mathbb{A}^{1}_{\mathbb{C}} = \operatorname{Spec} \mathbb{C}[T]$. Define
$\mathcal{E}^{1} := (\mathbb{C}, \mathcal{O}_{hol})$ — the topological space $\mathbb{C}$ with its sheaf of holomorphic
functions. This is the standard one-dimensional complex affine space.

We claim that $(\mathcal{E}^{1}, \phi_{\mathbb{A}^{1}})$ represents the functor $\Phi_{\mathbb{A}^{1}_{\mathbb{C}}}$,
where $\phi_{\mathbb{A}^{1}} : \mathcal{E}^{1} \to \mathbb{A}^{1}_{\mathbb{C}}$ is the *evident* morphism: on underlying
sets, it is the bijection $|\mathcal{E}^{1}| = \mathbb{C} \simeq \mathbb{A}^{1}(\mathbb{C}) = \mathbb{C}$; on structure
sheaves, it sends the algebraic function $T \in \mathbb{C}[T]$ to its holomorphic incarnation
$T \in \mathcal{O}_{hol}(\mathbb{C})$.

The universal property is essentially trivial: a morphism of locally-ringed $\mathbb{C}$-spaces
$\mathcal{X} \to \mathbb{A}^{1}_{\mathbb{C}}$ is the same thing as a $\mathbb{C}$-algebra map
$\mathbb{C}[T] \to \Gamma(\mathcal{X}, \mathcal{O}_{\mathcal{X}})$, which is the same thing as a section of
$\mathcal{O}_{\mathcal{X}}$ (the image of $T$). And a morphism of locally-ringed $\mathbb{C}$-spaces
$\mathcal{X} \to \mathcal{E}^{1}$ is also the same thing as a section of $\mathcal{O}_{\mathcal{X}}$ (the holomorphic
function on $\mathcal{X}$ obtained by pulling back the coordinate function on $\mathbb{C}$).

Hence

```text
Hom_{AnSp/ℂ}(𝒳, 𝓔^1) ≃ Γ(𝒳, 𝒪_𝒳) ≃ Hom_{LocRing/ℂ}(𝒳, 𝔸^1_ℂ).
```

The bijection $|\mathcal{E}^{1}| \simeq \mathbb{A}^{1}(\mathbb{C}) = \mathbb{C}$ is built into the construction.

The completion isomorphism at every point $x \in \mathbb{C}$: the local ring
$\mathcal{O}_{\mathbb{A}^{1}, x} = \mathbb{C}[T]_{(T - x)}$ has completion $\mathbb{C}[[T - x]]$. The local ring
$\mathcal{O}_{\mathcal{E}^{1}, x}$ is the ring of germs of holomorphic functions at $x$, which is the ring of
*convergent* power series in $T - x$. Its completion is the formal power series ring $\mathbb{C}[[T - x]]$. The natural
map $\mathbb{C}[T]_{(T - x)} \to \mathbb{C}\{T - x\} \to \mathbb{C}[[T - x]]$ is the composition of inclusion and
completion; after completion it is the identity on $\mathbb{C}[[T - x]]$. So $\hat{\phi}_{x}$ is the identity. ∎

> **Lemma (block c).** *XII.1.1 holds for $X = \mathbb{A}^{1}_{\mathbb{C}}$, with
> $(\mathbb{A}^{1}_{\mathbb{C}})^{an} = \mathcal{E}^{1} = (\mathbb{C}, \mathcal{O}_{hol})$.*

#### Assembling the proof of XII.1.1.

We now assemble blocks (a)–(c) to prove XII.1.1 for every $\mathbb{C}$-scheme $X$ locally of finite type.

**Step 1: affine $n$-space $\mathbb{A}^{n}_{\mathbb{C}}$.** By iterating block (b) starting from block (c), XII.1.1
holds for $\mathbb{A}^{n}_{\mathbb{C}} = \mathbb{A}^{1}_{\mathbb{C}} \times \cdots \times \mathbb{A}^{1}_{\mathbb{C}}$.
Explicitly: $(\mathbb{A}^{n}_{\mathbb{C}})^{an} = \mathcal{E}^{n} = (\mathbb{C}^{n}, \mathcal{O}_{hol})$.

**Step 2: affine $\mathbb{C}$-schemes of finite type.** Every affine $\mathbb{C}$-scheme
$X = \operatorname{Spec}(\mathbb{C}[T_{1}, \cdots, T_{n}] / I)$ of finite type is a closed subscheme of
$\mathbb{A}^{n}_{\mathbb{C}}$. By block (a) applied to $Y = \mathbb{A}^{n}_{\mathbb{C}}$, XII.1.1 holds for $X$.
Explicitly: $X^{an}$ is the closed analytic subspace of $\mathcal{E}^{n}$ cut out by
$I \cdot \mathcal{O}_{\mathcal{E}^{n}}$.

**Step 3: gluing.** Let $X$ be an arbitrary $\mathbb{C}$-scheme locally of finite type, and let $(U_{i})_{i \in I}$ be a
covering of $X$ by affine opens. By Step 2, each $U^{an}_{i}$ exists and satisfies XII.1.1. By block (a1) applied to
each pair $U_{i} \cap U_{j} \subset U_{i}$, the analytic open
$(U_{i} \cap U_{j})^{an} = \phi^{-1}_{U_{i}}(U_{i} \cap U_{j}) \subset U^{an}_{i}$ exists and agrees with the analytic
open computed inside $U^{an}_{j}$. We can therefore glue the analytic spaces $U^{an}_{i}$ along the analytic opens
$(U_{i} \cap U_{j})^{an}$ to produce an analytic space $X^{an}$ and a morphism $\phi : X^{an} \to X$. The universal
property for $X^{an}$ follows: a morphism $\alpha : \mathcal{X} \to X$ is determined by its restrictions to the open
cover $\alpha^{-1}(U_{i})$, and each restriction lifts uniquely to
$\tilde{\alpha}_{i} : \alpha^{-1}(U_{i}) \to U^{an}_{i}$, and these lifts glue.

The bijection on $\mathbb{C}$-points is local; the completion isomorphism at each point is local; both transfer to
$X^{an}$.

This completes the proof of XII.1.1. ∎

> **Slogan.** *$X^{an}$ is the analytic space whose underlying set is $X(\mathbb{C})$ and whose local rings at each
> closed point complete to the same formal power series ring as the local rings of $X$.* The functor
> $\Phi : X \mapsto X^{an}$ is the universal locally-ringed-$\mathbb{C}$-space gadget that solves the points functor.

#### Aside (why the universal property is the right organising principle).

There is a tempting alternative construction of $X^{an}$: take the underlying set $X(\mathbb{C})$, give it the analytic
topology inherited from a closed embedding of an affine chart into some $\mathbb{C}^{n}$, and put on the result the
sheaf of holomorphic functions modulo the ideal. This works, and is what Serre 1956 did for projective varieties. The
trouble is that *naturality* — functoriality in $X$ — and *coherence* across overlapping charts are then both extra
work, with no clean structural reason behind them.

The universal property packages all of this in one move. $X^{an}$ *is* whatever locally-ringed-$\mathbb{C}$-space turns
the points functor $\operatorname{Hom}_{LocRing/\mathbb{C}}(\_,X)$ into an analytic-space representable. The
functoriality $f \mapsto f^{an}$ is then *automatic* (the next section, XII.1.2). The compatibility with subschemes
(block a), with products (block b), and with affine $n$-space (block c) are forced by representability. Everything we
want from $X^{an}$ is encoded in the universal property; nothing else is.

This is the same organising principle that drives the construction of $\operatorname{Spec} A$, of the product of
schemes, of the formal-scheme completion $\hat{X}$ (file 18), of the étale fundamental group $\pi_{1}(S, a)$ (file 33),
and of the Picard scheme $\operatorname{Pic}_{X/S}$. Each time, the moral is the same: build the functor first; let
representability force the geometry.

______________________________________________________________________

## §XII.1.2 — Functoriality of analytification

<!-- source: XII.1.2 -->

The universal property in XII.1.1 immediately delivers functoriality. Given a morphism $f : X \to Y$ of
$\mathbb{C}$-schemes locally of finite type, consider the morphism of locally-ringed-$\mathbb{C}$-spaces

```text
f ∘ φ_X : X^an → X → Y.
```

By the universal property of $Y^{an}$, this morphism lifts to a unique morphism

$$
f^{an} : X^{an} \to Y^{an}
$$

such that $\phi_{Y} \circ f^{an} = f \circ \phi_{X}$ — that is, the analytification square

```text
X^an --φ_X→  X
 |            |
f^an         f
 |            |
Y^an --φ_Y→  Y
```

is commutative. Uniqueness makes $(f, g) \mapsto (f^{an}, g^{an})$ respect composition:
$(g \circ f)^{an} = g^{an} \circ f^{an}$, $id^{an} = id$. We have a functor

```text
Φ : Sch_{lft}/ℂ → AnSp/ℂ.
```

### Proposition XII.1.2 — $\Phi$ commutes with finite projective limits

<!-- source: XII.1.2 -->

**Proposition XII.1.2.** The functor `Φ : Sch_{lft}/ℂ → AnSp/ℂ` commutes with finite projective limits. In particular,
it commutes with fibre products:

```text
(X ×_Z Y)^an ≃ X^an ×_{Z^an} Y^an.
```

*This result says:* the analytification of a fibre product is the fibre product of the analytifications. The fibre
product on the right is computed in $AnSp/\mathbb{C}$.

**Proof.** It is enough to check the fibre-product case (a category with all finite limits is the same as a category
with terminal object and binary products of objects in a specific category-theoretic sense). Let $X$, $Y$, $Z$ be
$\mathbb{C}$-schemes locally of finite type and let $X \to Z$, $Y \to Z$ be morphisms.

By EGA I §1.8.1, the scheme-theoretic fibre product $X \times_{Z} Y$ is also the fibre product in the larger category
$LocRing/\mathbb{C}$. So a morphism $\alpha : \mathcal{X} \to X \times_{Z} Y$ in $LocRing/\mathbb{C}$ is the same datum
as a compatible pair $(\alpha_{X} : \mathcal{X} \to X, \alpha_{Y} : \mathcal{X} \to Y)$ of morphisms agreeing on $Z$. By
the universal property of $X^{an}, Y^{an}, Z^{an}$, each
$\alpha_{X}, \alpha_{Y}, \alpha_{X} \downarrow Z, \alpha_{Y} \downarrow Z$ lifts uniquely to the analytic side. The pair
$(\tilde{\alpha}_{X}, \tilde{\alpha}_{Y})$ of analytic lifts then defines a unique morphism
$\tilde{\alpha} : \mathcal{X} \to X^{an} \times_{Z^{an}} Y^{an}$ (universal property of the analytic fibre product).

This proves that $X^{an} \times_{Z^{an}} Y^{an}$ represents the functor
$\mathcal{X} \mapsto \operatorname{Hom}_{LocRing/\mathbb{C}}(\mathcal{X}, X \times_{Z} Y)$, which by XII.1.1 applied to
$X \times_{Z} Y$ is the same as $\operatorname{Hom}_{AnSp/\mathbb{C}}(\mathcal{X}, (X \times_{Z} Y)^{an})$. By Yoneda,
$(X \times_{Z} Y)^{an} \simeq X^{an} \times_{Z^{an}} Y^{an}$. ∎

> **Slogan.** *Analytification is a functor that respects fibre products.* In particular, it respects base change: the
> analytic space $(X \times_{Z} Z')^{an}$ is the analytic-base-change $X^{an} \times_{Z^{an}} Z'^{an}$.

#### Aside (forgetting to check commutation with limits).

This proposition will be used in essentially every later argument of files 58–60 without further comment. The two most
important consequences are:

1. **The diagonal is preserved.** If $f : X \to Y$ is a morphism, its diagonal $\Delta_{X/Y} : X \to X \times_{Y} X$
   analytifies to $\Delta_{X^{an} / Y^{an}} : X^{an} \to X^{an} \times_{Y^{an}} X^{an}$. The fact that $f^{an}$ is
   separated iff $\Delta$ is closed (for the analytic morphism) and the fact that $f$ is separated iff $\Delta$ is
   closed (for the scheme morphism) is the XII.3.1 (viii) iff — and it is preserved by XII.2.3 + XII.1.2 (file 58).
1. **Fibre $(f^{-1}(y))^{an} = (f^{an})^{-1}(y)$.** This is the key compatibility that lets us reduce questions about
   fibres of $f^{an}$ to questions about fibres of $f$, used throughout XII.3.

______________________________________________________________________

## §XII.1.3 — Sheaf-level analytification

<!-- source: XII.1.3 -->

We have built a functor $\Phi : X \mapsto X^{an}$ on $\mathbb{C}$-schemes locally of finite type. The next step is to
lift it to sheaves. Given an $\mathcal{O}_{X}$-module $F$, the pullback along the analytification morphism
$\phi : X^{an} \to X$ is an $\mathcal{O}_{X^{an}}$-module:

```text
F^an := φ*F = (φ⁻¹F) ⊗_{φ⁻¹𝒪_X} 𝒪_{X^an}.
```

This defines a functor

```text
Φ^# : Mod(𝒪_X) → Mod(𝒪_{X^an}),    F ↦ F^an.
```

The basic properties of $F \mapsto F^{an}$ come from general nonsense about pullback functors. Two stand out:

1. **Inductive limits.** Because pullback is a left adjoint (to pushforward), $\Phi^{#}$ commutes with all inductive
   limits — direct sums, cokernels, filtered colimits, tensor products. The reference is EGA `0_I` 4.3.2.
1. **Coherent sheaves go to coherent sheaves.** This uses the fact that $\mathcal{O}_{X^{an}}$ is itself a coherent
   sheaf of rings (Oka coherence, `oka-coherence`). The general statement (EGA `0_I` 5.3.11) is that if $f$ is a
   morphism of locally-ringed spaces and the target structure sheaf is coherent, then $f*$ carries coherent modules to
   coherent modules. We can therefore restrict $\Phi^{#}$ to coherent sheaves:

```text
Φ^#_{coh} : Coh(X) → Coh(X^an),    F ↦ F^an.
```

The substantive content of XII.1.3 is the next subproposition.

### Subproposition XII.1.3.1 — $F \mapsto F^{an}$ is exact, faithful, conservative on coherent sheaves

<!-- source: XII.1.3.1 -->

**Subproposition XII.1.3.1.** The functor `Φ^#_{coh} : Coh(X) → Coh(X^an)` is:

1. **exact** — sends short exact sequences of coherent sheaves to short exact sequences;
1. **faithful** — distinct morphisms $F \to G$ of coherent sheaves go to distinct morphisms $F^{an} \to G^{an}$;
1. **conservative** — a morphism $f : F \to G$ of coherent sheaves whose analytification $f^{an} : F^{an} \to G^{an}$ is
   an isomorphism is itself an isomorphism.

*This result says:* on coherent sheaves, the analytification functor preserves everything $Coh(X)$ carries as a abelian
category: kernels, cokernels, exact sequences, distinctness of morphisms, the property of being zero.

**Proof.**

**(1) Exactness.** A pullback functor $f*$ is exact iff $f$ is *flat* (this is the bridge between Tor-vanishing and
right-exactness of pullback). The flatness of $\phi : X^{an} \to X$ was the third clause of XII.1.1. Hence $\Phi^{#}$ is
exact on all $\mathcal{O}_{X}$-modules, in particular on coherent ones.

**(2) Faithfulness.** Because $\Phi^{#}$ is exact, it sends
$\operatorname{Hom}_{\mathcal{O}_{X}}(F, G) \hookrightarrow \operatorname{Hom}_{\mathcal{O}_{X^{an}}}(F^{an}, G^{an})$
to be injective iff $\Phi^{#}(F) = 0$ implies $F = 0$ (apply the cokernel of $f$ to detect distinct morphisms). So it
suffices to prove the next clause:

**(2′) If $F^{an} = 0$ then $F = 0$.** Suppose $F^{an} = (\phi*F) = 0$ as a sheaf on $X^{an}$. Pick any point
$x \in X^{an}$, let $y = \phi(x) \in X$. Then
$F^{an}_{x} = F_{y} \otimes_{\mathcal{O}_{X, y}} \mathcal{O}_{X^{an}, x} = 0$. The local map
$\mathcal{O}_{X, y} \to \mathcal{O}_{X^{an}, x}$ is faithfully flat: it is flat (a fortiori from completion-iso XII.1.1
(2): faithful flatness on completions plus completion-faithful-flatness
$\mathcal{O}_{X, y} \to \hat{\mathcal{O}}_{X, y}$ gives faithful flatness
$\mathcal{O}_{X, y} \to \hat{\mathcal{O}}_{X^{an}, x}$, which factors through $\mathcal{O}_{X^{an}, x}$). So faithful
flatness of the local map gives $F_{y} = 0$.

We have shown: $F_{y} = 0$ for every $y \in \phi(X^{an}) = X(\mathbb{C})$, i.e. for every closed point $y$ of $X$ with
residue field $\mathbb{C}$. But $X$ is a Jacobson scheme — and for a Jacobson scheme, *the closed points are very
dense*: a coherent sheaf $F$ is zero iff it is zero at every closed point. The fact that $X / \mathbb{C}$ locally of
finite type is Jacobson is recorded as `ega-iv-jacobson-nullstellensatz` (EGA IV §10.4.8). Hence $F = 0$.

**(3) Conservativeness.** Let $f : F \to G$ be a morphism of coherent sheaves on $X$ such that $f^{an}$ is an
isomorphism. Apply exactness to $0 \to \ker(f) \to F \to G \to \coker(f) \to 0$: by exactness, the analytified sequence
$0 \to (\ker f)^{an} \to F^{an} \to G^{an} \to (\coker f)^{an} \to 0$ is exact. Since $f^{an}$ is an iso,
$(\ker f)^{an} = 0$ and $(\coker f)^{an} = 0$. By faithfulness (clause 2), $\ker f = 0$ and $\coker f = 0$, so $f$ is an
iso.

This proves the three clauses. ∎

> **Slogan.** *The analytification functor on coherent sheaves loses no information about $F$ itself.* What it *does*
> lose, in principle, is information about higher direct images $R^{p}f_{*}F$ — these may or may not commute with
> analytification. The cohomological GAGA theorem (XII.4.2, file 59) says that *for $f$ proper*, no information is lost
> there either.

#### Aside (the philosophy of XII.1.3.1).

This subproposition is the analytic incarnation of a recurring philosophical principle in scheme theory: *the
analytification functor sees enough.* The completion isomorphism XII.1.1 (2) tells us that $\mathcal{O}_{X^{an}, x}$
remembers as much about $X$ as the formal completion $\hat{\mathcal{O}}_{X, x}$ does. The faithful flatness step in
clause (2′) of the proof then licenses propagation from completions back to $\mathcal{O}_{X, x}$. Jacobson then
propagates from a single closed point to all of $X$.

The full chain is:

```text
𝒪_{X, y}  ─inj→  𝒪̂_{X, y}  ─iso (XII.1.1)→  𝒪̂_{X^an, x}  ─inj←  𝒪_{X^an, x}.
```

The "inj" arrows are faithful flatness (`completion-flat` from file 17 and the analytic analogue). The "iso" arrow is
XII.1.1 (2). The composition is faithful flatness $\mathcal{O}_{X, y} \to \mathcal{O}_{X^{an}, x}$.

This is exactly the structural reason why everything in XII.2 and XII.3 (file 58) reduces to checking properties at
*closed points* and then transferring across the completion.

______________________________________________________________________

## §XII.1.4 — What is missing from XII.1

<!-- source: XII.1 -->

The functor $\Phi : X \mapsto X^{an}$ has been constructed (XII.1.1). It is functorial (XII.1.2) and respects fibre
products. It lifts to a faithful exact conservative functor `Φ^#_{coh} : Coh(X) → Coh(X^an)` (XII.1.3, XII.1.3.1).

But three big questions remain unaddressed, and each is the subject of one of files 58, 59, 60.

#### Q1: When does $f : X \to Y$ and $f^{an} : X^{an} \to Y^{an}$ carry the same properties?

The local properties of $X$ (regular, normal, Cohen–Macaulay, smooth, …) and the local properties of $f$ (flat,
unramified, étale, smooth, proper, finite, …) should transfer between the algebraic and analytic worlds, given that the
local rings agree after completion. **File 58 (XII.2, XII.3)** turns this expectation into a precise dictionary, with
eight scheme-level properties (XII.2.1) and seventeen morphism-level properties (XII.3.1, XII.3.2). Most proofs proceed
by reducing to a closed point via Jacobson and then transferring across the completion isomorphism XII.1.1 (2).

#### Q2: When is $\Phi^{#}_{coh}$ essentially surjective? When does $H^{p}(X, F) = H^{p}(X^{an}, F^{an})$?

XII.1.3.1 shows $\Phi^{#}_{coh}$ is faithful, exact, conservative. But for $X$ *proper*, it should be more — an
**equivalence of categories**, with cohomology preservation $H^{p}(X, F) \simeq H^{p}(X^{an}, F^{an})$. This is the
**relative GAGA theorem** of **file 59 (XII.4)**. The cohomology preservation upgrades to a comparison of higher direct
images $(R^{p} f_{*} F)^{an} \simeq R^{p} f^{an}_{*}(F^{an})$ for $f : X \to Y$ proper.

#### Q3: How does the étale fundamental group $\pi^{\acute{e}}_{1}t(X)$ relate to the topological fundamental group

$\pi^{top}_{1}(X^{an})$?

For $X = \mathbb{P}^{r}_{\mathbb{C}}$ the answer is "both are trivial" (file 52 XI.1.1 on the algebraic side; classical
homotopy theory on the analytic side). For abelian varieties (file 53 XI.2.3) the étale $\pi_{1}$ is the Tate module; on
the analytic side, $\pi^{top}_{1}(A^{an}) = H_{1}(A^{an}, \mathbb{Z}) \simeq \mathbb{Z}^{2g}$ is the integral homology
lattice. The two answers match precisely after **profinite completion** of $\pi^{top}_{1}$.

This is the **Riemann existence theorem** of **file 60 (XII.5)**. The clean form (XII.5.1): the functor
$\Psi : X' \mapsto X'^{an}$ is an equivalence between finite étale coverings of $X$ and finite étale coverings of
$X^{an}$. The $\pi_{1}$-corollary (XII.5.2): $\pi^{\acute{e}}_{1}t(X, \phi(x)) \simeq \hat{\pi}^{top}_{1}(X^{an}, x)$ as
profinite groups, where the right side is the profinite completion of the topological $\pi_{1}$.

The Riemann existence theorem is what powers the **transcendental method** of file 50 (X.2.6): the topological
calculation of
$\pi^{top}_{1}(\Sigma_{g}) = \langle s_{1}, \cdots, s_{g}, t_{1}, \cdots, t_{g} | \prod [s_{i}, t_{i}] = 1 \rangle$ for
a smooth proper curve of genus $g$ becomes, after profinite completion, the étale fundamental group
$\pi^{\acute{e}}_{1}t(X_{0})$ of any curve of genus $g$ in any characteristic — *via* Witt-vector lift to characteristic
0, base change to $\mathbb{C}$, and XII.5.2.

> **Closing slogan for file 57.** *$X^{an}$ is the analytic shadow of $X$.* It carries the same local data as $X$ at
> every closed point, after passage to completions. The functor $X \mapsto X^{an}$ is exact and faithful on coherent
> sheaves, and is the universal locally-ringed-$\mathbb{C}$-space gadget representing the points functor. What remains
> is to show that this functor — and the comparison morphism $\phi : X^{an} \to X$ it carries with it — preserves the
> global properties, the cohomology, and the finite étale category that the étale $\pi_{1}$ of files 30–56 was built to
> detect. That is the work of files 58–60.
