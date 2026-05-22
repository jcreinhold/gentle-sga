# Exposé VI §§1–5 (gentle): categories over a base and cartesian morphisms

<!-- source: VI -->

<!-- source: VI.1 -->

## What this file is about

Geometry over a base is geometry parameterised by points of the base. Move the parameter, and the object above moves
with it — a family of curves over a line, a family of spaces over a disc, a stack of sheets over a base of a covering
map. The data hanging over each parameter point is called the fibre. The whole apparatus is held together by a rule that
drags fibres from one point to another whenever a path or a map between points exists. Pulling that rule into focus and
stating exactly what it is, is the work of the next several files.

Replace the base space with a base category, and the family above with another category mapping down to it. The fibre
over an object of the base is what sits directly above that object. The drag rule becomes a question about morphisms:
which arrows above are the legitimate pulled-back versions of arrows below? The answer is a universal property called
being cartesian, and it pins down what pull-back must mean without choosing one. This file develops the basic vocabulary
— categories over a base, fibres, change of base — and ends at the cartesian property, which the next file uses to ask
when pull-back exists and behaves well.

## Opening: from base spaces to base categories

Topological covering theory begins with a base space $B$ and a total space $E \to B$. Algebraic-geometric Galois theory
begins with a base scheme $S$ and a finite étale cover $X \to S$. In both cases the geometry of the cover is controlled
by what happens fibre-wise as the base point varies.

Exposé VI replaces the base _space_ with a base _category_ $\mathcal{E}$, and the cover with a category $\mathcal{F}$
together with a projection functor $p : \mathcal{F} \to \mathcal{E}$. The "fibre over $S$" is the subcategory
$\mathcal{F}_{S} = p^{-1}(S)$ of objects mapping to $S$ and morphisms mapping to $id_{S}$. The structure problem the
exposé sets up: _what does it take for the fibre $\mathcal{F}_{S}$ to vary functorially in $S$ ∈ $\mathcal{E}$_?

The answer comes in three layers, each progressively more structure:

- a category over $\mathcal{E}$ (just the projection $p$),
- a _prefibred_ category (every base morphism $f : T \to S$ admits inverse images, file 36),
- a _fibred_ category (the inverse-image functors compose well, also file 36).

Files 35 (this file) and 36 introduce the layers in order. This file covers §§1–5: the basic vocabulary
($\mathcal{E}$-categories, $\mathcal{E}$-functors, fibre categories, base change in `Cat`) and the central concept of
_cartesian morphism_ — the universal-property formulation of "pull-back along $f$" that makes inverse images canonical
(up to canonical iso). §6's fibred-category axioms are cleanest stated in terms of cartesian morphisms; the work of §5
is to introduce them.

A reading note. SGA VI is bookkeeping-heavy in §§1–3 — many formulae of the form "this functor commutes with that
construction" — and lighter in §§4–5. We summarise the bookkeeping rather than reproducing it; the reader who wants
every diagrammatic verification should keep Vistoli §3.1
([`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained)) open in parallel.

**Running examples.** Two examples thread the abstract material of files 35–38 and connect it to geometry. The first is
the **arrow category** $Ar(\mathcal{E}) = \operatorname{Hom}(\Delta^{1}, \mathcal{E})$, developed as a full worked
section at the close of each file (this file's closing example at the bottom; file 36 §VI.7's cleavage; file 37 §VI.10's
direct image). The second is **quasi-coherent modules**, $S \mapsto QCoh(S)$ over the category of schemes, called out
inline after each key definition and again at file 38 §VI.11(b). The arrow-category example is the one Grothendieck uses
to motivate cartesian morphisms; the QCoh example is the one file 40 onward leans on. We keep both visible. A reader who
only wants the geometry should follow the QCoh callouts and skim the arrow-category sections.

## §VI.1 Universes, categories, equivalences

Throughout the exposé Grothendieck works with a fixed
[universe](34-sites-sheaves-and-pseudofunctors-gentle.md#module-b-2-categories-and-the-2-category-cat) $\mathcal{U}$.
`Set` denotes the category of $\mathcal{U}$-small sets, `Cat` the category of $\mathcal{U}$-small categories. (We do
_not_ use the 2-category structure of `Cat` until §VI.7; here `Cat` is just a 1-category.) $Ob(\mathcal{C})$ and
$Fl(\mathcal{C})$ are the sets of objects and arrows of a category $\mathcal{C}$.

A functor $F : \mathcal{C} \to \mathcal{C}'$ is **faithful** (resp. **fully faithful**) if
$\operatorname{Hom}_{\mathcal{C}}(S, T) \to \operatorname{Hom}_{\mathcal{C}'}(F S, F T)$ is injective (resp. bijective)
for every pair $(S, T)$. $F$ is an **equivalence** if it is fully faithful and every object of $\mathcal{C}'$ is
isomorphic to one of the form $F(S)$. Equivalently: there is a functor $G : \mathcal{C}' \to \mathcal{C}$ and natural
isomorphisms $G F \cong id_{\mathcal{C}}$, $F G \cong id_{\mathcal{C}'}$. The functor $G$ is called a **quasi-inverse**
of $F$. Quasi-inverses are unique up to unique isomorphism.

We assume the reader is comfortable with limits and colimits in `Cat` (in particular with the fibre product
$\mathcal{C} \times_{\mathcal{D}} \mathcal{C}'$, defined by
$Ob(\mathcal{C} \times_{\mathcal{D}} \mathcal{C}') = Ob(\mathcal{C}) \times_{Ob(\mathcal{D})} Ob(\mathcal{C}')$ and
similarly for arrows). These are the only categorical limits we use.

## §VI.2 Categories over $\mathcal{E}$

<!-- source: VI.2 -->

Fix a category $\mathcal{E}$. An object of $Cat_{/ \mathcal{E}}$ — that is, an **$\mathcal{E}$-category** — is a pair
$(\mathcal{F}, p)$ consisting of a category $\mathcal{F}$ and a functor $p : \mathcal{F} \to \mathcal{E}$, the
**projection**. We write just $\mathcal{F}$ when $p$ is understood.

An **$\mathcal{E}$-functor** $f : \mathcal{F} \to \mathcal{G}$ between $\mathcal{E}$-categories $(\mathcal{F}, p)$,
$(\mathcal{G}, q)$ is a functor satisfying $q \circ f = p$ strictly (not just up to isomorphism). The set of
$\mathcal{E}$-functors from $\mathcal{F}$ to $\mathcal{G}$ is

```text
Hom_ℰ(ℱ, 𝒢)  =  { f : ℱ → 𝒢  :  q ∘ f = p }.
```

These are the morphisms of $Cat_{/ \mathcal{E}}$.

### $\alpha$-morphisms

Given any morphism $\alpha : T \to S$ in $\mathcal{E}$ and any $\mathcal{E}$-category $(\mathcal{G}, q)$, a morphism $v$
in $\mathcal{G}$ is an **$\alpha$-morphism** if $q(v) = \alpha$. When $\alpha = id_{S}$, an $\alpha$-morphism is an
**$S$-morphism** — a morphism in the fibre $\mathcal{G}_{S}$ (= the inverse image of $id_{S}$).

### $\mathcal{E}$-natural transformations

For two $\mathcal{E}$-functors $f, g : \mathcal{F} \to \mathcal{G}$, an **$\mathcal{E}$-natural transformation** (or
**$\mathcal{E}$-homomorphism**) $u : f \Longrightarrow g$ is a natural transformation such that, for every
$\xi \in Ob \mathcal{F}$, the component $u(\xi) : f(\xi) \to g(\xi)$ is an $id_{p(\xi)}$-morphism in $\mathcal{G}$.

$\mathcal{E}$-functors and $\mathcal{E}$-natural transformations form a category

```text
Hom_{ℰ/-}(ℱ, 𝒢)  ⊆  Hom(ℱ, 𝒢)
```

— a (full? not quite: full on objects = on functors, but the hom-sets are restricted to $\mathcal{E}$-natural
transformations) — sub- 2-cell collection of the all-natural-transformations category. Vertical and horizontal
compositions of $\mathcal{E}$-natural transformations are again $\mathcal{E}$-natural; this is part of what makes
$Cat_{/ \mathcal{E}}$ itself a 2-category. The composition pairings `(I)`–`(IV)` of the source (the standard interchange
laws and unit laws for vertical and horizontal composition) hold; we do not reproduce them.

### Special notation: cartesian sections

When $\mathcal{F} = \mathcal{E}$ (the identity $\mathcal{E}$-category), an $\mathcal{E}$-functor
$\mathcal{E} \to \mathcal{G}$ is just a **section** of $q : \mathcal{G} \to \mathcal{E}$. We write

```text
Γ(𝒢 / ℰ)  =  Hom_ℰ(ℰ, 𝒢),
Γ(𝒢 / ℰ)̲  =  Hom_{ℰ/-}(ℰ, 𝒢),
```

for the set of sections (resp. category of sections and $\mathcal{E}$-natural transformations between them). We use this
notation in §VI.5 and again in file 38.

## §VI.3 Base change

<!-- source: VI.3 -->

Let $\lambda : \mathcal{E}' \to \mathcal{E}$ be a functor. For an $\mathcal{E}$-category $(\mathcal{F}, p)$, the **base
change** of $\mathcal{F}$ along $\lambda$ is the fibre product

```text
λ* ℱ  :=  ℱ ×_ℰ ℰ′,
```

regarded as an $\mathcal{E}'$-category via the projection
$pr_{2} : \mathcal{F} \times_{\mathcal{E}} \mathcal{E}' \to \mathcal{E}'$. This defines a functor

$$
\lambda*  :  Cat_{/\mathcal{E}}  \longrightarrow  Cat_{/\mathcal{E}'}.
$$

It is right adjoint to "restriction of the base" (which views an $\mathcal{E}'$-category as an $\mathcal{E}$-category by
composing with $\lambda$). Concretely, $\lambda*$ commutes with all categorical limits (since it is a right adjoint).

### The base-change isomorphism

The central diagram in this section is the canonical isomorphism

```text
(*)   Hom_{ℰ′/-}(λ*ℱ, λ*𝒢)  ≅  Hom_{ℰ/-}(λ*ℱ, 𝒢),
```

natural in $\mathcal{F}, \mathcal{G}, \mathcal{E}'$. The forward map is composition with
$pr_{1} : \lambda*\mathcal{G} = \mathcal{G} \times_{\mathcal{E}} \mathcal{E}' \to \mathcal{G}$. Both sides describe
"$\mathcal{E}'$-functors from the pulled-back source", with the right-hand side viewing the target as an
$\mathcal{E}$-category. _This result says: pulling back the source along $\lambda$ is the same as forgetting the
$\mathcal{E}'$-structure of the target._ (The proof is a direct verification on objects and 2-cells.)

A consequence we use: for every $\mathcal{E}$-functor $f : \mathcal{F} \to \mathcal{G}$, applying $\lambda*$ gives an
$\mathcal{E}'$-functor $f' = \lambda*(f) : \lambda*\mathcal{F} \to \lambda*\mathcal{G}$, and the assignment
$f \mapsto f'$ is the action of $\lambda*$ on 1-morphisms. On $\mathcal{E}$-natural transformations
$u : f \Longrightarrow g$, the component is $u'(\xi', S') = (u(\xi), id_{S'})$ for $\xi' = (\xi, S')$ in
$\lambda*\mathcal{F}$ over $S' \in Ob \mathcal{E}'$.

### Transitivity

For composable $\lambda' : \mathcal{E}'' \to \mathcal{E}'$ and $\lambda : \mathcal{E}' \to \mathcal{E}$, the canonical
isomorphism

```text
(λ ∘ λ')*  ≅  λ'* ∘ λ*
```

holds in $Cat_{/\mathcal{E}''}$. Concretely it is the canonical iso

```text
ℱ ×_ℰ ℰ″  ≅  (ℱ ×_ℰ ℰ′) ×_{ℰ′} ℰ″
```

— the associativity of the categorical fibre product. This is the bookkeeping that file 36's pentagon coherence will
refine into a 2-cell statement.

### Compatibility with composition

Base change preserves composition of $\mathcal{E}$-functors: $(g \circ f)' = g' \circ f'$ for composable
$f : \mathcal{F} \to \mathcal{G}$ and $g : \mathcal{G} \to \mathcal{H}$, and $(v * u)' = v' * u'$ for
$\mathcal{E}$-natural transformations. This is part of saying that $\lambda*$ is a 2-functor
$Cat_{/\mathcal{E}} \to Cat_{/\mathcal{E}'}$, though SGA VI does not state it that way. We use this fact freely.

## §VI.4 Fibre categories; $\mathcal{E}$-equivalences

<!-- source: VI.4 -->

For an $\mathcal{E}$-category $(\mathcal{F}, p)$ and $S \in Ob \mathcal{E}$, the **fibre category** $\mathcal{F}_{S}$ is

```text
ℱ_S  =  p⁻¹(S)  =  ℱ ×_ℰ {S},
```

where ${S}$ is the one-object subcategory of $\mathcal{E}$ containing just $id_{S}$. Concretely,
$Ob \mathcal{F}_{S} = { \xi \in Ob \mathcal{F} : p(\xi) = S}$ and morphisms
$\mathcal{F}_{S}(\xi, \xi') = { u : \xi \to \xi' in \mathcal{F} : p(u) = id_{S}}$.

Compatibility with base change. For any $\lambda : \mathcal{E}' \to \mathcal{E}$ and $S' \in Ob \mathcal{E}'$ with
$S = \lambda(S')$, the projection $pr_{1} : \lambda*\mathcal{F} \to \mathcal{F}$ restricts to an isomorphism of fibres

$$
(\lambda*\mathcal{F})_{S'}  \cong  \mathcal{F}_{S}.
$$

So fibres are intrinsic: they do not depend on whether we view ℱ as an $\mathcal{E}$- or an $\mathcal{E}'$-category.

### VI.4.1 — Fully faithful is preserved under base change

<!-- source: VI.4.1 -->

_This result says: if $f : \mathcal{F} \to \mathcal{G}$ is fully faithful as a functor (so the underlying map on
hom-sets is bijective), then the pulled-back functor $f' : \lambda*\mathcal{F} \to \lambda*\mathcal{G}$ is also fully
faithful, for every base change $\lambda : \mathcal{E}' \to \mathcal{E}$._

**Proposition.** Let $f : \mathcal{F} \to \mathcal{G}$ be an $\mathcal{E}$-functor that is fully faithful (as an
ordinary functor). Then for every $\lambda : \mathcal{E}' \to \mathcal{E}$, the functor
$f' = \lambda*(f) : \lambda*\mathcal{F} \to \lambda*\mathcal{G}$ is fully faithful.

**Proof.** A morphism $(u, \beta) : (\xi, S') \to (\xi', T')$ in $\lambda*\mathcal{F}$ projects to
$(p(u), \lambda(\beta)) = (p(u), \lambda(\beta))$ in $\mathcal{E}$. Bijectivity of $f'$ on the hom-set
$\operatorname{Hom}_{\lambda*\mathcal{F}}((\xi, S'), (\xi', T')) \to \operatorname{Hom}_{\lambda*\mathcal{G}}(...)$
follows from bijectivity of $f$ on the appropriate fibre — which is given by hypothesis. (More abstractly: a fibre
product of fully faithful functors with arbitrary functors is fully faithful, by a pointwise limit argument.) ∎

The analogous statement with "fully faithful" replaced by "equivalence" _fails_. The next proposition pins down the
correct strengthening.

### VI.4.2 — Characterisation of $\mathcal{E}$-equivalences

<!-- source: VI.4.2 -->

_This result says: an $\mathcal{E}$-functor $f : \mathcal{F} \to \mathcal{G}$ admits an $\mathcal{E}$-quasi- inverse iff
it is an equivalence on every fibre, iff base change preserves the property "is an equivalence", iff $f$ is fully
faithful and surjective on fibres up to $S$-isomorphism. The four conditions are equivalent._

**Proposition.** For an $\mathcal{E}$-functor $f : \mathcal{F} \to \mathcal{G}$, the following are equivalent:

1. There exists an $\mathcal{E}$-functor $g : \mathcal{G} \to \mathcal{F}$ and $\mathcal{E}$-natural isomorphisms
   $g f \cong id_{\mathcal{F}}$, $f g \cong id_{\mathcal{G}}$.
1. For every $\mathcal{E}' \to \mathcal{E}$, the functor
   $f' = f \times_{\mathcal{E}} \mathcal{E}' : \lambda*\mathcal{F} \to \lambda*\mathcal{G}$ is an equivalence of
   categories.
1. $f$ is an equivalence of categories, _and_ for every $S \in Ob \mathcal{E}$ the induced functor
   $f_{S} : \mathcal{F}_{S} \to \mathcal{G}_{S}$ is an equivalence.
1. $f$ is fully faithful, _and_ for every $S \in Ob \mathcal{E}$ and every $\eta \in Ob \mathcal{G}_{S}$, there exists
   $\xi \in Ob \mathcal{F}_{S}$ and an $S$-isomorphism $f(\xi) \cong \eta$.

**Proof sketch.** $(1) \Rightarrow (2)$: $(g, f g \cong id, g f \cong id)$ is preserved under base change by the
functoriality of $\lambda*$. $(2) \Rightarrow (3)$: take $\mathcal{E}' = \mathcal{E}$ (giving $f$ is an equivalence) and
$\mathcal{E}' = {S}$ (giving each $f_{S}$ is an equivalence). $(3) \Rightarrow (4)$: trivial. $(4) \Rightarrow (1)$:
choose, for each $\eta \in Ob \mathcal{G}$, an object $g(\eta) \in Ob \mathcal{F}$ with $p(g(\eta)) = q(\eta)$ and an
isomorphism $u(\eta) : f(g(\eta)) \to \eta$ over $id_{q(\eta)}$. Full-faithfulness of $f$ makes $g$ into a functor and
$u$ into an $\mathcal{E}$-natural isomorphism $f g \cong id_{\mathcal{G}}$. The dual $g f \cong id_{\mathcal{F}}$ is
then forced. ∎

### VI.4.3 — Definition of $\mathcal{E}$-equivalence

<!-- source: VI.4.3 -->

_This result says: a functor satisfying any one of the four equivalent conditions of VI.4.2 deserves a name; we call it
an **$\mathcal{E}$-equivalence**._

**Definition.** An $\mathcal{E}$-functor $f : \mathcal{F} \to \mathcal{G}$ is an **$\mathcal{E}$-equivalence** if it
satisfies the equivalent conditions of VI.4.2.

The distinction matters: not every equivalence of underlying categories is an $\mathcal{E}$-equivalence. The next
corollary identifies when it is.

### VI.4.4 — Transportable $\mathcal{E}$-categories

<!-- source: VI.4.4 -->

_This result says: when the projection $p : \mathcal{F} \to \mathcal{E}$ admits isomorphisms freely along base
isomorphisms ("transportable"), the pathology of the previous sentence vanishes: an underlying equivalence is
automatically an $\mathcal{E}$-equivalence._

**Corollary.** Suppose $p : \mathcal{F} \to \mathcal{E}$ is **transportable**: for every isomorphism $\alpha : T \to S$
in $\mathcal{E}$ and every $\xi \in \mathcal{F}_{T}$, there is an isomorphism $u$ in $\mathcal{F}$ with source $\xi$ and
$p(u) = \alpha$. Then every $\mathcal{E}$-functor $f : \mathcal{F} \to \mathcal{G}$ that is an equivalence of underlying
categories is an $\mathcal{E}$-equivalence.

**Proof.** Apply criterion (4) of VI.4.2: full-faithfulness is inherited from the underlying-categories statement; the
fibre-surjectivity follows from transportability of $p$ plus the essential surjectivity of $f$. ∎

The transportability hypothesis is mild — every fibred category in groupoids satisfies it (file 36 §VI.6.1) — but it is
not automatic.

### VI.4.5 — Hom-categories under $\mathcal{E}$-equivalence

<!-- source: VI.4.5 -->

*This result says: an $\mathcal{E}$-equivalence $f : \mathcal{F} \to \mathcal{G}$ induces equivalences of
$\mathcal{E}$-functor categories
$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{G}, \mathcal{H}) \simeq \operatorname{Hom}_{\mathcal{E}/-}(\mathcal{F}, \mathcal{H})$and$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{H}, \mathcal{F}) \simeq \operatorname{Hom}_{\mathcal{E}/-}(\mathcal{H}, \mathcal{G})$for
every other$\mathcal{E}$-category $\mathcal{H}$.*

**Corollary.** Let $f : \mathcal{F} \to \mathcal{G}$ be an $\mathcal{E}$-equivalence. For every $\mathcal{E}$-category
$\mathcal{H}$, the functors

```text
f^*  :  Hom_{ℰ/-}(𝒢, ℋ)  →  Hom_{ℰ/-}(ℱ, ℋ),    G ↦ G ∘ f,
f_*  :  Hom_{ℰ/-}(ℋ, ℱ)  →  Hom_{ℰ/-}(ℋ, 𝒢),    H ↦ f ∘ H,
```

are equivalences of categories.

**Proof.** Compose with the $\mathcal{E}$-quasi-inverse $g$ of $f$ from condition (1) of VI.4.2 to get a quasi-inverse
on either side. ∎

This is the "Yoneda" content of $\mathcal{E}$-equivalence: it does not just mean "equivalent", it means equivalent in a
way that preserves all the categorical mapping data over $\mathcal{E}$.

## §VI.5 Cartesian morphisms, inverse images, cartesian functors

<!-- source: VI.5 -->

The protagonist of the exposé. Let $(\mathcal{F}, p)$ be an $\mathcal{E}$-category and consider a morphism
$\alpha : \eta \to \xi$ in $\mathcal{F}$ over $f := p(\alpha) : T \to S$.

### Motivation

Take $\mathcal{E} = (Sch / S_{0})$ ($S$-schemes for some base $S_{0}$) and $\mathcal{F} = (Sch / S_{0})^{\to}$ (the
arrow category, with target functor to $\mathcal{E}$). An object of $\mathcal{F}$ is a pair $(X, X \to Y)$ (a scheme
with a distinguished morphism to its image in $\mathcal{E}$). A morphism $\alpha : (X', X' \to Y') \to (X, X \to Y)$ in
$\mathcal{F}$ is a square

$$
X'  \to  X
\downarrow      \downarrow
Y'  \to  Y.
$$

When the square is a _pullback square_, the universal property is: for any other map $X'' \to X$ over $Y' \to Y$, there
is a unique factorisation $X'' \to X' \to X$. This is the classical "$X'$ is the pullback $X \times_{Y} Y'$". The map
$\alpha$ represents the pullback, and the universal property is exactly that the hom-functor `Hom_{Sch/Y'}(–, X')` is
naturally isomorphic to a "hom over $f$" functor `Hom_f(–, X)`.

§VI.5.1 abstracts this universal property to any $\mathcal{E}$-category.

### VI.5.1 — Definition: cartesian morphism, inverse image

<!-- source: VI.5.1 -->

_This result says: a morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$ is **cartesian over $f$** when the pair
$(\eta, \alpha)$ represents the functor $\eta' \mapsto \operatorname{Hom}_{f}(\eta', \xi)$ from
$\mathcal{F}^{\circ}_{T}$ to `Set`. Equivalently: every other $f$-morphism into $\xi$ factors uniquely through $\alpha$
after restriction to a $T$-morphism. When such an $(\eta, \alpha)$ exists, it is unique up to unique $T$-isomorphism,
and $\eta$ is called the **inverse image** $f*(\xi)$ of $\xi$ along $f$._

**Definition.** A morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$ is **cartesian** (over $f := p(\alpha) : T \to S$)
if, for every $\eta' \in Ob \mathcal{F}_{T}$ and every $f$-morphism $u : \eta' \to \xi$, there exists a _unique_
$T$-morphism $\bar{u} : \eta' \to \eta$ such that $u = \alpha \circ \bar{u}$. Equivalently: the precomposition map

```text
α_* : Hom_T(η', η)  ⟶  Hom_f(η', ξ),    v ↦ α ∘ v,
```

is bijective for every $\eta' \in Ob \mathcal{F}_{T}$.

**Inverse image.** When such a pair $(\eta, \alpha)$ exists, $\eta$ is unique in $\mathcal{F}_{T}$ up to canonical
$T$-isomorphism. We call $\eta$ _an_ **inverse image** of $\xi$ along $f$, written $f*(\xi)$ or $\xi \times_{S} T$ when
no confusion arises. The chosen $\alpha$ is denoted $\alpha_{f}(\xi) : f*(\xi) \to \xi$.

When the inverse image of every $\xi \in Ob \mathcal{F}_{S}$ exists, the assignment $\xi \mapsto f*(\xi)$ becomes a
functor $f* : \mathcal{F}_{S} \to \mathcal{F}_{T}$ (covariant), called the **inverse-image functor** along $f$.
Functoriality on morphisms: for $\lambda : \xi \to \xi'$ an $S$-morphism and chosen cartesian morphisms
$\alpha_{f}(\xi) : f*(\xi) \to \xi$, $\alpha_{f}(\xi') : f*(\xi') \to \xi'$, there is a unique $T$-morphism
$f*(\lambda) : f*(\xi) \to f*(\xi')$ making the obvious square commute.

> **In quasi-coherent modules** ($\mathcal{E} = Sch$, $\mathcal{F}_{S} = QCoh(S)$). For $f : T \to S$ and a
> quasi-coherent module $M$ on $S$, the inverse image is the usual pullback sheaf
> $f*(M) = f^{-1}M \otimes_{f^{-1}\mathcal{O}_{S}} \mathcal{O}_{T}$. The cartesian morphism
> $\alpha_{f}(M) : f*(M) \to M$ is the canonical map in the sheaf category, and the universal property of VI.5.1 unpacks
> to the universal property of pullback. The inverse-image functor $f* : QCoh(S) \to QCoh(T)$ is the standard pullback
> of quasi-coherent sheaves. We will return to this example in §VI.11(b) and again in file 40 §VIII.1, where the QCoh
> fibred category is the protagonist.

### Properties of cartesian morphisms

Two facts we use without comment:

- **Stability under isomorphism.** If $\alpha : \eta \to \xi$ is cartesian over $f$, and $\mu : \eta' \to \eta$ is a
  $T$-isomorphism, $\lambda : \xi \to \xi'$ is an $S$-isomorphism, then $\lambda \circ \alpha \circ \mu^{-1}$ is
  cartesian over $f$.
- **Composition pasting (anticipating VI.6.1's Fib II).** If $\alpha : \eta \to \xi$ is cartesian over $f$ and
  $\beta : \zeta \to \eta$ is cartesian over $g$, then $\alpha \circ \beta : \zeta \to \xi$ is cartesian over
  $f \circ g$ _iff_ a certain coherence holds. (The "iff" is what Fib II asserts; not every prefibred category is
  fibred. This will be the point of file 36 §VI.6.1.)

### VI.5.2 — Definition: cartesian functor

<!-- source: VI.5.2 -->

_This result says: an $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ is **cartesian** when it sends cartesian
morphisms to cartesian morphisms. Cartesian functors form a full subcategory `Hom_cart(ℱ, 𝒢) ⊂ Hom_{ℰ/-}(ℱ, 𝒢)`._

**Definition.** An $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ is a **cartesian functor** if, for every
cartesian morphism $\alpha$ in $\mathcal{F}$, the image $F(\alpha)$ is cartesian in $\mathcal{G}$. We write
$\operatorname{Hom}_{cart}(\mathcal{F}, \mathcal{G})$ for the full subcategory of
$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{F}, \mathcal{G})$ whose objects are cartesian functors.

(Why "full"? Because the cartesianness is a property of objects — functors — not of morphisms. Every
$\mathcal{E}$-natural transformation between two cartesian functors is allowed; no extra restriction is imposed on
2-cells.)

The interpretation: cartesian functors are those that "respect the inverse-image structure" — they preserve the
universal property that defines $f*(\xi)$ from $\xi$. Equivalently, when both $\mathcal{F}$ and $\mathcal{G}$ have
inverse-image functors $f*_{\mathcal{F}} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ and
$f*_{\mathcal{G}} : \mathcal{G}_{S} \to \mathcal{G}_{T}$, a cartesian functor $F : \mathcal{F} \to \mathcal{G}$ provides
a _natural isomorphism_ $F \circ f*_{\mathcal{F}} \cong f*_{\mathcal{G}} \circ F$ (file 37 §VI.8 will make this 2-cell
explicit).

### VI.5.3 — $\mathcal{E}$-equivalences are cartesian

<!-- source: VI.5.3 -->

_This result says: every $\mathcal{E}$-equivalence is automatically a cartesian functor; cartesianness is invariant
under $\mathcal{E}$-natural isomorphism; composites of cartesian functors are cartesian. So $\operatorname{Hom}_{cart}$
is a sensible 2-categorical sub-structure of $\operatorname{Hom}_{\mathcal{E}/-}$._

**Proposition.**

1. Every $\mathcal{E}$-equivalence $F : \mathcal{F} \to \mathcal{G}$ is a cartesian functor. Moreover, a morphism
   $\alpha$ in $\mathcal{F}$ is cartesian iff $F(\alpha)$ is cartesian.
1. If $F, G : \mathcal{F} \to \mathcal{G}$ are isomorphic $\mathcal{E}$-functors and $F$ is cartesian, then $G$ is
   cartesian.
1. If $F : \mathcal{F} \to \mathcal{G}$ and $F' : \mathcal{G} \to \mathcal{H}$ are cartesian, then
   $F' \circ F : \mathcal{F} \to \mathcal{H}$ is cartesian.

**Proof.** (3) is immediate from the definition. (2) follows from the stability-under-isomorphism property of cartesian
morphisms. (1) follows from criterion (3) of VI.4.2: an $\mathcal{E}$-equivalence induces equivalences
$f_{S} : \mathcal{F}_{S} \to \mathcal{G}_{S}$ on every fibre, so the universal property of $\alpha : \eta \to \xi$ in
$\mathcal{F}_{T}$ translates to the universal property of $F(\alpha) : F(\eta) \to F(\xi)$ in $\mathcal{G}_{T}$ via the
equivalence. ∎

### VI.5.4 — Hom_cart is invariant under $\mathcal{E}$-equivalence

<!-- source: VI.5.4 -->

_This result says: an $\mathcal{E}$-equivalence induces equivalences not just of $\mathcal{E}$-functor categories
(VI.4.5) but of the cartesian- functor subcategories. So the fundamental structure `Hom_cart(–, –)` is preserved by
$\mathcal{E}$-equivalences._

**Corollary.** Let $F : \mathcal{F} \to \mathcal{G}$ be an $\mathcal{E}$-equivalence. For every $\mathcal{E}$-category
$\mathcal{H}$, the functors

```text
F^*  :  Hom_cart(𝒢, ℋ)  →  Hom_cart(ℱ, ℋ),    G ↦ G ∘ F,
F_*  :  Hom_cart(ℋ, ℱ)  →  Hom_cart(ℋ, 𝒢),    H ↦ F ∘ H,
```

are equivalences of categories. Furthermore, $G : \mathcal{G} \to \mathcal{H}$ is cartesian iff $G \circ F$ is
cartesian; $H : \mathcal{H} \to \mathcal{F}$ is cartesian iff $F \circ H$ is cartesian.

**Proof.** Apply VI.4.5 to get equivalences of $\operatorname{Hom}_{\mathcal{E}/-}$, then restrict to the cartesian
subcategories using VI.5.3 (1)–(3). ∎

A consequence we will use in file 37: there is a sub-2-category `Cat^{cart}_{/ ℰ} ⊆ Cat_{/ ℰ}` whose objects are
arbitrary $\mathcal{E}$-categories, whose 1-cells are cartesian functors, and whose 2-cells are $\mathcal{E}$-natural
transformations. The composition pairings of §VI.2 restrict to it.

### VI.5.5 — Cartesian sections

<!-- source: VI.5.5 -->

_This result says: the cartesian sections of $(\mathcal{F}, p)$ over $\mathcal{E}$ form a category, denoted
$Lim\leftarrow(\mathcal{F} / \mathcal{E})$, which is functorial (covariantly) in $\mathcal{F}$._

**Definition.** Let $(\mathcal{F}, p)$ be an $\mathcal{E}$-category. A **cartesian section** of $\mathcal{F}$ over
$\mathcal{E}$ is a cartesian $\mathcal{E}$-functor $s : \mathcal{E} \to \mathcal{F}$ (viewing $\mathcal{E}$ as an
$\mathcal{E}$-category via $id_{\mathcal{E}}$). The category of cartesian sections is

```text
Lim←(ℱ / ℰ)  =  Hom_cart(ℰ, ℱ)
```

— a sub-category of `Γ(ℱ / ℰ)̲ = Hom_{ℰ/-}(ℰ, ℱ)`.

By VI.5.4, `Lim←(– / ℰ)` is a functor `Cat^{cart}_{/ ℰ} → Cat`.

**Why "Lim←"?** Grothendieck's notation reflects the slogan that cartesian sections compute the _projective limit_ of a
fibred category over $\mathcal{E}$: the values $s(S) \in \mathcal{F}_{S}$ together with the cartesian transition data
form a coherent system, and the universal such system is the cartesian section. We will see this slogan again in file 38
§VI.12: a cartesian section is a "compatible family of fibre-wise objects" — exactly the data of descent.

## Worked example: the arrow category $Ar(Sch / S)$

The example we have alluded to throughout, made fully explicit. Fix a base scheme $S_{0}$ and let
$\mathcal{E} = (Sch / S_{0})$, the category of $S_{0}$-schemes. Define

```text
ℱ  =  Ar(ℰ)  =  Hom(Δ¹, ℰ)
```

— the arrow category of $\mathcal{E}$. An object of $\mathcal{F}$ is a morphism $X \to Y$ of $S_{0}$-schemes; a morphism
in $\mathcal{F}$ from $(X' \to Y')$ to $(X \to Y)$ is a commutative square

```text
X'  --u--> X
↓          ↓
Y'  --f--> Y.
```

The projection $p : \mathcal{F} \to \mathcal{E}$ sends $(X \to Y) \mapsto Y$ and a square to the bottom row $f$.

**Fibre over $Y$.** $\mathcal{F}_{Y} = (Sch / Y)$, the slice category over$Y$. (Objects are$S_{0}$-schemes mapping
to$Y$; morphisms are$Y$-morphisms.)

**$\mathcal{E}$-functors and $\mathcal{E}$-natural transformations.** An $\mathcal{E}$-functor
$Ar(\mathcal{E}) \to Ar(\mathcal{E})$ over$\mathcal{E}$is a functor that, on each fibre, sends$Y$-schemes to$Y$-schemes
(because it must preserve the projection to$Y$). The identity is one such; so is "take the fibre product with a
fixed$Y$-scheme$Z$":$(X \to Y) \mapsto (X \times_{Y} Z \to Y)$.

**Cartesian morphisms.** A square

```text
X'  --u--> X
↓          ↓
Y'  --f--> Y
```

is cartesian (over $f$) iff the square is a _pullback square_ of schemes. This is exactly the universal property: for
any $Y'$-scheme `X''` and any morphism $X'' \to X$ over $f$, there is a unique factorisation $X'' \to X' \to X$.

**Inverse-image functor.** For $f : Y' \to Y$ in$\mathcal{E}$, the inverse-image
functor$f^{*} : \mathcal{F}_{Y} \to \mathcal{F}_{Y'}$is the standard base
change:$(X \to Y) \mapsto (X \times_{Y} Y' \to Y')$. The inverse images exist for *every* morphism$f$and *every*
object$(X \to Y) \in \mathcal{F}_{Y}$, because fibre products of schemes always exist. So$Ar(\mathcal{E})$ is
*prefibred* over $\mathcal{E}$ — Fib I holds (file 36 §VI.6.1).

**Cartesian functors.** A functor $F : Ar(\mathcal{E}) \to Ar(\mathcal{E})$ over $\mathcal{E}$ is cartesian iff it
commutes with base change (up to canonical iso). The identity is cartesian; "fibre product with a fixed scheme $Z$ over
$S_{0}$", $(X \to Y) \mapsto (X \times_{S_{0}} Z \to Y)$, is cartesian (it sends pullback squares to pullback squares).

**Cartesian sections.** $Lim\leftarrow(Ar(\mathcal{E}) / \mathcal{E})$ is the category of cartesian
sections$s : \mathcal{E} \to Ar(\mathcal{E})$. A section assigns, to each $Y \in Ob \mathcal{E}$, an object
$(s(Y) \to Y) \in Ar(\mathcal{E})_{Y}$, and to each $f : Y' \to Y$ a square. Cartesianness says every such square is a
pullback square. So a cartesian section is the same as: a single object $X \to S_{0}$ in $Ar(\mathcal{E})_{S_{0}}$ such
that every fibre$s(Y) = X \times_{S_{0}} Y$, with cartesian transition squares. _That is: a cartesian section is
determined by its value at the terminal object $S_{0} \in Ob \mathcal{E}$._

This worked example will recur in files 36, 37, 38 (where it becomes file 38 §VI.11(a)).

## Continuing on

File 36 takes the next step: the **fibred category** axioms (Fib I, Fib II) demand that the inverse-image functors
_exist for every morphism_ (Fib I) _and that they compose well_ (Fib II). The arrow category above satisfies both — it
is fibred. In general, prefibred (Fib I alone) is not the same as fibred (Fib I + Fib II), and the "well" of Fib II is
exactly what file 36's **cleavages** organise into a coherent system.
