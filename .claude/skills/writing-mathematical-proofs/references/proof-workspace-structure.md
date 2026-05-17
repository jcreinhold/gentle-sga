# Proof Workspace Structure

Use this reference when a theorem-scale argument needs its own workspace in the filesystem.

## When to Create a Workspace

Create a dedicated theorem workspace only when:

- the argument has a theorem-scale proof architecture;
- the work needs more than one proof file;
- milestone propositions or reusable lemmas need their own notes;
- review, examples, and proof assembly need to stay visibly related.

Do not create a dedicated workspace for:

- a short proof that fits in one note;
- a one-use local lemma;
- an exploratory sketch with no stable claim yet.

## Default Layout

Start with:

```text
<theorem-slug>/
  README.md
  rapid-prototype.md
  proof-architecture.md
```

Add files only as needed:

```text
<theorem-slug>/
  README.md
  rapid-prototype.md
  proof-architecture.md
  theorem.md
  milestones/
    <milestone-slug>.md
  lemmas/
    <lemma-slug>.md
  examples.md
  review.md
```

## Placement

Place the theorem workspace in the most specific live work area that owns the question.

Do not create a proof workspace at the line root unless the theorem genuinely governs the whole line.

## File Roles

### `README.md`

This file contains:

- the theorem or claim under study;
- the current status;
- the canonical file to read first;
- a short list of the current proof spine;
- the current blocking point, if any.

### `rapid-prototype.md`

This file contains:

- the first bare-bones theorem skeleton;
- provisional theorem statements;
- candidate milestone propositions;
- candidate local lemmas;
- rough dependency notes;
- backward scratch work;
- simplified cases and discarded branches when they still inform the live search.

Create this file first.

### `proof-architecture.md`

This file contains:

- the current theorem statement;
- ambient assumptions and notation;
- milestone propositions;
- local technical lemmas;
- dependency order;
- open gaps, blocking lemmas, or stop rules;
- model examples or simplified cases only when they determine the scaffold.

Create this file after the prototype has exposed the rough shape of the argument.

### `theorem.md`

This file contains:

- the cleaned-up theorem statement;
- the assembled proof or proof sketch;
- references to milestone and lemma files as needed.

Create this file only after the theorem statement and proof spine are stable enough to present directly. Creating
`theorem.md` does not, by itself, end the project if the proved result already exposes the next best sequence.

### `milestones/`

This directory contains proposition-scale notes that:

- are conceptual turning points;
- are cited more than once;
- make the main theorem mostly formal once proved;
- or need their own review attention.

### `lemmas/`

This directory contains lemma-scale notes that:

- remove one technical obstacle cleanly;
- are reused across proofs;
- or are too large to remain inside another proof.

Do not move every short one-use subclaim into this directory.

### `examples.md`

This file contains:

- model examples;
- simplified cases;
- counterexamples;
- near-counterexamples;

only when they do theorem work for the proof architecture.

### `review.md`

This file contains:

- the review scope;
- the main findings;
- the status of each finding: resolved, deferred, or fatal.

Create this file only after adversarial review.

## Growth Order

Create files in this order:

1. `README.md`
1. `rapid-prototype.md`
1. `proof-architecture.md`
1. `theorem.md`, if the main theorem note is stable enough
1. `milestones/`, if milestone propositions need separate notes
1. `lemmas/`, if reusable or sizable lemmas need separate notes
1. `examples.md`, if examples determine the scaffold
1. `review.md`, after review

This order governs file creation, not work pacing.

Do not stop after creating `README.md`, `rapid-prototype.md`, and `proof-architecture.md` if the next research move is
clear. Once the workspace exists, keep working through the best available proof or counterexample sequence until a real
blocker, stop rule, redirect, or change of kind is reached. Do not stop after creating `theorem.md` either if that
theorem already sharpens the next best stop-rule proof, strengthening attempt, or redirect.

## Naming

Use stable top-level names:

- `README.md`
- `rapid-prototype.md`
- `proof-architecture.md`
- `theorem.md`
- `examples.md`
- `review.md`

Inside `milestones/` and `lemmas/`, use content-based slugs.

Avoid:

- `lemma-1.md`
- `misc.md`
- `temp.md`

## Scope Rule

Keep all files in the workspace about the same theorem-scale project.

If a lemma becomes important outside the workspace, move or restate it where its wider scope is accurate.
