# Rewritten Exposé XII, section XII.1 — the analytification functor `X ↦ X^an`

<!-- source: XII.1 -->

## What this file is about

A complex algebraic variety has two natures. From one side it is a system of polynomial equations and the geometry those
equations cut out, handled with rings and ideals. From the other side it is a complex-analytic space, locally like a
chunk of complex Euclidean space, with neighbourhoods and convergent power series and the usual tools of complex
analysis. The two natures describe the same underlying set of points but reach it through different machinery. The
question is how to set up a precise translation between them, so that any statement on one side has a counterpart on the
other. This file builds that translation, point by point, and shows that locally — after passing to the finest possible
neighbourhood of each point — the two descriptions carry exactly the same information.

Files 52–56 closed Exposé XI with the algebraic side of the étale `π₁` story carried to its sharpest limits. We computed
`π₁(ℙ^r) = 0` and threaded it out through the rational, unirational, and rationally connected hierarchies (file 52). We
computed `π₁(A) ≃ T·(A)` for abelian varieties and gave a gentle treatment of Nori's true fundamental group scheme (file
53). We exhibited sharp counterexamples to the X.1.3 / X.2.4 separability hypothesis through the projective-cone
construction and Zariski's Fermat-surface example (file 54). We built the descent-theoretic framework for principal
homogeneous bundles in the fpqc sense and the six-term cohomology exact sequence (file 55). And we fed the Kummer and
Artin–Schreier sequences into that machine to extract the Cartier-duality master formula
`H¹(S, G) ≃ Hom(D(G), Pic_{S/k})` (file 56).

Exposé XII now opens the second half of SGA 1's promised picture. The étale story we have been telling is purely
*algebraic*: schemes, ring maps, faithfully flat descent, no metric and no topology beyond Zariski. But for the most
important base field — `k = ℂ` — there is a parallel *analytic* story. To every `ℂ`-scheme `X` locally of finite type we
can attach a **complex analytic space** `X^an`, whose underlying set is `X(ℂ)` and whose structure sheaf `𝒪_{X^an}` is
the sheaf of holomorphic functions. The pairing `X ↦ X^an` is a functor; its first-named result, in this exposé, is the
**GAGA principle** — algebraic and analytic geometry over `ℂ` agree at the cohomological and fundamental-group level for
proper schemes. We split Exposé XII across four gentle files: this one (§XII.1, the analytification functor itself),
file 58 (§§XII.2–XII.3, the property dictionaries), file 59 (§XII.4, the cohomological GAGA theorem), and file 60
(§XII.5, the **Riemann existence theorem** and the analytic comparison of `π_1`).

This file (§XII.1) builds the functor `X ↦ X^an` from scratch. We give it the universal property that characterises it
(XII.1.1): `X^an` represents the functor `𝒳 ↦ Hom_ℂ(𝒳, X)` from complex analytic spaces to sets. The representing object
exists by gluing, with three building blocks — open subschemes, closed subschemes, and the affine line `𝔸^1_ℂ`. We
unpack the comparison morphism `φ : X^an → X` and prove its key local properties: it induces a bijection
`|X^an| ≃ X(ℂ)`, every local map `φ_x : 𝒪_{X, φ(x)} → 𝒪_{X^an, x}` becomes an isomorphism after passage to completions,
and consequently `φ` is *flat*. We make `X ↦ X^an` and `f ↦ f^an` into a functor commuting with finite projective limits
(XII.1.2), and we lift it to a functor `F ↦ F^an = φ*F` on `𝒪_X`-modules whose restriction to coherent sheaves is exact,
faithful, and conservative (XII.1.3, XII.1.3.1).

The slogan that emerges by the end of this file: **`X^an` is the analytic shadow of `X`.** A **closed point** of a
scheme is a point that is closed as a subset; in the algebraic geometry of varieties these are the classical points, and
for a scheme `Spec A` they correspond to the maximal ideals of `A`. The slogan: `X^an` carries the same local data as
`X` at every closed point, after passage to completions; the comparison morphism `φ` is locally as flat as one could
ask. The content of files 58–60 is then to upgrade this slogan from a local statement about completions to a global
statement about properties, cohomology, and fundamental groups.

______________________________________________________________________

## §XII.0 — Bridge: analytic spaces over `ℂ`

<!-- source: XII.1 -->

Before we can state what `X^an` is, we need a working definition of *complex analytic space*. The gentle SGA does not
develop the theory from scratch — that is the job of Gunning–Rossi or Grauert–Remmert. But we owe the reader a working
vocabulary for what we are about to do.

A **complex analytic space** is a locally-ringed space `(𝒳, 𝒪_𝒳)` over `ℂ` that is locally isomorphic to a **closed
analytic subspace** of an open subset `U ⊂ ℂⁿ`. A closed analytic subspace is the zero locus `Z(f_1, …, f_r) ⊂ U` of a
finite collection of holomorphic functions `f_1, …, f_r ∈ 𝒪(U)`, equipped with the sheaf of locally-defined holomorphic
functions modulo the ideal `(f_1, …, f_r)`. The structure sheaf `𝒪_𝒳` is, in this local picture, the quotient
`𝒪_U / (f_1, …, f_r) · 𝒪_U` restricted to the closed subset `Z(f_1, …, f_r)`.

Three things to keep in mind. First, complex analytic spaces are *locally-ringed* `ℂ`-spaces: each stalk `𝒪_{𝒳, x}` is a
local `ℂ`-algebra whose residue field is `ℂ`, and morphisms `(𝒳, 𝒪_𝒳) → (𝒴, 𝒪_𝒴)` are continuous maps together with
sheaf maps `𝒪_𝒴 → f_* 𝒪_𝒳` that respect localness. Second, the local stalks are *not* polynomial rings — they are rings
of convergent power series, henselian and complete in their `𝔪`-adic topology. The completion of `𝒪_{𝒳, x}` at the
maximal ideal is the formal power series ring `ℂ[[T_1, …, T_n]]` modulo the formal completion of `(f_1, …, f_r)`. Third
— and this is the **Oka coherence theorem**, the foundational result that licenses every later coherence statement — the
structure sheaf `𝒪_𝒳` is itself a coherent sheaf of rings (`oka-coherence`). Consequently the category of coherent
`𝒪_𝒳`-modules is closed under kernels, cokernels, finite direct sums, and tensor products, and the standard
sheaf-theoretic operations (pullback, pushforward along proper maps, `SheafHom`) preserve coherence under reasonable
hypotheses.

A **morphism of complex analytic spaces** `f : 𝒳 → 𝒴` is a morphism of locally-ringed `ℂ`-spaces; equivalently, a
continuous map `f_{top} : |𝒳| → |𝒴|` plus a sheaf map `f^# : 𝒪_𝒴 → f_* 𝒪_𝒳` such that the induced stalk maps are local
homomorphisms of local `ℂ`-algebras. We write `AnSp/ℂ` for the category of complex analytic spaces and `ℂ`-morphisms.

The fact that analytic spaces have fibre products in `AnSp/ℂ` is non-trivial. We will need it only locally — fibre
products of *affine analytic spaces* — and we cite Gunning–Rossi for the general construction.

#### The picture before XII.1.1.

We have on one side `Sch_{lft}/ℂ`, the category of `ℂ`-schemes locally of finite type. On the other side `AnSp/ℂ`,
complex analytic spaces. The XII.1 theorem-definition produces a functor

```text
Φ : Sch_{lft}/ℂ → AnSp/ℂ
       X ↦ X^an
```

with a natural transformation `φ : Φ ⇒ id_{LocRing/ℂ}` (where we view both categories as subcategories of locally-ringed
`ℂ`-spaces) — that is, a comparison morphism `φ_X : X^an → X` for every `X`. The functor `Φ` and the comparison morphism
are constructed simultaneously by representing a single functor, the **points functor**.

This is the moral content. The technical content is everything in §XII.1.1.

> *Working definition for the rest of the gentle SGA Exposé XII.* A complex analytic space is a locally-ringed `ℂ`-space
> locally modelled on `(Z(f_1, …, f_r), 𝒪_U / (f_i) · 𝒪_U)` for some open `U ⊂ ℂⁿ` and holomorphic `f_1, …, f_r ∈ 𝒪(U)`.
> The structure sheaf is coherent (Oka). Morphisms are sheaf maps respecting localness. Cohomology means sheaf
> cohomology of `𝒪_𝒳`-modules in the usual sense (Cartan's Theorem B vanishes it on Stein opens). See Gunning–Rossi or
> Grauert–Remmert (`gunning-rossi-analytic`, `grauert-remmert-coverings`) for the formal foundations.

______________________________________________________________________

## §XII.1.1 — Representability of analytification

<!-- source: XII.1.1 -->

### Theorem-Definition XII.1.1 — the analytic space associated with a `ℂ`-scheme

<!-- source: XII.1.1 -->

Let `X` be a `ℂ`-scheme locally of finite type. Define the **points functor**

```text
Φ_X : (AnSp/ℂ)^op → Set,         𝒳 ↦ Hom_{LocRing/ℂ}(𝒳, X),
```

where the right side is the set of morphisms of locally-ringed `ℂ`-spaces from `𝒳` to `X`.

**Theorem-Definition XII.1.1.** The functor `Φ_X` is representable. That is, there exists a complex analytic space
`X^an` and a morphism of locally-ringed `ℂ`-spaces

```text
φ = φ_X : X^an → X
```

such that for every analytic space `𝒳`, the canonical map

```text
Hom_{AnSp/ℂ}(𝒳, X^an) → Hom_{LocRing/ℂ}(𝒳, X),        ψ ↦ φ ∘ ψ,
```

is a bijection. The pair `(X^an, φ_X)` is unique up to unique isomorphism.

Moreover, `(X^an, φ_X)` has the following sharper local properties:

1. **Bijection on points.** The map `φ : |X^an| → |X|` induces a bijection between the underlying set `|X^an|` of `X^an`
    and the set `X(ℂ) ⊂ |X|` of `ℂ`-valued points of `X` (the closed points of `X` whose residue field is `ℂ`).
1. **Completion isomorphism.** For every point `x ∈ X^an`, the local map `φ_x : 𝒪_{X, φ(x)} → 𝒪_{X^an, x}` is a *local*
    homomorphism of local `ℂ`-algebras, and after passage to completions it becomes an isomorphism:

```text
φ̂_x : 𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}.
```

1. **Flatness.** Consequently `φ : X^an → X` is flat (every `φ_x` is flat because faithfully flat after completion).

*This result says:* the analytification is built once-and-for-all, glues over affine opens, and matches `X` exactly on
closed `ℂ`-points and after completion of every local ring. The data `(X^an, φ_X)` extracts from `X` precisely the
analytic-geometric information that `X` carries over `ℂ`.

#### Strategy of the proof.

We prove this in three building blocks. The first block (a) handles **subschemes**: if XII.1.1 holds for `Y`, then it
holds for every open subscheme and every closed subscheme of `Y`. The second block (b) handles **products**: if XII.1.1
holds for `X_1` and `X_2`, then it holds for `X_1 × X_2`. The third block (c) handles the **base case `X = 𝔸^1_ℂ`**
explicitly: we exhibit `(𝔸^1_ℂ)^an` as the topological space `ℂ` with its sheaf of holomorphic functions. From (b) and
(c) one deduces XII.1.1 for affine `n`-space `𝔸ⁿ_ℂ`. From (a) one deduces it for arbitrary affine `X` (which is a closed
subscheme of some `𝔸ⁿ_ℂ`). From (a) again — applied to *open* immersions and to the universal property — one then
deduces XII.1.1 for arbitrary `X` by gluing affine charts.

The completion isomorphism (2) is preserved by each step because it is local at every point. Flatness (3) is then
formal.

#### Block (a): reduction to subschemes.

<!-- source: XII.1.1 -->

Suppose XII.1.1 holds for `Y`: there exist `(Y^an, ψ : Y^an → Y)` representing `Φ_Y`, with bijection on `ℂ`-points and
completion isomorphism at every point. We must verify XII.1.1 for every subscheme `X ⊂ Y`.

**Sub-block (a1): open subscheme.** Let `X ⊂ Y` be an open subscheme. Define `X^an := ψ⁻¹(X) ⊂ Y^an`, an open subspace
of `Y^an` (with the induced analytic-space structure: open subset, restricted structure sheaf). Let
`φ := ψ|_{ψ⁻¹(X)} : X^an → X`.

We verify the universal property. Let `𝒳` be an analytic space and let `α : 𝒳 → X` be a morphism of locally-ringed
`ℂ`-spaces. The composition `𝒳 → X ↪ Y` is then a morphism of locally-ringed `ℂ`-spaces from `𝒳` to `Y`, and the
universal property of `Y^an` yields a unique lift `α̃ : 𝒳 → Y^an` with `ψ ∘ α̃ = α : 𝒳 → Y`. Since the image of `α̃`
lies inside `ψ⁻¹(X) = X^an` (a point `y ∈ 𝒳` maps to `α(y) ∈ X`, so `ψ(α̃(y)) ∈ X`, hence `α̃(y) ∈ ψ⁻¹(X)`), `α̃`
factors uniquely through `X^an`. This gives the bijection `Hom_{AnSp/ℂ}(𝒳, X^an) ≃ Hom_{LocRing/ℂ}(𝒳, X)`.

The bijection on `ℂ`-points and the completion isomorphism at every point are inherited from `Y^an`.

**Sub-block (a2): closed subscheme.** Let `X ⊂ Y` be a closed subscheme, defined by a coherent ideal sheaf `I ⊂ 𝒪_Y`.
Pull back along `ψ : Y^an → Y` to get the **analytic ideal sheaf** `I · 𝒪_{Y^an} ⊂ 𝒪_{Y^an}`. This is a coherent ideal
of `𝒪_{Y^an}` — coherent because `I` is coherent on `Y` and `𝒪_{Y^an}` is coherent (Oka, `oka-coherence`), so the
pullback `I · 𝒪_{Y^an}` is coherent. Define `X^an ⊂ Y^an` to be the closed analytic subspace cut out by `I · 𝒪_{Y^an}`,
with structure sheaf `𝒪_{Y^an} / I · 𝒪_{Y^an}` restricted to its support.

The morphism `φ : X^an → X` is the restriction of `ψ` to the closed analytic subspace, factored through `X ⊂ Y`.

We verify the universal property. Let `α : 𝒳 → X` be a morphism into the closed subscheme. Composing with `X ↪ Y` gives
a morphism `𝒳 → Y`, which lifts uniquely to `α̃ : 𝒳 → Y^an`. The image of `α̃` lies in the closed analytic subspace
defined by `I · 𝒪_{Y^an}` because `α` itself lands in the zero-locus of `I`. Hence `α̃` factors uniquely through `X^an`.

The completion isomorphism at a point `x ∈ X^an` is checked as follows. Let `y = ψ(x) ∈ X ⊂ Y`. The local map `φ_x` is
the composite

```text
𝒪_{X, y} = 𝒪_{Y, y} / I_y    →    𝒪_{X^an, x} = 𝒪_{Y^an, x} / I_y · 𝒪_{Y^an, x}.
```

After passage to completions this becomes

```text
𝒪̂_{Y, y} / I_y · 𝒪̂_{Y, y}    →    𝒪̂_{Y^an, x} / I_y · 𝒪̂_{Y^an, x},
```

an isomorphism because the underlying map `𝒪̂_{Y, y} → 𝒪̂_{Y^an, x}` is the iso `ψ̂_x`. The bijection on `ℂ`-points is
inherited.

> **Lemma (block a).** *If XII.1.1 holds for `Y`, it holds for every open and every closed subscheme of `Y`. Hence it
> holds for every subscheme of `Y`.*

#### Block (b): stability under products.

<!-- source: XII.1.1 -->

Suppose XII.1.1 holds for `X_1` and `X_2`. Let `φ_i : X_i^an → X_i` be the comparison morphisms. We claim that the
analytic-space product `X_1^an × X_2^an` (which exists in `AnSp/ℂ` by general nonsense + a local construction in
coordinate charts) together with the morphism

```text
φ := (φ_1 ∘ p_1, φ_2 ∘ p_2) : X_1^an × X_2^an → X_1 × X_2,
```

represents the functor `𝒳 ↦ Hom_{LocRing/ℂ}(𝒳, X_1 × X_2)`.

The proof is formal once we know that the scheme-theoretic product `X_1 × X_2` is also the product *in the larger
category of locally-ringed `ℂ`-spaces*. This fact is exactly **EGA I §1.8.1**: the fibre product of schemes in `LocRing`
(the category of locally-ringed spaces) coincides with the fibre product computed in `Sch`. Equivalently: the inclusion
`Sch_{lft}/ℂ ↪ LocRing/ℂ` preserves finite limits.

Granting EGA I §1.8.1, a morphism `α : 𝒳 → X_1 × X_2` in `LocRing/ℂ` is the same datum as a pair
`(α_1, α_2) : 𝒳 → X_1, 𝒳 → X_2`. By the universal property of `X_i^an`, each `α_i` lifts uniquely to
`α̃_i : 𝒳 → X_i^an`. The pair `(α̃_1, α̃_2)` defines a unique morphism `α̃ : 𝒳 → X_1^an × X_2^an` in `AnSp/ℂ` (via the
universal property of the analytic-space product). This gives the bijection
`Hom_{AnSp/ℂ}(𝒳, X_1^an × X_2^an) ≃ Hom_{LocRing/ℂ}(𝒳, X_1 × X_2)`.

The bijection on `ℂ`-points: `(X_1 × X_2)(ℂ) = X_1(ℂ) × X_2(ℂ)`, and similarly for analytic spaces, so
`|X_1^an × X_2^an| ≃ X_1(ℂ) × X_2(ℂ) ≃ (X_1 × X_2)(ℂ)`. The completion isomorphism at a point
`(x_1, x_2) ∈ X_1^an × X_2^an` is the tensor product of the completion isomorphisms at `x_1` and `x_2`.

> **Lemma (block b).** *If XII.1.1 holds for `X_1` and `X_2`, then it holds for `X_1 × X_2`.*

#### Block (c): the base case `X = 𝔸^1_ℂ`.

<!-- source: XII.1.1 -->

Let `X = 𝔸^1_ℂ = Spec ℂ[T]`. Define `𝓔^1 := (ℂ, 𝒪_hol)` — the topological space `ℂ` with its sheaf of holomorphic
functions. This is the standard one-dimensional complex affine space.

We claim that `(𝓔^1, φ_{𝔸^1})` represents the functor `Φ_{𝔸^1_ℂ}`, where `φ_{𝔸^1} : 𝓔^1 → 𝔸^1_ℂ` is the *evident*
morphism: on underlying sets, it is the bijection `|𝓔^1| = ℂ ≃ 𝔸^1(ℂ) = ℂ`; on structure sheaves, it sends the algebraic
function `T ∈ ℂ[T]` to its holomorphic incarnation `T ∈ 𝒪_hol(ℂ)`.

The universal property is essentially trivial: a morphism of locally-ringed `ℂ`-spaces `𝒳 → 𝔸^1_ℂ` is the same thing as
a `ℂ`-algebra map `ℂ[T] → Γ(𝒳, 𝒪_𝒳)`, which is the same thing as a section of `𝒪_𝒳` (the image of `T`). And a morphism
of locally-ringed `ℂ`-spaces `𝒳 → 𝓔^1` is also the same thing as a section of `𝒪_𝒳` (the holomorphic function on `𝒳`
obtained by pulling back the coordinate function on `ℂ`).

Hence

```text
Hom_{AnSp/ℂ}(𝒳, 𝓔^1) ≃ Γ(𝒳, 𝒪_𝒳) ≃ Hom_{LocRing/ℂ}(𝒳, 𝔸^1_ℂ).
```

The bijection `|𝓔^1| ≃ 𝔸^1(ℂ) = ℂ` is built into the construction.

The completion isomorphism at every point `x ∈ ℂ`: the local ring `𝒪_{𝔸^1, x} = ℂ[T]_{(T - x)}` has completion
`ℂ[[T - x]]`. The local ring `𝒪_{𝓔^1, x}` is the ring of germs of holomorphic functions at `x`, which is the ring of
*convergent* power series in `T - x`. Its completion is the formal power series ring `ℂ[[T - x]]`. The natural map
`ℂ[T]_{(T - x)} → ℂ\{T - x\} \to ℂ[[T - x]]` is the composition of inclusion and completion; after completion it is the
identity on `ℂ[[T - x]]`. So `φ̂_x` is the identity. ∎

> **Lemma (block c).** *XII.1.1 holds for `X = 𝔸^1_ℂ`, with `(𝔸^1_ℂ)^an = 𝓔^1 = (ℂ, 𝒪_hol)`.*

#### Assembling the proof of XII.1.1.

We now assemble blocks (a)–(c) to prove XII.1.1 for every `ℂ`-scheme `X` locally of finite type.

**Step 1: affine `n`-space `𝔸ⁿ_ℂ`.** By iterating block (b) starting from block (c), XII.1.1 holds for
`𝔸ⁿ_ℂ = 𝔸^1_ℂ × ⋯ × 𝔸^1_ℂ`. Explicitly: `(𝔸ⁿ_ℂ)^an = 𝓔ⁿ = (ℂⁿ, 𝒪_hol)`.

**Step 2: affine `ℂ`-schemes of finite type.** Every affine `ℂ`-scheme `X = Spec(ℂ[T_1, …, T_n] / I)` of finite type is
a closed subscheme of `𝔸ⁿ_ℂ`. By block (a) applied to `Y = 𝔸ⁿ_ℂ`, XII.1.1 holds for `X`. Explicitly: `X^an` is the
closed analytic subspace of `𝓔ⁿ` cut out by `I · 𝒪_{𝓔ⁿ}`.

**Step 3: gluing.** Let `X` be an arbitrary `ℂ`-scheme locally of finite type, and let `(U_i)_{i ∈ I}` be a covering of
`X` by affine opens. By Step 2, each `U_i^an` exists and satisfies XII.1.1. By block (a1) applied to each pair
`U_i ∩ U_j ⊂ U_i`, the analytic open `(U_i ∩ U_j)^an = φ_{U_i}^{-1}(U_i ∩ U_j) ⊂ U_i^an` exists and agrees with the
analytic open computed inside `U_j^an`. We can therefore glue the analytic spaces `U_i^an` along the analytic opens
`(U_i ∩ U_j)^an` to produce an analytic space `X^an` and a morphism `φ : X^an → X`. The universal property for `X^an`
follows: a morphism `α : 𝒳 → X` is determined by its restrictions to the open cover `α^{-1}(U_i)`, and each restriction
lifts uniquely to `α̃_i : α^{-1}(U_i) → U_i^an`, and these lifts glue.

The bijection on `ℂ`-points is local; the completion isomorphism at each point is local; both transfer to `X^an`.

This completes the proof of XII.1.1. ∎

> **Slogan.** *`X^an` is the analytic space whose underlying set is `X(ℂ)` and whose local rings at each closed point
> complete to the same formal power series ring as the local rings of `X`.* The functor `Φ : X ↦ X^an` is the universal
> locally-ringed-`ℂ`-space gadget that solves the points functor.

#### Aside (why the universal property is the right organising principle).

There is a tempting alternative construction of `X^an`: take the underlying set `X(ℂ)`, give it the analytic topology
inherited from a closed embedding of an affine chart into some `ℂⁿ`, and put on the result the sheaf of holomorphic
functions modulo the ideal. This works, and is what Serre 1956 did for projective varieties. The trouble is that
*naturality* — functoriality in `X` — and *coherence* across overlapping charts are then both extra work, with no clean
structural reason behind them.

The universal property packages all of this in one move. `X^an` *is* whatever locally-ringed-`ℂ`-space turns the points
functor `Hom_{LocRing/ℂ}(\_,X)` into an analytic-space representable. The functoriality `f ↦ f^an` is then *automatic*
(the next section, XII.1.2). The compatibility with subschemes (block a), with products (block b), and with affine
`n`-space (block c) are forced by representability. Everything we want from `X^an` is encoded in the universal property;
nothing else is.

This is the same organising principle that drives the construction of `Spec A`, of the product of schemes, of the
formal-scheme completion `X̂` (file 18), of the étale fundamental group `π₁(S, a)` (file 33), and of the Picard scheme
`Pic_{X/S}`. Each time, the moral is the same: build the functor first; let representability force the geometry.

______________________________________________________________________

## §XII.1.2 — Functoriality of analytification

<!-- source: XII.1.2 -->

The universal property in XII.1.1 immediately delivers functoriality. Given a morphism `f : X → Y` of `ℂ`-schemes
locally of finite type, consider the morphism of locally-ringed-`ℂ`-spaces

```text
f ∘ φ_X : X^an → X → Y.
```

By the universal property of `Y^an`, this morphism lifts to a unique morphism

```text
f^an : X^an → Y^an
```

such that `φ_Y ∘ f^an = f ∘ φ_X` — that is, the analytification square

```text
X^an --φ_X→  X
 |            |
f^an         f
 |            |
Y^an --φ_Y→  Y
```

is commutative. Uniqueness makes `(f, g) ↦ (f^an, g^an)` respect composition: `(g ∘ f)^an = g^an ∘ f^an`, `id^an = id`.
We have a functor

```text
Φ : Sch_{lft}/ℂ → AnSp/ℂ.
```

### Proposition XII.1.2 — `Φ` commutes with finite projective limits

<!-- source: XII.1.2 -->

**Proposition XII.1.2.** The functor `Φ : Sch_{lft}/ℂ → AnSp/ℂ` commutes with finite projective limits. In particular,
it commutes with fibre products:

```text
(X ×_Z Y)^an ≃ X^an ×_{Z^an} Y^an.
```

*This result says:* the analytification of a fibre product is the fibre product of the analytifications. The fibre
product on the right is computed in `AnSp/ℂ`.

**Proof.** It is enough to check the fibre-product case (a category with all finite limits is the same as a category
with terminal object and binary products of objects in a specific category-theoretic sense). Let `X`, `Y`, `Z` be
`ℂ`-schemes locally of finite type and let `X → Z`, `Y → Z` be morphisms.

By EGA I §1.8.1, the scheme-theoretic fibre product `X ×_Z Y` is also the fibre product in the larger category
`LocRing/ℂ`. So a morphism `α : 𝒳 → X ×_Z Y` in `LocRing/ℂ` is the same datum as a compatible pair
`(α_X : 𝒳 → X, α_Y : 𝒳 → Y)` of morphisms agreeing on `Z`. By the universal property of `X^an, Y^an, Z^an`, each
`α_X, α_Y, α_X ↓ Z, α_Y ↓ Z` lifts uniquely to the analytic side. The pair `(α̃_X, α̃_Y)` of analytic lifts then defines
a unique morphism `α̃ : 𝒳 → X^an ×_{Z^an} Y^an` (universal property of the analytic fibre product).

This proves that `X^an ×_{Z^an} Y^an` represents the functor `𝒳 ↦ Hom_{LocRing/ℂ}(𝒳, X ×_Z Y)`, which by XII.1.1 applied
to `X ×_Z Y` is the same as `Hom_{AnSp/ℂ}(𝒳, (X ×_Z Y)^an)`. By Yoneda, `(X ×_Z Y)^an ≃ X^an ×_{Z^an} Y^an`. ∎

> **Slogan.** *Analytification is a functor that respects fibre products.* In particular, it respects base change: the
> analytic space `(X ×_Z Z')^an` is the analytic-base-change `X^an ×_{Z^an} Z'^an`.

#### Aside (forgetting to check commutation with limits).

This proposition will be used in essentially every later argument of files 58–60 without further comment. The two most
important consequences are:

1. **The diagonal is preserved.** If `f : X → Y` is a morphism, its diagonal `Δ_{X/Y} : X → X ×_Y X` analytifies to
    `Δ_{X^an / Y^an} : X^an → X^an ×_{Y^an} X^an`. The fact that `f^an` is separated iff `Δ` is closed (for the
    analytic morphism) and the fact that `f` is separated iff `Δ` is closed (for the scheme morphism) is the XII.3.1
    (viii) iff — and it is preserved by XII.2.3 + XII.1.2 (file 58).
1. **Fibre `(f^{-1}(y))^an = (f^an)^{-1}(y)`.** This is the key compatibility that lets us reduce questions about fibres
    of `f^an` to questions about fibres of `f`, used throughout XII.3.

______________________________________________________________________

## §XII.1.3 — Sheaf-level analytification

<!-- source: XII.1.3 -->

We have built a functor `Φ : X ↦ X^an` on `ℂ`-schemes locally of finite type. The next step is to lift it to sheaves.
Given an `𝒪_X`-module `F`, the pullback along the analytification morphism `φ : X^an → X` is an `𝒪_{X^an}`-module:

```text
F^an := φ*F = (φ⁻¹F) ⊗_{φ⁻¹𝒪_X} 𝒪_{X^an}.
```

This defines a functor

```text
Φ^# : Mod(𝒪_X) → Mod(𝒪_{X^an}),    F ↦ F^an.
```

The basic properties of `F ↦ F^an` come from general nonsense about pullback functors. Two stand out:

1. **Inductive limits.** Because pullback is a left adjoint (to pushforward), `Φ^#` commutes with all inductive limits —
    direct sums, cokernels, filtered colimits, tensor products. The reference is EGA `0_I` 4.3.2.
1. **Coherent sheaves go to coherent sheaves.** This uses the fact that `𝒪_{X^an}` is itself a coherent sheaf of rings
    (Oka coherence, `oka-coherence`). The general statement (EGA `0_I` 5.3.11) is that if `f` is a morphism of
    locally-ringed spaces and the target structure sheaf is coherent, then `f*` carries coherent modules to coherent
    modules. We can therefore restrict `Φ^#` to coherent sheaves:

```text
Φ^#_{coh} : Coh(X) → Coh(X^an),    F ↦ F^an.
```

The substantive content of XII.1.3 is the next subproposition.

### Subproposition XII.1.3.1 — `F ↦ F^an` is exact, faithful, conservative on coherent sheaves

<!-- source: XII.1.3.1 -->

**Subproposition XII.1.3.1.** The functor `Φ^#_{coh} : Coh(X) → Coh(X^an)` is:

1. **exact** — sends short exact sequences of coherent sheaves to short exact sequences;
1. **faithful** — distinct morphisms `F → G` of coherent sheaves go to distinct morphisms `F^an → G^an`;
1. **conservative** — a morphism `f : F → G` of coherent sheaves whose analytification `f^an : F^an → G^an` is an
    isomorphism is itself an isomorphism.

*This result says:* on coherent sheaves, the analytification functor preserves everything `Coh(X)` carries as a abelian
category: kernels, cokernels, exact sequences, distinctness of morphisms, the property of being zero.

**Proof.**

**(1) Exactness.** A pullback functor `f*` is exact iff `f` is *flat* (this is the bridge between Tor-vanishing and
right-exactness of pullback). The flatness of `φ : X^an → X` was the third clause of XII.1.1. Hence `Φ^#` is exact on
all `𝒪_X`-modules, in particular on coherent ones.

**(2) Faithfulness.** Because `Φ^#` is exact, it sends `Hom_{𝒪_X}(F, G) ↪ Hom_{𝒪_{X^an}}(F^an, G^an)` to be injective
iff `Φ^#(F) = 0` implies `F = 0` (apply the cokernel of `f` to detect distinct morphisms). So it suffices to prove the
next clause:

**(2′) If `F^an = 0` then `F = 0`.** Suppose `F^an = (φ*F) = 0` as a sheaf on `X^an`. Pick any point `x ∈ X^an`, let
`y = φ(x) ∈ X`. Then `F^an_x = F_y ⊗_{𝒪_{X, y}} 𝒪_{X^an, x} = 0`. The local map `𝒪_{X, y} → 𝒪_{X^an, x}` is faithfully
flat: it is flat (a fortiori from completion-iso XII.1.1 (2): faithful flatness on completions plus
completion-faithful-flatness `𝒪_{X, y} → 𝒪̂_{X, y}` gives faithful flatness `𝒪_{X, y} → 𝒪̂_{X^an, x}`, which factors
through `𝒪_{X^an, x}`). So faithful flatness of the local map gives `F_y = 0`.

We have shown: `F_y = 0` for every `y ∈ φ(X^an) = X(ℂ)`, i.e. for every closed point `y` of `X` with residue field `ℂ`.
But `X` is a Jacobson scheme — and for a Jacobson scheme, *the closed points are very dense*: a coherent sheaf `F` is
zero iff it is zero at every closed point. The fact that `X / ℂ` locally of finite type is Jacobson is recorded as
`ega-iv-jacobson-nullstellensatz` (EGA IV §10.4.8). Hence `F = 0`.

**(3) Conservativeness.** Let `f : F → G` be a morphism of coherent sheaves on `X` such that `f^an` is an isomorphism.
Apply exactness to `0 → ker(f) → F → G → coker(f) → 0`: by exactness, the analytified sequence
`0 → (ker f)^an → F^an → G^an → (coker f)^an → 0` is exact. Since `f^an` is an iso, `(ker f)^an = 0` and
`(coker f)^an = 0`. By faithfulness (clause 2), `ker f = 0` and `coker f = 0`, so `f` is an iso.

This proves the three clauses. ∎

> **Slogan.** *The analytification functor on coherent sheaves loses no information about `F` itself.* What it *does*
> lose, in principle, is information about higher direct images `Rᵖf_*F` — these may or may not commute with
> analytification. The cohomological GAGA theorem (XII.4.2, file 59) says that *for `f` proper*, no information is lost
> there either.

#### Aside (the philosophy of XII.1.3.1).

This subproposition is the analytic incarnation of a recurring philosophical principle in scheme theory: *the
analytification functor sees enough.* The completion isomorphism XII.1.1 (2) tells us that `𝒪_{X^an, x}` remembers as
much about `X` as the formal completion `𝒪̂_{X, x}` does. The faithful flatness step in clause (2′) of the proof then
licenses propagation from completions back to `𝒪_{X, x}`. Jacobson then propagates from a single closed point to all of
`X`.

The full chain is:

```text
𝒪_{X, y}  ─inj→  𝒪̂_{X, y}  ─iso (XII.1.1)→  𝒪̂_{X^an, x}  ─inj←  𝒪_{X^an, x}.
```

The "inj" arrows are faithful flatness (`completion-flat` from file 17 and the analytic analogue). The "iso" arrow is
XII.1.1 (2). The composition is faithful flatness `𝒪_{X, y} → 𝒪_{X^an, x}`.

This is exactly the structural reason why everything in XII.2 and XII.3 (file 58) reduces to checking properties at
*closed points* and then transferring across the completion.

______________________________________________________________________

## §XII.1.4 — What is missing from XII.1

<!-- source: XII.1 -->

The functor `Φ : X ↦ X^an` has been constructed (XII.1.1). It is functorial (XII.1.2) and respects fibre products. It
lifts to a faithful exact conservative functor `Φ^#_{coh} : Coh(X) → Coh(X^an)` (XII.1.3, XII.1.3.1).

But three big questions remain unaddressed, and each is the subject of one of files 58, 59, 60.

#### Q1: When does `f : X → Y` and `f^an : X^an → Y^an` carry the same properties?

The local properties of `X` (regular, normal, Cohen–Macaulay, smooth, …) and the local properties of `f` (flat,
unramified, étale, smooth, proper, finite, …) should transfer between the algebraic and analytic worlds, given that the
local rings agree after completion. **File 58 (XII.2, XII.3)** turns this expectation into a precise dictionary, with
eight scheme-level properties (XII.2.1) and seventeen morphism-level properties (XII.3.1, XII.3.2). Most proofs proceed
by reducing to a closed point via Jacobson and then transferring across the completion isomorphism XII.1.1 (2).

#### Q2: When is `Φ^#_{coh}` essentially surjective? When does `H^p(X, F) = H^p(X^an, F^an)`?

XII.1.3.1 shows `Φ^#_{coh}` is faithful, exact, conservative. But for `X` *proper*, it should be more — an **equivalence
of categories**, with cohomology preservation `H^p(X, F) ≃ H^p(X^an, F^an)`. This is the **relative GAGA theorem** of
**file 59 (XII.4)**. The cohomology preservation upgrades to a comparison of higher direct images
`(R^p f_* F)^an ≃ R^p f_*^an(F^an)` for `f : X → Y` proper.

#### Q3: How does the étale fundamental group `π_1^ét(X)` relate to the topological fundamental group

`π_1^top(X^an)`?

For `X = ℙ^r_ℂ` the answer is "both are trivial" (file 52 XI.1.1 on the algebraic side; classical homotopy theory on the
analytic side). For abelian varieties (file 53 XI.2.3) the étale `π_1` is the Tate module; on the analytic side,
`π_1^top(A^an) = H_1(A^an, ℤ) ≃ ℤ^{2g}` is the integral homology lattice. The two answers match precisely after
**profinite completion** of `π_1^top`.

This is the **Riemann existence theorem** of **file 60 (XII.5)**. The clean form (XII.5.1): the functor `Ψ : X' ↦ X'^an`
is an equivalence between finite étale coverings of `X` and finite étale coverings of `X^an`. The `π_1`-corollary
(XII.5.2): `π_1^ét(X, φ(x)) ≃ π̂_1^top(X^an, x)` as profinite groups, where the right side is the profinite completion
of the topological `π_1`.

The Riemann existence theorem is what powers the **transcendental method** of file 50 (X.2.6): the topological
calculation of `π_1^top(Σ_g) = ⟨ s_1, …, s_g, t_1, …, t_g | ∏ [s_i, t_i] = 1 ⟩` for a smooth proper curve of genus `g`
becomes, after profinite completion, the étale fundamental group `π_1^ét(X_0)` of any curve of genus `g` in any
characteristic — *via* Witt-vector lift to characteristic 0, base change to `ℂ`, and XII.5.2.

> **Closing slogan for file 57.** *`X^an` is the analytic shadow of `X`.* It carries the same local data as `X` at every
> closed point, after passage to completions. The functor `X ↦ X^an` is exact and faithful on coherent sheaves, and is
> the universal locally-ringed-`ℂ`-space gadget representing the points functor. What remains is to show that this
> functor — and the comparison morphism `φ : X^an → X` it carries with it — preserves the global properties, the
> cohomology, and the finite étale category that the étale `π_1` of files 30–56 was built to detect. That is the work of
> files 58–60.
