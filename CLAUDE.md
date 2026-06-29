# saos

CLI tool for searching the SAOS Polish court judgments database.

## Structure

```
saos          — the script (Python 3, no external deps)
README.md     — usage docs
LICENSE       — MIT
dev/AAR.md    — after action reviews
dev/NEXT-SESSION.md — next session notes
```

## Installation

The script is symlinked into PATH from this repo:

```
/usr/local/bin/saos        -> /Users/marekkowalczyk/repos/saos-cli/saos
~/.local/bin/saos          -> /Users/marekkowalczyk/repos/saos-cli/saos
```

After editing the script here, both symlinks pick up changes immediately.

## Global skill

`~/.claude/commands/saos.md` — invoke as `/saos` from any project to search judgments via Claude Code.

## API

SAOS REST API: https://www.saos.org.pl/help/index.php/dokumentacja-api

Base URL: `https://www.saos.org.pl/api/search/judgments`
No authentication required.

## Session

Always run /start at the beginning of each session and /close at the end.
