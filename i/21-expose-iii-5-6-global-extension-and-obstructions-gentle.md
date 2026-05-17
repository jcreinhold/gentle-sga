# Exposé III, sections 5–6: global infinitesimal extension and cohomological obstructions (gentle)

## What this file is about

The previous file gave a local answer. On a small enough patch, a smooth shape over a point thickens to a smooth shape
one infinitesimal layer further out, and a map into such a shape extends one layer further. Neither answer is unique.
Different patches may produce different local extensions, and on overlaps the extensions may disagree.

The next question asks whether the local extensions paste together into a single answer over the whole space. They do
when a certain bookkeeping group, attached to the space and to a sheaf that measures direction along the smooth shape,
has only its zero element. Otherwise that group contains a single element that is exactly the obstruction to gluing, and
the obstruction vanishes precisely when a global answer exists. The file works out which group does which job for which
question.

Section III.4 (file 20) said: a smooth scheme over an infinitesimal thickening lifts smoothly **locally**. The local
lift is non-canonical (III.4.3, file 20), so gluing local lifts globally requires cohomological accounting. This file
does the accounting.

**Section III.5** handles the simpler question — extending a given **morphism** between two given schemes — and finds
the obstruction in `H¹(Y₀, 𝒢)` for a sheaf `𝒢` built from `Ω¹` and the square-zero ideal. **Section III.6** handles the
harder question — extending a **scheme** itself — and finds the obstruction in `H²(X₀, 𝒢)` for a sheaf `𝒢` built from
the **tangent sheaf** `𝔤_{X₀/S₀}` and a graded piece of the ideal `𝓘`. The H² calculation is Grothendieck's "silly
cocycle calculation," done because the more conceptual treatment in Giraud's _Cohomologie non abélienne_ was, at the
time, unwritten.

The cohomological machinery (`H¹` as torsors, `H²` as gluing obstructions, Leray's acyclic-cover theorem, the tangent
sheaf `𝔤_{X/S}`) is in **file 17**. Formal schemes and the algebraization theorem are in **file 18**. The local lifting
result (III.4.1) is in **file 20**. We freely cite all three.

The slogan that runs through:

> **Local lifts always exist; global lifts have a cohomological obstruction.** For a morphism: H¹ is the obstruction;
> vanishing H¹ guarantees a global lift, and the set of lifts is a torsor under H⁰ of the same coefficient sheaf. For a
> smooth scheme: H² is the obstruction; vanishing H² guarantees a global smooth lift, and the set of isomorphism classes
> of lifts is a torsor under H¹ of the tangent sheaf.

## III.5 Global infinitesimal extension of morphisms

<!-- source: III.5 -->

### Setup: formally principal homogeneous sheaves

We recall from file 17 the basic objects. Let `T` be a topological space and `𝒢` a sheaf of (commutative) groups on `T`.
A sheaf of sets `𝒫` on `T` is **formally principal homogeneous** under `𝒢` if the natural map `𝒢 × 𝒫 → 𝒫 × 𝒫` (sending
`(g, p) ↦ (p · g, p)`) is an isomorphism. Equivalently: on each open `U`, the set `𝒫(U)` is **either empty or a
principal homogeneous space** under `𝒢(U)` in the usual sense.

`𝒫` is a **principal homogeneous sheaf** under `𝒢` (or a **torsor under `𝒢`**) if in addition all stalks `𝒫_x` are
nonempty; equivalently, `𝒫` is locally trivial as a `𝒢`-set. The set of isomorphism classes of torsors under `𝒢` is in
natural bijection with `H¹(T, 𝒢)` — this is the central classifying theorem of file 17 (Giraud's classification,
appendix row `giraud-torsor`).

For a torsor `𝒫`, the cohomology class `c(𝒫) ∈ H¹(T, 𝒢)` vanishes iff `𝒫` is trivial (i.e., admits a global section).
For a formally principal homogeneous sheaf `𝒫` that is not yet known to have a global section, the cohomology class
vanishes iff the sheaf has **enough** sections — globally, on every open of a trivializing cover.

This is the language of §III.5. The setup will be:

- A morphism `g₀ : Y₀ → X` over `S` and a square-zero ideal `𝒥 ⊂ 𝒪_Y` defining a closed sub-prescheme `Y₀ ⊂ Y`.
- The sheaf `𝒫(g₀)` on `Y` whose sections over an open `U ⊂ Y` are the morphisms `g : U → X` over `S` that extend
    `g₀|_{U ∩ Y₀}`.
- The claim: `𝒫(g₀)` is formally principal homogeneous under a specific sheaf of groups `𝒢` built from `Ω¹` and `𝒥`.

### Proposition: `𝒫(g₀)` is formally principal homogeneous

<!-- source: III.5.1 -->

_This proposition says: the sheaf of extensions of `g₀` along a square-zero thickening is, naturally, a formally
principal homogeneous sheaf under a sheaf of derivation-valued maps. The proof is the construction of the bijection
between the two — a local diagonal / first-order-neighborhood calculation._

**Proposition III.5.1.** *Let `S` be a prescheme, `X` and `Y` preschemes over `S`, and `Y₀ ⊂ Y` a closed sub-prescheme
defined by a sheaf of ideals `𝒥` on `Y` of **square zero**. Let `g₀ : Y₀ → X` be an `S`-morphism, and let `𝒫(g₀)` be the
sheaf on `Y` whose sections on an open `U ⊂ Y` are the extensions `g : U → X` of `g₀|_{U ∩ Y*0}`to an`S`-morphism `g`.
Then `𝒫(g₀)` is, naturally, a **formally principal homogeneous** sheaf under the commutative sheaf of groups*

```text
𝒢 := ℋ𝓂_{𝒪_{Y₀}}(g₀^* (Ω¹_{X/S}), 𝒥).
```

**Proof construction.** We construct the action `𝒫(U) × 𝒢(U) → 𝒫(U)` by giving, for each fixed `g ∈ 𝒫(U)`, a canonical
bijection `𝒢(U) → 𝒫(U)`. The verifications that this assembles into a sheaf-of-sets action and that the action is
principal are mechanical and we omit them; see the source.

Fix `g ∈ 𝒫(Y)` (we may assume `U = Y` for clarity). We seek a canonical bijection

```text
ℋ𝓂_{𝒪_{Y₀}}(g₀^* (Ω¹_{X/S}), 𝒥) ⟶ 𝒫(Y),
```

where `𝒫(Y)` is the set of `S`-morphisms `g' : Y → X` inducing the same `g₀ : Y₀ → X` as `g`.

Giving such a `g'` is equivalent to giving an `S`-morphism `h : Y → X ×_S X` such that:

- `pr₁ ∘ h = g` (the first projection of `h` is the given `g`),
- `h ∘ i = (g₀, g₀) : Y₀ → X ×_S X` (where `i : Y₀ → Y` is the closed immersion).

Since `(g₀, g₀)` factors through the diagonal `Δ_{X/S} : X → X ×_S X` (it is the constant pair), and since `Y` lies in
the **first-order infinitesimal neighborhood of `Y₀`** (`𝒥² = 0`), the desired `h` necessarily factors uniquely through
the **first-order infinitesimal neighborhood `X^{(1)}` of the diagonal** in `X ×_S X`.

**Recall from file 03.** This first-order neighborhood `X^{(1)}` is, as an `X`-scheme via `pr₁`, the spectrum of the
sheaf of `𝒪_X`-algebras

```text
𝒪_X ⊕ Ω¹_{X/S}
```

with `Ω¹_{X/S}` regarded as a square-zero ideal (this is the "square-zero extension by `Ω¹`", file 03, "What `Ω¹`
represents abstractly"). The diagonal `X → X^{(1)}` corresponds to the canonical augmentation that kills `Ω¹`.

So, putting `Y' := X^{(1)} ×_X Y` (via `g`) and `Y'₀ := Y' ×_Y Y₀`, the desired `h` are in bijective correspondence with
**sections `u` of `Y' → Y` extending the canonical section `u₀` of `Y'₀ → Y₀`** (which is the augmentation killing `Ω¹`
when restricted).

We identify `Y'` with `Spec_Y(𝒜)` for the sheaf of `𝒪_Y`-algebras

```text
𝒜 := g^*(𝒪_X ⊕ Ω¹_{X/S}) = 𝒪_Y ⊕ g^*(Ω¹_{X/S}),
```

and `Y'₀` with `Spec_{Y₀}(𝒜₀)` for `𝒜₀ := 𝒜 ⊗_{𝒪_Y} 𝒪_{Y₀} = 𝒪_{Y₀} ⊕ g₀^*(Ω¹_{X/S})`. The canonical section `u₀` is the
augmentation of `𝒜₀`.

So `𝒫(Y)` identifies with the set of `𝒪_Y`-algebra maps `𝒜 → 𝒪_Y` inducing the augmentation `𝒜₀ → 𝒪_{Y₀}`. Algebra maps
`𝒜 → 𝒪_Y` correspond bijectively to module maps `g^*(Ω¹_{X/S}) → 𝒪_Y` (because `𝒜 = 𝒪_Y ⊕ g^*(Ω¹_{X/S})` has the
square-zero ideal `g^*(Ω¹_{X/S})`). The condition that the algebra map induces the canonical augmentation on `𝒜₀` says
**the module map sends `g^*(Ω¹_{X/S})` into the ideal `𝒥`** (the kernel of `𝒪_Y → 𝒪_{Y₀}`). So we get the set

```text
ℋ𝓂_{𝒪_Y}(g^*(Ω¹_{X/S}), 𝒥) = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X/S}), 𝒥)
```

(the second equality because `𝒥` is annihilated by `𝒥`, so it is naturally an `𝒪_{Y₀}`-module). This is the desired
bijection. ∎

In words: **extensions of `g₀` along the square-zero thickening `Y₀ ↪ Y` correspond bijectively to derivations from
`𝒪_X` (pulled back to `Y₀`) into the square-zero ideal `𝒥`** — once one fixed extension is chosen.

### Corollary: smooth case, torsor under `𝒢`

<!-- source: III.5.2 -->

_This corollary says: when `X` is smooth over `S`, the sheaf of extensions `𝒫(g₀)` is not just formally principal
homogeneous — it is a **torsor**. Equivalently, **local** extensions exist, so the obstruction to a **global** extension
is exactly the cohomology class of the torsor in `H¹(Y₀, 𝒢)`._

**Corollary III.5.2.** _If `X` is **smooth** over `S` at the points of `g₀(Y₀)`, then `𝒫(g₀)` is a **principal
homogeneous sheaf** under the commutative sheaf of groups `𝒢`. In this case `𝒢` may also be written_

```text
𝒢 = g₀^*(𝔤_{X/S}) ⊗_{𝒪_{Y₀}} 𝒥,
```

_where `𝔤_{X/S}`is the **tangent sheaf** of`X`over`S`(file 17): the dual of`Ω¹_{X/S}`. This rewriting holds because
`Ω¹_{X/S}`is locally free of finite type when`X`is smooth over`S` (file 15, II.4.3)._

_In particular, this principal homogeneous sheaf determines a **cohomology class in `H¹(Y₀, 𝒢)`**, whose vanishing is
necessary and sufficient for the existence of an `S`-morphism `g` extending `g₀`. If such an extension exists, the set
of all possible extensions is a homogeneous space under `H⁰(Y₀, 𝒢)`._

**Proof sketch.** Smoothness of `X` over `S` gives, by III.3.1 condition (iii) (file 20), the **local existence** of
extensions of `g₀`. So for every `y ∈ Y₀` there is an open neighborhood of `y` over which `𝒫(g₀)` has a section — the
sheaf is **locally trivializable**, hence (combined with the formally principal homogeneous structure of III.5.1) a
torsor.

The rewriting of `𝒢` uses `Ω¹` locally free for smooth: `ℋ𝓂(Ω¹, 𝒥) = (Ω¹)^∨ ⊗ 𝒥 = 𝔤 ⊗ 𝒥` when `Ω¹` is locally free. The
cohomological classification is from file 17: torsors under `𝒢` correspond to `H¹(Y₀, 𝒢)`, and the trivial class
corresponds to torsors with global sections.

For the H⁰ statement: given two extensions `g, g'` of `g₀`, the "difference" is a section of `𝒢`, i.e. a derivation from
`g₀^* Ω¹_{X/S}` into `𝒥`; conversely any such derivation modifies one extension into another. So the set of extensions,
when nonempty, is a torsor under `H⁰(Y₀, 𝒢)` — but `H⁰(Y₀, 𝒢) = Γ(Y₀, 𝒢)` is just global sections. ∎

This is the **first cohomological theorem of Exposé III**. The H¹ obstruction to extending a morphism is the carrier of
all subsequent cohomological reasoning in §III.6 and §III.7.

### Step-by-step extension along thickenings

<!-- source: III.5.3 -->

*This corollary says: when one extends a morphism through a chain of thickenings `S ⊃ S_n ⊃ S_{n-1} ⊃ ⋯ ⊃ S*0`, each
step is the square-zero situation of III.5.1, and the obstruction lives in H¹ of a sheaf built from `Ω¹`and the graded
piece`gr^{n+1}_{𝓘} (𝒪*Y)`.*

**Setup.** Let `S` be a prescheme equipped with a coherent sheaf of ideals `𝓘`, and let `S_n := V(𝓘^{n+1})` for each
`n ≥ 0`. For preschemes `X` and `Y` over `S`, let `X_n := X ×_S S_n` and `Y_n := Y ×_S S_n`. Suppose we are given an
`S_n`-morphism

```text
g_n : Y_n ⟶ X_n,
```

equivalently an `S`-morphism `Y_n → X` (or an `S_{n+1}`-morphism `Y_n → X_{n+1}`). We seek to extend it to an
`S_{n+1}`-morphism

```text
g_{n+1} : Y_{n+1} ⟶ X_{n+1}.
```

This is the situation of III.5.1 with `S` replaced by `S_{n+1}`, `X` by `X_{n+1}`, `Y` by `Y_{n+1}`, `Y₀` by `Y_n`, `g₀`
by `g_n`, and `𝒥` by

```text
𝒥 = 𝓘^{n+1} 𝒪_Y / 𝓘^{n+2} 𝒪_Y.
```

The square-zero condition `𝒥² = 0` is automatic since `𝓘^{n+1} · 𝓘^{n+1} = 𝓘^{2n+2} ⊂ 𝓘^{n+2}` for `n ≥ 0`.

**Corollary III.5.3.** *Let `S, X, Y, 𝓘, g_n` be as above. Let `𝒫(g_n)` be the sheaf on `Y` whose sections on an open
`U` are the extensions `g_{n+1}`of`g_n`to an`S_{n+1}`-morphism `Y_{n+1} → X_{n+1}`. Then `𝒫(g_n)` is a **formally
principal homogeneous** sheaf under the sheaf of groups*

```text
𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X₀/S₀}), gr^{n+1}_{𝓘 𝒪_Y}(𝒪_Y)),
```

*where `g₀ : Y₀ → X₀` is the morphism induced by `g_n` (and the inverse image of
`Ω¹_{X_{n+1}/S_{n+1}}`on`X*0`is`Ω¹_{X*0/S₀}`).*

**Proof sketch.** Direct application of III.5.1 with the identifications above. The simplification
`Ω¹_{X_{n+1}/S_{n+1}} |_{X₀} = Ω¹_{X₀/S₀}` follows from the compatibility of Kähler differentials with base change (file
03, "Two exact sequences"). The pullback `g_n^*(Ω¹_{X_{n+1}/S_{n+1}})` on `Y₀` reduces to `h₀^*(Ω¹_{X₀/S₀})`, where
`h₀ : Y₀ → X₀` is induced; and since `𝒥` is annihilated by `𝓘 𝒪_Y`, only the restriction to `Y₀` matters. ∎

### Smooth case, step-by-step

<!-- source: III.5.4 -->

_This corollary says: when `X` is smooth over `S`, the formally principal homogeneous sheaf of III.5.3 is a torsor, and
the obstruction to extending `g_n` to `g_{n+1}` is a cohomology class in H¹._

**Corollary III.5.4.** *If `X` is **smooth over `S`** (at the points of `g₀(Y₀)`), then `𝒫(g_n)` is a principal
homogeneous sheaf, and defines an obstruction class in `H¹(Y₀, 𝒢)`. Vanishing of this class is necessary and sufficient
for the existence of a global extension `g_{n+1}`of`g_n`. If the extension exists, the set of extensions is a principal
homogeneous space under `H⁰(Y₀, 𝒢)`.*

_The sheaf `𝒢` may then also be written_

```text
𝒢 = g₀^*(𝔤_{X₀/S₀}) ⊗_{𝒪_{Y₀}} gr^{n+1}_{𝓘 𝒪_Y}(𝒪_Y).
```

**Proof sketch.** Combine III.5.2 with III.5.3. Smoothness of `X` over `S` gives smoothness of `X₀` over `S₀` (file 15,
II.3.x), hence local extension of `g₀`, hence the formally principal homogeneous sheaf is a torsor. The cohomological
classification (file 17) gives the H¹ obstruction. The rewriting of `𝒢` uses local freeness of `Ω¹_{X₀/S₀}` (file 15,
II.4.3). ∎

This is the **iterated step**. To extend `g₀ : Y₀ → X₀` to arbitrarily high thickenings, we need the H¹ obstructions to
vanish at every step:

```text
H¹(Y₀, g₀^*(𝔤_{X₀/S₀}) ⊗ gr^n_{𝓘 𝒪_Y}(𝒪_Y)) = 0   for all n ≥ 1.
```

This is rare in general, but happens in special cases (affine `Y₀`, free `gr^n`, etc.) — addressed in III.5.5 below.

### Affine case: existence of a global extension

<!-- source: III.5.5 -->

_This corollary says: when `Y₀` is affine, the H¹ obstructions vanish trivially (Serre vanishing), so step-by-step
extension works for every n. Combined with III.3.1, this gives a stronger form of the lifting characterization that the
original proof of III.3.1 could not give._

**Corollary III.5.5.** _In the statement of Theorem III.3.1, one obtains a necessary and sufficient condition equivalent
to the others by supposing that the test prescheme `Y'` (in (ii) or (ii bis)) is **affine**, and by requiring the
existence of a **global extension `g`** of `g₀` to all of `Y'` (rather than merely a local extension)._

_The proof of III.3.1 could not have given this result directly — III.3.1 was proved by reducing to the lifting property
characterization of formal smoothness (III.2.1, file 19), which gives only local extensions._

**Proof sketch.** When `Y'` (and hence `Y'₀`) is affine, the cohomology `H¹(Y'₀, 𝒢)` vanishes for any **quasi-coherent**
`𝒢` by Serre's affine vanishing (appendix `serre-affine-vanishing`, file 17). So the H¹ obstruction in III.5.4 is zero
at every step, and step-by-step extension produces a global lift. ∎

### Free graded case: obstruction calculation

<!-- source: III.5.6 -->

_This corollary says: in the important case where `Y` is flat over `S` and the graded pieces `gr^n(𝒪_S)` are locally
free, the H¹ obstruction at step `n` factors as a tensor product, and the single condition `H¹(Y₀, 𝒢₀) = 0` (with `𝒢₀`
the tangent sheaf pulled back to `Y₀`) suffices for **all** the obstructions to vanish._

**Corollary III.5.6.** _Let `(S, X, Y, 𝓘, g_n)` be as in III.5.3. Suppose moreover that `X` is smooth over `S` and `Y`
is flat over `S`, and finally that `S` is affine (with ring `A`, ideal `I ⊂ A`) and the_

```text
gr^n(𝒪_S) = 𝓘^n / 𝓘^{n+1}
```

_are locally free over `S`. Then the obstruction to constructing `g_{n+1}` lies in_

```text
H¹(Y₀, 𝒢₀) ⊗_A gr^{n+1}_I(A),
```

*where `𝒢₀ = g₀^*(𝔤_{X*0/S₀})`. In particular, if `H¹(Y₀, 𝒢₀) = 0`, then `g_n`extends to an`Ŝ`-morphism `ĝ : Ŷ → X̂`.*

**Proof sketch.** When `Y` is flat over `S`, one has

```text
gr^n(𝒪_Y) = gr^n(𝒪_S) ⊗_{𝒪_{S₀}} 𝒪_{Y₀}.
```

When the `gr^n(𝒪_S)` are locally free, the `n`-th obstruction sheaf

```text
𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X₀/S₀}), 𝒪_{Y₀}) ⊗_{𝒪_{S₀}} gr^n(𝒪_S),
```

(by III.5.4 and the rewriting). The tensor product factor `gr^n (𝒪_S)`, being locally free over `S`, is acyclic for
cohomology on `Y₀`. By Serre's affine vanishing on `S` plus a Künneth-like argument:

```text
H^i(Y₀, 𝒢) = H^i(Y₀, 𝒢₀) ⊗_A gr^n_I(A)   for every i.
```

When `H¹(Y₀, 𝒢₀) = 0`, all `H¹(Y₀, 𝒢)` vanish, so all obstructions in III.5.4 are zero. Step-by-step extension produces
a compatible system of `g_n`, hence a formal-scheme morphism `Ŷ → X̂`. ∎

### Corollary: when the morphism is an isomorphism

<!-- source: III.5.7 -->

_This corollary says: under the conditions of III.5.6, if `g₀` is an isomorphism, then so is the formal extension `ĝ`._

**Corollary III.5.7.** _Under the conditions of III.5.6, if `g₀` is an isomorphism, then so is `ĝ`. The same result
holds for **closed immersions**._

**Proof sketch.** Apply Lemma III.4.2 (file 20) at each step: `g_n` is an isomorphism iff `g₀` is an isomorphism (since
`Y_n` is flat over `Y` over `S`). Take the inverse limit. The variant for closed immersions follows from the variant of
III.4.2 noted there (which doesn't even need flatness). ∎

### Proposition: extending isomorphisms of formal schemes

<!-- source: III.5.8 -->

_This proposition says: in the formal-scheme version, isomorphisms on the closed fiber lift to isomorphisms of the
formal schemes, provided the same H¹ vanishing condition holds. Uniqueness needs H⁰ to vanish too._

**Proposition III.5.8.** *Let `A` be a complete local ring with maximal ideal `𝔪` and residue field `k`. Let `𝔛, 𝔜` be
two `𝔪`-adic formal preschemes over `A`, both flat over `A` (meaning each `𝔛_n, 𝔜_n` is flat over `A_n = A / 𝔪^{n+1}`).
Suppose `X₀ = 𝔛 ⊗_A k` is **smooth over `k`** and `H¹(X₀, 𝔤_{X*0/k}) = 0`.*

*Then every `k`-isomorphism `Y₀ → X₀` extends to an `A`-isomorphism `𝔜 → 𝔛`. The extension is unique if moreover
`H⁰(X₀, 𝔤_{X*0/k}) = 0`.*

**Proof sketch.** Existence: apply III.5.6 with `S = Spec A`, `Y = 𝔜`, `X = 𝔛`, and `g₀` the given `k`-isomorphism. The
hypothesis `H¹(X₀, 𝔤_{X₀/k}) = 0` makes all obstructions vanish. Then by III.5.7 the resulting formal morphism
`ĝ : 𝔜 → 𝔛` is an isomorphism (since `g₀` is).

Uniqueness: two extensions differ by a section of `H⁰` of the appropriate sheaf (by III.5.4); if `H⁰(X₀, 𝔤_{X₀/k}) = 0`,
the two extensions coincide at every step, hence agree on the inverse limit. ∎

### Corollary: ordinary proper schemes

<!-- source: III.5.9 -->

_This corollary says: III.5.8's formal statement upgrades to a statement about ordinary proper schemes via the
Grothendieck existence theorem (algebraization)._

**Corollary III.5.9.** _Statement III.5.8 remains valid when `𝔛, 𝔜` are replaced by ordinary `A`-schemes `X, Y` **proper
over `A`**._

**Proof sketch.** By the Grothendieck existence theorem (file 18, appendix `grothendieck-existence`), for `A` complete
and `X, Y` proper over `A`, the formal completions are equivalent to the ordinary schemes (`X̂` algebraic). So the
extension `ĝ : Ŷ → X̂` of III.5.8 corresponds to an ordinary morphism `Y → X`. Apply III.5.8 to get the isomorphism. ∎

**Application — Severi-Brauer schemes.** When `𝔛 = ℙ^r_k` (or more generally a Severi-Brauer scheme), the cohomology
`H¹(ℙ^r_k, 𝔤_{ℙ^r_k/k})` vanishes (the tangent sheaf of `ℙ^r` is known explicitly via the Euler sequence). So every
formal scheme proper and flat over `A` with closed fiber `ℙ^r_k` is algebraizable, and is in fact isomorphic to the
formal completion of `ℙ^r_A`. By descent theory, this generalizes to non-complete `A` after a finite étale extension; we
will not pursue this here.

## III.6 Global infinitesimal extension of smooth `S`-schemes

<!-- source: III.6 -->

We now invert the question: instead of extending a given morphism between two given schemes, we extend a **scheme
itself**. Given a smooth `S_n`-scheme `X_n`, can it be lifted to a smooth `S_{n+1}`-scheme `X_{n+1}` reducing to `X_n`
along the inclusion `S_n ⊂ S_{n+1}`? Locally yes (file 20, III.4.1); globally we get an obstruction in `H²`.

### Proposition: the automorphism sheaf

<!-- source: III.6.1 -->

*This proposition says: when `X_{n+1}`is a chosen lift of`X_n`, the sheaf of `S_{n+1}`-automorphisms of
`X_{n+1}`inducing the identity on`X_n`is canonically isomorphic to a tensor product of the tangent sheaf with the
relevant graded piece of`𝓘`. This sheaf is the automorphism group `𝒢` for the H² obstruction calculation.*

**Proposition III.6.1.** *Let `X_{n+1}`over`S_{n+1}`reduce to`X_n`over`S_n`. Then the sheaf, on the topological space
underlying `X_n`(or equivalently`X₀`), of `S_{n+1}`-automorphisms of `X_{n+1}`inducing the identity on`X_n` is
canonically isomorphic to*

```text
𝒢 = 𝔤_{X₀/S₀} ⊗_{𝒪_{S₀}} gr^{n+1}_𝓘(𝒪_S),
```

_as a sheaf of groups._

**Proof sketch.** By III.5.4 and III.4.2, the automorphism sheaf is a principal homogeneous sheaf under `𝒢` (apply
III.5.4 with `Y = X_{n+1}`, `Y₀ = X_n`, `X = X_{n+1}`, `g_n = id`). Since the identity automorphism is a distinguished
section, the torsor is trivial; via this trivialization, the automorphism sheaf identifies with `𝒢` as a sheaf of sets.
One checks that the identification is compatible with the group structures (the verification is in the source; we omit).
∎

In particular: the sheaf of automorphisms of `X_{n+1}` over `X_n` is **commutative**. So if `X'_{n+1}` is another lift
of `X_n`, isomorphic to `X_{n+1}` over an open `U ⊂ X₀`, then the identification of the two automorphism sheaves over
`U` is **canonical** — does not depend on the choice of isomorphism. This is the rigidity that makes the H² calculation
work.

### Corollary: the isomorphism sheaf is a torsor under `𝒢`

<!-- source: III.6.2 -->

_This corollary says: the sheaf of isomorphisms between two lifts of `X_n` is naturally a torsor under `𝒢` from III.6.1.
Equivalently, two lifts are locally isomorphic, and the local isomorphism is determined up to a section of `𝒢`._

**Corollary III.6.2.** *Let `X_{n+1}`and`X'_{n+1}`be smooth over`S_{n+1}`and reduce to`X_n`. Then the sheaf, on the
space underlying `X₀`, of `S_{n+1}`-isomorphisms from `X_{n+1}`to`X'_{n+1}`inducing the identity on`X_n`is naturally a
**principal homogeneous sheaf** (= torsor) under`𝒢`.*

**Proof.** Two lifts are locally isomorphic (III.4.1, file 20), so the isomorphism sheaf has nonempty stalks. The action
of `𝒢` (automorphisms of one of the lifts) on this sheaf by composition makes it into a torsor under `𝒢`. ∎

This sets up the H² calculation. We now have:

- **Local existence** of lifts (III.4.1).
- **Local isomorphism** of any two lifts (III.6.2).
- **Local isomorphisms determined up to `𝒢`** (III.6.1, III.6.2).

The 2-cocycle of failure-of-transitivity in `𝒢` is the obstruction.

### Theorem: the H² obstruction class

<!-- source: III.6.3 -->

*This theorem says: the obstruction to lifting `X_n` globally to a smooth `X_{n+1}`over`S_{n+1}`is a canonical
cohomology class in`H²(X₀, 𝒢)`. Vanishing is necessary and sufficient. If the obstruction vanishes, the set of lifts is
a torsor under `H¹(X₀, 𝒢)`. This is the centerpiece of the exposé.*

**Theorem III.6.3.** *Let `(S, 𝓘, X_n)` be as above, with `X_n` **separated**. Then one can define canonically an
**obstruction class in `H²(X₀, 𝒢)`** — where `𝒢` is the sheaf of III.6.1 — whose vanishing is necessary and sufficient
for the existence of a smooth `X_{n+1}`over`S_{n+1}`reducing to`X_n`.*

*If the obstruction is zero, the set of isomorphism classes (with isomorphisms inducing the identity on `X_n`) of
`S_{n+1}`-preschemes `X_{n+1}`reducing to`X_n`is naturally a **principal homogeneous space under`H¹(X₀, 𝒢)`**.*

**Proof construction.** Choose an affine open cover `(U_i)` of `X_n` (the underlying space is `X₀`, separated). By local
existence (III.4.1, file 20), for each `i` there exists a smooth scheme `X^i / S_{n+1}` reducing to `U_i`. Since `X_n`
is separated, the double overlaps `U_{ij} = U_i ∩ U_j` are again affine.

By III.6.2, on each `U_{ij}` the schemes `X^i` and `X^j`, restricted to `U_{ij}`, are locally isomorphic; since `U_{ij}`
is affine and `H¹(U_{ij}, 𝒢)` vanishes by Serre's affine vanishing, **there is a global isomorphism** on `U_{ij}`:

```text
f_{ji} : X^i|_{U_{ij}} ⟶ X^j|_{U_{ij}}.
```

(This is a choice; the choice is determined up to a section of `𝒢|_{U_{ij}}`.)

For triples, on `U_{ijk} = U_i ∩ U_j ∩ U_k` we get three isomorphisms `f_{ji}, f_{kj}, f_{ki}`. The composite
`f_{ki}⁻¹ ∘ f_{kj} ∘ f_{ji}` is an automorphism of `X^i|_{U_{ijk}}` over `X_n|_{U_{ijk}}`, hence by III.6.1 a section of
`𝒢|_{U_{ijk}}`:

```text
f_{ijk} := (f_{ki})⁻¹ ∘ f_{kj} ∘ f_{ji} ∈ 𝒢(U_{ijk}).
```

A short formal calculation (the "silly cocycle calculation" III.6.4) shows that `(f_{ijk})` is a **2-cocycle** for `𝒢`
on the cover `(U_i)`. The triple-overlap consistency for the gluing of the `X^i` into a global `X_{n+1}` is precisely
the **vanishing of this 2-cocycle as a 2-coboundary**, i.e. the existence of sections `g_{ij} ∈ 𝒢(U_{ij})` such that the
modified `f_{ji} · g_{ij}` satisfy the cocycle relation. This means: the existence of `X_{n+1}` is equivalent to the
obstruction class `[f_{ijk}] ∈ Ȟ²((U_i), 𝒢)` being zero. By Leray (file 17, T3), since `(U_i)` is an affine open cover
of the separated scheme `X₀` and `𝒢` is quasi-coherent, this Čech class equals `H²(X₀, 𝒢)`. The class is independent of
the affine cover.

If the obstruction vanishes, the choices of `(g_{ij})` modifying the `f_{ji}` form a torsor under `Z¹((U_i), 𝒢)`
(1-cocycles), and two such choices give isomorphic `X_{n+1}` iff they differ by a 1-coboundary. So the set of
isomorphism classes of `X_{n+1}` is a torsor under `Ȟ¹((U_i), 𝒢) = H¹(X₀, 𝒢)`. ∎

### Remark: the cocycle calculation as makeshift

<!-- source: III.6.4 -->

_This remark says: starting from III.6.1, the arguments are purely formal and would be cleaner in the framework of
fibered categories or non-abelian cohomology. The 2-cocycle calculation in III.6.3 is what Grothendieck calls a
"makeshift" because the satisfactory reference (Giraud's_ Cohomologie non abélienne _) was not yet written._

**Remark III.6.4.** Starting from III.6.1, the arguments made here are purely formal, and are advantageously transcribed
in the setting of **local categories** (or even general fibered categories). The obstruction class to the existence of a
"global" object of a category, where one can find an object "locally", any two objects are always "locally isomorphic",
and the automorphism group of any object is commutative, obtained in this general context, contains as a special case
the "second boundary homomorphism" in an exact sequence of sheaves of not necessarily commutative groups, studied for
example by Grothendieck in Kansas or Tôhoku.

The "silly cocycle calculation" made here should therefore be regarded as a **makeshift**, due to the absence of a
satisfactory reference text. (Footnote in the source: see Giraud, _Cohomologie non abélienne_, Springer 1971, for the
satisfactory treatment.)

### Remark: localizing on `S`

<!-- source: III.6.5 -->

_This remark says: when one looks at the obstruction class fiber-by-fiber over `S`, even when the global obstruction is
zero in `H²(X₀, 𝒢)`, one may still have a non-trivial principal homogeneous sheaf on `S₀` with structure group the
relative cohomology `R²f__(𝒢)`. The interplay with `R¹f__(𝒢)` is what governs the structure of moduli of lifts._

**Remark III.6.5.** Note that in III.6.3 there is in general no distinguished element in the principal homogeneous space
under `H¹(X₀, 𝒢)`. This is reflected, after localizing on `S`, by the fact that one obtains a principal homogeneous
sheaf on `S₀` with structure group `R¹f_*(𝒢)`, which is not necessarily trivial.

In symbols: even when `H²(X₀, 𝒢)` vanishes globally, the relative cohomology sheaf `R²f_*(𝒢)` on `S₀` may be nonzero —
in which case the global vanishing translates to a section being zero in `H⁰(S₀, R²f_*(𝒢))`, and the choice of lift is
governed by `R¹f_*(𝒢)` on the base.

### Remark: what is unknown

<!-- source: III.6.6 -->

_This remark says: at the time of writing, very little was known about the precise form of the obstruction classes for
moduli problems — particularly for abelian schemes over artinian rings. This was an open problem the source explicitly
flags as interesting. The footnote (added in 2003) notes that the obstruction is now known to vanish for abelian
schemes._

**Remark III.6.6.** For the moment we know almost nothing about the general algebraic mechanism of the cohomology
classes introduced in this number and their relations with the preceding number. We have nothing precise to say in the
simplest particular cases, such as the case of **abelian schemes over artinian rings**.

(Footnote, added in 2003: It is now known that the obstruction is always zero in this case; cf. F. Oort, "Finite group
schemes, local moduli for abelian varieties and lifting problems", _Algebraic Geometry Oslo 1970_, 1972.)

One hopes that people will be found to work the question out thoroughly; it seems particularly interesting. It is
intimately linked, in particular, to the "module theory" of algebraic structures.

### Corollary: when both `H¹` and `H²` vanish

<!-- source: III.6.7 -->

_This corollary says: when `H²` vanishes, a lift `X_{n+1}`exists; when both`H¹`and`H²` vanish, the lift is unique up to
isomorphism._

**Corollary III.6.7.** *Suppose `H²(X₀, 𝒢) = 0`. Then a smooth `X_{n+1}`over`S_{n+1}`reducing to`X_n`exists. It is
unique up to isomorphism if moreover`H¹(X₀, 𝒢) = 0`.*

**Proof.** Direct from III.6.3. ∎

This is the form of the obstruction theorem most often invoked in practice.

### Corollary: the affine case

<!-- source: III.6.8 -->

_This corollary says: when `X₀` is affine, both `H¹` and `H²` of quasi-coherent sheaves vanish (Serre), so a smooth lift
exists and is unique up to non-unique isomorphism._

**Corollary III.6.8.** _Under the conditions of Theorem III.4.1 (file 20), if `X₀` is **affine**, then there exists a
smooth `X` over `Y` reducing to `X₀`, and this `X` is **unique up to non-unique isomorphism**._

**Proof.** When `X₀` is affine, `H^q(X₀, 𝓕) = 0` for all `q ≥ 1` and any quasi-coherent `𝓕` (Serre's affine vanishing,
appendix `serre-affine-vanishing`). In particular `H²(X₀, 𝒢) = H¹(X₀, 𝒢) = 0`. Apply III.6.7 (for `n = 0`). ∎

**Comment.** The direct proof of Theorem III.4.1 (file 20, by reducing to the étale lifting theorem I.8.3, file 11)
could not have given this stronger result, since it produced only a local lift, with no statement about uniqueness. The
cohomological proof of III.6.8 sees uniqueness as a vanishing of `H¹`, not something built into the construction.

### Corollary: the free graded case

<!-- source: III.6.9 -->

_This corollary says: in the important case where `S` is affine and the graded pieces `gr^n(𝒪_S)` are locally free, the
cohomology computation factors as a tensor product, and the obstruction lies in `H²(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A)`._

**Corollary III.6.9.** *Under the conditions of III.6.3, suppose `S` is affine with ring `A`, `𝓘` is defined by an ideal
`I ⊂ A`, and the graded pieces `gr^n*𝓘(𝒪*S) = 𝓘^n / 𝓘^{n+1}`are locally free. Then`H^i(X₀, 𝒢)` identifies with*

```text
H^i(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A),
```

*where `𝒢₀ = 𝔤_{X*0/S₀}`. So the obstruction class to extending `X_n`lies in`H²(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A)`, and (when
zero) the set of isomorphism classes of solutions is a principal homogeneous space under
`H¹(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A)`.*

**Proof sketch.** Same Künneth-style argument as in III.5.6: when `gr^n(𝒪_S)` is locally free, tensoring with it
commutes with cohomology on `X₀`. Since `S` is affine and `gr^n(𝒪_S)` is projective, `gr^n_I(A)` is a flat `A`-module,
and the cohomology commutes with tensor product. ∎

### Corollary: existence of a formal smooth scheme

<!-- source: III.6.10 -->

*This corollary says: under the cleaner conditions of III.6.9, when `H²(X₀, 𝔤_{X*0/S₀}) = 0`, one can lift step-by-step
and obtain an `𝓘̂`-adic formal smooth scheme `𝔛`over`Ŝ`reducing to`X_n`. Uniqueness if `H¹` also vanishes.*

**Corollary III.6.10.** *Under the conditions of III.6.9, suppose `H²(X₀, 𝔤_{X*0/S₀}) = 0`. Then there exists an
`𝓘̂`-adic formal scheme `𝔛`over the`𝓘`-adic formal completion `Ŝ`of`S`, **smooth over `S`** in the sense that each
`𝔛_p`is smooth over`S_p`, and reducing to `X_n`(i.e., equipped with an isomorphism`X_n → 𝔛 ×_S S_n`).*

*If moreover `H¹(X₀, 𝔤_{X*0/S₀}) = 0`, then such a `𝔛` is unique up to isomorphism.*

**Proof sketch.** Construct `X_{n+1}, X_{n+2}, …` step by step using III.6.9 (vanishing of the obstruction at every step
from the single condition `H²(X₀, 𝒢₀) = 0`). The limit `𝔛 = lim_p X_p` is a formal smooth scheme over `Ŝ`. The
uniqueness assertion already appears in III.6.9 (every step is unique up to non-unique isomorphism, but uniqueness up to
isomorphism in H¹-vanishing). ∎

This is the **headline of §III.6**: the cohomological condition `H²(X₀, 𝔤_{X₀/S₀}) = 0` is sufficient for the **formal**
extension of a smooth scheme. The next file (file 22) handles the algebraization step — promoting the formal scheme `𝔛`
to an ordinary algebraic scheme `X` over the (necessarily complete) base.

## What to remember

- **§III.5.1** is the structural fact: the sheaf `𝒫(g₀)` of extensions of a morphism `g₀` along a square-zero thickening
    `Y₀ ↪ Y` is **formally principal homogeneous** under the `Hom`-sheaf `𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^* Ω¹_{X/S}, 𝒥)`.
- **§III.5.2** upgrades this to a **torsor** when `X` is smooth over `S` (so local extensions exist by file 20,
    III.3.1). The obstruction class is in **`H¹(Y₀, 𝒢)`**; if it vanishes, the set of extensions is a torsor under
    `H⁰(Y₀, 𝒢)`. Using smoothness, `𝒢 = g₀^*(𝔤_{X/S}) ⊗ 𝒥`.
- **§§III.5.3–III.5.6** iterate the step-by-step extension along thickenings `S_n`. The free-graded case III.5.6 reduces
    all obstructions to the single condition `H¹(Y₀, g₀^* 𝔤_{X₀/S₀}) = 0`.
- **§III.5.7–III.5.9** deduce: morphisms whose closed-fiber values are isomorphisms / closed immersions extend to formal
    isomorphisms / closed immersions; the algebraization theorem (file 18) then upgrades to ordinary proper schemes.
- **§III.6.1** identifies the **automorphism sheaf** of a lift `X_{n+1}` (over `X_n`) with the tangent-sheaf-tensor
    `𝒢 = 𝔤_{X₀/S₀} ⊗ gr^{n+1}_𝓘(𝒪_S)`. **§III.6.2** identifies the isomorphism sheaf of two lifts with a torsor under
    `𝒢`.
- **§III.6.3** is the **centerpiece**: the obstruction to lifting a smooth `X_n` to `X_{n+1}` is a class in `H²(X₀, 𝒢)`.
    If it vanishes, the set of lifts is a torsor under `H¹(X₀, 𝒢)`. The proof is the "silly cocycle calculation"
    (III.6.4), which is honest in the sense of Giraud's non-abelian cohomology.
- **§§III.6.7–III.6.10** are the practical corollaries: the affine case is automatic (III.6.8); the free-graded case
    reduces all obstructions to a single `H²(X₀, 𝔤_{X₀/S₀})` vanishing (III.6.9); when it vanishes, a **formal smooth
    lift `𝔛 / Ŝ`** exists (III.6.10), unique up to isomorphism if `H¹` also vanishes.

The final step — **algebraization of the formal lift `𝔛` to an ordinary scheme `X`** — is the subject of file 22 (Exposé
III §7). Combined with the H² vanishing of this file, the headline **Theorem III.7.3** of file 22 will give: every
smooth projective scheme `X₀ / k` with `H²(𝔤_{X₀/k}) = H²(𝒪_{X₀}) = 0` lifts to a smooth projective scheme over any
complete local `A` with residue field `k`. The corollary, **III.7.4**: every smooth proper curve over `k` lifts (both
`H²` vanish trivially on a curve).
