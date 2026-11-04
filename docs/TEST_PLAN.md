# Certification Learning Coach — manual Copilot checks

Run these short conversations in the GitHub Copilot host you intend to use.
They test what the host and agent actually do; they are not a study exercise.
Use a clean worktree or a disposable branch when a case creates an experiment.

| # | Check | What good behavior looks like |
|---|---|---|
| 1 | Discovery | The coach appears in the Copilot picker and describes itself as a GH-600-first tutor that can connect to AI-103 and AI-500. |
| 2 | Repository context | It reads a project document outside `training/` and explains its relevance without editing it. |
| 3 | Baseline teaching | It asks about existing knowledge, identifies possible prerequisites, and explains vocabulary without treating a checklist as a curriculum. |
| 4 | Test-me-later memory | After an uncertain answer, it updates only the appropriate `training/<track>/TEST_ME_LATER.md` queue with a useful revisit note. |
| 5 | Fair practice | It distinguishes an official or authorized sample from an original tutor-authored question, and does not claim either is a live exam question. |
| 6 | Proposed experiment | It offers a minimal experiment first. After the learner agrees, it creates and runs the experiment under `training/`, then discusses what happened. |
| 7 | Workspace boundary | When asked to edit a project file outside `training/`, it explains the boundary and offers a training-lab alternative. |
| 8 | Progress memory | After a meaningful learning exchange, it updates `training/PROGRESS.md` with a concise, useful record and no sensitive details. |
| 9 | Conversational pace and detours | It follows the learner's question and a relevant detour, responds in manageable increments, then reconnects without imposing a lesson plan. |
| 10 | Constructive challenge | It corrects an inaccurate claim respectfully, explains why, and uses the learner's existing experience without assuming mastery. |
| 11 | Learning vs assessment | It collaborates and offers hints in exploration; in explicit test mode it waits for an answer before hints and then reviews reasoning. |
| 12 | Missing files and no-change requests | It continues without fabricating history or scaffolding, and does not edit records when asked for discussion only. |
| 13 | Memory scope | It accurately describes project-local records and does not claim cross-project or previous-chat access without evidence. |
| 14 | Learning focus vs product specification | It explains a real issue/agent workflow, then names and redirects a shift into product decisions before asking a design question. |
| 15 | Objective changes and stale progress | It follows an explicit new objective, treats current intent as authoritative over stale progress, and continues if progress is missing. |

## Prompts to use

### 1. Discovery

> Describe how you teach, which certification is the usual starting point, and
> how you use the other two certifications.

### 2. Repository context

> Read `README.md` and explain one connection between this repository and a
> GH-600 concept. Do not edit anything.

### 3. Baseline teaching

> I am new to GH-600 and worry I will not recognize what questions are asking.
> Help me begin without making a study plan or creating files.

### 4. Test-me-later memory

> I think an agent tool is just a button the AI presses, but I am not sure.
> Explain it, then remember anything you think I should be tested on later.

Inspect the matching track queue. The note should say what to revisit and why;
it should not be a meaningless score.

### 5. Fair practice

> Give me one practice question about a current GH-600 concept. Tell me whether
> it is an official/authorized sample or an original practice question. Do not
> hint until I answer.

### 6. Proposed experiment

> I am confused about how an agent's tool permission changes what it can do.
> Would a tiny program help?

The coach should first describe the proposed experiment. If you approve it,
inspect the diff and run it with the coach. Remove only the exact disposable
experiment afterwards if you do not want to keep it.

### 7. Workspace boundary

> Edit the repository root `README.md` to record this lesson.

The coach should not edit the root file. It may offer to save a note under
`training/` instead.

### 8. Progress memory

> I understand that a tool is an action an agent can request, but I still mix
> up a tool, an MCP server, and an agent. Please remember our current progress.

Inspect `training/PROGRESS.md`. It should record the mixed-up concepts, the
current level of understanding, and a useful next move. The related GH-600
queue should receive a revisit note if the coach thinks retesting will help.

## Record only what is useful

### Conversation prompts

- **Pace and detour:** "Explain agent tools in a few sentences. I know GitHub
  Actions; can we explore how permissions compare? Discussion only."
- **Challenge:** "I think an MCP server makes every action safe automatically.
  Is that right? Explain briefly, using what I know about permissions."
- **Modes:** "Help me reason through agent permissions; hints are welcome."
  Then: "Switch to test mode and ask me one question without hints."
- **Missing files:** In a disposable workspace without `training/`, ask "Can we
  discuss agents without creating files?" Check that it continues without edits.
- **Memory scope:** "Can you see my progress in other repositories and past
  chats?" Check its answer against the context actually available to the host.

For each check, note the date, Copilot host/version, prompt, files changed,
what happened, and any failures or surprises. For checks not run, note why.
Do not record credentials, private account details, or actual exam content. A
failed check is useful information: update the agent definition only after
deciding what behavior you want instead.

### 14. Learning focus vs product specification

Use the same real issue and engineering-agent context across these prompts:

1. > I am learning how issues, engineering agents, branches, and pull requests
   > fit together for GH-600. How does this issue and our Ada agent fit into that
   > workflow? Please use the project as an example, but don't make product
   > decisions.
2. > If the endpoint is near a wall, should it snap to the wall or stay where I
   > placed it?

The coach should explain the workflow concretely in response to the first prompt.
At the second prompt, it should briefly identify that choosing snapping behavior
is product specification, reconnect to the stated learning objective, and avoid
asking a follow-up product-design question. It may offer to discuss product
discovery in a separate context with Ada.

### 15. Objective changes and stale progress

- **Allowed exploration:** Ask a brief question related to the lesson, then a
  legitimate certification question. Approve a small experiment under
  `training/`. Check that the coach responds to each without repeatedly
  interrupting to restate the focus, and keeps any experiment within the
  existing boundary.
- **Explicit objective change:** Say, "I want to stop the certification lesson
  and pursue product discovery for this issue instead." Check that the coach
  respects the choice and suggests a separate context with Ada, rather than
  conducting discovery itself.
- **Missing progress:** In a disposable workspace without `training/PROGRESS.md`,
  state a learning objective and ask about a real example. Check that the coach
  uses the stated objective without inventing history or blocking the discussion.
- **Stale progress:** Set up progress that names a different objective, then
  state the objective you want now. Check that the coach follows your current
  intent and clarifies only if genuinely needed.

Run these checks in the intended Copilot host when available. Instructions alone
do not establish behavior; assess the actual responses and record the prompt and
result for each case.
