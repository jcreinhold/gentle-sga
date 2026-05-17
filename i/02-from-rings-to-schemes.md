# From rings to schemes

## What this file is about

The previous file taught the algebra. Rings, the operations on rings, the analogues of "subset" and "neighbourhood"
inside them — that vocabulary was advertised as geometry but never actually pinned to a geometric object. This file pins
it. Each ring acquires a literal geometric counterpart, a kind of space, and each algebraic operation acquires the
geometric operation it stands for. By the end every commutative ring is a space, and doing algebra on the ring is the
same activity as doing geometry on the space, seen from two angles.

The algebra is collected. Every operation we built — quotient, prime ideal, localization, tensor product — was
advertised as having a geometric meaning. None of it does yet. The dictionary points at a translation we have not
performed.

This file performs it. We attach to each ring `A` a geometric object `Spec A`, define morphisms `Spec B → Spec A` from
ring maps `A → B`, and check that every operation on the algebra side matches a natural operation on the geometric side.
The dictionary becomes tight enough that doing algebra on `A` and doing geometry on `Spec A` are the same activity
viewed from two angles. By the end of the file any commutative ring is a geometric space — enough to understand most of
Exposé I literally.

## Why maximal ideals already feel like points

Before building `Spec A` in general, look at the case where the dictionary is least surprising: the polynomial ring
`k[t]` over an algebraically closed field `k`, like `ℂ`.

Every maximal ideal of `k[t]` has the form `(t − a)` for some `a ∈ k`. This is a basic theorem: a monic irreducible
polynomial over an algebraically closed field has degree `1`. The quotient `k[t]/(t − a) = k`. Each maximal ideal pairs
with one point of `k`, and the residue field at each point is `k` itself.

So if you only knew the ring `k[t]` and not the underlying line `k`, you could recover `k` by listing maximal ideals.
The space of "points" of `k[t]`, in any reasonable algebraic sense, is literally `k`.

This is the smallest case where the dictionary works perfectly. Algebra reconstructs geometry.

For non-algebraically-closed fields, things get more interesting. The maximal ideals of `ℝ[t]` are `(t − a)` for `a ∈ ℝ`
(with quotient `ℝ`) and `(t² + bt + c)` for negative discriminant (with quotient `ℂ`). The algebra reports two kinds of
point: real points and conjugate-pair points. The geometry of `ℝ` only knew about the first kind. The algebra of `ℝ[t]`
knew about both.

For `ℤ`, the maximal ideals are `(p)` for prime numbers, with quotients `𝔽_p`. The algebra reports "one point per prime
number." The geometry — well, what geometry? Number theory. The algebra tells us that the right geometric object
underlying number theory has one point per prime number, plus a generic point.

Whatever notion of "space" we are about to define, it must include all these algebraic data. Conjugate pairs, prime
numbers, and generic points are honest points of that space.

## Building `Spec A` as a set

The hint from `k[t]` was that primes already index the points the algebra knows about. Promote that observation to a
definition. Let `A` be any commutative ring with `1`.

> **The points of `Spec A` are the prime ideals of `A`.**

That is the entire set-theoretic definition.

A prime ideal is a generalized point. A maximal ideal is an honest "closed" point with a residue field. A non-maximal
prime is a "generic" point of some closed subset.

Some examples make the definition concrete.

### `Spec ℤ`

The primes of `ℤ` are `(0)`, `(2)`, `(3)`, `(5)`, `(7)`, `(11)`, `…`. The non-zero primes are exactly the primes of `ℤ`
in the elementary-arithmetic sense, which is where the word comes from.

So `Spec ℤ` has one closed point per prime number, plus the generic point `(0)`. The residue fields are `𝔽_p` at `(p)`
and `ℚ` at `(0)`.

Slogan: number theory is algebraic geometry over `Spec ℤ`. We will not pursue the slogan, but this is what underlies it.
The prime numbers are not just numbers; they are points.

### `Spec k[t]` for a field `k`

The primes are `(0)` (the generic point) and `(F)` for each monic irreducible polynomial `F ∈ k[t]`. The residue field
at `(F)` is `k[t]/F`, a finite extension of `k`.

For `k = ℂ`, the irreducibles are linear, so the closed points are in bijection with `ℂ`. For `k = ℝ`, the closed points
are `ℝ ∪ { conjugate pairs }`. For `k = 𝔽_q`, the closed points correspond to Galois orbits of points of the algebraic
closure.

In every case, the generic point is `(0)` with residue field `k(t)`.

### `Spec k[ε]/(ε²)` — the fat point

The ring `k[ε]/(ε²)` has exactly two ideals: `(0)` and `(ε)`. Of these, `(ε)` is the only prime, and it is maximal. So
`Spec k[ε]/(ε²)` has **one point**, with residue field `k`.

But the ring is not just `k`. The nilpotent `ε` is non-zero in the ring even though it is "zero at every point." This is
the smallest example of a scheme whose underlying topological space lies about its structure.

We will use this scheme constantly. It is the universal "point with one infinitesimal direction." Anything to do with
derivatives in algebraic geometry will involve maps in or out of `Spec k[ε]/(ε²)`.

## A topology on `Spec A`

Points alone make `Spec A` a set, not a space. The topology comes from the ideals: each ideal cuts out the primes that
contain it.

For each ideal `I ⊆ A`, the **vanishing locus** is

```text
V(I) := { 𝔭 ∈ Spec A : I ⊆ 𝔭 }.
```

These are the primes "containing" `I`, which is the same as the primes where every element of `I` lies. Geometrically:
"points where every function in `I` vanishes."

Declare a subset `Z ⊆ Spec A` to be **closed** iff `Z = V(I)` for some ideal `I`. The complements are open. This defines
the **Zariski topology** on `Spec A`.

Three quick checks make this a topology. The empty set is `V(A)`; all of `Spec A` is `V((0))`. Finite unions of closed
sets are closed: `V(I) ∪ V(J) = V(I ∩ J)`. Arbitrary intersections of closed sets are closed: `⋂_α V(I_α) = V(∑_α I_α)`.
So we have a topology.

### The basic opens

The closed sets came from ideals; the open sets are their complements. One family of opens — one per element of the ring
— already generates the rest. For each `f ∈ A`,

```text
D(f) := { 𝔭 ∈ Spec A : f ∉ 𝔭 } = Spec A \ V((f)).
```

So `D(f)` is the set of primes where `f` is "not zero" — equivalently, the points where `f` has a nonzero value in the
residue field.

Every open set in `Spec A` is a union of distinguished opens. They form a basis of the topology.

### Localization is restriction

The distinguished opens have a beautiful identification:

```text
D(f) = Spec(A[1/f])    as topological spaces.
```

The bijection sends a prime `𝔭` of `A` not containing `f` to its image in `A[1/f]`. This is reversible because primes of
`A[1/f]` correspond exactly to primes of `A` not containing `f`.

This is the moment where the algebra of localization becomes the geometry of restriction:

> **Localizing a ring at `f` is the same as restricting `Spec` to the open subset where `f` is nonzero.**

The algebraic move "invert `f`" and the geometric move "restrict to where `f` doesn't vanish" are the same operation,
viewed from opposite sides.

### How coarse is the Zariski topology?

The Zariski topology has very few closed sets and very few open sets. The closed sets of `Spec ℂ[t]` are: the empty set,
all of `Spec`, and finite collections of closed points. The open sets are their complements — almost everything.

This is much coarser than the analytic topology you might expect. The point of cohomology theories like the étale
topology, hinted at later in SGA, is to refine the Zariski topology while keeping its algebraic character.

For reading Exposé I, the Zariski topology is enough. We use it silently when we say "open" and "closed."

## Functions on `Spec A`: the structure sheaf

`Spec A` is now a space with points and a notion of value at a point. Missing: a coherent ring of functions on each open
set. Localization-is-restriction tells us what to write down.

> On a distinguished open `D(f) ⊆ Spec A`, the regular functions are `A[1/f]`. On a general open `U`, the regular
> functions are the largest collection that restricts compatibly to every distinguished open inside `U`.

The technical machinery — sheaves, restriction maps, gluing axioms — gets developed in the next file. For now, all we
need is the operational rule:

> **Functions on `Spec A` globally are `A`. Functions on `D(f)` are `A[1/f]`. Restriction of functions corresponds to
> passing through localization maps.**

The pair `(Spec A, 𝒪_{Spec A})` of a topological space and its sheaf of regular functions is called an **affine
scheme**. We write `Spec A` and let `𝒪` be implicit.

## Schemes (briefly)

A **scheme** is a topological space `X` with a sheaf of rings `𝒪_X` such that, locally on `X`, the pair `(X, 𝒪_X)` looks
like `(Spec A, 𝒪_{Spec A})` for some ring `A`. Schemes are built by gluing affine schemes along open subsets.

The source of Exposé I uses the older word **prescheme** for what we have just defined, and reserves **scheme** for
those satisfying an additional **separation** condition. We follow the source's usage when we restate its theorems and
explain the separation issue when it matters. For most of the project, the distinction is invisible, and we work with
affine schemes anyway.

## Morphisms: ring maps in reverse

A scheme without morphisms is inert. The rule for affine schemes is forced by the ring side:

> **A morphism `Spec B → Spec A` of affine schemes is the same data as a ring homomorphism `A → B`, with the arrow
> flipped.**

So `Hom_{schemes}(Spec B, Spec A) = Hom_{rings}(A, B)`. The functor `Spec` is an equivalence

```text
Spec : (commutative rings)ᵒᵖ ≃ (affine schemes).
```

Concretely, given `φ : A → B`, the morphism `Spec φ : Spec B → Spec A` sends a prime `𝔮 ⊂ B` to its preimage
`φ⁻¹(𝔮) ⊂ A`. This is well-defined because preimages of primes are primes.

The arrow-flipping continues to bite. A ring map `A → B` runs in one direction; the corresponding geometric map
`Spec B → Spec A` runs in the other.

#### Aside (type-theory analogy).

_Skip this paragraph if dependent type theory and substitution calculus are not part of your background; nothing later
depends on it._

The substitution lemma in type theory has the same flavor: if you substitute terms of `Δ` into a context `Γ`, you
produce a substitution `Γ → Δ` in the type-theoretic sense, but a morphism of contexts `Δ → Γ` in the geometric sense.
The same contravariance.

### A worked morphism

The Gaussian integers `ℤ[i] = ℤ[t]/(t² + 1)` admit an obvious inclusion `ℤ → ℤ[i]`. This corresponds to a morphism

```text
f : Spec ℤ[i] → Spec ℤ.
```

What does `f` look like geometrically? On points, it sends a prime `𝔮 ⊂ ℤ[i]` to its contraction `𝔮 ∩ ℤ ⊂ ℤ`. The fibers
over each prime `(p) ⊂ ℤ` are the primes of `ℤ[i]` lying over `(p)`.

To compute the fiber, base-change to the residue field. Using the "killing relations" pattern from the previous file:

```text
ℤ[i] ⊗_ℤ 𝔽_p = ℤ[t]/(t² + 1) ⊗_ℤ 𝔽_p = 𝔽_p[t]/(t² + 1).
```

So the fiber over `(p)` is `Spec 𝔽_p[t]/(t² + 1)`. We want to know how this small scheme breaks down depending on `p`.

When does `t² + 1` factor mod `p`? Over `𝔽_p`, the polynomial has a root iff `−1` is a square mod `p`, iff `p ≡ 1 mod 4`
(or `p = 2`). The three cases:

- **`p ≡ 1 mod 4`** (e.g. `p = 5`, with `2² = 4 = −1`): `t² + 1 = (t − 2)(t + 2)` mod `5`, so the fiber is `𝔽₅ × 𝔽₅`,
    two distinct points each with residue field `𝔽₅`. **Split.**
- **`p ≡ 3 mod 4`** (e.g. `p = 3`): `t² + 1` is irreducible, so the fiber is `𝔽₉`, one point with residue field `𝔽₉`.
    **Extension.**
- **`p = 2`**: `t² + 1 = (t + 1)²` mod `2`, so the fiber is `𝔽₂[t]/(t + 1)² ≃ 𝔽₂[ε]/(ε²)` with `ε = t + 1`, one point
    with residue field `𝔽₂` and a nilpotent. **Ramified.**

The same trichotomy as the running `ℤ[√2]/ℤ` example, ramifying again at the prime `(2)` — though for a different
reason. The discriminant of `t² + 1` over `ℤ` is `−4`, supported only at the prime `2`. (The discriminant of `t² − 2`
was `8 = 2³`, also supported only at `2`. Both quadratic extensions of `ℤ` have all their ramification at `2`.)

This pattern is universal. Any morphism that "looks like" `Spec(A[t]/F) → Spec A` for monic `F` has fibers governed by
the factorization of `F` mod each prime of `A`, and the trichotomy appears as soon as you have a quadratic.

## Pullback in geometry, tensor product in algebra

The Gaussian fiber computation used tensor products silently. The previous file owed a geometric meaning for that
operation; the formula is now in reach:

> **For affine schemes, `Spec B ×_{Spec A} Spec C = Spec(B ⊗_A C)`.**

The fibered product of `Spec B` and `Spec C` over `Spec A`, as schemes, is `Spec` of the tensor product algebra.

Both sides have the same universal property. On the geometry side, the fibered product represents pairs of points lying
over a common point. On the algebra side, the tensor product is the coproduct in `A`-algebras. Universal properties
matched, contravariantly.

We have already used this implicitly to compute fibers. The fiber of `f : X → Y` over a point `y ∈ Y` is

```text
f⁻¹(y) := X ×_Y Spec(κ(y)),
```

a scheme over `κ(y)`. In the affine case with `Y = Spec A`, `X = Spec B`, and `y` the prime `𝔭`, this becomes
`Spec(B ⊗_A κ(𝔭))`, which is what we have been computing all along.

### The running example, viewed geometrically

Under the algebra of file 01, the morphism `Spec ℤ[t]/(t² − 2) → Spec ℤ` had fibers computed at `(7)`, `(5)`, `(2)` and
produced the trichotomy split / extension / ramified. The operation now has a geometric name: each fiber is a base
change to a residue field, base change is a tensor product, and tensor product is the algebraic shadow of "pull back to
a single point of the base."

Same picture, sharper language.

## Local rings on a scheme

For a scheme `X` and a point `x ∈ X`, the **local ring** at `x` is the ring of "germs of regular functions at `x`":

```text
𝒪_x := 𝒪_{X, x} := colim_{U ∋ x} 𝒪_X(U),
```

the **filtered colimit** (also called direct limit) of the rings of regular functions over open neighborhoods of `x`,
taken along the restriction maps. Operationally: an element of `𝒪_x` is represented by a function defined on **some**
open neighborhood of `x`, and two representatives are identified if they agree on a smaller open neighborhood.

In the affine case `X = Spec A` with `x = 𝔭`, the formula simplifies to

```text
𝒪_x = A_𝔭.
```

So the local rings of `Spec A` are exactly the localizations of `A` at primes. The ones we built in the previous file
are not abstract: they are the rings of regular functions in arbitrarily small neighborhoods of points.

A morphism of schemes `f : X → Y` induces, for each `x ∈ X` with `y = f(x)`, a **local homomorphism**

```text
𝒪_y → 𝒪_x.
```

This homomorphism sends the maximal ideal of `𝒪_y` into the maximal ideal of `𝒪_x`. Most properties of `f` near `x`
reduce to properties of this single local homomorphism.

#### Aside (elaborator analogy).

_Skip this paragraph if elaboration of dependent type theory is not part of your background; nothing later depends on
it._

The reduction is the same shape as the one in an elaborator: properties of the program at a single subterm reduce to
properties of the typing context at that subterm. Replace "scheme at a point" with "program at a subterm" and "local
ring" with "typing context" and the geometric statement becomes the elaboration-theoretic one.

This is the **discipline of locality** that runs through Exposé I: sliding from a scheme to a local ring at a point,
then to its residue field, then back. Every property in the four-class hierarchy of file 04 has a pointwise local form.

## Open and closed immersions: the simplest morphisms

The framework now handles arbitrary morphisms. Before turning that loose, fix the two extremes — pure restriction to an
open and pure restriction to a closed subset. They set the benchmark for what a "good" morphism looks like.

### Open immersions

A morphism `f : U → X` is an **open immersion** if locally on `X` it looks like the inclusion of a distinguished open:
`Spec(A[1/f]) → Spec A` for some `f ∈ A`. Equivalently, `U` is identified with an open subscheme of `X`, and the
structure sheaf restricts.

The picture: `U` is an honest open subset of `X` and the morphism is the inclusion. Geometrically, this is the algebraic
version of a "local homeomorphism that is also injective." It is the model for everything else.

The defining feature: an open immersion is a literal local isomorphism. The local ring at any point of `U` equals the
local ring at the corresponding point of `X`. The fiber at any point of `U` is a single point.

Examples that come up:

- `Spec ℤ[1/2] → Spec ℤ`: identifies `Spec ℤ[1/2]` with the open complement of the closed point `(2)`.
- `Spec(A[1/f]) → Spec A`: the canonical open immersion onto `D(f)`.
- `Spec(k[t, t⁻¹]) → Spec(k[t])`: identifies the multiplicative group `𝔾_m` with the punctured affine line.

Open immersions are étale, and they are the only étale morphisms that are also injective on points and trivial on
residue fields. This is theorem I.5.1 of the source — the "open immersion criterion" of file 05. Hold the example in
mind: it is the limit case toward which all of file 05 is climbing.

### Closed immersions

A morphism `f : Z → X` is a **closed immersion** if locally on `X` it looks like `Spec(A/I) → Spec A` for some ideal
`I ⊆ A`. The underlying topological map is a homeomorphism onto a closed subset of `X`, and the structure sheaf is the
obvious quotient.

Examples:

- `Spec 𝔽_p → Spec ℤ`: closed immersion onto the closed point `(p)`.
- `Spec(k[x]) → Spec(k[x, y])` via `y ↦ 0`: closed immersion onto the `x`-axis.
- `Spec(k[ε]/(ε²)) → Spec(k[ε]/(ε³))` via the obvious surjection: closed immersion that is **set-theoretically a
    homeomorphism** but algebraically nontrivial.

The third example is interesting. `Spec(k[ε]/(ε²))` and `Spec(k[ε]/(ε³))` have the same underlying topological space
(one point each). The closed immersion is "the same" topologically. But the structure sheaves differ: one has `ε² = 0`,
the other has `ε³ = 0`. The algebra distinguishes them; the topology cannot.

This is the phenomenon of **nilpotent thickening**. We meet it in file 03 (where it gives the first infinitesimal
neighborhood of the diagonal) and file 05 (where its invisibility to étale morphisms is the central theorem of section
I.5).

### Why closed immersions are usually not étale

A closed immersion that is also étale is exactly an isomorphism onto a connected component of the target. That is the
content of theorem I.5.2 of the source: a closed immersion `Z → X` that is étale, with `Z` connected, is an isomorphism
from `Z` onto one of the connected components of `X`. Generic closed immersions — like `Spec 𝔽_p ↪ Spec ℤ`, which lands
at a single point of an otherwise much bigger scheme — are not étale, because they are not flat (cf. file 04). Closed
immersions become étale only when they isolate clopen pieces of the ambient scheme.

## Separated morphisms: a brief technical note

A morphism `f : X → Y` is **separated** if the diagonal `Δ : X → X ×_Y X` is a closed immersion. Equivalently, the locus
where "two points of `X` agree over `Y`" is a closed subscheme.

For affine `X` and `Y`, every morphism is automatically separated. The diagonal `Spec B → Spec(B ⊗_A B)` is a closed
immersion because the multiplication map `B ⊗_A B → B` is surjective.

The distinction matters only for non-affine schemes. The standard non-separated example is the **affine line with
doubled origin**: take two copies of `Spec k[t]`, identify them on the open subset `Spec k[t, t⁻¹]`, but leave the two
origins distinct. This produces a scheme with two points lying over the "physical" origin. The diagonal is not closed:
it is an immersion onto a non-closed subset of the product.

In Grothendieck's vocabulary:

- **Prescheme** = locally `Spec A` (no separation required).
- **Scheme** = separated prescheme.

We follow the source's usage. When the source says "prescheme," we say "prescheme." Separation hypotheses appear only in
a few proofs.

## What you can now read

The dictionary in one table:

```text
algebra                              geometry
-----------------------              ----------------------------
ring A                               affine scheme Spec A
ring map A → B                       morphism Spec B → Spec A
prime ideal 𝔭 ⊂ A                    point of Spec A
maximal ideal 𝔪                      closed point
residue field κ(𝔭) = Frac(A/𝔭)       residue field at the point
ideal I                              closed subscheme V(I)
quotient A/I                         restriction to V(I)
localization A[1/f]                  open subscheme D(f)
localization A_𝔭                     local ring at the point 𝔭
tensor product B ⊗_A C               fibered product Spec B ×_{Spec A} Spec C
base change B ⊗_A A'                 pulled-back family over Spec A'
B ⊗_A κ(𝔭)                           fiber over 𝔭
nilpotent in A                       infinitesimal direction
separated morphism                   diagonal is closed
```

Geometry and algebra are now two views of the same thing. We can phrase a question in either language and translate
freely.

The next file does the same for one missing piece: how to talk about how things vary on a scheme. That requires sheaves,
diagonals, and Kähler differentials. They are the algebraic version of the differential calculus you already know.
