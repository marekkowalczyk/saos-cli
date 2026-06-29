# saos

CLI search tool for [SAOS](https://www.saos.org.pl) — System Analizy Orzeczeń Sądowych, the Polish court judgments database.

## Installation

```bash
git clone https://github.com/marekkowalczyk/saos.git
ln -s "$PWD/saos/saos" /usr/local/bin/saos
```

Requires Python 3, no external dependencies.

## Usage

```
saos search "PHRASE" [options]
saos law "YEAR/NUMBER" [options]
saos judgment ID
saos --help
```

### Options

| Flag | Values | Default |
|---|---|---|
| `--court` | `COMMON` `SUPREME` `CONSTITUTIONAL_TRIBUNAL` `NATIONAL_APPEAL_CHAMBER` `ADMINISTRATIVE` | all |
| `--cc-court` | `APPEAL` `REGIONAL` `DISTRICT` | all |
| `--type` | `SENTENCE` `DECISION` `RESOLUTION` `REGULATION` `REASONS` | all |
| `--judge NAME` | judge surname | — |
| `--case SIG` | case signature | — |
| `--from` / `--to` | `YYYY-MM-DD` | — |
| `--size N` | 1–100 | 10 |
| `--page N` | 0-indexed | 0 |
| `--sort` | `JUDGMENT_DATE` `DATABASE_ID` `REFERENCING_JUDGMENTS_COUNT` | `JUDGMENT_DATE` |
| `--direction` | `ASC` `DESC` | `DESC` |

### Examples

```bash
# Full-text search
saos search "zadośćuczynienie" --court SUPREME --size 5

# Filter by judgment type and date range
saos search "mobbing" --type SENTENCE --from 2020-01-01 --to 2024-12-31

# Search by law journal entry
saos law "1964/43/296" --size 10

# Filter by judge, common appeal courts only
saos search "odszkodowanie" --judge "Kowalski" --cc-court APPEAL

# Fetch a single judgment by ID
saos judgment 547779
```

Output is Markdown.

## License

MIT
