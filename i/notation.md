# Notation

This file lists the notation used throughout Gentle SGA I, with a short description of each symbol. Where a symbol
carries the same meaning as in the source, we follow the source.

## Categories and rings

| Symbol                              | Meaning                                                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------------------- |
| $A$, $B$, $C$                       | commutative rings (with `1`); often noetherian                                                 |
| $A \to B$                           | a ring homomorphism                                                                            |
| `A-Alg`                             | the category of commutative $A$-algebras                                                       |
| $\operatorname{Hom}_{A}(M, N)$      | the set of $A$-module homomorphisms                                                            |
| $\operatorname{Hom}_{A-alg}(B, B')$ | the set of $A$-algebra homomorphisms                                                           |
| $M \otimes_{A} N$                   | the tensor product of $A$-modules $M$ and $N$                                                  |
| $M^{n}$                             | the free $A$-module of rank $n$                                                                |
| $\check{M}$                         | the dual $A$-module $\operatorname{Hom}_{A}(M, A)$                                             |
| $\wedge^{n} M$                      | the $n$-th exterior power of an $A$-module                                                     |
| $S^{-1}A$                           | the localization of $A$ at a multiplicative subset $S$                                         |
| $A[1/f]$                            | the localization at the powers of $f$                                                          |
| $A_{\mathfrak{p}}$                  | the localization at a prime ideal $\mathfrak{p}$                                               |
| `Â`                                 | the completion of a local ring $A$ at its maximal ideal                                        |
| $\hat{R}$                           | the $\mathcal{I}$-adic completion of a noetherian ring $R$ (file 18)                           |
| $\mathcal{I}^{n+1}$                 | the $(n+1)$-th power of an ideal $\mathcal{I} \subset R$ (file 18)                             |
| $gr^{n}_{\mathcal{I}}(R)$           | the graded piece $\mathcal{I}^{n} / \mathcal{I}^{n+1}$ of an $\mathcal{I}$-adic ring (file 18) |
| $W = W(k)$                          | the Witt ring (Cohen ring) of a perfect field $k$ of characteristic $p$ (file 22)              |
| $A^{n}$                             | a free $A$-module of rank $n$, when used as a module                                           |
| $A^{\times}$                        | the group of units of $A$                                                                      |

## Ideals, primes, residue fields

| Symbol                       | Meaning                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------- |
| $I, J \subset A$             | ideals of $A$                                                                                |
| $\mathfrak{p}, \mathfrak{q}$ | prime ideals (typeset as fraktur p, q)                                                       |
| $\mathfrak{m}, \mathfrak{n}$ | maximal ideals                                                                               |
| $\mathfrak{r}(A)$            | the maximal ideal of a local ring $A$ (source's notation)                                    |
| $\kappa(\mathfrak{p})$       | the residue field at a prime $\mathfrak{p}$, equal to $Frac(A/\mathfrak{p})$                 |
| $\kappa(x)$                  | the residue field at a point $x$ of a scheme                                                 |
| $\sqrt{(0)}$                 | the nilradical of $A$                                                                        |
| $Ann(M)$                     | the annihilator of an $A$-module $M$                                                         |
| $V(I)$                       | the closed subset ${ \mathfrak{p} : I \subseteq \mathfrak{p}} \subset \operatorname{Spec} A$ |
| $D(f)$                       | the distinguished open $\operatorname{Spec} A[1/f] \subset \operatorname{Spec} A$            |

## Schemes and morphisms

| Symbol                         | Meaning                                                                                                   |
| ------------------------------ | --------------------------------------------------------------------------------------------------------- |
| $X$, $Y$, $Z$, $S$             | schemes (or preschemes)                                                                                   |
| $\operatorname{Spec} A$        | the spectrum of $A$                                                                                       |
| $Spf \hat{R}$                  | the formal spectrum of an adic ring $\hat{R}$ (file 18)                                                   |
| $\mathfrak{X}$, $\mathfrak{Y}$ | formal preschemes (files 18, 21, 22)                                                                      |
| `Ŝ`, $\hat{X}$                 | the $\mathcal{I}$-adic formal completion of $S$, $X$ (file 18)                                            |
| $f : X \to Y$                  | a morphism of schemes                                                                                     |
| $f^{-1}(y)$                    | the fiber of $f$ over $y \in Y$, equal to $X \times_{Y} \operatorname{Spec} \kappa(y)$                    |
| $f(X)$                         | the image of $f$, as a topological subset of $Y$                                                          |
| `X \| U`                       | the restriction of $X$ to an open subset $U$ of $Y$                                                       |
| $X \times_{Y} X'$              | the fibered product of $X$ and $X'$ over $Y$                                                              |
| $\operatorname{Hom}_{S}(Y, X)$ | the set of $S$-morphisms $Y \to X$                                                                        |
| $\Gamma_{g}$                   | the graph morphism of $g : X' \to X$                                                                      |
| $\Delta_{X/Y}$                 | the diagonal morphism $X \to X \times_{Y} X$                                                              |
| $\Delta^{n}_{X/Y}$             | the $n$-th infinitesimal neighborhood of the diagonal                                                     |
| $S_{n}$                        | the $n$-th thickening $\operatorname{Spec}(R/\mathcal{I}^{n+1})$ of $S = \operatorname{Spec} R$ (file 18) |
| $X_{n}$                        | the base-change $X \times_{S} S_{n}$ (file 18)                                                            |
| $f_{red}$                      | the morphism of underlying reduced schemes                                                                |
| $X_{red}$                      | the reduced subscheme of $X$                                                                              |

## Derived functors

| Symbol                  | Meaning                                                                                                                   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| $Tor^{A}_{i}(M, N)$     | the $i$-th left-derived functor of $- \otimes_{A} -$, computed from a free resolution (file 23)                           |
| $R^{p} G \circ R^{q} F$ | composite of derived functors of $F$ and $G$; appears as the $E^{2}$ page of the Grothendieck spectral sequence (file 23) |
| $gr^{0}_{I}(M)$         | the zeroth piece $M / I M$ of the $I$-adic filtration on an $A$-module $M$ (file 25)                                      |
| $gr_{I}(M)$             | the full associated graded module $\oplus_{n} I^{n} M / I^{n+1} M$ (files 25, 26)                                         |

## Sheaves and modules

| Symbol                            | Meaning                                                                                                                                               |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mathcal{O}_{X}$                 | the structure sheaf of $X$                                                                                                                            |
| $\mathcal{O}_{x}$                 | the local ring at the point $x \in X$                                                                                                                 |
| $\mathcal{I}_{X}$                 | the ideal sheaf of the diagonal in $X \times_{Y} X$                                                                                                   |
| $\Omega^{1}_{X/Y}$                | the sheaf of relative Kähler differentials                                                                                                            |
| $\Omega^{1}_{B/A}$                | the $B$-module of relative Kähler differentials                                                                                                       |
| $\mathcal{N}_{Y/X}$               | the conormal sheaf $\mathcal{J}/\mathcal{J}^{2}$ of a closed immersion $Y \hookrightarrow X$ (file 15)                                                |
| $\mathcal{P}^{n}_{X/S}$           | the principal-parts sheaf $\mathcal{O}_{X\times_{S} X}/\mathcal{I}^{n+1}_{X}$ (files 03, 15)                                                          |
| $\mathcal{P}^{\infty}_{X/S}$      | the projective limit $\lim_{n} \mathcal{P}^{n}_{X/S}$; structure sheaf of the formal completion of $X \times_{S} X$ along the diagonal (file 15)      |
| $\mathfrak{g}_{X/S}$              | the tangent sheaf $\mathcal{Hm}_{\mathcal{O}_{X}}(\Omega^{1}_{X/S}, \mathcal{O}_{X}) = \mathcal{D}er_{S}(\mathcal{O}_{X}, \mathcal{O}_{X})$ (file 17) |
| $\mathcal{Hm}_{\mathcal{O}_{X}}$  | the sheaf-Hom of $\mathcal{O}_{X}$-modules (files 17, 21)                                                                                             |
| $\mathcal{D}er_{S}$               | the sheaf of $S$-derivations into a given quasi-coherent module (file 17)                                                                             |
| $\mathcal{B}$                     | a coherent sheaf of $\mathcal{O}_{Y}$-algebras (file 04+)                                                                                             |
| $\mathcal{A}$                     | usually $\mathcal{O}_{Y}$, the structure sheaf of $Y$ (file 04+)                                                                                      |
| $tr_{\mathcal{B}/\mathcal{A}}$    | the trace homomorphism of an $\mathcal{A}$-algebra $\mathcal{B}$                                                                                      |
| $d_{X/Y}$                         | the discriminant section of a flat covering                                                                                                           |
| $\mathfrak{d}_{X/Y}$              | the different ideal: $Ann(\Omega^{1}_{X/Y})$                                                                                                          |
| $R(X)$                            | the ring of rational functions on a scheme $X$                                                                                                        |
| `f₀⁎(ℱ)`                          | the pushforward of a sheaf by a continuous map $f_{0}$                                                                                                |
| $f*\mathcal{G}$                   | the pullback of a quasi-coherent sheaf $\mathcal{G}$ along $f$ (file 03)                                                                              |
| $\mathcal{G}, \mathcal{P}(g_{0})$ | the sheaves of automorphisms / extensions in §III.5–§III.6 (file 21)                                                                                  |
| $Supp(F)$                         | the support of a coherent sheaf $F$: the closed subset of $X$ where the stalk is non-zero (file 27)                                                   |

## Points and degrees

| Symbol                    | Meaning                                                                                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| $n(y)$                    | the geometric number of points of the fiber $f^{-1}(y)$                                                                                   |
| $[L : K]$                 | the degree of a finite field extension                                                                                                    |
| $[L : K]_{s}$             | the separable degree of a finite extension                                                                                                |
| `deg F`                   | the degree of a polynomial $F$                                                                                                            |
| $trdeg_{k} K$             | the transcendence degree of an extension $K / k$ (file 16)                                                                                |
| $\dim_{x} f$              | the relative dimension of a smooth morphism $f$ at $x \in X$ (file 14)                                                                    |
| $Y[t_{1}, \cdots, t_{n}]$ | the relative polynomial scheme $Y \times_{\operatorname{Spec} \mathbb{Z}} \operatorname{Spec} \mathbb{Z}[t_{1}, \cdots, t_{n}]$ (file 14) |

## Polynomials and derivatives

| Symbol       | Meaning                                                 |
| ------------ | ------------------------------------------------------- |
| $F \in A[t]$ | a polynomial in one variable over $A$                   |
| $F'(t)$      | the formal derivative of $F$                            |
| $F'(u)$      | the value of $F'$ at $u$ (an element of an $A$-algebra) |
| $(F, F')$    | the ideal in `A[t]` generated by $F$ and $F'$           |
| $A[t]/F$     | shorthand for $A[t]/(F \cdot A[t])$                     |

## Function fields and extensions

| Symbol                           | Meaning                                                     |
| -------------------------------- | ----------------------------------------------------------- |
| $K = \kappa(generic point of Y)$ | the function field of an integral $Y$                       |
| $Frac(A)$                        | the field of fractions of an integral domain                |
| $L/K$                            | a finite field extension or a finite-rank algebra           |
| $\tilde{A}, A'$                  | normalization of $A$ (integral closure in $Frac(A)$)        |
| $Y' \to Y$                       | base change or normalization morphism, depending on context |

## Categories of objects

| Symbol                              | Meaning                                                     |
| ----------------------------------- | ----------------------------------------------------------- |
| ${\acute{e}tale Y-schemes}$         | the category of étale $Y$-schemes                           |
| ${\acute{e}tale coverings of Y}$    | the category of finite étale $Y$-schemes                    |
| ${finite \acute{e}tale A-algebras}$ | the algebraic analogue                                      |
| `{finite separable k-algebras}`     | finite products of finite separable field extensions of $k$ |

## Constants and algebraic structures

| Symbol           | Meaning                                                                     |
| ---------------- | --------------------------------------------------------------------------- |
| $\mathbb{Z}$     | the integers                                                                |
| $\mathbb{Q}$     | the rationals                                                               |
| $\mathbb{R}$     | the reals                                                                   |
| $\mathbb{C}$     | the complex numbers                                                         |
| $\mathbb{F}_{q}$ | the finite field with $q$ elements                                          |
| $\mathbb{Z}_{p}$ | the $p$-adic integers                                                       |
| $k$, $k'$        | fields, often the residue fields of local rings                             |
| $\epsilon$       | a generic infinitesimal: $\epsilon^{2} = 0$ in $k[\epsilon]/(\epsilon^{2})$ |
| $t$, $t_{i}$     | indeterminates                                                              |

## Group-theoretic notation

| Symbol                                           | Meaning                                                                                  |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| $\pi_{1}(C, \bar{a})$                            | the étale fundamental group of a connected scheme $C$ at a geometric point `ā` (file 33) |
| `Ẑ`                                              | the profinite completion of $\mathbb{Z}$ (also $\hat{\mathbb{Z}}$; files 28, 29, 33)     |
| `Ĝ`                                              | the profinite completion of an abstract group $G$ (file 29)                              |
| $H^{0}$, $H^{1}$, $H^{2}$                        | sheaf cohomology in low degrees on a scheme (file 17)                                    |
| $\check{H}^{\bullet}(\mathfrak{U}, \mathcal{F})$ | Čech cohomology of a sheaf $\mathcal{F}$ on an open cover $\mathfrak{U}$ (file 17)       |

## Profinite groups and Galois categories

| Symbol                                           | Meaning                                                                                                                           |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| $\pi^{top}_{1}(B, b_{0})$                        | the topological fundamental group of $B$ at $b_{0}$ (file 28)                                                                     |
| $\hat{\pi}^{top}_{1}(B, b_{0})$                  | the profinite completion of $\pi^{top}_{1}(B, b_{0})$; classifies finite covers (file 28)                                         |
| $\pi$, $\Pi$                                     | a profinite group (typically the fundamental group of a Galois category) (files 29, 31, 32)                                       |
| $\mathcal{C}(\pi)$                               | the category of finite discrete sets with continuous left $\pi$-action (file 29)                                                  |
| $\mathcal{C}'(\pi)$                              | the category of compact totally disconnected $\pi$-spaces (file 32, V.5.2)                                                        |
| $Pro-\mathcal{C}$                                | the category of pro-objects of $\mathcal{C}$ (file 29)                                                                            |
| $Ind-\mathcal{C}$                                | the category of ind-objects of $\mathcal{C}$ (file 29)                                                                            |
| $P = (P_{i})_{i \in I}$                          | a pro-object: a projective system of objects of $\mathcal{C}$ over a filtered ordered $I$ (file 29, file 31)                      |
| $\operatorname{Aut}(F)$, $\operatorname{Aut}(P)$ | the (profinite) automorphism group of a fibre functor or fundamental pro-object (file 31)                                         |
| $F$, $F_{a}$                                     | a fibre functor (= fundamental functor) of a Galois category; for schemes, $F_{a}$ = geometric points over $a$ (files 32, 33)     |
| $\Gamma$                                         | the fundamental groupoid of a Galois category: connected groupoid of fibre functors (file 32)                                     |
| $\Pi$                                            | the fundamental pro-group of a Galois category, with $F(\Pi) = \pi_{F}$ (file 32, V.5.10)                                         |
| $\mathcal{C}(S)$                                 | the Galois category of finite étale coverings of a connected locally noetherian $S$ (file 33)                                     |
| $\pi_{1}(S, a)$                                  | the étale fundamental group of $S$ at the geometric point $a$ (file 33)                                                           |
| $\pi_{1}(S; a, a')$                              | the set of path classes from $a$ to $a'$ in the fundamental groupoid of $S$ (file 33)                                             |
| $\Pi^{S}_{1}$                                    | the fundamental pro-group of $S$ (file 33, V.7)                                                                                   |
| $G_{d}(x)$                                       | the **decomposition group** of $x$ (= stabiliser in $G$) (file 30, V.2)                                                           |
| $G_{i}(x)$                                       | the **inertia group** of $x$ (= kernel of the residue-field action) (file 30, V.2)                                                |
| $Y \times E$                                     | the disjoint sum of `\|E\|` copies of $Y$ indexed by the set $E$ (file 30, V.1)                                                   |
| $P \times_{\pi} E$                               | the inverse functor in V.4.1: solution of $\operatorname{Hom}(P \times_{\pi} E, X) = \operatorname{Hom}_{\pi}(E, F(X))$ (file 31) |
| $\operatorname{Hom}_{\pi}(E, X)$                 | $\pi$-equivariant homomorphisms (file 31)                                                                                         |

## Fibred categories, sites, and descent (files 34–38)

| Symbol                                                          | Meaning                                                                                                                                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Cat`                                                           | the (2-)category of (small) categories, with functors as 1-cells and natural transformations as 2-cells (file 34)                                                           |
| $Cat_{/ \mathcal{E}}$                                           | the (1-)category of $\mathcal{E}$-categories: pairs $(\mathcal{F}, p)$ with $p : \mathcal{F} \to \mathcal{E}$ (file 35)                                                     |
| $Cat^{cart}_{/ \mathcal{E}}$                                    | the sub-2-category with cartesian functors as 1-cells (files 35, 36)                                                                                                        |
| $\mathcal{E}^{\circ}$                                           | the opposite category of $\mathcal{E}$ (used throughout files 34–38; pseudofunctors $\mathcal{E}^{\circ} \to Cat$)                                                          |
| $\mathcal{F}$, $(\mathcal{F}, p)$                               | an $\mathcal{E}$-category, with projection functor $p : \mathcal{F} \to \mathcal{E}$ (file 35, VI.2)                                                                        |
| $\mathcal{F}_{S}$                                               | the fibre category of $\mathcal{F}$ over $S \in Ob \mathcal{E}$; isomorphic to $\mathcal{F} \times_{\mathcal{E}} {S}$ (file 35, VI.4)                                       |
| $\tilde{\mathcal{F}}$                                           | the cartesian sub-fibred-category of a fibred $\mathcal{F}$: same objects, only cartesian morphisms (file 36, VI.6.1)                                                       |
| $\operatorname{Hom}_{\mathcal{E}}(\mathcal{F}, \mathcal{G})$    | the set of $\mathcal{E}$-functors $\mathcal{F} \to \mathcal{G}$ (file 35, VI.2)                                                                                             |
| $\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{F}, \mathcal{G})$  | the category of $\mathcal{E}$-functors and $\mathcal{E}$-natural transformations (file 35, VI.2)                                                                            |
| $\operatorname{Hom}_{cart}(\mathcal{F}, \mathcal{G})$           | the full subcategory of cartesian functors (file 35, VI.5.2)                                                                                                                |
| $\Gamma(\mathcal{G} / \mathcal{E})$                             | sections: $\operatorname{Hom}_{\mathcal{E}}(\mathcal{E}, \mathcal{G})$ (file 35, VI.2)                                                                                      |
| $Lim\leftarrow(\mathcal{F} / \mathcal{E})$                      | cartesian sections of $\mathcal{F}$ over $\mathcal{E}$: $\operatorname{Hom}_{cart}(\mathcal{E}, \mathcal{F})$ (file 35, VI.5.5)                                             |
| $\lambda*$                                                      | base change along $\lambda : \mathcal{E}' \to \mathcal{E}$: $\lambda*(\mathcal{F}) = \mathcal{F} \times_{\mathcal{E}} \mathcal{E}'$ (file 35, VI.3)                         |
| $f^{*}$ (in file 36)                                            | the inverse-image functor $\mathcal{F}_{S} \to \mathcal{F}_{T}$ for $f : T \to S$ (chosen by a cleavage); file 35 introduces, file 36 uses                                  |
| $f_{*}$ (in file 37)                                            | the direct-image functor $\mathcal{F}_{T} \to \mathcal{F}_{S}$ for $f : T \to S$ (chosen by a co-cleavage); right adjoint to $f^{*}$ in the bi-fibred case (file 37, VI.10) |
| $\alpha_{f}(\xi)$                                               | the chosen cartesian morphism $f^{*}(\xi) \to \xi$ of a cleavage (file 36, VI.7)                                                                                            |
| $c_{f, g}(\xi)$                                                 | the coherence isomorphism $g^{*} f^{*}(\xi) \to (fg)^{*}(\xi)$ of a cleavage; the pentagon's protagonist (file 36, VI.7)                                                    |
| $c^{f, g}$                                                      | the dual coherence iso $(fg)_{*} \to f_{*} g_{*}$ for a co-cleavage (file 37, VI.10)                                                                                        |
| $\varphi : \mathcal{E}^{\circ} \to Cat$                         | a pseudofunctor; data $(\varphi(S), f^{*}, c_{f, g})$ with pentagon (file 34, file 37)                                                                                      |
| $Ar(\mathcal{E}) = \operatorname{Hom}(\Delta^{1}, \mathcal{E})$ | the arrow category: objects are arrows of $\mathcal{E}$, morphisms are commutative squares (files 35, 36, 37, 38)                                                           |
| $\Delta^{1}$                                                    | the totally-ordered set `[0, 1]` viewed as a category: two objects, one non-identity arrow (files 35, 38)                                                                   |
| $Sh(\mathcal{E}, \tau)$, $PSh(\mathcal{E})$                     | sheaves / presheaves of sets on a site $(\mathcal{E}, \tau)$ (file 34)                                                                                                      |
| $\mathcal{U}(T)$                                                | the category of open subsets of a topological space $T$, with inclusions as morphisms (file 38, VI.11(b))                                                                   |
| $\mathcal{H}(\mathcal{F}, \mathcal{C})$                         | the category of fibre-wise functors `(F_S)` and coherence data $(\phi_{f})$ for a cloven $\mathcal{F}$; descent-data category (file 38, VI.12.1)                            |
| $\phi_{f}$                                                      | the natural transformation $F_{T} \circ f^{*} \Longrightarrow F_{S}$ extracted from a functor $F : \mathcal{F} \to \mathcal{C}$ via the cleavage (file 38, VI.12)           |
| $i_{S}$                                                         | the inclusion functor $\mathcal{F}_{S} \to \mathcal{F}$ of a fibre into the total category (file 38, VI.12)                                                                 |

## Faithfully flat descent (files 40–43)

| Symbol                                      | Meaning                                                                                                                                            |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| $g : S' \to S$                              | a faithfully flat quasi-compact (fpqc) morphism of preschemes (files 40–43)                                                                        |
| $S''$                                       | the double fibre product $S' \times_{S} S'$ (files 40–43)                                                                                          |
| $S'''$                                      | the triple fibre product $S' \times_{S} S' \times_{S} S'$ (files 40–43)                                                                            |
| `p₁, p₂ : S″ ⇉ S′`                          | the two projections of the double fibre product (files 40–43)                                                                                      |
| `p_{12}, p_{13}, p_{23} : S‴ ⇉ S″`          | the three projections of the triple fibre product onto the double fibre products (files 40–43)                                                     |
| $A''$                                       | the affine ring counterpart $A' \otimes_{A} A'$ of $S''$ when $S = \operatorname{Spec} A$, $S' = \operatorname{Spec} A'$ (file 40)                 |
| $A'''$                                      | the affine ring counterpart $A' \otimes_{A} A' \otimes_{A} A'$ of $S'''$ (file 40)                                                                 |
| $\phi : p^{*}_{1}(M') \simeq p^{*}_{2}(M')$ | a descent datum on a quasi-coherent module $M'$ on $S'$ (file 40, VIII.1)                                                                          |
| $QCoh(S' / g)$                              | the category of pairs $(M', \phi)$ of a quasi-coherent module on $S'$ with a descent datum relative to $g$ (file 40, VIII.1)                       |
| $R(x')$                                     | the fibre $q_{2}(q^{-1}_{1}(x'))$ of the equivalence relation defined by a descent datum on $X'$, considered as a subset of $X'$ (file 43, VIII.7) |
| `q₁, q₂ : X″ ⇉ X′`                          | the two projections of the descent-data equivalence pair on $X'$ (file 43, VIII.7)                                                                 |
| $N_{f}(s)$                                  | the norm of a section $s \in \Gamma(X, \mathcal{O}_{X})$ along a finite locally free morphism $f : X \to S$ (file 43, VIII.7.6)                    |
| $Norm_{q_{2}}$                              | the norm of a section along a finite locally free morphism $q_{2}$ of double-fibre-product schemes; descent-compatibility tool (file 43)           |
| $\operatorname{Proj}_{S}(\mathcal{S})$      | the relative `Proj` of a quasi-coherent graded $\mathcal{O}_{S}$-algebra (files 42, 43)                                                            |
| $\mathcal{L}$, $\mathcal{L}'$               | invertible sheaves on $X$ and on $X' = X \times_{S} S'$ respectively (files 42, 43)                                                                |

## Descent of étale morphisms and the fundamental group (files 44–47)

| Symbol                                | Meaning                                                                                                                                                               |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\Gamma_{f} \subset X \times_{S} Y$   | the graph of an $S$-morphism $f : X \to Y$; for $Y / S$ étale, an open subset with radicial-surjective first projection (file 44, IX.1.6)                             |
| $Open(X)$                             | the set of open subsets of a prescheme $X$, regarded as a poset (file 44, IX.2.3)                                                                                     |
| $\pi_{0}(S)$                          | the set of connected components of a prescheme $S$ (file 46, IX.5)                                                                                                    |
| $E' = \pi_{0}(S')$, $E''$, $E'''$     | the sets of connected components of $S'$, $S''$, $S'''$ respectively (file 46, IX.5)                                                                                  |
| $q_{i} = \pi_{0}(p_{i})$              | the maps $E'' \to E'$ induced from the two projections `p_i : S″ ⇉ S′` by applying $\pi_{0}$ (file 46, IX.5)                                                          |
| $q_{ij} = \pi_{0}(p_{ij})$            | the maps $E''' \to E''$ induced from the three projections `p_{ij} : S‴ ⇉ S″` by applying $\pi_{0}$ (file 46, IX.5)                                                   |
| $v_{i} = \pi_{0}(u_{i})$              | the three maps $E''' \to E'$ induced from the three projections `u_i : S‴ ⇉ S′` (file 46, IX.5)                                                                       |
| $\pi_{s'} = \pi_{1}(S', \bar{s'})$    | the étale fundamental group of the connected component of $S'$ named by $s' \in E'$, at a chosen geometric point (file 46, IX.5)                                      |
| $g_{s''}$                             | a generator of the Seifert–van-Kampen formula for $\pi_{1}(S, a)$, indexed by $s'' \in E''$; describes the gluing across the connected component $s''$ (file 46)      |
| $a^{s'''}_{i} \in \pi_{v_{i}(s''')}$  | the cocycle elements of the descent datum on the fibred category of finite étale coverings, indexed by $s''' \in E'''$ and $i \in {1, 2, 3}$ (file 46, IX.5)          |
| $n(s)$                                | the geometric number of points in the fibre $g^{-1}(s)$ of a finite morphism $g : S' \to S$ at $s \in S$; equivalently the separable degree (file 46, IX.5.4)         |
| $Sym^{n}(X)$                          | the $n$-th symmetric power $X^{n} / \mathfrak{S}_{n}$ of a scheme $X$ (file 46, IX.5.8)                                                                               |
| $S'_{g}$                              | for $\Gamma$ a finite group acting on $S'$ and $g \in \Gamma$, the subscheme of $S'$ on which $id_{S'}$ and $g$ agree (file 46, IX.5.8)                               |
| $\pi_{1}(S', \Gamma; a')$             | the automorphism group of the fibre functor on the Galois category $\mathcal{C}_{0}'$ of étale coverings of $S'$ equipped with a compatible $\Gamma$-action (file 46) |
| $\bar{X}_{0} = X \otimes_{k} \bar{k}$ | the geometric special fibre of an $S$-prescheme $X$ at a point $s \in S$ with residue field $k = \kappa(s)$ and algebraic closure $\bar{k}$ (file 47, IX.6)           |

## Specialization of the fundamental group (files 48–51)

| Symbol                                                  | Meaning                                                                                                                                                                                                                     |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\bar{X}_{y} = X_{y} \otimes_{\kappa(y)} \kappa\bar{y}$ | the geometric fibre of $f : X \to Y$ at $y \in Y$, base-changed to an algebraic closure of the residue field $\kappa(y)$ (file 48, X.1)                                                                                     |
| `sp` or $sp_{y_{0}, y_{1}}$                             | the specialization morphism $\pi_{1}(\bar{X}_{y_{1}}) \to \pi_{1}(\bar{X}_{y_{0}})$ for a specialisation `y₀ ⤳ y₁`, defined up to inner automorphism (file 49, X.2.3)                                                       |
| $K_{s}$                                                 | the separable closure of a field $K$ (used heavily in file 51 §X.3.7–3.8)                                                                                                                                                   |
| $\bar{K}$                                               | the algebraic closure of a field $K$                                                                                                                                                                                        |
| $W(k)$                                                  | the Witt-vector ring of an algebraically closed field $k$ of characteristic $p > 0$; complete DVR with residue field $k$, fraction field `K_0` of char 0 (file 50, X.2.6)                                                   |
| $G_{d}$                                                 | the decomposition subgroup of a Galois group at a chosen maximal ideal of the integral closure (file 51, X.3.6)                                                                                                             |
| $G_{i}$                                                 | the inertia subgroup of a Galois group at a chosen maximal ideal; order is the ramification index (file 51, X.3.6)                                                                                                          |
| $e_{L/K}(\mathcal{O})$                                  | the ramification index of a Galois extension $L/K$ at a chosen place over the DVR $\mathcal{O} \subset K$ (file 51, X.3.6)                                                                                                  |
| $G^{res}$                                               | the inverse limit of the finite *solvable* topological quotients of a profinite group $G$; the "solvable profinite quotient" (file 50, X.2.14)                                                                              |
| $\pi_{1}(X)^{(p)}$                                      | the prime-to-$p$ completion of $\pi_{1}(X)$: the maximal pro-(prime-to-$p$) quotient (file 51, X.3.9–3.10)                                                                                                                  |
| $\Gamma$                                                | the surface group on `2g` generators with one commutator relation $(s_{1} t_{1} s^{-1}_{1} t^{-1}_{1}) \cdots (s_{g} t_{g} s^{-1}_{g} t^{-1}_{g}) = 1$ (file 50, X.2.6)                                                     |
| $(s_{i}, t_{i})_{1 \leq i \leq g}$                      | the `2g` topological generators of $\pi_{1}(X_{0})$ for $X_{0} / k$ a proper smooth curve of genus $g$; geometrically, meridians and longitudes of the $i$-th handle of the associated topological surface (file 50, X.2.6) |
| $\Gamma^{(p)}$                                          | the prime-to-$p$ quotient of the surface group $\Gamma$: the universal pro-(prime-to-$p$) group on `2g` generators with the commutator relation (file 51, X.3.10)                                                           |
| $X_{K} = X \otimes_{R} K$                               | the generic fibre of a scheme $X / R$ ($R$ a DVR with fraction field $K$); cited in file 50 (X.2.6) and file 51 (X.3.7)                                                                                                     |

## Examples and complements (files 52–56)

| Symbol                                                       | Meaning                                                                                                                                                                                         |
| ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mu_{n, S}$                                                 | the Kummer group of rank $n$ over $S$: $\operatorname{Spec} \mathcal{O}_{S}[t] / (1 - t^{n})$; kernel of $n$-th power on $\mathbb{G}_{m, S}$ (file 56, XI.6.1)                                  |
| $\alpha_{p}$                                                 | kernel of Frobenius $F : \mathbb{G}_{a} \to \mathbb{G}_{a}$ over the prime field $\mathbb{F}_{p}$; an infinitesimal (non-étale) finite locally free group scheme of order $p$ (file 56, XI.6.5) |
| $\alpha_{p^{n}}$                                             | kernel of the $n$-th iterate $F^{n} : \mathbb{G}_{a} \to \mathbb{G}_{a}$ (file 56, XI.6.5)                                                                                                      |
| $F : \mathbb{G}_{a} \to \mathbb{G}_{a}$                      | Frobenius morphism over a char-$p$ base, $F(t) = t^{p}$ (file 56, XI.6.4)                                                                                                                       |
| $wp = id - F$                                                | Artin–Schreier endomorphism of $\mathbb{G}_{a}$ in char $p$ (file 56, XI.6.4)                                                                                                                   |
| $T_{\ell}(A)$                                                | $\ell$-adic Tate module of an abelian variety $A$: $\lim_{r} {}_{\ell^{r}}A(k)$ (file 53, XI.2.3)                                                                                               |
| $T\cdot(A)$                                                  | adelic Tate module $\prod_{\ell} T_{\ell}(A) = \lim_{n} {}_{nA}(k)$ (file 53, XI.2.3)                                                                                                           |
| ${}_{nA}$                                                    | kernel of multiplication by $n$ in a group scheme $A$ (file 53, XI.2.3); for an abelian variety, a finite flat group scheme of order $n^{2g}$                                                   |
| $\nu$                                                        | $p$-rank of an abelian variety $A / \bar{k}_{p}$: integer $0 \leq \nu \leq \dim A$ with ${}_{pA}(\bar{k}) \simeq (\mathbb{Z}/p)^{\nu}$ (file 53, XI.2.4)                                        |
| `D(G) = SheafHom_{S\text{-grp}}(G, 𝔾_m)`                     | Cartier dual of a finite commutative $S$-group scheme $G$ (file 56, XI.6.5)                                                                                                                     |
| $\operatorname{Pic}(S)$                                      | Picard group $H^{1}(S, \mathcal{O}^{*}_{S})$ of an $S$-scheme (file 56, XI.6.3)                                                                                                                 |
| $\operatorname{Pic}_{S / k}$                                 | Picard scheme of $S / k$ (file 56, XI.6.5)                                                                                                                                                      |
| $\operatorname{Pic}^{0}_{S / k}$                             | connected component of identity in $\operatorname{Pic}_{S/k}$ (file 56, XI.6.5)                                                                                                                 |
| $A^{\vee}$                                                   | dual abelian variety of $A$: $A^{\vee} = \operatorname{Pic}^{0}_{A/k}$ (file 56, XI.6.5)                                                                                                        |
| $H^{1}(S, G)$                                                | set of isomorphism classes of principal $G$-bundles over $S$ (in the fpqc / descent-theoretic sense of XI.4.1); a group when $G$ is commutative (file 55, XI.4.3)                               |
| $Ext(A, G)$                                                  | group of isomorphism classes of commutative extensions $0 \to G \to E \to A \to 0$ of an abelian variety $A$ by $G$ (file 53, XI.2.1)                                                           |
| $Z^{1}(\pi_{1}, \mathcal{G})$                                | set of 1-cocycles $\phi : \pi_{1} \to \mathcal{G}$ (with $\pi_{1}$ acting on $\mathcal{G}$) (file 55, XI.5)                                                                                     |
| $B^{1}(\pi_{1}, \mathcal{G})$                                | 1-coboundaries; $H^{1}(\pi_{1}, \mathcal{G}) = Z^{1} / B^{1}$ (file 55, XI.5)                                                                                                                   |
| $\pi^{N}_{1}(X, x)$                                          | Nori fundamental group scheme of $X$ pointed at $x$ (file 53, XI.2.5)                                                                                                                           |
| $T\cdot(\operatorname{Pic}_{X/k})$                           | "true Tate module of `Pic`": limit $\lim_{i} D(P_{i})$ over finite algebraic subgroups $P_{i} \subset \operatorname{Pic}_{X/k}$ (file 56, XI.6.5)                                               |
| ${}_{n} \operatorname{Pic}(S)$                               | $n$-torsion in $\operatorname{Pic}(S)$: kernel of multiplication by $n$ on $\operatorname{Pic}(S)$ (file 56, XI.6.3)                                                                            |
| $H^{0}(S, \mathcal{O}_{S})$, $H^{0}(S, \mathcal{O}^{*}_{S})$ | global sections of the structure sheaf and its unit group (file 55, XI.5)                                                                                                                       |
| $Gr(k, n)$                                                   | Grassmann variety of $k$-dimensional subspaces of an $n$-dimensional vector space (file 52, XI.1.2)                                                                                             |
| $G/P$                                                        | generalised flag variety: quotient of a connected linear group $G$ by a parabolic subgroup $P$ (file 52, XI.1.2)                                                                                |
| $\hat{C}_{V}$                                                | projective cone over a closed subscheme $V \subset \mathbb{P}^{r}$ (file 54, XI.3.1)                                                                                                            |
| `RC`, `sRC`                                                  | rationally connected, separably rationally connected (file 52, XI.1.4.4)                                                                                                                        |

## Algebraic and analytic geometry (files 57–60)

| Symbol                                                                                 | Meaning                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $X^{an}$                                                                               | the complex analytic space associated with a $\mathbb{C}$-scheme $X$ locally of finite type (file 57, XII.1.1)                                                                                             |
| \`                                                                                     | X^an                                                                                                                                                                                                       |
| $\phi : X^{an} \to X$                                                                  | canonical morphism of locally-ringed-$\mathbb{C}$-spaces representing the points functor $\mathcal{X} \mapsto \operatorname{Hom}_{LocRing/\mathbb{C}}(\mathcal{X}, X)$ (file 57, XII.1.1)                  |
| $\phi_{x} : \mathcal{O}_{X, \phi(x)} \to \mathcal{O}_{X^{an}, x}$                      | local map at $x \in X^{an}$; an isomorphism after passage to completions (file 57, XII.1.1)                                                                                                                |
| $\hat{\phi}_{x} : \hat{\mathcal{O}}_{X, \phi(x)} \simeq \hat{\mathcal{O}}_{X^{an}, x}$ | completion isomorphism — the local content of XII.1.1 (file 57)                                                                                                                                            |
| $f^{an} : X^{an} \to Y^{an}$                                                           | analytification of $f : X \to Y$; the unique morphism with $\phi_{Y} \circ f^{an} = f \circ \phi_{X}$ (file 57, XII.1.2)                                                                                   |
| $F^{an} = \phi^{*} F$                                                                  | analytification of an $\mathcal{O}_{X}$-module $F$; exact, faithful, conservative on coherent sheaves (file 57, XII.1.3.1)                                                                                 |
| $\mathcal{O}_{\mathcal{X}}$, $\mathcal{O}_{X^{an}}$                                    | structure sheaf of an analytic space; the sheaf of holomorphic functions modulo the defining ideal                                                                                                         |
| `Φ : Sch_{lft}/ℂ → AnSp/ℂ`                                                             | the analytification functor $X \mapsto X^{an}$; commutes with finite projective limits (file 57, XII.1.2)                                                                                                  |
| $\mathcal{E}^{n}$                                                                      | the analytic affine $n$-space $(\mathbb{C}^{n}, \mathcal{O}_{hol})$; equals $(\mathbb{A}^{n}_{\mathbb{C}})^{an}$ (file 57, XII.1.1.c)                                                                      |
| $\mathcal{B}$                                                                          | a (poly)disc / open ball in $\mathcal{E}^{n}$; the standard Stein neighbourhood (file 59, XII.4.2)                                                                                                         |
| $\mathcal{X}$, $\mathcal{Y}$, $\mathcal{P}$, $\mathcal{U}$, $\mathcal{V}$              | script letters: analytic spaces (following the SGA source convention for §§XII.4–XII.5)                                                                                                                    |
| $\operatorname{Spec}_{an}(\mathcal{A})$                                                | analytic spectrum of a coherent analytic $\mathcal{O}_{\mathcal{X}}$-algebra; the analytic analogue of $\operatorname{Spec}_{S}$ for a quasi-coherent $\mathcal{O}_{S}$-algebra (file 60, XII.5.4–XII.5.5) |
| $R^{p} f^{an}_{*}$                                                                     | higher direct image along an analytic morphism $f^{an}$ (file 59, XII.4.1)                                                                                                                                 |
| $\theta_{p} : (R^{p} f_{*} F)^{an} \to R^{p} f^{an}_{*}(F^{an})$                       | canonical comparison map for higher direct images; the GAGA datum (file 59, XII.4.1)                                                                                                                       |
| $\pi_{0}(X)$, $\pi_{0}(X^{an})$                                                        | set of connected components; the canonical map is a bijection by XII.2.6 (file 58)                                                                                                                         |
| $\pi^{top}_{1}(X^{an}, x)$                                                             | topological fundamental group of the analytic space at a base-point $x \in X^{an}$ (file 60, XII.5.2)                                                                                                      |
| $\hat{\pi}^{top}_{1}(X^{an}, x)$                                                       | profinite completion of $\pi^{top}_{1}(X^{an}, x)$; isomorphic to $\pi^{\acute{e}}_{1}t(X, \phi(x))$ by XII.5.2                                                                                            |
| $\pi^{\acute{e}}_{1}t(X, a)$                                                           | étale fundamental group of a scheme (file 33, V.7); analytic comparison is XII.5.2                                                                                                                         |

## Logical and categorical operators

| Symbol                 | Meaning                                                                |
| ---------------------- | ---------------------------------------------------------------------- |
| $\simeq$               | isomorphism                                                            |
| $\cong$                | isomorphism (used interchangeably with $\simeq$)                       |
| $\Longleftrightarrow$  | if and only if                                                         |
| $\Longrightarrow$      | implies                                                                |
| $\in$                  | element of                                                             |
| $\subset$, $\subseteq$ | subset of (we use $\subseteq$ to allow equality, $\subset$ for strict) |
| $\cup$, $\cap$         | union, intersection                                                    |
| $\amalg$               | disjoint union or coproduct                                            |
| $\mapsto$              | "maps to" in a function definition                                     |
| `:=`                   | definition equality                                                    |

## Étale cohomology, cohomological properness, and tame ramification (files 61–64)

| Symbol                                               | Meaning                                                                                                                                 |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| $X_{et}$, $X^{\sim}_{et}$                            | étale site of $X$; topos of étale sheaves on $X$ (XIII.B.1)                                                                             |
| $f_{*}$, $R^{q} f_{*}$                               | étale pushforward and higher direct images ($q \geq 0$); $R^{1} f_{*}$ makes sense for sheaves of groups (Giraud)                       |
| $\Phi^{q} : h^{*} R^{q} f_{*} F \to R^{q} f'_{*} F'$ | base-change comparison map for a cartesian square (XIII.B.3)                                                                            |
| $(F, f)$ coh-proper rel. $S$ in dim ≤ $n$            | $n \in {-1, 0, 1}$: comparison functor faithful / fully faithful / equivalence under every base change (XIII.1.1)                       |
| $H^{1}_{tame}(U, F)$                                 | subset of $H^{1}(U, F)$ of tamely ramified torsor classes (XIII.2.1.2)                                                                  |
| $R^{1}_{tame} f_{*} F$                               | subsheaf of $R^{1} f_{*} F$ consisting of tame classes (XIII.2.1.2)                                                                     |
| $\pi^{tame}_{1}((U, X)/S, a)$, $\pi^{tame}_{1}(U)$   | tame fundamental group of the open $U$ relative to the compactification $X$ and base $S$ (XIII.2.1.3)                                   |
| $\pi^{\mathcal{L}}_{1}(X, a)$                        | maximal pro-$\mathcal{L}$ quotient of $\pi^{\acute{e}}_{1}t(X, a)$ (XIII.4.0)                                                           |
| $\pi^{p'}_{1}(X)$                                    | prime-to-$p$ fundamental group; $\mathcal{L} = p'$                                                                                      |
| $\pi_{1}'(X, a)$                                     | quotient by the smallest distinguished pro-subgroup $N$ of $K = Ker(\pi_{1}(X) \to \pi_{1}(S))$ with $K/N$ pro-$\mathcal{L}$ (XIII.4.0) |
| $K^{\mathcal{L}}$                                    | maximal pro-$\mathcal{L}$ quotient of $K$                                                                                               |
| `SF`                                                 | sheaf of maximal subgerbes of a stack $F$ (XIII.0.3)                                                                                    |
| $C_{t} = C_{t}((U, X)/S)$                            | Galois category of tamely ramified étale coverings (XIII.2.1.3)                                                                         |
| `wp`, $wp(a) = a^{p} - a$                            | Artin–Schreier operator on a characteristic-$p$ ring (XIII.2.13)                                                                        |
| ${}^{P} F$                                           | inner twist of a sheaf of groups $F$ by a $F$-torsor $P$ (XIII.1.3.1)                                                                   |
| $P \wedge^{F} Q$                                     | contracted product of a right $F$-torsor $P$ and a left $F$-torsor $Q$                                                                  |

## Nonstandard or source-specific notation

| Symbol              | Meaning                                                                        |
| ------------------- | ------------------------------------------------------------------------------ |
| $K(A)$              | (in section I.7) the residue field $\kappa(A)$ of a local ring                 |
| $b \in B$           | element of an algebra (we sometimes use $b$ for ring elements rather than $x$) |
| "the multiplodocus" | Grothendieck's informal name for the larger SGA + EGA machine                  |
| **radicial**        | synonym for **universally injective** (Grothendieck's "radiciel"; file 05)     |
| **net**             | synonym for **unramified** (Grothendieck's "net"; file 04)                     |

## Cross-reference

Source labels of the form `I.x.y` (e.g., `I.5.1`) refer to the corresponding numbered statement in
$docs/books/sga/i/01-morphismes-etales.md$. Each rewritten statement in files 10, 11, 12 carries an HTML comment
recording its source label.
