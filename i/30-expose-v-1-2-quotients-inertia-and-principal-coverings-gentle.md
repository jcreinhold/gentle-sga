# Exposé V §§1–2 (gentle): quotients, inertia, principal coverings

<!-- source: V -->

<!-- source: V.1 -->

## What this file is about

When a finite group of symmetries acts on a space, the orbits of the action form a new space — the quotient — and the
map from the original to the quotient is, in good cases, an unbranched cover. This is the cleanest way to manufacture a
covering with a prescribed symmetry group, and over the complex numbers it is the source of nearly every example one
meets first.

This file does the algebraic version. A finite group acts on a geometric object built from rings, and the question is
when the orbit space exists at all, and when the resulting map is unbranched. The answer turns on two refinements of the
idea of an orbit's stabiliser. One records which symmetries fix a chosen point; the other records which fix the
algebraic data attached to that point. The map is unbranched exactly when the second is trivial.

## Opening: from deck transformations to inertia groups

Topological covering spaces carry a deck transformation group. A finite-sheeted Galois cover $p : E \to B$ has
$\operatorname{Aut}(E / B)$ of order equal to the degree, acting freely and transitively on each fibre. Inverting the
picture: a finite group $G$ acting freely on a "nice" total space $E$ produces a covering $E \to E / G$, with the
quotient inheriting the topology.

The algebraic analogue replaces "topological space" by "prescheme" and "free action" by "action by automorphisms with
trivial inertia". The first task is to make the quotient construction work — when does $X / G$ exist as a prescheme, and
how do its properties relate to those of $X$? §1 settles this. The construction is local-on-$Y$, requires only that
every orbit of $G$ on $X$ lie in an affine open (the **admissibility** condition V.1.7–V.1.8), and behaves well under
flat base change (V.1.9).

The second task: when is the quotient _étale_? §2 attaches to each $x \in X$ two subgroups of $G$ — the **decomposition
group** $G_{d}(x)$ (the stabiliser) and the **inertia group** $G_{i}(x)$ (the kernel of the residue-field action). The
étale case (V.2.3, V.2.4) is exactly: trivial inertia at every point. This pins down the algebraic shadow of "free
action" and the conditions under which $X \to X / G$ is an étale Galois cover.

The two sections close with **principal coverings** (V.2.6, V.2.8): the algebraic analogue of "Galois cover with deck
group $G$", characterised by four equivalent conditions (the formal-principal-homogeneous-bundle picture, the
trivialisation by faithfully flat base change, the trivialisation by an étale cover by $X$ itself, and the
inertia/quotient pair).

The covering theory of file 28 is the topological mirror to this algebraic story; the dictionary is

```text
deck transformation group         ↔   G acting on X
free action                       ↔   trivial inertia G_i(x)
covering map                      ↔   étale quotient morphism X → X/G
finite Galois cover               ↔   principal covering with group G.
```

Two pieces of terminology used throughout this file. When a group $G$ acts on a scheme $X$ and $x \in X$ is a fixed
point, the stabiliser acts on the residue field $\kappa(x)$ by ring automorphisms; this is the **residue-field action**.
The **decomposition group** $G_{d}(x) := {g \in G : g\cdot x = x}$ is the stabiliser of $x$ in $G$, and the **inertia
group** $G_{i}(x) \subset G_{d}(x)$ is the kernel of the residue-field action
$G_{d}(x) \to \operatorname{Aut}(\kappa(x))$ — the subgroup that fixes the residue field pointwise. The formal
restatement appears in §V.2.

We begin with the construction of $X / G$.

## §V.1 Prescheme with a finite group of operators; quotient prescheme

Let $X$ be a prescheme, and let $G$ be a finite group acting on $X$ by automorphisms on the right. (The right-action
convention is Grothendieck's; it makes the order of operations $(s t) \cdot x  =  t \cdot (s \cdot x)$ natural for
composition.) If $X = \operatorname{Spec}(A)$ is affine, then $G$ acts on the _left_ on the ring $A$, and the natural
object to consider is the subring of invariants

```text
A^G  =  { a ∈ A : s · a = a for all s ∈ G }.
```

For a general $Y$, we ask the universal property: a **quotient** of $X$ by $G$ is a $G$-invariant morphism $p : X \to Y$
such that, for every prescheme $Z$, the canonical map

```text
Hom(Y, Z)  ⟶  Hom(X, Z)^G,    g ↦ g ∘ p,
```

is a _bijection_ onto the set of $G$-invariant morphisms $X \to Z$. When such a $(Y, p)$ exists, it is determined up to
unique isomorphism, and we write $Y = X / G$.

### V.1.1 — $\operatorname{Spec}(A^{G})$ is the quotient

<!-- source: V.1.1 -->

_This result says: in the affine case the quotient prescheme exists and is $\operatorname{Spec}(A^{G})$; the morphism
$\operatorname{Spec}(A) \to \operatorname{Spec}(A^{G})$ is integral, surjective, has fibres equal to $G$-orbits, the
topology of the quotient is the quotient topology, and the residue-field extensions at points are quasi-Galois with
surjection from the decomposition group to the residue Galois group._

**Proposition.** Let $A$ be a ring on which the finite group $G$ acts on the left, let $B = A^{G}$, let
$X = \operatorname{Spec}(A)$, $Y = \operatorname{Spec}(B)$, and let $p : X \to Y$ be the canonical morphism (invariant
under $G$). Then:

1. $A$ is integral over $B$; equivalently, $p$ is an **integral morphism**.
1. $p$ is surjective; its fibres are the orbits of $G$ on $X$; the topology of $Y$ is the quotient of the topology of
   $X$ under the action.
1. For $x \in X$, $y = p(x)$, the residue extension $\kappa(x) / \kappa(y)$ is **quasi-Galois algebraic**, and the
   canonical map from $G_{d}(x)$ (stabiliser of $x$) to the group of $\kappa(y)$- automorphisms of $\kappa(x)$ is
   **surjective**.
1. $(Y, p)$ is a quotient prescheme of $X$ by $G$.

**Proof sketch.** For (i): every $a \in A$ satisfies the monic polynomial $\prod_{s \in G}(T - s \cdot a) \in B[T]$, so
$A$ is integral over $B$. For (ii): the surjectivity and the orbit-as-fibre description follow from going-up /
lying-over for integral extensions (Cohen–Seidenberg). For non-specialists: if $B \subset A$ is an integral ring
extension, every prime ideal of $B$ is the contraction of some prime of $A$ (lying-over), and a chain of primes in $B$
lifts to a chain of primes in $A$ (going-up). The topology assertion uses the extra fact that **integral morphisms are
closed**: an integral $p$ carries closed sets of $X$ to closed sets of $Y$ (because the image of $V(I) \subseteq X$ is
$V(I \cap B) \subseteq Y$). For (iii): both $G_{d}(x)$ and $\operatorname{Gal}(\kappa(x) / \kappa(y))$ are finite groups
acting on $\kappa(x) / \kappa(y)$; the surjectivity is a standard splitting-field argument. (See Bourbaki _Algèbre
Commutative_ V §1–§2 for full detail.) For (iv): combine (ii) and the universal property of $B = A^{G}$.

### V.1.2 — Sheaves of invariants

<!-- source: V.1.2 -->

_This result says: the structure sheaf of the quotient is the sheaf of $G$-invariants of the pushforward of the
structure sheaf of $X$._

**Corollary.** Under the conditions of V.1.1, the canonical homomorphism

$$
\mathcal{O}_{Y}  \longrightarrow  p_{*}(\mathcal{O}_{X})^{G}
$$

is an isomorphism.

**Proof.** It is enough to check on a basis of opens given by distinguished opens $D(f) \subseteq Y$ for $f \in B$. The
point is the formula

$$
(S^{-1}A)^{G}  =  S^{-1}(A^{G})
$$

valid for every multiplicatively stable $S \subseteq B$. Concretely for $S = {1, f, f^{2}, \cdots}$: the right side is
$B[1/f]$ and the left side is $(A[1/f])^{G} = A^{G}[1/f]$ because $f$ is $G$-invariant.

Beyond the affine case, we extract the _property_ that characterises a quotient morphism:

### V.1.3 — Sheaf-of-invariants criterion in general

<!-- source: V.1.3 -->

*This result says: V.1.1's conclusions hold for any $G$-invariant affine morphism $p : X \to Y$ such that the natural
map $\mathcal{O}_{Y} \to p_{*}(\mathcal{O}*X)^{G}$ is an isomorphism.*

**Proposition.** Let $X$ be a prescheme on which the finite group $G$ acts, and let $p : X \to Y$ be a $G$-invariant
**affine** morphism such that

$$
\mathcal{O}_{Y}  \longrightarrow  p_{*}(\mathcal{O}_{X})^{G}
$$

is an isomorphism. Then conclusions (i), (ii), (iii), (iv) of V.1.1 are still valid.

**Proof.** For (i)–(iii), reduce to the affine case $Y = \operatorname{Spec}(B)$, $X = \operatorname{Spec}(A)$. The
hypothesis says $B = A^{G}$, so V.1.1 applies. For (iv), use (ii) and the sheaf-of-invariants identification.

### V.1.4 — Restriction to opens

<!-- source: V.1.4 -->

_This result says: for any open $U \subseteq Y$, the preimage $p^{-1}(U) \subseteq X$ is a quotient of $U$ by $G$. The
construction is local on the base._

**Corollary.** Under the conditions of V.1.3, for every open $U \subseteq Y$, the morphism $p^{-1}(U) \to U$ induced by
$p$ makes $U$ a quotient of $p^{-1}(U) = X|_{U}$ by $G$.

**Proof.** The hypotheses transfer to $p^{-1}(U) \to U$ directly.

### V.1.5 — Permanence under base prescheme

<!-- source: V.1.5 -->

_This result says: if $X \to Z$ is affine (resp. separated, of finite type) over a base $Z$, the same holds for
$Y = X / G$, provided $G$ operates by $Z$-automorphisms; if $Z$ is locally noetherian and $X$ is finite type, then $Y$
is finite type._

**Corollary.** Suppose $X$ is a $Z$-prescheme and $G$ acts by $Z$-automorphisms (so that $Y = X / G$ is a $Z$-prescheme
by (iv) above). Then:

- $X$ is **affine** over $Z$ ⟺ $Y$ is.
- $X$ is **separated** over $Z$ ⟺ $Y$ is.
- If $X$ is **finite type** over $Z$, then $X$ is **finite** over $Y$. If moreover $Z$ is locally noetherian, then $Y$
  is finite type over $Z$.

**Proof.** Each claim is local on $Z$, so reduce to $Z$ affine. For "affine over $Z$": V.1.4 reduces to the case $Y$
affine, where $Y = \operatorname{Spec}(A^{G})$ is affine because $A$ is. For "separated": $p : X \to Y$ is integral
hence universally closed, and surjective; in the diagonal diagram

```text
X ×_Z X   --p ×_Z p-->  Y ×_Z Y
   ↑                       ↑
  Δ_X                     Δ_Y
   |                       |
   X       ----p---->      Y,
```

the closed image of $\Delta_{X}$ under $p \times_{Z} p$ is the diagonal of $Y$ (because $p$ is surjective). Hence if
$\Delta_{X}$ is closed, so is $\Delta_{Y}$. For "finite over $Y$": $X$ is integral over $Y$ and of finite type over $Y$,
so finite. For "finite type": $B = A^{G} \subset A$ and $A$ is finite type over $C = \mathcal{O}_{Z}(Z)$. By the
classical Hilbert-Noether finiteness theorem, $B$ is also of finite type over $C$ (since $A$ is finite over a
finite-type sub-$C$-algebra $B' \subset B$, and noetherianity of $B'$ makes $B$ finite over $B'$).

### V.1.6 — Affine and scheme properties

<!-- source: V.1.6 -->

_This result says: $X$ is affine (resp. a scheme) iff $Y = X / G$ is._

**Corollary.** $X$ is affine, respectively a scheme, iff $Y$ is.

The proof is the same combination of local-on-$Y$ reduction (V.1.4) and the affine $Y = \operatorname{Spec}(A^{G})$
description (V.1.1).

### V.1.7 — Definition of admissible action

<!-- source: V.1.7 -->

_This definition says: a finite group acts admissibly on a prescheme when the quotient $X / G$ exists and matches the
sheaf-of-invariants picture of V.1.3._

**Definition.** Let $X$ be a prescheme on which a finite group $G$ acts on the right. We say that $G$ **operates
admissibly** when there exists a morphism $p : X \to Y$ having the properties of V.1.3, equivalently when $X / G$ exists
as a prescheme and is isomorphic to $Y$.

### V.1.8 — Affine-orbit criterion

<!-- source: V.1.8 -->

_This result says: admissibility is the property "every orbit of $G$ lies in some affine open of $X$", equivalently "$X$
is covered by $G$-invariant affine opens"._

**Proposition.** Let $X$ be a prescheme on which the finite group $G$ acts. The following are equivalent:

1. $G$ operates **admissibly** on $X$.
1. $X$ is a union of affine opens stable under $G$.
1. Every orbit of $G$ on $X$ is contained in an affine open.

**Proof.** (1) ⟹ (2): use V.1.4 applied to a cover of $Y$ by affine opens. (2) ⟹ (3): trivial, since orbits are finite.
(3) ⟹ (2): for an orbit $T$ and an affine open $U \supseteq T$, the intersection $U' = \cap_{s \in G} s \cdot U$ is open
and $G$-stable; since affine opens form a base in $U$ and $T \subseteq U'$, take a finite affine open neighborhood
$V \subseteq U'$ of $T$, and let $U'' := \cap_{s \in G} s \cdot V$, which is a $G$-invariant affine open (intersection
of finitely many affine opens of the separated affine $U'$) containing $T$. (2) ⟹ (1): for each $G$-stable affine open
$X_{i} \subseteq X$, V.1.1 gives the quotient $Y_{i} = X_{i} / G$. Glue the $Y_{i}$ along the open subsets
$Y_{ij} \subset Y_{i}$ identified with $(X_{i} \cap X_{j}) / G$ by V.1.4. The result is a prescheme $Y$ together with a
morphism $X \to Y$ satisfying V.1.3.

A cleaner conceptual route (due to Serre): define $Y$ as the topological quotient of $X$ under the $G$-action, equip it
with the sheaf $p_{*}(\mathcal{O}_{X})^{G}$, and verify directly that the result is a prescheme satisfying V.1.3.

### Subgroups inherit admissibility

<!-- source: cor:V.1.7 -->

_This result says: if $G$ acts admissibly on $X$, every subgroup $H \subseteq G$ does too, and the quotient $X / H$
exists._

**Corollary.** If $G$ operates admissibly on $X$, the same is true for every subgroup $H \subseteq G$; hence $X / H$
exists.

**Proof.** Affineness of orbits transfers: every $H$-orbit is contained in a $G$-orbit, which lies in an affine open by
V.1.8.

### Affine over a base ⟹ admissible

<!-- source: cor:V.1.8 -->

_This result says: if $X$ is affine over some base $Z$, and $G$ acts by $Z$-automorphisms, then $G$ acts admissibly. In
that case, $X / G$ is constructed by taking the sheaf of $G$- invariants of the quasi-coherent algebra describing $X$
over $Z$._

**Corollary.** Suppose $X$ is affine over $Z$, and the operations of $G$ are $Z$-automorphisms. Then $G$ operates
admissibly on $X$. If $X$ is defined by a quasi-coherent sheaf of algebras $\mathcal{A}$ on $Z$, then $Y = X / G$ is
defined by the sheaf $\mathcal{A}^{G}$ of invariants of $\mathcal{A}$ under $G$.

### V.1.9 — Compatibility with flat base change

<!-- source: V.1.9 -->

_This result says: under flat base change $Z' \to Z$, the quotient construction commutes —
$(X / G) \times_{Z} Z'  \cong  (X \times_{Z} Z') / G$. Flatness is essential; without it the formula fails._

**Proposition.** Suppose $G$ operates admissibly on $X$, and $Y = X / G$ is a $Z$-prescheme. Let $Z' \to Z$ be a
base-change morphism, and put $X' = X \times_{Z} Z'$, $Y' = Y \times_{Z} Z'$. The morphism $p' : X' \to Y'$ (still
affine) is invariant under $G$. If $Z'$ is **flat** over $Z$, then $p'$ satisfies the hypotheses of V.1.3:

$$
\mathcal{O}_{Y'}  \longrightarrow  p'_{*}(\mathcal{O}_{X'})^{G}
$$

is an isomorphism. Hence $G$ operates admissibly on $X'$, and

```text
(X / G) ×_Z Z′  ≃  (X ×_Z Z′) / G.
```

**Proof sketch.** Reduce to $Z = Y$ and $Y, Y'$ affine. Need: if $B = A^{G}$ and $B'$ is flat over $B$, then
$B' = (A \otimes_{B} B')^{G}$. The exact sequence $0 \to B \to A \to A^{G}$ (where the last arrow is
$a \mapsto (s \cdot a - a)_{s \in G}$ and the target is the power $A^{G}$) remains exact after tensoring with $B'$
because $B'$ is flat — this is exactly what flatness gives.

**Why flatness is essential.** Without it, the formula fails in the simplest cases. Take
$Z = \operatorname{Spec} \mathbb{Z}$, $Y = \operatorname{Spec}(\mathbb{Z}[x])$, and
$Y' = \operatorname{Spec}(\mathbb{Z} / 2\mathbb{Z}[x])$ (a closed immersion, _not_ flat). Then $Y / G$ for various $G$
will not pass to $Y'$ correctly; in particular, taking $Y'$ to be a closed point of $Y$ and expecting to read off the
inertia group from $(X' / G)$ — **we will see that this reads off correctly when $X$ is étale over $Y$** (V.2 below; cf.
the discussion after V.1.9 in the source) but fails in general.

### The $Y \times E$ formalism

<!-- source: eq:V.1.* -->

For a prescheme $Y$ and a set $E$, the prescheme

```text
Y × E  :=  ⨆_{i ∈ E} Y_i,    each Y_i = Y,
```

is the disjoint sum of $|E|$ copies of $Y$. It is characterised by the universal property

```text
Hom(Y × E, Z)  =  Hom(E, Hom(Y, Z))    (sets of maps).
```

There is a canonical morphism $Y \times E \to Y$ making $Y \times E$ a prescheme over $Y$. Fibre product commutes with
disjoint sum, so for a base change $Z' \to Z$ we have $(Y \times E) \times_{Z} Z' = (Y \times_{Z} Z') \times E$. For two
sets `E, F`, $(Y \times E) \times F = Y \times (E \times F) = (Y \times E) \times_{Y} (Y \times F)$.

A finite group $G$ acting on the right on $E$ makes $Y \times E$ a prescheme with a right $G$-action, with
$(Y \times E) / G = Y \times (E / G)$. (The conditions of V.1.3 hold.) This is the **trivial-bundle** family of
examples.

The standard non-trivial-inertia example fits here: take $E = G$, with $G$ acting on itself by right translation. Then
$G$ operates with **trivial** inertia on $Y \times G$ (each fibre is a single $G$-orbit); the quotient is $Y$. This is
the algebraic analogue of the trivial topological cover $B \times G \to B$.

For $E = G \amalg G$, with $G$ acting diagonally (translating both copies), the fibre is two $G$-orbits, and the
quotient is $Y \amalg Y$. Inertia is still trivial.

For $E = G / H$ with $H \subseteq G$ a subgroup: the action is transitive on each fibre and the inertia of any point is
$H$ (the stabiliser). The quotient is $Y$.

## §V.2 Decomposition and inertia groups; the étale case

<!-- source: V.2 -->

Let $G$ be a finite group acting on the right on a prescheme $X$. For $x \in X$, the **decomposition group of $x$** is
the stabiliser

```text
G_d(x)  =  { s ∈ G : s · x = x }.
```

This group acts canonically (on the left) on the residue field $\kappa(x)$, and the kernel of that action is the
**inertia group**

```text
G_i(x)  =  { s ∈ G_d(x) : s acts trivially on κ(x) }.
```

The quotient $G_{d}(x) / G_{i}(x)$ injects into $\operatorname{Aut}_{\kappa(y)}(\kappa(x))$, and by V.1.1 (iii) the
injection is in fact an isomorphism onto $\operatorname{Gal}(\kappa(x) / \kappa(y))$ (with $y = p(x)$).

When $G$ operates admissibly and $Y = X / G$ is a $Z$-prescheme, fix a point $z \in Z$. For an algebraically closed
field $\Omega$ of sufficiently large transcendence degree over $\kappa(z)$, the geometric points
$\operatorname{Spec}(\Omega) \to X$ over $z$ correspond to $\kappa(z)$- algebra homomorphisms $\kappa(x) \to \Omega$
(where $x$ ranges over points of $X$ lying over $z$). Both $X(\Omega)$ and $Y(\Omega)$ are sets, and there is a natural
$G$-invariant map

$$
X(\Omega)  \longrightarrow  Y(\Omega).
$$

V.1.3 (ii) and (iii) say: this map is **surjective** and identifies $Y(\Omega)$ with the orbit space $X(\Omega) / G$;
moreover, for $a \in X(\Omega)$ localised at $x \in X$, the stabiliser of $a$ in $G$ is precisely the inertia group
$G_{i}(x)$.

### V.2.1 — Inertia is base-change invariant

<!-- source: V.2.1 -->

_This result says: passing to $X' = X \times_{Z} Z'$ does not change inertia groups; if $x'$ lies over $x$, then
$G_{i}(x) = G_{i}(x')$._

**Proposition.** Make a base extension $Z' \to Z$, whence $X' = X \times_{Z} Z'$. Let $x' \in X'$ and $x \in X$ its
image. Then $G_{i}(x) = G_{i}(x')$.

**Proof.** Take $\Omega$ to be an algebraically closed extension of $\kappa(z')$ of large transcendence degree, where
$z$, $z'$ are the images of $x$, $x'$ in $Z$, $Z'$. The geometric stabiliser characterisation of inertia (the paragraph
above) is the same viewed from $X$ and from $X'$, since geometric points over $z'$ correspond canonically to geometric
points over $z$ carrying the chosen $Z'$-structure.

### V.2.2 — Quotient by a subgroup gives an étale quotient when the inertia is contained

<!-- source: V.2.2 -->

_This result says: if $H \subseteq G$ contains the decomposition group of $x$, the homomorphism on completions
$\hat{\mathcal{O}}_{y} \to \hat{\mathcal{O}}_{x'}$(for$x' =$ image of$x$in$X / H$) is an isomorphism. If$H$contains the
inertia group, the morphism$\mathcal{O}_{y} \to \mathcal{O}_{x'}$is **étale** at$x'$._

**Proposition.** Under the conditions of V.1.3, suppose $Y$ is locally noetherian and $X$ is **finite** over $Y$. Let
$H \subseteq G$ be a subgroup, set $X' = X / H$ (cf. V.1.7), and let $x \in X$, $x' =$ image of$x$in$X'$,$y =$ image of
$x$ in $Y$. Then:

1. If $H \supseteq G_{d}(x)$, the homomorphism $\mathcal{O}_{y} \to \mathcal{O}_{x'}$ induces an isomorphism on
   completions.
1. If $H \supseteq G_{i}(x)$, the homomorphism $\mathcal{O}_{y} \to \mathcal{O}_{x'}$ is **étale**, i.e. $X'$ is étale
   over $Y$ at $x'$.

**Proof sketch.** Let $Y_{1} = \operatorname{Spec}(\hat{\mathcal{O}}_{y})$ and base-change to $Y_{1}$. We get
$X_{1} = X \times_{Y} Y_{1}$, finite over $Y_{1}$, with a $G$-action and quotient $Y_{1}$ (by V.1.9, since $Y_{1} \to Y$
is flat). The fibre of $X$ over $y$ is the disjoint union over points $x_{i} \in X$ over $y$ of
$\operatorname{Spec}(\kappa(x_{i}))$. Each $x_{i}$ lifts uniquely to $X_{1}$ (because $\kappa(y) = \kappa(y_{1})$); call
the lift $(x_{i})_{1}$. Set $A_{0} = \mathcal{O}_{(x_{0})_{1}}$ for our chosen $x = x_{0}$. Then $A =$ ring of$X_{1}$
decomposes as

```text
A  =  Hom_{G_d}(G, A₀)  =  { f : G → A₀ : f(s t) = s · f(t),
                                              s ∈ G_d },
```

with $G$ acting by $(u \cdot f)(t) = f(t u)$. For any $H \subseteq G$,

```text
A^H  =  { f : G → A₀ :  f(s t u) = s · f(t),  s ∈ G_d, u ∈ H },
```

a semi-local ring whose components correspond to the double classes $G_{d} \ G / H$. The component for the
identity-class double coset $G_{d} H$ is $A^{G_{d} \cap H}_{0}$. If $H \supseteq G_{d}$, this gives
$A^{G_{d}}_{0} = A^{G} = B$, so $\hat{\mathcal{O}}_{y} \to \hat{\mathcal{O}}_{x'}$ is an iso (claim (i)). For (ii) with
$H \supseteq G_{i}$: pass to a faithfully flat extension of $B$ so that the residue field becomes large enough to make
the residue extension $\kappa(x)/\kappa(y)$ trivial (using V.2.1); then $G_{i} = G_{d}$, reducing to case (i), which is
now stronger than étale.

### V.2.3 — Trivial inertia ⟹ étale

<!-- source: V.2.3 -->

_This result says: if every inertia group $G_{i}(x)$ is trivial, then $X \to Y = X / G$ is étale._

**Corollary.** Under the conditions of V.2.2, suppose $G_{i}(x) = {e}$. Then $X$ is étale over $Y$ at $x$. In
particular, if $G_{i}(x) = {e}$ for every $x \in X$, then $X \to Y$ is an étale morphism.

This is the principal **étale criterion**: trivial inertia is sufficient for étaleness of the quotient morphism.

### V.2.4 — Converse for connected $X$ and faithful $G$

<!-- source: V.2.4 -->

_This result says: when $X$ is connected and $G$ acts faithfully, étaleness of $X \to X / G$ is equivalent to trivial
inertia. In that case, $G = \operatorname{Aut}_{Y}(X)$._

**Corollary.** Suppose $X$ is **connected** and $G$ acts **faithfully** on $X$. Then $p : X \to Y = X / G$ is étale iff
the inertia groups $G_{i}(x)$ are trivial for every $x \in X$. If this holds, $G$ is canonically isomorphic to the group
of all $Y$-automorphisms of $X$.

**Proof.** "⟸" is V.2.3. For "⟹": use V.2.3 again — if $s \in G$ fixes some $x$ with non-trivial inertia, the residue
action is trivial, contradicting faithfulness once $X$ is connected (by the rigidity I.5.4 of file 11: an étale
$Y$-automorphism that agrees with the identity on a stalk agrees with the identity on the connected component). For the
"$G = \operatorname{Aut}_{Y}(X)$" statement: any $Y$-automorphism $u$ agrees, at every $x$, with some $s \in G$ (by
V.1.3 (ii) on geometric fibres: the orbit is a single $G$-orbit), and rigidity again forces $u = s$ globally.

### V.2.5 — Counterexamples to V.2.4 without the hypotheses

<!-- source: V.2.5 -->

_This remark says: both hypotheses ($X$ connected, $G$ faithful) are essential. If we drop "faithful", obviously inertia
matters less; if we drop "connected", we can have trivial-quotient cases with plenty of inertia._

**Remark.** The faithfulness hypothesis is essential. The connectedness hypothesis is essential too: take
$X = Y \times E$ for a finite set $E$ with $G$ acting on $E$ (e.g. $G$ = permutations of $E$). Then
$(Y \times E) / G = Y \times (E / G) = Y$, and $X$ is étale over $Y$. The inertia of a point $(y, e) \in Y \times E$ is
$Stab_{G}(e)$, which can be non-trivial. Yet $X \to Y$ is étale. The reason V.2.4 fails: $X$ is not connected (it has
$|E|$ connected components if $Y$ is connected), so the rigidity argument that powers "⟸" cannot conclude faithfulness
from triviality of inertia.

A second consequence of the $Y \times E$ example: taking $G \subsetneq Sym(E)$ transitive on $E$ exhibits a
$Y$-automorphism of $X$ not coming from any $s \in G$ — for instance an element of `Sym(E) \ G` acting permutationally
on the components.

A **trivial** prescheme with right $G$-action over $Y$ is one isomorphic to $Y \times G$ with $G$ acting by right
translations. Triviality is the local model: a principal covering looks locally (after base change) like $Y \times G$.

The transition to _principal coverings_ is the algebraic analogue of "Galois cover with deck group $G$":

### V.2.6 — Principal coverings: four equivalent conditions

<!-- source: V.2.6 -->

_This theorem says: there are **four equivalent ways** to characterise an algebraic Galois cover with group $G$. Two are
geometric (finite + trivial inertia + the right quotient; formal-principal-homogeneous + faithfully flat quasi-compact);
two are existence-of-trivialisation (becomes trivial after a fpqc base change; becomes trivial after a finite étale
surjective base change)._

**Theorem.** Let $Y$ be a locally noetherian prescheme, and let $X$ be a $Y$-prescheme with a finite group $G$ acting on
the right by $Y$-automorphisms. The following are equivalent:

1. $X$ is finite over $Y$, $Y = X / G$, and the inertia groups $G_{i}(x)$ are trivial for every $x \in X$.
1. There exists a faithfully flat quasi-compact base change $Y_{1} \to Y$ such that $X_{1} = X \times_{Y} Y_{1}$ is
   **trivial** as a $Y_{1}$-prescheme with operators (i.e. isomorphic to $Y_{1} \times G$).
1. As in (ii), but with $Y_{1} \to Y$ finite étale and surjective.
1. $X$ is **formally principal homogeneous** under `G_Y`, and faithfully flat and quasi-compact over $Y$.

**Proof of (i) ⟹ (iii).** Take $Y_{1} = X$. Then $X_{1} = X \times_{Y} X$, and the morphism $X \to Y$ is finite étale by
V.2.3. Trivialisation follows from the corollary V.2.7 below.

**(iii) ⟹ (ii)** is trivial.

**(ii) ⟹ (i).** The properties listed in (i) — finite over $Y$, quotient $Y$, trivial inertia — are all _invariant under
faithfully flat quasi-compact descent_. (For finiteness: cf. Grothendieck's Bourbaki seminar 190, that is,
[`bourbaki-sem-190`](appendix-black-boxes.md). For inertia: V.2.1. For the quotient: a converse to V.1.9 in the
faithfully flat setting.) The categorical framework that organises these descent statements — fibred categories,
cleavages, the descent isomorphism — is developed in files 34–38; see file 38 §VI.12 for the abstract identity that
`bourbaki-sem-190` is a geometric specialisation of.

**(i) ⟺ (iv).** "Formally principal homogeneous" means the canonical morphism $X \times_{Y} G_{Y} \to X \times_{Y} X$
whose components are the projection and the action map is an _isomorphism_. Combine with "faithfully flat and
quasi-compact" — this is the condition fpqc-trivialisation of (ii) viewed in self-image.

This is the principal definition of an algebraic Galois cover.

### V.2.7 — A section trivialises

<!-- source: V.2.7 -->

_This corollary says: under the conditions of V.2.6 (i), if $X$ admits a section over $Y$, then $X$ is *trivial* as a
space with operators — isomorphic to $Y \times G$._

**Corollary.** If V.2.6 (i) holds and $X$ admits a section $s : Y \to X$, then $X$ is a trivial space with operators,
i.e.

$$
X  \cong  Y \times G,
$$

with the standard right action of $G$ by translations on the factor $G$.

**Proof.** The section $s$ together with the action defines a morphism $Y \times G \to X$,
$(y, g) \mapsto s(y) \cdot g$, which is $G$- equivariant. It is **surjective** (because $G$ acts transitively on each
fibre by V.1.3 (ii)), **injective** (because the inertia is trivial), and a **local isomorphism** (by I.5.3 of file 11,
since $X / Y$ is étale by V.2.3). Hence an isomorphism.

### V.2.8 — Definition of principal covering

<!-- source: V.2.8 -->

_This definition says: a $Y$-prescheme $X$ with a $G$-action satisfying the equivalent V.2.6 conditions is a **principal
covering of $Y$ with Galois group $G$** — the algebraic generalisation of a finite Galois étale cover._

**Definition.** A $Y$-prescheme $X$ with a right group of operators $G$ satisfying the equivalent conditions of V.2.6 is
called a **principal covering of $Y$, with Galois group $G$**.

A principal covering is the algebraic analogue of a Galois cover with deck transformation group $G$ from file 28.

## Worked example: $\operatorname{Spec} \mathbb{Z}[\sqrt{2}] \to \operatorname{Spec} \mathbb{Z}$

Take $A = \mathbb{Z}[\sqrt{2}]$, $G = \mathbb{Z} / 2 = \langle \sigma \rangle$ with
$\sigma(a + b \sqrt{2}) = a - b \sqrt{2}$. The invariant subring is $\mathbb{Z}$ itself, so

```text
Spec(ℤ[√2])  --p-->  Spec(ℤ),    G = ℤ / 2.
```

By V.1.1, $p$ is integral, surjective, and the fibres are $G$-orbits.

**Compute the inertia at each prime $p \in \mathbb{Z}$.**

- $p = 2$: the prime $(\sqrt{2})$ ⊂ ℤ[√2] is the unique prime over `(2)`, with residue field $\mathbb{F}_{2}$. The
  decomposition group is all of $G$ (only one prime upstairs). The inertia group $G_{i}((\sqrt{2}))$ is also $G$ (since
  $\sigma$ fixes the residue $\mathbb{F}_{2} = \mathbb{Z}[\sqrt{2}] / (\sqrt{2})$). **Full inertia.** The map fails the
  étale criterion V.2.3 here.
- $p$ odd, $p \equiv \pm 1 (mod 8)$ (so `2` is a QR mod $p$): the prime `(p)` splits as
  $(p, \sqrt{2} - r)(p, \sqrt{2} + r)$ for $r^{2} \equiv 2 (mod p)$, giving two primes
  $\mathfrak{q}_{1}, \mathfrak{q}_{2}$. The decomposition group of each is trivial (the orbit
  ${\mathfrak{q}_{1}, \mathfrak{q}_{2}}$ is the whole fibre, and $\sigma$ swaps them). **Trivial inertia.**
- $p$ odd, $p \equiv \pm 3 (mod 8)$ (so `2` is a NR mod $p$): there is a unique prime $\mathfrak{q}$ over `(p)` with
  residue field $\mathbb{F}_{p^{2}}$. The decomposition group is all of $G$. The inertia group is _trivial_ (since
  $\sigma$ acts on $\mathbb{F}_{p^{2}} / \mathbb{F}_{p}$ as the Frobenius generator, non-trivially). **Trivial
  inertia.**

So $\operatorname{Spec}(\mathbb{Z}[\sqrt{2}]) \to \operatorname{Spec}(\mathbb{Z})$ is étale on
$\operatorname{Spec}(\mathbb{Z}[1/2])$ (V.2.3 applies), and _not_ étale at `(2)` (full inertia). Restricted to the open
$\operatorname{Spec}(\mathbb{Z}[1/2])$, the map is a **principal covering with Galois group $\mathbb{Z} / 2$** by V.2.6.

This recovers, in the inertia language of V.2, the file 06 discussion of where $\sqrt{2}$ "splits, is inert, or is
ramified." The arithmetic word **ramification** is exactly Grothendieck's **non-trivial inertia**.

## Worked example: $\operatorname{Spec} \mathbb{C}[x, y] / (y^{2} - x) \to \operatorname{Spec} \mathbb{C}[x]$

Take $B = \mathbb{C}[x]$, $A = \mathbb{C}[x, y] / (y^{2} - x) = \mathbb{C}[y]$ (using $x = y^{2}$),
$G = \mathbb{Z} / 2 = \langle \tau \rangle$ with $\tau(y) = -y$. Then $B = A^{G} = \mathbb{C}[y^{2}] = \mathbb{C}[x]$,
so this is a $G$-quotient in the sense of V.1.1.

**At a generic point $x = \alpha \in \mathbb{C}\^\times$ ($\alpha \neq 0$)**: there are two preimages
$y = \pm\sqrt{\alpha}$, swapped by $\tau$. Decomposition group of each is trivial; inertia is trivial. The morphism
$\operatorname{Spec}(A) \to \operatorname{Spec}(B)$ is étale at these points by V.2.3.

**At the origin $x = 0$**: the unique preimage is $y = 0$. Decomposition group is all of $G$. Residue field at
$(y) \subset A$ is $\mathbb{C}$, and $\tau$ fixes $\mathbb{C}$ (it acts only on the prime element $y$). Hence **full
inertia**: $G_{i}((y)) = G$. The morphism fails to be étale at `(y)`. This is the **branch point**.

Restricted to $\operatorname{Spec}(\mathbb{C}[x, x^{-1}])$, the morphism is a principal covering with Galois group
$\mathbb{Z} / 2$. The branch at $x = 0$ is the algebraic shadow of the topological ramification of the square-root map
$\sqrt{:} \mathbb{C} \ {0} \to \mathbb{C} \ {0}$. The algebraic fundamental group of $\mathbb{C} \ {0}$ is, again, the
profinite-completion $\hat{\mathbb{Z}}$ of file 28's $\pi^{top}_{1}(S^{1}) = \mathbb{Z}$.

## What this prepares

File 31 (= V.3, V.4) verifies the categorical axioms (G1)–(G6) for the category of finite étale coverings of a connected
locally noetherian base, then proves the abstract Galois theorem V.4.1. The principal-covering picture of V.2.6 is
exactly the algebraic version of "Galois cover" that the abstract theorem will identify with cosets $\pi / U$ for open
subgroups $U \subset \pi$. File 33 (= V.7) closes the loop: the étale fundamental group $\pi_{1}(S, a)$ is constructed
as $\operatorname{Aut}(F)$ for the fibre functor $F$ on the category of finite étale coverings of $S$, and principal
coverings correspond to **normal** open subgroups of $\pi_{1}$.
