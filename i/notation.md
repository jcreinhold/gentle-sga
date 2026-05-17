# Notation

This file lists the notation used throughout Gentle SGA I, with a short description of each symbol. Where a symbol
carries the same meaning as in the source, we follow the source.

## Categories and rings

| Symbol               | Meaning                                                                           |
| -------------------- | --------------------------------------------------------------------------------- |
| `A`, `B`, `C`        | commutative rings (with `1`); often noetherian                                    |
| `A → B`              | a ring homomorphism                                                               |
| `A-Alg`              | the category of commutative `A`-algebras                                          |
| `Hom_A(M, N)`        | the set of `A`-module homomorphisms                                               |
| `Hom_{A-alg}(B, B′)` | the set of `A`-algebra homomorphisms                                              |
| `M ⊗_A N`            | the tensor product of `A`-modules `M` and `N`                                     |
| `Mⁿ`                 | the free `A`-module of rank `n`                                                   |
| `M̌`                  | the dual `A`-module `Hom_A(M, A)`                                                 |
| `∧ⁿ M`               | the `n`-th exterior power of an `A`-module                                        |
| `S⁻¹A`               | the localization of `A` at a multiplicative subset `S`                            |
| `A[1/f]`             | the localization at the powers of `f`                                             |
| `A_𝔭`                | the localization at a prime ideal `𝔭`                                             |
| `Â`                  | the completion of a local ring `A` at its maximal ideal                           |
| `R̂`                  | the `𝓘`-adic completion of a noetherian ring `R` (file 18)                        |
| `𝓘^{n+1}`            | the `(n+1)`-th power of an ideal `𝓘 ⊂ R` (file 18)                                |
| `gr^n_𝓘(R)`          | the graded piece `𝓘^n / 𝓘^{n+1}` of an `𝓘`-adic ring (file 18)                    |
| `W = W(k)`           | the Witt ring (Cohen ring) of a perfect field `k` of characteristic `p` (file 22) |
| `Aⁿ`                 | a free `A`-module of rank `n`, when used as a module                              |
| `A^×`                | the group of units of `A`                                                         |

## Ideals, primes, residue fields

| Symbol     | Meaning                                                   |
| ---------- | --------------------------------------------------------- |
| `I, J ⊂ A` | ideals of `A`                                             |
| `𝔭, 𝔮`     | prime ideals (typeset as fraktur p, q)                    |
| `𝔪, 𝔫`     | maximal ideals                                            |
| `𝔯(A)`     | the maximal ideal of a local ring `A` (source's notation) |
| `κ(𝔭)`     | the residue field at a prime `𝔭`, equal to `Frac(A/𝔭)`    |
| `κ(x)`     | the residue field at a point `x` of a scheme              |
| `√(0)`     | the nilradical of `A`                                     |
| `Ann(M)`   | the annihilator of an `A`-module `M`                      |
| `V(I)`     | the closed subset `{ 𝔭 : I ⊆ 𝔭 } ⊂ Spec A`                |
| `D(f)`     | the distinguished open `Spec A[1/f] ⊂ Spec A`             |

## Schemes and morphisms

| Symbol             | Meaning                                                           |
| ------------------ | ----------------------------------------------------------------- |
| `X`, `Y`, `Z`, `S` | schemes (or preschemes)                                           |
| `Spec A`           | the spectrum of `A`                                               |
| `Spf R̂`            | the formal spectrum of an adic ring `R̂` (file 18)                 |
| `𝔛`, `𝔜`           | formal preschemes (files 18, 21, 22)                              |
| `Ŝ`, `X̂`           | the `𝓘`-adic formal completion of `S`, `X` (file 18)              |
| `f : X → Y`        | a morphism of schemes                                             |
| `f⁻¹(y)`           | the fiber of `f` over `y ∈ Y`, equal to `X ×_Y Spec κ(y)`         |
| `f(X)`             | the image of `f`, as a topological subset of `Y`                  |
| `X \| U`           | the restriction of `X` to an open subset `U` of `Y`               |
| `X ×_Y X′`         | the fibered product of `X` and `X′` over `Y`                      |
| `Hom_S(Y, X)`      | the set of `S`-morphisms `Y → X`                                  |
| `Γ_g`              | the graph morphism of `g : X′ → X`                                |
| `Δ_{X/Y}`          | the diagonal morphism `X → X ×_Y X`                               |
| `Δⁿ_{X/Y}`         | the `n`-th infinitesimal neighborhood of the diagonal             |
| `S_n`              | the `n`-th thickening `Spec(R/𝓘^{n+1})` of `S = Spec R` (file 18) |
| `X_n`              | the base-change `X ×_S S_n` (file 18)                             |
| `f_red`            | the morphism of underlying reduced schemes                        |
| `X_red`            | the reduced subscheme of `X`                                      |

## Derived functors

| Symbol          | Meaning                                                                                                                |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `Tor^A_i(M, N)` | the `i`-th left-derived functor of `− ⊗_A −`, computed from a free resolution (file 23)                                |
| `R^p G ∘ R^q F` | composite of derived functors of `F` and `G`; appears as the `E²` page of the Grothendieck spectral sequence (file 23) |
| `gr_I⁰(M)`      | the zeroth piece `M / I M` of the `I`-adic filtration on an `A`-module `M` (file 25)                                   |
| `gr_I(M)`       | the full associated graded module `⊕_n I^n M / I^{n+1} M` (files 25, 26)                                               |

## Sheaves and modules

| Symbol      | Meaning                                                                                                                   |
| ----------- | ------------------------------------------------------------------------------------------------------------------------- |
| `𝒪_X`       | the structure sheaf of `X`                                                                                                |
| `𝒪_x`       | the local ring at the point `x ∈ X`                                                                                       |
| `𝓘_X`       | the ideal sheaf of the diagonal in `X ×_Y X`                                                                              |
| `Ω¹_{X/Y}`  | the sheaf of relative Kähler differentials                                                                                |
| `Ω¹_{B/A}`  | the `B`-module of relative Kähler differentials                                                                           |
| `𝒩_{Y/X}`   | the conormal sheaf `𝒥/𝒥²` of a closed immersion `Y ↪ X` (file 15)                                                         |
| `𝒫ⁿ_{X/S}`  | the principal-parts sheaf `𝒪_{X×_S X}/𝓘_X^{n+1}` (files 03, 15)                                                           |
| `𝒫^∞_{X/S}` | the projective limit `lim_n 𝒫ⁿ_{X/S}`; structure sheaf of the formal completion of `X ×_S X` along the diagonal (file 15) |
| `𝔤_{X/S}`   | the tangent sheaf `ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, 𝒪_X) = 𝒟er_S(𝒪_X, 𝒪_X)` (file 17)                                                   |
| `ℋ𝓂_{𝒪_X}`  | the sheaf-Hom of `𝒪_X`-modules (files 17, 21)                                                                             |
| `𝒟er_S`     | the sheaf of `S`-derivations into a given quasi-coherent module (file 17)                                                 |
| `𝓑`         | a coherent sheaf of `𝒪_Y`-algebras (file 04+)                                                                             |
| `𝓐`         | usually `𝒪_Y`, the structure sheaf of `Y` (file 04+)                                                                      |
| `tr_{𝓑/𝓐}`  | the trace homomorphism of an `𝓐`-algebra `𝓑`                                                                              |
| `d_{X/Y}`   | the discriminant section of a flat covering                                                                               |
| `𝔡_{X/Y}`   | the different ideal: `Ann(Ω¹_{X/Y})`                                                                                      |
| `R(X)`      | the ring of rational functions on a scheme `X`                                                                            |
| `f₀⁎(ℱ)`    | the pushforward of a sheaf by a continuous map `f₀`                                                                       |
| `f*𝒢`       | the pullback of a quasi-coherent sheaf `𝒢` along `f` (file 03)                                                            |
| `𝒢, 𝒫(g₀)`  | the sheaves of automorphisms / extensions in §III.5–§III.6 (file 21)                                                      |
| `Supp(F)`   | the support of a coherent sheaf `F`: the closed subset of `X` where the stalk is non-zero (file 27)                       |

## Points and degrees

| Symbol         | Meaning                                                                   |
| -------------- | ------------------------------------------------------------------------- |
| `n(y)`         | the geometric number of points of the fiber `f⁻¹(y)`                      |
| `[L : K]`      | the degree of a finite field extension                                    |
| `[L : K]_s`    | the separable degree of a finite extension                                |
| `deg F`        | the degree of a polynomial `F`                                            |
| `trdeg_k K`    | the transcendence degree of an extension `K / k` (file 16)                |
| `dim_x f`      | the relative dimension of a smooth morphism `f` at `x ∈ X` (file 14)      |
| `Y[t₁, …, tₙ]` | the relative polynomial scheme `Y ×_{Spec ℤ} Spec ℤ[t₁, …, tₙ]` (file 14) |

## Polynomials and derivatives

| Symbol     | Meaning                                                 |
| ---------- | ------------------------------------------------------- |
| `F ∈ A[t]` | a polynomial in one variable over `A`                   |
| `F′(t)`    | the formal derivative of `F`                            |
| `F′(u)`    | the value of `F′` at `u` (an element of an `A`-algebra) |
| `(F, F′)`  | the ideal in `A[t]` generated by `F` and `F′`           |
| `A[t]/F`   | shorthand for `A[t]/(F · A[t])`                         |

## Function fields and extensions

| Symbol                      | Meaning                                                     |
| --------------------------- | ----------------------------------------------------------- |
| `K = κ(generic point of Y)` | the function field of an integral `Y`                       |
| `Frac(A)`                   | the field of fractions of an integral domain                |
| `L/K`                       | a finite field extension or a finite-rank algebra           |
| `Ã, A′`                     | normalization of `A` (integral closure in `Frac(A)`)        |
| `Y′ → Y`                    | base change or normalization morphism, depending on context |

## Categories of objects

| Symbol                          | Meaning                                                     |
| ------------------------------- | ----------------------------------------------------------- |
| `{étale Y-schemes}`             | the category of étale `Y`-schemes                           |
| `{étale coverings of Y}`        | the category of finite étale `Y`-schemes                    |
| `{finite étale A-algebras}`     | the algebraic analogue                                      |
| `{finite separable k-algebras}` | finite products of finite separable field extensions of `k` |

## Constants and algebraic structures

| Symbol     | Meaning                                          |
| ---------- | ------------------------------------------------ |
| `ℤ`        | the integers                                     |
| `ℚ`        | the rationals                                    |
| `ℝ`        | the reals                                        |
| `ℂ`        | the complex numbers                              |
| `𝔽_q`      | the finite field with `q` elements               |
| `ℤ_p`      | the `p`-adic integers                            |
| `k`, `k′`  | fields, often the residue fields of local rings  |
| `ε`        | a generic infinitesimal: `ε² = 0` in `k[ε]/(ε²)` |
| `t`, `t_i` | indeterminates                                   |

## Group-theoretic notation

| Symbol           | Meaning                                                                                  |
| ---------------- | ---------------------------------------------------------------------------------------- |
| `π₁(C, ā)`       | the étale fundamental group of a connected scheme `C` at a geometric point `ā` (file 33) |
| `Ẑ`              | the profinite completion of `ℤ` (also `ℤ̂`; files 28, 29, 33)                             |
| `Ĝ`              | the profinite completion of an abstract group `G` (file 29)                              |
| `H⁰`, `H¹`, `H²` | sheaf cohomology in low degrees on a scheme (file 17)                                    |
| `Ȟ^•(𝔘, 𝓕)`      | Čech cohomology of a sheaf `𝓕` on an open cover `𝔘` (file 17)                            |

## Profinite groups and Galois categories

| Symbol              | Meaning                                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `π₁^top(B, b₀)`     | the topological fundamental group of `B` at `b₀` (file 28)                                                                  |
| `π̂₁^top(B, b₀)`     | the profinite completion of `π₁^top(B, b₀)`; classifies finite covers (file 28)                                             |
| `π`, `Π`            | a profinite group (typically the fundamental group of a Galois category) (files 29, 31, 32)                                 |
| `𝒞(π)`              | the category of finite discrete sets with continuous left `π`-action (file 29)                                              |
| `𝒞′(π)`             | the category of compact totally disconnected `π`-spaces (file 32, V.5.2)                                                    |
| `Pro-𝒞`             | the category of pro-objects of `𝒞` (file 29)                                                                                |
| `Ind-𝒞`             | the category of ind-objects of `𝒞` (file 29)                                                                                |
| `P = (P_i)_{i ∈ I}` | a pro-object: a projective system of objects of `𝒞` over a filtered ordered `I` (file 29, file 31)                          |
| `Aut(F)`, `Aut(P)`  | the (profinite) automorphism group of a fibre functor or fundamental pro-object (file 31)                                   |
| `F`, `F_a`          | a fibre functor (= fundamental functor) of a Galois category; for schemes, `F_a` = geometric points over `a` (files 32, 33) |
| `Γ`                 | the fundamental groupoid of a Galois category: connected groupoid of fibre functors (file 32)                               |
| `Π`                 | the fundamental pro-group of a Galois category, with `F(Π) = π_F` (file 32, V.5.10)                                         |
| `𝒞(S)`              | the Galois category of finite étale coverings of a connected locally noetherian `S` (file 33)                               |
| `π₁(S, a)`          | the étale fundamental group of `S` at the geometric point `a` (file 33)                                                     |
| `π₁(S; a, a′)`      | the set of path classes from `a` to `a′` in the fundamental groupoid of `S` (file 33)                                       |
| `Π₁^S`              | the fundamental pro-group of `S` (file 33, V.7)                                                                             |
| `G_d(x)`            | the **decomposition group** of `x` (= stabiliser in `G`) (file 30, V.2)                                                     |
| `G_i(x)`            | the **inertia group** of `x` (= kernel of the residue-field action) (file 30, V.2)                                          |
| `Y × E`             | the disjoint sum of `\|E\|` copies of `Y` indexed by the set `E` (file 30, V.1)                                             |
| `P ×_π E`           | the inverse functor in V.4.1: solution of `Hom(P ×_π E, X) = Hom_π(E, F(X))` (file 31)                                      |
| `Hom_π(E, X)`       | `π`-equivariant homomorphisms (file 31)                                                                                     |

## Fibred categories, sites, and descent (files 34–38)

| Symbol               | Meaning                                                                                                                                       |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `Cat`                | the (2-)category of (small) categories, with functors as 1-cells and natural transformations as 2-cells (file 34)                             |
| `Cat_{/ ℰ}`          | the (1-)category of `ℰ`-categories: pairs `(ℱ, p)` with `p : ℱ → ℰ` (file 35)                                                                 |
| `Cat^{cart}_{/ ℰ}`   | the sub-2-category with cartesian functors as 1-cells (files 35, 36)                                                                          |
| `ℰ°`                 | the opposite category of `ℰ` (used throughout files 34–38; pseudofunctors `ℰ° → Cat`)                                                         |
| `ℱ`, `(ℱ, p)`        | an `ℰ`-category, with projection functor `p : ℱ → ℰ` (file 35, VI.2)                                                                          |
| `ℱ_S`                | the fibre category of `ℱ` over `S ∈ Ob ℰ`; isomorphic to `ℱ ×_ℰ {S}` (file 35, VI.4)                                                          |
| `ℱ̃`                  | the cartesian sub-fibred-category of a fibred `ℱ`: same objects, only cartesian morphisms (file 36, VI.6.1)                                   |
| `Hom_ℰ(ℱ, 𝒢)`        | the set of `ℰ`-functors `ℱ → 𝒢` (file 35, VI.2)                                                                                               |
| `Hom_{ℰ/-}(ℱ, 𝒢)`    | the category of `ℰ`-functors and `ℰ`-natural transformations (file 35, VI.2)                                                                  |
| `Hom_{cart}(ℱ, 𝒢)`   | the full subcategory of cartesian functors (file 35, VI.5.2)                                                                                  |
| `Γ(𝒢 / ℰ)`           | sections: `Hom_ℰ(ℰ, 𝒢)` (file 35, VI.2)                                                                                                       |
| `Lim←(ℱ / ℰ)`        | cartesian sections of `ℱ` over `ℰ`: `Hom_{cart}(ℰ, ℱ)` (file 35, VI.5.5)                                                                      |
| `λ*`                 | base change along `λ : ℰ' → ℰ`: `λ*(ℱ) = ℱ ×_ℰ ℰ'` (file 35, VI.3)                                                                            |
| `f^*` (in file 36)   | the inverse-image functor `ℱ_S → ℱ_T` for `f : T → S` (chosen by a cleavage); file 35 introduces, file 36 uses                                |
| `f_*` (in file 37)   | the direct-image functor `ℱ_T → ℱ_S` for `f : T → S` (chosen by a co-cleavage); right adjoint to `f^*` in the bi-fibred case (file 37, VI.10) |
| `α_f(ξ)`             | the chosen cartesian morphism `f^*(ξ) → ξ` of a cleavage (file 36, VI.7)                                                                      |
| `c_{f, g}(ξ)`        | the coherence isomorphism `g^* f^*(ξ) → (fg)^*(ξ)` of a cleavage; the pentagon's protagonist (file 36, VI.7)                                  |
| `c^{f, g}`           | the dual coherence iso `(fg)_* → f_* g_*` for a co-cleavage (file 37, VI.10)                                                                  |
| `ϕ : ℰ° → Cat`       | a pseudofunctor; data `(ϕ(S), f^*, c_{f, g})` with pentagon (file 34, file 37)                                                                |
| `Ar(ℰ) = Hom(Δ¹, ℰ)` | the arrow category: objects are arrows of `ℰ`, morphisms are commutative squares (files 35, 36, 37, 38)                                       |
| `Δ¹`                 | the totally-ordered set `[0, 1]` viewed as a category: two objects, one non-identity arrow (files 35, 38)                                     |
| `Sh(ℰ, τ)`, `PSh(ℰ)` | sheaves / presheaves of sets on a site `(ℰ, τ)` (file 34)                                                                                     |
| `𝒰(T)`               | the category of open subsets of a topological space `T`, with inclusions as morphisms (file 38, VI.11(b))                                     |
| `ℋ(ℱ, 𝒞)`            | the category of fibre-wise functors `(F_S)` and coherence data `(φ_f)` for a cloven `ℱ`; descent-data category (file 38, VI.12.1)             |
| `φ_f`                | the natural transformation `F_T ∘ f^* ⟹ F_S` extracted from a functor `F : ℱ → 𝒞` via the cleavage (file 38, VI.12)                           |
| `i_S`                | the inclusion functor `ℱ_S → ℱ` of a fibre into the total category (file 38, VI.12)                                                           |

## Faithfully flat descent (files 40–43)

| Symbol                             | Meaning                                                                                                                                   |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `g : S′ → S`                       | a faithfully flat quasi-compact (fpqc) morphism of preschemes (files 40–43)                                                               |
| `S″`                               | the double fibre product `S′ ×_S S′` (files 40–43)                                                                                        |
| `S‴`                               | the triple fibre product `S′ ×_S S′ ×_S S′` (files 40–43)                                                                                 |
| `p₁, p₂ : S″ ⇉ S′`                 | the two projections of the double fibre product (files 40–43)                                                                             |
| `p_{12}, p_{13}, p_{23} : S‴ ⇉ S″` | the three projections of the triple fibre product onto the double fibre products (files 40–43)                                            |
| `A″`                               | the affine ring counterpart `A′ ⊗_A A′` of `S″` when `S = Spec A`, `S′ = Spec A′` (file 40)                                               |
| `A‴`                               | the affine ring counterpart `A′ ⊗_A A′ ⊗_A A′` of `S‴` (file 40)                                                                          |
| `φ : p₁^*(M′) ≃ p₂^*(M′)`          | a descent datum on a quasi-coherent module `M′` on `S′` (file 40, VIII.1)                                                                 |
| `QCoh(S′ / g)`                     | the category of pairs `(M′, φ)` of a quasi-coherent module on `S′` with a descent datum relative to `g` (file 40, VIII.1)                 |
| `R(x′)`                            | the fibre `q₂(q₁⁻¹(x′))` of the equivalence relation defined by a descent datum on `X′`, considered as a subset of `X′` (file 43, VIII.7) |
| `q₁, q₂ : X″ ⇉ X′`                 | the two projections of the descent-data equivalence pair on `X′` (file 43, VIII.7)                                                        |
| `N_f(s)`                           | the norm of a section `s ∈ Γ(X, 𝒪_X)` along a finite locally free morphism `f : X → S` (file 43, VIII.7.6)                                |
| `Norm_{q₂}`                        | the norm of a section along a finite locally free morphism `q₂` of double-fibre-product schemes; descent-compatibility tool (file 43)     |
| `Proj_S(𝒮)`                        | the relative `Proj` of a quasi-coherent graded `𝒪_S`-algebra (files 42, 43)                                                               |
| `𝓛`, `𝓛′`                          | invertible sheaves on `X` and on `X′ = X ×_S S′` respectively (files 42, 43)                                                              |

## Descent of étale morphisms and the fundamental group (files 44–47)

| Symbol                       | Meaning                                                                                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Γ_f ⊂ X ×_S Y`              | the graph of an `S`-morphism `f : X → Y`; for `Y / S` étale, an open subset with radicial-surjective first projection (file 44, IX.1.6)                |
| `Open(X)`                    | the set of open subsets of a prescheme `X`, regarded as a poset (file 44, IX.2.3)                                                                      |
| `π₀(S)`                      | the set of connected components of a prescheme `S` (file 46, IX.5)                                                                                     |
| `E′ = π₀(S′)`, `E″`, `E‴`    | the sets of connected components of `S′`, `S″`, `S‴` respectively (file 46, IX.5)                                                                      |
| `q_i = π₀(p_i)`              | the maps `E″ → E′` induced from the two projections `p_i : S″ ⇉ S′` by applying `π₀` (file 46, IX.5)                                                   |
| `q_{ij} = π₀(p_{ij})`        | the maps `E‴ → E″` induced from the three projections `p_{ij} : S‴ ⇉ S″` by applying `π₀` (file 46, IX.5)                                              |
| `v_i = π₀(u_i)`              | the three maps `E‴ → E′` induced from the three projections `u_i : S‴ ⇉ S′` (file 46, IX.5)                                                            |
| `π_{s′} = π₁(S′, \bar{s′})`  | the étale fundamental group of the connected component of `S′` named by `s′ ∈ E′`, at a chosen geometric point (file 46, IX.5)                         |
| `g_{s″}`                     | a generator of the Seifert–van-Kampen formula for `π₁(S, a)`, indexed by `s″ ∈ E″`; describes the gluing across the connected component `s″` (file 46) |
| `a_i^{s‴} ∈ π_{v_i(s‴)}`     | the cocycle elements of the descent datum on the fibred category of finite étale coverings, indexed by `s‴ ∈ E‴` and `i ∈ {1, 2, 3}` (file 46, IX.5)   |
| `n(s)`                       | the geometric number of points in the fibre `g⁻¹(s)` of a finite morphism `g : S′ → S` at `s ∈ S`; equivalently the separable degree (file 46, IX.5.4) |
| `Sym^n(X)`                   | the `n`-th symmetric power `X^n / 𝔖_n` of a scheme `X` (file 46, IX.5.8)                                                                               |
| `S′_g`                       | for `Γ` a finite group acting on `S′` and `g ∈ Γ`, the subscheme of `S′` on which `id_{S′}` and `g` agree (file 46, IX.5.8)                            |
| `π₁(S′, Γ; a′)`              | the automorphism group of the fibre functor on the Galois category `𝓒_0′` of étale coverings of `S′` equipped with a compatible `Γ`-action (file 46)   |
| `X̄_0 = X ⊗_k \bar{k}`       | the geometric special fibre of an `S`-prescheme `X` at a point `s ∈ S` with residue field `k = κ(s)` and algebraic closure `\bar{k}` (file 47, IX.6)   |

## Specialization of the fundamental group (files 48–51)

| Symbol                       | Meaning                                                                                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `X̄_y = X_y ⊗_{κ(y)} κ(y)̄`   | the geometric fibre of `f : X → Y` at `y ∈ Y`, base-changed to an algebraic closure of the residue field `κ(y)` (file 48, X.1)                          |
| `sp` or `sp_{y₀, y₁}`        | the specialization morphism `π₁(X̄_{y₁}) → π₁(X̄_{y₀})` for a specialisation `y₀ ⤳ y₁`, defined up to inner automorphism (file 49, X.2.3)              |
| `K_s`                        | the separable closure of a field `K` (used heavily in file 51 §X.3.7–3.8)                                                                                |
| `K̄`                          | the algebraic closure of a field `K`                                                                                                                    |
| `W(k)`                       | the Witt-vector ring of an algebraically closed field `k` of characteristic `p > 0`; complete DVR with residue field `k`, fraction field `K_0` of char 0 (file 50, X.2.6) |
| `G_d`                        | the decomposition subgroup of a Galois group at a chosen maximal ideal of the integral closure (file 51, X.3.6)                                          |
| `G_i`                        | the inertia subgroup of a Galois group at a chosen maximal ideal; order is the ramification index (file 51, X.3.6)                                       |
| `e_{L/K}(𝒪)`                 | the ramification index of a Galois extension `L/K` at a chosen place over the DVR `𝒪 ⊂ K` (file 51, X.3.6)                                              |
| `G^{res}`                    | the inverse limit of the finite *solvable* topological quotients of a profinite group `G`; the "solvable profinite quotient" (file 50, X.2.14)           |
| `π₁(X)^{(p)}`                | the prime-to-`p` completion of `π₁(X)`: the maximal pro-(prime-to-`p`) quotient (file 51, X.3.9–3.10)                                                    |
| `Γ`                          | the surface group on `2g` generators with one commutator relation `(s_1 t_1 s_1^{-1} t_1^{-1}) ⋯ (s_g t_g s_g^{-1} t_g^{-1}) = 1` (file 50, X.2.6)       |
| `(s_i, t_i)_{1 ≤ i ≤ g}`     | the `2g` topological generators of `π₁(X₀)` for `X₀ / k` a proper smooth curve of genus `g`; geometrically, meridians and longitudes of the `i`-th handle of the associated topological surface (file 50, X.2.6) |
| `Γ^{(p)}`                    | the prime-to-`p` quotient of the surface group `Γ`: the universal pro-(prime-to-`p`) group on `2g` generators with the commutator relation (file 51, X.3.10) |
| `X_K = X ⊗_R K`              | the generic fibre of a scheme `X / R` (`R` a DVR with fraction field `K`); cited in file 50 (X.2.6) and file 51 (X.3.7)                                  |

## Examples and complements (files 52–56)

| Symbol                                  | Meaning                                                                                                                                                          |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `μ_{n, S}`                              | the Kummer group of rank `n` over `S`: `Spec 𝒪_S[t] / (1 − t^n)`; kernel of `n`-th power on `𝔾_{m, S}` (file 56, XI.6.1)                                          |
| `α_p`                                   | kernel of Frobenius `F : 𝔾_a → 𝔾_a` over the prime field `𝔽_p`; an infinitesimal (non-étale) finite locally free group scheme of order `p` (file 56, XI.6.5)     |
| `α_{p^n}`                               | kernel of the `n`-th iterate `F^n : 𝔾_a → 𝔾_a` (file 56, XI.6.5)                                                                                                  |
| `F : 𝔾_a → 𝔾_a`                         | Frobenius morphism over a char-`p` base, `F(t) = t^p` (file 56, XI.6.4)                                                                                          |
| `wp = id − F`                           | Artin–Schreier endomorphism of `𝔾_a` in char `p` (file 56, XI.6.4)                                                                                                |
| `T_ℓ(A)`                                | `ℓ`-adic Tate module of an abelian variety `A`: `lim_r _{ℓ^r}A(k)` (file 53, XI.2.3)                                                                              |
| `T·(A)`                                 | adelic Tate module `∏_ℓ T_ℓ(A) = lim_n _nA(k)` (file 53, XI.2.3)                                                                                                  |
| `_nA`                                   | kernel of multiplication by `n` in a group scheme `A` (file 53, XI.2.3); for an abelian variety, a finite flat group scheme of order `n^{2g}`                    |
| `ν`                                     | `p`-rank of an abelian variety `A / k̄_p`: integer `0 ≤ ν ≤ dim A` with `_pA(k̄) ≃ (ℤ/p)^ν` (file 53, XI.2.4)                                                       |
| `D(G) = SheafHom_{S\text{-grp}}(G, 𝔾_m)` | Cartier dual of a finite commutative `S`-group scheme `G` (file 56, XI.6.5)                                                                                      |
| `Pic(S)`                                | Picard group `H¹(S, 𝒪_S^*)` of an `S`-scheme (file 56, XI.6.3)                                                                                                    |
| `Pic_{S / k}`                           | Picard scheme of `S / k` (file 56, XI.6.5)                                                                                                                       |
| `Pic^0_{S / k}`                         | connected component of identity in `Pic_{S/k}` (file 56, XI.6.5)                                                                                                  |
| `A^∨`                                   | dual abelian variety of `A`: `A^∨ = Pic^0_{A/k}` (file 56, XI.6.5)                                                                                                |
| `H¹(S, G)`                              | set of isomorphism classes of principal `G`-bundles over `S` (in the fpqc / descent-theoretic sense of XI.4.1); a group when `G` is commutative (file 55, XI.4.3) |
| `Ext(A, G)`                             | group of isomorphism classes of commutative extensions `0 → G → E → A → 0` of an abelian variety `A` by `G` (file 53, XI.2.1)                                    |
| `Z¹(π₁, 𝒢)`                             | set of 1-cocycles `φ : π₁ → 𝒢` (with `π₁` acting on `𝒢`) (file 55, XI.5)                                                                                          |
| `B¹(π₁, 𝒢)`                             | 1-coboundaries; `H¹(π₁, 𝒢) = Z¹ / B¹` (file 55, XI.5)                                                                                                             |
| `π₁^N(X, x)`                            | Nori fundamental group scheme of `X` pointed at `x` (file 53, XI.2.5)                                                                                            |
| `T·(Pic_{X/k})`                         | "true Tate module of `Pic`": limit `lim_i D(P_i)` over finite algebraic subgroups `P_i ⊂ Pic_{X/k}` (file 56, XI.6.5)                                            |
| `_n Pic(S)`                             | `n`-torsion in `Pic(S)`: kernel of multiplication by `n` on `Pic(S)` (file 56, XI.6.3)                                                                            |
| `H⁰(S, 𝒪_S)`, `H⁰(S, 𝒪_S^*)`           | global sections of the structure sheaf and its unit group (file 55, XI.5)                                                                                        |
| `Gr(k, n)`                              | Grassmann variety of `k`-dimensional subspaces of an `n`-dimensional vector space (file 52, XI.1.2)                                                              |
| `G/P`                                   | generalised flag variety: quotient of a connected linear group `G` by a parabolic subgroup `P` (file 52, XI.1.2)                                                 |
| `Ĉ_V`                                   | projective cone over a closed subscheme `V ⊂ ℙ^r` (file 54, XI.3.1)                                                                                              |
| `RC`, `sRC`                             | rationally connected, separably rationally connected (file 52, XI.1.4.4)                                                                                         |

## Algebraic and analytic geometry (files 57–60)

| Symbol                                  | Meaning                                                                                                                                                          |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `X^an`                                  | the complex analytic space associated with a `ℂ`-scheme `X` locally of finite type (file 57, XII.1.1)                                                            |
| `|X^an|`                                | underlying set of `X^an`; bijects to `X(ℂ) ⊂ \|X\|` via `φ` (file 57, XII.1.1)                                                                                   |
| `φ : X^an → X`                          | canonical morphism of locally-ringed-`ℂ`-spaces representing the points functor `𝒳 ↦ Hom_{LocRing/ℂ}(𝒳, X)` (file 57, XII.1.1)                                  |
| `φ_x : 𝒪_{X, φ(x)} → 𝒪_{X^an, x}`       | local map at `x ∈ X^an`; an isomorphism after passage to completions (file 57, XII.1.1)                                                                          |
| `φ̂_x : 𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}`     | completion isomorphism — the local content of XII.1.1 (file 57)                                                                                                  |
| `f^an : X^an → Y^an`                    | analytification of `f : X → Y`; the unique morphism with `φ_Y ∘ f^an = f ∘ φ_X` (file 57, XII.1.2)                                                               |
| `F^an = φ^* F`                          | analytification of an `𝒪_X`-module `F`; exact, faithful, conservative on coherent sheaves (file 57, XII.1.3.1)                                                  |
| `𝒪_𝒳`, `𝒪_{X^an}`                       | structure sheaf of an analytic space; the sheaf of holomorphic functions modulo the defining ideal                                                               |
| `Φ : Sch_{lft}/ℂ → AnSp/ℂ`              | the analytification functor `X ↦ X^an`; commutes with finite projective limits (file 57, XII.1.2)                                                                |
| `𝓔ⁿ`                                    | the analytic affine `n`-space `(ℂⁿ, 𝒪_hol)`; equals `(𝔸ⁿ_ℂ)^an` (file 57, XII.1.1.c)                                                                             |
| `𝓑`                                     | a (poly)disc / open ball in `𝓔ⁿ`; the standard Stein neighbourhood (file 59, XII.4.2)                                                                            |
| `𝒳`, `𝒴`, `𝓟`, `𝓤`, `𝓥`                 | script letters: analytic spaces (following the SGA source convention for §§XII.4–XII.5)                                                                          |
| `Spec_an(𝒜)`                            | analytic spectrum of a coherent analytic `𝒪_𝒳`-algebra; the analytic analogue of `Spec_S` for a quasi-coherent `𝒪_S`-algebra (file 60, XII.5.4–XII.5.5)         |
| `R^p f_*^an`                            | higher direct image along an analytic morphism `f^an` (file 59, XII.4.1)                                                                                         |
| `θ_p : (R^p f_* F)^an → R^p f_*^an(F^an)` | canonical comparison map for higher direct images; the GAGA datum (file 59, XII.4.1)                                                                           |
| `π_0(X)`, `π_0(X^an)`                   | set of connected components; the canonical map is a bijection by XII.2.6 (file 58)                                                                               |
| `π_1^top(X^an, x)`                      | topological fundamental group of the analytic space at a base-point `x ∈ X^an` (file 60, XII.5.2)                                                                |
| `π̂_1^top(X^an, x)`                     | profinite completion of `π_1^top(X^an, x)`; isomorphic to `π_1^ét(X, φ(x))` by XII.5.2                                                                           |
| `π_1^ét(X, a)`                          | étale fundamental group of a scheme (file 33, V.7); analytic comparison is XII.5.2                                                                               |

## Logical and categorical operators

| Symbol   | Meaning                                                  |
| -------- | -------------------------------------------------------- |
| `≃`      | isomorphism                                              |
| `≅`      | isomorphism (used interchangeably with `≃`)              |
| `⟺`      | if and only if                                           |
| `⟹`      | implies                                                  |
| `∈`      | element of                                               |
| `⊂`, `⊆` | subset of (we use `⊆` to allow equality, `⊂` for strict) |
| `∪`, `∩` | union, intersection                                      |
| `⨿`      | disjoint union or coproduct                              |
| `↦`      | "maps to" in a function definition                       |
| `:=`     | definition equality                                      |

## Étale cohomology, cohomological properness, and tame ramification (files 61–64)

| Symbol                                | Meaning                                                                                                          |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `X_et`, `X_et^∼`                      | étale site of `X`; topos of étale sheaves on `X` (XIII.B.1)                                                      |
| `f_*`, `R^q f_*`                      | étale pushforward and higher direct images (`q ≥ 0`); `R^1 f_*` makes sense for sheaves of groups (Giraud)        |
| `Φ^q : h^* R^q f_* F → R^q f'_* F'`   | base-change comparison map for a cartesian square (XIII.B.3)                                                     |
| `(F, f)` coh-proper rel. `S` in dim ≤ `n` | `n ∈ {−1, 0, 1}`: comparison functor faithful / fully faithful / equivalence under every base change (XIII.1.1) |
| `H¹_tame(U, F)`                       | subset of `H^1(U, F)` of tamely ramified torsor classes (XIII.2.1.2)                                             |
| `R¹_tame f_* F`                       | subsheaf of `R^1 f_* F` consisting of tame classes (XIII.2.1.2)                                                  |
| `π₁^tame((U, X)/S, a)`, `π₁^tame(U)`  | tame fundamental group of the open `U` relative to the compactification `X` and base `S` (XIII.2.1.3)            |
| `π₁^ℒ(X, a)`                          | maximal pro-`ℒ` quotient of `π_1^ét(X, a)` (XIII.4.0)                                                            |
| `π₁^{p'}(X)`                          | prime-to-`p` fundamental group; `ℒ = p'`                                                                         |
| `π₁'(X, a)`                           | quotient by the smallest distinguished pro-subgroup `N` of `K = Ker(π_1(X) → π_1(S))` with `K/N` pro-`ℒ` (XIII.4.0) |
| `K^ℒ`                                 | maximal pro-`ℒ` quotient of `K`                                                                                  |
| `SF`                                  | sheaf of maximal subgerbes of a stack `F` (XIII.0.3)                                                             |
| `C_t = C_t((U, X)/S)`                 | Galois category of tamely ramified étale coverings (XIII.2.1.3)                                                  |
| `wp`, `wp(a) = a^p − a`               | Artin–Schreier operator on a characteristic-`p` ring (XIII.2.13)                                                 |
| `^P F`                                | inner twist of a sheaf of groups `F` by a `F`-torsor `P` (XIII.1.3.1)                                            |
| `P ∧^F Q`                             | contracted product of a right `F`-torsor `P` and a left `F`-torsor `Q`                                           |

## Nonstandard or source-specific notation

| Symbol              | Meaning                                                                        |
| ------------------- | ------------------------------------------------------------------------------ |
| `K(A)`              | (in section I.7) the residue field `κ(A)` of a local ring                      |
| `b ∈ B`             | element of an algebra (we sometimes use `b` for ring elements rather than `x`) |
| "the multiplodocus" | Grothendieck's informal name for the larger SGA + EGA machine                  |
| **radicial**        | synonym for **universally injective** (Grothendieck's "radiciel"; file 05)     |
| **net**             | synonym for **unramified** (Grothendieck's "net"; file 04)                     |

## Cross-reference

Source labels of the form `I.x.y` (e.g., `I.5.1`) refer to the corresponding numbered statement in
`docs/books/sga/i/01-morphismes-etales.md`. Each rewritten statement in files 10, 11, 12 carries an HTML comment
recording its source label.
