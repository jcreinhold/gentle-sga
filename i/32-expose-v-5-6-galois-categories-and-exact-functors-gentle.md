# Exposé V §§5–6 (gentle): Galois categories and exact functors

<!-- source: V.5 -->

## What this file is about

Read symmetries off a geometric object by picking a vantage point — a basepoint, a fibre, some choice of where to stand.
The symmetry group falls out. A different vantage point gives a different group. That is uncomfortable. A geometric
object should not have its symmetries depend on which observer looked first. The right question is whether the choices
are linked, and how tightly.

They are linked tightly. Any two vantage points give groups that are canonically isomorphic, up to a controlled inner
ambiguity. Bundle every vantage point as an object and every passage between them as an arrow, and the bundle carries
one well-defined symmetry structure attached intrinsically, no choice required. The same packaging makes comparison
work. A structure-preserving map from one Galois category to another translates, once vantage points are fixed on both
sides, into a continuous homomorphism between the attached groups. This is exactly the machinery later files need to
turn a geometric map between schemes into a homomorphism between their fundamental groups.

## Opening: from one fibre functor to the formalism

V.4.1 produced an equivalence `𝒞 ≃ 𝒞(π)` once a fibre functor `F` was _fixed_. The two sections of Exposé V we cover
here ask: what is intrinsic to the Galois category, _independent_ of the choice of `F`?

§V.5 develops the answer. Different fundamental functors give isomorphic profinite groups, so they package into a
connected groupoid `Γ` — the **fundamental groupoid** — whose objects are fibre functors and whose morphisms are
isomorphisms between them. Each object has automorphism group `π_F = Aut(F)`. The "local system of fundamental groups"
is `Π`, the **fundamental pro-group**, whose fibre at `F` is `π_F`.

§V.6 develops the **functoriality**: an exact functor `H : 𝒞 → 𝒞′` of Galois categories corresponds (after fixing fibre
functors) to a _continuous_ homomorphism `u : π_{F′} → π_F`, where `F = F′ ∘ H`. The dictionary continues: `u` is
trivial, injective, surjective, etc., iff `H` has corresponding properties on objects of `𝒞`.

The two sections together say: the 2-category of Galois categories with fibre functors is anti-equivalent to the
2-category of profinite groups with continuous homomorphisms. Continuous group homomorphisms in / continuous group
homomorphisms out — this is what file 33 will need to translate geometric morphisms `f : S′ → S` into homomorphisms
`π₁(f) : π₁(S′, a′) → π₁(S, a)`.

## §V.5 Galois categories

### V.5.1 — Definition of Galois category

<!-- source: V.5.1 -->

_This definition says: a Galois category is a category equivalent to `𝒞(π)` for some profinite group `π`. Equivalently
(by V.4.1), a category satisfying axioms (G1)–(G3) and admitting a fibre functor `F` satisfying (G4)–(G6)._

**Definition.** A **Galois category** is a category `𝒞` equivalent to a category `𝒞(π)` for some compact totally
disconnected (i.e. profinite) topological group `π`. By V.4.1, this is equivalent to: `𝒞` satisfies (G1)–(G3), and there
exists a covariant functor `F : 𝒞 → FSet` satisfying (G4)–(G6).

Such a functor is called a **fundamental functor** of `𝒞`, or equivalently a **fibre functor**; the two names are
synonymous and we use both throughout files 32–33 (see file 29).[^v-5-1-1] It is pro-representable (V.4.1) by a
pro-object `P_F`, called a **fundamental pro-object** of `𝒞`.

The category of fibre functors of `𝒞` is anti-equivalent to the category of fundamental pro-objects (`F ↔ P_F`). For
corresponding `F` and `P`, `Aut(F)` is canonically isomorphic to the opposite of `Aut(P)`; the group denoted `π` in
V.4.1 is none other than `Aut(F)`. In the typical case `𝒞 = 𝒞(π)` with `F =` forget, the fundamental pro-object is the
projective system of finite discrete quotients`(π / U)_U`(over open invariant subgroups`U ⊂ π`).

### V.5.2 — Pro-objects of `𝒞(π)`

<!-- source: V.5.2 -->

_This proposition says: pro-objects of `𝒞(π)` are exactly the compact totally disconnected `π`-spaces._

**Proposition.** The category `Pro-𝒞(π)` is canonically equivalent to the category `𝒞′(π)` of compact totally
disconnected topological spaces with continuous left `π`-action.

**Proof sketch.** The functor `g : Pro-𝒞(π) → 𝒞′(π)` sends a projective system `Q = (Q_i)` to its limit
`lim_i Q_i ∈ 𝒞′(π)`. The functor in the opposite direction `h : 𝒞′(π) → Pro-𝒞(π)` is defined by
`h(X)(E) = Hom_{𝒞′(π)}(X, E)` for `X ∈ 𝒞′(π)` and `E ∈ 𝒞(π)`. One checks `g` and `h` are quasi-inverse: `hg` is
canonically the identity, and every `X ∈ 𝒞′(π)` is the projective limit of its finite discrete `π`-stable quotients (by
compactness and total disconnectedness of `X`, plus the profinite-group continuity argument).

**Note.** The dual statement also holds: `Ind-𝒞(π)` is equivalent to the category of (possibly infinite) sets on which
`π` acts continuously. We will not need this.

### V.5.3 — Connectedness via the fibre functor

<!-- source: V.5.3 -->

_This proposition says: an object `X ∈ 𝒞` is connected (in the categorical sense of file 29) iff `π` acts transitively
on `F(X)`._

**Proposition.** Let `𝒞` be a Galois category, `F` a fibre functor, `P = (P_i)` the associated pro-object. Let `X ∈ 𝒞`.
Then `X` is **connected** iff `π = Aut(F)` acts **transitively** on `E = F(X)`.

**Proof.** Reduce to the typical case `𝒞 = 𝒞(π)`, `F =` forget, where the statement is the trivial "a finite`π`-set is
connected iff`π` is transitive on it".

### V.5.4 — Connected objects ↔ Galois `P_i`

<!-- source: V.5.4 -->

_This corollary says: the conditions "`X` is connected and non-initial" / "`π` is transitive on `F(X) ≠ ∅`" / "`X ≅ P_i`
for some `i`" are equivalent. In short: connected objects of `𝒞` are exactly the Galois objects of the fundamental
pro-system._

**Corollary.** For `X ∈ 𝒞`, the following are equivalent:

1. `X` is connected and `X ≄ ∅_𝒞`.
1. `π` is transitive on `E = F(X)` and `F(X) ≠ ∅`.
1. `X ≅ P_i` for some `i ∈ I`.

The equivalence (1) ⟺ (3) was already in V.4 step (e).

### V.5.5 — When does a pro-object correspond to a closed subgroup?

<!-- source: V.5.5 -->

_This proposition says: a pro-object `Q = (Q_i)` of `𝒞` whose associated functor `G(X) = Hom(Q, X)` commutes with finite
sums is exactly `Q ≅ π / H` for a closed subgroup `H ⊆ π`._

**Proposition.** Let `Q = (Q_i)_{i ∈ I}` be a normalised pro-object of `𝒞`, and let
`G(X) := Hom(Q, X) = colim_i Hom(Q_i, X)` be the associated functor `𝒞 → Set`. The following are equivalent:

1. `G` commutes with finite direct sums.
1. `G` commutes with the sum of two objects.
1. The `Q_i` are connected and `Q_i ≄ ∅_𝒞`.
1. `Q ≅ π / H` (after fixing a fibre functor and identifying `𝒞 = 𝒞(π)`), where `H` is a closed subgroup of `π`.
1. The functor `G` is isomorphic to `E ↦ E^H` (`H`-invariants), for a closed subgroup `H ⊂ π`.

**Proof sketch.** (1) ⟹ (2) trivial; (2) ⟹ (3) is V.4 step (d) applied to `Q` instead of `P`. (3) ⟹ (4): `lim_i Q_i` is
non- empty (projective limit of non-empty finite sets); pick `a ∈ lim_i Q_i`. The orbit map `π → Q`, `g ↦ g ⋅ a`, is
continuous and surjective (by V.5.3 applied at each level), giving `π / H ≃ Q` for `H` the stabiliser. (4) ⟹ (5) and (5)
⟹ (1) are formal.

### V.5.6 — Recognising fundamental pro-objects

<!-- source: V.5.6 -->

_This proposition says: a pro-object `P′ = (P′_i)` of `𝒞` is fundamental iff `P′ ≅ P` (the chosen fundamental
pro-object) iff its associated functor `F′` commutes with sums-of-two and sends non-initial objects to non-empty sets._

**Proposition.** Let `𝒞` be a Galois category, `P` a fundamental pro-object, `F` the associated fibre functor. Let
`P′ = (P′_i)` be a pro-object of `𝒞` (in normal form), and `F′ =` associated functor. The following are equivalent:

1. `P′ ≅ P` (equivalently `F′ ≅ F`).
1. `P′` is **fundamental** (equivalently `F′` is fundamental).
1. `F′` carries `A ⨿ B` to `F′(A) ⨿ F′(B)` (and sends `∅_𝒞 → ∅`), and `X ≄ ∅_𝒞` ⟹ `F′(X) ≠ ∅`.
1. The connected non-initial objects of `𝒞` are exactly the `P′_i`.

**Proof.** (1) ⟹ (3) and (1) ⟹ (2) are trivial; (2) ⟹ (4) is V.5.4 applied to `P′`. Either (3) or (4) implies, by V.5.5,
that `P′ ≅ π / H` for some closed `H ⊂ π`. Under (3), every finite quotient of `π` admits a `π`-homomorphism
`π / H → π / U`, forcing `H ⊆ U`. Taking the intersection over all open invariant `U`, `H = {1}`, hence `P′ ≅ π = P`.

### V.5.7 — The fundamental groupoid

<!-- source: V.5.7 -->

_This corollary says: the fundamental functors of `𝒞` form a **connected groupoid** `Γ` — every two are isomorphic, and
the isomorphism is canonical up to inner automorphism by the relevant `π_F`. Following the topology analogy, "objects of
`Γ`" play the role of "base points"._

**Corollary.** Let `𝒞` be a Galois category. The fundamental pro-objects (resp. fundamental functors) of `𝒞` are
pairwise isomorphic. The category of fundamental functors is therefore a **connected groupoid** `Γ`, called the
**fundamental groupoid** of `𝒞`. The category of fundamental pro-objects is equivalent to the _opposite_ of `Γ`.

If `𝒞 = 𝒞(π)`, the automorphism group of any object of `Γ` is canonically isomorphic to `π`, the isomorphism being well-
determined up to inner automorphism. For `F`, `F′ ∈ Γ`, the set

```text
π_{F′, F}  :=  Hom(F, F′)  =  Isom(F, F′)
```

is the **set of path classes from `F` to `F′`**. In particular, `π_{F, F} = π_F` is the **fundamental group of `𝒞` at
`F`** (constructed in V.4). The fundamental pro-object `P` associated with `F` plays the role of a **universal covering
of the final object `e_𝒞` at `F`**.

### V.5.8 — Description via local systems on `Γ`

<!-- source: V.5.8 -->

_This proposition says: `𝒞` is equivalent to the category of covariant functors `Γ → Set` ("local systems on `Γ`")
satisfying the continuity condition that, for every `F ∈ Γ`, the value at `F` is a finite set on which `π_F` acts
continuously._

**Proposition.** The functor `X ↦ E_X`, where `E_X(F) := F(X)`, is an equivalence of `𝒞` with the category of covariant
functors `Γ → Set` satisfying:

```text
For every F ∈ Γ, E_X(F) is a finite set on which π_F acts continuously.
```

**Proof.** Pick a base point `F₀ ∈ Γ`, set `π₀ = Aut(F₀)`. The functor `ξ ↦ ξ(F₀)` from the second category to `𝒞(π₀)`
is an equivalence. Composed with `X ↦ E_X` and the natural equivalence `𝒞 → 𝒞(π₀)` from V.4.1, this confirms `X ↦ E_X`
is an equivalence.

This is the **local-system** description of `𝒞`: an object of `𝒞` is a (representable) finite-set-valued local system on
the fundamental groupoid `Γ`.

### V.5.9 — Pro-`𝒞` description

<!-- source: V.5.9 -->

_This corollary says: the analogue for `Pro-𝒞`. A pro-object of `𝒞` is a covariant functor `ξ : Γ → Top` such that, for
every `F ∈ Γ`, `ξ(F)` is a compact totally disconnected space with continuous `π_F`-action._

**Corollary.** The category `Pro-𝒞` is canonically equivalent to the category of covariant functors `ξ : Γ → Top`
satisfying: for every `F ∈ Γ`, `ξ(F)` is a compact totally disconnected topological space with continuous `π_F`-action.

The proof is the same as V.5.8.

### V.5.10 — The fundamental pro-group `Π`

<!-- source: V.5.10 -->

_This remark says: the canonical pro-object whose fibre at any `F ∈ Γ` is `π_F` is itself a pro-**group** `Π` of `𝒞` —
the **fundamental pro-group**, the algebraic version of "local system of fundamental groups". `Π` is determined up to
unique isomorphism (unlike a fundamental pro-object `P`, which is determined only up to non-canonical isomorphism)._

**Remark.** Use V.5.9 to define a canonical pro-object as the functor `f : Γ → Top` with `f(F) := π_F = Aut(F)`. Each
`π_F` is a profinite group (a fortiori a compact totally disconnected topological space) with continuous `π_F`-action by
inner automorphisms; the functoriality in `F` is automatic. The corresponding pro-object is itself a **pro-group** `Π`
of `𝒞`, called the **fundamental pro-group of `𝒞`**, defined by

```text
F(Π)  ≃  π_F    (functorially in F).
```

For any pro-object `X` of `𝒞`, there is a canonical morphism `Π × X → X` making `X` an object with left `Π`-action in
`Pro-𝒞`. (Define it pointwise: `π_F × F(X) → F(X)` is the natural action.)

### V.5.11 — `Π` versus `P`

<!-- source: V.5.11 -->

_This remark says: the fundamental pro-object `P` and the fundamental pro-group `Π` are different things. `P` is
connected and not a group; `Π` is a pro-group and in general not connected. `P` is determined up to non-canonical
isomorphism (every two are isomorphic, but not canonically); `Π` is determined up to unique isomorphism._

**Remark.** Do not confuse:

- A fundamental pro-object `P` ∈ Pro-`𝒞`. Connected; carries no natural group structure; determined up to
    (non-canonical) isomorphism.
- The fundamental pro-group `Π` ∈ Pro-`𝒞`. A pro-**group**; in general not connected. Determined up to _unique_
    isomorphism. `Π` is connected iff `π_F` (acting on itself by inner automorphism) is transitive iff `π_F = {1}` iff
    `𝒞` is equivalent to FSet.

In topology terms: `P` is the universal cover (a single space with no chosen base-point isomorphism between any two),
and `Π` is the "local system of fundamental groups" (a canonically-defined pro-object encoding the group at every
point). The corresponding **principal-homogeneous** language: `X` is **principal homogeneous under `G`** in `𝒞` when,
after fixing a fibre functor, `F(X)` is principal homogeneous under `G` (i.e. `G` acts simply transitively); **formally
principal homogeneous** when `F(X)` is empty or principal homogeneous.

If a fibre functor `F` is fixed, the data of an `X ∈ 𝒞` principal homogeneous under a finite group `G` operating on the
right, together with a chosen point `a ∈ F(X)`, is equivalent to a homomorphism `π_F → G`. (Take `E = G` with `π_F`
acting through `π_F → G` and `G` acting on `E` by right translation; the marked point is `e ∈ G`.) This is the
**classifying-pointed covers** picture: principal coverings up to iso, _with chosen fibre point_, are classified by
`Hom_{cts}(π_F, G)`.

## §V.6 Exact functors from one Galois category to another

<!-- source: V.6 -->

A morphism between two Galois categories is an _exact functor_. After fixing fibre functors, exact functors correspond
to continuous group homomorphisms in the opposite direction (V.6.1 –V.6.3). The remaining propositions V.6.4–V.6.13 fill
in the **dictionary**: when is the homomorphism trivial / injective / surjective / an isomorphism, in terms of
properties of the original functor on the level of objects of `𝒞`.

### V.6.1 — Three formulations of exactness

<!-- source: V.6.1 -->

_This proposition says: for `H : 𝒞 → 𝒞′`, "exact" / "left exact + carries sums to sums + carries epis to epis" / "the
composite `F = F′ ∘ H` is again a fundamental functor on `𝒞`" are all equivalent._

**Proposition.** Let `𝒞`, `𝒞′` be Galois categories, `H : 𝒞 → 𝒞′` a covariant functor, `F′` a fundamental functor on
`𝒞′`, and `F := F′ ∘ H`. The following are equivalent:

1. `H` is **exact** (left exact and right exact).
1. `H` is left exact, transforms finite sums into finite sums, and transforms epimorphisms into epimorphisms;
    equivalently, transforms non-initial objects into non-initial objects.
1. `F` is a fundamental functor on `𝒞`.

**Proof.** (1) ⟹ (2) general fact about categories. (2) ⟹ (3): `F = F′ ∘ H` is left exact (composition of left-exact
functors) and is finite-set-valued; the criterion V.5.6 (3) applies to verify (G5)/(G6). (3) ⟹ (1): exactness of `F` and
conservativity of `F` (axiom (G6)) lift back through `H`.

### V.6.2 — Continuous group homomorphisms

<!-- source: V.6.2 -->

_This corollary says: any exact functor `H : 𝒞 → 𝒞′` arises (up to equivalence) from a continuous homomorphism
`u : π′ → π` of profinite groups, via `H_u : 𝒞(π) → 𝒞(π′)`._

**Corollary.** For an exact functor `H : 𝒞 → 𝒞′` of Galois categories, there exist equivalences `𝒞 ≃ 𝒞(π)` and
`𝒞′ ≃ 𝒞(π′)` that transform `H` into the functor `𝒞(π) → 𝒞(π′)` associated with a continuous homomorphism `u : π′ → π`
of topological (profinite) groups.

**Proof.** Set `F = F′ ∘ H` (a fundamental functor on `𝒞` by V.6.1). The transposed assignment `^t H : Γ′ → Γ`,
`F′ ↦ F = F′ ∘ H`, defines, on automorphism groups,

```text
^t H : π_{F′}  ⟶  π_F,    where F = ^t H(F′).
```

For every finite continuous `π_F`-set `E`, the group `π_{F′}` acts continuously on it through `^t H`, so applied to the
quotients `π_F / U` (`U` open invariant) we see that `^t H` itself is continuous. Set `u = ^t H`.

### V.6.3 — Functorial form

<!-- source: V.6.3 -->

_This corollary says: the category of exact functors `𝒞 → 𝒞′` is equivalent to the category of functors `Γ′ → Γ` whose
associated group homomorphisms (at any one point) are continuous._

**Corollary.** Let `𝒞`, `𝒞′` be Galois categories with fundamental groupoids `Γ`, `Γ′`. The category of exact functors
`𝒞 → 𝒞′` is equivalent to the category of functors `U : Γ′ → Γ` such that, for every `F′ ∈ Γ′` (equivalently, for one
`F′ ∈ Γ′`, since transitivity is automatic in a connected groupoid), the corresponding homomorphism

```text
π_{F′}  =  Aut(F′)  ⟶  π_F  =  Aut(F),    F = U(F′),
```

is continuous.

### Pointed objects

A **pointed object** of `(𝒞, F)` is a pair `(X, a)` with `X ∈ 𝒞` and `a ∈ F(X)`. Equivalently (after the equivalence
`𝒞 ≃ 𝒞(π_F)`), a finite continuous `π_F`-set with a chosen point. **Connected** pointed objects correspond, by V.5.3, to
**open subgroups** `U ⊆ π_F` (the stabiliser of the marked point). For two open subgroups `U, V ⊆ π_F` corresponding to
connected pointed objects `X, Y`: a pointed `𝒞`-morphism `X → Y` exists iff `U ⊆ V`, and is then unique.

The dictionary V.6.4–V.6.13 leverages this: properties of `u : π_{F′} → π_F` are read off from properties of `H(X)` for
chosen connected pointed `X ∈ 𝒞`.

### V.6.4 — Pointed sections and complete decomposition

<!-- source: V.6.4 -->

*This proposition says: for a connected pointed object `X` of `𝒞` corresponding to an open subgroup `U ⊆ π_F`, "pointed
section of `H(X)` exists" iff `U ⊇ u(π_{F′})`, and "`H(X)`is completely decomposed" iff`U`contains the closed normal
subgroup generated by`u(π_{F′})`.*

**Proposition.** Let `X` be a connected pointed object of `𝒞`, associated with an open subgroup `U ⊆ π_F`. Then:

- `U ⊇ u(π_{F′})` ⟺ `H(X)` admits a **pointed section** (over the final object `e_{𝒞′}`).
- `U ⊇ ⟨ u(π_{F′}) ⟩^{normal closure}` ⟺ `H(X)` is **completely decomposed**, i.e. isomorphic to a finite disjoint sum
    of final objects of `𝒞′`.

A **section** of `X ∈ 𝒞` over the final object `e_𝒞` is a morphism `e_𝒞 → X`, equivalently a `π_F`-fixed point of
`F(X)`. A **pointed section** when `(X, a)` is pointed is a section sending `e_𝒞`'s marked point to `a`.

### V.6.5 — Trivial `u`

<!-- source: V.6.5 -->

_This corollary says: `u` is trivial iff every `H(X)` is completely decomposed._

**Corollary.** `u` is trivial iff for every `X ∈ 𝒞`, `H(X)` is completely decomposed in `𝒞′`.

### V.6.6 — Containing the kernel

<!-- source: V.6.6 -->

_This proposition says: for a connected pointed `X′` of `𝒞′` with associated open `U′ ⊆ π_{F′}`, "`U′ ⊇ Ker u`" iff
there is a pointed homomorphism from the **neutral connected component** of `H(X)`(for some pointed`X ∈ 𝒞`) to `X′`. If
`u`is surjective, equivalently`X′`is isomorphic to`H(X)`for some pointed`X`._

**Proposition.** Let `X′` be a connected pointed object of `𝒞′`, associated with an open subgroup `U′ ⊆ π_{F′}`. Then
`U′ ⊇ Ker u` iff there exists a connected pointed object `X ∈ 𝒞` and a pointed homomorphism

```text
H(X)₀  ⟶  X′
```

from the neutral connected component `H(X)₀` of `H(X)` to `X′`. Equivalently, `X′` is isomorphic, as a pointed object,
to a quotient of `H(X)₀`. If furthermore `u` is **surjective**, this is also equivalent to the statement that
`X′ ≅ H(X)` for some pointed `X ∈ 𝒞`.

The **neutral connected component** of a pointed object `X` is the unique connected pointed sub-object of `X`; under
`𝒞 ≃ 𝒞(π_F)` it is the orbit of the marked point in `F(X)` (V.5.3).

### V.6.7 — Containing the kernel, unpointed form

<!-- source: V.6.7 -->

_This corollary says: the V.6.6 condition is equivalent (after forgetting the pointed structure) to "there is a morphism
from a connected component of `H(X)` to `X′` for some `X` in `𝒞`"._

**Corollary.** `U′ ⊇ Ker u` iff there exists `X ∈ 𝒞` (which may be assumed connected) and a morphism from a connected
component of `H(X)` to `X′`. If `u` is surjective, also iff `X′ ≅ H(X)` for some `X ∈ 𝒞`.

### V.6.8 — Injectivity of `u`

<!-- source: V.6.8 -->

_This corollary says: `u` is injective iff for every `X′ ∈ 𝒞′` there exist `X ∈ 𝒞` and a morphism from a connected
component of `H(X)` to `X′`._

**Corollary.** `u : π_{F′} → π_F` is injective iff for every `X′ ∈ 𝒞′`, there exist `X ∈ 𝒞` and a morphism from a
connected component of `H(X)` to `X′`.

### V.6.9 — Surjectivity of `u` ⟺ `H` fully faithful

<!-- source: V.6.9 -->

_This proposition says: three equivalent forms of "`u` is surjective" — including "`H` is fully faithful"._

**Proposition.** The following are equivalent:

1. `u : π_{F′} → π_F` is **surjective**.

1. For every connected `X ∈ 𝒞`, `H(X)` is connected in `𝒞′`.

1. `H : 𝒞 → 𝒞′` is **fully faithful**, i.e.

    ```text
    Hom_𝒞(X, Y)  ⟶  Hom_{𝒞′}(H(X), H(Y))
    ```

    is bijective for every `X, Y ∈ 𝒞`.

**Proof.** Combine V.6.6 (with `u` surjective) and V.5.4 to match (1) ⟺ (2). For (1) ⟺ (3), the equivalence is
straightforward from the `π_F` ↔ `π_{F′}`-set translation.

### V.6.10 — Isomorphism of `u` ⟺ equivalence

<!-- source: V.6.10 -->

_This corollary says: `u` is an isomorphism iff `H` is an equivalence iff "(1) `H` carries connected to connected and
(2) every object of `𝒞′` is in the essential image of `H`"._

**Corollary.** `u : π_{F′} → π_F` is an isomorphism iff `H : 𝒞 → 𝒞′` is an **equivalence of categories**, equivalently
iff:

1. For every connected `X ∈ 𝒞`, `H(X)` is connected.
1. Every object of `𝒞′` is isomorphic to one of the form `H(X)` for some `X ∈ 𝒞`.

### V.6.11 — Composability conditions

<!-- source: V.6.11 -->

_This proposition says: for a composable pair `H : 𝒞 → 𝒞′`, `H′ : 𝒞′ → 𝒞″` with associated `u, u′`, the inclusion
`Ker u ⊆ Im u′` (resp. `⊇`) translates into specific decomposition / covering properties of `H' ∘ H` (resp. `H, H′`
separately)._

**Proposition.** Let `H : 𝒞 → 𝒞′` and `H′ : 𝒞′ → 𝒞″` be exact functors of Galois categories, let `F″` be a fibre functor
on `𝒞″`, set `F′ = F″ ∘ H′`, `F = F′ ∘ H`, and consider the homomorphisms

```text
u′ : π_{F″} → π_{F′},     u : π_{F′} → π_F.
```

Then:

- `Ker u ⊆ Im u′` (i.e. `u u′` trivial) ⟺ for every `X ∈ 𝒞`, `H′(H(X))` is completely decomposed.
- `Ker u ⊇ Im u′` ⟺ for every connected pointed `X′ ∈ 𝒞′` such that `H′(X′)` admits a pointed section, there exist
    `X ∈ 𝒞` and a homomorphism from a connected component of `H(X)` to `X′`.

**Proof.** First assertion follows from V.6.4 last clause. Second from V.6.4 + V.6.6.

### V.6.12 — A subtle non-equivalence

<!-- source: V.6.12 -->

_This remark says: V.6.8 ("`u` injective ⟺ every `X′` admits a morphism from a component of some `H(X)`") does **not**
in general imply "every `X′` is isomorphic to an `H(X)`". The latter holds iff `u` is an isomorphism onto a **direct
factor** subgroup of `π_F`. In practice, the concrete way to verify this is to construct a homomorphism
`π_F → π_{F′}`inverse to`u`on the right, via a suitable exact functor`𝒞′ → 𝒞`._

**Remark.** Under V.6.8's conditions, it is not in general true that every `X′ ∈ 𝒞′` is isomorphic to an `H(X)`. The
condition "every connected (and hence every) `X′ ∈ 𝒞′` is isomorphic to some `H(X)`" is equivalent to "`u` is an
isomorphism onto a **direct factor** of `π_F`". In practice one verifies this by building a one-sided inverse
`π_F → π_{F′}` from a suitable exact functor `𝒞′ → 𝒞`.

### V.6.13 — The over-`S` Galois category

<!-- source: V.6.13 -->

*This proposition says: for a connected `S ∈ 𝒞`, the slice category `𝒞 / S` is Galois, and the functor `H(X) = X × S`
from `𝒞` to `𝒞 / S` is exact. The associated homomorphism `u : π_{F'} → π_F`is the inclusion of the open
subgroup`U ⊂ π_F`stabilising a chosen marked point`a ∈ F(S)`.*

**Proposition.** Let `𝒞` be a Galois category with fibre functor `F`, let `S ∈ 𝒞` be connected, and let `𝒞′ := 𝒞 / S` be
the slice category of objects over `S`. Then `𝒞′` is Galois, and the functor

```text
H : 𝒞 ⟶ 𝒞′,    X ↦ X × S
```

is exact. Pick `a ∈ F(S)` and define `F′ : 𝒞′ → FSet` by

```text
F′(X′)  =  ` inverse image of `a` under `F(X′) → F(S)`.
```

Then `F ≃ F′ ∘ H`, and the associated homomorphism

```text
u : π_{F′}  ⟶  π_F
```

is an **isomorphism** of `π_{F′}` onto the open subgroup `U ⊆ π_F` stabilising `a ∈ F(S)`.

(Proof left to the reader, per the source.)

This is the algebraic analogue of "fundamental group of a covering space `S → B` is a subgroup of the fundamental group
of `B`".

## Worked example: inflation along `ℤ̂ → ℤ_p`

Take `𝒞 = 𝒞(ℤ̂)` and `𝒞′ = 𝒞(ℤ_p)`. The canonical projection `ℤ̂ ↠ ℤ_p` (inflation; `ℤ̂ = ∏_q ℤ_q` projects to its `p`-
component) defines a functor `H : 𝒞(ℤ̂) → 𝒞(ℤ_p)` by restriction of action: a continuous `ℤ̂`-set becomes a continuous
`ℤ_p`-set via the pullback of the action.

Wait — for `H : 𝒞 → 𝒞′` we need a homomorphism `u : π_{F′} → π_F`, i.e. `u : ℤ_p → ℤ̂`. This is the _inclusion_ of `ℤ_p`
into `ℤ̂` as the `p`-factor. The functor `H : 𝒞(ℤ̂) → 𝒞(ℤ_p)` is then `E ↦ E_{| ℤ_p}` (restriction of the `ℤ̂`-action to
the sub-`ℤ_p` action via the inclusion `ℤ_p ↪ ℤ̂`).

Verify against V.6.4–V.6.10:

- `u(ℤ_p) = ℤ_p ⊂ ℤ̂` is dense in the `p`-part but **not surjective** (`ℤ̂` has many other components `ℤ_q`, `q ≠ p`).
- `u` is **injective** (it's the inclusion).
- By V.6.9, `H` is _not_ fully faithful, since `u` is not surjective. Indeed: there are non-iso `ℤ̂`-sets that become
    iso as `ℤ_p`-sets (e.g. `ℤ / qℤ` for `q ≠ p` becomes a trivial `ℤ_p`-set, isomorphic to a sum of `q` copies of the
    point).
- By V.6.8, every `X′ ∈ 𝒞(ℤ_p)` admits a morphism from a component of some `H(X)`. Concretely: every finite continuous
    `ℤ_p`-set comes from a finite continuous `ℤ̂`-set (lift the action through the projection `ℤ̂ ↠ ℤ_p`), so every `X′`
    is in the essential image of `H`.
- By V.6.12, the condition "every `X′` is isomorphic to some `H(X)`" combined with `u` injective tells us `u : ℤ_p ↪ ℤ̂`
    is an isomorphism onto a **direct factor**. This is true (`ℤ̂ = ℤ_p × ∏_{q ≠ p} ℤ_q`), confirming the
    `→ direct factor` subtlety.

The arithmetic content: when the base scheme `S` has a Galois- covering structure that splits into independent prime
parts (cf. file 33's `Spec ℤ` arithmetic), the étale fundamental group decomposes correspondingly.

## What this prepares

File 33 (= V.7, V.8, V.9) is the **geometric application**: take `𝒞 =` finite étale coverings of a connected locally
noetherian`S`, with fibre functor`F_a =` geometric points over a chosen geometric point `a`. The axioms (G1)–(G6) hold
(file 30's V.1 sorites, file 31's V.3.1, V.3.4, V.3.5, V.3.7), so V.4.1 yields a profinite group `π = π₁(S, a)` and an
equivalence `𝒞 ≃ 𝒞(π)`. The fundamental groupoid `Γ` of file 32 becomes the **groupoid of geometric points of `S`**
(V.5.7 specialised); the path classes `π₁(S; a, a′)` of V.7 are the morphisms in this groupoid; and the
**functoriality** V.6.1–V.6.13 becomes the functoriality of `π₁` under morphisms of base schemes: `f : S′ → S` connected
⟹ exact functor `f^* : 𝒞(S) → 𝒞(S′)` ⟹ continuous homomorphism `π₁(f; a′) : π₁(S′, a′) → π₁(S, a)`.

[^v-5-1-1]: Throughout files 32–33 we use _fibre functor_ and _fundamental functor_ interchangeably.
