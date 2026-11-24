## Step 1: Frame the problem in a proposal

Welcome back to the Contoso Health Plan delivery team, @{{ login }}! :wave: You've traced a loop, found missing rules and delivered an approved behavior. Now your lead hands you a problem nobody has specified yet and asks for a first spec by the end of the session. Copilot will be your drafting partner, but every decision in this exercise is yours.

### 📖 Theory: A proposal frames the change

An [OpenSpec change](https://github.com/Fission-AI/OpenSpec/blob/main/docs/concepts.md) is a folder under `openspec/changes/` that proposes new behavior before anyone builds it. Its `proposal.md` says **why** the change matters, **what changes**, and what is deliberately left out, the **non-goals**, so reviewers can agree on scope before they read a single requirement. Copilot can ask good questions and suggest wording, but it cannot know your business: it drafts, you decide. Where nobody knows the answer yet, write an open question instead of letting a plausible AI answer fill the gap.

Choose one of two problems. Both use fictional organizations and synthetic data only.

| | Option A: Record identification | Option B: Inbound document intake |
| --- | --- | --- |
| The problem | A lookup for Northwind Traders requests returns zero, one or several records | Fabrikam faxes arrive unreadable, incomplete, misrouted or duplicated, with a Proseware flyer mixed in |
| Intent brief | `intent/option-a-record-identification.md` | `intent/option-b-document-intake.md` |
| Change folder | `openspec/changes/add-record-identification/` | `openspec/changes/add-inbound-document-intake/` |

### ⌨️ Activity 1: Open your codespace and choose a problem

1. Right-click the button below and open it in a new tab, so you can keep these instructions open.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{ full_repo_name }}?quickstart=1)

1. On the codespace page, check that the repository is `{{ full_repo_name }}`, your copy, and not the original exercise. Then create the codespace and wait for the terminal at the bottom to report that packages were added. The first start takes about 2 to 4 minutes.

1. In the terminal, create a branch for your work.

   > ![Terminal command](https://img.shields.io/badge/Terminal-text?style=flat&logo=gnometerminal&labelColor=1f2328&color=eee)
   >
   > ```bash
   > git switch -c first-spec
   > ```

1. Read both intent briefs and choose one option. If you work in a pair, one of you plays the product owner and explains the outcome; the other restates it in their own words until you both agree.

<details>
<summary>Having trouble? 🤷</summary><br/>

- **No terminal is visible:** Open one from the editor menu with **Terminal** > **New Terminal**, or press `` Ctrl+` `` (`` ⌃` `` on Mac).

- **The codespace opened the original exercise:** Close that tab and use the button above, which points to your copy. You can also start one from your repository page: **Code** > **Codespaces** > **Create codespace on main**.

- **You can't choose:** Pick the option furthest from your daily work. An unfamiliar problem shows you which questions you skip when the domain feels obvious.

</details>

### ⌨️ Activity 2: Draft the proposal with Copilot

1. Open Copilot Chat: select the chat icon at the top of the editor, or press `Ctrl+Alt+I` (`⌃⌘I` on Mac).

1. Start the conversation with the product-owner prompt for your option. It asks Copilot to question you instead of writing a solution.

   <details>
   <summary>Option A: product-owner prompt</summary><br/>

   > ![Copilot prompt](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Read intent/option-a-record-identification.md. Do not write code or edit files.
   > Ask me to define intent, actors, scope and non-goals, then the exact matching fields
   > and normalization rules. Ask one material question at a time. Separate confirmed
   > decisions from assumptions; do not invent a unique identifier or approve anything.
   > ```

   </details>

   <details>
   <summary>Option B: product-owner prompt</summary><br/>

   > ![Copilot prompt](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Read intent/option-b-document-intake.md. Do not write code or edit files.
   > Ask me about intent, scope, document types, human responsibilities and non-goals,
   > one material question at a time. Distinguish classification, routing and attachment
   > from business decisions. Keep assumptions and unanswered questions explicit; never
   > invent approval.
   > ```

   </details>

1. Answer Copilot's questions one at a time. When you don't know an answer, say so, and keep it as an open question.

1. Create `proposal.md` in the change folder for your option, for example `openspec/changes/add-record-identification/proposal.md`. Write it with these three sections, using Copilot's suggestions only where you agree with them:

   ```markdown
   ## Why
   <!-- The problem, who it hurts and why it matters now. At least 50 characters. -->

   ## What Changes
   <!-- The behaviors this change adds, as short bullets. -->

   ## Non-goals
   <!-- What this change deliberately does not do. -->
   ```

   > 💡 **Tip:** You may add an `## Open questions` section too. Naming what you don't know is part of the work.

<details>
<summary>Having trouble? 🤷</summary><br/>

- **Copilot wrote a whole spec or code:** Ignore it and repeat the first sentence of the prompt: do not write code or edit files. You are drafting the proposal, not the solution.

- **Copilot answers without reading the brief:** Add the file to the chat: type `#` in the chat box and pick the intent brief.

- **You can't create a folder:** In the Explorer, right-click `openspec/changes`, select **New File...**, and type the whole path, such as `add-record-identification/proposal.md`. The folder is created with the file.

</details>

### ⌨️ Activity 3: Push your proposal

1. Reread your **Non-goals**. Would a reviewer know from each line what this change will not do? Sharpen any line that only restates a goal.

1. Save the file, then commit and push your branch.

   > ![Terminal command](https://img.shields.io/badge/Terminal-text?style=flat&logo=gnometerminal&labelColor=1f2328&color=eee)
   >
   > ```bash
   > git add openspec/changes
   > git commit -m "Propose my first OpenSpec change"
   > git push -u origin first-spec
   > ```

1. Go back to this issue in your browser. Wait a moment for Mona to check your work, provide feedback, and share the next lesson.

<details>
<summary>Having trouble? 🤷</summary><br/>

- **Mona says there is not exactly one change folder:** Keep one folder for your option under `openspec/changes/`. Delete any other folder you created, then commit and push again.

- **Mona says a section is missing or empty:** Check the headings: `## Why`, `## What Changes` and `## Non-goals`, each followed by your text. The **Why** section needs at least 50 characters.

- **Mona did not respond:** Check that you pushed to the `first-spec` branch and that a file under `openspec/changes/` changed. You can watch the run in the [Actions tab](https://github.com/{{ full_repo_name }}/actions).

</details>
