# Permanence, normality, and coverings

## What this file is about

A useful test for a good definition: can you push your hypothesis across it and have the hypothesis come out the other
side intact? If "smooth" or "without singularities" survives the trip, the bridge is structural; if those words break
when you cross, the bridge is the wrong one. This file runs that test on the algebraic notion of covering map. Five
standard local properties — being free of nilpotents, being free of certain singularities, being well-dimensioned, and
two close relatives — turn out to transfer in both directions across the bridge. That is the first half of the file.

The second half does what classical Galois theory does for fields, but for spaces. Over a sufficiently well-behaved base
space, the coverings are governed entirely by the algebra of the function field — the field of fractions whose elements
are the rational functions on the base. Coverings of the space and certain field extensions are the same catalogue.

Files 04 and 05 settled what an étale morphism _is_. They left open what an étale morphism is _for_. The covering-map
analogue would have to bring a covering-map's payoff: hypotheses transfer between the two ends of the morphism, and over
a sufficiently nice base the étale covers are governed by Galois theory. This file is the payoff.

The first half is **permanence**. If $f : A \to B$ is an étale extension of local rings, then $A$ and $B$ share
essentially every classical commutative-algebra property: regular, reduced, normal, Cohen-Macaulay all transfer in both
directions. You can move freely between $A$ and $B$ without losing your hypotheses. This is what makes the étale
topology a viable replacement for the Zariski topology in cohomology: étale extensions preserve local geometry.

The second half is the **étale coverings of a normal scheme**. Over a normal connected base $Y$, finite étale coverings
of $Y$ are exactly the finite separable extensions of the function field of $Y$ that are unramified over $Y$. Étale
geometry over a normal base is classical Galois theory of fields. The bridge is the function-field functor.

We motivate each piece, give the algebraic definitions, and state the main results; proofs are in file 12. Section I.11
of the source addresses what goes wrong when normality fails. Even there a clean diagnostic — **geometrically
unibranch** points — tells you when good behaviour is rescued.

## A short tour of the algebra we will use

Three commutative-algebra notions that haven't yet appeared.

### Reduced and integral

A ring $A$ is **reduced** if its **nilradical** $\sqrt{(0)} = { a : a^{n} = 0 for some n}$ is zero. So no nonzero
nilpotents.

A ring is **integral** (or an **integral domain**) if it is nonzero and has no zero divisors. Integral implies reduced.

A scheme is **reduced** if all its local rings are reduced.

Examples:

- $\mathbb{Z}$, $\mathbb{R}[t]$, $\mathbb{C}[x, y]$, every field: reduced.
- $k[\epsilon]/(\epsilon^{2})$: not reduced (the nilpotent $\epsilon$).
- The local ring of a node $k[x, y]/(xy)$ at the origin: reduced (no nilpotents) but not integral ($x$ and $y$ are zero
  divisors).

### Normal: integrally closed

A ring $A$ is **normal** if every localization at a prime is an integrally closed integral domain. "Integrally closed"
means: every element of $Frac(A_{\mathfrak{p}})$ integral over $A_{\mathfrak{p}}$ (satisfying a monic polynomial with
coefficients in $A_{\mathfrak{p}}$) is itself in $A_{\mathfrak{p}}$.

So normal = locally, integral and closed under taking integral extensions inside the field of fractions.

A scheme is **normal** if all its local rings are.

Geometrically, normal means **without certain singularities**. Smooth points are normal; cusps are normal; nodes are
not.

Examples:

- $\mathbb{Z}$ is normal. Its field of fractions is $\mathbb{Q}$. The integers are exactly the elements of $\mathbb{Q}$
  integral over $\mathbb{Z}$.
- $k[t_{1}, \cdots, t_{n}]$ is normal. Polynomial rings over a field are always normal.
- The cuspidal cubic $k[t, s]/(s^{2} - t^{3})$ at the origin is **not** normal. The element $s/t \in Frac$ satisfies
  $(s/t)^{2} = t$, hence is integral over the ring, but does not lie in the ring.
- The nodal cubic $k[t, s]/(s^{2} - t^{2} - t^{3})$ is integral as a ring (the polynomial $s^{2} - t^{2} - t^{3}$ is
  irreducible), but its **completion** at the origin splits into two formal branches. So the local ring at the node is
  integral but not analytically irreducible — equivalently, not **geometrically unibranch**, a notion we meet in the
  section on étale coverings of normal schemes below.

### Why normality earns its keep

Normality is a smoothness condition, but a flexible one. For a normal scheme $Y$:

- The integral closure of $\mathcal{O}_{Y}$ in any finite separable extension of the function field is **finite** over
  $\mathcal{O}_{Y}$.
- Connected unramified covers of $Y$ are automatically étale.
- The trace pairing on a finite separable extension defines a fundamental bilinear form **without flatness
  assumptions**.

Each of these we will use. They are the algebraic engine of the "étale-coverings-of-a-normal-scheme" story.

### Regular: the smoothness condition proper

A noetherian local ring $(A, \mathfrak{m})$ of dimension $n$ is **regular** if its maximal ideal $\mathfrak{m}$ can be
generated by $n$ elements. Equivalently, the dimension of $\mathfrak{m}/\mathfrak{m}^{2}$ over the residue field equals
$n$.

Regular is the algebraic analogue of "smooth point." A scheme is **regular** if all its local rings are.

Regular implies normal (for noetherian local rings of dimension ≥ 1).

### Cohen-Macaulay and depth

Cohen-Macaulay is the next step down from regular. To say what it means, we need depth.

#### Depth, geometrically

Take a point $p$ on a scheme $X$. You can sometimes locally **slice through $p$** with an effective Cartier divisor: cut
$X$ by a function $x_{1}$ that does not vanish identically on any irreducible piece of $X$ near $p$ (algebraically:
$x_{1}$ is not a zero divisor in the local ring at $p$). After slicing, you have a scheme of dimension one lower, still
containing $p$. You can try to slice again with $x_{2}$, and again with $x_{3}$. The **depth** of the local ring at $p$
is how many slices you can make in a row before $p$ becomes "stuck" — formally, before $p$ becomes an associated point
of the remaining slice. Vakil's _Rising Sea_ (§26.1) gives this slicing intuition; Grothendieck's EGA 0_IV §16.4.5 gives
the algebraic version.

Algebraically: an **$M$-regular sequence** in an ideal $I \subseteq A$ is a sequence $x_{1}, \cdots, x_{n} \in I$ such
that each $x_{i}$ is not a zero divisor on $M / (x_{1}, \cdots, x_{i-1}) M$. For $(A, \mathfrak{m})$ a noetherian local
ring and $M$ a finitely generated $A$-module, the **depth** of $M$ is

```text
depth M := sup { n : there is an M-regular sequence x₁, …, x_n in 𝔪 }.
```

Two facts. _(a)_ Maximal $M$-regular sequences in $\mathfrak{m}$ all have the same length, so depth is well-defined and
computable by greedy slicing (Vakil, theorem 26.1.3). _(b)_ `depth M ≤ dim Supp M`, with equality often failing — depth
measures the "slice-ability" of $M$, dimension the "stretch."

#### Cohen-Macaulay = depth meets dimension

A noetherian local ring $(A, \mathfrak{m})$ is **Cohen-Macaulay** if $depth A = \dim A$. A scheme is Cohen-Macaulay if
every local ring is.

Geometrically: you can slice $\operatorname{Spec} A$ at every point with as many effective Cartier divisors as the
dimension allows, never running into an associated point first. Cohen-Macaulay schemes have no embedded points; every
point is "slice-friendly" all the way down.

Regular implies Cohen-Macaulay: a regular local ring of dimension $n$ has its maximal ideal generated by $n$ elements
that form an $A$-regular sequence (Vakil, §26.2.5).

The operational fact, used silently from the start of section I.9 of the source:

> A local quasi-finite flat homomorphism $A \to B$ of noetherian local rings preserves Krull dimension and depth. Hence
> $A$ is Cohen-Macaulay iff $B$ is.

This is [`dim-depth-transfer`](appendix-black-boxes.md#dim-depth-transfer) together with
[`cm-transfer`](appendix-black-boxes.md#cm-transfer) in the appendix. It says that the most basic properties of local
rings (dimension, depth) survive any quasi-finite flat extension — and therefore any étale extension.

We use these five properties — reduced, normal, regular, Cohen-Macaulay, depth — at file 12, where each one is proved to
transfer unchanged across an étale extension. That is why the vocabulary is collected here. The proofs in file 12 will
be short; the substance has to be the definitions themselves, and the geometric meaning each one packages.

## Permanence: what étale preserves

Section I.9 proves that étale local extensions preserve essentially every classical local property of rings. We state
each main result and say why it works.

### Étale and regular

> For a local étale homomorphism $A \to B$, $A$ is regular iff $B$ is regular.

Why this works. Étale forces $\mathfrak{m}_{B} = \mathfrak{m}_{A} \cdot B$, plus flatness. The $\mathfrak{m}$-adic and
$\mathfrak{n}$-adic filtrations on $B$ therefore agree, and the associated graded rings satisfy

```text
gr_𝔫(B) = gr_𝔪(A) ⊗_k κ(B).
```

Either side is a polynomial algebra (over $k$, resp. over $\kappa(B)$) iff the other is. **Polynomial graded ring is the
regularity criterion.** Regularity transfers — étale is set up exactly so that the associated graded behaves correctly.

### Étale and reduced

> For a local étale homomorphism $A \to B$ essentially of finite type, $A$ is reduced iff $B$ is reduced.

One direction is short, the other longer.

For "B reduced ⟹ A reduced": faithful flatness makes $A \to B$ injective, so $A$ embeds in a reduced ring.

For "A reduced ⟹ B reduced": reduce to the case $A$ integral and tensor with $K = Frac(A)$. The fiber over the generic
point $B \otimes_{A} K$ is an étale algebra over a field, hence a finite product of finite separable field extensions —
reduced.

### Étale and normal

The most subtle of the three. Theorem I.9.5 of the source.

> For a local étale homomorphism $A \to B$ essentially of finite type, $A$ is normal iff $B$ is normal.

The source gives two proofs. The first uses [Serre's criterion for normality](appendix-black-boxes.md#serre-normality)
as a black box:

> A noetherian ring $A$ of nonzero dimension is normal iff regular in codimension 1 and depth ≥ 2 in codimension ≥ 2.

The second proof avoids Serre's criterion and uses the local form of étale algebras (story 4 of file 05) plus an
explicit trace-formula computation.

Both routes work. File 12 gives the cleaner first proof.

### Why this is striking

Normality is delicate. Many natural operations break it:

- Polynomial extensions: `A[t]` is normal iff $A$ is. Stable under this.
- Localization: $S^{-1}A$ is normal iff $A$ is, for nice $S$. Stable.
- Tensor product $A \otimes B$: in general, **not** normal even if $A$ and $B$ are.

So it is not obvious that **étale extensions** preserve normality. The proof leans on the explicit local form of étale
algebras together with Serre's criterion or trace identities.

### A surprising bonus: net + normal target = étale

Theorem I.9.5 (ii) goes in a different direction.

> If $A$ is normal and $f : A \to B$ is **injective** and **net** (unramified), then $f$ is automatically **étale**.

"Net" is normally strictly weaker than "étale": it lacks flatness. But if $A$ is normal and $f$ is injective, flatness
is forced.

Why. Normality of $A$ plus the local form of $B$ (from file 05) identifies $B$ as a localization of an integral closure
of $A$ in a finite separable extension of $Frac(A)$. That integral closure is automatically $A$-flat, so $B$ is flat,
hence étale.

The pattern — **normal + dominant + connected = irreducibility forced** — unifies many statements in section I.10.

## Connected dominant + normal = étale + irreducible

The local bonus has a global counterpart.

> Let $f : X \to Y$ be a **dominant** morphism with $Y$ normal and $X$ connected. If $f$ is **net**, then $f$ is
> **étale**, and $X$ is automatically **normal and irreducible**.

This is corollary I.9.11. Over a normal connected base, a connected dominant net cover is automatically étale and
irreducible.

Start with a connected unramified cover dominating a normal $Y$, and **flatness comes for free**. The cover must be
étale.

Without normality this fails. Section I.11 gives connected unramified covers of non-normal schemes that are not étale.

### The operational consequence

Over a normal base, the trichotomy "split / extension / ramified" collapses to "unramified or not"; no separate flatness
check is needed. The discriminant, $\Omega^{1}$, and fiber tests of file 04 become the only obstruction. This
simplification is what makes Galois theory of normal schemes tractable.

## Étale coverings of a normal scheme

So far we have shown that étale extensions transfer regularity, reducedness, and normality, and that over a normal
connected base "net" upgrades automatically to "étale" and forces irreducibility. The second half cashes those facts in:
with flatness for free and irreducibility forced, finite étale covers of a normal $Y$ admit a purely field-theoretic
description.

### What it says

Let $Y$ be a **normal connected** scheme with function field $K = \kappa(generic point)$. Define a **finite separable
extension $L/K$ unramified over $Y$** to be a finite product algebra $L = \prod K_{i}$ where each $K_{i} / K$ is a
finite separable field extension and the normalization $Y_{i}$ of $Y$ in $K_{i}$ is unramified — equivalently, étale —
over $Y$.

> The functor
>
> `X ↦ R(X) = ∏ (function fields of irreducible components of X)`
>
> is an **equivalence of categories** from connected étale coverings of $Y$ to finite separable extensions of $K$
> unramified over $Y$.
>
> The inverse functor is **normalization**: given $L/K$ unramified over $Y$, the normalization of $Y$ in $L$ is the
> corresponding étale covering.

This is corollary I.10.3 of the source.

### Why this is beautiful

Étale geometry is the right abstract setting for arithmetic Galois theory. This corollary makes the slogan explicit:

> **Étale geometry over a normal base = unramified Galois theory of the function field.**

The étale fundamental group $\pi_{1}(Y, \bar{y})$, defined in later exposés of SGA 1, is a profinite group. Finite étale
covers of $Y$ correspond bijectively to finite continuous representations of $\pi_{1}(Y, \bar{y})$. Over a normal $Y$,
by the corollary above, these are the same as finite separable extensions of $K$ unramified over $Y$ — that is, the
absolute Galois group of "the maximal extension of $K$ unramified over $Y$."

So the **étale fundamental group is the Galois group of the maximal unramified extension**.

(This forward-reference is satisfied by file 33, V.7–V.8.2. File 33 constructs $\pi_{1}(Y, \bar{y})$ as
$\operatorname{Aut}(F_{\bar{y}})$ for the fibre functor on finite étale coverings of $Y$, and V.8.2 identifies its
kernel-from-$\pi_{1}(\eta, \bar{y})$ with the unramified-over-$Y$ extensions of the function field, recovering the
slogan above verbatim.)

### The dictionary

Let $Y = \operatorname{Spec} A$ for a normal $A$ with field of fractions $K$.

| Geometric side                     | Algebraic side                                          |
| ---------------------------------- | ------------------------------------------------------- |
| Connected étale covering $X \to Y$ | Finite separable extension $L/K$ unramified over $A$    |
| Disjoint union of étale covers     | Finite product $\prod L_{i}/K$ of unramified extensions |
| $R(X) = \prod K_{i}$               | The corresponding extension algebra                     |
| Normalization of $Y$ in $L$        | The étale covering attached to $L$                      |

### Three permanence properties of unramifiedness

For unramified extensions over a normal base:

- $K$ itself is "unramified over $Y$" (trivially).
- **Transitivity.** If $L/K$ is unramified over $Y$ and $M/L$ is unramified over the normalization $Y'$ of $Y$ in $L$,
  then $M/K$ is unramified over $Y$.
- **Translation.** If $L/K$ is unramified over $Y$ and $Y' \to Y$ is a normal cover, then $L \otimes_{K} K' / K'$ is
  unramified over $Y'$.

These are proposition I.10.4. They make the category of "unramified-over-$Y$" extensions a clean tower.

## Counting points: the geometric number of points

The dictionary identifies finite étale covers with field extensions, but it does not yet say what "degree $n$ cover"
looks like fiber by fiber. A finite étale covering of degree $n$ should have, over each point of the base, $n$ discrete
geometric points. We make this precise.

### Definition

For a quasi-finite separated morphism $f : X \to Y$ and $y \in Y$, the **geometric number of points** of the fiber is

```text
n(y) := Σ_{x ∈ f⁻¹(y)} [κ(x) : κ(y)]_s,
```

where $[L : K]_{s}$ is the **separable degree** of $L/K$. The separable degree equals
$|\operatorname{Hom}_{K}(L, \bar{K})|$ for $\bar{K}$ an algebraic closure of $K$.

So $n(y)$ counts the points "with multiplicity coming from the separable degree of each residue extension." Over an
algebraically closed $\kappa(y)$, this is just "the number of points in the fiber."

### Semicontinuity

A standard theorem (proposition I.10.7, treated as a black box from EGA IV §15.5 on semicontinuity of fibre dimensions
for quasi-finite maps):

> For $f : X \to Y$ quasi-finite, separated, and **universally open**, the function $y \mapsto n(y)$ on $Y$ is **upper
> semicontinuous**.

So $n(y)$ does not jump up as $y$ specializes. It can jump down.

### Constancy of $n(y)$ characterizes étale

Over a normal base, constancy of $n(y)$ becomes the test for étale.

> Let $f : X \to Y$ be quasi-finite and separated, with $Y$ irreducible normal, every component of $X$ dominating $Y$,
> and $X$ reduced. Let $n$ be the degree of $X$ over $Y$ (sum of degrees of function-field extensions). Then
> $n(y) \leq n$, with equality iff $f$ is **étale** in a neighborhood of $y$.

This is theorem I.10.11.

Geometrically: an étale covering of degree $n$ over a normal base is one where every fiber has exactly $n$ geometric
points. The operational test for "is this étale?" over a normal base is to count the geometric points and check that you
hit the maximum.

### The example, one more time

For $\operatorname{Spec} \mathbb{Z}[\sqrt{2}] \to \operatorname{Spec} \mathbb{Z}$:

- $n((p)) = 2$ for $p = 7$: fiber $\mathbb{F}_{7} \times \mathbb{F}_{7}$, two points each with residue field
  $\mathbb{F}_{7}$, contributing $[\mathbb{F}_{7} : \mathbb{F}_{7}]_{s} = 1$ each.
- $n((p)) = 2$ for $p = 5$: fiber $\mathbb{F}_{25}$, one point with residue field $\mathbb{F}_{25}$, separable degree
  $[\mathbb{F}_{25} : \mathbb{F}_{5}]_{s} = 2$.
- $n((p)) = 1$ for $p = 2$: fiber $\mathbb{F}_{2}[t]/(t^{2})$, one point. The fiber has a nilpotent $t$, but the
  **residue field** of that point is just $\mathbb{F}_{2}[t]/(t^{2}) / (t) = \mathbb{F}_{2}$, contributing
  $[\mathbb{F}_{2} : \mathbb{F}_{2}]_{s} = 1$.

So $n$ is constant `= 2` on $\operatorname{Spec} \mathbb{Z}[1/2]$ and jumps down to `1` at `(2)`. The étale locus is
exactly where $n$ is constant equal to the degree, which is $\operatorname{Spec} \mathbb{Z}[1/2]$. The ramified prime is
the unique place where $n$ drops.

## When normality fails

The whole second half rested on $Y$ being normal. Section I.11 asks what breaks without that hypothesis. Two pivotal
examples.

### Example a: the nodal curve

Let $C$ be an algebraic curve with an **ordinary double point** (a node) at $x \in C$. Let $C'$ be its normalization,
with two preimages $a, b \in C'$ of $x$.

Take two copies $C'_{1}, C'_{2}$ of $C'$, with corresponding points $a_{i}, b_{i} \in C'_{i}$. Glue them by identifying

```text
a₁ ↔ b₂,    a₂ ↔ b₁.
```

The result is a curve `C''` that is **connected and reducible**: two irreducible components, each a copy of $C'$. The
morphism $C'' \to C$ is finite étale of degree 2, but `C''` has two components.

So even though the cover is "connected" in the topological sense, it has multiple irreducible components. This violates
the "connected étale = irreducible" rule we got over normal bases.

### Why this happens

The local ring $\mathcal{O}_{C, x}$ at the node is not a domain. It has zero divisors $xy = 0$, where `x, y` are the two
branches. A degree-2 cover can "choose differently on each branch," producing two distinct components.

Normality forbids this. A normal local ring is in particular a domain — no "different branches" to choose differently
on.

### Example b: a complete local ring with a non-radicial residue

Take $A = \mathbb{R}[[s, t]] / (s^{2} + t^{2})$. The normalization $A'$ is $\mathbb{C}[[u]]$, with residue field
$\mathbb{C}$. The residue extension $\mathbb{C}/\mathbb{R}$ is not radicial (it is separable, with nontrivial Galois
action).

For the field $k' = \mathbb{C}$, there is a finite étale $A$-algebra $B$ with residue field $\mathbb{C}$. Tensoring with
$A'$ gives an $A'$-algebra with residue algebra
$\mathbb{C} \otimes_{\mathbb{R}} \mathbb{C} \simeq \mathbb{C} \times \mathbb{C}$. Two components in the residue algebra
means two components in $B$ itself.

The explicit $B$ is the local ring of two intersecting lines in the plane at the intersection point. Connected, but two
components.

### The diagnostic: geometrically unibranch

One property fixes both examples.

> An integral local ring $A$ is **geometrically unibranch** if its normalization $A'$ is local and the residue extension
> $\kappa(A') / \kappa(A)$ is **purely inseparable** (radicial).

A point of an integral scheme is geometrically unibranch if its local ring is.

### Examples

- A normal point is geometrically unibranch (the normalization is the ring itself).
- An ordinary cusp on a curve is geometrically unibranch (the normalization is a smooth point with the same residue
  field).
- A node is **not** geometrically unibranch (the normalization has two maximal ideals).
- The local ring of $\mathbb{R}[s, t]/(s^{2} + t^{2})$ at the origin is **not** geometrically unibranch over
  $\mathbb{R}$ (the residue extension $\mathbb{C}/\mathbb{R}$ is separable, not purely inseparable).

### Theorem: unibranch saves you

The source states the rescue without full proof, citing later parts of EGA:

> If every point of $Y$ is geometrically unibranch, then every connected unramified $Y$-prescheme dominating $Y$ is
> étale and irreducible.

Unibranch is the right diagnostic for good behaviour of étale covers. Normal is the strongest case; unibranch — allowing
cusps but not nodes — is the right intermediate generality.

### A larger black box

Section I.11 closes with one more black-box theorem ([`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) in
the appendix):

> A **finite radicial surjective** morphism $Y' \to Y$ (sometimes called a **universal homeomorphism**) induces an
> equivalence of categories of étale covers.

Étale geometry is completely insensitive to universal homeomorphisms — the radicial extension of "the étale topology
does not see infinitesimal thickenings."

Universal homeomorphisms include Frobenius in characteristic $p$. So étale geometry does not see Frobenius. One of the
deep structural facts of étale cohomology.

## Closing

We have spent six files setting the stage for Exposé I. The investment buys two operational principles.

First, **étale extensions preserve essentially every classical local property**. Regular, reduced, normal,
Cohen-Macaulay — all transfer in both directions when the morphism is surjective. So étale is the right notion for
"local geometry that survives extension."

Second, over a normal connected base, **étale coverings are exactly finite separable unramified-over-the-base extensions
of the function field**. Étale geometry over a normal base is the classical Galois theory of fields, with the étale
fundamental group playing the role of the Galois group of the maximal unramified extension.

When normality fails, the natural diagnostic is **geometrically unibranch**. Under unibranchness, connected dominating
unramified covers are still étale and irreducible. Without unibranchness, they need not be — and the examples (nodal
curve, real local ring with complex residue extension) make the failure precise.

Files 10, 11, and 12 now revisit the same material as Exposé I itself, in the source's order, with proofs in detail. The
preparation arc has put every term Grothendieck uses on the page already; the rewrite is no longer about teaching the
vocabulary but about watching the theorems assemble. If you have read this far, you can read the source.

## A closing note on the running example

The morphism $\operatorname{Spec} \mathbb{Z}[\sqrt{2}] \to \operatorname{Spec} \mathbb{Z}$ has carried us through every
preparation file. It is small enough to fit on the page and rich enough to display the full trichotomy: split at most
primes, an extension at the inert ones, ramified at the divisor of the discriminant. That choice was not arbitrary.
$\mathbb{Z}[\sqrt{2}]/\mathbb{Z}$ is the smallest non-trivial example of the kind of arithmetic situation the étale
theory was built to handle.

Restrict the morphism to the open locus where `2` is invertible:
$\operatorname{Spec} \mathbb{Z}[\sqrt{2}] \to \operatorname{Spec} \mathbb{Z}[1/2]$. By the discriminant computation,
this restricted morphism is a **finite étale covering**. The next chapters of SGA (Exposé V, rewritten gently in files
28–33) attach to any connected normal scheme $Y$ an **étale fundamental group** that classifies finite étale coverings
of $Y$ — the algebraic-geometric counterpart of the topological fundamental group. For
$Y = \operatorname{Spec} \mathbb{Z}[1/2]$, our covering corresponds to one specific open subgroup of
$\pi_{1}(\operatorname{Spec} \mathbb{Z}[1/2], \bar{\eta})$ of index 2; by V.8.2 (file 33), this group is the absolute
Galois group of the maximal subextension of $\bar{\mathbb{Q}} / \mathbb{Q}$ unramified outside `2`. The splitting
behaviour we computed at each odd prime tells us exactly which subgroup.

That is the level at which the gentle SGA's running example sits inside the larger story. The mechanism that promotes
"splitting behaviour at primes" to "subgroup of a fundamental group" is the content of class field theory; for the
quadratic case, it reduces to quadratic reciprocity. We will not develop either here.

The point: the discriminant, the ramified prime `(2)`, the splitting behaviour at odd primes — every quantity we
computed for $\mathbb{Z}[\sqrt{2}]/\mathbb{Z}$ — is the right data, and reappears verbatim in the classification
statements of the later exposés. The toy is the machine.
