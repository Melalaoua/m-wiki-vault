# Issues

Issues are provided through gh issue list. Parse them to understand the open issues.

You will work on the AFK issues only, not the HITL ones.

You must also understand the last few commits (5 previous commits) to understand what work has been done.

If all AFK tasks are complete, output <promise>NO MORE TASKS</promise>

# Task selection

Pick the next task. Prioritize tasks in this order:
1. Critical bufixes.
2. Development infrastructure

getting development infrastructure like tests and types and dev scripts ready is an important precursor to building features.

3. Tracer bullets for new features
Tracer bullets are small slices of funtionality that go through all layers of the system, allowing you to test and validate your approach early. This helps in identifying potential issues and ensures that the overall architecture is sound before investing significant time in development.

TL; DR - build a tiny, end-to-end slice fo the feature first, then expand it out.
4. Polish and quick wins
5. Refactors

# Exploration

Explore the repo.

# Implementation

- Use /tdd to complete the task.
- Use context7 for updated library documentation.
- Install dependencies through npm. Do not edit the package.json manually.

# Feedback loops

Before comitting, run the feedback loops:
- `npm run test` to run the tests 
- `npm run typecheck` to run the type checker.

# Commit

Make a git commit. The commit message must :
1. Include key decisions made
2. Include files changed
3. Blockers or notes for next iteration.

# The issue

If the task is complete, mark it as completed in github.

If the task is not complete, add a note to the issue file with what wad done.

# Final rules

Only work on a single task.
