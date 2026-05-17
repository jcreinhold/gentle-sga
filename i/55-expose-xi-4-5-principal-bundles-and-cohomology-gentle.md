# Rewritten Exposé XI, sections XI.4–XI.5 — principal bundles and the cohomology exact sequence

<!-- source: XI.4 -->

## What this file is about

A principal bundle is geometry twisted by a group. Above each point of a base space sits a copy of the group, glued
so that the group slides the copies along each other. A Möbius strip rotating around its central circle is the
simplest example. In algebraic geometry the group is itself a geometric object, and the early framework only allowed
the well-behaved ones. That left out some of the most interesting groups in positive characteristic, whose points are
all squashed onto a single basepoint but which carry rich internal structure.

Widen the gluing requirement and the framework opens up. Principal bundles for any reasonable algebraic group fit
into one framework, and a six-term sequence ties bundles for one group to bundles for a related one. For the
classical groups the wider and narrower notions collapse together. The setup is the engine the next file uses.

Files 30–33 (gentle Exposé V) introduced **principal coverings** for finite étale group schemes `G`: an étale
covering `P → S` together with a free transitive right `G`-action on `P` whose quotient is `S` (V.2.7, file 30).
Files 40–43 (gentle Exposé VIII) developed **faithfully flat descent** in detail: faithfully flat quasi-compact
morphisms `S' → S` are morphisms of *effective* descent for the categories of quasi-coherent modules, affine
schemes, and various structural conditions (VIII.2.1, VIII.5.6, VIII.7.5–8).

Exposé XI §§4–5 combine these two ingredients. The principal-cover notion of V.2.7 was restricted to finite **étale**
`G`, because Galois categories are built on finite étale covers. But there are interesting non-étale finite flat
group schemes — `μ_p` and `α_p` in characteristic `p` — whose principal bundles classify finer information than the
étale `π₁`. Exposé XI extends the principal-cover notion to such `G` via **fpqc-local trivialisation**, leaning on
VIII to make the extension well-defined.

This file (gentle Exposé XI §§XI.4–XI.5) develops:

- §XI.4: **principal homogeneous bundles** in the fpqc / descent-theoretic sense (XI.4.1), the criterion for these
  in terms of formally-principal-homogeneous + fpqc descent (XI.4.2), associated bundles and twists, `H⁰` and
  `H¹` defined for fpqc-sheaf cohomology of commutative `S`-groups, and the **six-term cohomology exact sequence**
  (XI.4.5) attached to a short exact sequence `0 → G' → G → G'' → 0`.

- §XI.5: the **special cases** of GL_n, 𝔾_m, 𝔾_a. Every principal bundle for these groups is **Zariski-locally**
  trivial (XI.5.1), not just fpqc-locally trivial — the difference between the two topologies collapses. As a
  consequence, `H¹(S, GL_n)` is canonically isomorphic to the set of locally-free rank-`n` sheaves on `S`,
  `H¹(S, 𝔾_m) ≃ Pic(S)`, and `H¹(S, 𝔾_a) ≃ H¹(S, 𝒪_S)` — the classical Zariski cohomology groups (XI.5.3).

The framework set up here is what file 56 will use for **Kummer and Artin–Schreier theories**: feed the Kummer
exact sequence `0 → μ_n → 𝔾_m → 𝔾_m → 0` into the XI.4.5 six-term sequence, use XI.5.3 to identify
`H¹(S, 𝔾_m) = Pic(S)`, and read off `H¹(S, μ_n) = \text{some quotient of } Pic(S)`. The same recipe with the
Artin–Schreier sequence in characteristic `p` reads off `H¹(S, ℤ/pℤ)` in terms of `H¹(S, 𝒪_S)`.

______________________________________________________________________

## §XI.4.0 — Bridge from V.2.7 (file 30) to XI.4.1

<!-- source: XI.4 -->

Recall the principal-cover definition from V.2.7 (file 30):

**Definition (V.2.7).** Let `G` be a **finite étale** group scheme over `S`. A **principal `G`-covering** of `S`
is an étale finite morphism `P → S` together with a right `G`-action on `P` such that:

(i) the action map `P × G → P × P`, `(p, g) ↦ (p, p · g)`, is an isomorphism;

(ii) `P → S` is **étale-locally trivial**: there exists an étale cover `\{U_i → S\}` such that `P \times_S U_i \cong
G \times_S U_i` (with `G \times_S U_i` acting on itself by translation).

The étale-local-trivialisation hypothesis is intrinsic to the Galois-category framework: étale topology is what
detects étale-finite group schemes.

The XI.4 generalisation replaces "étale-locally trivial" with "**fpqc-locally trivial**" — fpqc standing for
*faithfully flat, quasi-compact*, the strictly coarser topology of file 40:

**Definition (XI.4.1, sketch).** Let `G` be a quasi-compact flat affine `S`-group scheme (possibly non-étale).
A **principal homogeneous bundle** under `G` is a prescheme `P` with a right `G`-action such that:

(i) the action map `P × G → P × P` is an isomorphism;

(ii) `P → S` is **fpqc-locally trivial**: there exists a faithfully flat quasi-compact `S' → S` such that
`P \times_S S' \cong G \times_S S'`.

The two definitions agree when `G` is finite étale (étale-locally trivial implies fpqc-locally trivial), but XI.4.1
admits much larger classes of `G`:

- `G = 𝔾_m`, `𝔾_a`, `GL_n` — *connected* algebraic groups, neither étale nor finite. Principal bundles for these
  are classical objects (Picard group, vector bundles), now subsumed into the XI.4 framework.
- `G = μ_p`, `α_p` — *infinitesimal* group schemes in characteristic `p`. Principal bundles for these are
  invisible to the étale `π₁` but visible to the flat / Nori `π₁^N` (file 53 §XI.2.5).

> **Slogan.** *XI.4.1 generalises V.2.7 by replacing étale-local with fpqc-local trivialisation.* The class of
> structure groups grows from finite étale to quasi-compact flat affine.

______________________________________________________________________

## §XI.4.1 — Principal homogeneous bundles in the fpqc sense

<!-- source: XI.4.1 -->

### Definition XI.4.1 — principal homogeneous bundle

<!-- source: XI.4.1 -->

**Definition XI.4.1.** Let `G` be an `S`-group (a group object in the category `Sch_{/S}` of `S`-preschemes). A
**formally principal homogeneous bundle** under `G` is an `S`-prescheme `P` with a right `G`-action — i.e., a
morphism `\pi : P \times_S G \to P` satisfying the standard action axioms — such that the morphism

```text
P \times_S G \to P \times_S P, \qquad (x, g) \mapsto (x, x \cdot g)
```

is an **isomorphism**.

A **principal homogeneous bundle** under `G` is a formally principal homogeneous bundle `P` such that there exists
a covering `\{U_i\}` of `S` by open subsets and, for each `i`, a faithfully flat quasi-compact morphism `S'_i \to
U_i` such that the base change `P \times_S S' \cong G \times_S S'` as `(G \times_S S')`-spaces (with `G` acting on
itself by right translation), where `S' = \coprod_i S'_i`.

*This definition says:* a principal homogeneous bundle is a formally principal homogeneous bundle that is locally
trivial in the **fpqc** topology — there is a faithfully flat quasi-compact base change that trivialises it.

> **Slogan.** *Principal homogeneous = formally principal homogeneous + fpqc-locally trivial.*

#### Aside (set-theoretic interpretation).

For every `S`-prescheme `S'`, the set `P(S') := \text{Hom}_S(S', P)` is a set with right operator group `G(S') :=
\text{Hom}_S(S', G)`. The "formally principal homogeneous" condition says: `P(S')` is either **empty** or a
**principal homogeneous `G(S')`-set** (transitive free action). The "fpqc-locally trivial" condition adds: there is
an fpqc cover `S' \to S` such that `P(S')` is non-empty (hence isomorphic to `G(S')` as a `G(S')`-set).

In topological language: a principal `G`-bundle is a "twisted" copy of `G` over `S`, locally indistinguishable
from `G` in the fpqc topology.

______________________________________________________________________

### Proposition XI.4.2 — criterion

<!-- source: XI.4.2 -->

**Proposition XI.4.2.** Let `G` be an `S`-group, **flat and quasi-compact** over `S`. Let `P` be a formally
principal homogeneous bundle under `G`. The following are equivalent:

(i) `P` is a principal homogeneous bundle (XI.4.1).

(ii) `P → S` is **faithfully flat and quasi-compact** (i.e., `P → S` is itself an fpqc morphism).

*This result says:* for flat quasi-compact `G`, the fpqc-local-triviality hypothesis of XI.4.1 is **equivalent** to
the simpler condition that `P → S` is itself fpqc.

**Proof.**

**(i) ⇒ (ii):** Suppose `P` is principal homogeneous, with `S' → S` an fpqc trivialising base change so that
`P \times_S S' \cong G \times_S S'`. The pulled-back morphism `G \times_S S' \to S'` is fpqc (since `G \to S` is
fpqc by hypothesis on `G`), hence so is its identification `P \times_S S' \to S'`. By **fpqc descent of fpqc**
(VIII.5.6 in file 42, or VIII.3.1 for surjectivity and quasi-compactness, plus VIII for flatness), the original
morphism `P \to S` is fpqc.

**(ii) ⇒ (i):** Suppose `P \to S` is fpqc. Take `S' := P` itself. The base change `P \times_S P` is then a
formally principal homogeneous `G \times_S P`-bundle over `P`. By the formal-principality, this base change is
canonically isomorphic to `G \times_S P` via `(p_1, p_2) \mapsto (p_1, g)` where `g \in G(P)` is the unique
element with `p_2 = p_1 \cdot g`. Hence `P \times_S P \cong G \times_S P`, so `S' = P` is a trivialising base
change. ✓

> **Slogan.** *For flat quasi-compact `G`, principal homogeneous = formally principal homogeneous + structural
> morphism fpqc.*

______________________________________________________________________

### Corollary XI.4.3 — affine flat `G` gives affine flat `P`

<!-- source: XI.4.3 -->

**Corollary XI.4.3.** If `G` is **affine and flat** over `S`, every principal homogeneous bundle `P` under `G` is
**affine and flat** over `S`.

**Proof.** With `S' → S` a trivialising fpqc base change, `P \times_S S' \cong G \times_S S'` is affine and flat
over `S'` (since `G` is so over `S` and base change preserves affineness and flatness). Then by **VIII.5.6** (file
42) — properties stable under fpqc descent — `P → S` is itself affine and flat. ✓

> **Slogan.** *Affine flat `G` ⇒ affine flat principal `G`-bundle.* Descent of affineness and flatness via
> VIII.5.6.

______________________________________________________________________

## §XI.4.2 — Associated bundles and twists

<!-- source: XI.4 -->

### The associated-bundle construction

<!-- source: XI.4 -->

Given a principal `G`-bundle `P → S` and an `S`-prescheme `E` with a **left** `G`-action, we want to construct
the **associated bundle** `E^{(P)} := (P \times_S E) / G`. This is the "twist of `E` by `P`".

The `G`-action on `P \times_S E` is the **diagonal** action:

```text
(x, y) \cdot g := (x \cdot g, g^{-1} \cdot y).
```

(In the set-theoretic picture: `(x, y) \mapsto (x g, g^{-1} y)`, with `x` having right action and `y` having left
action, the actions intertwine; the quotient is the orbit space.)

**Construction.** With an fpqc trivialising base change `S' \to S` (so `P \times_S S' \cong G \times_S S'`), the
pulled-back diagonal action of `G` on `P \times_S E \times_S S'` is the action of `G` on `G \times_S E \times_S S'`
given by `(g_0, y) \cdot g = (g_0 g, g^{-1} y)`. The quotient is `E \times_S S'`: the morphism
`(g_0, y) \mapsto g_0 \cdot y` factors through this quotient. So `E^{(P)} \times_S S' \cong E \times_S S'`.

Now we **descend** `E^{(P)}` from `S'` to `S` via fpqc descent. This requires checking the descent datum on
`S'' := S' \times_S S'`. The descent datum is constructed from the fact that the two pull-backs of `P \times_S E$
to `S''` are canonically isomorphic via the `G`-cocycle defining `P` (Vistoli §4.6 in
[`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained); more concretely, the cocycle for `P`
trivialised over `S'` lives in `G(S'')`).

By **VIII.2.1** (file 41), the descent is effective when `E` is **affine** over `S` (and `G` is qcaffine), so the
quotient `E^{(P)}` exists as an `S`-prescheme:

```text
E^{(P)} := (P \times_S E) / G \quad \text{(exists when $E$ is affine; descent via VIII.2.1).}
```

**Twist of structure-group homomorphism.** Given a homomorphism of `S`-groups `\phi : G \to H` and a principal
`G`-bundle `P`, set `E := H` with left `G`-action via `\phi`. Then `E^{(P)} = (P \times_S H) / G` is a principal
`H`-bundle. This is the **induced bundle**:

```text
\text{ind}_G^H : H^1(S, G) \to H^1(S, H), \qquad [P] \mapsto [(P \times_S H)/G].
```

(See V.2.6, file 30, for the étale-finite analogue.)

> **Slogan.** *Associated bundles and structure-group twists exist; they are constructed by fpqc descent.*

______________________________________________________________________

## §XI.4.3 — `H⁰` and `H¹`

<!-- source: XI.4.4 -->

### Definition XI.4.4 — H⁰ and H¹

<!-- source: XI.4.4 -->

**Definition XI.4.4.** Let `G` be an `S`-group.

- `H^0(S, G) := \Gamma(S, G) = \text{Hom}_S(S, G)` is the **set of sections** of `G` over `S`. When `G` is a group,
  this is a group.

- `H^1(S, G) := \{[P] : P \text{ a principal homogeneous bundle under } G \}` is the **set of isomorphism classes
  of principal `G`-bundles**, with basepoint corresponding to the **trivial** bundle `G \to S` itself.

#### Group structure on `H¹` for commutative `G`.

When `G` is a *commutative* affine `S`-group, the set `H^1(S, G)` becomes an **abelian group** under the following
operation: given two principal `G`-bundles `P, Q`, form their **Baer sum**:

```text
P + Q := (P \times_S Q) / G,
```

where `G` acts diagonally on `P \times_S Q$ as `g \cdot (p, q) = (p \cdot g, q \cdot g^{-1})`. (This uses the
commutativity of `G$: if `G$ were non-commutative, the diagonal action might fail to be free, and the quotient
might not be a principal bundle.) The trivial bundle is the identity; the inverse of `P$ is `P$ with the
**inverted** `G$-action (`p \cdot g := p \cdot g^{-1}$).

So `H^1(S, G)` is a contravariant functor on `(\text{commutative affine } S\text{-groups})` to the category of
abelian groups, sending products to products.

> **Slogan.** *`H^0$ is sections; `H^1$ is principal bundles; both functors send products to products. For
> commutative `G$, `H^1(S, G)$ is an abelian group.*

______________________________________________________________________

## §XI.4.4 — The six-term cohomology exact sequence

<!-- source: XI.4.5 -->

### Definition — exact sequence of `S`-groups

<!-- source: XI.4.5 -->

A sequence of commutative affine `S`-groups `0 \to G' \to G \to G'' \to 0` is called **exact** if:

(i) the composition `G' \to G \to G''` is zero;

(ii) `G \to G''` makes `G` into a **principal homogeneous bundle** over `G''` under the structure group
    `G' \times_S G''$ (viewed as a group scheme over `G''` via projection).

Condition (i) makes `G'$ a sub-`S$-group of `G$. Condition (ii) is the "kernel-cokernel" generalisation of
"`G \to G''` is surjective with kernel `G'`" appropriate to descent.

In particular: condition (ii) implies `G \to G''` is **faithfully flat quasi-compact** (the structural morphism
of a principal bundle is fpqc by XI.4.2). So an exact sequence in this sense is, in particular, a "surjection
with kernel `G'`" in the fpqc topology.

### Theorem XI.4.5 — the six-term sequence

<!-- source: XI.4.5 -->

**Theorem XI.4.5.** Let `0 \to G' \to G \to G'' \to 0` be an exact sequence of commutative affine `S`-groups in
the sense above. Then there is a **canonical exact sequence** of abelian groups

```text
0 \to H^0(S, G') \to H^0(S, G) \to H^0(S, G'') \xrightarrow{\partial} H^1(S, G') \to H^1(S, G) \to H^1(S, G''),
```

natural in the exact triple `(G', G, G'')` and in `S`.

*This result says:* fpqc cohomology of commutative `S$-groups has a six-term exact sequence attached to a short
exact sequence of `S$-groups, exactly analogous to classical sheaf cohomology.

**Proof.** The proof reproduces the standard six-term construction:

**Step 1 — Exactness at `H^0(S, G')`.** The map `H^0(S, G') \to H^0(S, G)$ is injective because `G' \to G$ is a
mono (i.e., `(G \to G''$ has kernel `G'$ implies `G' \to G$ is a closed immersion at the level of group schemes).

**Step 2 — Exactness at `H^0(S, G)`.** Standard kernel-cokernel.

**Step 3 — The connecting map `\partial$.** Given a section `f : S \to G''$ — i.e., an element of `H^0(S, G'')$ —
form the **pullback** along `f$ of the principal `G'$-bundle `G \to G''$:

```text
P_f := f^*(G) = G \times_{G''} S \quad \text{(via } f \text{)}.
```

This is the inverse image of the subscheme `\{f(s) : s \in S\} \subset G''$ in `G$. The `G'$-action on `G$ (by
the kernel embedding `G' \hookrightarrow G$) restricts to a `G'$-action on `P_f$. By construction, `P_f \to S$ is
the pullback of an fpqc morphism, hence fpqc, hence is a principal `G'$-bundle (by XI.4.2).

Set `\partial(f) := [P_f] \in H^1(S, G')$. One verifies:

- `\partial$ is a group homomorphism: `\partial(f_1 + f_2) = \partial(f_1) + \partial(f_2)$ (via the Baer sum).
- The image of `\partial$ lies in the kernel of `H^1(S, G') \to H^1(S, G)$: the pullback `f^*(G)$ becomes trivial
  as a principal `G$-bundle (because pulled back over `f$, it has a section, namely the diagonal section
  `(g, s) \mapsto g \cdot s$ at level of sets).

**Step 4 — Exactness at `H^1(S, G')`.** If `P' \in H^1(S, G')$ has trivial image in `H^1(S, G)$, then
`(P' \times_S G) / G' = G$ (trivial). One checks: this happens iff `P'$ comes from a section `f : S \to G''$ via
`\partial$. The argument is essentially Yoneda + the principal-bundle definition.

**Step 5 — Exactness at `H^1(S, G)`.** Standard.

This completes the proof. ∎

> **Slogan.** *Six-term exact sequence for fpqc cohomology of commutative `S$-groups: the algebraic-geometric
> analogue of the topological six-term sequence in `H^1$ for a short exact sequence of abelian sheaves.*

______________________________________________________________________

## §XI.4.5 — Variants: quasi-projective, locally trivial, higher Weil cohomology, non-commutative

<!-- source: XI.4.6 -->

### Variant XI.4.6 — quasi-projective structure groups

<!-- source: XI.4.6 -->

**Variant.** When `G$ is **quasi-projective** over `S$ (instead of affine), the same XI.4.1–XI.4.5 framework
works, with VIII.7.7 (Theorem of effective fpqc descent for fibred categories of quasi-projective `S$-schemes,
file 43) replacing VIII.2.1 in the descent step. This variant is **needed** to handle abelian schemes
`A \to S$, which are quasi-projective but not affine.

> **Slogan.** *Quasi-projective version uses VIII.7.7 instead of VIII.2.1 for descent.*

### Variant XI.4.7 — locally trivial bundles

<!-- source: XI.4.7 -->

**Variant.** Demand the trivialising base change `S' \to S$ to be Zariski (not fpqc): there exists a Zariski cover
`\{U_i \to S\}` such that `P|_{U_i} \cong G|_{U_i}$ as a `G|_{U_i}$-space. This gives a **smaller** class than
XI.4.1: every Zariski-locally trivial bundle is fpqc-locally trivial, but not conversely.

The corresponding `H^1_{Zar}(S, G) \subset H^1(S, G)$ is the **Zariski-sheaf cohomology** of the sheaf of `G$-sections
`\mathcal{O}_X(G)$. For Kummer / Artin–Schreier theory in §XI.6, we will need both pictures: the fpqc `H^1$ and
the Zariski `H^1$, related by an injection. The injection is an iso for `G = GL_n, 𝔾_m, 𝔾_a$ by XI.5 below.

> **Slogan.** *Zariski-locally trivial ⊂ fpqc-locally trivial; equality for GL_n, 𝔾_m, 𝔾_a.*

### Variant XI.4.8 — higher Weil cohomology `H^i(S, G)$

<!-- source: XI.4.8 -->

**Variant (pointer).** Define the **Weil cohomology** of `S$ as the derived functors of the global-sections
functor `\Gamma : \text{Sh}_{fpqc}(S) \to \text{Ab}$, restricted to abelian Weil sheaves on the site
`(\text{quasi-compact preschemes / S}, \text{fpqc})$. This gives higher cohomology groups `H^i(S, \mathcal{F})$ for
`\mathcal{F}$ an abelian Weil sheaf, with `H^0 = \Gamma(S, \cdot)$ and `H^1 = `classical $H^1$$ in the sense above.

Every commutative `S$-group defines such a Weil sheaf (its functor of points), and the XI.4.5 six-term sequence
extends to a **long exact sequence**:

```text
\cdots \to H^i(S, G') \to H^i(S, G) \to H^i(S, G'') \to H^{i+1}(S, G') \to \cdots.
```

This is the framework Grothendieck developed in SGA 4 I–IX. The higher `H^i$ are not central to Exposé XI; the
six-term sequence (XI.4.5) is what we need for Kummer and Artin–Schreier theories. We mention the higher
cohomology only as a pointer forward to SGA 4.

> **Slogan.** *Higher Weil cohomology `H^i(S, G)$ exists; see SGA 4 for the systematic framework.*

### Variant XI.4.9 — non-commutative

<!-- source: XI.4.9 -->

**Variant (pointer).** For non-commutative `G$, the set `H^1(S, G)$ is no longer an abelian group — it is only a
*pointed* set. The XI.4.5 six-term sequence becomes an **exact sequence of pointed sets** for the first few terms,
with `\partial : H^0(S, G'') \to H^1(S, G')$ a map of pointed sets but not a group homomorphism. The full
non-commutative `H^2$ and beyond is developed in J. Giraud's *Cohomologie non abélienne* (Springer 1971; appendix
[`giraud-cohomologie-non-abelienne`](appendix-black-boxes.md#giraud-cohomologie-non-abelienne)).

> **Slogan.** *For non-commutative `G$, `H^1(S, G)$ is a pointed set; full theory in Giraud 1971.*

______________________________________________________________________

## §XI.5.1 — `H¹(S, GL_n)$, `H¹(S, 𝔾_m)$, `H¹(S, 𝔾_a)$ are Zariski-locally trivial

<!-- source: XI.5.1 -->

### Theorem XI.5.1 — Zariski-local triviality for GL_n, 𝔾_m, 𝔾_a

<!-- source: XI.5.1 -->

**Theorem XI.5.1.** Let `S$ be a prescheme and let `G$ be one of the `S$-groups:

(a) `GL_{n, S}$ for some integer `n \geq 0$ (the general linear group of rank `n$);

(b) `𝔾_{m, S} = \text{Spec } \mathcal{O}_S[t, t^{-1}]$ (the multiplicative group);

(c) `𝔾_{a, S} = \text{Spec } \mathcal{O}_S[t]$ (the additive group).

Then every principal homogeneous bundle under `G$ is **Zariski-locally trivial**. Equivalently, the inclusion
`H^1_{Zar}(S, G) \subset H^1_{fpqc}(S, G)$ is an **isomorphism**.

*This result says:* for these special groups, the fpqc topology of XI.4.1 collapses to the Zariski topology.
Principal `GL_n$-bundles are just **locally-free rank-`n$ sheaves**; principal `𝔾_m$-bundles are **line bundles**;
principal `𝔾_a$-bundles are **extensions of `\mathcal{O}_S$ by `\mathcal{O}_S$**.

**Proof of (a) GL_n.**

The functor `T \mapsto GL_n(T) = GL(n, \Gamma(T, \mathcal{O}_T))$ is represented by `GL_{n, S}$. Concretely, the
automorphism functor of the trivial rank-`n$ locally-free sheaf is `T \mapsto \text{Aut}(\mathcal{O}_T^n)$.

By **VIII.1.12** (file 41), the **fpqc morphisms** are morphisms of effective descent for the fibred category of
locally-free sheaves of rank `n$. Hence, a principal `GL_n$-bundle `P \to S$, fpqc-locally trivial by definition,
descends to a locally-free rank-`n$ sheaf `\mathcal{E}$ on `S$ — i.e., `P$ is the **frame bundle** of some
locally-free `\mathcal{E}$ on `S$.

But locally-free sheaves of rank `n$ on `S$ are by definition **Zariski-locally** of the form `\mathcal{O}_S^n$ on
some open cover. So the frame bundle `P$ is **Zariski-locally trivial** on `S$. ✓

**Proof of (b) 𝔾_m.** Special case of (a) with `n = 1$: `𝔾_m \cong GL_1$, and locally-free rank-1 sheaves are
exactly **line bundles**.

**Proof of (c) 𝔾_a.**

The functor `T \mapsto 𝔾_{a, S}(T) = \Gamma(T, \mathcal{O}_T)$ is the additive group. A principal `𝔾_a$-bundle
`P \to S$ corresponds to an **extension** of `\mathcal{O}_S$ by `\mathcal{O}_S$:

```text
0 \to \mathcal{O}_S \to \mathcal{E} \to \mathcal{O}_S \to 0.
```

By the **descent theory for extensions** (VIII.1.1, file 41, extended to the fibred category of `\mathcal{O}_S$-
modules with extension structure), fpqc-locally trivial extensions are exactly Zariski-locally trivial extensions
— in fact, **all** extensions of `\mathcal{O}_S$ by `\mathcal{O}_S$ are Zariski-locally trivial, because every
locally-free module on an affine open is free, and extensions over an affine are classified by `\text{Ext}^1_{
\mathcal{O}}( \mathcal{O}, \mathcal{O}) = 0$ on an affine (using Serre vanishing for affines, appendix
[`serre-affine-vanishing`](appendix-black-boxes.md#serre-affine-vanishing)).

Hence principal `𝔾_a$-bundles are Zariski-locally trivial. ✓

> **Slogan.** *GL_n, 𝔾_m, 𝔾_a are "tame" in that their fpqc `H^1$ agrees with their Zariski `H^1$.*

______________________________________________________________________

### Remark XI.5.2 — symplectic and orthogonal variants

<!-- source: XI.5.2 -->

**Remark.** The **symplectic** group `\text{Sp}(2n)_S$ also satisfies XI.5.1: its principal bundles are
Zariski-locally trivial. The argument is the same: principal `\text{Sp}(2n)$-bundles correspond to
locally-free rank-`2n$ sheaves with a non-degenerate alternating form, and any such form is Zariski-locally the
standard one (by a structure theorem in linear algebra).

By contrast, the **orthogonal** group `O(n)$ does *not* satisfy the analogous statement: there exist quadratic
forms over a local ring that are **not** isomorphic to the standard form. So `H^1(S, O(n))$ contains genuinely
non-Zariski-locally-trivial classes (corresponding to non-trivial quadratic forms). This is one of the first
obstructions to a "Zariski-collapses-everything" theorem.

(For the structure theorem on which groups satisfy XI.5.1, see Grothendieck *Torsion homologique et sections
rationnelles*, Séminaire Chevalley 1958, reference XI.3 in the SGA bibliography. The general answer: groups that
can be "dévissés" — built up by successive extensions — from `GL$, `𝔾_m$, `𝔾_a$, `\text{Sp}$ are exactly the
ones where every principal bundle is Zariski-locally trivial.)

> **Slogan.** *Sp behaves like GL and 𝔾_m; O does not.* Symplectic and linear groups have "tame" `H^1$; orthogonal
> groups have genuine `H^1$.*

______________________________________________________________________

## §XI.5.3 — Classical interpretations of `H¹(S, GL_n)$, `H¹(S, 𝔾_m)$, `H¹(S, 𝔾_a)$

<!-- source: XI.5.3 -->

### Corollary XI.5.3 — explicit classical identifications

<!-- source: XI.5.3 -->

**Corollary XI.5.3.** There are canonical bijections, natural in `S$:

```text
H^1(S, GL_n) \cong H^1(S, GL_n(\mathcal{O}_S)),
```

```text
H^1(S, 𝔾_m) \cong H^1(S, \mathcal{O}_S^*) = \text{Pic}(S),
```

```text
H^1(S, 𝔾_a) \cong H^1(S, \mathcal{O}_S),
```

where the right-hand sides are **ordinary Zariski-sheaf cohomology** of the corresponding sheaves on `S$.

#### Restatements of XI.5.3.

- `H^1(S, GL_n)$ = isomorphism classes of **locally-free rank-`n$ sheaves** on `S$.
- `H^1(S, 𝔾_m)$ = **Picard group** `\text{Pic}(S)$ = isomorphism classes of line bundles.
- `H^1(S, 𝔾_a)$ = isomorphism classes of **extensions** `0 \to \mathcal{O}_S \to \mathcal{E} \to \mathcal{O}_S \to
  0$ of structure-sheaf modules.

**Proof.** By XI.5.1, every principal `GL_n$-bundle is Zariski-locally trivial. Its class in `H^1(S, GL_n) = $
fpqc-`H^1$ equals its class in Zariski-`H^1(S, GL_n)$, which by the standard definition of Zariski-sheaf
cohomology is `H^1(S, GL_n(\mathcal{O}_S))$. Specialising to `n = 1$ recovers `\text{Pic}(S) = H^1(S, 𝔾_m)$.

For `𝔾_a$: the same XI.5.1 argument gives `H^1(S, 𝔾_a) = H^1(S, 𝒪_S)$. ✓

> **Slogan.** *`H^1(S, GL_n) \leftrightarrow $ rank-`n$ vector bundles; `H^1(S, 𝔾_m) = \text{Pic}(S)$;
> `H^1(S, 𝔾_a) = H^1(S, 𝒪_S)$.* These are the **classical** interpretations.

______________________________________________________________________

## Closing of file 55

We extended the principal-cover notion of V.2.7 (file 30) from finite étale `G$ to arbitrary quasi-compact flat
affine `S$-groups, in the **fpqc** sense (XI.4.1). We proved the criterion XI.4.2 (`P → S$ principal homogeneous
iff `P → S$ formally principal homogeneous + structure morphism fpqc), the affineness corollary XI.4.3, the
associated-bundle / twist construction (§XI.4.2), and the **six-term cohomology exact sequence** XI.4.5 attached
to a short exact sequence of commutative `S$-groups. The §XI.4.5 variants (quasi-projective, locally trivial,
higher Weil, non-commutative) sketched the wider framework.

In §XI.5, we proved that **GL_n, 𝔾_m, 𝔾_a have Zariski-locally trivial principal bundles** (XI.5.1), so their
fpqc-`H^1$ equals their classical Zariski-`H^1$ (XI.5.3): rank-`n$ vector bundles, `\text{Pic}(S)$, and
`H^1(S, 𝒪_S)$ respectively.

Next, file 56 (final gentle file of Exposé XI) feeds two specific exact sequences into the XI.4.5 machine:

- **Kummer:** `0 \to \mu_n \to 𝔾_m \to 𝔾_m \to 0$ (`n$-th power, `n$ prime to char). The output: `H^1(S, \mu_n) =
  $ Kummer covers of `S$, with the resulting six-term sequence relating `H^1(S, \mu_n)$ to `\text{Pic}(S)$ via
  XI.5.3.

- **Artin–Schreier:** `0 \to \mathbb{Z}/p\mathbb{Z} \to 𝔾_a \to 𝔾_a \to 0$ (`wp = id − F$ in characteristic `p$).
  The output: `H^1(S, \mathbb{Z}/p\mathbb{Z}) = $ Artin–Schreier covers, with the resulting six-term sequence
  relating it to `H^1(S, 𝒪_S)$ via XI.5.3.

The culminating remark XI.6.11 ties everything to the **Cartier-duality master formula** `H^1(S, G) \cong
\text{Hom}(D(G), \text{Pic}_{S/k})$, which links the file-53 "true fundamental group" of an abelian variety to
the Picard scheme.
