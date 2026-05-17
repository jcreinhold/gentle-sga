# Exposé VI §§6–7 (gentle): fibred categories and cleavages

## What this file is about

A pull-back rule is supposed to do two things. It is supposed to exist — every map between base points should drag
fibres above one to fibres above the other. And it is supposed to compose well — dragging along a path of two steps
should give the same answer as dragging along the steps in turn. Spelling out each demand carefully separates them, and
the two demands turn out to be independent. The first can hold without the second. The first alone is enough to define
inverse images; the second is what makes them honest functors of the base.

Naming these two demands as axioms turns "category over a base" into a real structure. The weaker one alone gives a
prefibred category; both together give a fibred category. Once a fibred category has been singled out, one can ask for
something more: an explicit choice of inverse image for every base map, rather than just the assurance that one exists.
That choice is a cleavage. Cleavages make the framework concrete enough to compute with, but the choice is never
canonical. The looseness it introduces — a coherence isomorphism mediating composed pull-backs — is exactly the two-cell
that bridges abstract fibrations to the explicit functor-valued machinery the next file develops.

## Opening: from cartesian arrows to fibred structure

§5 (file 35) introduced the _property_ of being a cartesian morphism — the universal-property formulation of "pull-back
along `f`". §6 turns the property into _structure_:

- **Fib I.** Every morphism `f : T → S` of the base admits inverse images. (Equivalently: the inverse-image functor
    `f^* : ℱ_S → ℱ_T` exists.) An `ℰ`-category satisfying Fib I is **prefibred**.
- **Fib II.** Composites of cartesian morphisms are cartesian. A prefibred category satisfying Fib II is **fibred**.

The two axioms are independent. Fib I gives us the inverse-image functors; Fib II ensures they compose well — that
`(g f)^* ≅ f^* g^*` as functors `ℱ_R → ℱ_T` for composable `T → S → R`. Without Fib II we still have inverse-image
functors but no coherent way to identify "pull-back along the composite" with "successive pull-backs". The pentagon
coherence of file 34 Module C is exactly the 2-cell incarnation of "Fib II".

§7 then adds **structure-as-data**: a **cleavage** is an _explicit choice_ of inverse-image functor for every
`f ∈ Fl(ℰ)`, together with the chosen cartesian morphisms `α_f(ξ) : f^*(ξ) → ξ`. Every prefibred category admits a
cleavage (axiom of choice on objects); the cleavage is _not_ canonical. Once a cleavage is chosen, we can write down a
natural transformation `c_{f, g} : g^* f^* ⟹ (fg)^*` — the **coherence isomorphism** — and ask whether it is invertible.
_VI.7.2_: cloven `ℱ` is fibred iff every `c_{f, g}` is invertible. This is the bridge between "abstract fibred" (a
property of `ℱ → ℰ`) and "concrete cleaved" (an explicit pseudofunctor `ℰ° → Cat`).

We follow the source's order: §6 first (axioms and the properties they grant), §7 second (cleavages and coherence). The
worked example — the cleaved arrow category of file 35 — runs throughout.

## §VI.6 Fibred categories

<!-- source: VI.6 -->

### VI.6.1 — Definition: prefibred, fibred, fibred in groupoids

<!-- source: VI.6.1 -->

_This result says: an `ℰ`-category `ℱ → ℰ` is **prefibred** when every base morphism admits inverse images (Fib I), and
**fibred** when additionally composites of cartesian morphisms are cartesian (Fib II). It is **fibred in groupoids**
when every morphism of `ℱ` is cartesian — equivalently, when `ℱ` is fibred and every fibre `ℱ_S` is a groupoid._

**Definition.** Let `ℱ` be an `ℰ`-category, with projection `p : ℱ → ℰ`.

- `ℱ` is **prefibred over `ℰ`** if it satisfies:

    - **Fib I.** For every morphism `f : T → S` in `ℰ`, the inverse-image functor `f^* : ℱ_S → ℱ_T` exists (i.e., for
        every `ξ ∈ Ob ℱ_S`, there is a cartesian `f`-morphism `f^*(ξ) → ξ`).

- `ℱ` is **fibred over `ℰ`** (the projection `p` is **fibrant**) if it satisfies Fib I and:

    - **Fib II.** The composite of two cartesian morphisms is cartesian.

- `ℱ` is **fibred in groupoids over `ℰ`** if every morphism of `ℱ` is cartesian. Equivalently: `ℱ` is fibred and each
    fibre `ℱ_S` is a groupoid.

**Subcategory variants.** A subcategory `𝒢 ⊆ ℱ` is a **(pre)fibred subcategory** if it is itself (pre)fibred over `ℰ`
and the inclusion `𝒢 ↪ ℱ` is a cartesian functor. For _full_ subcategories, this reduces to: for every `f : T → S` and
every `ξ ∈ Ob 𝒢_S`, the inverse image `f^*_ℱ(ξ)` is `T`-isomorphic to an object of `𝒢_T`. (The full-subcategory case is
what most geometric examples will satisfy.)

**The cartesian sub-fibred-category.** Given a fibred `ℱ`, let `ℱ̃ ⊆ ℱ` be the subcategory with the same objects but
with only _cartesian_ morphisms (so `ℱ̃_S =` the **groupoid of fibre isomorphisms** of `ℱ_S`, since `S`-morphisms that
are also cartesian are exactly the `S`-isomorphisms; cf. file 35 §VI.5.1's "stability" property). Then `ℱ̃` is a fibred
subcategory of `ℱ`, and `Hom_{ℰ/-}(ℰ, ℱ̃) → Lim←(ℱ / ℰ)` is faithful (but in general not full).

**Example: extensions of groups.** Take `ℰ` and `ℱ` to be one-object groupoids defined by groups `E` and `F`, and the
projection `p : F → E` to be a group homomorphism. Then `ℱ` is fibred over `ℰ` iff `p` is _surjective_, in which case
`p` exhibits `F` as an extension of `E` by `G = ker p`. Fibres are all isomorphic to `BG` (the one-object groupoid of
`G`), and inverse-image functors are inner automorphisms by lifts.

### VI.6.2 — Fibredness invariant under `ℰ`-equivalence

<!-- source: VI.6.2 -->

_This result says: if `F : ℱ → 𝒢` is an `ℰ`-equivalence (file 35 §VI.4.3), then `ℱ` is (pre)fibred iff `𝒢` is._

**Proposition.** Let `F : ℱ → 𝒢` be an `ℰ`-equivalence. Then `ℱ` is fibred (resp. prefibred) over `ℰ` iff `𝒢` is.

**Proof.** By VI.5.3 (1) (file 35), a morphism `α` of `ℱ` is cartesian iff `F(α)` is cartesian in `𝒢`. Since `F` is an
`ℰ`-equivalence, every object of `𝒢` is in the essential image of `F`, and inverse-image data on either side transports
across the equivalence. Fib I and Fib II therefore correspond term by term. ∎

### VI.6.3 — Cartesianness in products is componentwise

<!-- source: VI.6.3 -->

*This result says: a morphism `(α₁, α₂)` of `ℱ₁ ×*ℰ ℱ*2`is cartesian iff each`α_i` is cartesian.*

**Proposition.** Let `ℱ₁, ℱ₂` be `ℰ`-categories and let `α = (α₁, α₂)` be a morphism in `ℱ = ℱ₁ ×_ℰ ℱ₂` over
`f : T → S`. Then `α` is cartesian iff each `α_i` is cartesian.

**Proof sketch.** The hom-set commutative square

```text
Hom_T(η', η)                       →  Hom_f(η', ξ)
   ∥                                       ∥
Hom_T(η'₁, η₁) × Hom_T(η'₂, η₂)  →  Hom_f(η'₁, ξ₁) × Hom_f(η'₂, ξ₂)
```

has bijective vertical arrows by the universal property of fibre products; the bottom arrow is bijective iff each
component is. That gives the equivalence "top arrow bijective ⟺ bottom arrow bijective", which is "α cartesian ⟺ each
α_i cartesian" after fixing `η' = (η'₁, η'₂)` appropriately. ∎

### VI.6.4 — Cartesian functors into a product

<!-- source: VI.6.4 -->

*This result says: a functor `F : 𝒢 → ℱ₁ ×*ℰ ℱ*2`is cartesian iff each component`F_i = pr_i ∘ F : 𝒢 → ℱ_i`is.
Equivalently,`Hom_{cart}` factors through products.*

**Corollary.** Let `ℱ = ℱ₁ ×_ℰ ℱ₂`, let `𝒢` be an `ℰ`-category, and let `F = (F₁, F₂)` be an `ℰ`-functor `𝒢 → ℱ`. Then
`F` is cartesian iff `F₁` and `F₂` are cartesian. This gives an isomorphism of categories

```text
Hom_{cart}(𝒢,  ℱ₁ ×_ℰ ℱ₂)  ≅  Hom_{cart}(𝒢, ℱ₁)  ×  Hom_{cart}(𝒢, ℱ₂),
```

and in particular, taking `𝒢 = ℰ`,

```text
Lim←((ℱ₁ ×_ℰ ℱ₂) / ℰ)  ≅  Lim←(ℱ₁ / ℰ)  ×  Lim←(ℱ₂ / ℰ).
```

**Proof.** Apply VI.6.3 morphism-by-morphism. ∎

### VI.6.5 — Products of (pre)fibred are (pre)fibred

<!-- source: VI.6.5 -->

_This result says: the fibre product over `ℰ` of (pre)fibred categories is (pre)fibred. Same statement extends to
arbitrary families._

**Corollary.** Let `ℱ₁, ℱ₂` be (pre)fibred over `ℰ`. Then `ℱ₁ ×_ℰ ℱ₂` is (pre)fibred over `ℰ`.

**Proof.** Fib I: an inverse image of `(ξ₁, ξ₂)` is `(f^*₁ ξ₁, f^*₂ ξ₂)`, with the product cartesian morphism (VI.6.3).
Fib II: composites of cartesian morphisms in the product are componentwise composites, each cartesian (Fib II in each
`ℱ_i`), so the product composite is cartesian (VI.6.3 again). ∎

### VI.6.6 — Cartesianness preserved under base change

<!-- source: VI.6.6 -->

*This result says: a morphism `α'` in `ℱ' = ℱ ×*ℰ ℰ'`is cartesian iff its image`α`in`ℱ` is cartesian.*

**Proposition.** Let `ℱ` be an `ℰ`-category, `λ : ℰ' → ℰ`, and `ℱ' = ℱ ×_ℰ ℰ'` viewed as `ℰ'`-category. A morphism `α'`
of `ℱ'` is cartesian (over its image in `ℰ'`) iff `pr₁(α')` is cartesian (over its image in `ℰ`).

**Proof.** Direct verification on the universal property, identifying fibres `(ℱ')_{S'} = ℱ_{λ(S')}`. ∎

### VI.6.7 — Base change of a cartesian functor is cartesian

<!-- source: VI.6.7 -->

*This result says: if `F : ℱ → 𝒢` is cartesian, so is `F' := F ×*ℰ ℰ' : ℱ' → 𝒢'`. So base change restricts to a functor
on cartesian-functor categories: `Hom_{cart}(ℱ, 𝒢) → Hom_{cart}(ℱ', 𝒢')`.*

**Corollary.** For every cartesian `ℰ`-functor `F : ℱ → 𝒢` and every `λ : ℰ' → ℰ`, the pulled-back functor
`F' = F ×_ℰ ℰ' : ℱ' → 𝒢'` is a cartesian `ℰ'`-functor. Consequently, base change refines to a functor

```text
Hom_{cart}(ℱ, 𝒢)  ⟶  Hom_{cart}(ℱ', 𝒢')
```

natural in `ℰ', ℱ, 𝒢`.

**Proof.** Cartesianness on `ℱ' → 𝒢'` corresponds to cartesianness on `ℱ → 𝒢` by VI.6.6 applied to source and target. ∎

### VI.6.8 — Lim← as cartesian sections

<!-- source: VI.6.8 -->

*This result says: cartesian sections `s : ℰ' → ℱ'` over `ℰ'` of `ℱ' = ℱ ×*ℰ ℰ'`are the same as`ℰ`-functors `ℰ' → ℱ`that
send arbitrary morphisms to cartesian morphisms. Equivalently (when`ℱ`is
fibred):`Ob Lim←(ℱ' / ℰ') ≅ Hom_{ℰ/-}(ℰ', ℱ̃)`for`ℱ̃` the cartesian sub-fibred-category.*

**Corollary.** `Lim←(ℱ' / ℰ')` is naturally isomorphic to the full subcategory of `Hom_{ℰ/-}(ℰ', ℱ)` whose objects are
the `ℰ`-functors `ℰ' → ℱ` sending arbitrary morphisms to cartesian morphisms. When `ℱ` is fibred, with cartesian
sub-fibred-category `ℱ̃ ⊂ ℱ`,

```text
Ob Lim←(ℱ' / ℰ')  ≅  Hom_{ℰ/-}(ℰ', ℱ̃).
```

This is the technical version of "a cartesian section assigns fibre-wise objects with cartesian transition data". The
`ℰ' → ℱ̃` formulation will recur in file 38 §VI.12 as "a section is the same as a coherent compatible family".

### VI.6.9 — Base change of (pre)fibred is (pre)fibred

<!-- source: VI.6.9 -->

_This result says: pulling a (pre)fibred category `ℱ → ℰ` back along `λ : ℰ' → ℰ` gives a (pre)fibred category
`ℱ' → ℰ'`._

**Corollary.** If `ℱ` is (pre)fibred over `ℰ`, then `ℱ' = ℱ ×_ℰ ℰ'` is (pre)fibred over `ℰ'`.

**Proof.** Fib I and Fib II both transport across the identification of fibres `(ℱ')_{S'} ≅ ℱ_{λ(S')}` (file 35 §VI.4)
and the cartesianness statement VI.6.6. ∎

### VI.6.10 — Faithful / fully faithful / equivalence on fibres

<!-- source: VI.6.10 -->

_This result says: for a cartesian `ℰ`-functor `F : ℱ → 𝒢` between prefibred categories, `F` is faithful (resp. fully
faithful, resp. an `ℰ`-equivalence) iff each fibre functor `F_S : ℱ_S → 𝒢_S` is._

**Proposition.** Let `F : ℱ → 𝒢` be a cartesian `ℰ`-functor of prefibred `ℰ`-categories. Then `F` is faithful (resp.
fully faithful, resp. an `ℰ`-equivalence) iff every fibre functor `F_S : ℱ_S → 𝒢_S` is.

**Proof.** Fix `f : T → S` and morphisms `u, v : η → ξ` in `ℱ` over `f`. Choose cartesian morphisms
`α_f^ℱ(ξ) : f^*_ℱ(ξ) → ξ` and `α_f^𝒢(F ξ) : f^*_𝒢(F ξ) → F(ξ)`. Cartesianness of `F` gives an isomorphism
`F(f^*_ℱ(ξ)) ≅ f^*_𝒢(F ξ)` over `T`. Hence `Hom_f(η, ξ)` in `ℱ` is in bijection with `Hom_T(η, f^*_ℱ(ξ))` via the
universal property; same on the`𝒢`side. The action of`F`on`Hom_f`reduces to the action on`Hom_T` via these bijections.
So fibre-wise faithful (resp. fully faithful) implies global. The equivalence statement follows by combining with VI.4.2
(file 35 §VI.4.2 (3)). ∎

### VI.6.11 — Fib II equivalent to a stronger universal property

<!-- source: VI.6.11 -->

_This result says: a prefibred `ℱ` is fibred iff its cartesian morphisms enjoy a stronger universal property than the
definition demands. The stronger property is that for cartesian `α : η → ξ` over `f` and *any* further morphism
`g : U → T`, precomposition `Hom_g(ζ, η) → Hom_{fg}(ζ, ξ)` is bijective._

**Proposition.** A prefibred `ℰ`-category `ℱ` is fibred iff it satisfies:

- **Fib II′.** For every cartesian morphism `α : η → ξ` in `ℱ` over `f : T → S`, every morphism `g : U → T` in `ℰ`, and
    every `ζ ∈ Ob ℱ_U`, the precomposition map

    ```text
    α_*  :  Hom_g(ζ, η)  ⟶  Hom_{fg}(ζ, ξ),    u ↦ α ∘ u,
    ```

    is bijective.

The original Fib II (composites of cartesian morphisms are cartesian) is the special case `g = id_T`. So Fib II′ is a
priori stronger; the proposition says it is in fact equivalent to Fib II for prefibred `ℱ`.

**Proof.** Fib II′ ⟹ Fib II: take `g = id_T` in Fib II′ to get the bijection `Hom_T(ζ, η) ≅ Hom_f(ζ, ξ)`, which is
exactly `α` cartesian (file 35 §VI.5.1). Fib II ⟹ Fib II′: pick a cartesian `g`-morphism `β : ζ' → η` above`g`;
then`α ∘ β`is cartesian (by Fib II) over`fg`, so cartesianness of`α ∘ β` gives the universal property in question. ∎

### VI.6.12 — When is a morphism an isomorphism?

<!-- source: VI.6.12 -->

_This result says: an isomorphism `α` in `ℱ` projects to an isomorphism `p(α)` in `ℰ` and is automatically cartesian.
The converse holds when `ℱ` is fibred: `α` is an isomorphism iff `p(α)` is an isomorphism and `α` is cartesian._

**Corollary.** Let `ℱ` be an `ℰ`-category and `α : η → ξ` a morphism. If `α` is an isomorphism, then `p(α)` is an
isomorphism and `α` is cartesian. Conversely, if `ℱ` is fibred and `p(α)` is an isomorphism and `α` is cartesian, then
`α` is an isomorphism.

**Proof.** "Only if": every isomorphism enjoys precomposition bijectivity unrestrictedly, hence cartesianness. "If"
(when `ℱ` fibred): use Fib II′ (VI.6.11) plus the fact that `α` is cartesian and `p(α)` is iso to read off, for every
`ζ ∈ Ob ℱ`, that `Hom(ζ, η) → Hom(ζ, ξ)` is bijective. By Yoneda `α` is iso. ∎

### VI.6.13 — Two-of-three for cartesian morphisms (in fibred ℱ)

<!-- source: VI.6.13 -->

_This result says: in a fibred category, given composable morphisms `α : η → ξ` (cartesian) and `β : ζ → η`, the
composite `α β` is cartesian iff `β` is. So "cartesian" satisfies a two-of-three property along with the cartesianness
of `α`._

**Corollary.** Let `ℱ` be fibred over `ℰ`. For composable morphisms `β : ζ → η` and `α : η → ξ` in `ℱ`, with `α`
cartesian: `αβ` is cartesian iff `β` is cartesian.

**Proof.** Use Fib II′ (VI.6.11): cartesianness of `α` gives, for every `g : U → T` and every `ζ' ∈ ℱ_U`, the bijection
`Hom_g(ζ', η) → Hom_{fg}(ζ', ξ)`; the further claim that the map sends `β ∘ –` bijectively onto `(α β) ∘ –` is
mechanical. ∎

## §VI.7 Cloven categories

<!-- source: VI.7 -->

We arrive at the structural choice that turns "abstract fibred" into "concrete pseudofunctorial data". Throughout, `ℱ`
is an `ℰ`-category.

### VI.7.1 — Definition: cleavage, normalised cleavage, cloven category

<!-- source: VI.7.1 -->

*This result says: a **cleavage** of `ℱ` is a function `f ↦ f^*` choosing, for every `f ∈ Fl(ℰ)`, an inverse-image
functor `f^* : ℱ_S → ℱ_T`. The cleavage is **normalised** if `(id_S)^* = id_{ℱ_S}`for every`S`. A **cloven category** is
an `ℰ`-category with a chosen cleavage. Cleavages exist iff `ℱ`is prefibred. Equivalently, a cleavage is a
subset`K ⊂ Fl(ℱ)`of **transport morphisms**, one over each`(f, ξ)`, all cartesian.*

**Definition.** Let `ℱ` be an `ℰ`-category.

- A **cleavage** of `ℱ` is the data of, for every `f ∈ Fl(ℰ)`, an inverse-image functor
    `f^* := f^*_ℱ : ℱ_{p(target(f))} → ℱ_{p(source(f))}`, together with a chosen cartesian morphism
    `α_f(ξ) : f^*(ξ) → ξ` for every `ξ ∈ Ob ℱ_{target(f)}`.
- A cleavage is **normalised** if for every `S ∈ Ob ℰ`, `(id_S)^* = id_{ℱ_S}` and `α_{id_S}(ξ) = id_ξ`.
- A **cloven category** (resp. **normalised cloven category**) is an `ℰ`-category with a (resp. normalised) cleavage.

**Existence.** `ℱ` admits a cleavage iff `ℱ` is prefibred. (Fib I says inverse-image functors exist; the cleavage
_names_ one for every `f`. Existence of names uses choice on objects.) Any prefibred `ℱ` admits a _normalised_ cleavage
(replace `(id_S)^*` by`id_{ℱ_S}`and adjust`α_{id_S}`).

**Equivalent presentation: transport morphisms.** The set of cleavages of `ℱ` is in bijection with the set of subsets
`K ⊂ Fl(ℱ)` satisfying:

1. Every `α ∈ K` is a cartesian morphism.
1. For every `f : T → S` in `ℰ` and every `ξ ∈ Ob ℱ_S`, there is _exactly one_ `f`-morphism in `K` with target `ξ`.

The cleavage is normalised iff `K` additionally satisfies:

1. Every identity morphism of `ℱ` is in `K`.

The morphisms in `K` are called the **transport morphisms** of the cleavage.

> **In quasi-coherent modules.** A cleavage of the QCoh fibred category is a choice of pullback functor
> `f^* : QCoh(S) → QCoh(T)` for every morphism `f : T → S` of schemes, plus the canonical transport
> `α_f(M) : f^*(M) → M` for every quasi-coherent module `M` on `S`. The standard sheaf-theoretic pullback gives a
> normalised cleavage: `(id_S)^* = id` on quasi-coherent sheaves over `S`. This is the cleavage Hartshorne or Vakil uses
> implicitly every time they write `f^*`.

### From cleavage to coherence: defining `c_{f, g}`

Given a cloven `ℱ` and composable `g : U → T`, `f : T → S` in `ℰ`, and `ξ ∈ Ob ℱ_S`, the universal property of the
cartesian morphism `α_{fg}(ξ) : (fg)^*(ξ) → ξ` (which is over `fg`) gives a unique `U`-morphism

```text
c_{f, g}(ξ)  :  g^* f^*(ξ)  ⟶  (fg)^*(ξ)
```

making the diagram

```text
g^* f^*(ξ)  --α_g(f^*(ξ))-->  f^*(ξ)
   |                              |
   c_{f, g}(ξ)                    α_f(ξ)
   ↓                              ↓
(fg)^*(ξ)  --α_{fg}(ξ)-->         ξ
```

commute. Naturally in `ξ`, this is a 2-cell of `Cat`:

```text
c_{f, g}  :  g^* f^*  ⟹  (fg)^*    :   ℱ_S ⟶ ℱ_U.
```

(Note the contravariant order: `c_{f, g}` goes from `g^* f^*`, the "inner pull-back along`g`, then outer along`f`",
to`(fg)^*`, the "pull-back along the composite". This matches the convention of file 34 Module C.)

The 2-cell `c_{f, g}` need not be invertible; that is what the next proposition addresses.

### VI.7.2 — Cloven `ℱ` is fibred ⟺ every `c_{f, g}` is invertible

<!-- source: VI.7.2 -->

_This result says: a cloven `ℰ`-category is fibred iff every coherence 2-cell `c_{f, g}` is a natural isomorphism. So
"fibred" is the precise abstract condition that the cleavage's pseudofunctorial data is
pseudofunctorial-with-isomorphism, not merely with-natural-transformation._

**Proposition.** A cloven `ℰ`-category `ℱ` is fibred iff for every composable pair `(f, g)` of arrows of `ℰ`, the
coherence 2-cell `c_{f, g} : g^* f^* ⟹ (fg)^*` is a natural isomorphism.

**Proof.** "⟹": Fib II says the composite `α_f(ξ) ∘ α_g(f^*(ξ))` is cartesian over`fg`. By the universal property of the
chosen cartesian morphism `α_{fg}(ξ)`, the unique `U`-morphism `c_{f, g}(ξ)` from `g^* f^*(ξ)` to`(fg)^_(ξ)` filling the
diagram is an isomorphism. (Two cartesian morphisms over the same `fg` with the same target are unique up to unique
`U`-isomorphism.) "⟸": Conversely, if every`c_{f, g}` is invertible, then the composite `α_f(ξ) ∘ α_g(f^_(ξ))` is, up to
invertible 2-cell, the chosen cartesian `α_{fg}`, hence cartesian. ∎

### VI.7.3 — In fibred cloven `ℱ`, `f^*` is an equivalence for `f` iso

<!-- source: VI.7.3 -->

_This result says: in a fibred cloven category, when `f : T → S` is an isomorphism in `ℰ`, the inverse-image functor
`f^* : ℱ_S → ℱ_T` is an equivalence of categories (with quasi-inverse `(f⁻¹)^*` up to canonical iso)._

**Corollary.** Let `ℱ` be a fibred cloven `ℰ`-category. For every isomorphism `f : T → S` in `ℰ`, the functor
`f^* : ℱ_S → ℱ_T` is an equivalence of categories.

**Proof.** Take `g = f⁻¹` in VI.7.2:`c_{f, f⁻¹} : (f⁻¹)^* f^* ⟹ (id_S)^* = id_{ℱ_S}` is a natural isomorphism (using
normalisation). Symmetrically `c_{f⁻¹, f} : f^_ (f⁻¹)^_ ⟹ id_{ℱ_T}` is a natural isomorphism. So `(f⁻¹)^*` is a
quasi-inverse to`f^*`. ∎

### VI.7.4 — Coherence identities A) and B)

<!-- source: VI.7.4 -->

*This result says: the coherence 2-cells `c_{f, g}`of any cloven category satisfy two identities. **A)** Two unit
identities (absorbed into the normalisation when the cleavage is normalised):`c_{f, id_T}(ξ) = α_{id_T}(f^*(ξ))`
and`c_{id_S, f}(ξ) = f^*(α_{id_S}(ξ))`. **B)** A pentagon: for composable `h : V → U → T → S` and `ξ ∈ ℱ_S`,*

```text
c_{f, gh}  ∘  (h^* * c_{g, h})    =    c_{fg, h}  ∘  (c_{f, g} * h^*),
```

_i.e., the two natural transformations `h^* g^* f^* ⟹ (fgh)^*` agree. This is **the** pentagon coherence of file 34
Module C._

**Proposition.** Let `ℱ` be a cloven `ℰ`-category. Then for every composable triple `h : V → U`, `g : U → T`,
`f : T → S` in `ℰ`, and every `ξ ∈ Ob ℱ_S`:

- **A) Unit identities.**

    ```text
    c_{f, id_T}(ξ)  =  α_{id_T}(f^*(ξ)),
    c_{id_S, f}(ξ)  =  f^*(α_{id_S}(ξ)).
    ```

    In a normalised cleavage these become `c_{f, id_T} = id_{f^*}` and`c_{id_S, f} = id_{f^*}` — call this **A′)**.

- **B) Pentagon.** The diagram of natural transformations of functors `ℱ_S → ℱ_V`

    ```text
    h^* g^* f^*       --c_{g, h} * f^*-->   (gh)^* f^*
         |                                       |
         h^* * c_{f, g}                          c_{f, gh}
         ↓                                       ↓
    h^* (fg)^*        --c_{fg, h}-->        (fgh)^*
    ```

    commutes. Equivalently:

    ```text
    c_{f, gh}  ∘  (h^* * c_{g, h})  =  c_{fg, h}  ∘  (c_{f, g} * h^*).
    ```

In the **fibred case** (where every `c_{f, g}` is invertible by VI.7.2), the pentagon expresses the slogan that "any two
parallel pasting compositions of coherence isomorphisms agree" — this is the
\[`mac-lane-coherence`\](appendix-black-boxes.md#mac-lane-coherence) input to file 34 Module C. Without invertibility,
the pentagon is still an equality, but the theorem-statement is about pasting natural transformations, not isomorphisms.

**Proof of B).** Both sides are `(fgh)`-morphisms`h^_ g^_ f^_(ξ) → (fgh)^_(ξ)`. By the universal property of
`α_{fgh}(ξ) : (fgh)^*(ξ) → ξ`, two such morphisms are equal iff they have the same composite with `α_{fgh}(ξ)`. Form the
cube whose top face is the diagram in the proposition (with`(fgh)^*(ξ)` added at the bottom-right corner) and whose four
side faces are obtained by attaching `α`-morphisms to each vertex; the side faces commute by naturality and by the
definition of the various `c_{·, ·}`'s. Hence the bottom face commutes, which is exactly the equality sought. ∎

### Summary: cloven category as pseudofunctorial data

Specialise to a **normalised** cloven `ℰ`-category. The data extracts as:

1. A function `S ↦ ℱ_S : Ob ℰ → Cat` (the fibres).
1. A function `f ↦ f^* : Fl(ℰ) → Mor(Cat)` (the inverse-image functors), with `(id_S)^* = id_{ℱ_S}`.
1. A family of natural transformations `c_{f, g} : g^_ f^_ ⟹ (fg)^*`, satisfying A′) and B).

This is exactly the data of a **pseudofunctor** `ℰ° → Cat` in the sense of file 34 Module C, except for the (mild)
reformulation of contravariance. File 37 §VI.8 gives the _converse_ construction: from any pseudofunctor, build a cloven
category. The two operations are mutually inverse (up to a 2-categorical equivalence we will name but not prove).

## Worked example: cleavage of the arrow category

Continue the worked example of file 35. Take `ℰ = (Sch / S₀)` and`ℱ = Ar(ℰ)`, the arrow category.

**A canonical cleavage.** For each `f : Y' → Y` in`ℰ` and each `(X → Y) ∈ Ob ℱ_Y`, define

```text
f^*(X → Y)  :=  (X ×_Y Y'  →  Y'),
α_f(X → Y)  :=   the cartesian square X ×_Y Y' → X over f.
```

This requires a _choice_ of fibre product `X ×_Y Y'` for every`(X, Y, Y', f)`; the choice depends on a choice of
representing object for each fibre-product universal property. Once made, we have a cleavage.

**Normalisation.** When `f = id_Y`, the chosen fibre product`X ×*Y Y` is canonically isomorphic to `X`, but not equal to
it. We normalise by stipulating `(id_Y)^* = id_{ℱ_Y}` and adjusting`α_{id_Y}(X → Y) = id_X`.

**Coherence isomorphisms.** For composable `g : Y'' → Y'` and`f : Y' → Y` in `ℰ`, the coherence
`c_{f, g}(X → Y) : g^_ f^_(X → Y) → (fg)^*(X → Y)` is the canonical isomorphism

```text
(X ×_Y Y') ×_{Y'} Y''  ≅  X ×_Y Y''.
```

This is the **associativity of fibre products**. It is invertible (both sides represent the same universal property of
"object with three compatible morphisms to `X, Y, Y''`, then`Y`"). So by VI.7.2, `Ar(ℰ)` is fibred — Fib II holds.

**Pentagon check.** For composable `h : Y''' → Y''`,`g`,`f`, both pasting compositions of `c`'s yield natural
isomorphisms `((X ×*Y Y') ×_{Y'} Y'') ×_{Y''} Y''' ≅ X ×_Y Y'''`. Both are the unique iso witnessing the four-fold
universal property; by uniqueness, they agree. The pentagon B) holds.

**The split-vs-cloven question.** Is `Ar(ℰ)` a *split* category (file 37 §VI.9)? That is, can the cleavage be chosen so
that`(fg)^_ = g^_ f^*` on the nose, with `c_{f, g} = id`? Equivalently: can we choose fibre products coherently so that
`(X ×*Y Y') ×_{Y'} Y'' = X ×_Y Y''` literally, for *all*`(X, Y, Y', Y'')`?

The answer is **no** — there is no global functorial choice of "fibre product" in `(Sch / S₀)` that strictly satisfies
associativity. (The category of fibre products is equivalent to, but not isomorphic to, a strict-associative version.
The strictification theorem [`strictification`](appendix-black-boxes.md#strictification) of file 37 §VI.9 says we *can*
make`Ar(ℰ)` equivalent to a split category, but the equivalence is not the identity.)

This is the example whose strictification failure motivates fibred-category theory: one _cannot_ pretend the
inverse-image functors compose strictly; one _must_ track the coherence isomorphisms `c_{f, g}`.

## Continuing on

File 37 takes the next step: from a normalised cloven category we extract a pseudofunctor `ℰ° → Cat` (the
natural-transformation data of §VI.7.4). The reverse construction — from a pseudofunctor`ϕ : ℰ° → Cat`, build a cloven
category over `ℰ` — is **§VI.8**, the central reconstruction theorem of the exposé. The two operations together
establish a bijection between cloven categories over `ℰ` and normalised pseudofunctors`ℰ° → Cat`.

§VI.9 then isolates the _split_ case (where `c_{f, g} = id` on the nose), and §VI.10 dualises to **co-cartesian**
morphisms, **direct images**`f**`, and **bi-fibred** categories — the setting in which adjoint pairs `(f^*, f**)` live.

After file 37, file 38 closes Exposé VI with the example library (§VI.11) and the **descent isomorphism** (§VI.12.1):
the categorical identity that says "a global functor on a fibred category is determined by fibre-wise data plus a
cocycle." The geometric specialisation (faithfully flat descent of modules and schemes) lives in Exposés VIII–IX; we
close with a forward pointer.
