### Admin_CLI_Explore (private)

`Admin_CLI_Explore` is the local clone of the plugin's pre-launch history (`gs-admin-cli-docs-private-archive`).

Measured 2026-10-05 at `origin/main` (188ffc4).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 1311 | `git -C Admin_CLI_Explore rev-list --count 188ffc4` |
| Non-merge commits | 1133 | `git -C Admin_CLI_Explore rev-list --count --no-merges 188ffc4` |
| First commit | 2026-06-27 | `git -C Admin_CLI_Explore log --reverse --format=%as 188ffc4 \| head -1` |
| Latest commit | 2026-09-08 | `git -C Admin_CLI_Explore log -1 --format=%as 188ffc4` |
| Active days | 47 | `git -C Admin_CLI_Explore log --format=%as 188ffc4 \| sort -u \| wc -l` |
| Commits on origin/dev at 4ad79e4 (integration branch) | 1260 | `git -C Admin_CLI_Explore rev-list --count 4ad79e4` |
| Tags reachable from the ref | 23 (latest: v0.37.0, v0.36.3, v0.36.2) | `git -C Admin_CLI_Explore tag --merged 188ffc4 \| wc -l` |
| Version in package.json | 1.0.0 | `git -C Admin_CLI_Explore show 188ffc4:package.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Version in plugins/gs-superadmin/.claude-plugin/plugin.json | 0.37.0 | `git -C Admin_CLI_Explore show 188ffc4:plugins/gs-superadmin/.claude-plugin/plugin.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Versions recorded in plugins/gs-superadmin/CHANGELOG.md | 93 (more than this repo's tags: the changelog may predate its history) | `git -C Admin_CLI_Explore show 188ffc4:plugins/gs-superadmin/CHANGELOG.md \| grep -cE '^##\s+\[?v?[0-9]+\.[0-9]+'` |
| Skills (SKILL.md files) | 8 | `git -C Admin_CLI_Explore ls-tree -r --name-only 188ffc4 \| grep -cE '(^\|/)skills/[^/]+/SKILL\.md$'` |
| Test-tree files (tests, harness and fixtures) | 73 | `git -C Admin_CLI_Explore ls-tree -r --name-only 188ffc4 \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| CI workflows | 3 | `git -C Admin_CLI_Explore ls-tree -r --name-only 188ffc4 -- .github/workflows \| wc -l` |
| Lines of JavaScript/TypeScript, excluding tests | 25731 (42 files) | `git -C Admin_CLI_Explore grep -I -c '' 188ffc4 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript in test files | 25314 (42 files) | `git -C Admin_CLI_Explore grep -I -c '' 188ffc4 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 17316 | `git -C Admin_CLI_Explore grep -I -c '' 188ffc4 -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 1 | `git -C Admin_CLI_Explore log --format=%aN 188ffc4 \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| dev-loop findings on the bus, live + archive (at origin/dev 4ad79e4: the release strips dev/) | 446 (434 VERIFIED) | `git -C Admin_CLI_Explore show 4ad79e4:dev/FEEDBACK.md 4ad79e4:dev/FEEDBACK-archive.md \| grep -oE '^## F-[0-9]+' \| sort -u \| wc -l` |
| Merged pull requests | 154 | `gh pr list -R BradleyDB/gs-admin-cli-docs-private-archive --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 1 | `gh pr list -R BradleyDB/gs-admin-cli-docs-private-archive --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

