# Project Manager Memory

## Docket CLI Reference Corrections
- `docket issue link add` relation types: `blocks`, `depends_on`, `relates_to`, `duplicates` (NOT `blocked-by`)
- File attachments may duplicate if `-f` is used on create AND `file add` after -- use one or the other

## Project Structure
- QA tests: `scripts/qa/test_*.sh` (29 scripts, alphabetical naming: a-z, then za, zb, zc...)
- No CLI-level Go tests exist (`internal/cli/` has no `*_test.go` files)
- Go unit tests are in `internal/db/`, `internal/model/`, `internal/output/`, `internal/render/`, `internal/planner/`
- TTY detection pattern: `term.IsTerminal(int(os.Stdout.Fd()))` used across 12+ CLI files
- Testing spec: `docs/spec/testing.md`; TDDs: `docs/tdd/`; UX specs: `docs/ux/`

## Docket Vote Subcommand
- Files: `internal/cli/vote.go`, `vote_cast.go`, `vote_create.go`, `vote_show.go`, `vote_list.go`, `vote_result.go`, `vote_link.go`, `vote_commit.go`
- TDD: `docs/tdd/vote-subcommand.md`
- No QA shell tests for vote commands yet (next slot: `test_zd_vote_cast.sh`)
- `config.DefaultAuthor()` resolves via `git config user.name` with 2s timeout
