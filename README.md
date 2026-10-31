# Certification Learning Coach

The Certification Learning Coach is a GitHub Copilot custom agent for learning
GH-600, AI-103, and AI-500 by talking, testing, researching, and building small
experiments together. GH-600 is the default starting point; AI-103 and AI-500
are brought in when they make an idea clearer or deeper.

It is a free-form learning companion, not a workflow-compliance agent. It reads
the current project for context, but creates and runs its notes and experiments
only under the project's `training/` directory.

This repository is an initial draft. It has been loaded successfully by the
GitHub Copilot CLI, but its behavior has not yet been validated end to end in
the VS Code agent picker.

## Contents

| Path | Purpose |
|---|---|
| `agents/certification-learning-coach.agent.md` | The agent definition. |
| `training-template/` | Blank starter files that become a project's `training/` directory. |
| `docs/TEST_PLAN.md` | Short manual checks of the coach's actual behavior. |
| `docs/COMPONENT_LAYOUT.md` | Where each piece lives once installed, and naming for future components. |
| `docs/INSPIRATION_RESOURCES.md` | Index of the per-certification inspiration shelves. |
| `docs/AGENTS_SNIPPET.md` | Optional text for a project's `AGENTS.md`. |

## Install

The coach always works in the current project's `training/` directory, so every
project you study in needs its own copy of `training-template/`, whichever way
you install the agent.

Run these commands on the machine where the Copilot harness runs. For a VS Code
Remote-SSH setup, that is the remote machine, not the laptop running the UI.

```bash
git clone https://github.com/TimmyTheTurtle/certification-learning-coach.git
COACH=$PWD/certification-learning-coach
```

### Option 1 — one project (recommended)

```bash
cd /path/to/your-project
mkdir -p .github/agents
cp "$COACH/agents/certification-learning-coach.agent.md" .github/agents/
cp -r "$COACH/training-template" training   # skip if training/ already exists
```

Optionally, add the text in [`docs/AGENTS_SNIPPET.md`](docs/AGENTS_SNIPPET.md)
to the project's `AGENTS.md` so other project rules don't conflict with the
coach's training-only work.

### Option 2 — your user account

```bash
mkdir -p ~/.copilot/agents
cp "$COACH/agents/certification-learning-coach.agent.md" ~/.copilot/agents/
```

Then copy `training-template/` to `training/` in each project you study in.

If a `training/` directory already exists, merge the template by hand instead of
overwriting your notes, `PROGRESS.md`, or `TEST_ME_LATER.md` queues.

`training-template/.gitignore` keeps `training/.secrets/` out of Git. Check it
is present before saving any lab credentials there.

## Check that it is installed

1. In VS Code, select the **Copilot** harness with the **Session Target** control.
2. Open **Customizations** → **Agents** and look for **Certification Learning
   Coach** under **Workspace** (Option 1) or **User** (Option 2).
3. Start a new session and select it from the **Agent** dropdown in chat.
4. Run the checks in [`docs/TEST_PLAN.md`](docs/TEST_PLAN.md).

The coach can also be started directly with the Copilot CLI from the project
directory:

```bash
copilot --agent certification-learning-coach
```

### Known issue

In VS Code Insiders 1.145 with Copilot Chat 0.73 over Remote-SSH, the remote
Copilot Chat log has repeatedly shown
`[CopilotCLIAgents] Failed to fetch custom agents: Canceled: Canceled`. While
that happens, no custom agents appear in the dropdown even though the file is
valid. The cause has not been confirmed. Use the Copilot CLI command above as a
fallback, and check **Output → GitHub Copilot Chat** for this message.

## Update or uninstall

Installed copies do not update themselves. To update, pull this repository and
copy the agent file again. Don't recopy `training-template/` over a project's
`training/` directory; it would reset your learning records.

To uninstall, delete the copied `certification-learning-coach.agent.md`. Keep or
delete the project's `training/` directory as you prefer.

## Boundaries

The training-only write rule is an instruction to the agent, not a
host-enforced filesystem sandbox. Test it with `docs/TEST_PLAN.md` before
relying on it, and review its changes. The coach must never record credentials,
private account details, or real exam content. Tutor-authored questions are
original practice, not real exam questions.

## Sources

[VS Code custom agents](https://code.visualstudio.com/docs/agent-customization/custom-agents)
· [GH-600 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-600)
· [AI-103 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-103)
· [AI-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-500)
