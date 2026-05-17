# Exposé VI §§8–10 (gentle): pseudofunctors, split categories, and the dual story

## What this file is about

A cleavage on a fibred category packages its pull-back rule into an assignment: each base map gets an explicit inverse
image, and composed maps get an isomorphism between the composed inverse images. Read in the other direction, the same
data is a rule that hands a category to each base object and a comparison map between categories to each base map,
satisfying a coherence law. This second view is older and lighter — it speaks the language of functors, with one
controlled relaxation. Pinning down the dictionary between the two views, and showing it really is a dictionary, is the
substantive content here.

Tighten the comparison maps to identities and the relaxation goes away. The category-valued rule becomes an honest
strict functor of the base. Categories arising this way are split, and the case is clean but rare in geometry — most
natural pull-backs only agree up to canonical isomorphism, not on the nose. Reverse the direction of pull-back instead
and one gets push-forward — the dual story of co-fibred categories. When both directions exist and are adjoint, the
structure is bi-fibred, and the prototypical example is the pair of inverse-image and direct-image functors on
quasi-coherent sheaves over a scheme.

## Opening: cleavages reconstructed from pseudofunctors

File 36 §VI.7 turned a fibred category with a chosen cleavage into a coherent system of inverse-image functors
`(f^*, c_{f, g})` satisfying the pentagon. §VI.8 reverses the construction: given such data — a **pseudofunctor**
`ϕ : ℰ° → Cat` in the sense of
[file 34 Module C](34-sites-sheaves-and-pseudofunctors-gentle.md#module-c-pseudofunctors-cat-and-the-coherence-pentagon)
— we recover a cloven category over `ℰ`. The two operations are mutually inverse, in the (somewhat technical) sense that
they extend to an _equivalence of 2-categories_ between cloven `ℰ`-categories and normalised pseudofunctors `ℰ° → Cat`.

§VI.9 then isolates the special case where the coherence isomorphisms `c_{f, g}` are identities: a **split category**.
These are the cloven categories arising from honest functors `ℰ° → Cat` (no 2-cells), which is the simplest case but
rare in geometry. Some fibred categories admit a unique split form (when fibres are rigid, VI.9 closing remark); most do
not, because strictification fails.

§VI.10 dualises: replace "inverse image" by "direct image" and get **co-fibred**, **bi-fibred** (when both) categories.
The geometric instance is `(f^*, f_*)` adjoint pairs for quasi-coherent sheaves (file 17), which gives a bi-fibred
category over `(Sch / S₀)`.

The arc from §VI.6 to §VI.10:

```text
fibred  ⟷  cloven (with coherence)  ⟷  pseudofunctor  ⟷  split  ⟸  bi-fibred
                 §VI.7                       §VI.8         §VI.9       §VI.10
```

§VI.10 is independent of §VI.8–9 (one can dualise any of the preceding without touching pseudofunctorial reformulation),
and we treat it last because the adjoint-pair perspective of bi-fibred categories is the cleanest geometric upshot of
the framework.

## §VI.8 Cloven category from a pseudofunctor

<!-- source: VI.8 -->

*This section says: every normalised pseudofunctor `ϕ : ℰ° → Cat` defines a cloven category `ℱ*ϕ`over`ℰ`whose fibres are
canonically isomorphic to the values`ϕ(S)`. The construction is inverse to the one of §VI.7. The two together establish
a bijection (extending to a 2-equivalence) between normalised cloven categories over `ℰ`and normalised
pseudofunctors`ℰ° → Cat`.*

> **In quasi-coherent modules.** The pseudofunctor side of the dictionary is the one Hartshorne or Vakil writes when
> they say "pullback along `f`": the assignment `S ↦ QCoh(S)`, `f ↦ f^*`, equipped with the canonical iso
> `g^* f^* ≃ (fg)^*` of quasi-coherent pullback. The pentagon identity is the routine compatibility that
> `h^* g^* f^* ≃ (fgh)^*` agrees no matter which two factors one associates first; in QCoh it is true on the nose for
> the pullback formula `f^* M = f^{-1}M ⊗_{f^{-1}𝒪_S} 𝒪_T`. The cloven category recovered from this pseudofunctor is the
> QCoh fibred category of §VI.7's running example.

### The construction

Fix a normalised pseudofunctor `ϕ : ℰ° → Cat` with data:

- a category `ϕ(S)` for each `S ∈ Ob ℰ`;
- a functor `f^* : ϕ(S) → ϕ(T)` for each `f : T → S`, with `(id_S)^* = id_{ϕ(S)}` strictly;
- a natural isomorphism `c_{f, g} : g^* f^* ⟹ (fg)^* : ϕ(R) → ϕ(U)` for each composable `U --g--> T --f--> R`,
    satisfying the pentagon identity B) of
    [§VI.7.4](36-expose-vi-6-7-fibred-categories-and-cleavages-gentle.md#vi74--coherence-identities-a-and-b) and the
    unit identities A′) (normalisation).

Define the _associated cloven category_ `ℱ = ℱ_ϕ` as follows.

**Objects** of `ℱ`:

```text
Ob(ℱ)  =  ⨆_{S ∈ Ob ℰ} Ob(ϕ(S))
```

— pairs `(S, ξ)` with `S ∈ Ob ℰ` and `ξ ∈ Ob ϕ(S)`. Write `ξ̄ = (S, ξ)` (so `S` is determined by `ξ̄`).

**Morphisms** of `ℱ` from `η̄ = (T, η)` to `ξ̄ = (S, ξ)` over a fixed `f : T → S`:

```text
h_f(η̄, ξ̄)  =  Hom_{ϕ(T)}(η, f^*(ξ)).
```

**All morphisms** from `η̄` to `ξ̄` (varying the base map `f`):

```text
h(η̄, ξ̄)  =  ⨆_{f : T → S} h_f(η̄, ξ̄).
```

(The disjoint union is necessary: two arrows of `ℰ` from `T` to `S` may be different but give the same `f^*`.)

**Composition.** For composable `(η̄, ξ̄)` and`(ζ̄, η̄)` over `f : T → S` and `g : U → T`, the
composition`h_f(η̄, ξ̄) × h_g(ζ̄, η̄) → h_{fg}(ζ̄, ξ̄)` is

```text
(u, v)  ↦  c_{f, g}(ξ)  ·  g^*(u)  ·  v,
```

i.e., the composite

```text
ζ  --v-->  g^*(η)  --g^*(u)-->  g^* f^*(ξ)  --c_{f, g}(ξ)-->  (fg)^*(ξ).
```

Note that `c_{f, g}(ξ)` is the coherence isomorphism evaluated at`ξ`.

**Identity.** For `ξ̄ = (S, ξ)`, the identity element of`Hom_{ϕ(S)}(ξ, ξ) = h_{id_S}(ξ̄, ξ̄)` (using normalisation
`(id_S)^* = id_{ϕ(S)}`) is the identity morphism of `ξ̄` in`ℱ`.

**Projection** `p : ℱ → ℰ` sends`ξ̄ = (S, ξ) ↦ S` and a morphism in `h_f(η̄, ξ̄)` to `f`.

### Verification

The verification has six steps, all routine; we reproduce the two crucial ones (associativity of composition,
cartesianness of the canonical morphisms) and refer to Vistoli §3.1.3 for the remaining four.

**Step 1: Associativity.** For composable `V --h--> U --g--> T --f--> S`,
objects`ξ ∈ ϕ(S), η ∈ ϕ(T), ζ ∈ ϕ(U), τ ∈ ϕ(V)`, and morphisms

```text
u ∈ h_f(η̄, ξ̄)  =  Hom_{ϕ(T)}(η, f^*(ξ)),
v ∈ h_g(ζ̄, η̄)  =  Hom_{ϕ(U)}(ζ, g^*(η)),
w ∈ h_h(τ̄, ζ̄)  =  Hom_{ϕ(V)}(τ, h^*(ζ)),
```

we have `(u ∘ v) ∘ w = u ∘ (v ∘ w)` in`Hom_{ϕ(V)}(τ, (fgh)^*(ξ))`. Both sides are obtained by composing along the upper
/ lower contour of the diagram

```text
τ --w--> h^*(ζ) --h^*(v)--> h^*g^*(η) --h^*g^*(u)--> h^*g^*f^*(ξ) --h^*(c_{f, g}(ξ))--> h^*(fg)^*(ξ)
                                  \                       |  c_{g, h}(f^*(ξ))             |  c_{fg, h}(ξ)
                                   v ∘ w                  ↓                               ↓
                                                      (gh)^* (η) --(gh)^*(u)--> (gh)^* f^*(ξ) --c_{f, gh}(ξ)--> (fgh)^*(ξ).
```

The middle square commutes by naturality of `c_{g, h}`; the right square is exactly the pentagon B) of file 36 §VI.7.4.
So both contours agree. ∎

**Step 2: Cartesian transport morphisms.** For each `f : T → S` and each`ξ̄ = (S, ξ) ∈ Ob ℱ`, set `η̄ = (T, f^*(ξ))` and
let

```text
α_f(ξ̄)  ∈  h_f(η̄, ξ̄)
```

be the element corresponding to `id_{f^*(ξ)} ∈ Hom_{ϕ(T)}(f^*(ξ), f^*(ξ))`. We claim`α_f(ξ̄)` is a cartesian morphism
over `f`. For any `η̄' = (T, η')` and any`f`-morphism `u' : η̄' → ξ̄` in `ℱ`
(so`u' ∈ h_f(η̄', ξ̄) = Hom_{ϕ(T)}(η', f^_(ξ))`), the unique `T`-morphism `ū : η̄' → η̄` with`α_f(ξ̄) ∘ ū = u'` is
exactly `u'` itself, viewed in `Hom_{ϕ(T)}(η', f^_(ξ)) = h_{id_T}(η̄', η̄)`. (Use normalisation:`c_{f, id_T}(ξ̄) = id`
by A′).) ∎

The other steps verify:

1. The projection `p : ℱ → ℰ` is a functor; the bijection`h_f(η̄, ξ̄) ≅ Hom_f(η̄, ξ̄)` is the identity.
1. The fibres `ℱ_S` are canonically isomorphic to`ϕ(S)` via `(S, ξ) ↦ ξ`.
1. The chosen `α_f(ξ̄)`'s define a normalised cleavage of`ℱ → ℰ`.
1. The coherence isomorphisms `c_{f, g}` associated with this cleavage agree, under the iso of step 4, with the
    original`c_{f, g}` of `ϕ`.

### Grothendieck's axioms A′ and B

The pentagon B) of file 36 §VI.7.4 (= "the diagram of `c`'s commutes") and the unit conditions A′) of normalisation are
together what one needs to _define_ a pseudofunctor in the strict sense. SGA VI states them in the form

```text
A′)  c_{f, id_T}  =  id_{f^*}    and    c_{id_S, f}  =  id_{f^*},
B)   c_{f, gh}  ∘  (h^* * c_{g, h})    =    c_{fg, h}  ∘  (c_{f, g} * h^*).
```

Mac Lane's coherence theorem ([`mac-lane-coherence`](appendix-black-boxes.md#mac-lane-coherence)) guarantees that A′) +
B) imply _every_ coherence diagram commutes (e.g. the four-fold associator for composable quadruples gives, a priori,
two parallel pasting compositions of five `c`'s — they automatically agree). We use this freely without further comment.

### The bijection (cloven categories ↔ normalised pseudofunctors)

The construction of §VI.7 (cloven category → pseudofunctor) and the construction of §VI.8 (pseudofunctor → cloven
category) are mutually inverse, in the sense that:

- Starting from a normalised cloven `ℱ → ℰ`, applying §VI.7 gives a normalised pseudofunctor`ϕ_ℱ`, then applying §VI.8
    gives a normalised cloven `ℱ_{ϕ_ℱ} → ℰ` canonically isomorphic to the original `ℱ` as a cloven category.
- Starting from a normalised pseudofunctor `ϕ`, applying §VI.8 then §VI.7 gives a normalised pseudofunctor`ϕ_{ℱ*ϕ}`
    isomorphic to `ϕ` as a pseudofunctor.

The precise statement is that the two assignments extend to quasi-inverse 2-functors between the 2-category `Cleav(ℰ)`
of normalised cloven`ℰ`-categories (with appropriately-defined 1-cells and 2-cells) and the 2-category `PsFun(ℰ°, Cat)`
of normalised pseudofunctors. We name this for context and refer to
[`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained) §3.1.3–§3.1.4 for the precise statement and its
verification.

The slogan: **a fibred category with a chosen cleavage _is_ the same data as a normalised pseudofunctor `ℰ° → Cat`**.
The fibre-and-pull-back perspective and the value-and-coherence perspective are interconvertible. SGA VI uses both, and
so will files 38 and (in the future) Exposé VIII.

## §VI.9 Split categories

<!-- source: VI.9 -->

_This section says: a cloven category whose coherence isomorphisms `c_{f, g}` are _identities_ (rather than just
isomorphisms) is called **split**. Equivalently, the cleavage arises from an honest functor`ϕ \: ℰ° → Cat` (no 2-cells).
Some fibred categories admit a splitting, some do not; an obstruction class lives in `H²(E, G)` when the relevant data
come from a group extension. Fibred categories with rigid fibres (no non-trivial automorphisms) always admit a unique
splitting._

### Definition

A cleavage of an `ℰ`-category `ℱ` is a **splitting** if every coherence isomorphism`c_{f, g}` is the identity:

```text
(fg)^*  =  g^* f^*    (strict equality of functors),
c_{f, g}  =  id_{(fg)^*}.
```

Equivalently, in transport-morphism terms (file 36 §VI.7.1): the set `K ⊂ Fl(ℱ)` of transport morphisms is closed under
composition.

A category `ℱ → ℰ` with a chosen splitting is a **split`ℰ`-category**.

The category of split `ℰ`-categories is equivalent to`Hom(ℰ°, Cat)` — honest functors, with no pseudo-prefix. Every
split category is a fortiori cloven (and a fortiori prefibred, and is automatically fibred since the identity 2-cell is
an isomorphism).

### Existence of a splitting

A fibred `ℱ` admits a splitting iff its coherence data can be chosen identically. This may fail.

**Failure example: group extensions.** Take `ℰ` and`ℱ` to be one-object groupoids defined by groups `E` and `F`,
and`p : F → E` a surjective group homomorphism (so `ℱ` is fibred over `ℰ`, file 36 §VI.6.1). Let`G = ker p`. The set of
cleavages of `ℱ` over `ℰ` is in bijection with the set of _set-theoretic sections_`s : E → F` with `p ∘ s = id_E` —
i.e., systems of representatives for `F / G`. A cleavage is a splitting iff`s` is a _group homomorphism_. So splittings
exist iff the group extension

```text
1 → G → F → E → 1
```

splits as an exact sequence of groups. When `G` is abelian, the obstruction lives in`H²(E, G)` (group cohomology, with
`E` acting on `G` by inner automorphisms). For non-trivial extensions this`H²` class is non-zero, and the splitting
fails.

**Success: rigid fibres.** Suppose `ℱ` is fibred over`ℰ` and each fibre `ℱ_S` is **rigid** (every object of `ℱ_S` has
only the identity automorphism). Then`ℱ` admits a _unique_ splitting.

_Reason_: by VI.6.2, replacing `ℱ` by an`ℰ`-equivalent category does not change the splitting question, and one can
replace `ℱ_S` by the equivalent rigid-and-reduced category (where two isomorphic objects are equal). In a
rigid-and-reduced category, every isomorphism between functors `H → ℱ_S` is the identity, so the inverse-image
functors`f^*` are determined uniquely (no 2-cells to pin down). ∎

### Strictification

Even when no splitting exists, every pseudofunctor is _equivalent_ to a strict 2-functor, after replacing the values
with equivalent categories. Precisely: every pseudofunctor `ϕ : ℰ° → Cat` is equivalent (in the 2-category of
pseudofunctors) to a strict 2-functor`ϕ̃ : ℰ° → Cat`. Equivalently, every fibred category is `ℰ`-equivalent to a split
category.

We name this as the appendix slug [`strictification`](appendix-black-boxes.md#strictification). The result is the
categorical-coherence half of Mac Lane's coherence story; for a modern treatment see Power, _A general coherence
result_, or Riehl, _Categorical Homotopy Theory_ §10.

### Why splittings still matter when strictification exists

The strictification is constructive but _enlarges_ the source data. For the QCoh pseudofunctor (file 34 Module C example
3), the strictification replaces `QCoh(S)` by a different (but equivalent) category — typically, a category of "global
modules with a chosen pull-back compatibility for every base morphism". Geometrically, this loses the simplicity of
"quasi-coherent sheaf on`S`". Working with the un-strictified pseudofunctor and tracking the coherence isomorphisms
`c_{f, g}` is therefore preferable in practice; the splitting-versus-cleavage choice is philosophical, not just
technical.

This is one reason SGA VI develops _both_ the abstract fibred formalism (no choice required) _and_ the
cloven/pseudofunctorial form (choice exposed): the abstract form is canonical, the cloven form is computable, and the
relation between them is a 2-equivalence.

## §VI.10 Co-fibred and bi-fibred categories

<!-- source: VI.10 -->

_This section says: dualise everything. Replace "inverse image" by "direct image" and "cartesian morphism" by
**co-cartesian morphism**. An `ℰ`-category is **co-fibred** if every base morphism admits direct images and they compose
well. **Bi-fibred** = both fibred and co-fibred; in this case `(f^*, f_*)` is an adjoint pair on each fibre._

### Definitions

Let `ℱ` be an`ℰ`-category with projection`p`. A morphism `α : η → ξ` in `ℱ` over`f : T → S` is **co-cartesian** if for
every `ξ' ∈ Ob ℱ_S` the post-composition map

```text
α^*  :  Hom_S(ξ, ξ')  ⟶  Hom_f(η, ξ'),    u ↦ u ∘ α,
```

is bijective. Equivalently: `α` is cartesian for`ℱ° → ℰ°` (the opposite-category formulation). The dual notion, **direct
image** of `η` along `f`, is any`(ξ, α)` with `α` co-cartesian over `f`. We write`f_*(η)` for the direct image (when it
exists), to distinguish from the inverse image `f^*`.

`ℱ` is **co-prefibred** over`ℰ` if every `f : T → S` admits direct images for every `η ∈ Ob ℱ_T`.`ℱ` is **co-fibred** if
it is co-prefibred and composites of co-cartesian morphisms are co-cartesian. `ℱ` is **bi-fibred** if it is both fibred
and co-fibred.

### The adjoint-pair perspective

When both `f^*` and`f_*` exist (i.e., `ℱ` is prefibred and co-prefibred), the universal properties give canonical
isomorphisms

```text
Hom_S(f_*(η), ξ)  ≅  Hom_f(η, ξ)  ≅  Hom_T(η, f^*(ξ)),
```

natural in `(η, ξ) ∈ ℱ_T° × ℱ_S`. Reading the outer two:`f__` is **left adjoint** to `f^_`.

```text
f_*  :  ℱ_T  ⇄  ℱ_S  :  f^*,    f_* ⊣ f^*.
```

This is the central geometric instance: the pair `(f^*, f_*)` of inverse and direct images for quasi-coherent sheaves on
schemes (file 17) are an adjoint pair, and`(QCoh(–), pull-back, push- forward)` is a bi-fibred category over
`(Sch / S₀)`.

### Composability of the coherence isomorphisms

For composable `g : U → T` and`f : T → S`, the cleavage provides

```text
c_{f, g}  :  g^* f^*  ⟹  (fg)^*    (file 36 §VI.7),
c^{f, g}  :  (fg)_*  ⟹  f_* g_*    (the dual in the co-fibred case).
```

If `(f^* ⊣ f_*)` and`(g^_ ⊣ g__)` are read as adjoint pairs, then `(g^* f^*) ⊣ (f_* g_*)` as composite adjoint pairs
(left adjoints compose with right adjoints in opposite order). Composing with `((fg)^_ ⊣ (fg)__)`, we see that`c_{f, g}`
and `c^{f, g}` are _adjoint_ natural transformations. Hence one is an isomorphism iff the other is, and:

### VI.10.1 — Bi-fibred ⟺ prefibred + co-prefibred + (one of) the c's invertible

<!-- source: VI.10.1 -->

_This result says: a prefibred and co-prefibred `ℰ`-category is fibred iff it is co-fibred. Equivalently: the existence
of all inverse and direct images automatically forces both Fib II's (the fibred and the co-fibred), via the adjoint
relation`f__ ⊣ f^_`._

**Proposition.** Suppose `ℱ` is prefibred and co-prefibred over`ℰ`. Then `ℱ` is fibred iff it is co-fibred.

**Proof.** Use the adjointness of `c_{f, g}` and`c^{f, g}` described above. Fib II is the assertion that every
`c_{f, g}` is an iso (file 36 §VI.7.2); the dual Fib II is that every `c^{f, g}` is an iso. Adjoints share
invertibility, so the two conditions are equivalent. ∎

This is the structural cleanest statement of bi-fibredness: it is automatic given prefibredness + co-prefibredness + the
existence of the adjoint pair. In particular, _every_ situation where we have _both_ well-defined inverse and direct
images of some kind gives a bi-fibred category.

## Worked example: direct image in `Ar(Sch / S₀)`

Continue the running example. Take `ℰ = (Sch / S₀)` and`ℱ = Ar(ℰ)`, the arrow category (file 35, file 36 worked
examples). We saw that `ℱ` is fibred over `ℰ` via the **target** projection.

**Direct image: composition of arrows.** For `f : Y' → Y` in`ℰ` and `(X → Y') ∈ Ob ℱ_{Y'}` (a `Y'`-scheme), the direct
image`f_*(X → Y')` is

```text
f_*(X → Y')  =  (X --(f ∘ –)--> Y),
```

— composing the structure morphism `X → Y'` with`f : Y' → Y` gives a `Y`-scheme. The co-cartesian morphism

```text
(X → Y')  --(id_X, f)-->  (X → Y)
```

is the square with vertical maps `id_X` and`f`.

**Verification of co-cartesianness.** For any `(X' → Y) ∈ Ob ℱ_Y` and any`f`-morphism `(u, f) : (X → Y') → (X' → Y)` (a
square), there is a unique `Y`-morphism`(u, id_Y) : (X → Y) → (X' → Y)` — namely `u` itself — such that the composite
`(u, id_Y) ∘ (id_X, f) = (u, f)`. ∎

**Bi-fibredness.** `Ar(ℰ)` is **bi-fibred** over`ℰ`: it is fibred (file 36 worked example) and co-fibred (just
verified). The adjoint pair `f_* ⊣ f^*` on each fibre is

```text
(Sch / Y')  ⇄  (Sch / Y),
```

with `f_*(X → Y') = (X → Y' → Y)` (composition) and`f^*(X → Y) = (X ×_Y Y' → Y')` (base change). The classical "base
change is right adjoint to composition" statement for slice categories becomes a special case of VI.10.1.

**Cohomological side.** The geometric specialisation we will care about in Exposé VIII: when `ℰ = (Sch / S₀)`
and`ℱ_S = QCoh(S)`, the inverse image `f^*` is module pull-back and the direct image `f*_` is push-forward. The
adjunction`f^_ ⊣ f_*` (now for *quasi-coherent sheaves*, with `f^*` left adjoint, the opposite direction from the
arrow-category example) is the classical adjunction of file 03 §3.4. This gives `QCoh` as a bi-fibred category
over`(Sch / S₀)` — the central example whose descent statements live in Exposé VIII.

## Continuing on

File 38 closes Exposé VI with the example library (§VI.11) and the **descent isomorphism** (§VI.12.1). The descent
isomorphism is the categorical identity that makes the entire framework pay off:

> A global `ℰ`-functor `F : ℱ → 𝒞` on a cloven`ℰ`-category`ℱ` is determined by its fibre-wise restrictions
> `F_S = F|_{ℱ_S}` together with coherence data `(φ_f)_{f ∈ Fl(ℰ)}` satisfying a normalisation and a cocycle identity.

Specialising to `ℱ_S = QCoh(S)` and`𝒞 =` Set / Mod gives "global quasi-coherent sheaf assignment = local data + gluing"
— a baby version of fpqc descent. The _strong_ form of this statement, _for an effective fpqc cover_, is the central
theorem of Exposé VIII; we name it but defer its proof.

The §VI.10 example (`Ar(ℰ)` as a bi-fibred category) and the QCoh pseudofunctor (file 34 Module C) are the two instances
we reuse in file 38.
