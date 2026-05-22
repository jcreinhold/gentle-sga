# Exposé VIII §§VIII.2–4 (gentle): affine descent, properties of morphisms, topology

## What this file is about

A geometric object often has a base — a space of parameters it sits over — and a covering by simpler pieces. Two quite
different questions can be asked. Local-on-the-base asks whether a property holds when checked on every piece of the
base. Local-on-the-source asks whether a property holds when checked after pulling everything back to a covering. For
honest geometry these should agree, but they need not, and a careful translation between the two is the price of working
with general bases.

This file develops the translation for the simplest enrichments of the previous file's gluing theorem — algebras instead
of modules, with consequences for how maps between objects behave: surjectivity, finiteness, openness, separation,
properness.

## Opening: from modules to schemes and their properties

File 40 proved Theorem VIII.1.1 in full. Once the descent of quasi-coherent modules is in hand, three families of
geometric descent statements unfold by direct specialisation.

- **§VIII.2.** A quasi-coherent algebra is a quasi-coherent module with an extra structure (commutative multiplication
  with unit) that is preserved by inverse image. By VIII.1.12, the *fibred subcategory* of quasi-coherent algebras
  inherits effective descent along faithfully flat quasi-compact morphisms. Geometrically, this is descent of affine
  morphisms, via the equivalence between quasi-coherent $\mathcal{O}_{S}$-algebras and affine $S$-preschemes.
- **§VIII.3.** Properties of morphisms that one can read off from fibres or from finite-type generators — surjectivity,
  radiciality, quasi-compactness, finite type, quasi-finiteness — descend through faithfully flat quasi-compact base
  change by short colimit arguments.
- **§VIII.4.** Topological properties: closure, openness, separation, properness. The conceptual core is the formula
  $g^{-1}(closure Z) = closure(g^{-1} Z)$ for flat $g$ and $Z$ quasi-compact-image, which lifts to the statement that
  $S$ is the *quotient* of $S'$ by $R(g) = q_{1}(q^{-1}_{2}(\cdot))$. Once $Y$ is a quotient topological space of $Y'$,
  open/closed/locally closed sets, open maps, closed maps, homeomorphisms, separated and proper morphisms all descend.

We are still doing module-and-algebra-flavoured bookkeeping. Section §VIII.5 (file 42) is where the algebraic machinery
meets the geometric machinery in earnest, and §VIII.6 (file 42) is where descent + noetherian induction together prove
Grothendieck's algebraic Zariski Main Theorem variants. The present file is the bridge.

## §VIII.2 Descent of affine preschemes

<!-- source: VIII.2 -->

### Vocabulary: affine morphisms

_Inline mini-introduction; cited from [`ega-ii-affine-morphisms`](appendix-black-boxes.md#ega-ii-affine-morphisms)._

An $S$-prescheme $f : X \to S$ is **affine** when $f^{-1}(U)$ is an affine scheme for every affine open $U \subset S$.
The basic fact (EGA II §1.4) is that the assignment

```text
{ quasi-coherent 𝒪_S-algebras 𝒜 }  ⟶  { affine S-preschemes X → S },
𝒜  ↦  Spec_S(𝒜),
```

is an **anti-equivalence of categories**, where $\operatorname{Spec}_{S}(\mathcal{A})$ denotes the relative spectrum.
Under it, tensor operations on the algebra side correspond to fibre products and base change on the prescheme side: if
$g : T \to S$ is any morphism,
$g^{*}(\operatorname{Spec}_{S}(\mathcal{A})) = \operatorname{Spec}_{T}(g^{*}(\mathcal{A}))$. So affine morphisms
$X \to S$ are, up to direction, the same data as quasi-coherent algebras on $S$.

This is the structural fact that makes Theorem VIII.2.1 follow from Theorem VIII.1.1 with only one extra verification —
that descent data on quasi-coherent algebras respect the algebra structure.

### VIII.2.1 — Faithfully flat descent of affine preschemes

<!-- source: VIII.2.1 -->

_This result says: faithfully flat quasi-compact morphisms are morphisms of effective descent for affine schemes.
Specialising VIII.1.1 to the fibred subcategory of quasi-coherent algebras — whose anti-equivalent geometric face is
affine morphisms — gives this as an immediate corollary._

**Theorem.** Let $\mathcal{F}'$ be the fibred category of affine morphisms $f : X \to S$ over the base `Sch`, viewed as
a fibred subcategory of the arrow fibration $Ar(Sch) \to Sch$ (file 35, file 38). Let $g : S' \to S$ be a faithfully
flat quasi-compact morphism. Then $g$ is a morphism of effective $\mathcal{F}'$-descent.

**Proof.** The inverse-image functor of modules is compatible with the tensor product, hence with all tensor operations
defining algebraic structures (associative multiplication, commutativity, unit). Apply VIII.1.1 to the quasi-coherent
$\mathcal{O}_{S'}$-algebra $\mathcal{O}_{X'}$ of the affine $S'$-prescheme $X' \to S'$ carrying descent data: the
descent datum on $\mathcal{O}_{X'}$ as a module is automatically an *algebra* descent datum, since the multiplication
map is itself the inverse image of the multiplication map on the candidate descended algebra. The descended
quasi-coherent algebra $\mathcal{A}$ on $S$ then has $\operatorname{Spec}_{S}(\mathcal{A})$ as the descended affine
$S$-prescheme. The geometric face of VIII.1.2 (descent of algebra maps) gives full faithfulness; VIII.1.3 gives
essential surjectivity. ∎

The slogan: **descent of affines = descent of their quasi-coherent algebras.**

A useful refinement: the *structured* form of VIII.2.1 also covers pairings, multilinear maps, and other tensor-
flavoured data on quasi-coherent modules. If $F$, $G$, $H$ are quasi-coherent modules on $S'$ with descent data
compatible with a pairing $F \otimes G \to H$, the descended modules carry a compatible pairing — and conversely. This
is the content of VIII.2.1's preamble in the source. Applied to $F = G = H = \mathcal{A}'$ it gives algebra descent;
applied to a pairing $\mathcal{L} \otimes \mathcal{L} \to \mathcal{O}$ it gives descent of invertible sheaves with their
line-bundle structure; and so on. We use the phrase "descent of a *structured* quasi-coherent module" for any of these
variants.

#### Aside (representability analogy).

_Skip if the notion of an affine morphism as a relative Spec is already settled._

If you think of affine morphisms as "relative Spec", the statement VIII.2.1 reads: descent for the functor
`S ↦ { \text{quasi-coherent } 𝒪_S\text{-algebras} }` is the same as descent for the (anti-equivalent) functor
`S ↦ { \text{affine } S\text{-preschemes} }`. The descent property is the same data viewed through different
presentations. This is the simplest case of "descent is *representable*": the descent property of one fibred category is
inherited by any *equivalent* fibred category.

## §VIII.3 Descent of set-theoretic and finiteness properties of morphisms

<!-- source: VIII.3 -->

This section is technically the easiest of Exposé VIII: short propositions and short proofs. Conceptually it is also the
most general, because the *only* hypotheses used are: (a) $g : S' \to S$ is surjective (sometimes radicial, sometimes
faithfully flat), and (b) $g$ is quasi-compact (for the finite-type statement).

We adopt the standing notation: $f : X \to Y$ is an $S$-morphism, $g : S' \to S$ a base-change morphism, and
$f' : X' \to Y'$ the morphism $X \times_{S} S' \to Y \times_{S} S'$ deduced from $f$ by base change. The diagram

```text
X′ ──f′──> Y′
│           │
↓           ↓
X  ──f───> Y
```

is cartesian on both squares.

### VIII.3.1 — Surjectivity and radiciality descend under surjective base change

<!-- source: VIII.3.1 -->

_This result says: surjectivity and radiciality of $f$ are detected by $f'$, provided $g$ is surjective. No flatness or
quasi-compactness needed._

**Proposition.** Let $f : X \to Y$ be an $S$-morphism, let $g : S' \to S$ be surjective, and let $f' : X' \to Y'$ be the
base change. Then $f$ is surjective (respectively radicial) iff $f'$ is.

**Proof.** The base change $Y' \to Y$ is surjective since it is the pull-back of the surjective $g : S' \to S$. For
$y \in Y$ and $y' \in Y'$ lying over $y$, the fibre comparison is

```text
X′_{y′}  ≃  X_y ⊗_{κ(y)} κ(y′).
```

The fibre $X_{y}$ is nonempty iff $X'_{y'}$ is nonempty (because `κ(y′) ⊗_{κ(y)} (–)` reflects nonemptiness —
$\kappa(y')$ is a nonzero field extension of $\kappa(y)$). The fibre $X_{y}$ has at most one point and that point's
residue extension is radicial iff $X'_{y'}$ has the same property (a base change of a radicial morphism by a field
extension stays radicial, and the converse follows from the same fibre formula). ∎

### VIII.3.2 — Injectivity and bijectivity ascend

<!-- source: VIII.3.2 -->

**Corollary.** Under the conditions of VIII.3.1, if $f'$ is injective (respectively bijective), then $f$ is.

**Proof.** If $X'_{y'}$ has at most one point, the same holds for $X_{y}$, since $X'_{y'} \to X_{y}$ is surjective
(being deduced from the surjective $\operatorname{Spec}(\kappa(y')) \to \operatorname{Spec}(\kappa(y))$). ∎

### VIII.3.3 — Quasi-compactness and finite type descend

<!-- source: VIII.3.3 -->

_This result says: under surjective quasi-compact (resp. faithfully flat quasi-compact) base change, the property "$f$
is quasi-compact" (resp. "of finite type") descends._

**Proposition.** With the notation of VIII.3.1, suppose $g : S' \to S$ is surjective and quasi-compact (resp. faithfully
flat and quasi-compact). Then $f$ is quasi-compact (resp. of finite type) iff $f'$ is.

**Proof.** Only "if" needs proof. We may replace $f : X \to Y$ by its analogue with $Y = S$ (the conditions on $g$
transfer to $Y' \to Y$); we may further reduce to $Y$ affine, in which case $Y'$ is quasi-compact.

*Quasi-compactness.* By hypothesis $f'$ is quasi-compact, so $X'$ is quasi-compact. Cover $X$ by affine opens
$(X_{i})_{i \in I}$. Their inverse images $X'_{i}$ cover $X'$; by quasi-compactness of $X'$ a finite subfamily already
covers $X'$. Since $X' \to X$ is surjective, the corresponding finite subfamily of $(X_{i})$ covers $X$. Hence $X$ is
quasi-compact.

*Finite type.* Reduce further to $Y'$ affine (replace by a sum of affine opens). With $Y, Y'$ affine and $X$
quasi-compact, cover $X$ by finitely many affine opens $X_{i}$. Showing each $X_{i} \to Y$ is of finite type is then the
content of the algebraic corollary VIII.3.4 below. ∎

### VIII.3.4 — Algebraic version: finite-type descends along faithful flatness

<!-- source: VIII.3.4 -->

**Corollary.** Let $B$ be an $A$-algebra, $A'$ a faithfully flat $A$-algebra, and $B' = B \otimes_{A} A'$. Then $B$ is
of finite type over $A$ iff $B'$ is of finite type over $A'$.

**Proof.** "If" only. Write $B = colim_{i} B_{i}$ over the finite-type $A$-subalgebras $B_{i} \subset B$. Filtered
colimits commute with $\otimes$, so $B' = colim_{i} B_{i}'$. If $B'$ is of finite type, the identity $B' \to B'$ factors
through some $B_{i}'$. So $B_{i}' \to B'$ is surjective; by faithful flatness, $B_{i} \to B$ is surjective, hence
$B_{i} = B$. ∎

### VIII.3.5 — Quasi-finiteness descends

<!-- source: VIII.3.5 -->

**Corollary.** With $g : S' \to S$ faithfully flat and quasi-compact, $f$ is quasi-finite iff $f'$ is.

**Proof.** Quasi-finite means: of finite type, and with finite fibres. Finite type descends by VIII.3.3; the finite-
fibre condition descends by the fibre argument of VIII.3.1 (which only used surjectivity). ∎

### VIII.3.6 — Remark: finite presentation

<!-- source: VIII.3.6 -->

**Remark.** A morphism $f : X \to Y$ is of **finite presentation** when, locally on $Y$, $X$ is the pull-back via
$Y \to Y_{0}$ of a finite-type $Y_{0}$-scheme with $Y_{0}$ *noetherian*. (Equivalent local condition: locally, $X$ is
given by a polynomial algebra modulo a finite-type ideal.) Finite presentation is preserved under base change and
composition. The statements VIII.1.10 and VIII.3.3 remain valid when "of finite type" is replaced by "of finite
presentation"; the proof proceeds in the same way using finite-type subalgebras and the noetherian reduction
\[`ega-iv-constructibility-via-finite-presentation`\](appendix-black-boxes.md#ega-iv-constructibility-via-finite-
presentation).

The slogan: **set-theoretic and finite-type-flavoured properties descend along (faithful) flat quasi-compact covers.**

## §VIII.4 Descent of topological properties

<!-- source: VIII.4 -->

The topological half of Exposé VIII rests on a single key theorem (VIII.4.1) about how a flat morphism interacts with
closure, plus its faithful-flatness amplification (VIII.4.3) which says that a faithfully flat quasi-compact morphism
realises $Y$ as a *quotient topological space* of $Y'$. Once this is in hand, every named topological condition on a
morphism descends.

### VIII.4.1 — Flat morphisms preserve closures of quasi-compact images

<!-- source: VIII.4.1 -->

_This result says: for a flat $g : Y' \to Y$ and a subset $Z \subset Y$ that is the image of a quasi-compact morphism,
the flat pull-back commutes with closure: $g^{-1}(cl Z) = cl(g^{-1} Z)$. This is the **one** place in Exposé VIII where
mere flatness — not faithful flatness — does the substantive work._

**Theorem.** Let $g : Y' \to Y$ be a flat morphism. Let $Z \subset Y$ be a subset such that $Z = f(X)$ for some
quasi-compact morphism $f : X \to Y$. (If $Y$ is noetherian, "$Z$ is constructible" suffices.) Then

$$
g^{-1}(closure(Z))  =  closure(g^{-1}(Z)).
$$

**Proof.** Reduce to $Y$ affine, then $Y'$ affine. Since $f$ is quasi-compact and $Y$ is affine, $X$ is a finite union
of affine opens $X_{i}$. Replace $X$ by the disjoint sum of the $X_{i}$ and assume $X$ itself is affine.

Now let $A, A', B$ be the rings of $Y, Y', X$ with $B' = B \otimes_{A} A'$ the ring of $X' = X \times_{Y} Y'$. Set

```text
I  =  ker(A → B),    I′  =  ker(A′ → B′).
```

The closure of $Z = f(X)$ in $Y$ is the closed subset $V(I) \subset Y$ (the radical of $I$ cuts out $Im(f)$'s closure as
a set), and similarly $cl(g^{-1}(Z)) = V(I')$ in $Y'$. The pre-image $g^{-1}(V(I)) = V(IA')$. So the claim reduces to:

$$
I'  =  IA'.
$$

This is the *flatness* of $A' / A$: the sequence $0 \to I \to A \to B \to 0$ is exact, and tensoring with $A'$ preserves
exactness, giving $0 \to I \otimes_{A} A' \to A' \to B' \to 0$ exact. The kernel of $A' \to B'$ is
$I \otimes_{A} A' = IA'$, hence $I' = IA'$. ∎

The slogan: **flat base change commutes with closure of quasi-compact-image subsets, and this is the only place flat
(not faithfully flat) is used.**

### VIII.4.2 — Saturated closed subsets

<!-- source: VIII.4.2 -->

_This result says: a closed subset of $Y'$ saturated by the equivalence relation of $g$ is the pre-image of its
image-closure in $Y$. The topology on $g(Y')$ induced by $Y$ is the quotient topology of $Y'$._

**Corollary.** Let $g : Y' \to Y$ be flat and quasi-compact. Let $Z' \subset Y'$ be a closed subset saturated for the
set- theoretic equivalence relation defined by $g$ (i.e. $Z' = g^{-1}(g(Z'))$). Then

$$
Z'  =  g^{-1}(closure(g(Z'))).
$$

**Proof.** Write $Z = g(Z')$. Then $Z' = g^{-1}(Z)$. Apply VIII.4.1 to $Z$: it has a quasi-compact-image presentation
given by $Z'$ itself, endowed with the reduced induced structure ($g$ quasi-compact ⇒ the restricted morphism is
quasi-compact). Hence $g^{-1}(cl Z) = cl(g^{-1} Z) = cl(Z') = Z'$ (the last equality because $Z'$ is closed). ∎

The slogan in the source: **the topology on $g(Y')$ induced by $Y$ is the quotient of the topology of $Y'$.**

### VIII.4.3 — Faithfully flat quasi-compact morphisms give the quotient topology

<!-- source: VIII.4.3 -->

_This result says: when $g$ is *faithfully* flat and quasi-compact (so also surjective), $Y$ is a quotient topological
space of $Y'$: a subset of $Y$ is open / closed iff its pre-image in $Y'$ is._

**Corollary.** Let $g : Y' \to Y$ be a faithfully flat quasi-compact morphism. Then $g$ makes $Y$ a quotient topological
space of $Y'$: for any subset $Z \subset Y$, $Z$ is closed (resp. open) iff $Z' = g^{-1}(Z)$ is.

**Proof.** Surjectivity of $g$ already gives $Z = g(Z')$ for $Z' = g^{-1}(Z)$. If $Z'$ is closed (resp. open) in $Y'$,
then $Z' = g^{-1}(g(Z')) = g^{-1}(Z)$ is saturated and closed (resp. open); by VIII.4.2 applied to closed (or to
complements), $Z = g(Z')$ is closed (resp. open) in $Y$. ∎

The slogan: **$g$ faithfully flat quasi-compact ⟹ $Y = Y' / R(g)$ as topological spaces.**

### VIII.4.4 — Descent of open and closed subsets

<!-- source: VIII.4.4 -->

_This result says: for the standard fibred categories of open / closed subsets, $g$ is a morphism of effective descent.
Two elements of $Y'$ agree in $Y$ iff they fit a triangle through $Y''$, so descent data on subsets are sieves
saturating across $Y''$._

**Corollary.** For $g : Y' \to Y$ as in VIII.4.3 and for every prescheme $X$, write $Open(X)$ for its set of open
subsets and $Closed(X)$ for its set of closed subsets. Then the diagrams of set-maps

```text
Open(Y)   ⟶  Open(Y′)   ⇉  Open(Y″),
Closed(Y) ⟶  Closed(Y′) ⇉  Closed(Y″)
```

are exact (i.e. each map identifies its source with the equaliser of the two parallel maps to its right).

**Proof.** Two points $a, b \in Y'$ have the same image in $Y$ iff they are the two components $p_{1}(c), p_{2}(c)$ of
some $c \in Y'' = Y' \times_{Y} Y'$ (this is the standard "same fibre ⇔ in the relation" characterisation of the
topological quotient). Combined with VIII.4.3, this gives the equaliser description. ∎

### VIII.4.5 — Locally closed subsets

<!-- source: VIII.4.5 -->

_This result says: locally closed subsets (intersections of open and closed) descend under the same hypothesis._

**Corollary.** Let $g : Y' \to Y$ be faithfully flat and quasi-compact, and let $Z \subset Y$ satisfy the
quasi-compact-image condition of VIII.4.1 (for instance: $Z$ constructible and $Y$ noetherian). Then $Z$ is locally
closed in $Y$ iff $Z' = g^{-1}(Z)$ is locally closed in $Y'$.

**Proof.** "If" direction. Let `Y_1` be the closed subprescheme of $Y$ with underlying set $cl(Z)$ (with the reduced
induced structure), and let $Y_{1}' = Y_{1} \times_{Y} Y'$ be its pullback in $Y'$. The set of $Y_{1}'$ is
$g^{-1}(cl(Z))$, which by VIII.4.1 equals $cl(g^{-1}(Z)) = cl(Z')$. Since $Z'$ is locally closed in $Y'$, it is open in
its closure $cl(Z') = Y_{1}'$. But $Y_{1}' \to Y_{1}$ is faithfully flat and quasi-compact (inherited from $g$), so by
VIII.4.3 the open subset $Z$ of `Y_1`-with-pre-image-$Z'$ is open in `Y_1`, hence in $cl(Z)$. So $Z$ is locally closed.
∎

### VIII.4.6 — Descent of open and closed maps; of homeomorphisms

<!-- source: VIII.4.6 -->

_This result says: open maps, closed maps, homeomorphisms-into-image, and homeomorphisms descend along faithfully flat
quasi-compact base change._

**Corollary.** Let $g : S' \to S$ be faithfully flat and quasi-compact; let $f : X \to Y$ be an $S$-morphism; let
$f' : X' \to Y'$ be the base change. Suppose $f'$ is an open map (resp. closed map; resp. quasi-compact homeomorphism
into its image; resp. homeomorphism onto). Then $f$ has the same property.

**Proof.** Replace $Y$ by $S$ (since $Y' \to Y$ is itself faithfully flat quasi-compact). Let $h : X' \to X$ be the
projection. For $Q \subset X$,

$$
g^{-1}(f(Q))  =  f'(h^{-1}(Q)).
$$

If $Q$ is open (resp. closed), then $h^{-1}(Q)$ is, so $f'(h^{-1}(Q))$ is by the assumed openness (resp. closedness) of
$f'$. By VIII.4.3, $f(Q)$ is therefore open (resp. closed) in $Y$. This proves the open / closed cases.

For homeomorphism-into-image: $f$ is injective by VIII.3.2, quasi-compact by VIII.3.3. It remains to show $f$ is open
onto its image, i.e. for every closed $Z \subset X$, $Z = f^{-1}(cl(f Z))$. Since $h$ is surjective, this is equivalent
(after pullback to $X'$) to the formula $Z' = f'^{-1}(cl(f' Z'))$ where $Z' = h^{-1}(Z)$; by VIII.4.1 applied to
$f(Z) \subset Y$ we have $g^{-1}(cl(f Z)) = cl(g^{-1}(f Z))$, and the pullback formula reduces to the hypothesis that
$f'$ is a homeomorphism into its image.

The case "homeomorphism onto" follows from "homeomorphism into image" + surjectivity (VIII.3.1).

_N.B._ The proof of the open / closed cases used quasi-compactness of $g$ only via VIII.4.3. For the homeomorphism-
into-image case the proof only needed $g$ faithfully flat (not quasi-compact); cf. the source remark inside VIII.4.6. ∎

### VIII.4.7 — Universal versions

<!-- source: VIII.4.7 -->

**Corollary.** Under the conditions of VIII.4.6, $f$ is universally open (resp. universally closed, resp. a universal
homeomorphism into its image, resp. a universal homeomorphism) iff $f'$ is.

**Proof.** Apply VIII.4.6 after any base change $S_{1} \to S$. The hypotheses on $g$ are stable under base change. ∎

### VIII.4.8 — Separated and proper morphisms descend

<!-- source: VIII.4.8 -->

_This result says: separation and properness descend through faithfully flat quasi-compact base change._

**Corollary.** Under the conditions of VIII.4.6, $f$ is separated (resp. proper) iff $f'$ is.

**Proof.** *Separated.* The diagonal $\Delta_{f} : X \to X \times_{Y} X$ is universally closed iff $f$ is separated. By
VIII.4.7, this universal-closedness descends.

*Proper.* Recall $f$ proper means: (a) of finite type, (b) separated, (c) universally closed. Each descends: (a) by
VIII.3.3, (b) by the separated case, (c) by VIII.4.7. ∎

### VIII.4.9 — Remarks: quasi-compactness is essential

<!-- source: VIII.4.9 -->

**Remarks.** Two cautionary observations the gentle reader should internalise.

*First.* When $g : Y' \to Y$ is *flat of finite type* with $Y$ locally noetherian, $g$ is in fact *open* (file 27,
IV.6.6). This is sharper than VIII.4.3 (which only asserts the quotient-topology property). In general a faithfully flat
quasi-compact morphism of noetherian preschemes need not be open: take $Y$ irreducible whose generic point $y$ is not
open (e.g. an algebraic curve), and $Y' = Y \amalg \operatorname{Spec}(\kappa(y))$. Then the image in $Y$ of the open
part $\operatorname{Spec}(\kappa(y)) \subset Y'$ is ${y}$, which is not open. So "faithfully flat + quasi-compact +
noetherian" is a strictly weaker hypothesis than "flat + finite type + noetherian".

*Second.* The various statements of §VIII.4 *fail* if we drop quasi-compactness. The standard counterexample: let $Y$ be
an irreducible algebraic curve and $Y' = \amalg_{y \in Y} \operatorname{Spec}(\mathcal{O}_{Y, y})$ the disjoint sum of
the spectra of all local rings of points of $Y$. Then $Y' \to Y$ is faithfully flat but *not* quasi-compact, and the
pre-image in $Y'$ of the generic point ${y_{0}} \subset Y$ is open in $Y'$ (it is a connected component), while
${y_{0}}$ itself is not open in $Y$. So the quotient-topology conclusion VIII.4.3 fails. The intuition:
quasi-compactness controls the size of fibres of $g$, and without that control "small" subsets of $Y$ can have "large"
pre-images that are nevertheless open.

### VIII.4.10 — Note: a weakening of flatness

<!-- source: VIII.4.10 -->

**Note.** Several statements in §§VIII.1, VIII.3, VIII.4 remain valid when "$Y'$ is flat over $Y$" is replaced by:
"there exists a finite-type module $F$ on $Y'$ whose support is all of $Y'$ and which is flat over $Y$". The faithful-
flatness hypothesis is then replaced by the conjunction of the preceding and surjectivity of $Y' \to Y$. This applies to
the first two assertions of VIII.1.10 (finite type, finite presentation), to VIII.3.3, VIII.3.5, VIII.4.1, and hence to
all the results of the present section. The mechanism: faithful flatness of $Y' \to Y$ is being used only to reflect
exactness of certain module sequences, and the weaker hypothesis above also reflects them through $F$.

We do not pursue this generalisation; the standard fpqc hypothesis is enough for everything that follows.

## Closing: the quotient-topology bridge

Section §VIII.4 is a chain of corollaries of one fact: when $g : S' \to S$ is flat and $f : X \to Y$ is quasi-compact
into $Y = S$, the operations of taking image-closure commute with pulling back along $g$. From this it follows that
faithfully flat quasi-compact $g$ makes $S$ a quotient topological space of $S'$ (VIII.4.3). From the quotient- topology
property cascade the descent statements for open / closed / locally closed subsets, for open and closed maps, for
separation and properness.

The next file (§VIII.5) puts the quotient-topology fact together with descent of quasi-coherent sheaves (file 40
§VIII.1) to descend full morphisms of preschemes — not just *properties* of morphisms. Once that is done, §VIII.6 proves
Grothendieck's algebraic Zariski-Main-Theorem variants by combining descent with noetherian induction on $\dim Y$.

The slogan: **descent for topology is the quotient-topology formula $S = S' / R(g)$, and every named topological
property of morphisms descends through it.**

#### Aside (categorical perspective).

_Skip if categorical fibrations are not part of your background._

The fibred category of *opens* (resp. *closed subsets*) over `Sch` is a 0-truncated stack in the fpqc topology — a
sheaf, indeed. VIII.4.4 is the unwinding: the open/closed-subset functor is a sheaf with respect to single-cover fpqc
covers $S' \to S$. Vistoli's notes §4.1 spell out the general phenomenon (sheaf-on-a-site, fibred category, stack) of
which §§VIII.1 and §VIII.4 are two instances. The contrast: §VIII.1 is a non-trivial stack (a 1-stack — descent includes
1-morphism data, i.e. descent data); §VIII.4 is a sheaf (a 0-stack — descent reduces to set-level equalisers).

______________________________________________________________________

This closes §§VIII.2–4 in the gentle reading. Affine descent is in hand by direct reduction to module descent;
properties of morphisms (surjectivity, radiciality, finite type, quasi-finiteness) descend by short colimit arguments;
topological properties descend via the quotient-topology formula. The next file specialises to descent of *morphisms*
themselves in the category `Sch`.
