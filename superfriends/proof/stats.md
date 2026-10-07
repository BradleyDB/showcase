### gs-admin-superfriends (private)

Measured 2026-10-06 at `origin/main` (1bd3309).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 76 | `git -C gs-admin-superfriends rev-list --count 1bd3309` |
| Non-merge commits | 53 | `git -C gs-admin-superfriends rev-list --count --no-merges 1bd3309` |
| First commit | 2026-06-27 | `git -C gs-admin-superfriends log --reverse --format=%as 1bd3309 \| head -1` |
| Latest commit | 2026-10-06 | `git -C gs-admin-superfriends log -1 --format=%as 1bd3309` |
| Active days | 19 | `git -C gs-admin-superfriends log --format=%as 1bd3309 \| sort -u \| wc -l` |
| Commits on origin/dev at 5e5aed0 (integration branch) | 67 | `git -C gs-admin-superfriends rev-list --count 5e5aed0` |
| Tags reachable from the ref | 9 (latest: release-2026-10-06, release-2026-10-05, release-2026-09-29.2) | `git -C gs-admin-superfriends tag --merged 1bd3309 \| wc -l` |
| Version in plugins/superfriends/.claude-plugin/plugin.json | 1.4.1 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/.claude-plugin/plugin.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Skills (SKILL.md files) | 10 | `git -C gs-admin-superfriends ls-tree -r --name-only 1bd3309 \| grep -cE '(^\|/)skills/[^/]+/SKILL\.md$'` |
| Test-tree files (tests, harness and fixtures) | 2 | `git -C gs-admin-superfriends ls-tree -r --name-only 1bd3309 \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| CI workflows | 0 | `git -C gs-admin-superfriends ls-tree -r --name-only 1bd3309 -- .github/workflows \| wc -l` |
| Lines of Python, excluding tests | 467 (4 files) | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.py' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript, excluding tests | 2300 (10 files) | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript in test files | 351 (1 files) | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Shell, excluding tests | 276 (3 files) | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.sh' '*.bash' '*.ps1' '*.cmd' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Shell in test files | 128 (1 files) | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.sh' '*.bash' '*.ps1' '*.cmd' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 6402 | `git -C gs-admin-superfriends grep -I -c '' 1bd3309 -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 0 | `git -C gs-admin-superfriends log --format=%aN 1bd3309 \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| Commits that name the finding that drove them | 11 | `git -C gs-admin-superfriends log 1bd3309 --format=%s \| grep -cE 'F-[0-9]+'` |
| Past findings the dev-loop skill cites as precedent for its rules | 14 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/dev-loop/SKILL.md \| grep -oE 'F-[0-9]+' \| sort -u \| wc -l` |
| Lines in the four process skills (SKILL.md and README.md) | 1877 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/dev-loop/SKILL.md 1bd3309:plugins/superfriends/skills/dev-loop/README.md 1bd3309:plugins/superfriends/skills/team-loop/SKILL.md 1bd3309:plugins/superfriends/skills/team-loop/README.md 1bd3309:plugins/superfriends/skills/handoff-plan/SKILL.md 1bd3309:plugins/superfriends/skills/external-pr-intake/SKILL.md \| wc -l` |
| Design questions asked of every outside PR | 10 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/external-pr-intake/SKILL.md \| grep -cE '^- [*][*]D[0-9]+ '` |
| Handoff-home resolver test cases | 6 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/handoff-plan/scripts/test-handoff-home.sh \| grep -cE '^ *run "'` |
| Merged pull requests | 23 | `gh pr list -R BradleyDB/gs-admin-superfriends --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/gs-admin-superfriends --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

