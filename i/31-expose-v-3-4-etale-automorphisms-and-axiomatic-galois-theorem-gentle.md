# Exposé V §§3–4 (gentle): étale automorphisms and the axiomatic Galois theorem

<!-- source: V.3 -->

## What this file is about

Classical Galois theory pairs an algebraic equation with a finite group encoding how its roots permute. Pick a
polynomial; the group is its Galois group, and the whole subject hangs on recovering that group from the equation.
Grothendieck noticed that the recovery does not really use the equation, or even the field it lives in. It uses only the
shape of the *category* of finite extensions, together with the rule that sends each extension to its set of embeddings
into a fixed algebraic closure.

Strip the field away. Six structural conditions on a category and an accompanying set-valued functor capture exactly
what classical Galois theory needed. Any pair meeting them is the category of finite sets on which some compact symmetry
group acts continuously, and the group is uniquely determined by the data. The geometric setting of Exposés I–IV —
finite étale coverings of a scheme, with each cover sent to its geometric fibre — meets the six conditions verbatim. The
symmetry group that falls out is the étale fundamental group of the scheme.

## Opening: from concrete étale covers to the axiomatic theorem

§3 finishes the étale-cover side of the story: it verifies the structural axioms (G1)–(G6) for the category of finite
étale coverings of a connected locally noetherian base, in the form that file 33 will use to apply Theorem V.4.1. The
proofs are short, but the content is what makes the apparatus mean what it is supposed to mean: every morphism of étale
coverings factors as a strict epimorphism (the surjective étale piece) followed by the inclusion of an open-and-closed
subset, and étale coverings are determined by their geometric fibre at any single point.

§4 abstracts these properties to the six axioms (G1)–(G6) on a pair $(\mathcal{C}, F)$ of a category and a
finite-set-valued functor, and proves the centerpiece **V.4.1**: such a pair is equivalent to
$(\mathcal{C}(\pi), forget)$ for a uniquely-determined profinite group $\pi$. The proof builds the pro-object $P$
representing $F$, extracts the group $\pi = \operatorname{Aut}(P)$ topologised as the projective limit of the finite
groups $\operatorname{Aut}(P_{i})$ for the cofinal Galois sub-system, and constructs the inverse functor
$G(E) = P \times_{\pi} E$. This is the **abstract Galois theorem**, and it is the algebraic generalisation of the
topological main theorem of file 28 ($\mathcal{C}^{top}_{B} \simeq \mathcal{C}(\hat{\pi}^{top}_{1})$).

The §3 results are pure étale geometry; the §4 result is pure category theory. The two halves come together in file 33,
where we apply V.4.1 to $\mathcal{C} =$ finite étale coverings of$S$, with$F =$ geometric fibre at $a$. The output is
$\pi = \pi_{1}(S, a)$.

## §V.3 Automorphisms and morphisms of étale coverings

### V.3.1 — Quotients of étale coverings are étale

<!-- source: V.3.1 -->

_This result says: if a finite group $G$ acts on an étale separated finite-type $Y$-scheme $X$ by $Y$-automorphisms, the
action is admissible and $X / G$ is étale over $Y$._

**Proposition.** Let $X$ be étale, separated, and of finite type over a locally noetherian $Y$, and let $G$ be a finite
group acting on $X$ by $Y$-automorphisms. Then $G$ operates admissibly on $X$, and the quotient prescheme $X / G$ is
étale over $Y$.

(Note: $X$ need not be finite over $Y$. It is, however, **quasi- projective** over $Y$, which suffices for V.1.8.)

**Proof.** Quasi-projectivity gives admissibility (V.1.8: every orbit lies in an affine open). The étaleness of $X / G$
over $Y$ follows from the next two results: V.3.2 says $X \to X / G$ is étale, and V.3.3 then says the third of the
triangle $X \to X / G \to Y$ is étale.

### V.3.2 — $X \to X / G$ is étale

<!-- source: V.3.2 -->

_This result says: under V.3.1's hypotheses, the morphism $X \to X / G$ is itself étale._

**Corollary.** The morphism $X \to X / G$ is étale.

**Proof.** Reduce to $G$ faithful on $X$ and $X$ connected. Then the étale-and-faithful case V.2.4 gives trivial
inertia, and V.2.3 yields étaleness of $X \to X / G$.

### V.3.3 — Lemma "remorse about Exposé I"

<!-- source: V.3.3 -->

_This lemma says: if two of the morphisms $X \to X' \to Y$ are étale at marked points, the third is étale too. The lemma
is "remorseful" because it should have appeared in Exposé I; the gentle reader can read it as completing the I.4 sorites
with the third leg of the triangle._

**Lemma.** Let $X \to X' \to Y$ be morphisms of finite type, with $Y$ locally noetherian. Let $x \in X$ with images
$x' \in X'$ and $y \in Y$. If two of the three morphisms are étale at the relevant marked points, then so is the third.

**Proof of the case relevant to V.3.1.** Suppose $X \to X'$ and $X \to Y$ are étale at $x$. We want $X' \to Y$ étale at
$x'$. Make a flat extension of $Y$ so that the residue extension $\kappa(x) / \kappa(y)$ becomes trivial. Then the
completion homomorphisms

$$
\hat{\mathcal{O}}_{y}  \to  \hat{\mathcal{O}}_{x'}  \to  \hat{\mathcal{O}}_{x}
$$

are such that the composite and the second factor are isomorphisms, so the first factor
$\hat{\mathcal{O}}_{y} \to \hat{\mathcal{O}}_{x'}$ is an isomorphism too, proving étaleness of $X' \to Y$ at $x'$.

### V.3.4 — Finite étale quotients

<!-- source: V.3.4 -->

_This result says: if $X$ is finite étale over $Y$ and $G$ acts by $Y$-automorphisms, then $X / G$ is finite étale over
$Y$._

**Corollary.** If $X$ is finite and étale over $Y$, then $X / G$ is finite and étale over $Y$.

**Proof.** Étaleness of $X / G$ is V.3.1; finiteness follows from V.1.5 (third bullet), since $X$ is finite type over
$Y$.

### V.3.5 — Factoring morphisms of étale coverings

<!-- source: V.3.5 -->

_This result says: every morphism of étale coverings of $Y$ factors as a surjective étale morphism followed by the
inclusion of an open-and-closed subset._

**Proposition.** Let $X$ and $X'$ be two étale coverings of $Y$. Every $Y$-morphism $f : X \to X'$ factors as a product

```text
X  --u--→  X″  --i--→  X′,
```

where $u$ is a surjective étale morphism and $i : X'' \to X'$ is the canonical immersion of an open-and-closed subset
$X'' \subseteq X'$.

**Proof.** By I.4.8 (file 11), $f$ is étale, hence open. Since $X$ is finite over $Y$, $f$ is also closed. So
$f(X) = X'' \subseteq X'$ is open and closed.

This is the geometric content of axiom (G3): the factorisation strict-epi + monomorphism-onto-direct-summand exists.

### V.3.6 — The factorisation is strict-epi + strict-mono

<!-- source: V.3.6 -->

_This corollary says: in V.3.5's factorisation, $u$ is a strict epimorphism and $i$ is a strict monomorphism in the
category of preschemes._

**Corollary.** In the V.3.5 factorisation, $u : X \to X''$ is a **strict epimorphism** and $i : X'' \to X'$ is a
**strict monomorphism** in the category of preschemes.

**Proof.** The strict-epi statement uses that $u$ is finite and faithfully flat. (Cf. Grothendieck's Bourbaki seminar
190, that is, [`bourbaki-sem-190`](appendix-black-boxes.md): a finite faithfully flat morphism is a strict epimorphism
in the category of preschemes. The abstract descent framework underlying this fact — fibred categories, cleavages, and
the descent isomorphism — is developed in files 34–38; cf. file 38 §VI.12 for the categorical statement.) The
strict-mono statement is even more elementary: an open-and-closed immersion is a closed immersion, hence a regular
monomorphism, hence a strict monomorphism.

For the categorical purist who prefers other formulations: a factorisation $f = f' f''$ with `f''` a strict epimorphism
and $f'$ a monomorphism is unique up to unique isomorphism in any category. (There may simultaneously exist a _dual_
factorisation $f = f_{1} f_{2}$ with $f_{1}$ a strict monomorphism and $f_{2}$ an epimorphism, also unique up to unique
isomorphism, that is not isomorphic to the first one — in non-abelian categories the two factorisations can differ. The
example to keep in mind is topological vector spaces with non-closed image.)

### V.3.7 — Étale coverings determined by geometric fibres

<!-- source: V.3.7 -->

_This result says: a $Y$-morphism between two étale coverings of a connected $Y$ is an isomorphism iff it induces an
isomorphism on geometric fibres at any single chosen point._

**Proposition.** Let $Y$ be a **connected** locally noetherian prescheme, let $y \in Y$, and let $\Omega$ be an
algebraically closed extension of $\kappa(y)$. For every $X / Y$, denote by $X(\Omega)$ the set of points of $X$ with
values in $\Omega$ (= the geometric fibre over $y$). Let $X, X'$ be étale coverings of $Y$, and let $u : X \to X'$ be a
$Y$-morphism such that the corresponding map $X(\Omega) \to X'(\Omega)$ is a bijection. Then $u$ is an isomorphism.

**Proof.** Reduce to $X'$ connected. Since $X \to X'$ is finite étale, the geometric fibre cardinality
$r(u) = |u^{-1}(\bar{x}')|$ is locally constant on $X'$ (by I.4.5 of file 11), hence constant on connected $X'$. The map
$X(\Omega) \to X'(\Omega)$ has fibre of size $r(u)$. Bijection ⟹ $r(u) = 1$ ⟹ $u$ is an isomorphism.

This is the crucial **conservativity** statement that powers axiom (G6) for the category of étale coverings.

## §V.4 Axiomatic conditions for a Galois theory

<!-- source: V.4 -->

We now move from concrete étale-cover geometry to the abstract axiomatisation. The pair $(\mathcal{C}, F)$ to be
axiomatised is: a category $\mathcal{C}$ together with a covariant functor $F : \mathcal{C} \to FSet$ to the category of
finite sets. The six axioms (G1)–(G6) record the structural properties of $\mathcal{C}$ (axioms G1, G2, G3) and the
properties of $F$ (axioms G4, G5, G6).

### The axioms (G1)–(G6)

**(G 1)** — $\mathcal{C}$ has a _final object_, and the _fibre product_ of two objects over a third exists in
$\mathcal{C}$. (Equivalently, finite projective limits exist in $\mathcal{C}$.)

**(G 2)** — _Finite sums_ exist in $\mathcal{C}$, hence so does an _initial object_ $\emptyset_{\mathcal{C}}$ (the sum
of the empty family). The _quotient_ of an object by a finite group of automorphisms exists in $\mathcal{C}$.

**(G 3)** — Every morphism $u : X \to Y$ in $\mathcal{C}$ factors as

```text
X  --u′--→  Y′  --u″--→  Y,
```

with $u'$ a **strict epimorphism** and $u''$ a **monomorphism** that is an _isomorphism onto a direct summand_ of $Y$.

**(G 4)** — $F$ is **left exact**, i.e. preserves the final object and commutes with fibre products. (Equivalently,
given (G1), $F$ preserves all finite projective limits.)

**(G 5)** — $F$ _commutes with finite sums_; _carries strict epimorphisms to epimorphisms_; and _commutes with quotients
by finite groups of automorphisms_.

**(G 6)** — $F$ is **conservative**: $F(u)$ an isomorphism in `FSet` ⟹ $u$ is an isomorphism in $\mathcal{C}$.

The reformulation **(G′ 2)** "finite inductive limits exist in $\mathcal{C}$" implies (G 2); **(G′ 5)** "$F$ is right
exact" implies (G 5). The reformulations are equivalent given (G1)–(G6) by the structure theorem V.4.1 below; but
verifying (G2) and (G5) directly is often easier in practice, which is why Grothendieck keeps the weaker forms.

### Theorem V.4.1: the equivalence $\mathcal{C} \simeq \mathcal{C}(\pi)$

<!-- source: V.4.1 -->

_This theorem says: any pair $(\mathcal{C}, F)$ satisfying (G1)–(G6) is canonically equivalent to
$(\mathcal{C}(\pi), forget)$ for a uniquely- determined profinite group $\pi$. Concretely: there exists a pro-object $P$
of $\mathcal{C}$ representing $F$, and $\pi = \operatorname{Aut}(F) = \operatorname{Aut}(P)$, topologised as the
projective limit of the finite groups $\operatorname{Aut}(P_{i})$ over the cofinal Galois sub-system._

**Theorem (Grothendieck).** Let $\mathcal{C}$ be a category satisfying (G1)–(G3), and let $F : \mathcal{C} \to FSet$ be
a covariant functor satisfying (G4)–(G6). Then:

1. $F$ is strictly pro-representable: there exists a pro-object $P = (P_{i})_{i \in I}$ of $\mathcal{C}$, in normal form
   (transition maps $\phi_{ji} : P_{i} \to P_{j}$ epimorphisms; every epimorphism $P_{i} \to P'$ equivalent to one of
   the $\phi_{ji}$), and a functorial isomorphism

    ```text
    F(X)  ≅  Hom_{Pro-𝒞}(P, X)  =  colim_i Hom_𝒞(P_i, X).
    ```

1. The group $\pi := \operatorname{Aut}(P)$ is profinite, the projective limit of the finite groups
   $\operatorname{Aut}(P_{i})$ over the cofinal sub-system of _Galois_ $P_{i}$ (those for which
   $\operatorname{Aut}(P_{i})$ acts simply transitively on $F(P_{i})$).

1. The functor $F : \mathcal{C} \to \mathcal{C}(\pi)$ defined by sending $X \in \mathcal{C}$ to $F(X)$ (a finite set)
   with the natural left action of $\pi$ (factoring through some finite $\operatorname{Aut}(P_{i})$) is an **equivalence
   of categories**.

1. The inverse functor $G : \mathcal{C}(\pi) \to \mathcal{C}$ is given by $G(E) = P \times_{\pi} E$, where
   $P \times_{\pi} E$ is defined as the solution of the universal problem

    ```text
    Hom_𝒞(P ×_π E, X)  ≃  Hom_π(E, Hom(P, X))  =  Hom_π(E, F(X)).
    ```

The proof occupies the bulk of §V.4 of the source. We organise it into three blocks. (The 14-step labelling matches the
source.)

### Proof of V.4.1, block A: preliminaries (steps a, b)

**Step (a) — monomorphisms in $\mathcal{C}$ ↔ monomorphisms in `Set`.**

For $u : X \to Y$ in $\mathcal{C}$, $u$ is a monomorphism iff $F(u)$ is.

_Proof._ $u$ is a monomorphism iff $pr_{1} : X \times_{Y} X \to X$ is an isomorphism. $F$ preserves fibre products by
(G4) and is conservative by (G6), so this property is detected on $F$.

**Step (b) — every object is artinian.**

If $X' \to X'' \to X$ are monomorphisms in $\mathcal{C}$ such that $F(X') \to F(X'')$ and $F(X'') \to F(X)$ have the
same image, then the inclusion $F(X') \to F(X'')$ is an isomorphism (by injectivity plus equal images), so $X' \to X''$
is an isomorphism by (G6). Hence every descending chain of monomorphisms into a fixed $X$ stabilises, since $F(X)$ is
finite.

This is the **artinian** property that the strict pro- representability theorem of file 29 requires.

### Proof of V.4.1, block B: building the pro-object $P$ and the group $\pi$ (steps c, d, e, f, g, h)

**Step (c) — strict pro-representability of $F$.**

Apply [`bourbaki-sem-195`](appendix-black-boxes.md): on an artinian category, a left-exact set-valued functor with
finite values is strictly pro-representable. Output: a normalised pro-object $P = (P_{i})_{i \in I}$ and a functorial
isomorphism

```text
F(X)  =  colim_i Hom_𝒞(P_i, X),
```

realised by an element $\phi \in \lim_{i} F(P_{i}) = F(P)$. The transition morphisms $\phi_{ji} : P_{i} \to P_{j}$ for
$i \geq j$ are epimorphisms; every epimorphism $P_{i} \to P'$ is equivalent to one of these.

**Step (d) — the $P_{i}$ are connected and not initial.**

If some $P_{i}$ were initial ($P_{i} \cong \emptyset_{\mathcal{C}}$), it would have no non-trivial maps out, so for
every $X$ we would have $F(X) = \operatorname{Hom}(P, X)$ mapping to a single-element set, contradicting
$F(\emptyset {}_{\mathcal{C}}) = \emptyset$. So no $P_{i}$ is initial. If some $P_{i}$ decomposed as
$P_{i} = A \amalg B$, then $F(P_{i}) = F(A) \amalg F(B)$ (axiom G5), and the marked element $a_{i} \in F(P_{i})$ lies in
one of the two — say $F(A)$. By the cofinality of the index, some $j \geq i$ has
$\phi_{ij} : P_{j} \to P_{i} = A \amalg B$ factoring through $A \to P_{i}$. Then $F(P_{j}) \to F(P_{i})$ factors through
$F(A)$, but surjectivity forces $F(B) = \emptyset$, hence $B = \emptyset_{\mathcal{C}}$ by (G6). So each $P_{i}$ is
connected.

**Step (e) — every endomorphism of a $P_{i}$ is an automorphism.**

Let $u : P_{i} \to P_{i}$. By (G3), factor as $u = i \circ u'$ with $u'$ a strict epimorphism and $i$ a monomorphism.
Since $P_{i}$ is connected and not initial, the strict-epi $u'$ lands in a non- initial direct summand of $P_{i}$ — but
the only such summand is $P_{i}$ itself. So $i = id$ and $u = u'$ is a strict epi. By (G5), $F(u)$ is an epimorphism in
`FSet`, i.e. surjective; and since $F(P_{i})$ is finite, $F(u)$ is bijective. By (G6), $u$ is an isomorphism.

In particular, $\operatorname{Hom}(P_{i}, P_{i}) = \operatorname{Aut}(P_{i})$ is a _finite group_ (finite because every
endomorphism is determined by its image on $F(P_{i})$, a finite set).

**Step (f) — Galois objects.**

A $P_{i}$ is **Galois** when $\operatorname{Aut}(P_{i})$ acts _simply transitively_ on $F(P_{i})$. Equivalently:

(i) The natural map $\operatorname{Aut}(P_{i}) \to \operatorname{Hom}(P, P_{i}) \simeq F(P_{i})$ (sending
$v \mapsto F(v)(\phi_{i})$) is _bijective_.

(ii) $\operatorname{Aut}(P_{i})$ acts _transitively_ on $F(P_{i})$.

(iii) $\operatorname{Aut}(P_{i})$ acts _simply_ on $F(P_{i})$.

The injectivity is automatic; surjectivity is the content.

**Step (g) — Galois objects are cofinal.**

For every $X \in \mathcal{C}$, there exists a Galois $P_{i}$ such that every $u : P \to X$ factors through
$P \to P_{i} \to X$.

_Sketch._ Take $J = \operatorname{Hom}(P, X) = F(X)$, a finite set. There is some $P_{j}$ with every $P \to X$ factoring
as $P \to P_{j} \to X$. The diagonal morphism $P \to X^{J}$ factors as $P \to P_{j} \to X^{J}$, and by (G3) the second
factor decomposes through a strict-epi $P_{j} \to P_{i}$, with $P_{i}$ a sub-summand of $X^{J}$. One checks $P {}_{i}$
is Galois by an explicit argument: any morphism $\psi : P_{k} \to P_{i}$ (for $k \geq j$ cofinally chosen) is shown to
come from an automorphism of $P_{i}$, by tracing the action on the finite set $J = \operatorname{Hom}(P_{i}, X)$ and
using uniqueness of the strict-epi / mono factorisation. (Full detail in the source proof; cf. also
[Murre/Cadoret Ch. 3](appendix-black-boxes.md), appendix slug `murre-cadoret-galois-categories`, for the cleanest modern
walk-through; and [Lenstra Ch. 3](appendix-black-boxes.md), appendix slug `lenstra-galois-theory-schemes`, for the
alternative axiomatisation that drops the "strict" qualifier on epimorphisms.)

**Step (h) — $\operatorname{Aut}(P)$ is the projective limit of $\operatorname{Aut}(P_{i})$.**

Restricting the projective system to Galois $P_{i}$, we have

```text
Hom(P, P)  =  lim_i Hom(P, P_i)  =  lim_i Hom(P_i, P_i)
            =  lim_i Aut(P_i),
```

with surjective transition maps (because $F$ carries strict- epi to surjective and $F(\phi_{ji}) =$
projection$\operatorname{Aut}(P_{j}) \to \operatorname{Aut}(P_{i})$is surjective, via the simple-transitivity of (f)).
Equip the limit with the projective-limit topology from the discrete topologies on$\operatorname{Aut}(P_{i})$. The
result is **profinite**.

The **fundamental group** of $(\mathcal{C}, F)$ is

```text
π  :=  Aut(P)^{op}  =  lim_i Aut(P_i)^{op},
```

acting on the right on $P$ (and on the left on $F(X) = \operatorname{Hom}(P, X)$ for every $X$). By (g), the action is
**continuous**: the stabiliser of any $\alpha \in F(X)$ contains the open subgroup ${g : g \cdot \alpha = \alpha}$,
which factors through one of the $\pi_{i} = \operatorname{Aut}(P_{i})^{op}$.

Thus we have a covariant functor

```text
F : 𝒞  ⟶  𝒞(π),    X ↦ (F(X), π action).
```

### Proof of V.4.1, block C: the inverse functor $G(E) = P \times_{\pi} E$ (steps i, j, k, l, m, n)

**Step (i) — basic case: $P_{i}$ Galois, $E$ a $\pi_{i}$-set.**

Let $Q \in \mathcal{C}$ carry a right action of a finite group $H$, and let $E$ be a finite set with a left $H$-action.
Then $Q \times_{H} E$ exists and $F(Q) \times_{H} E \simeq F(Q \times_{H} E)$.

_Sketch._ Reduce to $H$ transitive on $E$: write $E = \amalg_{j} E_{j}$ as $H$-orbits,
$Q \times_{H} E = \amalg_{j} Q \times_{H} E_{j}$. For a transitive $E$ with point stabiliser $K \subseteq H$, identify
$Q \times_{H} E \simeq Q / K$, existing by axiom (G2).

**Step (j) — extending to $E \in \mathcal{C}(\pi)$.**

Let $E \in \mathcal{C}(\pi)$ and let $P_{i}$ be Galois such that $\pi_{i}$ acts on $E$ (i.e. the action factors through
$\pi \to \pi_{i}$). By (i), $P_{i} \times_{\pi_{i}} E$ exists and $F(P_{i} \times_{\pi_{i}} E) \simeq E$. Moreover, for
any $j \geq i$ with $P_{j}$ Galois, the canonical map $P_{j} \times_{\pi {}_{j}} E \to P_{i} \times_{\pi_{i}} E$ is an
isomorphism (use G6).

**Step (k) — $P \times_{\pi} E$ exists, equal to $P_{i} \times_{\pi_{i}} E$.**

For $X \in \mathcal{C}_{j}$ (the subcategory where $\operatorname{Hom}(P_{j}, X) \to F(X)$ is bijective), and
$j \geq i$,

```text
Hom_π(E, Hom(P, X))  ≃  Hom_π(E, Hom(P_j, X))
                      ≃  Hom_{π_j}(E, Hom(P_j, X))
                      ≃  Hom(P_j ×_{π_j} E, X).
```

Combining with step (j),

```text
Hom_π(E, Hom(P, X))  ≃  Hom(P_i ×_{π_i} E, X),
```

functorially. So $P \times_{\pi} E := P_{i} \times_{\pi_{i}} E$ solves the universal problem; we set
$G(E) := P \times_{\pi} E$.

**Step (l) — the unit $\alpha : id_{\mathcal{C}(\pi)} \to F G$.**

The natural map

```text
α(E) :  E  ⟶  F G(E)  =  F(P ×_π E),
```

defined as the composite $E \to F(P) \times_{\pi} E \to F(P \times_{\pi} E)$, is an isomorphism (by step j, since
$F(P) \times_{\pi} E = (\lim_{i} \operatorname{Aut}(P_{i})) \times_{\pi} E \simeq E$ once one identifies
$\lim_{i} \operatorname{Aut}(P_{i})$ with $\pi$ and recalls that $\pi$ acts simply transitively on itself).

**Step (m) — the counit $\beta : G F \to id_{\mathcal{C}}$.**

The associated $\pi$-homomorphism $F(X) \to \operatorname{Hom}(P, X)$ (inverse of the canonical iso
$\operatorname{Hom}(P, X) \to F(X)$) corresponds to a morphism $\beta(X) : P \times_{\pi} F(X) \to X$. The composites

```text
F(X)  --α(F(X))-->  F G F(X)  --F(β(X))-->  F(X),
G(E)  --G(α(E))-->  G F G(E)  --β(G(E))-->  G(E)
```

are the identity isomorphisms (formal verification: "the donkey trots", in Grothendieck's phrase).

**Step (n) — $\beta$ is an isomorphism.**

Combine with step (l) and the conservativity (G6) of $F$: if $F(\beta(X))$ is an isomorphism (which it is, by step l),
then $\beta(X)$ is an isomorphism.

This finishes the proof of V.4.1.

### V.4.2 — Equivalent formulations and a footnote

<!-- source: V.4.2 -->

_This remark says: (G2) and (G5) admit the stronger formulations (G′ 2) "finite inductive limits exist in $\mathcal{C}$"
and (G′ 5\) "$F$ is right exact". The stronger forms are *equivalent* to the original axioms by V.4.1 itself, since
$\mathcal{C}(\pi)$ has all finite inductive limits and $forget : \mathcal{C}(\pi) \to FSet$ is right exact. Verifying
the stronger forms upfront seems harder in practice, which is why Grothendieck keeps the weaker (G2), (G5)._

**Remark.** The statement of (G1)–(G6) becomes simpler if (G2) and (G5) are replaced by the apparently stronger:

**(G′ 2)** Finite inductive limits exist in $\mathcal{C}$.

**(G′ 5)** $F$ is right exact, i.e. commutes with finite inductive limits.

These appear stronger than (G2) and (G5), but follow at once from V.4.1. Note however that in practice — for the étale
covering category that file 33 considers — verifying (G2) and (G5) is effectively easier than verifying (G′ 2) and (G′
5).

(The footnote in V.4.2: Grothendieck remarks that he does not know whether the "isomorphism onto a direct summand" part
of (G3) is essential. Lenstra's _Galois Theory for Schemes_ uses the streamlined axiom system mentioned in file 29's
"Aside"; the equivalence is proved there.)

### Equation reference

<!-- source: eq:V.4.* -->

The functorial isomorphism `F(X) = Hom(P, X) = colim_i Hom(P_i, X)` produced by step (c) is referred to in the source as
equation $V.4.(*)$; we use it in step (k) to identify $\operatorname{Hom}_{\pi}(E, \operatorname{Hom}(P, X))$ with
$\operatorname{Hom}_{\pi_{j}}(E, \operatorname{Hom}(P_{j}, X))$.

## Worked example: $\mathcal{C} = \mathcal{C}(\hat{\mathbb{Z}})$, $F =$ forget

Take $\mathcal{C} = \mathcal{C}(\hat{\mathbb{Z}})$, the category of finite continuous $\hat{\mathbb{Z}}$-sets. The
fundamental functor $F : \mathcal{C} \to FSet$ is the forgetful functor.

**The pro-object $P$.** The connected $\hat{\mathbb{Z}}$-sets are the cosets $\mathbb{Z} / n\mathbb{Z}$ for $n \geq 1$
(with $\hat{\mathbb{Z}}$ acting through its quotient $\mathbb{Z} / n\mathbb{Z}$ by left translation). Every connected
$\hat{\mathbb{Z}}$-set is isomorphic to one of these. The Galois $P_{i}$ are exactly these $\mathbb{Z} / n\mathbb{Z}$
(since $\operatorname{Aut}(\mathbb{Z} / n\mathbb{Z}) = (\mathbb{Z} / n\mathbb{Z})^{\times}$ … wait, need to think).
Actually: $\mathbb{Z} / n\mathbb{Z}$ has automorphism group $(\mathbb{Z} / n\mathbb{Z})^{\times}$ (unit-multiplication),
but $\hat{\mathbb{Z}}$ acts through the *full* $\mathbb{Z} / n\mathbb{Z}$ by _translation_, and
$\operatorname{Aut}_{\mathcal{C}(\hat{\mathbb{Z}})}(\mathbb{Z} / n\mathbb{Z}) = \mathbb{Z} / n\mathbb{Z}$ acts _by
translation_ — i.e. via right cosets. The simple- transitivity is "right translation acts simply transitively on left
cosets", which is true. So all the $\mathbb{Z} / n\mathbb{Z}$ are Galois.

The $P_{i}$ form the projective system $(\mathbb{Z} / n\mathbb{Z})_{n}$ along the divisibility ordering, with transition
maps $\mathbb{Z} / m\mathbb{Z} \to \mathbb{Z} / n\mathbb{Z}$ for $n | m$ the obvious surjections. By construction,

```text
P  =  lim_n ℤ / nℤ  =  ℤ̂,
```

and $\pi = \operatorname{Aut}(P)^{op} = \hat{\mathbb{Z}}^{op} = \hat{\mathbb{Z}}$ ($\hat{\mathbb{Z}}$ is abelian).

**The equivalence $F : \mathcal{C}(\hat{\mathbb{Z}}) \to \mathcal{C}(\hat{\mathbb{Z}})$.** This is the identity functor
(modulo the cosmetic op-versus-not-op swap that disappears since $\hat{\mathbb{Z}}$ is abelian). The "typical case"
$\mathcal{C} = \mathcal{C}(\pi)$ with $F =$ forget reads off$\pi$ itself as the output of V.4.1.

**The inverse functor $G(E) = P \times_{\pi} E$.** For any finite continuous $\hat{\mathbb{Z}}$-set $E$ (factoring
through some $\mathbb{Z} / n\mathbb{Z}$):

```text
P ×_{ℤ̂} E  =  (ℤ / nℤ) ×_{ℤ / nℤ} E  =  E,
```

confirming $G \circ F = id$.

This worked example is the **base case** for file 33's
$\pi_{1}(\operatorname{Spec} \mathbb{F}_{p}, \bar{a}) = \hat{\mathbb{Z}}$ calculation. The category
$\mathcal{C}(\operatorname{Spec} \mathbb{F}_{p}) =$ finite étale coverings of$\operatorname{Spec} \mathbb{F}*p$is
equivalent (as a Galois category) to$\mathcal{C}(\hat{\mathbb{Z}})$, with the equivalence sending the étale
cover$\operatorname{Spec} \mathbb{F}_{p^{n}} \to \operatorname{Spec} \mathbb{F}_{p}$to
the$\hat{\mathbb{Z}}$-set$\mathbb{Z} / n\mathbb{Z}$on which$\hat{\mathbb{Z}}$acts by translation through its
quotient$\mathbb{Z} / n\mathbb{Z}$.

## What this prepares

File 32 (= V.5, V.6) develops the formalism — the fundamental groupoid, the fundamental pro-group, the dictionary
between exact functors and continuous group homomorphisms — using V.4.1 as the engine.

File 33 (= V.7) applies V.4.1 to the category of finite étale coverings of a connected locally noetherian $S$, with
$F =$ geometric fibre at$a$. Verification of axioms (G1)–(G6) uses V.3.1 (admissibility), V.3.4 (étale quotient),
V.3.5–V.3.6 (strict-epi factorisation), and V.3.7 (conservativity); together with file 30's V.1, V.2 sorites, this
completes the verification. The output is$\pi = \pi_{1}(S, a)$.
