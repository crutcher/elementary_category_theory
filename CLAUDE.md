# CLAUDE.md — Project Directives for Elementary Category Theory

## Working Process

### Feedback is accumulative dialog

- Feedback rounds establish plans and take notes. They do not trigger immediate rewrites.
- Rewriting / applying complex feedback is expensive. Minimize those cycles,
  especially before integrating all feedback and plans into a coherent set of changes.

### History is immutable

- Never edit files in `history/`. Only add new files.
- If a previous directive needs clarification, add a clarifying entry — do not rewrite the past.

### Notes are mutable working accumulation

- `notes/` is the working scratchpad: running plans, open questions, decisions pending,
  accumulated feedback summaries. Files here may be updated over time.
- `history/` is the permanent record. Files there are append-only.

### Build discipline

1. Do not edit or rebuild the book in response to feedback alone.
2. Before applying a batch of changes to the book, ask/verify with the user to
   create a new branch for those changes.
3. Before merging that branch to main, ask for explicit review and commitment.

### Branch conventions

- Development branch: `claude/category-theory-book-mdgQ3`
- All book edits go to a named feature branch, reviewed, then merged.
- Never push book content changes directly to `main` without explicit approval.
