### gs-admin-cli-docs (public)

Measured 2026-10-05 at `origin/main` (5353b7f).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 163 | `git -C gs-admin-cli-docs rev-list --count 5353b7f` |
| Non-merge commits | 144 | `git -C gs-admin-cli-docs rev-list --count --no-merges 5353b7f` |
| First commit | 2026-09-09 | `git -C gs-admin-cli-docs log --reverse --format=%as 5353b7f \| head -1` |
| Latest commit | 2026-09-28 | `git -C gs-admin-cli-docs log -1 --format=%as 5353b7f` |
| Active days | 11 | `git -C gs-admin-cli-docs log --format=%as 5353b7f \| sort -u \| wc -l` |
| Commits on origin/dev at 0543ff0 (integration branch) | 235 | `git -C gs-admin-cli-docs rev-list --count 0543ff0` |
| Tags reachable from the ref | 4 (latest: v0.43.3, v0.43.0, v0.42.0) | `git -C gs-admin-cli-docs tag --merged 5353b7f \| wc -l` |
| Version in package.json | 1.0.0 | `git -C gs-admin-cli-docs show 5353b7f:package.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Version in plugins/gs-superadmin/.claude-plugin/plugin.json | 0.43.3 | `git -C gs-admin-cli-docs show 5353b7f:plugins/gs-superadmin/.claude-plugin/plugin.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Versions recorded in plugins/gs-superadmin/CHANGELOG.md | 105 (more than this repo's tags: the changelog may predate its history) | `git -C gs-admin-cli-docs show 5353b7f:plugins/gs-superadmin/CHANGELOG.md \| grep -cE '^##\s+\[?v?[0-9]+\.[0-9]+'` |
| Skills (SKILL.md files) | 8 | `git -C gs-admin-cli-docs ls-tree -r --name-only 5353b7f \| grep -cE '(^\|/)skills/[^/]+/SKILL\.md$'` |
| Test-tree files (tests, harness and fixtures) | 73 | `git -C gs-admin-cli-docs ls-tree -r --name-only 5353b7f \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| CI workflows | 3 | `git -C gs-admin-cli-docs ls-tree -r --name-only 5353b7f -- .github/workflows \| wc -l` |
| Lines of JavaScript/TypeScript, excluding tests | 27258 (42 files) | `git -C gs-admin-cli-docs grep -I -c '' 5353b7f -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript in test files | 27083 (42 files) | `git -C gs-admin-cli-docs grep -I -c '' 5353b7f -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 18208 | `git -C gs-admin-cli-docs grep -I -c '' 5353b7f -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 3 | `git -C gs-admin-cli-docs log --format=%aN 5353b7f \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| dev-loop findings on the bus, live + archive (at origin/dev 0543ff0: the release strips dev/) | 35 (32 VERIFIED) | `git -C gs-admin-cli-docs show 0543ff0:dev/FEEDBACK.md 0543ff0:dev/FEEDBACK-archive.md \| grep -oE '^## F-[0-9]+' \| sort -u \| wc -l` |
| gs-admin-cli-docs files naming dev-utils on dev | 8 | `git -C gs-admin-cli-docs grep -l -i dev-utils 0543ff0 -- . \| wc -l` |
| Merged pull requests | 28 | `gh pr list -R BradleyDB/gs-admin-cli-docs --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 3 | `gh pr list -R BradleyDB/gs-admin-cli-docs --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

### gs-fortress (private)

Measured 2026-10-05 at `origin/main` (ff5ff42).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 165 | `git -C gs-fortress rev-list --count ff5ff42` |
| Non-merge commits | 150 | `git -C gs-fortress rev-list --count --no-merges ff5ff42` |
| First commit | 2026-07-27 | `git -C gs-fortress log --reverse --format=%as ff5ff42 \| head -1` |
| Latest commit | 2026-10-04 | `git -C gs-fortress log -1 --format=%as ff5ff42` |
| Active days | 16 | `git -C gs-fortress log --format=%as ff5ff42 \| sort -u \| wc -l` |
| Commits on origin/dev at b0f0b94 (integration branch) | 151 | `git -C gs-fortress rev-list --count b0f0b94` |
| Tags reachable from the ref | 8 (latest: v0.6.0, v0.5.1, v0.5.0) | `git -C gs-fortress tag --merged ff5ff42 \| wc -l` |
| Version in plugins/gs-fortress/.claude-plugin/plugin.json | 0.6.0 | `git -C gs-fortress show ff5ff42:plugins/gs-fortress/.claude-plugin/plugin.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Versions recorded in plugins/gs-fortress/CHANGELOG.md | 9 (more than this repo's tags: the changelog may predate its history) | `git -C gs-fortress show ff5ff42:plugins/gs-fortress/CHANGELOG.md \| grep -cE '^##\s+\[?v?[0-9]+\.[0-9]+'` |
| Skills (SKILL.md files) | 1 | `git -C gs-fortress ls-tree -r --name-only ff5ff42 \| grep -cE '(^\|/)skills/[^/]+/SKILL\.md$'` |
| Test-tree files (tests, harness and fixtures) | 10 | `git -C gs-fortress ls-tree -r --name-only ff5ff42 \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| CI workflows | 0 | `git -C gs-fortress ls-tree -r --name-only ff5ff42 -- .github/workflows \| wc -l` |
| Lines of JavaScript/TypeScript, excluding tests | 1861 (5 files) | `git -C gs-fortress grep -I -c '' ff5ff42 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript in test files | 2157 (8 files) | `git -C gs-fortress grep -I -c '' ff5ff42 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 8953 | `git -C gs-fortress grep -I -c '' ff5ff42 -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 0 | `git -C gs-fortress log --format=%aN ff5ff42 \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| dev-loop findings on the bus, live + archive | 25 (24 VERIFIED) | `git -C gs-fortress show ff5ff42:dev/FEEDBACK.md ff5ff42:dev/FEEDBACK-archive.md \| grep -oE '^## F-[0-9]+' \| sort -u \| wc -l` |
| Audit reports | 5 | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/reports/ \| grep -c 'audit-'` |
| Adopt decisions recorded | 5 | `git -C gs-fortress show ff5ff42:ledger/state.json \| grep -c '"decision": "adopt"'` |
| Upstream known issues tracked | 20 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -oE '"id": *"KI-[0-9]+"' \| sort -u \| wc -l` |
| … since resolved upstream | 7 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -c '"status": "resolved"'` |
| Vendor-ready reports sent | 8 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"sent": "[0-9]'` |
| Reports with a vendor acknowledgement stamped | 0 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"acknowledged": "[0-9]'` |
| gs-fortress files citing /dev-loop or handoff-plan | 5 | `git -C gs-fortress grep -l -i -e /dev-loop -e handoff-plan ff5ff42 -- . \| wc -l` |
| Merged pull requests | 14 | `gh pr list -R BradleyDB/gs-fortress --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/gs-fortress --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

### gs-admin-superfriends (private)

Measured 2026-10-05 at `origin/main` (1452475).

| Measure | Value | Reproduce with |
|---|---|---|
| Commits | 58 | `git -C gs-admin-superfriends rev-list --count 1452475` |
| Non-merge commits | 40 | `git -C gs-admin-superfriends rev-list --count --no-merges 1452475` |
| First commit | 2026-06-27 | `git -C gs-admin-superfriends log --reverse --format=%as 1452475 \| head -1` |
| Latest commit | 2026-09-29 | `git -C gs-admin-superfriends log -1 --format=%as 1452475` |
| Active days | 16 | `git -C gs-admin-superfriends log --format=%as 1452475 \| sort -u \| wc -l` |
| Commits on origin/dev at 398e187 (integration branch) | 53 | `git -C gs-admin-superfriends rev-list --count 398e187` |
| Tags reachable from the ref | 7 (latest: release-2026-09-29.2, release-2026-09-29, release-2026-09-28) | `git -C gs-admin-superfriends tag --merged 1452475 \| wc -l` |
| Version in plugins/superfriends/.claude-plugin/plugin.json | 1.3.0 | `git -C gs-admin-superfriends show 1452475:plugins/superfriends/.claude-plugin/plugin.json \| grep -m1 -E '"?version"?\s*[:=]'` |
| Skills (SKILL.md files) | 9 | `git -C gs-admin-superfriends ls-tree -r --name-only 1452475 \| grep -cE '(^\|/)skills/[^/]+/SKILL\.md$'` |
| Test-tree files (tests, harness and fixtures) | 1 | `git -C gs-admin-superfriends ls-tree -r --name-only 1452475 \| grep -cE '(^\|/)(tests?\|__tests__)/\|\.test\.[a-z]+$\|_test\.[a-z]+$\|(^\|/)test_[^/]*\.py$\|(^\|/)test-[^/]*\.(mjs\|js\|sh)$'` |
| CI workflows | 0 | `git -C gs-admin-superfriends ls-tree -r --name-only 1452475 -- .github/workflows \| wc -l` |
| Lines of Python, excluding tests | 467 (4 files) | `git -C gs-admin-superfriends grep -I -c '' 1452475 -- '*.py' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of JavaScript/TypeScript, excluding tests | 951 (5 files) | `git -C gs-admin-superfriends grep -I -c '' 1452475 -- '*.mjs' '*.cjs' '*.js' '*.ts' '*.tsx' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Shell, excluding tests | 276 (3 files) | `git -C gs-admin-superfriends grep -I -c '' 1452475 -- '*.sh' '*.bash' '*.ps1' '*.cmd' \| awk -F: '$2 !~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Shell in test files | 128 (1 files) | `git -C gs-admin-superfriends grep -I -c '' 1452475 -- '*.sh' '*.bash' '*.ps1' '*.cmd' \| awk -F: '$2 ~ "(^\|/)(tests?\|__tests__)/\|\\.test\\.[a-z]+$\|_test\\.[a-z]+$\|(^\|/)test_[^/]*\\.py$\|(^\|/)test-[^/]*\\.(mjs\|js\|sh)$" {s+=$NF} END {print s+0}'` |
| Lines of Markdown (docs, skills, ledgers) | 5734 | `git -C gs-admin-superfriends grep -I -c '' 1452475 -- '*.md' \| awk -F: '{s+=$NF} END {print s+0}'` |
| Commit authors other than the owner (count only) | 0 | `git -C gs-admin-superfriends log --format=%aN 1452475 \| sort -u \| grep -vixF -e 'bradleydb' -e 'bradley' \| wc -l` |
| Merged pull requests | 19 | `gh pr list -R BradleyDB/gs-admin-superfriends --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/gs-admin-superfriends --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

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
| Merged pull requests | 30 | `gh pr list -R BradleyDB/dev-utils --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/dev-utils --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

### Cross-references (tracked files in one repo that name another)

| From | To | Files | Reproduce with |
|---|---|---|---|
| gs-admin-cli-docs | gs-fortress | 14 | `git -C gs-admin-cli-docs grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-fortress)($\|[^A-Za-z0-9_-])' 5353b7f -- . \| wc -l` |
| gs-admin-cli-docs | gs-admin-superfriends | 0 | `git -C gs-admin-cli-docs grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-superfriends\|superfriends)($\|[^A-Za-z0-9_-])' 5353b7f -- . \| wc -l` |
| gs-admin-cli-docs | dev-utils | 0 | `git -C gs-admin-cli-docs grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(dev-utils)($\|[^A-Za-z0-9_-])' 5353b7f -- . \| wc -l` |
| gs-fortress | gs-admin-cli-docs | 27 | `git -C gs-fortress grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-cli-docs\|gs-superadmin)($\|[^A-Za-z0-9_-])' ff5ff42 -- . \| wc -l` |
| gs-fortress | gs-admin-superfriends | 0 | `git -C gs-fortress grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-superfriends\|superfriends)($\|[^A-Za-z0-9_-])' ff5ff42 -- . \| wc -l` |
| gs-fortress | dev-utils | 2 | `git -C gs-fortress grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(dev-utils)($\|[^A-Za-z0-9_-])' ff5ff42 -- . \| wc -l` |
| gs-admin-superfriends | gs-admin-cli-docs | 5 | `git -C gs-admin-superfriends grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-cli-docs\|gs-superadmin)($\|[^A-Za-z0-9_-])' 1452475 -- . \| wc -l` |
| gs-admin-superfriends | gs-fortress | 0 | `git -C gs-admin-superfriends grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-fortress)($\|[^A-Za-z0-9_-])' 1452475 -- . \| wc -l` |
| gs-admin-superfriends | dev-utils | 6 | `git -C gs-admin-superfriends grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(dev-utils)($\|[^A-Za-z0-9_-])' 1452475 -- . \| wc -l` |
| dev-utils | gs-admin-cli-docs | 8 | `git -C dev-utils grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-cli-docs\|gs-superadmin)($\|[^A-Za-z0-9_-])' c2ebd66 -- . \| wc -l` |
| dev-utils | gs-fortress | 2 | `git -C dev-utils grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-fortress)($\|[^A-Za-z0-9_-])' c2ebd66 -- . \| wc -l` |
| dev-utils | gs-admin-superfriends | 6 | `git -C dev-utils grep -I -l -i -E '(^\|[^A-Za-z0-9_-])(gs-admin-superfriends\|superfriends)($\|[^A-Za-z0-9_-])' c2ebd66 -- . \| wc -l` |

