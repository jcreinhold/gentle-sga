# The main properties of étale morphisms

## What this file is about

A good definition earns its keep by what falls out of it. The previous file isolated the algebraic notion that wants to
play the role of a covering map. It was short — two clauses, both technical. Whether the choice is right has to be
settled by what the clauses can prove.

This file collects four payoffs. Each one says that the new notion behaves the way a covering ought to behave: it is
rigid where rigidity is the right word, determined by very little data, indifferent to certain kinds of algebraic noise,
and always presentable in a clean local form. Read together, they amount to the case for the definition. The four
results are stated here with sketches; the full proofs are gathered later, in the chapter that walks through the
original source line by line.

We have a definition: flat plus unramified. The definition is short. What it does is not. The slogan that accompanied us
through file 04 — "étale is the algebraic analogue of a local isomorphism" — has not yet been earned. So far it is a
hope built on a covering-map analogy. This file earns it.

Sections I.5 through I.8 of the source establish four facts, each striking enough to be a centerpiece. An étale morphism
that is also set-theoretically injective with purely inseparable residue extensions is literally an open immersion. The
category of étale schemes over `Y` is unchanged when you replace `Y` by a nilpotent thickening. Over a complete local
ring, finite étale extensions are determined entirely by the residue field. And every étale algebra has a uniform local
form: it is, locally, `(A[t]/F)_{(F'(t))}` for some monic `F`. The four facts together say: étale morphisms are
extraordinarily rigid, determined by surprisingly little data, and they behave exactly the way "local isomorphism"
should behave.

This file states each fact, says why it is true, and motivates the shape of the proof. The proofs in detail live in file
11\.

## A small bit of setup: radicial morphisms

The four properties all rest on one extra condition. We define it now.

A morphism `f : X → Y` is **radicial** if it is "set-theoretically injective with purely inseparable residue
extensions." Equivalently, `f` is **universally injective**: every base change `X ×_Y Y' → Y'` is injective on points.

The English term you might know is "universally injective." The source uses "radicial" because that is the French. We
keep both.

The geometric content sits in the residue extensions. A field extension `k ⊆ k'` is **purely inseparable** when every
element of `k'` satisfies a polynomial of the form `tᵖⁿ - a` over `k`, with `a ∈ k`. In characteristic 0 the only such
extension is `k = k'`. In characteristic `p`, the model case is the Frobenius pair `k ⊆ k^{1/p}`: each element of `k'`
has a unique `p`-th power in `k`. Either way, the extension has no nontrivial automorphism over `k` — no Galois action,
nothing to split.

That is why radicial is the right partner for étale. Étale gives flat plus unramified — a clean local algebraic match.
Radicial strips away the only remaining flexibility étale tolerates: the residue field at a point of `X` may differ from
the residue field at its image, and Galois may permute the points above. Force the residue extensions to be purely
inseparable and that flexibility collapses. The morphism has nowhere left to go but onto an open piece of `Y`. So in
characteristic 0, "radicial" reduces to "set-theoretically injective with identical residue fields." In characteristic
`p`, Frobenius-style extensions are allowed too.

### Examples

- An immersion (open or closed) of irreducible reduced schemes is radicial.
- The **Frobenius morphism** `F : Spec 𝔽_p[t] → Spec 𝔽_p[t]`, defined on rings by `t ↦ tᵖ` (in characteristic `p`), is
    radicial. On points it sends each closed point to its `p`-th power, which is set-theoretically injective; the
    residue extension at each point is `𝔽_p ⊆ 𝔽_p`-via-`p`-th-power, purely inseparable.
- The closed immersion `Spec k[t]/(tᵖ) → Spec k[t]` is also radicial: it is set-theoretically a single point, and the
    residue extension is the identity (trivially purely inseparable).
- A finite separable field extension `Spec k' → Spec k` (with `k' ≠ k`) is **not** radicial. The residue extension is
    separable, not purely inseparable. Galois acts on it.

### Radicial plus unramified is monomorphism

A useful characterization, due to Grothendieck (EGA IV §17.2.6): for a morphism `f : X → Y` locally of finite type, the
following are equivalent:

- `f` is a monomorphism in the category of schemes.
- `f` is radicial and unramified.
- For each `y ∈ Y`, the fibre `f⁻¹(y)` is empty or `κ(y)`-isomorphic to `Spec(κ(y))`.

In words: radicial + unramified is exactly the condition that each non-empty fiber is a single point with the residue
field of the base.

The key conjunction in this file is **étale + radicial**. Story 1 shows it forces an open immersion.

## Story 1: étale plus radicial equals open immersion

> A morphism `f : X → Y` of finite type is an **open immersion** if and only if it is **étale and radicial**.

This is theorem I.5.1 of the source. It is the **fundamental property** of étale morphisms, and the slogan it deserves
is:

> Étale almost is open immersion. Only the residue-field flexibility prevents the collapse.

### Why this is striking

Étale on its own does not force open immersion. A finite separable field extension `Spec ℂ → Spec ℝ` is étale but degree
2; an open immersion must have degree 1.

Radicial on its own does not force open immersion. The Frobenius morphism is radicial but not étale (it is purely
inseparable, the opposite of separable; not flat-and-unramified in the right way).

The conjunction works. Étale ensures local rings match cleanly: no infinitesimal slack, the family varies without
algebraic jumps. Radicial ensures the morphism is set-theoretically a bijection in a controlled way and that residue
fields match exactly. Together, they force `f` to be the inclusion of an open subscheme.

### Why we care

Two corollaries do most of the work.

**Sections of étale morphisms are open immersions onto components.** A section `s : Y → X` of an étale morphism `X → Y`
is automatically a closed immersion: an étale morphism is locally of finite type and hence locally separated, so its
diagonal `Δ_{X/Y}` is an immersion; on each affine piece this immersion is closed, so `s` (which is the base change of
`Δ_{X/Y}` along `s`) is a closed immersion. It is étale by the corollary I.4.8 we used in file 04 (étale source mapping
to an étale target — the graph trick). And it is radicial (sections are set-theoretically injective). So `s` is, by
I.5.1, an open immersion. Sections of étale morphisms cut out **open subschemes** of the source.

**Maps into étale schemes are determined by their value at one point.** If `Y` is connected, `X` is étale over `S`, and
`f, g : Y → X` are two `S`-morphisms agreeing at a single point with the same residue map, then `f = g`. Their equalizer
is open (because `X / S` is unramified, the equalizer is a section of the étale `X ×_S X → S`) and closed (because
`X / S` is separated). A nonempty clopen of a connected scheme is the whole scheme.

This is the algebraic version of analytic continuation: an analytic function on a connected open set is determined by
its values on any open piece. With "analytic" replaced by "étale" and "connected open" replaced by "connected scheme,"
the same rigidity holds.

#### Aside (elaborator analogy).

_Skip this paragraph if dependent-type-theory elaboration and unification are not part of your background; nothing later
depends on it._

The same rigidity is the algebraic-geometry analog of unique-up-to-judgmental-equality solutions of unification
problems. Once you have committed at one point, the rest is forced.

## Story 2: lifting across nilpotent thickenings

> The category of étale `Y`-schemes is the same as the category of étale `Y₀`-schemes, for any nilpotent thickening
> `Y₀ → Y`.

Story 1 fixed an étale morphism by what it does at one point on a connected base. Story 2 fixes the whole étale category
by what it does on a smaller base. The thickening direction is new; the rigidity is the same. This is the conjunction of
theorems I.5.5 (uniqueness) and I.8.3 (existence) of the source.

### An equivalent modern definition

Most contemporary expositions take this lifting property as the **definition** of étale. Grothendieck's EGA IV 17.1.1
reads:

> A morphism `f : X → Y` is **formally étale** if, for every closed subscheme `Y₀′ ⊂ Y′` of an affine scheme `Y′`
> defined by a nilpotent ideal of `𝒪_{Y′}`, and every morphism `Y′ → Y`, the restriction map
>
> `Hom_Y(Y′, X) → Hom_Y(Y₀′, X)`
>
> is **bijective**. The morphism `f` is **étale** if it is formally étale and locally of finite presentation.

The black-box appendix records this as [`formally-etale-lifting`](appendix-black-boxes.md#formally-etale-lifting). The
equivalence with our definition (flat + unramified, locally of finite type) is exactly the conjunction of theorems I.5.5
and I.8.3 below — the first gives uniqueness of the lift, the second gives existence. So the gentle SGA's "flat +
unramified + finite-type" definition and the modern "lifting + finite-presentation" definition are equivalent, and the
equivalence is the substance of section I.5 + I.8.

### What's a nilpotent thickening

A **nilpotent thickening** `Y₀ → Y` is a closed immersion of schemes with the same underlying topological space, defined
by a sheaf of ideals `𝓘 ⊂ 𝒪_Y` with `𝓘ⁿ = 0` for some `n`. Concretely, `Y₀` and `Y` look identical as topological
spaces; the difference is in the structure sheaf, where `Y` has additional nilpotents.

In the affine case: `Y₀ = Spec(A/I)`, `Y = Spec A`, with `I ⊂ A` nilpotent (`Iⁿ = 0`).

The smallest example: `Y₀ = Spec k`, `Y = Spec k[ε]/(ε²)` (the [fat point](glossary.md#fat-point)). Same underlying
space (one point), but `Y` has the infinitesimal direction `ε`.

### What lifting should mean

You have an étale `Y₀`-scheme `X₀`. Question: can you **lift** `X₀` to an étale `Y`-scheme `X` such that
`X ×_Y Y₀ ≃ X₀`?

Two sub-questions: existence (does `X` exist?) and uniqueness (if it does, is it unique up to canonical isomorphism?).

The answer to both is yes. Uniqueness is theorem I.5.5; existence is theorem I.8.3.

### The uniqueness theorem (I.5.5)

> Let `S` be a scheme, `S₀ ⊆ S` a closed subscheme with the same underlying space (a nilpotent thickening). Let `X, Y`
> be `S`-schemes, and `X₀ = X ×_S S₀`, `Y₀ = Y ×_S S₀`. If `X` is étale over `S`, then the natural map
>
> `Hom_S(Y, X) → Hom_{S₀}(Y₀, X₀)`
>
> is **bijective**.

In words: a morphism `Y → X` over `S` is the same data as a morphism `Y₀ → X₀` over `S₀`. The thickening is invisible at
the level of morphisms into étale things.

The algebraic shadow: for a nilpotent ideal `I ⊆ A` and an étale `A`-algebra `B`, the restriction map

```text
Hom_A(B, R) → Hom_{A/I}(B/IB, R/IR)
```

is a bijection for any `A`-algebra `R`. Morphisms into étale algebras do not contribute extra data through nilpotent
ideals.

### Why this is true (one-paragraph version)

A morphism `Y → X` over `S` factors uniquely as: the value at one point, plus the connected component of `X` it lands
in. Story 1 told us sections of étale morphisms are open immersions onto components, so the connected component data
does not change under nilpotent thickening (thickening adds nilpotents, not new components of the underlying space). The
value at one point also does not change, because the residue field at the point is the same for `S` and `S₀`. So the
morphism does not change.

### The existence theorem (I.8.3)

> The functor `X ↦ X ×_Y Y₀` from étale `Y`-schemes to étale `Y₀`-schemes is an **equivalence of categories**.

So every étale `Y₀`-scheme lifts uniquely to an étale `Y`-scheme. The two categories are interchangeable.

The proof has a local part and a gluing part. Locally, a single étale algebra over `A/I` lifts to an étale algebra over
`A`, using the local form of étale algebras (story 4 below) to choose explicit lifts. Globally, the local lifts glue
uniquely because of theorem I.5.5: any two local lifts agree on overlaps by the uniqueness statement.

### What this buys

Étale geometry is **completely insensitive** to nilpotent thickenings. If you want to study étale `Y`-schemes, you can
pass to `Y_red` (the underlying reduced subscheme) without losing anything. This is a major simplification, and it is
the foundation of étale cohomology in later exposés.

## Story 3: étale extensions of complete local rings

The first half of the chapter pinned down rigidity from the outside: étale + radicial is open immersion (story 1), and
the étale category is blind to nilpotent thickenings (story 2). Both say what étale morphisms cannot do. The second half
asks what they look like. Story 3 reads off finite étale theory over a complete local ring from a single residue field.
Story 4 writes every étale local algebra in one explicit form.

> Over a **complete** noetherian local ring `A` with residue field `k`, finite étale `A`-algebras correspond bijectively
> (under `B ↦ B ⊗_A k`) to finite separable `k`-algebras.

This is theorem I.6.1 of the source. It is the most concrete version of "the étale theory is determined by the residue
field."

### What it says

Over `A` complete, you can read off the entire finite étale theory from the residue field `k`. Every finite separable
extension of `k` lifts uniquely to a finite étale `A`-algebra.

This is a strong analog of the topological statement: an unramified covering of a manifold is determined by the action
of the fundamental group. The "fundamental group" here is the absolute Galois group `Gal(k^sep / k)`, which classifies
finite separable extensions of `k`.

#### Sidebar: the absolute Galois group of a finite field

This sidebar paraphrases Lenstra's _Galois Theory for Schemes_ §2.5; readers who have seen Galois theory of finite
fields can skip it.

For a finite field `𝔽_q` (`q = p^a`), the only finite extensions inside an algebraic closure `𝔽̄_q` are the fields

```text
𝔽_{qⁿ} = { α ∈ 𝔽̄_q : α^{qⁿ} = α },    n ≥ 1.
```

Each `𝔽_{qⁿ}` is Galois over `𝔽_q` with cyclic Galois group

```text
Gal(𝔽_{qⁿ} / 𝔽_q) ≅ ℤ / nℤ,
```

generated by the **Frobenius automorphism** `F : α ↦ α^q`. So the finite separable extensions of `𝔽_q` are classified by
`n` (one extension of each degree), and the Galois action is generated by a single element, Frobenius.

Taking projective limits over `n`, the **absolute Galois group** of `𝔽_q` is

```text
Gal(𝔽̄_q / 𝔽_q) ≅ ℤ̂ = lim_n ℤ/nℤ    (the profinite completion of ℤ),
```

with `1 ∈ ℤ̂` corresponding to Frobenius. The closure of the subgroup generated by `F` is the whole group; in this sense
Frobenius is a _topological generator_ of the absolute Galois group.

(File 33 (V.8.1) closes this sidebar's forward-reference: the absolute Galois group `Gal(k^sep / k)` of any field is
exactly the **étale fundamental group** `π₁(Spec k, ā)`, where `ā` is the geometric point chosen by an algebraic closure
of `k`.)

That is the structure I.6.1 transports across complete local rings: an étale `A`-algebra of degree `n` corresponds to a
finite separable `k`-algebra of degree `n`, which (when `k = 𝔽_q`) is `𝔽_{qⁿ}` (or a product of such), parametrized by
which `n` and how Frobenius acts.

### Hensel's lemma in disguise

Theorem I.6.1 contains the classical [**Hensel's lemma**](appendix-black-boxes.md#hensel) as a special case.

> Let `A` be a complete noetherian local ring with residue field `k`. Let `F ∈ A[t]` be a polynomial whose reduction
> `F̄ ∈ k[t]` factors as `F̄ = ḡ · h̄` with `ḡ`, `h̄` coprime monic. Then `F` factors as `F = g · h` over `A`, with
> `g, h ∈ A[t]` lifting `ḡ`, `h̄`.

Hensel's lemma says coprime factorizations lift from the residue field to the complete ring. Theorem I.6.1 generalizes
this to: finite separable extensions lift, and morphisms between them lift, and the categorical structure lifts.
Hensel's lemma is the "factorization-of-a-polynomial" version.

### Why complete?

The completeness hypothesis is essential. Without it, lifting fails.

For instance, `A = ℤ_{(p)}` (the localization, **not** the completion) has residue field `𝔽_p`. A finite separable
extension of `𝔽_p` corresponds to an irreducible polynomial over `𝔽_p`. To lift, we would lift the polynomial — but the
lift is not unique up to isomorphism: different lifts can produce non-isomorphic étale algebras.

The completion `A = ℤ_p` (the `p`-adic integers) eliminates the ambiguity. Hensel + uniqueness gives a canonical lifted
polynomial, hence a canonical étale algebra.

### A concrete instance

Take `A = ℤ₃`, residue field `𝔽₃`. A finite étale degree-3 algebra over `ℤ₃` corresponds, by theorem I.6.1, to a finite
separable degree-3 algebra over `𝔽₃`.

Such an algebra is `𝔽_27 = 𝔽₃[t]/(F̄)` for some monic irreducible cubic `F̄ ∈ 𝔽₃[t]`. Lift `F̄` to a monic cubic
`F ∈ ℤ₃[t]`. By Hensel, `F` is irreducible over `ℤ₃`, and `B = ℤ₃[t]/F` is the corresponding étale `ℤ₃`-algebra of
degree 3. Different lifts give isomorphic `B`.

This is a corner of class field theory in disguise. The unramified extensions of `ℚ_p` correspond, under theorem I.6.1,
to extensions of the residue field `𝔽_p` — and the absolute Galois group of `𝔽_p` is generated by the Frobenius
automorphism, which classifies them.

## Story 4: local form

Story 3 classified the finite étale theory over a complete local ring by residue data. It still left the étale algebras
themselves abstract. Story 4 writes them down.

> Every étale local algebra is, locally, `(A[t]/F)_{(F'(t))}` for some monic polynomial `F` whose derivative `F'(t)` is
> a unit after the localization.

This is theorem I.7.6 of the source — the algebraic version of the inverse function theorem.

### What it says

Étale local algebras are not abstract objects. Every one of them is, up to localization, a quotient of a polynomial ring
by a single monic polynomial, localized at a point where the polynomial's formal derivative is a unit.

In other words:

> **Étale local algebras are locally `(A[t]/F)_{(F')}`.**

That is the standard form. We saw in file 04 that `B = A[t]/F` for monic `F` is automatically free, hence flat, and that
the unramified condition is exactly `F'(t)` being a unit. So the "standard" examples we have been computing are not
isolated cases — they are the universal local model.

### Why this is the right form

Two reasons.

**Construction.** Standard étale algebras are explicit. You can write down `F`, check that `F` and `F'` generate the
unit ideal, and conclude that `A[t]/F` is étale. This gives a constructive way to build étale extensions from polynomial
data.

**Uniformity.** Every étale local algebra has this form. So local questions about étale algebras reduce to questions
about polynomials and their derivatives. This is how the source proves many permanence properties: write the étale
algebra in standard form and chase the polynomial.

### Geometric corollary

Corollary I.7.8 reads the local-form theorem geometrically:

> A morphism `f : X → Y` of finite type is **net** (unramified) at `x` iff there is an open neighborhood `U` of `x` and
> a factorization
>
> `U → X' → Y`
>
> where `U → X'` is a **closed immersion** and `X' → Y` is **étale**.

So unramified morphisms factor locally as "closed immersion into étale." Étale ones factor as "identity into étale" —
they are themselves étale.

#### Aside (elaborator analogy).

_Skip this paragraph if dependent-type-theory elaboration is not part of your background; nothing later depends on it._

Every type-checking step that is "rigid in the typing context up to first order" can be presented as `A[t]/F` for some
explicit polynomial `F` with `F'(t)` invertible. The local form of étale algebras is the algebraic shadow of "every
elaboration step is, locally, a solvable equation in one variable."

### How the proof works

The proof of theorem I.7.6 uses [**Zariski's Main Theorem**](appendix-black-boxes.md#zmt) as a black box. Zariski's Main
Theorem says:

> A quasi-finite morphism is, locally on the source, an open immersion into a finite morphism.

Net implies quasi-finite (file 04), so net morphisms factor as "open immersion into finite." After bookkeeping with
maximal ideals and generators, the finite morphism in question can be taken to be `A[t]/F` for an appropriate monic `F`.

We treat Zariski's Main Theorem as a black box throughout. It is a deep result of EGA IV.

## How the four stories interact

The four stories are not independent. The dependency runs roughly from concrete to abstract.

```text
Story 4 (local form, I.7.6)
   |
   v
Story 2 (lifting / equivalence, I.5.5 + I.8.3) ── uses local form for existence
   |
   v
Story 1 (open immersion criterion, I.5.1) ─── uses lifting as ingredient
   |
   v
[Sections, components, rigidity]

Story 3 (complete local rings, I.6.1) ── independent, uses I.5.5 in its proof
```

The local form is the most concrete; it gives the explicit shape of étale algebras. The lifting equivalence builds on
the local form: existence of a global lift comes from existence of local lifts plus uniqueness gluing them. The
open-immersion criterion combines lifting with separation. Story 3 is independent in spirit but uses I.5.5 in its proof.

## A note on Zariski's Main Theorem

Zariski's Main Theorem (ZMT) appears as a black box in two places.

**First use** (theorem I.5.1, second proof). To conclude that a flat radicial proper morphism is finite. The first proof
of I.5.1 uses Chevalley's theorem instead, also as a black box.

**Second use** (theorem I.7.6). To conclude that a quasi-finite morphism is locally an open immersion into a finite
morphism.

Both are proved in EGA IV. We do not prove ZMT here. The operational summary is:

> **Quasi-finite means "locally open inside finite."**

That is enough.

## Auxiliary tools we will use without proof

Every black box invoked in Exposé I — flatness sorites, Zariski's Main Theorem, Chevalley on proper morphisms, faithful
flatness of completion, Hensel's lemma, Serre's criterion for normality, Nagata's finiteness theorem,
universal-homeomorphism invariance, Krull's intersection theorem, Nakayama's lemma — is collected in
[appendix 13](appendix-black-boxes.md), with statement, role, and source citation. Inline mentions in this file and
later files link to the appendix by anchor; cite from there as needed.

## Closing

Étale morphisms are extraordinarily rigid. The four stories of this file say so from four directions.

- **Open-immersion criterion.** Étale + radicial = open immersion. Almost the whole gap between étale and "literal local
    isomorphism" is the residue-field flexibility.
- **Lifting across nilpotent thickenings.** The étale category over `Y` and over `Y₀` (any nilpotent thickening) are
    equivalent. The thickening is invisible.
- **Complete local rings.** Over a complete local ring, finite étale extensions are exactly the same data as finite
    separable extensions of the residue field.
- **Local form.** Every étale local algebra is, locally, the standard `(A[t]/F)_{(F')}` for a monic polynomial.

All four are proved in detail in file 11, where we rewrite the source theorems in the same gentle style. The next file
(06) prepares the last piece of Exposé I: how étale extensions interact with the classical notions of regularity,
reducedness, and normality, and the bridge between étale coverings and Galois theory of fields.

## The running example, end to end

Before continuing, walk the running example `f : Spec ℤ[√2] → Spec ℤ` through every lens of the preparation arc, at
every prime of `ℤ`, in one continuous narrative. The base ring is `A = ℤ`, the cover is `B = ℤ[t]/(t² − 2) = ℤ[√2]`, and
the defining polynomial is `F = t² − 2` with derivative `F'(t) = 2t`.

**At `p = 7`.** Reduce the polynomial: `t² − 2` factors mod `7` as `(t − 3)(t + 3)`, since `3² = 9 ≡ 2`. The fiber is

```text
B ⊗_ℤ 𝔽₇ = 𝔽₇[t]/(t² − 2) ≃ 𝔽₇ × 𝔽₇,
```

two distinct closed points. In the fiber, `2t` is a unit (both `2` and `t` are nonzero), so `Ω¹_{B/A}` vanishes there —
net. The discriminant of `B/ℤ` is `8 = 2³`, a unit mod `7`, so the discriminant criterion confirms étale. The geometric
point count is `n((7)) = 1 + 1 = 2`. **Verdict: étale.**

**At `p = 5`.** The polynomial `t² − 2` is irreducible mod `5` because `2` is not a square mod `5`. The fiber is the
single closed point

```text
B ⊗_ℤ 𝔽₅ = 𝔽₅[t]/(t² − 2) ≃ 𝔽_25,
```

a finite separable extension of `𝔽₅`. Both `2` and `t` are nonzero in `𝔽_25`, so `2t` is a unit and `Ω¹` vanishes — net.
The discriminant `8` is again a unit mod `5`. The single residue extension `𝔽_25 / 𝔽₅` has separable degree `2`, so
`n((5)) = 2`. **Verdict: étale.**

**At `p = 2`.** The polynomial `t² − 2` reduces to `t² ≡ t · t` mod `2`. The fiber is

```text
B ⊗_ℤ 𝔽₂ = 𝔽₂[t]/(t²),
```

a single point whose residue field is `𝔽₂[t]/(t² , t) = 𝔽₂`, _with a nilpotent direction_ `t` (note `t² = 0` but
`t ≠ 0`). Here `2t ≡ 0 · t = 0` mod `2`, so `Ω¹_{B/A}` is the full fiber — the entire `𝔽₂[t]/(t²)` is its support. The
discriminant `8` has `2`-adic valuation `3`, so the discriminant criterion fails. The geometric point count is
`n((2)) = 1` (one residue field, with separable degree 1). **Verdict: ramified.**

Five different tests at every prime give the same verdict. The summary table at the end of file 04 records the same data
in a single grid. The closed locus of ramification is the prime `(2)`, and the open complement `Spec ℤ[1/2]` is the
étale locus of `f`.

This is what the four rigidity stories of this file say at the level of a single concrete morphism: the same data,
viewed through the fiber, `Ω¹`, the discriminant, and the geometric point count, always tells the same story.
