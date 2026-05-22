# Expose XIII §§3–4 (gentle) — generic local acyclicity, homotopy exact sequences, and the Künneth formula for $\pi^{p'}_{1}$

<!-- source: XIII.3 -->

## What this file is about

Push a sheaf forward along a map and ask: does the value at a base point equal what one sees at the fibre above that
point? The previous file isolated a clean special case. The general case is harder and cannot be settled everywhere —
over special points the comparison can fail. The realistic hypothesis is generic. Restrict to a non-empty open piece of
the base, and over that piece the comparison works for every reasonable coefficient.

This generic statement is the engine behind two structural theorems for the algebraic fundamental group. The first
assembles the fundamental groups of fibre, total space, and base into a three-term sequence — the same kind topologists
write for fibre bundles. The second is a product formula for the part coprime to the characteristic. Both run on inputs
imported from later Grothendieck seminars as black boxes.

File 62 isolated tame ramification along an NC divisor as the operative case of cohomological properness. File 63
extracts the *general* mechanism: **generic local acyclicity** (§XIII.3) gives cohomological properness over a non-empty
open of an irreducible base, and this is exactly the input that produces the **étale homotopy exact sequence**
(§XIII.4.1) and the **Künneth formula** $\pi^{p'}_{1}(X \times_{k} Y) \simeq \pi^{p'}_{1}(X) \times \pi^{p'}_{1}(Y)$
(§XIII.4.6) for $k$ separably closed and $p$ its characteristic.

Throughout this file we quote the SGA 4 / SGA 5 bridge of file 61 §XIII.B. Proofs are sketched in the gentle voice; the
SGA 4 inputs (locally aspherical morphisms, smooth base change, the radicial-base-change reduction VIII 1.1) are named
explicitly at each use.

______________________________________________________________________

## §XIII.3 — Generic local acyclicity

<!-- source: XIII.3 -->

The slogan for §XIII.3 is the **generic** in "generically local acyclic": for $f : X \to Y$ of finite presentation over
an irreducible base $S$ with generic point $s$, one can find a non-empty open $S' \subseteq S$ over which $(F, f)$ is
cohomologically proper *and* $f_{*} F$ is constructible — for every reasonable étale sheaf $F$. The point is that *some*
hypothesis on the base is needed (cohomological properness fails over the generic point of a general base), but a
generic one suffices.

### XIII.3.1 — Theorem (generic cohomological properness for sheaves of sets).

<!-- source: XIII.3.1 -->

Let $S$ be an irreducible scheme with generic point $s$, `X, Y` two $S$-schemes of finite presentation, and
$f : X \to Y$ an $S$-morphism. For every $S$-scheme $S' \to S$ write `Y', X', etc.` for the pullbacks. Then:

(1.a) *Generic dim $\leq 0$ properness, sheaves of sets.* One can find a non-empty open $S' \subseteq S$ such that for
every *finite constant sheaf of sets* $F'$ on $X'$, $f'_{*} F'$ is constructible and `(F', f')` is cohomologically
proper relative to $S'$ in dim $\leq 0$.

(1.b) *Generic dim $\leq 0$ properness, fixed constructible coefficient.* Let $F$ be a constructible sheaf of sets on
$X$. One can find a non-empty open $S' \subseteq S$, depending on $F$, such that $f'_{*} F'$ is constructible and
`(F', f')` is cohomologically proper relative to $S'$ in dim $\leq 0$.

*Proof.* The standard reduction is by Noetherian induction on $Y$ and dévissage on $F$. The two key SGA-4 inputs are:

- [`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic) (SGA 4 XV 1.3, 4.1) — passage to the limit
  along the generic fibre lets us assume $S$ is the spectrum of a noetherian local ring with $s$ the closed point;
- [`sga-4-xvi-base-change-smooth`](appendix-black-boxes.md#sga-4-xvi-base-change-smooth) (SGA 4 XVI 3.2) — smooth base
  change for sheaves pulled back from the base.

The argument is: spread the constructibility of $F$ (B.5) into a stratification of $X$ that is geometrically rigid over
$S'$; on each stratum, $F$ becomes a finite constant sheaf, and the standard cohomologically-proper-of-finite-
constant-coefficients reduction (B.4 applied to the projection from a relative compactification) gives the result after
shrinking $S$ enough.

Slogan: **constructibility + finite-presentation + irreducibility gives cohomological properness on a non-empty open of
the base.**

### XIII.3.1.1 — Generic dim $\leq 1$ properness for $\mathcal{L}$-group coefficients.

<!-- source: XIII.3.1.1 -->

Under the hypotheses of XIII.3.1, fix a set of primes $\mathcal{L}$. There exists a non-empty open $S' \subseteq S$ such
that for every *finite constant sheaf of $\mathcal{L}$-groups* $F'$ on $X'$, `(F', f')` is cohomologically proper
relative to $S'$ in dim $\leq 1$, and both $f'_{*} F'$ and $R^{1} f'_{*} F'$ are constructible.

*Proof.* The sheaf-of-sets case is XIII.3.1; the additional $R^{1}$ clause comes from XIII.1.14 (the cohomologically-
proper-in-dim-$\leq 1$ ⇒ constructible-specialisation criterion). The constructibility of $R^{1}$ for finite
$\mathcal{L}$-group coefficients uses the relative étale cohomology calculation
[`sga-4-constructible-sheaves`](appendix-black-boxes.md#sga-4-constructible-sheaves) (SGA 4 IX 2.3).

### XIII.3.1.2 — Soritic: passage to a subscheme of $Y$.

<!-- source: XIII.3.1.2 -->

If XIII.3.1 (or XIII.3.1.1) holds for $(f : X \to Y, F)$, the analogous statement holds for
$(f|_{X'} : X' \to Y', F|_{X'})$ for every constructible subset $Y'$ of $Y$. (Cf. SGA 4 IX 2.7.4.)

### XIII.3.1.3 — Soritic: composition.

<!-- source: XIII.3.1.3 -->

If XIII.3.1 holds for $f : X \to Y$ and $g : Y \to Z$ separately (with the generic-open shrinking compatible), it holds
for the composite $gf : X \to Z$. (Combine XIII.1.6 with the noetherian-induction step.)

### XIII.3.2 — Field base case: full cohomological properness in dim $\leq 0$.

<!-- source: XIII.3.2 -->

Let $k$ be a field of characteristic $p \geq 0$, $p'$ the set of primes $\neq p$, and $f : X \to \operatorname{Spec}(k)$
a coherent morphism. Then:

(1) For *every* sheaf of sets $F$ on $X$, $(F, f)$ is cohomologically proper relative to $\operatorname{Spec}(k)$ in dim
$\leq 0$.

(2) Suppose moreover one of the following:

(2.a) $f$ is of finite type and the finite-type schemes of dimension $\leq \dim X$ over an algebraic closure of $k$ are
*strongly desingularizable*
([`sga-5-i-strongly-desingularizable`](appendix-black-boxes.md#sga-5-i-strongly-desingularizable)).

(2.b) The finite-type schemes over an algebraic closure of $k$ are strongly desingularizable.

Then for every finite constant sheaf of $p'$-groups $F$ on $X$, $(F, f)$ is cohomologically proper relative to
$\operatorname{Spec}(k)$ in dim $\leq 1$, and $R^{1} f_{*} F$ is constructible.

*Proof of (1).* When the base is a field, every base change $\operatorname{Spec}(k') \to \operatorname{Spec}(k)$ is flat
(vacuously over the point), so the base-change comparison map $\Phi^{0} : k' \otimes_{k} f_{*} F \to f'_{*} (h^{*} F)$
is the usual $H^{0}$-base-change for sheaves of sets — automatic over a field.

*Proof of (2).* The strongly-desingularizable hypothesis gives a resolution $\tilde{X} \to X$ to which we apply
XIII.3.1.1 in its global form (the base $\operatorname{Spec}(k)$ is a single point, so the "generic open" is the whole
base). The proper-smooth case is then handled by B.4 applied to the projection from the resolution.

### XIII.3.3 — Strongly-desingularizable ⇒ universal local 1-asphericity.

<!-- source: XIII.3.3 -->

Let $k$ be a field of characteristic $p \geq 0$, $p'$ the set of primes $\neq p$, and $f : X \to \operatorname{Spec}(k)$
coherent. Under hypothesis (2.a) or (2.b) of XIII.3.2, $f$ is **universally locally `1`-aspherical for $p'$**: for every
base change $X \times_{k} T \to T$ and every torsion $p'$-group constant sheaf $F$, the map $F \to R f_{*} f^{*} F$ is
an iso through degree `1` over every strict localisation of $T$.

*Proof.* The hypothesis gives global cohomological-properness in dim $\leq 1$ (XIII.3.2 (2)); by XIII.1.6 and the limit
form XIII.1.12, the property propagates to every coherent base change. Local 1-asphericity on the strict henselisation
is then the strict-localisation form of cohomological-properness in dim $\leq 1$ (XIII.1.5 e).

### XIII.3.4 — Universally locally 1-aspherical for $p'$.

<!-- source: XIII.3.4 -->

Let $k$, $p'$ be as in XIII.3.3, and $f : X \to \operatorname{Spec}(k)$ coherent. Suppose hypothesis (2.a) or (2.b).
Then $f$ is universally locally 1-aspherical for $p'$.

This is XIII.3.3 in the more usable formulation: it generalises to "the geometric fibres of $f$ are universally locally
1-aspherical for $p'$," used in the Künneth proof XIII.4.6 below.

*Reduction in case (b).* The question is local on $X$; we may suppose $X$ is affine. By passage to the limit
[`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic) (SGA 4 XV 1.3), one is reduced to the case $X$ is
of finite type over $k$. Then case (b) reduces to case (a).

### XIII.3.5 — Specialisation of $\pi^{\mathcal{L}}_{1}$ along generic specialisations.

<!-- source: XIII.3.5 -->

Let $S$ be an irreducible scheme with generic point $s$, $f : X \to S$ of finite presentation. Suppose the finite-type
schemes of dimension $\leq \dim X_{s}$ over an algebraic closure $\bar{k}$ of $\kappa(s)$ are strongly desingularizable.
Let $\mathcal{L}$ be the set of primes not in the residual characteristics of $S$. Then there exists a non-empty open
$S_{1} \subseteq S$ such that for every specialisation $\bar{s}_{1} \to \bar{s}_{2}$ of geometric points of `S_1`, the
specialisation morphism

$$
\pi^{\mathcal{L}}_{1}(X_{\bar{s}_{1}})  \to  \pi^{\mathcal{L}}_{1}(X_{\bar{s}_{2}})
$$

is *bijective*.

*Proof.* By XIII.3.1 + XIII.3.3, after shrinking $S$ to a non-empty open we may assume $f$ is locally 1-aspherical for
$\mathcal{L}$ and that $(F, f)$ is cohomologically proper in dim $\leq 1$ for every finite constant sheaf $F$ of
$\mathcal{L}$-groups on $X$. Then XIII.1.14 gives bijective cospecialisation of $R^{1} f_{*} F$. Translating
cospecialisation of $R^{1} f_{*} F$ into bijectivity of
$\pi^{\mathcal{L}}_{1}(X_{\bar{s}_{1}}) \to \pi^{\mathcal{L}}_{1}(X_{\bar{s}_{2}})$ uses V.6.9 of file 33 and the
description of $\pi^{\mathcal{L}}_{1}$ as the pro-$\mathcal{L}$ Galois category of $X_{\bar{s}}$.

Slogan for XIII.3: **after shrinking the base to a non-empty open, cohomological properness in dim $\leq 1$ for
$\mathcal{L}$-group coefficients holds, and $\pi^{\mathcal{L}}_{1}$ of the geometric fibre is locally constant on the
base.**

______________________________________________________________________

## §XIII.4 — Exact homotopy sequences

<!-- source: XIII.4 -->

We now use the cohomologically-proper machinery of §§XIII.1–3 to produce the **étale homotopy exact sequence**: for a
"good" morphism $f : X \to S$, a geometric point $\bar{s} \to S$ and a geometric point $a \to X_{\bar{s}}$,

```text
π_1^ℒ(X_{s̄}, a)  →  π_1'(X, a)  →  π_1(S, a)  →  1
```

is exact (XIII.4.1, XIII.4.3). The Künneth formula XIII.4.6 follows by combining the homotopy exact sequence with
XIII.3.4.

### XIII.4.0 — The group $\pi_{1}'(X, a)$ and the candidate sequence.

<!-- source: XIII.4.0 -->

Let `X, S` be connected schemes, $f : X \to S$ a morphism, $a$ a geometric point of $X$. Let $\mathcal{L}$ be a set of
primes. Set

```text
K := Ker( π_1(X, a) → π_1(S, a) )
```

(a closed normal pro-subgroup of $\pi_{1}(X, a)$), and let $N \subseteq K$ be the *smallest* closed normal pro-subgroup
such that $K / N$ is a pro-$\mathcal{L}$-group; write $K^{\mathcal{L}} := K / N$ (the maximal pro-$\mathcal{L}$ quotient
of $K$). The subgroup $N$ is closed normal not only in $K$ but in $\pi_{1}(X, a)$ (because conjugation by
$\pi_{1}(X, a)$ preserves both $K$ and the pro-$\mathcal{L}$ property). We define

```text
π_1'(X, a) := π_1(X, a) / N.
```

If $a$ is a geometric point of a geometric fibre $X_{\bar{s}}$, the canonical morphisms

```text
π_1(X_{s̄}, a)  →  π_1(X, a)  →  π_1(S, a)
```

induce morphisms

```text
π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a).
```

Visibly $v \circ u = 0$: the image of $\pi_{1}(X_{\bar{s}})$ in $\pi_{1}(X)$ lies in $K$, and $K / N = K^{\mathcal{L}}$
injects into $\pi_{1}'(X)$, so $u$ factors through the pro-$\mathcal{L}$ quotient of $K$. After passing further to
$\pi_{1}(X) / N = \pi_{1}'(X)$, the composite $\pi^{\mathcal{L}}_{1}(X_{\bar{s}}) \to \pi_{1}'(X) \to \pi_{1}(S)$
annihilates $K^{\mathcal{L}}$ and hence everything in the image of $u$.

### XIII.4.1 — Theorem: exactness of the right two terms.

<!-- source: XIII.4.1 -->

Let $S$ be a connected scheme, $f : X \to S$ a *locally 0-acyclic* morphism (SGA 4 XV 1.11) that is moreover *0-acyclic*
— for coherent $f$, equivalent to "the geometric fibres of $f$ are connected" (SGA 4 XV 1.16). Let $\mathcal{L}$ be a
set of primes. Suppose that for every étale cover $S' \to S$ and every étale cover $E \to X'$ (with
$X' = X \times_{S} S'$) that is a quotient of a Galois cover with $\mathcal{L}$-group, `(E, f')` is cohomologically
proper relative to $S'$ in dim $\leq 0$ and $f'_{*} E$ is constructible.

Then for every geometric point $\bar{s}$ of $S$ and every geometric point $a$ of $X_{\bar{s}}$, the sequence

```text
π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a)  →  1
```

is *exact*.

*Proof.* We have already noted $v u = 0$. We split exactness into surjectivity of $v$ and surjectivity of $u$ onto
$K^{\mathcal{L}} = Ker(v)$.

**Surjectivity of $v$.** Equivalent (V.6.9 of file 33) to: for every connected étale cover $S' \to S$,
$X' = X \times_{S} S'$ is also connected. Let $C$ be any set with $|C| \geq 2$; since $f$ is 0-acyclic, the canonical
map $H^{0}(S', C_{S'}) \to H^{0}(X', C_{X'})$ is bijective; hence the number of connected components of $X'$ equals the
number of connected components of $S'$, which is `1`.

**Surjectivity of $u$ onto $K^{\mathcal{L}}$.** By definition of $K^{\mathcal{L}}$, this is equivalent to: for every
étale cover $S' \to S$ and every Galois cover $Q \to X' = X \times_{S} S'$ with $\mathcal{L}$-group $F$, such that
$P = Q \times_{X'} \tilde{X}$ is connected on the universal cover $\tilde{X} = \tilde{S} \times_{S} X$,
$Q|_{X_{\bar{s}}}$ is *connected*.

By the standard equivalence-of-categories argument we may instead show the contrapositive: if $Q|_{X_{\bar{s}}}$ is
*disconnected*, then *after possibly replacing $S'$ by an étale cover*, $Q$ itself is disconnected. So suppose
$Q|_{X_{\bar{s}}}$ is disconnected. Then there is a subgroup $G \subsetneq F$ and a $(G|_{X_{\bar{s}}})$-torsor $R$ on
$X_{\bar{s}}$ such that $Q|_{X_{\bar{s}}}$ arises from $R$ by extension of structure group $G \to F$. Let $E := Q / G$
(an étale cover of $X'$ with $F / G \neq 1$ as a quotient of its structure group); then $E|_{X_{\bar{s}}}$ *has a
section*.

By the cohomologically-proper hypothesis applied to `(E, f')`, $f'_{*} E$ is a locally constant constructible sheaf on
$S'$. Replacing $S'$ by a further étale cover, we may assume $f'_{*} E$ is *constant*. Cohomological properness in dim
$\leq 0$ says $(f'_{*} E)_{\bar{s}} \simeq H^{0}(X_{\bar{s}}, E|_{X_{\bar{s}}}) \neq \emptyset$ (because
$E|_{X_{\bar{s}}}$ has a section). So $H^{0}(S', f'_{*} E) \neq \emptyset$, which gives a section of $E \to X'$, which
shows $E = Q / G$ admits a section, contradiction — so $Q$ was already disconnected after the étale cover. This proves
surjectivity of $u$.

Slogan: **the cohomologically-proper-coefficients hypothesis is what produces the homotopy exact sequence; under it,
every disconnection of $Q|_{X_{\bar{s}}}$ lifts to a disconnection of $Q|_{X'}$.**

### XIII.4.2 — Coherent corollary.

<!-- source: XIII.4.2 -->

Let $S$ be a connected scheme, $f : X \to S$ a *coherent* morphism that is *locally 0-acyclic* and *0-acyclic*,
$\mathcal{L}$ a set of primes. Suppose that for every finite constant sheaf of $\mathcal{L}$-groups $F$ on $X$, $(F, f)$
is cohomologically proper relative to $S$ in dim $\leq 0$ and $f_{*} F$ is constructible. Then the exact sequence

```text
π_1^ℒ(X_{s̄}, a)  →  π_1'(X, a)  →  π_1(S, a)  →  1
```

of XIII.4.1 holds.

*Proof.* Specialise XIII.4.1 to the coherent + finite-constant-coefficient case. Coherence ensures the geometric- fibre
criterion XIII.1.5 b applies; 0-acyclicity gives the surjectivity of $v$. The remaining cohomologically- proper
hypothesis is the one assumed.

### XIII.4.3 — Exactness of the full four-term sequence.

<!-- source: XIII.4.3 -->

Let $S$ be connected, $f : X \to S$ a 0-acyclic morphism that is *locally 1-aspherical for $\mathcal{L}$*, and let
$g : S \to X$ be a section of $f$. Let $\bar{s}$, $a$ be as in XIII.4.0. Suppose for every constant sheaf of
$\mathcal{L}$-groups $F$, $(F, f)$ is cohomologically proper in dim $\leq 1$, the direct image by $f$ of $Tors(F)$ is
1-constructible, and for every étale cover $E \to X'$ that is a quotient of a Galois $\mathcal{L}$-group cover,
$f'_{*} E$ is constructible. Then

```text
1  →  π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a)  →  1
```

is exact.

*Proof.* The right exactness is XIII.4.2. The new content is injectivity of $u$. By V.6.8 (file 33), $u$ injective is
equivalent to: every principal cover $\bar{Z} \to X_{\bar{s}}$ with $\mathcal{L}$-group $C$ arises (up to connected
component) as the restriction $Z|_{X_{\bar{s}}}$ of some étale cover $Z \to X$.

Let $\bar{z} \in H^{1}(X_{\bar{s}}, C_{X_{\bar{s}}})$ be the class of $\bar{Z}$. By XIII.1.5 d (the geometric-fibre
form),

```text
(R^1 f_* C_X)_{s̄}  ≃  H^1(X_{s̄}, C_{X_{s̄}}).
```

By XIII.1.16, $R^{1} f_{*} C_{X}$ is locally constant constructible on $S$, so it is constant on an étale cover
$S' \to S$. Pulling $\bar{s}$ through to a geometric point $\bar{s} \to S'$, we find
$z \in H^{0}(S', R^{1} f_{*} C_{X})$ mapping to $\bar{z}$. By the sublemma XIII.4.3.1 below, there is a further étale
cover $S'_{1} \to S'$, a torsor $P$ on $X'_{1} = X \times_{S} S'_{1}$ with group $C$, whose image in
$H^{0}(S'_{1}, R^{1} f_{*} C)$ is the pullback of $z$. The torsor $P$ is representable by an étale cover $Z \to X'_{1}$
such that $Z \times_{X'_{1}} X_{\bar{s}} \simeq \bar{Z}$; viewed as an étale cover of $X$ over the cover $X'_{1} \to X$
of $X$, this gives the desired étale cover whose $X_{\bar{s}}$-restriction realises $\bar{z}$.

### XIII.4.3.1 — Sublemma (descent of a torsor class from $R^{1} f_{*}$).

<!-- source: XIII.4.3.1 -->

Let $f : X \to S$ be 0-acyclic and locally 0-acyclic, $g : S \to X$ a section, $C$ a finite constant group with
$(C_{X}, f)$ cohomologically proper in dim $\leq 0$ and $f_{*} Tors(C_{X})$ constructible. Then for every
$z \in H^{0}(S, R^{1} f_{*} C_{X})$, there is an étale cover $S_{1} \to S$ and an element of $H^{1}(X_{1}, C_{X_{1}})$
(where $X_{1} = X \times_{S} S_{1}$) whose image in $H^{0}(S_{1}, R^{1} f_{*} C_{X_{1}})$ is the pullback of $z$.

*Proof.* For $S' \to S$ étale, set $X' = X \times_{S} S'$. Let $G$ be the presheaf

```text
G(S') = { iso classes (P, ι : g'^* P ≃ C_{S'}) : P a C_{X'}-torsor on X' }.
```

$G$ is in fact a sheaf (descent for the torsor + the section-trivialisation), and the forgetful map
$G \to R^{1} f_{*} C_{X}$ is surjective. Let $z \in H^{0}(S, R^{1} f_{*} C_{X})$, $H \subseteq G$ its preimage. It
suffices to show $H$ is locally constant constructible. Locally on $S$ we may assume $z$ is represented by a torsor $P$
on $X$ with $g^{*} P \simeq C_{S}$. The trivialisations of $g^{*} P$ are a torsor under
$\operatorname{Aut}_{C_{S}}(g^{*} P) \simeq C$ (with $C$ viewed as a constant sheaf on $S$), modulo the image of
$f_{*} \operatorname{Aut}_{C_{X}}(P) \to C$. Since $f_{*} \operatorname{Aut}_{C_{X}}(P)$ is locally constant
constructible by XIII.1.16, the quotient $H$ is so too.

### XIII.4.4 — Examples: when the hypotheses are satisfied.

<!-- source: XIII.4.4 -->

The hypotheses of XIII.4.1 are satisfied in two key examples:

(i) $f$ is *proper, flat, of finite presentation, with connected separable geometric fibres*; $\mathcal{L}$ arbitrary.
(Cf. X.1.3 of file 48 for the smooth analogue.)

(ii) $f$ is the projection $X \to S$ of the complement of an NC divisor relative to $S$ in a proper smooth scheme
$Z \to S$ (XIII.2.4 of file 62), $\mathcal{L}$ arbitrary.

The hypotheses of XIII.4.3 are satisfied in case (i) if additionally $f$ is *smooth* and has a section, with
$\mathcal{L}$ = primes not in the residual characteristics of $S$ (B.4 + SGA 4 XVI 5.2).

### XIII.4.5 — Cleaner pro-$\mathcal{L}$ versions of XIII.4.3.

<!-- source: XIII.4.5 -->

Three refinements of XIII.4.3 in the pro-$\mathcal{L}$ regime.

#### XIII.4.5.1 — Pro-$\mathcal{L}$-quotient version.

If the section $g$ of XIII.4.3 is replaced by a section "up to pro-$\mathcal{L}$ ambiguity," the same conclusion holds
for the sequence of pro-$\mathcal{L}$ fundamental groups.

#### XIII.4.5.2 — Smooth-proper case.

If $f$ is smooth proper with connected fibres and a section, with $\mathcal{L}$ = primes not in the residual
characteristics of $S$:

```text
1  →  π_1^ℒ(X_{s̄}, a)  →  π_1^ℒ(X, a)  →  π_1^ℒ(S, a)  →  1
```

is exact.

#### XIII.4.5.3 — Pro-$p'$ version for $S = \operatorname{Spec}(k)$ with $k$ separably closed.

$S$ reduces to a point and $\pi^{\mathcal{L}}_{1}(S) = 1$; the sequence collapses to an iso
$\pi^{\mathcal{L}}_{1}(X_{\bar{s}}) \simeq \pi^{\mathcal{L}}_{1}(X)$. Used in the Künneth proof XIII.4.6 below.

### XIII.4.6 — The Künneth formula for $\pi^{p'}_{1}$.

<!-- source: XIII.4.6 -->

Let $k$ be a separably closed field of characteristic $p \geq 0$, $X$ and $Y$ two connected $k$-schemes, $a$ a geometric
point of $X$, $b$ a geometric point of $Y$, $c$ a geometric point of $X \times_{k} Y$ above $a$ and $b$. Suppose:

(a) $X$ is of finite type over $k$, and the finite-type schemes of dim $\leq \dim X$ over an algebraic closure $\bar{k}$
of $k$ are strongly desingularizable; OR

(b) $X$ is quasi-compact and quasi-separated, and every finite-type scheme over $\bar{k}$ is strongly desingularizable.

Let $p'$ be the set of primes $\neq p$. Then the morphism

```text
π_1^{p'}(X ×_k Y, c)  →  π_1^{p'}(X, a) × π_1^{p'}(Y, b)
```

induced by the two projections is an *isomorphism*.

*Proof.* We may suppose $k$ algebraically closed and $X$ reduced
([`sga-4-viii-1-1-reduction`](appendix-black-boxes.md#sga-4-viii-1-1-reduction); SGA 4 VIII 1.1). Let
$Z = X \times_{k} Y$, $g : X \to k$ and $f : Z \to Y$ the canonical morphisms. By XIII.3.5 / XIII.3.4 the morphism $g$,
and hence $f$, is *universally locally 1-aspherical for $p'$*. Since $X$ is connected, $f$ is 0-acyclic
([`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic); SGA 4 XV 1.16). On the other hand, by XIII.3.2,
for every finite constant $p'$-group $C$ the pair $(C_{X}, g)$ is cohomologically proper relative to $k$ in dim
$\leq 1$; it follows by XIII.1.5 c that $(C_{Z}, f)$ is cohomologically proper relative to $Y$ in dim $\leq 1$, and that
$f_{*} C_{Z}$ and $R^{1} f_{*} C_{Z}$ are constant sheaves on $Y$. So $f$ satisfies all the hypotheses of XIII.4.2.

Thus we have the exact sequence

```text
π_1^{p'}(X_b, c)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)  →  1.
```

The composite

```text
π_1^{p'}(X_b, c)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)
```

is zero (composition factors through $K$); but moreover the canonical morphism
$\pi^{p'}_{1}(X_{b}, c) \to \pi^{p'}_{1}(X, a)$ is an isomorphism (since $X_{b} \simeq X$ as a fibre of the projection
$Z \to Y$). So we have a commutative diagram of exact sequences

```text
π_1^{p'}(X, a)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)  →  1
   ‖                    ↓                    ‖
π_1^{p'}(X, a)  →  π_1^{p'}(X, a) × π_1^{p'}(Y, b)  →  π_1^{p'}(Y, b)  →  1.
```

The bottom row is split exact (a product). The vertical map in the middle is the natural one to the product. Since both
rows are exact and the outer verticals are isos, the middle vertical is an iso. This is the desired Künneth.

Slogan: **the Künneth formula for $\pi^{p'}_{1}$ is the composite of (i) "smooth-and-projection-onto-$Y$ is locally
aspherical" XIII.3.4 and (ii) "the homotopy exact sequence" XIII.4.2, both rendered cleanly by the SGA 4 / SGA 5
bridge.**

### XIII.4.7 — Variants and refinements.

<!-- source: XIII.4.7 -->

Several technical variants used in the proper-smooth-surface application:

#### XIII.4.7 (main) — Homotopy exact sequence with retrocompact open.

Let $S$ be a connected normal scheme, $U \subseteq S$ a dense retrocompact open, $f : X \to S$ proper of finite
presentation with geometrically connected and irreducible fibres at every point of $T := S - U$. Suppose $f$ is
*separable*, *smooth at the points of $f^{-1}(U) \cup g(T)$* (for some section $g : T \to X$), $\mathcal{L}$ = primes
not in the residual characteristics of $S$, and $X$ *regular* at every point of $X_{t}$ for $t \in T$. Then the homotopy
exact sequence of XIII.4.3 holds for $f : X \to S$.

#### XIII.4.7.4 — Proper-smooth-fibration variant.

If additionally the fibres $X_{t}$ for $t \in T$ are proper smooth and $f$ extends to a proper smooth
$\tilde{X} \to \tilde{S}$ over a closure $\tilde{S}$ of $S$, the exact sequence
$1 \to \pi^{\mathcal{L}}_{1}(X_{\bar{s}}) \to \pi^{\mathcal{L}}_{1}(X) \to \pi^{\mathcal{L}}_{1}(S) \to 1$ holds,
*generalising* the standard smooth-proper case to a singular base.

### XIII.4.8 — Topological finite presentation of $\pi^{\mathcal{L}}_{1}(X)$ under $\pi_{1}(S) = 1$.

<!-- source: XIII.4.8 -->

The hypotheses are those of XIII.4.7.4. Suppose moreover $\pi_{1}(S, a) = 1$. Then

```text
π_1^ℒ(X, a)  ≃  π_1^ℒ(X_{s̄}, a)_K,
```

where the subscript $K$ denotes coinvariants under the natural action of $K = Ker(\pi_{1}(X) \to \pi_{1}(S))$ on the
fibre group (restricted to its $\mathcal{L}$-quotient).

In particular: if $\pi^{\mathcal{L}}_{1}(X_{\bar{s}}, a)$ is topologically of finite presentation and $K$ acts through a
group of finite type, then $\pi^{\mathcal{L}}_{1}(X, a)$ is topologically of finite presentation.

*Proof.* The iso $\pi^{\mathcal{L}}_{1}(X, a) \simeq \pi^{\mathcal{L}}_{1}(X_{\bar{s}}, a)_{K}$ is XIII.4.7.4 with
$\pi_{1}(S, a) = 1$. The finite-presentation part: suppose
$\pi^{\mathcal{L}}_{1}(X_{\bar{s}}, a) = L(x_{1}, \cdots, x_{n}) / \langle y_{1}, \cdots, y_{p}\rangle$ (a quotient of
the free pro-$\mathcal{L}$ group on $n$ generators by the closed normal subgroup generated by $p$ elements); suppose $K$
acts through a finite-type group generated by $k_{1}, \cdots, k_{q}$. Let $z_{ij} \in L(x_{1}, \cdots, x_{n})$ lift
$(k_{j} \cdot x_{i}) x^{-1}_{i}$. Then $\pi^{\mathcal{L}}_{1}(X_{\bar{s}}, a)_{K}$ is the quotient of
$L(x_{1}, \cdots, x_{n})$ by the closed normal subgroup generated by $y_{1}, \cdots, y_{p}$ and $z_{ij}$
($1 \leq i \leq n$, $1 \leq j \leq q$), which is finitely many elements.

#### Murre's application to proper smooth surfaces.

XIII.4.8 + a Murre fibration argument (reduce a connected proper smooth surface $X / k$ to a fibration
$X \to \mathbb{P}^{1}_{k}$ over an open $U \subseteq \mathbb{P}^{1}_{k}$ via blow-up, then apply XIII.4.7 + XIII.4.8)
gives:

**Theorem (Murre, after Raynaud).** *For $X$ a proper smooth surface over a separably closed field $k$ of characteristic
$p$, $\pi^{p'}_{1}(X)$ is topologically of finite presentation. More generally, for any connected finite-type $k$-scheme
$X$ such that the finite-type schemes over $\bar{k}$ of dimension $\leq \dim X$ are strongly desingularizable,
$\pi^{p'}_{1}(X)$ is topologically of finite presentation.*

The full Murre / Raynaud argument is in
[`sga-7-fund-group-proper-smooth`](appendix-black-boxes.md#sga-7-fund-group-proper-smooth) (SGA 7).

Slogan for XIII.4.8: **with simply-connected base and strongly-desingularizable fibres, the étale $\pi^{p'}_{1}$ of the
total space is the coinvariants of the geometric-fibre group under the base monodromy — and is therefore topologically
of finite presentation in standard situations.**

______________________________________________________________________

## Closing pointer

File 64 (gentle §XIII.5) develops the Abhyankar variants quoted in file 62 (§XIII.2.4.3) and file 63 (§XIII.4 via the
XIII.2.4 application): the local Kummer cover XIII.5.1, the absolute Abhyankar lemma XIII.5.2, and the relative variants
XIII.5.3–XIII.5.6. After file 64, the gentle SGA project closes; the forward path is SGA 4 (étale cohomology in full),
SGA 4½ + Deligne (Weil conjectures), and SGA 5 (higher cohomologically-proper machinery + trace formula).
