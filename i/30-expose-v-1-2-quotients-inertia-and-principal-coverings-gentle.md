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

Topological covering spaces carry a deck transformation group. A finite-sheeted Galois cover `p : E → B` has
`Aut(E / B)` of order equal to the degree, acting freely and transitively on each fibre. Inverting the picture: a finite
group `G` acting freely on a "nice" total space `E` produces a covering `E → E / G`, with the quotient inheriting the
topology.

The algebraic analogue replaces "topological space" by "prescheme" and "free action" by "action by automorphisms with
trivial inertia". The first task is to make the quotient construction work — when does `X / G` exist as a prescheme, and
how do its properties relate to those of `X`? §1 settles this. The construction is local-on-`Y`, requires only that
every orbit of `G` on `X` lie in an affine open (the **admissibility** condition V.1.7–V.1.8), and behaves well under
flat base change (V.1.9).

The second task: when is the quotient _étale_? §2 attaches to each `x ∈ X` two subgroups of `G` — the **decomposition
group** `G_d(x)` (the stabiliser) and the **inertia group** `G_i(x)` (the kernel of the residue-field action). The étale
case (V.2.3, V.2.4) is exactly: trivial inertia at every point. This pins down the algebraic shadow of "free action" and
the conditions under which `X → X / G` is an étale Galois cover.

The two sections close with **principal coverings** (V.2.6, V.2.8): the algebraic analogue of "Galois cover with deck
group `G`", characterised by four equivalent conditions (the formal-principal-homogeneous-bundle picture, the
trivialisation by faithfully flat base change, the trivialisation by an étale cover by `X` itself, and the
inertia/quotient pair).

The covering theory of file 28 is the topological mirror to this algebraic story; the dictionary is

```text
deck transformation group         ↔   G acting on X
free action                       ↔   trivial inertia G_i(x)
covering map                      ↔   étale quotient morphism X → X/G
finite Galois cover               ↔   principal covering with group G.
```

Two pieces of terminology used throughout this file. When a group `G` acts on a scheme `X` and `x ∈ X` is a fixed point,
the stabiliser acts on the residue field `κ(x)` by ring automorphisms; this is the **residue-field action**. The
**decomposition group** `G_d(x) := {g ∈ G : g·x = x}` is the stabiliser of `x` in `G`, and the **inertia group**
`G_i(x) ⊂ G_d(x)` is the kernel of the residue-field action `G_d(x) → Aut(κ(x))` — the subgroup that fixes the residue
field pointwise. The formal restatement appears in §V.2.

We begin with the construction of `X / G`.

## §V.1 Prescheme with a finite group of operators; quotient prescheme

Let `X` be a prescheme, and let `G` be a finite group acting on `X` by automorphisms on the right. (The right-action
convention is Grothendieck's; it makes the order of operations `(s t) ⋅ x  =  t ⋅ (s ⋅ x)` natural for composition.) If
`X = Spec(A)` is affine, then `G` acts on the _left_ on the ring `A`, and the natural object to consider is the subring
of invariants

```text
A^G  =  { a ∈ A : s · a = a for all s ∈ G }.
```

For a general `Y`, we ask the universal property: a **quotient** of `X` by `G` is a `G`-invariant morphism `p : X → Y`
such that, for every prescheme `Z`, the canonical map

```text
Hom(Y, Z)  ⟶  Hom(X, Z)^G,    g ↦ g ∘ p,
```

is a _bijection_ onto the set of `G`-invariant morphisms `X → Z`. When such a `(Y, p)` exists, it is determined up to
unique isomorphism, and we write `Y = X / G`.

### V.1.1 — `Spec(A^G)` is the quotient

<!-- source: V.1.1 -->

_This result says: in the affine case the quotient prescheme exists and is `Spec(A^G)`; the morphism
`Spec(A) → Spec(A^G)` is integral, surjective, has fibres equal to `G`-orbits, the topology of the quotient is the
quotient topology, and the residue-field extensions at points are quasi-Galois with surjection from the decomposition
group to the residue Galois group._

**Proposition.** Let `A` be a ring on which the finite group `G` acts on the left, let `B = A^G`, let `X = Spec(A)`,
`Y = Spec(B)`, and let `p : X → Y` be the canonical morphism (invariant under `G`). Then:

1. `A` is integral over `B`; equivalently, `p` is an **integral morphism**.
1. `p` is surjective; its fibres are the orbits of `G` on `X`; the topology of `Y` is the quotient of the topology of
    `X` under the action.
1. For `x ∈ X`, `y = p(x)`, the residue extension `κ(x) / κ(y)` is **quasi-Galois algebraic**, and the canonical map
    from `G_d(x)` (stabiliser of `x`) to the group of `κ(y)`- automorphisms of `κ(x)` is **surjective**.
1. `(Y, p)` is a quotient prescheme of `X` by `G`.

**Proof sketch.** For (i): every `a ∈ A` satisfies the monic polynomial `∏_{s ∈ G}(T − s · a) ∈ B[T]`, so `A` is
integral over `B`. For (ii): the surjectivity and the orbit-as-fibre description follow from going-up / lying-over for
integral extensions (Cohen–Seidenberg). For non-specialists: if `B ⊂ A` is an integral ring extension, every prime ideal
of `B` is the contraction of some prime of `A` (lying-over), and a chain of primes in `B` lifts to a chain of primes in
`A` (going-up). The topology assertion uses the extra fact that **integral morphisms are closed**: an integral `p`
carries closed sets of `X` to closed sets of `Y` (because the image of `V(I) ⊆ X` is `V(I ∩ B) ⊆ Y`). For (iii): both
`G_d(x)` and `Gal(κ(x) / κ(y))` are finite groups acting on `κ(x) / κ(y)`; the surjectivity is a standard
splitting-field argument. (See Bourbaki _Algèbre Commutative_ V §1–§2 for full detail.) For (iv): combine (ii) and the
universal property of `B = A^G`.

### V.1.2 — Sheaves of invariants

<!-- source: V.1.2 -->

_This result says: the structure sheaf of the quotient is the sheaf of `G`-invariants of the pushforward of the
structure sheaf of `X`._

**Corollary.** Under the conditions of V.1.1, the canonical homomorphism

```text
𝒪_Y  ⟶  p_*(𝒪_X)^G
```

is an isomorphism.

**Proof.** It is enough to check on a basis of opens given by distinguished opens `D(f) ⊆ Y` for `f ∈ B`. The point is
the formula

```text
(S⁻¹A)^G  =  S⁻¹(A^G)
```

valid for every multiplicatively stable `S ⊆ B`. Concretely for `S = {1, f, f², …}`: the right side is `B[1/f]` and the
left side is `(A[1/f])^G = A^G[1/f]` because `f` is `G`-invariant.

Beyond the affine case, we extract the _property_ that characterises a quotient morphism:

### V.1.3 — Sheaf-of-invariants criterion in general

<!-- source: V.1.3 -->

*This result says: V.1.1's conclusions hold for any `G`-invariant affine morphism `p : X → Y` such that the natural map
`𝒪_Y → p_*(𝒪*X)^G` is an isomorphism.*

**Proposition.** Let `X` be a prescheme on which the finite group `G` acts, and let `p : X → Y` be a `G`-invariant
**affine** morphism such that

```text
𝒪_Y  ⟶  p_*(𝒪_X)^G
```

is an isomorphism. Then conclusions (i), (ii), (iii), (iv) of V.1.1 are still valid.

**Proof.** For (i)–(iii), reduce to the affine case `Y = Spec(B)`, `X = Spec(A)`. The hypothesis says `B = A^G`, so
V.1.1 applies. For (iv), use (ii) and the sheaf-of-invariants identification.

### V.1.4 — Restriction to opens

<!-- source: V.1.4 -->

_This result says: for any open `U ⊆ Y`, the preimage `p⁻¹(U) ⊆ X` is a quotient of `U` by `G`. The construction is
local on the base._

**Corollary.** Under the conditions of V.1.3, for every open `U ⊆ Y`, the morphism `p⁻¹(U) → U` induced by `p` makes `U`
a quotient of `p⁻¹(U) = X|_U` by `G`.

**Proof.** The hypotheses transfer to `p⁻¹(U) → U` directly.

### V.1.5 — Permanence under base prescheme

<!-- source: V.1.5 -->

_This result says: if `X → Z` is affine (resp. separated, of finite type) over a base `Z`, the same holds for
`Y = X / G`, provided `G` operates by `Z`-automorphisms; if `Z` is locally noetherian and `X` is finite type, then `Y`
is finite type._

**Corollary.** Suppose `X` is a `Z`-prescheme and `G` acts by `Z`-automorphisms (so that `Y = X / G` is a `Z`-prescheme
by (iv) above). Then:

- `X` is **affine** over `Z` ⟺ `Y` is.
- `X` is **separated** over `Z` ⟺ `Y` is.
- If `X` is **finite type** over `Z`, then `X` is **finite** over `Y`. If moreover `Z` is locally noetherian, then `Y`
    is finite type over `Z`.

**Proof.** Each claim is local on `Z`, so reduce to `Z` affine. For "affine over `Z`": V.1.4 reduces to the case `Y`
affine, where `Y = Spec(A^G)` is affine because `A` is. For "separated": `p : X → Y` is integral hence universally
closed, and surjective; in the diagonal diagram

```text
X ×_Z X   --p ×_Z p-->  Y ×_Z Y
   ↑                       ↑
  Δ_X                     Δ_Y
   |                       |
   X       ----p---->      Y,
```

the closed image of `Δ_X` under `p ×_Z p` is the diagonal of `Y` (because `p` is surjective). Hence if `Δ_X` is closed,
so is `Δ_Y`. For "finite over `Y`": `X` is integral over `Y` and of finite type over `Y`, so finite. For "finite type":
`B = A^G ⊂ A` and `A` is finite type over `C = 𝒪_Z(Z)`. By the classical Hilbert-Noether finiteness theorem, `B` is also
of finite type over `C` (since `A` is finite over a finite-type sub-`C`-algebra `B′ ⊂ B`, and noetherianity of `B′`
makes `B` finite over `B′`).

### V.1.6 — Affine and scheme properties

<!-- source: V.1.6 -->

_This result says: `X` is affine (resp. a scheme) iff `Y = X / G` is._

**Corollary.** `X` is affine, respectively a scheme, iff `Y` is.

The proof is the same combination of local-on-`Y` reduction (V.1.4) and the affine `Y = Spec(A^G)` description (V.1.1).

### V.1.7 — Definition of admissible action

<!-- source: V.1.7 -->

_This definition says: a finite group acts admissibly on a prescheme when the quotient `X / G` exists and matches the
sheaf-of-invariants picture of V.1.3._

**Definition.** Let `X` be a prescheme on which a finite group `G` acts on the right. We say that `G` **operates
admissibly** when there exists a morphism `p : X → Y` having the properties of V.1.3, equivalently when `X / G` exists
as a prescheme and is isomorphic to `Y`.

### V.1.8 — Affine-orbit criterion

<!-- source: V.1.8 -->

_This result says: admissibility is the property "every orbit of `G` lies in some affine open of `X`", equivalently "`X`
is covered by `G`-invariant affine opens"._

**Proposition.** Let `X` be a prescheme on which the finite group `G` acts. The following are equivalent:

1. `G` operates **admissibly** on `X`.
1. `X` is a union of affine opens stable under `G`.
1. Every orbit of `G` on `X` is contained in an affine open.

**Proof.** (1) ⟹ (2): use V.1.4 applied to a cover of `Y` by affine opens. (2) ⟹ (3): trivial, since orbits are finite.
(3) ⟹ (2): for an orbit `T` and an affine open `U ⊇ T`, the intersection `U′ = ∩_{s ∈ G} s · U` is open and `G`-stable;
since affine opens form a base in `U` and `T ⊆ U′`, take a finite affine open neighborhood `V ⊆ U′` of `T`, and let
`U″ := ∩_{s ∈ G} s · V`, which is a `G`-invariant affine open (intersection of finitely many affine opens of the
separated affine `U′`) containing `T`. (2) ⟹ (1): for each `G`-stable affine open `X_i ⊆ X`, V.1.1 gives the quotient
`Y_i = X_i / G`. Glue the `Y_i` along the open subsets `Y_{ij} ⊂ Y_i` identified with `(X_i ∩ X_j) / G` by V.1.4. The
result is a prescheme `Y` together with a morphism `X → Y` satisfying V.1.3.

A cleaner conceptual route (due to Serre): define `Y` as the topological quotient of `X` under the `G`-action, equip it
with the sheaf `p_*(𝒪_X)^G`, and verify directly that the result is a prescheme satisfying V.1.3.

### Subgroups inherit admissibility

<!-- source: cor:V.1.7 -->

_This result says: if `G` acts admissibly on `X`, every subgroup `H ⊆ G` does too, and the quotient `X / H` exists._

**Corollary.** If `G` operates admissibly on `X`, the same is true for every subgroup `H ⊆ G`; hence `X / H` exists.

**Proof.** Affineness of orbits transfers: every `H`-orbit is contained in a `G`-orbit, which lies in an affine open by
V.1.8.

### Affine over a base ⟹ admissible

<!-- source: cor:V.1.8 -->

_This result says: if `X` is affine over some base `Z`, and `G` acts by `Z`-automorphisms, then `G` acts admissibly. In
that case, `X / G` is constructed by taking the sheaf of `G`- invariants of the quasi-coherent algebra describing `X`
over `Z`._

**Corollary.** Suppose `X` is affine over `Z`, and the operations of `G` are `Z`-automorphisms. Then `G` operates
admissibly on `X`. If `X` is defined by a quasi-coherent sheaf of algebras `𝒜` on `Z`, then `Y = X / G` is defined by
the sheaf `𝒜^G` of invariants of `𝒜` under `G`.

### V.1.9 — Compatibility with flat base change

<!-- source: V.1.9 -->

_This result says: under flat base change `Z′ → Z`, the quotient construction commutes —
`(X / G) ×_Z Z′  ≅  (X ×_Z Z′) / G`. Flatness is essential; without it the formula fails._

**Proposition.** Suppose `G` operates admissibly on `X`, and `Y = X / G` is a `Z`-prescheme. Let `Z′ → Z` be a
base-change morphism, and put `X′ = X ×_Z Z′`, `Y′ = Y ×_Z Z′`. The morphism `p′ : X′ → Y′` (still affine) is invariant
under `G`. If `Z′` is **flat** over `Z`, then `p′` satisfies the hypotheses of V.1.3:

```text
𝒪_{Y′}  ⟶  p′_*(𝒪_{X′})^G
```

is an isomorphism. Hence `G` operates admissibly on `X′`, and

```text
(X / G) ×_Z Z′  ≃  (X ×_Z Z′) / G.
```

**Proof sketch.** Reduce to `Z = Y` and `Y, Y′` affine. Need: if `B = A^G` and `B′` is flat over `B`, then
`B′ = (A ⊗_B B′)^G`. The exact sequence `0 → B → A → A^G` (where the last arrow is `a ↦ (s · a − a)_{s ∈ G}` and the
target is the power `A^G`) remains exact after tensoring with `B′` because `B′` is flat — this is exactly what flatness
gives.

**Why flatness is essential.** Without it, the formula fails in the simplest cases. Take `Z = Spec ℤ`, `Y = Spec(ℤ[x])`,
and `Y′ = Spec(ℤ / 2ℤ[x])` (a closed immersion, _not_ flat). Then `Y / G` for various `G` will not pass to `Y′`
correctly; in particular, taking `Y′` to be a closed point of `Y` and expecting to read off the inertia group from
`(X′ / G)` — **we will see that this reads off correctly when `X` is étale over `Y`** (V.2 below; cf. the discussion
after V.1.9 in the source) but fails in general.

### The `Y × E` formalism

<!-- source: eq:V.1.* -->

For a prescheme `Y` and a set `E`, the prescheme

```text
Y × E  :=  ⨆_{i ∈ E} Y_i,    each Y_i = Y,
```

is the disjoint sum of `|E|` copies of `Y`. It is characterised by the universal property

```text
Hom(Y × E, Z)  =  Hom(E, Hom(Y, Z))    (sets of maps).
```

There is a canonical morphism `Y × E → Y` making `Y × E` a prescheme over `Y`. Fibre product commutes with disjoint sum,
so for a base change `Z′ → Z` we have `(Y × E) ×_Z Z′ = (Y ×_Z Z′) × E`. For two sets `E, F`,
`(Y × E) × F = Y × (E × F) = (Y × E) ×_Y (Y × F)`.

A finite group `G` acting on the right on `E` makes `Y × E` a prescheme with a right `G`-action, with
`(Y × E) / G = Y × (E / G)`. (The conditions of V.1.3 hold.) This is the **trivial-bundle** family of examples.

The standard non-trivial-inertia example fits here: take `E = G`, with `G` acting on itself by right translation. Then
`G` operates with **trivial** inertia on `Y × G` (each fibre is a single `G`-orbit); the quotient is `Y`. This is the
algebraic analogue of the trivial topological cover `B × G → B`.

For `E = G ⨿ G`, with `G` acting diagonally (translating both copies), the fibre is two `G`-orbits, and the quotient is
`Y ⨿ Y`. Inertia is still trivial.

For `E = G / H` with `H ⊆ G` a subgroup: the action is transitive on each fibre and the inertia of any point is `H` (the
stabiliser). The quotient is `Y`.

## §V.2 Decomposition and inertia groups; the étale case

<!-- source: V.2 -->

Let `G` be a finite group acting on the right on a prescheme `X`. For `x ∈ X`, the **decomposition group of `x`** is the
stabiliser

```text
G_d(x)  =  { s ∈ G : s · x = x }.
```

This group acts canonically (on the left) on the residue field `κ(x)`, and the kernel of that action is the **inertia
group**

```text
G_i(x)  =  { s ∈ G_d(x) : s acts trivially on κ(x) }.
```

The quotient `G_d(x) / G_i(x)` injects into `Aut_{κ(y)}(κ(x))`, and by V.1.1 (iii) the injection is in fact an
isomorphism onto `Gal(κ(x) / κ(y))` (with `y = p(x)`).

When `G` operates admissibly and `Y = X / G` is a `Z`-prescheme, fix a point `z ∈ Z`. For an algebraically closed field
`Ω` of sufficiently large transcendence degree over `κ(z)`, the geometric points `Spec(Ω) → X` over `z` correspond to
`κ(z)`- algebra homomorphisms `κ(x) → Ω` (where `x` ranges over points of `X` lying over `z`). Both `X(Ω)` and `Y(Ω)`
are sets, and there is a natural `G`-invariant map

```text
X(Ω)  ⟶  Y(Ω).
```

V.1.3 (ii) and (iii) say: this map is **surjective** and identifies `Y(Ω)` with the orbit space `X(Ω) / G`; moreover,
for `a ∈ X(Ω)` localised at `x ∈ X`, the stabiliser of `a` in `G` is precisely the inertia group `G_i(x)`.

### V.2.1 — Inertia is base-change invariant

<!-- source: V.2.1 -->

_This result says: passing to `X′ = X ×_Z Z′` does not change inertia groups; if `x′` lies over `x`, then
`G_i(x) = G_i(x′)`._

**Proposition.** Make a base extension `Z′ → Z`, whence `X′ = X ×_Z Z′`. Let `x′ ∈ X′` and `x ∈ X` its image. Then
`G_i(x) = G_i(x′)`.

**Proof.** Take `Ω` to be an algebraically closed extension of `κ(z′)` of large transcendence degree, where `z`, `z′`
are the images of `x`, `x′` in `Z`, `Z′`. The geometric stabiliser characterisation of inertia (the paragraph above) is
the same viewed from `X` and from `X′`, since geometric points over `z′` correspond canonically to geometric points over
`z` carrying the chosen `Z′`-structure.

### V.2.2 — Quotient by a subgroup gives an étale quotient when the inertia is contained

<!-- source: V.2.2 -->

_This result says: if `H ⊆ G` contains the decomposition group of `x`, the homomorphism on completions
`𝒪̂_y → 𝒪̂_{x'}`(for`x' =` image of`x`in`X / H`) is an isomorphism. If`H`contains the inertia group, the
morphism`𝒪_y → 𝒪_{x'}`is **étale** at`x'`._

**Proposition.** Under the conditions of V.1.3, suppose `Y` is locally noetherian and `X` is **finite** over `Y`. Let
`H ⊆ G` be a subgroup, set `X′ = X / H` (cf. V.1.7), and let `x ∈ X`, `x′ =` image of`x`in`X′`,`y =` image of `x` in
`Y`. Then:

1. If `H ⊇ G_d(x)`, the homomorphism `𝒪_y → 𝒪_{x′}` induces an isomorphism on completions.
1. If `H ⊇ G_i(x)`, the homomorphism `𝒪_y → 𝒪_{x′}` is **étale**, i.e. `X′` is étale over `Y` at `x′`.

**Proof sketch.** Let `Y₁ = Spec(𝒪̂_y)` and base-change to `Y₁`. We get `X₁ = X ×_Y Y₁`, finite over `Y₁`, with a
`G`-action and quotient `Y₁` (by V.1.9, since `Y₁ → Y` is flat). The fibre of `X` over `y` is the disjoint union over
points `x_i ∈ X` over `y` of `Spec(κ(x_i))`. Each `x_i` lifts uniquely to `X₁` (because `κ(y) = κ(y₁)`); call the lift
`(x_i)₁`. Set `A₀ = 𝒪_{(x₀)₁}` for our chosen `x = x₀`. Then `A =` ring of`X₁` decomposes as

```text
A  =  Hom_{G_d}(G, A₀)  =  { f : G → A₀ : f(s t) = s · f(t),
                                              s ∈ G_d },
```

with `G` acting by `(u · f)(t) = f(t u)`. For any `H ⊆ G`,

```text
A^H  =  { f : G → A₀ :  f(s t u) = s · f(t),  s ∈ G_d, u ∈ H },
```

a semi-local ring whose components correspond to the double classes `G_d \ G / H`. The component for the identity-class
double coset `G_d H` is `A₀^{G_d ∩ H}`. If `H ⊇ G_d`, this gives `A₀^{G_d} = A^G = B`, so `𝒪̂_y → 𝒪̂_{x'}` is an iso
(claim (i)). For (ii) with `H ⊇ G_i`: pass to a faithfully flat extension of `B` so that the residue field becomes large
enough to make the residue extension `κ(x)/κ(y)` trivial (using V.2.1); then `G_i = G_d`, reducing to case (i), which is
now stronger than étale.

### V.2.3 — Trivial inertia ⟹ étale

<!-- source: V.2.3 -->

_This result says: if every inertia group `G_i(x)` is trivial, then `X → Y = X / G` is étale._

**Corollary.** Under the conditions of V.2.2, suppose `G_i(x) = {e}`. Then `X` is étale over `Y` at `x`. In particular,
if `G_i(x) = {e}` for every `x ∈ X`, then `X → Y` is an étale morphism.

This is the principal **étale criterion**: trivial inertia is sufficient for étaleness of the quotient morphism.

### V.2.4 — Converse for connected `X` and faithful `G`

<!-- source: V.2.4 -->

_This result says: when `X` is connected and `G` acts faithfully, étaleness of `X → X / G` is equivalent to trivial
inertia. In that case, `G = Aut_Y(X)`._

**Corollary.** Suppose `X` is **connected** and `G` acts **faithfully** on `X`. Then `p : X → Y = X / G` is étale iff
the inertia groups `G_i(x)` are trivial for every `x ∈ X`. If this holds, `G` is canonically isomorphic to the group of
all `Y`-automorphisms of `X`.

**Proof.** "⟸" is V.2.3. For "⟹": use V.2.3 again — if `s ∈ G` fixes some `x` with non-trivial inertia, the residue
action is trivial, contradicting faithfulness once `X` is connected (by the rigidity I.5.4 of file 11: an étale
`Y`-automorphism that agrees with the identity on a stalk agrees with the identity on the connected component). For the
"`G = Aut_Y(X)`" statement: any `Y`-automorphism `u` agrees, at every `x`, with some `s ∈ G` (by V.1.3 (ii) on geometric
fibres: the orbit is a single `G`-orbit), and rigidity again forces `u = s` globally.

### V.2.5 — Counterexamples to V.2.4 without the hypotheses

<!-- source: V.2.5 -->

_This remark says: both hypotheses (`X` connected, `G` faithful) are essential. If we drop "faithful", obviously inertia
matters less; if we drop "connected", we can have trivial-quotient cases with plenty of inertia._

**Remark.** The faithfulness hypothesis is essential. The connectedness hypothesis is essential too: take `X = Y × E`
for a finite set `E` with `G` acting on `E` (e.g. `G` = permutations of `E`). Then `(Y × E) / G = Y × (E / G) = Y`, and
`X` is étale over `Y`. The inertia of a point `(y, e) ∈ Y × E` is `Stab_G(e)`, which can be non-trivial. Yet `X → Y` is
étale. The reason V.2.4 fails: `X` is not connected (it has `|E|` connected components if `Y` is connected), so the
rigidity argument that powers "⟸" cannot conclude faithfulness from triviality of inertia.

A second consequence of the `Y × E` example: taking `G ⊊ Sym(E)` transitive on `E` exhibits a `Y`-automorphism of `X`
not coming from any `s ∈ G` — for instance an element of `Sym(E) \ G` acting permutationally on the components.

A **trivial** prescheme with right `G`-action over `Y` is one isomorphic to `Y × G` with `G` acting by right
translations. Triviality is the local model: a principal covering looks locally (after base change) like `Y × G`.

The transition to _principal coverings_ is the algebraic analogue of "Galois cover with deck group `G`":

### V.2.6 — Principal coverings: four equivalent conditions

<!-- source: V.2.6 -->

_This theorem says: there are **four equivalent ways** to characterise an algebraic Galois cover with group `G`. Two are
geometric (finite + trivial inertia + the right quotient; formal-principal-homogeneous + faithfully flat quasi-compact);
two are existence-of-trivialisation (becomes trivial after a fpqc base change; becomes trivial after a finite étale
surjective base change)._

**Theorem.** Let `Y` be a locally noetherian prescheme, and let `X` be a `Y`-prescheme with a finite group `G` acting on
the right by `Y`-automorphisms. The following are equivalent:

1. `X` is finite over `Y`, `Y = X / G`, and the inertia groups `G_i(x)` are trivial for every `x ∈ X`.
1. There exists a faithfully flat quasi-compact base change `Y₁ → Y` such that `X₁ = X ×_Y Y₁` is **trivial** as a
    `Y₁`-prescheme with operators (i.e. isomorphic to `Y₁ × G`).
1. As in (ii), but with `Y₁ → Y` finite étale and surjective.
1. `X` is **formally principal homogeneous** under `G_Y`, and faithfully flat and quasi-compact over `Y`.

**Proof of (i) ⟹ (iii).** Take `Y₁ = X`. Then `X₁ = X ×_Y X`, and the morphism `X → Y` is finite étale by V.2.3.
Trivialisation follows from the corollary V.2.7 below.

**(iii) ⟹ (ii)** is trivial.

**(ii) ⟹ (i).** The properties listed in (i) — finite over `Y`, quotient `Y`, trivial inertia — are all _invariant under
faithfully flat quasi-compact descent_. (For finiteness: cf. Grothendieck's Bourbaki seminar 190, that is,
[`bourbaki-sem-190`](appendix-black-boxes.md). For inertia: V.2.1. For the quotient: a converse to V.1.9 in the
faithfully flat setting.) The categorical framework that organises these descent statements — fibred categories,
cleavages, the descent isomorphism — is developed in files 34–38; see file 38 §VI.12 for the abstract identity that
`bourbaki-sem-190` is a geometric specialisation of.

**(i) ⟺ (iv).** "Formally principal homogeneous" means the canonical morphism `X ×_Y G_Y → X ×_Y X` whose components are
the projection and the action map is an _isomorphism_. Combine with "faithfully flat and quasi-compact" — this is the
condition fpqc-trivialisation of (ii) viewed in self-image.

This is the principal definition of an algebraic Galois cover.

### V.2.7 — A section trivialises

<!-- source: V.2.7 -->

_This corollary says: under the conditions of V.2.6 (i), if `X` admits a section over `Y`, then `X` is *trivial* as a
space with operators — isomorphic to `Y × G`._

**Corollary.** If V.2.6 (i) holds and `X` admits a section `s : Y → X`, then `X` is a trivial space with operators, i.e.

```text
X  ≅  Y × G,
```

with the standard right action of `G` by translations on the factor `G`.

**Proof.** The section `s` together with the action defines a morphism `Y × G → X`, `(y, g) ↦ s(y) · g`, which is `G`-
equivariant. It is **surjective** (because `G` acts transitively on each fibre by V.1.3 (ii)), **injective** (because
the inertia is trivial), and a **local isomorphism** (by I.5.3 of file 11, since `X / Y` is étale by V.2.3). Hence an
isomorphism.

### V.2.8 — Definition of principal covering

<!-- source: V.2.8 -->

_This definition says: a `Y`-prescheme `X` with a `G`-action satisfying the equivalent V.2.6 conditions is a **principal
covering of `Y` with Galois group `G`** — the algebraic generalisation of a finite Galois étale cover._

**Definition.** A `Y`-prescheme `X` with a right group of operators `G` satisfying the equivalent conditions of V.2.6 is
called a **principal covering of `Y`, with Galois group `G`**.

A principal covering is the algebraic analogue of a Galois cover with deck transformation group `G` from file 28.

## Worked example: `Spec ℤ[√2] → Spec ℤ`

Take `A = ℤ[√2]`, `G = ℤ / 2 = ⟨ σ ⟩` with `σ(a + b √2) = a − b √2`. The invariant subring is `ℤ` itself, so

```text
Spec(ℤ[√2])  --p-->  Spec(ℤ),    G = ℤ / 2.
```

By V.1.1, `p` is integral, surjective, and the fibres are `G`-orbits.

**Compute the inertia at each prime `p ∈ ℤ`.**

- `p = 2`: the prime `(√2)` ⊂ ℤ[√2] is the unique prime over `(2)`, with residue field `𝔽₂`. The decomposition group is
    all of `G` (only one prime upstairs). The inertia group `G_i((√2))` is also `G` (since `σ` fixes the residue
    `𝔽₂ = ℤ[√2] / (√2)`). **Full inertia.** The map fails the étale criterion V.2.3 here.
- `p` odd, `p ≡ ±1 (mod 8)` (so `2` is a QR mod `p`): the prime `(p)` splits as `(p, √2 - r)(p, √2 + r)` for
    `r² ≡ 2 (mod p)`, giving two primes `𝔮₁, 𝔮₂`. The decomposition group of each is trivial (the orbit `{𝔮₁, 𝔮₂}` is
    the whole fibre, and `σ` swaps them). **Trivial inertia.**
- `p` odd, `p ≡ ±3 (mod 8)` (so `2` is a NR mod `p`): there is a unique prime `𝔮` over `(p)` with residue field
    `𝔽_{p²}`. The decomposition group is all of `G`. The inertia group is _trivial_ (since `σ` acts on `𝔽_{p²} / 𝔽_p` as
    the Frobenius generator, non-trivially). **Trivial inertia.**

So `Spec(ℤ[√2]) → Spec(ℤ)` is étale on `Spec(ℤ[1/2])` (V.2.3 applies), and _not_ étale at `(2)` (full inertia).
Restricted to the open `Spec(ℤ[1/2])`, the map is a **principal covering with Galois group `ℤ / 2`** by V.2.6.

This recovers, in the inertia language of V.2, the file 06 discussion of where `√2` "splits, is inert, or is ramified."
The arithmetic word **ramification** is exactly Grothendieck's **non-trivial inertia**.

## Worked example: `Spec ℂ[x, y] / (y² − x) → Spec ℂ[x]`

Take `B = ℂ[x]`, `A = ℂ[x, y] / (y² − x) = ℂ[y]` (using `x = y²`), `G = ℤ / 2 = ⟨ τ ⟩` with `τ(y) = −y`. Then
`B = A^G = ℂ[y²] = ℂ[x]`, so this is a `G`-quotient in the sense of V.1.1.

**At a generic point `x = α ∈ ℂ\^×` (`α ≠ 0`)**: there are two preimages `y = ±√α`, swapped by `τ`. Decomposition group
of each is trivial; inertia is trivial. The morphism `Spec(A) → Spec(B)` is étale at these points by V.2.3.

**At the origin `x = 0`**: the unique preimage is `y = 0`. Decomposition group is all of `G`. Residue field at `(y) ⊂ A`
is `ℂ`, and `τ` fixes `ℂ` (it acts only on the prime element `y`). Hence **full inertia**: `G_i((y)) = G`. The morphism
fails to be étale at `(y)`. This is the **branch point**.

Restricted to `Spec(ℂ[x, x⁻¹])`, the morphism is a principal covering with Galois group `ℤ / 2`. The branch at `x = 0`
is the algebraic shadow of the topological ramification of the square-root map `√ : ℂ \ {0} → ℂ \ {0}`. The algebraic
fundamental group of `ℂ \ {0}` is, again, the profinite-completion `ℤ̂` of file 28's `π₁^top(S¹) = ℤ`.

## What this prepares

File 31 (= V.3, V.4) verifies the categorical axioms (G1)–(G6) for the category of finite étale coverings of a connected
locally noetherian base, then proves the abstract Galois theorem V.4.1. The principal-covering picture of V.2.6 is
exactly the algebraic version of "Galois cover" that the abstract theorem will identify with cosets `π / U` for open
subgroups `U ⊂ π`. File 33 (= V.7) closes the loop: the étale fundamental group `π₁(S, a)` is constructed as `Aut(F)`
for the fibre functor `F` on the category of finite étale coverings of `S`, and principal coverings correspond to
**normal** open subgroups of `π₁`.
