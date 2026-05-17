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

- **Profinite groups** — the values of `Aut(F)` for a fundamental functor `F` are profinite, and the equivalence
    `𝒞 ≃ 𝒞(π)` of V.4.1 lives in the category of finite continuous `π`-sets;
- **Pro-objects of a category** — the fundamental functor `F` is represented by a pro-object `P = (P_i)`, whose
    automorphisms form `π`;
- **Strict epimorphism, strict monomorphism** — the words appear in axiom (G3) and pervasively in V.3, V.4, V.5;
- **Connected object in a category** — Grothendieck uses "connected" with no topological underlay; V.5.3 characterises
    connectedness via transitivity of the `π`-action.

We collect these here in working order, so that files 30–33 can quote without redeveloping. File 28 supplied the
topological geometric picture; this file supplies the algebraic toolkit.

## Profinite groups

A **profinite group** is a topological group `Π` that is

- **Hausdorff**,
- **compact**,
- **totally disconnected** (the only connected components are single points).

Equivalently: a topological group isomorphic, as a topological group, to a projective limit of finite (discrete) groups,

```text
Π  ≅  lim_{i ∈ I} G_i,
```

over a filtered ordered set `I` with finite groups `G_i` and group homomorphisms `G_j → G_i` for every `i ≤ j`. Both
descriptions are equivalent (the implication "compact + Hausdorff + totally disconnected ⟹ projective limit of finite"
uses Stone duality applied to clopen subsets).

### Examples

- `ℤ̂  =  lim_n ℤ / nℤ`. Concretely, `Ẑ` is the set of compatible systems `(a_n mod n)_{n ≥ 1}`, a topological ring
    under componentwise operations. Contains `ℤ` densely. By the Chinese remainder theorem, `ℤ̂  ≅  ∏_p ℤ_p`, the
    product over primes of the `p`-adic integers.
- `ℤ_p  =  lim_n ℤ / pⁿℤ`. The `p`-adic integers, a compact Hausdorff totally disconnected topological ring. Contains
    `ℤ` densely.
- `Gal(K^sep / K)` for any field `K`. A profinite group with the Krull topology: open subgroups are exactly
    `Gal(K^sep / L)` for `L / K` finite separable. Generalises both `ℤ̂` (take `K = 𝔽_p`) and the absolute Galois groups
    of number fields.
- `F̂_n`, the **free profinite group on `n` generators**: the profinite completion of the free group `F_n` on `n`
    letters. For `n ≥ 2`, `F̂_n` is uncountable, non-abelian, and somewhat mysterious.
- Any finite group, viewed as a profinite group with the discrete topology.

### The topology

Open subgroups of a profinite group `Π` are exactly the preimages of subgroups of finite quotients in the projective
system. They form a **fundamental system of neighborhoods of the identity**: every neighborhood of `1 ∈ Π` contains some
open subgroup. Open subgroups are automatically of finite index, but not every finite-index subgroup is open.
(Counter-example: abstractly, `ℤ̂` has uncountably many subgroups of finite index; only countably many are open.)

A **closed subgroup** of a profinite group is the intersection of the open subgroups containing it. Two consequences:

- A closed subgroup `H ⊆ Π` is itself profinite (with the subspace topology).
- For two closed subgroups `M, N ⊆ Π`, `M ⊆ N` iff every open subgroup containing `N` contains `M`. (This is the
    technical fact V.6.4 and V.6.6 lean on.)

The intersection of any family of closed subgroups is closed. Among closed subgroups, the **closed normal subgroups**
are those preserved by the conjugation action of `Π` — equivalently, those that are kernels of continuous homomorphisms
to other profinite groups.

### Continuous actions on finite sets

A **continuous action** of a profinite group `Π` on a discrete finite set `E` is a homomorphism `ρ : Π → Sym(E)` that is
continuous when `Sym(E)` carries the discrete topology. Equivalently: the stabiliser `Stab_Π(e)` of every `e ∈ E` is an
**open subgroup** of `Π`. Equivalently again: the action factors through a finite discrete quotient `Π → Π / U` for some
open invariant subgroup `U ⊆ Π`.

The **category `𝒞(Π)`** has as objects the finite discrete sets on which `Π` acts continuously on the left, and as
morphisms the `Π`-equivariant maps. This category appears in V.4 as the target of the equivalence `𝒞 ≃ 𝒞(π)`.

### The profinite completion

Let `G` be an abstract group. The **profinite completion** of `G` is

```text
Ĝ  :=  lim_{N ⊲ G, [G : N] < ∞}  G / N,
```

the projective limit over all finite-index normal subgroups. By construction `Ĝ` is profinite, and there is a canonical
homomorphism `G → Ĝ` whose image is dense.

The **universal property** of `Ĝ`: for any profinite group `Π`,

```text
Hom_{groups}(G, Π)  =  Hom_{cts. groups}(Ĝ, Π)
```

(continuous homomorphisms on the right). In particular, every continuous action of `G` on a finite set extends uniquely
to a continuous action of `Ĝ`.

### Examples of profinite completion

- `ℤ̂`, the profinite completion of `ℤ`. Used pervasively as the Galois group `Gal(𝔽̄_p / 𝔽_p)` and as `π̂₁^top(S¹)`.
- `ℤ_p`, the profinite completion of `ℤ` along the powers of `p`. Equivalently the `p`-adic part of `ℤ̂` under the
    decomposition `ℤ̂ = ∏_p ℤ_p`.
- `F̂_n`, the profinite completion of `F_n`.

#### Aside (number fields).

_Skip if you do not yet care about arithmetic._ The absolute Galois group `Gal(ℚ̄ / ℚ)` is _not_ the profinite
completion of any abstract group. It is profinite, but its structure as a projective limit of finite groups carries
arithmetic information that no abstract group can supply. This is why the étale fundamental group
`π₁^ét(Spec ℤ[1/N], η̄)` (= a quotient of `Gal(ℚ̄ / ℚ)`) is a nontrivial object of arithmetic geometry.

## Pro-objects of a category

Let `𝒞` be a category. A **pro-object** of `𝒞` is a projective system `(P_i)_{i ∈ I}` indexed by a filtered ordered set
`I`, with transition morphisms `φ_{ji} : P_i → P_j` for every `i ≥ j` satisfying `φ_{kj} ∘ φ_{ji} = φ_{ki}`.

Pro-objects form a category `Pro-𝒞` whose morphisms are

```text
Hom_{Pro-𝒞}(P, Q)  :=  lim_j  colim_i  Hom_𝒞(P_i, Q_j)
```

for `P = (P_i)_{i ∈ I}` and `Q = (Q_j)_{j ∈ J}`. The category `𝒞` embeds fully faithfully into `Pro-𝒞` by
`X ↦ (X)_{i ∈ {*}}`, the constant pro-object on the one-element index set. Dually, `Ind-𝒞` is the category of **filtered
colimits** of objects of `𝒞`, with `Hom`-formula

```text
Hom_{Ind-𝒞}(P, Q)  :=  lim_i  colim_j  Hom_𝒞(P_i, Q_j).
```

A **pro-object represents a functor** `F : 𝒞 → Set` when there is a functorial isomorphism

```text
F(X)  ≅  Hom_{Pro-𝒞}(P, X)  =  colim_i  Hom_𝒞(P_i, X).
```

We then say `F` is **pro-representable**.

### Strict pro-representability

A set-valued functor `F : 𝒞 → Set` is **strictly pro- representable** when it admits a representing pro-object as above
_and_ the index `I` may be chosen so that all transition morphisms `φ_{ji} : P_i → P_j` for `i ≥ j` are _epimorphisms_,
and so that every epimorphism `P_i → P′` (in `𝒞`) is equivalent to one of the `φ_{ji}`. The pro-object is then
determined up to unique isomorphism, and we say it is in **normal form**.

The fundamental fact, due to Grothendieck (Bourbaki seminar 195, Feb 1960):

**Theorem (strict pro-representability).** Let `𝒞` be a category in which every object is **artinian** (every descending
chain of subobjects is eventually constant), and let `F : 𝒞 → Set` be a left-exact functor (i.e. `F` carries finite
limits to finite limits) with finite values. Then `F` is strictly pro-representable.

This is the **black box** [`bourbaki-sem-195`](appendix-black-boxes.md) that file 31's walk-through of V.4.1 will quote.
A Galois category (defined in V.5.1; see file 32) is in particular artinian (V.4 step b), and a fundamental functor `F`
is left- exact (axiom (G4)) and finite-set-valued, so the theorem applies. (Equivalently called a **fibre functor**;
"fundamental functor" is the term Grothendieck uses in Exposé V, "fibre functor" is the modern name, and the two are
synonymous — we use both.) The pro-object that emerges is the **fundamental pro-object** `P_F`, whose automorphism
group is the **fundamental group** `π = Aut(F)`.

### Why pro-objects, not just objects

`𝒞` itself may have no terminal object whose hom-functor is `F`. Consider `𝒞 = 𝒞(π)` for a profinite group `π`, and
`F = forget` to finite sets. The "object that represents `F`" would have to be `π` itself with its left-multiplication
action — a continuous, totally disconnected, _infinite_ `π`-set, not an object of `𝒞` (which contains only finite sets).
The remedy: present `π` as a projective limit of its finite discrete quotients `π / U` for open invariant subgroups
`U ⊂ π`, each of which _is_ an object of `𝒞`. The system `(π / U)_U` is the pro-object representing `F`, and
`Aut(P) = π` recovers the original group.

We cash this in at file 31 V.4 step (a). The étale fundamental group is generally infinite, while the category of finite
étale coverings has only finite objects. The universal cover therefore cannot live in that category; it lives as a
pro-object — a compatible system of finite covers — and the fundamental group is recovered as its automorphism group.

## Strict epimorphisms and strict monomorphisms

Let `u : X → Y` be a morphism in a category `𝒞` admitting fibre products. We say `u` is a **strict epimorphism** when
the fibre product `X ×_u,Y,u X` exists and the diagram

```text
X ×_Y X  ⇉  X  →  Y
```

is a coequaliser: for every `Z ∈ 𝒞` and every `ψ : X → Z` with `ψ ∘ p₁ = ψ ∘ p₂` (where `p₁, p₂ : X ×_Y X → X` are the
two projections), there exists a _unique_ `ψ̃ : Y → Z` with `ψ̃ ∘ u = ψ`.

Dually, `u : X → Y` is a **strict monomorphism** when the push-out `X ⨿_u Y ⨿_u X` exists and the dual diagram is an
equaliser.

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

Let `𝒞` be a category with finite coproducts and an initial object `∅_𝒞`. An object `X ∈ 𝒞` is **connected** when

- `X ≄ ∅_𝒞` (i.e. `X` is not initial), and
- for every isomorphism `X ≅ A ⨿ B` with `A, B ∈ 𝒞`, either `A ≅ ∅_𝒞` or `B ≅ ∅_𝒞`.

In `Set`: the connected objects are the singletons. (`∅_𝒞` is excluded by the first clause.)

In `𝒞(π)` for a profinite group `π`: the connected objects are the finite sets on which `π` acts _transitively_. (V.5.3
will phrase this via the fundamental functor.)

In the category of topological spaces: connected objects in this categorical sense agree with topologically-connected
non-empty spaces.

### Connectedness and the fundamental functor

A central fact, used throughout V.5: in a Galois category `𝒞` with fundamental functor `F`, an object `X ∈ 𝒞` is
connected if and only if `F(X)` is **transitive** under the canonical action of `π = Aut(F)`. (This is V.5.3.) The two
conditions match because:

- `X` connected as a categorical object ⟹ `F(X)` does not split as a disjoint union of two non-empty `π`-stable subsets
    ⟹ `π` acts transitively;
- `F(X)` transitive ⟹ any decomposition `X = A ⨿ B` would force `F(A) = ∅` or `F(B) = ∅` (since `π` cannot act
    transitively on a disjoint union), and hence `A = ∅_𝒞` or `B = ∅_𝒞` by the conservativity of `F` (axiom (G6)).

### Examples

- `𝒞(ℤ̂)`: the connected objects are the cosets `ℤ̂ / nℤ̂` for `n ≥ 1`, equivalently the finite cyclic `ℤ̂`-sets
    `ℤ / nℤ` with `ℤ̂` acting through its quotient `ℤ / nℤ`. Each such is one orbit.
- `𝒞(F̂₂)`: the connected objects are finite sets on which `F̂₂` acts transitively. There are infinitely many up to iso
    for each given cardinality.
- The category of finite étale coverings of `Spec 𝔽_p`: connected objects are `Spec 𝔽_{pⁿ}` for `n ≥ 1`, matching
    `𝒞(ℤ̂)` under the equivalence `π₁(Spec 𝔽_p, ā) = ℤ̂` of file 33.

## What this prepares

File 30 (= V.1, V.2) uses pro-objects implicitly in handling the orbits of a finite-group action and the fundamental
groupoid of points over a fixed base. File 31 (= V.3, V.4) verifies the strict-epimorphism axiom (G3) for finite étale
covers (V.3.5), and the pro-object `P` representing `F` is built by quoting
[`bourbaki-sem-195`](appendix-black-boxes.md) in V.4 step c. File 32 (= V.5, V.6) develops the formalism: the
closed-subgroup ↔ open-subgroup duality of profinite groups (and continuous actions on finite sets) drives V.5.5, V.6.4,
V.6.6 verbatim. File 33 (= V.7) yields `π₁(S, a)` as a profinite group whose continuous action on `F_a(X)` for `X / S`
étale is the engine of the equivalence `𝒞(S) ≃ 𝒞(π₁(S, a))`.
