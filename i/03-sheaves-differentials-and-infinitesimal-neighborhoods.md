# Sheaves, differentials, and infinitesimal neighborhoods

## What this file is about

Calculus opens with the derivative. A smooth curve in the plane has, at every point, a best linear approximation; the
slope of that approximation is the derivative, and it captures how the curve moves in a vanishingly small neighborhood
of the point. Algebra has its own version of this idea, and it does not need limits or epsilons. It only needs a way to
compare two points that are infinitely close — closer than any actual separation, but not quite the same. The algebraic
record of such an infinitely small separation is the differential.

This file builds that record from scratch. The destination is a way to say, in pure algebra, that an algebraic map
between two spaces has no infinitesimal looseness along its fibres — that locally, near each output point, the input
points sit cleanly apart with nothing wiggling between them. That property is the gatekeeper for everything in the files
that follow.

We can read a ring as a geometric space, take fibers, form pullbacks, and slide between local rings and global ones.
What we cannot yet do is **calculus** — not in the analytic sense, but in the algebraic one: derivatives, infinitesimal
directions, the difference between a function and its first-order approximation. Without that we cannot say what "no
infinitesimal slack along the fiber" means, and without that we cannot define unramifiedness in file 04.

This file builds the calculus. The destination is the sheaf of relative Kähler differentials `Ω¹_{X/Y}`, which records
how points of `X` over `Y` can differ to first order. Once we have it, the central condition of unramifiedness will be
the single algebraic equation `Ω¹_{X/Y} = 0`.

The path goes through three stages. First we install a small amount of sheaf language — enough to talk about "regular
functions on each open" coherently. Then we look at the **diagonal**, which algebraically encodes "two points equal over
the base." Finally we extract first-order data from the diagonal by killing higher-order infinitesimals; that is
`Ω¹_{X/Y}`.

#### Aside (type-theory analogy).

_Skip this paragraph if dependent type theory and the equality predicate of an elaborator are not part of your
background; nothing later depends on it._

The diagonal plays the role of the equality predicate of an elaborator. In a dependent type theory, you can ask whether
two terms are definitionally equal: the equality is a proposition that holds on the diagonal of pairs of terms.
Algebraic geometry has the same setup. The diagonal `Δ : X → X ×_Y X` is the geometric witness of "two points over `Y`
are equal," and `Ω¹_{X/Y}` is its first-order linearization.

## Why sheaves at all

The previous file gave us regular functions on a distinguished open `D(f) ⊂ Spec A`: they are `A[1/f]`. That handles a
basis of opens. A general open is not on the list, and a scheme glued from many affine pieces has no preferred basis at
all. We need a systematic language for "ring of functions on each open, with restriction maps that fit together."

That language is sheaves. Take only what this file needs: enough to make sense of `𝒪_X`, the ideal sheaf of the diagonal
`𝓘_X`, and the sheaf of differentials `Ω¹_{X/Y}`.

### A tiny worked example

Before any abstract definition, here is the picture in miniature.

Take `X = ℝ`, the real line, and consider the rule

```text
ℱ(U) := { continuous real-valued functions on U }
```

for each open `U ⊆ ℝ`. So `ℱ((0, 1))` is the ring of continuous functions on the open interval `(0, 1)`; `ℱ(ℝ)` is the
ring of continuous functions on the whole line.

This rule has two properties worth naming.

First, if `V ⊆ U` is a smaller open subset, you can **restrict** a function on `U` to a function on `V`. So there is a
ring map

```text
ℱ(U) → ℱ(V),    f ↦ f|_V.
```

These restrictions compose: restricting from `U` to `V` and then to `W` is the same as restricting directly from `U` to
`W`. And restricting from `U` to itself is the identity. This part of the data — open sets, restrictions, composition
rule — is the **presheaf** axiom. Nothing more.

Second, the rule has a **gluing** property. Suppose `(0, 2)` is covered by the two intervals `(0, 1.5)` and `(0.5, 2)`.
If you have a continuous function `f` on `(0, 1.5)` and another `g` on `(0.5, 2)`, and they agree on the overlap
`(0.5, 1.5)`, then there is a **unique** continuous function `h` on `(0, 2)` that restricts to `f` on `(0, 1.5)` and to
`g` on `(0.5, 2)`. You glue the two functions together, and the glued function is unique.

This second property is the **sheaf** axiom. It says that "globally consistent local data assembles into unique global
data." Most of the natural rings of functions you might think of — continuous, smooth, holomorphic, regular — satisfy
this.

Now we abstract.

### Presheaves: the data, with no axioms beyond restriction

A **presheaf of rings** `ℱ` on a topological space `X` is the following data.

- For each open `U ⊆ X`, a ring `ℱ(U)`.

- For each pair of opens `V ⊆ U`, a ring map

    ```text
    ρ_{V, U} : ℱ(U) → ℱ(V)
    ```

    called the **restriction** from `U` to `V`. We write `f|_V` instead of `ρ_{V, U}(f)` when the meaning is clear.

The restriction maps satisfy two axioms.

- `ρ_{U, U}` is the identity on `ℱ(U)`.
- For `W ⊆ V ⊆ U`, restricting in two steps equals restricting in one: `ρ_{W, V} ∘ ρ_{V, U} = ρ_{W, U}`.

That is the presheaf data. Continuous functions on `ℝ` are a presheaf. Polynomial functions on each `D(f) ⊆ Spec A` are
a presheaf. Both examples have one extra property — they glue — which is what makes them sheaves.

### Sheaves: data plus gluing

A **sheaf** is a presheaf where local data glues uniquely to global data.

Stated formally. Let `U ⊆ X` be open, and let `{U_i}` be an open cover of `U` (the `U_i` are open subsets of `U` whose
union is `U`). A sheaf satisfies, for any such cover:

- **Identity.** If `s, s' ∈ ℱ(U)` satisfy `s|_{U_i} = s'|_{U_i}` for every `i`, then `s = s'`.

- **Gluing.** If we have `s_i ∈ ℱ(U_i)` for each `i`, with the property that `s_i` and `s_j` agree on the overlap
    (`s_i|_{U_i ∩ U_j} = s_j|_{U_i ∩ U_j}` for every pair `i, j`), then there exists `s ∈ ℱ(U)` such that
    `s|_{U_i} = s_i` for every `i`.

The identity axiom says local agreement implies global equality; the gluing axiom says compatible local data assemble
into a global section. Together: data on `U` is exactly the same as compatible data on a cover of `U`.

The continuous-functions example we just did is a sheaf: agreement of continuous functions on a cover implies global
equality (identity), and continuous functions on overlapping opens that agree assemble into a global continuous function
(gluing).

The slogan to hold: **a sheaf is the right notion of "globally consistent local data."**

### The structure sheaf, properly

The construction of the previous file extends. There is a unique sheaf of rings `𝒪_X` on `Spec A` such that
`𝒪_X(D(f)) = A[1/f]` for every distinguished open. Globally,

```text
𝒪_X(Spec A) = A.
```

So the global sections recover the original ring, and the restriction-to-distinguished-opens is localization.

For a general scheme `X` glued from affine pieces, the structure sheaf is built by gluing the pieces. The sheaf
condition guarantees the gluing is well-defined.

The **stalk** of `𝒪_X` at a point `x ∈ X` is the filtered colimit `𝒪_{X, x} = colim_{U ∋ x} 𝒪_X(U)` over open
neighborhoods of `x`, along restriction maps. This is the local ring at `x`, which we already have under the name `𝒪_x`.
Stalks of sheaves are "local data at a single point."

#### Aside (elaborator analogy).

_Skip this paragraph if elaboration of dependent type theory is not part of your background; nothing later depends on
it._

A stalk is the algebraic-geometric counterpart of the typing context an elaborator sees at one subterm: a piece of local
data attached to a single position in a larger global structure.

### Quasi-coherent sheaves

We need one slightly richer class of sheaves: those that look, locally, like modules over a ring.

A sheaf `ℱ` of `𝒪_X`-modules is **quasi-coherent** if, on every affine open `U = Spec A ⊂ X`, the sheaf comes from an
`A`-module `M` in the same way `𝒪_X` came from `A`:

```text
ℱ(D(f)) = M[1/f] = M ⊗_A A[1/f].
```

So a quasi-coherent sheaf on `Spec A` is the same data as an `A`-module. Globally on `X`, it is a gluing of modules on
affine pieces.

The dictionary continues:

> **Quasi-coherent sheaves on `Spec A` ↔ `A`-modules.**

A quasi-coherent sheaf is **of finite type** if locally it comes from a finitely generated module. **Locally free of
rank `n`** if locally it comes from `Aⁿ`. These are the algebraic counterparts of vector bundles.

That is enough sheaf language.

## The diagonal: a geometric witness of equality

Fix a morphism `f : X → Y`. We want to talk about pairs of points of `X` lying over the same point of `Y`. The right
object is the fibered product

```text
X ×_Y X.
```

Its points are pairs `(x, x')` with `f(x) = f(x') ∈ Y`. Among such pairs, the "trivial" ones are those with `x = x'`.
They sit inside `X ×_Y X` via the **diagonal morphism**

```text
Δ_{X/Y} : X → X ×_Y X,    x ↦ (x, x).
```

Categorically, `Δ_{X/Y}` is the morphism induced by the pair `(id_X, id_X) : X → X` and the universal property of the
fibered product. We write `Δ` when the context is clear.

### What the diagonal does

The image of `Δ` inside `X ×_Y X` is the locus where the two points agree. It is the algebraic-geometric witness of
"equality of pairs of points over the base."

#### Aside (type-theory analogy).

_Skip this paragraph if dependent type theory and its equality predicate are not part of your background; nothing later
depends on it._

Think of `X` as a type parametrized by `Y`; then `X ×_Y X` is "pairs of inhabitants over the same parameter," and the
diagonal is "the pairs where the two inhabitants are literally the same term." The structure of the diagonal — and of
the ideal cutting it out — encodes how loose or tight the equality predicate is.

### Algebraic version

For `Spec B → Spec A`, the diagonal corresponds to the **multiplication map**

```text
μ : B ⊗_A B → B,    b ⊗ b' ↦ bb'.
```

Why? Because the diagonal of `Spec B` is the morphism into `Spec(B ⊗_A B)` representing the pair `(id, id)`, and on
rings this is the unique `A`-algebra map sending the two natural inclusions of `B` into `B ⊗_A B` to the identity on
`B`. That map is multiplication.

Concretely: `μ` sends `b ⊗ 1 ↦ b · 1 = b` and `1 ⊗ b ↦ 1 · b = b`, so it reads `b ⊗ 1` as "the value of `b` at the first
factor" and `1 ⊗ b` as "the value of `b` at the second factor." The kernel element `b ⊗ 1 − 1 ⊗ b` is then the
_difference_ between those two values, which is exactly the algebraic shadow of "two points disagree on `b`."

`μ` is surjective: every `b ∈ B` is `μ(b ⊗ 1)`. So the diagonal `Spec B → Spec(B ⊗_A B)` is, on rings, a surjection —
which means it is, geometrically, a **closed immersion**. The image of the diagonal is a closed subscheme.

The claim "`Δ_{X/Y}` is a closed immersion" is the **separation** condition we mentioned in the previous file. For
affine `X` and `Y`, separation is automatic — exactly because `μ` is always surjective for the algebraic version.

A morphism `f : X → Y` is **separated** when the diagonal `Δ_{X/Y} : X → X ×_Y X` is a closed immersion. Geometrically:
the locus in `X ×_Y X` where two points have the same image is itself closed, so distinct points cannot infinitesimally
approach being identified.

For non-affine schemes, separation can fail. The source of Exposé I addresses this in section I.1 by remarking that even
when `Δ` is not closed it is at least an immersion, and that requiring separation here "would be farcical." We follow
the source. From now on, treat `Δ` as a closed (or at least locally closed) immersion.

## The ideal of the diagonal

A closed immersion is cut out by an ideal. So the diagonal carries a defining **ideal sheaf** `𝓘_X ⊂ 𝒪_{X×_Y X}`: the
sheaf of functions on `X ×_Y X` that vanish identically on the diagonal.

Equivalently, on the algebraic side: `𝓘_X` corresponds to the kernel `I = ker(μ)` of the multiplication map.

The ideal `𝓘_X` records "functions of pairs `(x, x')` over `Y` that vanish whenever `x = x'`." These are, more or less,
the **differences** between values at `x` and at `x'`.

Concretely, `b ⊗ 1 − 1 ⊗ b ∈ I` for every `b ∈ B`, because `μ(b ⊗ 1 − 1 ⊗ b) = b − b = 0`. The element `b ⊗ 1 − 1 ⊗ b`
is the algebraic version of "the difference of `b` evaluated at the two points."

### Why we want this

We are setting up algebraic calculus. In ordinary calculus, the **derivative** of `g(x)` at a point measures how much
`g` changes when you nudge `x` by a small amount `dx`. The recipe: expand `g(x + dx) = g(x) + g'(x) dx + O(dx²)`. The
derivative is the linear part.

To do the same in algebra, we need a way to talk about "small nudges." The diagonal and its ideal provide exactly that.
A point near the diagonal is a pair `(x, x')` where `x ≠ x'` but `x` and `x'` are "close." Functions in `𝓘_X` measure
"how close." Functions in `𝓘_X²` measure "second-order closeness" — the part you should ignore for first-order calculus.

To extract the first-order data, kill `𝓘_X²`:

```text
Ω¹_{X/Y} := 𝓘_X / 𝓘_X².
```

This is the **sheaf of relative Kähler differentials** of `X/Y`. It records "first-order infinitesimal differences
between points of `X` over `Y`."

Algebraically, for `Spec B → Spec A`,

```text
Ω¹_{B/A} := I / I²,    I = ker(μ : B ⊗_A B → B).
```

It is naturally a `B`-module.

### Where `d` comes from

So far `Ω¹_{B/A}` is just the quotient `I/I²` — a `B`-module attached to the diagonal. We have not yet said what map
carries elements of `B` into it. The map turns out to be forced by the geometry.

`B` sits inside `B ⊗_A B` two different ways: as `b ↦ b ⊗ 1` (the "value at the first factor") and as `b ↦ 1 ⊗ b` (the
"value at the second factor"). Both are ring homomorphisms `B → B ⊗_A B`. Define

```text
d : B → I/I² = Ω¹_{B/A},    d(b) := (1 ⊗ b − b ⊗ 1) mod I².
```

This is the **difference** of the two embeddings. Two ring homomorphisms agreeing on the diagonal disagree off it by
elements of `I`, so the difference lands in `I`; modulo `I²` we get an `A`-linear map into `Ω¹_{B/A}`.

The Leibniz rule is automatic. Compute `d(bb')` in `I` and add and subtract the cross-term `b ⊗ b'`:

```text
d(bb') = 1 ⊗ bb' − bb' ⊗ 1
       = (1 ⊗ b)(1 ⊗ b') − (b ⊗ 1)(b' ⊗ 1)
       = (1 ⊗ b − b ⊗ 1)(1 ⊗ b') + (b ⊗ 1)(1 ⊗ b' − b' ⊗ 1)
       = d(b) · (1 ⊗ b') + (b ⊗ 1) · d(b').
```

Reduce modulo `I`: in `I/I²`, `1 ⊗ b' ≡ b' · 1 ⊗ 1` and `b ⊗ 1 ≡ b · 1 ⊗ 1`, so

```text
d(bb') ≡ b' · d(b) + b · d(b') mod I².
```

The product rule is not an axiom we impose; it is a one-line consequence of "the difference of two ring homomorphisms
agreeing on the diagonal is a derivation modulo `I²`." Grothendieck phrases the corresponding sheaf statement as
`dt = d¹t − t`, where `d¹` is the homomorphism `𝒪_X → 𝒫¹_{X/Y} = 𝒪_{X×_Y X}/𝓘²` induced by the second projection (EGA IV
§16.3.6).

This is the algebraic shadow of the calculus picture. The two embeddings of `B` into `B ⊗_A B` correspond to "evaluating
at the two coordinates of a pair" — the two points in `X ×_Y X`. Their difference, modulo second-order data, is the
first-order direction from one point to the other.

## Computing `Ω¹` for polynomial rings and quotients

We have the object `Ω¹_{B/A} = I/I²` and its canonical derivation `d`. Time to compute. We start with the
polynomial-ring case, then the quotient case, and read off where `Ω¹` vanishes for the running example.

For `B = A[t₁, …, t_n]`,

```text
Ω¹_{B/A} = B · dt₁ ⊕ … ⊕ B · dt_n,
```

a free `B`-module of rank `n` with basis `dt₁, …, dt_n`. The canonical `d` constructed above sends a polynomial to its
**formal differential**:

```text
d : B → Ω¹_{B/A},    F(t₁, …, t_n) ↦ Σᵢ (∂F/∂t_i) dt_i.
```

This is the formula you know from calculus, written algebraically. The partial derivatives `∂F/∂t_i` are computed by the
elementary rules of polynomial differentiation, which work over any commutative ring.

For a quotient `B = A[t₁, …, t_n]/I`, the differentials of `B` are the differentials of the polynomial ring modulo the
differentials of the relations:

```text
Ω¹_{B/A} = ( ⊕ᵢ B · dt_i ) / ⟨ dG : G generates I ⟩.
```

This is the formula we will compute with. It is a special case of the **conormal sequence** for the surjection
`A[t₁, …, t_n] → B`, which we state alongside its companion (the relative cotangent sequence) in the subsection "Two
exact sequences for `Ω¹`" below.

## What `Ω¹` represents abstractly

The computation above produced a `B`-module with a distinguished map `d : B → Ω¹_{B/A}` satisfying the Leibniz rule. The
same object can be characterized by a universal property, without ever referring to a presentation of `B`. Stating that
characterization is the job of this section.

The clean statement of what `Ω¹_{B/A}` is, abstractly:

> `Ω¹_{B/A}` is the universal `B`-module receiving an `A`-linear derivation of `B`.

We need to unpack "derivation."

An `A`-linear **derivation** of `B` into a `B`-module `M` is an `A`-linear map `δ : B → M` satisfying the **Leibniz
rule**:

```text
δ(bb') = b · δ(b') + b' · δ(b).
```

So `δ` is "almost" `B`-linear, but instead of being multiplicative on `B`, it follows the product rule of
differentiation. Derivations are the abstract version of "differential operators of order 1."

The universal property: the canonical `A`-linear derivation we constructed above,

```text
d : B → Ω¹_{B/A},    b ↦ (1 ⊗ b − b ⊗ 1) mod I²,
```

has the property that any `A`-derivation `δ : B → M` factors uniquely as `δ = δ̃ ∘ d` for a unique `B`-linear
`δ̃ : Ω¹_{B/A} → M`. For `B = A[t₁, …, t_n]/I`, this `d` agrees with the polynomial-ring formal differential computed
above; the universal property guarantees that the formula does not depend on the chosen presentation.

So `Ω¹_{B/A}` is "the universal target of derivations." We never need to look inside it. We use only the universal
property and the explicit computation we already have.

## Two exact sequences for `Ω¹`

Two exact sequences govern how `Ω¹` behaves under composition and under quotients. The polynomial-ring formula and the
quotient formula are special cases. Both sequences use the **pullback** of a quasi-coherent sheaf along a morphism,
which we recall first.

### Pullback of a quasi-coherent sheaf

For a morphism `f : X → Y` and a quasi-coherent sheaf `𝒢` on `Y`, the **pullback** `f*𝒢` is a quasi-coherent sheaf on
`X`. The affine-local description is the cleanest. Cover `X` by affines `Spec C` mapping into affines `Spec B ⊂ Y`; if
`𝒢` corresponds to the `B`-module `N` on `Spec B`, then `f*𝒢` corresponds to the `C`-module `N ⊗_B C` on `Spec C`. The
tensor `⊗_B C` is "base change of `N` along the ring map `B → C`," so pullback of a sheaf is base change of a module,
glued affine-locally.

Three special cases worth holding in mind (Vakil's _Rising Sea_ §14.5.1):

- If `f : U ↪ Y` is an open embedding, `f*𝒢` is `𝒢|_U`, the restriction.
- If `f : Spec κ(p) → Y` is the inclusion of a single point `p`, `f*𝒢` is the **fiber** `𝒢|_p = 𝒢_p ⊗_{𝒪_{Y,p}} κ(p)`.
- If `𝒢` corresponds to a vector bundle, `f*𝒢` is the pulled-back vector bundle in the usual sense.

For full statements and proofs, see Vakil §14.5 (three perspectives on pullback) and EGA 0_I §3.5–§4.3 (sheaf inverse
image and modules over ringed spaces). In what follows, when we write `f*(Ω¹_{Y/Z})`we mean: compute`Ω¹_{Y/Z}`as a
quasi-coherent sheaf on`Y`, base-change it affine-locally to `X`along`f`.

### The relative cotangent sequence (composition)

For a composition `X → Y → Z` of morphisms — algebraically, ring maps `A → B → C` with `Spec C = X`, `Spec B = Y`,
`Spec A = Z` — the cotangent sequence relates the differentials at the three levels:

```text
f*(Ω¹_{Y/Z}) → Ω¹_{X/Z} → Ω¹_{X/Y} → 0,
```

or in algebraic form:

```text
Ω¹_{B/A} ⊗_B C → Ω¹_{C/A} → Ω¹_{C/B} → 0.
```

(The arrow direction reverses: `f : X → Y` corresponds to `B → C`, so a structure map of `Y/Z` becomes a structure map
of `B/A`.) The sequence is exact at the right two terms in general, and exact on the left exactly when `f : X → Y` is
**formally smooth** — one of the EGA characterizations of formal smoothness.

### The conormal sequence (immersion)

For a closed immersion `Z ↪ X` defined by an ideal sheaf `𝓙` (or algebraically `J ⊂ R` with `B = R/J`), the conormal
sequence is:

```text
𝓙 / 𝓙²  →  Ω¹_{X/S} ⊗_{𝒪_X} 𝒪_Z  →  Ω¹_{Z/S}  →  0.
```

The first map sends the class of a function `g ∈ 𝓙` to its differential `dg`, restricted to `Z`. The cokernel is
`Ω¹_{Z/S}`.

This is the sequence that produces our quotient formula. For `R = A[t₁, …, t_n]` and `B = R/J`, the middle term is
`B · dt₁ ⊕ … ⊕ B · dt_n` (free of rank `n`), the first map sends `G ∈ J` to `Σᵢ (∂G/∂t_i) dt_i`, and the cokernel is
`Ω¹_{B/A}` — exactly the quotient formula we wrote earlier.

Both sequences are split exact when the morphism in question is formally smooth. The conormal sequence reappears in file
11 as the engine of corollary I.7.2, identifying the different ideal of `B = A[t]/F` with `(F'(u))`.

For full statements and proofs, see EGA IV §16.4.19 (relative cotangent) and §16.4.21 (conormal).

### The key example: `B = A[t]/F`

For one variable and one relation, the formula reads:

```text
Ω¹_{B/A} = B · dt / (dF) = B · dt / (F'(t) · dt) = B / F'(t) · B.
```

So `Ω¹_{B/A}` is the quotient of the rank-one free `B`-module by the principal ideal generated by `F'(t)`.

It is **zero** iff `F'(t)` is a unit in `B`.

That is the algebraic test for unramifiedness in the simplest case: the algebra `A[t]/F` is unramified over `A` iff the
formal derivative `F'(t)` of the defining polynomial is a unit in the quotient.

### The running example, computed yet again

In file 02 we walked through the fibers of `Spec ℤ[t]/(t² − 2) → Spec ℤ` and saw the trichotomy: split at most primes,
an extension at the inert ones, ramified at `(2)`. The same computation now recovers the ramification locus from `Ω¹`
alone. With `F = t² − 2` we have `F'(t) = 2t`, so

```text
Ω¹_{B/A} = B / 2t · B.
```

To see when this vanishes at a point, base change to the residue field:

**`p = 7`.** In `𝔽₇[t]/(t² − 2)`, the element `2` is a unit (since `2 ≠ 0` mod `7`) and `t` is a unit (since
`t² = 2 ≠ 0`). So `2t` is a unit, and `Ω¹` vanishes in the fiber.

**`p = 5`.** Same logic: `2 ≠ 0` mod `5` and `t² = 2 ≠ 0`, so `2t` is a unit, and `Ω¹` vanishes.

**`p = 2`.** Now `2 = 0` in `𝔽₂`, so `2t = 0` in the fiber. Then `Ω¹` is the entire fiber `𝔽₂[t]/(t²)`, which is
non-zero.

So `Ω¹_{B/A}` is supported only at the prime `(2)`. The morphism `Spec B → Spec ℤ` is **unramified at every other
prime** and **ramified at `(2)`** — and `Ω¹` has located the ramified place without ever computing a fiber.

> **`Ω¹_{X/Y}` is a sheaf supported on the ramification locus of `f : X → Y`.**

In file 04, we will turn this observation into a definition. The **different ideal** `𝔡_{X/Y} := Ann(Ω¹_{X/Y})` cuts out
the ramified locus.

## Infinitesimal neighborhoods

We took `Ω¹` by killing `𝓘_X²` — first-order data only. The ideal itself contains more. Powers of `𝓘_X` carry
higher-order information, and quotienting by them gives a tower of thickenings of the diagonal:

```text
𝒪_{X ×_Y X} / 𝓘_X^{n+1} =: 𝓟ⁿ_{X/Y},    n ≥ 0.
```

For `n = 0`, this is `𝒪_{X ×_Y X} / 𝓘_X = 𝒪_X` — the structure sheaf of the diagonal itself, which is just `X`.

For `n = 1`, this is `𝒪 / 𝓘²`. The corresponding scheme `Δ¹_{X/Y}` is the **first infinitesimal neighborhood** of the
diagonal: the diagonal "thickened by first-order infinitesimals." Sections of `Δ¹_{X/Y}` carry exactly the data of
`Ω¹_{X/Y}`.

For higher `n`, we get higher-order thickenings.

The source remarks that the bookkeeping is "of total triviality, although rather long," and notes that these objects
only earn their keep when smooth morphisms enter the picture (in later parts of SGA). For Exposé I, only `n = 0` and
`n = 1` matter, and only as carriers for `Ω¹`. We will not develop the higher thickenings.

### A picture of the first infinitesimal neighborhood

For concreteness, take `X = Spec k[t]` (the affine line) and `Y = Spec k`. The fibered product is

```text
X ×_Y X = Spec(k[t] ⊗_k k[t']) = Spec k[t, t'],
```

renaming the second variable `t'`. The diagonal corresponds to the multiplication map `k[t, t'] → k[t]` sending both `t`
and `t'` to `t`. Its kernel `I` is the ideal `(t' − t)` — "the difference of the two coordinates."

The first infinitesimal neighborhood is

```text
k[t, t'] / (t' − t)² = k[t, ε] / (ε²),    ε := t' − t.
```

This is "the affine line, fattened by an infinitesimal `ε` at every point." The differential `dt` corresponds to the
class of `ε` in `Ω¹`. Modulo `(ε²)`, "increments in `t` of order higher than one" vanish.

You should think of this as the algebraic version of the tangent bundle of the line: at every point of `𝔸¹`, an
infinitesimal direction `ε` records "first-order motion."

## The connection to "no ramification"

The example told us where `Ω¹` lives: on the ramified locus. The slogan that drives file 04 is the converse reading.

`Ω¹_{B/A}` measures first-order infinitesimal differences between points of `Spec B` over `Spec A`. If it vanishes near
`x`, no such differences exist there: any two points of `Spec B` over `Spec A` that are "infinitesimally close" are
literally equal.

That is the algebraic version of what makes a covering map a covering map: the fiber should be **discrete**, with no
continuous deformations of a point inside the fiber.

### Why `Ω¹ = 0` is the right algebraic test

A more precise restatement, which file 04 will turn into a definition: vanishing of `Ω¹_{B/A}` is exactly the
**lifting** condition along square-zero thickenings of the base.

Here is why. Take the base ring `A` and "fatten" it by a square-zero ideal: form `A' = A ⊕ I` with multiplication
`(a, x)(a', x') = (aa', ax' + a'x)`. The corresponding morphism `Spec(A') → Spec(A)` is a square-zero thickening. A
`Y`-morphism `Spec(A') → Spec(B)` is, on rings, an `A`-algebra map `B → A'`; reduced mod `I`, it is the structure map
`B → A`. The freedom to vary the lift, on top of the structure map, is exactly an `A`-linear derivation `B → I`.

The set of derivations `B → I` is `Hom_B(Ω¹_{B/A}, I)` — by the universal property. So:

> `Ω¹_{B/A} = 0` ⟺ no derivations `B → I` exist for any `I` ⟺ the lift, if it exists, is unique.

This is the **formally unramified** condition: lifts across nilpotent thickenings of the base are unique when they
exist. EGA takes this lifting property as the _definition_ of formally unramified, and proves the equivalence with
`Ω¹ = 0` in two lines (EGA IV §17.2.1). The gentle reading runs in the other direction — `Ω¹ = 0` is the working
definition, lifting is the consequence — but the equivalence is what makes both viewpoints legitimate.

We will state the lifting form precisely in file 05 and use it in the equivalent characterizations of unramified
gathered in file 04:

- `Ω¹_{X/Y} = 0` near `x`,
- the diagonal `Δ_{X/Y}` is locally an open immersion near `x`,
- the residue extension is finite separable and `𝔪_y · 𝒪_x = 𝔪_x`,
- lifts across square-zero thickenings of the base are unique,

each of which captures the same intuition from a different angle.

## Closing

We have built three things in this file. A small piece of sheaf theory (`𝒪_X`, quasi-coherent sheaves), enough to make
the local data on a scheme cohere globally. The diagonal `Δ : X → X ×_Y X`, which encodes "two points equal over the
base." And the sheaf of relative Kähler differentials `Ω¹_{X/Y} = 𝓘_X / 𝓘_X²`, the universal target of `A`-linear
derivations of `B`, which extracts first-order infinitesimal information from the diagonal.

We computed `Ω¹` for polynomial rings (free, with the obvious basis) and for `B = A[t]/F` (the rank-one quotient
`B / F'(t) · B`). For our running example, `Ω¹` is supported precisely on the ramified prime `(2)`.

The next file uses `Ω¹` to define **unramified** morphisms, and then combines that condition with **flatness** to define
**étale** morphisms — the algebraic analogue of covering maps. The trichotomy we have been computing all along (split,
extension, ramified) becomes the trichotomy of fiber types.
