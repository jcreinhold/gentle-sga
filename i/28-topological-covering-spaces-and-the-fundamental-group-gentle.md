# Topological covering spaces and the fundamental group

## What this file is about

Wrap a rubber band around a doughnut and there is no way to slide it off without breaking the doughnut. Wrap it around
a ball and it slips free. The difference is captured by a single object attached to each shape: a group whose elements
are loops that cannot be pulled tight, considered up to continuous deformation. This is the fundamental group, the
oldest precise sense in which a space has a shape distinct from its size.

A second picture stacks above the first. Some shapes admit unbranched covers — neat stacks of identical sheets laid
over the original. The covers of a space are governed by its fundamental group in a tight and surprising way. The rest
of this book will rebuild both pictures in algebra, for objects that have no points and no loops. This file states the
geometric original they will be made to recover.

## Why this file exists

Files 31–33 generalise topological covering theory and the topological fundamental group to schemes via Galois
categories. The gentle reader is owed the geometric picture before the algebra. This file collects, in working detail,
the parts of covering-space theory that the rewrite of Exposé V mirrors: covering maps, the fundamental group
`π₁^top(B, b₀)`, the universal cover, the Galois correspondence between subgroups of `π₁^top` and connected coverings,
and — for the algebraic analogy specifically — the **profinite completion** `π̂₁^top(B, b₀)` that classifies _finite_
coverings.

A reader fluent in the algebraic-topology textbook treatment (Hatcher Ch. 1; May Ch. 3) can skip this file entirely. A
reader who wants only Exposés I–IV can also skip it. A reader who wants Exposé V should read it, lightly, before files
30–33: each algebraic theorem in the rewrite has a topological prototype displayed here.

## Covering maps

A continuous surjection `p : E → B` is a **covering map** when every point `b ∈ B` has an open neighborhood `U ⊆ B` such
that the inverse image splits as a disjoint union of homeomorphic copies of `U`:

```text
p⁻¹(U) ≅ ⨆_{d ∈ D} U_d,    each p|_{U_d} : U_d → U a homeomorphism,
```

where `D` is some discrete set called the **fibre over `b`**. The fibres of a covering are discrete, the local picture
is trivial (`U × D`), and the global picture is a stack of sheets that twists over `B` in a way controlled by the
topology of `B`.

The simplest non-trivial example is the exponential map

```text
p : ℝ → S¹,    p(t) = e^{2πi t},
```

with discrete fibre `ℤ`. Every connected component of `p⁻¹(U)` for a small enough open arc `U ⊆ S¹` maps
homeomorphically onto `U`. A second example: the squaring map `q : S¹ → S¹`, `z ↦ z²`, with discrete fibre of
cardinality `2`. The exponential example is **infinite-sheeted**; the squaring example is **finite-sheeted of degree
`2`**.

A covering is **finite** when every fibre is finite. (For `B` connected, all fibres then have the same cardinality.)
Finite coverings are the topological analogue of finite étale morphisms.

#### Aside (algebraic geometry analogy).

_Skip if you have not read file 04._ A covering `p : E → B` of topological spaces is the geometric prototype of an étale
morphism `f : X → Y` of schemes. The "local triviality" `p⁻¹(U) ≅ U × D` is the topological shadow of the local form
theorem I.7.6 (file 11), and the discrete fibre `D` is the topological shadow of the étale fibre
`Spec(κ(y)^{sep, finite})`. File 04's split-into-fields description of the étale fibre is the algebraic version of "the
fibre of `p` is a discrete set."

## Lifting paths and homotopies

The fundamental theorem about coverings is **path lifting**: if `p : E → B` is a covering, `e₀ ∈ E`, and
`γ : [0, 1] → B` is a path with `γ(0) = p(e₀)`, then there exists a _unique_ path `γ̃ : [0, 1] → E` with `γ̃(0) = e₀`
and `p ∘ γ̃ = γ`.

The corresponding **homotopy lifting** holds: a homotopy `H : [0, 1] × [0, 1] → B` of paths in `B`, together with a lift
`γ̃₀` of one boundary path, lifts uniquely to a homotopy in `E`. Concretely, two paths `γ`, `γ′ : [0, 1] → B` from `b₀`
to `b₁` that are homotopic (rel endpoints) lift to paths `γ̃`, `γ̃′ : [0, 1] → E` with the _same_ endpoint
`γ̃(1) = γ̃′(1)` over `b₁`, provided they start at the same `e₀` over `b₀`.

This last sentence is the engine. It says:

```text
Two homotopic loops at b₀ in B lift to two paths in E with
the same terminal point, regardless of starting point.
```

So a loop `γ` at `b₀` defines a permutation of the fibre `p⁻¹(b₀)`: each `e ∈ p⁻¹(b₀)` lifts the loop to a path ending
at some `γ ⋅ e ∈ p⁻¹(b₀)`. This permutation depends only on the _homotopy class_ of `γ`. In symbols,

```text
π₁^top(B, b₀)   ⟶   Sym(p⁻¹(b₀)),    [γ] ↦ (e ↦ γ ⋅ e),
```

is a group homomorphism — the **monodromy representation** of `p` at `b₀`.

## The fundamental group `π₁^top(B, b₀)`

Pick a base point `b₀ ∈ B`. A **loop** at `b₀` is a continuous map `γ : [0, 1] → B` with `γ(0) = γ(1) = b₀`. Two loops
`γ`, `γ′` are **homotopic rel endpoints** if there is a continuous `H : [0, 1] × [0, 1] → B` with

```text
H(0, t) = γ(t),    H(1, t) = γ′(t),
H(s, 0) = H(s, 1) = b₀    for every s.
```

The set of homotopy classes of loops at `b₀` is the **fundamental group** of `B` at `b₀`, denoted `π₁^top(B, b₀)`. The
group operation is concatenation: `[γ] ⋅ [γ′] := [γ * γ′]`, where

```text
(γ * γ′)(t) =  γ(2t)         for 0 ≤ t ≤ 1/2,
              γ′(2t − 1)    for 1/2 ≤ t ≤ 1,
```

with identity the constant loop at `b₀` and inverse `[γ]⁻¹ := [γ̄]`, where `γ̄(t) = γ(1 − t)` is the loop run backwards.

A space `B` is **simply connected** when `π₁^top(B, b₀) = 1`.

### Examples

- `π₁^top(ℝⁿ) = 1`. Every loop in `ℝⁿ` shrinks to the constant loop along straight lines.
- `π₁^top(S¹) = ℤ`. The "winding number" of a loop computes its homotopy class. The generator is the loop
    `t ↦ e^{2πi t}` going once counterclockwise.
- `π₁^top(ℂ × {0}) = ℤ`. Same as `S¹`, since `ℂ × {0}` deformation- retracts to the unit circle.
- `π₁^top(S²) = 1`. Spheres of dimension `≥ 2` are simply connected.
- `π₁^top(S¹ ∨ S¹) = F₂`, the free group on two generators. Each generator is the loop going once around one of the two
    circles in the wedge.
- `π₁^top(S¹ × S¹) = ℤ × ℤ`. The torus has two independent loops, the meridian and the longitude, and they commute.

The **change of base point** is harmless when `B` is path- connected: any path `α` from `b₀` to `b₁` defines a group
isomorphism `α_* : π₁^top(B, b₀) → π₁^top(B, b₁)` by `[γ] ↦ [ᾱ * γ * α]`. The isomorphism depends on `[α]` up to inner
automorphism. We will write `π₁^top(B)` when the base point is inessential, but every concrete computation lives at a
chosen base point.

## The universal cover

Suppose `B` is connected, locally arcwise connected, and locally simply connected — three mild conditions satisfied by
every manifold and every CW complex. Then `B` admits a **universal cover** `p̃ : B̃ → B`, characterised by `B̃` simply
connected. The universal cover dominates every connected cover of `B`: if `p : E → B` is connected, there is a covering
map `q : B̃ → E` with `p ∘ q = p̃`.

The universal cover supports an action of the **deck transformation group** `Aut(B̃ / B)` of homeomorphisms
`φ : B̃ → B̃` with `p̃ ∘ φ = p̃`. The fundamental theorem of covering theory identifies it with the fundamental group:

```text
Aut(B̃ / B)  ≅  π₁^top(B, b₀).
```

The isomorphism is constructive: pick any lift `b̃₀ ∈ p̃⁻¹(b₀)`; each loop `γ` at `b₀` lifts to a path `γ̃` from `b̃₀`
to some other point `γ̃(1) ∈ p̃⁻¹(b₀)`, and the deck transformation sending `b̃₀ ↦ γ̃(1)` is the image of `[γ]`.

For `B = S¹`: the universal cover is `ℝ`, and the deck group is `ℤ` acting by integer translations. Match:
`π₁^top(S¹) = ℤ`.

For `B = S¹ ∨ S¹`: the universal cover is the infinite 4-valent tree, and the deck group is `F₂` acting by graph
automorphisms.

## The Galois correspondence between subgroups and coverings

Once the universal cover exists, every connected covering of `B` arises as a quotient of the universal cover by a
subgroup of `π₁^top(B, b₀)`. This is the [**topological covering-space classification**](appendix-black-boxes.md)
(appendix slug `topological-covering-space-classification`):

```text
{ connected coverings of B, up to iso }
   ≃   { subgroups H ⊆ π₁^top(B, b₀), up to conjugacy }
```

Concretely, given a subgroup `H ⊆ π = π₁^top(B, b₀)`, the quotient `B̃ / H` is a connected covering of `B` whose
fundamental group at `b̃₀` is `H`. The fibre over `b₀` is the coset space `π / H`, and `π` acts on the fibre by left
translation. **Subgroup ↔ cover** is the topological prototype of the **closed-subgroup ↔ Galois-category-object**
dictionary that file 32 will deliver.

A connected covering corresponds to a _subgroup_; an arbitrary (not necessarily connected) covering corresponds to a
finite `π`-set, i.e. a disjoint union of coset spaces `π / H_i`. This matches the slogan that `𝒞^top_B`, the category of
all coverings (or all finite coverings) of `B`, is equivalent to `π`-sets (or finite `π`-sets).

## Finite coverings and the profinite completion

The algebra of Exposé V will not see `π₁^top` directly — it will see only its **profinite completion**

```text
π̂₁^top(B, b₀)  :=  lim_{H ⊲ π, [π : H] < ∞} π / H,
```

the projective limit of all finite quotients. An open subgroup of `π̂₁^top` is, by definition, the preimage of a
subgroup of some finite quotient `π / H`; it is automatically of finite index in `π̂₁^top`, and corresponds via the
universal-cover construction to a _finite_ connected cover of `B`.

Restricting the equivalence above to finite coverings, we get:

```text
{ finite connected coverings of B, up to iso }
   ≃   { open subgroups of π̂₁^top(B, b₀), up to conjugacy }.
```

The category `𝒞^top_B` of finite coverings of `B` is equivalent to the category `𝒞(π̂₁^top)` of finite continuous
`π̂₁^top`-sets. This is the **topological main theorem** that file 31 will generalise to schemes.

### Examples of `π̂₁^top`

- `B = S¹`: `π₁ = ℤ`, `π̂₁ = ℤ̂ = lim_n ℤ / nℤ`. Finite covers of `S¹` are the `n`-th-power maps `S¹ → S¹`, `z ↦ zⁿ`,
    classified by the open subgroups `nℤ̂ ⊂ ℤ̂`.
- `B = ℂ \ {0}`: same as `S¹`, since `ℂ \ {0}` deformation- retracts to the unit circle. Finite covers:
    `ℂ \ {0} → ℂ \ {0}`, `z ↦ zⁿ`.
- `B = S¹ ∨ S¹`: `π₁ = F₂`, `π̂₁ = F̂₂`, the free profinite group on two generators. Finite covers correspond to open
    subgroups of `F̂₂`.
- `B = S¹ × S¹`: `π₁ = ℤ²`, `π̂₁ = ℤ̂²`. Finite covers of the torus are quotients by finite-index sublattices of `ℤ²`,
    all of which are again tori.

#### Aside (why profinite, not finite-index).

_Skip if you already know._ The quotient `ℤ / nℤ` is finite discrete, so already a topological group; but
`ℤ̂ = lim_n ℤ / nℤ` is not the same as `ℤ` itself, even as an abstract group. `ℤ̂` is uncountable, and contains `ℤ`
densely. The topology distinguishes them: open subgroups of `ℤ̂` are `nℤ̂` for `n ≥ 1`, all of finite index; subgroups
of _finite index_ in `ℤ` are also `nℤ`, but the profinite version pre-packages the projective limit relationship between
them. The relationship `Hom(Ĝ, Π) = Hom_cts(G, Π)` for any profinite `Π` (universal property of the profinite
completion) makes this precise: continuous homomorphisms from `G` to a profinite group factor through `Ĝ`.

## Galois (= regular) coverings

A connected covering `p : E → B` is **Galois** (or **regular**) when its deck transformation group `Aut(E / B)` acts
transitively on a — equivalently every — fibre. Equivalently, the subgroup `p_* π₁^top(E) ⊆ π₁^top(B)` is _normal_.

For a Galois cover, `Aut(E / B)` is canonically isomorphic to the quotient `π₁^top(B) / p_* π₁^top(E)`, the **Galois
group** of the cover.

For example, the squaring map `S¹ → S¹` is Galois with deck group `ℤ / 2ℤ` (acting by `z ↦ −z`). The universal cover
`ℝ → S¹` is Galois with deck group `ℤ`.

For a connected cover that is _not_ Galois, the deck group fails to act transitively — the fibre still admits a
`π₁^top`-action by monodromy, but the deck group sits inside the normaliser of the corresponding subgroup, not the whole
of `π₁^top`.

## What this prepares

File 30 (= V.1, V.2) introduces the algebraic analogue of deck- transformation groups: a finite group `G` acting on a
prescheme `X` by automorphisms, and the **inertia group** at fixed points. The condition "the inertia is trivial
everywhere" is V.2.3's characterisation of when the quotient is étale, and is the algebraic shadow of the topological
condition "the cover is unramified."

File 31 (= V.3, V.4) verifies axioms (G1)–(G6) for finite étale coverings of a connected base and proves the abstract
Galois theorem V.4.1: any category satisfying these axioms is equivalent to `𝒞(π)` for a profinite group `π`. This is
the algebraic generalisation of the topological main theorem `𝒞^top_B ≃ 𝒞(π̂₁^top)` displayed above.

File 32 (= V.5, V.6) develops the formalism — the **fundamental groupoid** (objects = fibre functors, the algebraic
version of "objects = base points"), the **fundamental pro-group**, and the dictionary between exact functors of Galois
categories and continuous group homomorphisms. The change-of- base-point isomorphism
`α_* : π₁^top(B, b₀) → π₁^top(B, b₁)` of the topological setting becomes the path-class isomorphism `π₁(S; a, a′)` of
V.7.

File 33 (= V.7) defines

```text
π₁(S, a)  :=  Aut(F_a),
```

where `S` is a connected locally noetherian scheme, `a` is a geometric point of `S`, and `F_a` is the fibre functor
"geometric points of `X` over `a`" on the category of finite étale coverings of `S`. The slogan: **the étale fundamental
group `π₁(S, a)` is to schemes as the profinite completion `π̂₁^top(B, b)` is to topological spaces**.
