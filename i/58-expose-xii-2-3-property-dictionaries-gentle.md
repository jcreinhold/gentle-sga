# Rewritten Exposé XII, sections XII.2–XII.3 — the property dictionaries

<!-- source: XII.2 XII.3 -->

## What this file is about

A complex algebraic variety has two faces: an algebraic one made of polynomial equations, and an analytic one made of
neighbourhoods and power series. The previous file built the translation between them. How well does the translation
preserve the properties one cares about? If a variety is smooth on the algebraic side, is its analytic counterpart
smooth? If a map between two varieties is well-behaved in one sense, is it well-behaved in the other?

The translation respects every reasonable property. This file compiles two dictionaries, one for spaces and one for
maps. The dictionary for spaces covers eight basic properties and runs both ways for each. The dictionary for maps
covers eleven, with six more added under a mild size hypothesis. Two small warnings close the file.

File 57 built the analytification functor `Φ : X ↦ X^an` and its comparison morphism `φ : X^an → X`. The defining
content of XII.1.1 was *local*: the completion isomorphism `𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}` at every point, together with
the bijection `|X^an| ≃ X(ℂ)` between underlying sets. We saw two immediate consequences in file 57: the analytification
functor commutes with fibre products (XII.1.2), and the inverse-image functor on coherent sheaves is exact, faithful,
and conservative (XII.1.3.1).

This file (§§XII.2 and XII.3) builds the **property dictionaries**. There are two dictionaries to build, one for schemes
and one for morphisms.

The **scheme dictionary** (XII.2) is the assertion that eight reasonable local and global properties of `X` correspond
to the same properties of `X^an`. The list is: nonempty, discrete, Cohen–Macaulay, `S_n`, regular, `R_n`, normal,
reduced, of dimension `n`. We also pin down a closure-compatibility statement (XII.2.2) — `φ` commutes with closure for
locally constructible subsets — and its corollary on open/closed/dense subsets (XII.2.3). The most substantive piece of
the scheme dictionary is the bijection of connected components (XII.2.6), which uses a finer analytic-geometric input
(the connectedness lemma XII.2.5).

The **morphism dictionary** (XII.3) is more elaborate. Without finite-type hypotheses, XII.3.1 lists eleven properties
that transfer between `f` and `f^an`: flat, unramified, étale, smooth, normal, reduced, injective, separated,
isomorphism, monomorphism, open immersion. With a finite-type hypothesis on `f`, XII.3.2 adds six more: surjective,
dominant, closed immersion, immersion, proper, finite. The properness step uses Chow's lemma. XII.3.3 records two
warnings: local isomorphism for `f^an` does not imply local isomorphism for `f`, and the finite-type hypothesis cannot
be dropped from XII.3.2 (the `⊔_{ℤ} Spec ℂ → 𝔸^1_ℂ` example).

The slogan that emerges by the end of this file: **the scheme `X` and its analytification `X^an` carry the same
local-ring and global-property information; the morphisms `f` and `f^an` agree on every reasonable finite-presentation
property.** Everything reduces, via the Jacobson and excellence properties of `ℂ`-schemes locally of finite type, to a
comparison at closed points, where the completion isomorphism XII.1.1 closes the question.

______________________________________________________________________

## §XII.2.0 — Bridge and proof strategy

<!-- source: XII.2 -->

A scheme and its analytification carry the same local-ring and global-property information; a morphism and its
analytification agree on every reasonable finite-presentation property. The rest of this file builds those two
dictionaries entry by entry, and every entry reduces to the same comparison at closed points.

Every proof uses the same two structural inputs. They are worth stating up front because they appear repeatedly.

#### Input 1 — Jacobson and very-dense closed points.

A scheme `X` locally of finite type over `ℂ` is **Jacobson**: every locally closed subset of `X` meets `X(ℂ)` densely.
This is `ega-iv-jacobson-nullstellensatz` (EGA IV §10.4.8). The practical consequences are three:

- A locally constructible subset `T ⊂ X` is determined by `T ∩ X(ℂ)`. In particular, two locally constructible subsets
    agreeing on `ℂ`-points are equal.
- A coherent sheaf `F` on `X` is zero iff `F_y = 0` for every closed point `y ∈ X` (very dense).
- A property holding at every closed point of `X` and *known to define an open subset of `X`* automatically holds
    everywhere.

The third bullet is the bridge between "agrees on `ℂ`-points" (the analytic-comparison content) and "holds everywhere"
(the algebraic content).

#### Input 2 — excellence and openness of regularity-type loci.

A `ℂ`-scheme `X` locally of finite type is **excellent** (EGA IV §7.8.6 (iii)). For every "local-ring-type" property `P`
in the list

```text
Cohen–Macaulay,    S_n,    regular,    R_n,    normal,    reduced,
```

the locus `{x ∈ X : 𝒪_{X, x} has property P}` is *open* in `X` (EGA IV §6.12). Combined with Input 1, this means each
such `P` is detected by its restriction to the closed points: if `P` holds at every closed point, `P` holds on `X`.

The completion isomorphism XII.1.1 (2) extends each `P` from the algebraic local ring `𝒪_{X, y}` (`y` closed) to the
analytic local ring `𝒪_{X^an, x}` (`x = φ^{-1}(y)`) and back. Because the completion `𝒪̂_{X, y}` agrees with
`𝒪̂_{X^an, x}`, and because for an excellent local ring each `P` is preserved by passage to completion (and reflected,
by faithful flatness of completion), the comparison is bidirectional.

We will quote both inputs by name as we work through the propositions.

______________________________________________________________________

## §XII.2.1 — Property dictionary for schemes

<!-- source: XII.2.1 -->

### Proposition XII.2.1 — eight properties agree on `X` and `X^an`

<!-- source: XII.2.1 -->

**Proposition XII.2.1.** Let `X` be a `ℂ`-scheme locally of finite type, and let `X^an` be its analytification. Let
`n ≥ 0` be an integer, and let `P` be one of the following properties:

```text
(i)    nonempty
(i')   discrete
(ii)   Cohen-Macaulay
(iii)  (S_n)
(iv)   regular
(v)    (R_n)
(vi)   normal
(vii)  reduced
(viii) of dimension n.
```

Then `X` has property `P` if and only if `X^an` has property `P`.

*This result says:* every standard local-ring property and the basic dimensional/topological properties transfer between
the algebraic and analytic worlds — `X` is regular iff `X^an` is regular, `X` has dimension `n` iff `X^an` does, and so
on.

**Proof.** Let `φ : X^an → X` be the canonical morphism.

**(i) Nonempty.** By XII.1.1, the underlying set of `X^an` is `X(ℂ) ⊂ |X|`. So `X^an = ∅` iff `X(ℂ) = ∅`. Now `X` is
Jacobson; closed points are very dense; so `X = ∅` iff `X` has no closed points iff `X` has no `ℂ`-points iff
`X(ℂ) = ∅`. The last equivalence uses that residue fields of closed points of a `ℂ`-scheme locally of finite type are
*finite* extensions of `ℂ`, hence equal to `ℂ`. So `X` is nonempty iff `X^an` is.

**(i′) Discrete.** A scheme `X` (resp. an analytic space `X^an`) is discrete iff `dim X = 0` (resp. `dim X^an = 0`);
this is `[XII.4, no. 19, §4, cor. 6]` for analytic spaces and standard for schemes. So (i′) follows from (viii).

**(ii)–(vii).** Each of these is a local property in the list of Input 2 above. Combining Inputs 1 and 2, for `X` to
have property `P` it is necessary and sufficient that `P` hold at every closed point of `X`. Similarly, for `X^an` to
have property `P` it is necessary and sufficient that `P` hold at every point of `X^an`.

The completion isomorphism XII.1.1 (2) says `𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}` for every `x ∈ X^an`. Since each of the six
properties is preserved and reflected by passage to the completion *for excellent local rings*, the property holds at
`𝒪_{X, φ(x)}` iff at `𝒪̂_{X, φ(x)}` iff at `𝒪̂_{X^an, x}` iff at `𝒪_{X^an, x}`. The first and third "iffs" are
excellence + completion-faithful-flatness; the middle iff is XII.1.1 (2).

Hence `P` holds at every closed point of `X` iff `P` holds at every point of `X^an`. By the reduction above, `X` has `P`
iff `X^an` has `P`.

**(viii) Dimension.** Combine the comparisons

```text
dim X = sup_y dim 𝒪_{X, y}     and     dim X^an = sup_x dim 𝒪_{X^an, x},
```

where in both cases the sup is taken over closed points (algebraic side) / all points (analytic side). At matched points
`y = φ(x)`, the dimension of `𝒪_{X, y}` agrees with the dimension of `𝒪̂_{X, y}` (excellence again), which agrees with
`dim 𝒪̂_{X^an, x} = dim 𝒪_{X^an, x}`. So the suprema match, and `dim X = n` iff `dim X^an = n`.

This proves the proposition. ∎

> **Slogan.** *Local-ring properties and dimension transfer between `X` and `X^an` at every point and globally.* The
> bridge is Jacobson (closed points are enough) and excellence (completions preserve the property).

#### Aside (the "what excellence buys you" sidebar).

The seven-line proof of (ii)–(vii) is the most concentrated payoff of the excellence machinery in the gentle SGA. For a
non-excellent ring, the implication "the local-ring property `P` holds at every closed point ⟹ `P` holds on the scheme"
can fail in cardinally bad ways — examples in Matsumura, _Commutative Ring Theory_ §32 — and the machinery of passing
from "true on completions" back to "true on local rings" needs more care. For `ℂ`-schemes locally of finite type, all of
this is automatic. The same is true of analytic spaces, whose local rings are *henselian* and complete with respect to
the maximal ideal in a way that mirrors excellence.

This is why the file 58 dictionary is short: the work is being done by EGA IV.

______________________________________________________________________

## §XII.2.2 — Compatibility with closure for locally constructible sets

<!-- source: XII.2.2 -->

### Proposition XII.2.2 — `φ` commutes with closure on locally constructible subsets

<!-- source: XII.2.2 -->

**Proposition XII.2.2.** Let `X` be a `ℂ`-scheme locally of finite type, let `φ : X^an → X` be the canonical morphism,
and let `T ⊂ X` be a locally constructible subset. Then

```text
φ^{-1}(closure(T)) = closure(φ^{-1}(T)),
```

where the closures are taken in `X` and `X^an` respectively.

*This result says:* the analytic comparison map respects topological closure for *locally constructible* subsets. Note
that this is generally false for arbitrary subsets, but locally constructible subsets are exactly the content the
Jacobson property pins down.

**Proof.** We reduce to the case where `T` is a dense open subset of `X`. (Indeed, every locally constructible subset is
a finite Boolean combination of locally closed subsets, and the closure operation is determined by its action on each
locally closed piece. The case "`T = U \ Z` for `U` open and `Z` a closed subset of `U`" reduces to the dense-open case
after working inside `U`.)

So suppose `T ⊂ X` is dense open. Let `H ⊂ X` be the reduced closed subscheme with underlying space `X − T`. The
associated analytic space `H^an` is a closed analytic subspace of `X^an` with underlying space `X^an − φ^{-1}(T)` (by
XII.1.1 block (a) and the bijection of `ℂ`-points on `H`).

We must show that every point `x ∈ H^an` belongs to the closure of `φ^{-1}(T)`. Equivalently: every open neighbourhood
of `x` in `X^an` meets `φ^{-1}(T)`. Suppose for contradiction that some open `V ∋ x` is disjoint from `φ^{-1}(T)`, that
is, `V ⊂ H^an` (as sets).

At the point `x`, the germ of analytic space `(X^an, x)` contains the subgerm `(H^an, x)` as a closed analytic subspace.
Because `T` is *dense* open in `X`, the closed subscheme `H` is *proper* (i.e. `H ≠ X`); hence the ideal sheaf
`I_H ⊂ 𝒪_X` is non-nilpotent at `x` (the local ring `𝒪_{X, φ(x)}` has nontrivial quotient `𝒪_{H, φ(x)}` ≠ 0, because
`𝒪_{X, φ(x)}` is reduced enough that nilpotents alone cannot generate `I_H`). After passage to the analytic side, the
analytic ideal `I_H · 𝒪_{X^an, x} = I_{H^an, x}` is non-nilpotent in `𝒪_{X^an, x}`.

By the **Nullstellensatz for complex analytic spaces** (Gunning–Rossi, equivalently `[XII.4, no. 19, §4, cor. 3]` in the
source), a non-nilpotent ideal in an analytic local ring at `x` has zero locus *strictly smaller* than the ambient germ
— i.e. every neighbourhood of `x` contains points where some element of `I_H · 𝒪_{X^an, x}` is nonzero, i.e. points of
`X^an − H^an = φ^{-1}(T)`. This contradicts `V ⊂ H^an`.

Hence every neighbourhood of `x` meets `φ^{-1}(T)`, so `x ∈ closure(φ^{-1}(T))`, as desired.

The reverse inclusion `closure(φ^{-1}(T)) ⊂ φ^{-1}(closure(T))` is automatic: `φ` is continuous, so `φ^{-1}(closure(T))`
is closed and contains `φ^{-1}(T)`, hence contains the closure. ∎

> **Slogan.** *Topology of locally constructible subsets transfers in both directions under `φ`.* The Jacobson property
> of `X` and the analytic Nullstellensatz of `X^an` make this a clean equality, not just an inclusion.

### Corollary XII.2.3 — open / closed / dense subsets are detected by `φ`

<!-- source: XII.2.3 -->

**Corollary XII.2.3.** Let `T ⊂ X` be a locally constructible subset of a `ℂ`-scheme `X` locally of finite type. Then:

```text
(a)  T  is open    iff  φ^{-1}(T)  is open  in  X^an;
(b)  T  is closed  iff  φ^{-1}(T)  is closed in  X^an;
(c)  T  is dense   iff  φ^{-1}(T)  is dense  in  X^an.
```

**Proof.** Clauses (a), (b), (c) are dual to XII.2.2 by elementary set-theoretic manipulation. For (b): `T` is closed
iff `T = closure(T)` iff `φ^{-1}(T) = φ^{-1}(closure(T)) = closure(φ^{-1}(T))` (XII.2.2) iff `φ^{-1}(T)` is closed. (a)
is dual. (c) is `closure(T) = X` iff `closure(φ^{-1}(T)) = φ^{-1}(closure(T)) = φ^{-1}(X) = X^an`, using that `φ` is
surjective on closed points (which together with Jacobson gives surjection of locally constructible subsets).

For the converse direction in (a)–(b), use the Jacobson property: two locally constructible subsets agreeing on `X(ℂ)`
are equal (Input 1). If `φ^{-1}(T)` is open / closed / dense, the locally constructible subsets `T` and the open /
closed / dense locally constructible set in `X` with the same `ℂ`-points are equal. ∎

> **Slogan.** *On locally constructible subsets, "open / closed / dense" is decided on the analytic side.*

______________________________________________________________________

## §XII.2.3 — Connectedness, irreducibility, and `π_0`

<!-- source: XII.2.4 -->

The next step is the comparison of *global* topological invariants: connected components, irreducibility, and the set
`π_0`. The proof of XII.2.4 uses Serre's original projective GAGA on a compactification and a finer lemma (XII.2.5) on
rare-set complements in normal analytic spaces.

### Proposition XII.2.4 — connectedness and irreducibility transfer

<!-- source: XII.2.4 -->

**Proposition XII.2.4.** Let `X` be a `ℂ`-scheme locally of finite type. Then:

```text
(a)  X  is connected     iff  X^an  is connected,
(b)  X  is irreducible   iff  X^an  is irreducible.
```

*This result says:* the global topology of `X` (its number of connected components, its decomposition into irreducible
pieces) matches the global topology of `X^an`.

**Proof.**

**Forward directions.** Suppose `X^an` is connected (resp. irreducible). The image `φ(|X^an|) = X(ℂ) ⊂ |X|` is then
connected (resp. irreducible) as a subspace of `|X|`. Two locally constructible subsets of `X` agreeing on `X(ℂ)` are
equal (Jacobson); the *closed subsets* of `X` are locally constructible; so connectedness / irreducibility of `X(ℂ)`
lifts to connectedness / irreducibility of `X`. (This uses `ega-iv-1-8-4-constructible` plus the Jacobson property; cf.
EGA IV §10.1.2.)

**Reverse directions.** Suppose `X` is connected (resp. irreducible); we show `X^an` is.

**Reduction to irreducible case.** First, suppose `X` connected. Given `x ∈ X`, the set of `y ∈ X` for which there
exists a chain of irreducible closed subschemes `X_1, …, X_n ⊂ X` with `x ∈ X_1`, `y ∈ X_n`, `X_i ∩ X_{i+1} ≠ ∅` for
`1 ≤ i < n` is both open and closed in `X` (chains can be extended at either end), hence equal to all of `X`. For such a
chain, also `X_i^an ∩ X_{i+1}^an ≠ ∅`. If we know the `X_i^an` are connected, then `X^an` is connected (as a union of
connected sets with pairwise non-empty pairwise intersections along a chain). So it suffices to prove the irreducible
case.

**Reduction to affine case.** Suppose `X` irreducible. Let `(U_i)_{i ∈ I}` be an affine open cover of `X`. Any two
`U_i, U_j` have non-empty intersection (because `X` is irreducible). After analytification,
`U_i^an ∩ U_j^an = (U_i ∩ U_j)^an` is non-empty (XII.1.2 and (i) of XII.2.1). If we know each `U_i^an` is irreducible,
then `X^an` is irreducible (a union of irreducible spaces pairwise meeting is irreducible).

**Reduction to normal affine case.** Suppose `X` affine irreducible. Let `X̃ → X` be the normalisation morphism;
`X̃ → X` is finite and surjective, so `X̃^an → X^an` is finite and surjective (anticipating XII.3.2 (i), (vi); also
clear at the analytic level by Oka coherence + Nullstellensatz). If `X̃^an` is irreducible, then so is `X^an` (image of
an irreducible under a continuous surjection).

**Affine normal irreducible case.** Suppose `X` affine normal irreducible. Then the local rings of `X` are integral
domains, and by XII.2.1 (vi) the local rings of `X^an` are integral domains too. For a normal analytic space with
integral local rings, *connectedness implies irreducibility* (any closed analytic subset `𝓕 ⊂ X^an` has its
zero-codimension locus closed and open; in a connected normal space this is empty or everything). It therefore suffices
to show `X^an` is *connected*.

**The compactification step.** Choose a *normal projective* compactification `i : X → P` of `X`, where `P` is a normal
projective `ℂ`-scheme and `i` is a dominant open immersion. (Normal projective compactifications exist — take the
normalisation of the projective closure of an affine embedding; one has to check the closure is projective, which
follows from finite-typeness, and normality, which is the normalisation step.)

By Serre's original projective GAGA (`gaga-serre-original`), `P^an` is *connected* (Serre 1956 computes that for a
projective `ℂ`-variety the analytification has the same `π_0` as the variety; specifically for `P` connected, `P^an` is
connected). Since `X = P − (P − X)` is the complement of a proper closed subscheme of `P`, and `P` is *normal*, the
analytic space `X^an = P^an − (P − X)^an` is the complement in the connected normal analytic space `P^an` of a rare
closed analytic subset.

The next lemma (XII.2.5) then forces `X^an` connected. ∎

### Lemma XII.2.5 — rare closed analytic subsets do not disconnect

<!-- source: XII.2.5 -->

**Lemma XII.2.5.** Let `𝓟` be a connected normal complex analytic space, and let `𝓨 ⊂ 𝓟` be a rare (nowhere dense)
closed analytic subset. Then `𝓧 := 𝓟 − 𝓨` is connected.

*This result says:* removing a thin closed analytic subset from a connected normal analytic space leaves connectedness
intact. The proof factors through Serre's prolongation theorem (codim ≥ 2 case) and the implicit function theorem
(general case).

**Proof.**

**Case 1: `codim_𝓟(𝓨) ≥ 2`.** By Serre's prolongation theorem (`serre-prolongement-faisceaux`,
`[XII.11, no. 3, prop. 4]` in the source), the canonical map `𝒪_𝓟 → i_* 𝒪_𝓧` (where `i : 𝓧 ↪ 𝓟` is the inclusion) is an
isomorphism. Consequently `Γ(𝓟, 𝒪_𝓟) = Γ(𝓧, 𝒪_𝓧)`. If `𝓧` were disconnected as `𝓧 = 𝓧_1 ⊔ 𝓧_2`, the indicator function
of `𝓧_1` would be a locally constant section of `𝒪_𝓧` with two distinct values; pulling back via the isomorphism, this
gives a locally constant section of `𝒪_𝓟` with two values, contradicting connectedness of `𝓟`.

**Case 2: general case.** Let `𝓨' ⊂ 𝓟` be the singular locus of `𝓨` (the closed analytic subset of `𝓨` where `𝓨` is not
regular). Then `dim 𝓨' < dim 𝓨` (Grauert–Remmert), so by induction on `dim 𝓨` we may assume `𝓨'` is empty — that is, `𝓨`
is a regular submanifold of `𝓟`. By the implicit function theorem, every point `y ∈ 𝓨` has a neighbourhood `𝓤 ⊂ 𝓟`
isomorphic to a ball in `ℂⁿ`, such that `𝓤 ∩ 𝓨` is defined by the vanishing of a fixed number of coordinate functions.
Then `𝓤 − 𝓤 ∩ 𝓨` is the complement of a coordinate linear subspace in a ball, which is path-connected (in fact
homotopy-equivalent to a torus).

We have shown: every point `y ∈ 𝓨` has a *connected* neighbourhood in `𝓧 = 𝓟 − 𝓨`. Since `𝓟` is connected and `𝓧` is the
complement of a closed subset, this local connectedness propagates to global connectedness of `𝓧`. (Pick two points
`x_1, x_2 ∈ 𝓧`; connect them by a path in `𝓟`; the path can be perturbed locally inside `𝓤_y` near each intersection
point `y ∈ 𝓨` to avoid `𝓨`.)

This proves the lemma. ∎

### Corollary XII.2.6 — `π_0(X^an) → π_0(X)` is a bijection

<!-- source: XII.2.6 -->

**Corollary XII.2.6.** Let `X` be a `ℂ`-scheme locally of finite type. The canonical map

```text
π_0(X^an) → π_0(X)
```

induced by `φ : X^an → X` is a bijection.

*This result says:* the analytic and algebraic comparisons of connected components agree exactly.

**Proof.** Surjectivity: `φ : X^an → X` surjects on `X(ℂ)`, which meets every connected component of `X` (Jacobson).
Injectivity: by XII.2.4, two connected components of `X^an` cannot map to the same connected component of `X` (they
would merge into one analytic component). ∎

> **Slogan.** *Connected components transfer bijectively between `X` and `X^an`.* This is the input the Riemann
> existence theorem of file 60 attaches to: a connected finite étale covering of `X^an` is a connected component of
> `X' ×_X X''` for some `X', X'' / X`; XII.2.6 + XII.3.1 (ix) close the morphism-side comparison.

______________________________________________________________________

## §XII.3 — Property dictionary for morphisms

<!-- source: XII.3 -->

We turn now to the morphism dictionary. The structure is parallel to XII.2.1, but more elaborate because there are more
properties of morphisms than of schemes. We split the morphism dictionary into two propositions: XII.3.1 collects
properties that transfer without a finite-type hypothesis on `f`, and XII.3.2 collects properties that require one. The
XII.3.3 remarks at the end warn about two failures: local isomorphism cannot be reflected from the analytic side, and
the finite-type hypothesis cannot be dropped from XII.3.2.

### Proposition XII.3.1 — eleven properties without finite-type

<!-- source: XII.3.1 -->

**Proposition XII.3.1.** Let `f : X → Y` be a morphism of `ℂ`-schemes locally of finite type, and let
`f^an : X^an → Y^an` be its analytification. Let `P` be one of the following properties of a morphism:

```text
(i)    flat
(ii)   net  (= unramified)
(iii)  étale
(iv)   smooth
(v)    normal       (= geometric fibres are normal)
(vi)   reduced      (= geometric fibres are reduced)
(vii)  injective
(viii) separated
(ix)   an isomorphism
(x)    a monomorphism
(xi)   an open immersion.
```

Then `f` has property `P` if and only if `f^an` has property `P`.

*This result says:* of the eleven listed morphism properties, none requires a finite-type hypothesis to transfer between
scheme-theoretic morphisms and analytic morphisms.

**Proof.** Let `φ : X^an → X` and `ψ : Y^an → Y` be the canonical morphisms. Let `x ∈ X^an` and put
`y = f^an(x) ∈ Y^an`. The local maps `𝒪_{Y^an, y} → 𝒪_{X^an, x}` and `𝒪_{Y, ψ(y)} → 𝒪_{X, φ(x)}` deduced from `f^an` and
`f` give the *same* morphism after passage to completions (because of XII.1.1 (2) applied to each side).

**(i) Flat.** A morphism is flat iff every local map `𝒪_{Y, ψ(y)} → 𝒪_{X, φ(x)}` is flat (for `x` over `y`). Flatness of
an `A`-module is preserved and reflected by passage to the completion of `A` (when `A` is noetherian, EGA `0_I` §10.2 /
`[XII.2, ch. 3, §5, prop. 4]`). So `f` is flat at `φ(x)` iff `f^an` is flat at `x`. For the global statement, use that
the flat locus of a finite-presentation morphism is open in `X` (`ega-iv-flat-locus-open` = EGA IV §11.1.1) and the
Jacobson property (closed points decide membership in an open). The corresponding statement on the analytic side — flat
locus of `f^an` is open in `X^an` — is the analytic analogue (Gunning–Rossi). Conclusion: `f` is flat iff `f^an` is.

**(ii) Net (unramified).** Same argument as (i), with "flat" replaced by "unramified" and EGA IV §17.4.4 in place of
§11.1.1 (`ega-iv-unramified-locus-open`). The unramified property is preserved and reflected by completions of the local
rings.

**(iii) Étale.** Étale = flat + unramified. Combine (i) and (ii).

**(iv) Smooth.** Smooth = flat + geometrically regular fibres. The flatness comparison is (i). For the fibres, take a
fibre `f^{-1}(ψ(y))` and the corresponding analytic fibre `(f^an)^{-1}(y)` (these are matched by XII.1.2: fibre products
commute with analytification). By XII.2.1 (iv) applied to each fibre, "regular" agrees between the scheme-theoretic
fibre and the analytic fibre. The smooth-fibre locus is open on the base (`ega-iv-12-1-7-smooth-fibre-locus` = EGA IV
§12.1.7) and analytic openness mirrors this. Conclusion as for (i).

**(v) Normal fibres.** Same as (iv), using XII.2.1 (vi) and EGA IV §12.1.7 for the normality variant.

**(vi) Reduced fibres.** Same, using XII.2.1 (vii).

**(vii) Injective.** If `f` is injective, so is `f^an` (the underlying set map on `ℂ`-points is the restriction of `f`
to `X(ℂ) ↪ Y(ℂ)`). Conversely, suppose `f^an` is injective; we show `f` is.

We may suppose `f` of finite type (the global statement reduces to the finite-type case via affine opens). Since `f^an`
is injective, the fibres of `f^an` over each `y ∈ Y^an` are at most singletons. Hence the fibres of `f` over each closed
point `ψ(y) ∈ Y` are *radicial* (= geometrically have at most one point). The locus `{y ∈ Y : f^{-1}(y) is radicial}` is
locally constructible (`ega-iv-radicial-constructible` = EGA IV §9.6.1), and contains every closed point of `Y` (the
closed points are radicial), and `Y` is Jacobson; hence the locus is all of `Y`. So `f` is radicial, hence injective on
points.

**(viii) Separated.** Separatedness of `f` is the property that the diagonal `Δ_{X/Y} : X → X ×_Y X` is a closed
immersion. By XII.1.2, the diagonal of `f^an` is the analytification of the diagonal of `f`. By XII.2.3, the property of
being a closed subspace transfers between schemes and analytic spaces. So `Δ_{X/Y}` is closed iff `(Δ_{X/Y})^an` is.

But "closed immersion" requires more than "closed image": it requires the local map of structure sheaves to be
surjective. This surjectivity *is* preserved by analytification (closed-immersion definition is local on the target;
analytification preserves local-ringed structure). Hence `f` separated iff `f^an` separated.

**(xi) Open immersion.** A morphism is an open immersion iff it is *étale and injective* (`ega-iv-unramified-locus-open`
= EGA IV §17.9.1; also part of file 04). The same characterisation holds in the analytic category. Combine (iii) and
(vii).

**(ix) Isomorphism.** Iso = open immersion + surjective. The "+surjective" is XII.3.2 (i) in the next proposition; the
"open immersion" is (xi). Both transfer; their conjunction does.

**(x) Monomorphism.** `f` is a monomorphism iff its diagonal `Δ_{X/Y} : X → X ×_Y X` is an isomorphism. By (ix), this
transfers between `Δ_f` and `(Δ_f)^an = Δ_{f^an}`. So `f` mono iff `f^an` mono.

This proves all eleven clauses. ∎

> **Slogan.** *Flat, unramified, étale, smooth, normal-fibred, reduced-fibred, injective, separated, isomorphism, mono,
> open-immersion: each transfers between `f` and `f^an` without a finite-type assumption on `f`.*

### Proposition XII.3.2 — six properties with finite-type hypothesis

<!-- source: XII.3.2 -->

**Proposition XII.3.2.** Let `X, Y` be `ℂ`-schemes locally of finite type, let `f : X → Y` be a morphism *of finite
type*, and let `f^an : X^an → Y^an` be its analytification. Let `P` be one of the following:

```text
(i)   surjective
(ii)  dominant
(iii) a closed immersion
(iv)  an immersion
(v)   proper
(vi)  finite.
```

Then `f` has property `P` if and only if `f^an` has property `P`.

*This result says:* the six surjection-/closure-related properties require `f` of finite type to transfer correctly. The
example in XII.3.3 (b) below shows the hypothesis is necessary.

**Proof.** As before let `φ, ψ` be the canonical morphisms.

**(i) Surjective.** Suppose `f` surjective. For every `y ∈ Y^an`, `f^{-1}(ψ(y)) ⊂ X` is a non-empty (because `f`
surjective) closed subset of finite-type `X`; it has at least one closed point (Jacobson). Hence `f^an` surjects.

Conversely, suppose `f^an` surjective. Then `f(X) ⊂ Y` is locally constructible (`ega-iv-1-8-4-constructible` = EGA IV
§1.8.4) and contains all closed points of `Y` (every closed point lies in `ψ(X^an) = f(X(ℂ)) ⊂ f(X)`). Jacobson then
forces `f(X) = Y`.

**(ii) Dominant.** `f` dominant iff `closure(f(X)) = Y` iff (by XII.2.2) `closure(f^an(X^an)) = Y^an` iff `f^an`
dominant.

**(iii) Closed immersion.** If `f` is a closed immersion, so is `f^an` (XII.1.1 block (a2)). Conversely, suppose `f^an`
is a closed immersion. Then `f^an` is in particular a *proper monomorphism* (closed immersion = proper + mono). By
XII.3.2 (v) below and XII.3.1 (x), `f` is also a proper monomorphism. By `ega-iv-8-11-5-proper-mono` (EGA IV §8.11.5), a
proper monomorphism is a closed immersion.

**(iv) Immersion.** Immersion = open immersion of `X` into a closed subscheme of `Y`. If `f` is an immersion, so is
`f^an` by (iii) and XII.3.1 (xi). Conversely, suppose `f^an` is an immersion. Let `T = f(X)` and let `T̄` be the
scheme-theoretic closure of `T` in `Y`. Factor `f = j ∘ i` with `i : X → T̄` and `j : T̄ → Y` a closed immersion. Then
`f^an = j^an ∘ i^an` with `j^an` a closed immersion (by (iii) just proved).

By XII.2.2, `T̄^an = closure(f^an(X^an))`. Since `f^an` is an immersion, `f^an(X^an)` is locally closed in `Y^an`, i.e.
open in its closure `T̄^an`. So `i^an(X^an)` is open in `T̄^an`, hence `i(X)` is open in `T̄` (XII.2.3 (a)).

Factor `i` further as `i = i_2 ∘ i_1`, where `i_1 : X → i(X)` is the canonical morphism and `i_2 : i(X) → T̄` is the
open immersion. The morphism `i_1^an` is a *proper monomorphism* (proper because finite-type, and mono because `f^an` is
an immersion), hence so is `i_1` by XII.3.2 (v) and XII.3.1 (x). By `ega-iv-8-11-5-proper-mono`, `i_1` is a closed
immersion. Composing with the open immersion `i_2`, `i = i_2 ∘ i_1` is an immersion, hence so is `f = j ∘ i`.

**(v) Proper.** This is the key case. Properness is a global condition that does not localise to completions; we need a
different argument.

**(v) Forward direction (`f` proper ⟹ `f^an` proper).** Properness of `f^an` is local on `Y^an`, so we may assume `Y`
affine. By **Chow's lemma** (EGA II §5.6.1, also `chow-lemma` in the gentle appendix), there exist a projective
`Y`-scheme `X'` and a projective surjective morphism `g : X' → X`. Then `f ∘ g : X' → Y` is projective. After
analytification, `(f ∘ g)^an = f^an ∘ g^an` is projective (a projective morphism's analytification is projective — embed
in `ℙ^N_Y` and apply XII.1.2 to the closed embedding). A projective morphism of analytic spaces is proper
(`[XII.1, ch. 1, §10]`, the analytic analogue of "projective ⟹ proper"). And `g^an` is surjective by XII.3.2 (i).
Properness then descends from `f^an ∘ g^an` along `g^an`: if a composition is proper and the first map is surjective,
the second is proper.

**(v) Reverse direction (`f^an` proper ⟹ `f` proper).** Suppose `f^an` proper; we show `f` proper. By XII.3.1 (viii),
`f` is separated. It remains to show `f` is universally closed. In fact it is enough to show `f` is *closed*, because
base-changing `f` to any `Y'`-scheme of finite type still gives a finite-type morphism `X ×_Y Y' → Y'` whose
analytification is the base change of `f^an`, hence proper.

So let `T ⊂ X` be closed. The image `f(T) ⊂ Y` is locally constructible (`ega-iv-1-8-4-constructible`); we want `f(T)`
closed. The analytic image `f^an(φ^{-1}(T)) = ψ^{-1}(f(T))` is closed in `Y^an` because `f^an` is proper. By XII.2.2,
`ψ^{-1}(closure(f(T))) = closure(ψ^{-1}(f(T))) = ψ^{-1}(f(T))`. The Jacobson property then forces
`closure(f(T)) = f(T)`, that is, `f(T)` is closed. So `f` is closed, hence proper.

**(vi) Finite.** A morphism is finite iff it is proper with finite fibres (EGA III §4.4.2 plus `[XII.4, no. 19, §5]`).
The set of points `y ∈ Y` where the fibre `f^{-1}(y)` is finite is locally constructible (`ega-iv-9-7-9-finite-fibre` =
EGA IV §9.7.9), and by XII.1.2 the fibres of `f` are finite iff the fibres of `f^an` are. So (vi) follows from (v).

This proves all six clauses. ∎

> **Slogan.** *Six more morphism properties — surjective, dominant, closed-immersion, immersion, proper, finite —
> transfer between `f` and `f^an`, under the finite-type hypothesis on `f`. Properness routes through Chow's lemma;
> finiteness through finite-fibre constructibility.*

### Remark XII.3.3 — two warnings

<!-- source: XII.3.3 -->

**Remark XII.3.3.** Two warnings about the boundaries of the dictionary.

**(a) Local isomorphism for `f^an` does not imply local isomorphism for `f`.** For example, suppose `f : X → Y` is étale
(but not an open immersion: connected total space, finite-fibred, non-trivial cover). Then `f^an` is a local
biholomorphism (= local isomorphism in the analytic sense, `[XII.4, no. 13, §1]`). But `f` itself, viewed as a morphism
of schemes, is generally *not* a Zariski-local isomorphism — a Zariski-local isomorphism is the same as an open
immersion, which forces injectivity (XII.3.1 (vii)).

The point is that "local isomorphism" in the analytic category means "isomorphism on small Euclidean neighbourhoods",
which is much weaker than "Zariski-local open immersion". The analytic local-iso condition is exactly étaleness, by the
implicit function theorem in the analytic context.

**(b) The finite-type hypothesis cannot be dropped from XII.3.2.** A simple counterexample for clause (iii): let
`X = ⊔_{n ∈ ℤ} Spec ℂ` (a countable disjoint union of points), `Y = 𝔸^1_ℂ`, and `f : X → Y` the morphism sending the
points of `X` to a discrete sequence `{0, 1, -1, 2, -2, …}` of points in `𝔸^1_ℂ`. Then `f` is *not* of finite type (it
is countably-presented but not finitely-presented over `Y`). The analytification `f^an` sends `X^an = ⊔_ℤ {pt}` to the
discrete subset `ℤ ⊂ ℂ` of the analytic affine line `𝔸^1_ℂ^an = ℂ`. The discrete subset is a *closed* analytic subset of
`𝔸^1_ℂ^an` (it is closed and locally finite), so `f^an` is a closed immersion of an analytic-finite space into the
analytic affine line. But `f` is not a closed immersion in the scheme sense: the image `f(X) = ℤ ⊂ 𝔸^1_ℂ` is not closed
(its closure is all of `𝔸^1_ℂ` because the closed subsets of `𝔸^1_ℂ` are finite sets of points, the empty set, and the
whole space).

The failure of XII.3.2 (iii) here illustrates a more general phenomenon: without finite-type, the "locally
constructible" framework of XII.2.2–XII.2.3 has no traction, so global properties like closedness do not transfer.

> **Slogan for XII.3.3.** *The analytic-side and scheme-side categories of morphisms agree on the finite-presentation
> properties, but the finite-type hypothesis is load-bearing.*

______________________________________________________________________

## §XII.3.4 — Closing of file 58

<!-- source: XII.3 -->

By the end of this file we have the **scheme-and-morphism dictionary** between `Sch_{lft}/ℂ` and `AnSp/ℂ`:

- (XII.2.1) Eight scheme-level properties (nonempty, discrete, CM, `S_n`, regular, `R_n`, normal, reduced, dim `n`)
    transfer between `X` and `X^an`.
- (XII.2.2–XII.2.3) Locally constructible subsets and their closure / open / dense behaviour transfer between `X` and
    `X^an`.
- (XII.2.4) Connectedness and irreducibility transfer between `X` and `X^an`.
- (XII.2.5) Rare closed analytic subsets of normal connected analytic spaces do not disconnect.
- (XII.2.6) The map `π_0(X^an) → π_0(X)` is a bijection.
- (XII.3.1) Eleven morphism-level properties (flat, net, étale, smooth, normal-fibred, reduced-fibred, injective,
    separated, isomorphism, mono, open-immersion) transfer between `f` and `f^an` without a finite-type hypothesis.
- (XII.3.2) Six more morphism-level properties (surjective, dominant, closed-immersion, immersion, proper, finite)
    transfer between `f` and `f^an` under a finite-type hypothesis.
- (XII.3.3) Two warnings: local iso for `f^an` does not imply local iso for `f`; the finite-type hypothesis cannot be
    dropped from XII.3.2.

The cohomological side of the dictionary — the equivalence of coherent-sheaf categories on proper schemes, the
comparison `H^p(X, F) ≃ H^p(X^an, F^an)`, and the higher-direct-image comparison `(R^p f_* F)^an ≃ R^p f_*^an(F^an)` —
is the content of **file 59 (§XII.4)**, the relative cohomological GAGA.

> **Final slogan for file 58.** *Locally and globally, `X` and `X^an` carry the same property data; under finite-type
> hypotheses, so do `f` and `f^an`.* The completion isomorphism XII.1.1, the Jacobson and excellence properties of
> `ℂ`-schemes locally of finite type, the analytic Nullstellensatz, and Serre's prolongation theorem together close
> every clause of XII.2 and XII.3.
