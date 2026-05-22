# Exposé V §§5–6 (gentle): Galois categories and exact functors

<!-- source: V.5 -->

## What this file is about

Read symmetries off a geometric object by picking a vantage point — a basepoint, a fibre, some choice of where to stand.
The symmetry group falls out. A different vantage point gives a different group. That is uncomfortable. A geometric
object should not have its symmetries depend on which observer looked first. The right question is whether the choices
are linked, and how tightly.

They are linked tightly. Any two vantage points give groups that are canonically isomorphic, up to a controlled inner
ambiguity. Bundle every vantage point as an object and every passage between them as an arrow, and the bundle carries
one well-defined symmetry structure attached intrinsically, no choice required. The same packaging makes comparison
work. A structure-preserving map from one Galois category to another translates, once vantage points are fixed on both
sides, into a continuous homomorphism between the attached groups. This is exactly the machinery later files need to
turn a geometric map between schemes into a homomorphism between their fundamental groups.

## Opening: from one fibre functor to the formalism

V.4.1 produced an equivalence $\mathcal{C} \simeq \mathcal{C}(\pi)$ once a fibre functor $F$ was _fixed_. The two
sections of Exposé V we cover here ask: what is intrinsic to the Galois category, _independent_ of the choice of $F$?

§V.5 develops the answer. Different fundamental functors give isomorphic profinite groups, so they package into a
connected groupoid $\Gamma$ — the **fundamental groupoid** — whose objects are fibre functors and whose morphisms are
isomorphisms between them. Each object has automorphism group $\pi_{F} = \operatorname{Aut}(F)$. The "local system of
fundamental groups" is $\Pi$, the **fundamental pro-group**, whose fibre at $F$ is $\pi_{F}$.

§V.6 develops the **functoriality**: an exact functor $H : \mathcal{C} \to \mathcal{C}'$ of Galois categories
corresponds (after fixing fibre functors) to a _continuous_ homomorphism $u : \pi_{F'} \to \pi_{F}$, where
$F = F' \circ H$. The dictionary continues: $u$ is trivial, injective, surjective, etc., iff $H$ has corresponding
properties on objects of $\mathcal{C}$.

The two sections together say: the 2-category of Galois categories with fibre functors is anti-equivalent to the
2-category of profinite groups with continuous homomorphisms. Continuous group homomorphisms in / continuous group
homomorphisms out — this is what file 33 will need to translate geometric morphisms $f : S' \to S$ into homomorphisms
$\pi_{1}(f) : \pi_{1}(S', a') \to \pi_{1}(S, a)$.

## §V.5 Galois categories

### V.5.1 — Definition of Galois category

<!-- source: V.5.1 -->

_This definition says: a Galois category is a category equivalent to $\mathcal{C}(\pi)$ for some profinite group $\pi$.
Equivalently (by V.4.1), a category satisfying axioms (G1)–(G3) and admitting a fibre functor $F$ satisfying (G4)–(G6)._

**Definition.** A **Galois category** is a category $\mathcal{C}$ equivalent to a category $\mathcal{C}(\pi)$ for some
compact totally disconnected (i.e. profinite) topological group $\pi$. By V.4.1, this is equivalent to: $\mathcal{C}$
satisfies (G1)–(G3), and there exists a covariant functor $F : \mathcal{C} \to FSet$ satisfying (G4)–(G6).

Such a functor is called a **fundamental functor** of $\mathcal{C}$, or equivalently a **fibre functor**; the two names
are synonymous and we use both throughout files 32–33 (see file 29).[^v-5-1-1] It is pro-representable (V.4.1) by a
pro-object `P_F`, called a **fundamental pro-object** of $\mathcal{C}$.

The category of fibre functors of $\mathcal{C}$ is anti-equivalent to the category of fundamental pro-objects
($F \leftrightarrow P_{F}$). For corresponding $F$ and $P$, $\operatorname{Aut}(F)$ is canonically isomorphic to the
opposite of $\operatorname{Aut}(P)$; the group denoted $\pi$ in V.4.1 is none other than $\operatorname{Aut}(F)$. In the
typical case $\mathcal{C} = \mathcal{C}(\pi)$ with $F =$ forget, the fundamental pro-object is the projective system of
finite discrete quotients$(\pi / U)_{U}$(over open invariant subgroups$U \subset \pi$).

### V.5.2 — Pro-objects of $\mathcal{C}(\pi)$

<!-- source: V.5.2 -->

_This proposition says: pro-objects of $\mathcal{C}(\pi)$ are exactly the compact totally disconnected $\pi$-spaces._

**Proposition.** The category $Pro-\mathcal{C}(\pi)$ is canonically equivalent to the category $\mathcal{C}'(\pi)$ of
compact totally disconnected topological spaces with continuous left $\pi$-action.

**Proof sketch.** The functor $g : Pro-\mathcal{C}(\pi) \to \mathcal{C}'(\pi)$ sends a projective system $Q = (Q_{i})$
to its limit $\lim_{i} Q_{i} \in \mathcal{C}'(\pi)$. The functor in the opposite direction
$h : \mathcal{C}'(\pi) \to Pro-\mathcal{C}(\pi)$ is defined by $h(X)(E) = \operatorname{Hom}_{\mathcal{C}'(\pi)}(X, E)$
for $X \in \mathcal{C}'(\pi)$ and $E \in \mathcal{C}(\pi)$. One checks $g$ and $h$ are quasi-inverse: `hg` is
canonically the identity, and every $X \in \mathcal{C}'(\pi)$ is the projective limit of its finite discrete
$\pi$-stable quotients (by compactness and total disconnectedness of $X$, plus the profinite-group continuity argument).

**Note.** The dual statement also holds: $Ind-\mathcal{C}(\pi)$ is equivalent to the category of (possibly infinite)
sets on which $\pi$ acts continuously. We will not need this.

### V.5.3 — Connectedness via the fibre functor

<!-- source: V.5.3 -->

_This proposition says: an object $X \in \mathcal{C}$ is connected (in the categorical sense of file 29) iff $\pi$ acts
transitively on $F(X)$._

**Proposition.** Let $\mathcal{C}$ be a Galois category, $F$ a fibre functor, $P = (P_{i})$ the associated pro-object.
Let $X \in \mathcal{C}$. Then $X$ is **connected** iff $\pi = \operatorname{Aut}(F)$ acts **transitively** on
$E = F(X)$.

**Proof.** Reduce to the typical case $\mathcal{C} = \mathcal{C}(\pi)$, $F =$ forget, where the statement is the trivial
"a finite$\pi$-set is connected iff$\pi$ is transitive on it".

### V.5.4 — Connected objects ↔ Galois $P_{i}$

<!-- source: V.5.4 -->

_This corollary says: the conditions "$X$ is connected and non-initial" / "$\pi$ is transitive on $F(X) \neq \emptyset$"
/ "$X \cong P_{i}$ for some $i$" are equivalent. In short: connected objects of $\mathcal{C}$ are exactly the Galois
objects of the fundamental pro-system._

**Corollary.** For $X \in \mathcal{C}$, the following are equivalent:

1. $X$ is connected and `X ≄ ∅_𝒞`.
1. $\pi$ is transitive on $E = F(X)$ and $F(X) \neq \emptyset$.
1. $X \cong P_{i}$ for some $i \in I$.

The equivalence (1) ⟺ (3) was already in V.4 step (e).

### V.5.5 — When does a pro-object correspond to a closed subgroup?

<!-- source: V.5.5 -->

_This proposition says: a pro-object $Q = (Q_{i})$ of $\mathcal{C}$ whose associated functor
$G(X) = \operatorname{Hom}(Q, X)$ commutes with finite sums is exactly $Q \cong \pi / H$ for a closed subgroup
$H \subseteq \pi$._

**Proposition.** Let $Q = (Q_{i})_{i \in I}$ be a normalised pro-object of $\mathcal{C}$, and let
`G(X) := Hom(Q, X) = colim_i Hom(Q_i, X)` be the associated functor $\mathcal{C} \to Set$. The following are equivalent:

1. $G$ commutes with finite direct sums.
1. $G$ commutes with the sum of two objects.
1. The $Q_{i}$ are connected and `Q_i ≄ ∅_𝒞`.
1. $Q \cong \pi / H$ (after fixing a fibre functor and identifying $\mathcal{C} = \mathcal{C}(\pi)$), where $H$ is a
   closed subgroup of $\pi$.
1. The functor $G$ is isomorphic to $E \mapsto E^{H}$ ($H$-invariants), for a closed subgroup $H \subset \pi$.

**Proof sketch.** (1) ⟹ (2) trivial; (2) ⟹ (3) is V.4 step (d) applied to $Q$ instead of $P$. (3) ⟹ (4):
$\lim_{i} Q_{i}$ is non- empty (projective limit of non-empty finite sets); pick $a \in \lim_{i} Q_{i}$. The orbit map
$\pi \to Q$, $g \mapsto g \cdot a$, is continuous and surjective (by V.5.3 applied at each level), giving
$\pi / H \simeq Q$ for $H$ the stabiliser. (4) ⟹ (5) and (5) ⟹ (1) are formal.

### V.5.6 — Recognising fundamental pro-objects

<!-- source: V.5.6 -->

_This proposition says: a pro-object $P' = (P'_{i})$ of $\mathcal{C}$ is fundamental iff $P' \cong P$ (the chosen
fundamental pro-object) iff its associated functor $F'$ commutes with sums-of-two and sends non-initial objects to
non-empty sets._

**Proposition.** Let $\mathcal{C}$ be a Galois category, $P$ a fundamental pro-object, $F$ the associated fibre functor.
Let $P' = (P'_{i})$ be a pro-object of $\mathcal{C}$ (in normal form), and $F' =$ associated functor. The following are
equivalent:

1. $P' \cong P$ (equivalently $F' \cong F$).
1. $P'$ is **fundamental** (equivalently $F'$ is fundamental).
1. $F'$ carries $A \amalg B$ to $F'(A) \amalg F'(B)$ (and sends $\emptyset_{\mathcal{C}} \to \emptyset$), and `X ≄ ∅_𝒞`
   ⟹ $F'(X) \neq \emptyset$.
1. The connected non-initial objects of $\mathcal{C}$ are exactly the $P'_{i}$.

**Proof.** (1) ⟹ (3) and (1) ⟹ (2) are trivial; (2) ⟹ (4) is V.5.4 applied to $P'$. Either (3) or (4) implies, by V.5.5,
that $P' \cong \pi / H$ for some closed $H \subset \pi$. Under (3), every finite quotient of $\pi$ admits a
$\pi$-homomorphism $\pi / H \to \pi / U$, forcing $H \subseteq U$. Taking the intersection over all open invariant $U$,
$H = {1}$, hence $P' \cong \pi = P$.

### V.5.7 — The fundamental groupoid

<!-- source: V.5.7 -->

_This corollary says: the fundamental functors of $\mathcal{C}$ form a **connected groupoid** $\Gamma$ — every two are
isomorphic, and the isomorphism is canonical up to inner automorphism by the relevant $\pi_{F}$. Following the topology
analogy, "objects of $\Gamma$" play the role of "base points"._

**Corollary.** Let $\mathcal{C}$ be a Galois category. The fundamental pro-objects (resp. fundamental functors) of
$\mathcal{C}$ are pairwise isomorphic. The category of fundamental functors is therefore a **connected groupoid**
$\Gamma$, called the **fundamental groupoid** of $\mathcal{C}$. The category of fundamental pro-objects is equivalent to
the _opposite_ of $\Gamma$.

If $\mathcal{C} = \mathcal{C}(\pi)$, the automorphism group of any object of $\Gamma$ is canonically isomorphic to
$\pi$, the isomorphism being well- determined up to inner automorphism. For $F$, $F' \in \Gamma$, the set

```text
π_{F′, F}  :=  Hom(F, F′)  =  Isom(F, F′)
```

is the **set of path classes from $F$ to $F'$**. In particular, $\pi_{F, F} = \pi_{F}$ is the **fundamental group of
$\mathcal{C}$ at $F$** (constructed in V.4). The fundamental pro-object $P$ associated with $F$ plays the role of a
**universal covering of the final object $e_{\mathcal{C}}$ at $F$**.

### V.5.8 — Description via local systems on $\Gamma$

<!-- source: V.5.8 -->

_This proposition says: $\mathcal{C}$ is equivalent to the category of covariant functors $\Gamma \to Set$ ("local
systems on $\Gamma$") satisfying the continuity condition that, for every $F \in \Gamma$, the value at $F$ is a finite
set on which $\pi_{F}$ acts continuously._

**Proposition.** The functor $X \mapsto E_{X}$, where $E_{X}(F) := F(X)$, is an equivalence of $\mathcal{C}$ with the
category of covariant functors $\Gamma \to Set$ satisfying:

```text
For every F ∈ Γ, E_X(F) is a finite set on which π_F acts continuously.
```

**Proof.** Pick a base point $F_{0} \in \Gamma$, set $\pi_{0} = \operatorname{Aut}(F_{0})$. The functor
$\xi \mapsto \xi(F_{0})$ from the second category to $\mathcal{C}(\pi_{0})$ is an equivalence. Composed with
$X \mapsto E_{X}$ and the natural equivalence $\mathcal{C} \to \mathcal{C}(\pi_{0})$ from V.4.1, this confirms
$X \mapsto E_{X}$ is an equivalence.

This is the **local-system** description of $\mathcal{C}$: an object of $\mathcal{C}$ is a (representable)
finite-set-valued local system on the fundamental groupoid $\Gamma$.

### V.5.9 — Pro-$\mathcal{C}$ description

<!-- source: V.5.9 -->

_This corollary says: the analogue for $Pro-\mathcal{C}$. A pro-object of $\mathcal{C}$ is a covariant functor
$\xi : \Gamma \to Top$ such that, for every $F \in \Gamma$, $\xi(F)$ is a compact totally disconnected space with
continuous $\pi_{F}$-action._

**Corollary.** The category $Pro-\mathcal{C}$ is canonically equivalent to the category of covariant functors
$\xi : \Gamma \to Top$ satisfying: for every $F \in \Gamma$, $\xi(F)$ is a compact totally disconnected topological
space with continuous $\pi_{F}$-action.

The proof is the same as V.5.8.

### V.5.10 — The fundamental pro-group $\Pi$

<!-- source: V.5.10 -->

_This remark says: the canonical pro-object whose fibre at any $F \in \Gamma$ is $\pi_{F}$ is itself a pro-**group**
$\Pi$ of $\mathcal{C}$ — the **fundamental pro-group**, the algebraic version of "local system of fundamental groups".
$\Pi$ is determined up to unique isomorphism (unlike a fundamental pro-object $P$, which is determined only up to
non-canonical isomorphism)._

**Remark.** Use V.5.9 to define a canonical pro-object as the functor $f : \Gamma \to Top$ with
$f(F) := \pi_{F} = \operatorname{Aut}(F)$. Each $\pi_{F}$ is a profinite group (a fortiori a compact totally
disconnected topological space) with continuous $\pi_{F}$-action by inner automorphisms; the functoriality in $F$ is
automatic. The corresponding pro-object is itself a **pro-group** $\Pi$ of $\mathcal{C}$, called the **fundamental
pro-group of $\mathcal{C}$**, defined by

```text
F(Π)  ≃  π_F    (functorially in F).
```

For any pro-object $X$ of $\mathcal{C}$, there is a canonical morphism $\Pi \times X \to X$ making $X$ an object with
left $\Pi$-action in $Pro-\mathcal{C}$. (Define it pointwise: $\pi_{F} \times F(X) \to F(X)$ is the natural action.)

### V.5.11 — $\Pi$ versus $P$

<!-- source: V.5.11 -->

_This remark says: the fundamental pro-object $P$ and the fundamental pro-group $\Pi$ are different things. $P$ is
connected and not a group; $\Pi$ is a pro-group and in general not connected. $P$ is determined up to non-canonical
isomorphism (every two are isomorphic, but not canonically); $\Pi$ is determined up to unique isomorphism._

**Remark.** Do not confuse:

- A fundamental pro-object $P$ ∈ Pro-$\mathcal{C}$. Connected; carries no natural group structure; determined up to
  (non-canonical) isomorphism.
- The fundamental pro-group $\Pi$ ∈ Pro-$\mathcal{C}$. A pro-**group**; in general not connected. Determined up to
  _unique_ isomorphism. $\Pi$ is connected iff $\pi_{F}$ (acting on itself by inner automorphism) is transitive iff
  $\pi_{F} = {1}$ iff $\mathcal{C}$ is equivalent to FSet.

In topology terms: $P$ is the universal cover (a single space with no chosen base-point isomorphism between any two),
and $\Pi$ is the "local system of fundamental groups" (a canonically-defined pro-object encoding the group at every
point). The corresponding **principal-homogeneous** language: $X$ is **principal homogeneous under $G$** in
$\mathcal{C}$ when, after fixing a fibre functor, $F(X)$ is principal homogeneous under $G$ (i.e. $G$ acts simply
transitively); **formally principal homogeneous** when $F(X)$ is empty or principal homogeneous.

If a fibre functor $F$ is fixed, the data of an $X \in \mathcal{C}$ principal homogeneous under a finite group $G$
operating on the right, together with a chosen point $a \in F(X)$, is equivalent to a homomorphism $\pi_{F} \to G$.
(Take $E = G$ with $\pi_{F}$ acting through $\pi_{F} \to G$ and $G$ acting on $E$ by right translation; the marked point
is $e \in G$.) This is the **classifying-pointed covers** picture: principal coverings up to iso, _with chosen fibre
point_, are classified by $\operatorname{Hom}_{cts}(\pi_{F}, G)$.

## §V.6 Exact functors from one Galois category to another

<!-- source: V.6 -->

A morphism between two Galois categories is an _exact functor_. After fixing fibre functors, exact functors correspond
to continuous group homomorphisms in the opposite direction (V.6.1 –V.6.3). The remaining propositions V.6.4–V.6.13 fill
in the **dictionary**: when is the homomorphism trivial / injective / surjective / an isomorphism, in terms of
properties of the original functor on the level of objects of $\mathcal{C}$.

### V.6.1 — Three formulations of exactness

<!-- source: V.6.1 -->

_This proposition says: for $H : \mathcal{C} \to \mathcal{C}'$, "exact" / "left exact + carries sums to sums + carries
epis to epis" / "the composite $F = F' \circ H$ is again a fundamental functor on $\mathcal{C}$" are all equivalent._

**Proposition.** Let $\mathcal{C}$, $\mathcal{C}'$ be Galois categories, $H : \mathcal{C} \to \mathcal{C}'$ a covariant
functor, $F'$ a fundamental functor on $\mathcal{C}'$, and $F := F' \circ H$. The following are equivalent:

1. $H$ is **exact** (left exact and right exact).
1. $H$ is left exact, transforms finite sums into finite sums, and transforms epimorphisms into epimorphisms;
   equivalently, transforms non-initial objects into non-initial objects.
1. $F$ is a fundamental functor on $\mathcal{C}$.

**Proof.** (1) ⟹ (2) general fact about categories. (2) ⟹ (3): $F = F' \circ H$ is left exact (composition of left-exact
functors) and is finite-set-valued; the criterion V.5.6 (3) applies to verify (G5)/(G6). (3) ⟹ (1): exactness of $F$ and
conservativity of $F$ (axiom (G6)) lift back through $H$.

### V.6.2 — Continuous group homomorphisms

<!-- source: V.6.2 -->

_This corollary says: any exact functor $H : \mathcal{C} \to \mathcal{C}'$ arises (up to equivalence) from a continuous
homomorphism $u : \pi' \to \pi$ of profinite groups, via $H_{u} : \mathcal{C}(\pi) \to \mathcal{C}(\pi')$._

**Corollary.** For an exact functor $H : \mathcal{C} \to \mathcal{C}'$ of Galois categories, there exist equivalences
$\mathcal{C} \simeq \mathcal{C}(\pi)$ and $\mathcal{C}' \simeq \mathcal{C}(\pi')$ that transform $H$ into the functor
$\mathcal{C}(\pi) \to \mathcal{C}(\pi')$ associated with a continuous homomorphism $u : \pi' \to \pi$ of topological
(profinite) groups.

**Proof.** Set $F = F' \circ H$ (a fundamental functor on $\mathcal{C}$ by V.6.1). The transposed assignment
${}^{t} H : \Gamma' \to \Gamma$, $F' \mapsto F = F' \circ H$, defines, on automorphism groups,

```text
^t H : π_{F′}  ⟶  π_F,    where F = ^t H(F′).
```

For every finite continuous $\pi_{F}$-set $E$, the group $\pi_{F'}$ acts continuously on it through ${}^{t} H$, so
applied to the quotients $\pi_{F} / U$ ($U$ open invariant) we see that ${}^{t} H$ itself is continuous. Set
$u = {}^{t} H$.

### V.6.3 — Functorial form

<!-- source: V.6.3 -->

_This corollary says: the category of exact functors $\mathcal{C} \to \mathcal{C}'$ is equivalent to the category of
functors $\Gamma' \to \Gamma$ whose associated group homomorphisms (at any one point) are continuous._

**Corollary.** Let $\mathcal{C}$, $\mathcal{C}'$ be Galois categories with fundamental groupoids $\Gamma$, $\Gamma'$.
The category of exact functors $\mathcal{C} \to \mathcal{C}'$ is equivalent to the category of functors
$U : \Gamma' \to \Gamma$ such that, for every $F' \in \Gamma'$ (equivalently, for one $F' \in \Gamma'$, since
transitivity is automatic in a connected groupoid), the corresponding homomorphism

```text
π_{F′}  =  Aut(F′)  ⟶  π_F  =  Aut(F),    F = U(F′),
```

is continuous.

### Pointed objects

A **pointed object** of $(\mathcal{C}, F)$ is a pair $(X, a)$ with $X \in \mathcal{C}$ and $a \in F(X)$. Equivalently
(after the equivalence $\mathcal{C} \simeq \mathcal{C}(\pi_{F})$), a finite continuous $\pi_{F}$-set with a chosen
point. **Connected** pointed objects correspond, by V.5.3, to **open subgroups** $U \subseteq \pi_{F}$ (the stabiliser
of the marked point). For two open subgroups $U, V \subseteq \pi_{F}$ corresponding to connected pointed objects `X, Y`:
a pointed $\mathcal{C}$-morphism $X \to Y$ exists iff $U \subseteq V$, and is then unique.

The dictionary V.6.4–V.6.13 leverages this: properties of $u : \pi_{F'} \to \pi_{F}$ are read off from properties of
$H(X)$ for chosen connected pointed $X \in \mathcal{C}$.

### V.6.4 — Pointed sections and complete decomposition

<!-- source: V.6.4 -->

*This proposition says: for a connected pointed object $X$ of $\mathcal{C}$ corresponding to an open subgroup
$U \subseteq \pi_{F}$, "pointed section of $H(X)$ exists" iff $U \supseteq u(\pi_{F'})$, and "$H(X)$is completely
decomposed" iff$U$contains the closed normal subgroup generated by$u(\pi_{F'})$.*

**Proposition.** Let $X$ be a connected pointed object of $\mathcal{C}$, associated with an open subgroup
$U \subseteq \pi_{F}$. Then:

- $U \supseteq u(\pi_{F'})$ ⟺ $H(X)$ admits a **pointed section** (over the final object $e_{\mathcal{C}'}$).
- $U \supseteq \langle u(\pi_{F'}) \rangle^{normal closure}$ ⟺ $H(X)$ is **completely decomposed**, i.e. isomorphic to a
  finite disjoint sum of final objects of $\mathcal{C}'$.

A **section** of $X \in \mathcal{C}$ over the final object $e_{\mathcal{C}}$ is a morphism $e_{\mathcal{C}} \to X$,
equivalently a $\pi_{F}$-fixed point of $F(X)$. A **pointed section** when $(X, a)$ is pointed is a section sending
$e_{\mathcal{C}}$'s marked point to $a$.

### V.6.5 — Trivial $u$

<!-- source: V.6.5 -->

_This corollary says: $u$ is trivial iff every $H(X)$ is completely decomposed._

**Corollary.** $u$ is trivial iff for every $X \in \mathcal{C}$, $H(X)$ is completely decomposed in $\mathcal{C}'$.

### V.6.6 — Containing the kernel

<!-- source: V.6.6 -->

_This proposition says: for a connected pointed $X'$ of $\mathcal{C}'$ with associated open $U' \subseteq \pi_{F'}$,
"$U' \supseteq Ker u$" iff there is a pointed homomorphism from the **neutral connected component** of $H(X)$(for some
pointed$X \in \mathcal{C}$) to $X'$. If $u$is surjective, equivalently$X'$is isomorphic to$H(X)$for some pointed$X$._

**Proposition.** Let $X'$ be a connected pointed object of $\mathcal{C}'$, associated with an open subgroup
$U' \subseteq \pi_{F'}$. Then $U' \supseteq Ker u$ iff there exists a connected pointed object $X \in \mathcal{C}$ and a
pointed homomorphism

$$
H(X)_{0}  \longrightarrow  X'
$$

from the neutral connected component $H(X)_{0}$ of $H(X)$ to $X'$. Equivalently, $X'$ is isomorphic, as a pointed
object, to a quotient of $H(X)_{0}$. If furthermore $u$ is **surjective**, this is also equivalent to the statement that
$X' \cong H(X)$ for some pointed $X \in \mathcal{C}$.

The **neutral connected component** of a pointed object $X$ is the unique connected pointed sub-object of $X$; under
$\mathcal{C} \simeq \mathcal{C}(\pi_{F})$ it is the orbit of the marked point in $F(X)$ (V.5.3).

### V.6.7 — Containing the kernel, unpointed form

<!-- source: V.6.7 -->

_This corollary says: the V.6.6 condition is equivalent (after forgetting the pointed structure) to "there is a morphism
from a connected component of $H(X)$ to $X'$ for some $X$ in $\mathcal{C}$"._

**Corollary.** $U' \supseteq Ker u$ iff there exists $X \in \mathcal{C}$ (which may be assumed connected) and a morphism
from a connected component of $H(X)$ to $X'$. If $u$ is surjective, also iff $X' \cong H(X)$ for some
$X \in \mathcal{C}$.

### V.6.8 — Injectivity of $u$

<!-- source: V.6.8 -->

_This corollary says: $u$ is injective iff for every $X' \in \mathcal{C}'$ there exist $X \in \mathcal{C}$ and a
morphism from a connected component of $H(X)$ to $X'$._

**Corollary.** $u : \pi_{F'} \to \pi_{F}$ is injective iff for every $X' \in \mathcal{C}'$, there exist
$X \in \mathcal{C}$ and a morphism from a connected component of $H(X)$ to $X'$.

### V.6.9 — Surjectivity of $u$ ⟺ $H$ fully faithful

<!-- source: V.6.9 -->

_This proposition says: three equivalent forms of "$u$ is surjective" — including "$H$ is fully faithful"._

**Proposition.** The following are equivalent:

1. $u : \pi_{F'} \to \pi_{F}$ is **surjective**.

1. For every connected $X \in \mathcal{C}$, $H(X)$ is connected in $\mathcal{C}'$.

1. $H : \mathcal{C} \to \mathcal{C}'$ is **fully faithful**, i.e.

    ```text
    Hom_𝒞(X, Y)  ⟶  Hom_{𝒞′}(H(X), H(Y))
    ```

    is bijective for every $X, Y \in \mathcal{C}$.

**Proof.** Combine V.6.6 (with $u$ surjective) and V.5.4 to match (1) ⟺ (2). For (1) ⟺ (3), the equivalence is
straightforward from the $\pi_{F}$ ↔ $\pi_{F'}$-set translation.

### V.6.10 — Isomorphism of $u$ ⟺ equivalence

<!-- source: V.6.10 -->

_This corollary says: $u$ is an isomorphism iff $H$ is an equivalence iff "(1) $H$ carries connected to connected and
(2) every object of $\mathcal{C}'$ is in the essential image of $H$"._

**Corollary.** $u : \pi_{F'} \to \pi_{F}$ is an isomorphism iff $H : \mathcal{C} \to \mathcal{C}'$ is an **equivalence
of categories**, equivalently iff:

1. For every connected $X \in \mathcal{C}$, $H(X)$ is connected.
1. Every object of $\mathcal{C}'$ is isomorphic to one of the form $H(X)$ for some $X \in \mathcal{C}$.

### V.6.11 — Composability conditions

<!-- source: V.6.11 -->

_This proposition says: for a composable pair $H : \mathcal{C} \to \mathcal{C}'$, $H' : \mathcal{C}' \to \mathcal{C}''$
with associated $u, u'$, the inclusion $Ker u \subseteq Im u'$ (resp. $\supseteq$) translates into specific
decomposition / covering properties of $H' \circ H$ (resp. $H, H'$ separately)._

**Proposition.** Let $H : \mathcal{C} \to \mathcal{C}'$ and $H' : \mathcal{C}' \to \mathcal{C}''$ be exact functors of
Galois categories, let $F''$ be a fibre functor on $\mathcal{C}''$, set $F' = F'' \circ H'$, $F = F' \circ H$, and
consider the homomorphisms

```text
u′ : π_{F″} → π_{F′},     u : π_{F′} → π_F.
```

Then:

- $Ker u \subseteq Im u'$ (i.e. $u u'$ trivial) ⟺ for every $X \in \mathcal{C}$, $H'(H(X))$ is completely decomposed.
- $Ker u \supseteq Im u'$ ⟺ for every connected pointed $X' \in \mathcal{C}'$ such that $H'(X')$ admits a pointed
  section, there exist $X \in \mathcal{C}$ and a homomorphism from a connected component of $H(X)$ to $X'$.

**Proof.** First assertion follows from V.6.4 last clause. Second from V.6.4 + V.6.6.

### V.6.12 — A subtle non-equivalence

<!-- source: V.6.12 -->

_This remark says: V.6.8 ("$u$ injective ⟺ every $X'$ admits a morphism from a component of some $H(X)$") does **not**
in general imply "every $X'$ is isomorphic to an $H(X)$". The latter holds iff $u$ is an isomorphism onto a **direct
factor** subgroup of $\pi_{F}$. In practice, the concrete way to verify this is to construct a homomorphism
$\pi_{F} \to \pi_{F'}$inverse to$u$on the right, via a suitable exact functor$\mathcal{C}' \to \mathcal{C}$._

**Remark.** Under V.6.8's conditions, it is not in general true that every $X' \in \mathcal{C}'$ is isomorphic to an
$H(X)$. The condition "every connected (and hence every) $X' \in \mathcal{C}'$ is isomorphic to some $H(X)$" is
equivalent to "$u$ is an isomorphism onto a **direct factor** of $\pi_{F}$". In practice one verifies this by building a
one-sided inverse $\pi_{F} \to \pi_{F'}$ from a suitable exact functor $\mathcal{C}' \to \mathcal{C}$.

### V.6.13 — The over-$S$ Galois category

<!-- source: V.6.13 -->

*This proposition says: for a connected $S \in \mathcal{C}$, the slice category $\mathcal{C} / S$ is Galois, and the
functor $H(X) = X \times S$ from $\mathcal{C}$ to $\mathcal{C} / S$ is exact. The associated homomorphism
$u : \pi_{F'} \to \pi_{F}$is the inclusion of the open subgroup$U \subset \pi_{F}$stabilising a chosen marked
point$a \in F(S)$.*

**Proposition.** Let $\mathcal{C}$ be a Galois category with fibre functor $F$, let $S \in \mathcal{C}$ be connected,
and let $\mathcal{C}' := \mathcal{C} / S$ be the slice category of objects over $S$. Then $\mathcal{C}'$ is Galois, and
the functor

```text
H : 𝒞 ⟶ 𝒞′,    X ↦ X × S
```

is exact. Pick $a \in F(S)$ and define $F' : \mathcal{C}' \to FSet$ by

```text
F′(X′)  =  ` inverse image of `a` under `F(X′) → F(S)`.
```

Then $F \simeq F' \circ H$, and the associated homomorphism

$$
u : \pi_{F'}  \longrightarrow  \pi_{F}
$$

is an **isomorphism** of $\pi_{F'}$ onto the open subgroup $U \subseteq \pi_{F}$ stabilising $a \in F(S)$.

(Proof left to the reader, per the source.)

This is the algebraic analogue of "fundamental group of a covering space $S \to B$ is a subgroup of the fundamental
group of $B$".

## Worked example: inflation along $\hat{\mathbb{Z}} \to \mathbb{Z}_{p}$

Take $\mathcal{C} = \mathcal{C}(\hat{\mathbb{Z}})$ and $\mathcal{C}' = \mathcal{C}(\mathbb{Z}_{p})$. The canonical
projection $\hat{\mathbb{Z}} \twoheadrightarrow \mathbb{Z}_{p}$ (inflation;
$\hat{\mathbb{Z}} = \prod_{q} \mathbb{Z}_{q}$ projects to its $p$- component) defines a functor
$H : \mathcal{C}(\hat{\mathbb{Z}}) \to \mathcal{C}(\mathbb{Z}_{p})$ by restriction of action: a continuous
$\hat{\mathbb{Z}}$-set becomes a continuous $\mathbb{Z}_{p}$-set via the pullback of the action.

Wait — for $H : \mathcal{C} \to \mathcal{C}'$ we need a homomorphism $u : \pi_{F'} \to \pi_{F}$, i.e.
$u : \mathbb{Z}_{p} \to \hat{\mathbb{Z}}$. This is the _inclusion_ of $\mathbb{Z}_{p}$ into $\hat{\mathbb{Z}}$ as the
$p$-factor. The functor $H : \mathcal{C}(\hat{\mathbb{Z}}) \to \mathcal{C}(\mathbb{Z}_{p})$ is then
$E \mapsto E_{| \mathbb{Z}_{p}}$ (restriction of the $\hat{\mathbb{Z}}$-action to the sub-$\mathbb{Z}_{p}$ action via
the inclusion $\mathbb{Z}_{p} \hookrightarrow \hat{\mathbb{Z}}$).

Verify against V.6.4–V.6.10:

- $u(\mathbb{Z}_{p}) = \mathbb{Z}_{p} \subset \hat{\mathbb{Z}}$ is dense in the $p$-part but **not surjective**
  ($\hat{\mathbb{Z}}$ has many other components $\mathbb{Z}_{q}$, $q \neq p$).
- $u$ is **injective** (it's the inclusion).
- By V.6.9, $H$ is _not_ fully faithful, since $u$ is not surjective. Indeed: there are non-iso $\hat{\mathbb{Z}}$-sets
  that become iso as $\mathbb{Z}_{p}$-sets (e.g. $\mathbb{Z} / q\mathbb{Z}$ for $q \neq p$ becomes a trivial
  $\mathbb{Z}_{p}$-set, isomorphic to a sum of $q$ copies of the point).
- By V.6.8, every $X' \in \mathcal{C}(\mathbb{Z}_{p})$ admits a morphism from a component of some $H(X)$. Concretely:
  every finite continuous $\mathbb{Z}_{p}$-set comes from a finite continuous $\hat{\mathbb{Z}}$-set (lift the action
  through the projection $\hat{\mathbb{Z}} \twoheadrightarrow \mathbb{Z}_{p}$), so every $X'$ is in the essential image
  of $H$.
- By V.6.12, the condition "every $X'$ is isomorphic to some $H(X)$" combined with $u$ injective tells us
  $u : \mathbb{Z}_{p} \hookrightarrow \hat{\mathbb{Z}}$ is an isomorphism onto a **direct factor**. This is true
  ($\hat{\mathbb{Z}} = \mathbb{Z}_{p} \times \prod_{q \neq p} \mathbb{Z}_{q}$), confirming the $\to direct factor$
  subtlety.

The arithmetic content: when the base scheme $S$ has a Galois- covering structure that splits into independent prime
parts (cf. file 33's $\operatorname{Spec} \mathbb{Z}$ arithmetic), the étale fundamental group decomposes
correspondingly.

## What this prepares

File 33 (= V.7, V.8, V.9) is the **geometric application**: take $\mathcal{C} =$ finite étale coverings of a connected
locally noetherian$S$, with fibre functor$F_{a} =$ geometric points over a chosen geometric point $a$. The axioms
(G1)–(G6) hold (file 30's V.1 sorites, file 31's V.3.1, V.3.4, V.3.5, V.3.7), so V.4.1 yields a profinite group
$\pi = \pi_{1}(S, a)$ and an equivalence $\mathcal{C} \simeq \mathcal{C}(\pi)$. The fundamental groupoid $\Gamma$ of
file 32 becomes the **groupoid of geometric points of $S$** (V.5.7 specialised); the path classes $\pi_{1}(S; a, a')$ of
V.7 are the morphisms in this groupoid; and the **functoriality** V.6.1–V.6.13 becomes the functoriality of $\pi_{1}$
under morphisms of base schemes: $f : S' \to S$ connected ⟹ exact functor $f^{*} : \mathcal{C}(S) \to \mathcal{C}(S')$ ⟹
continuous homomorphism $\pi_{1}(f; a') : \pi_{1}(S', a') \to \pi_{1}(S, a)$.

[^v-5-1-1]: Throughout files 32–33 we use _fibre functor_ and _fundamental functor_ interchangeably.
