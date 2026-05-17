# Exposé VI §§11–12 (gentle): examples and the descent isomorphism

## What this file is about

Local data plus gluing instructions ought to determine global data. A surface is built from charts and overlap rules. A
vector field on a manifold is given chart by chart together with how the local pieces transform across overlaps. The
slogan is reassuring, but the precise statement — when exactly does fibre-wise data plus compatibility produce a single
object above? — has been deferred all through the framework. Examples first. The geometric instances that drove the
abstraction in the previous files: families of maps, sheaves on varying spaces, modules over varying rings, and
finite-cover data over schemes.

Then the slogan becomes a theorem. For a fibred category of any kind, the category of functors out of the whole
structure is canonically the same as the category of fibre-wise data equipped with gluing compatibility and a cocycle
law. This is the descent isomorphism. Every later faithfully-flat descent result — for modules, for sheaves, for
morphisms of schemes — is this single isomorphism specialised to a particular setting. The cost paid is purely formal: a
cocycle condition controls how local data agrees on triple overlaps. The payoff is one statement that covers many.

## Opening: from framework to descent

A global object on a fibred category is determined by local data on each fibre, plus gluing instructions across the
base, plus a cocycle condition on triple overlaps. That is the descent isomorphism, and §VI.12 states it once and for
all. Every later faithfully-flat descent theorem — for modules, sheaves, morphisms of schemes — is this one isomorphism
specialised.

Files 35–37 set up the apparatus. **§VI.11** collects the examples that show the apparatus was worth setting up — seven
sub-examples (a)–(g) ranging from the running arrow category through presheaves / sheaves on variable spaces to the
two-object base. **§VI.12** distils the entire formalism into a single isomorphism (VI.12.1):

> For a normalised cloven `ℰ`-category `ℱ` and any target category `𝒞`, the category `Hom(ℱ, 𝒞)` of _functors out of
> `ℱ`_ is canonically isomorphic to a category `ℋ(ℱ, 𝒞)` of _fibre-wise data plus coherence_.

This is the **descent isomorphism**: local data (functors `F_S` on each fibre `ℱ_S`), gluing instructions (natural
transformations `φ_f : F_T ∘ f^* ⟹ F_S`), and a cocycle condition.

SGA VI does not specialise the statement to schemes — that is **Exposé VIII**'s job. But the apparatus is already sharp:
every later "faithfully flat descent of modules / quasi-coherent sheaves / morphisms" theorem is a specialisation of
VI.12.1 to a particular cloven `ℱ` and a particular target `𝒞`. We close the file (and the present pass of the gentle
SGA project) with a forward pointer.

## §VI.11 Examples

<!-- source: VI.11 -->

We treat (a)–(g) at varying depth: (a) and (b) get a full walk-through (these are the examples we will reuse); (c)–(g)
get a short paragraph.

### a) Arrow categories `Ar(ℰ) = Hom(Δ¹, ℰ)`

The running example of the entire exposé (see file 35, file 36, file 37).

Take `Δ¹` to be the totally-ordered set `[0, 1]` viewed as a category (two objects `0, 1`; one non-identity arrow
`(0, 1) : 0 → 1`). The **arrow category** `Ar(ℰ)` is

```text
Ar(ℰ)  =  Hom(Δ¹, ℰ),
```

with objects = arrows of `ℰ` and morphisms = commutative squares. The two object inclusions `0, 1 : pt → Δ¹` give two
canonical functors

```text
Ar(ℰ)  --source-->  ℰ,        Ar(ℰ)  --target-->  ℰ.
```

For our running example we use the **target** projection. Then the fibre `Ar(ℰ)_S = ℰ_{/ S}` is the slice category of
`S`-objects.

**Bi-fibred when fibre products exist.** As we worked out in files 35–37: `Ar(ℰ)` is co-fibred with co-splitting (direct
image = composition: `f_*(η : Y → T) = (Y → T → S)`); it is prefibred iff fibre products exist in `ℰ` (inverse image =
base change: `f^*(ξ : X → S) = (X ×_S T → T)`); when both hold, it is bi-fibred (file 37 §VI.10.1). The coherence
isomorphism `c_{f, g}` for the cleavage of file 36 is the associativity of fibre products.

A morphism in `Ar(ℰ)` is in bijective correspondence with a commutative square

```text
Y  --u-->  X
↓v          ↓
T  --f-->  S.
```

The morphism is **cartesian** (over `f`) iff the square is a *pullback square* in`ℰ`. The morphism is **co-cartesian**
(over `v`) iff the upper arrow `u` is the identity (file 37 worked example).

**Specialisation to schemes.** When `ℰ = (Sch / S₀)`, the arrow category`Ar(ℰ) → ℰ` is bi-fibred (fibre products of
`S₀`-schemes always exist). This is the foundational fibred category that all later examples — quasi-coherent sheaves,
modules, finite étale covers — embed into or descend from.

### b) Presheaves and sheaves on variable spaces

Let `ℰ = Top` (or any category of "spaces" — topological, schemes with the étale site, etc.). For each `T ∈ Ob ℰ`, write
`𝒰(T)` for its category of opens (with inclusions). For a fixed target category `𝒞`, write `𝒫(T) = Hom(𝒰(T)°, 𝒞)` for
the category of`𝒞`-valued presheaves on `T`, and `𝒮h(T) ⊂ 𝒫(T)` for the full subcategory of sheaves (file 34 Module A).

**Direct image.** A continuous map `f : T → S` gives, via`U ↦ f⁻¹(U)`, a functor `𝒰(S) → 𝒰(T)`, and so a _push-forward_
functor

```text
f_*  :  𝒫(T)  →  𝒫(S),    (f_* P)(U)  =  P(f⁻¹(U)).
```

The push-forward of a sheaf is a sheaf (this is automatic from the definition; left exactness is preserved). So `f_*`
also restricts to`𝒮h(T) → 𝒮h(S)`.

**Functoriality is strict.** `(g f)_* = g_* f_*` holds *on the nose* (composition of preimages). So`S ↦ 𝒫(S)` is an
honest covariant functor `Top → Cat`. Equivalently, `S ↦ 𝒫(S)°` is a contravariant functor`Top → Cat`, hence by §VI.9 a
*split* category over `Top`.

**Inverse image is more delicate.** When the target `𝒞` admits small filtered colimits, the inverse image
`f^* : 𝒫(S) → 𝒫(T)` exists (left adjoint to `f_*`). For sheaves, however, the inverse image of a sheaf is *not in
general* a sheaf — one has to apply the sheafification functor. So while `𝒮h(–)` is a co-fibred subcategory of `𝒫(–)`,
the inclusion `𝒮h ↪ 𝒫` is **not a fibred subcategory** of the (fibred) category `𝒫°` over `Top°`. This is the
categorical reason why "the inverse image of a sheaf" notation `f^*` is a slight abuse — it is the *sheafification of
the inverse-image presheaf*, not the inverse-image presheaf itself.

**The general form.** SGA VI also describes the larger fibred category `Cat_{//𝒞}` over`Cat` from which `𝒫` is recovered
by base change along `Top° → Cat`,`S ↦ 𝒰(S)`. We name this for context and refer the interested reader to Vistoli §3.2
([`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained)).

### c) Objects-with-operators over an object-with-operators

Take a group `G` acting on the left on an object`S` of `ℰ`. Encode `G ↷ S` as a functor`λ : ℰ' → ℰ` from the one-object
groupoid `ℰ' = BG` to `ℰ`, with`λ` sending the unique object of `BG` to `S` and each`g ∈ G` to `g ⋅ • : S → S`.

Base-changing a fibred `ℱ → ℰ` along`λ` gives a fibred `ℱ' = ℱ ×_ℰ ℰ' → ℰ'`. By VI.6.9 (file 36), `ℱ'` inherits the
(pre)fibred structure. A cartesian section`s : ℰ' → ℱ'` is the same as an `ℰ`-functor `ℰ' → ℱ` over`λ`, which in this
case is a `G`-equivariant object `ξ ∈ ℱ_S` — an object with operators.

This is the categorical generalisation of file 30's `Y × E` formalism: the principal-covering data of file 30 §V.2.6 are
sections of an appropriate fibred category over`BG`.

### d) Pairs of quasi-inverse adjoint functors; autodualities

Let `ℰ` be the connected rigid groupoid with two objects`a, b` and a single non-identity isomorphism `f : a → b` (with
inverse `g = f⁻¹`). A normalised cloven category`ℱ → ℰ` is the same data as:

- two categories `ℱ_a, ℱ_b`,
- two functors `F = f^* : ℱ_b → ℱ_a` and`G = g^* : ℱ_a → ℱ_b`,
- two natural isomorphisms `c_{f, g} : F G ⟹ id_{ℱ_a}` and`c_{g, f} : G F ⟹ id_{ℱ_b}`,

with the pentagon B) of file 36 §VI.7.4 (applied to the composables `fgf` and`gfg`) automatically supplying the
adjunction triangle identities. So `(F, G)` is a quasi-inverse _adjoint equivalence_.

The **autoduality** specialisation: `ℱ_b = ℱ_a°`,`G = F°`, `c_{g, f} = c_{f, g}°`. An _autoduality_ on a category `𝒞` is
a functor`D : 𝒞 → 𝒞°` together with an iso `u : D D° ⟹ id_𝒞` satisfying `D(u(x)) = u(D(x))` for every`x`. Examples:
vector spaces with `D = (–)^*` and `u =` canonical biduality on finite-dimensional spaces.

### e) Discrete bases

If `ℰ` is a discrete category (only identity arrows), an`ℰ`-category `ℱ` is just an `Ob ℰ`-indexed family of categories
`(ℱ_i)_{i ∈ Ob ℰ}`. Every `ℰ`-category is automatically fibred (every `ℰ`-morphism is an identity, hence cartesian). One
has

```text
Hom_{ℰ/-}(ℱ, 𝒢)  ≅  ∏_i Hom(ℱ_i, 𝒢_i),
Lim←(ℱ / ℰ)  ≅  ∏_i ℱ_i.
```

A degenerate but useful case: it shows that the framework _reduces to_ the obvious thing when there is no base structure
to deal with.

### f) Two-object base with one non-identity arrow

`ℰ` has two objects`S, T` and one non-identity arrow `f : T → S`. An `ℰ`-category`ℱ` is determined by:

- two categories `ℱ_S, ℱ_T`,
- a bifunctor `H : ℱ_T° × ℱ_S → Set`, where`H(η, ξ) = Hom_f(η, ξ)` in `ℱ`.

`ℱ` is prefibred (= fibred, since the only base composition is trivial) iff`H(η, –)` is representable in `ξ` for every
`η` — i.e., iff`f^*` exists. Dually for co-prefibred.

This is the categorical compactification of "fibred categories over a single arrow are _correspondences_ `ℱ_S ⇢ ℱ_T`" —
the simplest non-trivial fibred-category situation.

### g) Constant fibre

Let `ℱ = 𝒞 × ℰ` with projection`pr₂ : ℱ → ℰ`. Then `ℱ` is both fibred and co-fibred over `ℰ`, with canonical splittings
corresponding to the constant functor`S ↦ 𝒞` (and likewise on `ℰ°`). The fibre `ℱ_S = 𝒞` for every`S`. One has

```text
Γ̲(ℱ / ℰ)  ≅  Hom(ℰ, 𝒞),
Lim←(ℱ / ℰ)  ⊆  Hom(ℰ, 𝒞)
```

— the latter being the full subcategory of functors `ℰ → 𝒞` sending every morphism to an isomorphism (i.e., factoring
through the localisation`ℰ → ℰ[ℰ⁻¹]`).

## §VI.12 Functors on a cloven category and the descent isomorphism

<!-- source: VI.12 -->

We arrive at the categorical heart of descent theory. Throughout, `ℱ → ℰ` is a normalised cloven category with cleavage
data `(f^*, α_f, c_{f, g})` as in file 36 §VI.7. Let `i_S : ℱ_S → ℱ` denote the inclusion of the fibre.

### Concrete reading: covers, gluings, triple overlaps

Before the abstract statement, the picture the abstract statement records.

Pick the running example **quasi-coherent modules**: `ℰ` is the category of schemes, `ℱ → ℰ` is the fibred category whose
fibre over a scheme `S` is the category of quasi-coherent `𝒪_S`-modules, and for a morphism `f : T → S` the inverse
image `f^*` is the usual pullback of quasi-coherent sheaves.

In this setting, descent data on a cover `{U_i → S}` of a scheme `S` is exactly what one's intuition expects.

- **Local pieces.** A quasi-coherent module `M_i` on each `U_i`.
- **Gluings on pairwise overlaps.** An isomorphism `φ_{ij} : M_j |_{U_i ×_S U_j} ≅ M_i |_{U_i ×_S U_j}` for each
    ordered pair `(i, j)`, telling how `M_i` and `M_j` are to be identified on the overlap. The convention here is
    that `φ_{ii} = id` and `φ_{ji} = φ_{ij}^{-1}`.
- **Cocycle condition on triple overlaps.** On the triple overlap `U_i ×_S U_j ×_S U_k`,

    ```text
    φ_{ij}  ∘  φ_{jk}  =  φ_{ik}.
    ```

    Going `k → j → i` agrees with going `k → i`. This is the obstruction to inconsistent gluings: if the cocycle
    identity fails, two different routes through the overlaps give two different identifications, and the local data
    cannot assemble.

The descent isomorphism VI.12.1 says: **giving such a triple `((M_i), (φ_{ij}))` satisfying the cocycle condition is the
same data as giving a single global quasi-coherent module `M` on `S`.** The forward direction is restriction: `M_i := M
|_{U_i}`, and the `φ_{ij}` are the canonical identifications. The backward direction is the substance — gluings that
agree on triple overlaps assemble to a unique global module.

The abstract statement below replaces "module" with "functor into a target category `𝒞`," and replaces "restriction to
`U_i`" with "the fibre-wise functor `F_S`," and replaces the pairwise gluings `φ_{ij}` with natural transformations
`φ_f` along base maps. The cocycle condition stays the same shape: it asks that two routes through the cleavage agree,
which is what the diagram in subsection b) below expresses for the natural transformations `φ_f`. Reading the abstract
statement, hold the QCoh picture in mind; the diagram of `φ_f`'s recovers the triple-overlap identity for `φ_{ij}`'s
under the dictionary

```text
covering map   U_i → S        ⟷    base morphism   f : T → S
restriction    M |_{U_i}       ⟷    inverse image   f^* M
overlap        U_i ×_S U_j     ⟷    composable pair g : U → T,  f : T → S
gluing         φ_{ij}           ⟷    natural transformation     φ_f
cocycle        φ_{ij} ∘ φ_{jk} ⟷    cocycle diagram of φ_f, φ_g, c_{f, g}.
```

This dictionary will resurface in file 40 §VIII.1, where descent specialises to quasi-coherent modules and the global
module is constructed concretely from `((M_i), (φ_{ij}))`. The abstract content of VI.12.1 is what makes that
construction work; here, we keep both readings in mind and prove the abstract version.

### Set-up: the functorial homomorphism `α_f`

The cleavage's transport morphisms `α_f(ξ) : f^*(ξ) → ξ` package into a natural transformation

```text
α_f  :  i_T ∘ f^*  ⟹  i_S    :   ℱ_S → ℱ.
```

Naturally in `ξ`, this is the data "the`f`-morphism component of the cleavage". When we apply any functor `F : ℱ → 𝒞` to
`α_f`, we get a natural transformation

```text
φ_f  :=  F * α_f    :    F_T ∘ f^*  ⟹  F_S    :   ℱ_S → 𝒞,
```

where `F_S := F ∘ i_S : ℱ_S → 𝒞` is the restriction of`F` to the fibre.

### The data `(F_S, φ_f)`

So every functor `F : ℱ → 𝒞` produces:

- a family `(F_S)_{S ∈ Ob ℰ}` of functors`F_S : ℱ_S → 𝒞`;
- a family `(φ_f)_{f ∈ Fl(ℰ)}` of natural transformations`φ_f : F_T ∘ f^* ⟹ F_S`.

These satisfy:

- **a) Normalisation.** `φ_{id_S} = id_{F_S}` (using the normalised-cleavage assumption that`α_{id_S} = id`).

- **b) Cocycle identity.** For composable `g : U → T` and`f : T → S` in `ℰ`, the diagram of natural transformations of
    functors `ℱ_S → 𝒞`

    ```text
    F_U ∘ g^* ∘ f^*    --F_U * c_{f, g}-->    F_U ∘ (fg)^*
         |                                          |
         φ_g * f^*                                  φ_{fg}
         ↓                                          ↓
    F_T ∘ f^*           --φ_f-->                   F_S
    ```

    commutes. This is the consistency between successive pull-backs (`g^* f^*` vs`(fg)^*`) and the way `F` assigns
    morphisms to the cleavage transports.

The cocycle identity b) is what makes "compatible families of fibre-wise functors" into something rigid enough to
recover the global functor `F`.

### Morphisms of `(F_S, φ_f)`

Given two functors `F, G : ℱ → 𝒞` with associated data`(F_S, φ_f)` and `(G_S, ψ_f)`, a natural transformation
`u : F ⟹ G` produces:

- a family `(u_S)_{S ∈ Ob ℰ}` of natural transformations`u_S : F_S ⟹ G_S`,

satisfying:

- **c) Compatibility with cleavage.** For every `f : T → S` in`ℰ`, the square

    ```text
    F_T ∘ f^*    --φ_f-->    F_S
         |                       |
         u_T * f^*                u_S
         ↓                       ↓
    G_T ∘ f^*    --ψ_f-->    G_S
    ```

    commutes.

### The category `ℋ(ℱ, 𝒞)`

We package the data into a category `ℋ(ℱ, 𝒞)`:

- **Objects:** pairs of families `((F_S)_{S ∈ Ob ℰ}, (φ_f)_{f ∈ Fl(ℰ)})` satisfying a) and b).
- **Morphisms:** families `(u_S)_{S ∈ Ob ℰ}` satisfying c).
- **Composition:** componentwise composition of natural transformations.

The construction `F ↦ ((F_S), (φ_f))` is a functor

```text
K  :  Hom(ℱ, 𝒞)  ⟶  ℋ(ℱ, 𝒞).
```

### VI.12.1 — The descent isomorphism

<!-- source: VI.12.1 -->

_This result says: the functor `K` is **an isomorphism of categories**. Every system `((F_S), (φ_f))` satisfying a) and
b) comes from a unique global functor `F : ℱ → 𝒞`; every compatible family `(u_S)` satisfying c) comes from a unique
natural transformation`u : F ⟹ G`. The categorical statement "functors out of `ℱ` are the same as compatible fibre-wise
data" is the **descent isomorphism**._

**Proposition.** The functor

```text
K  :  Hom(ℱ, 𝒞)  ⟶  ℋ(ℱ, 𝒞)
```

is an **isomorphism of categories**.

**Proof.** _Functoriality of `K`_ is clear from the construction.

_Fully faithful:_ for `F, G : ℱ → 𝒞`, the map`Hom(F, G) → Hom(K F, K G)` is trivially injective (a natural
transformation is determined by its components). It is surjective because condition c) in `ℋ(ℱ, 𝒞)` exactly says that
the family `(u_S(ξ))`, on objects of the fibres, extends to a natural transformation on`ℱ`: every `f`-morphism
`α : η → ξ` in`ℱ` factors uniquely as `α = α_f(ξ) ∘ ū` for a unique `T`-morphism`ū : η → f^*(ξ)` (file 35 §VI.5.1), and
so the value `u(α)` is determined by `u_T(ū)` (functoriality on the fibre`ℱ_T`) and `u_S(ξ)` together with `ψ_f` via
condition c).

_Bijective on objects:_ the surjectivity is the substantive content. Given `((F_S), (φ_f))` in`ℋ(ℱ, 𝒞)`, define
`F : ℱ → 𝒞` by

```text
F(ξ)  =  F_S(ξ)        for ξ ∈ Ob ℱ_S,
F(α_f(ξ) ∘ ū)  =  φ_f(ξ) ∘ F_T(ū)    for ū : η → f^*(ξ) a T-morphism.
```

_Functoriality of `F`_: every morphism `α : η → ξ` in`ℱ` over `f : T → S` factors uniquely as `α_f(ξ) ∘ ū` (file 35
§VI.5.1 again). Composability`F(u v) = F(u) F(v)` for `u : η → ξ` over `f` and`v : ζ → η` over `g` reduces to the
equality

```text
F(u) F(v)  =  φ_f(ξ)  ∘  F_T(u') v'    via the c_{f, g} pasting,
```

which holds by the cocycle identity b) (and by the definition of composition in the cloven-category construction of file
37 §VI.8).

The verification is the diagram

```text
F_U(ζ) ──F_U(v')──> F_U g^*(η) ──F_U g^*(u')──> F_U g^* f^*(ξ) ──F_U(c_{f,g}(ξ))──> F_U(fg)^*(ξ)
   ____________ F(v) ___________/                    | φ_g(f^*(ξ))                       | φ_{fg}(ξ)
                                                       ↓                                   ↓
                                          F_T(η) ──F_T(u')──> F_T f^*(ξ) ──φ_f(ξ)──> F_S(ξ).
```

The left triangle commutes by the definition of `F(v)`; the middle square commutes by naturality of`φ_g`; the right
square commutes by condition b). So the outer perimeter commutes, which is exactly `F(u v) = F(u) F(v)`. ∎

The slogan: **a global functor on a fibred category is the same data as fibre-wise functors plus a cocycle.**

### Refinement: `ℰ`-functors into a cloven target `𝒢`

When the target `𝒞` is itself a normalised cloven`ℰ`-category `𝒢` — say with cleavage `(f^*_𝒢, α^𝒢_f, c^𝒢_{f, g})` — and
we restrict to **`ℰ`-functors** `F : ℱ → 𝒢`, the descent isomorphism refines to use the cleavage of `𝒢` as well.

For each `f : T → S` in`ℰ`, the `f`-morphism `F(α_f(ξ))` in`𝒢` factors uniquely as `α^𝒢_f(F_S(ξ)) ∘ φ_f(ξ)` for a unique
`T`-morphism

```text
φ_f(ξ)  :  F_T(f^*_ℱ(ξ))  ⟶  f^*_𝒢(F_S(ξ)).
```

Naturally in `ξ`, this is

```text
φ_f  :  F_T ∘ f^*_ℱ  ⟹  f^*_𝒢 ∘ F_S    :   ℱ_S → 𝒢_T.
```

The data `(F_S, φ_f)` now satisfies:

- **a′)** `φ_{id_S} = id_{F_S}` (normalisation).

- **b′)** Compatibility with both cleavages: the diagram

    ```text
    F_U ∘ g^*_ℱ ∘ f^*_ℱ        --F_U * c^ℱ_{f, g}-->        F_U ∘ (fg)^*_ℱ
          |                                                       |
          φ_g * f^*_ℱ                                              φ_{fg}
          ↓                                                       ↓
    g^*_𝒢 ∘ F_T ∘ f^*_ℱ
          |
          g^*_𝒢 * φ_f
          ↓
    g^*_𝒢 ∘ f^*_𝒢 ∘ F_S        --c^𝒢_{f, g} * F_S-->        (fg)^*_𝒢 ∘ F_S
    ```

    commutes. The two pasting compositions reach `(fg)^*_𝒢 ∘ F_S` by tracking the`f`-pull-back through `F` in two ways.

The descent isomorphism extends: `ℰ`-functors`F : ℱ → 𝒢` correspond bijectively to systems `((F_S), (φ_f))` satisfying
a′) and b′). **Cartesian** `ℰ`-functors`F` correspond exactly to those systems for which every `φ_f` is an _isomorphism_
(rather than just a natural transformation).

We do not reproduce the (entirely parallel) verification.

### The remark of VI.12

Grothendieck closes the section with a remark we should internalise: _it is usually better to reason directly on fibred
categories without using explicit cleavages_. The cloven description is computable but imposes choices that pollute
intrinsic statements; the abstract fibred description is canonical. The descent isomorphism is therefore best read as a
_structural_ statement about `Hom_{ℱ, ℰ}(ℱ, 𝒞)`, not as a recipe for "construct`F` from cleavage data". This is the
philosophical point of file 37 §VI.9's "splittings rarely exist": in geometry, forcing a strict choice obscures the
natural picture.

## §VI.13 Bibliography

<!-- source: VI.13 -->

The exposé closes with two references, both to Grothendieck's own works:

- **[VI.1]** Grothendieck, _Sur quelques points d'algèbre homologique_, Tôhoku Math. J. **9** (1957), 119–221. The
    Tôhoku paper is the original source for abelian categories, derived functors, and the categorical infrastructure SGA
    VI draws on for its category-of-categories formalism (file 35 §VI.1).
- **[VI.2]** Grothendieck, _Technique de descente et théorèmes d'existence en géométrie algébrique I_, Séminaire
    Bourbaki 190, December 1959. The Bourbaki seminar that introduced fpqc descent of modules — already cited in our
    appendix as [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190). The geometric content of VI.2 is what
    Exposé VIII works out in full.

(Exposé VII does not exist in SGA 1 — Grothendieck reserved the number but never wrote the corresponding text.)

## Closing pointer: faithfully flat descent (Exposés VIII and IX)

The descent isomorphism VI.12.1 is the categorical core. Its geometric specialisations live in the next two exposés.

**Exposé VIII** — _Descente fidèlement plate_. The fibred category of _quasi-coherent sheaves_
`QCoh : (Sch / S₀)° → Cat` (file 34 Module C example 3, file 37 §VI.10 worked example) is equipped with the *fpqc
topology* on`(Sch / S₀)` (file 34 Module A). For an fpqc cover `T → S`, the *category* `QCoh(T)` together with its
inverse-image data along`T → S` classifies quasi-coherent sheaves on `S`. Concretely:

> A quasi-coherent sheaf on `S` is the same data as: a quasi-coherent sheaf on`T` together with a _descent datum_ — an
> isomorphism between its two pull-backs to `T ×_S T` satisfying the cocycle condition on `T ×_S T ×_S T`.

This is the special case of VI.12.1 in which `ℰ = (` a single arrow`T → S` in the fpqc site`)`, `ℱ = QCoh(–)`, and the
cocycle reduces to the cleanly visible "agreement on overlaps". The general fpqc-cover version follows by Čech- type
assembly.

**Exposé IX** — _Descente des morphismes étales_. The same machinery applied to the fibred category of finite étale
coverings (file 33 §V.7) over `(Sch / S₀)` gives:

> A finite étale cover of `S` is the same data as: a finite étale cover of`T` together with a descent datum on
> `T ×_S T`.

This is the precise version of "principal coverings descend along faithfully flat covers" that we cited via
[`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) in file 30 (V.2.6), file 31 (V.3.6), and file 33 (V.7).

The project's central toy examples line up. The principal covering `Spec ℤ[√2] → Spec ℤ[1/2]` (file 30, file 33) is a
fpqc cover; the descent datum for an arbitrary scheme`X / Spec ℤ[1/2]` along this cover is _exactly_ the `ℤ/2`-Galois
data that file 33 V.7 used to construct objects classified by `π₁(Spec ℤ[1/2], a)`. The Exposés VIII and IX statements
turn the working ad hoc descent of file 30 into a rigorous theorem.

A future pass of the gentle SGA project will rewrite Exposés VIII and IX. For now, the reader who wants the geometric
content of fpqc descent should open Vistoli's notes Ch. 4 or Poonen, _Rational Points on Varieties_, Ch. 4 — both modern
accounts that work out the descent statements via VI.12.1's machinery.

______________________________________________________________________

This closes Exposé VI in the gentle reading. The framework is in place; the geometric application is one exposé away.

The arc through six exposés:

- **Exposé I** (étale, file 12 closing). Étale = smooth + relative dimension `0`.
- **Exposé II** (smooth, file 16 closing). Smooth = locally étale over a polynomial scheme.
- **Exposé III** (formally smooth, file 22 closing). Formally smooth = lifting + cohomological vanishing.
- **Exposé IV** (flat, file 27 "Continuing on"). Flat = exactness of `M ⊗_A –`; flat morphisms are open; generic
    flatness is the spread-out theorem.
- **Exposé V** (étale fundamental group, file 33 "Closing the project"). The étale fundamental group `π₁(S, a)` is the
    Galois group of the universal finite étale cover.
- **Exposé VI** (fibred categories and descent, _this file_). A global functor on a fibred category is determined by its
    fibre-wise restrictions plus a cocycle.

The first five build the étale story to its global Galois statement; the sixth provides the framework that Exposés VIII
and IX (faithfully flat descent of modules and morphisms) then turn into a working geometric tool.
