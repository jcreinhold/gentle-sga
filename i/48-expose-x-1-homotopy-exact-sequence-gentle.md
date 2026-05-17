# Rewritten Exposé X, section X.1 — the homotopy exact sequence for a proper separable morphism

<!-- source: X.1 -->

## What this file is about

The previous file proved a three-term sequence connecting the fundamental groups of a fibre, of the total space, and
of the base — but only under a strong hypothesis: the base had to be local and small in a specific sense. Real
families of geometric objects live over bases that are typically larger and more global.

This file removes the hypothesis, at the price of identifying the right replacement: a separability condition on the
family, demanding that fibres remain reduced under any further extension of scalars. With that condition the
three-term sequence holds over any reasonable base. Three early consequences follow: a product formula, invariance
under enlarging an algebraically closed ground field, and a slogan that families of coverings over a compact-like base
are rigid.

File 47 closed Exposé IX with the **fundamental exact sequence**

```text
1 → π₁(X̄_0, ā) → π₁(X, a) → π₁(S, b) → 1
```

valid for `X → S` proper surjective with geometrically connected fibres over an **artinian** base `S` (file 47, IX.6.1).
The artinian hypothesis was load-bearing: it made the Stein factorisation `X → S′ → S` *trivially* a single point in
each fibre, so that one could read off "`f_*𝒪_X = 𝒪_S` = `S′` connected" directly. Exposé X opens by asking what happens
when the base is allowed to be any locally noetherian prescheme. The first step is to identify the right hypothesis to
put in the place of "artinian." It is not "noetherian local" — at least not by itself — and it is not "geometrically
connected fibres" alone. The right hypothesis is **separability** of the morphism: `f` flat with geometrically reduced
fibres, plus the residue extensions of generic fibre points are separable. With separability in hand, the technical
content of Exposé IX *and* the Stein-factorisation upgrade of EGA III §7.8 combine to deliver the **homotopy exact
sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

for any proper separable `f : X → Y` with geometrically connected fibres, with `Y` locally noetherian.

Two qualifiers are important. The arrow at the left is **not** asserted to be injective; the algebraic analogue of the
topological `π₂(Y, b)` is unavailable in the algebraic-geometric setting at the level of SGA 1. And the right-hand "`e`"
is mandatory: surjectivity at `π₁(Y, b)` is the content of IX.3.4 (file 45) made *geometric* via Stein factorisation,
and there is no further term beyond it for our purposes here. The price of dropping the artinian-base hypothesis is the
loss of left-exactness; the gain is that the sequence holds over *any* base, with separability the controlling
hypothesis.

The rest of this file unpacks the proof and three early consequences: the **product formula** `π₁(X ×_k Y) ≃ π₁(X) ×
π₁(Y)` (X.1.7) — which was foreshadowed in file 46 IX.5.4 (pinching) and file 46 IX.5.8 (symmetric powers); the
**algebraic-closure invariance** `π₁(X) = π₁(X ⊗_k k′)` for `X` proper connected over an algebraically closed `k` and
`k′ ⊇ k` algebraically closed (X.1.8); and the slogan that **families of étale coverings of a proper scheme are
constant** (X.1.9). The exposé closes with the Lang–Serre counterexample: dropping properness in characteristic `p` is
fatal — the Artin–Schreier family `x^p − x = st` over the affine plane gives a non-constant family of étale coverings of
`𝔸¹` parametrised by another `𝔸¹` (X.1.10).

## §X.1.1 — Separable morphisms

<!-- source: X.1.1 -->

### Definition X.1.1 — separable morphism

<!-- source: X.1.1 -->

**Definition X.1.1.** A prescheme `X` over a field `k` is called **separable**, or **separable over `k`**, if for every
field extension `K / k`, the base change `X ⊗_k K` is **reduced**. A morphism of preschemes `f : X → Y` is called
**separable**, or `X` is said to be **separable over `Y`**, if (i) `f` is **flat**, and (ii) for every `y ∈ Y`, the
fibre `X_y = X ⊗_Y κ(y)` is separable over `κ(y)` in the sense just defined.

*This definition says:* a morphism is separable when it is flat and its geometric fibres remain reduced after any
further extension of the residue field. The vocabulary echoes the field-theoretic word "separable" — and not by
accident: when `X` is a `k`-scheme of finite type, separability of `X` over `k` is equivalent to the residue fields
`κ(x)` at generic points of irreducible components being **separable extensions** of `k`, which is the usual
field-theoretic condition.

#### Aside (perfect base fields).

*Skip if the equivalence "separable = reduced" over a perfect field is already familiar.*

If `k` is **perfect** — that is, every algebraic extension of `k` is separable — then `X / k` is separable if and only
if `X / k` is reduced. This is because in a perfect field there is no inseparability to detect after base extension: the
residue-field extensions `κ(x) / k` at generic points are automatically separable. In particular, over characteristic
zero or over the algebraic closure of any field, "separable" reduces to "reduced." Over an imperfect field of
characteristic `p` — for instance `𝔽_p(t)` — the gap between "reduced" and "separable" is real: the inseparable curve
`Spec(𝔽_p(t)[x] / (x^p − t))` is reduced (the polynomial is irreducible) but becomes non-reduced after base change to
`𝔽_p(t^{1/p})`, where it acquires a `p`-th-power factor.

______________________________________________________________________

### Sorites X.1.1.1 — base change preserves separability

<!-- source: X.1.1 -->

**Sorites.** Let `f : X → Y` be separable. For any base change `Y′ → Y`, the pullback `f′ : X ×_Y Y′ → Y′` is again
separable. Indeed, flatness is preserved by base change, and a fibre `(X ×_Y Y′)_{y′}` at `y′ ∈ Y′` is canonically
isomorphic to the fibre `X_{f′(y′)}` of `f` base-changed to `κ(y′)`, which remains separable over `κ(y′)` by the
field-theoretic stability of separability.

The composition statement is more delicate; under suitable finiteness hypotheses, the composite of two separable
morphisms is separable. We shall need only the following form, which is an immediate consequence of the definitions
together with (file 12) I.9.2 (étale base change preserves separability of fibres):

**Sorites (étale composition).** If `X` is separable over `Y` and `X′ → X` is étale, then `X′` is separable over `Y`.

This is exactly what we shall use repeatedly: separability "lives upstairs" under any further étale base change. The
proof is the one-sentence one: étale morphisms are flat, so the composite is flat; and étale base change preserves
reducedness of fibres (file 12, I.9.2).

> **Slogan.** *Separable = flat + geometrically reduced fibres. The hypothesis behaves well under base change and
> further étale extension; it is the right vocabulary for "a morphism whose fibres are honest geometric pieces, with no
> inseparable hidden structure."*

## §X.1.2 — Stein factorisation upgrade

<!-- source: X.1.2 -->

### Proposition X.1.2 — the Stein factorisation of a proper separable morphism is finite étale

<!-- source: X.1.2 -->

**Proposition X.1.2.** Let `f : X → Y` be a **proper** and **separable** morphism with `Y` locally noetherian. Consider
its **Stein factorisation** `X → Y′ → Y`, where `Y′ = Spec_Y(f_*𝒪_X)` is the relative spectrum of the structure
direct image; the canonical map `X → Y′` is proper with geometrically connected fibres satisfying `(X → Y′)_*𝒪_X =
𝒪_{Y′}`, and `Y′ → Y` is **finite**. Then `Y′ → Y` is **étale**: the Stein factorisation is finite étale.

*This result says:* under proper-separable hypotheses, the "factor out the connected-fibre content" decomposition `X
→ Y′ → Y` from EGA III §4.3 (file 47's [`ega-iii-stein-factorisation`](appendix-black-boxes.md#ega-iii-stein-factorisation))
is upgraded: the residual finite morphism `Y′ → Y` is no longer merely finite, it is finite **étale** — exactly the
class of "covering" morphisms whose theory we developed in Exposé V (files 30–33).

*Sketch.* The proof appears as the **EGA III 7.8.10(i) corollary**; the gentle outline along the SGA-source lines is
the following. One reduces to the case where `Y = Spec(A)` is the spectrum of a complete noetherian local ring. After a
suitable finite faithfully flat extension `A → A′` corresponding to a residue-field extension, one arranges that the
connected components of the fibre `X_y = X ⊗_A κ(A)` over the closed point are **geometrically** connected. This is
equivalent to saying that

```text
H⁰(X_y, 𝒪_{X_y}) = ∏_i k_i,
```

a product of fields equal to `k = κ(A)`. Supposing `X` is connected (one may, by working component by component), one
gets `H⁰(X_y, 𝒪_{X_y}) = k`, and the homomorphism `A → H⁰(X_y, 𝒪_{X_y})` is **surjective**. The Künneth-type
proper-base-change formula EGA III §7 then says that `f_*𝒪_X` is a free `A`-module `B` with `B / 𝔪B ≃
H⁰(X_y, 𝒪_{X_y}) = k`. Thus `B` is a noetherian local `A`-algebra, free over `A`, with residue extension `k → k`
the identity — that is, `B` is **finite locally free** of rank `1`, and étale-ness reduces to checking the discriminant.
Separability of `X / Y` is what guarantees that the discriminant is nonzero — that the residue extension is the
identity, not a non-trivial inseparable thickening. Combining: `B` is finite étale over `A`, hence `Y′ = Spec(B) → Y`
is finite étale.

The full proof appears in **EGA III §7.8.10(i)**, which we record as a new black-box row
[`ega-iii-7-stein-finite-etale`](appendix-black-boxes.md#ega-iii-7-stein-finite-etale).

> **Slogan.** *The Stein factorisation of a proper separable morphism is finite étale. The general Stein factorisation
> only gives a finite morphism with connected fibres; separability upgrades "finite" to "finite étale."*

This proposition is the workhorse of §X.1. It says that *separability* converts the "Stein factor" `Y′` from a vague
non-étale finite cover into an honest étale `Y`-cover, which we can think of in the categorical language of (file 33)
Galois categories without modification.

## §X.1.3 — Descent of étale coverings to the base

<!-- source: X.1.3 -->

### Theorem X.1.3 — descent of an étale `X`-covering to an étale `Y`-covering

<!-- source: X.1.3 -->

**Theorem X.1.3.** Let `f : X → Y` be **proper** and **separable** with `Y` locally noetherian and **connected**, and
suppose `f_*𝒪_X = 𝒪_Y`. (By X.1.2, this is equivalent to saying that the fibres of `f` are geometrically connected.) Let
`y ∈ Y`, let `κ(y)̄` be an algebraic closure of `κ(y)`, and let `X̄_y = X_y ⊗_{κ(y)} κ(y)̄` be the geometric fibre at `y`.

Let `X′` be a **connected** étale covering of `X`, and let `X̄′_y = X′ ×_X X̄_y` be the induced étale covering of `X̄_y`.
Then the following are equivalent:

1. There exists an étale covering `Y′ → Y` and an `X`-isomorphism `X′ ≃ X ×_Y Y′`;
1. `X̄′_y → X̄_y` admits a **section**.

*This result says:* descent of a connected étale covering `X′ → X` to an étale covering `Y′ → Y` is controlled by a
single discrete piece of data — whether the geometric fibre `X̄′_y` of the upstairs covering at any chosen `y ∈ Y`
admits a section. If yes, then `X′` does descend to `Y` (so `π₁(X) → π₁(Y)` factors through `π₁(X̄_y)`); if no, then
`X′` is "genuinely new on `X`," and contributes to the kernel of `π₁(X) → π₁(Y)`.

*Proof.* (1) ⟹ (2): if `X′ ≃ X ×_Y Y′` for some étale `Y′ → Y`, then `X̄′_y = X̄_y ×_Y Y′_y`. The geometric fibre `Y′_y =
Y′ ⊗_Y κ(y)̄` is a finite disjoint union `⨿_i Spec(L_i)` of separable extensions of `κ(y)̄`. Since `κ(y)̄` is
algebraically closed, each `L_i = κ(y)̄`, so `Y′_y` is a finite disjoint union of copies of `Spec(κ(y)̄)`. Choose any
one of these copies; the corresponding `Spec(κ(y)̄) → Y′_y` pulls back to a section `X̄_y → X̄′_y`.

(2) ⟹ (1): suppose a section `σ : X̄_y → X̄′_y` is given. We construct `Y′` as the Stein factorisation of the composite
`X′ → X → Y`. Concretely, set

```text
h : X′ → Y,    h = f ∘ (X′ → X),    Y′ := Spec_Y(h_*𝒪_{X′}).
```

The composite `X′ → Y′ → Y` is the Stein factorisation of `h`; the morphism `X′ → Y′` is proper with geometrically
connected fibres, and `Y′ → Y` is finite. Since `X′` is connected and `h_*𝒪_{X′}` is therefore a local-on-`Y` algebra
with one connected component over each point, `Y′ → Y` is the **étale covering** of `Y` controlled by `f` and `X′`.
That `Y′ → Y` is *étale* follows from X.1.2 applied to `h = f ∘ (X′ → X)`: this morphism is proper (composite of proper)
and separable (composite of proper separable with étale, by the X.1.1 sorites). Hence the Stein factor `Y′ → Y` is
étale by X.1.2.

It remains to identify `X′` with `X ×_Y Y′`. The canonical comparison map `X′ → X ×_Y Y′` is a morphism of étale
`X`-coverings (étale because both `X → Y` and `Y′ → Y` are, by file 12, I.4.8), so it is étale. It is between
**connected** schemes: `X′` is connected by hypothesis; `X ×_Y Y′` is connected because `Y′ → Y` has connected fibres
(`Y′` is connected as the image of the connected `X′`) and `X → Y` has connected fibres ((file 45) IX.3.4 + the
strict-epimorphism (file 33) V.6.9(iii)). So the comparison `X′ → X ×_Y Y′` is an étale morphism between connected
schemes, and to show it is an isomorphism it suffices to show that the projection degree at *one* point of `X ×_Y Y′`
equals 1.

This is where the section `σ` comes in. The hypothesis gives a point `x̄ ∈ X̄_y` over which `X̄′_y → X̄_y` has a
distinguished section, hence has projection degree exactly 1 at `x̄`. The geometric fibre `(X ×_Y Y′)_y → X̄_y`, after
extension to `κ(y)̄`, picks out the chosen `Y′`-component of `Y′_y`, so the projection degree of `X̄′_y → (X ×_Y Y′)_y`
at `x̄` is again 1 — and projection degree is constant in connected components, so it is 1 everywhere. This proves
`X′ → X ×_Y Y′` is an isomorphism.

> **Slogan.** *Descent of a connected étale covering of `X` to the base `Y` is detected by a single section over the
> geometric fibre. The descended `Y′` is the Stein factorisation of `X′ → Y`; X.1.2 is what makes it étale.*

The proof made critical use of X.1.2 (Stein factor is étale), of IX.3.4 (file 45; geometrically connected fibres ⇒
fully faithful descent on `Sch`), and of the V.6.9 dictionary (file 33; surjective on objects = epi on `π₁`). The proof
also used a fact about étale morphisms between connected schemes: an étale morphism `φ : A → B` of connected schemes is
an isomorphism iff its projection degree at one (any) point of `B` is 1 (file 11, I.5.5 corollary). This is the
"covering-space" rigidity that the étale machinery was built to detect.

## §X.1.4 — The homotopy exact sequence

<!-- source: X.1.4 -->

### Corollary X.1.4 — the homotopy exact sequence on `π₁`

<!-- source: X.1.4 -->

With `f : X → Y` proper and separable, `Y` locally noetherian and connected, `f_*𝒪_X = 𝒪_Y` (equivalently, the
geometric fibres are connected), choose a point `y ∈ Y`, an algebraic closure `κ(y)̄`, and a geometric point
`ā ∈ X̄_y`. Let `a` and `b` be its images in `X` and `Y`.

**Corollary X.1.4.** The sequence of group homomorphisms

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

is **exact** at `π₁(X, a)` and at `π₁(Y, b)`.

*This result says:* under proper-separable + geometrically-connected-fibres, the canonical map `π₁(X) → π₁(Y)` is
**surjective**, and the inverse image (in `π₁(X)`) of the trivial subgroup of `π₁(Y)` is the closed normal subgroup
generated by the image of `π₁(X̄_y) → π₁(X)`. Categorically: the finite étale coverings of `Y` are exactly the finite
étale coverings of `X` that become trivial after base change to a geometric fibre.

*Proof.* This is the rewrite of X.1.3 into the language of fundamental groups, via the V.6 dictionary (file 33). By
(file 33) V.6.9(iii) and V.6.11, a continuous homomorphism `φ : π₁(X) → π₁(Y)` is **surjective** if and only if the
corresponding pullback functor on finite étale categories `𝒞(Y) → 𝒞(X)` (taking `Y′ ↦ X ×_Y Y′`) is **fully faithful
with image closed under disjoint union and connected quotients**. By IX.3.4 (file 45), this pullback functor *is* fully
faithful under our hypotheses (geometrically connected fibres). The image is closed under disjoint union and
quotients trivially. So `π₁(X, a) → π₁(Y, b)` is surjective; this gives exactness at `π₁(Y, b)` and the final `e`.

For exactness at `π₁(X, a)`: this is the V.6.9(ii)-type statement that the kernel of `π₁(X) → π₁(Y)` (a closed normal
subgroup) is the closed normal subgroup generated by the image of `π₁(X̄_y) → π₁(X)`. Translated through the dictionary,
this says: a connected étale cover `X′ → X` becomes trivial after base change to `Y` — i.e. comes from an étale cover
`Y′ → Y` — iff its geometric fibre `X̄′_y` admits a section. That is exactly X.1.3.

> **Slogan.** *Proper separable + geometrically connected fibres ⇒ `π₁(X) → π₁(Y)` is surjective with kernel the
> closed normal subgroup generated by `π₁(X̄_y)`.*

The exact sequence has no left term `1 → π₁(X̄_y) → …`; the leftmost arrow is **not** asserted to be injective. The
algebraic-topology analogue would assert that the kernel of `π₁(X̄_y) → π₁(X)` is the image of `π₂(Y, b)`, but `π₂`
of a scheme is not (in any standard way) part of SGA 1's vocabulary.

## §X.1.5 — Why the proof works: the role of formal geometry

<!-- source: X.1.5 -->

### Remark X.1.5 — IX.1.10 is the load-bearing input

<!-- source: X.1.5 -->

The proof of X.1.3 — and hence of X.1.4 — uses X.1.2 in an essential way. X.1.2, in turn, uses the **first comparison
theorem in algebraic-formal geometry** (i.e. (file 44) IX.1.10, which we cite via
[`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence) and the proper-base-change formula of
EGA III §7.8). This is what we record as the new appendix row
[`ega-iii-7-formal-functions`](appendix-black-boxes.md#ega-iii-7-formal-functions). Without it, separability of `f`
would not suffice to upgrade the Stein factorisation to étale.

By contrast, the descent theory of Exposé IX is used only via **IX.3.4** (file 45) — the assertion that geometrically
connected fibres of `f` imply the descent functor `g^* : \mathrm{ét}(Y) → \mathrm{ét}(X)` is fully faithful. In the
*proper* case under consideration, IX.3.4 admits a particularly simple direct proof, which we record here for
completeness.

#### Aside (direct proof of IX.3.4 in the proper case).

*Skip if you are comfortable with the file 45 derivation; this is a one-paragraph alternative.*

Let `Y′ → Y` be étale and suppose `X′ = X ×_Y Y′` is the disjoint union of two non-empty open subsets `X′_1` and `X′_2`.
We show the same is true of `Y′`. Locally on `Y` we have `Y′ = Spec(𝒜)` for a quasi-coherent `𝒪_Y`-algebra `𝒜`, hence
`X′ = Spec(𝒜 ⊗_{𝒪_Y} 𝒪_X) = Spec(𝒜 ⊗_𝓞 𝒪_X)`. The decomposition `X′ = X′_1 ⨿ X′_2` corresponds to a decomposition of
`𝒜 ⊗ 𝒪_X` into two non-zero `𝒪_X`-algebras `𝒜 ⊗ 𝒪_X = 𝓑_1 × 𝓑_2`. Applying `f_*`, since `f_*𝒪_X = 𝒪_Y`, we get
`𝒜 = f_*(𝓑_1) × f_*(𝓑_2)` — a decomposition of `𝒜` into two `𝒪_Y`-algebras. To conclude that these are *non-zero*, note
that their unit sections are non-zero (they are the unit sections of the original `𝓑_i`, which are non-zero by
hypothesis). So `Y′ = Spec(𝒜) = Spec(f_*𝓑_1) ⨿ Spec(f_*𝓑_2)` is a non-trivial decomposition. This proves IX.3.4 in the
proper case directly. □

______________________________________________________________________

## §X.1.6 — Extension to the seven-term sequence on `π₀`

<!-- source: X.1.6 -->

### Remark X.1.6 — the seven-term homotopy sequence

<!-- source: X.I.6 -->

Suppose `f : X → Y` is proper and separable as in X.1.4, but now drop the hypothesis `f_*𝒪_X = 𝒪_Y`. The Stein
factorisation `f : X → Y′ → Y` then has `Y′ → Y` an étale (in general non-trivial) covering of `Y`, pointed above `b`
by the image `b′ ∈ Y′` of the geometric point `a ∈ X`. Applying X.1.4 to the canonical morphism `X → Y′` and supposing
`f` surjective, the exact sequence X.1.4 extends to the **seven-term sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → π₀(X̄_y, ā) → π₀(X, a) → π₀(Y, b) → e,
```

analogous to the **long exact sequence of homotopy groups of a fibration** in algebraic topology. Here `π₀(Z, z)` denotes
the pointed set of connected components of `Z` at `z` — the "discrete homotopy `0`-th group."

*This result says:* even when `f_*𝒪_X ≠ 𝒪_Y`, the failure is recorded by the connected-component structure of the
geometric fibre via the Stein factorisation, and the resulting seven-term sequence is the analogue of the topological
homotopy LES (low-degree) of a fibration.

The honest qualifier: in topology, the kernel of `π₁(\mathrm{fibre}) → π₁(\mathrm{total})` is the image of
`π₂(\mathrm{base})`. In algebraic geometry, the analogue of `π₂` is not (in any received way) part of SGA 1's
vocabulary; results in this direction would require a "higher homotopy" theory of schemes, which Grothendieck flags as
desirable but unavailable at the time of writing. (Modern work via étale homotopy theory — Artin–Mazur, Friedlander —
addresses this; we do not pursue it here.)

> **Slogan.** *The proper-separable π₁ exact sequence extends to a seven-term `π₁ → π₁ → π₁ → π₀ → π₀ → π₀ → e`
> sequence analogous to the homotopy LES of a fibration. Higher terms would require a higher-homotopy theory of
> schemes, which is not part of SGA 1.*

## §X.1.7 — The product formula

<!-- source: X.1.7 -->

### Corollary X.1.7 — `π₁` of a product

<!-- source: X.1.7 -->

**Corollary X.1.7.** Let `k` be an algebraically closed field, and let `X` and `Y` be two connected preschemes over `k`,
with `X` **proper** over `k` and `Y` locally noetherian. Let `a` be a geometric point of `X` and `b` a geometric point
of `Y`, both with values in the same algebraically closed extension `K / k`. Consider the geometric point `c = (a, b)`
of `X ×_k Y`. Then the canonical homomorphism

```text
π₁(X ×_k Y, c) → π₁(X, a) × π₁(Y, b),
```

induced by the two projections, is an **isomorphism**.

*This result says:* over an algebraically closed `k`, the étale fundamental group is **multiplicative under products
with a proper factor**: `π₁` of `X ×_k Y` is the direct product of the individual `π₁`'s, exactly as in topology for
the analogous topological case `π₁(X × Y) = π₁(X) × π₁(Y)`.

This formula was foreshadowed in file 46 (IX.5.4 pinching, IX.5.5 nodal-cubic, IX.5.8 symmetric powers); it is the
formal underpinning of computations like `π₁(Sym^n X) = π₁(X)^{ab}` (file 46, IX.5.8).

*Proof.* First suppose `K = k` (i.e. `a` and `b` are `k`-rational). Set `Z = X ×_k Y`. Apply X.1.4 to the projection
`f : Z → Y` and the geometric point `b ∈ Y`. Two preliminary observations:

- After replacing `X` by `X_{red}` (which does not change `π₁(X, a)`, since the reduction is a universal homeomorphism
  and étale coverings are invariant under such by IX.4.10 (file 45)), we may assume `X` is **reduced**, hence
  **separable** over `k` (recall: over an algebraically closed `k`, separable = reduced). Therefore the projection
  `Z = X ×_k Y → Y` is separable: it is the base change of the separable `X → \mathrm{Spec}(k)` along `Y → \mathrm{Spec}(k)`.
- The geometric fibre `Z_b` of `Z → Y` over the algebraically closed `b ∈ Y` is canonically `X ⊗_k κ(b) = X` (the
  hypothesis `K = k` gives `κ(b) = k`). So `π₁(Z̄_b) = π₁(X, a)`.

Hence X.1.4 applied to `Z → Y` yields the exact sequence

```text
π₁(X, a) → π₁(Z, c) → π₁(Y, b) → e.
```

The composite `X → Z → X` is the identity (where the first arrow is `id_X × b : X → X ×_k Y = Z` and the second is the
projection to `X`). This shows that `π₁(X, a) → π₁(Z, c)` is **injective**: any element of its kernel must come from an
element of `π₁(Z, c)` that is killed by the projection to `X`, but the composite is the identity, so the kernel is
trivial.

Together: we have an exact sequence

```text
e → π₁(X, a) → π₁(Z, c) → π₁(Y, b) → e.
```

On the other hand, there is the canonical exact sequence

```text
e → π₁(X, a) → π₁(X, a) × π₁(Y, b) → π₁(Y, b) → e
```

with the canonical inclusion and projection. The canonical homomorphism `π₁(Z, c) → π₁(X, a) × π₁(Y, b)` is a
homomorphism of short exact sequences with identity maps on the two end terms. Commutativity of the diagram is
immediate. By the five lemma, the middle map is an isomorphism. This proves X.1.7 in the case `K = k`.

When `K ≠ k`, we have only an isomorphism `π₁(Z, c) → π₁(X ⊗_k K, a) × π₁(Y, b)`. Reducing to the previous case requires
the next corollary:

> **Slogan.** *Over an algebraically closed `k`, `π₁` is multiplicative under products with a proper factor: `π₁(X
> ×_k Y) = π₁(X) × π₁(Y)`. The "with a proper factor" qualifier is sharp; X.1.10 shows that dropping it leads to
> non-product behaviour.*

## §X.1.8 — Algebraic-closure invariance for `π₁`

<!-- source: X.1.8 -->

### Corollary X.1.8 — `π₁` of a proper scheme over an algebraically closed field is invariant under further algebraically closed extension

<!-- source: X.1.8 -->

**Corollary X.1.8.** Let `X` be a **proper connected** scheme over an algebraically closed field `k`, let `k′ / k` be
an extension with `k′` again algebraically closed, let `a′` be a geometric point of `X ⊗_k k′`, and let `a` be its
image in `X`. Then the canonical homomorphism

```text
π₁(X ⊗_k k′, a′) → π₁(X, a)
```

is an **isomorphism**.

*This result says:* the étale fundamental group of a proper scheme over an algebraically closed field does not change
under further extension of the algebraically closed base field. In particular, computing `π₁(X)` is "absolute" — once
`k` is algebraically closed, no further base extension can refine the answer.

*Proof.* **Surjectivity.** Saying `π₁(X ⊗_k k′, a′) → π₁(X, a)` is surjective is the assertion: for every connected
étale covering `X′ → X`, the pullback `X′ ⊗_k k′ → X ⊗_k k′` is again connected. This follows from `k` algebraically
closed: a connected algebraic extension of an algebraically closed field is the algebraically closed field itself.
Equivalently, this is a special case of (file 45) IX.3.4 with `g : X ⊗_k k′ → X` (note: properness is not used yet).

**Injectivity.** This is the substantive content. It says: **every étale covering of `X ⊗_k k′` is isomorphic to the
pullback of an étale covering of `X`**.

Let `X′' → X ⊗_k k′` be an étale covering. By a standard "sorital" finiteness argument (étale coverings are finite type
over the base), one can find a finite-type sub-`k`-algebra `A ⊂ k′` and an étale covering `X′_A → X ⊗_k A` whose
pullback to `X ⊗_k k′` is `X′`. Let `Y = \mathrm{Spec}(A)` — an integral `k`-scheme of finite type, hence having
`k`-rational points (since `k` is algebraically closed and finite-type integral implies non-empty `k`-points by
Hilbert's Nullstellensatz). Applying X.1.7 to `π₁(X × Y)` at a `k`-rational point `(a, b) ∈ X × Y`: every connected
étale covering of `X × Y` is the quotient of `X̃ × Ỹ` by a subgroup of `G × G′`, where `X̃ → X` is a Galois étale
cover with group `G`, `Ỹ → Y` is Galois with group `G′`, and the quotient subgroup is some `H ⊂ G × G′`.

Following the same reasoning on `X × Y′`, where `Y′ = \mathrm{Spec}(L)` for `L` the function field of `Y` (a finite
separable extension of which contains `k′`-algebraically-closed-data), one finds that the original `X′ → X ⊗_k L`
becomes isomorphic to a pullback `X₁′ ⊗_k L′` (for some finite separable extension `L′ ⊃ L` and `X₁′ → X` étale) — and
this `L′` may be taken in `k′` since `k′` is algebraically closed. Pulling back along `L′ → k′`, we conclude
`X′ ≃ X₁′ ⊗_k k′`. Injectivity proved. □

> **Slogan.** *`π₁` of a proper connected scheme over an algebraically closed field is invariant under further
> algebraically closed extension. The proof reduces "extend the base field" to "find a `k`-rational point in the
> parameter space" via Hilbert's Nullstellensatz and the X.1.7 product formula.*

The cycle X.1.7 ⟹ X.1.8 (and X.1.8 closes the proof of X.1.7 by reducing `K = k` ⟹ general `K`) closes off the
product/base-change story for `π₁` of a proper scheme.

## §X.1.9 — Families of étale coverings of a proper scheme are constant

<!-- source: X.1.9 -->

### Corollary X.1.9 — constant families

<!-- source: X.1.9 -->

**Corollary X.1.9.** Let `k` be an algebraically closed field, let `X` and `Y` be two locally noetherian preschemes over
`k`, and let `Z = X ×_k Y`. Let `Z′ → Z` be an étale covering. For every `k`-rational point `y ∈ Y(k)`, let
`i_y : \mathrm{Spec}(k) → Y` be the associated point and let `j_y = id_X ×_k i_y : X → Z` be the inclusion of the
fibre. Let `X_y′ = X ×_Z Z′ = (j_y)^* Z′` be the induced étale covering of `X` from `j_y`.

Assume `Y` is **connected** and that **one** of `X`, `Y` is **proper** over `k`. Then the coverings `X_y′` of `X` are
**all isomorphic**.

*This result says:* a family of étale coverings of `X` parametrised by a connected `Y` — i.e. a single étale covering
of `X × Y` whose fibre at each `y` is the corresponding member of the family — is **constant** when one of `X`, `Y` is
proper over `k`. The "constant family" intuition is: there are no continuous variations in étale-covering topology over
a proper base.

*Proof.* By X.1.7, every connected étale covering of `X ×_k Y` is a quotient of `X̃ ×_k Ỹ` by a subgroup of `G × G′`,
where `X̃ → X` and `Ỹ → Y` are Galois étale coverings with groups `G` and `G′`. The fibre at a `k`-rational `y ∈ Y(k)`
is then a quotient of `X̃ ×_k \mathrm{Spec}(k)` by a subgroup of `G × G′_y`, where `G′_y` is the stabiliser of `y` in
`G′`. But since `Y` is connected, the action of `G′` on `Y(k)` is transitive (assuming `Ỹ → Y` is Galois étale connected
and Galois acts transitively on geometric fibres), so all stabilisers `G′_y` are conjugate in `G′`. Hence all
quotients `(X̃ × \mathrm{Spec}(k)) / (G × G′_y)` are isomorphic as étale `X`-coverings. This is X.1.9. □

> **Slogan.** *Étale coverings of `X`, parametrised by a connected proper `Y` (or with `X` proper itself), are constant:
> they don't move with `y`. This is the algebraic counterpart of "constancy of monodromy along a proper-base
> deformation" in classical algebraic geometry.*

## §X.1.10 — The Lang–Serre counterexample

<!-- source: X.1.10 -->

### Remarks X.1.10 — properness cannot be dropped

<!-- source: X.1.10 -->

**Remark X.1.10.** Corollaries X.1.7, X.1.8, and X.1.9 are due to **Lang and Serre** ([X.2]: S. Lang and J.-P. Serre,
"Sur les revêtements non ramifiés des variétés algébriques," *Amer. J. Math.* **79** (1957), 319–330) in the case of
normal algebraic schemes. Their work was the **initial motivation** for Grothendieck's theory of the étale fundamental
group developed in SGA 1.

These results become **false** if the properness hypothesis is dropped, at least in characteristic `p > 0`. The
canonical counterexample is the **Artin–Schreier family**.

**Example.** Take `k` algebraically closed of characteristic `p > 0`. Let `X = \mathrm{Spec}(k[t])` be the affine line
and `Y = \mathrm{Spec}(k[s])` another affine line. Consider the family of `k[t, s]`-algebras

```text
B_s = k[t, s][x] / (x^p − x − s t).
```

For each fixed value of `s` (regarded as a parameter), the family member `B_s|_{s = s₀}` for `s₀ ∈ k`, `s₀ ≠ 0`, defines
an étale covering `X_{s₀}′ → X`: it is a non-trivial Artin–Schreier `ℤ/p`-cover of `𝔸¹_k` ramified only at `∞`. Two such
coverings `X_{s₀}′` and `X_{s₁}′`, for `s₀ ≠ s₁` (both non-zero), are **non-isomorphic** as étale `X`-coverings — this
is the classical fact that Artin–Schreier extensions of `k[t]` corresponding to different choices of `s ∈ k^×` give
non-isomorphic ramified extensions of `k(t)` at `∞`.

Hence: the étale `(X × Y)`-covering `\mathrm{Spec}(B) → \mathrm{Spec}(k[t, s])` (where `B = k[t, s][x] / (x^p − x − st)`)
has all-non-trivial fibres over `Y$, and pairwise distinct fibres over distinct `s₀ ∈ Y(k)$. This contradicts X.1.9, so
*a fortiori* X.1.7 fails over `X × Y` here.

Similarly, treating `s$ as a transcendental element in an algebraically closed extension `K / k$, one obtains an étale
covering `X′ → X ⊗_k K` that does **not** come from any étale covering of `X` — contradicting X.1.8.

> **Slogan.** *In characteristic `p$, the affine line over `k$ admits a non-constant family of étale coverings of itself
> parametrised by another affine line — the Artin–Schreier family `x^p − x − st`. Properness is the hypothesis that
> rules out such families and makes X.1.7–9 hold.*

The Artin–Schreier family illustrates the **structural** reason why properness matters here: in characteristic `p$,
inseparable phenomena give rise to non-trivial étale coverings of affine schemes that don't extend to coverings of the
projective compactification. Properness "boxes in" the inseparability by forcing the cover to extend over the boundary,
which then forces constancy in the family.

This counterexample also closes the loop on X.2.5 (file 49): dropping the *separability* hypothesis on `f$ in X.1.4
or X.2.4 produces families where the specialisation `π₁` morphism fails to be surjective. The Lang–Serre Artin–Schreier
phenomenon is the same "wild" inseparable behaviour that makes characteristic-`p$ algebraic geometry strictly richer
than characteristic-0 algebraic geometry.

______________________________________________________________________

## Closing pointer: X.1 in context

This file gave the **homotopy exact sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

for `X → Y` proper separable with geometrically connected fibres (X.1.4), the **product formula** `π₁(X ×_k Y) ≃
π₁(X) × π₁(Y)` for `X` proper connected over algebraically closed `k$ (X.1.7), and the **algebraic-closure invariance**
of `π₁(X)$ under further algebraically closed extension (X.1.8). The qualifier "the leftmost map is not asserted to be
injective" is structural: the algebraic-geometric analogue of `π₂$ of the base is not in our vocabulary at the level of
SGA 1.

File 49 continues with X.2.1–X.2.5: under a **complete-local** base hypothesis the leftmost map *is* in fact injective
((file 47) IX.6.1 supplies this), and the exact sequence becomes left-exact too — yielding the canonical
**specialisation morphism** `\mathrm{sp} : π₁(X̄_{y₁}) → π₁(X̄_{y₀})` for a specialisation `y_0 ⤳ y_1` in `Y$. The
specialisation map is **surjective** under proper separable hypotheses (upper semicontinuity of fibre `π₁$), but it can
drop strictly along a non-trivial specialisation — even in characteristic 0, even for proper *separable* families —
and the canonical counterexamples (degenerate elliptic curves, M. Artin's unpublished obstruction to fibre `π₁$ as a
local system) are recorded faithfully there.

File 50 carries the story through to the **transcendental method**: in characteristic 0 (and lifted to characteristic
`p` via Witt vectors plus the X.2.3 surjectivity), the fundamental group of a proper smooth curve of genus `g$ has a
clean topological presentation, with `2g$ generators and one commutator relation. File 51 closes Exposé X by proving
the **continuity theorem** for proper smooth morphisms: the specialisation map is an isomorphism on prime-to-`p$
quotients, with **Abhyankar's lemma** as the technical input.
