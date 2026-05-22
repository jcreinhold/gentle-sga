# Glossary

This glossary collects the technical terms used in Gentle SGA I. Each entry gives a short plain-English description and
a pointer to the file or sections where the term is introduced. Historical and French terminology is included where
helpful.

## Algebraic terms

**affine scheme.** The geometric object $\operatorname{Spec} A$ attached to a commutative ring $A$. File 02.

**algebra (over $A$).** A ring $B$ together with a structure homomorphism $A \to B$. Morphisms must commute with
structure maps. File 01.

**algebraization.** The promotion of a formal scheme $\mathfrak{X} \to \hat{S}$ (or a formal sheaf on it) to an ordinary
algebraic scheme $X \to S$ (or sheaf on $X$) whose formal completion is the formal object. The Grothendieck existence
theorem (file 18, appendix [`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence)) gives the
algebraization of coherent sheaves on $\hat{X}$ for $X$ proper. The **ample-sheaf criterion** (EGA III §4.7.1, appendix
[`algebraization-via-ample`](appendix-black-boxes.md#algebraization-via-ample)) algebraizes formal schemes themselves.
File 18, file 22.

**analytically reduced.** A noetherian local ring whose completion has no nilpotents. File 06; first inline cross-link
in file 12 at the proof of corollary I.9.4.

**augmentation ideal.** The kernel of a structure map $A \to k$ to a field, or analogously the kernel of a
multiplication map $B \otimes_{A} B \to B$. File 03.

**base change.** The operation $B \mapsto B \otimes_{A} A'$ (or its geometric counterpart $X \mapsto X \times_{Y} Y'$)
attached to a homomorphism $A \to A'$ (or morphism $Y' \to Y$). File 01, file 02.

**Cohen-Macaulay.** A noetherian local ring whose depth equals its Krull dimension. The transfer of Cohen-Macaulay along
quasi-finite flat (and so along étale) is [`cm-transfer`](appendix-black-boxes.md#cm-transfer) in the appendix. File 06.

**Cohen ring.** A complete noetherian local ring $W$ whose maximal ideal is `(p)` for some prime $p > 0$ (or `(0)`, in
which case $W$ is a field) and whose residue field is perfect. For $k = \mathbb{F}_{p}$ the Cohen ring is
$\mathbb{Z}_{p}$. For perfect $k$ of characteristic $p > 0$ the Cohen ring is the **ring of Witt vectors** $W(k)$. By
Cohen's structure theorem (EGA 0_IV §19.8, appendix [`cohen-ring`](appendix-black-boxes.md#cohen-ring)), every complete
noetherian local ring $(A, \mathfrak{m}, k)$ is a quotient of $W[[T_{1}, \cdots, T_{n}]]$ for some Cohen ring $W$ with
the same residue field. Synonymously: **Cohen $p$-ring** when emphasizing the mixed-characteristic case. _Intuition_: a
Cohen ring is the mixed-characteristic counterpart of a coefficient field — the canonical way to lift the residue field
$k$ from characteristic $p$ back to characteristic zero. File 22.

**coefficient field.** For an equicharacteristic complete local ring $(A, \mathfrak{m}, k)$, a subfield $k' \subset A$
mapping isomorphically to the residue field $k = A/\mathfrak{m}$. Existence is part of Cohen's structure theorem (EGA
0_IV §19.6, appendix [`coefficient-field`](appendix-black-boxes.md#coefficient-field)). A coefficient field gives the
trivial lift $X = X_{0} \otimes_{k} A$ of any $k$-scheme $X_{0}$. _Intuition_: in the equal-characteristic case, the
residue field $k$ sits inside $A$ itself as a subring — the residue projection has a section, so every object over $k$
lifts canonically to $A$. File 22\.

**conormal sheaf $\mathcal{N}_{Y/X}$.** For a closed immersion $Y \hookrightarrow X$ defined by a coherent ideal sheaf
$\mathcal{J}$, the coherent sheaf $\mathcal{J}/\mathcal{J}^{2}$ on $Y$. Records first-order behavior of $X$ along $Y$.
Sits in the **conormal exact sequence**

```text
𝒩_{Y/X}  →  Ω¹_{X/S} ⊗_{𝒪_X} 𝒪_Y  →  Ω¹_{Y/S}  →  0,
```

which is split exact under the Jacobian criterion (file 15, II.4.10). File 03 builds it for the diagonal; file 15
develops it for general closed immersions.

**completion.** For a noetherian local ring $(A, \mathfrak{m})$, the $\mathfrak{m}$-adic completion
$\hat{A} = \lim_{n} A/\mathfrak{m}^{n}$. File 05. Generalized to **$\mathcal{I}$-adic completion** of a noetherian ring
$R$ along an ideal $\mathcal{I} \subset R$ in file 18; the geometric counterpart is the **formal scheme**. Flatness of
$R \to \hat{R}$ is proved in file 25 (IV.3.1); faithful flatness under the radical hypothesis is file 25 (IV.3.2).

**constructible set.** A subset of a topological space that is a finite union of locally closed subsets. In a noetherian
space, the constructible subsets form a Boolean algebra (closed under finite union, finite intersection, complement).
Chevalley's theorem (file 27, IV.6.2; appendix
[`chevalley-constructibility`](appendix-black-boxes.md#chevalley-constructibility)) says the image of a finite-type
morphism between noetherian schemes is constructible. File 27.

**different ideal $\mathfrak{d}_{X/Y}$.** The annihilator of $\Omega^{1}_{X/Y}$. Cuts out the closed subscheme of $X$
where $X/Y$ is ramified. Related to the **discriminant** by $disc(\mathcal{B}/\mathcal{O}_{Y}) = N(\mathfrak{d}_{X/Y})$
(the norm to the base) when $X \to Y$ is finite locally free. File 04, file 10.

**differentially smooth.** A morphism $f : X \to Y$ such that the diagonal $\Delta_{X/Y} : X \to X \times_{Y} X$ is a
**regular immersion**. Equivalently: $\Omega^{1}_{X/Y}$ is locally free and the canonical surjection
$S_{\mathcal{O}_{X}}(\Omega^{1}_{X/Y}) \to gr_{*}(\mathcal{P}^{\infty}_{X/Y})$ from the symmetric algebra to the
associated graded of the principal-parts sheaf is an isomorphism. Smooth = flat + differentially smooth (file 15,
II.4.18). File 15.

**discriminant.** For a finite locally free covering $X \to Y$ of degree $n$, the section
$d_{X/Y} \in \Gamma(Y, \wedge^{n}\check{\mathcal{B}} \otimes \wedge^{n}\check{\mathcal{B}})$ measuring nondegeneracy of
the trace pairing. The covering is étale iff the discriminant is invertible (the discriminant ideal is the unit ideal).
Related to the **different ideal** by $disc(\mathcal{B}/\mathcal{O}_{Y}) = N(\mathfrak{d}_{X/Y})$. File 04, file 10.

**dominant morphism.** A morphism $f : X \to Y$ whose image hits the generic point of every irreducible component of
$Y$. File 12.

**embedded prime.** A prime ideal $\mathfrak{p} \subset A$ that is associated to $A$ (i.e. the annihilator of some
element of $A$) but is _not_ a minimal prime. Used in file 12 section I.9.

**equidimensional.** A morphism whose fiber components all have the same dimension. The condition is flagged by
Grothendieck's footnote to IV.6.6 (file 27) as generally **not** implied by flatness alone. The answer to whether a flat
finite-type morphism with integral base induces equidimensional fiber components on each component of the source: yes
for components, no for fibers in general; cf. EGA IV 12.1.1.5. File 27.

**essentially of finite type.** An $A$-algebra $B$ is _essentially of finite type_ over $A$ if $B$ is isomorphic to a
localization $C_{\mathfrak{q}}$ of an $A$-algebra $C$ of finite type at a prime $\mathfrak{q} \subset C$. Used in files
11 and 12.

**étale morphism.** A morphism of finite type that is **flat** and **unramified**. The algebraic analogue of a local
isomorphism. File 04, file 10.

**étale covering.** A finite étale morphism. The algebraic analogue of a finite covering space. The category of étale
coverings of a connected locally noetherian $S$ is a Galois category (file 33, V.7), with associated profinite group the
**étale fundamental group** $\pi_{1}(S, a)$. Inertia analysis for étale coverings arising from quotients $X \to X / G$
is in file 30, V.2. File 04, file 10, file 30, file 33.

**étale site $X_{et}$.** The Grothendieck site whose underlying category is the category of étale morphisms $U \to X$
and whose covering families are the jointly surjective collections of étale morphisms. The general notion of
Grothendieck site is set up in file 34, Module A; the étale site itself is the standard setting for étale sheaves, étale
cohomology, and the operations $f_{*}$, $R^{q} f_{*}$ used throughout files 61–64. _Intuition_: this is the natural home
for the étale version of cohomology — every gluing question that uses étale (rather than Zariski) covers takes place
here. File 34, file 61.

**faithfully flat.** A flat $A$-module $M$ such that $M \otimes_{A} -$ _reflects_ exactness, equivalently
$M \otimes_{A} N = 0 \Longrightarrow N = 0$, equivalently $M \otimes_{A} A/\mathfrak{m} \neq 0$ for every maximal ideal
$\mathfrak{m}$. For a ring map $A \to B$ viewed as making $B$ an $A$-module: $B$ is faithfully flat over $A$ iff
$\operatorname{Spec} B \to \operatorname{Spec} A$ is surjective and $B$ is $A$-flat. The descent hypothesis of
Grothendieck's school. Six-condition equivalence in file 24, IV.2.6. File 01, file 24.

**fat point.** The scheme $\operatorname{Spec} k[\epsilon]/(\epsilon^{2})$ for a field $k$. Topologically a single
point, but the structure ring carries one nonzero infinitesimal direction $\epsilon$ with $\epsilon^{2} = 0$. The
universal "point with one infinitesimal direction"; everything involving derivatives in algebraic geometry maps in or
out of it. Files 02, 03, 04, 05.

**fiber.** For $f : X \to Y$ and $y \in Y$, the scheme $f^{-1}(y) = X \times_{Y} \operatorname{Spec} \kappa(y)$ over the
residue field of $y$. File 02.

**finite morphism.** A morphism $f : X \to Y$ such that, locally on $Y$, $X$ corresponds to a finite-rank
$\mathcal{O}_{Y}$-algebra. File 02.

**finite locally free.** A morphism $f : X \to Y$ such that the corresponding sheaf of $\mathcal{O}_{Y}$-algebras is
locally a finite free $\mathcal{O}_{Y}$-module of constant rank. Equivalent to "finite + flat + finitely presented" via
the [local flatness criterion](appendix-black-boxes.md#local-flatness-criterion). The setting where the trace pairing
and the discriminant are defined. File 04.

**finite type.** A morphism $f : X \to Y$ such that, locally on $Y$, $X$ is `Spec` of a finitely generated
$\mathcal{O}_{Y}$-algebra. File 01.

**flat morphism.** A morphism $f : X \to Y$ such that $\mathcal{O}_{x}$ is flat over $\mathcal{O}_{f(x)}$ for every
$x \in X$. Used as a black box in files 04–22; the
[local flatness criterion](appendix-black-boxes.md#local-flatness-criterion) (file 26, IV.5.6) gives flat ⟺ free for
finitely generated modules over a local noetherian ring. The full sorites of flatness — closure under composition, base
change, transitive combination, and the relationship to Tor — are in file 24, §IV.1. The geometric consequences
(open-image theorem, openness of the flat locus, generic flatness) are in file 27, §IV.6. File 04, files 24–27.

**formal scheme.** A topologically ringed space locally isomorphic to $Spf \hat{R}$ for some noetherian adic ring
$\hat{R}$; equivalently, an inverse system of ordinary schemes $(S_{n})$ indexed by infinitesimal precision and sharing
a common underlying space. The $\mathcal{I}$-adic completion of an ordinary scheme $S$ along the closed subscheme
$V(\mathcal{I})$ is the prototype. File 18.

**formally étale.** A morphism $f : X \to Y$ such that for every closed subscheme $Y_{0}' \subset Y'$ defined by a
nilpotent ideal of $\mathcal{O}_{Y'}$ and every morphism $Y' \to Y$, the restriction
$\operatorname{Hom}_{Y}(Y', X) \to \operatorname{Hom}_{Y}(Y_{0}', X)$ is a bijection. Étale morphisms are exactly the
formally étale morphisms locally of finite presentation; see
[`formally-etale-lifting`](appendix-black-boxes.md#formally-etale-lifting) in the appendix. File 05. In Exposé III:
**formally étale = formally smooth + trivial residual extension** (equivalently, formally smooth of relative dimension
`0`). File 19.

**formally smooth.** A local homomorphism of noetherian local rings $A \to B$ with finite residual extension such that
the conditions of Definition III.1.1 (file 19) hold; equivalently, the lifting property of Theorem III.2.1 (every
algebra map $B \to C/J$ to an artinian quotient by a nilpotent ideal lifts to $B \to C$). For finite-type morphisms,
**formally smooth = smooth** (file 19, III.1.9). The most general modern definition is in EGA 0_IV §19.3.1; appendix
[`formally-smooth-ega`](appendix-black-boxes.md#formally-smooth-ega). File 19.

**formally unramified.** A local homomorphism $A \to B$ satisfying the unramified analogue of III.2.1's lifting property
(lifts of $B \to C/J$ exist and are unique). The renaming of Exposé I's "essentially unramified"; see file 19, III.1.2.

**function field.** For an integral scheme $Y$, the field $\kappa(generic point of Y)$. File 12.

**generic flatness.** For $f : X \to Y$ of finite type with $Y$ integral noetherian and $F$ a coherent sheaf on $X$:
there exists a non-empty open $V \subset Y$ such that $F$ is flat over $Y$ at every point of $f^{-1}(V)$. The
"spread-out" theorem used freely in arithmetic geometry (file 27, IV.6.11). The weaker form needs only generic freeness
(IV.6.7); the stronger "openness of the flat locus" (IV.6.10) needs the local flatness criterion. File 27.

**generic freeness.** For $A$ noetherian integral, $B$ a finite-type $A$-algebra, $M$ a finite-type $B$-module: there
exists a non-zero $f \in A$ such that $M_{f}$ is free over $A_{f}$. The algebraic input behind generic flatness; proved
in file 27 (IV.6.7) by induction on the dimension of the support, using Noether normalization. File 27.

**generization.** A point $y$ of a topological space is a generization of $x$ if $x \in closure({y})$ (the closure of
${y}$). For $\operatorname{Spec} A$, this corresponds to $\mathfrak{p}_{y} \subset \mathfrak{p}_{x}$ (inclusion of
primes, with $y$ having the smaller prime). The generic point of an irreducible closed subset is the generization of
every point of that subset. File 27.

**generic point.** For an integral scheme, the point `(0)` whose closure is the whole space. File 02.

**Grothendieck existence theorem.** EGA III §5.4.1: for $X \to \operatorname{Spec} R$ proper with $R$ complete and
noetherian, the functor $\mathcal{F} \mapsto \hat{\mathcal{F}}$ is an equivalence of categories from coherent sheaves on
$X$ to coherent sheaves on the formal completion $\hat{X}$. The algebraization of coherent sheaves; appendix
[`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence). File 18, file 21, file 22.

**geometrically unibranch.** An integral local ring whose normalization is local with radicial residue extension. The
diagnostic for connectedness preservation under étale covers. File 06, file 12.

**graph morphism.** For $g : X' \to X$, the morphism $\Gamma_{g} : X' \to X \times_{Y} X$ sending $x'$ to $(x', g(x'))$.
File 10.

**henselian (local ring).** A local ring $(A, \mathfrak{m})$ with residue field $\kappa = A/\mathfrak{m}$ is _henselian_
if for every monic polynomial $f \in A[t]$ whose reduction $\bar{f} \in \kappa[t]$ factors as
$\bar{f} = \bar{g} \cdot \bar{h}$ with $\bar{g}, \bar{h}$ coprime monics in $\kappa[t]$, there is a factorisation
$f = g \cdot h$ in `A[t]` with `g, h` monic of the same degrees as $\bar{g}, \bar{h}$ respectively and lifting them.
Equivalently: every étale $A$-algebra that admits a section over $\kappa$ already admits a section over $A$. Complete
local rings are henselian; the henselisation $A^{h}$ is the universal henselian local extension of $A$ with the same
residue field. _Intuition_: Hensel's lemma holds in $A$ — a coprime factorisation of a polynomial over the residue field
always lifts back to the ring, so étale covers behave as if they were already split when the residue-field obstruction
is removed. Files 05, 11 (used as a hypothesis in Hensel-type lifting arguments); see the appendix entry
[`hensel`](appendix-black-boxes.md#hensel).

**$\mathcal{I}$-adic completion.** For a noetherian ring $R$ and ideal $\mathcal{I} \subset R$, the inverse limit
$\hat{R} = \lim_{n} R/\mathcal{I}^{n+1}$ with the inverse-limit topology. The structure sheaf of the formal scheme
$Spf \hat{R}$. Generalizes the **completion** of a local ring. The map $R \to \hat{R}$ is flat; faithfully flat after
localizing at primes containing $\mathcal{I}$. File 18.

**ideal of definition.** In a noetherian local ring $B$ with maximal ideal $\mathfrak{n}$, an ideal $I$ with
$\mathfrak{n}^{n} \subseteq I \subseteq \mathfrak{n}$ for some $n$. File 04. In a formal scheme: an ideal whose powers
form a fundamental system of open neighborhoods of zero in the structure sheaf. File 18.

**immersion.** A morphism that locally factors as a closed immersion followed by an open immersion. File 02.

**infinitesimal neighborhood.** The $n$-th infinitesimal neighborhood
$\Delta^{n}_{X/Y} = (|X|, \mathcal{O}_{X\times_{Y} X}/\mathcal{I}^{n+1})$ of the diagonal. Also written
$\operatorname{Spec} \mathcal{P}^{n}_{X/Y}$ for the **principal-parts sheaf**. File 03, file 10, file 15.

**infinitesimal thickening.** A closed immersion $Y_{0} \hookrightarrow Y$ defined by a sheaf of ideals
$\mathcal{J} \subset \mathcal{O}_{Y}$ that is **nilpotent** (or, in the formal context, locally nilpotent). The two
preschemes share their underlying space; $Y_{0} \hookrightarrow Y$ adds higher-order infinitesimal structure. The
square-zero case ($\mathcal{J}^{2} = 0$) is the basic step of deformation theory. The thickenings
$S_{n} = V(\mathcal{I}^{n+1})$ of an ordinary scheme along an ideal sheaf are the prototypical example. Files 18, 20,
21\.

**Jacobian criterion.** The characterization of smoothness of a closed sub-prescheme $Y \hookrightarrow X$ (with $X$
smooth) in terms of generators of the defining ideal whose differentials are linearly independent at the point. Theorem
II.4.10 (file 15). The classical form: a hypersurface ${F = 0}$ in a smooth ambient is smooth at $x$ iff $dF(x) \neq 0$
(II.4.12, file 15).

**integral domain.** A nonzero commutative ring with no zero divisors. File 06.

**integral closure.** For an integral ring $A$ with field of fractions $K$, the set of elements of $K$ integral over
$A$. File 06, file 12.

**integrally closed.** Equivalent to **normal**: every element of the field of fractions integral over the ring lies in
the ring. File 06.

**Kähler differentials.** The $B$-module $\Omega^{1}_{B/A} = \ker(\mu)/\ker(\mu)^{2}$, where
$\mu : B \otimes_{A} B \to B$. Represents $A$-derivations of $B$. File 03. The dual
$\operatorname{Hom}_{B}(\Omega^{1}_{B/A}, B) = \operatorname{Der}_{A}(B, B)$ is the algebraic counterpart of the
**tangent sheaf**.

**Krull dimension.** The supremum of lengths of chains of prime ideals. File 06.

**local homomorphism.** A homomorphism $A \to B$ of local rings sending the maximal ideal of $A$ into the maximal ideal
of $B$. File 01.

**local ring.** A ring with exactly one maximal ideal. File 01.

**locally noetherian.** A scheme covered by spectra of noetherian rings. File 01.

**Main Theorem (Zariski).** A quasi-finite morphism is locally an open immersion into a finite morphism. Used as a black
box; see [`zmt`](appendix-black-boxes.md#zmt) in the appendix. File 05.

**maximal ideal.** A proper ideal not contained in any larger proper ideal. File 01.

**monogenic module.** Synonym for **cyclic**: an $A$-module of the form $A/I$ for some ideal $I \subset A$, equivalently
a module generated by a single element. Every finite-type module admits a composition series with monogenic quotients.
File 24.

**multiplodocus.** Grothendieck's informal name for the larger SGA

- EGA machine. Mentioned in the source in sections I.6 and I.7. We treat citations to the multiplodocus as black-box
  references to later parts of EGA/SGA.

**Nagata ring.** A noetherian ring such that the integral closure of every reduced quotient in a finite extension of its
total ring of fractions is finite. The setting where normalization behaves well. Nagata's theorem on finiteness of
normalizations is [`nagata-finite`](appendix-black-boxes.md#nagata-finite) in the appendix. File 06.

**net morphism.** Synonym for **unramified morphism**. The French source uses "net" because Grothendieck preferred it;
we keep both words until the eye gets used to either. File 04, file 10.

**Noether normalization.** Lemma: every finite-type integral algebra $B$ over a field $K$ is finite over a polynomial
subring $K[t_{1}, \cdots, t_{n}]$ for some algebraically independent $t_{1}, \cdots, t_{n} \in B$. Geometrically: every
affine variety of dimension $n$ over a field admits a finite map to $\mathbb{A}^{n}$. The inductive base of the
generic-freeness lemma (file 27, IV.6.7). Appendix
[`noether-normalization`](appendix-black-boxes.md#noether-normalization). File 23.

**nilpotent.** An element $a$ with $a^{n} = 0$ for some $n$. File 01.

**nilpotent thickening.** A closed immersion $Y_{0} \to Y$ with the same underlying topological space, defined by an
ideal $I$ with $I^{n} = 0$ for some $n$. The étale category is invariant under such thickenings. File 05, file 11.

**noetherian.** A ring in which every ascending chain of ideals stabilizes; equivalently, every ideal is finitely
generated. File 01.

**normal.** A ring whose localization at every prime is an integrally closed integral domain. A scheme is normal if all
its local rings are normal. File 06, file 12.

**normalization.** For an integral ring or scheme, the universal normal ring or scheme together with a finite-type map
to the original. The "remove non-normal singularities" operation. File 06.

**open immersion.** A morphism that locally identifies the source with an open subscheme of the target, with structure
sheaf the restriction of $\mathcal{O}_{target}$. The simplest étale morphism. File 02.

**open morphism.** A morphism $f : X \to Y$ that maps open subsets of $X$ to open subsets of $Y$. The open-image theorem
(file 27, IV.6.6) says that a finite-type morphism carrying a coherent sheaf with full support that is flat over the
base is open. **Universally open** = open after every base change; flatness gives universally open by IV.1's closure
properties. File 27.

**prescheme.** Grothendieck's term for what we now call a "scheme without separation hypothesis." Modern usage often
drops this prefix. File 02.

**principal homogeneous sheaf.** A sheaf $\mathcal{P}$ of sets equipped with a sheaf-of-sets action of a sheaf of groups
$\mathcal{G}$ such that the natural map $\mathcal{G} \times \mathcal{P} \to \mathcal{P} \times \mathcal{P}$ is an
isomorphism, and the stalks of $\mathcal{P}$ are nonempty. Equivalent: locally, $\mathcal{P}$ admits a
$\mathcal{G}$-equivariant isomorphism with $\mathcal{G}$ itself (acting by translation). Synonym: **torsor under
$\mathcal{G}$** (Giraud). The set of isomorphism classes of torsors under $\mathcal{G}$ is in canonical bijection with
$H^{1}(X, \mathcal{G})$; appendix [`giraud-torsor`](appendix-black-boxes.md#giraud-torsor). The H¹ obstruction in §III.5
(file 21) is exactly the cohomology class of the torsor of extensions. Files 17, 21.

**prime ideal.** A proper ideal $\mathfrak{p} \subset A$ such that $ab \in \mathfrak{p}$ implies $a \in \mathfrak{p}$ or
$b \in \mathfrak{p}$. File 02.

**projective module.** An $A$-module $P$ such that $\operatorname{Hom}_{A}(P, -)$ is exact, equivalently a direct factor
of a free $A$-module. Projective ⟹ flat. Over a noetherian local ring with $A/I$ a field (e.g. the residue field),
projective ⟺ free ⟺ flat (file 25, IV.4.3). File 24.

**principal parts sheaf $\mathcal{P}^{n}_{X/S}$.** For an $S$-prescheme $X$, the quasi-coherent sheaf of algebras
$\mathcal{O}_{X \times_{S} X} / \mathcal{I}^{n+1}_{X}$ on $X$ (regarded as $\mathcal{O}_{X}$-algebra via the first
projection). The infinite-order limit $\mathcal{P}^{\infty}_{X/S} = \lim_{n} \mathcal{P}^{n}_{X/S}$ is the structure
sheaf of the formal completion of $X \times_{S} X$ along the diagonal. Universal carrier of differential operators of
order $\leq n$ on $\mathcal{O}_{X}$ relative to $S$. File 03 (n=0, 1), file 15 (general n).

**proper morphism.** A separated, universally closed morphism of finite type. File 11. Used in the proof of theorem
I.5.1.

**quasi-coherent sheaf.** A sheaf of $\mathcal{O}_{X}$-modules that, on each affine open
$\operatorname{Spec} A \subseteq X$, comes from an $A$-module. File 03.

**quasi-finite.** A morphism $f : X \to Y$ such that $x$ is isolated in its fiber $f^{-1}(f(x))$ for every $x$. File 04,
file 10\.

**radicial morphism.** A universally injective morphism: injective on points with purely inseparable residue extensions.
The condition that, combined with étale, forces an open immersion. File 05, file 11.

**ramified.** "Not unramified." The locus where $f : X \to Y$ is ramified is the support of $\Omega^{1}_{X/Y}$,
equivalently the closed subscheme of $X$ cut out by the different ideal $\mathfrak{d}_{X/Y}$. File 04.

**rank.** For a locally free $\mathcal{O}_{Y}$-module of finite type, the locally constant function on $Y$ giving the
rank of the fiber as a free module. File 04.

**reduced.** A ring or scheme with no nonzero nilpotents. File 06.

**regular.** A noetherian local ring whose maximal ideal is generated by $\dim A$ elements. The algebraic analogue of a
smooth point. File 06.

**regular immersion.** A closed immersion $Y \hookrightarrow X$ whose defining ideal sheaf $\mathcal{J}$ admits, locally
near every point of $Y$, a regular system of generators — equivalently, $\mathcal{J}/\mathcal{J}^{2}$ is locally free as
an $\mathcal{O}_{Y}$-module and $S_{\mathcal{O}_{Y}}(\mathcal{J}/\mathcal{J}^{2}) \to gr^{\mathcal{J}}(\mathcal{O}_{X})$
is an isomorphism. The intrinsic form of "smooth submanifold" in algebraic geometry. File 15\.

**relative differentials.** The sheaf $\Omega^{1}_{X/Y}$, which represents relative $Y$-derivations of
$\mathcal{O}_{X}$. File 03, file 10; locally free of rank equal to the relative dimension under smoothness (file 15).

**relative dimension.** For a smooth morphism $f : X \to Y$ and a point $x \in X$, the integer
$\dim_{x} f = \dim \mathcal{O}_{f^{-1}(f(x)), x}$. Equivalently, the rank of $\Omega^{1}_{X/Y}$ at $x$ (file 15, II.4.3)
or the integer $n$ in any smoothness witness $U \to Y[t_{1}, \cdots, t_{n}]$ (file 14, II.1.1). Additive under
composition of smooth morphisms. File 14.

**residue extension.** For a local homomorphism $A \to B$, the induced extension $\kappa(A) \to \kappa(B)$ of residue
fields. File 01.

**residue field.** For a prime $\mathfrak{p} \subset A$, the field $\kappa(\mathfrak{p}) = Frac(A/\mathfrak{p})$. File
01, file 02.

**Serre's criterion (for normality).** [`serre-normality`](appendix-black-boxes.md#serre-normality) in the appendix. A
noetherian ring of nonzero dimension is normal iff regular in codimension `1` and depth $\geq 2$ in codimension
$\geq 2$. Black box. File 12.

**section.** For $f : X \to Y$, a morphism $s : Y \to X$ with $f \circ s = id_{Y}$. File 11.

**separable algebra.** A finite-rank algebra over a field that is isomorphic to a finite product of finite separable
field extensions. File 04.

**separable extension.** A finite field extension $L/K$ such that the minimal polynomial of every element of $L$ over
$K$ is separable (has distinct roots in an algebraic closure). File 04. For arbitrary (not necessarily finite)
extensions: $L/K$ is separable if $L \otimes_{K} K^{1/p^{\infty}}$ is reduced (when $char K = p$), equivalently if every
finitely generated intermediate extension admits a separating transcendence basis (file 16).

**separating transcendence basis.** For a field extension $K / k$, a transcendence basis $t_{1}, \cdots, t_{n}$ of $K$
over $k$ such that $K / k(t_{1}, \cdots, t_{n})$ is finite separable. Equivalently (file 16, II.5.6): the differentials
$dt_{i}$ form a $K$-basis of $\Omega^{1}_{K/k}$. File 16.

**separated morphism.** A morphism whose diagonal is a closed immersion. Standard hypothesis for "scheme" in the
source's terminology. File 02.

**simple point.** Older terminology (pre-1960) for a smooth point. Grothendieck dropped the term because of conflict
with "simple" used elsewhere (simple algebras, simple groups). Synonym for **smooth at $x$**. File 14.

**specialization.** A point $x$ of a topological space is a specialization of $y$ if $x \in closure({y})$, i.e. $y$ is a
**generization** of $x$. The dual notion to generization. For $\operatorname{Spec} A$, $x$ specializes $y$ iff
$\mathfrak{p}_{y} \subset \mathfrak{p}_{x}$. File 27.

**spectral sequence (for composite functors).** Grothendieck's spectral sequence relating the derived functors of a
composite $G \circ F$ to the iterated derived functors of $F$ and $G$ separately, when $F$ carries projectives to
$G$-acyclics: $R^{p} G(R^{q} F(M)) \Rightarrow R^{p + q}(G \circ F)(M)$. The five-term exact sequence in low degrees is
what file 26 invokes in its proof of IV.5.2. Appendix
[`spectral-sequence-composite-functors`](appendix-black-boxes.md#spectral-sequence-composite-functors). File 23.

**smooth morphism.** A morphism $f : X \to Y$ that is, locally on the source, étale over a relative polynomial scheme
$Y[t_{1}, \cdots, t_{n}]$ for some $n$. Equivalently (II.2.1, file 14): flat plus smooth fibers. The algebraic analogue
of a submersion. The integer $n$ is the **relative dimension** at the point. Étale morphisms are smooth of relative
dimension `0`. File 14.

**smooth at a point.** A morphism $f : X \to Y$ is smooth at $x \in X$ if there is an open neighborhood $U$ of $x$ and
an étale $Y$-morphism $U \to Y[t_{1}, \cdots, t_{n}]$ for some $n$. The smoothness locus is open. File 14.

**spectrum ($\operatorname{Spec} A$).** The geometric object attached to a ring $A$: the set of prime ideals with the
Zariski topology and the canonical structure sheaf. File 02.

**stalk.** For a sheaf $\mathcal{F}$ on $X$ and a point $x \in X$, the limit
$\mathcal{F}_{x} = \lim_{U \ni x} \mathcal{F}(U)$ over open neighborhoods. File 03\.

**tangent sheaf.** For a morphism $X \to S$ of preschemes, the dual of relative differentials:
$\mathfrak{g}_{X/S} := \mathcal{Hm}_{\mathcal{O}_{X}}(\Omega^{1}_{X/S}, \mathcal{O}_{X})$. Equivalently, the sheaf of
$S$-derivations of $\mathcal{O}_{X}$ into itself. For $X$ smooth over $S$ of relative dimension $n$,
$\mathfrak{g}_{X/S}$ is locally free of rank $n$ — the algebraic counterpart of the classical tangent bundle. The H²
obstructions to lifting smooth schemes (file 21) and the counterexamples preserving non-liftability (file 22) are stated
in $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/S_{0}})$. Files 17, 21, 22.

**strict henselization.** Not used in this exposé but the standard "smallest étale local extension that splits all
finite étale extensions." Mentioned for completeness.

**structure sheaf.** The sheaf $\mathcal{O}_{X}$ of regular functions on a scheme. On $\operatorname{Spec} A$, given by
$\mathcal{O}_{X}(D(f)) = A[1/f]$. File 02\.

**support of a sheaf.** For a coherent sheaf $F$ on a scheme $X$, the closed subset
$Supp(F) = { x \in X : F_{x} \neq 0}$. For a finite-type module $M$ over $B$, $Supp(\tilde{M}) = V(Ann_{B}(M))$. The
"full support" hypothesis $Supp(F) = X$ is the condition under which IV.6.6 applies. File 27.

**tensor product.** For modules `M, N` over $A$, the universal target of bilinear maps $M \times N \to ?$ over $A$. For
algebras, the coproduct. File 01.

**topological space underlying a scheme.** The space of points of the scheme, with the Zariski topology. File 02.

**Tor functor.** The left-derived functor of $M \otimes_{A} -$. Built from a free resolution
$\cdots \to L_{1} \to L_{0} \to M \to 0$ by $Tor^{A}_{i}(M, N) := H_{i}(L_{\bullet} \otimes_{A} N)$. Independence of the
resolution, symmetry $Tor^{A}_{i}(M, N) \cong Tor^{A}_{i}(N, M)$, and the long exact sequence in either argument are
recorded in file 23. The vanishing characterization of flatness: $M$ is $A$-flat iff $Tor^{A}_{1}(M, N) = 0$ for every
$N$. Appendix [`tor-derived-functor`](appendix-black-boxes.md#tor-derived-functor). File 23.

**torsion-free module.** An $A$-module $M$ such that for every non-zero-divisor $x \in A$, multiplication by $x$ is
injective on $M$. Over an integral ring, every flat module is torsion-free (file 24, IV.1.3 (i)); over a Dedekind ring
(or PID), the converse holds (file 24, IV.1.3 (ii)). File 24.

**torsor.** Synonym for **principal homogeneous sheaf** (Giraud's term). File 17.

**total ring of fractions.** For a ring $A$, the localization at the multiplicative system of nonzerodivisors. Equals
the field of fractions when $A$ is integral. File 12.

**trace pairing.** For a finite locally free $\mathcal{A}$-algebra $\mathcal{B}$, the bilinear form
$(b, b') \mapsto tr_{\mathcal{B}/\mathcal{A}}(bb')$. Nondegeneracy is the discriminant criterion for étaleness. File 04,
file 12.

**unibranch (geometrically).** See **geometrically unibranch**.

**universal homeomorphism.** A finite, radicial, surjective morphism. Invisible to the étale category; the invariance
statement is [`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) in the appendix. File 12.

**universal property.** A property characterizing an object up to unique isomorphism by morphisms in or out. File 01.

**universally injective.** Synonym for **radicial**. File 05.

**universally open.** A morphism such that every base change is open. Flat finite-type morphisms with full-support
coherent sheaf are universally open by IV.6.6 + base-change preservation of flatness. File 12, file 27.

**unramified morphism.** Synonym for **net morphism**. A morphism of finite type with $\Omega^{1}_{X/Y} = 0$ near the
relevant point. File 04, file 10.

**Witt vectors.** For a perfect field $k$ of characteristic $p > 0$, the unique complete discrete valuation ring $W(k)$
with residue field $k$, characteristic zero, and uniformizer $p$. The **Cohen ring** of $k$ in mixed characteristic. For
$k = \mathbb{F}_{p}$, $W(k) = \mathbb{Z}_{p}$. For $k = \mathbb{F}_{q}$ with $q = p^{r}$, $W(k)$ is the unramified
extension of $\mathbb{Z}_{p}$ of degree $r$. The universal mixed-characteristic lift of $k$. _Intuition_: Witt vectors
are the canonical way to lift a characteristic-$p$ ring to characteristic zero — every element of $W(k)$ has a unique
expansion as a sequence of Teichmüller representatives in $k$, with addition and multiplication given by universal
integer polynomials. File 22; full account in Serre, _Local Fields_ Ch. II.

## Geometric and historical terms

**branch point.** A point of the target where a covering is ramified. The standard model: $t \mapsto t^{2}$ over the
origin in characteristic not `2`. File 04.

**covering map (analytic analogue).** A topological covering of manifolds. Étale morphisms are the algebraic analogue,
but the analogy is not literal: the algebraic category does not equal the topological one. File 04.

**double point.** A simple algebraic singularity of a curve (a node). File 12.

**Frobenius morphism.** The map $x \mapsto x^{p}$ in characteristic $p$. Radicial but not étale. File 05.

**Hensel's lemma.** Two related statements over a complete noetherian local ring $(A, \mathfrak{m})$: the **algebra
form** (every finite étale $k$-algebra lifts uniquely to a finite étale $A$-algebra) is the engine of theorem I.6.1; the
**polynomial form** (a coprime factorization of a monic polynomial mod $\mathfrak{m}$ lifts to a factorization over $A$)
is its classical corollary. See [`hensel`](appendix-black-boxes.md#hensel) in the appendix. File 05.

**Krull's intersection theorem.** Used inside the proof of proposition I.3.1 (ii) ⟹ (iii); see
[`krull-intersection`](appendix-black-boxes.md#krull-intersection). File 10.

**Nakayama's lemma.** Standard tool: for $M$ finitely generated over a local ring $(A, \mathfrak{m})$,
$M = \mathfrak{m}M \Longrightarrow M = 0$. Used throughout the source; see
[`nakayama`](appendix-black-boxes.md#nakayama). File 11.

**ordinary cusp.** Geometrically unibranch curve singularity. File 06.

**ordinary double point (node).** Not geometrically unibranch. File 12.

**Tate curve.** Not used in this exposé but a recurring example elsewhere in arithmetic geometry; mentioned only for
completeness.

**Zariski topology.** The standard topology on $\operatorname{Spec} A$: closed sets are vanishing loci of ideals. File
02.

## Profinite groups, Galois categories, and the étale fundamental group (files 28–33)

These terms appear in the rewrite of Exposé V (files 28–33). Most generalise topological notions from covering-space
theory (file 28); the algebraic counterparts live in the Galois- category formalism of file 32 and the
étale-fundamental-group construction of file 33.

**connected object (in a category).** An object $X$ of a category $\mathcal{C}$ with finite coproducts and an initial
object $\emptyset_{\mathcal{C}}$ such that `X ≄ ∅_𝒞` and any decomposition $X \cong A \amalg B$ forces
$A \cong \emptyset_{\mathcal{C}}$ or $B \cong \emptyset_{\mathcal{C}}$. In $\mathcal{C}(\pi)$, the connected objects are
the finite sets on which $\pi$ acts transitively. In $\mathcal{C}(S)$ (file 33), they are the topologically-connected
finite étale coverings. File 29.

**covering map (topological).** A continuous surjection $p : E \to B$ such that every $b \in B$ has an open neighborhood
$U$ with $p^{-1}(U) \cong U \times D$ for some discrete set $D$ (the **fibre over $b$**). The geometric prototype of an
étale morphism. File 28.

**deck transformation.** For a covering $p : E \to B$, a homeomorphism $\phi : E \to E$ with $p \circ \phi = p$. The
deck transformations form a group $\operatorname{Aut}(E / B)$, which equals $\pi^{top}_{1}(B, b_{0})$ for the universal
cover. The algebraic analogue of a deck transformation is $s \in G$ for a finite group $G$ acting on $X$ by
$Y$-automorphisms (file 30). File 28.

**decomposition group $G_{d}(x)$.** For a finite group $G$ acting on a prescheme $X$ and a point $x \in X$, the
stabiliser $G_{d}(x) = { s \in G : s \cdot x = x}$ of $x$ in $G$. The decomposition group acts on the residue field
$\kappa(x)$ over $\kappa(p(x))$, and the natural map $G_{d}(x) \to \operatorname{Gal}(\kappa(x) / \kappa(p(x)))$ is
surjective by V.1.1 (iii). File 30.

**étale fundamental group $\pi_{1}(S, a)$.** For a connected locally noetherian prescheme $S$ and a geometric point
$a : \operatorname{Spec}(\Omega) \to S$, the profinite group $\operatorname{Aut}(F_{a})$, where $F_{a}$ is the fibre
functor "geometric points of $X / S$ lying over $a$" on the category of finite étale coverings of $S$. Constructed by
applying Theorem V.4.1 (file 31) to $(\mathcal{C}(S), F_{a})$. The classifying invariant:
$\mathcal{C}(S) \simeq \mathcal{C}(\pi_{1}(S, a))$. For $S = \operatorname{Spec}(k)$,
$\pi_{1}(S, \bar{a}) = \operatorname{Gal}(\bar{k} / k)$ (V.8.1). For $S = \operatorname{Spec} \mathbb{Z}$,
$\pi_{1} = (1)$ (Minkowski). File 33.

**fibre functor (= fundamental functor).** For a Galois category $\mathcal{C}$, a covariant functor
$F : \mathcal{C} \to FSet$ to finite sets satisfying axioms (G4)–(G6): exact, conservative, and finite- set-valued. By
V.4.1, every fibre functor $F$ is pro- representable, with associated profinite group $\pi = \operatorname{Aut}(F)$ and
equivalence $\mathcal{C} \simeq \mathcal{C}(\pi)$. The terminology: Grothendieck's _fundamental functor_ and the more
transparent _fibre functor_ (suggested in his footnote V.5.1.1) are the same notion. For $\mathcal{C} = \mathcal{C}(S)$,
$F_{a}(X) =$ geometric points of$X$over$a$. File 31, file 32, file 33.

**formally principal homogeneous.** A $Y$-prescheme $X$ with right $G$-action under a $Y$-group scheme `G_Y` such that
the canonical morphism $X \times_{Y} G_{Y} \to X \times_{Y} X$ (combining projection and action) is an **isomorphism**.
Adding "faithfully flat quasi-compact" gives a principal homogeneous space. File 30, V.2.6.

**fundamental groupoid.** For a Galois category $\mathcal{C}$, the connected groupoid $\Gamma$ whose objects are fibre
functors of $\mathcal{C}$ and whose morphisms are isomorphisms of functors. Each object has automorphism group
$\pi_{F} = \operatorname{Aut}(F)$. Two objects are related by a _path class_ $\pi_{F, F'} = Isom(F, F')$, the algebraic
analogue of a homotopy class of paths in topology. For $\mathcal{C}(S)$, the fundamental groupoid is the groupoid of
geometric points of $S$ with morphisms = path classes $\pi_{1}(S; a, a')$. File 32, V.5.7; file 33, V.7.

**fundamental pro-group $\Pi$.** For a Galois category $\mathcal{C}$, the canonical pro-group of $\mathcal{C}$ whose
fibre at any fundamental functor $F$ is $\pi_{F} = \operatorname{Aut}(F)$. Determined up to _unique_ isomorphism (unlike
a fundamental pro-object, which is determined only up to non-canonical isomorphism). File 32, V.5.10. For schemes:
$\Pi^{S}_{1}$ is the fundamental pro-group of the scheme $S$, and its fibre at an ordinary point $s \in S$ deserves the
name $\pi_{1}(S, s)$ (a pro-group over $\kappa(s)$). File 33, V.7.

**fundamental pro-object `P_F`.** For a Galois category $\mathcal{C}$ and a fibre functor $F$, the pro-object of
$\mathcal{C}$ representing $F$: a normalised projective system $(P_{i})_{i \in I}$ with
$F(X) = colim_{i} \operatorname{Hom}(P_{i}, X)$. The "universal cover at $F$" of the final object of $\mathcal{C}$.
Connected, but carries no group structure. Determined up to non-canonical isomorphism. File 31, V.4 step c.

**Galois category.** A category $\mathcal{C}$ equivalent to $\mathcal{C}(\pi)$ for some profinite group $\pi$;
equivalently (V.4.1), a category satisfying axioms (G1)–(G3) and admitting a fibre functor satisfying (G4)–(G6). The
category of finite étale coverings of a connected locally noetherian scheme is a Galois category (file 33, V.7). File
32, V.5.1.

**geometric point (of $S$).** A morphism $a : \operatorname{Spec}(\Omega) \to S$ from the spectrum of an algebraically
closed field $\Omega$. Equivalently: an ordinary point $s \in S$ together with an algebraically closed extension of
$\kappa(s)$. The "geometric base point" for the étale fundamental group. File 33.

**inertia group $G_{i}(x)$.** For a finite group $G$ acting on a prescheme $X$ and a point $x \in X$ with decomposition
group $G_{d}(x)$, the inertia group is the kernel of the action of $G_{d}(x)$ on the residue field $\kappa(x)$:

```text
G_i(x) = { s ∈ G_d(x) : s acts trivially on κ(x) }.
```

Trivial inertia at every $x \in X$ is V.2.3's criterion for $X \to X / G$ to be étale. File 30.

**monodromy.** For a topological covering $p : E \to B$, the action of $\pi^{top}_{1}(B, b_{0})$ on the fibre
$p^{-1}(b_{0})$ defined by path lifting: $[\gamma] \cdot e = \tilde{\gamma}(1)$ where $\tilde{\gamma}$ is the unique
lift of $\gamma$ starting at $e$. The algebraic analogue: the action of $\pi_{1}(S, a)$ on $F_{a}(X)$ for an étale
covering $X / S$. File 28.

**multi-Galois category.** A category equivalent to a _product_ of Galois categories $\prod_{i} \mathcal{C}(\pi_{i})$.
The natural setting for $\mathcal{C}(S)$ when $S$ is not connected: $\mathcal{C}(S) \simeq \prod_{i} \mathcal{C}(S_{i})$
with $S_{i}$ the connected components. File 33, V.9.

**path class.** For two fibre functors $F, F'$ of a Galois category, an element of
$\operatorname{Hom}(F, F') = Isom(F, F')$ (every morphism between fibre functors is automatically an iso, by V.5.7). The
algebraic analogue of a homotopy class of paths between two base points in topology. The collection of path classes
between geometric points of $S$ makes the **fundamental groupoid** of $S$. File 32, V.5.7; file 33, V.7.

**principal covering (with Galois group $G$).** A $Y$-prescheme $X$ with right $G$-action satisfying the equivalent
V.2.6 conditions: (i) finite over $Y$, $Y = X / G$, trivial inertia; (ii) trivialised by a faithfully flat quasi-
compact base change; (iii) trivialised by a finite étale surjective base change; (iv) formally principal homogeneous +
faithfully flat + quasi-compact. The algebraic analogue of a finite Galois étale cover with deck group $G$. File 30,
V.2.8.

**profinite completion.** For an abstract group $G$, the profinite group `Ĝ = lim_{N ⊲ G, [G : N] < ∞} G / N`, the
projective limit over all finite-index normal subgroups. Universal property: `Hom_{cts}(Ĝ, Π) = Hom(G, Π)` for $\Pi$
profinite. Examples: $\hat{\mathbb{Z}}$, $\hat{F}_{n}$. The topological counterpart $\hat{\pi}^{top}_{1}(B, b_{0})$ of
$\pi^{top}_{1}(B, b_{0})$ classifies _finite_ covers of $B$. File 29.

**profinite group.** A topological group that is Hausdorff, compact, and totally disconnected; equivalently, a
projective limit of finite (discrete) groups. Examples: $\hat{\mathbb{Z}}$, $\mathbb{Z}_{p}$,
$\operatorname{Gal}(K^{sep} / K)$, $\hat{F}_{n}$. The values of $\operatorname{Aut}(F)$ for fibre functors of Galois
categories are profinite by construction (V.4.1, file 31). File 29.

**pro-object (of a category).** A projective system $(P_{i})_{i \in I}$ of objects of $\mathcal{C}$ indexed by a
filtered ordered set $I$, viewed as a representative of the functor
$X \mapsto colim_{i} \operatorname{Hom}(P {}_{i}, X)$. The category $Pro-\mathcal{C}$. A set-valued functor
$F : \mathcal{C} \to FSet$ is **pro-representable** when there is a pro-object $P$ with
$F(X) \simeq \operatorname{Hom}_{Pro-\mathcal{C}}(P, X)$. Strict pro-representability (file 29) is the form Grothendieck
uses in V.4 step c. File 29.

**strict epimorphism.** A morphism $u : X \to Y$ such that the fibre product $X \times_{Y} X$ exists and
`X ⇉ X ×_Y X → Y` is a coequaliser: every $\psi : X \to Z$ with $\psi \circ p_{1} = \psi \circ p_{2}$ factors uniquely
through $u$. In `Set`, every epimorphism is strict; in topological spaces, strict epis are the quotient maps. Used in
axiom (G3) of file 31 and verified for surjective finite étale morphisms in V.3.6 (file 31). File 29.

**strict monomorphism.** Dual of strict epimorphism: $u : X \to Y$ such that the push-out $X \amalg_{u} Y \amalg_{u} X$
exists and `Y → Y ⨿_u Y ⇇ Y` is an equaliser. Closed-and-open immersions of schemes are strict monomorphisms; this
powers V.3.6 (file 31). File 29.

**topological fundamental group $\pi^{top}_{1}(B, b_{0})$.** For a path- connected topological space $B$ and a base
point $b_{0} \in B$, the group of homotopy classes of loops at $b_{0}$, with multiplication = concatenation. The
algebraic counterpart for schemes is $\pi_{1}(S, a)$ after profinite completion. Examples:
$\pi^{top}_{1}(S^{1}) = \mathbb{Z}$, $\pi^{top}_{1}(S^{1} \vee S^{1}) = F_{2}$. File 28.

**universal cover (topological).** For a connected, locally arcwise connected, locally simply connected $B$, the unique
(up to isomorphism) connected covering $\tilde{p} : \tilde{B} \to B$ with $\tilde{B}$ simply connected. The
deck-transformation group $\operatorname{Aut}(\tilde{B} / B) = \pi^{top}_{1}(B, b_{0})$. The algebraic analogue is the
_fundamental pro-object_ $P$ of file 31. File 28.

## Fibred categories, sites, and descent (files 34–38)

These terms appear in the rewrite of Exposé VI (files 34–38). File 34 introduces the categorical / topological prep
(Grothendieck topologies, sheaves on a site, 2-categories, pseudofunctors); files 35–37 develop the abstract framework
of fibred categories, cleavages, and pseudofunctors; file 38 closes with the descent isomorphism (VI.12.1).

**2-category.** A category with extra structure: between any two objects `A, B` is not just a set but a _category_
$\mathcal{K}(A, B)$ of 1-cells (functors-like) and 2-cells (natural-transformation- like), with horizontal and vertical
compositions satisfying the interchange law. The motivating example is `Cat`: objects are small categories, 1-cells are
functors, 2-cells are natural transformations. File 34.

**base change (in `Cat`).** For a functor $\lambda : \mathcal{E}' \to \mathcal{E}$ of 1-categories, the operation
$\mathcal{F} \mapsto \lambda*(\mathcal{F}) := \mathcal{F} \times_{\mathcal{E}} \mathcal{E}'$ sending
$\mathcal{E}$-categories to $\mathcal{E}'$-categories. A right adjoint to "restrict the base via $\lambda$". Compatible
with all categorical limits. File 35, VI.3.

**bi-fibred category.** An $\mathcal{E}$-category that is both fibred (file 36, VI.6.1) and co-fibred (file 37, VI.10).
Equivalently: prefibred + co-prefibred + (file 37, VI.10.1) the $c_{f, g}$ isomorphism is automatic. The natural setting
for adjoint pairs $f^{*} \dashv f_{*}$. The bi-fibred example for schemes: `(QCoh(–), pull-back, push-forward)` over
$(Sch / S_{0})$. File 37.

**cartesian functor.** An $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ between $\mathcal{E}$-categories that
sends cartesian morphisms (file 35, VI.5.1) to cartesian morphisms. The category
$\operatorname{Hom}_{cart}(\mathcal{F}, \mathcal{G})$ of cartesian functors is a full subcategory of
$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{F}, \mathcal{G})$. Cartesian functors are those that "respect the
inverse-image structure" — they commute with $f^{*}$ up to canonical iso. File 35, VI.5.2.

**cartesian morphism.** A morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$ over $f : T \to S = p(\alpha)$ such that for
every $\eta' \in Ob \mathcal{F}_{T}$, the precomposition map
$\operatorname{Hom}_{T}(\eta', \eta) \to \operatorname{Hom}_{f}(\eta', \xi)$ is bijective. The universal-property
formulation of "the inverse image $f^{*}(\xi)$ of $\xi$ along $f$". When such an $(\eta, \alpha)$ exists, $\eta$ is
unique up to canonical $T$-iso. File 35, VI.5.1.

**cleavage (clivage).** For a prefibred $\mathcal{E}$-category $\mathcal{F}$, an _explicit choice_ of inverse-image
functor $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ for every $f : T \to S$, together with chosen cartesian morphisms
$\alpha_{f}(\xi) : f^{*}(\xi) \to \xi$. Equivalently (file 36): a subset $K \subset Fl(\mathcal{F})$ of _transport
morphisms_, exactly one over each $(f, \xi)$. Cleavages exist iff $\mathcal{F}$ is prefibred; they are not canonical.
File 36, VI.7.1.

**cloven category.** An $\mathcal{E}$-category equipped with a chosen cleavage. **Normalised cloven category**: cleavage
with $(id_{S})^{*} = id_{\mathcal{F}_{S}}$ and $\alpha_{id_{S}}(\xi) = id_{\xi}$. The data of a normalised cloven
category is equivalent to that of a normalised pseudofunctor $\mathcal{E}^{\circ} \to Cat$ (file 37, VI.8). File 36,
VI.7.1.

**co-cartesian morphism.** Dual of cartesian: a morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$ over $f : T \to S$
such that for every $\xi' \in Ob \mathcal{F}_{S}$, the post-composition map
$\operatorname{Hom}_{S}(\xi, \xi') \to \operatorname{Hom}_{f}(\eta, \xi')$ is bijective. Defines the **direct image**
$f_{*}(\eta)$. File 37, VI.10.

**co-fibred category.** An $\mathcal{E}$-category $\mathcal{F}$ such that $\mathcal{F}^{\circ}$ is fibred over
$\mathcal{E}^{\circ}$. Equivalently: every $f : T \to S$ admits direct images ($f_{*}$ exists) and composites of
co-cartesian morphisms are co-cartesian. File 37, VI.10.

**coherence isomorphism $c_{f, g}$.** For a cleavage of an $\mathcal{E}$-category and composable $g : U \to T$,
$f : T \to S$ in $\mathcal{E}$, the natural transformation $c_{f, g} : g^{*} f^{*} \Longrightarrow (fg)^{*}$ of functors
$\mathcal{F}_{S} \to \mathcal{F}_{U}$ arising from the universal property of the cartesian morphism $\alpha_{fg}$. By
VI.7.2, $\mathcal{F}$ is fibred iff every $c_{f, g}$ is a _natural isomorphism_. File 36, VI.7.

**descent datum.** Given a cloven $\mathcal{E}$-category $\mathcal{F}$ and a morphism $f : T \to S$ in $\mathcal{E}$, a
_descent datum on a fibre-wise object_: a pair $(\eta, \phi)$ with $\eta \in Ob \mathcal{F}_{T}$ and $\phi$ an
isomorphism between two pull-backs of $\eta$ to a triple-overlap satisfying the cocycle condition. In SGA VI's general
form (VI.12), descent data are objects of the category $\mathcal{H}(\mathcal{F}, \mathcal{C})$ of fibre-wise functors
plus coherence. The geometric form lives in Exposés VIII–IX. File 38, VI.12.

**descent isomorphism.** The categorical statement (VI.12.1): for a cloven $\mathcal{E}$-category $\mathcal{F}$ and any
target category $\mathcal{C}$, the category $\operatorname{Hom}(\mathcal{F}, \mathcal{C})$ of functors out of
$\mathcal{F}$ is canonically isomorphic to the category $\mathcal{H}(\mathcal{F}, \mathcal{C})$ of fibre-wise data plus
cocycle. The categorical core of all later geometric descent statements. File 38.

**direct image (in a fibred category).** For a co-prefibred $\mathcal{E}$-category $\mathcal{F}$ and $f : T \to S$,
$\eta \in Ob \mathcal{F}_{T}$, an object $f_{*}(\eta) \in Ob \mathcal{F}_{S}$ together with a co-cartesian $f$-morphism
$\eta \to f_{*}(\eta)$. When $\mathcal{F}$ is bi-fibred, $f_{*}$ is left adjoint to $f^{*}$. File 37, VI.10.

**$\mathcal{E}$-category.** A category $\mathcal{F}$ equipped with a _projection functor_
$p : \mathcal{F} \to \mathcal{E}$. Synonym: _category over $\mathcal{E}$_. The prototypical examples: $(Sch / S)$
(slice), $Ar(\mathcal{E})$ (arrow category, file 35–38 worked example), `QCoh` (file 34 module C). File 35, VI.2.

**$\mathcal{E}$-equivalence.** An $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ of $\mathcal{E}$-categories
satisfying the four equivalent conditions of VI.4.2 (file 35): admits an $\mathcal{E}$-quasi-inverse, equivalence on
every fibre, an underlying equivalence with fibre-wise equivalences, etc. _Not_ every equivalence of underlying
categories is an $\mathcal{E}$-equivalence; the gap is closed by transportability (VI.4.4). File 35, VI.4.3.

**fibre category $\mathcal{F}_{S}$.** For an $\mathcal{E}$-category $(\mathcal{F}, p)$ and $S \in Ob \mathcal{E}$, the
subcategory $\mathcal{F}_{S} = p^{-1}(S) \subset \mathcal{F}$ of objects over $S$ and morphisms over $id_{S}$ (i.e.
$S$-morphisms). Canonically $\mathcal{F}_{S} \cong \mathcal{F} \times_{\mathcal{E}} {S}$. File 35, VI.4.

**fibred category.** An $\mathcal{E}$-category $\mathcal{F} \to \mathcal{E}$ satisfying: (Fib I) every morphism of
$\mathcal{E}$ admits inverse images, and (Fib II) composites of cartesian morphisms are cartesian. Fib I alone is
**prefibred**. The cleavage of a fibred category yields a coherent system of inverse-image functors with invertible
coherence isomorphisms $c_{f, g}$ (file 36, VI.7.2). Equivalently (file 37): a normalised pseudofunctor
$\mathcal{E}^{\circ} \to Cat$. File 36, VI.6.1.

**fibred in groupoids.** An $\mathcal{E}$-category in which _every_ morphism is cartesian. Equivalently: a fibred
category whose fibres $\mathcal{F}_{S}$ are groupoids. The natural setting for moduli problems (the fibres
$\mathcal{F}_{S}$ parametrise families of objects up to isomorphism, with no non-invertible morphisms allowed). File 36,
VI.6.1.

**Grothendieck topology.** On a category $\mathcal{E}$ (with fibre products), an assignment to each object $S$ of a
class of **covering families** ${U_{i} \to S}_{i}$ satisfying isomorphism + stability under base change + transitivity.
A category equipped with a Grothendieck topology is a **site**. The five sites on $(Sch / S_{0})$: Zariski ⊂ Nisnevich ⊂
étale ⊂ fppf ⊂ fpqc. File 34.

**inverse image (in a fibred category).** For a prefibred $\mathcal{E}$-category $\mathcal{F}$ and $f : T \to S$,
$\xi \in Ob \mathcal{F}_{S}$, an object $f^{*}(\xi) \in Ob \mathcal{F}_{T}$ together with a cartesian $f$-morphism
$\alpha_{f}(\xi) : f^{*}(\xi) \to \xi$. Unique up to canonical $T$-iso. The naming via a cleavage gives the
inverse-image _functor_ $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$. File 35, VI.5.1.

**normalised cleavage.** A cleavage with $(id_{S})^{*} = id_{\mathcal{F}_{S}}$ and $\alpha_{id_{S}}(\xi) = id_{\xi}$.
Every cleavage is equivalent to a normalised one. The normalised case is what corresponds bijectively to (normalised)
pseudofunctors $\mathcal{E}^{\circ} \to Cat$ (file 37, VI.8). File 36, VI.7.1.

**pentagon identity (for pseudofunctors).** For a pseudofunctor $\varphi : \mathcal{E}^{\circ} \to Cat$ and composable
`f, g, h` in $\mathcal{E}$, the equality $c_{f, gh} \circ (h^{*} * c_{g, h}) = c_{fg, h} \circ (c_{f, g} * h^{*})$ of
natural transformations $h^{*} g^{*} f^{*} \Longrightarrow (fgh)^{*}$. The 2-categorical incarnation of associativity.
By Mac Lane's coherence theorem ([`mac-lane-coherence`](appendix-black-boxes.md#mac-lane-coherence)), the pentagon plus
normalisation force every higher-coherence diagram to commute. File 34, file 36, file 37, file 38.

**prefibred category.** An $\mathcal{E}$-category satisfying axiom Fib I: every $f \in Fl(\mathcal{E})$ admits inverse
images. Equivalent to admitting a cleavage. _Not_ automatically fibred — Fib II (composites of cartesians are cartesian)
can fail. File 36, VI.6.1.

**pseudofunctor.** A "weak functor" $\varphi : \mathcal{E}^{\circ} \to Cat$ consisting of a category $\varphi(S)$ for
each $S$, a functor $f^{*} : \varphi(S) \to \varphi(T)$ for each $f : T \to S$, and an _invertible_ coherence 2-cell
$c_{f, g} : g^{*} f^{*} \Longrightarrow (fg)^{*}$ for each composable pair, subject to the pentagon identity and a
normalisation condition. Equivalently: data of a normalised cloven $\mathcal{E}$-category, by file 37, VI.8. The natural
target of the "fibres functor" $S \mapsto \mathcal{F}_{S}$. File 34, file 36, file 37.

**sheaf on a site.** For a site $(\mathcal{E}, \tau)$, a presheaf $F : \mathcal{E}^{\circ} \to Set$ (or `Ab`, `Grp`,
`Cat`, ...) such that for every covering family ${U_{i} \to S}_{i}$ the sequence
`F(S) → ∏_i F(U_i) ⇉ ∏_{i, j} F(U_i ×_S U_j)` is an equaliser. Generalises file 03's Zariski sheaf condition. The
descent isomorphism of file 38 §VI.12 is the categorified analogue. File 34.

**sieve.** For a category $\mathcal{E}$ and $S \in Ob \mathcal{E}$, a sub-presheaf of `Hom_ℰ(–, S)`. Equivalently: a
class $R$ of arrows into $S$ closed under precomposition. Sieves are the formal data of "the covering families" used in
the abstract definition of a Grothendieck topology. File 34.

**site.** A category equipped with a Grothendieck topology (= the topology of sieves generated by a pretopology). The
standard sites on schemes: Zariski, Nisnevich, étale, fppf, fpqc. File 34.

**split category.** A cloven $\mathcal{E}$-category whose coherence isomorphisms $c_{f, g}$ are _identities_ (rather
than just isomorphisms). Equivalently: arises from an honest functor $\mathcal{E}^{\circ} \to Cat$ (no 2-cells). Some
fibred categories admit a splitting, some do not (the obstruction lives in $H^{2}$ for certain group-extension
examples). Fibred categories with rigid fibres always admit a unique splitting. File 37, VI.9.

**transport morphism.** For a cloven $\mathcal{E}$-category, an element of the subset $K \subset Fl(\mathcal{F})$ of
cartesian morphisms naming the cleavage. There is exactly one transport morphism over each pair $(f, \xi)$. The cleavage
is normalised iff identity morphisms are transport morphisms; the cleavage is a _splitting_ iff transport morphisms are
closed under composition (file 37, VI.9). File 36, VI.7.1.

## Faithfully flat descent (files 40–43)

These terms appear in the rewrite of Exposé VIII (files 40–43), the geometric specialisation of the descent isomorphism
VI.12.1 to schemes.

**descent algebra.** When a faithfully flat quasi-compact morphism $g : S' \to S$ has affine source and target with
rings $A \to A'$, a descent datum on an $A'$-module $M'$ is an isomorphism
$\phi : M' \otimes_{A} A' \simeq A' \otimes_{A} M'$ of $A'' = A' \otimes_{A} A'$-modules satisfying the cocycle on
$A'''$. The descended module is then the equaliser $N = { x \in M' : \phi(x \otimes 1) = 1 \otimes x}$, called the
_descended $A$-module_ or the _descent algebra_ when $M'$ carries an algebra structure. File 40, VIII.1.6.

**descent datum (geometric form).** For $g : S' \to S$ and a quasi-coherent module $M'$ (or scheme $X'$, or other
object) on $S'$, an isomorphism $\phi : p^{*}_{1}(M') \simeq p^{*}_{2}(M')$ on $S'' = S' \times_{S} S'$ satisfying the
cocycle condition $p^{*}_{13}(\phi) = p^{*}_{23}(\phi) \circ p^{*}_{12}(\phi)$ on $S'''$. Specialisation of the general
descent datum (file 38) to a single-cover fpqc site. File 40, VIII.1.

**effective descent datum.** A descent datum $(M', \phi)$ is _effective_ when $(M', \phi) \simeq (g^{*}(M), \phi_{M})$
for some object $M$ on $S$ — i.e. when it comes from descent of an honest object below. File 40, VIII.1.3.

**effective epimorphism (in `Sch`).** A morphism $g : S' \to S$ is an _effective epimorphism_ when for every prescheme
$Z$, the diagram `Hom(S, Z) → Hom(S′, Z) ⇉ Hom(S″, Z)` is exact (so $S$ is the coequaliser of the two projections
`S″ ⇉ S′`). A faithfully flat quasi-compact morphism is a _universal effective epimorphism_ (effective epimorphism after
any base change). File 42, VIII.5.3.

**fpqc.** Abbreviation for **f**idèlement **p**lat et **q**uasi-**c**ompact = _faithfully flat and quasi-compact_. The
condition on $g : S' \to S$ under which Theorem VIII.1.1 (descent of quasi-coherent modules) holds and the basis for the
**fpqc topology** on $(Sch / S_{0})$ (file 34 Module A). File 40, VIII §1 preamble.

**fpqc topology.** The Grothendieck topology on $(Sch / S_{0})$ whose covers are finite, jointly surjective families
${T_{i} \to S}$ of flat morphisms with $\amalg T_{i} \to S$ quasi-compact. Largest standard topology on schemes; descent
for quasi-coherent sheaves works in it (Theorem VIII.1.1). File 34, file 40.

**morphism of $\mathcal{F}$-descent.** A morphism $g : S' \to S$ such that the base-change functor
$g^{*} : \mathcal{F}_{S} \to \mathcal{F}_{S'}$ is fully faithful as a functor into descent data — equivalently, the
natural functor $\mathcal{F}_{S} \to \mathcal{F}_{S'}/g$ (= descent data on $S'$ relative to $g$) is fully faithful.
File 40, VIII.1.1.

**morphism of effective $\mathcal{F}$-descent.** Stronger than the above: $g^{*}$ is moreover essentially surjective on
descent data, i.e. every descent datum is effective. Equivalent to $g^{*}$ being an equivalence of categories. File 40,
VIII.1.3; file 41, VIII.2.1; file 42, VIII.5.2; file 43, VIII.7.

**norm (of a section under a finite locally free morphism).** For $f : X \to S$ finite locally free of constant rank
$r$, multiplication by $s \in \Gamma(X, \mathcal{O}_{X})$ is an $\mathcal{O}_{S}$-linear endomorphism of
$f_{*}(\mathcal{O}_{X})$; its determinant $N_{f}(s) \in \Gamma(S, \mathcal{O}_{S})$ is the _norm_. Compatible with base
change. Used to produce saturated open neighbourhoods in the finite-locally- free effectivity criterion VIII.7.6. File
43, VIII.7.6. See \[`ega-ii-norm-finite-locally-free`\](appendix-black- boxes.md#ega-ii-norm-finite-locally-free).

**quasi-affine morphism.** A morphism $f : X \to S$ such that for every affine open $U \subset S$, $f^{-1}(U)$ is
isomorphic to an open subscheme of an affine scheme (and is quasi-compact). Equivalently (EGA II 5.1.1):
$\mathcal{O}_{X}$ is ample relative to $f$. Descends along faithfully flat quasi-compact morphisms (VIII.5.9). File 42.

**quasi-compact morphism.** A morphism $f : X \to Y$ such that the inverse image of every quasi-compact open of $Y$ is
quasi-compact in $X$. For schemes: every affine open $U \subset Y$ has $f^{-1}(U)$ a finite union of affine opens of
$X$. The finite-cover hypothesis used to reduce most descent arguments to affine bases. File 40, VIII §1 preamble.

**radicial morphism.** A morphism $f : X \to Y$ that is universally injective with purely inseparable residue field
extensions. Equivalently: $f$ is injective on geometric points and, for every $y \in Y$ and $x \in X$ over $y$, the
residue extension $\kappa(y) \subset \kappa(x)$ is purely inseparable. Under faithful flatness and quasi-compactness,
radicial $g$ makes every descent datum effective (VIII.7.5). File 43.

**saturated subset (under a descent datum).** A subset $U' \subset X'$ is _saturated_ (or _stable under the descent
datum_) when $q^{-1}_{1}(U') = q^{-1}_{2}(U')$ in $X''$, equivalently when the descent datum restricts to a descent
datum on $U'$. The open-cover effectivity criterion VIII.7.2: a descent datum is effective iff $X'$ has a cover by
saturated open subsets whose induced descent data are effective. File 43, VIII.7.2.

**universal effective epimorphism.** A morphism $g : S' \to S$ which is an effective epimorphism (see above) and remains
so after any base change $S_{1} \to S$. Equivalent for a faithfully flat quasi-compact morphism by VIII.5.3 to being a
universally effective morphism of `Sch`-descent. File 42, VIII.5.3.

## Descent of étale morphisms and the fundamental group (files 44–47)

**submersive morphism.** A morphism $g : S' \to S$ that is **surjective** and makes $S$ carry the **quotient topology**
from $S'$: a subset $U \subset S$ is open iff $g^{-1}(U) \subset S'$ is open. The schematic word for "quotient map" in
topology. File 44, IX.2.1.

**universally submersive morphism.** A morphism $g : S' \to S$ such that every base change
$g_{T} : S' \times_{S} T \to T$ is submersive. Every proper surjective morphism, every faithfully flat quasi-compact
morphism, and every surjective open or closed morphism is universally submersive. The hypothesis under which IX.3
establishes descent of étale morphisms. File 44, IX.2.1; file 45, IX.3.

**graph (of an $S$-morphism with étale target).** For $Y / S$ étale and $f : X \to Y$ an $S$-morphism, the subset
$\Gamma_{f} = {(x, f(x))} \subset X \times_{S} Y$. By IX.1.6, $\Gamma_{f}$ is an open subset of $X \times_{S} Y$ whose
first projection $\Gamma_{f} \to X$ is radicial and surjective; conversely every such open subset is the graph of a
unique $S$-morphism $X \to Y$. The single lemma that makes file 45 §IX.3 work. File 44, IX.1.6.

**geometrically connected fibres.** A morphism $g : S' \to S$ has _geometrically connected fibres_ when, for every
$s \in S$ and every field extension $K / \kappa(s)$, the base change $g^{-1}(s) \otimes_{\kappa(s)} K$ is connected. The
key hypothesis under which the descent functor $g^{*} : \mathcal{F}_{S} \to \mathcal{F}_{S'}$ (for the fibred category
of finite étale coverings) is fully faithful; equivalently, under which the homomorphism $\pi_{1}(S') \to \pi_{1}(S)$ is
surjective. File 45, IX.3.4; file 47, IX.6.

**geometrically trivial covering.** Given $X \to S$ proper surjective with geometrically connected fibres, an étale
covering $X' \to X$ is _geometrically trivial_ when its fibre $\bar{X}_{0}' \to \bar{X}_{0}$ over a geometric point of
$\bar{X}_{0}$ (equivalently, over every fibre of $X \to S$) is _completely decomposed_, i.e. isomorphic to a disjoint
union of copies of $\bar{X}_{0}$. The criterion for $X'$ to come from an étale $S'$ via pullback. File 47, IX.6.2,
IX.6.7.

**Stein factorisation.** For a proper morphism $f : X \to S$ of locally noetherian preschemes, the canonical
factorisation $f : X \to S' \to S$ with $S' = \operatorname{Spec}_{S}(f_{*}(\mathcal{O}_{X}))$, $X \to S'$ proper with
geometrically connected fibres and satisfying $(X \to S')_{*}(\mathcal{O}_{X}) = \mathcal{O}_{S'}$, and $S' \to S$
finite. The universal way to "factor out the connected-fibre content" of a proper morphism. File 47, IX.6.5–6.6. See
[`ega-iii-stein-factorisation`](appendix-black-boxes.md#ega-iii-stein-factorisation).

**topological invariance of the étale site.** The theorem (IX.4.10) that for $g : S' \to S$ finite radicial surjective
(equivalently, a _universal homeomorphism_), the functor $X \mapsto X \times_{S} S'$ is an **equivalence** from étale
$S$-preschemes to étale $S'$-preschemes. Étale topology cannot distinguish $S$ from any finite radicial cover; in
particular Frobenius and nilpotent thickenings are invisible to the étale fundamental group. File 45, IX.4.10. The
black-box row [`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) — used since file 06 — is unpacked here.

**galoisian-type group generated by ${\pi_{i}}$ and ${g_{j}}$ subject to relations.** The inverse limit of the quotients
of the (abstract) free product $(\amalg \pi_{i}) * F(g_{j}) / \langle relations\rangle$ by subgroups of finite index
whose inverse images in each $\pi_{i}$ are open. Equivalently, the completion of the relevant free product / quotient in
the topology of finite-quotient subgroups. The Seifert–van-Kampen description of $\pi_{1}(S, a)$ in IX.5.1 expresses it
as a galoisian-type group of this form. File 46, IX.5.1.

**pinching (of a scheme along a finite set of points).** Given a scheme $S$ and a discrete set $T \subset S$ together
with a choice of identifications of geometric points of $S$ lying over each $t \in T$, the _pinched_ scheme
$S_{pinched}$ is the universal scheme to which $S$ admits a morphism collapsing the chosen geometric points. Pinching
$\mathbb{P}^{1}$ along two geometric points produces the nodal cubic; the étale fundamental group of the result is the
free profinite group on one generator. File 46, IX.5.4–5.

**symmetric power of a scheme.** For $X / k$ and $n \geq 2$, the $n$-th symmetric power
$Sym^{n}(X) = X^{n} / \mathfrak{S}_{n}$ where $\mathfrak{S}_{n}$ permutes coordinates. For $X$ proper connected over an
algebraically closed field, $\pi_{1}(Sym^{n} X) = \pi_{1}(X)^{ab}$ (the abelianisation of $\pi_{1}(X)$); this is one of
the striking consequences of the IX.5.8 quotient-by-finite-group formula. File 46, IX.5.8.

**cokernel (in the category of Galois-type groups).** For two morphisms $f_{1}, f_{2} : H \to G$ of Galois-type groups,
the _cokernel_ is the quotient of $G$ by the closed normal subgroup generated by $\{f_{1}(h) f_{2}(h)^{-1} : h \in H\}$,
equipped with its quotient topology in the category of Galois-type groups. The π₁ formulation of IX.5.6: for $g$
universally submersive with geometrically connected fibres, $\pi_{1}(S, a)$ is the cokernel of
`(p_1^*, p_2^*) : π₁(S″, s″) ⇉ π₁(S′, s′)`. File 46, IX.5.6.

**fundamental exact sequence.** For $X \to S$ proper surjective with geometrically connected fibres, $s \in S$, and a
geometric point `ā` of the geometric fibre $\bar{X}_{0} = X \otimes_{\kappa(s)} \bar{\kappa(s)}$ over $s$, the canonical
exact sequence

```text
1  →  π₁(X̄_0, ā)  →  π₁(X, a)  →  π₁(S, b)  →  1
```

where $a$ is the image of `ā` in $X$ and $b$ its image in $S$. The fundamental theorem of file 47 §IX.6. File 47,
IX.6.1.

## Specialization of the fundamental group (files 48–51)

**separable scheme over a field.** A prescheme $X$ over a field $k$ is *separable* if for every field extension $K / k$,
the base change $X \otimes_{k} K$ is **reduced**. Equivalently, the residue fields $\kappa(x)$ at generic points of
irreducible components of $X$ are separable extensions of $k$. Over a perfect $k$, separable = reduced. File 48, X.1.1.

**separable morphism.** A morphism $f : X \to Y$ is *separable* if $f$ is **flat** and every fibre
$X_{y} = X \otimes_{Y} \kappa(y)$ is separable over $\kappa(y)$ in the above sense. Base change preserves separability;
the composite with an étale morphism on the upper side preserves separability. The right vocabulary for "a morphism
whose fibres are honest geometric pieces with no inseparable hidden structure." File 48, X.1.1.

**Stein factorisation refined to étale.** EGA III §7.8.10(i): for $f : X \to Y$ proper separable with $Y$ locally
noetherian, the Stein factor $Y' = \operatorname{Spec}_{Y}(f_{*}\mathcal{O}_{X})$ over $Y$ is **finite étale**, not
merely finite. Upgrades the general Stein factorisation (file 47, IX.6) to a covering in the étale sense. File 48,
X.1.2. See [`ega-iii-7-stein-finite-etale`](appendix-black-boxes.md#ega-iii-7-stein-finite-etale).

**homotopy exact sequence (for proper separable).** For $f : X \to Y$ proper separable with $Y$ locally noetherian and
connected, $f_{*}\mathcal{O}_{X} = \mathcal{O}_{Y}$ (equivalently, geometrically connected fibres), and geometric points
$\bar{a} \in \bar{X}_{y}$, $a \in X$, $b \in Y$, the sequence

```text
π₁(X̄_y, ā) → π₁(X, a) → π₁(Y, b) → e
```

is exact at $\pi_{1}(X, a)$ and at $\pi_{1}(Y, b)$. Surjectivity at $\pi_{1}(Y, b)$ is (file 45) IX.3.4 + (file 33)
V.6.9; exactness at $\pi_{1}(X, a)$ is the descent statement X.1.3 made via the (file 33) V.6 dictionary. **Not**
left-exact: injectivity of the leftmost arrow would require an algebraic-geometric analogue of $\pi_{2}$ of the base,
which is unavailable. File 48, X.1.4.

**constant family of coverings.** A family ${X_{y}' \to X}_{y \in Y(k)}$ of étale coverings of $X$ parametrised by the
$k$-rational points of a connected scheme $Y$ is *constant* if all members are pairwise isomorphic as étale
$X$-coverings. Equivalently: the étale $(X \times Y)$-covering whose fibre at each $y \in Y(k)$ realises the family is
constant. The slogan: families of étale coverings of a proper scheme (or parametrised by a proper scheme) over an
algebraically closed field are constant. File 48, X.1.9.

**Artin–Schreier family.** In characteristic $p > 0$, the family $B_{s} = k[t, s][x] / (x^{p} - x - st)$ over
$\operatorname{Spec}(k[t, s]) = \mathbb{A}^{2} {}_{k}$. For each fixed $s \neq 0$, $B_{s}$ defines a non-trivial
$\mathbb{Z}/p$-cover of $\mathbb{A}^{1}_{k}$; for distinct $s_{0} \neq s_{1}$, the covers are non-isomorphic. Hence the
family is *non-constant*, contradicting the analogue of X.1.9 over a non-proper base — Lang–Serre's counterexample to
dropping properness. File 48, X.1.10.

**specialization morphism on $\pi_{1}$.** For $f : X \to Y$ proper separable with $Y$ locally noetherian and `y₀ ⤳ y₁` a
specialisation in $Y$ (i.e. $y_{0} \in \mathrm{cl}(\{y_{1}\})$), the canonical homomorphism

```text
sp : π₁(X̄_{y₁}, ā₁) → π₁(X̄_{y₀}, ā₀)
```

defined up to inner automorphism of $\pi_{1}(X, a_{0})$ and depending only on the path-class choice. Construction via a
commutative diagram of two homotopy exact sequences (file 48, X.1.4) on the closed and generic fibres, with the
right-hand vertical arrows isomorphisms. File 49, X.2.3–2.4.

**upper semicontinuity of fibre $\pi_{1}$.** Under proper separable hypotheses, the specialisation morphism `sp` is
**surjective**: $\pi_{1}(\bar{X}_{y_{0}})$ is a quotient of $\pi_{1}(\bar{X}_{y_{1}})$. The drop along a specialisation
can be strict (degenerate elliptic curves drop $\hat{\mathbb{Z}}^{2}$ to $\hat{\mathbb{Z}}$, $e$, or $e$; M. Artin's
unpublished counterexample (file 49, X.2.5) shows even smooth proper families exhibit non-flat-local-system behaviour).
File 49, X.2.3–2.5.

**transcendental method.** For $X_{0} / k$ proper smooth connected of genus $g$ over an algebraically closed $k$ of char
0, compute $\pi_{1}(X_{0})$ by reducing
`k$ to a subfield of`ℂ`(via X.1.8 algebraic-closure invariance), then comparing`π₁^ét(X₀ ⊗
ℂ)`with the **profinite completion** of the topological fundamental group of the associated complex analytic surface of genus`g`. The latter has the **surface presentation** with`2g\`
generators and one commutator relation. File 50, X.2.6.

**Witt-vector lift of a smooth proper curve.** For $X_{0} / k$ smooth proper connected of genus $g$ over an
algebraically closed $k$ of char $p > 0$, the lift $X / W(k)$ over the Witt ring (SGA 1 III.7.4, gentle in file 22) is a
smooth proper curve of the same genus, with closed fibre $X_{0}$ and generic fibre $X_{K} = X \otimes K$ smooth proper
of dimension 1 and genus $g$ (by Euler–Poincaré invariance). The transcendental method applied to
`X_K$ then descends via X.2.3 to give a presentation of`π₁(X₀)`. File 50, X.2.6. See [`witt-vectors-lifting-smooth-curves\`\](appendix-black-boxes.md#witt-vectors-lifting-smooth-curves).

**prime-to-$p$ completion $\pi_{1}(X)^{(p)}$.** For a profinite group $G$ and a prime $p$, the *prime-to-$p$ completion*
is the quotient of $G$ by the closed normal subgroup generated by a $p$-Sylow subgroup. Equivalently: the inverse limit
of those finite quotients of $G$ of order coprime to $p$. For a proper smooth connected curve $X_{0} / k$ over an
algebraically closed $k$ of char $p$, the continuity theorem X.3.8 gives a clean description of $\pi_{1}(X_{0})^{(p)}$
purely algebraically, while the full $\pi_{1}(X_{0})$ remains opaque. File 51, X.3.9–3.10.

**decomposition subgroup $G_{d}$.** For a Galois extension $L / K$ of fraction fields of complete DVRs and a maximal
ideal $\mathfrak{m}'$ of the normalisation $V' \subset L$, the subgroup
`G_d = \{ σ ∈ \mathrm{Gal}(L/K) : σ(𝔪′) = 𝔪′ \}$ — the elements that preserve the chosen prime. Acts on the residue extension`k′
= V′/𝔪′$. File 51, X.3.6.

**inertia subgroup $G_{i}$.** Within `G_d$, the subgroup of elements that act trivially on`k′$. Order equals the
*ramification index* `e_{L/K}$ of \`L / K$ at the chosen prime. Cyclic in the tame case. File 51, X.3.6.

**tame ramification.** A Galois extension `L / K$ over a complete DVR is *tamely ramified* if`|G_i|$ is coprime to the
residue characteristic `p$. In the tame case, `G_i ↪ k′^×$ canonically, so`G_i$ is cyclic of order coprime to
`p$. Automatically the case in characteristic 0. Typical tame example: $L = K[t]/(t^{n} - u)$ for$u$ a uniformiser of
`V$ and `n$ coprime to`p$. File 51, X.3.6. See
[`serre-local-fields-tameness`](appendix-black-boxes.md#serre-local-fields-tameness).

**Abhyankar's lemma.** Let `V$ be a DVR with fraction field`K$. Let `L, K′$ be tamely ramified Galois extensions of `K$
over`V$ with inertia groups of orders `m, n$. Let $L'$ be a composite extension. If$m$ is a multiple of `n$, then `L′$
is **unramified** over the localisations of the normal closure of`V$ in `K′$. The composite of two tamely ramified
extensions with inertia orders dividing each other becomes unramified. File 51, X.3.6.

**Zariski–Nagata purity of the branch locus.** For `f : X → Y$ quasi-finite dominant with`X$ normal and `Y$ regular
locally noetherian, the branch locus is either everything or **pure of codimension 1** in `X$. Equivalently: étale
coverings of`Y$ extend uniquely across any closed subscheme of `Y$ of codimension
`≥ 2$. Proved generally in **SGA 2 X.3.4**; the dim-2 case is proved inline in file 51 via depth-`≥
2` + freeness over a regular dim-2 local ring. File 51, X.3.1–3.3. See [`zariski-nagata-purity\`\](appendix-black-boxes.md#zariski-nagata-purity).

**birational invariance of $\pi_{1}$.** For `X, Y$ proper regular`k$-schemes and `f : X ⤏ Y$ a birational map, the
induced homomorphism `π₁(X, a) → π₁(Y, b)$ is an isomorphism. Equivalently:`π₁$ of a smooth proper variety is a
*birational invariant*. File 51, X.3.4.

**continuity theorem (for proper smooth).** For `f : X → Y$ proper smooth with geometrically connected fibres,`Y$
locally noetherian, and `y₀ ⤳ y₁$ in `Y$, the specialisation morphism`sp : π₁(X̄\_{y₁}) → π₁(X̄\_{y₀})$ is **surjective**
and induces an **isomorphism** on the prime-to-`p$ completions $\pi^{(p)}_{1}$, where$p = \\mathrm{char}(κ(y₀))$. The
prime-to-`p$ étale fundamental group is **rigid** under specialisation in a proper smooth family. File 51, X.3.8.

**anabelian (pointer entry).** A theorem in *anabelian geometry* asserts that an arithmetic-geometric object (e.g. a
hyperbolic curve over a number field) is determined up to isomorphism by its étale fundamental group, possibly with
extra structure (a section, an outer Galois action, etc.). Tamagawa's solvable specialisation theorem (file 50, X.2.14)
is an anabelian rigidity statement: solvable potential good reduction of a curve over a complete DVR forces the curve to
be constant. The broader framework is surveyed in Nakamura–Tamagawa–Mochizuki *Sugaku Expositions* 14 (2001) and
Szamuely §6.7. File 50, X.2.14.

## Examples and complements (files 52–56)

**rational variety.** A proper integral $k$-scheme $X$ whose function field $k(X)$ is purely transcendental over $k$,
i.e. $k(X) \simeq k(t_{1}, \cdots, t_{r})$ for $r = \dim X$. Equivalently, $X$ is birational to $\mathbb{P}^{r}_{k}$.
File 52, XI.1.2.

**unirational variety (weak vs strong).** A proper integral $k$-scheme $X$ whose function field $k(X)$ is contained in a
purely transcendental extension $K' = k(t_{1}, \cdots, t_{r})$. **Weakly unirational**: the embedding can be
inseparable. **Strongly unirational**: the embedding is separable, equivalently the dominant rational
$f : \mathbb{P}^{r} \dashrightarrow X$ is generically smooth. In characteristic 0 the two notions coincide; in char
$p > 0$ strongly ⊊ weakly. File 52, XI.1.3, XI.1.4.2.

**rationally connected variety.** A normal integral projective $k$-variety $V$ admitting
$F : T \times \mathbb{P}^{1} \to V$ with the two-point evaluation
$T \times \mathbb{P}^{1} \times \mathbb{P}^{1} \to V \times V$, $(t, u, u') \mapsto (F(t, u), F(t, u'))$ *dominant*.
Equivalently: any two general points are joined by a rational curve. File 52, XI.1.4.4.

**separably rationally connected variety (sRC).** As above, with the two-point evaluation additionally *generically
smooth*. In char 0, RC = sRC; in char $p > 0$, sRC ⊊ RC. Kollár's theorem (file 52, XI.1.4.5) gives sRC ⇒ trivial
$\pi^{\acute{e}}_{1}t$. File 52, XI.1.4.4.

**abelian variety.** A proper smooth geometrically connected $k$-group scheme. Automatically commutative as a group
scheme; carries a biduality $A^{\vee\vee} \simeq A$ (Mumford TIFR Ch. III). The "richest-π₁" object among proper smooth
varieties of a given dimension. File 53, §XI.2.

**Tate module $T_{\ell}(A)$.** For $A$ an abelian variety of dimension $g$ over algebraically closed $k$, the inverse
limit $T_{\ell}(A) := \lim_{r} {}_{\ell^{r}}A(k)$ along multiplication-by-$\ell$ transition maps. A free
$\mathbb{Z}_{\ell}$-module of rank `2g` when $\ell \neq char(k)$; of rank $\nu \leq g$ (the **$p$-rank**) when
$\ell = p = char(k) > 0$. The adelic version is $T\cdot(A) := \prod_{\ell} T_{\ell}(A) = \lim_{n} {}_{nA}(k)$. File 53,
§§XI.2.3–XI.2.4. See [`tate-module-weil`](appendix-black-boxes.md#tate-module-weil).

**$p$-rank $\nu$ of an abelian variety.** For $A / \bar{k}_{p}$ an abelian variety of dimension $g$, $\nu = \nu(A)$ is
the integer such that ${}_{pA}(\bar{k})$ is a free $\mathbb{Z}/p\mathbb{Z}$-module of rank $\nu$. Equivalently,
$T_{p}(A) \simeq \mathbb{Z}^{\nu}_{p}$. The $p$-rank classifies abelian varieties by their $p$-divisible group;
$\nu = g$ (**ordinary**), $\nu = 0$ (**supersingular**), $0 < \nu < g$ (**intermediate**). File 53, §XI.2.4.

**Cartier dual.** For $G$ a finite commutative group scheme over a base scheme $S$, the Cartier dual is
$D(G) := SheafHom_{S-grp}(G, \mathbb{G}_{m, S})$, itself a finite commutative $S$-group scheme. Cartier duality is
*involutive*: $D(D(G)) \simeq G$. Examples: $D(\mu_{n}) = (\mathbb{Z}/n\mathbb{Z})$,
$D((\mathbb{Z}/n\mathbb{Z})) = \mu_{n}$, $D(\alpha_{p}) = \alpha_{p}$ in char $p$. File 56, §XI.6.5. See
[`cartier-duality`](appendix-black-boxes.md#cartier-duality).

**true fundamental group / Nori fundamental group $\pi^{N}_{1}$.** For $X$ proper connected reduced over a perfect field
$k$ with a rational point $x \in X(k)$, the **Nori fundamental group scheme** is a pro-finite-group-scheme
$\pi^{N}_{1}(X, x)$ over $k$ classifying principal $G$-bundles for $G$ an arbitrary finite (possibly non-étale) group
scheme over $k$. For $X = A$ an abelian variety, $\pi^{N}_{1}(A, 0) = \lim_{n} {}_{nA}$ (as a pro-finite flat group
scheme). Distinct from the étale $\pi_{1}(X, x)$ exactly when $X$ admits principal bundles with infinitesimal structure
group. File 53, §XI.2.5. See [`nori-fundamental-group`](appendix-black-boxes.md#nori-fundamental-group).

**projective cone over $V \subset \mathbb{P}^{r}$.** For $V$ a closed subscheme of $\mathbb{P}^{r}_{k}$, the
**projective cone** $\hat{C}_{V}$ is the projective completion of the affine cone $C_{V} = V(\mathcal{O}_{V}(1))$ —
equivalently, $\hat{C}_{V} = \mathbb{P}(\mathcal{O}_{V} \oplus \mathcal{O}_{V}(1))$ (a $\mathbb{P}^{1}$-bundle over $V$)
with the zero section contracted to a single vertex point $y_{0}$. The contraction $f : X \to \hat{C}_{V}$ (where
$X = \mathbb{P}(\mathcal{O}_{V} \oplus \mathcal{O}_{V}(1))$) is the universal example of a proper morphism that is *not*
separable (fibres are $\mathbb{P}^{1}$ away from $y_{0}$, but $V$ over $y_{0}$). File 54, §XI.3.1.

**principal homogeneous bundle (fpqc sense).** An $S$-prescheme $P$ with a right action of an $S$-group $G$ such that
there exists an fpqc base change $S' \to S$ with $P \times_{S} S' \simeq G \times_{S} S'$ (with $G \times_{S} S'$ acting
on itself by right translation). Equivalently (XI.4.2): $P$ is *formally* principal homogeneous (the map
$P \times_{S} G \to P \times_{S} P$, $(x, g) \mapsto (x, x \cdot g)$, is an isomorphism) and $P \to S$ is itself fpqc.
The set of isomorphism classes is $H^{1}(S, G)$. Generalises the V.2.7 principal-covering notion (file 30) to non-étale
$G$. File 55, §XI.4.1.

**formally principal homogeneous bundle.** An $S$-prescheme $P$ with right $G$-action such that the map
$P \times_{S} G \to P \times_{S} P$, $(x, g) \mapsto (x, x \cdot g)$, is an isomorphism. Weaker than principal
homogeneous: does not require local-triviality. File 55, §XI.4.1.

**Kummer covering of rank $n$.** A principal $\mu_{n, S}$-bundle over $S$, where
$\mu_{n, S} = \operatorname{Spec} \mathcal{O}_{S}[t]/(1 - t^{n})$ is the **Kummer group of rank $n$**. The set of these
is $H^{1}(S, \mu_{n})$. When $n$ is invertible in $\mathcal{O}_{S}$ and $S$ admits a primitive $n$-th root of unity,
$\mu_{n, S} \simeq (\mathbb{Z}/n\mathbb{Z})_{S}$ and the Kummer covering is a principal
$\mathbb{Z}/n\mathbb{Z}$-covering in the classical sense. File 56, §XI.6.1–XI.6.2.

**Artin–Schreier covering.** A principal $(\mathbb{Z}/p\mathbb{Z})_{S}$-bundle over $S$ in characteristic $p$,
classified by $H^{1}(S, \mathbb{Z}/p\mathbb{Z}) \simeq A/wp(A)$ (in the affine case) via the Artin–Schreier exact
sequence $0 \to (\mathbb{Z}/p\mathbb{Z})_{S} \to \mathbb{G}_{a},S \xrightarrow{wp} \mathbb{G}_{a},S \to 0$. The
$p$-power analogue of Kummer theory in characteristic $p$. File 56, §XI.6.4.

**Frobenius morphism $F$.** Over a base $S$ of characteristic $p > 0$ (i.e. $p \cdot \mathcal{O}_{S} = 0$), the
**Frobenius morphism** $F : \mathbb{G}_{a, S} \to \mathbb{G}_{a, S}$ is the group homomorphism sending a section $t$ to
$t^{p}$. More generally, for $G$ a group scheme over $\mathbb{F}_{p}$ and $S \to \operatorname{Spec} \mathbb{F}_{p}$,
$F : G_{S} \to G_{S}$ is the corresponding $p$-th-power morphism. File 56, §XI.6.4.

**Artin–Schreier endomorphism $wp = id - F$.** The difference of the identity and Frobenius on $\mathbb{G}_{a, S}$ in
char $p$. Its kernel is $(\mathbb{Z}/p\mathbb{Z})_{S}$. File 56, §XI.6.4.

**infinitesimal group scheme $\alpha_{p}$.** The kernel of $F : \mathbb{G}_{a} \to \mathbb{G}_{a}$ over a char-$p$ base,
equal to $\operatorname{Spec} \mathcal{O}_{S}[t]/(t^{p})$. A **non-étale** finite locally free group scheme of order
$p$, radical over $S$. Cartier-self-dual: $D(\alpha_{p}) = \alpha_{p}$. Witnesses one of the simplest finite flat group
schemes that is not étale. File 56, §XI.6.5.

**Picard scheme $\operatorname{Pic}_{S/k}$.** For $S \to \operatorname{Spec} k$ a proper morphism with certain
flatness/cohomological hypotheses, the **Picard scheme** is the scheme representing the relative Picard functor
$T \mapsto \operatorname{Pic}(S_{T}) / \operatorname{Pic}(T)$. Its connected component $\operatorname{Pic}^{0}_{S/k}$ is
a $k$-group scheme. For $S = A$ an abelian variety, $\operatorname{Pic}^{0}_{A/k} = A^{\vee}$ is the **dual abelian
variety**. Black-box reference: see [`pic-scheme-fga`](appendix-black-boxes.md#pic-scheme-fga). File 56, §§XI.6.3,
XI.6.5.

## Algebraic and analytic geometry (files 57–60)

**Complex analytic space.** A locally-ringed-$\mathbb{C}$-space $(\mathcal{X}, \mathcal{O}_{\mathcal{X}})$ locally
modelled on a closed analytic subspace of an open $U \subset \mathbb{C}^{n}$ cut out by a finite collection of
holomorphic functions $f_{1}, \cdots, f_{r} \in \mathcal{O}(U)$, equipped with the quotient structure sheaf
$\mathcal{O}_{U} / (f_{1}, \cdots, f_{r}) \cdot \mathcal{O}_{U}$. Morphisms are sheaf maps of
locally-ringed-$\mathbb{C}$-spaces. Black-box references:
[`gunning-rossi-analytic`](appendix-black-boxes.md#gunning-rossi-analytic),
[`grauert-remmert-coverings`](appendix-black-boxes.md#grauert-remmert-coverings). File 57, §XII.0.

**The analytic space $X^{an}$ associated with a $\mathbb{C}$-scheme $X$ locally of finite type.** The complex analytic
space representing the functor $\mathcal{X} \mapsto \operatorname{Hom}_{LocRing/\mathbb{C}}(\mathcal{X}, X)$. Exists by
Theorem-Definition XII.1.1. Together with the **canonical morphism** $\phi : X^{an} \to X$ of
locally-ringed-$\mathbb{C}$-spaces, $(X^{an}, \phi)$ is unique up to unique isomorphism; on underlying sets
$|X^{an}| \simeq X(\mathbb{C})$; at every point $x \in X^{an}$, the local map $\phi_{x}$ becomes an isomorphism after
passage to completions. File 57.

**Analytification of a morphism / a sheaf.** The functor $\Phi : X \mapsto X^{an}$ extends to morphisms: a scheme
morphism $f : X \to Y$ yields a unique analytic morphism $f^{an} : X^{an} \to Y^{an}$ with
$\phi_{Y} \circ f^{an} = f \circ \phi_{X}$ (XII.1.2). It also extends to $\mathcal{O}_{X}$-modules:
$F \mapsto F^{an} := \phi^{*} F$ is exact, faithful, and conservative on coherent sheaves (XII.1.3.1). File 57\.

**Stein open / Stein cover.** An open $\mathcal{U} \subset \mathcal{X}$ on which Cartan's Theorem B vanishes the
cohomology of every coherent analytic sheaf: $H^{p}(\mathcal{U}, \mathcal{F}) = 0$ for every $p \geq 1$. The analytic
analogue of "affine open". The standard cover of $\mathbb{P}^{r}_{\mathcal{Y}}$ by $r + 1$ opens
$\mathcal{U}_{i} \simeq \mathcal{B} \times \mathcal{E}^{r}$ consists of Stein opens, and Čech computes derived
cohomology on this cover. Black-box reference:
[`cartan-faisceaux-analytiques`](appendix-black-boxes.md#cartan-faisceaux-analytiques). File 59, §XII.4.2.

**Finite covering of an analytic space (XII.5.0).** An analytic morphism $\mathcal{X}' \to \mathcal{X}$ that is finite
(proper with finite fibres) and such that *every* irreducible component of $\mathcal{X}'$ dominates an irreducible
component of $\mathcal{X}$. The dominance hypothesis is the analytic analogue of the algebraic condition that the cover
is "everywhere of full rank". File 60, §XII.5.0.

**Finite étale covering of an analytic space.** A finite covering that is étale (locally biholomorphic). Equivalent to:
finite + flat + unramified, or finite + locally biholomorphic. File 60, §XII.5.

**Riemann existence theorem (XII.5.1).** The functor $X' \mapsto X'^{an}$ from finite étale coverings of $X$ to finite
étale coverings of $X^{an}$ is an *equivalence of categories*, for every $\mathbb{C}$-scheme $X$ locally of finite type.
The analytic counterpart of the classical Riemann existence theorem on Riemann surfaces. File 60, §XII.5.1.

**Grauert–Remmert theorem (XII.5.4).** A normal finite covering of an open subset $\mathcal{U} \subset \mathcal{X}$ of a
normal analytic space, étale on `𝒰 minus a rare closed analytic subset`, extends uniquely to a normal finite covering of
$\mathcal{X}$. The codimension-$\geq 2$ version (XII.5.5 strengthening) removes the étaleness hypothesis. File 60,
§XII.5.4.

**GAGA (Géométrie Algébrique et Géométrie Analytique).** The comparison principle of Serre 1956
([`gaga-serre-original`](appendix-black-boxes.md#gaga-serre-original)) and its extension to relative proper morphisms
(XII.4.2). For $f : X \to Y$ proper and $F$ coherent on $X$, the canonical map
$(R^{p} f_{*} F)^{an} \to R^{p} f^{an}_{*}(F^{an})$ is an isomorphism for every $p \geq 0$. Specialised to
$Y = \operatorname{Spec} \mathbb{C}$: $H^{p}(X, F) \simeq H^{p}(X^{an}, F^{an})$ for $X$ proper. Specialised to
functoriality: $Coh(X) \simeq Coh(X^{an})$ and the analytification functor is fully faithful on the category of proper
$\mathbb{C}$-schemes. File 59.

**Higman group.** A finitely-presented infinite group with no proper subgroup of finite index — equivalently, trivial
profinite completion. Constructed by G. Higman in 1951
([`higman-non-residually-finite`](appendix-black-boxes.md#higman-non-residually-finite)). If realised as
$\pi^{top}_{1}(V^{an})$ for $V / \mathbb{C}$ smooth projective, the natural map to the étale fundamental group is
trivial — but no such $V$ is currently known. File 60, §XII.5.5.

**Algebraically simply connected vs topologically simply connected.** For $X / \mathbb{C}$ a proper smooth scheme: *X is
algebraically simply connected* means $\pi^{\acute{e}}_{1}t(X) = 1$, equivalently $\hat{\pi}^{top}_{1}(X^{an}) = 1$
(XII.5.2); *X^an is topologically simply connected* means $\pi^{top}_{1}(X^{an}) = 1$. The two notions are equivalent
when $\pi^{top}_{1}(X^{an})$ is residually finite; in general the topological condition is strictly stronger. Toledo's
construction ([`toledo-non-residually-finite-pi1`](appendix-black-boxes.md#toledo-non-residually-finite-pi1)) shows the
strictness is real. File 60, §XII.5.5.

## Étale cohomology, cohomological properness, and tame ramification (files 61–64)

**Étale site, étale sheaf.** The *étale site* $X_{et}$ of a scheme $X$ is the category of étale $X$-schemes with the
étale topology (surjective families of étale morphisms cover). An *étale sheaf of sets / groups / abelian groups* on $X$
is a presheaf on $X_{et}$ satisfying the sheaf condition for étale coverings. Source:
[`sga-4-etale-site`](appendix-black-boxes.md#sga-4-etale-site). File 61 §XIII.B.1.

**Pushforward, higher direct images, base-change comparison.** For $f : X \to Y$ and an étale sheaf $F$ on $X$, the
pushforward $f_{*} F$ and the higher direct images $R^{q} f_{*} F$ ($q \geq 0$) are again étale sheaves on $Y$; their
stalk at a geometric point `ȳ` is $H^{q}(X \times_{Y} Y_{(\bar{y})}, F)$. The base-change comparison map
$\Phi^{q} : h^{*} R^{q} f_{*} F \to R^{q} f'_{*} (h'^{*} F)$ is the canonical natural transformation for a cartesian
square. Source: [`sga-4-direct-image-and-rqf`](appendix-black-boxes.md#sga-4-direct-image-and-rqf). File 61
§XIII.B.2–B.3.

**Cohomologically proper relative to $S$ in dimension $\leq n$.** A pair $(F, f : X \to Y)$ with $F$ an étale sheaf /
stack on $X$ is *cohomologically proper relative to $S$ in dimension $\leq n$* ($n \in {-1, 0, 1}$) if the comparison
functor $g^{*} f_{*} F \to f'_{*} h^{*} F$ is faithful / fully faithful / an equivalence under every base change
$S' \to S$. Concretely: for every base change $S' \to S$, the comparison map
$(R^{q} f_{*} F)|_{S'} \to R^{q} f'_{*} (F|_{X_{S'}})$ is an isomorphism for every $q \leq n$. Specialised to sheaves of
sets (XIII.1.2): $\Phi^{q}$ an iso for $q \leq n$. Specialised to sheaves of groups (XIII.1.3.1): every inner twist
${}^{P} F$ survives base change at $H^{0}$, and the non-abelian $R^{1}$ survives base change. _Intuition_: the
cohomology of $f$ survives base change up to degree $n$ — the value computed at a fibre matches the value seen at the
corresponding point of the base. Source:
[`sga-5-ii-cohomologically-proper`](appendix-black-boxes.md#sga-5-ii-cohomologically-proper). File 61 §XIII.1.

**Locally $n$-acyclic, $n$-acyclic morphism.** A morphism $f : X \to S$ is *locally $n$-acyclic* (for a coefficient
ring) if $F \to R f_{*} f^{*} F$ is an iso through degree $n$ over every strict localisation of $S$; *$n$-acyclic* if
the same is true globally over $S$. Equivalently, at every geometric point of $S$ the étale cohomology of the geometric
fibre agrees with the relative cohomology up to degree $n$. For coherent $f$, 0-acyclic ⇔ geometrically connected
fibres. Smooth morphisms are locally $n$-aspherical for $n < \dim_{rel}$ and prime-to-residue-characteristic
coefficients. _Intuition_: cohomology commutes with base change generically — over open dense pieces of the parameter
space — not everywhere. Source: [`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic). File 61
§XIII.B.6; file 63 §XIII.3, §XIII.4.

**Constructible étale sheaf.** An étale sheaf $F$ on $X$ is *constructible* if there is a finite stratification of $X$
into locally closed constructible subsets on which the restriction of $F$ is locally constant with finite fibres.
Source: [`sga-4-constructible-sheaves`](appendix-black-boxes.md#sga-4-constructible-sheaves). File 61 §XIII.B.5.

**Stack on $X_{et}$.** A fibred category $F \to X_{et}$ with effective descent for the étale topology (XIII.0.1).
Examples: the discrete-category stack of an étale sheaf of sets; the stack $Tors(G)$ of $G$-torsors for a sheaf of
groups $G$.

**Gerbe on $X_{et}$.** A stack $F$ whose fibres are non-empty connected groupoids (XIII.0.2). The stack of $G$-torsors
is a gerbe; conversely, a gerbe with a section is canonically $Tors(SheafAut(x))$.

**Sheaf of maximal subgerbes `SF`.** The sheafification of "isomorphism classes of objects of $F_{X'}$" (XIII.0.3). For
$F = Tors(G)$, $SF = R^{1} f_{*} G$ in the non-abelian sense.

**Strongly desingularizable schemes (in dim $\leq d$ over $k$).** Schemes of finite type over $k$ for which every
reduced closed subscheme of dimension $\leq d$ admits a strong resolution of singularities. Hironaka gives this in
characteristic zero for every $d$; in characteristic $p > 0$ it is an open hypothesis. Source:
[`sga-5-i-strongly-desingularizable`](appendix-black-boxes.md#sga-5-i-strongly-desingularizable). File 63.

**Tamely ramified algebra over a DVR.** An étale $K$-algebra $L = \prod L_{i}$ over the fraction field $K$ of a DVR $R$
of residual characteristic $p$ is *tamely ramified over $R$* if the inertia group $I_{i}$ of the Galois closure
$L'_{i} / K$ at $R$ has order prime to $p$. Equivalently, for $R$ strictly local: $[L_{i} : K]$ is prime to $p$. Inertia
is in any case an extension of `cyclic-prime-to-p` by $p$-group
([`serre-local-fields-iv-7`](appendix-black-boxes.md#serre-local-fields-iv-7)); the gentle file reproduces the proof in
the general non-separable-residue case. File 62 §XIII.2.0.

**Normal-crossings divisor relative to $S$; strict-NC.** A divisor $D \geq 0$ on an $S$-scheme $X$ is *strictly with
normal crossings relative to $S$* (SGA 5 II 4.2) if there is a finite family $(f_{i})$ in $\Gamma(X, \mathcal{O}_{X})$
with $D = \sum div(f_{i})$ such that at every point of `Supp D` the subscheme cut out by the $f_{i} \in I(x)$ is smooth
over $S$ of codimension `#I(x)` in $X$. *Normal crossings relative to $S$* is the étale-local version. File 62
§XIII.2.1.0.

**Tame ramification (along a divisor).** For a covering $Y \to X$ ramified along a normal-crossings divisor
$D \subset X$ of residual characteristic $p$ (relative to a base $S$), the ramification is *tame* if at every generic
point of every irreducible component of $D$ the ramification index is coprime to $p$; otherwise it is *wild*.
Equivalently, the inertia group of the Galois closure at each generic point of $D$ has order coprime to $p$. The local
pointwise version along a DVR is **Tamely ramified algebra over a DVR** above. _Intuition_: the branching is controlled
by the prime characteristic of the base — tame means the characteristic does not divide the index, so ramification is
"visible" in the residue field; wild means the characteristic divides the index, and ramification hides higher-order
arithmetic that the residue field cannot see. File 62 §XIII.2.1.

**Tamely ramified sheaf on $U = X - Y$ along $D$ relative to $S$.** An étale sheaf $F$ of sets on $U$ whose restriction
to the fraction field $K$ of $\mathcal{O}_{X_{\bar{s}}, y}$ is representable by an étale $K$-algebra tame over
$\mathcal{O}_{X_{\bar{s}}, y}$, for every geometric point $\bar{s}$ of $S$ and every maximal point $y$ of the geometric
fibre $Y_{\bar{s}}$. File 62 §XIII.2.1.1.

**$H^{1}_{tame}(U, F)$, $R^{1}_{tame} f_{*} F$.** The subset of $H^{1}(U, F)$ formed by torsor classes tamely ramified
on $X$ relative to $S$ (XIII.2.1.2); the subsheaf of $R^{1} f_{*} F$ whose stalks classify such tame torsors. File 62
§XIII.2.1.2.

**Tame fundamental group $\pi^{tame}_{1}((U, X)/S, a)$.** Pro-representing group of the Galois category
$C_{t}((U, X)/S)$ of tamely ramified étale coverings of $U$ (XIII.2.1.3). A quotient of $\pi_{1}(U, a)$. File 62
§XIII.2.1.3.

**Pro-$\mathcal{L}$ fundamental group $\pi^{\mathcal{L}}_{1}(X, a)$; prime-to-$p$ fundamental group $\pi^{p'}_{1}(X)$.**
Maximal pro-$\mathcal{L}$ quotient of the étale $\pi_{1}$, for a set of primes $\mathcal{L}$. When $\mathcal{L} = p'$ is
the complement of the residual characteristic, this is the prime-to-$p$ fundamental group. File 63 §XIII.4.0.

**$\pi_{1}'(X, a)$.** For a morphism $X \to S$ of connected schemes with $K = Ker(\pi_{1}(X) \to \pi_{1}(S))$, the
quotient of $\pi_{1}(X)$ by the smallest distinguished pro-subgroup $N$ of $K$ such that $K/N$ is a
pro-$\mathcal{L}$-group $K^{\mathcal{L}}$. Lives in the exact sequence
$\pi^{\mathcal{L}}_{1}(X_{\bar{s}}) \to \pi_{1}'(X) \to \pi_{1}(S)$. File 63 §XIII.4.0.

## Notation lookups

For symbol-by-symbol notation, see [notation.md](notation.md).

## Black boxes

Every theorem the gentle reading cites but does not prove is collected in
[appendix-black-boxes.md](appendix-black-boxes.md), with statement, role, and source citation. Entries in this glossary
for **finite locally free**, **flat morphism**, **formally étale**, **Main Theorem (Zariski)**, **Cohen-Macaulay**,
**Serre's criterion**, **Nagata ring**, **Hensel's lemma**, **universal homeomorphism**, **Krull's intersection
theorem**, and **Nakayama's lemma** point at the matching row there.

## Cross-references between gentle SGA and the source

Each rewritten theorem in files 10, 11, 12 carries an HTML comment of the form `<!-- source: I.x.y -->` linking it to
the source label in `01-morphismes-etales.md`. To find a result quickly, search the gentle file for the corresponding
label.
