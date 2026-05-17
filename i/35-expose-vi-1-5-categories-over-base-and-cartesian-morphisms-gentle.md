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

Topological covering theory begins with a base space `B` and a total space `E → B`. Algebraic-geometric Galois theory
begins with a base scheme `S` and a finite étale cover `X → S`. In both cases the geometry of the cover is controlled by
what happens fibre-wise as the base point varies.

Exposé VI replaces the base _space_ with a base _category_ `ℰ`, and the cover with a category `ℱ` together with a
projection functor `p : ℱ → ℰ`. The "fibre over `S`" is the subcategory `ℱ_S = p⁻¹(S)` of objects mapping to `S` and
morphisms mapping to `id_S`. The structure problem the exposé sets up: _what does it take for the fibre `ℱ_S` to vary
functorially in `S` ∈ `ℰ`_?

The answer comes in three layers, each progressively more structure:

- a category over `ℰ` (just the projection `p`),
- a _prefibred_ category (every base morphism `f : T → S` admits inverse images, file 36),
- a _fibred_ category (the inverse-image functors compose well, also file 36).

Files 35 (this file) and 36 introduce the layers in order. This file covers §§1–5: the basic vocabulary (`ℰ`-categories,
`ℰ`-functors, fibre categories, base change in `Cat`) and the central concept of _cartesian morphism_ — the
universal-property formulation of "pull-back along `f`" that makes inverse images canonical (up to canonical iso). §6's
fibred-category axioms are cleanest stated in terms of cartesian morphisms; the work of §5 is to introduce them.

A reading note. SGA VI is bookkeeping-heavy in §§1–3 — many formulae of the form "this functor commutes with that
construction" — and lighter in §§4–5. We summarise the bookkeeping rather than reproducing it; the reader who wants
every diagrammatic verification should keep Vistoli §3.1
([`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained)) open in parallel.

**Running examples.** Two examples thread the abstract material of files 35–38 and connect it to geometry. The first is
the **arrow category** `Ar(ℰ) = Hom(Δ¹, ℰ)`, developed as a full worked section at the close of each file (this file's
closing example at the bottom; file 36 §VI.7's cleavage; file 37 §VI.10's direct image). The second is **quasi-coherent
modules**, `S ↦ QCoh(S)` over the category of schemes, called out inline after each key definition and again at file 38
§VI.11(b). The arrow-category example is the one Grothendieck uses to motivate cartesian morphisms; the QCoh example is
the one file 40 onward leans on. We keep both visible. A reader who only wants the geometry should follow the QCoh
callouts and skim the arrow-category sections.

## §VI.1 Universes, categories, equivalences

Throughout the exposé Grothendieck works with a fixed
[universe](34-sites-sheaves-and-pseudofunctors-gentle.md#module-b-2-categories-and-the-2-category-cat) `𝒰`. `Set`
denotes the category of `𝒰`-small sets, `Cat` the category of `𝒰`-small categories. (We do _not_ use the 2-category
structure of `Cat` until §VI.7; here `Cat` is just a 1-category.) `Ob(𝒞)` and `Fl(𝒞)` are the sets of objects and arrows
of a category `𝒞`.

A functor `F : 𝒞 → 𝒞′` is **faithful** (resp. **fully faithful**) if `Hom_𝒞(S, T) → Hom_{𝒞′}(F S, F T)` is injective
(resp. bijective) for every pair `(S, T)`. `F` is an **equivalence** if it is fully faithful and every object of `𝒞′` is
isomorphic to one of the form `F(S)`. Equivalently: there is a functor `G : 𝒞′ → 𝒞` and natural isomorphisms
`G F ≅ id_𝒞`, `F G ≅ id_{𝒞′}`. The functor `G` is called a **quasi-inverse** of `F`. Quasi-inverses are unique up to
unique isomorphism.

We assume the reader is comfortable with limits and colimits in `Cat` (in particular with the fibre product `𝒞 ×_𝒟 𝒞′`,
defined by `Ob(𝒞 ×_𝒟 𝒞′) = Ob(𝒞) ×_{Ob(𝒟)} Ob(𝒞′)` and similarly for arrows). These are the only categorical limits we
use.

## §VI.2 Categories over `ℰ`

<!-- source: VI.2 -->

Fix a category `ℰ`. An object of `Cat_{/ ℰ}` — that is, an **`ℰ`-category** — is a pair `(ℱ, p)` consisting of a
category `ℱ` and a functor `p : ℱ → ℰ`, the **projection**. We write just `ℱ` when `p` is understood.

An **`ℰ`-functor** `f : ℱ → 𝒢` between `ℰ`-categories `(ℱ, p)`, `(𝒢, q)` is a functor satisfying `q ∘ f = p` strictly
(not just up to isomorphism). The set of `ℰ`-functors from `ℱ` to `𝒢` is

```text
Hom_ℰ(ℱ, 𝒢)  =  { f : ℱ → 𝒢  :  q ∘ f = p }.
```

These are the morphisms of `Cat_{/ ℰ}`.

### `α`-morphisms

Given any morphism `α : T → S` in `ℰ` and any `ℰ`-category `(𝒢, q)`, a morphism `v` in `𝒢` is an **`α`-morphism** if
`q(v) = α`. When `α = id_S`, an `α`-morphism is an **`S`-morphism** — a morphism in the fibre `𝒢_S` (= the inverse image
of `id_S`).

### `ℰ`-natural transformations

For two `ℰ`-functors `f, g : ℱ → 𝒢`, an **`ℰ`-natural transformation** (or **`ℰ`-homomorphism**) `u : f ⟹ g` is a
natural transformation such that, for every `ξ ∈ Ob ℱ`, the component `u(ξ) : f(ξ) → g(ξ)` is an `id_{p(ξ)}`-morphism in
`𝒢`.

`ℰ`-functors and `ℰ`-natural transformations form a category

```text
Hom_{ℰ/-}(ℱ, 𝒢)  ⊆  Hom(ℱ, 𝒢)
```

— a (full? not quite: full on objects = on functors, but the hom-sets are restricted to `ℰ`-natural transformations) —
sub- 2-cell collection of the all-natural-transformations category. Vertical and horizontal compositions of `ℰ`-natural
transformations are again `ℰ`-natural; this is part of what makes `Cat_{/ ℰ}` itself a 2-category. The composition
pairings `(I)`–`(IV)` of the source (the standard interchange laws and unit laws for vertical and horizontal
composition) hold; we do not reproduce them.

### Special notation: cartesian sections

When `ℱ = ℰ` (the identity `ℰ`-category), an `ℰ`-functor `ℰ → 𝒢` is just a **section** of `q : 𝒢 → ℰ`. We write

```text
Γ(𝒢 / ℰ)  =  Hom_ℰ(ℰ, 𝒢),
Γ(𝒢 / ℰ)̲  =  Hom_{ℰ/-}(ℰ, 𝒢),
```

for the set of sections (resp. category of sections and `ℰ`-natural transformations between them). We use this notation
in §VI.5 and again in file 38.

## §VI.3 Base change

<!-- source: VI.3 -->

Let `λ : ℰ′ → ℰ` be a functor. For an `ℰ`-category `(ℱ, p)`, the **base change** of `ℱ` along `λ` is the fibre product

```text
λ* ℱ  :=  ℱ ×_ℰ ℰ′,
```

regarded as an `ℰ′`-category via the projection `pr₂ : ℱ ×_ℰ ℰ′ → ℰ′`. This defines a functor

```text
λ*  :  Cat_{/ℰ}  ⟶  Cat_{/ℰ′}.
```

It is right adjoint to "restriction of the base" (which views an `ℰ′`-category as an `ℰ`-category by composing with
`λ`). Concretely, `λ*` commutes with all categorical limits (since it is a right adjoint).

### The base-change isomorphism

The central diagram in this section is the canonical isomorphism

```text
(*)   Hom_{ℰ′/-}(λ*ℱ, λ*𝒢)  ≅  Hom_{ℰ/-}(λ*ℱ, 𝒢),
```

natural in `ℱ, 𝒢, ℰ′`. The forward map is composition with `pr₁ : λ*𝒢 = 𝒢 ×_ℰ ℰ′ → 𝒢`. Both sides describe
"`ℰ′`-functors from the pulled-back source", with the right-hand side viewing the target as an `ℰ`-category. _This
result says: pulling back the source along `λ` is the same as forgetting the `ℰ′`-structure of the target._ (The proof
is a direct verification on objects and 2-cells.)

A consequence we use: for every `ℰ`-functor `f : ℱ → 𝒢`, applying `λ*` gives an `ℰ′`-functor `f' = λ*(f) : λ*ℱ → λ*𝒢`,
and the assignment `f ↦ f'` is the action of `λ*` on 1-morphisms. On `ℰ`-natural transformations `u : f ⟹ g`, the
component is `u'(ξ', S') = (u(ξ), id_{S'})` for `ξ' = (ξ, S')` in `λ*ℱ` over `S' ∈ Ob ℰ′`.

### Transitivity

For composable `λ' : ℰ″ → ℰ′` and `λ : ℰ′ → ℰ`, the canonical isomorphism

```text
(λ ∘ λ')*  ≅  λ'* ∘ λ*
```

holds in `Cat_{/ℰ″}`. Concretely it is the canonical iso

```text
ℱ ×_ℰ ℰ″  ≅  (ℱ ×_ℰ ℰ′) ×_{ℰ′} ℰ″
```

— the associativity of the categorical fibre product. This is the bookkeeping that file 36's pentagon coherence will
refine into a 2-cell statement.

### Compatibility with composition

Base change preserves composition of `ℰ`-functors: `(g ∘ f)' = g' ∘ f'` for composable `f : ℱ → 𝒢` and `g : 𝒢 → ℋ`, and
`(v * u)' = v' * u'` for `ℰ`-natural transformations. This is part of saying that `λ*` is a 2-functor
`Cat_{/ℰ} → Cat_{/ℰ′}`, though SGA VI does not state it that way. We use this fact freely.

## §VI.4 Fibre categories; `ℰ`-equivalences

<!-- source: VI.4 -->

For an `ℰ`-category `(ℱ, p)` and `S ∈ Ob ℰ`, the **fibre category** `ℱ_S` is

```text
ℱ_S  =  p⁻¹(S)  =  ℱ ×_ℰ {S},
```

where `{S}` is the one-object subcategory of `ℰ` containing just `id_S`. Concretely, `Ob ℱ_S = { ξ ∈ Ob ℱ : p(ξ) = S }`
and morphisms `ℱ_S(ξ, ξ') = { u : ξ → ξ' in ℱ : p(u) = id_S }`.

Compatibility with base change. For any `λ : ℰ′ → ℰ` and `S' ∈ Ob ℰ′` with `S = λ(S')`, the projection `pr₁ : λ*ℱ → ℱ`
restricts to an isomorphism of fibres

```text
(λ*ℱ)_{S'}  ≅  ℱ_S.
```

So fibres are intrinsic: they do not depend on whether we view ℱ as an `ℰ`- or an `ℰ′`-category.

### VI.4.1 — Fully faithful is preserved under base change

<!-- source: VI.4.1 -->

_This result says: if `f : ℱ → 𝒢` is fully faithful as a functor (so the underlying map on hom-sets is bijective), then
the pulled-back functor `f' : λ*ℱ → λ*𝒢` is also fully faithful, for every base change `λ : ℰ′ → ℰ`._

**Proposition.** Let `f : ℱ → 𝒢` be an `ℰ`-functor that is fully faithful (as an ordinary functor). Then for every
`λ : ℰ′ → ℰ`, the functor `f' = λ*(f) : λ*ℱ → λ*𝒢` is fully faithful.

**Proof.** A morphism `(u, β) : (ξ, S') → (ξ', T')` in `λ*ℱ` projects to `(p(u), λ(β)) = (p(u), λ(β))` in `ℰ`.
Bijectivity of `f'` on the hom-set `Hom_{λ*ℱ}((ξ, S'), (ξ', T')) → Hom_{λ*𝒢}(...)` follows from bijectivity of `f` on
the appropriate fibre — which is given by hypothesis. (More abstractly: a fibre product of fully faithful functors with
arbitrary functors is fully faithful, by a pointwise limit argument.) ∎

The analogous statement with "fully faithful" replaced by "equivalence" _fails_. The next proposition pins down the
correct strengthening.

### VI.4.2 — Characterisation of `ℰ`-equivalences

<!-- source: VI.4.2 -->

_This result says: an `ℰ`-functor `f : ℱ → 𝒢` admits an `ℰ`-quasi- inverse iff it is an equivalence on every fibre, iff
base change preserves the property "is an equivalence", iff `f` is fully faithful and surjective on fibres up to
`S`-isomorphism. The four conditions are equivalent._

**Proposition.** For an `ℰ`-functor `f : ℱ → 𝒢`, the following are equivalent:

1. There exists an `ℰ`-functor `g : 𝒢 → ℱ` and `ℰ`-natural isomorphisms `g f ≅ id_ℱ`, `f g ≅ id_𝒢`.
1. For every `ℰ′ → ℰ`, the functor `f' = f ×_ℰ ℰ' : λ*ℱ → λ*𝒢` is an equivalence of categories.
1. `f` is an equivalence of categories, _and_ for every `S ∈ Ob ℰ` the induced functor `f_S : ℱ_S → 𝒢_S` is an
    equivalence.
1. `f` is fully faithful, _and_ for every `S ∈ Ob ℰ` and every `η ∈ Ob 𝒢_S`, there exists `ξ ∈ Ob ℱ_S` and an
    `S`-isomorphism `f(ξ) ≅ η`.

**Proof sketch.** `(1) ⇒ (2)`: `(g, f g ≅ id, g f ≅ id)` is preserved under base change by the functoriality of `λ*`.
`(2) ⇒ (3)`: take `ℰ' = ℰ` (giving `f` is an equivalence) and `ℰ' = {S}` (giving each `f_S` is an equivalence).
`(3) ⇒ (4)`: trivial. `(4) ⇒ (1)`: choose, for each `η ∈ Ob 𝒢`, an object `g(η) ∈ Ob ℱ` with `p(g(η)) = q(η)` and an
isomorphism `u(η) : f(g(η)) → η` over `id_{q(η)}`. Full-faithfulness of `f` makes `g` into a functor and `u` into an
`ℰ`-natural isomorphism `f g ≅ id_𝒢`. The dual `g f ≅ id_ℱ` is then forced. ∎

### VI.4.3 — Definition of `ℰ`-equivalence

<!-- source: VI.4.3 -->

_This result says: a functor satisfying any one of the four equivalent conditions of VI.4.2 deserves a name; we call it
an **`ℰ`-equivalence**._

**Definition.** An `ℰ`-functor `f : ℱ → 𝒢` is an **`ℰ`-equivalence** if it satisfies the equivalent conditions of
VI.4.2.

The distinction matters: not every equivalence of underlying categories is an `ℰ`-equivalence. The next corollary
identifies when it is.

### VI.4.4 — Transportable `ℰ`-categories

<!-- source: VI.4.4 -->

_This result says: when the projection `p : ℱ → ℰ` admits isomorphisms freely along base isomorphisms ("transportable"),
the pathology of the previous sentence vanishes: an underlying equivalence is automatically an `ℰ`-equivalence._

**Corollary.** Suppose `p : ℱ → ℰ` is **transportable**: for every isomorphism `α : T → S` in `ℰ` and every `ξ ∈ ℱ_T`,
there is an isomorphism `u` in `ℱ` with source `ξ` and `p(u) = α`. Then every `ℰ`-functor `f : ℱ → 𝒢` that is an
equivalence of underlying categories is an `ℰ`-equivalence.

**Proof.** Apply criterion (4) of VI.4.2: full-faithfulness is inherited from the underlying-categories statement; the
fibre-surjectivity follows from transportability of `p` plus the essential surjectivity of `f`. ∎

The transportability hypothesis is mild — every fibred category in groupoids satisfies it (file 36 §VI.6.1) — but it is
not automatic.

### VI.4.5 — Hom-categories under `ℰ`-equivalence

<!-- source: VI.4.5 -->

*This result says: an `ℰ`-equivalence `f : ℱ → 𝒢` induces equivalences of `ℰ`-functor categories
`Hom_{ℰ/-}(𝒢, ℋ) ≃ Hom_{ℰ/-}(ℱ, ℋ)`and`Hom_{ℰ/-}(ℋ, ℱ) ≃ Hom_{ℰ/-}(ℋ, 𝒢)`for every other`ℰ`-category `ℋ`.*

**Corollary.** Let `f : ℱ → 𝒢` be an `ℰ`-equivalence. For every `ℰ`-category `ℋ`, the functors

```text
f^*  :  Hom_{ℰ/-}(𝒢, ℋ)  →  Hom_{ℰ/-}(ℱ, ℋ),    G ↦ G ∘ f,
f_*  :  Hom_{ℰ/-}(ℋ, ℱ)  →  Hom_{ℰ/-}(ℋ, 𝒢),    H ↦ f ∘ H,
```

are equivalences of categories.

**Proof.** Compose with the `ℰ`-quasi-inverse `g` of `f` from condition (1) of VI.4.2 to get a quasi-inverse on either
side. ∎

This is the "Yoneda" content of `ℰ`-equivalence: it does not just mean "equivalent", it means equivalent in a way that
preserves all the categorical mapping data over `ℰ`.

## §VI.5 Cartesian morphisms, inverse images, cartesian functors

<!-- source: VI.5 -->

The protagonist of the exposé. Let `(ℱ, p)` be an `ℰ`-category and consider a morphism `α : η → ξ` in `ℱ` over
`f := p(α) : T → S`.

### Motivation

Take `ℰ = (Sch / S₀)` (`S`-schemes for some base `S₀`) and `ℱ = (Sch / S₀)^→` (the arrow category, with target functor
to `ℰ`). An object of `ℱ` is a pair `(X, X → Y)` (a scheme with a distinguished morphism to its image in `ℰ`). A
morphism `α : (X', X' → Y') → (X, X → Y)` in `ℱ` is a square

```text
X'  →  X
↓      ↓
Y'  →  Y.
```

When the square is a _pullback square_, the universal property is: for any other map `X'' → X` over `Y' → Y`, there is a
unique factorisation `X'' → X' → X`. This is the classical "`X'` is the pullback `X ×_Y Y'`". The map `α` represents the
pullback, and the universal property is exactly that the hom-functor `Hom_{Sch/Y'}(–, X')` is naturally isomorphic to a
"hom over `f`" functor `Hom_f(–, X)`.

§VI.5.1 abstracts this universal property to any `ℰ`-category.

### VI.5.1 — Definition: cartesian morphism, inverse image

<!-- source: VI.5.1 -->

_This result says: a morphism `α : η → ξ` in `ℱ` is **cartesian over `f`** when the pair `(η, α)` represents the functor
`η' ↦ Hom_f(η', ξ)` from `ℱ_T°` to `Set`. Equivalently: every other `f`-morphism into `ξ` factors uniquely through `α`
after restriction to a `T`-morphism. When such an `(η, α)` exists, it is unique up to unique `T`-isomorphism, and `η` is
called the **inverse image** `f*(ξ)` of `ξ` along `f`._

**Definition.** A morphism `α : η → ξ` in `ℱ` is **cartesian** (over `f := p(α) : T → S`) if, for every `η' ∈ Ob ℱ_T`
and every `f`-morphism `u : η' → ξ`, there exists a _unique_ `T`-morphism `ū : η' → η` such that `u = α ∘ ū`.
Equivalently: the precomposition map

```text
α_* : Hom_T(η', η)  ⟶  Hom_f(η', ξ),    v ↦ α ∘ v,
```

is bijective for every `η' ∈ Ob ℱ_T`.

**Inverse image.** When such a pair `(η, α)` exists, `η` is unique in `ℱ_T` up to canonical `T`-isomorphism. We call `η`
_an_ **inverse image** of `ξ` along `f`, written `f*(ξ)` or `ξ ×_S T` when no confusion arises. The chosen `α` is
denoted `α_f(ξ) : f*(ξ) → ξ`.

When the inverse image of every `ξ ∈ Ob ℱ_S` exists, the assignment `ξ ↦ f*(ξ)` becomes a functor `f* : ℱ_S → ℱ_T`
(covariant), called the **inverse-image functor** along `f`. Functoriality on morphisms: for `λ : ξ → ξ'` an
`S`-morphism and chosen cartesian morphisms `α_f(ξ) : f*(ξ) → ξ`, `α_f(ξ') : f*(ξ') → ξ'`, there is a unique
`T`-morphism `f*(λ) : f*(ξ) → f*(ξ')` making the obvious square commute.

> **In quasi-coherent modules** (`ℰ = Sch`, `ℱ_S = QCoh(S)`). For `f : T → S` and a quasi-coherent module `M` on `S`,
> the inverse image is the usual pullback sheaf `f*(M) = f^{-1}M ⊗_{f^{-1}𝒪_S} 𝒪_T`. The cartesian morphism
> `α_f(M) : f*(M) → M` is the canonical map in the sheaf category, and the universal property of VI.5.1 unpacks to the
> universal property of pullback. The inverse-image functor `f* : QCoh(S) → QCoh(T)` is the standard pullback of
> quasi-coherent sheaves. We will return to this example in §VI.11(b) and again in file 40 §VIII.1, where the QCoh
> fibred category is the protagonist.

### Properties of cartesian morphisms

Two facts we use without comment:

- **Stability under isomorphism.** If `α : η → ξ` is cartesian over `f`, and `μ : η' → η` is a `T`-isomorphism,
    `λ : ξ → ξ'` is an `S`-isomorphism, then `λ ∘ α ∘ μ⁻¹` is cartesian over `f`.
- **Composition pasting (anticipating VI.6.1's Fib II).** If `α : η → ξ` is cartesian over `f` and `β : ζ → η` is
    cartesian over `g`, then `α ∘ β : ζ → ξ` is cartesian over `f ∘ g` _iff_ a certain coherence holds. (The "iff" is
    what Fib II asserts; not every prefibred category is fibred. This will be the point of file 36 §VI.6.1.)

### VI.5.2 — Definition: cartesian functor

<!-- source: VI.5.2 -->

_This result says: an `ℰ`-functor `F : ℱ → 𝒢` is **cartesian** when it sends cartesian morphisms to cartesian morphisms.
Cartesian functors form a full subcategory `Hom_cart(ℱ, 𝒢) ⊂ Hom_{ℰ/-}(ℱ, 𝒢)`._

**Definition.** An `ℰ`-functor `F : ℱ → 𝒢` is a **cartesian functor** if, for every cartesian morphism `α` in `ℱ`, the
image `F(α)` is cartesian in `𝒢`. We write `Hom_cart(ℱ, 𝒢)` for the full subcategory of `Hom_{ℰ/-}(ℱ, 𝒢)` whose objects
are cartesian functors.

(Why "full"? Because the cartesianness is a property of objects — functors — not of morphisms. Every `ℰ`-natural
transformation between two cartesian functors is allowed; no extra restriction is imposed on 2-cells.)

The interpretation: cartesian functors are those that "respect the inverse-image structure" — they preserve the
universal property that defines `f*(ξ)` from `ξ`. Equivalently, when both `ℱ` and `𝒢` have inverse-image functors
`f*_ℱ : ℱ_S → ℱ_T` and `f*_𝒢 : 𝒢_S → 𝒢_T`, a cartesian functor `F : ℱ → 𝒢` provides a _natural isomorphism_
`F ∘ f*_ℱ ≅ f*_𝒢 ∘ F` (file 37 §VI.8 will make this 2-cell explicit).

### VI.5.3 — `ℰ`-equivalences are cartesian

<!-- source: VI.5.3 -->

_This result says: every `ℰ`-equivalence is automatically a cartesian functor; cartesianness is invariant under
`ℰ`-natural isomorphism; composites of cartesian functors are cartesian. So `Hom_cart` is a sensible 2-categorical
sub-structure of `Hom_{ℰ/-}`._

**Proposition.**

1. Every `ℰ`-equivalence `F : ℱ → 𝒢` is a cartesian functor. Moreover, a morphism `α` in `ℱ` is cartesian iff `F(α)` is
    cartesian.
1. If `F, G : ℱ → 𝒢` are isomorphic `ℰ`-functors and `F` is cartesian, then `G` is cartesian.
1. If `F : ℱ → 𝒢` and `F' : 𝒢 → ℋ` are cartesian, then `F' ∘ F : ℱ → ℋ` is cartesian.

**Proof.** (3) is immediate from the definition. (2) follows from the stability-under-isomorphism property of cartesian
morphisms. (1) follows from criterion (3) of VI.4.2: an `ℰ`-equivalence induces equivalences `f_S : ℱ_S → 𝒢_S` on every
fibre, so the universal property of `α : η → ξ` in `ℱ_T` translates to the universal property of `F(α) : F(η) → F(ξ)` in
`𝒢_T` via the equivalence. ∎

### VI.5.4 — Hom_cart is invariant under `ℰ`-equivalence

<!-- source: VI.5.4 -->

_This result says: an `ℰ`-equivalence induces equivalences not just of `ℰ`-functor categories (VI.4.5) but of the
cartesian- functor subcategories. So the fundamental structure `Hom_cart(–, –)` is preserved by `ℰ`-equivalences._

**Corollary.** Let `F : ℱ → 𝒢` be an `ℰ`-equivalence. For every `ℰ`-category `ℋ`, the functors

```text
F^*  :  Hom_cart(𝒢, ℋ)  →  Hom_cart(ℱ, ℋ),    G ↦ G ∘ F,
F_*  :  Hom_cart(ℋ, ℱ)  →  Hom_cart(ℋ, 𝒢),    H ↦ F ∘ H,
```

are equivalences of categories. Furthermore, `G : 𝒢 → ℋ` is cartesian iff `G ∘ F` is cartesian; `H : ℋ → ℱ` is cartesian
iff `F ∘ H` is cartesian.

**Proof.** Apply VI.4.5 to get equivalences of `Hom_{ℰ/-}`, then restrict to the cartesian subcategories using VI.5.3
(1)–(3). ∎

A consequence we will use in file 37: there is a sub-2-category `Cat^{cart}_{/ ℰ} ⊆ Cat_{/ ℰ}` whose objects are
arbitrary `ℰ`-categories, whose 1-cells are cartesian functors, and whose 2-cells are `ℰ`-natural transformations. The
composition pairings of §VI.2 restrict to it.

### VI.5.5 — Cartesian sections

<!-- source: VI.5.5 -->

_This result says: the cartesian sections of `(ℱ, p)` over `ℰ` form a category, denoted `Lim←(ℱ / ℰ)`, which is
functorial (covariantly) in `ℱ`._

**Definition.** Let `(ℱ, p)` be an `ℰ`-category. A **cartesian section** of `ℱ` over `ℰ` is a cartesian `ℰ`-functor
`s : ℰ → ℱ` (viewing `ℰ` as an `ℰ`-category via `id_ℰ`). The category of cartesian sections is

```text
Lim←(ℱ / ℰ)  =  Hom_cart(ℰ, ℱ)
```

— a sub-category of `Γ(ℱ / ℰ)̲ = Hom_{ℰ/-}(ℰ, ℱ)`.

By VI.5.4, `Lim←(– / ℰ)` is a functor `Cat^{cart}_{/ ℰ} → Cat`.

**Why "Lim←"?** Grothendieck's notation reflects the slogan that cartesian sections compute the _projective limit_ of a
fibred category over `ℰ`: the values `s(S) ∈ ℱ_S` together with the cartesian transition data form a coherent system,
and the universal such system is the cartesian section. We will see this slogan again in file 38 §VI.12: a cartesian
section is a "compatible family of fibre-wise objects" — exactly the data of descent.

## Worked example: the arrow category `Ar(Sch / S)`

The example we have alluded to throughout, made fully explicit. Fix a base scheme `S₀` and let `ℰ = (Sch / S₀)`, the
category of `S₀`-schemes. Define

```text
ℱ  =  Ar(ℰ)  =  Hom(Δ¹, ℰ)
```

— the arrow category of `ℰ`. An object of `ℱ` is a morphism `X → Y` of `S₀`-schemes; a morphism in `ℱ` from `(X' → Y')`
to `(X → Y)` is a commutative square

```text
X'  --u--> X
↓          ↓
Y'  --f--> Y.
```

The projection `p : ℱ → ℰ` sends `(X → Y) ↦ Y` and a square to the bottom row `f`.

**Fibre over `Y`.** `ℱ_Y = (Sch / Y)`, the slice category over`Y`. (Objects are`S₀`-schemes mapping to`Y`; morphisms
are`Y`-morphisms.)

**`ℰ`-functors and `ℰ`-natural transformations.** An `ℰ`-functor `Ar(ℰ) → Ar(ℰ)` over`ℰ`is a functor that, on each
fibre, sends`Y`-schemes to`Y`-schemes (because it must preserve the projection to`Y`). The identity is one such; so is
"take the fibre product with a fixed`Y`-scheme`Z`":`(X → Y) ↦ (X ×_Y Z → Y)`.

**Cartesian morphisms.** A square

```text
X'  --u--> X
↓          ↓
Y'  --f--> Y
```

is cartesian (over `f`) iff the square is a _pullback square_ of schemes. This is exactly the universal property: for
any `Y'`-scheme `X''` and any morphism `X'' → X` over `f`, there is a unique factorisation `X'' → X' → X`.

**Inverse-image functor.** For `f : Y' → Y` in`ℰ`, the inverse-image functor`f^* : ℱ_Y → ℱ_{Y'}`is the standard base
change:`(X → Y) ↦ (X ×_Y Y' → Y')`. The inverse images exist for *every* morphism`f`and *every* object`(X → Y) ∈ ℱ_Y`,
because fibre products of schemes always exist. So`Ar(ℰ)` is *prefibred* over `ℰ` — Fib I holds (file 36 §VI.6.1).

**Cartesian functors.** A functor `F : Ar(ℰ) → Ar(ℰ)` over `ℰ` is cartesian iff it commutes with base change (up to
canonical iso). The identity is cartesian; "fibre product with a fixed scheme `Z` over `S₀`",
`(X → Y) ↦ (X ×_{S₀} Z → Y)`, is cartesian (it sends pullback squares to pullback squares).

**Cartesian sections.** `Lim←(Ar(ℰ) / ℰ)` is the category of cartesian sections`s : ℰ → Ar(ℰ)`. A section assigns, to
each `Y ∈ Ob ℰ`, an object `(s(Y) → Y) ∈ Ar(ℰ)_Y`, and to each `f : Y' → Y` a square. Cartesianness says every such
square is a pullback square. So a cartesian section is the same as: a single object `X → S₀` in `Ar(ℰ)_{S₀}` such that
every fibre`s(Y) = X ×_{S₀} Y`, with cartesian transition squares. _That is: a cartesian section is determined by its
value at the terminal object `S₀ ∈ Ob ℰ`._

This worked example will recur in files 36, 37, 38 (where it becomes file 38 §VI.11(a)).

## Continuing on

File 36 takes the next step: the **fibred category** axioms (Fib I, Fib II) demand that the inverse-image functors
_exist for every morphism_ (Fib I) _and that they compose well_ (Fib II). The arrow category above satisfies both — it
is fibred. In general, prefibred (Fib I alone) is not the same as fibred (Fib I + Fib II), and the "well" of Fib II is
exactly what file 36's **cleavages** organise into a coherent system.
