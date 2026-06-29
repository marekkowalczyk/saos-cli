# After Action Review

Continuous improvement log. Each session ends with a brief review: what went well, what didn't, what to change. This is the POOGI (Process Of Ongoing Improvement) record for this project.

## 2026-06-29 — Fix saos law HTTP 400; add criminal procedure guidance to skill

**What went well:**
- Diagnosing `saos law` HTTP 400 from first principles (live curl probes) confirmed the root cause in minutes — the 3-part journal code format is rejected by the API; no guessing needed
- Full-text Dz.U. citation workaround recovered 14,698 results vs. 5 before — an immediate, testable improvement
- Checking the SAOS query language docs proactively turned a one-line observation (operators work passthrough) into a documented, usable feature in the skill

**What didn't go well:**
- README had a wrong `git clone` URL (`saos.git` instead of `saos-cli.git`) since the initial repo creation — caught only at close

**What we'll do differently:**
- On any rename or repo-creation session, verify the README clone URL before closing

## 2026-06-29 — Bootstrap session: saos CLI tool built from scratch

**What went well:**
- API exploration first (live curl probes) caught the `chambers` vs `chamber` structural difference between search results and single-judgment responses before it became a production bug
- The Unix citizenship review caught missing error handling early; clean stderr + exit codes added before shipping
- Script was small enough to hold entirely in main context — no subagent needed

**What didn't go well:**
- `saos/saos` double-naming wasn't noticed before the repo was populated, forcing a rename mid-session
- Renaming the repo directory while the Bash tool's cwd was anchored to it broke all subsequent shell commands, requiring workarounds for the rest of the session
- Three bugs in `saos judgment` (wrong response envelope, raw HTML in textContent, empty fields) went undetected until the first real run — only `saos search` was tested after each fix cycle

**What we'll do differently:**
- Decide the repo name before creating any files in it
- Test `saos judgment ID` immediately after writing `cmd_judgment`, not only after `search` is verified
- When renaming a repo mid-session, open a new Claude Code session from the new path before continuing work

## 2026-06-29 — Housekeeping: GitHub repo, gitignore, dev/ layout

**What went well:**
- `gh repo create` worked first try; push was clean
- `.gitignore` pattern (ignore `.claude/` except `commands/`) is correct and idiomatic
- Spotted and cleared the stale "set up GitHub remote" item from NEXT-SESSION before closing

**What didn't go well:**
- Ghost `saos/` directory required manual cleanup — carried-over friction from the previous session's rename
- `dev/CLAUDE.md` detour: moved it there, then had to move it back — one unnecessary round-trip

**What we'll do differently:**
- Before reorganising files into subdirs, confirm which files are special (CLAUDE.md must stay at root) — decide once, not twice
