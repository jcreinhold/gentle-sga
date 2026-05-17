# Reading guide

Topology has a notion of covering map. A continuous surjection `E → B` is a covering when, near every point of `B`, the
source splits into a disjoint stack of copies of a neighborhood. The fibers are discrete, the local picture is trivial,
and the global picture is a finite or infinite stack of sheets that twist over `B` in a controlled way. Once you have
covering maps, you have the fundamental group, you have monodromy, you have classical Galois theory of unbranched
covers.

Algebraic geometry, in 1960, did not have its version. The objects were rings — or, after Grothendieck, schemes — and
the natural morphisms were ring maps in reverse. Some of these morphisms were clearly "covering-like": a finite
separable field extension, an unramified extension of number rings, the projection of a non-singular curve to its base.
Others were not, and the boundary was not visible from the algebra. There was no single condition that picked out
exactly the right class.

Exposé I of SGA 1 picks out that class. The condition is called **étale**, and the phrase that describes it is "the
algebro-geometric analogue of a local isomorphism." An étale morphism has finite fibers, has no first-order
infinitesimal slack along those fibers, and varies without algebraic jumps as you move on the base. Each clause is an
algebraic condition extracted from the minimum data the ring map provides. The conjunction is rigid enough to force the
behaviour you want from a covering map and loose enough to admit the examples — separable extensions, unramified covers,
the open locus of a finite map — that any reasonable definition has to admit.

This project is a gentle reader's companion to that exposé. The source — Grothendieck, _Séminaire de Géométrie
Algébrique du Bois Marie_ 1, _Revêtements Étales et Groupe Fondamental_ — is short and fast. It assumes EGA-level
fluency in scheme theory, sheaf theory, and commutative algebra. We assume categories and rings. The change is in pace
and in what we explain. We define every technical term before we use it, give intuition before each formal statement,
and reach for concrete examples whenever they pin a definition down. The mathematics is the mathematics of Exposé I. We
do not paraphrase results into vague slogans. The theorems are stated exactly. Some proofs are reproduced in full;
others are sketched, with honest pointers to the larger machine they rely on.

## If you are not a mathematician

Each exposé file opens with a short section titled **What this file is about**, written in plain English with no
mathematical symbols. The path through these sections — file by file, from 01 to 64 — gives a coherent narrative arc
through SGA 1 that does not require fluency in algebraic geometry. A reader can stop at the first technical heading in
each file and still understand what was at stake, what was discovered, and how the result connects to the rest of the
seminar. The interiors are graduate-level by intent; the openings are not.

## Who this is for

You should be comfortable with sets, functions, and equivalence relations; with groups, rings, ideals, quotient rings,
and fields; with vector spaces and tensor products at the level of a first algebra course; and with basic category
theory — objects and morphisms, functors, natural transformations, universal properties, limits and colimits, and
pullbacks in particular.

You do not need schemes, sheaves, local rings beyond the bare definition, noetherian rings, flatness, unramifiedness,
Kähler differentials, completions, normality, Nagata rings, formal schemes, or étale fundamental groups. Each of these
is built when it first becomes necessary.

## How the files are arranged

Files 01–06 are the preparation arc. They build, from the ring side, the geometry of `Spec A`, the dictionary that
translates ring operations into geometric ones, the first-order infinitesimal data carried by Kähler differentials, and
the four-step hierarchy quasi-finite ⇒ unramified ⇒ étale ⇒ open immersion. By the end of file 06 you have the substance
of Exposé I in a more leisurely order. Files 10–12 are the rewritten Exposé I itself, presenting sections I.1–I.11 of
the source in the same gentle style, with proofs in detail. Files 14–16 extend the project to Exposé II (smooth
morphisms): II.1–II.5 in the same voice, reusing the preparation arc and citing Exposé I rather than redeveloping it.

Files 17–18 are extra preparation specific to Exposé III. They develop sheaf cohomology in low degrees, torsors, the
tangent sheaf, and formal schemes — the machinery the deformation-theoretic arguments of §§5–7 rely on. A reader who
only wants Exposés I and II can skip them; a reader who wants Exposé III should read 17–18 before 19–22. Files 19–22
then rewrite Exposé III itself (extension properties of smooth morphisms): III.1–III.7 in the same gentle style, citing
the new prep where it lands.

File 23 is extra preparation specific to Exposé IV. It develops the Tor functor (the left-derived functor of the tensor
product), the spectral sequence for composite functors in its low-degree five-term form, and Noether's normalization
lemma — the conceptual machinery the rewrite of §§5–6 leans on. A reader who only wants Exposés I, II, III can skip it;
a reader who wants Exposé IV should read 23 before 24–27. Files 24–27 then rewrite Exposé IV itself (flat morphisms):
§§1–6 in the same gentle style, opening the flatness black boxes that the étale and smooth theories have been leaning on
since file 04.

Files 28 and 29 are extra preparation specific to Exposé V. File 28 develops the topological covering-space picture and
the topological fundamental group `π₁^top` — the geometric analogy that the algebraic story of files 30–33 generalises.
File 29 develops profinite groups, pro-objects of a category, strict epimorphisms / monomorphisms, and connected objects
in a category — the categorical and topological-algebra toolkit used throughout the §§4–6 axiomatic theory. A reader who
only wants Exposés I–IV can skip them; a reader who wants Exposé V should read 28–29 before 30–33. Files 30–33 then
rewrite Exposé V itself (the fundamental group: generalities): §§1–9 in the same gentle style, building the **étale
fundamental group `π₁(S, a)`** that has been forward-referenced from files 05, 06, 22, and 27.

File 34 is extra preparation specific to Exposé VI. It introduces sites and Grothendieck topologies (a vocabulary for
"covers and gluing"), the 2-category `Cat` (so that pseudofunctors are well-typed), and pseudofunctors `ℰ° → Cat` with
their coherence pentagon. A reader who only wants the geometric exposés (I–V) can skip file 34; a reader who wants
Exposé VI should read it before files 35–38. Files 35–38 then rewrite Exposé VI itself (_Catégories fibrées et
descente_): §§1–5 (file 35: categories over a base, cartesian morphisms), §§6–7 (file 36: fibred categories, cleavages,
coherence), §§8–10 (file 37: pseudofunctors, split categories, co-fibred and bi-fibred), §§11–12 (file 38: examples, the
descent isomorphism `Hom(ℱ, 𝒞) ≅ ℋ(ℱ, 𝒞)`). The framework Exposé VI develops is what the étale story has been quietly
leaning on every time it has invoked [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) ("faithfully flat
descent") since file 30 V.2.6. Files 34–38 deliver that framework; files 40–43 then specialise it geometrically to
faithfully flat descent of quasi-coherent modules, affine schemes, properties of morphisms, morphisms in `Sch`, and the
effectivity criteria (Exposé VIII). Files 44–47 then complete the loop on descent of *étale* morphisms (Exposé IX): the
**topological invariance of the étale site** under finite radicial surjective base change, the **Seifert–van-Kampen
formula** for `π₁` of a prescheme, and the **fundamental exact sequence** `1 → π₁(X̄_0) → π₁(X) → π₁(S) → 1` for `X → S`
proper surjective with geometrically connected fibres. With files 44–47 in place, every `bourbaki-sem-190` citation in
files 30, 31, 33 refers to developed mathematics. Files 48–51 then carry the story into Exposé X: the **homotopy exact
sequence** `π₁(X̄_y) → π₁(X) → π₁(Y) → e` for a proper separable morphism, the **specialisation morphism**
`sp : π₁(X̄_{y₁}) → π₁(X̄_{y₀})` on the étale fundamental group, the **transcendental method** for the fundamental group
of a proper smooth curve, and the **continuity theorem** for proper smooth morphisms (the specialisation morphism is an
isomorphism on prime-to-`p` quotients). Files 52–56 then carry the story into Exposé XI: the computation `π₁(ℙ^r) = 0`
and its consequences (rational and rationally connected varieties), the **Serre–Lang theorem** `π₁(A) ≃ T·(A)` for
abelian varieties and the gentle treatment of Nori's true fundamental group scheme, the projective-cone and
Zariski-Fermat-surface counterexamples to the separability hypotheses of Exposé X, the descent-theoretic framework for
**principal homogeneous bundles** and the six-term cohomology exact sequence, and the **Kummer** and **Artin–Schreier**
theories culminating in the **Cartier-duality master formula** `H¹(S, G) ≃ Hom(D(G), Pic_{S/k})`. Files 57–60 then carry
the story into Exposé XII (GAGA): the analytification functor `X ↦ X^an` and its representing universal property, the
property dictionaries between schemes and their analytifications and between morphisms and their analytifications, the
**relative GAGA theorem** comparing coherent cohomology on a proper `ℂ`-scheme and on its analytification, and the
**Riemann existence theorem** identifying finite étale coverings of `X` with finite étale coverings of `X^an` — with the
`π_1` corollary `π_1^ét(X) ≃ π̂_1^top(X^an)` that underwrites the transcendental method of file 50. The gentle SGA
project — as of files 52–60 — now covers Exposés I, II, III, IV, V, VI, VIII, IX, X, XI, XII; Exposé XIII (proper
cohomological base change) of SGA 1 remains as a future gentle pass.

| File                    | What it covers                                                                                  |
| ----------------------- | ----------------------------------------------------------------------------------------------- |
| 00                      | This reading guide.                                                                             |
| 01                      | Categories, rings, locality, base change.                                                       |
| 02                      | From rings to schemes: `Spec A`, points, fibers, families.                                      |
| 03                      | Sheaves, differentials `Ω¹_{X/Y}`, infinitesimal neighborhoods.                                 |
| 04                      | The hierarchy `quasi-finite ⟸ unramified ⟸ étale ⟸ finite étale, open immersion`.               |
| 05                      | Main properties of étale: open-immersion criterion, lifting, local form.                        |
| 06                      | Permanence, normality, étale coverings of normal schemes.                                       |
| 10                      | Rewritten Exposé I, sections I.1–I.4.                                                           |
| 11                      | Rewritten Exposé I, sections I.5–I.8.                                                           |
| 12                      | Rewritten Exposé I, sections I.9–I.11.                                                          |
| 14                      | Rewritten Exposé II, sections II.1–II.2 (smooth morphisms and criteria).                        |
| 15                      | Rewritten Exposé II, sections II.3–II.4 (permanence and differentials).                         |
| 16                      | Rewritten Exposé II, section II.5 (case of a base field).                                       |
| 17                      | Prep for Exposé III: sheaf cohomology in low degrees, torsors, the tangent sheaf.               |
| 18                      | Prep for Exposé III: formal schemes and 𝓘-adic completion.                                      |
| 19                      | Rewritten Exposé III, sections III.1–III.2 (formally smooth, lifting characterization).         |
| 20                      | Rewritten Exposé III, sections III.3–III.4 (local infinitesimal extension).                     |
| 21                      | Rewritten Exposé III, sections III.5–III.6 (global extension; H¹/H² obstructions).              |
| 22                      | Rewritten Exposé III, section III.7 (algebraization over complete local rings).                 |
| 23                      | Prep for Exposé IV: Tor, the spectral sequence for composite functors, Noether normalization.   |
| 24                      | Rewritten Exposé IV, sections IV.1–IV.2 (sorites on flat modules; faithfully flat).             |
| 25                      | Rewritten Exposé IV, sections IV.3–IV.4 (completion is flat; flatness vs freeness).             |
| 26                      | Rewritten Exposé IV, section IV.5 (the local flatness criterion).                               |
| 27                      | Rewritten Exposé IV, section IV.6 (constructibility, open morphisms, generic flatness).         |
| 28                      | Prep for Exposé V: topological covering spaces and `π₁^top` (the geometric analogy).            |
| 29                      | Prep for Exposé V: profinite groups, pro-objects, strict epi/mono, connected objects.           |
| 30                      | Rewritten Exposé V, sections V.1–V.2 (quotients, inertia, principal coverings).                 |
| 31                      | Rewritten Exposé V, sections V.3–V.4 (étale automorphisms; the axiomatic Galois theorem).       |
| 32                      | Rewritten Exposé V, sections V.5–V.6 (Galois categories; exact functors and continuous homs).   |
| 33                      | Rewritten Exposé V, sections V.7–V.9 (the étale fundamental group `π₁(S, a)`; closing).         |
| 34                      | Prep for Exposé VI: sites, sheaves on a site, 2-categories, pseudofunctors `ℰ° → Cat`.          |
| 35                      | Rewritten Exposé VI, sections VI.1–VI.5 (categories over a base; cartesian morphisms).          |
| 36                      | Rewritten Exposé VI, sections VI.6–VI.7 (fibred categories; cleavages and coherence).           |
| 37                      | Rewritten Exposé VI, sections VI.8–VI.10 (pseudofunctors; split categories; co/bi-fibred).      |
| 38                      | Rewritten Exposé VI, sections VI.11–VI.12 (examples; the descent isomorphism; closing).         |
| 40                      | Rewritten Exposé VIII, section VIII.1 (descent of quasi-coherent modules).                      |
| 41                      | Rewritten Exposé VIII, sections VIII.2–VIII.4 (affine descent; properties; topology).           |
| 42                      | Rewritten Exposé VIII, sections VIII.5–VIII.6 (descent of morphisms; finite-fibre Zariski).     |
| 43                      | Rewritten Exposé VIII, section VIII.7 (effectivity criteria; closing).                          |
| 44                      | Rewritten Exposé IX, sections IX.1–IX.2 (étale reminders; submersive morphisms).                |
| 45                      | Rewritten Exposé IX, sections IX.3–IX.4 (descent of étale morphisms; effectivity criteria).     |
| 46                      | Rewritten Exposé IX, section IX.5 (`π₁` via Seifert–van-Kampen).                                |
| 47                      | Rewritten Exposé IX, section IX.6 (fundamental exact sequence; Stein factorisation).            |
| 48                      | Rewritten Exposé X, section X.1 (the homotopy exact sequence for a proper separable morphism).  |
| 49                      | Rewritten Exposé X, sections X.2.1–X.2.5 (semicontinuity of fibre `π₁`; drop counterexamples).  |
| 50                      | Rewritten Exposé X, sections X.2.6–X.2.14 (transcendental method; finite generation; Tamagawa). |
| 51                      | Rewritten Exposé X, section X.3 (continuity theorem via purity and Abhyankar's lemma).          |
| 52                      | Rewritten Exposé XI, section XI.1 (projective spaces, unirational and rationally connected).    |
| 53                      | Rewritten Exposé XI, section XI.2 (abelian varieties, Tate module, true `π₁` / Nori).           |
| 54                      | Rewritten Exposé XI, section XI.3 (projective cones; Zariski's flat counterexample).            |
| 55                      | Rewritten Exposé XI, sections XI.4–XI.5 (principal bundles in fpqc sense; GL_n / 𝔾_m / 𝔾_a).    |
| 56                      | Rewritten Exposé XI, section XI.6 (Kummer and Artin–Schreier; Cartier-duality master formula).  |
| 57                      | Rewritten Exposé XII, section XII.1 (the analytification functor `X ↦ X^an`).                   |
| 58                      | Rewritten Exposé XII, sections XII.2–XII.3 (property dictionaries for schemes and morphisms).   |
| 59                      | Rewritten Exposé XII, section XII.4 (cohomological GAGA; equivalence of coherent categories).   |
| 60                      | Rewritten Exposé XII, section XII.5 (Riemann existence theorem; `π_1^ét ≃ π̂_1^top`).            |
| glossary.md             | Every technical term, in plain English.                                                         |
| notation.md             | Every symbol, with a description.                                                               |
| appendix-black-boxes.md | Black-box theorems cited but not proved, with statement, role, and source.                      |

A reader new to the material should read in order. A reader who already knows scheme theory through fibers and base
change can skip 01–03 and start at 04. A reader who only wants to consult the gentle exposés themselves can read 10–12
(Exposé I), 14–16 (Exposé II), 19–22 (Exposé III; preceded by 17–18 if the cohomology of §§5–7 is unfamiliar), 24–27
(Exposé IV; preceded by 23 if Tor is unfamiliar), 30–33 (Exposé V; preceded by 28–29 if topological covering theory or
profinite groups are unfamiliar), 35–38 (Exposé VI; preceded by 34 if Grothendieck topologies and pseudofunctors are
unfamiliar), 40–43 (Exposé VIII; preceded by 24–27 and 35–38, since the file leans on flatness and on the descent
isomorphism VI.12.1), and 44–47 (Exposé IX; preceded by 30–33 and 40–43, since the file leans on the étale fundamental
group and on the Exposé VIII descent machinery), dipping back into the preparation files when a term is unfamiliar; the
glossary points back into the body. Read the preparation files lightly the first time. Most of their vocabulary becomes
meaningful only once it is in use. The exposés build cumulatively: read files 10–12 before 14–16, and 14–16 before
19–22, and 19–22 before 24–27 (Exposé IV opens the flatness boxes that the étale and smooth theories have been treating
as black since file 04), and 24–27 before 30–33 (Exposé V builds the étale fundamental group `π₁(S, a)` that has been
forward-referenced since file 05). Exposé VI (files 34–38) is structurally orthogonal to the geometric arc — it provides
the fibred-category framework that supports the descent technique used throughout files 30–33; it can be read after
Exposé V or after Exposé IV without missing geometric context.

## Conventions

We follow Grothendieck's term **prescheme**, which in modern language is what most people call a **scheme**. The
distinction matters mostly for separation hypotheses, and we say so when it does. We keep the French word **étale**,
with the accent. We use **net** alongside **unramified** until both feel natural.

Some sections include asides marked `#### Aside (… analogy).` These point at parallels in adjacent subjects — dependent
type theory, elaboration, Rust trait resolution — for readers who already know that material. They are optional. The
mathematics does not depend on them; the surrounding sentences read coherently if the asides are skipped. Each aside
starts with an italic skip line that names the prerequisite, so a reader can decide quickly whether to read on or move
past.

Notation is plain Unicode mathematics. Tensor product is `⊗`. Spectrum is `Spec`. Maximal ideals are `𝔪` or `𝔫`, prime
ideals `𝔭` or `𝔮`, residue fields `κ(x)`. The diagonal is `Δ_{X/Y}`. The sheaf of relative Kähler differentials is
`Ω¹_{X/Y}`. We do not use LaTeX commands. Anywhere we write `Spec A` you can read "the geometric object whose ring of
functions is `A`," and that is exactly what it will mean.

## A note on voice

The original is sharp, sometimes wry, and freely jumps between local algebra and global geometry. We keep that movement.
Where Grothendieck calls a long bookkeeping step "farcical" or refers to the larger SGA-EGA machine as the
"multiplodocus," we keep the spirit and explain the reference. The mathematics is what matters; we do not flatten it
into textbook prose.

## Borrowed from later chapters

A handful of terms appear in the gentle SGA as forward-references — we use them honestly to motivate the étale theory,
but their construction belongs to a later exposé or a different book. A first-time reader can nod past them. If you want
the construction:

- **Étale fundamental group `π₁^ét(X, x̄)`** appears in file 06's closing note and is now the centerpiece of files
    28–33. The functor "finite étale coverings of a connected scheme `X`" is pro-representable, and `π₁^ét(X, x̄)` is
    the pro-representing profinite group, generalizing the Galois group of a field. Constructed in SGA 1 Exposé V
    (rewritten gently in files 30–33); modern reader's-companion accounts that parallel the rewrite: Lenstra, _Galois
    Theory for Schemes_ (Chs. 3–6); Cadoret (or Murre), _Galois Categories_ (Chs. 2–6). The appendix entries
    [`lenstra-galois-theory-schemes`](appendix-black-boxes.md) and
    [`murre-cadoret-galois-categories`](appendix-black-boxes.md) collect the cross-references.
- **Absolute Galois group `Gal(k^sep / k)` of a field** appears in file 05 story 3. Classifies finite separable
    extensions of `k` via the main theorem of (infinite) Galois theory. The case `k = 𝔽_q` (Frobenius generates `ℤ̂`) is
    the only one we use, and is summarized in a sidebar in file 05. Full account: Lenstra, _Galois Theory for Schemes_
    §2.
- **Sheaf pullback `f*`** appears in file 03's "Two exact sequences for `Ω¹`." We give the affine-local definition
    there. Full treatment: Vakil, _Rising Sea_ §2.7 (inverse image of a sheaf) and §14.5 (pullback of a quasi-coherent
    sheaf, with three perspectives); the EGA source is 0_I §3.5–§4.3.
- **Depth and Cohen-Macaulay** appear in file 06. We give the slicing intuition and definition there. Full account:
    Vakil, _Rising Sea_ §26.1–§26.2; the EGA source is 0_IV §16.
- **Cohen rings and coefficient fields** appear in file 22 for Exposé III's algebraization story. We define them inline
    there. Full account: EGA 0_IV §19.6, §19.8; for Witt vectors as the prototypical mixed-characteristic Cohen ring see
    Serre, *Local Fields* Ch. II.
- **Grothendieck's existence theorem** for coherent sheaves on a proper scheme over a complete base appears in files 18,
    21, 22. We state it as a black box. Full account: EGA III §5.4.1; modern exposition in Vakil, _Rising Sea_ Ch. 28
    (the Theorem on Formal Functions, of which the existence theorem is the algebraization upgrade).
- **Torsors and `H¹` non-abelian cohomology** appear in file 17, and are used heavily in files 21–22. We give the
    working definition there. Full account: Giraud, _Cohomologie non abélienne_ (Springer 1971); Milne, _Étale
    Cohomology_ Ch. III §4.
- **Deformation theory** in textbook form is the modern home of Exposé III §§5–7. We do not cite it inline. Reader's
    reference: Sernesi, _Deformations of Algebraic Schemes_ (Springer 2006); Hartshorne, _Deformation Theory_ (Springer
    2010).
- **Bourbaki, _Algèbre Commutative_, Chap. I (Modules plats)** is the canonical alternative source for §§1–2 of Exposé
    IV. SGA 1 IV explicitly cites it in its opening footnote. We reproduce the needed sorites in files 24–25; readers
    who want the noncommutative- base-ring version should open Bourbaki directly.
- **EGA IV §§11–12** carry out the systematic study of the fibers of `X → Y` locally of finite type with a coherent
    sheaf flat over `Y` — fiber dimension, cohomological dimension, depth, Bertini- and Seidenberg-type theorems for
    hyperplane sections. SGA 1 IV.0 flags this as the long-form sequel. Out of scope here; cited as a black-box pointer
    in file 24.
- **Cartan-Eilenberg, _Homological Algebra_** is the canonical source for the Tor functor as a derived functor and for
    the spectral sequence of a composite functor (XV.5). Modern alternative: Weibel, _Introduction to Homological
    Algebra_ (chapters 3 and 5). File 23 cites both as black boxes for the derivations of the constructions.
- **Vistoli, _Notes on Grothendieck topologies, fibered categories and descent theory_** (in _FGA Explained_, AMS 2005;
    arXiv math/0412512) is the canonical modern long-form treatment of SGA 1 VI + VIII + IX. Vistoli §2.3 develops
    Grothendieck topologies (the source for file 34 Module A); §3.1 develops fibred categories and the cleavage /
    pseudofunctor 2-equivalence (the source for files 35–37); §3.2 develops the QCoh fibred category (the running
    example in file 34 Module C and the closing pointer of file 38); Ch. 4 covers descent for quasi-coherent sheaves and
    stacks (the geometric content of the deferred Exposés VIII–IX). Cited throughout files 34–38 as
    [`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained).
- **Mac Lane, _Categories for the Working Mathematician_**, Ch. VII §2 is the standard reference for the coherence
    theorem for monoidal / 2-categorical data: pentagon plus normalisation imply every coherence diagram commutes. Cited
    in files 34 and 37 as [`mac-lane-coherence`](appendix-black-boxes.md#mac-lane-coherence).

These pointers cover every concept the gentle SGA invokes but does not develop. The étale story itself — files 01
through 12 — is self-contained. Files 14–16 add the smooth story; files 17–22 add the formal-smooth and lifting story;
files 23–27 open the flat story, with file 23 supplying the Tor / spectral-sequence / Noether-normalization machinery
that §§5–6 lean on; files 28–33 build the étale fundamental group, with files 28–29 supplying the topological
covering-space picture, profinite groups, and pro-objects of a category. Files 34–38 then add the abstract descent
framework — fibred categories, cleavages, pseudofunctors, and the descent isomorphism (VI.12.1) — with file 34 supplying
the sites, sheaves, and 2-categorical prep.

Begin with file 01.
