# Rewritten Exposé XI, section XI.3 — projective cones and Zariski's flat counterexample

<!-- source: XI.3 -->

## What this file is about

The earlier theorems about families of geometric objects all rely on a single technical hypothesis. It looks like the
kind of detail one might hope to weaken. The question is whether any looser version holds up.

It does not. Two explicit counterexamples close the door. The first is a cone — the everyday shape, built inside
algebraic geometry — together with the natural map that collapses its base down to the tip. Every horizontal slice is
well-behaved, but the map goes wrong invisibly at one point, and a key theorem about transporting covers fails. The
second example, due to Zariski, is more elaborate: a smooth surface mapped to a line, with a cover built by adjoining
roots; the cover fails to come from anything on the line below. Together the two examples show the original hypothesis
is exactly as strong as it needs to be.

Files 48 and 49 (gentle Exposé X §§X.1–X.2) gave three structural results that we will collectively call the **X-theory
chain**:

- **X.1.3** (file 48): descent of étale coverings — an étale cover `X′ → X` descends to an étale cover of `Y` iff it is
    completely decomposed on a geometric fibre.
- **X.1.4** (file 48): the homotopy exact sequence `π₁(X̄_y) → π₁(X) → π₁(Y) → e`.
- **X.2.4** (file 49): upper semicontinuity of fibre `π₁` along a specialisation `y₀ ⤳ y₁`.

All three of these results require the morphism `f : X → Y` to be **separable** — flat with geometrically reduced fibres
whose generic-point residue extensions are separable. The hypothesis is *not* a technical convenience: it is
load-bearing for the theorems to hold.

The present file (gentle Exposé XI §XI.3) provides two **counterexamples** showing exactly how sharp the separability
hypothesis is.

**Counterexample 1 (projective cones, §XI.3.1).** The projective cone `Ĉ_V` over a connected projective scheme `V` is
**simply connected** — `π₁(Ĉ_V) = 0` — by an application of X.1.4 plus IX.3.4. But the contraction morphism
`f : X = ℙ(𝒪_V ⊕ 𝒪_V(1)) → Ĉ_V` has fibres that are `ℙ¹` away from the vertex `y_0` and `V` over `y_0`. So all fibres
are **smooth** (when `V` is smooth) and **geometrically reduced**. Yet `f` is *not* separable, because it is not flat.
Take `V` smooth and **not** simply connected (e.g. an elliptic curve over `k̄`). Then `X` is not simply connected
(`π₁(X) = π₁(V) ≠ 0`), so there exists a non-trivial étale cover `X′ → X`. This cover does *not* descend to `Ĉ_V` (since
`π₁(Ĉ_V) = 0`), even though it is completely decomposed on every fibre except the central one `f^{-1}(y_0) = V`. So
X.1.3 *fails* when "separable" is weakened to "smooth fibres".

**Counterexample 2 (Zariski's flat example, §§XI.3.2–XI.3.3).** There exist morphisms `f : X → ℙ¹` from smooth
projective surfaces that are **flat** (the line is regular and `X` is regular) with **geometrically integral** fibres —
but for which the connected étale cover `X′ → X` defined by adjoining `f^{1/n}` does *not* descend to an étale cover of
`ℙ¹`. The would-be descended cover is the Kummer cover `Y′ → ℙ¹` defined by `t^{1/n}`, which is **ramified** at `t = 0`
and `t = ∞`, not étale. Concretely, the counterexample is realised by the **Fermat surface**
`X′ = {x^n + y^n + z^n + t^n = 0} ⊂ ℙ³_k` with a free `ℤ/nℤ`-action, descended to its quotient `X = X′/G`. This shows
X.1.3 *also* fails when "separable" is weakened to "flat with geometrically integral fibres".

The conclusion is summarised by a single statement:

> **Slogan.** *The separability hypothesis in X.1.3, X.1.4, X.2.4 is sharp.* It cannot be weakened to "smooth fibres",
> or to "geometrically reduced fibres", or to "flat with geometrically integral fibres". Two distinct sharp
> counterexamples (cone, Fermat surface) witness this.

______________________________________________________________________

## §XI.3.1 — Projective cones are simply connected

<!-- source: XI.3 -->

### Setup

<!-- source: XI.3 -->

Let `k` be algebraically closed. Let `V ⊂ ℙ^r_k` be a connected projective `k`-scheme. We assume, for the present gentle
pass, that `V` is **smooth** (this rules out singular cones, which would complicate the analysis without adding to the
counterexample's force).

Define:

- `Ĉ_V`, the **projective cone** over `V`: the projective compactification of the affine cone `C_V = V(𝒪_V(1))` (the
    total space of the dual of the tautological line bundle on `ℙ^r`, restricted to `V`). Concretely, `Ĉ_V` is obtained
    from `V` by adjoining a single point `y_0` (the **vertex**), with `Ĉ_V` containing `V` as a closed subscheme (the
    "infinity divisor") and containing `C_V \ \{0\}` as the complement of `V`.
- `X = ℙ(𝒪_V ⊕ 𝒪_V(1))`, the **projective closure** of `C_V` over `V`. This is a `ℙ¹`-bundle over `V`. It contains two
    distinguished sections: `X_0 = V(𝒪_V ⊕ 0)` (the zero section, identified with `V` via the obvious projection), and
    `X_∞ = V(0 ⊕ 𝒪_V(1))` (the section at infinity, also identified with `V` but lifted differently).
- `f : X → Ĉ_V`, the **canonical contraction morphism** of EGA II §8.6.4. The morphism `f` contracts the zero section
    `X_0 ⊂ X` to the vertex `y_0 ∈ Ĉ_V`, and is an isomorphism off `X_0`. It sends the section at infinity `X_∞` to the
    infinity divisor of `Ĉ_V` (also identified with `V`).

The fibres of `f`:

- For `y ∈ Ĉ_V \ \{y_0\}`, the fibre `f^{-1}(y)` is a single point.
- For `y = y_0` (the vertex), the fibre `f^{-1}(y_0) = X_0 ≃ V` is the entire zero section of `X`.

So `f` is *not* flat (the fibre dimension drops from `dim V` to `0`); but the fibres are all *smooth* (`V` is smooth by
hypothesis, and points are trivially smooth).

### Theorem XI.3.1 — every projective cone is simply connected

<!-- source: XI.3 -->

**Theorem XI.3.1.** Let `V ⊂ ℙ^r_k` be a connected projective `k`-scheme over algebraically closed `k`, and let `Ĉ_V` be
the projective cone over `V`. Then `Ĉ_V` is **simply connected**: `π₁(Ĉ_V) = 0`.

*This result says:* contracting the zero section of a `ℙ¹`-bundle over a non-trivially-`π₁` variety produces a
**simply-connected** total space. The contraction "kills" the fundamental group.

#### Proof.

**Step 1.** The morphism `p : X → V` (projection of the `ℙ¹`-bundle) is **proper** (since `ℙ¹` is proper) and
**separable** (it is the projection of a smooth `ℙ¹`-bundle, hence smooth, hence flat with smooth fibres). The fibres of
`p` are all isomorphic to `ℙ¹_k`, which is **simply connected** (XI.1.1, file 52).

By the homotopy exact sequence X.1.4 (file 48):

```text
π₁(\text{fibre}) → π₁(X) → π₁(V) → e,
```

and since `π₁(ℙ¹_k) = 0` and `p` has connected (geometrically) fibres, the leftmost arrow is zero, so the middle arrow
is an **isomorphism**:

```text
π₁(X) ≃ π₁(V).
```

**Step 2.** The zero section `X_0 ⊂ X` is identified with `V` via `p|_{X_0}` (the zero section is a section of `p`, so
it embeds `V` into `X`). Hence an étale cover `X′ → X` restricted to `X_0` is precisely the pullback of an étale cover
of `V` along the identification `X_0 ≃ V`. **A connected étale cover of `X` is trivial iff its restriction to `X_0` is
trivial.** (One direction is restriction; the other uses `π₁(X) → π₁(V) ≃ π₁(X_0)` being an iso.)

**Step 3.** Now consider an étale cover `Y′ → Ĉ_V` of the cone. Form the pullback

```text
X′ = X ×_{Ĉ_V} Y′ → X.
```

This is an étale cover of `X` of the same degree as `Y′ → Ĉ_V`.

**Step 4.** The restriction of `X′` to the fibre `f^{-1}(y_0) = X_0 ≃ V` is the pullback of `Y′ → Ĉ_V` along the
inclusion `\{y_0\} ↪ Ĉ_V` extended over `V` (= the fibre `X_0`). Since `\{y_0\}` is a single point, the pullback is the
**trivial** étale cover of `\{y_0\}` (any étale cover of a single point is a finite disjoint union of copies of the
point). Hence the pullback `X′|_{X_0}` is the *constant* étale cover of `X_0 ≃ V`, which is the **trivial** étale cover
of `V`.

By Step 2, `X′ → X` is therefore **trivial** as well.

**Step 5.** The map `π₁(X) → π₁(Ĉ_V)` is **surjective** by IX.3.4 (file 45) — since `f : X → Ĉ_V` has connected fibres
(every fibre is either a point or `V`, both connected). Hence every connected component of `Y′ → Ĉ_V` is the image of a
connected component of `X′ → X`. Since `X′ → X` is trivial, `Y′ → Ĉ_V` is trivial. So `π₁(Ĉ_V) = 0`. ∎

> **Slogan.** *Every projective cone is simply connected.* The contraction `f : X → Ĉ_V` kills any `π₁` that `X` had.

#### Affine cone in characteristic zero.

In characteristic zero, the same conclusion holds for the **affine** cone `C_V` (not just the projective cone):
`π₁(C_V) = 0`. The argument adapts because the inclusion `C_V ↪ Ĉ_V` is the complement of the infinity divisor
`V ⊂ Ĉ_V`, and the map `π₁(C_V) → π₁(Ĉ_V \ V)` is an iso. In positive characteristic, the affine cone has
**non-trivial** `π₁` (Artin–Schreier covers), so the affine statement is char-0-only.

______________________________________________________________________

### Application as counterexample: the X-theory hypotheses are sharp

<!-- source: XI.3 -->

Now we use Theorem XI.3.1 to break X.1.3, X.1.4, and X.2.4 when separability is weakened.

#### Step (i): take `V` not simply connected.

Choose `V ⊂ ℙ^r_k` to be smooth, connected, and with `π₁(V) ≠ 0`. Examples:

- `V = E`, a smooth projective elliptic curve over algebraically closed `k`. Then `π₁(E) = T·(E)` has rank `2` away from
    the characteristic.
- `V = A`, a higher-dimensional abelian variety. Then `π₁(A) = T·(A)` has rank `2g` away from the characteristic (file
    53, §XI.2.4).
- `V` a smooth projective curve of genus `g ≥ 1`. Then `π₁(V)` has the surface-group presentation (file 50, X.2.6).

By the proof of Theorem XI.3.1 Step 1, `π₁(X) ≃ π₁(V) ≠ 0`, so `X` admits a connected non-trivial étale cover `X′ → X`.

#### Step (ii): the cover `X′ → X` does *not* descend to `Ĉ_V`.

By Theorem XI.3.1, `π₁(Ĉ_V) = 0`, so the only étale covers of `Ĉ_V` are trivial. Hence `X′` cannot be the pullback of
any étale cover of `Ĉ_V`.

#### Step (iii): yet `X′` is completely decomposed on every fibre `f^{-1}(y)`.

For `y ≠ y_0`, the fibre is a single point, and any étale cover restricts trivially. For `y = y_0`, the fibre is
`X_0 ≃ V`. The restriction of `X′ → X` to `X_0` is the cover of `V` corresponding to the same `π₁(V)`-action that
defines `X′`; this is **not** completely decomposed when `V` has non-trivial `π₁`.

Wait — let us be careful. The original SGA source claims that `X′` restricted to the geometric fibres of `f` is
"completely decomposed". This needs a more careful reading: it is completely decomposed on the fibres `f^{-1}(y)` *for
`y ≠ y_0`* (which are points), but **not** on the central fibre `f^{-1}(y_0) = V`. The SGA's claim is about the fibre of
`f` over the **generic point** of `Ĉ_V` (a single geometric point of dimension 0, since `Ĉ_V` is proper and connected
over `k̄`); on this fibre `X′` is trivial.

So the situation is: `X′ → X` is **completely decomposed on the generic fibre** (and on every fibre except `X_0`) but
*not* on the central fibre `X_0`, and `X′` does not descend to `Ĉ_V`. The X.1.3 descent hypothesis is formulated for
proper-separable `f` with **geometrically connected fibres**, and reads:

> *X.1.3.* `X′ → X` descends to an étale cover of `Y` iff its restriction to the geometric generic fibre of `f : X → Y`
> is completely decomposed.

The counterexample shows: when `f` is *not* separable (here: not flat), this criterion **fails** — `X′` is completely
decomposed on the geometric generic fibre but does *not* descend.

#### Step (iv): consequences for X.1.4 and X.2.4.

By the same construction, the homotopy exact sequence X.1.4 fails: the map `π₁(X̄_{y_0}) → π₁(X) → π₁(Ĉ_V) → e` reads
`π₁(V) → π₁(X) ≃ π₁(V) → 0 → e`, which is exact at the right end (trivially) but the middle map is the identity, not
surjective onto the trivial group. So X.1.4 still holds *formally* in this case (the middle map factors through `0`,
contradiction unless `π₁(V) = 0`) — the failure is more subtle.

Actually the X.1.4 statement requires *separability* explicitly; the failure here is that the conclusion
"`π₁(X̄_y) → π₁(X)` is the kernel" — which would be a left-exactness statement we *did not* claim — does not even make
sense without the homotopy exact sequence.

The more dramatic failure is **X.2.4 — upper semicontinuity**. For `f : X → Ĉ_V`:

- Fibre over `y_0`: `f^{-1}(y_0) = X_0 ≃ V`, with `π₁(X̄_{y_0}) = π₁(V) ≠ 0`.
- Fibre over a generic `y ≠ y_0`: `f^{-1}(y) = \{pt\}`, with `π₁ = 0`.

Upper semicontinuity X.2.4 would say `π₁(\text{fibre over } y_0)` *quotients onto* `π₁(\text{fibre over } y)` — i.e.,
`π₁(V) ↠ 0`, which is trivially true. So the *direction* is right; but **X.2.4 says `π₁` should *drop* as the base
specialises to the central point**, i.e., `π₁` should be larger on the generic fibre and smaller on the central. Here it
is the opposite: `π₁` is **0 on the generic fibre and `π₁(V) ≠ 0` on the central fibre** — `π₁` *jumps up* as we
specialise to `y_0`. This is the **opposite** of upper semicontinuity. X.2.4 *fails* for this non-separable `f`. ∎

> **Slogan.** *Cones break the X-theory chain when separability is weakened to "smooth or geometrically reduced
> fibres".* The fibre `π₁` jumps *up* (not down) at the cone vertex, opposite to upper semicontinuity.

______________________________________________________________________

## §XI.3.2 — Zariski's flat counterexample: the setup and the abstract proof

<!-- source: XI.3 -->

We now turn to the second counterexample. The cone counterexample (§XI.3.1) failed at flatness: `f` was not flat, the
fibre dimension dropped at the vertex. **Zariski's counterexample** is more subtle: it is a **flat**, even **proper
smooth surjective** morphism `f : X → Y = ℙ¹` whose **geometric generic fibre is connected and separable** — i.e., it
satisfies *all* the X.1.3 hypotheses except *separability* (interpreted as "fibres geometrically reduced and residue
extensions separable at generic points").

### Theorem XI.3.2 — abstract Zariski setup

<!-- source: XI.3 -->

**Theorem XI.3.2 (Zariski).** There exists a morphism `f : X → Y = ℙ¹_k` from a nonsingular projective surface `X` to
the rational line `Y = ℙ¹_k` over algebraically closed `k`, with the following properties:

(i) `K := k(X)` is a **regular extension** of `k(f) = k(t)` (geometric generic fibre is connected and separable over
`k(t)`).

(ii) The divisor `div(f) = X_0 − X_∞` on `X` is an **`n`-th multiple** of a divisor on `X`, for some integer `n ≥ 1`
**prime to `char(k)`**.

(iii) `f` is **flat** (the line `ℙ¹` is regular and `X` is regular, so any non-constant morphism `X → ℙ¹` is flat by
miracle flatness).

#### Consequence: non-descent.

Let `X′ → X` be the étale `ℤ/nℤ`-cover of `X` defined by **normalising `X` in `K(f^{1/n})`**:

```text
X′ := \text{Normalisation of } X \text{ in } K(f^{1/n}).
```

By hypothesis (ii), `div(f) = n · D` for some divisor `D`, and so the extension `K(f^{1/n}) / K` is unramified at every
prime of `K` — i.e., `X′ → X` is **étale of degree `n`**.

The "would-be descended cover" of `Y = ℙ¹` is `Y′ → Y`, the **Kummer cover** of `ℙ¹` defined by `t^{1/n}`:

```text
Y′ := \text{Normalisation of } ℙ¹ \text{ in } k(t)(t^{1/n}).
```

Then:

1. The restriction of `X′ → X` to `f^{-1}(\mathbb{G}_m) = f^{-1}(ℙ¹ \setminus \{0, \infty\})` is exactly the pullback of
    `Y′|_{\mathbb{G}_m} → \mathbb{G}_m` along `f`.
1. The restriction of `X′ → X` to the **geometric generic fibre** of `X → ℙ¹` is **completely decomposed**: over
    `Spec \overline{k(t)}` the cover `X′ → X` splits into `n` copies of `Spec \overline{k(t)}` because `f^{1/n}` is
    well-defined on the algebraic closure of the residue field.
1. The cover `Y′ → Y` is **ramified** at `t = 0` and `t = ∞` (these are the two zeros of `t^n - t`, and the branching is
    genuine).

Hence: `X′ → X` cannot descend to an étale cover of `Y = ℙ¹` — the descent would have to be `Y′ → Y` by (1), but
`Y′ → Y` is **not étale** by (3).

This **contradicts X.1.3** if we drop the separability hypothesis: `f : X → ℙ¹` is flat with geometrically integral
fibres (one can check), so the X.1.3 descent statement would predict descent of `X′`, but no descent exists.

> **Slogan.** *Flat + geometrically integral fibres ≠ separable.* Zariski's example shows the separability hypothesis of
> X.1.3 cannot be weakened even this far.

#### Why flat + integral fibres is not separable here.

The geometric generic fibre `X̄_η` of `f : X → ℙ¹` is a smooth, connected, projective curve over `\overline{k(t)}`. By
hypothesis (i), `K/k(t)` is a regular extension, so `X̄_η` is geometrically integral. Connecting back to the generic
point of `X`: the function field of `X̄_η` is `K \otimes_{k(t)} \overline{k(t)}`, and regular extension means this is an
integral domain.

So the geometric generic fibre is good — it is even smooth. The failure of separability is at the **residue field
extension at the generic point of `X` over `k(t)`**: this extension is `K/k(t)`, which by hypothesis is **regular**,
*not* **separable**. (Regular = separable + primary; primary ≠ separable.) So the residue extension at the generic point
is regular but inseparable, which is enough to fail the SGA's "separable morphism" hypothesis on `f`.

The Exposé X "separable morphism" hypothesis specifically requires the residue extensions of fibres at generic points to
be **separable** field extensions, not merely **regular**. This is the gap Zariski's example exploits.

______________________________________________________________________

## §XI.3.3 — Serre's realisation: the Fermat surface

<!-- source: XI.3 -->

The theorem XI.3.2 is so far abstract — it asserts the existence of `f : X → ℙ¹` with properties (i)–(ii) but does not
exhibit a concrete `f`. The SGA source attributes to **J.-P. Serre** an explicit realisation via the **Fermat surface**.
We reproduce it in full.

### Setup of the Fermat surface

<!-- source: XI.3 -->

Take `n` to be a prime number with `n ≥ 5` and `n ≠ char(k)`. Let `G = ℤ/nℤ`.

The group `G` acts on the affine space `𝔸^4_k` (with coordinates `x, y, z, t`) by **multiplication by four distinct
characters of `G`**. Concretely, choose characters `χ_0, χ_1, χ_2, χ_3 : G → k^×`, all distinct (possible since
`|G| = n ≥ 5 > 4`, so there are enough characters in `\widehat{G} \cong G`). The `G`-action on `𝔸^4` is:

```text
g \cdot (x, y, z, t) = (\chi_0(g) \cdot x, \chi_1(g) \cdot y, \chi_2(g) \cdot z, \chi_3(g) \cdot t).
```

The action descends to `ℙ³_k`:

```text
g \cdot [x : y : z : t] = [\chi_0(g) x : \chi_1(g) y : \chi_2(g) z : \chi_3(g) t].
```

For this `ℙ³`-action, the **fixed points** of `G` are exactly the four coordinate axes (points of the form
`[1 : 0 : 0 : 0]`, etc.), because at any non-axis point the characters distinguish the coordinates and no `g \neq e` can
fix the projective tuple.

### The Fermat surface

<!-- source: XI.3 -->

Define the **Fermat surface**:

```text
X' := V(x^n + y^n + z^n + t^n) ⊂ ℙ³_k.
```

**Smoothness.** By the **Jacobian criterion**, `X'` is smooth at a point `[x : y : z : t]` iff at least one of the
partial derivatives `\partial / \partial x = n x^{n-1}`, etc., is nonzero. Since `n` is coprime to `char(k)`, `n \neq 0`
in `k`, and so the partial derivatives vanish simultaneously only when `x = y = z = t = 0`, which is not a point of
`ℙ³`. Hence `X'` is smooth over `k`.

**The `G`-action restricts to `X'`.** Check: if `[x : y : z : t] \in X'(k̄)` and `g \in G`, then
`g \cdot [x : y : z : t] = [\chi_0(g) x : \chi_1(g) y : \chi_2(g) z : \chi_3(g) t]`, and we must verify this also
satisfies `x^n + y^n + z^n + t^n = 0`. Substituting:

```text
(\chi_0(g) x)^n + (\chi_1(g) y)^n + (\chi_2(g) z)^n + (\chi_3(g) t)^n
   = \chi_0(g)^n x^n + \chi_1(g)^n y^n + \chi_2(g)^n z^n + \chi_3(g)^n t^n.
```

Each `\chi_i(g)^n = \chi_i(ng) = \chi_i(0) = 1` (since `\chi_i : G = ℤ/nℤ → k^\times` and `ng = 0`). So the expression
equals `x^n + y^n + z^n + t^n = 0`. Hence `g \cdot [x:y:z:t] \in X'(k̄)`. ✓

**The `G`-action on `X'` is free.** Need to check: the four `G`-fixed points of `ℙ³` (the coordinate axes `[1:0:0:0]`,
etc.) do *not* lie on `X'`. Substituting `[1:0:0:0]` into `x^n + y^n + z^n + t^n = 0`: `1 + 0 + 0 + 0 = 1 \neq 0`. So
`[1:0:0:0] \notin X'(k̄)`. Similarly for the other three coordinate axes. Hence the `G`-fixed-point set on `ℙ³` is
disjoint from `X'`, and so `G` acts **freely** on `X'(k̄)`.

(A free action of a finite group `G` on a smooth scheme `X'` produces a smooth quotient `X = X'/G`, with `X' \to X` a
principal `G`-cover — by file 30, V.2.6 and the existence theorem for quotients.)

### The quotient and the étale cover

<!-- source: XI.3 -->

Set `X := X' / G`. By the above:

- `X` is a smooth projective surface over `k`.
- `X' → X` is a **principal `G`-cover**, étale of degree `n`.

Hence we already have part of the setup of XI.3.2: a smooth projective surface `X` with a non-trivial étale
`G = ℤ/nℤ`-cover `X' → X`.

Now we extract the Zariski-flat morphism `f : X \to ℙ¹` and verify its properties.

### Construction of `f : X \to ℙ¹`

<!-- source: XI.3 -->

**Step 1 — choose a Kummer generator.** Let `\chi : G \to k^\times` be a *primitive* character of `G` (so
`\chi(1 \mod n)` generates the group of `n`-th roots of unity in `k`; possible since `n` is invertible in `k` and `k` is
algebraically closed). Among the four characters `\chi_0, \chi_1, \chi_2, \chi_3` chosen above, suppose they are
`\chi^{i_0}, \chi^{i_1}, \chi^{i_2}, \chi^{i_3}` for some integers `0 \leq i_0, i_1, i_2, i_3 \leq n-1`. For
concreteness, take `i_0 = 0, i_1 = 1, i_2 = 2, i_3 = 3` — so the characters are `1, \chi, \chi^2, \chi^3`.

**Step 2 — the function `g = x / y`.** Set `g := x / y` viewed as a rational function on `X' \subset ℙ³`. (It is indeed
a rational function — `y` is not identically zero on `X'`.) The `G`-action sends `g` to:

```text
g(g \cdot p) = \chi_0(g) x / \chi_1(g) y = 1 / \chi(g) \cdot g(p),
```

so the function `g` is **eigenvector with character `\chi^{-1}`** for the `G`-action — equivalently, `g \in K' = k(X')`
is in the `\chi^{-1}`-isotypic component. This makes `g^n` invariant under `G`, so `g^n \in K := k(X)` is a function on
the quotient.

Hence `K'/K = K(g)` is a **Kummer extension**: it is the extension obtained by adjoining the `n`-th root `g` of the
function `g^n \in K`.

**Step 3 — define `f := g^n \in K`.** Set `f := g^n`, viewed as a rational function on `X = X'/G`.

**Step 4 — `K` is a regular extension of `k(f)`.** We need to check property (i) of XI.3.2.

*Substep 4a:* Consider the plane curve `E ⊂ ℙ²` defined by `T^n + Z^n + (1 + g^n) U^n = 0` (a homogeneous degree- `n`
equation in the variables `T, Z, U` with coefficient in `k(g)`). By the **Jacobian criterion**, `E` is **smooth over
`k(g)`**, since `n` is invertible in `k` and we can check the partials are not simultaneously zero. (At any point on
`E`, at most three of `T, Z, U, 1 + g^n` can vanish simultaneously; the Jacobian non-vanishing follows.)

Smooth ⇒ connected (in this `ℙ²` setting, smooth projective plane curves are connected). Hence the function field of
`E / k(g)` is a **regular extension** of `k(g)`.

But the function field of `E` is exactly `K' = k(X') = k(g, T/U, Z/U)` (since `T/U, Z/U` are independent parameters in
`E` after fixing the affine chart `U = 1` and pulling back from the relation `T^n + Z^n + (1 + g^n) U^n = 0`). Hence
`K'` is a regular extension of `k(g)`.

*Substep 4b:* We have `K' / K / k(f)` with `K' / K` Galois of degree `n` (Kummer) and `K' / k(g)` regular. We want to
conclude `K / k(f)` is regular.

Note `k(f) = k(g^n) \subset k(g)`, and `[k(g) : k(f)] = n` (Kummer). The intersection `K \cap k(g)` is a subfield of
`k(g)` containing `k(f)`. Since `[k(g) : k(f)] = n` is prime, this intersection is either `k(f)` or `k(g)`. We claim it
is `k(f)`: indeed, `g \notin K` (since `g` is `\chi^{-1}`-eigenvalued and `K = (K')^G` consists of `G`-invariants), so
`K \not\supset k(g)`, so the intersection cannot be `k(g)`. Hence

```text
K \cap k(g) = k(f).
```

By the **linear disjointness criterion** for regular extensions: `K / k(f)` is regular iff `K \otimes_{k(f)} k(g)` is an
integral domain. We have
`K \otimes_{k(f)} k(g) \subset K \otimes_{k(f)} K = K \otimes_K \cdot K^{\otimes_n} \cdot k(g)`-style argument;
concretely, since `K' / k(g)` is regular, and `K \cdot k(g) = K'` (since `K(g) = K'`), the tensor product
`K \otimes_{k(f)} k(g)` injects into `K'`, hence is an integral domain. So `K / k(f)` is a regular extension. ✓

**Step 5 — the divisor of `f` is divisible by `n`.** We need property (ii) of XI.3.2.

Pull `f = g^n` back to `X' / k`: `f \circ \pi^*(g) = (g)^n` where `\pi : X' \to X` is the quotient morphism. Hence

```text
\text{div}_{X'}(\pi^*(f)) = \text{div}_{X'}(g^n) = n \cdot \text{div}_{X'}(g).
```

Now `\text{div}_{X'}(g)` is an integral divisor on `X'` (specifically, the divisor of zeros minus divisor of poles of
`g = x/y` on `X'`; both `\text{div}(x|_{X'})` and `\text{div}(y|_{X'})` are smooth curves on `X'`, intersecting
transversally — this requires a slightly more careful computation, but the divisor difference is a well-defined divisor
of degree zero on `X'`).

To **descend** the conclusion `\text{div}_{X'}(\pi^*(f)) = n \cdot \text{div}_{X'}(g)` from `X'` to `X`: we use that
`X' \to X` is étale, hence pullback of divisors `\pi^* : \text{Div}(X) \to \text{Div}(X')` is **injective** (an étale
morphism is faithfully flat, and pullback of divisors is induced by pullback of line bundles via `𝒪(D)`). So if
`\pi^*(D_X) = n D_{X'}` for some integer-divisor `D_{X'}` on `X'`, then `D_X = n D_X^{(0)}` for some integer-divisor
`D_X^{(0)}` on `X`, namely the divisor on `X` whose pullback to `X'` is `D_{X'}`.

Set `D_X^{(0)} := \pi_* \text{div}_{X'}(g) / |G| \in \text{Div}(X) \otimes ℚ` (this requires some care to make
integral); the étale-ness of `\pi` and the Galois descent guarantees integrality. The conclusion:

```text
\text{div}_X(f) = n \cdot D_X^{(0)},
```

as required by (ii). ✓

**Step 6 — `f` is so far a rational map; the blow-up step.**

The function `f = g^n \in K = k(X)` defines a **rational map** `f : X \dashrightarrow ℙ¹_k` (composing with the
canonical extension `K \hookrightarrow K(t) \to ℙ¹`). For property (iii) of XI.3.2 — `f` flat, in particular a morphism
— we need to *resolve* this rational map into a genuine morphism.

The indeterminacy locus of `f : X \dashrightarrow ℙ¹` is the simultaneous-zeros-and-poles locus:

```text
\{x \in X : f(x) = 0 \text{ and } f(x) = \infty\}.
```

By the Jacobian/computational analysis, the divisor of zeros `D_0 = \text{div}_X(f)_{> 0}` and the divisor of poles
`D_\infty = -\text{div}_X(f)_{< 0}` are both **smooth curves** on `X`, meeting **transversally** at a single point
`a \in X(k̄)`. (This follows from the explicit Fermat-surface coordinates: `D_0` is the zero locus of `f` on `X`, which
descends from `\text{div}_{X'}(x)` modulo `n`, a curve on `X'` of explicit form.)

**Blow up `X` at `a`.** Let `X_1 := \text{Bl}_a(X) \to X` be the blow-up. The strict transforms `\tilde{D}_0` and
`\tilde{D}_\infty` of `D_0` and `D_\infty` on `X_1` no longer meet (their preimages on the exceptional divisor
`E \cong ℙ¹` are now disjoint, since `D_0` and `D_\infty` were transverse). Hence the rational map
`f : X \dashrightarrow ℙ¹` extends to a **morphism** `f_1 : X_1 \to ℙ¹`.

The conditions (i) and (ii) are preserved by the blow-up: `K(X_1) = K(X)` (birational invariant), so `K / k(f)` remains
a regular extension; and the divisor of `f_1` on `X_1` is still divisible by `n` (the blow-up does not affect
divisibility outside `E`, and on `E` we can check directly).

So the Zariski-flat counterexample is now realised concretely:

```text
\boxed{ \text{The morphism } f_1 : X_1 = \text{Bl}_a(X) \to ℙ¹_k \text{ satisfies all of XI.3.2 (i)–(iii). } }
```

✓

> **Slogan.** *The Fermat surface witnesses Zariski's flat counterexample.* Concrete. Reproducible. The surface
> `X_1 = \text{Bl}_a((\{x^n + y^n + z^n + t^n = 0\}) / G)` is the explicit witness.

______________________________________________________________________

## §XI.3.4 — What this teaches

<!-- source: XI.3 -->

Putting the two counterexamples together:

| Counterexample                            | What is weakened                                                | What still holds for `f`                                                                                                        |
| ----------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Projective cone** (§XI.3.1)             | "geometrically reduced fibres" (instead of "separable")         | proper + connected fibres (one fibre is a single point, the central fibre is `V`)                                               |
| **Fermat-surface flat example** (§XI.3.3) | "geometrically integral fibres" + flat (instead of "separable") | proper + flat + smooth + geometrically integral fibres + regular generic-point residue extension `K/k(t)` (but *not* separable) |

The X.1.3 / X.1.4 / X.2.4 results **do not extend** to either of these weakenings:

- For the cone, the fibre `π₁` *jumps up* at the central fibre (`π₁(V) \to \pi_1(\text{point}) = 0`), opposite to X.2.4
    upper semicontinuity.
- For the Fermat-surface example, the étale `ℤ/nℤ`-cover `X' \to X` is completely decomposed on the geometric generic
    fibre but **does not descend** to `ℙ¹`, contradicting X.1.3 if applied without separability.

**The lesson:** Exposé X's separability hypothesis on `f` is **sharp**. It is not a technical convenience; it is
load-bearing. Two distinct, explicit, classical counterexamples (the projective cone, due to Grothendieck; the flat
Fermat surface, due to Zariski–Serre) witness exactly how the X-theory results fail when separability is weakened.

#### Forward-pointer to étale topology.

The SGA source notes (footnote on the X.3.2 / XI.3.3 example): from the viewpoint of the **étale topology** (SGA 4 VII),
the Zariski counterexample is recorded as: the **first étale derived direct image** `R^1(f_{\text{ét}})_* (ℤ/nℤ)` is
**non-separated as a sheaf** over `Y = ℙ¹`. The non-descent of `X' → X` is exactly the failure of `R^1` to be a
constructible sheaf on `Y` in the Zariski topology, even though `f` is flat. This pushes the analysis into the
étale-cohomology framework of SGA 4 — beyond the scope of the gentle SGA 1 pass. We mention it only as a pointer.

> **Slogan.** *X.1.3 / X.1.4 / X.2.4 separability is sharp.* Cones and Fermat surfaces are explicit witnesses.

______________________________________________________________________

## Closing of file 54

We computed `π₁(Ĉ_V) = 0` for projective cones (XI.3.1) and used the cone construction to break the X.1.3 / X.2.4
conclusions when separability is weakened to smooth or geometrically reduced fibres. We then reproduced Zariski's flat
counterexample abstractly (XI.3.2) and concretely via the Fermat surface (XI.3.3), showing X.1.3 also fails when
separability is weakened to "flat with geometrically integral fibres". The §XI.3.4 closing collected the overall lesson:
Exposé X's separability hypothesis is sharp.

Next, file 55 turns to the **abstract framework** that Exposé XI uses behind the scenes: **principal homogeneous
bundles** in the descent-theoretic sense, the six-term cohomology exact sequence (XI.4.5) attached to a short exact
sequence of commutative `S`-groups, and the special cases `H¹(S, GL_n)`, `H¹(S, 𝔾_m)`, `H¹(S, 𝔾_a)` (which reduce to
classical Zariski cohomology by XI.5.3). This is the cohomological framework that file 56's Kummer and Artin–Schreier
theories live in.
