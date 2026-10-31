# Component layout

The pieces Copilot discovers and the learner's material live in different
places. That is normal. Keep the agent in a Copilot-native location and keep
all of the coach's learning work inside the project's `training/` directory.

## Once installed in a project

```text
your-project/
├── training/                                    # copied from training-template/
│   ├── README.md
│   ├── PROGRESS.md                              # shared progress memory
│   ├── .gitignore                               # keeps .secrets/ out of Git
│   ├── gh-600/  README.md, INSPIRATION_RESOURCES.md, TEST_ME_LATER.md
│   ├── ai-103/  README.md, INSPIRATION_RESOURCES.md, TEST_ME_LATER.md
│   └── ai-500/  README.md, INSPIRATION_RESOURCES.md, TEST_ME_LATER.md
│
└── .github/agents/
    └── certification-learning-coach.agent.md    # project install only
```

With a user-account install, the agent file is in `~/.copilot/agents/` instead
and the project contains only `training/`.

## Naming convention

Use the `certification-learning-coach-` prefix for every Copilot-facing
component belonging to this tutor. The part after the prefix says what it does.

| Component | Example name |
|---|---|
| Agent | `certification-learning-coach.agent.md` |
| Skill folder | `certification-learning-coach-calibration/` |
| Skill folder | `certification-learning-coach-assessment/` |
| Prompt file | `certification-learning-coach-baseline.prompt.md` |
| Prompt file | `certification-learning-coach-test-me.prompt.md` |

This is a way to find related pieces, not a requirement to create all of them.
Add a skill only after a useful workflow repeats, and a prompt only when a
focused entry point would make learning easier.

## Learning-lab content

The coach may read the whole project for context. Its notes, questions, source
material, and exploratory code belong under `training/`. Each certification
directory holds its own `TEST_ME_LATER.md` queue, and `training/PROGRESS.md`
keeps cross-track memory in a small, dashboard-friendly format. Experiments can
live wherever under `training/` is easiest to find.

The agent file is installed and maintained by the person setting up the tutor.
A running coach does not edit it.
