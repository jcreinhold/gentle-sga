# Exposé VIII §VIII.1 (gentle): descent of quasi-coherent modules

## What this file is about

Imagine building a surface from a handful of local patches together with instructions for how to glue the patches along
their overlaps. The patches alone do not determine the surface; the gluing instructions do half the work. In algebra the
same question appears: a global object lives over a base, and pulling it back to a covering gives pieces, while the
overlap data records how the pieces line up. The natural question is when the pieces and the gluing data, taken
together, determine a unique global object.

The answer is yes, under a clean local-to-global condition on the covering. This file proves the first geometric version
of that statement, for the simplest kind of object — what algebraic geometers call a quasi-coherent module.

## Opening: from framework to first geometric specialisation

**fpqc descent.** A module on a scheme can be reconstructed from its pullback along a faithfully flat quasi-compact
cover, together with a gluing rule on the double overlap. This is the algebraic counterpart of recovering a vector
bundle on a topological space from a trivialisation over a covering family plus the transition functions on
intersections; the role of the open cover is played by the fpqc cover, and the role of transition functions is played by
the descent datum.

File 38 closed Exposé VI with the **descent isomorphism** VI.12.1: a global functor on a normalised cloven fibred
category `ℱ → ℰ` is the same data as fibre-wise functors `F_S : ℱ_S → 𝒞` plus natural transformations
`φ_f : F_T ∘ f^* ⟹ F_S` satisfying normalisation and a cocycle identity. That is a categorical statement. It is silent
on which morphisms `g : S′ → S` of which base category `ℰ` make the descent data actually *come from* a global object.

Exposé VIII fixes the base `ℰ` to be `Sch`, fixes the fibred category to be **quasi-coherent modules on preschemes** —
the running example we previewed in file 34 Module C and file 38 example b — and proves the geometric specialisation.
The condition on `g` that makes descent work is the conjunction of two properties Grothendieck takes from Bourbaki:
**flatness** (`g` is flat in the sense of file 24, IV.1), and a mild finiteness condition (**quasi-compact**). Then `g`
faithfully flat and quasi-compact is exactly the condition under which "a quasi-coherent module on `S` is the same data
as a quasi-coherent module on `S′` together with a descent datum relative to `g`".

The statement we are unpacking is the one we have been citing for ten files as
[`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190): the load-bearing black box behind file 30 (V.2.6's
principal coverings descend), file 31 (V.3.6's strict-epimorphism for finite étale), and file 33 (V.7's principal-
homogeneous classification). What this exposé proves first — and almost everything later in Exposé VIII reduces to it —
is **Theorem VIII.1.1**: faithfully flat quasi-compact morphisms are morphisms of effective descent for quasi-coherent
modules. The proof is an algebraic reduction (open-cover ⇒ affine target ⇒ affine source and target) followed by a short
module-theoretic computation. We reproduce both in full.

## Opening preliminaries

<!-- source: VIII §1 preamble -->

### Faithfully flat and quasi-compact

_Recap from file 24._ An `A`-algebra `A → A′` is **faithfully flat** when (equivalently): the functor `M ↦ M ⊗_A A′` is
exact and reflects exactness; for every nonzero `A`-module `M`, the base change `M ⊗_A A′` is nonzero; for every prime
`𝔭 ⊂ A` there exists a prime `𝔭′ ⊂ A′` lying over `𝔭`. The geometric face: a morphism `g : S′ → S` of preschemes is
faithfully flat iff `g` is **flat** (`𝒪_{S′,s′}` is a flat `𝒪_{S,g(s′)}`-module for every `s′`) and **surjective** on
underlying topological spaces.

A morphism `g : S′ → S` is **quasi-compact** when the inverse image of every quasi-compact open of `S` is quasi-compact
in `S′`. For schemes the working translation is: every affine open `U ⊂ S` has `g⁻¹(U)` a *finite* union of affine
opens. Quasi-compactness is the finite-cover hypothesis that lets us reduce most arguments to the affine case.

The conjunction **faithfully flat and quasi-compact** is the hypothesis under which the descent technique works for
quasi-coherent modules and a wide class of schemes derived from them. It is sometimes abbreviated **fpqc**.

#### Aside (analogy).

_Skip if Galois descent is not part of your background._

For `S = Spec k` with `k` a field and `S′ = Spec k′` with `k′ / k` a finite Galois extension, `g` is finite (hence
quasi-compact) and surjective, and flatness is automatic since `k′` is a flat `k`-module. So `Spec k′ → Spec k` is
faithfully flat and quasi-compact, and Theorem VIII.1.1 specialises to Weil's classical Galois descent. Poonen's
treatment (Rational Points on Varieties §4.4) makes this specialisation explicit.

### The fpqc covering condition as a Grothendieck topology

File 34 Module A defined a Grothendieck topology on `(Sch / S₀)` by declaring covering sieves. The **fpqc topology**
takes its covers to be finite jointly-surjective collections `{T_i → S}` such that each `T_i → S` is flat and the total
map `⨿ T_i → S` is quasi-compact. The simplest fpqc cover is a single faithfully flat quasi-compact morphism
`g : S′ → S`, regarded as the one-element cover `{S′ → S}`. Throughout this file we work with such single-element
covers; the general fpqc cover follows by Čech-type assembly that we comment on but do not repeat (see Vistoli §4.1).

### The fibred category of quasi-coherent modules

<!-- source: VIII §1 preamble -->

For each prescheme `X`, write `QCoh(X)` for its category of quasi-coherent `𝒪_X`-modules. For a morphism `f : X → Y`,
the **inverse image** `f^* : QCoh(Y) → QCoh(X)` carries `F` to the quasi-coherent module locally given (on affines) by
`M ↦ M ⊗_A B` for `B = 𝒪_X` an `A = 𝒪_Y`-algebra. Inverse image is functorial up to a canonical natural isomorphism
`(gf)^* ≃ f^* ∘ g^*`, so the assignment

```text
S ↦ QCoh(S)°,    f ↦ (f^*)°
```

is a pseudofunctor `Sch° → Cat`, hence (file 37 §VI.8) a fibred category over `Sch` after the cleavage construction.
*Note the opposite.* As Grothendieck flags in the preamble of VIII §1, the fibre at `X` of the SGA-style fibred category
of pairs `(X, F)` is the *opposite* of `QCoh(X)`, because we used direct image to package morphisms into the total
category. Working with the inverse-image pseudofunctor is equivalent and conventionally cleaner; we adopt it without
further comment.

For an fpqc cover `g : S′ → S` write

```text
p₁, p₂ : S″ = S′ ×_S S′ ⇉ S′,
p_{12}, p_{13}, p_{23} : S‴ = S′ ×_S S′ ×_S S′ ⇉ S″.
```

The cleavage's coherence isomorphism `c_{f, g}` (file 36 VI.7) is here the canonical comparison
`p_i^* g^* F ≃ (g p_i)^* F`, which is *strict* — fibre products of schemes are associative on the nose.

### Descent data in module form

<!-- source: VIII §1 preamble; specialisation of VI.12.1 -->

Recall (VI.12.1, file 38): the descent isomorphism says that a section of a fibred category over a base `S` is the same
data as a family of sections over a cover of `S` together with gluing isomorphisms on the pairwise overlaps, subject to
a cocycle condition on the triple overlaps.

Specialising file 38's descent isomorphism VI.12.1 to the cloven category `QCoh(–)°` and to the one-arrow base
`{T → S} ⊂ Sch`, a **descent datum** on a quasi-coherent `𝒪_{S′}`-module `M′` relative to `g : S′ → S` is an isomorphism

```text
φ : p₁^*(M′)  ⟶  p₂^*(M′)    of quasi-coherent 𝒪_{S″}-modules
```

satisfying the **cocycle condition** on `S‴`:

```text
p_{13}^*(φ)  =  p_{23}^*(φ) ∘ p_{12}^*(φ).
```

A morphism of pairs `(M′, φ) → (N′, ψ)` is an `𝒪_{S′}`-linear map `u′ : M′ → N′` compatible with the descent data, i.e.
such that `ψ ∘ p₁^*(u′) = p₂^*(u′) ∘ φ`. This is the *category of `g`-descent data* for quasi-coherent modules; we
denote it `QCoh(S′ / g)`.

A descent datum is **effective** if `(M′, φ)` is isomorphic to `(g^* M, φ_M)` for some `M ∈ QCoh(S)`, where `φ_M` is the
canonical descent datum on `g^* M` (the cleavage comparison `p₁^* g^* M ≃ (g p₁)^* M ≃ (g p₂)^* M ≃ p₂^* g^* M`). The
morphism `g` is a **morphism of `QCoh`-descent** when `g^*` is fully faithful as a functor `QCoh(S) → QCoh(S′ / g)`, and
a **morphism of effective `QCoh`-descent** when this functor is an equivalence (every descent datum is effective).

### The ring-theoretic translation

When `S = Spec A` and `S′ = Spec A′` are affine and `g` corresponds to a ring map `A → A′`, the data becomes purely
algebraic. Set

```text
A″ = A′ ⊗_A A′,    A‴ = A′ ⊗_A A′ ⊗_A A′.
```

A quasi-coherent `𝒪_{S′}`-module is an `A′`-module `M′`. Its two pull-backs to `S″` correspond, respectively, to the
`A″`-modules `M′ ⊗_A A′` (where the tensor is over the left copy of `A′` in `A″`) and `A′ ⊗_A M′` (right copy). A
descent datum is an `A″`-linear isomorphism

```text
φ : M′ ⊗_A A′  ⟶  A′ ⊗_A M′
```

satisfying the cocycle on `A‴`. Effectivity means `M′ ≅ M ⊗_A A′` for some `A`-module `M`, with `φ` the canonical "flip"
comparing the two tensor orderings. This is the form in which Grothendieck proves VIII.1.1, and the form in which the
proof is shortest.

## §VIII.1 Faithfully flat descent of quasi-coherent modules

<!-- source: VIII.1 -->

### VIII.1.1 — The descent theorem for `QCoh`

<!-- source: VIII.1.1 -->

_This result says: a faithfully flat quasi-compact morphism `g : S′ → S` makes the category of quasi-coherent modules on
`S` equivalent to the category of quasi-coherent modules on `S′` with descent data relative to `g`. Every descent datum
is effective; descent data with a morphism between them comes from a unique module map upstairs._

**Theorem.** Let `g : S′ → S` be a faithfully flat and quasi-compact morphism of preschemes. Then `g` is a morphism of
effective `QCoh`-descent: the inverse image functor

```text
g^* : QCoh(S) ⟶ QCoh(S′ / g),    M ↦ (g^* M, φ_M)
```

is an equivalence of categories.

The slogan: **faithfully flat quasi-compact = effective descent for quasi-coherent modules.**

**Proof.** The proof is a chain of two reductions followed by a module-theoretic core. We label the reductions so the
shape is visible.

*Reduction 1 (open cover ⇒ affine target).* Suppose first that `T` is an `S`-prescheme `S`-isomorphic to the disjoint
sum of the inclusions of an open cover `{S_i ⊂ S}` of `S`. Then the morphism `T → S` is plainly a morphism of effective
`QCoh`-descent: descent data on a quasi-coherent module on `T` are exactly the standard gluing data on the `S_i`-pieces
with the standard cocycle on overlaps, and the gluing theorem for quasi-coherent sheaves (file 03 / EGA 0_I §3.5)
recovers a unique `M` on `S`. The hypothesis "`T` is the disjoint sum of an open cover" is stable under arbitrary base
change, so `T → S` is a *universal* morphism of effective `QCoh`-descent.

To prove that `g : S′ → S` is a morphism of effective descent, it suffices to verify it after the base change `T → S` —
this is the general fact about descent morphisms recalled in `[VIII.D]` (\[Giraud, *Méthode de la descente*, 1964\]).
Taking the `S_i` to be affine open subsets covering `S` reduces the proof to the case where **`S` is affine**.

*Reduction 2 (affine target ⇒ affine source).* With `S = Spec A` affine and `g` quasi-compact, `S′` is a finite union of
affine opens. Let `S₁` be their disjoint sum; this is an affine `S`-scheme, and the canonical morphism `S₁ → S′` is flat
and surjective. Composing, `S₁ → S` is faithfully flat and affine over `S`. If a faithfully flat *affine* morphism is a
strict morphism of `QCoh`-descent (the case we are about to reduce to), then since the hypothesis is stable under base
change and `S₁ → S′` has an `S`-section above each `S′`, the general lemma `[VIII.D]` again upgrades the descent
property of `S₁ → S` to `S′ → S`. So we may suppose **both `S` and `S′` affine**, with `g` corresponding to an
`A`-algebra map `A → A′` faithfully flat.

In this affine setting VIII.1.1 becomes the conjunction of two algebraic statements: the *exactness* of the hom-set
sequence (VIII.1.4 below, which gives full faithfulness of `g^*`), and the *reconstruction* of a module from its descent
datum (VIII.1.6 below, which gives essential surjectivity). We state and prove each in turn. ∎

The two lemmas VIII.1.4 and VIII.1.6 are what the rest of §VIII.1 builds on. We prove them next, then collect the
geometric corollaries.

### VIII.1.2 — Descent of homomorphisms (corollary)

<!-- source: VIII.1.2 -->

_This result says: morphisms between two quasi-coherent modules on `S` are exactly the morphisms between their inverse
images on `S′` that agree on the two pull-backs to `S″`._

**Corollary.** Let `g : S′ → S` be faithfully flat and quasi-compact. Let `F`, `G` be quasi-coherent modules on `S`,
with inverse images `F′, G′` on `S′` and `F″, G″` on `S″`. Then the diagram

```text
Hom_S(F, G)  ⟶  Hom_{S′}(F′, G′)  ⇉  Hom_{S″}(F″, G″)
```

is exact, i.e. the first map is a bijection onto the equaliser of the second pair.

Equivalently, the inverse image functor `F ↦ (F′, φ_F)` is **fully faithful** as a functor `QCoh(S) → QCoh(S′ / g)`.

This is the full-faithfulness half of VIII.1.1. It is the form of the theorem we usually invoke in practice.

### VIII.1.3 — Descent of modules (corollary)

<!-- source: VIII.1.3 -->

_This result says: every descent datum on a quasi-coherent module on `S′` is effective, hence the fully faithful functor
of VIII.1.2 is an equivalence._

**Corollary.** For every quasi-coherent module `F′` on `S′` equipped with a descent datum `φ` relative to `g`, the pair
`(F′, φ)` is isomorphic to `(g^* F, φ_F)` for a quasi-coherent module `F` on `S`, determined up to unique isomorphism by
VIII.1.2.

In practice: **giving a quasi-coherent module on `S` is the same as giving a quasi-coherent module on `S′` with a
descent datum relative to `g`.**

### VIII.1.4 — The exact hom-sequence Lemma (rings)

<!-- source: VIII.1.4 -->

_This result says: when `A′` is a faithfully flat `A`-algebra, hom-sets of `A`-modules form a 3-term exact sequence
under base change. The first arrow is injective by faithful flatness; the equaliser condition reduces the proof to a
sharper special case (VIII.1.5)._

**Lemma.** Let `A` be a ring, `A → A′` a faithfully flat ring homomorphism, `M`, `N` two `A`-modules, `M′`, `N′` the
`A′`-modules obtained by base change `A → A′`, and `M″`, `N″` the `A″ = A′ ⊗_A A′`-modules obtained by base change
`A → A″`. Then the sequence

```text
Hom_A(M, N)  ⟶  Hom_{A′}(M′, N′)  ⇉  Hom_{A″}(M″, N″)
```

is exact.

**Proof.** *Injectivity of the first map.* If `u : M → N` becomes zero after `⊗_A A′`, then for each `x ∈ M` the element
`u(x) ∈ N` has image `0` in `N′ = N ⊗_A A′`. But `N → N′` is injective by faithful flatness of `A′ / A` (the arrow
`N → N ⊗_A A′` is the unit of an exact functor that reflects monomorphisms onto rings). So `u(x) = 0` in `N`, hence
`u = 0`.

*Exactness at `Hom_{A′}(M′, N′)`.* Let `u′ : M′ → N′` be an `A′`-homomorphism such that the two `A″`-extensions
`u′ ⊗_A A′` and `A′ ⊗_A u′` agree as maps `M″ → N″`. We claim `u′ = u ⊗_A A′` for some unique `A`-linear `u : M → N`.

The identifications `M = (M ⊗_A A′)`-equalizer-of-the-two-base-changes-`M ⇉ M ⊗_A A″` and similarly for `N` reduce the
claim to: an `A′`-linear `u′` whose two `A″`-extensions agree carries the subset `M ⊂ M′` into the subset `N ⊂ N′`. The
restriction `u : M → N` is then `A`-linear because `u′` is `A′`-linear (and `M` consists of elements `x ∈ M′` with
`x ⊗ 1 = 1 ⊗ x` in `M″`), and `u′ = u ⊗_A A′` is automatic since both maps agree on `M ⊂ M′` and are `A′`-linear.

So the lemma reduces to: for `x ∈ M`, the element `u′(x) ∈ N′` lies in the kernel of the pair `N′ ⇉ N″`; we must show
that this kernel equals `N`. That kernel-equals-`N` statement is precisely the special case `M = A` of the lemma:

### VIII.1.5 — The case `M = A`

<!-- source: VIII.1.5 -->

_This result says: the canonical map `N → N′` identifies `N` with the equaliser of the two natural maps `N′ ⇉ N″`.
Equivalently, faithfully flat base change reflects "originating from below"._

**Corollary.** Let `N` be an `A`-module. Then the sequence

```text
N  ⟶  N′  ⇉  N″
```

is exact.

**Proof.** To prove exactness of the sequence, it suffices to prove that the sequence obtained by base change to some
*further* faithfully flat `A`-algebra `A₁` is exact. (Indeed, base change to `A₁` is exact by flatness; if the
base-changed sequence is exact at the middle term, faithful flatness of `A₁ / A` reflects exactness at the original
middle term.)

Take `A₁ = A′`. The sequence to prove exact then becomes the analogous one for the `A₁ = A′`-module `N₁ = N ⊗_A A′` and
the `A₁`-algebra `A′_1 = A₁ ⊗_A A′ = A′ ⊗_A A′ = A″`. But the morphism `Spec A″ → Spec A′` *has a section*: the
multiplication `A″ = A′ ⊗_A A′ → A′` is a ring map splitting both projections `p₁, p₂ : A′ ⇉ A″`. For any morphism
`g : T → U` with a section, every fibred category over `Sch` (in particular `QCoh`) has `g` as a strict morphism of
effective descent — see `[VIII.D]` for the abstract reason, or unfold by hand: the section gives a way to recover
elements of `N₁` from elements of `N₁ ⊗_{A₁} A′_1 = N₁ ⊗_{A′} A″`, and the equaliser computation is immediate.

So the case after base change to `A₁ = A′` is exact, hence so was the original. ∎

*Remark on the trick.* The choice "base change again to `A₁ = A′`" looks magical. The mechanism is: faithful flatness of
`A → A′` lets one freely apply base change `A → A′` to detect exactness; after the change of rings, the morphism under
consideration acquires a *section* (because `A′ → A″` splits via multiplication), and *any* morphism with a section is a
strict morphism of effective descent for trivial reasons. This is the same dance used in VIII.1.6 below.

### VIII.1.6 — The reconstruction Lemma (keystone)

<!-- source: VIII.1.6 -->

_This result says: from a descent datum on `N′` we can build a candidate `A`-module `N` as the equaliser, and faithful
flatness then forces the canonical map `N ⊗_A A′ → N′` to be an isomorphism. This is the substantive content of VIII.1.1
— the surjective-on-objects half of "`g^*` is an equivalence"._

**Lemma.** Let `A′` be an `A`-algebra, and let `N′` be an `A′`-module equipped with a descent datum
`φ : N′ ⊗_A A′ ≃ A′ ⊗_A N′` relative to `A → A′` (i.e. an `A″`-linear isomorphism between the two `A″`-modules deduced
from `N′`, satisfying the cocycle on `A‴`). Define the `A`-submodule

```text
N  =  { x ∈ N′  :  φ(x ⊗ 1) = 1 ⊗ x  in N′ ⊗_A A′ }
```

and consider the canonical homomorphism

```text
ι : N ⊗_A A′  ⟶  N′,    n ⊗ a′ ↦ a′ · n_{| N′}.
```

This homomorphism is compatible with the descent data on the two sides (the canonical one on `N ⊗_A A′` and the given
one on `N′`).

*If `A′` is faithfully flat over `A`, then `ι` is an isomorphism.*

**Proof.** Compatibility of `ι` with descent data is a routine unfolding of the definitions (the canonical descent datum
on `N ⊗_A A′` is `φ_{can}(n ⊗ a ⊗ b) = (n ⊗ b ⊗ a)`, which the inclusion `N ⊂ N′` carries to `φ` by the defining
equation of `N`).

For the isomorphism claim, the same base-change trick as in VIII.1.5 applies. By flatness of `A → A′` (which holds under
our faithful-flatness hypothesis), and *again* using that exactness of an `A`-module sequence can be detected after base
change to a faithfully flat `A`-algebra, it suffices to show that `ι` becomes an isomorphism after `⊗_A A′`.

But after base change `A → A′`, the situation `(A → A′, N′, φ)` becomes `(A′ → A″ = A′ ⊗_A A′, N′ ⊗_A A′, φ ⊗_A A′)`,
and one checks (using the description of `N` and a careful unwinding of the descent datum `φ`) that the canonical map
`ι ⊗_A A′ : (N ⊗_A A′) ⊗_A A′ → N′ ⊗_A A′` becomes the map analogous to `ι` for the *new* situation — for which the ring
map `A′ → A″` again has a section (multiplication). A morphism with a section is a strict morphism of effective descent
for any fibred category over `Sch` (`[VIII.D]`), so the map analogous to `ι` is an isomorphism. Pulling back to the
original situation, `ι` itself is an isomorphism. ∎

This proves VIII.1.1: VIII.1.4 (with VIII.1.5 as its supporting kernel) is the full faithfulness, and VIII.1.6 is the
essential surjectivity. The pair gives `g^*` as an equivalence.

The slogan: **descent of `QCoh` is descent of `A`-modules along `A → A′`, reconstructed as the equaliser inside the
upstairs module.**

### VIII.1.7 — Descent of sections

<!-- source: VIII.1.7 -->

_This result says: global sections of a quasi-coherent module are themselves expressible as an equaliser of the sections
upstairs and on the two pull-backs._

**Corollary.** Let `g : S′ → S` be faithfully flat and quasi-compact. For every quasi-coherent module `G` on `S` with
inverse images `G′` on `S′` and `G″` on `S″ = S′ ×_S S′`, let `h : S″ → S` be the structural morphism. The diagram of
homomorphisms of `𝒪_S`-modules

```text
G  ⟶  g_*(G′)  ⇉  h_*(G″)
```

is exact.

**Proof.** Equivalent to VIII.1.2 applied to `F = 𝒪_S` and `G = G`: sections of `G` over an open `U ⊂ S` are
`Hom_{𝒪_U}(𝒪_U, G|_U)`, and the diagram above on `U` is exactly the VIII.1.2 diagram for that hom-set. ∎

### VIII.1.8 — Descent of quotient modules

<!-- source: VIII.1.8 -->

_This result says: a quasi-coherent quotient of `G` on `S` is the same data as a quasi-coherent quotient of `G′` on `S′`
whose two pull-backs to `S″` agree._

**Corollary.** With notation as in VIII.1.7, let `Quot(G)` denote the set of quasi-coherent quotient modules of `G`.
Then

```text
Quot(G)  ⟶  Quot(G′)  ⇉  Quot(G″)
```

is exact.

**Proof.** Inverse image is right exact, hence carries quotients to quotients. VIII.1.3 promotes this from objects to
quotient classes. The same statement holds, by symmetry, for submodules. ∎

### VIII.1.9 — Descent of closed subpreschemes

<!-- source: VIII.1.9 -->

_This result says: a closed subprescheme of `S` is the same data as a closed subprescheme of `S′` whose two pull-backs
to `S″` agree. This is the geometric face of VIII.1.8 with `G = 𝒪_S`._

**Corollary.** For a prescheme `X`, write `H(X)` for the set of closed subpreschemes of `X` (i.e. quasi-coherent
quotients of `𝒪_X`). Under the conditions of VIII.1.7, the diagram

```text
H(S)  ⟶  H(S′)  ⇉  H(S″)
```

is exact.

**Proof.** Apply VIII.1.8 to `G = 𝒪_S` — closed subpreschemes correspond to quasi-coherent ideals, which are kernels of
quotients of `𝒪_S`. ∎

### VIII.1.10–11 — Descent of finiteness properties

<!-- source: VIII.1.10, VIII.1.11 -->

_This result says: finiteness conditions on quasi-coherent modules (finite type, finite presentation, locally free of
finite type) descend along faithfully flat quasi-compact morphisms. The proof is a colimit argument using faithful
flatness to transfer finite generation back across the base change._

**Proposition (VIII.1.10).** Let `g : S′ → S` be faithfully flat and quasi-compact. For a quasi-coherent module `F` on
`S` with inverse image `F′` on `S′`, the property "`F` is of finite type" (respectively "of finite presentation",
respectively "locally free of finite type") holds for `F` iff it holds for `F′`.

The "only if" direction is automatic (base change preserves these finiteness properties). The substance is the "if"
direction, which reduces to the affine algebraic statement:

**Corollary (VIII.1.11).** Let `A` be a ring, `A′` a faithfully flat `A`-algebra, `M` an `A`-module, and
`M′ = M ⊗_A A′`. Then `M` is of finite type (respectively finite presentation, locally free of finite type) iff `M′` is.

**Proof of VIII.1.11.** *Finite type.* Write `M = colim_i M_i` over the finite-type submodules of `M`. Base change
commutes with filtered colimits, so `M′ = colim_i M_i′` with `M_i′ = M_i ⊗_A A′`. If `M′` is of finite type, the
identity of `M′` factors through some `M_i′`; that is, the inclusion `M_i′ → M′` is surjective. By faithful flatness
(which reflects surjectivity), the inclusion `M_i → M` is surjective, so `M_i = M` and `M` is of finite type.

*Finite presentation.* Once `M` is of finite type, pick a surjection `L → M → 0` with `L` free of finite type, and let
`R` be the kernel. Then `0 → R → L → M → 0` is exact; tensoring with `A′` gives `0 → R′ → L′ → M′ → 0` exact (`A′ / A`
is flat). If `M′` is of finite presentation, then `R′` is of finite type; the finite-type case above gives `R` of finite
type, hence `M` of finite presentation.

*Locally free of finite type.* In the noetherian case (which is what we use throughout the gentle series): locally free
of finite type is finite presentation + flat. Both descend along faithful flatness — finite presentation by the
preceding part, flatness because `M ⊗_A A′ = M′` is flat over `A′` and the local flatness criterion (file 26 IV.5)
transfers flatness back. ∎

### VIII.1.12 — Remark: restricted subcategories

<!-- source: VIII.1.12 -->

**Remark.** The conjunction of VIII.1.1 and VIII.1.10 has the following form. The fibred subcategory `ℱ' ⊂ ℱ` of
quasi-coherent modules of finite type (respectively finite presentation, respectively locally free of finite type,
respectively locally free of given rank `n`) is itself a fibred subcategory over `Sch`, and the statement of VIII.1.1
remains valid when one replaces `ℱ` by `ℱ'`. In short: each *property-restricted* sub-fibration of `QCoh` over `Sch` is
again equipped with effective descent along faithfully flat quasi-compact covers.

This will matter when we descend morphisms of schemes that come with extra structure (an ample line bundle, a
`G`-action, a polarisation) — the relevant fibred category is one of these restricted subcategories, and VIII.1.12 says
descent works there too.

## Closing: the algebraic shape of `QCoh`-descent

The substance of §VIII.1 is two reductions and two algebraic lemmas. The reductions move the problem from a general
faithfully flat quasi-compact `g : S′ → S` to a faithfully flat ring map `A → A′` between affine pieces. The two lemmas
— VIII.1.4 (the hom-equaliser) and VIII.1.6 (the reconstruction `N = { x : φ(x ⊗ 1) = 1 ⊗ x }`) — are the *only* places
where faithful flatness genuinely enters. Everything else in §VIII.1 is a consequence.

Two recurrent tricks. First, *exactness of an `A`-module sequence is detectable after faithfully flat base change*; both
VIII.1.5 and VIII.1.6 use it. Second, *any ring map with a section is a strict morphism of effective descent* (this is
the formal `[VIII.D]` content). Together they let one fix the base change `A → A′` once, then re-base-change along
`A → A′` a *second time*; the second base change converts `A → A′` into `A′ → A″ = A′ ⊗_A A′`, which now has the
multiplication section. The pattern is
`(\text{exactness after faithful flat base change}) ∘ (\text{descent along a morphism with a section})`, and it is the
algebraic engine of every descent statement in this exposé.

The slogan: **descent for `QCoh` is descent for `A`-modules over rings, recovered as equalisers via faithful flatness.**

The rest of Exposé VIII — affine descent (§VIII.2), descent of properties (§§VIII.3–4), descent of morphisms (§VIII.5),
the Zariski-Main-Theorem applications (§VIII.6), and the effectivity criteria for schemes (§VIII.7) — all reduce
ultimately to VIII.1.1, by recasting the geometric object as a quasi-coherent module (or quasi-coherent algebra)
equipped with extra structure. Section VIII.2, immediately next, is the simplest such recasting: an affine `S`-prescheme
is the same data as a quasi-coherent `𝒪_S`-algebra, so descent for affines is descent for algebra-modules.

### Forward pointers

- The faithfully flat descent of *affine* schemes (VIII.2.1) is file 41 §VIII.2.
- The faithfully flat descent of *morphisms* in `Sch` (VIII.5.2) and of *immersions, ampleness, quasi-affineness*
    (VIII.5.4–9) is file 42 §VIII.5.
- The faithfully flat descent of *finite étale coverings* — the precise content of \[`bourbaki-sem-190`\](appendix-
    black-boxes.md#bourbaki-sem-190) used in files 30, 31, 33 — is Exposé IX, deferred to a future pass of the gentle
    SGA project. With VIII.1.1 in hand, the IX statement reads: finite étale covers descend along faithfully flat
    quasi-compact morphisms.

#### Aside (Vistoli / Poonen analogy).

_Skip if Vistoli's FGA Explained or Poonen's Rational Points on Varieties is not part of your background._

Vistoli §4.1 proves VIII.1.1 in modern stack-theoretic notation: the fpqc topology is a Grothendieck topology, and
quasi-coherent sheaves form a *stack* with respect to it. Poonen §4.2 gives the same statement after a sheaf-gluing
motivation (Section 4.1.3 builds the cocycle viewpoint by analogy with the topological sheaf-gluing case). Either is a
good modern parallel to the proof above; both ultimately reduce to VIII.1.4 + VIII.1.6 in some guise. The Stacks Project
Tag 023A collects the abstract form (descent along fppf / fpqc covers for various fibred categories), and Tag 03O2 the
QCoh specialisation.

______________________________________________________________________

This closes §VIII.1 in the gentle reading. The faithfully flat descent of quasi-coherent modules is now in hand, which
means every later `QCoh`-flavoured descent statement of Exposé VIII (affine schemes, quasi-coherent algebras with
additional structure, descent of closed/open subschemes via VIII.1.9) is already a corollary.
