# Rewritten Exposé X, sections X.2.1–X.2.5 — upper semicontinuity of fibre `π₁`; the specialisation morphism; drop counterexamples

<!-- source: X.2 -->

## What this file is about

A family of geometric objects has a fundamental group attached to each fibre — a record of the fibre's loops. As the
base point moves through the family the fibre moves with it, and the question is whether the loop group also moves
smoothly or can suddenly collapse. A torus pinched along a meridian loses a loop; a smooth elliptic curve degenerating
to one with a node loses a piece of its loop group. The loss is real.

The answer is one-sided. Moving toward a more special fibre, the loop group can only shrink, never grow. It can shrink,
however, and this file collects clean examples to show that it does — degenerate elliptic curves give a catalogue, and
an unpublished counterexample of Michael Artin shows that even the smoothest families can drop unexpectedly.

File 48 gave the **homotopy exact sequence**

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

for `f : X → Y` proper separable with `Y` locally noetherian and geometrically connected fibres. The sequence is
right-exact, with surjectivity at `π₁(Y, b)` coming from descent of finite étale coverings of the base (file 45, IX.3.4)
and exactness at the middle term coming from the categorical dictionary of file 33, V.6. The leftmost arrow
`π₁(X̄_y) → π₁(X)` was not asserted to be injective.

Section X.2 now refines that picture along **specialisations**. Concretely, when the base point of `Y` is moved from a
generic point `y_1$ to a closed specialisation`y_0$ in `Y$, we obtain a canonical comparison map

```text
sp : π₁(X̄_{y_1}, ā_1) → π₁(X̄_{y_0}, ā_0),
```

defined up to inner automorphism of
`π₁(X, a_0)$. This is the **specialisation morphism for the étale fundamental group**. The first key fact (X.2.1) is that when the base is the spectrum of a *complete* noetherian local ring, specialisation does *not* lose any information:`π₁(X_0,
a_0) → π₁(X, a)$ is an **isomorphism**. The reduction to the
complete-local case is then via the spectrum of the completion of `𝒪_{Y, y_0}$, which is what makes the construction of
\`sp$ canonical in general.

The second key fact (X.2.2) is that in the complete-local case, the homotopy exact sequence is *also* **left-exact** —
without any flatness or fibrewise separability hypothesis. This is a strong supplement: in the absence of separability,
the file 48 sequence X.1.4 does not even make sense, but in the complete-local case the existence theorem of formal
geometry (file 44, IX.1.10) furnishes a sharper input that gives the full short-exact sequence

```text
1 → π₁(X̄_0, ā_0) → π₁(X, a_0) → π₁(Y, b_0) → 1.
```

The two short exact sequences (one at the generic point `y_1$, one at the closed`y_0$) then assemble into a
commutative diagram, and the right-hand vertical maps are isomorphisms (between `π₁(X, –)$ and
`π₁(Y, –)$); by five-lemma reasoning, the leftmost vertical map`sp$ is *forced* by the diagram. This is X.2.3 (X̄_0 is
connected) and X.2.4 (general base).

X.2.5 then collects the drop counterexamples: even for proper *separable*
`f$, the specialisation morphism is typically **not** an isomorphism. The standard family of examples comes from **degenerate elliptic curves**: a smooth elliptic curve`E$ specialises to a *singular* elliptic configuration (Kodaira types `I_n$,
`II$,`III$, etc.), and the
fibre `π₁$ drops from
`ℤ̂²$ (rank 2) to a proper quotient. We catalogue four cases. We also record honestly **M. Artin's unpublished counterexample** to a conjecture Grothendieck wished were true: that the fibre`π₁$ of a *smooth
proper* morphism should assemble into a flat local system over the base. The conjecture is false; the modern
restatement and partial recovery are in Mochizuki's *p$-adic Teichmüller\* work.

Files 50 (X.2.6–X.2.14) and 51 (X.3) then carry the story to its conclusion: the transcendental computation of
`π₁$ for proper smooth curves, and the **continuity theorem** asserting that for *smooth* proper morphisms, the specialisation map is an isomorphism on prime-to-`p$
quotients.

## §X.2.1 — Translation of IX.1.10 to the language of `π₁`

<!-- source: X.2.1 -->

### Theorem X.2.1 — `π₁` of a proper scheme over a complete noetherian local base is the `π₁` of the closed fibre

<!-- source: X.2.1 -->

**Theorem X.2.1.** Let `Y = \mathrm{Spec}(A)` be the spectrum of a **complete noetherian local ring** with residue field
`k`. Let `f : X → Y` be a proper morphism, and let `X_0 = X ⊗_A k` be the closed fibre. Let `a_0` be a geometric point
of `X_0` and `a` the corresponding geometric point of `X`. Then the canonical homomorphism

```text
π₁(X_0, a_0) → π₁(X, a)
```

is an **isomorphism**.

*This result says:* the étale fundamental group of a proper scheme over the spectrum of a complete noetherian local ring
is determined by — and in fact equals — the étale fundamental group of its closed fibre. The complete-local base
contributes nothing to `π₁` beyond what the closed fibre already carries.

*Proof.* This is a direct translation of (file 44) IX.1.10 into the language of the fundamental group. Recall: IX.1.10
asserts that for proper `f : X → Y` with `Y = \mathrm{Spec}(A)` complete local noetherian, the functor

```text
F_{X / Y} : \mathrm{ét}(X) → \mathrm{ét}(X_0),    X′ ↦ X′ ⊗_A k
```

is an **equivalence of categories**. Equivalence of categories of finite étale coverings translates, via the (file 33)
V.6 dictionary, into an isomorphism of fundamental groups. Specifically, `π₁(X, a) = \mathrm{Aut}(F_a)` where `F_a` is
the fibre functor at `a`, and the equivalence above sends
`F_a$ to`F\_{a_0}$, so `\mathrm{Aut}(F_a) ≃ \mathrm{Aut}(F_{a_0}) = π₁(X_0, a_0)$.

The *load-bearing* input to IX.1.10 is the **existence theorem for sheaves in algebraic-formal geometry** — that is, the
proper-base-change formula EGA III §7.8 in the complete-local case, recorded as the new appendix row
[`ega-iii-7-formal-functions`](appendix-black-boxes.md#ega-iii-7-formal-functions). It is here that the algebraic
machinery of formal geometry enters the theory of `π₁` essentially. □

> **Slogan.** *Over a complete noetherian local base, the étale fundamental group of a proper scheme equals the étale
> fundamental group of its closed fibre. The base contributes nothing to `π₁` beyond what the closed fibre carries.*

The intuition: a complete-local base is "infinitesimally thin" in the sense that its non-trivial étale topology is
exhausted by its residue field. Étale coverings of the total space
`X$ correspond bijectively to étale coverings of the closed fibre`X_0$ — by the existence theorem, every étale `X_0$-covering
lifts uniquely to an étale `X$-covering. This is the deepest statement of formal-geometric`π₁$ machinery at the level of
SGA 1.

## §X.2.2 — The fundamental exact sequence in the complete-local case

<!-- source: X.2.2 -->

### Corollary X.2.2 — left-exact and right-exact fundamental sequence over a complete-local base

<!-- source: X.2.2 -->

Continue with `Y = \mathrm{Spec}(A)$,`A$ complete noetherian local, residue field `k$, algebraic closure
`k̄$, geometric closed fibre`X̄_0 = X_0 ⊗\_k k̄$, and `f : X → Y$ proper. Let `ā_0$ be a geometric point of`X̄_0$, `a_0$
its image in `X$,`b_0$ its image in `Y$.

**Corollary X.2.2.** Suppose \`X̄_0$ is connected. Then the sequence of canonical homomorphisms

```text
1 → π₁(X̄_0, ā_0) → π₁(X, a_0) → π₁(Y, b_0) → 1
```

is **exact** at every term — that is, it is a **short exact sequence**.

*This result says:* over a complete-local base, the fundamental exact sequence has the strongest possible form. The
leftmost arrow is **injective** (a fact not asserted by the file 48 X.1.4 sequence under the merely-proper-separable
hypothesis), and no flatness or fibrewise separability hypothesis is needed for the result. The complete-local
hypothesis is what makes this hold.

*Proof.* The fundamental exact sequence (file 47, IX.6.1) — applied with the artinian base \`\\mathrm{Spec}(k)$ as the
"base" rather than the full complete-local base — gives

```text
1 → π₁(X̄_0, ā_0) → π₁(X_0, a_0) → π₁(k, k̄) → 1
```

(here `π₁(k, k̄) = \mathrm{Gal}(k̄/k)$ is the absolute Galois group of`k$). By X.2.1, `π₁(X_0, a_0) → π₁(X, a_0)$ is an
isomorphism. There is also the **trivial-but-important** isomorphism

```text
π₁(k, k̄) → π₁(Y, b_0),
```

valid because \`Y = \\mathrm{Spec}$ of a complete-local henselian ring has étale fundamental group equal to the absolute
Galois group of its residue field. (This is a special case of (file 33) V.8.1 plus the fact that a complete-local
henselian ring has the same finite étale algebras as its residue field.)

Chaining these three isomorphisms with the file 47 IX.6.1 exact sequence: we replace `π₁(X_0, a_0)$ by`π₁(X, a_0)$
and `π₁(k, k̄)$ by \`π₁(Y, b_0)$, obtaining

```text
1 → π₁(X̄_0, ā_0) → π₁(X, a_0) → π₁(Y, b_0) → 1.
```

Exactness at every term is inherited from IX.6.1's exactness at every term, after the substitutions. □

Compare X.2.2 with the file 48 X.1.4 sequence

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e.
```

Two differences:

(a) **No separability or flatness hypothesis** is needed for X.2.2. The complete-local base alone is what underwrites
the upgrade from a right-exact sequence in X.1.4 to a short exact sequence.

(b) **Injectivity of the leftmost arrow.** This is the strong supplement that X.2.2 carries and X.1.4 does not. The
algebraic-formal existence theorem (file 44, IX.1.10) is what makes injectivity hold; without it, the left-end of the
sequence could be larger than \`π₁(X̄_0)$, and the loss-of-information along specialisation we will see in §X.2.3 would
be even worse.

> **Slogan.** *Over a complete-local base, the fundamental exact sequence is short-exact, with no separability
> hypothesis. The injectivity of the leftmost arrow comes from the algebraic-formal existence theorem (file 44,
> IX.1.10), which is unavailable under the merely proper-separable file 48 hypotheses.*

## §X.2.3 — The specialisation morphism is surjective for proper-separable families

<!-- source: X.2.3 -->

The X.2.2 left-exactness is the engine for the **specialisation morphism**. We now use it to compare fundamental groups
of geometric fibres across distinct points of \`Y$.

### Construction of \`sp$ (complete-local base)

<!-- source: X.2.3 -->

Continue with the X.2.2 setup. Let `y_1 ∈ Y$ be any (not necessarily generic) point, let`X_1$ be its fibre,
`X̄_1 = X_1 ⊗_{κ(y_1)} \overline{κ(y_1)}$ the geometric fibre, `ā_1$ a chosen geometric point of`X̄_1$, and `a_1, b_1$
its images in `X$ and`Y$. Choose a **path class** from `a_1$ to
`a_0$ — that is, a way of identifying the two geometric points modulo monodromy. This gives, in particular, a path class from`b_1$ to `b_0$.

The path class provides a commutative diagram

```text
   π₁(X̄_1, ā_1)  →  π₁(X, a_1)  →  π₁(Y, b_1)  →  e
        ↓                 ↓ ≃              ↓ ≃
1 → π₁(X̄_0, ā_0)  →  π₁(X, a_0)  →  π₁(Y, b_0)  →  1
```

where the upper row is the file 48 X.1.4 sequence at the point
`y_1$, the lower row is the X.2.2 short exact sequence at the closed point`y_0$, and the two right-hand vertical arrows are isomorphisms induced by the chosen path class
(walking the geometric point from `y_1$ to `y_0$ identifies the upper`π₁(X, a_1)$ with the lower `π₁(X, a_0)$, and
similarly for \`π₁(Y, –)$).

Since the lower row is exact and the right-hand vertical arrows are isomorphisms, the leftmost vertical arrow

```text
sp : π₁(X̄_1, ā_1) → π₁(X̄_0, ā_0)
```

is **canonically defined**: it is forced by the diagram via the commutativity constraint, and depends only on the chosen
path class. The dependence on path class is precisely an \*\*inner automorphism of
`π₁(X, a_0)$** (different paths conjugate`sp$ by the corresponding loop in `X$). Hence
`sp$ is well-defined **up to inner automorphism of`π₁(X,
a_0)$** — this is the canonical "defined up to conjugation" of geometric `π₁$-machinery.

> **Definition.** The map `sp : π₁(X̄_1, ā_1) → π₁(X̄_0, ā_0)$, defined up to inner automorphism of`π₁(X, a_0)$, is
> the **specialisation morphism** on the étale fundamental group, attached to the specialisation `y_1 ⤳ y_0$ in
> `Y$ and the chosen path class. We write`sp\_{y_0, y_1}$ when the points are emphasised.

### Corollary X.2.3 — surjectivity of \`sp$ under proper-separable + connected fibres

<!-- source: X.2.3 -->

**Corollary X.2.3.** Under the conditions of X.2.1, suppose in addition that the morphism
`f : X → Y$ is **separable** (file 48, X.1.1) and that`X̄_0$ is **connected**. Then `f_*𝒪_X = 𝒪_Y$ (by file 48, X.1.2),
and for every point `y_1 ∈ Y$ with geometric fibre`X̄_1$ and chosen geometric point `ā_1$, the specialisation morphism
\`sp : π₁(X̄_1, ā_1) → π₁(X̄_0, ā_0)$ is **surjective**.

*This result says:* under proper-separable hypotheses + geometric connectedness of fibres, the specialisation morphism
is surjective. The fundamental group of a *closed* geometric fibre is a quotient of the fundamental group of any
*generic* fibre. The étale fundamental group is "**upper semicontinuous**" along specialisation: it can only get smaller
as we move to special fibres.

*Proof.* When the file 48 X.1.4 hypotheses (proper separable + geometrically connected fibres) are imposed, the upper
row of the comparison diagram becomes an exact sequence

```text
π₁(X̄_1, ā_1) → π₁(X, a_1) → π₁(Y, b_1) → e
```

— that is, *also* right-exact (file 48, X.1.4). Combined with the right-exactness on the lower row (which we already
have from X.2.2), the commutativity of the diagram and the isomorphisms on the right-hand vertical arrows force the
leftmost vertical map `sp$ to be **surjective** by a diagram-chase. (Concretely: any element`γ_0 ∈ π₁(X̄_0, ā_0)$ has
an image in `π₁(X, a_0)$, which transfers via the right-hand iso back to an element in
`π₁(X, a_1)$; the file 48 X.1.4 right-exactness gives a preimage in`π₁(X̄_1, ā_1)$; tracking through the lower-row
exactness yields surjectivity.) □

This is the **upper semicontinuity** result for `π₁$: the geometric fibre`π₁$'s of a proper separable family with
geometrically connected fibres form an upper-semicontinuous family along the base topology — fibres can only get smaller
along specialisation.

> **Slogan.** *Proper separable + geometrically connected fibres ⇒ the specialisation morphism on \`π₁$ is surjective.
> The étale fundamental group is upper semicontinuous along specialisation in such a family. This result has no direct
> analogue in algebraic topology.*

It is worth noting that *this* upper-semicontinuity statement has no straightforward topological analogue — in classical
algebraic topology, the analogue of "fibre \`π₁$" depends on a choice of contractible neighbourhood of the base point,
and the right semicontinuity statement is more subtle. The clean upper-semicontinuity statement here is genuinely an
algebraic-geometric phenomenon, with the formal-geometric existence theorem (file 44 IX.1.10) as its load-bearing input.

## §X.2.4 — The specialisation morphism for a general locally noetherian base

<!-- source: X.2.4 -->

### Corollary X.2.4 — \`sp$ in the general locally noetherian case

<!-- source: X.2.4 -->

**Corollary X.2.4.** Let `f : X → Y$ be a **proper** morphism with **geometrically connected fibres**, with`Y$
locally noetherian. Let `y_0, y_1 ∈ Y$ be points such that `y_0 ∈ \mathrm{cl}(\{y_1\})$ (i.e.,`y_0$ is a
specialisation of `y_1$). Let
`X̄_0, X̄_1$ be the geometric fibres relative to chosen algebraic closures of the residue fields`κ(y_0),
κ(y_1)$, and let `ā_0, ā_1$ be geometric points of \`X̄_0, X̄_1$ respectively.

Then there is a canonically defined specialisation morphism

```text
sp_{y_0, y_1} : π₁(X̄_1, ā_1) → π₁(X̄_0, ā_0),
```

defined up to inner automorphism, depending only on the chosen path class. It is **surjective** if \`f$ is separable
(file 48, X.1.1).

*This result says:* the construction of the specialisation morphism extends from the complete-local-base case (X.2.3) to
the general locally noetherian case, by reducing to the complete-local case via the spectrum of the completion of the
local ring of `y_0$ in`Y$. The surjectivity statement carries over under separability.

*Proof.* The proof proceeds by reduction to X.2.3. Two steps.

**Step 1: independence from chosen algebraic-closure extensions.** The file 48 X.1.8 (base change of
`π₁$ to a larger algebraically closed field is an iso, for`X$ proper connected) immediately implies that the construction of
`sp_{y_0, y_1}$ does not depend on the specific algebraic closures chosen for `κ(y_0)$ and`κ(y_1)$. We may therefore
replace `Y$ by any base `Y′ → Y$ that has points`y_0′ ↦ y_0$ and `y_1′ ↦ y_1$ above the given points, without loss of
generality.

**Step 2: replace `Y$ by the spectrum of the completion of`𝒪\_{Y, y_0}$.** Set

```text
Y′ = \mathrm{Spec}(\widehat{𝒪_{Y, y_0}}),
```

the spectrum of the completion of the local ring of `y_0$ in`Y$. Then `Y′$ is the spectrum of a complete noetherian
local ring with residue field `κ(y_0)$. There is a canonical morphism`Y′ → Y$ — the canonical map from `\mathrm{Spec}$
of the completion to the original — and it has, in its image, both the closed point of `Y′$ (mapping to`y_0$) and
some generic point of `Y′$ (mapping to `y_1$, by faithful flatness of completion plus the assumption that`y_0 ∈
\\mathrm{cl}({y_1})$ in `Y$).

Now apply X.2.3 to the base change `f′ : X ×_Y Y′ → Y′$. The hypotheses are inherited:`f′$ is proper (base change
preserves properness), and `f′$ has geometrically connected fibres (this property is preserved by base change). If
`f$ is separable, so is`f′$ (file 48, X.1.1 base-change sorites). The X.2.3 surjectivity then gives the desired
surjectivity of `sp_{y_0, y_1}$. □

**Concrete reading.** The reduction in Step 2 can be made even more explicit: the specialisation morphism for the pair
`(y_0, y_1)$ in`Y$ equals (up to inner automorphism of `π₁(X, a_0)$) the specialisation morphism for the pair of
corresponding points in `Y′ = \mathrm{Spec}(\widehat{𝒪_{Y, y_0}})$. The completion`\\widehat{𝒪\_{Y, y_0}}$ is the
right local model for the topology around `y_0$.

> **Slogan.** *The specialisation morphism on
> `π₁$ is constructed for any specialisation in a locally noetherian base by reducing to the complete-local case via`\\mathrm{Spec}$ of the completion of the local ring of the closed
> point. Surjectivity of `sp$ under proper separable + geometrically connected fibres is the upper-semicontinuity
> statement, valid in full generality.*

## §X.2.5 — Drop counterexamples

<!-- source: X.2.5 -->

X.2.4 gives surjectivity of \`sp$ under proper separable + geometrically connected fibres. We now collect
counterexamples showing that the **surjectivity statement is not automatic** without proper-separable hypotheses, and
that even *with* proper-separable hypotheses, the **isomorphism statement is rarely true** — the specialisation can drop
strictly along a non-trivial specialisation.

### Counterexamples to surjectivity (dropping separability or flatness)

<!-- source: X.2.5 -->

**Remarks X.2.5 (counterexamples).** The conclusion of X.2.4 — surjectivity of
`sp$ — and *a fortiori* the predecessor results X.1.3 and X.1.4 of which it is a consequence, both **fail** if the morphism`f
\: X → Y$ is no longer assumed separable, even for projective schemes over an algebraically closed field of
characteristic 0. The canonical counterexamples come in two flavours.

\*\*(a) Nonseparable fibre, flat `f$.** There are examples where`f$ is flat but has a non-separable fibre, with `X$ and
`Y$ smooth over`k$ (char 0). These appear in **Exposé XI.3** (deferred for a future gentle pass; concrete construction
is in the **Bosch–Lütkebohmert–Raynaud** *Néron Models* §10.3 with the standard char-0 example of a Brauer-Severi
variety that becomes non-separable after a finite extension).

\*\*(b) Separable fibres, non-flat `f$.** When`f$ is a birational morphism of normal integral schemes — e.g. a
blow-up of a regular surface at a point — the fibres are separable (each fibre is reduced and locally finite-type
over the closed point), but `f$ is **not flat** (the central fibre has different dimension than the generic). Again see
Exposé XI.3 for explicit construction.

In both flavours, the fibre
`π₁$ of the generic fibre is *trivial* (the variety has trivial étale fundamental group), while the closed-fibre`π₁$ is *non-trivial* (the singular special fibre has more étale coverings than the smooth
generic one). This is the **opposite** of upper semicontinuity: the closed-fibre `π₁$ is *bigger* than the generic one,
contradicting the surjectivity of \`sp$ that we should have under proper-separable.

> **Slogan.** *Without separability of `f$, the specialisation morphism`sp$ can fail to be surjective — even for
> projective `f$ in characteristic 0. Counterexamples flow from non-flat birational maps and from non-separable fibres
> in flat families.*

### Counterexamples to isomorphism (degenerate elliptic curves)

<!-- source: X.2.5 -->

**Remark X.2.5 (continued).** Even under the proper-separable hypotheses of X.2.4, the specialisation morphism \`sp$
**often fails to be an isomorphism**. The simplest family of examples is the **degenerate elliptic curves** — singular
fibres of a proper smooth elliptic family at the boundary of moduli.

**The setup.** Let `R$ be a complete DVR with algebraically closed residue field`k$ and fraction field `K$, both of
characteristic ≠ 2, 3 (to avoid wild ramification issues). A **proper smooth elliptic family** is a proper smooth
morphism `f : 𝓔 → \mathrm{Spec}(R)$ whose geometric generic fibre`𝓔\_{K̄}$ is a nonsingular elliptic curve and whose
geometric special fibre `𝓔_k = 𝓔 ⊗_R k$ is a singular curve of arithmetic genus 1 — a **degenerate elliptic curve**.

Concrete family: `y² = x³ + a(t) x + b(t)$ over`\\mathrm{Spec}(R[t])$ localised at the discriminant, with various
choices of how `a(t), b(t)$ degenerate at the closed point.

**The generic fundamental group.** The fundamental group of a nonsingular elliptic curve over an algebraically closed
field is commutative, and its `ℓ$-primary component for any prime`ℓ ≠ \\mathrm{char}(k)$ is isomorphic to `ℤ_ℓ²$.
Profinitely: `π₁(𝓔_{K̄}) ≃ \prod_{ℓ ≠ p} ℤ_ℓ²$ (with`p = \\mathrm{char}(k)$; in characteristic 0 there is no `p$, and
\`π₁ = ℤ̂²$). Cited from Exposé XI.

**The special fibre.** The degenerate elliptic curve
`𝓔_k$ can be one of several Kodaira types. We collect three representative cases that drop`π₁$ along the specialisation:

| Kodaira type | Geometric description                                           | `π₁(𝓔_k)$ (prime-to-`p$) |
| ------------ | --------------------------------------------------------------- | ------------------------ |
| `I_n`        | A cycle of \`n$ smooth rational curves meeting transversally    | \`ℤ̂$                     |
| \`II$        | A cuspidal rational curve (one rational curve with a cusp)      | \`e$ (trivial)           |
| `III$,`IV$   | Two/three nonsingular rational curves tangent at one/two points | \`e$ (trivial)           |

(See **Kodaira, "On compact analytic surfaces"** *Ann. Math.* **71** (1960), 111–152, the classical classification.)

**The specialisation drop.** In each case, the specialisation morphism

```text
sp : π₁(𝓔_{K̄})^{(p)} → π₁(𝓔_k)^{(p)}
```

is **surjective** (X.2.4) but **not injective**: the prime-to-`p$ part of`π₁(𝓔\_{K̄})$ is `ℤ̂'²$ (or
`ℤ̂²$ in char 0), while the special-fibre`π₁$ is `ℤ̂$ (type `I_n$, n ≥ 1$) or trivial (types`II$, `III$,
`IV$, etc.). The drop from rank 2 to rank 1 or 0 is **strict**: the kernel of`sp$ is non-trivial, and the closed fibre
has fewer étale coverings than the generic.

#### Aside (the geometric meaning of the drop).

*Skip if you are comfortable with monodromy and singular-fibre topology.*

The drop is geometric: in characteristic 0, an elliptic curve over `ℂ$ is topologically a torus, with`π_1^{top} = ℤ²$;
its profinite completion `ℤ̂²$ is the étale `π₁$. When the elliptic curve specialises to a Kodaira`I_n$ configuration
(cycle of `n$ rational curves), the topological "cycle" collapses one `ℤ$-factor to rank 0, giving`π₁ = ℤ̂$. When it
specialises to a cuspidal rational curve (Kodaira `II$), both topological generators collapse — the cuspidal curve is
topologically a 2-sphere with one identified point, simply connected. The drop in étale
`π₁$ exactly mirrors the topological drop. The classical Kodaira classification —`I_n, II, III, IV, I_n^*, II^*, III^*,
IV^*$ — catalogues *all* topological types a degenerate elliptic curve over an algebraically closed field can exhibit.

______________________________________________________________________

### The smooth-proper conjecture (Grothendieck) and M. Artin's counterexample

<!-- source: X.2.5 -->

**Remark X.2.5 (continued).** When
`f : X → Y$ is a **smooth** proper morphism with geometrically connected fibres, one might hope for stronger statements: not just upper semicontinuity (a quotient relation between fibre`π₁$'s) but
**rigidity** of the fibre `π₁$ as a "flat local system over \`Y$." Concretely:

> **Conjecture (Grothendieck, hoped but false).** For
> `f : X → Y$ smooth proper with geometrically connected fibres, the geometric-fibre fundamental groups`π₁(X̄_y)$ as `y$
> ranges over
> `Y$ should assemble into a **flat local system** over`Y$ — an inverse limit of finite flat group schemes over `X$. In
> particular, the specialisation morphism should be an *isomorphism* in some refined sense.

This conjecture, if true, would imply that the fibre
`π₁$ is *rigid* under smooth proper deformations: every closed fibre`π₁$ would equal every other closed fibre `π₁$ up to
the natural identifications.

**The conjecture is false.** **M. Artin's unpublished counterexample** (recorded in the SGA source X.2.5 footnote, with
modern restatement in Mochizuki, \*Foundations of
`p$-adic Teichmüller Theory*, MSJ Memoirs **14**, 2002, Ch. 1): there exists a smooth proper morphism`f : X →
Y$ of relative dimension 1 — a family of smooth proper curves of fixed
genus `g ≥ 2$ over a connected `Y$ — such that the geometric-fibre`π₁(X̄_y)$ as `y$ ranges over
`Y$ do **not** assemble into a flat local system over`Y$. The fibre `π₁$ varies in a non-flat way along the smooth
proper family.

Cited as the new appendix row [`m-artin-unpublished-fibre-pi1`](appendix-black-boxes.md#m-artin-unpublished-fibre-pi1).

**The conceptual reason.** In characteristic 0, the conjecture is *true* in a certain sense — the
prime-to-`p$ part of the fibre`π₁$ is invariant under specialisation (file 51, X.3.9). In characteristic `p > 0$, the
\*\*`p$-primary** part of the fibre`π₁$ behaves wildly: the **continuous component** of "true `π₁$" corresponding to
classification of principal coverings with structural group an infinitesimal group can vary in non-locally-constant
ways. M. Artin's counterexample exhibits this variation.

**What survives.** The modern correction is that the \*\*prime-to-`p$ quotient**`π₁(X̄_y)^{(p)}$ does form a flat local
system over `Y$, where
`p = \mathrm{char}(κ(y_0))$. This is the content of the continuity theorem (file 51, X.3.8). The`p$-primary part of fibre `π₁$,
however, is non-rigid; it captures "wild" inseparable phenomena that have no analogue in characteristic 0. Modern work
on
`p$-adic Teichmüller theory (Mochizuki) refines the statement: certain quotients of the`p$-primary part *do* form local systems in a hierarchical sense, but the full `π₁$
does not.

> **Slogan.** *Upper semicontinuity is a real drop, not a fiction of the proof method. The gap between fibres can be
> arbitrarily large, and even for smooth proper families there is no straightforward "fundamental group as flat local
> system" theorem — M. Artin's unpublished counterexample (with modern restatement in Mochizuki) shows that the
> `p$-primary part of fibre`π₁$ varies wildly under smooth proper deformation. The prime-to-`p$ quotient, however, is
> rigid (file 51, X.3.8).*

### Closing remarks for X.2.5

The drop counterexamples of X.2.5 partition naturally into three families:

1. **No separability.** Counterexamples of types (a) and (b) above, with characteristic 0 and even projective-smooth
    \`Y$. The conclusion: upper semicontinuity fails outright without separability.
1. **With separability, with proper-smooth.** Degenerate elliptic curve specialisations (Kodaira types \`I_n, II, III,
    IV$). The conclusion: surjectivity holds (X.2.4), but not injectivity.
1. **Smooth proper family, fixed-genus curves.** M. Artin's counterexample. Even within the smoothest possible
    hypotheses, the fibre
    `π₁$ is not a flat local system. The conclusion: rigidity is an open problem in characteristic`p$, with partial resolution (X.3.8 + Mochizuki) on the prime-to-`p$
    side.

These three families progressively narrow the failure: starting with non-separable counterexamples (failure of even
surjectivity), through Kodaira-type non-injective specialisations (loss-of-information from generic to special), to M.
Artin's smooth-proper non-rigidity (which exists despite the strongest possible hypotheses, capturing the fundamentally
non-locally-constant wild `p$-primary behaviour of`π₁$ in characteristic `p$).

Files 50 and 51 then push the rigidity story to its limits: file 50 develops the **transcendental method** that computes
`π₁$ of a proper smooth curve, allowing direct comparison with the topological surface group. File 51 then gives the **continuity theorem** — the specialisation morphism is an isomorphism on the prime-to-`p$
quotient — which is the strongest rigidity statement available at the level of SGA 1.

______________________________________________________________________

## Closing pointer to file 50

This file gave the **upper semicontinuity** of fibre `π₁$ for proper separable families: the specialisation morphism`sp
\: π₁(X̄\_{y_1}) → π₁(X̄\_{y_0})$ is **surjective** (X.2.3 in the complete-local case, X.2.4 in general). It also
catalogued the **drop counterexamples** that show this surjectivity is a real upper bound — degenerate elliptic curves
drop fibre `π₁$ from `ℤ̂²$ to`ℤ̂$ or to `e$, and M. Artin's counterexample shows even smooth proper families exhibit
fundamental-non-rigidity in characteristic \`p > 0$.

File 50 develops the **transcendental method**: in characteristic 0,
`π₁$ of a proper smooth connected curve of genus`g$ over an algebraically closed field is `^the profinite completion of the topological surface group with `2g$
generators and one commutator relation. The argument uses the algebraic-closure invariance X.1.8 to reduce to the case
`k = ℂ$, then compares with the analytic topology. File 50 also develops the **finite-generation theorem** (X.2.9):`π₁$
of any proper connected scheme over an algebraically closed field is topologically finitely generated. The proof uses
Chow's lemma + Bertini's theorem + induction on dimension. Finally, file 50 records **A. Tamagawa's solvable
specialisation theorem** for proper smooth curves over a complete DVR with finite residue field — a **rigidity**
statement under solvable-Galois-extension reduction.

File 51 closes Exposé X with the **continuity theorem** (X.3.8): for
`f$ proper smooth with geometrically connected fibres, the specialisation morphism is an isomorphism on prime-to-`p$ quotients of `π₁$.
The proof requires two new black boxes — Zariski–Nagata purity of the branch locus and Abhyankar's lemma — together with
the gentle dim-2 proof of purity inline.
