# Exposé IX §IX.6 (gentle): the fundamental exact sequence and Stein factorisation; closing of the gentle SGA

## What this file is about

A family of geometric objects has three natural fundamental groups attached to it: one for a typical fibre, one for the
total space, and one for the base of parameters. These three groups are not independent. In topology they fit into a
short three-term sequence — every loop in the base comes from a loop in the total space, and the loops in the total
space that vanish in the base are exactly the loops carried by the fibre. The same sequence is what one would hope to
prove algebraically.

This file proves the first algebraic version. Under a properness condition on the family — meaning, roughly, that the
fibres do not leak off to infinity — the three fundamental groups fit into the expected three-term sequence. It is the
first homotopy exact sequence in the book and the technical climax of the gentle pass through SGA 1.

## Opening: from descent to a homotopy exact sequence

File 46 closed §IX.5 with the **Seifert–van-Kampen formula** for `π₁(S, a)`: when `g : S′ → S` is an effective descent
morphism for finite étale coverings, `π₁(S, a)` is a galoisian-type group on generators `π_{s′}` (`s′ ∈ E′ = π₀(S′)`)
and `g_{s″}` (`s″ ∈ E″`) with cocycle relations on `S‴`. In the special case where `g` has geometrically connected
fibres (corollary IX.5.6), the formula collapses to a clean cokernel:

```text
π₁(S)  ≃  cokernel of  (p_1^*, p_2^*) : π₁(S″) ⇉ π₁(S′)  in Galois-type groups.
```

This file takes the *geometric* specialisation: `g = f : X → S` is **proper surjective with geometrically connected
fibres**. By IX.4.12 (file 45), `f` is an effective descent morphism for finite étale coverings. By IX.5.6, the
fundamental group of `X` is a cokernel of `π₁(X″ = X ×_S X) ⇉ π₁(X)`. But we can do better: combining this with **Stein
factorisation** (the canonical decomposition of a proper morphism as a connected-fibres step followed by a finite step;
a new EGA III §4.3 black box, see [`ega-iii-stein-factorisation`](appendix-black-boxes.md#ega-iii-stein-factorisation))
and IX.1.10 (file 44), we obtain the **fundamental exact sequence**

```text
1  →  π₁(X̄_0, ā)  →  π₁(X, a)  →  π₁(S, b)  →  1,
```

where `X̄_0 = X ⊗_{κ(s)} \bar{κ(s)}` is the **geometric special fibre** at some `s ∈ S`. This is the algebraic analogue
of the **homotopy exact sequence of a fibre bundle** in topology, and it is the conceptual climax of the gentle SGA.

The same machinery gives **Stein factorisation criteria** (IX.6.5–6.6) and the **global existence theorem** (IX.6.7) for
étale morphisms over `X / S`. With this file, every black box of the form
[`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) that was cited from files 30, 31, 33 now points back to
developed mathematics in files 40–47. Exposé X continues the story in files 48–51 (the homotopy exact sequence for a
proper separable morphism, the specialisation morphism on `π_1`, and the continuity theorem).

## §IX.6 — A fundamental exact sequence; descent by morphisms with relatively connected fibres

<!-- source: IX.6 -->

### IX.6.1 — The fundamental exact sequence

<!-- source: IX.6.1 -->

**Theorem IX.6.1.** Let `S = Spec(A)` with `A` an **artinian** ring with residue field `k`, let `\bar{k}` be an
algebraic closure of `k`, let `X` be an `S`-prescheme with `X_0 = X ⊗_A k` quasi-compact and **geometrically connected**
over `k`. Let `ā` be a geometric point of `\bar{X} = X ⊗_A \bar{k}` lying over `\bar{k}`, let `a` be its image in `X`,
and let `b` be its image in `S`. Then the canonical sequence of homomorphisms

```text
1  →  π₁(\bar{X}_0, ā)  →  π₁(X, a)  →  π₁(S, b)  →  1
```

is **exact**, and `π₁(S, b) ≃ π₁(k, \bar{k}) =  \mathrm{Gal}(\bar{k} / k)`.

*This result says:* **for `X / S` "geometrically connected" over the residue field `k`, the étale fundamental groups fit
into the homotopy exact sequence of a fibration.** The base `π₁(S, b)` is the absolute Galois group of the residue field
`k`.

*Proof.* The fundamental group is invariant under killing nilpotents (file 33 V.8 + IX.4.11 = topological invariance,
file 45): `S_{red} → S` is finite radicial surjective, and IX.4.10 / IX.4.11 force `π₁(S, b) = π₁(S_{red}, b)`. Applied
to `S = Spec(A)`, the reduced subscheme is `Spec(k)`. So we may assume `A = k` is a *field*; the isomorphism
`π₁(S, b) ≃ π₁(k, \bar{k}) = \mathrm{Gal}(\bar{k} / k)` is then file 33 V.9 (the spectrum-of-a-field case).

**Reduction to `k` perfect.** Let `k′ \subset \bar{k}` be the *separable closure* of `k` in `\bar{k}`, and set
`X′ = X ⊗_k k′` and `a′` the image of `ā` in `X′`. There is a canonical sequence

```text
1  →  π₁(\bar{X}_0, ā)  →  π₁(X′, a′)  →  π₁(S′, b′)  →  1,    where S′ = Spec(k′).
```

and a canonical homomorphism from this sequence to the sequence we want to prove exact for `X / k`, coming from the
evident diagram. **This homomorphism of sequences is an isomorphism by IX.4.11**: the morphism `Spec(\bar{k} / k′)` is
*radicial* (it is a purely inseparable algebraic extension), and faithfully flat and quasi-compact, so by IX.4.11 it
induces an equivalence on finite étale categories. Hence it suffices to prove the second sequence exact, i.e. we may
assume `k` is **perfect** and equal to its separable closure in `\bar{k}`. Then `S′ = Spec(k)`, and `\bar{k} / k` is
*purely transcendental* (since `k` is perfect and contains `k′`). The exact sequence we want becomes

```text
1  →  π₁(\bar{X}_0, ā)  →  π₁(X, a)  →  π₁(k, \bar{k}) = \mathrm{Gal}(\bar{k} / k)  →  1.
```

**Computation via finite Galois sub-extensions.** Let `\{k_i\}` be the directed system of finite Galois sub-extensions
of `k` in `\bar{k}`. Set `X_i = X ⊗_k k_i` and `a_i` the image of `ā` in `X_i`. The reader should verify that the
natural homomorphism

```text
π₁(\bar{X}_0, ā)  ≃  \mathrm{lim}_i \, π₁(X_i, a_i)
```

is an *isomorphism*. (Statement: an étale covering of `\bar{X}_0` comes from an étale covering of some `X_i`, and the
latter is essentially unique after passing to an `X_j` with `j ≥ i`. Proof: étale coverings of `\bar{X}_0` are finite
étale algebras over `\bar{k} ⊗_k 𝒪_{X_0}`; finiteness of the resulting algebra forces it to descend to a sub-algebra
over `k_i ⊗_k 𝒪_{X_0}` for some `i`, by a standard limit argument.)

On the other hand, let `π_i = \mathrm{Gal}(k_i / k)` (the Galois group of `k_i` over `k`). By IX.3.4 (file 45) applied
to the morphism `\mathrm{Spec}(k_i) → \mathrm{Spec}(k)` (finite étale over a field), the functor
`X ↦ X ×_S \mathrm{Spec}(k_i)` from étale coverings of `S` to étale coverings of `X` is fully faithful, hence the
homomorphism on fundamental groups is an *epi*. Combined with the basic file 33 V.9.4 exact sequence

```text
1  →  π₁(X_i, a_i)  →  π₁(X, a)  →  π_i  →  1
```

— this is the file 33 V.9.4 result for a finite Galois sub-extension — passing to the inverse limit over `i` gives the
desired exact sequence, since the category of Galois-type groups has exact inverse limits along directed systems. ∎

> **Slogan.** *For `X / k` geometrically connected, the étale fundamental group sits in a homotopy exact sequence over
> the absolute Galois group of `k`.*

### IX.6.2 — Geometrically trivial coverings

<!-- source: IX.6.2 -->

**Corollary IX.6.2.** Under the conditions of IX.6.1, let `X′` be an étale covering of `X`, and let `\bar{X}_0'` be the
corresponding étale covering of `\bar{X}_0`. The following conditions are equivalent:

1. There exists an `S′` étale over `S` and an `X`-isomorphism `X′ ≃ X ×_S S′`. (`S′` is determined up to unique
    isomorphism by IX.3.4.)
1. `\bar{X}_0'` is **completely decomposed** over `\bar{X}_0`, i.e. isomorphic to a disjoint union of copies of
    `\bar{X}_0`.

If `X′` is **connected**, these are also equivalent to:

1. `\bar{X}_0'` has a **section** over `\bar{X}_0`.

When these equivalent conditions hold, we say `X′` is **geometrically trivial**.

*Proof.* The equivalence of (1) and (2) is the right exactness in IX.6.1: an étale `X′ → X` is the pullback of an étale
`S′ → S` iff its monodromy representation `π₁(X, a) → \mathrm{Sym}(X_a')` factors through `π₁(S, b)`, iff the image of
`π₁(\bar{X}_0, ā) → π₁(X, a)` acts trivially on `X_a'`, iff `\bar{X}_0' \to \bar{X}_0` is trivial.

For connected `X′`, condition (3) is just that "trivial cover has a section." ∎

> **Caveat.** The equivalence of (1) and (2) means only that the *quotient* `π₁(S, b) = π₁(X, a) / N` for some `N`
> *containing* the image of `π₁(\bar{X}_0, ā)`, *not* that `N` *equals* the image. This is the central technicality of
> the exact sequence: the image of `π₁(\bar{X}_0, ā)` is *not always* a normal subgroup of `π₁(X, a)`; one has to take
> its closed normal *closure*.

### IX.6.3 — Counterexample to dropping properness

<!-- source: IX.6.3 -->

**Remark IX.6.3 (Artin–Schreier).** In IX.6.1 one *cannot* replace `\bar{k}` by an arbitrary algebraically closed
extension of `k`, even if `k` is already algebraically closed. In characteristic `p > 0`, the **affine line**
`X = 𝔸^1_k` has the property that its étale fundamental group **grows** when one passes from `\bar{k} = k` to a larger
algebraically closed extension `K`. The reason: **Artin–Schreier coverings** (étale coverings of `𝔸^1_k` given by
`y^p - y = f(x)` for `f \in k[x]`) of `𝔸^1_k` exist for every `f`, and the family of all such `f` defines a *continuous*
parameter space (`f ∈ k[x]_{∞}`, the polynomial ring). Passing to a larger `K` adds *new* polynomials `f`, and hence new
Artin–Schreier coverings.

So `π₁(𝔸^1_k, a) \neq π₁(𝔸^1_K, a)` for `k \subsetneq K` both algebraically closed in characteristic `p > 0`. The
*proper* condition in IX.6.1 (or rather: quasi-compact + geometrically connected over the residue field) is
**essential**.

In characteristic `0`, no such phenomenon arises: étale coverings of `𝔸^1_{\bar{k}}` are *finite* and *abelian* (by
Riemann–Hurwitz over `\mathbb{C}`), and there are no continuous families. Transcendental methods then prove
finite-presentation of `π₁` in characteristic `0` for any geometrically connected variety.

### IX.6.4 — Splitting when there is a rational point

<!-- source: IX.6.4 -->

**Corollary IX.6.4.** Under the conditions of IX.6.1, suppose the geometric base point `a` is localised at an `x ∈ X`
that is **rational over `k`** (or more generally has residue field radicial over `k`). Then the exact sequence IX.6.1 is
**split**.

*Proof.* Without loss assume `S = \mathrm{Spec}(k)`. If `x` is rational over `k`, it gives a section `s : S \to X` of
`X / S`, sending the base point of `S` to `a`. This section defines a homomorphism `π₁(S, b) \to π₁(X, a)` that is a
right inverse to `π₁(X, a) \to π₁(S, b)`. If `\kappa(x) / k` is radicial, reduce to the rational case by base change
`\mathrm{Spec}(\kappa(x)) \to \mathrm{Spec}(k)` (which is radicial and so does not change π₁ by IX.4.11). ∎

> **Slogan.** *A `k`-rational point of `X` splits the fundamental exact sequence.*

### IX.6.5 — The existence theorem via Stein factorisation

<!-- source: IX.6.5 -->

#### Mini-introduction: Stein factorisation

For a **proper** morphism `f : X → S` of locally noetherian preschemes, the **Stein factorisation** is the canonical
factorisation

```text
f :  X  -->^{f^{Stein}}  S′ = Spec_S(f_*(𝒪_X))  -->^{g}  S,
```

where `X → S′` is the morphism induced by the unit `𝒪_S → f_*(𝒪_X)`, and `S′ → S` is the morphism associated to the
quasi-coherent `𝒪_S`-algebra `f_*(𝒪_X)`. By EGA III §4.3.1 (\[`ega-iii-stein-factorisation`\]
(appendix-black-boxes.md#ega-iii-stein-factorisation)), `X → S′` is proper with **geometrically connected fibres** (the
geometric content of "Stein factorisation = factor out the connected-fibre piece") and satisfies
`(X → S′)_*(𝒪_X) = 𝒪_{S′}`, while `S′ → S` is **finite**. The intermediate scheme `S′` is locally noetherian.

The Stein factorisation lets one reduce questions about proper morphisms with arbitrary fibres to questions about proper
morphisms with **connected fibres** plus questions about **finite morphisms**.

**Theorem IX.6.5.** Let `f : X → S` be a **proper and surjective morphism of finite presentation, with geometrically
connected fibres**; let `X′` be a prescheme **of finite presentation** and **proper over `X`**; let `s ∈ S` and let
`F = X_s` (the fibre of `X` at `s`); and let `F₁′` be a **connected component** of the fibre `F′ = X′_s` of `X′` at `s`.
**There exists an open neighbourhood `X_1′` of `F₁′` in `X′`, an `S`-scheme `S₁′ → S` that is étale, and an
`X`-isomorphism `X_1′ ≃ S_1′ ×_S X`** if and only if `X′` is **étale over `X` at the points of `F₁′`** and `F_1′` is a
**geometrically trivial covering** of `F`.

*This result says:* **`X′ → X` is étale over `X` and geometrically trivial on `F` iff `X′` is locally isomorphic to the
pullback from an étale `S′ → S`.**

*Proof.* Necessity is trivial (étale `S_1′ → S` pulled back to `X` produces an étale `S_1′ ×_S X` over `X`; its fibre is
a trivial covering of `F`). For sufficiency:

**Step 1: reduce to noetherian.** Easily reduce to `S` noetherian (via `ega-iv-limit-of-rings`).

**Step 2: Stein-factorise `f`.** Set `T = \mathrm{Spec}_S(f_*(𝒪_X))`. Then `X \to T \to S` is the Stein factorisation;
the morphism `X \to T` is proper with geometrically connected fibres and `f_*(𝒪_X) = 𝒪_T`, while `T \to S` is finite. By
IX.4.10 (file 45), every `T′ \to T` étale comes uniquely from an `S′ \to S` étale (because `T \to S` is finite
surjective; in fact `T \to S` is finite *radicial* surjective when `f` itself has geometrically connected fibres, by
*Stein factorisation's fundamental property*: a proper morphism factoring with connected fibres through a finite map is
*fibre-wise* radicial on the finite part). This **reduces** the problem from `S` to `T`. So we may assume `T = S`, i.e.
`f_*(𝒪_X) = 𝒪_S`.

**Step 3: Stein-factorise `X′ → S`.** Now the morphism `h : X′ \to S` is proper of finite presentation. Let
`X′ \to S′ \to S` be its Stein factorisation, `S′ = \mathrm{Spec}_S(h_*(𝒪_{X′}))`. The morphisms `X′ \to X` and
`X′ \to S′` define a canonical morphism

```text
X′  \to  X ×_S S′,
```

and our assertion is equivalent to: **the morphism `X′ \to X ×_S S′` is an isomorphism above an open neighbourhood of
`s′ \in S′`, and `S′` is étale over `S` at `s′`.** This is what we prove in IX.6.6 below.

### IX.6.6 — The Stein-factorisation criterion

<!-- source: IX.6.6 -->

**Corollary IX.6.6.** Let `f : X \to S` be a proper morphism of locally noetherian preschemes such that
`f_*(𝒪_X) = 𝒪_S`, and let `X′` be a prescheme proper over `X`. Consider the Stein factorisation `X′ \to S′ \to S` of
`X′ \to S` and the canonical morphism `X′ \to X ×_S S′`. Let `s ∈ S`, and let `s′ ∈ S′` lie over `s`, corresponding to a
connected component `F_1′` of the fibre `X′_s` of `X′` at `s`. **The morphism `X′ \to X ×_S S′` is an isomorphism above
an open neighbourhood `U′` of `s′` étale over `S` if and only if `X′` is étale over `X` at the points of `F_1′` and
`F_1′` is a geometrically trivial covering of `F = X_s`.**

*Proof.* Necessity is trivial.

For sufficiency: the conclusion equivalently says that

- (a) the morphism deduced from `X′ \to X ×_S S′` by the base change `\mathrm{Spec}(\hat{𝒪}_{s′}) \to S′` is an
    isomorphism, and
- (b) `S′` is étale over `S` at `s′`, i.e. `\hat{𝒪}_{s′}` is étale over `\hat{𝒪}_s`.

The hypotheses and the conclusion are invariant under base change `\mathrm{Spec}(\hat{𝒪}_s) \to S`. Since the hypotheses
are stable, we may suppose `S = \mathrm{Spec}(A)` with `A` a complete noetherian local ring. We may also suppose `X′`
connected, which forces `S′ = \mathrm{Spec}(𝒪_{s′})` and `F′ = F_1′`.

**Open property of étaleness.** The set of points of `X′` at which `X′` is étale over `X` is open. It contains the fibre
`X′_{s′} = F′`. Since `X′` is proper over `S`, the locus of étaleness is therefore *all* of `X′`. (Properness plus open
property of étaleness on the closed fibre force étaleness on the entire proper variety.)

Now `X′ \to X` is étale, and on the special fibre it induces an étale covering of `F = X_s` isomorphic to
`F ⊗_{\kappa(s)} L` for some finite étale `L / \kappa(s)` (this is the "trivial covering" condition: `F_1′ →  F` trivial
means `F_1′ ≃ F ⊗ L` for a finite étale `\kappa(s)`-algebra `L`).

**Apply IX.1.10 (file 44).** Since `X / S` is proper with `S = \mathrm{Spec}(A)` complete local, **IX.1.10** says the
functor `X′ \mapsto X′ ×_X X_0` (where `X_0` is the special fibre) is an *equivalence* from étale coverings of `X` to
étale coverings of `X_0`. Our `X′ \to X` corresponds to `F_1′ \to F`, which is isomorphic to `F ⊗_{\kappa(s)} L`;
pulling back, this is `(X ⊗_S T) \to X` for `T = \mathrm{Spec}(L \otimes_{\kappa(s)} A^{Stein})` where `A^{Stein}` is
the Stein algebra. Up to the canonical Stein-factorisation isomorphism, this is exactly `X ×_S T_{global}` for a finite
étale `T_{global} \to S`.

Hence `X′ ≃ X ×_S T_{global}`, with `T_{global}` finite étale over `S`. Since `f_*(𝒪_X) = 𝒪_S` (by Stein factorisation
of `f`), it follows that `h_*(𝒪_{X′}) = B$ where`T\_{global} = \\mathrm{Spec}(B)`, and the canonical morphism`X′ \\to X
×\_S S′ ≃ X ×_S T_{global}\` is the isomorphism we want. This completes the proof. ∎

> **Slogan.** *Stein factorisation reduces "proper + étale on fibres + trivial" to a finite étale base change upstairs
> and a finite-étale-over-`S′` correspondence downstairs.*

### IX.6.7 — Global version: descent of étale `X′ \to X` to étale `S′ \to S`

<!-- source: IX.6.7 -->

**Corollary IX.6.7.** Under the conditions of IX.6.5, **there exists a prescheme `S′` étale over `S` and an
`X`-isomorphism `X′ ≃ X ×_S S′`** if and only if `X′` is **étale over `X`** and, for every `s ∈ S`, the fibre `X′_s` is
a **geometrically trivial covering** of `X_s`.

*Proof.* Necessity is trivial. For sufficiency: by IX.6.5 each fibre's connected component has an open neighbourhood in
`X′` of the form `X ×_S S_i′` for some étale `S_i′ \to S`. The local `S_i′` glue compatibly: the descent data for
`X′ \to X` (relative to `X \to S`) restrict to descent data on each `X_i′`, and the gluing is determined uniquely by the
global structure. Globally we obtain an `S′ \to S` étale and an `X`-isomorphism `X′ ≃ X ×_S S′`. ∎

### IX.6.8 — `f` is effective for finite étale, identification of categories

<!-- source: IX.6.8 -->

**Corollary IX.6.8.** Let `f : X \to S` be a **proper surjective morphism of finite presentation with geometrically
connected fibres**. Then `f` is a morphism of **effective descent** for the fibred category of preschemes **finite étale
over other preschemes**. The functor `S′ \mapsto X ×_S S′` induces an **equivalence** from the category of finite étale
`S`-preschemes to the category of finite étale `X`-preschemes that are **geometrically trivial** on every fibre.

*Proof.* Combine IX.6.7 with IX.3.4 + IX.4.12 (file 45). ∎

### IX.6.9 — Alternative proof of IX.4.12

<!-- source: IX.6.9 -->

**Remark IX.6.9.** Let `f : X \to S` be **proper surjective with `S` locally noetherian**. Then `f` factors as
`X \to S′ \to S` where the first morphism satisfies the hypothesis of IX.6.8 (proper surjective with geometrically
connected fibres) and the second is finite surjective covered by IX.4.7 (file 45). Thus `f` is a **composite of two
universal effective descent morphisms** for finite étale coverings, hence itself a universal effective descent morphism.
**This recovers IX.4.12** (file 45) by an alternative route — via Stein factorisation rather than via IX.1.10's
complete-local equivalence.

### IX.6.10 — Counterexample: non-proper case

<!-- source: IX.6.10 -->

**Remark IX.6.10 (Counterexample).** The conclusion of IX.6.7 does **not** remain valid if "proper" is replaced by "`X`
is of finite type over `S` and admits a section over `S`" (so `f` is universally submersive and a descent morphism for
étale preschemes, by IX.3.3), even when `S` is the spectrum of a discrete valuation ring and `X′` is an étale covering
of `X`.

A concrete counterexample (Grothendieck's, in IX.6.10): start with `Z` proper over `S` whose generic fibre is a
non-singular rational curve and whose **special fibre `Z_0` consists of two intersecting lines**. For example, if `t` is
a uniformiser of the valuation ring `A` of `S`, take the closed subscheme `Z \subset ℙ²_A` defined by

```text
x² + y² + t z² = 0.
```

The generic fibre is the non-singular conic `x² + y² + z² = 0`; the special fibre `Z_0 \subset ℙ²_k` is the union
`L_1 \cup L_2` of two intersecting lines `(x + iy)(x - iy) = 0`. Set `X` to be the complement of the singular point `a`
of `Z_0` in `Z \cup ℙ²_k` (where the union is along `Z_0 \subset ℙ²_k`). The fibres of `X / S` are `ℙ¹_k` and
`ℙ²_k - \{a\}`, both **geometrically simply connected**.

But one can construct étale coverings of `X` that do **not** come from étale coverings of `S`, by gluing the trivial
covering of `Z - a$ with a non-trivial one of`ℙ²_k - a`(in characteristic`0`, the simply-connected`ℙ²_k -
a`has no non-trivial étale coverings; in characteristic`p\` it does, by Artin–Schreier). So the criterion of IX.6.7
fails without properness.

> **Slogan.** *Properness in IX.6.7 is essential; without it, Artin–Schreier phenomena in characteristic `p` (or
> non-uniqueness of gluings in general) break the criterion.*

Grothendieck adds in IX.6.10:

> It is possible, on the other hand, that the conclusion of IX.6.7 remains true if the properness hypothesis is replaced
> by the hypothesis that `X` be **universally open** of finite presentation over `S`. \[Translator note: this is now
> proved, with `g` only universally open and surjective; cf. SGA 4 XV 1.15.\] This is at least true if the fibres of `X`
> over `S` are **geometrically irreducible**, and not merely geometrically connected.

### IX.6.11 — π₁ translation

<!-- source: IX.6.11 -->

**Corollary IX.6.11.** Let `f : X \to S` be a **proper surjective morphism of finite presentation with geometrically
connected fibres**. Suppose `X` (hence `S`) is **connected**. Let `a` be a geometric point of `X`, let `b` be its image
in `S`, and for every `s \in S` choose an algebraic closure `\bar{\kappa(s)}` of `\kappa(s)`, a geometric point `a_s` of
`\bar{X}_s = X_s ⊗ \bar{\kappa(s)}`, and a path class from `a_s$ to`a\`. This gives canonical homomorphisms

```text
π₁(\bar{X}_s, a_s)  \to  π₁(X, a).
```

Then the homomorphism `π₁(X, a) \to π₁(S, b)` is **surjective**, and its **kernel** is the closed normal subgroup of
`π₁(X, a)` generated by the images of the `π₁(\bar{X}_s, a_s)` as `s` ranges over `S`.

*Proof.* This is the π₁-translation of IX.6.7: "geometrically trivial on every fibre" is the assertion that the
representation of `π₁(X, a)` on a fibre `X_a'$ factors through`π₁(S, b)`, iff the image of each`π₁(\\bar{X}\_s)\` acts
trivially. ∎

> **Slogan.** *The π₁ exact sequence is "fibre-wise" in `s`: the kernel of `π₁(X) \to π₁(S)` is generated by the images
> of the fibre π₁'s, ranging over all `s`.*

### IX.6.12 — Jacobson reduction

<!-- source: IX.6.12 -->

**Remark IX.6.12.** Under the conditions of IX.6.7, with `S` noetherian, one can show that the set of `s \in S` such
that the corresponding fibre `X_s′ \to X_s` is geometrically trivial is **constructible**; if moreover `X′` is proper
over `X`, this set is even **open** (as one sees from IX.6.6). Hence: if `S` is a **Jacobson** prescheme (for example,
finite type over a field), or if `X′` is proper over `X`, it is enough — to verify the conditions of IX.6.7 — to
restrict to the **closed points `s ∈ S`**.

Likewise, in IX.6.11 it is then enough to take the `π₁(\bar{X}_s, a_s)` for the **closed points** of `S`.

> **Slogan.** *For Jacobson `S`, the π₁ exact sequence and the geometric-triviality condition are determined by the
> closed points.*

This is the "rational-points-suffice" technique in geometric class field theory: most arithmetic information about a
scheme over a number field or finite field is detected at the closed (i.e. arithmetic) points.

## Connection back to files 30–33; pointer to file 48

The étale fundamental group story is now **self-contained** from file 01 through file 47:

- Files 01–06: preparation arc (rings, schemes, sheaves, étale).
- Files 10–12: Exposé I — étale morphisms.
- Files 14–16: Exposé II — smooth morphisms.
- Files 17–22: Exposé III — formal-smooth, lifting, algebraisation.
- Files 23–27: Exposé IV — flatness, faithfully flat, generic flatness.
- Files 28–33: Exposé V — the étale fundamental group `π₁(S, a)`.
- Files 34–38: Exposé VI — sites, fibred categories, descent.
- Files 40–43: Exposé VIII — faithfully flat descent of quasi-coherent modules and schemes.
- Files 44–47: Exposé IX — descent of étale morphisms, the Seifert–van-Kampen formula, the fundamental exact sequence.

Every black-box invocation of [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) in files 30, 31, 33 now
refers to a *developed theorem* in files 40–47. The black-box invocation of
[`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) in files 06 and 12 now refers to **IX.4.10** of file 45.

### What remains beyond Exposé IX

Files 48–51 carry the gentle pass through **Exposé X — Théorie de la spécialisation du groupe fondamental**: the
homotopy exact sequence for a proper separable morphism (X.1.4 in file 48), the specialisation morphism on `π₁` and its
upper semicontinuity (X.2.3–X.2.4 in file 49), the transcendental method for `π₁` of a proper smooth curve (X.2.6 in
file 50) and the surface presentation with `2g` generators and one commutator relation, and the continuity theorem for
proper smooth morphisms via Zariski–Nagata purity and Abhyankar's lemma (X.3.8 in file 51). The X.1.7 product formula
`π₁(X ×_k Y) ≃ π₁(X) × π₁(Y)` developed in file 48 is the formal underpinning of the pinching and symmetric-power
applications IX.5.4 and IX.5.8 above.

The remaining exposés of SGA 1, not yet part of the gentle pass:

- **Exposé XI — Exemples et compléments.** Examples and additional computations of `π₁` for various classes of schemes
    (curves, complete intersections, etc.). Cited from file 49 (X.2.5) for explicit nonseparable counterexamples.
- **Exposé XII — Géométrie algébrique et géométrie analytique.** The comparison theorem (GAGA): for `X` proper over
    `\mathbb{C}`, `π₁^{ét}(X) ≃ π₁^{top}(X^{an})` (after profinite completion). The bridge between étale and classical
    algebraic topology — the formal foundation of the transcendental method used in file 50.
- **Exposé XIII — Propriété cohomologique.** Cohomological invariance under base change for proper morphisms.

These three remain as future gentle passes. Their content is partially surveyed by modern accounts (Vistoli, Murre,
Szamuely) which we cite below.

### Modern parallel accounts

- **Vistoli, _Notes on Grothendieck topologies, fibered categories and descent theory_** (FGA Explained, AMS 2005; arXiv
    math/0412512). Ch. 4 in particular covers the descent material of file 45 cleanly. See
    [`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained).
- **Murre, _Lectures on an Introduction to Grothendieck's Theory of the Fundamental Group_** (Tata IFR 1967) /
    **Cadoret, _Galois Categories_**. Ch. 7 in particular develops the étale fundamental group with full categorical
    packaging. See [`murre-cadoret-galois-categories`](appendix-black-boxes.md#murre-cadoret-galois-categories).
- **Szamuely, _Galois Groups and Fundamental Groups_** (Cambridge Studies in Advanced Mathematics 117, CUP 2009). §5.6
    in particular gives a clean modern proof of the fundamental exact sequence (IX.6.1). See
    [`szamuely-fundamental-groups`](appendix-black-boxes.md#szamuely-fundamental-groups).
- **Bosch–Lütkebohmert–Raynaud, _Néron Models_** (Springer 1990), Ch. 6: the closest modern treatment in spirit to
    Grothendieck's original.
- **Stacks Project**, especially Tags 023A (fpqc descent), 03O2 (QCoh descent), 0247 (descent of schemes), 04TQ (descent
    of morphisms), 0BTW (the fundamental exact sequence).

### Brief retrospective: the arc so far

The eight exposés covered through file 47, in arc form:

- **Exposé I** (étale, files 10–12). Étale = smooth + relative dimension `0`.
- **Exposé II** (smooth, files 14–16). Smooth = locally étale over a polynomial scheme.
- **Exposé III** (formally smooth, files 19–22). Formally smooth = lifting + cohomological vanishing.
- **Exposé IV** (flat, files 24–27). Flat = exactness of `M ⊗_A -`; flat morphisms are open; generic flatness is the
    spread-out theorem.
- **Exposé V** (étale fundamental group, files 30–33). `π₁(S, a)` is the Galois group of the universal finite étale
    cover.
- **Exposé VI** (fibred categories and descent, files 35–38). A global functor on a fibred category is determined by its
    fibre-wise restrictions plus a cocycle.
- **Exposé VIII** (faithfully flat descent of schemes, files 40–43). Faithfully flat quasi-compact morphisms are
    morphisms of effective `QCoh`-descent; descent of schemes is effective in five canonical cases.
- **Exposé IX** (descent of étale morphisms, files 44–47). Universally submersive morphisms are descent morphisms for
    étale preschemes; effective descent holds in five sharper hypotheses; the topological invariance of the étale site
    (IX.4.10) is the algebraic counterpart of "universal homeomorphism doesn't change π₁"; the Seifert–van-Kampen
    formula (IX.5.1) computes `π₁(S, a)` from descent data; the fundamental exact sequence (IX.6.1) is the algebraic
    analogue of the homotopy exact sequence of a fibration.

The arc is from *local* to *global*: étale and smooth morphisms are local conditions on tangent vectors and fibres;
their global structure is captured by `π₁`; descent reconstructs the global structure from a cover; and the fundamental
exact sequence stitches together π₁ over a base with π₁ of the geometric fibre. The whole arc rests on *flatness*
(Exposé IV) as its commutative-algebra foundation and on *fibred categories* (Exposé VI) as its categorical foundation.

#### Aside (the philosophical takeaway).

_Skip if the philosophical perspective on Grothendieck's programme is not part of your current concern._

The technique of Exposé IX — **descent of finite étale coverings** — is one of the most powerful tools in Grothendieck's
geometric arsenal. It says: when the étale fundamental group of a scheme `S` is hard to compute directly, one can
compute it on a cover `S′ → S` (where finite étale coverings have a transparent description, e.g. because `S′` is the
spectrum of a complete local ring), provided the cover is well-behaved (universally submersive, or proper surjective
with geometrically connected fibres). The Seifert–van-Kampen formula then gives an explicit presentation of `π₁(S, a)`
in terms of `π₁` of the components of `S′`, `S″`, `S‴` and cocycle data.

The deep observation: **the étale fundamental group is a *functor of descent data*.** Descent doesn't merely tell us how
to glue local pictures; it tells us how to glue *fundamental groups* of local pictures, and the answer is always a
galoisian-type group with a presentation extracted from the cover. The fundamental exact sequence is the particular case
where the cover is a fibration `X → S` with geometrically connected fibres — the algebraic analogue of the long exact
sequence of homotopy groups for a fibration.

This is the heart of Grothendieck's program: every *global* invariant (the étale fundamental group, étale cohomology,
ℓ-adic cohomology) is a *functor of descent data*, and descent reduces global computations to local ones plus
combinatorics on covers. The fundamental exact sequence is the cleanest realisation of this principle for π₁; analogous
principles drive étale cohomology (via SGA 4), motivic cohomology (via Voevodsky), and the entire six-functor formalism
(via Ayoub, Cisinski–Déglise, Mann).

______________________________________________________________________

## Pointer to file 48

File 48 opens Exposé X. The homotopy exact sequence developed there generalises IX.6.1 to a proper *separable* morphism
over any locally noetherian base, at the price that the leftmost arrow `π₁(X̄_y) → π₁(X)` is no longer asserted
injective. The engine is the upgrade of EGA III §4.3's Stein factorisation to a finite *étale* covering under
separability (EGA III §7.8.10(i), recorded as the new appendix row
[`ega-iii-7-stein-finite-etale`](appendix-black-boxes.md#ega-iii-7-stein-finite-etale)). The narrative arc of Exposé X
then proceeds from upper semicontinuity (file 49) through the transcendental method (file 50) to continuity via purity
and Abhyankar's lemma (file 51).
