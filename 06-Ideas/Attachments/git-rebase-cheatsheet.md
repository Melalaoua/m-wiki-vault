# Rebase & conflict cheat sheet

Working notes for landing a branch on `main` when concurrent agents have moved it
underneath you — the normal case in this repo's AFK workflow.

## The workflow

```bash
# 1. Get the REAL upstream state. `ahead/behind` is only as fresh as your last fetch.
git fetch origin
git status -sb                        # ahead N, behind M
git log --oneline HEAD..origin/main   # what's coming at you

# 2. Predict the conflicts before starting.
#    Only files touched by BOTH sides can conflict.
comm -12 <(git diff --name-only HEAD...origin/main | sort) \
         <(git diff --name-only origin/main...HEAD | sort)

# 3. Safety net — write this down.
git rev-parse HEAD

# 4. Go.
git rebase origin/main

# ── on conflict ──
git status                            # literally tells you the next command
#   edit the files: delete the markers, make the result COHERENT
grep -rnE '^(<<<<<<<|=======|>>>>>>>)' . --exclude-dir=.git   # prove none survive
git add <file>                        # "resolved" == add. Never `git commit`.
git rebase --continue

# ── escape hatch, at any point ──
git rebase --abort                    # back to exactly step 3
```

Then **verify before pushing**:

```bash
bun install        # REQUIRED if package.json / bun.lock moved in the rebase
bun run typecheck
bun run test
git push origin main
```

## Conflict marker anatomy

```
<<<<<<< HEAD
**Usage meter**:                    ← "ours"
=======
**Reading evidence**:               ← "theirs"
>>>>>>> be23cd5 (refactor(reading): ...)
```

Everything outside the markers merged fine. You only ever resolve the disputed lines.

## The inversion that costs people their work

During a **rebase**, git replays your commits *on top of* upstream — so at each step
`HEAD` is upstream, and the commit named at the bottom marker is **yours**. This reads
backwards from a merge:

| | `HEAD` / `--ours` | bottom / `--theirs` |
|---|---|---|
| **merge** | your branch | the branch being merged in |
| **rebase** | upstream you're rebasing onto | **your own commit** |

`git checkout --ours <file>` during a rebase therefore **discards your change**. When in
doubt, don't use `--ours`/`--theirs` at all — read the content and decide.

## Five things that actually bite

1. **Same file ≠ conflict.** Git merges by hunk, not by file. Two sides can edit the same
   file all day and apply cleanly if the regions don't overlap.
2. **`HEAD` is upstream during a rebase, not you.** See the table above.
3. **A clean auto-merge proves nothing about correctness.** Git guarantees the *text*
   merged — never that the result compiles, passes, or means what you intended.
4. **A rebase that moves the lockfile leaves `node_modules` stale.** Symptom: typecheck
   errors about missing `@types/*` in files you never touched. Fix: `bun install`.
5. **Diagnose whose breakage it is** before editing anything. Errors in files that came
   from upstream are usually environmental (see 4), not a bad resolution.

## Resolving is not "delete the markers"

Deleting the three marker lines gets you syntactically valid text that is often still
wrong — a lost blank line, a duplicated import, two entries in a nonsensical order. Read
the resolved region as if you'd written it from scratch.

## Escape hatches

| Situation | Command |
|---|---|
| Bail out entirely | `git rebase --abort` |
| This commit is now redundant upstream | `git rebase --skip` |
| Lost after a finished rebase | `git reflog`, then `git reset --hard <pre-rebase-sha>` |
| See both sides of a conflicted file | `git diff` (combined diff, during the conflict) |
| Whole-file take (know the inversion first!) | `git checkout --ours/--theirs <file>` |

## Repo-specific notes

- **Only rebase commits you haven't pushed.** Rebasing shared history rewrites commits
  others may have pulled.
- **Check ADR numbers after fetching.** Concurrent agents claim numbers independently;
  a rebase can leave you writing an ADR whose number was just taken upstream.
- **Push over HTTPS first.** If it fails with `Could not resolve host: github.com`
  (network-dependent, not permanent), use:
  `git push ssh://git@ssh.github.com:443/Melalaoua/M-wiki.git main`
