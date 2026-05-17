# Structured Proofs: Sources and Mapping

Read this when you want the primary literature behind the structured-proof discipline named in the SKILL.md "Lemmas as
Interfaces" section, or when you need to cite specific claims. Order: Tao first (most directly applicable to writing
lemmas), then Leron (comprehensibility), then Lamport 1993 + 2012 (error prevention and the formal-proof connection).

## Tao, "Create Lemmas (and don't be afraid to invent new ones)"

Source: Terence Tao, _Advice on Writing Papers_ (blog page,
`https://terrytao.wordpress.com/advice-on-writing-papers/create-lemmas/`).

**The canonical rule:**

> One should write the statement of a lemma in a way that makes it easy to _use_, rather than easy to _prove_.

This is the deep-module-design "cost is the interface, not the implementation" applied to lemmas. Every lemma is paid
for at every citation; its statement is its interface; the cost of that interface is paid by every later argument that
has to invoke it.

**The unify-when-only-useful-together rule:**

> If you have a pair of technical lemmas, neither of which is of much interest in its own right, but only become useful
> when used together, then they should be unified into a single lemma.

This is the proof analogue of `deep-module-design`'s better-together-or-apart question: combine when information is
shared, separate when concerns vary independently.

**Other Tao prescriptions in the post:**

- Extract a lemma when the facts encapsulated will not be reused but currently force the reader to track them mentally.
- Extract when the result is likely to be important later in the paper.
- Extract to localise notation that is special to one section.
- Extract to make assumptions and conventions explicit at the point they are needed.

## Leron, "Structuring Mathematical Proofs"

Source: Uri Leron, _American Mathematical Monthly_ 90:3 (March 1983), pp. 174–185 (ERIC EJ277000).

Per the ERIC abstract: "an alternative method for arranging proofs... arranges development in levels... triggered by
recent ideas from computer science... to increase the comprehensibility of mathematical presentations while retaining
their rigor."

**The Leron-test for an LLM agent's proof:** read the proof at speed, skipping subclaim bodies. Does it still read as
mathematics? If not, the structure isn't doing its job.

Note: Lamport (1993, §1) explicitly distinguishes his hierarchical method from Leron's. Leron aims at _communication_;
Lamport aims at _correctness_. Both motivate decomposition; the goals are different.

## Lamport, "How to Write a Proof" (1993)

Source: Leslie Lamport, Digital SRC Research Report (Feb 1993, revised Dec 1993). Local copy at
`/Users/jcreinhold/Code/papers/references/lamport-how-to-write-a-proof.md`.

**Method:** hierarchical numbering `⟨n⟩k`, with each step a named claim followed by its own proof (which may itself be
hierarchical). Primitives:

- `Assume:` / `Prove:` clauses.
- `Choose ... such that ...` for existence elimination.
- `Let: x ≜ …` for definitions.
- `Case:` construct for case analysis.
- Equality chains with right-column justifications, which "should be used whenever possible" (1993 §2.2) for any
    transitive relation.
- `Q.E.D.` at every level.

**References within a proof:** `⟨n⟩k.j` denotes part `j` of step `k` at level `n`; `⟨n⟩:k` denotes the `k`-th assumption
of the level-`n` ancestor.

**Writing rule (§4.2):**

> Expand the proof until the lowest level statements are obvious, and then continue for one more level.

**Empirical claim from working with Abadi (§4.1):**

> Almost every one had serious mistakes, though the theorems were correct.

**The Schroeder-Bernstein anecdote (§4.1):** Lamport found a bug in Kelley's classic half-page proof only by rewriting
it as a structured proof; "within minutes, I rediscovered the error."

**On reading:** "the best way to read a structured proof is level by level — first reading the high-level steps ⟨1⟩1,
⟨1⟩2, ⟨1⟩3, ..., then the proofs of those steps, and so on" (§4.3).

## Lamport, "How to Write a 21st Century Proof" (2012)

Source: Leslie Lamport, _Journal of Fixed Point Theory and Applications_ 11 (2012), pp. 43–63.
(`https://lamport.azurewebsites.net/pubs/proof.pdf`)

**Method:** the 1993 method refined with primitives chosen to support the formal-proof system TLA+ / TLAPS. The new
primitives are the ones used in this skill's tactic-mapping table:

- `ASSUME : H` / `PROVE : G` — entry into an implication / new hypothesis (Lean: `intro`).
- `NEW x : T` — introduce a fresh variable (Lean: `intro x : T`).
- `SUFFICES h : P FROM …` — reduce to a stronger claim (Lean: `suffices h : P by …`).
- `PICK` — existence elimination (Lean: `obtain`).
- `CASE` — case split (Lean: `rcases`).

**Confirmation-bias warning** (the load-bearing argument for an LLM agent):

> Your natural desire to confirm what you already believe to be true will cause you to miss gaps.

**Gradual-adoption advice:** _"You can begin by just adding structure to an existing proof."_

**The "curious child" framing:** _"Every time we write an assertion, the child asks: Why?"_

## Wells, "Communicating Mathematics: Useful Ideas from Computer Science"

Source: Charles Wells, _American Mathematical Monthly_ 102:5 (May 1995). Pointer only — primary text was not retrievable
during the writing of this reference. Cited as a map of CS-into-mathematics ideas (specification, syntax/semantics,
formal transformations, types, self-monitoring), but specific claims should not be attributed to Wells without checking
the primary text.

## Patterson, "Structured proofs" bibliography

Source: Evan Patterson, `https://www.epatters.org/wiki/logic-plt/structured-proofs`. Useful as a literature map covering
Leron, Lamport, Wiedijk, Barendregt, Wells, and adjacent material on declarative-style proof languages (Mizar, Isar).

## Mapping to deep-module-design

| `deep-module-design` term      | Structured-proof analogue                               |
| ------------------------------ | ------------------------------------------------------- |
| theorem statement              | interface                                               |
| proof                          | implementation                                          |
| lemma                          | function                                                |
| Lamport step `⟨n⟩k`            | named claim with hidden body                            |
| depth ratio (impl / interface) | long-proof, short-statement                             |
| classitis                      | lemma-itis                                              |
| complecting                    | braided proof block (cases + side conditions + algebra) |
| cost is the interface          | Tao's "easy to use, not easy to prove"                  |
| pass-through method            | lemma that just renames or rewrites another             |
| design it twice                | two substantively different proof strategies            |

For the Lean-tactic realisations of Lamport's primitives, load `translating-proofs-to-lean4`.
