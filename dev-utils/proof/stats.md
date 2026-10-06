### dev-utils (private)

Measured 2026-10-05 at `origin/main` (c2ebd66).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 237 | `git -C dev-utils rev-list --count c2ebd66` |
| Non-merge commits | 207 | `git -C dev-utils rev-list --count --no-merges c2ebd66` |
| First commit | 2026-07-22 | `git -C dev-utils log --reverse --format=%as c2ebd66 \| head -1` |
| Latest commit | 2026-10-04 | `git -C dev-utils log -1 --format=%as c2ebd66` |
| Active days | 12 | `git -C dev-utils log --format=%as c2ebd66 \| sort -u \| wc -l` |
| Commits on origin/dev at 84caf0b (integration branch) | 225 | `git -C dev-utils rev-list --count 84caf0b` |
| Tags reachable from the ref | 6 (latest: v0.5.1, v0.5.0, v0.4.0) | `git -C dev-utils tag --merged c2ebd66 \| wc -l` |
| Test-tree files (tests, harness and fixtures) | 20 | `git -C dev-utils ls-tree -r --name-only c2ebd66 \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| Python test cases (def test_…) | 240 | `git -C dev-utils grep -I -c -E '^\s*(async\s+)?def test_' c2ebd66 -- '*.py' \| awk -F: '{s+=$NF} END {print s+0}'` |
| CI workflows | 0 | `git -C dev-utils ls-tree -r --name-only c2ebd66 -- .github/workflows \| wc -l` |
| Lines of Python, excluding tests | 5351 (13 files) | `git -C dev-utils grep -I -c '' c2ebd66 -- '*.py' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Python in test files | 5199 (19 files) | `git -C dev-utils grep -I -c '' c2ebd66 -- '*.py' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 1127 | `git -C dev-utils grep -I -c '' c2ebd66 -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 0 | `git -C dev-utils log --format=%aN c2ebd66 \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| dev-loop findings on the bus, live + archive | 31 (28 VERIFIED) | `git -C dev-utils show c2ebd66:dev/FEEDBACK.md c2ebd66:dev/FEEDBACK-archive.md \| grep -oE '^## F-[0-9]+' \| sort -u \| wc -l` |
| Fixes carrying an independent `Judge:` line | 26 | `git -C dev-utils show c2ebd66:dev/FEEDBACK.md c2ebd66:dev/FEEDBACK-archive.md \| grep -c '^Judge:'` |
| Fixes that name the design they replace (`Redesign:`) | 4 | `git -C dev-utils show c2ebd66:dev/FEEDBACK.md c2ebd66:dev/FEEDBACK-archive.md \| grep -c '^Redesign:'` |
| Release tags | 6 | `git -C dev-utils tag --merged c2ebd66 \| wc -l` |
| Deliberate re-pins to the skill spec | 13 | `git -C dev-utils log c2ebd66 --format=%s \| grep -ci 're-pin'` |
| Python source | 5351 | `git -C dev-utils grep -I -c '' c2ebd66 -- '*.py' ':!tests/' \| awk -F: '{s+=$NF} END {print s}'` |
| Commits | 237 | `git -C dev-utils rev-list --count c2ebd66` |
| CI workflows | 0 | `git -C dev-utils ls-tree -r --name-only c2ebd66 -- .github/workflows \| wc -l` |
| Merged pull requests | 30 | `gh pr list -R BradleyDB/dev-utils --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/dev-utils --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

