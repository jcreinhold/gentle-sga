# Exposé VIII §VIII.7 (gentle): effectivity criteria for a descent datum, and closing

## What this file is about

Suppose we have pieces and gluing instructions for how to assemble them along their overlaps. The instructions look
internally consistent. Even so, the assembly might fail: the pieces are real, the instructions are written down, but
there is no global object on the other side. The instructions describe a phantom. This is not a paranoid concern. The
literature has clean examples of consistent gluing data that simply does not come from anything.

So the natural question is when one can be sure the assembly succeeds. There is no one universal hypothesis that
guarantees it, only a small catalogue of sufficient conditions. This file presents five canonical conditions and shows
why each is enough. Together they cover essentially all the gluing problems that arise in everyday algebraic geometry.

## Opening: which descent data are effective?

File 42 closed with Theorem VIII.5.2: faithfully flat quasi-compact $g : S' \to S$ is a *descent morphism* in `Sch`. The
inverse-image functor

```text
g^*  :  Sch / S  ⟶  (Sch / S′) / g
```

into descent-data preschemes is fully faithful. But — as VIII.5.10 emphasised, and Hironaka's example confirms — it is
*not* in general essentially surjective: not every descent datum on $X'$ over $S'$ comes from a prescheme $X$ over $S$.
When it does come from below, the descent datum is **effective**. The question of §VIII.7 is: when?

The general fact is structural. By the abstract descent machinery `[VIII.D]` (Giraud, _Méthode de la descente_, 1964), a
descent datum on $X'$ relative to $g$ is effective iff the associated *equivalence relation* $R = (q_{1}, q_{2})$ on
$X'$ admits an effective quotient, with $X' \to X' / R$ faithfully flat and quasi-compact. So effectivity reduces to a
question about effective quotients of equivalence relations in `Sch` — and that question has its own well-known
delicacies.

The substance of §VIII.7 is a sequence of *sufficient conditions* under which effectivity is automatic:

- **Open-cover criterion (VIII.7.2):** effectivity is local on the source for descent-stable covers. This is the
  workhorse.
- **Affine criterion (VIII.7.4):** when $S, S'$ are affine, a descent datum is effective iff $X'$ has a cover by
  descent-stable *affine* opens.
- **Radicial criterion (VIII.7.5):** if $g$ is also radicial, every descent datum on every $X'$ is effective.
- **Finite locally free + affine fibres (VIII.7.6):** if $g$ is finite locally free and surjective, the descent datum is
  effective iff every equivalence-relation fibre $R(x')$ lies in an affine open. Automatic for quasi-projective $X'$.
- **Ample invertible sheaf criterion (VIII.7.8):** if $g$ is faithfully flat quasi-compact and $X'$ carries an ample
  invertible sheaf *with a compatible descent datum*, the descent datum on $X'$ is effective.

These are, as Grothendieck remarked, "essentially the only known effectivity criteria" — and were stated as such in the
source. The translator's note adds that this opinion turned out to be slightly too pessimistic (Néron, Raynaud, Murre
extended the catalogue), but for the gentle reading we content ourselves with the canonical five.

The slogan: **descent data on schemes are effective when they restrict to effective descent data on a descent-stable
affine open cover. The five criteria are five sufficient conditions for the cover to exist.**

## §VIII.7 Effectivity criteria

<!-- source: VIII.7 -->

### Setup: descent data as equivalence pairs

<!-- source: VIII.7 preamble -->

We unpack the descent datum on $X' \to S'$ into its equivalence-relation form (file 38 §VI.12 specialised to a
single-cover fpqc site ${S' \to S}$).

Consider a morphism $g : S' \to S$ and an $S'$-prescheme $X'$. By VII §9 (Giraud's general descent formalism), giving a
descent datum on $X'$ relative to $g$ is equivalent to giving an **equivalence pair**

```text
q_1, q_2  :  X″  ⇉  X′
```

(where $X'' = X' \times_{S' \times_{S} S'} X'$, the pull-back of the descent-datum diagram), such that the structural
morphism $X' \to S'$ is compatible with the pair $(q_{1}, q_{2})$ and with

```text
p_1, p_2  :  S″ = S′ ×_S S′  ⇉  S′
```

defined by $g$, and such that the resulting cartesian squares

```text
X′ ←──q_i── X″
│            │
↓            ↓ p_i
S′ ←──p_i── S″
```

(for either $i = 1$ or $i = 2$, both squares are cartesian by symmetry) are indeed cartesian.

A **solution** of the descent problem — i.e. effectivity of the descent datum — is a cartesian square

```text
X  ←─── X′
│        │
↓        ↓
S  ←─── S′
```

satisfying $h q_{1} = h q_{2}$, with $X \to S$ the descended prescheme. So effectivity = existence of an $X \to S$ whose
inverse image along $g$ is $X'$ with the prescribed descent data.

### VIII.7.1 — General effectivity criterion via quotient schemes

<!-- source: VIII.7.1 -->

_This result says: the question of effectivity reduces to the question of when the equivalence relation
$R = (q_{1}, q_{2})$ on $X'$ admits an effective quotient, i.e. when the quotient $X' / R$ exists in `Sch` and
$X' \to X' / R$ is itself faithfully flat quasi-compact._

**Proposition.** Suppose $g : S' \to S$ is faithfully flat and quasi-compact. A descent datum on $X'$ relative to $g$ is
effective iff the equivalence relation $R = (q_{1}, q_{2})$ it defines on $X'$ is *effective* (i.e. the quotient
$X' / R$ exists in `Sch` and $X''$ becomes the fibre square of $X'$ over $X' / R$), and the canonical morphism
$X' \to X' / R$ is faithfully flat and quasi-compact.

**Proof.** Apply the general fact `[VIII.D]`: descent morphisms are stable under base change, and a faithfully flat
quasi-compact morphism is a universal effective epimorphism by VIII.5.3. Effectivity of the descent datum corresponds
exactly to the equivalence relation's effective quotient property. ∎

The remark of the source: this reduces effectivity of descent data to a special case of effectivity of equivalence
graphs in `Sch`. But §VIII.7 actually gets more concrete by using VIII.2.1 (descent of affine preschemes): *if $X'$ is
affine over $S'$, every descent datum is effective*. This is the seed of all the criteria below. The criteria themselves
work by reducing the global descent problem to descent on a descent-stable cover of $X'$ by affine opens.

### Vocabulary: saturated open subsets

A subprescheme (or subobject) $U' \subset X'$ is **stable under the descent datum**, or **saturated**, when the descent
datum on $X'$ restricts to a descent datum on $U'$ compatible with the inclusion $U' \to X'$. Equivalently: the two
inverse images $q^{-1}_{1}(U')$ and $q^{-1}_{2}(U')$ agree as subobjects of $X''$. The restricted descent datum, called
the **induced descent datum**, is then unique.

### VIII.7.2 — Open-cover effectivity criterion (the workhorse)

<!-- source: VIII.7.2 -->

_This result says: effectivity of a descent datum is **local on the source** for descent-stable covers. If $X'$ has an
open cover by descent-stable subsets whose induced descent data are each effective, then so is the descent datum on
$X'$._

**Proposition.** Let $(X_{i}')$ be an open cover of $X'$ by descent-stable opens. The descent datum on $X'$ is effective
iff each induced descent datum on $X_{i}'$ is effective.

**Proof sketch.** Apply VIII.7.1: an effective quotient on each $X_{i}'$ glues to an effective quotient on $X'$ by the
faithfully-flat-descent gluing principle (this is VIII.5.5 + VIII.4.4 in disguise). The details — gluing the
locally-existing $X_{i} = X_{i}' / R_{i}$ and checking the resulting $X$ is faithfully flat quasi-compact — are routine
and left to the reader. ∎

The slogan: **descent is effective iff it is effective on an affine cover stable under the descent datum.**

### VIII.7.3 — Reduction to affine base

<!-- source: VIII.7.3 -->

_This result says: open coverings of the base $S$ reduce the effectivity question to the case where $S$ is affine._

**Corollary.** Let $(S_{i})$ be an open cover of $S$, and let $S_{i}' = g^{-1}(S_{i})$,
$X_{i}' = g^{-1}(S_{i}) \times_{S_{i}'} X'$ be the restrictions. The descent datum on $X'$ is effective iff for every
$i$ the descent datum on $X_{i}'$ relative to $g_{i} : S_{i}' \to S_{i}$ is effective.

**Proof.** Specialisation of VIII.7.2 to the pullbacks $X_{i}' = X' \times_{S'} S_{i}'$, which are descent-stable. ∎

So effectivity is almost always reduced to the case where $S$ is affine. With one more reduction:

### VIII.7.4 — Affine criterion

<!-- source: VIII.7.4 -->

_This result says: when $S$ and $S'$ are both affine, the descent datum is effective iff $X'$ has an open cover by
**affine** descent-stable opens. The "if" direction is the application of VIII.2.1 (affine descent) to each piece; the
"only if" is by tracking through what the descended $X$ looks like locally._

**Corollary.** Suppose $S$ and $S'$ are affine. The descent datum on $X'$ is effective iff $X'$ is a union of affine
descent-stable open subsets.

**Proof.** *Sufficient.* If $X' = \cup X_{i}'$ with each $X_{i}'$ affine and descent-stable, then $X_{i}'$ is affine
over $S'$ (VIII.5.6 applied to the inclusion), so VIII.2.1 says the induced descent datum on $X_{i}'$ is effective. By
VIII.7.2, the descent datum on $X'$ is then effective.

*Necessary.* If $X' \simeq g^{*}(X)$ for some $X$ over $S$ with descent datum the canonical one, take an affine open
cover $(X_{i})$ of $X$. Then $X_{i}' = X_{i} \times_{S} S' = g^{*}(X_{i})$ are affine descent-stable opens covering
$X'$. ∎

### VIII.7.5 — Radicial descent: every descent datum is effective

<!-- source: VIII.7.5 -->

_This result says: when $g : S' \to S$ is faithfully flat quasi-compact **radicial**, every descent datum on every
$X' \to S'$ is effective. This is the only criterion that gives effectivity unconditionally; it covers the case of
quotient maps $S \to S/G$ for $G$ acting freely-and-radicially on a separated scheme._

**Corollary.** Let $g : S' \to S$ be faithfully flat, quasi-compact, and **radicial**. Then $g$ is a morphism of
*effective* descent: every descent datum on every $X'$ over $S'$ is effective.

**Proof.** By VIII.7.3 we may suppose $S$ affine. Since $S' \to S$ is radicial, it is separated, so $S'$ is separated.

We claim every $x' \in X'$ has a *singleton* equivalence-relation fibre

```text
R(x′)  =  q_2\bigl( q_1⁻¹(x′) \bigr)  =  \{ x′ \}.
```

Indeed, radiciality of $g : S' \to S$ is preserved by base change (file 04 §V.4), so the two projections
`p_1, p_2 : S″ ⇉ S′` deduced from $g$ are radicial, and hence so are `q_1, q_2 : X″ ⇉ X′` (which are deduced from
$p_{1}, p_{2}$ by the base change $X' \to S'$). A radicial morphism has fibres consisting of a single point with purely
inseparable residue extension, so each $q^{-1}_{i}(x')$ is a single point, and $q_{2}(q^{-1}_{1}(x')) = \{x'\}$.

Since $R(x')$ is a singleton for every $x'$, *every* open subset $U' \subset X'$ is descent-stable (because
$q^{-1}_{1}(U') = q^{-1}_{2}(U')$ element-wise). In particular every affine open is descent-stable. Cover $X'$ by affine
opens $X_{i}'$; each $X_{i}'$ is affine over $S$ (since $S' \to S$ is separated, an affine open of $S' \to S$-trace is
affine *over* $S$). VIII.2.1 says the induced descent data are effective; VIII.7.2 then concludes. ∎

**Remark.** VIII.7.5 covers a striking set of cases. The Frobenius $\operatorname{Spec} A \to \operatorname{Spec} A$
($a \mapsto a^{p}$) in characteristic $p$ is radicial; so is the quotient
$\operatorname{Spec}(A^{G}) \to \operatorname{Spec} A$ for a finite group $G$ acting *radicially*. The classical case
$\operatorname{Spec}(k') \to \operatorname{Spec}(k)$ for $k' / k$ a purely inseparable finite extension is radicial.
None of these admits any descent obstruction.

Notice (as Grothendieck does) that VIII.7.5 gives **the only known case of an effective descent morphism in `Sch` across
the board** — possibly the only case in general, even restricted to noetherian or finite-type-over-field schemes.
(Subsequent work — Murre, Néron, Raynaud — exhibited other criteria for *particular* classes of $X'$.)

### Vocabulary: norm of a finite locally free morphism

_Inline mini-introduction; cited from \[`ega-ii-norm-finite-locally-free`\](appendix-black-boxes.md#ega-ii-norm-
finite-locally-free)._

For a finite locally free morphism $f : X \to S$ of *constant rank* $r$, multiplication by a local section
$s \in \Gamma(X, \mathcal{O}_{X})$ defines an $\mathcal{O}_{S}$-linear endomorphism of the locally free
$\mathcal{O}_{S}$-module $f_{*}(\mathcal{O}_{X})$ (of rank $r$). Its **determinant** is a section

$$
N_{f}(s)  \in  \Gamma(S, \mathcal{O}_{S}),
$$

the **norm of $s$** along $f$. The norm satisfies:

- *(Base change.)* Compatible with base change $T \to S$: $N_{f_{T}}(s_{T}) = N_{f}(s)|_{T}$.
- *(Multiplicativity.)* $N_{f}(s_{1} s_{2}) = N_{f}(s_{1}) N_{f}(s_{2})$.
- *(Vanishing locus.)* $Z(N_{f}(s)) = f(Z(s))$ as closed subsets of $S$.

The most consequential property for descent: the norm of a section *equalises* the two projections in an equivalence
relation built from finite-locally-free covers, so produces *descent-compatible* invariant sections. We use it once
below in the proof of VIII.7.6.

### VIII.7.6 — Finite locally free effectivity (Weil-Cartier criterion)

<!-- source: VIII.7.6 -->

_This result says: when $g : S' \to S$ is finite locally free surjective, the descent datum on $X' \to S'$ is effective
iff every equivalence-relation fibre $R(x') = q_{2}(q^{-1}_{1}(x'))$ is contained in an affine open of $X'$. The
condition is automatic when $X'$ is quasi-projective over $S'$. This generalises Weil's Galois descent and Cartier's
inseparable descent._

**Corollary.** Let $g : S' \to S$ be a finite locally free surjective morphism — i.e. defined by an
$\mathcal{O}_{S}$-algebra that is a locally free $\mathcal{O}_{S}$-module of finite type. Then $g$ is faithfully flat
and quasi-compact, hence a descent morphism (VIII.5.2). Let $X' \to S'$ be an $S'$-prescheme equipped with a descent
datum.

(i) The descent datum is effective iff for every $x' \in X'$, the fibre $R(x') \subset X'$ is contained in an affine
open subset of $X'$.

(ii) The condition (i) is automatic when $X'$ is quasi-projective over $S'$.

**Proof of (ii).** Let $s \in S$ be the image of $x'$ (which lies in some affine open of $S'$ covering $s$). Then
$R(x')$ is finite (since $q_{1}, q_{2}$ are finite) and contained in the fibre $X_{s}' = X' \times_{S'} \kappa(s')$.
Since $X'$ is quasi-projective over $S'$ and $S'$ is finite over $S$, $X'$ is quasi-projective over $S$; hence each
fibre $X_{s}'$ over $S$ is contained in an affine open of $X'$ (this is the property "quasi-projective over an affine =
affine

- open-immersion-into-projective"). So `R(x′) ⊂ X_s′ ⊂ \text{affine open}`. ∎

**Proof of (i).** *Necessary.* If the descent datum is effective with descended $X \to S$, fix an affine open
$X_{0} \subset X$ containing the image of $R(x')$ (which is a finite subset of $X$); then
$X_{0} \times_{S} S' \subset X'$ is an affine open containing $R(x')$.

*Sufficient.* By VIII.7.3 we may suppose $S$ (and hence $S'$) affine; the hypothesis "every $R(x')$ lies in an affine
open" is preserved by replacing $S$ with an affine cover. By VIII.7.4 it then suffices to show that every $x' \in X'$
has a descent-stable affine open neighbourhood. Let $U \subset X'$ be an affine open containing the finite set $R(x')$.
The **saturation**

```text
\overline U  :=  X′ \ q_2\bigl( q_1⁻¹(X′ \ U) \bigr)
```

is the largest descent-stable subset of $U$ containing $x'$. We need to find a *descent-stable affine* refinement of
$\overline U$ containing $x'$.

Since $q_{2}$ is finite (because $g$, hence $p_{2}$, is finite) and therefore closed, $q_{2}(q^{-1}_{1}(X' \ U))$ is a
closed subset of $X'$. So $\overline U = U_{0} := U \ q_{2}(q^{-1}_{1}(X' \ U))$ is an *open* subset of $U$ containing
$R(x')$ and is descent-stable, but a priori *not* affine.

To refine to an affine descent-stable open. A finite subset $R(x')$ of an affine scheme $U$ has a fundamental system of
affine neighbourhoods of the form $U_{f} = \{ u \in U : f(u) \neq 0 \}$ for some $f \in \Gamma(U, \mathcal{O})$.
Restricting $f$ to $U_{0} \subset U$ gives a section $f \in \Gamma(U_{0}, \mathcal{O})$ with
$(U_{0})_{f} = U_{f} \cap U_{0}$ affine and containing $R(x')$.

Set $U_{0}'' = q^{-1}_{1}(U_{0}) = q^{-1}_{2}(U_{0})$ and let `q_1, q_2 : U_0″ ⇉ U_0` denote the restricted morphisms
(both finite locally free, since $g$ is). Consider

```text
f′  =  \mathrm{Norm}_{q_2}\bigl( q_1^*(f) \bigr)  ∈  Γ(U_0, 𝒪).
```

By base-change compatibility of norms, $q^{*}_{1}(f') = q^{*}_{2}(f')$ (an *invariant section*), which is exactly the
condition for $(U_{0})_{f'}$ to be **descent-stable** in `U_0`. By the vanishing-locus property of norms,

```text
Z(f′)  =  q_2\bigl( Z(q_1^*(f)) \bigr)  =  q_2\bigl( q_1^*(Z(f)) \bigr)  =  R(U_0 \ U_{0, f}),
```

so $(U_{0})_{f'}$ is the saturation of $(U_{0})_{f}$ and contains $R(x')$.

Now $(U_{0})_{f'} \subseteq (U_{0})_{f}$ is open in $(U_{0})_{f}$, and $(U_{0})_{f}$ is affine. Hence $(U_{0})_{f'}$ is
affine (an open of an affine scheme cut out by a single section is affine). So $(U_{0})_{f'}$ is a *descent-stable
affine open* containing $R(x')$, hence $x'$. This proves (i). ∎

**Remarks.** Two notes from the source.

*First.* This argument applies whenever $X'$ carries an equivalence relation (or pre-equivalence relation; see [VIII.3])
that is finite and locally free. The descent statement VIII.7.6 is therefore a *special case* of an analogous result for
finite locally free pre-equivalences. (Loc. cit.)

*Second.* Once the existence of a saturated *quasi-affine* open $U'$ containing $x'$ has been obtained — by the
saturation argument above without the norm step — one can also conclude via VIII.7.9 below (descent of quasi-affine
schemes), which avoids the use of norms. The norm argument is the more elementary route.

### VIII.7.7 — Finite locally free effective descent for quasi-projective $X'$

<!-- source: VIII.7.7 -->

_This result says: when $g : S' \to S$ is finite locally free surjective, descent is effective for quasi-projective
preschemes $X'$. The descended $X$ is quasi-projective over $S$._

**Corollary.** A finite locally free surjective morphism $g : S' \to S$ is a morphism of effective descent for the
fibred category of preschemes quasi-projective over the base. Concretely: for every $X'$ quasi-projective over $S'$ with
descent datum, the descent datum is effective, and the descended $S$-prescheme $X$ is quasi-projective over $S$.

**Proof.** Effectivity follows from VIII.7.6(ii): quasi-projective over $S'$ implies every $R(x')$ lies in an affine
open of $X'$. So the descent datum is effective with descended $X \to S$.

For the conclusion that $X$ is quasi-projective over $S$: the morphism $X' \to X$ is finite locally free surjective (a
base change of $g$). By EGA II 6.6.4, if $X'$ is quasi-projective over $S$ then so is $X$ — and an ample invertible
sheaf on $X$ is obtained as the *norm* of an ample invertible sheaf on $X'$ relative to $S$. ∎

### VIII.7.8 — Ample invertible sheaf effectivity criterion

<!-- source: VIII.7.8 -->

_This result says: descent data are effective whenever they come with an ample invertible sheaf carrying its own descent
datum. This is the cleanest sufficient condition for quasi-projective effectivity in the general fpqc setting (no
finite-locally-free hypothesis needed)._

**Proposition.** Let $g : S' \to S$ be faithfully flat and quasi-compact. Let $X' \to S'$ be quasi-compact and equipped
with a descent datum relative to $g$. Suppose $X'$ carries an invertible sheaf $\mathcal{L}'$ ample relative to $S'$,
*together with a descent datum* relative to the descent datum on $X'$ — i.e. an $\mathcal{O}_{X''}$-linear isomorphism
$q^{*}_{1}(\mathcal{L}') \simeq q^{*}_{2}(\mathcal{L}')$ satisfying the cocycle on $X'''$.

Then the descent datum on $X'$ is effective; the descended invertible sheaf $\mathcal{L}$ on $X$ is ample relative to
$S$.

**Proof.** Analogous to the proof of VIII.5.8 (ampleness descends). Consider the quasi-coherent graded
$\mathcal{O}_{S'}$-algebra

```text
𝓢′  =  \bigoplus_{n ≥ 0}  f′_*\bigl( 𝓛′^{⊗ n} \bigr).
```

The descent datum on $\mathcal{L}'$ induces a descent datum on each $\mathcal{L}'^{\otimes n}$, hence on $\mathcal{S}'$.
By VIII.1.1 (descent of quasi-coherent modules, applied to graded algebras — the structured form of VIII.1.12),
$\mathcal{S}'$ descends to a quasi- coherent graded $\mathcal{O}_{S}$-algebra $\mathcal{S}$ on $S$, with
$g^{*}(\mathcal{S}) = \mathcal{S}'$.

Take $P = \mathrm{Proj}_{S}(\mathcal{S})$ over $S$, with $P' = g^{*}(P) = \mathrm{Proj}_{S'}(\mathcal{S}')$ over $S'$.
By ampleness of $\mathcal{L}'$, $X'$ is an open of $P'$ (the canonical immersion $X' \hookrightarrow P'$ is an open
immersion). This open is descent-stable in $P'$ (the descent datum on $X'$ is the restriction of the canonical descent
datum on $P'$, by construction), so by VIII.7.2 the descent datum on $X'$ is effective. The descended $X$ is the
corresponding open of $P$, hence quasi-projective over $S$. ∎

### VIII.7.9 — Quasi-affine schemes descend; quasi-finite separated effective descent

<!-- source: VIII.7.9 -->

_This result says: every descent datum on a quasi-affine $S'$-prescheme is effective. Combined with VIII.6.2,
quasi-finite separated $X' \to S'$ over locally noetherian $S'$ carries effective descent data._

**Corollary.** Let $g : S' \to S$ be faithfully flat and quasi-compact, and let $X' \to S'$ be quasi-affine. Then every
descent datum on $X'$ relative to $g$ is effective, with the descended $X \to S$ again quasi-affine.

**Proof.** Apply VIII.7.8 with $\mathcal{L}' = \mathcal{O}_{X'}$: when $\mathcal{L}' = \mathcal{O}_{X'}$, the canonical
descent datum on $\mathcal{L}'$ always exists (it is the identity), and ampleness of $\mathcal{O}_{X'}$ is exactly
quasi-affineness of $X' \to S'$ (EGA II 5.1.1). The proposition gives effectivity. ∎

**Special cases.** If $S'$ is locally noetherian and $X' \to S'$ is quasi-finite separated, then $X'$ is quasi-affine
over $S'$ by VIII.6.2 (file 42); hence every descent datum on $X'$ is effective. More generally, when $S'$ is arbitrary
and $X' \to S'$ is of finite presentation, quasi-finite, and separated, the noetherian reduction VIII.6.6 (file 42)
brings us back to the noetherian case, and the same conclusion holds (cf. VIII.6.6).

### VIII.7.10 — Counterexamples (Serre, Hironaka)

<!-- source: VIII.7.10 -->

**Remarks.** The criteria of §VIII.7 essentially exhaust the explicitly known effectivity criteria of the SGA period.
(_Translator's note: this opinion turned out partly erroneous — see Murre's appendix to Bourbaki seminar 294 (May 1965),
and special results of Néron and Raynaud; for descent of group schemes, see Raynaud's 1968 thesis._) The following
counterexamples bound the criteria from below.

*Serre's counterexample.* Take $S = \mathrm{Spec} k$ the spectrum of a field, $S' = \mathrm{Spec} k'$ for a quadratic
Galois extension $k' / k$. There exists $X' \to S'$ *proper and smooth* of dimension 3, equipped with a descent datum
relative to $g : S' \to S$, that is *not* effective. The construction: a 3-dimensional proper smooth `X_0` over $k$ on
which $G = \mathbb{Z}/2\mathbb{Z}$ acts without inertia, with two $k$-rational points `a, b` congruent under $G$ but not
contained in any common affine open. Setting $X' = X_{0} \times_{k} k'$ and letting $G$ act diagonally produces the
descent datum. The points $a', b'$ of $X'$ over `a, b` are congruent under $G$ (the descent-datum equivalence relation),
but cannot lie in a common affine open: an affine open $U'$ containing both would, after descent, give $(a, b)$ an
affine open neighbourhood in `X_0`, which is forbidden. So the descent datum is not effective.

*Hironaka's counterexample.* Take $S = \mathrm{Spec} R$ for a regular local ring of dimension 3 (e.g. the local ring of
an algebraic scheme over a field). Let $T \to S$ be a principal $\mathbb{Z}/2\mathbb{Z}$-covering. Let $t \in T$ be a
point over the closed point $s \in S$, and $S' = T \ \{t\}$. There exists a *projective* $X' \to S'$, regular, equipped
with a descent datum relative to $g : S' \to S$, that is not effective. The construction uses Hironaka's example of a
non- projective proper variety: $X_{0} \to Y$ proper birational over a projective smooth $Y$, with the same
$G = \mathbb{Z}/2\mathbb{Z}$ acting compatibly on `X_0` and $Y$. Set $S' = Y \ f(b)$ and $X' = X_{0}|_{S'}$; the
canonical descent datum on `X_0` relative to $Y \to Y/G$ restricts to one on $X'$, which is non-effective for the same
reason as Serre's example.

Both counterexamples turn on the same obstruction: *not every finite set of points has a common affine open
neighbourhood*. This is the geometric face of "projectivity does not descend automatically" (file 42, VIII.5.10).

The slogan: **effectivity criteria are sufficient conditions for descent-stable affine open covers to exist;
counterexamples are obstructions to such covers, all reducing to the affine-neighbourhood failure for finite point sets
in non-projective varieties.**

## Closing pointer: Exposé IX and the fundamental group

§VIII.7 closes the descent-of-schemes layer of the gentle SGA. With faithfully flat descent of quasi-coherent modules,
affine schemes, properties of morphisms, morphisms in `Sch`, and the effectivity criteria above, every black-box
invocation of [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) in files 30, 31, 33 now refers to a
*developed* theorem in files 40–43 (with the specific statement in each case quoted in the appendix). Files 44–47 then
take the étale-specific layer.

### Exposé IX — descent of étale morphisms (files 44–47)

The geometric specialisation to étale morphisms is **SGA Exposé IX** — _Descente des morphismes étales_. It is developed
in the gentle SGA in files 44–47:

> Universally submersive $g : S' \to S$ is a descent morphism for étale preschemes (IX.3.3, file 45); effective descent
> holds in five sharper hypotheses, including **topological invariance of the étale site** under finite radicial
> surjective base change (IX.4.10, file 45). The descent equivalence then computes the étale fundamental group via a
> **Seifert–van-Kampen formula** (IX.5.1, file 46), and the descent of finite étale coverings along a proper surjective
> morphism with geometrically connected fibres becomes the **fundamental exact sequence**
> $1 \to \pi_{1}(\bar{X}_{0}) \to \pi_{1}(X) \to \pi_{1}(S) \to 1$ (IX.6.1, file 47).

The principal-coverings-descend statement cited via [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) at
file 30 V.2.6, file 31 V.3.6, and file 33 V.7 is the special case **IX.4.7 + IX.4.1** of file 45: a finite étale cover
is a finite locally free morphism (file 12 I.5.1) plus the étale condition (unramified + flat); finite locally free
descend by VIII.5.7; the étale condition descends because flatness and unramifiedness descend separately (the former is
VIII.5.7's "locally free + finite presentation + flat" descent, the latter is descent of the differential
$\Omega^{1}_{X/S} = 0$ condition, which is descent of a quasi-coherent sheaf via VIII.1.1); descent data on the result
is then automatic in the finite étale setting via IX.3.3.

The bridge to file 33 (étale fundamental group):

> The étale fundamental group $\pi_{1}(S, a)$ classifies finite étale covers of $S$ up to descent, and the descent
> machinery of IX.4 makes "up to descent" precise. Seifert–van-Kampen (IX.5.1) computes $\pi_{1}(S, a)$ from the descent
> data; the fundamental exact sequence (IX.6.1) is the special case where the cover is $f : X \to S$ proper surjective
> with geometrically connected fibres.

### Modern parallel accounts

For the reader who wants the modern long-form treatment:

- **Vistoli**, _Notes on Grothendieck topologies, fibered categories and descent theory_ (FGA Explained, AMS 2005; arXiv
  math/0412512). Ch. 4 covers the present material with cleaner categorical language and worked examples. Vistoli §4.3
  spells out exactly what stack each effectivity criterion identifies as a sub-stack of `Sch`.
- **Poonen**, _Rational Points on Varieties_ (AMS 2017), Ch. 4. The shortest pedagogical account, with topological
  motivation (§4.1 develops the sheaf-gluing perspective), the descent equivalence (§4.2), descent for schemes (§4.3
  with Table 1 of properties that descend), and Galois descent (§4.4) — the classical case
  $\operatorname{Spec} k' \to \operatorname{Spec} k$.
- **Bosch–Lütkebohmert–Raynaud**, _Néron Models_ (Springer 1990), Ch. 6. The canonical arithmetic-geometry treatment;
  the closest in spirit to Grothendieck's original proof.
- **Stacks Project**, especially Tags 023A (fpqc descent for fibred categories), 03O2 (QCoh descent), 0247 (descent of
  schemes), 04TQ (descent of morphisms).

### Brief retrospective

The arc through seven exposés (with Exposé IX continued in files 44–47):

- **Exposé I** (étale, file 12 closing). Étale = smooth + relative dimension `0`.
- **Exposé II** (smooth, file 16 closing). Smooth = locally étale over a polynomial scheme.
- **Exposé III** (formally smooth, file 22 closing). Formally smooth = lifting + cohomological vanishing.
- **Exposé IV** (flat, file 27 "Continuing on"). Flat = exactness of `M ⊗_A –`; flat morphisms are open; generic
  flatness is the spread-out theorem.
- **Exposé V** (étale fundamental group, file 33 "Closing the project"). The étale fundamental group $\pi_{1}(S, a)$ is
  the Galois group of the universal finite étale cover.
- **Exposé VI** (fibred categories and descent, file 38). A global functor on a fibred category is determined by its
  fibre-wise restrictions plus a cocycle.
- **Exposé VIII** (faithfully flat descent, _this file_ and files 40–42). Faithfully flat quasi-compact morphisms are
  morphisms of effective `QCoh`-descent, of affine-scheme descent, of `Sch`-descent for morphisms, and (in the five
  canonical cases) for descent of schemes themselves. Combined with noetherian induction, descent proves the
  Zariski-Main-Theorem variants VIII.6.1 and VIII.6.2.

The étale story is self-contained from file 01 through file 43 up to the point where descent of finite étale coverings
is needed; files 44–47 then cover Exposé IX (descent of étale morphisms; topological invariance; Seifert–van-Kampen; the
fundamental exact sequence) and close the gentle SGA loop.

#### Aside (the philosophical takeaway).

_Skip if the philosophical perspective on Grothendieck's program is not part of your current concern._

The technique of Exposé VIII — *descent* — is one of the most powerful tools Grothendieck introduced. It says: when a
geometric object is too big or too singular to construct directly, one can construct it on a *cover* (where the object
becomes simpler), provided one supplies the gluing data (the descent datum) connecting the local pictures. The
faithfully-flat-quasi-compact hypothesis is the universal condition under which descent works for quasi-coherent
modules; for schemes, the same hypothesis works *up to effectivity*, where five canonical criteria suffice in all
classical applications.

The deep observation embedded in §VIII.1.6's "the descended module is the equaliser
$N = \{ x \in N' : \phi(x \otimes 1) = 1 \otimes x \}$" is that descent is *reconstruction by symmetry*: the descended
object is what remains when we discard the part of $N'$ that the descent datum *moves*. This is the algebraic heart of
Grothendieck's idea, and it carries over to every later descent statement — including the étale descent of Exposé IX and
the higher-categorical descent of stacks. The general principle: **descent = equalisers under symmetry actions**.

______________________________________________________________________

This closes Exposé VIII in the gentle reading. The faithfully flat descent of quasi-coherent modules and affine schemes
is unconditional. The descent of morphisms in `Sch` is unconditional. The descent of *schemes themselves* is effective
in five canonical cases (radicial, finite locally free with affine fibres or quasi-projective, ample invertible sheaf
with descent datum, quasi-affine, quasi-finite separated noetherian) and obstructed by Hironaka / Serre counterexamples
otherwise. The étale fundamental group's principal-covering story now rests on developed mathematics.

Exposé IX is continued in files 44–47, where the étale-descent half of the bourbaki-sem-190 black box is unpacked.
Beyond Exposé IX, the work of Murre, Néron, Raynaud, and the later flow toward Grothendieck's stacks-and-six-functors
machinery remains a thread for a future pass.
