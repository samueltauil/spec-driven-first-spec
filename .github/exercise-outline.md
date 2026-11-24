# Exercise outline: Draft Your First Spec

## Logistics

- **Exercise title:** Draft Your First Spec
- **Repository name candidates:** `spec-driven-first-spec`, `draft-your-first-spec`, `spec-driven-capstone`
- **Recommended repository name:** `spec-driven-first-spec` — the shared `spec-driven-` prefix groups the four
  workshop exercises, and "first spec" names the outcome.
- **Learner copy name:** `skills-spec-driven-first-spec`
- **Experience level:** Intermediate (capstone)
- **Target owner:** samueltauil (assumed; confirm at publish)
- **Copyright holder:** acworkma
- **Series:** Spec-Driven Delivery workshop, exercise 4 of 4. Previous: Deliver an Approved Behavior with
  Copilot. Next: none (the learner runs the loop on a real backlog item with their team).
- **Environment:** GitHub Codespaces (Node.js 22 and the OpenSpec CLI preinstalled), Copilot Chat
- **exercise-toolkit version:** v0.9.3

## Learner

- **Persona:** A member of a mixed-role delivery team (product owner, business analyst, tester, developer or
  architect) at a fictional health plan, Contoso, who finished exercises 1 to 3: traced a loop, found missing
  rules and delivered an approved behavior with Copilot. Works alone or in a pair.
- **Can already:** Read an OpenSpec change and Given/When/Then scenarios; run strict validation; create a branch,
  commit, push and open a pull request; prompt Copilot Chat.
- **New to:** Drafting a change from a blank page for an unfamiliar problem, and making the Ready to build call
  themself.
- **Likely misconceptions:** "Strict validation passing means the spec is ready." "If Copilot says a capability
  exists, it is confirmed." "Not ready is a failure." "A rough baseline number is better than none."
- **Motivation:** Next week their team writes its own first spec for a real backlog item, and they want to lead
  it.
- **Constraints:** About 60 minutes (70 in the instructor-led agenda, with a pair swap at minute 50); no code;
  personal account with Codespaces free allowance; never paste real work items or data.
- **Access needs to design for:** Keyboard-only use of the codespace, screen readers (no information in images
  only), non-native English readers (short sentences).

## Objective and evidence

**Exercise objective:** Independently draft a candidate OpenSpec change for an unfamiliar problem, with a
proposal, at least three scenarios including edge cases that pass strict validation, and a reasoned Ready to build
decision with measures.

| Step | Objective (observable) | Activity that performs it | Evidence afterwards | Automated check (what it proves) | Not proven by the check | Feedback if it fails |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Write a proposal with why, what changes and non-goals | Choose option A or B; answer Copilot's product-owner questions; write `proposal.md`; push | `openspec/changes/<name>/proposal.md` on `first-spec` | Exactly one change folder; Why section of 50+ characters; What Changes and Non-goals sections with content | That the scope is sensible or the non-goals are real exclusions | Keep one change folder; use the three headings with your own text |
| 2 | Write requirements and 3+ scenarios with edge cases that pass strict validation | Challenge the proposal with Copilot; decide outcomes; write the delta; validate; push | `openspec/changes/<name>/specs/<capability>/spec.md` | Delta with `## ADDED Requirements`; `openspec validate <name> --strict` passes; 3+ `#### Scenario:` headings | That the scenarios cover the right edge cases or are concrete | Fix validation messages; MUST/SHALL in capitals; add edge-case scenarios |
| 3 | Record readiness and make a reasoned gate decision with measures | Copy and fill the readiness template; pressure-test; decide; open a pull request | `openspec/changes/<name>/readiness.md`; pull request to `main` | File exists; a `Decision: ready` or `not ready` line; a reason; 3+ edge cases; one measures row with five filled cells; strict validation still passes | That confirmations are honest or the decision is right | Copy the template; write one decision and a reason; fill a measures row, using `unknown — owner to provide` when needed |

## Story

Your lead at Contoso Health Plan hands you a problem nobody has specified yet: either a record lookup for
Northwind Traders requests that returns zero, one or several records (option A), or Fabrikam faxes that arrive
unreadable, incomplete, misrouted or duplicated, with a Proseware flyer mixed in (option B). By the end of the
session the team needs a first spec and an honest answer to "Is this ready to build?". Copilot drafts; you decide.

## README

- **One-line description:** Turn an unfamiliar business problem into a validated OpenSpec change, and decide
  honestly whether it is ready to build.
- **Who is this for:** Product owners, analysts, testers, developers and architects who can read an OpenSpec
  change and scenarios, ideally after exercises 1 to 3.
- **What you'll learn:** Framing a proposal, writing edge-case scenarios that pass strict validation, and making a
  reasoned Ready to build decision with measures, with Copilot as a drafting partner.
- **What you'll build:** A new OpenSpec change (proposal, spec delta, readiness record) in a pull request.
- **Prerequisites:** Comfort with branches, commits and pull requests
  ([Introduction to GitHub](https://github.com/skills/introduction-to-github)); GitHub Codespaces; Copilot Chat
  (Copilot Free is enough).
- **How long:** About 60 minutes.
- **In this exercise, you will:** (1) write a proposal with why, what changes and non-goals, (2) write
  requirements and three or more scenarios including edge cases that pass strict validation, (3) record readiness,
  measures and a ready or not ready decision in a pull request.

## Support curve and learning moves

This is the capstone, so support is faded from the start: goals, hints and tips, with one example prompt in
step 1 and the learner's own prompts afterwards. Product-owner prompts stay hidden in `<details>` as a fallback.

| Step | Support level | Retrieval or generation moment | Prediction or reflection prompt |
| --- | --- | --- | --- |
| 1 | Completion: section headings given, one example prompt per option, content generated by the learner | Generate intent, scope and non-goals from the brief | "Would a reviewer know from each non-goal what this change will not do?" |
| 2 | Independent with hints: learner writes the prompt; skeleton shows shape only | Recall GIVEN/WHEN/THEN and MUST/SHALL from exercise 2 before looking | Predict whether strict validation passes on the first try |
| 3 | Independent: goals plus hidden prompts; learner makes the gate call | Generate confirmations, edge cases, data, decision and measures | "If a material capability is still unconfirmed, what is the honest decision?" |

## Steps

### Step 1 - Frame the problem in a proposal

- **Question this step answers:** What is this change for, and what is it not?
- **Estimated learner time:** 20 minutes (including codespace start).

**📖 Theory:** An OpenSpec change is a folder under `openspec/changes/` that proposes behavior before anyone builds
it. Its `proposal.md` says why, what changes and the non-goals, so reviewers agree on scope first. Copilot drafts;
you decide; unknowns stay as open questions.

**References:** [OpenSpec concepts](https://github.com/Fission-AI/OpenSpec/blob/main/docs/concepts.md).

**⌨️ Activity 1:** Open your codespace and choose a problem (badge, confirm the repository is the learner's copy,
`git switch -c first-spec`, read both intent briefs, choose A or B; pairs restate the outcome).

**⌨️ Activity 2:** Draft the proposal with Copilot (product-owner prompt 1 for the option, answer one question at a
time, write `proposal.md` with `## Why`, `## What Changes`, `## Non-goals`; skeleton guidance in HTML comments).

**⌨️ Activity 3:** Reread the non-goals, commit and `git push -u origin first-spec`.

**Having trouble?** Codespace opened the original → use the badge; Copilot wrote a spec or code → repeat "do not
write code or edit files"; can't create the folder → New File with the whole path; Mona silent → check the branch.

**Transition**

- **Actions trigger:** `push` to branch `first-spec` with `paths: openspec/changes/**`.
- **Copy-time safety:** The copy push targets `main` only; `first-spec` does not exist in the template.
- **Grading checks (bash):** exactly one folder under `openspec/changes/` other than `archive`; the `## Why`
  section has 50+ characters (OpenSpec's own minimum for a why); `## What Changes` and `## Non-goals` (or
  `## Out of scope`) have 10+ characters. Blank lines and single-line HTML comments are ignored, so the skeleton
  alone fails. Strict validation is not run: a change without a delta always fails it.
- **Failure feedback:** one row per check; tips: keep one folder, use the three headings, push again.
- **Learner artifact:** `proposal.md` on `first-spec`.

### Step 2 - Write requirements and scenarios that catch edge cases

- **Question this step answers:** What MUST happen, including for the inputs nobody planned for?
- **Estimated learner time:** 20 minutes.

**📖 Theory:** A spec delta at `specs/<capability>/spec.md` lists rules under `## ADDED Requirements`; each
requirement uses MUST or SHALL and has at least one `#### Scenario:` with GIVEN, WHEN and THEN. Good specs cover
empty, conflicting and unexpected inputs. Strict validation checks structure, not correctness.

**References:** [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119),
[OpenSpec: writing good specs](https://github.com/Fission-AI/OpenSpec/blob/main/docs/writing-specs.md).

**⌨️ Activity 1:** Recall the scenario parts and keywords; write your own prompt to challenge the proposal (prompt 2
hidden as a fallback); decide outcomes; write the delta from a shape-only skeleton.

**⌨️ Activity 2:** Predict, run `npm run validate:spec`, fix errors, push.

**Transition**

- **Actions trigger:** same as step 1 (`push` to `first-spec`, `paths: openspec/changes/**`); only the enabled
  step workflow runs.
- **Copy-time safety:** as step 1.
- **Grading checks (bash after `actions/setup-node@v6` and `npm ci --ignore-scripts`):** exactly one change
  folder; a delta spec at `specs/*/spec.md` contains `## ADDED Requirements`;
  `npx --no -- openspec validate <name> --type change --strict --no-interactive` passes; 3+ `#### Scenario:`
  headings across the delta specs.
- **Failure feedback:** one row per check; tips: delta path and heading, validation fixes, add edge cases.
- **Learner artifact:** spec delta on `first-spec`.

### Step 3 - Decide whether your spec is ready to build

- **Question this step answers:** Is this change ready to build, and how will we know it helped?
- **Estimated learner time:** 20 minutes.

**📖 Theory:** Ready to build is a human gate: bounded scope, material questions answered by named people,
capabilities confirmed with evidence, synthetic data with a source and owner per scenario. Unconfirmed
capabilities block it; "not ready" with named blockers is respectable. Measures record what is counted, the
baseline period, source, owner and availability date; never invent a baseline.

**References:** [Creating a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

**⌨️ Activity 1:** Copy `worksheets/readiness-template.md` to the change folder as `readiness.md`; fill capability
confirmation, dependencies, three or more edge cases and synthetic data (prompt 3 hidden); downgrade unverified
confirmations to `unconfirmed`.

**⌨️ Activity 2:** Pressure-test (pair swap, or a review prompt with prompt 4 hidden); write the decision, reasons,
decision owners and missing items; fill a measures row; validate and push.

**⌨️ Activity 3:** Open a pull request from `first-spec` to `main`.

**Transition**

- **Actions trigger:** `pull_request` to `main`, types `opened`, `synchronize`, `reopened`.
- **Copy-time safety:** not a push event.
- **Grading checks (bash on `readiness.md`):** file exists in the single change folder; a line
  `Decision: ready` or `Decision: not ready` (bold markers and bullets ignored; "ready / not ready" rejected); the
  `Reasons:` label in the Decision section has 15+ characters; 3+ non-empty list items in the Edge cases section;
  1+ Measures table row (not the header or separator) with all five cells filled, where a value such as
  `unknown — owner to provide` counts; strict validation still passes.
- **Failure feedback:** one row per check; tips: copy the template, one decision and a reason, fill a measures row
  without inventing numbers, validate and push.
- **Learner artifact:** pull request with the complete change.

## Review

- **Recap (capabilities):** You can frame a change with why, what changes and non-goals; write requirements and
  edge-case scenarios that pass strict validation; record readiness and measures and make an honest gate decision.
- **Recall questions:** Does passing strict validation mean ready to build? What do you write when Copilot says a
  capability exists? What goes in the measures table when there is no baseline?
- **Transfer prompt:** With your team, write a proposal and three scenarios for a real backlog item in your own
  repository and record a Ready to build decision with named owners.
- **What's next:** Run the loop on that backlog item; OpenSpec docs on writing specs and team workflow; prompt
  engineering for Copilot Chat; more GitHub Skills exercises.

## File map

| File | Purpose |
| --- | --- |
| `.github/exercise-outline.md` | This approved outline |
| `README.md` | Landing page with the Copy Exercise button |
| `LICENSE` | MIT; copyright line feeds the README footer |
| `.github/steps/1-step.md` … `3-step.md` | Step content |
| `.github/steps/x-review.md` | Recap, recall, transfer, what's next |
| `.github/workflows/0-start-exercise.yml` | Starts the exercise, posts step 1 |
| `.github/workflows/1-step.yml` | Graded push to `first-spec` (proposal), posts step 2 |
| `.github/workflows/2-step.yml` | Graded push to `first-spec` (delta and strict validation), posts step 3 |
| `.github/workflows/3-step.yml` | Final step: graded pull request, posts the review |
| `.github/copilot-instructions.md` | Spec-driven rules for Copilot |
| `.devcontainer/devcontainer.json` | Node.js 22, `npm ci`, Copilot Chat |
| `intent/option-a-record-identification.md` | Option A intent brief (Northwind Traders) |
| `intent/option-b-document-intake.md` | Option B intent brief (Fabrikam, Proseware) |
| `openspec/specs/member-eligibility/spec.md` | Format example of a current spec |
| `openspec/changes/.gitkeep` | Keeps the empty changes folder |
| `worksheets/readiness-template.md` | Readiness record template with gate and measures guidance |
| `package.json`, `package-lock.json` | Pinned OpenSpec CLI and the `validate:spec` script |

## Test plan

- **Walkthrough personas:** product owner who has never written a requirement; developer who skims and pastes
  Copilot output.
- **Negative tests:** step 1 with two change folders, or with the skeleton pasted unchanged; step 2 with a
  requirement without MUST, or only two scenarios; step 3 with no decision line, "ready / not ready" left in, an
  empty measures cell, or CRLF line endings.
- **Environments to test:** personal account, Codespaces free allowance, Copilot Free.

## Risks and open questions

- Learners may let Copilot write the whole change in agent mode; the prompts and tips say "do not write code or
  edit files", and the review asks them to defend decisions, but no check can prove authorship.
- Checks prove structure, not quality; the readout and pair swap are where content is judged.
- Learners who rename sections (for example `## Scope exclusions`) fail the Non-goals check; the tip names the
  accepted headings.

## Future considerations

- A "bring your own fictional problem" option C with the same checks.
- A follow-up exercise that takes the pull request through the plan gate with a design and tasks.
