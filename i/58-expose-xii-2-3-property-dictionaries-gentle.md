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

File 57 built the analytification functor $\Phi : X \mapsto X^{an}$ and its comparison morphism $\phi : X^{an} \to X$.
The defining content of XII.1.1 was *local*: the completion isomorphism
$\hat{\mathcal{O}}_{X, \phi(x)} \simeq \hat{\mathcal{O}}_{X^{an}, x}$ at every point, together with the bijection
$|X^{an}| \simeq X(\mathbb{C})$ between underlying sets. We saw two immediate consequences in file 57: the
analytification functor commutes with fibre products (XII.1.2), and the inverse-image functor on coherent sheaves is
exact, faithful, and conservative (XII.1.3.1).

This file (§§XII.2 and XII.3) builds the **property dictionaries**. There are two dictionaries to build, one for schemes
and one for morphisms.

The **scheme dictionary** (XII.2) is the assertion that eight reasonable local and global properties of $X$ correspond
to the same properties of $X^{an}$. The list is: nonempty, discrete, Cohen–Macaulay, $S_{n}$, regular, $R_{n}$, normal,
reduced, of dimension $n$. We also pin down a closure-compatibility statement (XII.2.2) — $\phi$ commutes with closure
for locally constructible subsets — and its corollary on open/closed/dense subsets (XII.2.3). The most substantive piece
of the scheme dictionary is the bijection of connected components (XII.2.6), which uses a finer analytic-geometric input
(the connectedness lemma XII.2.5).

The **morphism dictionary** (XII.3) is more elaborate. Without finite-type hypotheses, XII.3.1 lists eleven properties
that transfer between $f$ and $f^{an}$: flat, unramified, étale, smooth, normal, reduced, injective, separated,
isomorphism, monomorphism, open immersion. With a finite-type hypothesis on $f$, XII.3.2 adds six more: surjective,
dominant, closed immersion, immersion, proper, finite. The properness step uses Chow's lemma. XII.3.3 records two
warnings: local isomorphism for $f^{an}$ does not imply local isomorphism for $f$, and the finite-type hypothesis cannot
be dropped from XII.3.2 (the $\sqcup_{\mathbb{Z}} \operatorname{Spec} \mathbb{C} \to \mathbb{A}^{1}_{\mathbb{C}}$
example).

The slogan that emerges by the end of this file: **the scheme $X$ and its analytification $X^{an}$ carry the same
local-ring and global-property information; the morphisms $f$ and $f^{an}$ agree on every reasonable finite-presentation
property.** Everything reduces, via the Jacobson and excellence properties of $\mathbb{C}$-schemes locally of finite
type, to a comparison at closed points, where the completion isomorphism XII.1.1 closes the question.

______________________________________________________________________

## §XII.2.0 — Bridge and proof strategy

<!-- source: XII.2 -->

A scheme and its analytification carry the same local-ring and global-property information; a morphism and its
analytification agree on every reasonable finite-presentation property. The rest of this file builds those two
dictionaries entry by entry, and every entry reduces to the same comparison at closed points.

Every proof uses the same two structural inputs. They are worth stating up front because they appear repeatedly.

#### Input 1 — Jacobson and very-dense closed points.

A scheme $X$ locally of finite type over $\mathbb{C}$ is **Jacobson**: every locally closed subset of $X$ meets
$X(\mathbb{C})$ densely. This is `ega-iv-jacobson-nullstellensatz` (EGA IV §10.4.8). The practical consequences are
three:

- A locally constructible subset $T \subset X$ is determined by $T \cap X(\mathbb{C})$. In particular, two locally
  constructible subsets agreeing on $\mathbb{C}$-points are equal.
- A coherent sheaf $F$ on $X$ is zero iff $F_{y} = 0$ for every closed point $y \in X$ (very dense).
- A property holding at every closed point of $X$ and *known to define an open subset of $X$* automatically holds
  everywhere.

The third bullet is the bridge between "agrees on $\mathbb{C}$-points" (the analytic-comparison content) and "holds
everywhere" (the algebraic content).

#### Input 2 — excellence and openness of regularity-type loci.

A $\mathbb{C}$-scheme $X$ locally of finite type is **excellent** (EGA IV §7.8.6 (iii)). For every "local-ring-type"
property $P$ in the list

```text
Cohen–Macaulay,    S_n,    regular,    R_n,    normal,    reduced,
```

the locus ${x \in X : \mathcal{O}_{X, x} has property P}$ is *open* in $X$ (EGA IV §6.12). Combined with Input 1, this
means each such $P$ is detected by its restriction to the closed points: if $P$ holds at every closed point, $P$ holds
on $X$.

The completion isomorphism XII.1.1 (2) extends each $P$ from the algebraic local ring $\mathcal{O}_{X, y}$ ($y$ closed)
to the analytic local ring $\mathcal{O}_{X^{an}, x}$ ($x = \phi^{-1}(y)$) and back. Because the completion
$\hat{\mathcal{O}}_{X, y}$ agrees with $\hat{\mathcal{O}}_{X^{an}, x}$, and because for an excellent local ring each $P$
is preserved by passage to completion (and reflected, by faithful flatness of completion), the comparison is
bidirectional.

We will quote both inputs by name as we work through the propositions.

______________________________________________________________________

## §XII.2.1 — Property dictionary for schemes

<!-- source: XII.2.1 -->

### Proposition XII.2.1 — eight properties agree on $X$ and $X^{an}$

<!-- source: XII.2.1 -->

**Proposition XII.2.1.** Let $X$ be a $\mathbb{C}$-scheme locally of finite type, and let $X^{an}$ be its
analytification. Let $n \geq 0$ be an integer, and let $P$ be one of the following properties:

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

Then $X$ has property $P$ if and only if $X^{an}$ has property $P$.

*This result says:* every standard local-ring property and the basic dimensional/topological properties transfer between
the algebraic and analytic worlds — $X$ is regular iff $X^{an}$ is regular, $X$ has dimension $n$ iff $X^{an}$ does, and
so on.

**Proof.** Let $\phi : X^{an} \to X$ be the canonical morphism.

**(i) Nonempty.** By XII.1.1, the underlying set of $X^{an}$ is $X(\mathbb{C}) \subset |X|$. So $X^{an} = \emptyset$ iff
$X(\mathbb{C}) = \emptyset$. Now $X$ is Jacobson; closed points are very dense; so $X = \emptyset$ iff $X$ has no closed
points iff $X$ has no $\mathbb{C}$-points iff $X(\mathbb{C}) = \emptyset$. The last equivalence uses that residue fields
of closed points of a $\mathbb{C}$-scheme locally of finite type are *finite* extensions of $\mathbb{C}$, hence equal to
$\mathbb{C}$. So $X$ is nonempty iff $X^{an}$ is.

**(i′) Discrete.** A scheme $X$ (resp. an analytic space $X^{an}$) is discrete iff $\dim X = 0$ (resp.
$\dim X^{an} = 0$); this is `[XII.4, no. 19, §4, cor. 6]` for analytic spaces and standard for schemes. So (i′) follows
from (viii).

**(ii)–(vii).** Each of these is a local property in the list of Input 2 above. Combining Inputs 1 and 2, for $X$ to
have property $P$ it is necessary and sufficient that $P$ hold at every closed point of $X$. Similarly, for $X^{an}$ to
have property $P$ it is necessary and sufficient that $P$ hold at every point of $X^{an}$.

The completion isomorphism XII.1.1 (2) says $\hat{\mathcal{O}}_{X, \phi(x)} \simeq \hat{\mathcal{O}}_{X^{an}, x}$ for
every $x \in X^{an}$. Since each of the six properties is preserved and reflected by passage to the completion *for
excellent local rings*, the property holds at $\mathcal{O}_{X, \phi(x)}$ iff at $\hat{\mathcal{O}}_{X, \phi(x)}$ iff at
$\hat{\mathcal{O}}_{X^{an}, x}$ iff at $\mathcal{O}_{X^{an}, x}$. The first and third "iffs" are excellence +
completion-faithful-flatness; the middle iff is XII.1.1 (2).

Hence $P$ holds at every closed point of $X$ iff $P$ holds at every point of $X^{an}$. By the reduction above, $X$ has
$P$ iff $X^{an}$ has $P$.

**(viii) Dimension.** Combine the comparisons

```text
dim X = sup_y dim 𝒪_{X, y}     and     dim X^an = sup_x dim 𝒪_{X^an, x},
```

where in both cases the sup is taken over closed points (algebraic side) / all points (analytic side). At matched points
$y = \phi(x)$, the dimension of $\mathcal{O}_{X, y}$ agrees with the dimension of $\hat{\mathcal{O}}_{X, y}$ (excellence
again), which agrees with $\dim \hat{\mathcal{O}}_{X^{an}, x} = \dim \mathcal{O}_{X^{an}, x}$. So the suprema match, and
$\dim X = n$ iff $\dim X^{an} = n$.

This proves the proposition. ∎

> **Slogan.** *Local-ring properties and dimension transfer between $X$ and $X^{an}$ at every point and globally.* The
> bridge is Jacobson (closed points are enough) and excellence (completions preserve the property).

#### Aside (the "what excellence buys you" sidebar).

The seven-line proof of (ii)–(vii) is the most concentrated payoff of the excellence machinery in the gentle SGA. For a
non-excellent ring, the implication "the local-ring property $P$ holds at every closed point ⟹ $P$ holds on the scheme"
can fail in cardinally bad ways — examples in Matsumura, _Commutative Ring Theory_ §32 — and the machinery of passing
from "true on completions" back to "true on local rings" needs more care. For $\mathbb{C}$-schemes locally of finite
type, all of this is automatic. The same is true of analytic spaces, whose local rings are *henselian* and complete with
respect to the maximal ideal in a way that mirrors excellence.

This is why the file 58 dictionary is short: the work is being done by EGA IV.

______________________________________________________________________

## §XII.2.2 — Compatibility with closure for locally constructible sets

<!-- source: XII.2.2 -->

### Proposition XII.2.2 — $\phi$ commutes with closure on locally constructible subsets

<!-- source: XII.2.2 -->

**Proposition XII.2.2.** Let $X$ be a $\mathbb{C}$-scheme locally of finite type, let $\phi : X^{an} \to X$ be the
canonical morphism, and let $T \subset X$ be a locally constructible subset. Then

$$
\phi^{-1}(closure(T)) = closure(\phi^{-1}(T)),
$$

where the closures are taken in $X$ and $X^{an}$ respectively.

*This result says:* the analytic comparison map respects topological closure for *locally constructible* subsets. Note
that this is generally false for arbitrary subsets, but locally constructible subsets are exactly the content the
Jacobson property pins down.

**Proof.** We reduce to the case where $T$ is a dense open subset of $X$. (Indeed, every locally constructible subset is
a finite Boolean combination of locally closed subsets, and the closure operation is determined by its action on each
locally closed piece. The case "`T = U \ Z` for $U$ open and $Z$ a closed subset of $U$" reduces to the dense-open case
after working inside $U$.)

So suppose $T \subset X$ is dense open. Let $H \subset X$ be the reduced closed subscheme with underlying space $X - T$.
The associated analytic space $H^{an}$ is a closed analytic subspace of $X^{an}$ with underlying space
$X^{an} - \phi^{-1}(T)$ (by XII.1.1 block (a) and the bijection of $\mathbb{C}$-points on $H$).

We must show that every point $x \in H^{an}$ belongs to the closure of $\phi^{-1}(T)$. Equivalently: every open
neighbourhood of $x$ in $X^{an}$ meets $\phi^{-1}(T)$. Suppose for contradiction that some open $V \ni x$ is disjoint
from $\phi^{-1}(T)$, that is, $V \subset H^{an}$ (as sets).

At the point $x$, the germ of analytic space $(X^{an}, x)$ contains the subgerm $(H^{an}, x)$ as a closed analytic
subspace. Because $T$ is *dense* open in $X$, the closed subscheme $H$ is *proper* (i.e. $H \neq X$); hence the ideal
sheaf $I_{H} \subset \mathcal{O}_{X}$ is non-nilpotent at $x$ (the local ring $\mathcal{O}_{X, \phi(x)}$ has nontrivial
quotient $\mathcal{O}_{H, \phi(x)}$ ≠ 0, because $\mathcal{O}_{X, \phi(x)}$ is reduced enough that nilpotents alone
cannot generate `I_H`). After passage to the analytic side, the analytic ideal
$I_{H} \cdot \mathcal{O}_{X^{an}, x} = I_{H^{an}, x}$ is non-nilpotent in $\mathcal{O}_{X^{an}, x}$.

By the **Nullstellensatz for complex analytic spaces** (Gunning–Rossi, equivalently `[XII.4, no. 19, §4, cor. 3]` in the
source), a non-nilpotent ideal in an analytic local ring at $x$ has zero locus *strictly smaller* than the ambient germ
— i.e. every neighbourhood of $x$ contains points where some element of $I_{H} \cdot \mathcal{O}_{X^{an}, x}$ is
nonzero, i.e. points of $X^{an} - H^{an} = \phi^{-1}(T)$. This contradicts $V \subset H^{an}$.

Hence every neighbourhood of $x$ meets $\phi^{-1}(T)$, so $x \in closure(\phi^{-1}(T))$, as desired.

The reverse inclusion $closure(\phi^{-1}(T)) \subset \phi^{-1}(closure(T))$ is automatic: $\phi$ is continuous, so
$\phi^{-1}(closure(T))$ is closed and contains $\phi^{-1}(T)$, hence contains the closure. ∎

> **Slogan.** *Topology of locally constructible subsets transfers in both directions under $\phi$.* The Jacobson
> property of $X$ and the analytic Nullstellensatz of $X^{an}$ make this a clean equality, not just an inclusion.

### Corollary XII.2.3 — open / closed / dense subsets are detected by $\phi$

<!-- source: XII.2.3 -->

**Corollary XII.2.3.** Let $T \subset X$ be a locally constructible subset of a $\mathbb{C}$-scheme $X$ locally of
finite type. Then:

```text
(a)  T  is open    iff  φ^{-1}(T)  is open  in  X^an;
(b)  T  is closed  iff  φ^{-1}(T)  is closed in  X^an;
(c)  T  is dense   iff  φ^{-1}(T)  is dense  in  X^an.
```

**Proof.** Clauses (a), (b), (c) are dual to XII.2.2 by elementary set-theoretic manipulation. For (b): $T$ is closed
iff $T = closure(T)$ iff $\phi^{-1}(T) = \phi^{-1}(closure(T)) = closure(\phi^{-1}(T))$ (XII.2.2) iff $\phi^{-1}(T)$ is
closed. (a) is dual. (c) is $closure(T) = X$ iff
$closure(\phi^{-1}(T)) = \phi^{-1}(closure(T)) = \phi^{-1}(X) = X^{an}$, using that $\phi$ is surjective on closed
points (which together with Jacobson gives surjection of locally constructible subsets).

For the converse direction in (a)–(b), use the Jacobson property: two locally constructible subsets agreeing on
$X(\mathbb{C})$ are equal (Input 1). If $\phi^{-1}(T)$ is open / closed / dense, the locally constructible subsets $T$
and the open / closed / dense locally constructible set in $X$ with the same $\mathbb{C}$-points are equal. ∎

> **Slogan.** *On locally constructible subsets, "open / closed / dense" is decided on the analytic side.*

______________________________________________________________________

## §XII.2.3 — Connectedness, irreducibility, and $\pi_{0}$

<!-- source: XII.2.4 -->

The next step is the comparison of *global* topological invariants: connected components, irreducibility, and the set
$\pi_{0}$. The proof of XII.2.4 uses Serre's original projective GAGA on a compactification and a finer lemma (XII.2.5)
on rare-set complements in normal analytic spaces.

### Proposition XII.2.4 — connectedness and irreducibility transfer

<!-- source: XII.2.4 -->

**Proposition XII.2.4.** Let $X$ be a $\mathbb{C}$-scheme locally of finite type. Then:

```text
(a)  X  is connected     iff  X^an  is connected,
(b)  X  is irreducible   iff  X^an  is irreducible.
```

*This result says:* the global topology of $X$ (its number of connected components, its decomposition into irreducible
pieces) matches the global topology of $X^{an}$.

**Proof.**

**Forward directions.** Suppose $X^{an}$ is connected (resp. irreducible). The image
$\phi(|X^{an}|) = X(\mathbb{C}) \subset |X|$ is then connected (resp. irreducible) as a subspace of $|X|$. Two locally
constructible subsets of $X$ agreeing on $X(\mathbb{C})$ are equal (Jacobson); the *closed subsets* of $X$ are locally
constructible; so connectedness / irreducibility of $X(\mathbb{C})$ lifts to connectedness / irreducibility of $X$.
(This uses `ega-iv-1-8-4-constructible` plus the Jacobson property; cf. EGA IV §10.1.2.)

**Reverse directions.** Suppose $X$ is connected (resp. irreducible); we show $X^{an}$ is.

**Reduction to irreducible case.** First, suppose $X$ connected. Given $x \in X$, the set of $y \in X$ for which there
exists a chain of irreducible closed subschemes $X_{1}, \cdots, X_{n} \subset X$ with $x \in X_{1}$, $y \in X_{n}$,
$X_{i} \cap X_{i+1} \neq \emptyset$ for $1 \leq i < n$ is both open and closed in $X$ (chains can be extended at either
end), hence equal to all of $X$. For such a chain, also $X^{an}_{i} \cap X^{an}_{i+1} \neq \emptyset$. If we know the
$X^{an}_{i}$ are connected, then $X^{an}$ is connected (as a union of connected sets with pairwise non-empty pairwise
intersections along a chain). So it suffices to prove the irreducible case.

**Reduction to affine case.** Suppose $X$ irreducible. Let $(U_{i})_{i \in I}$ be an affine open cover of $X$. Any two
$U_{i}, U_{j}$ have non-empty intersection (because $X$ is irreducible). After analytification,
$U^{an}_{i} \cap U^{an}_{j} = (U_{i} \cap U_{j})^{an}$ is non-empty (XII.1.2 and (i) of XII.2.1). If we know each
$U^{an}_{i}$ is irreducible, then $X^{an}$ is irreducible (a union of irreducible spaces pairwise meeting is
irreducible).

**Reduction to normal affine case.** Suppose $X$ affine irreducible. Let $\tilde{X} \to X$ be the normalisation
morphism; $\tilde{X} \to X$ is finite and surjective, so $\tilde{X}^{an} \to X^{an}$ is finite and surjective
(anticipating XII.3.2 (i), (vi); also clear at the analytic level by Oka coherence + Nullstellensatz). If
$\tilde{X}^{an}$ is irreducible, then so is $X^{an}$ (image of an irreducible under a continuous surjection).

**Affine normal irreducible case.** Suppose $X$ affine normal irreducible. Then the local rings of $X$ are integral
domains, and by XII.2.1 (vi) the local rings of $X^{an}$ are integral domains too. For a normal analytic space with
integral local rings, *connectedness implies irreducibility* (any closed analytic subset $\mathcal{F} \subset X^{an}$
has its zero-codimension locus closed and open; in a connected normal space this is empty or everything). It therefore
suffices to show $X^{an}$ is *connected*.

**The compactification step.** Choose a *normal projective* compactification $i : X \to P$ of $X$, where $P$ is a normal
projective $\mathbb{C}$-scheme and $i$ is a dominant open immersion. (Normal projective compactifications exist — take
the normalisation of the projective closure of an affine embedding; one has to check the closure is projective, which
follows from finite-typeness, and normality, which is the normalisation step.)

By Serre's original projective GAGA (`gaga-serre-original`), $P^{an}$ is *connected* (Serre 1956 computes that for a
projective $\mathbb{C}$-variety the analytification has the same $\pi_{0}$ as the variety; specifically for $P$
connected, $P^{an}$ is connected). Since $X = P - (P - X)$ is the complement of a proper closed subscheme of $P$, and
$P$ is *normal*, the analytic space $X^{an} = P^{an} - (P - X)^{an}$ is the complement in the connected normal analytic
space $P^{an}$ of a rare closed analytic subset.

The next lemma (XII.2.5) then forces $X^{an}$ connected. ∎

### Lemma XII.2.5 — rare closed analytic subsets do not disconnect

<!-- source: XII.2.5 -->

**Lemma XII.2.5.** Let $\mathcal{P}$ be a connected normal complex analytic space, and let
$\mathcal{Y} \subset \mathcal{P}$ be a rare (nowhere dense) closed analytic subset. Then
$\mathcal{X} := \mathcal{P} - \mathcal{Y}$ is connected.

*This result says:* removing a thin closed analytic subset from a connected normal analytic space leaves connectedness
intact. The proof factors through Serre's prolongation theorem (codim ≥ 2 case) and the implicit function theorem
(general case).

**Proof.**

**Case 1: $codim_{\mathcal{P}}(\mathcal{Y}) \geq 2$.** By Serre's prolongation theorem (`serre-prolongement-faisceaux`,
`[XII.11, no. 3, prop. 4]` in the source), the canonical map
$\mathcal{O}_{\mathcal{P}} \to i_{*} \mathcal{O}_{\mathcal{X}}$ (where $i : \mathcal{X} \hookrightarrow \mathcal{P}$ is
the inclusion) is an isomorphism. Consequently
$\Gamma(\mathcal{P}, \mathcal{O}_{\mathcal{P}}) = \Gamma(\mathcal{X}, \mathcal{O}_{\mathcal{X}})$. If $\mathcal{X}$ were
disconnected as $\mathcal{X} = \mathcal{X}_{1} \sqcup \mathcal{X}_{2}$, the indicator function of $\mathcal{X}_{1}$
would be a locally constant section of $\mathcal{O}_{\mathcal{X}}$ with two distinct values; pulling back via the
isomorphism, this gives a locally constant section of $\mathcal{O}_{\mathcal{P}}$ with two values, contradicting
connectedness of $\mathcal{P}$.

**Case 2: general case.** Let $\mathcal{Y}' \subset \mathcal{P}$ be the singular locus of $\mathcal{Y}$ (the closed
analytic subset of $\mathcal{Y}$ where $\mathcal{Y}$ is not regular). Then $\dim \mathcal{Y}' < \dim \mathcal{Y}$
(Grauert–Remmert), so by induction on $\dim \mathcal{Y}$ we may assume $\mathcal{Y}'$ is empty — that is, $\mathcal{Y}$
is a regular submanifold of $\mathcal{P}$. By the implicit function theorem, every point $y \in \mathcal{Y}$ has a
neighbourhood $\mathcal{U} \subset \mathcal{P}$ isomorphic to a ball in $\mathbb{C}^{n}$, such that
$\mathcal{U} \cap \mathcal{Y}$ is defined by the vanishing of a fixed number of coordinate functions. Then
$\mathcal{U} - \mathcal{U} \cap \mathcal{Y}$ is the complement of a coordinate linear subspace in a ball, which is
path-connected (in fact homotopy-equivalent to a torus).

We have shown: every point $y \in \mathcal{Y}$ has a *connected* neighbourhood in
$\mathcal{X} = \mathcal{P} - \mathcal{Y}$. Since $\mathcal{P}$ is connected and $\mathcal{X}$ is the complement of a
closed subset, this local connectedness propagates to global connectedness of $\mathcal{X}$. (Pick two points
$x_{1}, x_{2} \in \mathcal{X}$; connect them by a path in $\mathcal{P}$; the path can be perturbed locally inside
$\mathcal{U}_{y}$ near each intersection point $y \in \mathcal{Y}$ to avoid $\mathcal{Y}$.)

This proves the lemma. ∎

### Corollary XII.2.6 — $\pi_{0}(X^{an}) \to \pi_{0}(X)$ is a bijection

<!-- source: XII.2.6 -->

**Corollary XII.2.6.** Let $X$ be a $\mathbb{C}$-scheme locally of finite type. The canonical map

$$
\pi_{0}(X^{an}) \to \pi_{0}(X)
$$

induced by $\phi : X^{an} \to X$ is a bijection.

*This result says:* the analytic and algebraic comparisons of connected components agree exactly.

**Proof.** Surjectivity: $\phi : X^{an} \to X$ surjects on $X(\mathbb{C})$, which meets every connected component of $X$
(Jacobson). Injectivity: by XII.2.4, two connected components of $X^{an}$ cannot map to the same connected component of
$X$ (they would merge into one analytic component). ∎

> **Slogan.** *Connected components transfer bijectively between $X$ and $X^{an}$.* This is the input the Riemann
> existence theorem of file 60 attaches to: a connected finite étale covering of $X^{an}$ is a connected component of
> $X' \times_{X} X''$ for some $X', X'' / X$; XII.2.6 + XII.3.1 (ix) close the morphism-side comparison.

______________________________________________________________________

## §XII.3 — Property dictionary for morphisms

<!-- source: XII.3 -->

We turn now to the morphism dictionary. The structure is parallel to XII.2.1, but more elaborate because there are more
properties of morphisms than of schemes. We split the morphism dictionary into two propositions: XII.3.1 collects
properties that transfer without a finite-type hypothesis on $f$, and XII.3.2 collects properties that require one. The
XII.3.3 remarks at the end warn about two failures: local isomorphism cannot be reflected from the analytic side, and
the finite-type hypothesis cannot be dropped from XII.3.2.

### Proposition XII.3.1 — eleven properties without finite-type

<!-- source: XII.3.1 -->

**Proposition XII.3.1.** Let $f : X \to Y$ be a morphism of $\mathbb{C}$-schemes locally of finite type, and let
$f^{an} : X^{an} \to Y^{an}$ be its analytification. Let $P$ be one of the following properties of a morphism:

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

Then $f$ has property $P$ if and only if $f^{an}$ has property $P$.

*This result says:* of the eleven listed morphism properties, none requires a finite-type hypothesis to transfer between
scheme-theoretic morphisms and analytic morphisms.

**Proof.** Let $\phi : X^{an} \to X$ and $\psi : Y^{an} \to Y$ be the canonical morphisms. Let $x \in X^{an}$ and put
$y = f^{an}(x) \in Y^{an}$. The local maps $\mathcal{O}_{Y^{an}, y} \to \mathcal{O}_{X^{an}, x}$ and
$\mathcal{O}_{Y, \psi(y)} \to \mathcal{O}_{X, \phi(x)}$ deduced from $f^{an}$ and $f$ give the *same* morphism after
passage to completions (because of XII.1.1 (2) applied to each side).

**(i) Flat.** A morphism is flat iff every local map $\mathcal{O}_{Y, \psi(y)} \to \mathcal{O}_{X, \phi(x)}$ is flat
(for $x$ over $y$). Flatness of an $A$-module is preserved and reflected by passage to the completion of $A$ (when $A$
is noetherian, EGA `0_I` §10.2 / `[XII.2, ch. 3, §5, prop. 4]`). So $f$ is flat at $\phi(x)$ iff $f^{an}$ is flat at
$x$. For the global statement, use that the flat locus of a finite-presentation morphism is open in $X$
(`ega-iv-flat-locus-open` = EGA IV §11.1.1) and the Jacobson property (closed points decide membership in an open). The
corresponding statement on the analytic side — flat locus of $f^{an}$ is open in $X^{an}$ — is the analytic analogue
(Gunning–Rossi). Conclusion: $f$ is flat iff $f^{an}$ is.

**(ii) Net (unramified).** Same argument as (i), with "flat" replaced by "unramified" and EGA IV §17.4.4 in place of
§11.1.1 (`ega-iv-unramified-locus-open`). The unramified property is preserved and reflected by completions of the local
rings.

**(iii) Étale.** Étale = flat + unramified. Combine (i) and (ii).

**(iv) Smooth.** Smooth = flat + geometrically regular fibres. The flatness comparison is (i). For the fibres, take a
fibre $f^{-1}(\psi(y))$ and the corresponding analytic fibre $(f^{an})^{-1}(y)$ (these are matched by XII.1.2: fibre
products commute with analytification). By XII.2.1 (iv) applied to each fibre, "regular" agrees between the
scheme-theoretic fibre and the analytic fibre. The smooth-fibre locus is open on the base
(`ega-iv-12-1-7-smooth-fibre-locus` = EGA IV §12.1.7) and analytic openness mirrors this. Conclusion as for (i).

**(v) Normal fibres.** Same as (iv), using XII.2.1 (vi) and EGA IV §12.1.7 for the normality variant.

**(vi) Reduced fibres.** Same, using XII.2.1 (vii).

**(vii) Injective.** If $f$ is injective, so is $f^{an}$ (the underlying set map on $\mathbb{C}$-points is the
restriction of $f$ to $X(\mathbb{C}) \hookrightarrow Y(\mathbb{C})$). Conversely, suppose $f^{an}$ is injective; we show
$f$ is.

We may suppose $f$ of finite type (the global statement reduces to the finite-type case via affine opens). Since
$f^{an}$ is injective, the fibres of $f^{an}$ over each $y \in Y^{an}$ are at most singletons. Hence the fibres of $f$
over each closed point $\psi(y) \in Y$ are *radicial* (= geometrically have at most one point). The locus
${y \in Y : f^{-1}(y) is radicial}$ is locally constructible (`ega-iv-radicial-constructible` = EGA IV §9.6.1), and
contains every closed point of $Y$ (the closed points are radicial), and $Y$ is Jacobson; hence the locus is all of $Y$.
So $f$ is radicial, hence injective on points.

**(viii) Separated.** Separatedness of $f$ is the property that the diagonal $\Delta_{X/Y} : X \to X \times_{Y} X$ is a
closed immersion. By XII.1.2, the diagonal of $f^{an}$ is the analytification of the diagonal of $f$. By XII.2.3, the
property of being a closed subspace transfers between schemes and analytic spaces. So $\Delta_{X/Y}$ is closed iff
$(\Delta_{X/Y})^{an}$ is.

But "closed immersion" requires more than "closed image": it requires the local map of structure sheaves to be
surjective. This surjectivity *is* preserved by analytification (closed-immersion definition is local on the target;
analytification preserves local-ringed structure). Hence $f$ separated iff $f^{an}$ separated.

**(xi) Open immersion.** A morphism is an open immersion iff it is *étale and injective* (`ega-iv-unramified-locus-open`
= EGA IV §17.9.1; also part of file 04). The same characterisation holds in the analytic category. Combine (iii) and
(vii).

**(ix) Isomorphism.** Iso = open immersion + surjective. The "+surjective" is XII.3.2 (i) in the next proposition; the
"open immersion" is (xi). Both transfer; their conjunction does.

**(x) Monomorphism.** $f$ is a monomorphism iff its diagonal $\Delta_{X/Y} : X \to X \times_{Y} X$ is an isomorphism. By
(ix), this transfers between $\Delta_{f}$ and $(\Delta_{f})^{an} = \Delta_{f^{an}}$. So $f$ mono iff $f^{an}$ mono.

This proves all eleven clauses. ∎

> **Slogan.** *Flat, unramified, étale, smooth, normal-fibred, reduced-fibred, injective, separated, isomorphism, mono,
> open-immersion: each transfers between $f$ and $f^{an}$ without a finite-type assumption on $f$.*

### Proposition XII.3.2 — six properties with finite-type hypothesis

<!-- source: XII.3.2 -->

**Proposition XII.3.2.** Let `X, Y` be $\mathbb{C}$-schemes locally of finite type, let $f : X \to Y$ be a morphism *of
finite type*, and let $f^{an} : X^{an} \to Y^{an}$ be its analytification. Let $P$ be one of the following:

```text
(i)   surjective
(ii)  dominant
(iii) a closed immersion
(iv)  an immersion
(v)   proper
(vi)  finite.
```

Then $f$ has property $P$ if and only if $f^{an}$ has property $P$.

*This result says:* the six surjection-/closure-related properties require $f$ of finite type to transfer correctly. The
example in XII.3.3 (b) below shows the hypothesis is necessary.

**Proof.** As before let $\phi, \psi$ be the canonical morphisms.

**(i) Surjective.** Suppose $f$ surjective. For every $y \in Y^{an}$, $f^{-1}(\psi(y)) \subset X$ is a non-empty
(because $f$ surjective) closed subset of finite-type $X$; it has at least one closed point (Jacobson). Hence $f^{an}$
surjects.

Conversely, suppose $f^{an}$ surjective. Then $f(X) \subset Y$ is locally constructible (`ega-iv-1-8-4-constructible` =
EGA IV §1.8.4) and contains all closed points of $Y$ (every closed point lies in
$\psi(X^{an}) = f(X(\mathbb{C})) \subset f(X)$). Jacobson then forces $f(X) = Y$.

**(ii) Dominant.** $f$ dominant iff $closure(f(X)) = Y$ iff (by XII.2.2) $closure(f^{an}(X^{an})) = Y^{an}$ iff $f^{an}$
dominant.

**(iii) Closed immersion.** If $f$ is a closed immersion, so is $f^{an}$ (XII.1.1 block (a2)). Conversely, suppose
$f^{an}$ is a closed immersion. Then $f^{an}$ is in particular a *proper monomorphism* (closed immersion = proper +
mono). By XII.3.2 (v) below and XII.3.1 (x), $f$ is also a proper monomorphism. By `ega-iv-8-11-5-proper-mono` (EGA IV
§8.11.5), a proper monomorphism is a closed immersion.

**(iv) Immersion.** Immersion = open immersion of $X$ into a closed subscheme of $Y$. If $f$ is an immersion, so is
$f^{an}$ by (iii) and XII.3.1 (xi). Conversely, suppose $f^{an}$ is an immersion. Let $T = f(X)$ and let $\bar{T}$ be
the scheme-theoretic closure of $T$ in $Y$. Factor $f = j \circ i$ with $i : X \to \bar{T}$ and $j : \bar{T} \to Y$ a
closed immersion. Then $f^{an} = j^{an} \circ i^{an}$ with $j^{an}$ a closed immersion (by (iii) just proved).

By XII.2.2, $\bar{T}^{an} = closure(f^{an}(X^{an}))$. Since $f^{an}$ is an immersion, $f^{an}(X^{an})$ is locally closed
in $Y^{an}$, i.e. open in its closure $\bar{T}^{an}$. So $i^{an}(X^{an})$ is open in $\bar{T}^{an}$, hence $i(X)$ is
open in $\bar{T}$ (XII.2.3 (a)).

Factor $i$ further as $i = i_{2} \circ i_{1}$, where $i_{1} : X \to i(X)$ is the canonical morphism and
$i_{2} : i(X) \to \bar{T}$ is the open immersion. The morphism $i^{an}_{1}$ is a *proper monomorphism* (proper because
finite-type, and mono because $f^{an}$ is an immersion), hence so is $i_{1}$ by XII.3.2 (v) and XII.3.1 (x). By
`ega-iv-8-11-5-proper-mono`, $i_{1}$ is a closed immersion. Composing with the open immersion $i_{2}$,
$i = i_{2} \circ i_{1}$ is an immersion, hence so is $f = j \circ i$.

**(v) Proper.** This is the key case. Properness is a global condition that does not localise to completions; we need a
different argument.

**(v) Forward direction ($f$ proper ⟹ $f^{an}$ proper).** Properness of $f^{an}$ is local on $Y^{an}$, so we may assume
$Y$ affine. By **Chow's lemma** (EGA II §5.6.1, also `chow-lemma` in the gentle appendix), there exist a projective
$Y$-scheme $X'$ and a projective surjective morphism $g : X' \to X$. Then $f \circ g : X' \to Y$ is projective. After
analytification, $(f \circ g)^{an} = f^{an} \circ g^{an}$ is projective (a projective morphism's analytification is
projective — embed in $\mathbb{P}^{N}_{Y}$ and apply XII.1.2 to the closed embedding). A projective morphism of analytic
spaces is proper (`[XII.1, ch. 1, §10]`, the analytic analogue of "projective ⟹ proper"). And $g^{an}$ is surjective by
XII.3.2 (i). Properness then descends from $f^{an} \circ g^{an}$ along $g^{an}$: if a composition is proper and the
first map is surjective, the second is proper.

**(v) Reverse direction ($f^{an}$ proper ⟹ $f$ proper).** Suppose $f^{an}$ proper; we show $f$ proper. By XII.3.1
(viii), $f$ is separated. It remains to show $f$ is universally closed. In fact it is enough to show $f$ is *closed*,
because base-changing $f$ to any $Y'$-scheme of finite type still gives a finite-type morphism $X \times_{Y} Y' \to Y'$
whose analytification is the base change of $f^{an}$, hence proper.

So let $T \subset X$ be closed. The image $f(T) \subset Y$ is locally constructible (`ega-iv-1-8-4-constructible`); we
want $f(T)$ closed. The analytic image $f^{an}(\phi^{-1}(T)) = \psi^{-1}(f(T))$ is closed in $Y^{an}$ because $f^{an}$
is proper. By XII.2.2, $\psi^{-1}(closure(f(T))) = closure(\psi^{-1}(f(T))) = \psi^{-1}(f(T))$. The Jacobson property
then forces $closure(f(T)) = f(T)$, that is, $f(T)$ is closed. So $f$ is closed, hence proper.

**(vi) Finite.** A morphism is finite iff it is proper with finite fibres (EGA III §4.4.2 plus `[XII.4, no. 19, §5]`).
The set of points $y \in Y$ where the fibre $f^{-1}(y)$ is finite is locally constructible (`ega-iv-9-7-9-finite-fibre`
= EGA IV §9.7.9), and by XII.1.2 the fibres of $f$ are finite iff the fibres of $f^{an}$ are. So (vi) follows from (v).

This proves all six clauses. ∎

> **Slogan.** *Six more morphism properties — surjective, dominant, closed-immersion, immersion, proper, finite —
> transfer between $f$ and $f^{an}$, under the finite-type hypothesis on $f$. Properness routes through Chow's lemma;
> finiteness through finite-fibre constructibility.*

### Remark XII.3.3 — two warnings

<!-- source: XII.3.3 -->

**Remark XII.3.3.** Two warnings about the boundaries of the dictionary.

**(a) Local isomorphism for $f^{an}$ does not imply local isomorphism for $f$.** For example, suppose $f : X \to Y$ is
étale (but not an open immersion: connected total space, finite-fibred, non-trivial cover). Then $f^{an}$ is a local
biholomorphism (= local isomorphism in the analytic sense, `[XII.4, no. 13, §1]`). But $f$ itself, viewed as a morphism
of schemes, is generally *not* a Zariski-local isomorphism — a Zariski-local isomorphism is the same as an open
immersion, which forces injectivity (XII.3.1 (vii)).

The point is that "local isomorphism" in the analytic category means "isomorphism on small Euclidean neighbourhoods",
which is much weaker than "Zariski-local open immersion". The analytic local-iso condition is exactly étaleness, by the
implicit function theorem in the analytic context.

**(b) The finite-type hypothesis cannot be dropped from XII.3.2.** A simple counterexample for clause (iii): let
$X = \sqcup_{n \in \mathbb{Z}} \operatorname{Spec} \mathbb{C}$ (a countable disjoint union of points),
$Y = \mathbb{A}^{1}_{\mathbb{C}}$, and $f : X \to Y$ the morphism sending the points of $X$ to a discrete sequence
${0, 1, -1, 2, -2, \cdots}$ of points in $\mathbb{A}^{1}_{\mathbb{C}}$. Then $f$ is *not* of finite type (it is
countably-presented but not finitely-presented over $Y$). The analytification $f^{an}$ sends
$X^{an} = \sqcup_{\mathbb{Z}} {pt}$ to the discrete subset $\mathbb{Z} \subset \mathbb{C}$ of the analytic affine line
`𝔸^1_ℂ^an = ℂ`. The discrete subset is a *closed* analytic subset of `𝔸^1_ℂ^an` (it is closed and locally finite), so
$f^{an}$ is a closed immersion of an analytic-finite space into the analytic affine line. But $f$ is not a closed
immersion in the scheme sense: the image $f(X) = \mathbb{Z} \subset \mathbb{A}^{1}_{\mathbb{C}}$ is not closed (its
closure is all of $\mathbb{A}^{1}_{\mathbb{C}}$ because the closed subsets of $\mathbb{A}^{1}_{\mathbb{C}}$ are finite
sets of points, the empty set, and the whole space).

The failure of XII.3.2 (iii) here illustrates a more general phenomenon: without finite-type, the "locally
constructible" framework of XII.2.2–XII.2.3 has no traction, so global properties like closedness do not transfer.

> **Slogan for XII.3.3.** *The analytic-side and scheme-side categories of morphisms agree on the finite-presentation
> properties, but the finite-type hypothesis is load-bearing.*

______________________________________________________________________

## §XII.3.4 — Closing of file 58

<!-- source: XII.3 -->

By the end of this file we have the **scheme-and-morphism dictionary** between $Sch_{lft}/\mathbb{C}$ and
$AnSp/\mathbb{C}$:

- (XII.2.1) Eight scheme-level properties (nonempty, discrete, CM, $S_{n}$, regular, $R_{n}$, normal, reduced, dim $n$)
  transfer between $X$ and $X^{an}$.
- (XII.2.2–XII.2.3) Locally constructible subsets and their closure / open / dense behaviour transfer between $X$ and
  $X^{an}$.
- (XII.2.4) Connectedness and irreducibility transfer between $X$ and $X^{an}$.
- (XII.2.5) Rare closed analytic subsets of normal connected analytic spaces do not disconnect.
- (XII.2.6) The map $\pi_{0}(X^{an}) \to \pi_{0}(X)$ is a bijection.
- (XII.3.1) Eleven morphism-level properties (flat, net, étale, smooth, normal-fibred, reduced-fibred, injective,
  separated, isomorphism, mono, open-immersion) transfer between $f$ and $f^{an}$ without a finite-type hypothesis.
- (XII.3.2) Six more morphism-level properties (surjective, dominant, closed-immersion, immersion, proper, finite)
  transfer between $f$ and $f^{an}$ under a finite-type hypothesis.
- (XII.3.3) Two warnings: local iso for $f^{an}$ does not imply local iso for $f$; the finite-type hypothesis cannot be
  dropped from XII.3.2.

The cohomological side of the dictionary — the equivalence of coherent-sheaf categories on proper schemes, the
comparison $H^{p}(X, F) \simeq H^{p}(X^{an}, F^{an})$, and the higher-direct-image comparison
$(R^{p} f_{*} F)^{an} \simeq R^{p} f^{an}_{*}(F^{an})$ — is the content of **file 59 (§XII.4)**, the relative
cohomological GAGA.

> **Final slogan for file 58.** *Locally and globally, $X$ and $X^{an}$ carry the same property data; under finite-type
> hypotheses, so do $f$ and $f^{an}$.* The completion isomorphism XII.1.1, the Jacobson and excellence properties of
> $\mathbb{C}$-schemes locally of finite type, the analytic Nullstellensatz, and Serre's prolongation theorem together
> close every clause of XII.2 and XII.3.
