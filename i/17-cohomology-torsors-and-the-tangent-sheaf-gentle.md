# Cohomology in low degrees, torsors, and the tangent sheaf (gentle prep for Exposé III)

## What this file is about

A familiar question in geometry asks how much local information determines a global object. Pick a covering of a space
by small patches. On each patch the answer to some question is easy. On the overlaps, the easy answers may disagree. The
disagreements form a kind of bookkeeping problem, and there is a standard apparatus for tracking when the local answers
fit together into a global one and, if they do not, how badly they fail.

This file sets that apparatus up in the small. Three groups of numbers attached to a covering measure, in turn, the
global sections, the principal-bundle-like objects sitting over the space, and the obstruction to gluing locally defined
structures into a single global structure. The later files in this batch use the third group to count the ways a smooth
shape over a thickened point can be extended one infinitesimal step further.

Files 19–22 walk Exposé III. Sections III.1–III.4 reuse machinery already in place: completions of local rings (file
04), formally smooth as a property of homomorphisms (defined inside file 19), infinitesimal neighborhoods (file 03).
Sections III.5–III.7 do not. They pivot to **sheaf cohomology in low degrees**, the classification of **torsors** by
`H¹`, and the appearance of `H²` as a **gluing obstruction** for lifting smooth schemes. They also use the **tangent
sheaf** `𝔤_{X/S}`, dual to the Kähler differentials `Ω¹_{X/S}` of file 03.

This file is the working survey. We do not redevelop sheaf cohomology from scratch; we set up just enough that the
cocycle calculations in files 21–22 land cleanly. A reader who already knows Liu Chapter 5 or Hartshorne Chapter III may
skim. A reader who has only the file-03 picture of sheaves should read carefully — this file does most of the conceptual
work, and files 21–22 then just apply it.

The slogan that runs through:

> **`H⁰` measures sections. `H¹` measures torsors. `H²` measures the obstruction to gluing local solutions into a global
> one.** Each step up adds one cocycle dimension; each step says something concrete you can compute on an open cover.

## Recap: what file 03 already gives us

A **sheaf** of abelian groups on a topological space `X` is a presheaf — a functor `F : Open(X)^op → Ab` — that
satisfies gluing: compatible local data assemble uniquely into global data. File 03 gives the full definition; here we
need only the gluing axiom in the form

```text
0 → F(X) → ∏_i F(U_i) ⇉ ∏_{i,j} F(U_i ∩ U_j),
```

an **equalizer** in `Ab`: a global section is exactly a tuple `(s_i)` of local sections, one per open in a cover
`𝔘 = (U_i)`, that agree on every overlap.

We will work with sheaves of `𝒪_X`-modules (almost always **quasi-coherent**, often **coherent**). The structure-sheaf
`𝒪_X` itself is a sheaf of rings; a quasi-coherent sheaf is what you get by sheafifying a module — locally `M̃` for some
`𝒪_X(U)`-module `M`. Coherent quasi-coherent on a noetherian scheme means `finitely generated as a module locally`, with
finitely generated relations.

File 03 also gives the **diagonal** `Δ_{X/Y} : X ↪ X ×_Y X` and its ideal sheaf, and the universal target of
`Y`-derivations `Ω¹_{X/Y}`. These re-enter at the end of this file when we define the tangent sheaf.

## `H⁰`, `H¹`, `H²` via Čech

### What cohomology is, in one paragraph

A short orientation before any formula. The setting is always a left-exact functor on sheaves — typically global
sections `F ↦ F(X)` — that fails to be right-exact. **Cohomology measures exactly that failure.** Given a short exact
sequence of sheaves `0 → F' → F → F'' → 0`, applying global sections produces a sequence

```text
0 → F'(X) → F(X) → F''(X)
```

that may not extend to a `0 → … → 0` at the right. The cohomology groups `H¹, H², …` fill the gap into a long exact
sequence. Concretely:

- `H⁰(X, F) = F(X)` is the global sections, the data the sheaf already gives you;
- `H¹(X, F)` measures the obstruction to gluing local sections to a global one — given a `F''`-section globally and
    `F'`-lifts on each piece of a cover, an `H¹`-class records whether the lifts agree on overlaps;
- `H²(X, F)` measures the obstruction to gluing the gluing data — given gluings on overlaps, an `H²`-class records
    whether they cohere on triple overlaps.

Higher `H^q` extend the pattern: `H^q` is the obstruction to gluing the data at depth `q − 1`. Every formula in this
file unpacks one of these slogans. **Čech cohomology** is one concrete recipe for computing the groups; it works
whenever the cover is sufficiently fine. We use it as a calculator.

The cleanest way to compute sheaf cohomology in low degrees is therefore **Čech cohomology** on an open cover. We define
it concretely; every formula in file 21 will be a Čech formula in disguise.

### The Čech complex

Fix a sheaf `F` of abelian groups on `X` and an open cover `𝔘 = (U_i)_{i ∈ I}` with a choice of total order on `I`. The
**Čech complex** `Č^•(𝔘, F)` is the cochain complex with

```text
Č^p(𝔘, F) = ∏_{i₀ < i₁ < ... < i_p} F(U_{i₀ i₁ ... i_p}),
```

where `U_{i₀ i₁ ... i_p} := U_{i₀} ∩ U_{i₁} ∩ ... ∩ U_{i_p}`. A `p`-cochain is a tuple of sections, one per `(p+1)`-fold
ordered intersection. The differential `d : Č^p → Č^{p+1}` is the alternating restriction:

```text
(dc)_{i₀ ... i_{p+1}} = Σ_{r=0}^{p+1} (−1)^r c_{i₀ ... î_r ... i_{p+1}}|_{U_{i₀ ... i_{p+1}}},
```

where the hat means "delete this index" and the restriction is to the smaller intersection that includes the new index.

**Čech cohomology of the cover:**

```text
Ȟ^p(𝔘, F) := H^p(Č^•(𝔘, F)) = ker(d_p) / im(d_{p−1}).
```

This is a cover-dependent computation. The **global** Čech cohomology `Ȟ^p(X, F)` is the colimit over refinements of
`𝔘`. On the schemes we care about — separated, with affine open covers whose intersections are again affine — every
cohomology group we will name is computable directly from a single affine cover; the colimit is a technicality we do not
need.

### `H⁰` is the gluing equalizer

In degree `0`, `Č⁰(𝔘, F) = ∏_i F(U_i)` and `Č¹(𝔘, F) = ∏_{i<j} F(U_{ij})`. The differential sends `(s_i)` to the family
`(s_j|_{U_{ij}} − s_i|_{U_{ij}})`. So `ker(d) ⊂ ∏_i F(U_i)` is exactly the set of compatible local sections — the
equalizer of the two restriction maps in the sheaf axiom.

Combining with the axiom itself:

```text
Ȟ⁰(𝔘, F) = F(X).
```

For any cover, `H⁰` is just global sections. Cohomology becomes non-trivial in degree `≥ 1`.

### `H¹` and Mayer-Vietoris

In degree `1`, a `1`-cochain is a family `(c_{ij})_{i<j}` with `c_{ij} ∈ F(U_{ij})`. It is a **`1`-cocycle** if its
differential in `Č²` vanishes, i.e. for every triple `i < j < k`,

```text
c_{jk}|_{U_{ijk}} − c_{ik}|_{U_{ijk}} + c_{ij}|_{U_{ijk}} = 0
```

(the **cocycle condition** on triple overlaps). It is a **`1`-coboundary** if there exists `(s_i)_i` with `s_i ∈ F(U_i)`
and `c_{ij} = s_j|_{U_{ij}} − s_i|_{U_{ij}}`. Then

```text
Ȟ¹(𝔘, F) = {1-cocycles} / {1-coboundaries}.
```

When `X = U ∪ V` is a two-element cover, the Čech complex collapses to the **Mayer-Vietoris sequence**

```text
0 → F(X) → F(U) ⊕ F(V) → F(U ∩ V) → Ȟ¹(𝔘, F) → 0.
```

`Ȟ¹` is exactly the failure of the restriction map `F(U) ⊕ F(V) → F(U ∩ V)` to be surjective — the failure of being able
to realize an arbitrary section on the overlap as a difference of sections from the two halves.

### `H²` and triple-overlap obstructions

In degree `2`, a `2`-cochain is a family `(c_{ijk})_{i<j<k}` with `c_{ijk} ∈ F(U_{ijk})`. The cocycle condition is on
`4`-fold overlaps:

```text
c_{jkl} − c_{ikl} + c_{ijl} − c_{ijk} = 0   on U_{ijkl}.
```

A `2`-coboundary is `c_{ijk} = b_{jk} − b_{ik} + b_{ij}` for some `1`-cochain `(b_{ij})`. We will not need the full
machinery of `Ȟ²`. We will need the special case where local data are given on each pair `U_{ij}` (an isomorphism
`f_{ji}` between two locally isomorphic schemes), and the failure of the cocycle relation `f_{kj} f_{ji} = f_{ki}`
produces a `2`-cocycle measuring **transitivity failure on triple overlaps**. This is exactly the shape of the
obstruction in §III.6.3 (file 21).

> _The slogan_: a `1`-cocycle is data on pairs that **almost glues** to a global object; a `2`-cocycle is data on
> triples that **almost cancels** out of a transitivity check. Both become trivial cohomology classes precisely when the
> gluing or cancellation actually goes through.

## Vanishing on affines (Serre)

The reason cohomology of quasi-coherent sheaves on schemes is **computable** is one foundational vanishing.

**Serre's theorem.** _For any affine scheme `X = Spec A` and any quasi-coherent `𝒪_X`-module `𝓕`,_

```text
H^i(X, 𝓕) = 0   for all i ≥ 1.
```

We treat this as a black box (`serre-affine-vanishing` row of the appendix; the original is Serre, _Faisceaux
algébriques cohérents_ III.3, also EGA III §1.3.1). The intuition: an affine has "enough global sections" to glue any
local quasi-coherent data; there is no room for higher obstruction.

This vanishing is the engine. Given any noetherian separated scheme `X` covered by affines `(U_i)` with all finite
intersections `U_{i₀ ... i_p}` again affine — which holds automatically on a separated scheme — the cohomology of any
quasi-coherent sheaf is computable from a single Čech complex. We make this precise next.

## Leray's acyclic-cover theorem

Sheaf cohomology has a derived-functor definition (`H^q(X, 𝓕) := R^q Γ(X, −)(𝓕)`) which we take as authoritative but
treat in the background. Čech cohomology of a particular cover is concrete and computable. The bridge:

**Leray's theorem.** *Let `F` be a sheaf of abelian groups on `X`, and let `𝔘 = (U_i)` be an open cover such that every
finite nonempty intersection `U_{i*0 ... i_p}`is`F`-acyclic, meaning `H^q(U_{i*0 ... i_p}, F) = 0`for all`q ≥ 1`. Then
the natural map*

```text
Ȟ^p(𝔘, F) ⟶ H^p(X, F)
```

_is an isomorphism for every `p`._

(Black box; appendix row `leray-acyclic-cover`; standard sources Godement II.5, EGA 0_III §12.4.)

For us: combine with Serre's vanishing. On a noetherian separated scheme `X` with an affine open cover `𝔘 = (U_i)`
(whose finite intersections are then again affine, by separation), every quasi-coherent sheaf `𝓕` is `𝓕`-acyclic on each
`U_{i₀ ... i_p}`. Leray then says

```text
Ȟ^p(𝔘, 𝓕) = H^p(X, 𝓕)  for every p.
```

Every cocycle calculation in file 21 takes place inside one such Čech complex on one such affine cover. We do not need
anything deeper.

## Principal homogeneous sheaves and `H¹`

Now the geometric meaning of `H¹`. Every cocycle calculation in §III.5 of file 21 is a 1-cocycle calculation, and the
reason is that the natural carrier of "extensions of a given morphism along a square-zero thickening" is a **torsor
under a sheaf of groups**.

### Definition

Let `𝒢` be a sheaf of (commutative) groups on `X`. A **formally principal homogeneous sheaf** under `𝒢`, also called a
**`𝒢`-torsor in formation**, is a sheaf `𝒫` of sets together with a sheaf-of-sets action

```text
𝒫 × 𝒢 ⟶ 𝒫
```

such that the natural map `𝒢 × 𝒫 → 𝒫 × 𝒫` sending `(g, p) ↦ (p · g, p)` is an **isomorphism** of sheaves of sets.
Concretely: on each open `U`, either `𝒫(U)` is empty or it is a torsor under `𝒢(U)` in the usual sense — a set on which
`𝒢(U)` acts simply transitively.

We say `𝒫` is a **principal homogeneous sheaf**, or simply a **torsor**, under `𝒢` if in addition every stalk `𝒫_x` is
nonempty. Equivalently: there is an open cover `(U_i)` on which `𝒫|_{U_i}` admits a section, i.e. is **trivial** in the
sense that one can choose a `𝒢|_{U_i}`-equivariant isomorphism `𝒫|_{U_i} ≃ 𝒢|_{U_i}` (with `𝒢` acting on itself by right
translation).

The terminology comes from Giraud's _Cohomologie non abélienne_; Grothendieck cites it explicitly in SGA 1 III.5.0. For
our purposes, "torsor under `𝒢`" and "principal homogeneous sheaf under `𝒢`" are interchangeable.

### From a torsor to a 1-cocycle

Let `𝒫` be a torsor under `𝒢`, trivial on a cover `(U_i)`. Pick a section `p_i ∈ 𝒫(U_i)` for each `i`. On every overlap
`U_{ij}` both `p_i` and `p_j` are sections of the same torsor `𝒫|_{U_{ij}}`, which by simple transitivity is just
`𝒢|_{U_{ij}}` once a section is chosen. So there is a unique `g_{ij} ∈ 𝒢(U_{ij})` with

```text
p_j|_{U_{ij}} = p_i|_{U_{ij}} · g_{ij}.
```

On a triple overlap `U_{ijk}` we apply this twice and once:

```text
p_k = p_j · g_{jk} = (p_i · g_{ij}) · g_{jk} = p_i · (g_{ij} · g_{jk}),
```

so `p_k = p_i · g_{ik}` gives **`g_{ik} = g_{ij} · g_{jk}`** on `U_{ijk}`. Writing the group additively (we are working
with sheaves of abelian groups), this is the cocycle condition

```text
g_{jk} − g_{ik} + g_{ij} = 0   on U_{ijk}.
```

So the `(g_{ij})` form a Čech 1-cocycle for `𝒢` on `𝔘`.

### From a 1-cocycle to a torsor

Conversely: given a 1-cocycle `(g_{ij})` for `𝒢` on a cover `(U_i)`, glue copies of `𝒢|_{U_i}` along the isomorphisms
"translation by `g_{ij}`" on each overlap. The cocycle condition is exactly the consistency required to make the gluing
well-defined on triple overlaps. The result is a sheaf `𝒫` with a `𝒢`-action, trivial on each `U_i`, hence a torsor.

### Isomorphic torsors and cohomologous cocycles

If two torsors `𝒫, 𝒫′` under `𝒢` are isomorphic over an open cover `(U_i)` via maps that may differ from the chosen
trivializations, the resulting cocycles `(g_{ij})` and `(g′_{ij})` differ by a coboundary
`g′_{ij} = g_{ij} + (h_j − h_i)` for some `(h_i)` with `h_i ∈ 𝒢(U_i)`. The verification is mechanical; the content is
that **isomorphism classes of trivializing data** correspond to **cohomology classes**.

### The classification: `{torsors under 𝒢} / iso ⟷ Ȟ¹(X, 𝒢)`

Combining all of the above:

> **Theorem (Giraud).** _The set of isomorphism classes of torsors under `𝒢` is in natural bijection with `Ȟ¹(X, 𝒢)`.
> The trivial class — `𝒢` acting on itself — corresponds to torsors that globally admit a section._

(For abelian `𝒢` this is in any standard cohomology textbook; the non-abelian generalization is Giraud's book. We treat
both as the black-box row `giraud-torsor`. The classifying claim is what Grothendieck appeals to in SGA 1
III.5.0–III.5.4.)

This is the geometric meaning of `H¹`: it is the **set of twisted forms** of `𝒢` itself — sheaves locally isomorphic to
`𝒢` but globally distinct, classified by how the local trivializations disagree on overlaps.

## `H²` as a gluing obstruction

The cohomology group `H²(X, 𝒢)` plays a different role. It is not the classification of objects; it is the **obstruction
to gluing locally given objects into a global one**. We now spell out the shape of this obstruction so the reader
recognizes it when it appears in §III.6.

### The local-data setup

Suppose we have a problem of the following form. On each pair `U_{ij}` of an open cover `(U_i)`, we are given an object
— say, two locally isomorphic schemes `X^i` and `X^j`, restricted to `U_{ij}` — together with an **isomorphism**

```text
f_{ji} : X^i|_{U_{ij}} ⟶ X^j|_{U_{ij}}.
```

We want to find a global object `X` whose restriction to each `U_i` is `X^i`, with the `f_{ji}` as the gluing
isomorphisms. The necessary condition is the **cocycle condition** on triple overlaps:

```text
f_{kj} ∘ f_{ji} = f_{ki}   on U_{ijk}.
```

This is a triple-overlap consistency. If it holds, gluing succeeds — this is the standard sheaf gluing argument promoted
from sections to objects with isomorphisms.

### The 2-cocycle

In general the `f_{ji}` are not unique: each is determined up to composition with an automorphism of the local object,
and the local object's automorphism sheaf — call it `𝒢` — is non-trivial. So the cocycle relation may **fail** by an
automorphism on each triple overlap:

```text
f_{ijk} := (f_{ki})⁻¹ ∘ f_{kj} ∘ f_{ji} ∈ 𝒢(U_{ijk}).
```

A short calculation (Grothendieck's "silly calculation," SGA 1 III.6.3) shows that the family `(f_{ijk})` is a 2-cocycle
for `𝒢` on the cover. It is a **coboundary** — i.e. its class in `H²(X, 𝒢)` is zero — exactly when one can adjust the
`f_{ji}` by sections `g_{ij} ∈ 𝒢(U_{ij})` so that the corrected `f_{ji} g_{ij}` satisfy the cocycle relation. That is,
**the obstruction class in `H²(X, 𝒢)` vanishes if and only if the local data glue**.

### What vanishing buys

If `[f_{ijk}] = 0` in `H²(X, 𝒢)`, then a global object `X` exists. The set of such global objects — modulo isomorphism
inducing the identity on every `U_i` — is then a torsor under `H¹(X, 𝒢)`, and hence (by the previous section) a
principal homogeneous space under `H¹(X, 𝒢)`.

In file 21 this is exactly the statement of Theorem III.6.3: for the lifting of a smooth scheme `X_n` to `X_{n+1}`, the
obstruction lives in `H²(X₀, 𝒢)` with `𝒢 = 𝔤_{X₀/S₀} ⊗ gr^{n+1}_{𝓘}(𝒪_S)`, and if it vanishes the set of lifts is a
principal homogeneous space under `H¹(X₀, 𝒢)`.

> _Why this works in practice._ On the schemes of interest — `X₀` separated, affine cover with affine intersections —
> Leray reduces every `H¹` and `H²` to a Čech computation, every Čech computation to a finite calculation in the global
> sections of `𝒢` on the various overlaps. The cohomological obstruction is not an abstract invariant; it is a 2-cocycle
> one can write down, at least in principle.

## The tangent sheaf

The remaining ingredient that files 21–22 use is the **tangent sheaf** `𝔤_{X/S}`. This is just the dual of the Kähler
differential sheaf `Ω¹_{X/S}` from file 03, packaged the right way.

### Recap from file 03: `Hom_B(Ω¹_{B/A}, M) = Der_A(B, M)`

For a ring map `A → B` and any `B`-module `M`, file 03 (the "What `Ω¹` represents abstractly" subsection) proved:

> *An `A`-linear derivation `δ : B → M` factors uniquely through the universal derivation
> `d : B → Ω¹_{B/A}`as`δ = ϕ ∘ d`for a unique`B`-module map `ϕ : Ω¹_{B/A} → M`.*

In symbols, `Hom_B(Ω¹_{B/A}, M) ≃ Der_A(B, M)` naturally in `M`. This is the universal property of `Ω¹`: it is the
universal target of `A`-linear derivations of `B`.

### The tangent sheaf `𝔤_{X/S}`

For a morphism `X → S` of schemes and a quasi-coherent `𝒪_X`-module `ℳ`, the **sheaf of `S`-derivations of `𝒪_X` into
`ℳ`** is the sheaf

```text
𝒟er_S(𝒪_X, ℳ) : U ⟼ Der_{𝒪_S(?)}(𝒪_X(U), ℳ(U))
```

(with the right base-ring on `S` chosen via the structure map; the construction is standard and globalizes the affine
case identification above). The universal property of the relative differentials sheaf `Ω¹_{X/S}` (constructed in file
03\) gives a canonical isomorphism

```text
𝒟er_S(𝒪_X, ℳ) ≃ ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, ℳ).
```

In particular, taking `ℳ = 𝒪_X`:

> **Definition.** _The **tangent sheaf** of `X` over `S` is the dual of the relative cotangent sheaf:_
>
> ```text
> 𝔤_{X/S} := ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, 𝒪_X) = 𝒟er_S(𝒪_X, 𝒪_X).
> ```

It is a quasi-coherent sheaf on `X`, the algebraic analogue of the classical tangent bundle. Its sections over an open
`U` are the `S`-derivations `𝒪_X(U) → 𝒪_X(U)`.

### Dual to `Ω¹` for smooth morphisms

When `X → S` is **smooth** of relative dimension `n` (file 14), file 15 proved that `Ω¹_{X/S}` is locally free of rank
`n`. Then `𝔤_{X/S}` is **also locally free of rank `n`**, dual to `Ω¹_{X/S}` in the sense of locally free sheaves:
pairing with `Ω¹_{X/S}` gives the rank-1 trivial line bundle. Conversely, for a smooth morphism `Ω¹_{X/S}` and `𝔤_{X/S}`
exchange roles under duality, and either one can play the part of "tangent data" depending on context.

The cohomology groups that appear in files 21–22 are uniformly of the form `H^q(X₀, 𝔤_{X₀/S₀} ⊗ ℳ)` for various
auxiliary tensoring with quasi-coherent `ℳ`. The reader should think of `𝔤_{X₀/S₀}` as **the local degrees of freedom
for infinitesimal moves of `X₀` over `S₀`** — exactly what the deformation-theoretic obstruction is measuring.

## What this prepares

We now have:

- **Čech cohomology** in low degrees on a separated noetherian scheme with an affine cover. By Serre's vanishing and
    Leray's theorem, this computes the derived-functor cohomology of any quasi-coherent sheaf.
- **`H¹` classifies torsors** (= principal homogeneous sheaves) under any sheaf of abelian groups. A torsor is "an
    object locally trivializable to the group itself."
- **`H²` measures gluing obstructions**: when local objects come with isomorphisms on overlaps that fail to compose
    correctly on triple overlaps by an automorphism, the class in `H²` of the resulting 2-cocycle of automorphisms is
    the obstruction to gluing globally.
- **The tangent sheaf** `𝔤_{X/S} = ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, 𝒪_X)` is the dual of relative differentials. For smooth `X / S` it
    is locally free of rank equal to the relative dimension.

These are the four ingredients file 21 stitches together. To preview:

- **§III.5** uses the H¹ classification: the sheaf `𝒫(g₀)` of extensions of a given morphism `g₀ : Y₀ → X` along a
    square-zero thickening `Y₀ ↪ Y` is a torsor under `𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^* Ω¹_{X/S}, 𝒥)`. Its class in `H¹(Y₀, 𝒢)` is
    the obstruction to extending `g₀` globally.
- **§III.6** uses the H² obstruction story. To lift a smooth `X_n / S_n` to a smooth `X_{n+1} / S_{n+1}`: locally, lifts
    exist (file 20, III.4.1); the local lifts come with isomorphisms on overlaps determined up to automorphisms in
    `𝒢 = 𝔤_{X₀/S₀} ⊗ gr^{n+1}_{𝓘}(𝒪_S)`; the resulting 2-cocycle's class in `H²(X₀, 𝒢)` is the obstruction to gluing
    them into a global lift.
- **§III.7** combines the obstruction theory with vanishing arguments. For a smooth proper **curve** over `k`, both
    `H²(X₀, 𝔤_{X₀/k})` and `H²(X₀, 𝒪_{X₀})` vanish for dimension reasons; the curve lifts to any complete local ring
    with residue field `k`.

## What to remember

- Sheaf cohomology in low degrees on a separated noetherian scheme is computable as **Čech cohomology** on any affine
    open cover.
- `H⁰(X, 𝓕) = Γ(X, 𝓕)` is global sections (the gluing equalizer).
- `H¹(X, 𝒢)` classifies **torsors** under a sheaf of (abelian) groups `𝒢`: principal homogeneous sheaves, locally
    isomorphic to `𝒢` itself but possibly globally non-trivial.
- `H²(X, 𝒢)` is the **obstruction class** when local objects with isomorphisms on overlaps fail to satisfy the
    triple-overlap cocycle. Vanishing of the class means the obstruction can be killed by adjusting the isomorphisms —
    the local objects glue.
- The **tangent sheaf** `𝔤_{X/S} = ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, 𝒪_X)` is the universal carrier of `S`-derivations of `𝒪_X`. For
    smooth `X / S` it is locally free of rank equal to the relative dimension.
- Files 21–22 will write down explicit `H¹` and `H²` cohomology classes; the calculations are concrete Čech bookkeeping
    on affine covers, made legitimate by Serre's vanishing and Leray's theorem.
