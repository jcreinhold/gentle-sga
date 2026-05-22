# Topological covering spaces and the fundamental group

## What this file is about

Wrap a rubber band around a doughnut and there is no way to slide it off without breaking the doughnut. Wrap it around a
ball and it slips free. The difference is captured by a single object attached to each shape: a group whose elements are
loops that cannot be pulled tight, considered up to continuous deformation. This is the fundamental group, the oldest
precise sense in which a space has a shape distinct from its size.

A second picture stacks above the first. Some shapes admit unbranched covers — neat stacks of identical sheets laid over
the original. The covers of a space are governed by its fundamental group in a tight and surprising way. The rest of
this book will rebuild both pictures in algebra, for objects that have no points and no loops. This file states the
geometric original they will be made to recover.

## Why this file exists

Files 31–33 generalise topological covering theory and the topological fundamental group to schemes via Galois
categories. The gentle reader is owed the geometric picture before the algebra. This file collects, in working detail,
the parts of covering-space theory that the rewrite of Exposé V mirrors: covering maps, the fundamental group
$\pi^{top}_{1}(B, b_{0})$, the universal cover, the Galois correspondence between subgroups of $\pi^{top}_{1}$ and
connected coverings, and — for the algebraic analogy specifically — the **profinite completion**
$\hat{\pi}^{top}_{1}(B, b_{0})$ that classifies _finite_ coverings.

A reader fluent in the algebraic-topology textbook treatment (Hatcher Ch. 1; May Ch. 3) can skip this file entirely. A
reader who wants only Exposés I–IV can also skip it. A reader who wants Exposé V should read it, lightly, before files
30–33: each algebraic theorem in the rewrite has a topological prototype displayed here.

## Covering maps

A continuous surjection $p : E \to B$ is a **covering map** when every point $b \in B$ has an open neighborhood
$U \subseteq B$ such that the inverse image splits as a disjoint union of homeomorphic copies of $U$:

```text
p⁻¹(U) ≅ ⨆_{d ∈ D} U_d,    each p|_{U_d} : U_d → U a homeomorphism,
```

where $D$ is some discrete set called the **fibre over $b$**. The fibres of a covering are discrete, the local picture
is trivial ($U \times D$), and the global picture is a stack of sheets that twists over $B$ in a way controlled by the
topology of $B$.

The simplest non-trivial example is the exponential map

```text
p : ℝ → S¹,    p(t) = e^{2πi t},
```

with discrete fibre $\mathbb{Z}$. Every connected component of $p^{-1}(U)$ for a small enough open arc
$U \subseteq S^{1}$ maps homeomorphically onto $U$. A second example: the squaring map $q : S^{1} \to S^{1}$,
$z \mapsto z^{2}$, with discrete fibre of cardinality `2`. The exponential example is **infinite-sheeted**; the squaring
example is **finite-sheeted of degree `2`**.

A covering is **finite** when every fibre is finite. (For $B$ connected, all fibres then have the same cardinality.)
Finite coverings are the topological analogue of finite étale morphisms.

#### Aside (algebraic geometry analogy).

_Skip if you have not read file 04._ A covering $p : E \to B$ of topological spaces is the geometric prototype of an
étale morphism $f : X \to Y$ of schemes. The "local triviality" $p^{-1}(U) \cong U \times D$ is the topological shadow
of the local form theorem I.7.6 (file 11), and the discrete fibre $D$ is the topological shadow of the étale fibre
`Spec(κ(y)^{sep, finite})`. File 04's split-into-fields description of the étale fibre is the algebraic version of "the
fibre of $p$ is a discrete set."

## Lifting paths and homotopies

The fundamental theorem about coverings is **path lifting**: if $p : E \to B$ is a covering, $e_{0} \in E$, and
$\gamma : [0, 1] \to B$ is a path with $\gamma(0) = p(e_{0})$, then there exists a _unique_ path
$\tilde{\gamma} : [0, 1] \to E$ with $\tilde{\gamma}(0) = e_{0}$ and $p \circ \tilde{\gamma} = \gamma$.

The corresponding **homotopy lifting** holds: a homotopy $H : [0, 1] \times [0, 1] \to B$ of paths in $B$, together with
a lift $\tilde{\gamma}_{0}$ of one boundary path, lifts uniquely to a homotopy in $E$. Concretely, two paths $\gamma$,
$\gamma' : [0, 1] \to B$ from $b_{0}$ to $b_{1}$ that are homotopic (rel endpoints) lift to paths $\tilde{\gamma}$,
$\tilde{\gamma}' : [0, 1] \to E$ with the _same_ endpoint $\tilde{\gamma}(1) = \tilde{\gamma}'(1)$ over $b_{1}$,
provided they start at the same $e_{0}$ over $b_{0}$.

This last sentence is the engine. It says:

```text
Two homotopic loops at b₀ in B lift to two paths in E with
the same terminal point, regardless of starting point.
```

So a loop $\gamma$ at $b_{0}$ defines a permutation of the fibre $p^{-1}(b_{0})$: each $e \in p^{-1}(b_{0})$ lifts the
loop to a path ending at some $\gamma \cdot e \in p^{-1}(b_{0})$. This permutation depends only on the _homotopy class_
of $\gamma$. In symbols,

```text
π₁^top(B, b₀)   ⟶   Sym(p⁻¹(b₀)),    [γ] ↦ (e ↦ γ ⋅ e),
```

is a group homomorphism — the **monodromy representation** of $p$ at $b_{0}$.

## The fundamental group $\pi^{top}_{1}(B, b_{0})$

Pick a base point $b_{0} \in B$. A **loop** at $b_{0}$ is a continuous map $\gamma : [0, 1] \to B$ with
$\gamma(0) = \gamma(1) = b_{0}$. Two loops $\gamma$, $\gamma'$ are **homotopic rel endpoints** if there is a continuous
$H : [0, 1] \times [0, 1] \to B$ with

```text
H(0, t) = γ(t),    H(1, t) = γ′(t),
H(s, 0) = H(s, 1) = b₀    for every s.
```

The set of homotopy classes of loops at $b_{0}$ is the **fundamental group** of $B$ at $b_{0}$, denoted
$\pi^{top}_{1}(B, b_{0})$. The group operation is concatenation: $[\gamma] \cdot [\gamma'] := [\gamma * \gamma']$, where

```text
(γ * γ′)(t) =  γ(2t)         for 0 ≤ t ≤ 1/2,
              γ′(2t − 1)    for 1/2 ≤ t ≤ 1,
```

with identity the constant loop at $b_{0}$ and inverse $[\gamma]^{-1} := [\bar{\gamma}]$, where
$\bar{\gamma}(t) = \gamma(1 - t)$ is the loop run backwards.

A space $B$ is **simply connected** when $\pi^{top}_{1}(B, b_{0}) = 1$.

### Examples

- $\pi^{top}_{1}(\mathbb{R}^{n}) = 1$. Every loop in $\mathbb{R}^{n}$ shrinks to the constant loop along straight lines.
- $\pi^{top}_{1}(S^{1}) = \mathbb{Z}$. The "winding number" of a loop computes its homotopy class. The generator is the
  loop $t \mapsto e^{2\pi i t}$ going once counterclockwise.
- $\pi^{top}_{1}(\mathbb{C} \times {0}) = \mathbb{Z}$. Same as $S^{1}$, since $\mathbb{C} \times {0}$ deformation-
  retracts to the unit circle.
- $\pi^{top}_{1}(S^{2}) = 1$. Spheres of dimension $\geq 2$ are simply connected.
- $\pi^{top}_{1}(S^{1} \vee S^{1}) = F_{2}$, the free group on two generators. Each generator is the loop going once
  around one of the two circles in the wedge.
- $\pi^{top}_{1}(S^{1} \times S^{1}) = \mathbb{Z} \times \mathbb{Z}$. The torus has two independent loops, the meridian
  and the longitude, and they commute.

The **change of base point** is harmless when $B$ is path- connected: any path $\alpha$ from $b_{0}$ to $b_{1}$ defines
a group isomorphism $\alpha_{*} : \pi^{top}_{1}(B, b_{0}) \to \pi^{top}_{1}(B, b_{1})$ by
$[\gamma] \mapsto [\bar{\alpha} * \gamma * \alpha]$. The isomorphism depends on $[\alpha]$ up to inner automorphism. We
will write $\pi^{top}_{1}(B)$ when the base point is inessential, but every concrete computation lives at a chosen base
point.

## The universal cover

Suppose $B$ is connected, locally arcwise connected, and locally simply connected — three mild conditions satisfied by
every manifold and every CW complex. Then $B$ admits a **universal cover** $\tilde{p} : \tilde{B} \to B$, characterised
by $\tilde{B}$ simply connected. The universal cover dominates every connected cover of $B$: if $p : E \to B$ is
connected, there is a covering map $q : \tilde{B} \to E$ with $p \circ q = \tilde{p}$.

The universal cover supports an action of the **deck transformation group** $\operatorname{Aut}(\tilde{B} / B)$ of
homeomorphisms $\phi : \tilde{B} \to \tilde{B}$ with $\tilde{p} \circ \phi = \tilde{p}$. The fundamental theorem of
covering theory identifies it with the fundamental group:

```text
Aut(B̃ / B)  ≅  π₁^top(B, b₀).
```

The isomorphism is constructive: pick any lift $\tilde{b}_{0} \in \tilde{p}^{-1}(b_{0})$; each loop $\gamma$ at $b_{0}$
lifts to a path $\tilde{\gamma}$ from $\tilde{b}_{0}$ to some other point $\tilde{\gamma}(1) \in \tilde{p}^{-1}(b_{0})$,
and the deck transformation sending $\tilde{b}_{0} \mapsto \tilde{\gamma}(1)$ is the image of $[\gamma]$.

For $B = S^{1}$: the universal cover is $\mathbb{R}$, and the deck group is $\mathbb{Z}$ acting by integer translations.
Match: $\pi^{top}_{1}(S^{1}) = \mathbb{Z}$.

For $B = S^{1} \vee S^{1}$: the universal cover is the infinite 4-valent tree, and the deck group is $F_{2}$ acting by
graph automorphisms.

## The Galois correspondence between subgroups and coverings

Once the universal cover exists, every connected covering of $B$ arises as a quotient of the universal cover by a
subgroup of $\pi^{top}_{1}(B, b_{0})$. This is the
[**topological covering-space classification**](appendix-black-boxes.md) (appendix slug
`topological-covering-space-classification`):

```text
{ connected coverings of B, up to iso }
   ≃   { subgroups H ⊆ π₁^top(B, b₀), up to conjugacy }
```

Concretely, given a subgroup $H \subseteq \pi = \pi^{top}_{1}(B, b_{0})$, the quotient $\tilde{B} / H$ is a connected
covering of $B$ whose fundamental group at $\tilde{b}_{0}$ is $H$. The fibre over $b_{0}$ is the coset space $\pi / H$,
and $\pi$ acts on the fibre by left translation. **Subgroup ↔ cover** is the topological prototype of the
**closed-subgroup ↔ Galois-category-object** dictionary that file 32 will deliver.

A connected covering corresponds to a _subgroup_; an arbitrary (not necessarily connected) covering corresponds to a
finite $\pi$-set, i.e. a disjoint union of coset spaces $\pi / H_{i}$. This matches the slogan that
$\mathcal{C}^{top}_{B}$, the category of all coverings (or all finite coverings) of $B$, is equivalent to $\pi$-sets (or
finite $\pi$-sets).

## Finite coverings and the profinite completion

The algebra of Exposé V will not see $\pi^{top}_{1}$ directly — it will see only its **profinite completion**

```text
π̂₁^top(B, b₀)  :=  lim_{H ⊲ π, [π : H] < ∞} π / H,
```

the projective limit of all finite quotients. An open subgroup of $\hat{\pi}^{top}_{1}$ is, by definition, the preimage
of a subgroup of some finite quotient $\pi / H$; it is automatically of finite index in $\hat{\pi}^{top}_{1}$, and
corresponds via the universal-cover construction to a _finite_ connected cover of $B$.

Restricting the equivalence above to finite coverings, we get:

```text
{ finite connected coverings of B, up to iso }
   ≃   { open subgroups of π̂₁^top(B, b₀), up to conjugacy }.
```

The category $\mathcal{C}^{top}_{B}$ of finite coverings of $B$ is equivalent to the category
$\mathcal{C}(\hat{\pi}^{top}_{1})$ of finite continuous $\hat{\pi}^{top}_{1}$-sets. This is the **topological main
theorem** that file 31 will generalise to schemes.

### Examples of $\hat{\pi}^{top}_{1}$

- $B = S^{1}$: $\pi_{1} = \mathbb{Z}$, $\hat{\pi}_{1} = \hat{\mathbb{Z}} = \lim_{n} \mathbb{Z} / n\mathbb{Z}$. Finite
  covers of $S^{1}$ are the $n$-th-power maps $S^{1} \to S^{1}$, $z \mapsto z^{n}$, classified by the open subgroups
  $n\hat{\mathbb{Z}} \subset \hat{\mathbb{Z}}$.
- $B = \mathbb{C} \ {0}$: same as $S^{1}$, since $\mathbb{C} \ {0}$ deformation- retracts to the unit circle. Finite
  covers: $\mathbb{C} \ {0} \to \mathbb{C} \ {0}$, $z \mapsto z^{n}$.
- $B = S^{1} \vee S^{1}$: $\pi_{1} = F_{2}$, $\hat{\pi}_{1} = \hat{F}_{2}$, the free profinite group on two generators.
  Finite covers correspond to open subgroups of $\hat{F}_{2}$.
- $B = S^{1} \times S^{1}$: $\pi_{1} = \mathbb{Z}^{2}$, $\hat{\pi}_{1} = \hat{\mathbb{Z}}^{2}$. Finite covers of the
  torus are quotients by finite-index sublattices of $\mathbb{Z}^{2}$, all of which are again tori.

#### Aside (why profinite, not finite-index).

_Skip if you already know._ The quotient $\mathbb{Z} / n\mathbb{Z}$ is finite discrete, so already a topological group;
but $\hat{\mathbb{Z}} = \lim_{n} \mathbb{Z} / n\mathbb{Z}$ is not the same as $\mathbb{Z}$ itself, even as an abstract
group. $\hat{\mathbb{Z}}$ is uncountable, and contains $\mathbb{Z}$ densely. The topology distinguishes them: open
subgroups of $\hat{\mathbb{Z}}$ are $n\hat{\mathbb{Z}}$ for $n \geq 1$, all of finite index; subgroups of _finite index_
in $\mathbb{Z}$ are also $n\mathbb{Z}$, but the profinite version pre-packages the projective limit relationship between
them. The relationship `Hom(Ĝ, Π) = Hom_cts(G, Π)` for any profinite $\Pi$ (universal property of the profinite
completion) makes this precise: continuous homomorphisms from $G$ to a profinite group factor through `Ĝ`.

## Galois (= regular) coverings

A connected covering $p : E \to B$ is **Galois** (or **regular**) when its deck transformation group
$\operatorname{Aut}(E / B)$ acts transitively on a — equivalently every — fibre. Equivalently, the subgroup
$p_{*} \pi^{top}_{1}(E) \subseteq \pi^{top}_{1}(B)$ is _normal_.

For a Galois cover, $\operatorname{Aut}(E / B)$ is canonically isomorphic to the quotient
$\pi^{top}_{1}(B) / p_{*} \pi^{top}_{1}(E)$, the **Galois group** of the cover.

For example, the squaring map $S^{1} \to S^{1}$ is Galois with deck group $\mathbb{Z} / 2\mathbb{Z}$ (acting by
$z \mapsto -z$). The universal cover $\mathbb{R} \to S^{1}$ is Galois with deck group $\mathbb{Z}$.

For a connected cover that is _not_ Galois, the deck group fails to act transitively — the fibre still admits a
$\pi^{top}_{1}$-action by monodromy, but the deck group sits inside the normaliser of the corresponding subgroup, not
the whole of $\pi^{top}_{1}$.

## What this prepares

File 30 (= V.1, V.2) introduces the algebraic analogue of deck- transformation groups: a finite group $G$ acting on a
prescheme $X$ by automorphisms, and the **inertia group** at fixed points. The condition "the inertia is trivial
everywhere" is V.2.3's characterisation of when the quotient is étale, and is the algebraic shadow of the topological
condition "the cover is unramified."

File 31 (= V.3, V.4) verifies axioms (G1)–(G6) for finite étale coverings of a connected base and proves the abstract
Galois theorem V.4.1: any category satisfying these axioms is equivalent to $\mathcal{C}(\pi)$ for a profinite group
$\pi$. This is the algebraic generalisation of the topological main theorem
$\mathcal{C}^{top}_{B} \simeq \mathcal{C}(\hat{\pi}^{top}_{1})$ displayed above.

File 32 (= V.5, V.6) develops the formalism — the **fundamental groupoid** (objects = fibre functors, the algebraic
version of "objects = base points"), the **fundamental pro-group**, and the dictionary between exact functors of Galois
categories and continuous group homomorphisms. The change-of- base-point isomorphism
$\alpha_{*} : \pi^{top}_{1}(B, b_{0}) \to \pi^{top}_{1}(B, b_{1})$ of the topological setting becomes the path-class
isomorphism $\pi_{1}(S; a, a')$ of V.7.

File 33 (= V.7) defines

$$
\pi_{1}(S, a)  :=  \operatorname{Aut}(F_{a}),
$$

where $S$ is a connected locally noetherian scheme, $a$ is a geometric point of $S$, and $F_{a}$ is the fibre functor
"geometric points of $X$ over $a$" on the category of finite étale coverings of $S$. The slogan: **the étale fundamental
group $\pi_{1}(S, a)$ is to schemes as the profinite completion $\hat{\pi}^{top}_{1}(B, b)$ is to topological spaces**.
