# Exposé I, sections 9–11: permanence and normal coverings (gentle)

## What this file is about

The previous file showed that the algebraic notion of a covering map is rigid: small inputs determine it completely.
Rigidity is necessary but not sufficient. A useful structure also has to preserve things — to carry meaningful
properties of the base across to the cover and back. This file shows that it does. Smoothness, the absence of certain
singularities, even-handed dimension, and several close relatives all survive the bridge in both directions.

The file then turns to a parallel question. Classical Galois theory studies field extensions, the algebraic stuff
produced when you adjoin the root of a polynomial. Over a sufficiently well-behaved base, the coverings of the space
correspond exactly to the field extensions of its function field that are clean — no branching — over the space.
Coverings of the space and unbranched extensions of the function field are then the same subject, viewed twice. A
closing section diagnoses, with surgical care, where this dictionary fails and what to look at instead.

The rigidity established in file 11 left one question. An étale extension is hard to deform, hard to twist, and hard to
lift ambiguously — but does it _preserve_ anything you care about? And when the base is well-behaved, does the étale
theory simplify into something computable? Sections I.9 through I.11 close both questions in turn.

The first half is permanence (I.9). For a local étale homomorphism $A \to B$, regularity, reducedness, normality,
dimension, depth, and Cohen–Macaulayness all transfer in both directions. The étale topology survives every classical
local hypothesis you might want to impose. The second half (I.10) specializes to a normal connected base $Y$ and
identifies finite étale covers of $Y$ with the finite separable extensions of the function field that are unramified
over $Y$. Étale geometry over a normal base is the Galois theory of unbranched extensions of the function field. Where
normality fails (I.11), connected étale covers may decompose, but a clean diagnostic — geometrically unibranch points —
sorts the honest failures from the ones rescued by a finer-grained local condition.

Background commutative algebra is in file 06. The standing assumption remains: locally noetherian preschemes.

## I.9 Permanence properties

<!-- source: I.9 -->

Rigidity told us how an étale extension fails to deform. Permanence tells us what it carries. For a local étale
homomorphism $A \to B$, nearly every classical commutative-algebra property of $A$ transfers to $B$ and back. The
source's strategy is two-step: first the properties that already follow from quasi-finite flatness, then the
étale-specific arguments for regular, reduced, and normal.

### General opening

Quasi-finite flatness alone gives the following (no étaleness needed):

- $A$ and $B$ have the same Krull dimension.
- $A$ and $B$ have the same depth.
- Hence $A$ is Cohen-Macaulay iff $B$ is Cohen-Macaulay ([`cm-transfer`](appendix-black-boxes.md#cm-transfer),
  consequence of [`dim-depth-transfer`](appendix-black-boxes.md#dim-depth-transfer)).
- $A$ has no [embedded primes](glossary.md#embedded-prime) iff $B$ has none.
- For any prime $\mathfrak{q} \subset B$ with trace $\mathfrak{p}$ on $A$, $B_{\mathfrak{q}}$ is quasi-finite and flat
  over $A_{\mathfrak{p}}$ (assuming $B$ is [essentially of finite type](glossary.md#essentially-of-finite-type) over
  $A$).
- $A \to B$ is faithfully flat (a flat local homomorphism is faithfully flat).
- $\mathfrak{p}$ and $\mathfrak{q}$ have the same rank when they correspond.

Standard facts about flat morphisms with zero-dimensional fibers. We treat them as black boxes.

### Proposition

<!-- source: I.9.1 -->

_This result says: regularity transfers in both directions across local étale extensions._

**Proposition I.9.1.** Let $A \to B$ be a local étale homomorphism. Then $A$ is **regular** iff $B$ is **regular**.

### Proof

Let $k = \kappa(A)$, $L = \kappa(B)$. Since $A \to B$ is étale, $B$ is flat over $A$, $L = B/\mathfrak{m}B$, and
$\mathfrak{n} = \mathfrak{m}B$ (where $\mathfrak{m} = \mathfrak{m}_{A}$, $\mathfrak{n} = \mathfrak{m}_{B}$). The
$\mathfrak{m}$-adic and $\mathfrak{n}$-adic filtrations on $B$ agree. Therefore the associated graded rings satisfy

```text
gr_𝔫(B) = gr_𝔪(A) ⊗_k L.
```

Either side is a polynomial algebra (over $k$, resp. over $L$) iff the other is. Polynomial associated graded is the
regularity criterion. Done.

### Comment

The source notes: "we did not use the fact that $L/k$ is separable." The argument runs purely on flatness plus
$\mathfrak{n} = \mathfrak{m}B$.

### Corollary

<!-- source: I.9.2 -->

_This result says: geometrically, étale preserves regularity, and reflects it under surjectivity._

**Corollary I.9.2.** Let $f : X \to Y$ be étale. If $Y$ is regular, then $X$ is regular. The converse holds if $f$ is
**surjective**.

### Proposition

<!-- source: prop:I.9.2 -->

_This result says: étale preserves reducedness, and reflects it under surjectivity._

**Proposition (reduction transfer).** Let $f : X \to Y$ be étale. If $Y$ is **reduced**, then $X$ is reduced. The
converse holds if $f$ is **surjective**.

The geometric statement is equivalent to the algebraic statement below; we prove the algebraic form.

### Corollary

<!-- source: I.9.3 -->

_This result says: algebraic form — $A$ is reduced iff $B$ is, for an étale $A \to B$ with $B$ essentially of finite
type._

**Corollary I.9.3.** Let $f : A \to B$ be a local étale homomorphism with $B$ essentially of finite type over $A$. Then
$A$ is **reduced** iff $B$ is **reduced**.

### Proof

Necessity: $A \to B$ is faithfully flat, hence injective; $B$ reduced forces $A$ reduced.

Sufficiency: assume $A$ reduced. Let $\mathfrak{p}_{i}$ be the minimal primes of $A$. The map
$A \to \prod A/\mathfrak{p}_{i}$ is injective (because $A$ is reduced). Tensoring with the flat $A$-module $B$:

```text
B → ∏ B / 𝔭_i B    is injective.
```

So it suffices to show each $B / \mathfrak{p}_{i} B$ is reduced. Each is étale over $A/\mathfrak{p}_{i}$ (étale is
preserved by base change). So we may assume $A$ integral.

Let $K = Frac(A)$. Then $A \to K$ is injective, and tensoring with $B$ (flat) gives $B \to B \otimes_{A} K$ injective.
So $B \otimes_{A} K$ reduced implies $B$ reduced.

$B$ is essentially of finite type over $A$, so $B = (C)_{\mathfrak{q}}$ for some finite-type $A$-algebra $C$ and a prime
$\mathfrak{q} \subset C$. Then $B \otimes_{A} K$ is a localization of $C \otimes_{A} K$. Since
$X = \operatorname{Spec}(C)$ is étale over $Y = \operatorname{Spec}(A)$, the base change
$X \otimes_{A} K = \operatorname{Spec}(C \otimes_{A} K)$ is étale over `Spec K = Spec(field)`, hence is a finite product
of finite separable field extensions of $K$. In particular reduced. Done.

### Corollary

<!-- source: I.9.4 -->

_This result says: étale preserves analytic reducedness (no nilpotents in the completion)._

**Corollary I.9.4.** Let $f : A \to B$ be a local étale homomorphism. If $A$ is
[**analytically reduced**](glossary.md#analytically-reduced) (`Â` has no nilpotents), then $B$ is analytically reduced
and a fortiori reduced.

### Proof

$\hat{B}$ is finite étale over `Â` (étale on completions; cf. proposition I.4.2). Apply I.9.3 to $\hat{A} \to \hat{B}$.
Done.

### Theorem

<!-- source: I.9.5 -->

_This result says: (i) normality transfers in both directions across étale extensions, and (ii) over a normal $A$,
"injective and net" already implies étale._

**Theorem I.9.5.** Let $f : A \to B$ be a local homomorphism with $B$ essentially of finite type over $A$.

1. If $f$ is étale, $A$ is **normal** iff $B$ is **normal**.
1. If $A$ is **normal**, $f$ is étale iff $f$ is **injective and net**. Then $B$ is normal by (i).

### Proof of (i): two proofs

The source gives two. The first uses only flatness; the second uses I.7.6, which routes through
[Zariski's Main Theorem](appendix-black-boxes.md#zmt). Part (ii) needs [ZMT](appendix-black-boxes.md#zmt) either way.

#### First proof of (i): via Serre's criterion

We use:

[**Serre's criterion**](appendix-black-boxes.md#serre-normality) (Cf. EGA IV 5.8.6.) A noetherian ring $A$ of nonzero
dimension is normal iff:

1. For every prime $\mathfrak{p} \subset A$ of rank 1, $A_{\mathfrak{p}}$ is regular.
1. For every prime $\mathfrak{p} \subset A$ of rank ≥ 2, $depth A_{\mathfrak{p}} \geq 2$.

Black box. Its advantage: no a priori reducedness or integrality.

Now apply this. Primes $\mathfrak{p}$ of $A$ of rank 1 (resp. ≥ 2) are exactly the traces on $A$ of primes
$\mathfrak{q}$ of $B$ of rank 1 (resp. ≥ 2), by the fact that $A \to B$ preserves dimension. For corresponding
$\mathfrak{p} \leftrightarrow \mathfrak{q}$, $B_{\mathfrak{q}}$ is étale over $A_{\mathfrak{p}}$, hence has the same
depth (depth is preserved by flat morphisms with zero-dimensional fibers), and is regular iff $A_{\mathfrak{p}}$ is
regular by I.9.1. Serre's criterion transfers.

#### Second proof of (i): via I.7.6 and trace formulas

Suppose $B$ is normal. Let $L = Frac(B)$, $K = Frac(A)$. Then $A$ is integral (because $B$ is and $A \to B$ is
injective). From the proof of I.9.3, $B \otimes_{A} K$ is a finite product of fields. As it is contained in $L$ and
contains $B$, $B \otimes_{A} K = L$.

Take $x \in K$ integral over $A$. Then $x$ is integral over $B$ (as $x \in K \subseteq L$), hence $x \in B$ ($B$
normal), hence $x \in B \cap K = A$ (faithful flatness gives $B \cap K = A$). Done for "$B$ normal ⟹ $A$ normal."

For "$A$ normal ⟹ $B$ normal": apply I.7.6 to write $B = B'_{\mathfrak{n}}$ with $B' = A[t]/FA[t]$, $F$ monic. Then
$L = B \otimes_{A} K$ is a localization of $B' \otimes_{A} K = K[t]/FK[t]$, which is a product of finite separable
extensions of $K$. In particular, $L$ is a direct factor of $K[t]/F K[t]$, corresponding to a factorization
$F = F_{1} F_{2}$ in `K[t]` with $F_{1}$ annihilating `t mod L`.

By normality of $A$, $F_{1}, F_{2} \in A[t]$, both monic. With minimal choice of $F$, $F_{2} = 1$, so $F = F_{1}$ and

```text
L = B ⊗_A K = K[t] / F K[t].
```

$F$ is consequently a separable polynomial in `K[t]` (since $F'(u) \neq 0$ for $u$ the class of $t$ in $L$).

A computational lemma now finishes:

#### Lemma

<!-- source: I.9.6 -->

_This result says: a trace-pairing identity for $K[t]/F$ with $F$ monic separable — the basis $u^{i}$ is dual to
$u^{i} / F'(u)$ up to a unit determinant._

**Lemma I.9.6.** Let $K$ be a ring, $F \in K[t]$ a monic separable polynomial, $L = K[t]/FK[t]$, $u = class of t \in L$,
so $F'(u)$ is invertible in $L$. Then for $n = deg F$:

```text
tr_{L/K}(uⁱ / F′(u)) = 0    for 0 ≤ i < n − 1,
tr_{L/K}(uⁿ⁻¹ / F′(u)) = 1.
```

#### Corollary

<!-- source: I.9.7 -->

_This result says: the matrix expressing the trace-dual basis has determinant $(-1)^{n(n-1)/2}$, hence is invertible in
any subring._

**Corollary I.9.7.** The matrix $(u^{j} \cdot u^{i} / F'(u))_{0 \leq i, j \leq n-1}$ has determinant $(-1)^{n(n-1)/2}$,
invertible in any subring $A \subseteq K$.

#### Corollary

<!-- source: I.9.8 -->

_This result says: the trace dual of the $A$-module generated by $u^{i}$ is the $A$-module generated by
$u^{i} / F'(u)$._

**Corollary I.9.8.** With $A \subseteq K$, let $V = \langle u^{i} : 0 \leq i \leq n-1\rangle_{A}$ and
$V' = {x \in L : tr_{L/K}(xy) \in A for all y \in V}$. Then $V'$ is the $A$-module with basis $u^{i} / F'(u)$ for
$0 \leq i \leq n-1$.

#### Corollary

<!-- source: I.9.9 -->

_This result says: for normal $A$, the integral closure of $A$ in $L = K[t]/F$ lies in $A[u][1/F'(u)]$._

**Corollary I.9.9.** Suppose $A$ is a normal integral ring with field of fractions $K$, and $F \in A[t]$ monic. Then in
the notation above, $V'$ contains the integral closure `Ã` of $A$ in $L$, which is therefore contained in
$A[u][1/F'(u)]$.

#### Concluding (i) of I.9.5

Apply I.9.9 to our situation: $\tilde{A} \subseteq A[u][1/F'(u)] \subseteq B$ (since $F'(u)$ is invertible in $B$, which
contains `A[u]`). So $\tilde{A} \subseteq B$. By [Zariski's Main Theorem](appendix-black-boxes.md#zmt), $B$ is a
localization of `Ã` (or by direct check via $B = A[u]_{\mathfrak{n}}$). `Ã` is normal, hence so is $B$.

### Proof of (ii)

Suppose $A$ normal. We show: $f : A \to B$ étale ⟺ $f$ injective and net.

$\Longrightarrow$ is trivial (étale ⊃ injective and net for the integral case).

$\Longleftarrow$ is the new content. Suppose $f$ is injective and net. Apply I.7.6 to choose $F$ and $\mathfrak{n}$ such
that the relation $(*) : L = B \otimes_{A} K = K[t]/FK[t]$ still holds, with the proviso that $B \to L$ need not be
injective without flatness.

Let $B_{1}$ = image of $B \to L$. Then $B_{1}$ is a localization of $A[u]/FA[u]$ (free over $A$, hence flat). The
morphism $B \to B_{1}$ between étale algebras is étale (by I.4.8) and surjective, hence **an isomorphism**. So
$B = B_{1}$ is flat over $A$, hence étale. Done.

### Comment on order

The source remarks that the last two proofs should be interchanged and the lemma's formal computations split off. We
agree, but follow the source's order to keep correspondences clean.

### Corollary

<!-- source: I.9.10 -->

_This result says: geometric form — étale preserves normality, and reflects it under surjectivity._

**Corollary I.9.10.** Let $f : X \to Y$ be étale. If $Y$ is normal, then $X$ is normal. Conversely if $f$ is surjective.

### Corollary

<!-- source: I.9.11 -->

_This result says: over a normal connected base, a connected dominant net cover is automatically étale and irreducible._

**Corollary I.9.11.** Let $f : X \to Y$ be a **dominant** morphism, with $Y$ normal and $X$ connected. If $f$ is
**net**, then $f$ is **étale**, hence $X$ is normal and irreducible.

### Proof

Let $U$ ⊆ $X$ be the locus where $f$ is étale. $U$ is open (proposition I.4.5) and we must show it is also closed and
nonempty.

**Nonempty**: $f$ is étale at every preimage of the generic point of $Y$, since over a field "unramified" already equals
"étale." Since $f$ dominates, the generic point has at least one preimage.

**Closed**: Let $x \in closure(U)$. Then $x$ lies in the closure of some irreducible component $U_{i}$ of $U$. The
closure $X_{i} := closure(U_{i})$ is an irreducible component of $X$ meeting $U$, so $X_{i}$ dominates $Y$ (every
component of $U$ is flat over $Y$, hence dominates).

Let $y$ be the projection of $x$ to $Y$. Then $\mathcal{O}_{y}$ is integral (since $Y$ is integral at $y$, by normality
plus connectedness), and $\mathcal{O}_{y} \to \mathcal{O}_{x}$ is **injective**. We have $\mathcal{O}_{y}$ normal and
$\mathcal{O}_{y} \to \mathcal{O}_{x}$ net, so by I.9.5 (ii), $\mathcal{O}_{y} \to \mathcal{O}_{x}$ is étale. Hence $f$
is étale at $x$, so $x \in U$. Done.

### Corollary

<!-- source: I.9.12 -->

_This result says: for a dominant finite-type morphism with $Y$ normal and $X$ irreducible, the étale locus is exactly
the complement of the different ideal — the support of $\Omega^{1}_{X/Y}$._

**Corollary I.9.12.** Let $f : X \to Y$ be a dominant morphism of finite type, with $Y$ normal and $X$ irreducible. The
étale locus of $f$ is **exactly** the complement of the support of $\Omega^{1}_{X/Y}$, that is, the complement of the
closed subscheme of $X$ cut out by the different ideal $\mathfrak{d}_{X/Y}$.

### Comment

This is the "less trivial" statement promised in the remark of section I.4 (after proposition I.4.10). It is the
normal-base strengthening of the discriminant criterion.

### Remark

The source warns: a connected étale covering of an irreducible scheme is **not necessarily irreducible** if the base is
not normal. Section I.11 gives examples.

### What to remember

For an étale extension $A \to B$:

- regular ↔ regular,
- reduced ↔ reduced,
- analytically reduced ↔ analytically reduced (one direction),
- normal ↔ normal,
- the étale locus over a normal connected base is closed under specialization (so connected dominant net = étale).

Étale extensions preserve the entire classical local commutative algebra of $A$. This is what makes the étale topology a
viable substitute for the Zariski topology in cohomology theory.

## I.10 Étale coverings of a normal scheme

<!-- source: I.10 -->

Permanence says normality transfers under étale extensions. Combined with the local form from I.7.6, this lets us
identify étale coverings over a normal connected base with classical algebraic data. The function field $K = R(Y)$ is
the bridge: étale coverings of $Y$ correspond to finite separable extensions of $K$ that are unramified over $Y$. The
functor $X \mapsto R(X)$ realizes the correspondence in one direction; normalization realizes it in the other.

### Proposition

<!-- source: I.10.1 -->

_This result says: over a normal connected base, the connected components of an étale separated scheme are integral,
finite over the base in their function fields, and dense open in the normalization._

**Proposition I.10.1.** Let $X$ be étale and separated over a connected normal $Y$ with function field $K$. Then:

- the connected components $X_{i}$ of $X$ are integral,
- their function fields $K_{i}$ are finite separable extensions of $K$,
- each $X_{i}$ is a nonempty open subset of the normalization of $Y$ in $K_{i}$,
- $X$ is a dense open subset of the normalization of $Y$ in $R(X) = \prod K_{i}$.

### Proof

By corollary I.9.10, $X$ is normal. So local rings of $X$ are integral, hence connected components are irreducible. Each
$X_{i}$ is normal, finite, and dominant over $Y$. By a special (almost trivial) case of
[Zariski's Main Theorem](appendix-black-boxes.md#zmt), $X_{i}$ is an open subset of the normalization of $Y$ in $K_{i}$.

### Corollary

<!-- source: I.10.2 -->

_This result says: an étale separated $X/Y$ is a finite covering iff it equals the normalization of $Y$ in its
function-field algebra._

**Corollary I.10.2.** Under I.10.1, $X$ is **finite** over $Y$ (an étale covering) iff $X \simeq Y' :=$ normalization of
$Y$ in $R(X)$.

### Proof

The normalization is finite over $Y$ (because $Y$ is normal and $R(X)/K$ is separable, by the standard finite-extension
theorem). If $X$ is finite over $Y$, then $X \to Y'$ is finite, hence its image is closed and dense in $Y'$, hence
$X = Y'$.

### Definition (unramified extension)

A finite-rank $K$-algebra $L$ is **unramified over $Y$** (or simply unramified over $K$ when $Y$ is understood) if:

- $L$ is a separable algebra over $K$ (a product of finite separable extensions),
- the normalization $Y'$ of $Y$ in $L$ (the disjoint union of normalizations in each $K_{i}$) is unramified, hence by
  I.9.11 étale, over $Y$.

### Corollary

<!-- source: I.10.3 -->

_This result says: connected étale coverings of a normal connected $Y$ are equivalent to finite separable extensions of
the function field unramified over $Y$; the inverse functor is normalization._

**Corollary I.10.3.** For every $X$ finite over $Y$ with each irreducible component dominating $Y$, let $R(X)$ be the
ring of rational functions on $X$. The functor $X \mapsto R(X)$ establishes an **equivalence of categories** from
connected étale coverings of $Y$ to extensions $L/K$ unramified over $Y$. The inverse functor is **normalization**.

### Affine case

Suppose $Y = \operatorname{Spec} A$ for a normal $A$ with field of fractions $K$. Let $L$ be a finite separable
$K$-algebra (product of fields). Then the normalization $Y' = \operatorname{Spec}(A')$ where $A' =$ integral closure of
$A$ in $L$. "Unramified over $Y$" is equivalent to: $A'/A$ is unramified, equivalently étale.

For a local normal $A$, this is equivalent to: each $A'_{\mathfrak{n}}$ for $\mathfrak{n}$ running over the maximal
ideals of $A'$ (the primes above $\mathfrak{m}$) is unramified, hence étale, over the local $A$.

### Discriminant variant

The discriminant criterion of I.4.10 still applies. The source formulates a **flatness-free** variant:

**Variant.** Let $Y$ be locally integral, $A \to B$ corresponding to $X \to Y$ finite, with $X$ dominating $Y$. Then
$A \to B$ is injective (since $X$ dominates $Y$) and $B \to B \otimes_{A} K = L$ is injective. So $tr_{L/K}$ is defined.
There is a fundamental bilinear form $B \times B \to A$ if there exist $x_{1}, \cdots, x_{n} \in B$ (where
$n = [L : K]$) such that

```text
tr_{L/K}(x_i x_j) ∈ A    and    det(tr_{L/K}(x_i x_j)) ∈ A^×.
```

This is the trace pairing being nondegenerate, with all entries in $A$.

### Proposition

<!-- source: I.10.4 -->

_This result says: the function field is unramified, unramifiedness is transitive across normal covers, and it
translates under base change to another normal cover._

**Proposition I.10.4.** Let $Y$ be a normal integral prescheme with function field $K$.

1. $K$ is unramified over $Y$.
1. **Transitivity.** If $L/K$ is unramified over $Y$, $Y'$ is a normal prescheme dominating $Y$ with function field $L$
   (e.g., the normalization of $Y$ in $L$), and $M/L$ is unramified over $Y'$, then $M/K$ is unramified over $Y$.
1. **Translation.** Let $Y'$ be a normal integral prescheme dominating $Y$ with function field $K'/K$. If $L/K$ is
   unramified over $Y$, then $L \otimes_{K} K'$ is an extension of $K'$ unramified over $Y'$.

### Corollary

<!-- source: I.10.5 -->

_This result says: affine form — the normalization in the tensor-product extension is the tensor product of
normalizations._

**Corollary I.10.5.** Under (iii), if $Y = \operatorname{Spec} A$ and $Y' = \operatorname{Spec} A'$, the normalization
$\bar{A}'$ of $Y'$ in $L' = L \otimes_{K} K'$ identifies with $\bar{A} \otimes_{A} A'$, where `Ā` is the normalization
of $A$ in $L$.

### Corollary

<!-- source: I.10.6 -->

*This result says: the integral closure in a compositum is generated by the two factor integral closures — *only* under
the unramifiedness hypothesis.*

**Corollary I.10.6.** Under (iii), let $L_{1}$ be a compositum of $L/K$ and $K'/K$ inside some larger field. Then
$L_{1}/K'$ is unramified over $Y'$. In the affine case $Y = \operatorname{Spec} A$, $Y' = \operatorname{Spec} A'$,

$$
\bar{A}_{1} = A[\bar{A}, A'],
$$

i.e. the integral closure of $A'$ in $L_{1}$ is generated as an $A$-algebra by $A'$ and `Ā`.

### Comment

The source notes that this last fact is **false** without the unramifiedness hypothesis, even for composita of number
fields.

### Geometric number of points

The source now turns to the intuitive image: an étale covering should have the **maximum number of geometric points**
over each point of $Y$. This is captured via **upper semicontinuity** of the geometric fiber count.

### Universally open morphisms

Recall: $f : X \to Y$ of finite type is **universally open** if for every base extension $Y' \to Y$ (with $Y'$ locally
noetherian), the base change $f' : X' \to Y'$ is open. One can restrict to $Y'$ of finite type or even
$Y' = Y[t_{1}, \cdots, t_{r}]$.

A universally open morphism is open. Conversely, if $Y$ is normal and irreducible and $f$ is open with all components of
fibers of the same dimension (the dimension of the generic fiber), then $f$ is universally open. So for $f : X \to Y$
quasi-finite with $Y$ normal irreducible, $f$ is universally open iff every irreducible component of $X$ dominates $Y$.
Flat morphisms of finite type are universally open.

### Proposition

<!-- source: I.10.7 -->

_This result says: for quasi-finite separated universally open morphisms, the geometric point count $n(y)$ is upper
semicontinuous; constancy near $y$ forces finiteness on a neighborhood._

**Proposition I.10.7.** Let $f : X \to Y$ be quasi-finite, separated, universally open. For each $y \in Y$, let $n(y)$
be the geometric number of points of the fiber $f^{-1}(y)$:

```text
n(y) = Σ_{x ∈ f⁻¹(y)} [κ(x) : κ(y)]_s
```

(sum of separable degrees of residue extensions). Then $y \mapsto n(y)$ is **upper semicontinuous** on $Y$. Constancy of
$n(y)$ near $y$ (equality $n(y) = n(z_{i})$ for $z_{i}$ the generic points of components of $Y$ containing $y$) implies
the existence of a neighborhood $U$ of $y$ such that $X|U$ is **finite** over $U$. (Cf. EGA IV 15.5.1.)

### Black box

Treated as a black box in the source. The proof uses **Chevalley's technique of constructible sets** and a little
**descent theory**.

### Corollary

<!-- source: I.10.8 -->

_This result says: constancy of $n(y)$ plus geometrically unibranch $Y$ forces the irreducible components of $X$ to be
disjoint._

**Corollary I.10.8.** If $n(y)$ is constant and $Y$ is geometrically unibranch (cf. section I.11 below), then the
irreducible components of $X$ are disjoint.

### Proposition

<!-- source: I.10.9 -->

_This result says: for étale separated $f$, constancy of $n(y)$ is equivalent to $X|U$ being a finite étale covering on
a neighborhood._

**Proposition I.10.9.** Let $f : X \to Y$ be étale and separated. Then $n(y)$ is upper semicontinuous, and constancy
near $y$ is equivalent to existence of a neighborhood $U$ of $y$ such that $X|U$ is **finite** over $U$, i.e. an **étale
covering** of $U$.

### Corollary

<!-- source: I.10.10 -->

_This result says: over a connected base, an étale separated morphism is a finite étale covering iff all fibers have the
same geometric point count._

**Corollary I.10.10.** For $f : X \to Y$ étale and separated with $Y$ **connected**, $f$ is finite (i.e. $X$ is an étale
covering of $Y$) iff all fibers have the **same** geometric number of points.

### Theorem

<!-- source: I.10.11 -->

_This result says: for quasi-finite separated $f$ with $Y$ irreducible normal and $X$ reduced dominating, the geometric
point count $n(y)$ is at most the degree, with equality exactly when $X|U$ is a finite étale covering._

**Theorem I.10.11.** Let $f : X \to Y$ be quasi-finite and separated, with $Y$ irreducible, every component of $X$
dominating $Y$, and $X$ reduced. Let $n$ be the **degree** of $X$ over $Y$ (sum of degrees over $K = \kappa(generic)$ of
the function fields $K_{i}$ of components $X_{i}$). Let $y \in Y$ be a **normal** point. Then $n(y) \leq n$, with
equality iff there is a neighborhood $U$ of $y$ such that $X|U$ is an **étale covering** of $U$.

### Proof

The "only if" is trivial. For the "if": let $z$ be the generic point of $Y$. Then
$n(z) = \Sigma [K_{i} : K]_{s} \leq n$. By I.10.7, $n(y) \leq n(z) \leq n$, with equality forcing $X|U$ finite over $U$
for some neighborhood $U$.

So we may assume $X$ finite over $Y$ and $n(y')$ constant. By I.10.8, $X$ is the disjoint union of its components, so we
reduce to $X$ irreducible, hence integral. Reduce further to $Y = \operatorname{Spec} \mathcal{O}_{y}$. The theorem
becomes:

#### Corollary

<!-- source: I.10.12 -->

_This result says: local form — for normal local $A$, the separable degree of $B/\mathfrak{m}B$ is at most $n_{s}$, with
equality iff $B$ is unramified, hence étale, over $A$._

**Corollary I.10.12.** Let $A$ be a normal local noetherian ring with field of fractions $K$. Let $L$ be a finite
extension of $K$ of degree $n$, separable degree $n_{s}$. Let $B \subseteq L$ be a subring finite over $A$ with
$Frac(B) = L$. Let $\mathfrak{m}$ be the maximal of $A$ and let $n'$ be the separable degree of $B/\mathfrak{m}B$ over
$A/\mathfrak{m} = k$ (the sum of separable degrees of the residue extensions of $B/\mathfrak{m}B$). Then
$n' \leq n_{s} \leq n$, with $n' = n$ iff $B$ is unramified, hence étale, over $A$.

### Proof of I.10.12

We must show $n' = n$ ⟹ $B$ étale over $A$. Assume $k$ is infinite (reduction to this case is below).

Suppose $B$ not étale, then $R := B/\mathfrak{m}B$ is not separable over $k$. By a classical lemma, there exists
$a \in R$ whose minimal polynomial over $k$ has degree $> n'$. Lift $a$ to $x \in B$. The minimal polynomial of $x$ over
$K$ (as element of $L$) has degree $\leq n$ and, by $A$ normal, has coefficients in $A$. Reducing mod $\mathfrak{m}$
gives a monic polynomial in `k[t]` of degree $\leq n = n'$ annihilating $a$, contradicting `deg(min poly of a) > n′`.

For $k$ finite: pass to $Y' = \operatorname{Spec} A[t]$, faithfully flat over $Y$, and the generic point $y'$ of the
fiber over $y$. $X$ is net at $y$ over $Y$ iff $X' = X \times_{Y} Y' = \operatorname{Spec}(B[t])$ is net at $y'$ over
$Y'$. The residue field at $y'$ is $k(t)$, infinite. $y'$ is normal in $Y'$, so the previous case applies. Done.

### What to remember

- Over a normal connected $Y$, étale coverings of $Y$ and finite-separable-unramified-over-$Y$ extensions of the
  function field are the same data.
- The geometric number of points $n(y)$ of a fiber is upper semicontinuous; constancy is the operational test for a
  neighborhood to be an étale covering.
- For a quasi-finite morphism with $Y$ normal irreducible and $X$ reduced dominating, $n(y) = deg(X/Y)$ characterizes
  étale coverings.
- The equivalence of categories I.10.3 is the bridge between the geometric notion of étale covering and the classical
  field-theoretic notion of "good" finite separable extension.

## I.11 Some complements

<!-- source: I.11 -->

Drop normality and the irreducibility of I.9.11 fails. Two examples make the failure concrete: a curve with an ordinary
double point and a complete integral local ring whose normalization has a non-radicial residue extension. Each carries a
connected reducible étale covering. The diagnostic that survives is **geometrically unibranch**: it isolates the
non-normal points where I.9.11 still holds. The section closes by extending theorem I.8.3 to
[**finite radicial surjective** ("universal homeomorphism") morphisms](appendix-black-boxes.md#univ-homeo-equiv).

### Example a): a curve with an ordinary double point

Let $C$ be an algebraic curve with an ordinary double point $x$. Let $C'$ be its normalization, with two preimages
$a, b \in C'$ of $x$.

Take two copies $C'_{1}, C'_{2}$ of $C'$, with corresponding points $a_{i}, b_{i} \in C'_{i}$. In the disjoint union
$C'_{1} \amalg C'_{2}$, identify

```text
a₁ ↔ b₂,    a₂ ↔ b₁.
```

The result $C''$ is a **connected and reducible** curve, an étale covering of $C$ of **degree 2**.

The reader can check (using a precise definition of the gluing, treated in Chapter VI of EGA in the multiplodocus, or in
Serre's algebraic curves book over an algebraically closed field):

In general, the connected "Galois" étale coverings $C''$ of $C$ whose pullback to $C'$ is a trivial covering are
**cyclic of degree $n$**. For each $n > 0$, one can construct such a connected cyclic étale covering of degree $n$.

In the language of fundamental groups: the quotient of $\pi_{1}(C)$ by the closed normal subgroup generated by the image
of $\pi_{1}(C') \to \pi_{1}(C)$ is the **profinite completion of $\mathbb{Z}$**.

More precisely (the source conjectures): the fundamental group of $C$ should be the topological **free product** of
$\pi_{1}(C')$ and the profinite completion of $\mathbb{Z}$.

These questions gave rise to **descent theory for schemes**. The fibred-category framework that organises descent is
developed in files 34–38 (Exposé VI); the geometric specialisation to faithfully flat covers is the subject of the
deferred Exposés VIII–IX.

### Example b): a complete integral local ring

Let $A$ be a complete integral local ring. By [Nagata's theorem](appendix-black-boxes.md#nagata-finite), the
normalization $A'$ is finite over $A$, hence semilocal and complete, hence **local** (since $A$ is integral and
$A' \subseteq Frac(A)$).

Suppose the residue extension $L/k = \kappa(A')/\kappa(A)$ is **not radicial**. We will say $A$ is **not geometrically
unibranch** (definition below). For instance,

```text
A = ℝ[[s, t]] / (s² + t²),
```

where $\mathbb{R}$ is the field of real numbers. Here $A'$ is $\mathbb{C}[[u]]$ for $u = (s + it)/(s - it)$ or similar,
with residue field extension $\mathbb{C}/\mathbb{R}$, not radicial.

Let $k' \supset k$ be a finite Galois extension such that $L \otimes_{k} k'$ **decomposes** (e.g., $k' = \mathbb{C}$ for
$k = \mathbb{R}$, $L = \mathbb{C}$). Let $B$ be a finite étale $A$-algebra corresponding to $k'$ (essentially unique by
I.6.1).

Then $B' := A' \otimes_{A} B$. Its residue algebra is $L \otimes_{k} k'$, which is not local. So $B'$ is not local,
hence (being complete) has zero divisors.

Since $B'$ is contained in the total ring of fractions of $B$ (as $B'$ is $A'$-free, hence $A$-torsion-free, hence
contained in $B \otimes_{A} K$ for $K = Frac(A)$), and

```text
B′ ⊗_A K = A′ ⊗_A B ⊗_A K = K ⊗_K B_K = B_K,
```

(using $A' \otimes_{A} K = K$), we get $B$ not integral.

For the example $A = \mathbb{R}[[s, t]]/(s^{2} + t^{2})$ and $k' = \mathbb{C}$, $B$ is the local ring of two
intersecting lines in the plane at the intersection point. Connected, but **two components**.

### Connection to ramification

The source observes: in both examples, a connected étale cover $X$ of an integral non-normal $Y$ is **reducible**. Each
irreducible component of $X$ then gives an example of an unramified $X' \to Y$ that **dominates** $Y$ but is **not
étale**.

In example a), $C' \to C$ is unramified but not étale at `a, b`. From the formal viewpoint, $C'$ at $a$ identifies with
a closed subscheme of $C$ at $x$, namely one of the two "branches" of $C$ through $x$.

### Definition (geometrically unibranch)

An integral local ring $A$ is **geometrically unibranch** if its normalization $A'$ has only one maximal ideal, with
residue extension $L/k$ **radicial**.

A point $y$ of an integral prescheme is **geometrically unibranch** if its local ring is.

### Examples

- A **normal** point is geometrically unibranch ($A = A'$).
- An **ordinary cusp** of a curve is geometrically unibranch.
- An **ordinary node** is **not** geometrically unibranch.
- The local ring of $\mathbb{R}[[s, t]]/(s^{2} + t^{2})$ at the origin is **not** geometrically unibranch over
  $\mathbb{R}$.

### Conjecture and theorem

The source states: if $Y$ has a non-unibranch point, there always exists a connected non-irreducible étale covering of
$Y$ (verified for `Y = Spec(complete local)` in example b)).

By contrast, if **every** point of $Y$ is geometrically unibranch, then every connected unramified $Y$-prescheme
dominating $Y$ is **étale and irreducible**. The proof repeats the proof of I.9.5 using:

### Generalization of theorem I.8.3

_This result says: a finite radicial surjective morphism induces an equivalence of étale categories — universal
homeomorphisms are invisible to étale geometry._

**Theorem (universal-homeomorphism form).** Let $Y' \to Y$ be a **finite, radicial, surjective** morphism (a "universal
homeomorphism"). The functor

```text
X ↦ X ×_Y Y′
```

from étale $Y$-schemes to étale $Y'$-schemes is an **equivalence of categories**.

### Proof

Black box. Cf. IX 4.10; for a more direct proof, EGA IV 18.10.3, using a variant of I.9.5 for geometrically unibranch
local rings.

### Applications

This applies, for example, when $Y'$ is the **normalization** of $Y$ with $Y$ unibranch and $Y'$ finite over $Y$ (the
typical case in practice), or when $Y''$ is sandwiched between $Y$ and its normalization.

### What to remember

- Connected étale coverings of integral non-normal bases need not be irreducible. Two canonical examples: a curve with
  an ordinary double point, and a complete local integral ring whose normalization has a non-radicial residue extension.
- The diagnostic for "still good behavior" is **geometrically unibranch** points: integral local rings whose
  normalization is local with radicial residue extension.
- For a unibranch base, every connected dominating unramified cover is étale and irreducible.
- Universal homeomorphisms (finite, radicial, surjective) are invisible to the étale category: they induce equivalences
  on étale schemes.

## End of Exposé I

Exposé I is rewritten. Étale morphisms have a definition (flat plus unramified), a hierarchy that places them between
quasi-finite and open immersion, and a discriminant test. They are rigid under nilpotent thickening, determined over a
complete local ring by their residue data, and standardized by a single local form. They preserve every classical local
property under permanence. Over a normal connected base they realize the Galois theory of unramified extensions of the
function field. Where normality fails, the geometrically unibranch diagnostic isolates what is salvaged.

The arc that opened in the reading guide closes here for the étale theory. Topology had covering maps; algebra now has
étale morphisms; and the slogan "étale = local isomorphism" is a working theorem rather than an analogy.

**Continuing on.** Exposé II — _Smooth morphisms: generalities and differential properties_ — is rewritten in files
14–16 in the same gentle style. Smooth morphisms are the algebraic analogue of submersions, étale recovered as smooth of
relative dimension `0`. Exposé III — _Smooth morphisms: extension properties_ — is rewritten in files 19–22 (with prep
files 17–18 on cohomology in low degrees, torsors, the tangent sheaf, and formal schemes). Section III.7 delivers the
headline arithmetic application: every smooth proper curve over a field lifts to a smooth proper curve over any complete
local ring with the same residue field. Exposé IV — _Flat morphisms_ — is rewritten in files 24–27 (with prep file 23 on
the Tor functor, the spectral sequence for composite functors, and Noether's normalization). The headline geometric
application is **generic flatness** (IV.6.11): every coherent sheaf on a finite-type morphism to an integral noetherian
base is flat over a non-empty open of the base. Exposé V — _The fundamental group: generalities_ — is rewritten in files
30–33 (with prep files 28–29 on topological covering theory and profinite groups / pro-objects). The headline
construction is the **étale fundamental group $\pi_{1}(S, a)$** of a connected locally noetherian scheme: a profinite
group whose continuous finite-set actions classify the finite étale coverings of $S$. The Galois theory of étale
coverings is the equivalence $\mathcal{C}(S) \simeq \mathcal{C}(\pi_{1}(S, a))$ of file 33; the file 06
forward-reference to the étale fundamental group is satisfied there.
