### gs-fortress (private)

Measured 2026-10-06 at `origin/main` (ff5ff42).

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
| Impact-checklist items | 13 | `git -C gs-fortress show ff5ff42:plugins/gs-fortress/skills/gs-admin-cli-watch/reference/impact-checklist.md \| grep -cE '^[0-9]+\. \*\*'` |
| Impact-checklist items at the first audit (b9b6d3a, 2026-07-27) | 8 | `git -C gs-fortress show b9b6d3a:plugins/gs-fortress/skills/gs-admin-cli-watch/reference/impact-checklist.md \| grep -cE '^[0-9]+\. \*\*'` |
| Upstream releases audited (audit reports) | 5 | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/reports/ \| grep -cE '/audit-[0-9.]+\.md$'` |
| Build-kickoff files (change plans handed to build sessions) | 5 | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/reports/ \| grep -cE '/build-kickoffs-[0-9.]+\.md$'` |
| Adopt/defer decisions recorded | 5 | `git -C gs-fortress show ff5ff42:ledger/state.json \| grep -c '"decision":'` |
| Decisions that were adopt | 5 | `git -C gs-fortress show ff5ff42:ledger/state.json \| grep -c '"decision": "adopt"'` |
| Tracked upstream defects (known-issues entries) | 20 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"id": "KI-[0-9]+"'` |
| Tracked defects resolved upstream | 7 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -c '"status": "resolved"'` |
| Vendor-ready defect reports on file | 8 | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/upstream-feedback/reports/ \| grep -c '\.md$'` |
| Defect reports recorded as sent | 8 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"sent": "[0-9]{4}-'` |
| Defect reports recorded as acknowledged | 0 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"acknowledged": "[0-9]{4}-'` |
| Resolved defects that had a report on file | 2 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| node -e "const j=JSON.parse(require('fs').readFileSync(0,'utf8'));console.log(j.issues.filter(e=>e.report&&e.status==='resolved').length)"` |
| Tracked defects carrying the 2026-07-30 vendor reply | 5 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"upstreamResponse": "2026-07-30'` |
| Of those, resolved in 1.0.8 | 4 | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| node -e "const j=JSON.parse(require('fs').readFileSync(0,'utf8'));console.log(j.issues.filter(e=>String(e.upstreamResponse\|\|'').startsWith('2026-07-30')&&e.resolvedOn==='1.0.8').length)"` |
| Bus findings reopened at least once (by a tester or the owner) | 8 | `git -C gs-fortress show ff5ff42:dev/FEEDBACK.md ff5ff42:dev/FEEDBACK-archive.md \| awk '/^## F-[0-9]+/{f=$2} /^Reopened/{print f}' \| sort -u \| wc -l` |
| Test suites (*.test.mjs) | 6 | `git -C gs-fortress ls-tree -r --name-only ff5ff42 plugins/gs-fortress/test \| grep -cE '\.test\.mjs$'` |
| Watcher invariants restated to every agent | 8 | `git -C gs-fortress show ff5ff42:plugins/gs-fortress/skills/gs-admin-cli-watch/SKILL.md \| sed -n '/^## Invariants/,/^## Stage 0/p' \| grep -cE '^[0-9]+\. '` |
| Build kickoffs written as handoff-plan sets (session map, frozen contracts) | 2 | `git -C gs-fortress grep -l '^## Session map' ff5ff42 -- ledger/reports/ \| wc -l` |
| Frozen contracts in the 1.0.10 build plan | 4 | `git -C gs-fortress show ff5ff42:ledger/reports/build-kickoffs-1.0.10.md \| awk '/^## Frozen contracts/{f=1;next} /^## /{f=0} f && /^- /' \| wc -l` |
| Merged pull requests | 14 | `gh pr list -R BradleyDB/gs-fortress --state merged --limit 2000 --json number --jq length` |
| Merged PRs by someone other than the owner (count only) | 0 | `gh pr list -R BradleyDB/gs-fortress --state merged --limit 2000 --json author --jq '[.[] \| select(.author.login != "BradleyDB")] \| length'` |

