# Exposé IX §§IX.3–IX.4 (gentle): descent of étale morphisms and effectivity criteria

## What this file is about

Covering maps are rigid enough that knowing one over a covering of the base should be enough to recover it over the base
itself. The previous file laid out the étale vocabulary; this file delivers on the promise. When the base is covered in
any reasonable way — by something flat, finite, finite-type, or proper — a covering of the cover descends without
obstruction to a covering of the base. Where the corresponding statement for general geometric objects needed a list of
fine-print conditions, the étale version is essentially free.

One consequence is especially clean. A map that is finite and identifies points without separating their tangent
directions induces no change at all on the world of coverings above. The covering theory cannot tell two such bases
apart — a topological-invariance principle this file makes precise.

## Opening: from prerequisites to the geometric climax

File 44 collected the two technical inputs we need from Exposé I: the **graph theorem IX.1.6** ("$S$-morphisms with
étale target are open subsets of the fibre product with radicial-surjective first projection") and the **saturated-
opens equaliser IX.2.3** ("open subsets of $S$ descend uniquely from saturated open subsets of $S'$ along any submersive
$g$"). An open $U \subseteq X$ is **saturated** relative to a morphism $f : X \to S$ when $U$ is a union of fibres of
$f$ — equivalently, $U = f^{-1}(f(U))$. Combined: an $S$-morphism with étale target is *exactly the data* of an open
subset of $X \times_{S} Y$ that descends along submersive base change. This is the engine of §IX.3.

The present file extracts the consequences. §IX.3 proves that every **universally submersive** $g : S' \to S$ is a
*descent morphism* for the fibred category of étale preschemes — unconditionally, and with no hypothesis on whether the
candidate $X'$ is qf, finite, or finite type. §IX.4 then asks when this descent is *effective*: when does a descent
datum on $X' \to S'$ actually come from an $X \to S$? Five sufficient hypotheses give five effectivity theorems, each
subtler than the last:

- **IX.4.1** — $g$ faithfully flat quasi-compact ⇒ effective for étale separated finite-type schemes.
- **IX.4.7** — $g$ finite surjective of finite presentation ⇒ same.
- **IX.4.9** — $g$ finite-type surjective universally open + $S$ locally noetherian ⇒ same.
- **IX.4.10** — $g$ finite radicial surjective ⇒ **equivalence** of étale categories.
- **IX.4.12** — $g$ proper surjective of finite presentation ⇒ effective for *finite étale* coverings.

The fourth, **IX.4.10**, is the **topological invariance of the étale site**: a universal homeomorphism (finite +
radicial + surjective) induces an equivalence of étale categories. This unpacks the load-bearing black-box row
[`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) that we have been citing since file 06.

## §IX.3 — Descent of morphisms of étale preschemes

<!-- source: IX.3 -->

### IX.3.1 — Injectivity of $f \mapsto f'$ for étale target

<!-- source: IX.3.1 -->

**Proposition IX.3.1.** Let $g : S' \to S$ be a **surjective** morphism of preschemes, let $X$ and $Y$ be two preschemes
over $S$, and let $X'$, $Y'$ be their inverse images over $S'$. If $Y / S$ is **unramified**, then the canonical map

```text
Hom_S(X, Y)  →  Hom_{S′}(X′, Y′),    f ↦ f′ = f ×_S id_{S′},
```

is **injective**.

*This result says:* a morphism with unramified target is *uniquely* determined by its base change to $S'$, provided
$S' \to S$ is surjective.

*Proof.* By IX.1.6 (file 44), an $S$-morphism $f : X \to Y$ with $Y / S$ étale is encoded by its graph $\Gamma_{f}$, an
open subset of $Z = X \times_{S} Y$ whose first projection to $X$ is radicial and surjective. More generally, for
$Y / S$ only *unramified* the same conclusion holds: the graph is a *locally closed* subset of $Z$ with the same
projection properties (file 11 I.5.1; the radicial+surjective characterisation only uses unramifiedness, not étaleness).

Now $Z' = Z \times_{S} S' = X' \times_{S'} Y'$ and the projection $Z' \to Z$ is the base change of $g$, hence
surjective. So the underlying set of $\Gamma_{f} \subset Z$ is *determined* by the underlying set of its pullback
$\Gamma_{f'} = \Gamma_{f} \times_{S} S' \subset Z'$. Two morphisms $f_{1}, f_{2}$ with the same $f_{1}' = f_{2}'$
therefore have $\Gamma_{f_{1}} = \Gamma_{f_{2}}$ as subsets of $Z$, hence by IX.1.6 we conclude $f_{1} = f_{2}$. ∎

### IX.3.2 — The descent diagram for `Hom`s

<!-- source: IX.3.2 -->

**Proposition IX.3.2.** Let $g : S' \to S$ be a **universally submersive** morphism, set $S'' = S' \times_{S} S'$, let
$X$ and $Y$ be $S$-preschemes, let $X'$, $Y'$ be their inverse images over $S'$, and let $X''$, $Y''$ be their inverse
images over $S''$. If $Y / S$ is **étale**, then the canonical diagram of maps

```text
Hom_S(X, Y)  →  Hom_{S′}(X′, Y′)  ⇉  Hom_{S″}(X″, Y″)
```

is an **equaliser**: an $S'$-morphism $f' : X' \to Y'$ is the pullback of an $S$-morphism $f : X \to Y$ iff the two
pullbacks $p^{*}_{1}(f')$ and $p^{*}_{2}(f')$ from $\operatorname{Hom}_{S''}(X'', Y'')$ agree.

*This result says:* **every universally submersive morphism is a descent morphism for the fibred category of étale
preschemes.** Descent data on a single $S'$-morphism with étale target are *automatically effective*.

*Proof.* Injectivity of $\operatorname{Hom}_{S}(X, Y) \to \operatorname{Hom}_{S'}(X', Y')$ is IX.3.1 (using $g$
surjective, which follows from universal submersion).

For the surjectivity onto the equaliser: given $f' : X' \to Y'$ with $p^{*}_{1}(f') = p^{*}_{2}(f')$ in
$\operatorname{Hom}_{S''}(X'', Y'')$, we want an $f : X \to Y$ with $f' = f \times_{S} id_{S'}$. By IX.1.6 applied on
$S'$, $f'$ corresponds to an open subset $\Gamma' \subset Z' = X' \times_{S'} Y'$ with $\Gamma' \to X'$ radicial and
surjective. The equaliser hypothesis says the two pullbacks of $\Gamma'$ to $Z'' = Z' \times_{Z} Z' = Z \times_{S} S''$
(where $Z = X \times_{S} Y$) agree — i.e. $\Gamma'$ is **saturated** for the equivalence relation defined by $Z' \to Z$.

Now $Z' \to Z$ is the base change of $g : S' \to S$ to $Z$, hence universally submersive (base change preserves
universally submersive, IX.2.1). By IX.2.3, the saturated open subsets of $Z'$ correspond bijectively to open subsets of
$Z$. So $\Gamma' = \pi^{-1}(\Gamma)$ for a unique open subset $\Gamma \subset Z$, where $\pi : Z' \to Z$.

It remains to check that $\Gamma \to X$ is radicial and surjective (so that, by IX.1.6 again, $\Gamma$ is the graph of
an $S$-morphism $f : X \to Y$). Radiciality and surjectivity descend along the surjective map $X' \to X$ (this is part
of file 41 VIII.3.1: surjectivity and radiciality descend along universally submersive base change). Hence $\Gamma$ is
the graph of some $f : X \to Y$, and $\Gamma'$ is its pullback, so $f'$ is the pullback of $f$. ∎

> **Slogan.** *Descent of $S$-morphisms with étale target is descent of saturated open subsets along universally
> submersive base change.*

### IX.3.3 — Universally submersive = descent morphism for étale preschemes

<!-- source: IX.3.3 -->

**Corollary IX.3.3.** Let $g : S' \to S$ be universally submersive. Then $g$ is a **morphism of descent** for the fibred
category of étale preschemes over `Sch`.

*Proof.* Specialising IX.3.2 to `X, Y` both étale over $S$, we get the descent equaliser for
$\operatorname{Hom}_{Sch}((X, Y))$ whenever the target is étale. Since the fibred category of étale preschemes is closed
under base change (IX.1.3) and the descent equaliser for morphisms is the defining property of a descent morphism (file
38 VI.12.1), $g$ is a descent morphism. ∎

> **Caveat.** "Descent morphism" is *strictly weaker* than "effective descent morphism." The corollary asserts that
> descent data on étale $S'$-preschemes are *uniquely determined* by $X'$ plus the cocycle — but does **not** assert
> that every such descent datum *comes from* an étale $X / S$. The five theorems of §IX.4 supply the additional
> hypotheses under which effectivity holds. Grothendieck remarks (`IX.3.3` body, file $09-descente-\cdots$, page 233):

> > I do not know, however, whether it is necessarily a morphism of **effective** descent for the fibred category in
> > question, even under the additional hypotheses that $S$ be noetherian and $g$ of finite type, and even restricting
> > to étale coverings.

> Sixty years later this is still open in full generality (cf. Stacks Project tag 0244 for the modern packaging).

### IX.3.4 — Geometrically connected fibres ⇒ fully faithful descent

<!-- source: IX.3.4 -->

**Corollary IX.3.4.** Let $g : S' \to S$ be **universally submersive** with **geometrically connected fibres**, i.e. for
every $s \in S$ and every extension $K / \kappa(s)$, the fibre $g^{-1}(s) \otimes_{\kappa(s)} K$ is connected. Then:

1. If $S$ is connected, then $S'$ is connected.
1. The functor $g^{*}$ from étale $S$-preschemes to étale $S'$-preschemes is **fully faithful**.

*This result says:* under geometric connectedness of fibres, the descent functor $g^{*}$ is *fully faithful* — i.e.
descent data are *automatic* whenever they exist, and $g^{*}$ is an equivalence onto its essential image.

*Proof.* (1) An open-and-closed subset $U \subset S'$ is saturated for the equivalence relation
$Z(g) = S' \times_{S} S' \to S'$ because the fibres of $g$ are connected and $U$ is open-and-closed: each fibre lies
entirely in $U$ or entirely in the complement. Since $g$ is universally submersive, IX.2.3 implies $U = g^{-1}(V)$ for
some $V \subset S$ open. The same argument applied to the complement gives $V$ closed. So $V$ is open-and-closed; if $S$
is connected, $V = \emptyset$ or $V = S$, hence $U = \emptyset$ or $U = S'$, so $S'$ is connected.

(2) Let `X, Y` be étale over $S$, and let $u' : X' \to Y'$ be an $S'$-morphism. By IX.3.3 we need to verify that the two
pullbacks `u_1″, u_2″ : X″ ⇉ Y″` of $u'$ agree on $S'' = S' \times_{S} S'$. The subscheme of $S''$ on which $u_{1}''$
and $u_{2}''$ agree is the inverse image of the diagonal of $Y''$ over $S''$, an open subprescheme of $S''$ whose fibres
are **closed in the fibres of $S'' \to S$** (the fibres of an étale morphism are sums of separable extensions, hence
separated). So this open subscheme is the inverse image of an open of $S$. Since it contains the diagonal
$S' \hookrightarrow S''$, it contains the (connected) fibre of $S' \to S$ over every point of $S$, hence (by the
connected-fibres hypothesis) it contains all of $S''$. Hence $u_{1}'' = u_{2}''$ everywhere. ∎

> **Slogan.** *Geometrically connected fibres of $g$ force the descent equaliser to be automatic; $g^{*}$ is then an
> isomorphism onto its image.*

> **Connection to file 47.** In file 47 we re-read this corollary as the statement that $\pi_{1}(S') \to \pi_{1}(S)$ is
> *surjective* (modulo a base-point matching argument). The π₁ language makes the result transparent: a fully faithful
> pullback functor on étale categories means an *epi* on fundamental groups (file 32 V.6.9).

## §IX.4 — Effectivity criteria

<!-- source: IX.4 -->

The five effectivity criteria. Each follows the same architectural template:

1. State the hypothesis on $g : S' \to S$.
1. Reduce, by IX.4.3 + IX.4.6, to the case where $S$ is the spectrum of a complete noetherian local ring.
1. Reduce further to the special fibre using IX.1.8 / IX.1.10 (file 44).
1. Verify effectivity for the residue-field case directly.

The sorites IX.4.2–IX.4.6 are the bookkeeping that makes the reductions work; the substance is in IX.4.1, IX.4.7,
IX.4.9, IX.4.10, IX.4.12.

### IX.4.1 — Faithfully flat quasi-compact: the strongest general criterion

<!-- source: IX.4.1 -->

**Proposition IX.4.1.** Let $g : S' \to S$ be **faithfully flat and quasi-compact**. Then $g$ is a morphism of
**effective descent** for the fibred category of preschemes **étale, separated, and of finite type** over other
preschemes.

*This result says:* fpqc descent works for the property "étale separated finite-type": every descent datum on such an
$X' / S'$ comes from a *unique* $X / S$ étale, separated, and of finite type.

*Proof.* By IX.3.3 (which uses only that fpqc $g$ is universally submersive by IX.2.2 (b)), $g$ is a descent morphism
for the fibred category of étale preschemes. We need to show that every descent datum on an étale, separated,
finite-type $X' / S'$ is effective.

The descent of "étale separated finite-type" as a property of morphisms follows from IX.1.1 + IX.2.4: étaleness descends
from $X' / S'$ to $X / S$ via the non-noetherian definition, separatedness descends by IX.2.4, and finite type descends
by file 41 VIII.3.3.

It remains to descend the *scheme* $X$ itself. Here we invoke the file 42–43 machinery:

- $X'$ is **quasi-affine** over $S'$. This is a consequence of file 42 VIII.6.2 (quasi-finite separated of finite type
  over noetherian = quasi-affine after reduction) combined with file 42 VIII.6.6 (the noetherian-reduction sorites for
  finite-presentation morphisms over an arbitrary base). The hypothesis "étale of finite type" implies "quasi-finite of
  finite type," and after IX.4.6's reduction to a noetherian local base the conclusion holds.
- *Effective descent of quasi-affine $S'$-preschemes* with descent datum is file 43 VIII.7.9.

Combining the two: $X'$ is a quasi-affine $S'$-prescheme with descent datum, hence by VIII.7.9 descends to a
quasi-affine $S$-prescheme $X$, which is étale separated finite-type over $S$ because the property descends. ∎

> **Slogan.** *Faithfully flat quasi-compact descent of étale separated finite-type schemes is quasi-affine descent plus
> property descent.*

### IX.4.2 — Reduction along refined covers

<!-- source: IX.4.2 -->

**Corollary IX.4.2.** Let $g : S' \to S$ be universally submersive, let $X'$ be an étale, separated, finite-type
$S'$-prescheme with descent datum relative to $g$, and let $S_{1} \to S$ be **faithfully flat and quasi-compact**. Form
$S_{1}' = S' \times_{S} S_{1}$ and $X_{1}' = X' \times_{S'} S_{1}'$. Then the descent datum on $X'$ is effective iff the
corresponding descent datum on $X_{1}'$ (relative to $g_{1} : S_{1}' \to S_{1}$) is effective.

*Proof sketch.* This is one of the standard sorites of descent theory in categories (Giraud,
[`giraud-descent`](appendix-black-boxes.md#giraud-descent)). The descent-data category is preserved under refinement of
covers; if $S_{1} \to S$ is itself an effective descent morphism (which fpqc $S_{1} \to S$ is by IX.4.1), and $S' \to S$
is at least a descent morphism, then effectivity passes through the refinement. ∎

### IX.4.3 — Local-on-base reduction

<!-- source: IX.4.3 -->

**Corollary IX.4.3.** Let $g : S' \to S$ be universally submersive, let $X' \to S'$ be étale with descent datum relative
to $g$, and let $\{S_{i}\}$ be a Zariski open cover of $S$. Then the descent datum on $X'$ is effective iff, for every
$i$, the descent datum on $X_{i}' = X' \times_{S'} (S' \times_{S} S_{i})$ (relative to
$g_{i} : S' \times_{S} S_{i} \to S_{i}$) is effective.

*Proof sketch.* Effectivity is Zariski-local on the base (Giraud). The proof packages the Zariski cover as an fpqc
refinement of $S$ and applies IX.4.2 in reverse. ∎

### IX.4.4 — Local effectivity around a single point

<!-- source: IX.4.4 -->

**Proposition IX.4.4.** Let $g : S' \to S$ be of **finite presentation** and **universally submersive**, let $X' \to S'$
be étale of finite presentation with descent datum, and let $a \in S$. There exists an open neighbourhood $U \ni a$ such
that the descent datum on $X_{U}' = X' \times_{S} U$ (relative to $g_{U} : S' \times_{S} U \to U$) is effective iff the
descent datum on $X_{a}' = X' \times_{S} \operatorname{Spec}(\mathcal{O}_{a})$ (relative to
$g_{a} : S' \times_{S} \operatorname{Spec}(\mathcal{O}_{a}) \to \operatorname{Spec}(\mathcal{O}_{a})$) is effective.

*Proof sketch.* Necessity is trivial. For sufficiency, assume the descent datum on $X_{a}'$ is effective with descended
scheme $X_{a}$ étale of finite type over $\operatorname{Spec}(\mathcal{O}_{a})$. The standard "passage to a limit of
rings" technique ([`ega-iv-limit-of-rings`](appendix-black-boxes.md#ega-iv-limit-of-rings)) extends an étale prescheme
over the filtered colimit `Spec(𝒪_a) = colim_{f ∉ 𝔭_a} Spec(A_f)` to an étale prescheme over some
$\operatorname{Spec}(A_{f}) = U$. After shrinking $U$ if necessary, the isomorphism
$X_{a}' \simeq X_{a} \times_{\operatorname{Spec}(\mathcal{O}_{a})} S_{a}'$ extends to an isomorphism
$X_{U}' \simeq X_{U} \times_{U} S_{U}'$, and after a further shrink it is compatible with the descent data. ∎

### IX.4.5 — Local-on-points reduction

<!-- source: IX.4.5 -->

**Corollary IX.4.5.** Under the conditions of IX.4.4, the descent datum on $X'$ is effective iff, for every $a \in S$,
the corresponding descent datum on $X_{a}'$ (relative to the morphism
$S' \times_{S} \operatorname{Spec}(\mathcal{O}_{a}) \to \operatorname{Spec}(\mathcal{O}_{a})$) is effective. When $S$ is
locally noetherian and $X'$ is separated over $S'$, one may replace $\mathcal{O}_{a}$ by its **completion** in the
preceding criterion.

*Proof sketch.* The first assertion combines IX.4.4 with IX.4.3. The second uses IX.4.2 with
`S_1 = Spec(\hat{𝒪_a}) → Spec(𝒪_a) = S`, which is faithfully flat by
[`completion-flat`](appendix-black-boxes.md#completion-flat). ∎

### IX.4.6 — Reduction to a complete local base with algebraically closed residue field

<!-- source: IX.4.6 -->

**Corollary IX.4.6.** Under the conditions of IX.4.4 with $X' \to S'$ separated and $S$ locally noetherian, the descent
datum on $X'$ is effective iff, for every $S$-scheme `S_1` that is the spectrum of a **complete local ring with
algebraically closed residue field**, the descent datum on $X_{1}' = X' \times_{S} S_{1}$ is effective.

*Proof sketch.* Combine IX.4.5 with IX.4.2 to reduce first to $S_{1} = \operatorname{Spec}(\hat{\mathcal{O}_{a}})$ and
then enlarge the residue field of $\mathcal{O}_{a}$ to its algebraic closure (a faithfully flat base change between
complete local rings; cf. EGA 0_IV §19.8). ∎

### IX.4.7 — Finite surjective: effective descent for separated étale finite-type

<!-- source: IX.4.7 -->

**Theorem IX.4.7.** Let $g : S' \to S$ be a **finite**, **surjective**, **finite-presentation** morphism (the
finite-presentation hypothesis follows from the other two when $S$ is locally noetherian; in fact it suffices that $g$
be **integral** by EGA IV §8). Then $g$ is a morphism of **effective descent** for the fibred category of preschemes
étale, separated, and of finite type over other preschemes.

*This result says:* finite surjective descent is effective for the "étale separated finite-type" fibred category. The
full proof — via noetherian induction on $\dim S$ — is one of the structural arguments of Exposé IX and we reproduce it
in detail.

*Proof.* As in IX.4.1, $g$ is a descent morphism for étale preschemes (IX.3.3 plus the fact that finite surjective
implies universally submersive, IX.2.2 (a)). We must show that every descent datum on étale separated finite-type
$X' / S'$ is effective.

**Step 1: Reduce to $S$ noetherian.** By IX.4.3, effectivity is local on $S$. Cover $S$ by affine opens; each is the
spectrum of a ring. By IX.4.2 and EGA-style passage to noetherian sub-rings
([`ega-iv-constructibility-via-finite-presentation`](appendix-black-boxes.md#ega-iv-constructibility-via-finite-presentation)),
we reduce to the case where $S = \operatorname{Spec}(A)$ is the spectrum of a **noetherian** ring.

**Step 2: Reduce to $S$ the spectrum of a complete local noetherian ring.** By IX.4.5, it suffices to verify effectivity
at each $a \in S$ after passing to $\operatorname{Spec}(\hat{\mathcal{O}_{a}})$. So we may assume
$S = \operatorname{Spec}(A)$ with $A$ a **complete** noetherian local ring; set $n = \dim S = \dim A$.

**Step 3: Noetherian induction on $n = \dim S$.** The base case $n = -\infty$ (i.e. $S = \emptyset$) is vacuous. The
base case $n = 0$ (i.e. $A = k$ a field) holds by **Step 5** below applied to $T = \emptyset$.

Assume $n \geq 1$ and the theorem holds for all complete noetherian local rings of strictly smaller dimension. Set
`T = S - \{s\}` where $s$ is the closed point of $S$. Then $T$ is the complement of a closed point in a noetherian local
scheme; the structural ring $\bigotimes_{s \in T} \mathcal{O}_{S, s}$ has lower dimension. Set $T' = S' \times_{S} T$
and $X_{T}' = X' \times_{S'} T'$. Then $T' \to T$ is finite surjective (inherited from $g$), and $X_{T}' \to T'$ is
étale separated finite-type, with the restricted descent datum.

**Step 4: Decompose $X' = X_{1}' \amalg X_{2}'$.** Since $S = \operatorname{Spec}(A)$ with $A$ complete local, $S'$ is a
finite disjoint union of spectra of complete local rings (the closed-fibre components of $g$). Each connected component
of $S'$ maps to $S$ finitely. Decompose $X'$ according to which closed points of $S'$ it lies over:

```text
X_1′  :=  inverse image in X′ of closed points of S′,    (a finite étale scheme over S′)
X_2′  :=  inverse image in X′ of T′.                       (étale over T′)
```

Then $X' = X_{1}' \amalg X_{2}'$ *as a scheme over $S'$*, because closed points of $S'$ are isolated in $S'$ (each is
the closed point of a connected component) and the étale $X'$ over $S'$ decomposes accordingly.

The descent datum on $X'$ decomposes correspondingly: the cocycle on
$X'' = q^{-1}_{1}(X_{1}') \amalg q^{-1}_{1}(X_{2}')$ matches the cocycle on $X'$. (Verification: the morphism
`q_i : X″ ⇉ X′` factors $q^{-1}_{i}(X_{1}') \amalg q^{-1}_{i}(X_{2}')$ consistently for $i = 1, 2$, by the universal
property of $X_{2}'$ as the inverse image of $T'$.)

**Step 5: Apply the inductive hypothesis to $X_{2}'$ and the residue-field case to $X_{1}'$.**

(a) *Descent of $X_{2}'$.* $X_{2}' \to T' \to T$ is finite surjective of strictly lower dimension. By the inductive
hypothesis, the descent datum on $X_{2}'$ (relative to $T' \to T$) is effective; let $X_{2} / T$ be the descended
scheme. By the local-effectivity criterion IX.4.4, we get an open neighbourhood $U \supset T$ of the open subset
`T = S - \{s\}` such that the descent datum on $X_{2}' \times_{T'} (T' \cap S_{U}')$ is effective. Since $S - U$ is
closed in $S$ and contained in `\{s\}`, $U = S$ or $U = T$. Either way, $X_{2} / T$ extends to an étale separated
finite-type scheme over $S$ (by Zariski gluing if $U = T$).

(b) *Descent of $X_{1}'$.* $X_{1}' \to S'$ is **finite étale** (since "étale + closed in a separated finite-type scheme"
forces finiteness over the residue-field component, by a Krull-dimension argument). Apply IX.1.8 (file 44): the finite
étale $X_{1}'$ is determined by its base change to $S_{0}' = S' \times_{S} \operatorname{Spec}(k)$, where
$k = \kappa(s)$. The descent datum on $X_{1}'$ translates to a descent datum on $X_{1,0}' / S_{0}'$ along the morphism
$g_{0} : S_{0}' \to S_{0} = \operatorname{Spec}(k)$. Since `S_0` is a field, $g_{0}$ is faithfully flat quasi-compact
(everything over a field is flat); by IX.4.1, the descent datum on $X_{1,0}'$ is effective. Lifting back via IX.1.8
gives an effective descent for $X_{1}' / S'$.

Combining (a) and (b): the descent datum on $X' = X_{1}' \amalg X_{2}'$ is effective.

This completes the induction. ∎

> **Inline aside (technical observation).** The proof of IX.4.7 is **elementary** — it does not use the EGA III §5
> existence theorem ([`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence)). The induction base
> ($X_{1}'$ finite étale) reduces to IX.4.1 (fpqc descent), which in turn uses only the file 42–43 quasi-affine-descent
> machinery. The proof of IX.4.12 below will need the existence theorem (specifically IX.1.10's fully-faithful
> direction); this is the technical distinction Grothendieck flags in the original SGA text.

### IX.4.8 — Universally submersive + quasi-finite + finite type, locally noetherian

<!-- source: IX.4.8 -->

**Corollary IX.4.8.** The conclusion of IX.4.7 holds when $g : S' \to S$ is **universally submersive**, **of finite
type**, and **quasi-finite**, with $S$ locally noetherian.

*Proof.* By IX.4.6, we may assume $S = \operatorname{Spec}(A)$ with $A$ a complete noetherian local ring. By IX.2.5
(file 44), there exists a finite surjective $S_{1} \to S$ and an $S$-morphism $S_{1} \to S'$. (Specifically: `S_1` is
the sum of the spectra of the local rings $\mathcal{O}_{S', s'}$ over closed points of the fibre $S'_{s}$; IX.2.5 says
that universally submersive + quasi-finite + finite-type forces this $S_{1} \to S'$ to be surjective.)

Since $S_{1} \to S$ is finite surjective, IX.4.7 says it is an effective descent morphism. By the descent-theory sorites
of Giraud ([`giraud-descent`](appendix-black-boxes.md#giraud-descent)), $g : S' \to S$ is also a strict effective
descent morphism for the fibred category in question (the composite $S_{1} \to S' \to S$ is universally submersive, and
$S_{1} \to S$ is strict effective). ∎

### IX.4.9 — Universally open + finite type + surjective, locally noetherian

<!-- source: IX.4.9 -->

**Corollary IX.4.9.** Let $g : S' \to S$ be **of finite type**, **surjective**, and **universally open**, with $S$
locally noetherian. Then $g$ is a morphism of **effective descent** for étale separated finite-type preschemes.

*Proof.* By IX.4.6, reduce to $S = \operatorname{Spec}(A)$ with $A$ a complete noetherian local ring. We further reduce
to the case where $A$ is **integral**: replace $A$ by $\prod A / \mathfrak{p}_{i}$ over the minimal primes
$\mathfrak{p}_{i}$, observe that effectivity distributes over the product, and verify that the hypotheses on $g$ are
preserved (universal openness, finite type, surjectivity all distribute).

With $A$ integral complete noetherian local, the **integral-dominant-subscheme** result
([`ega-iv-integral-dominant`](appendix-black-boxes.md#ega-iv-integral-dominant)) provides an integral closed subscheme
$S_{1} \subset S'$, of finite type and dominant over $S$, passing through some point of $S'_{s}$. Since $A$ is complete,
dominant \+ finite type + complete-local = **finite**, so $S_{1} \to S$ is finite.

Surjectivity of $S_{1} \to S$: dominance + complete-local + integral target = surjective (because the image is a closed
subset of $S$ containing the generic point of $S$, hence all of $S$ since $S$ is irreducible).

So $S_{1} \to S$ is finite surjective. By IX.4.7 it is an effective descent morphism for the étale-separated-finite-type
fibred category. The composite $S_{1} \to S' \to S$ is also universally submersive (composite of two universally
submersive morphisms is universally submersive). By Giraud's sorites again, $g : S' \to S$ is an effective descent
morphism. ∎

### IX.4.10 — Topological invariance of the étale site

<!-- source: IX.4.10 -->

**Theorem IX.4.10.** Let $g : S' \to S$ be **finite**, **radicial**, **surjective**, and of **finite presentation** (the
last condition is automatic when $S$ is locally noetherian; in fact it suffices that $g$ be **integral**, **radicial**,
and **surjective**, by EGA IV §8). Then the **inverse image functor** $X \mapsto X \times_{S} S'$ induces an
**equivalence** from the category of preschemes **étale over $S$** to the category of preschemes **étale over $S'$**.

*This result says:* **the étale site is invariant under universal homeomorphisms.** Étale topology cannot distinguish
$S$ from $S'$ when $S' \to S$ is a universal homeomorphism (= finite + radicial + surjective).

*Proof.* The diagonal $S' \to S' \times_{S} S'$ is a surjective immersion (file 11 I.5.1 + IX.1.4); hence by IX.1.7
(file 44) the functor $X \mapsto X \times_{S'} (S' \times_{S} S')$ is an *equivalence* from étale $S'$-preschemes to
étale $(S' \times_{S} S')$-preschemes. Iterating, the same holds for the diagonal
$S' \to S' \times_{S} S' \times_{S} S'$.

It follows from Giraud's descent-theory sorites ([`giraud-descent`](appendix-black-boxes.md#giraud-descent)) that
**every** $X'$ étale over $S'$ is endowed with **one and only one** descent datum relative to $g : S' \to S$. (The
descent datum is the cocycle in the equivalence relation; since the cocycle category over $S' \times_{S} S'$ is
*equivalent* to the category over $S'$, every étale $X'$ has a unique cocycle.)

By IX.3.3, the inverse image functor $g^{*}$ from étale $S$-preschemes to étale $S'$-preschemes is **fully faithful**.
It remains to verify **essential surjectivity**: every étale $X' / S'$ is isomorphic to the inverse image of some étale
$X / S$.

The question is local on $S$ *and on $X'$* (since étaleness is a local property and base change preserves it). So we may
assume $S$, $S'$, and $X'$ all **affine**. Then $X'$ is separated and of finite type over $S'$, and IX.4.7 applies: the
descent datum on $X'$ is effective, giving an étale $X / S$ with $X \times_{S} S' \simeq X'$. ∎

> **Slogan.** *Étale topology cannot see Frobenius, nilpotents, or any other universal-homeomorphism phenomenon.*

> **Black-box unpacking.** The black-box row [`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) — cited in
> files 06 and 12 since the rewrite of Exposé I — is exactly IX.4.10. The appendix now points back here.

### IX.4.11 — Faithfully flat quasi-compact + radicial: same conclusion

<!-- source: IX.4.11 -->

**Corollary IX.4.11.** The conclusion of IX.4.10 holds if "finite radicial surjective" is replaced by **"faithfully
flat, quasi-compact, and radicial."**

*Proof.* The proof is identical to IX.4.10, with IX.4.1 used in place of IX.4.7 to drive the effective descent step
(IX.4.1's quasi-affine-descent argument works equally well for fpqc + radicial bases). ∎

### IX.4.12 — Proper surjective: effective for finite étale coverings

<!-- source: IX.4.12 -->

**Theorem IX.4.12.** Let $g : S' \to S$ be **proper**, **surjective**, of **finite presentation** (the last condition
follows from the others if $S$ is locally noetherian). Then $g$ is a morphism of **effective descent** for the fibred
category of **étale coverings** (= finite étale morphisms).

*This result says:* proper surjective $g$ is effective for finite étale, even though it need not be effective for the
larger fibred category of étale-separated-finite-type schemes.

*Proof.* By IX.3.3 (using IX.2.2 (a): proper surjective is universally submersive), $g$ is a descent morphism for the
fibred category of étale coverings. We must show effective descent.

By IX.4.3, reduce to $S$ noetherian. By IX.4.6, reduce to $S$ the spectrum of a complete noetherian local ring $A$,
introduce $S'' = S' \times_{S} S'$ and $S''' = S' \times_{S} S' \times_{S} S'$ as usual. Let $k$ be the residue field of
$A$, $S_{0} = \operatorname{Spec}(k)$, and $S_{0}' = S' \times_{S} S_{0}$ the geometric special fibre of $g$. Set
$S_{0}''$, $S_{0}'''$ analogously.

By IX.1.10 (file 44), the morphisms $S_{0} \to S$, $S_{0}' \to S'$, etc. induce **equivalences** from the category of
étale coverings of the target to the category of étale coverings of the source, *provided* we use only the
**fully-faithful direction** of IX.1.10 (which uses only the Theorem on Formal Functions, not the EGA III §5 existence
theorem). For the essential-surjective direction we *do* use EGA III §5, but only on the **target side**, which can be
circumvented as follows: the equivalence on étale coverings *only requires* the fully-faithful direction for the proof
of IX.4.12 to work, because we are reducing to the descent question at the level of *descent data*, which is preserved
by fully faithful functors.

By the descent-theory sorites (Giraud), $g : S' \to S$ is a strict descent morphism for the fibred category of étale
coverings iff $g_{0} : S_{0}' \to S_{0}$ is so. But $g_{0}$ is a proper surjective morphism over a *field*; so $g_{0}$
is faithfully flat quasi-compact (everything over a field is flat), and IX.4.1 applies. Hence $g_{0}$ is an effective
descent morphism for étale separated finite-type schemes, and a fortiori for étale coverings. ∎

> **Caveat (load-bearing).** The proof uses IX.1.10 (file 44) — but only the **fully-faithful direction**, which
> requires the Theorem on Formal Functions (EGA III §4.3) and not the existence theorem (EGA III §5). The original SGA 1
> IX text records this carefully; the technical point is what lets IX.4.12 *and* IX.4.7 fit in the same chapter despite
> the latter being "elementary" and the former leaning on the proper-coherent machinery.

> **Slogan.** *Proper surjective descent of finite étale coverings reduces to fpqc descent over the residue field via
> the Theorem on Formal Functions.*

## Closing slogan and pointer to file 46

The five effectivity criteria of §IX.4 each give effective descent for a different combination of "how rigid is the
target" (étale separated finite-type vs. finite étale) and "how strong is the base morphism" (faithfully flat
quasi-compact, finite surjective, universally open of finite type, finite radicial surjective, or proper surjective).
The most striking is **IX.4.10**: a finite radicial surjective base change induces an **equivalence** of étale
categories, the **topological invariance of the étale site**.

> **Closing slogan.** *Descent of étale morphisms holds unconditionally; descent of étale schemes is effective in five
> canonical cases; topological invariance is the corner where descent becomes equivalence.*

File 46 turns the descent equivalence into a **calculation** of $\pi_{1}(S, a)$: the descent data on a fibred category
of finite étale coverings is the same as a *galoisian-type group presentation* of $\pi_{1}(S, a)$ in terms of $\pi_{s'}$
for $s'$ in connected components of $S'$. This is the algebraic analogue of Seifert–van Kampen, and the bridge to file
47's fundamental exact sequence.
