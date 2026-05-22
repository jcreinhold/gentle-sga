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
the obstruction in $H^{1}(Y_{0}, \mathcal{G})$ for a sheaf $\mathcal{G}$ built from $\Omega^{1}$ and the square-zero
ideal. **Section III.6** handles the harder question — extending a **scheme** itself — and finds the obstruction in
$H^{2}(X_{0}, \mathcal{G})$ for a sheaf $\mathcal{G}$ built from the **tangent sheaf** $\mathfrak{g}_{X_{0}/S_{0}}$ and
a graded piece of the ideal $\mathcal{I}$. The H² calculation is Grothendieck's "silly cocycle calculation," done
because the more conceptual treatment in Giraud's _Cohomologie non abélienne_ was, at the time, unwritten.

The cohomological machinery ($H^{1}$ as torsors, $H^{2}$ as gluing obstructions, Leray's acyclic-cover theorem, the
tangent sheaf $\mathfrak{g}_{X/S}$) is in **file 17**. Formal schemes and the algebraization theorem are in **file 18**.
The local lifting result (III.4.1) is in **file 20**. We freely cite all three.

The slogan that runs through:

> **Local lifts always exist; global lifts have a cohomological obstruction.** For a morphism: H¹ is the obstruction;
> vanishing H¹ guarantees a global lift, and the set of lifts is a torsor under H⁰ of the same coefficient sheaf. For a
> smooth scheme: H² is the obstruction; vanishing H² guarantees a global smooth lift, and the set of isomorphism classes
> of lifts is a torsor under H¹ of the tangent sheaf.

## III.5 Global infinitesimal extension of morphisms

<!-- source: III.5 -->

### Setup: formally principal homogeneous sheaves

We recall from file 17 the basic objects. Let $T$ be a topological space and $\mathcal{G}$ a sheaf of (commutative)
groups on $T$. A sheaf of sets $\mathcal{P}$ on $T$ is **formally principal homogeneous** under $\mathcal{G}$ if the
natural map $\mathcal{G} \times \mathcal{P} \to \mathcal{P} \times \mathcal{P}$ (sending
$(g, p) \mapsto (p \cdot g, p)$) is an isomorphism. Equivalently: on each open $U$, the set $\mathcal{P}(U)$ is **either
empty or a principal homogeneous space** under $\mathcal{G}(U)$ in the usual sense.

$\mathcal{P}$ is a **principal homogeneous sheaf** under $\mathcal{G}$ (or a **torsor under $\mathcal{G}$**) if in
addition all stalks $\mathcal{P}_{x}$ are nonempty; equivalently, $\mathcal{P}$ is locally trivial as a
$\mathcal{G}$-set. The set of isomorphism classes of torsors under $\mathcal{G}$ is in natural bijection with
$H^{1}(T, \mathcal{G})$ — this is the central classifying theorem of file 17 (Giraud's classification, appendix row
`giraud-torsor`).

For a torsor $\mathcal{P}$, the cohomology class $c(\mathcal{P}) \in H^{1}(T, \mathcal{G})$ vanishes iff $\mathcal{P}$
is trivial (i.e., admits a global section). For a formally principal homogeneous sheaf $\mathcal{P}$ that is not yet
known to have a global section, the cohomology class vanishes iff the sheaf has **enough** sections — globally, on every
open of a trivializing cover.

This is the language of §III.5. The setup will be:

- A morphism $g_{0} : Y_{0} \to X$ over $S$ and a square-zero ideal $\mathcal{J} \subset \mathcal{O}_{Y}$ defining a
  closed sub-prescheme $Y_{0} \subset Y$.
- The sheaf $\mathcal{P}(g_{0})$ on $Y$ whose sections over an open $U \subset Y$ are the morphisms $g : U \to X$ over
  $S$ that extend $g_{0}|_{U \cap Y_{0}}$.
- The claim: $\mathcal{P}(g_{0})$ is formally principal homogeneous under a specific sheaf of groups $\mathcal{G}$ built
  from $\Omega^{1}$ and $\mathcal{J}$.

### Proposition: $\mathcal{P}(g_{0})$ is formally principal homogeneous

<!-- source: III.5.1 -->

_This proposition says: the sheaf of extensions of $g_{0}$ along a square-zero thickening is, naturally, a formally
principal homogeneous sheaf under a sheaf of derivation-valued maps. The proof is the construction of the bijection
between the two — a local diagonal / first-order-neighborhood calculation._

**Proposition III.5.1.** *Let $S$ be a prescheme, $X$ and $Y$ preschemes over $S$, and $Y_{0} \subset Y$ a closed
sub-prescheme defined by a sheaf of ideals $\mathcal{J}$ on $Y$ of **square zero**. Let $g_{0} : Y_{0} \to X$ be an
$S$-morphism, and let $\mathcal{P}(g_{0})$ be the sheaf on $Y$ whose sections on an open $U \subset Y$ are the
extensions $g : U \to X$ of $g_{0}|_{U \cap Y*0}$to an$S$-morphism $g$. Then $\mathcal{P}(g_{0})$ is, naturally, a
**formally principal homogeneous** sheaf under the commutative sheaf of groups*

```text
𝒢 := ℋ𝓂_{𝒪_{Y₀}}(g₀^* (Ω¹_{X/S}), 𝒥).
```

**Proof construction.** We construct the action $\mathcal{P}(U) \times \mathcal{G}(U) \to \mathcal{P}(U)$ by giving, for
each fixed $g \in \mathcal{P}(U)$, a canonical bijection $\mathcal{G}(U) \to \mathcal{P}(U)$. The verifications that
this assembles into a sheaf-of-sets action and that the action is principal are mechanical and we omit them; see the
source.

Fix $g \in \mathcal{P}(Y)$ (we may assume $U = Y$ for clarity). We seek a canonical bijection

```text
ℋ𝓂_{𝒪_{Y₀}}(g₀^* (Ω¹_{X/S}), 𝒥) ⟶ 𝒫(Y),
```

where $\mathcal{P}(Y)$ is the set of $S$-morphisms $g' : Y \to X$ inducing the same $g_{0} : Y_{0} \to X$ as $g$.

Giving such a $g'$ is equivalent to giving an $S$-morphism $h : Y \to X \times_{S} X$ such that:

- $pr_{1} \circ h = g$ (the first projection of $h$ is the given $g$),
- $h \circ i = (g_{0}, g_{0}) : Y_{0} \to X \times_{S} X$ (where $i : Y_{0} \to Y$ is the closed immersion).

Since $(g_{0}, g_{0})$ factors through the diagonal $\Delta_{X/S} : X \to X \times_{S} X$ (it is the constant pair), and
since $Y$ lies in the **first-order infinitesimal neighborhood of $Y_{0}$** ($\mathcal{J}^{2} = 0$), the desired $h$
necessarily factors uniquely through the **first-order infinitesimal neighborhood $X^{(1)}$ of the diagonal** in
$X \times_{S} X$.

**Recall from file 03.** This first-order neighborhood $X^{(1)}$ is, as an $X$-scheme via $pr_{1}$, the spectrum of the
sheaf of $\mathcal{O}_{X}$-algebras

$$
\mathcal{O}_{X} \oplus \Omega^{1}_{X/S}
$$

with $\Omega^{1}_{X/S}$ regarded as a square-zero ideal (this is the "square-zero extension by $\Omega^{1}$", file 03,
"What $\Omega^{1}$ represents abstractly"). The diagonal $X \to X^{(1)}$ corresponds to the canonical augmentation that
kills $\Omega^{1}$.

So, putting $Y' := X^{(1)} \times_{X} Y$ (via $g$) and $Y'_{0} := Y' \times_{Y} Y_{0}$, the desired $h$ are in bijective
correspondence with **sections $u$ of $Y' \to Y$ extending the canonical section $u_{0}$ of $Y'_{0} \to Y_{0}$** (which
is the augmentation killing $\Omega^{1}$ when restricted).

We identify $Y'$ with $\operatorname{Spec}_{Y}(\mathcal{A})$ for the sheaf of $\mathcal{O}_{Y}$-algebras

```text
𝒜 := g^*(𝒪_X ⊕ Ω¹_{X/S}) = 𝒪_Y ⊕ g^*(Ω¹_{X/S}),
```

and $Y'_{0}$ with $\operatorname{Spec}_{Y_{0}}(\mathcal{A}_{0})$ for
$\mathcal{A}_{0} := \mathcal{A} \otimes_{\mathcal{O}_{Y}} \mathcal{O}_{Y_{0}} = \mathcal{O}_{Y_{0}} \oplus g^{*}_{0}(\Omega^{1}_{X/S})$.
The canonical section $u_{0}$ is the augmentation of $\mathcal{A}_{0}$.

So $\mathcal{P}(Y)$ identifies with the set of $\mathcal{O}_{Y}$-algebra maps $\mathcal{A} \to \mathcal{O}_{Y}$ inducing
the augmentation $\mathcal{A}_{0} \to \mathcal{O}_{Y_{0}}$. Algebra maps $\mathcal{A} \to \mathcal{O}_{Y}$ correspond
bijectively to module maps $g^{*}(\Omega^{1}_{X/S}) \to \mathcal{O}_{Y}$ (because
$\mathcal{A} = \mathcal{O}_{Y} \oplus g^{*}(\Omega^{1}_{X/S})$ has the square-zero ideal $g^{*}(\Omega^{1}_{X/S})$). The
condition that the algebra map induces the canonical augmentation on $\mathcal{A}_{0}$ says **the module map sends
$g^{*}(\Omega^{1}_{X/S})$ into the ideal $\mathcal{J}$** (the kernel of $\mathcal{O}_{Y} \to \mathcal{O}_{Y_{0}}$). So
we get the set

```text
ℋ𝓂_{𝒪_Y}(g^*(Ω¹_{X/S}), 𝒥) = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X/S}), 𝒥)
```

(the second equality because $\mathcal{J}$ is annihilated by $\mathcal{J}$, so it is naturally an
$\mathcal{O}_{Y_{0}}$-module). This is the desired bijection. ∎

In words: **extensions of $g_{0}$ along the square-zero thickening $Y_{0} \hookrightarrow Y$ correspond bijectively to
derivations from $\mathcal{O}_{X}$ (pulled back to $Y_{0}$) into the square-zero ideal $\mathcal{J}$** — once one fixed
extension is chosen.

### Corollary: smooth case, torsor under $\mathcal{G}$

<!-- source: III.5.2 -->

_This corollary says: when $X$ is smooth over $S$, the sheaf of extensions $\mathcal{P}(g_{0})$ is not just formally
principal homogeneous — it is a **torsor**. Equivalently, **local** extensions exist, so the obstruction to a **global**
extension is exactly the cohomology class of the torsor in $H^{1}(Y_{0}, \mathcal{G})$._

**Corollary III.5.2.** _If $X$ is **smooth** over $S$ at the points of $g_{0}(Y_{0})$, then $\mathcal{P}(g_{0})$ is a
**principal homogeneous sheaf** under the commutative sheaf of groups $\mathcal{G}$. In this case $\mathcal{G}$ may also
be written_

```text
𝒢 = g₀^*(𝔤_{X/S}) ⊗_{𝒪_{Y₀}} 𝒥,
```

_where $\mathfrak{g}_{X/S}$is the **tangent sheaf** of$X$over$S$(file 17): the dual of$\Omega^{1}_{X/S}$. This rewriting
holds because $\Omega^{1}_{X/S}$is locally free of finite type when$X$is smooth over$S$ (file 15, II.4.3)._

_In particular, this principal homogeneous sheaf determines a **cohomology class in $H^{1}(Y_{0}, \mathcal{G})$**, whose
vanishing is necessary and sufficient for the existence of an $S$-morphism $g$ extending $g_{0}$. If such an extension
exists, the set of all possible extensions is a homogeneous space under $H^{0}(Y_{0}, \mathcal{G})$._

**Proof sketch.** Smoothness of $X$ over $S$ gives, by III.3.1 condition (iii) (file 20), the **local existence** of
extensions of $g_{0}$. So for every $y \in Y_{0}$ there is an open neighborhood of $y$ over which $\mathcal{P}(g_{0})$
has a section — the sheaf is **locally trivializable**, hence (combined with the formally principal homogeneous
structure of III.5.1) a torsor.

The rewriting of $\mathcal{G}$ uses $\Omega^{1}$ locally free for smooth:
$\mathcal{Hm}(\Omega^{1}, \mathcal{J}) = (\Omega^{1})^{\vee} \otimes \mathcal{J} = \mathfrak{g} \otimes \mathcal{J}$
when $\Omega^{1}$ is locally free. The cohomological classification is from file 17: torsors under $\mathcal{G}$
correspond to $H^{1}(Y_{0}, \mathcal{G})$, and the trivial class corresponds to torsors with global sections.

For the H⁰ statement: given two extensions `g, g'` of $g_{0}$, the "difference" is a section of $\mathcal{G}$, i.e. a
derivation from $g^{*}_{0} \Omega^{1}_{X/S}$ into $\mathcal{J}$; conversely any such derivation modifies one extension
into another. So the set of extensions, when nonempty, is a torsor under $H^{0}(Y_{0}, \mathcal{G})$ — but
$H^{0}(Y_{0}, \mathcal{G}) = \Gamma(Y_{0}, \mathcal{G})$ is just global sections. ∎

This is the **first cohomological theorem of Exposé III**. The H¹ obstruction to extending a morphism is the carrier of
all subsequent cohomological reasoning in §III.6 and §III.7.

### Step-by-step extension along thickenings

<!-- source: III.5.3 -->

*This corollary says: when one extends a morphism through a chain of thickenings
$S \supset S_{n} \supset S_{n-1} \supset \cdots \supset S*0$, each step is the square-zero situation of III.5.1, and the
obstruction lives in H¹ of a sheaf built from $\Omega^{1}$and the graded piece$gr^{n+1}_{\mathcal{I}} (\mathcal{O}*Y)$.*

**Setup.** Let $S$ be a prescheme equipped with a coherent sheaf of ideals $\mathcal{I}$, and let
$S_{n} := V(\mathcal{I}^{n+1})$ for each $n \geq 0$. For preschemes $X$ and $Y$ over $S$, let
$X_{n} := X \times_{S} S_{n}$ and $Y_{n} := Y \times_{S} S_{n}$. Suppose we are given an $S_{n}$-morphism

$$
g_{n} : Y_{n} \longrightarrow X_{n},
$$

equivalently an $S$-morphism $Y_{n} \to X$ (or an $S_{n+1}$-morphism $Y_{n} \to X_{n+1}$). We seek to extend it to an
$S_{n+1}$-morphism

$$
g_{n+1} : Y_{n+1} \longrightarrow X_{n+1}.
$$

This is the situation of III.5.1 with $S$ replaced by $S_{n+1}$, $X$ by $X_{n+1}$, $Y$ by $Y_{n+1}$, $Y_{0}$ by $Y_{n}$,
$g_{0}$ by $g_{n}$, and $\mathcal{J}$ by

```text
𝒥 = 𝓘^{n+1} 𝒪_Y / 𝓘^{n+2} 𝒪_Y.
```

The square-zero condition $\mathcal{J}^{2} = 0$ is automatic since
$\mathcal{I}^{n+1} \cdot \mathcal{I}^{n+1} = \mathcal{I}^{2n+2} \subset \mathcal{I}^{n+2}$ for $n \geq 0$.

**Corollary III.5.3.** *Let $S, X, Y, \mathcal{I}, g_{n}$ be as above. Let $\mathcal{P}(g_{n})$ be the sheaf on $Y$
whose sections on an open $U$ are the extensions $g_{n+1}$of$g_{n}$to an$S_{n+1}$-morphism $Y_{n+1} \to X_{n+1}$. Then
$\mathcal{P}(g_{n})$ is a **formally principal homogeneous** sheaf under the sheaf of groups*

```text
𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X₀/S₀}), gr^{n+1}_{𝓘 𝒪_Y}(𝒪_Y)),
```

*where $g_{0} : Y_{0} \to X_{0}$ is the morphism induced by $g_{n}$ (and the inverse image of
$\Omega^{1}_{X_{n+1}/S_{n+1}}$on$X*0$is$\Omega^{1}_{X*0/S_{0}}$).*

**Proof sketch.** Direct application of III.5.1 with the identifications above. The simplification
$\Omega^{1}_{X_{n+1}/S_{n+1}} |_{X_{0}} = \Omega^{1}_{X_{0}/S_{0}}$ follows from the compatibility of Kähler
differentials with base change (file 03, "Two exact sequences"). The pullback $g^{*}_{n}(\Omega^{1}_{X_{n+1}/S_{n+1}})$
on $Y_{0}$ reduces to $h^{*}_{0}(\Omega^{1}_{X_{0}/S_{0}})$, where $h_{0} : Y_{0} \to X_{0}$ is induced; and since
$\mathcal{J}$ is annihilated by $\mathcal{I} \mathcal{O}_{Y}$, only the restriction to $Y_{0}$ matters. ∎

### Smooth case, step-by-step

<!-- source: III.5.4 -->

_This corollary says: when $X$ is smooth over $S$, the formally principal homogeneous sheaf of III.5.3 is a torsor, and
the obstruction to extending $g_{n}$ to $g_{n+1}$ is a cohomology class in H¹._

**Corollary III.5.4.** *If $X$ is **smooth over $S$** (at the points of $g_{0}(Y_{0})$), then $\mathcal{P}(g_{n})$ is a
principal homogeneous sheaf, and defines an obstruction class in $H^{1}(Y_{0}, \mathcal{G})$. Vanishing of this class is
necessary and sufficient for the existence of a global extension $g_{n+1}$of$g_{n}$. If the extension exists, the set of
extensions is a principal homogeneous space under $H^{0}(Y_{0}, \mathcal{G})$.*

_The sheaf $\mathcal{G}$ may then also be written_

```text
𝒢 = g₀^*(𝔤_{X₀/S₀}) ⊗_{𝒪_{Y₀}} gr^{n+1}_{𝓘 𝒪_Y}(𝒪_Y).
```

**Proof sketch.** Combine III.5.2 with III.5.3. Smoothness of $X$ over $S$ gives smoothness of $X_{0}$ over $S_{0}$
(file 15, II.3.x), hence local extension of $g_{0}$, hence the formally principal homogeneous sheaf is a torsor. The
cohomological classification (file 17) gives the H¹ obstruction. The rewriting of $\mathcal{G}$ uses local freeness of
$\Omega^{1}_{X_{0}/S_{0}}$ (file 15, II.4.3). ∎

This is the **iterated step**. To extend $g_{0} : Y_{0} \to X_{0}$ to arbitrarily high thickenings, we need the H¹
obstructions to vanish at every step:

```text
H¹(Y₀, g₀^*(𝔤_{X₀/S₀}) ⊗ gr^n_{𝓘 𝒪_Y}(𝒪_Y)) = 0   for all n ≥ 1.
```

This is rare in general, but happens in special cases (affine $Y_{0}$, free $gr^{n}$, etc.) — addressed in III.5.5
below.

### Affine case: existence of a global extension

<!-- source: III.5.5 -->

_This corollary says: when $Y_{0}$ is affine, the H¹ obstructions vanish trivially (Serre vanishing), so step-by-step
extension works for every n. Combined with III.3.1, this gives a stronger form of the lifting characterization that the
original proof of III.3.1 could not give._

**Corollary III.5.5.** _In the statement of Theorem III.3.1, one obtains a necessary and sufficient condition equivalent
to the others by supposing that the test prescheme $Y'$ (in (ii) or (ii bis)) is **affine**, and by requiring the
existence of a **global extension $g$** of $g_{0}$ to all of $Y'$ (rather than merely a local extension)._

_The proof of III.3.1 could not have given this result directly — III.3.1 was proved by reducing to the lifting property
characterization of formal smoothness (III.2.1, file 19), which gives only local extensions._

**Proof sketch.** When $Y'$ (and hence $Y'_{0}$) is affine, the cohomology $H^{1}(Y'_{0}, \mathcal{G})$ vanishes for any
**quasi-coherent** $\mathcal{G}$ by Serre's affine vanishing (appendix `serre-affine-vanishing`, file 17). So the H¹
obstruction in III.5.4 is zero at every step, and step-by-step extension produces a global lift. ∎

### Free graded case: obstruction calculation

<!-- source: III.5.6 -->

_This corollary says: in the important case where $Y$ is flat over $S$ and the graded pieces $gr^{n}(\mathcal{O}_{S})$
are locally free, the H¹ obstruction at step $n$ factors as a tensor product, and the single condition
$H^{1}(Y_{0}, \mathcal{G}_{0}) = 0$ (with $\mathcal{G}_{0}$ the tangent sheaf pulled back to $Y_{0}$) suffices for
**all** the obstructions to vanish._

**Corollary III.5.6.** _Let $(S, X, Y, \mathcal{I}, g_{n})$ be as in III.5.3. Suppose moreover that $X$ is smooth over
$S$ and $Y$ is flat over $S$, and finally that $S$ is affine (with ring $A$, ideal $I \subset A$) and the_

$$
gr^{n}(\mathcal{O}_{S}) = \mathcal{I}^{n} / \mathcal{I}^{n+1}
$$

_are locally free over $S$. Then the obstruction to constructing $g_{n+1}$ lies in_

```text
H¹(Y₀, 𝒢₀) ⊗_A gr^{n+1}_I(A),
```

*where $\mathcal{G}_{0} = g^{*}_{0}(\mathfrak{g}_{X*0/S_{0}})$. In particular, if $H^{1}(Y_{0}, \mathcal{G}_{0}) = 0$,
then $g_{n}$extends to an`Ŝ`-morphism $\hat{g} : \hat{Y} \to \hat{X}$.*

**Proof sketch.** When $Y$ is flat over $S$, one has

```text
gr^n(𝒪_Y) = gr^n(𝒪_S) ⊗_{𝒪_{S₀}} 𝒪_{Y₀}.
```

When the $gr^{n}(\mathcal{O}_{S})$ are locally free, the $n$-th obstruction sheaf

```text
𝒢 = ℋ𝓂_{𝒪_{Y₀}}(g₀^*(Ω¹_{X₀/S₀}), 𝒪_{Y₀}) ⊗_{𝒪_{S₀}} gr^n(𝒪_S),
```

(by III.5.4 and the rewriting). The tensor product factor $gr^{n} (\mathcal{O}_{S})$, being locally free over $S$, is
acyclic for cohomology on $Y_{0}$. By Serre's affine vanishing on $S$ plus a Künneth-like argument:

```text
H^i(Y₀, 𝒢) = H^i(Y₀, 𝒢₀) ⊗_A gr^n_I(A)   for every i.
```

When $H^{1}(Y_{0}, \mathcal{G}_{0}) = 0$, all $H^{1}(Y_{0}, \mathcal{G})$ vanish, so all obstructions in III.5.4 are
zero. Step-by-step extension produces a compatible system of $g_{n}$, hence a formal-scheme morphism
$\hat{Y} \to \hat{X}$. ∎

### Corollary: when the morphism is an isomorphism

<!-- source: III.5.7 -->

_This corollary says: under the conditions of III.5.6, if $g_{0}$ is an isomorphism, then so is the formal extension
`ĝ`._

**Corollary III.5.7.** _Under the conditions of III.5.6, if $g_{0}$ is an isomorphism, then so is `ĝ`. The same result
holds for **closed immersions**._

**Proof sketch.** Apply Lemma III.4.2 (file 20) at each step: $g_{n}$ is an isomorphism iff $g_{0}$ is an isomorphism
(since $Y_{n}$ is flat over $Y$ over $S$). Take the inverse limit. The variant for closed immersions follows from the
variant of III.4.2 noted there (which doesn't even need flatness). ∎

### Proposition: extending isomorphisms of formal schemes

<!-- source: III.5.8 -->

_This proposition says: in the formal-scheme version, isomorphisms on the closed fiber lift to isomorphisms of the
formal schemes, provided the same H¹ vanishing condition holds. Uniqueness needs H⁰ to vanish too._

**Proposition III.5.8.** *Let $A$ be a complete local ring with maximal ideal $\mathfrak{m}$ and residue field $k$. Let
$\mathfrak{X}, \mathfrak{Y}$ be two $\mathfrak{m}$-adic formal preschemes over $A$, both flat over $A$ (meaning each
$\mathfrak{X}_{n}, \mathfrak{Y}_{n}$ is flat over $A_{n} = A / \mathfrak{m}^{n+1}$). Suppose
$X_{0} = \mathfrak{X} \otimes_{A} k$ is **smooth over $k$** and $H^{1}(X_{0}, \mathfrak{g}_{X*0/k}) = 0$.*

*Then every $k$-isomorphism $Y_{0} \to X_{0}$ extends to an $A$-isomorphism $\mathfrak{Y} \to \mathfrak{X}$. The
extension is unique if moreover $H^{0}(X_{0}, \mathfrak{g}_{X*0/k}) = 0$.*

**Proof sketch.** Existence: apply III.5.6 with $S = \operatorname{Spec} A$, $Y = \mathfrak{Y}$, $X = \mathfrak{X}$, and
$g_{0}$ the given $k$-isomorphism. The hypothesis $H^{1}(X_{0}, \mathfrak{g}_{X_{0}/k}) = 0$ makes all obstructions
vanish. Then by III.5.7 the resulting formal morphism $\hat{g} : \mathfrak{Y} \to \mathfrak{X}$ is an isomorphism (since
$g_{0}$ is).

Uniqueness: two extensions differ by a section of $H^{0}$ of the appropriate sheaf (by III.5.4); if
$H^{0}(X_{0}, \mathfrak{g}_{X_{0}/k}) = 0$, the two extensions coincide at every step, hence agree on the inverse limit.
∎

### Corollary: ordinary proper schemes

<!-- source: III.5.9 -->

_This corollary says: III.5.8's formal statement upgrades to a statement about ordinary proper schemes via the
Grothendieck existence theorem (algebraization)._

**Corollary III.5.9.** _Statement III.5.8 remains valid when $\mathfrak{X}, \mathfrak{Y}$ are replaced by ordinary
$A$-schemes `X, Y` **proper over $A$**._

**Proof sketch.** By the Grothendieck existence theorem (file 18, appendix `grothendieck-existence`), for $A$ complete
and `X, Y` proper over $A$, the formal completions are equivalent to the ordinary schemes ($\hat{X}$ algebraic). So the
extension $\hat{g} : \hat{Y} \to \hat{X}$ of III.5.8 corresponds to an ordinary morphism $Y \to X$. Apply III.5.8 to get
the isomorphism. ∎

**Application — Severi-Brauer schemes.** When $\mathfrak{X} = \mathbb{P}^{r}_{k}$ (or more generally a Severi-Brauer
scheme), the cohomology $H^{1}(\mathbb{P}^{r}_{k}, \mathfrak{g}_{\mathbb{P}^{r}_{k}/k})$ vanishes (the tangent sheaf of
$\mathbb{P}^{r}$ is known explicitly via the Euler sequence). So every formal scheme proper and flat over $A$ with
closed fiber $\mathbb{P}^{r}_{k}$ is algebraizable, and is in fact isomorphic to the formal completion of
$\mathbb{P}^{r}_{A}$. By descent theory, this generalizes to non-complete $A$ after a finite étale extension; we will
not pursue this here.

## III.6 Global infinitesimal extension of smooth $S$-schemes

<!-- source: III.6 -->

We now invert the question: instead of extending a given morphism between two given schemes, we extend a **scheme
itself**. Given a smooth $S_{n}$-scheme $X_{n}$, can it be lifted to a smooth $S_{n+1}$-scheme $X_{n+1}$ reducing to
$X_{n}$ along the inclusion $S_{n} \subset S_{n+1}$? Locally yes (file 20, III.4.1); globally we get an obstruction in
$H^{2}$.

### Proposition: the automorphism sheaf

<!-- source: III.6.1 -->

*This proposition says: when $X_{n+1}$is a chosen lift of$X_{n}$, the sheaf of $S_{n+1}$-automorphisms of
$X_{n+1}$inducing the identity on$X_{n}$is canonically isomorphic to a tensor product of the tangent sheaf with the
relevant graded piece of$\mathcal{I}$. This sheaf is the automorphism group $\mathcal{G}$ for the H² obstruction
calculation.*

**Proposition III.6.1.** *Let $X_{n+1}$over$S_{n+1}$reduce to$X_{n}$over$S_{n}$. Then the sheaf, on the topological
space underlying $X_{n}$(or equivalently$X_{0}$), of $S_{n+1}$-automorphisms of $X_{n+1}$inducing the identity on$X_{n}$
is canonically isomorphic to*

```text
𝒢 = 𝔤_{X₀/S₀} ⊗_{𝒪_{S₀}} gr^{n+1}_𝓘(𝒪_S),
```

_as a sheaf of groups._

**Proof sketch.** By III.5.4 and III.4.2, the automorphism sheaf is a principal homogeneous sheaf under $\mathcal{G}$
(apply III.5.4 with $Y = X_{n+1}$, $Y_{0} = X_{n}$, $X = X_{n+1}$, $g_{n} = id$). Since the identity automorphism is a
distinguished section, the torsor is trivial; via this trivialization, the automorphism sheaf identifies with
$\mathcal{G}$ as a sheaf of sets. One checks that the identification is compatible with the group structures (the
verification is in the source; we omit). ∎

In particular: the sheaf of automorphisms of $X_{n+1}$ over $X_{n}$ is **commutative**. So if $X'_{n+1}$ is another lift
of $X_{n}$, isomorphic to $X_{n+1}$ over an open $U \subset X_{0}$, then the identification of the two automorphism
sheaves over $U$ is **canonical** — does not depend on the choice of isomorphism. This is the rigidity that makes the H²
calculation work.

### Corollary: the isomorphism sheaf is a torsor under $\mathcal{G}$

<!-- source: III.6.2 -->

_This corollary says: the sheaf of isomorphisms between two lifts of $X_{n}$ is naturally a torsor under $\mathcal{G}$
from III.6.1. Equivalently, two lifts are locally isomorphic, and the local isomorphism is determined up to a section of
$\mathcal{G}$._

**Corollary III.6.2.** *Let $X_{n+1}$and$X'_{n+1}$be smooth over$S_{n+1}$and reduce to$X_{n}$. Then the sheaf, on the
space underlying $X_{0}$, of $S_{n+1}$-isomorphisms from $X_{n+1}$to$X'_{n+1}$inducing the identity on$X_{n}$is
naturally a **principal homogeneous sheaf** (= torsor) under$\mathcal{G}$.*

**Proof.** Two lifts are locally isomorphic (III.4.1, file 20), so the isomorphism sheaf has nonempty stalks. The action
of $\mathcal{G}$ (automorphisms of one of the lifts) on this sheaf by composition makes it into a torsor under
$\mathcal{G}$. ∎

This sets up the H² calculation. We now have:

- **Local existence** of lifts (III.4.1).
- **Local isomorphism** of any two lifts (III.6.2).
- **Local isomorphisms determined up to $\mathcal{G}$** (III.6.1, III.6.2).

The 2-cocycle of failure-of-transitivity in $\mathcal{G}$ is the obstruction.

### Theorem: the H² obstruction class

<!-- source: III.6.3 -->

*This theorem says: the obstruction to lifting $X_{n}$ globally to a smooth $X_{n+1}$over$S_{n+1}$is a canonical
cohomology class in$H^{2}(X_{0}, \mathcal{G})$. Vanishing is necessary and sufficient. If the obstruction vanishes, the
set of lifts is a torsor under $H^{1}(X_{0}, \mathcal{G})$. This is the centerpiece of the exposé.*

**Theorem III.6.3.** *Let $(S, \mathcal{I}, X_{n})$ be as above, with $X_{n}$ **separated**. Then one can define
canonically an **obstruction class in $H^{2}(X_{0}, \mathcal{G})$** — where $\mathcal{G}$ is the sheaf of III.6.1 —
whose vanishing is necessary and sufficient for the existence of a smooth $X_{n+1}$over$S_{n+1}$reducing to$X_{n}$.*

*If the obstruction is zero, the set of isomorphism classes (with isomorphisms inducing the identity on $X_{n}$) of
$S_{n+1}$-preschemes $X_{n+1}$reducing to$X_{n}$is naturally a **principal homogeneous space
under$H^{1}(X_{0}, \mathcal{G})$**.*

**Proof construction.** Choose an affine open cover $(U_{i})$ of $X_{n}$ (the underlying space is $X_{0}$, separated).
By local existence (III.4.1, file 20), for each $i$ there exists a smooth scheme $X^{i} / S_{n+1}$ reducing to $U_{i}$.
Since $X_{n}$ is separated, the double overlaps $U_{ij} = U_{i} \cap U_{j}$ are again affine.

By III.6.2, on each $U_{ij}$ the schemes $X^{i}$ and $X^{j}$, restricted to $U_{ij}$, are locally isomorphic; since
$U_{ij}$ is affine and $H^{1}(U_{ij}, \mathcal{G})$ vanishes by Serre's affine vanishing, **there is a global
isomorphism** on $U_{ij}$:

$$
f_{ji} : X^{i}|_{U_{ij}} \longrightarrow X^{j}|_{U_{ij}}.
$$

(This is a choice; the choice is determined up to a section of $\mathcal{G}|_{U_{ij}}$.)

For triples, on $U_{ijk} = U_{i} \cap U_{j} \cap U_{k}$ we get three isomorphisms $f_{ji}, f_{kj}, f_{ki}$. The
composite $f^{-1}_{ki} \circ f_{kj} \circ f_{ji}$ is an automorphism of $X^{i}|_{U_{ijk}}$ over $X_{n}|_{U_{ijk}}$,
hence by III.6.1 a section of $\mathcal{G}|_{U_{ijk}}$:

```text
f_{ijk} := (f_{ki})⁻¹ ∘ f_{kj} ∘ f_{ji} ∈ 𝒢(U_{ijk}).
```

A short formal calculation (the "silly cocycle calculation" III.6.4) shows that $(f_{ijk})$ is a **2-cocycle** for
$\mathcal{G}$ on the cover $(U_{i})$. The triple-overlap consistency for the gluing of the $X^{i}$ into a global
$X_{n+1}$ is precisely the **vanishing of this 2-cocycle as a 2-coboundary**, i.e. the existence of sections
$g_{ij} \in \mathcal{G}(U_{ij})$ such that the modified $f_{ji} \cdot g_{ij}$ satisfy the cocycle relation. This means:
the existence of $X_{n+1}$ is equivalent to the obstruction class $[f_{ijk}] \in \check{H}^{2}((U_{i}), \mathcal{G})$
being zero. By Leray (file 17, T3), since $(U_{i})$ is an affine open cover of the separated scheme $X_{0}$ and
$\mathcal{G}$ is quasi-coherent, this Čech class equals $H^{2}(X_{0}, \mathcal{G})$. The class is independent of the
affine cover.

If the obstruction vanishes, the choices of $(g_{ij})$ modifying the $f_{ji}$ form a torsor under
$Z^{1}((U_{i}), \mathcal{G})$ (1-cocycles), and two such choices give isomorphic $X_{n+1}$ iff they differ by a
1-coboundary. So the set of isomorphism classes of $X_{n+1}$ is a torsor under
$\check{H}^{1}((U_{i}), \mathcal{G}) = H^{1}(X_{0}, \mathcal{G})$. ∎

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

### Remark: localizing on $S$

<!-- source: III.6.5 -->

_This remark says: when one looks at the obstruction class fiber-by-fiber over $S$, even when the global obstruction is
zero in $H^{2}(X_{0}, \mathcal{G})$, one may still have a non-trivial principal homogeneous sheaf on $S_{0}$ with
structure group the relative cohomology $R^{2}f_{{}_{\mathcal{G}}}$. The interplay with $R^{1}f_{{}_{\mathcal{G}}}$ is
what governs the structure of moduli of lifts._

**Remark III.6.5.** Note that in III.6.3 there is in general no distinguished element in the principal homogeneous space
under $H^{1}(X_{0}, \mathcal{G})$. This is reflected, after localizing on $S$, by the fact that one obtains a principal
homogeneous sheaf on $S_{0}$ with structure group $R^{1}f_{*}(\mathcal{G})$, which is not necessarily trivial.

In symbols: even when $H^{2}(X_{0}, \mathcal{G})$ vanishes globally, the relative cohomology sheaf
$R^{2}f_{*}(\mathcal{G})$ on $S_{0}$ may be nonzero — in which case the global vanishing translates to a section being
zero in $H^{0}(S_{0}, R^{2}f_{*}(\mathcal{G}))$, and the choice of lift is governed by $R^{1}f_{*}(\mathcal{G})$ on the
base.

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

### Corollary: when both $H^{1}$ and $H^{2}$ vanish

<!-- source: III.6.7 -->

_This corollary says: when $H^{2}$ vanishes, a lift $X_{n+1}$exists; when both$H^{1}$and$H^{2}$ vanish, the lift is
unique up to isomorphism._

**Corollary III.6.7.** *Suppose $H^{2}(X_{0}, \mathcal{G}) = 0$. Then a smooth $X_{n+1}$over$S_{n+1}$reducing
to$X_{n}$exists. It is unique up to isomorphism if moreover$H^{1}(X_{0}, \mathcal{G}) = 0$.*

**Proof.** Direct from III.6.3. ∎

This is the form of the obstruction theorem most often invoked in practice.

### Corollary: the affine case

<!-- source: III.6.8 -->

_This corollary says: when $X_{0}$ is affine, both $H^{1}$ and $H^{2}$ of quasi-coherent sheaves vanish (Serre), so a
smooth lift exists and is unique up to non-unique isomorphism._

**Corollary III.6.8.** _Under the conditions of Theorem III.4.1 (file 20), if $X_{0}$ is **affine**, then there exists a
smooth $X$ over $Y$ reducing to $X_{0}$, and this $X$ is **unique up to non-unique isomorphism**._

**Proof.** When $X_{0}$ is affine, $H^{q}(X_{0}, \mathcal{F}) = 0$ for all $q \geq 1$ and any quasi-coherent
$\mathcal{F}$ (Serre's affine vanishing, appendix `serre-affine-vanishing`). In particular
$H^{2}(X_{0}, \mathcal{G}) = H^{1}(X_{0}, \mathcal{G}) = 0$. Apply III.6.7 (for $n = 0$). ∎

**Comment.** The direct proof of Theorem III.4.1 (file 20, by reducing to the étale lifting theorem I.8.3, file 11)
could not have given this stronger result, since it produced only a local lift, with no statement about uniqueness. The
cohomological proof of III.6.8 sees uniqueness as a vanishing of $H^{1}$, not something built into the construction.

### Corollary: the free graded case

<!-- source: III.6.9 -->

_This corollary says: in the important case where $S$ is affine and the graded pieces $gr^{n}(\mathcal{O}_{S})$ are
locally free, the cohomology computation factors as a tensor product, and the obstruction lies in
$H^{2}(X_{0}, \mathcal{G}_{0}) \otimes_{A} gr^{n+1}_{I}(A)$._

**Corollary III.6.9.** *Under the conditions of III.6.3, suppose $S$ is affine with ring $A$, $\mathcal{I}$ is defined
by an ideal $I \subset A$, and the graded pieces
$gr^{n}*\mathcal{I}(\mathcal{O}*S) = \mathcal{I}^{n} / \mathcal{I}^{n+1}$are locally free.
Then$H^{i}(X_{0}, \mathcal{G})$ identifies with*

```text
H^i(X₀, 𝒢₀) ⊗_A gr^{n+1}_I(A),
```

*where $\mathcal{G}_{0} = \mathfrak{g}_{X*0/S_{0}}$. So the obstruction class to extending $X_{n}$lies
in$H^{2}(X_{0}, \mathcal{G}_{0}) \otimes_{A} gr^{n+1}_{I}(A)$, and (when zero) the set of isomorphism classes of
solutions is a principal homogeneous space under $H^{1}(X_{0}, \mathcal{G}_{0}) \otimes_{A} gr^{n+1}_{I}(A)$.*

**Proof sketch.** Same Künneth-style argument as in III.5.6: when $gr^{n}(\mathcal{O}_{S})$ is locally free, tensoring
with it commutes with cohomology on $X_{0}$. Since $S$ is affine and $gr^{n}(\mathcal{O}_{S})$ is projective,
$gr^{n}_{I}(A)$ is a flat $A$-module, and the cohomology commutes with tensor product. ∎

### Corollary: existence of a formal smooth scheme

<!-- source: III.6.10 -->

*This corollary says: under the cleaner conditions of III.6.9, when $H^{2}(X_{0}, \mathfrak{g}_{X*0/S_{0}}) = 0$, one
can lift step-by-step and obtain an $\hat{\mathcal{I}}$-adic formal smooth scheme $\mathfrak{X}$over`Ŝ`reducing
to$X_{n}$. Uniqueness if $H^{1}$ also vanishes.*

**Corollary III.6.10.** *Under the conditions of III.6.9, suppose $H^{2}(X_{0}, \mathfrak{g}_{X*0/S_{0}}) = 0$. Then
there exists an $\hat{\mathcal{I}}$-adic formal scheme $\mathfrak{X}$over the$\mathcal{I}$-adic formal completion
`Ŝ`of$S$, **smooth over $S$** in the sense that each $\mathfrak{X}_{p}$is smooth over$S_{p}$, and reducing to
$X_{n}$(i.e., equipped with an isomorphism$X_{n} \to \mathfrak{X} \times_{S} S_{n}$).*

*If moreover $H^{1}(X_{0}, \mathfrak{g}_{X*0/S_{0}}) = 0$, then such a $\mathfrak{X}$ is unique up to isomorphism.*

**Proof sketch.** Construct $X_{n+1}, X_{n+2}, \cdots$ step by step using III.6.9 (vanishing of the obstruction at every
step from the single condition $H^{2}(X_{0}, \mathcal{G}_{0}) = 0$). The limit $\mathfrak{X} = \lim_{p} X_{p}$ is a
formal smooth scheme over `Ŝ`. The uniqueness assertion already appears in III.6.9 (every step is unique up to
non-unique isomorphism, but uniqueness up to isomorphism in H¹-vanishing). ∎

This is the **headline of §III.6**: the cohomological condition $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/S_{0}}) = 0$ is
sufficient for the **formal** extension of a smooth scheme. The next file (file 22) handles the algebraization step —
promoting the formal scheme $\mathfrak{X}$ to an ordinary algebraic scheme $X$ over the (necessarily complete) base.

## What to remember

- **§III.5.1** is the structural fact: the sheaf $\mathcal{P}(g_{0})$ of extensions of a morphism $g_{0}$ along a
  square-zero thickening $Y_{0} \hookrightarrow Y$ is **formally principal homogeneous** under the `Hom`-sheaf
  $\mathcal{G} = \mathcal{Hm}_{\mathcal{O}_{Y_{0}}}(g^{*}_{0} \Omega^{1}_{X/S}, \mathcal{J})$.
- **§III.5.2** upgrades this to a **torsor** when $X$ is smooth over $S$ (so local extensions exist by file 20,
  III.3.1). The obstruction class is in **$H^{1}(Y_{0}, \mathcal{G})$**; if it vanishes, the set of extensions is a
  torsor under $H^{0}(Y_{0}, \mathcal{G})$. Using smoothness,
  $\mathcal{G} = g^{*}_{0}(\mathfrak{g}_{X/S}) \otimes \mathcal{J}$.
- **§§III.5.3–III.5.6** iterate the step-by-step extension along thickenings $S_{n}$. The free-graded case III.5.6
  reduces all obstructions to the single condition $H^{1}(Y_{0}, g^{*}_{0} \mathfrak{g}_{X_{0}/S_{0}}) = 0$.
- **§III.5.7–III.5.9** deduce: morphisms whose closed-fiber values are isomorphisms / closed immersions extend to formal
  isomorphisms / closed immersions; the algebraization theorem (file 18) then upgrades to ordinary proper schemes.
- **§III.6.1** identifies the **automorphism sheaf** of a lift $X_{n+1}$ (over $X_{n}$) with the tangent-sheaf-tensor
  $\mathcal{G} = \mathfrak{g}_{X_{0}/S_{0}} \otimes gr^{n+1}_{\mathcal{I}}(\mathcal{O}_{S})$. **§III.6.2** identifies
  the isomorphism sheaf of two lifts with a torsor under $\mathcal{G}$.
- **§III.6.3** is the **centerpiece**: the obstruction to lifting a smooth $X_{n}$ to $X_{n+1}$ is a class in
  $H^{2}(X_{0}, \mathcal{G})$. If it vanishes, the set of lifts is a torsor under $H^{1}(X_{0}, \mathcal{G})$. The proof
  is the "silly cocycle calculation" (III.6.4), which is honest in the sense of Giraud's non-abelian cohomology.
- **§§III.6.7–III.6.10** are the practical corollaries: the affine case is automatic (III.6.8); the free-graded case
  reduces all obstructions to a single $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/S_{0}})$ vanishing (III.6.9); when it vanishes,
  a **formal smooth lift $\mathfrak{X} / \hat{S}$** exists (III.6.10), unique up to isomorphism if $H^{1}$ also
  vanishes.

The final step — **algebraization of the formal lift $\mathfrak{X}$ to an ordinary scheme $X$** — is the subject of file
22 (Exposé III §7). Combined with the H² vanishing of this file, the headline **Theorem III.7.3** of file 22 will give:
every smooth projective scheme $X_{0} / k$ with $H^{2}(\mathfrak{g}_{X_{0}/k}) = H^{2}(\mathcal{O}_{X_{0}}) = 0$ lifts
to a smooth projective scheme over any complete local $A$ with residue field $k$. The corollary, **III.7.4**: every
smooth proper curve over $k$ lifts (both $H^{2}$ vanish trivially on a curve).
