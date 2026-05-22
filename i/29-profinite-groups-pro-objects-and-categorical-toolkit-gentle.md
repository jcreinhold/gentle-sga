# Profinite groups, pro-objects, and the categorical toolkit

## What this file is about

Two pieces of background, both standing between the geometric picture of the previous file and the algebra of the next.

The first is a kind of group whose elements are compatible choices made across infinitely many finite groups at once.
Picture a sequence of finite rotation groups, each one refining the last; an element of the limiting group is a single
choice in every group that respects every refinement. Groups built this way are compact, totally disconnected, and
infinitely structured. They are the natural symmetry groups for objects assembled from finite layers.

The second is a way of speaking about a single large object as a system of smaller finite shadows it casts. Together
these tools let the book talk about the symmetries of a covering when the cover itself is infinite and only its finite
pieces are tractable.

## Why this file exists

The rewrite of Exposé V §§4–6 cites four pieces of background that have not all appeared in the project before:

- **Profinite groups** — the values of $\operatorname{Aut}(F)$ for a fundamental functor $F$ are profinite, and the
  equivalence $\mathcal{C} \simeq \mathcal{C}(\pi)$ of V.4.1 lives in the category of finite continuous $\pi$-sets;
- **Pro-objects of a category** — the fundamental functor $F$ is represented by a pro-object $P = (P_{i})$, whose
  automorphisms form $\pi$;
- **Strict epimorphism, strict monomorphism** — the words appear in axiom (G3) and pervasively in V.3, V.4, V.5;
- **Connected object in a category** — Grothendieck uses "connected" with no topological underlay; V.5.3 characterises
  connectedness via transitivity of the $\pi$-action.

We collect these here in working order, so that files 30–33 can quote without redeveloping. File 28 supplied the
topological geometric picture; this file supplies the algebraic toolkit.

## Profinite groups

A **profinite group** is a topological group $\Pi$ that is

- **Hausdorff**,
- **compact**,
- **totally disconnected** (the only connected components are single points).

Equivalently: a topological group isomorphic, as a topological group, to a projective limit of finite (discrete) groups,

```text
Π  ≅  lim_{i ∈ I} G_i,
```

over a filtered ordered set $I$ with finite groups $G_{i}$ and group homomorphisms $G_{j} \to G_{i}$ for every
$i \leq j$. Both descriptions are equivalent (the implication "compact + Hausdorff + totally disconnected ⟹ projective
limit of finite" uses Stone duality applied to clopen subsets).

### Examples

- $\hat{\mathbb{Z}}  =  \lim_{n} \mathbb{Z} / n\mathbb{Z}$. Concretely, `Ẑ` is the set of compatible systems
  $(a_{n} mod n)_{n \geq 1}$, a topological ring under componentwise operations. Contains $\mathbb{Z}$ densely. By the
  Chinese remainder theorem, $\hat{\mathbb{Z}}  \cong  \prod_{p} \mathbb{Z}_{p}$, the product over primes of the
  $p$-adic integers.
- $\mathbb{Z}_{p}  =  \lim_{n} \mathbb{Z} / p^{n}\mathbb{Z}$. The $p$-adic integers, a compact Hausdorff totally
  disconnected topological ring. Contains $\mathbb{Z}$ densely.
- $\operatorname{Gal}(K^{sep} / K)$ for any field $K$. A profinite group with the Krull topology: open subgroups are
  exactly $\operatorname{Gal}(K^{sep} / L)$ for $L / K$ finite separable. Generalises both $\hat{\mathbb{Z}}$ (take
  $K = \mathbb{F}_{p}$) and the absolute Galois groups of number fields.
- $\hat{F}_{n}$, the **free profinite group on $n$ generators**: the profinite completion of the free group $F_{n}$ on
  $n$ letters. For $n \geq 2$, $\hat{F}_{n}$ is uncountable, non-abelian, and somewhat mysterious.
- Any finite group, viewed as a profinite group with the discrete topology.

### The topology

Open subgroups of a profinite group $\Pi$ are exactly the preimages of subgroups of finite quotients in the projective
system. They form a **fundamental system of neighborhoods of the identity**: every neighborhood of $1 \in \Pi$ contains
some open subgroup. Open subgroups are automatically of finite index, but not every finite-index subgroup is open.
(Counter-example: abstractly, $\hat{\mathbb{Z}}$ has uncountably many subgroups of finite index; only countably many are
open.)

A **closed subgroup** of a profinite group is the intersection of the open subgroups containing it. Two consequences:

- A closed subgroup $H \subseteq \Pi$ is itself profinite (with the subspace topology).
- For two closed subgroups $M, N \subseteq \Pi$, $M \subseteq N$ iff every open subgroup containing $N$ contains $M$.
  (This is the technical fact V.6.4 and V.6.6 lean on.)

The intersection of any family of closed subgroups is closed. Among closed subgroups, the **closed normal subgroups**
are those preserved by the conjugation action of $\Pi$ — equivalently, those that are kernels of continuous
homomorphisms to other profinite groups.

### Continuous actions on finite sets

A **continuous action** of a profinite group $\Pi$ on a discrete finite set $E$ is a homomorphism
$\rho : \Pi \to Sym(E)$ that is continuous when $Sym(E)$ carries the discrete topology. Equivalently: the stabiliser
$Stab_{\Pi}(e)$ of every $e \in E$ is an **open subgroup** of $\Pi$. Equivalently again: the action factors through a
finite discrete quotient $\Pi \to \Pi / U$ for some open invariant subgroup $U \subseteq \Pi$.

The **category $\mathcal{C}(\Pi)$** has as objects the finite discrete sets on which $\Pi$ acts continuously on the
left, and as morphisms the $\Pi$-equivariant maps. This category appears in V.4 as the target of the equivalence
$\mathcal{C} \simeq \mathcal{C}(\pi)$.

### The profinite completion

Let $G$ be an abstract group. The **profinite completion** of $G$ is

```text
Ĝ  :=  lim_{N ⊲ G, [G : N] < ∞}  G / N,
```

the projective limit over all finite-index normal subgroups. By construction `Ĝ` is profinite, and there is a canonical
homomorphism $G \to \hat{G}$ whose image is dense.

The **universal property** of `Ĝ`: for any profinite group $\Pi$,

```text
Hom_{groups}(G, Π)  =  Hom_{cts. groups}(Ĝ, Π)
```

(continuous homomorphisms on the right). In particular, every continuous action of $G$ on a finite set extends uniquely
to a continuous action of `Ĝ`.

### Examples of profinite completion

- $\hat{\mathbb{Z}}$, the profinite completion of $\mathbb{Z}$. Used pervasively as the Galois group
  $\operatorname{Gal}(\bar{\mathbb{F}}_{p} / \mathbb{F}_{p})$ and as $\hat{\pi}^{top}_{1}(S^{1})$.
- $\mathbb{Z}_{p}$, the profinite completion of $\mathbb{Z}$ along the powers of $p$. Equivalently the $p$-adic part of
  $\hat{\mathbb{Z}}$ under the decomposition $\hat{\mathbb{Z}} = \prod_{p} \mathbb{Z}_{p}$.
- $\hat{F}_{n}$, the profinite completion of $F_{n}$.

#### Aside (number fields).

_Skip if you do not yet care about arithmetic._ The absolute Galois group
$\operatorname{Gal}(\bar{\mathbb{Q}} / \mathbb{Q})$ is _not_ the profinite completion of any abstract group. It is
profinite, but its structure as a projective limit of finite groups carries arithmetic information that no abstract
group can supply. This is why the étale fundamental group
$\pi^{\acute{e}}_{1}t(\operatorname{Spec} \mathbb{Z}[1/N], \bar{\eta})$ (= a quotient of
$\operatorname{Gal}(\bar{\mathbb{Q}} / \mathbb{Q})$) is a nontrivial object of arithmetic geometry.

## Pro-objects of a category

Let $\mathcal{C}$ be a category. A **pro-object** of $\mathcal{C}$ is a projective system $(P_{i})_{i \in I}$ indexed by
a filtered ordered set $I$, with transition morphisms $\phi_{ji} : P_{i} \to P_{j}$ for every $i \geq j$ satisfying
$\phi_{kj} \circ \phi_{ji} = \phi_{ki}$.

Pro-objects form a category $Pro-\mathcal{C}$ whose morphisms are

```text
Hom_{Pro-𝒞}(P, Q)  :=  lim_j  colim_i  Hom_𝒞(P_i, Q_j)
```

for $P = (P_{i})_{i \in I}$ and $Q = (Q_{j})_{j \in J}$. The category $\mathcal{C}$ embeds fully faithfully into
$Pro-\mathcal{C}$ by $X \mapsto (X)_{i \in {*}}$, the constant pro-object on the one-element index set. Dually,
$Ind-\mathcal{C}$ is the category of **filtered colimits** of objects of $\mathcal{C}$, with `Hom`-formula

```text
Hom_{Ind-𝒞}(P, Q)  :=  lim_i  colim_j  Hom_𝒞(P_i, Q_j).
```

A **pro-object represents a functor** $F : \mathcal{C} \to Set$ when there is a functorial isomorphism

```text
F(X)  ≅  Hom_{Pro-𝒞}(P, X)  =  colim_i  Hom_𝒞(P_i, X).
```

We then say $F$ is **pro-representable**.

### Strict pro-representability

A set-valued functor $F : \mathcal{C} \to Set$ is **strictly pro- representable** when it admits a representing
pro-object as above _and_ the index $I$ may be chosen so that all transition morphisms $\phi_{ji} : P_{i} \to P_{j}$ for
$i \geq j$ are _epimorphisms_, and so that every epimorphism $P_{i} \to P'$ (in $\mathcal{C}$) is equivalent to one of
the $\phi_{ji}$. The pro-object is then determined up to unique isomorphism, and we say it is in **normal form**.

The fundamental fact, due to Grothendieck (Bourbaki seminar 195, Feb 1960):

**Theorem (strict pro-representability).** Let $\mathcal{C}$ be a category in which every object is **artinian** (every
descending chain of subobjects is eventually constant), and let $F : \mathcal{C} \to Set$ be a left-exact functor (i.e.
$F$ carries finite limits to finite limits) with finite values. Then $F$ is strictly pro-representable.

This is the **black box** [`bourbaki-sem-195`](appendix-black-boxes.md) that file 31's walk-through of V.4.1 will quote.
A Galois category (defined in V.5.1; see file 32) is in particular artinian (V.4 step b), and a fundamental functor $F$
is left- exact (axiom (G4)) and finite-set-valued, so the theorem applies. (Equivalently called a **fibre functor**;
"fundamental functor" is the term Grothendieck uses in Exposé V, "fibre functor" is the modern name, and the two are
synonymous — we use both.) The pro-object that emerges is the **fundamental pro-object** `P_F`, whose automorphism group
is the **fundamental group** $\pi = \operatorname{Aut}(F)$.

### Why pro-objects, not just objects

$\mathcal{C}$ itself may have no terminal object whose hom-functor is $F$. Consider $\mathcal{C} = \mathcal{C}(\pi)$ for
a profinite group $\pi$, and $F = forget$ to finite sets. The "object that represents $F$" would have to be $\pi$ itself
with its left-multiplication action — a continuous, totally disconnected, _infinite_ $\pi$-set, not an object of
$\mathcal{C}$ (which contains only finite sets). The remedy: present $\pi$ as a projective limit of its finite discrete
quotients $\pi / U$ for open invariant subgroups $U \subset \pi$, each of which _is_ an object of $\mathcal{C}$. The
system $(\pi / U)_{U}$ is the pro-object representing $F$, and $\operatorname{Aut}(P) = \pi$ recovers the original
group.

We cash this in at file 31 V.4 step (a). The étale fundamental group is generally infinite, while the category of finite
étale coverings has only finite objects. The universal cover therefore cannot live in that category; it lives as a
pro-object — a compatible system of finite covers — and the fundamental group is recovered as its automorphism group.

## Strict epimorphisms and strict monomorphisms

Let $u : X \to Y$ be a morphism in a category $\mathcal{C}$ admitting fibre products. We say $u$ is a **strict
epimorphism** when the fibre product $X \times_{u},Y,u X$ exists and the diagram

```text
X ×_Y X  ⇉  X  →  Y
```

is a coequaliser: for every $Z \in \mathcal{C}$ and every $\psi : X \to Z$ with $\psi \circ p_{1} = \psi \circ p_{2}$
(where $p_{1}, p_{2} : X \times_{Y} X \to X$ are the two projections), there exists a _unique_ $\tilde{\psi} : Y \to Z$
with $\tilde{\psi} \circ u = \psi$.

Dually, $u : X \to Y$ is a **strict monomorphism** when the push-out $X \amalg_{u} Y \amalg_{u} X$ exists and the dual
diagram is an equaliser.

In `Set` (and in many concrete categories), every epimorphism is a strict epimorphism and every monomorphism is a strict
monomorphism. The distinction matters in categories where this fails — for instance, in topological spaces `Top`, a
morphism that is set-theoretically surjective need not be a quotient map, and only the quotient maps are strict
epimorphisms.

For the Galois-category axiomatic theory (file 31), the relevant fact is V.3.5–V.3.6: every morphism of finite étale
coverings of a connected locally noetherian base factors as a strict epimorphism (the surjective étale piece) followed
by a strict monomorphism (the inclusion of an open-and-closed subset). This verifies axiom (G3) for the étale-cover
category.

#### Aside (Lenstra's simplification).

_Skip if you have not seen Lenstra._ Lenstra's _Galois Theory for Schemes_ (Ch. 3) presents the axioms with
"epimorphism" in place of Grothendieck's "strict epimorphism". The two axiom systems are equivalent for the Galois
categories that arise in practice — Grothendieck's "strict" qualifier is needed only to handle a category-theoretic
subtlety in the proof of V.4.1 step c. Our walk-through uses Grothendieck's wording because it matches the source
labels.

## Connected objects in a category

Let $\mathcal{C}$ be a category with finite coproducts and an initial object $\emptyset_{\mathcal{C}}$. An object
$X \in \mathcal{C}$ is **connected** when

- `X ≄ ∅_𝒞` (i.e. $X$ is not initial), and
- for every isomorphism $X \cong A \amalg B$ with $A, B \in \mathcal{C}$, either $A \cong \emptyset_{\mathcal{C}}$ or
  $B \cong \emptyset_{\mathcal{C}}$.

In `Set`: the connected objects are the singletons. ($\emptyset_{\mathcal{C}}$ is excluded by the first clause.)

In $\mathcal{C}(\pi)$ for a profinite group $\pi$: the connected objects are the finite sets on which $\pi$ acts
_transitively_. (V.5.3 will phrase this via the fundamental functor.)

In the category of topological spaces: connected objects in this categorical sense agree with topologically-connected
non-empty spaces.

### Connectedness and the fundamental functor

A central fact, used throughout V.5: in a Galois category $\mathcal{C}$ with fundamental functor $F$, an object
$X \in \mathcal{C}$ is connected if and only if $F(X)$ is **transitive** under the canonical action of
$\pi = \operatorname{Aut}(F)$. (This is V.5.3.) The two conditions match because:

- $X$ connected as a categorical object ⟹ $F(X)$ does not split as a disjoint union of two non-empty $\pi$-stable
  subsets ⟹ $\pi$ acts transitively;
- $F(X)$ transitive ⟹ any decomposition $X = A \amalg B$ would force $F(A) = \emptyset$ or $F(B) = \emptyset$ (since
  $\pi$ cannot act transitively on a disjoint union), and hence $A = \emptyset_{\mathcal{C}}$ or
  $B = \emptyset_{\mathcal{C}}$ by the conservativity of $F$ (axiom (G6)).

### Examples

- $\mathcal{C}(\hat{\mathbb{Z}})$: the connected objects are the cosets $\hat{\mathbb{Z}} / n\hat{\mathbb{Z}}$ for
  $n \geq 1$, equivalently the finite cyclic $\hat{\mathbb{Z}}$-sets $\mathbb{Z} / n\mathbb{Z}$ with $\hat{\mathbb{Z}}$
  acting through its quotient $\mathbb{Z} / n\mathbb{Z}$. Each such is one orbit.
- $\mathcal{C}(\hat{F}_{2})$: the connected objects are finite sets on which $\hat{F}_{2}$ acts transitively. There are
  infinitely many up to iso for each given cardinality.
- The category of finite étale coverings of $\operatorname{Spec} \mathbb{F}_{p}$: connected objects are
  $\operatorname{Spec} \mathbb{F}_{p^{n}}$ for $n \geq 1$, matching $\mathcal{C}(\hat{\mathbb{Z}})$ under the
  equivalence $\pi_{1}(\operatorname{Spec} \mathbb{F}_{p}, \bar{a}) = \hat{\mathbb{Z}}$ of file 33.

## What this prepares

File 30 (= V.1, V.2) uses pro-objects implicitly in handling the orbits of a finite-group action and the fundamental
groupoid of points over a fixed base. File 31 (= V.3, V.4) verifies the strict-epimorphism axiom (G3) for finite étale
covers (V.3.5), and the pro-object $P$ representing $F$ is built by quoting
[`bourbaki-sem-195`](appendix-black-boxes.md) in V.4 step c. File 32 (= V.5, V.6) develops the formalism: the
closed-subgroup ↔ open-subgroup duality of profinite groups (and continuous actions on finite sets) drives V.5.5, V.6.4,
V.6.6 verbatim. File 33 (= V.7) yields $\pi_{1}(S, a)$ as a profinite group whose continuous action on $F_{a}(X)$ for
$X / S$ étale is the engine of the equivalence $\mathcal{C}(S) \simeq \mathcal{C}(\pi_{1}(S, a))$.
