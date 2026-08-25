# Initiatives — how this folder works

One folder per initiative. The folder is the unit; everything about an initiative lives inside it.

```
initiatives/
├── _dashboard.md                  # The single overview of everything in flight — read this first
├── _org_initiative_template.md    # Comprehensive template (org-wide, DACI, formal tracking)
├── _project_template.md           # Lightweight template (personal / small-group work)
├── active/                        # Initiatives you're currently running
│   └── <initiative-name>/
│       ├── _initiative.md         # The hub file — status, plan, progress log, references
│       └── ...                    # Supporting docs, research, drafts, decks live beside it
└── completed/                     # Finished initiatives, kept for a quarter before archiving
    └── <initiative-name>/
```

## Starting an initiative

1. Create a folder under `active/` named for the initiative (kebab-case, e.g. `active/q3-hiring-plan/`).
2. Copy a template into it as `_initiative.md`:
   - `_project_template.md` for personal or small-group work.
   - `_org_initiative_template.md` for org-wide initiatives with stakeholders and formal tracking.
3. Add a row to `_dashboard.md` so it shows up in your overview.
4. Keep everything for that initiative — notes, research, drafts, diagrams — inside the folder.

The `_` prefix on `_initiative.md` keeps the hub file sorted to the top of its folder. Some initiatives use a `_vision.md` or `_strategy.md` hub instead when the work is a vision or strategy piece rather than a tracked project — same idea, different starting shape.

## Finishing an initiative

1. Fill in the retrospective section of `_initiative.md`.
2. Move the folder from `active/` to `completed/`.
3. Log it under **Recently Completed** in `_dashboard.md`.

## Reviewing

`_dashboard.md` is the operating view — by priority, by your role, upcoming milestones, decisions needed. Walk it during your weekly review (there's a checklist at the bottom of the dashboard) and refresh it monthly.
