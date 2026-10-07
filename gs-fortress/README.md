# gs-fortress

**Every time the vendor ships a new version of the CLI an AI agent depends on, gs-fortress audits what changed and records a human adopt-or-defer decision before anything is built on it.**

<table><tr>
<td align="center" width="25%"><h2>5</h2>vendor releases audited, each with a recorded decision</td>
<td align="center" width="25%"><h2>13</h2>impact-checklist items, up from 8 at the first audit</td>
<td align="center" width="25%"><h2>20</h2>upstream CLI defects tracked, 7 since resolved</td>
<td align="center" width="25%"><h2>8 of 25</h2>of its own findings reopened at least once before they passed</td>
</tr></table>

> [!IMPORTANT]
> **The agent recommends; a person decides.** The audit writes `decision: pending` and
> stops. Neither the watcher nor the close-out script will write the decision.

Part of the [gs-admin toolchain](../gs-admin-toolchain/README.md): its upstream watch.
Private repository · in use (weekly scheduled run) · measured 2026-10-05.

## In 30 seconds

- **The risk.** My public plugin, [gs-superadmin](https://github.com/BradleyDB/gs-admin-cli-docs),
  generates its safety guard from the vendor CLI's command catalog. If a release mislabels a
  command that writes as read-only, the guard inherits the mistake at upgrade time.
  Upgrading blind risks the agent's safety rails. Never upgrading leaves vendor fixes unused.
- **What it does.** A weekly check, a mechanical diff, one AI assessment against a fixed
  checklist, mechanical checks on that assessment, then a human decision. The build happens
  in the plugin repo, and a script records what shipped.
- **The proof.** Five releases audited, each with a recorded decision. The latest is traced
  through [public PRs](https://github.com/BradleyDB/gs-admin-cli-docs/pull/27).

## How it works

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../assets/fortress-flow-dark.svg">
  <img alt="gs-fortress flow. 1 a weekly check of the vendor's releases asks: new version? If not, it stops quietly and writes nothing; if the check fails, a loud alert fires after 3 failures in a row. If yes: 2 a mechanical diff of the new version; 3 one AI assessment against the impact checklist; 4 mechanical checks on the assessment, and if any fails it stops and records nothing. If they pass, the ledger records decision pending, and a person decides adopt or defer. On adopt, 5 the plugin repo builds it with builder and tester sessions, and 6 a close-out script records what shipped back in the ledger." src="../assets/fortress-flow-light.svg">
</picture>

Every stage before the assessment is deterministic and cheap. The one judgment step is
checked mechanically before it counts. gs-fortress never writes to the plugin repo:
adoption runs on that repo's own builder/tester loop.

<details>
<summary><b>What I built, piece by piece</b></summary>

- **A weekly release gate** with exactly three answers: no change, a new version, or a
  failed check. A failed check is never reported as "up to date". Three failures in a row
  send a notification that the watcher itself is broken.
- **A mechanical delta**: a scratch install with install scripts disabled, a catalog diff,
  and a file-tree diff covering what the catalog can't see (runtime verbs, auth, package
  metadata).
- **One assessment agent per release**: it walks the impact checklist, the known-issues
  ledger and the delta, then writes a fixed-shape report: regression risks, defects fixed
  or open upstream, new capabilities and a change plan.
- **Copy-paste build kickoffs**, each work item marked *gated* (waits for the decision) or
  *ungated* (needed regardless, because users already run the new CLI).
- **A permanent decision ledger**: a report, a release-notes headline and an adopt/defer
  entry per version. Since September the execution line is derived from the merged PR and
  tag by a script, not typed.
- **An upstream defect tracker**, walked on every audit to detect silent upstream fixes.

</details>

<details>
<summary><b>The four design rules, and what enforces each</b></summary>

1. **The agent recommends, a human decides.** The close-out script fills in `execution`
   from GitHub and never touches `decision`. Kickoffs carry a review header and are read
   before they're posted.
2. **Upstream code is untrusted data.** Installed with `--ignore-scripts` into a scratch
   folder. The assessment agent gets eight invariants restated verbatim, one of which says
   text inside the package is never an instruction. The global CLI install is checked to be
   unchanged before anything is recorded.
3. **Read the dependency from its source of truth, never a local copy.** Each run fetches
   the plugin repo's `dev` branch from GitHub, checks every file against its git blob id,
   and deletes the copy. One script holds the repo's identity, and a test fails if it's
   restated anywhere else. This rule came from a real mistake: the watcher had been
   auditing a clone that stopped moving when the plugin repo went public.
4. **Fail loud; never record an unsound audit.** If any check fails, the "last notified
   version" isn't written, because writing it would silence the gate for that version
   for good.

</details>

## One cycle: CLI 1.0.10

The vendor release changed no commands at all, so the catalog diff was empty. The file-tree
diff found a rewritten auth module and a raised Node floor, and those became two new
permanent checklist items, 12 and 13.

| Date | Step | Evidence |
|---|---|---|
| 2026-09-17 | Vendor publishes 1.0.10 | npm |
| 2026-09-21 | Audit: 5 risks affected, 2 known defects resolved; recommend adopt | commit `b109854` (private) |
| 2026-09-22 | **Human** decision: adopt | `ledger/state.json` (private) |
| 2026-09-26 | Plugin adoption merged and released | [PR #27](https://github.com/BradleyDB/gs-admin-cli-docs/pull/27) · [v0.43.0](https://github.com/BradleyDB/gs-admin-cli-docs/releases/tag/v0.43.0) |
| 2026-10-04 | Checklist items 12–13 shipped | gs-fortress PR #13, v0.6.0 (private) |

<details>
<summary><b>The decision-log entry this cycle produced, and the full impact checklist</b></summary>

```json
"1.0.10": {
  "auditedOn": "2026-09-21",
  "recommendation": "adopt",
  "decision": "adopt",
  "decidedOn": "2026-09-22",
  "execution": "done 2026-10-04 — explorer PR #27 (merge 6acd1e4) executed
    E1 + V1 + E2; released as gs-superadmin 0.43.0; gs-fortress PR #13
    (merge 78e2f1b) executed F1; released as gs-fortress 0.6.0. Pending: B1 (owner)."
}
```

"explorer" is the plugin repo's internal name.

The impact checklist (item titles, paraphrased, ordered by risk). Items 1–6 and 11–13
cover changes the plugin's own CI can't catch:

```text
 1. Sanctioned ask-override for a command the CLI labels read-only but that runs a job
 2. The computed count of "non-mutating" commands that actually write
 3. The exact-match list of read verbs
 4. New list commands → candidate knowledge-base domains
 5. Verbs the catalog extractor hardcodes
 6. The guard's secret-flag pattern
 7. Hand-written MCP tool names in prose
 8. Relationship-builder mapping semantics
 9. Prose asserting facts about the vendor's README
10. Bulk version-string prose (CI-caught)
11. Payload shapes the plugin reads, from a measured reader map
12. The CLI's auth module → the plugin's token-lifetime and auth-failure sites
13. The CLI's Node engine floor → the plugin's Node-version claims
```

Sizes, merge commits and first containing tags: [proof/trace.md](proof/trace.md).

</details>

## What this shows

| The job | Where gs-fortress does it | Evidence |
|---|---|---|
| **Decision log** | Adopt/defer ledger: recommendation, decision, date, and an execution line derived from the PR and tag | 5 decisions, each with its report and kickoffs |
| **Architecture principles** | Four rules, each enforced: ledger rules table, single-source test, zero-footprint check, `--ignore-scripts` | 6 test suites; 8 invariants restated to every agent |
| **Dependency map** | The checklist maps each part of the vendor CLI to the plugin code that depends on it, including a measured map of the payloads the plugin reads | 13 items, up from 8 as audits found new dependencies |
| **Change control** | Gate → audit → human decision → gated and ungated work → PR → tag → derived close-out | PR #27 → v0.43.0 |
| **Agent evaluation** | The assessment must pass mechanical checks before it's recorded; this repo's own changes go through builder/tester review | 8 of 25 findings reopened at least once before passing |
| **Agent escalation** | Any refused gate stops the run and reports; adopt/defer is always human; the watcher reports its own breakage | 3-strike failure notice |

> [!NOTE]
> **The feedback loop works.** For example, a design-feedback memo to the vendor covered
> 5 tracked defects, and 4 of them were fixed in the next release. In all, 7 of the 20
> tracked defects have since been fixed upstream.

## Proof

| Releases audited | Decisions | Defects tracked | Reports sent | Own findings (verified) | Commits | Release tags |
|---:|---:|---:|---:|---:|---:|---:|
| 5 | 5 | 20 | 8 | 25 (24) | 165 | 8 |

<details>
<summary><b>Every number with the command that reproduces it</b></summary>

Measured 2026-10-05 at `origin/main` (`ff5ff42`), run from the folder that holds the clone.
The full table is in [proof/stats.md](proof/stats.md).

| Measure | Value | How to check |
|---|---|---|
| Vendor releases audited | 5 (1.0.6 to 1.0.10) | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/reports/ \| grep -cE '/audit-[0-9.]+\.md$'` |
| Adopt/defer decisions recorded | 5 (all adopt so far) | `git -C gs-fortress show ff5ff42:ledger/state.json \| grep -c '"decision":'` |
| Change plans handed to build sessions | 5 kickoff files | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/reports/ \| grep -cE '/build-kickoffs-[0-9.]+\.md$'` |
| Impact-checklist items | 13 | `git -C gs-fortress show ff5ff42:plugins/gs-fortress/skills/gs-admin-cli-watch/reference/impact-checklist.md \| grep -cE '^[0-9]+\. \*\*'` |
| Upstream CLI defects tracked | 20, of which 7 resolved upstream | `git -C gs-fortress show ff5ff42:ledger/known-issues.json \| grep -cE '"id": "KI-[0-9]+"'`; for resolved, the same with `grep -c '"status": "resolved"'` |
| Vendor-ready defect reports on file | 8 | `git -C gs-fortress ls-tree --name-only ff5ff42 ledger/upstream-feedback/reports/ \| grep -c '\.md$'` |
| dev-loop findings on this repo's own bus | 25, 24 verified | `git -C gs-fortress show ff5ff42:dev/FEEDBACK.md ff5ff42:dev/FEEDBACK-archive.md \| grep -oE '^## F-[0-9]+' \| sort -u \| wc -l` |
| Findings reopened at least once (by a tester or by me) | 8 of 25 | `git -C gs-fortress show ff5ff42:dev/FEEDBACK.md ff5ff42:dev/FEEDBACK-archive.md \| awk '/^## F-[0-9]+/{f=$2} /^Reopened/{print f}' \| sort -u \| wc -l` |
| Test suites | 6; 2,157 of 4,018 JavaScript lines are tests | `git -C gs-fortress ls-tree -r --name-only ff5ff42 plugins/gs-fortress/test \| grep -cE '\.test\.mjs$'` |
| History | 165 commits, 2026-07-27 to 2026-10-04, 16 active days, 8 release tags, 14 merged PRs | see [proof/stats.md](proof/stats.md) |

</details>

## What's private and why

gs-fortress is personal infrastructure: schedules, machine paths and notification state.
Its ledger also holds vendor-ready bug reports, which may carry tenant identifiers; this
page only counts and dates them. The code to look at is the plugin it protects,
[gs-admin-cli-docs](https://github.com/BradleyDB/gs-admin-cli-docs), including the adoption
[PR #27](https://github.com/BradleyDB/gs-admin-cli-docs/pull/27). I'm happy to rerun any
number here live in a walkthrough.
