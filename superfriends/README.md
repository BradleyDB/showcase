# superfriends

**AI sessions start cold, forget everything between sessions and grade their own work generously. superfriends is the rulebook that lets them build across weeks, models and repos anyway, with a person deciding at the points that matter.**

<table><tr>
<td align="center" width="25%"><h2>91</h2>findings through these rules in the system's other three repos</td>
<td align="center" width="25%"><h2>14</h2>past findings the dev-loop rules cite as the incident behind them</td>
<td align="center" width="25%"><h2>11</h2>commits that name the finding behind the change</td>
<td align="center" width="25%"><h2>9</h2>releases from 23 merged pull requests</td>
</tr></table>

> [!IMPORTANT]
> **The session that wrote a fix never verifies it.** The other role does, against a build
> it has proved it loaded. Merging stays a person's call.

Part of the [gs-admin toolchain](../gs-admin-toolchain/README.md): the process its AI
sessions follow, and the rules [dev-utils](../dev-utils/README.md) turns into code.
Private repository · in use · measured 2026-10-06. This page covers the four
development-process skills; the repo also holds personal utilities that aren't part of
this system.

## In 30 seconds

- **The problem.** A build spread over many AI sessions drifts: a shared format gets
  quietly patched, a fix is "verified" against a stale copy, a deferred bug is forgotten.
- **What I built.** Four Claude Code skills, shipped as one plugin. **handoff-plan** turns a
  plan into files a fresh session on any model can execute. **dev-loop** and **team-loop**
  run builder and tester sessions against each other. **external-pr-intake** gives every
  outside pull request the same opening review.
- **The proof.** The system's other three repos run on dev-loop, and the last two
  gs-fortress audits handed their builds off as handoff-plan sets, including the
  [worked example](../gs-admin-toolchain/README.md#worked-example-cli-1010-from-vendor-release-to-shipped-fix).

## How it works

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../assets/superfriends-flow-dark.svg">
  <img alt="superfriends process in 7 numbered steps. 1 handoff-plan writes the plan: stable work-item IDs, frozen contracts and a session map. 2 a person reviews the plan and starts each session with its kickoff prompt. 3 a builder session builds only its assigned items and names a judge for each fix; if a frozen contract must change, it stops and reports to a person, who decides on a version bump. 4 a tester session proves which build it loaded, then verifies each fix or sends it back to step 3; a person steps in when needed to set a severity tier, defer a finding or rule it WONTFIX. 5 the session records what shipped: a ledger line and as-shipped notes, the next session’s only memory. 6 the release re-decides deferrals, runs code review, strips dev-only files in one commit and opens the PR, then stops. 7 a person merges the PR, or has a session merge it." src="../assets/superfriends-flow-light.svg">
</picture>

<details>
<summary><b>The flow, step by step</b></summary>

A plan starts as a conversation, and handoff-plan turns it into files (1). Each work item
gets a permanent ID and a concrete "done when". Interfaces that more than one session
builds against are listed as frozen contracts, and a session map assigns two to four
items to each session, one repo per session. I review the set and start each session
with its copy-paste kickoff prompt (2). The prompt carries nine required elements: read
the plan and nothing else, build these IDs only, check dependencies are merged, review,
open a PR and leave it unmerged, and record what shipped.

A builder session builds its items (3). Before a fix counts, it names the class of defect
behind the reported instances, tries a sibling case the tester didn't list, and names an
independent judge of correctness. If a frozen contract turns out to be wrong, the session
stops and reports; a contract change is a version bump and a sync of every copy, never a
quiet patch. A tester session then proves which build it loaded (4): a token on dev-loop,
commit ancestry on team-loop. Only then does it verify each fix or send it back. I step
in when a round needs it, with each ruling written as a dated line.

The session ends by recording what actually shipped (5): one ledger line, plus an "as
shipped" note under each item. That record is the next session's only memory. The
release (6) re-decides every deferral, runs code review, strips the dev-only files in one
commit, opens the PR and stops. I merge, or tell a session to (7).

</details>

## The four skills

| Skill | Its job | What it never does | Status |
|---|---|---|---|
| **handoff-plan** | Turns a planning conversation into a plan file (IDs, house rules, frozen contracts, session map, session ledger), kickoff prompts and a cleanup plan | Hand off a chat transcript, or let a session patch a frozen contract | In use: gs-fortress's build kickoffs |
| **dev-loop** | Builder and tester sessions on one machine, sharing a findings file, each handoff proven by a token | Let a session verify its own fix, push `main`, or merge on its own | In use in the system's other three repos |
| **team-loop** | The same loop for several people and machines: GitHub Issues as the findings log, provenance by commit ancestry, rules enforced by GitHub | The same | Designed; no repo runs it yet |
| **external-pr-intake** | A fixed opening for an outside PR: mechanical checks, the repo's gates on a trial merge, ten design questions, a change list | Act on the PR without a yes for each step, or block a merge | Developed on the first outside PR; refined and used live on the second and third |

<details>
<summary><b>The design rules, and what enforces each</b></summary>

1. **The plan file is the interface, never a chat transcript.** Every kickoff prompt must
   carry the nine elements, and the author re-reads the set as a cold executor before
   handing it over.
2. **Contracts freeze once something builds on them.** A change means stop, report, bump
   the version and sync every copy. The plan states what isn't frozen, too.
3. **Judge the class, not the instance.** A fix that names a defect class must name an
   independent judge, and a finding reopened twice needs a `Redesign:` line before it can
   be fixed again. dev-utils refuses a flip that breaks either rule.
4. **Prove the build before the verdict.** A missing canary means no verdicts at all; a
   stale token means reload and recheck.
5. **Ceremony in proportion to risk.** Every finding declares a tier (polish, normal or
   high) by asking whether what ships is wrong for a user. Polish rides the next round;
   high gets a round of its own and blocks even a feature merge.
6. **Deferral is re-decided at every release.** A deferral carries a reason and a reopen
   trigger, and the next release reopens it.
7. **A rule carries the incident that produced it.** "A defect in a fix's own mechanism
   reopens that finding" cites one mechanism that took five finding numbers and five
   rounds, while the one fix that carried a `Redesign:` line never came back.
8. **Where a plan may live is decided by a script.** Handoff sets are ignored in public
   repos and tracked in private ones. The resolver stops and asks on anything ambiguous,
   and a test covers every exit path. It exists because a handoff set once reached a
   public `dev` branch: a release strip is not a privacy boundary.

</details>

<details>
<summary><b>Excerpts: the severity rule and the intake questions</b></summary>

The severity question, as dev-loop states it (abridged):

```text
Is the shipped behaviour wrong for a user of this repo?
  No (tests, tooling, docs, lint; what ships is correct)   -> polish
  Yes                                                     -> normal
  Yes, and it must not reach anyone before the fix lands  -> high
  Unsure                                                  -> normal
Reachability first: a state the artifact refuses to create is polish at most.
```

The design questions external-pr-intake answers for every outside PR, one line each with
a file and line as evidence (titles only):

```text
D1 One canon             D6 Fence discipline
D2 Always-on cost        D7 Lock strength
D3 Exemplar proportion   D8 Scope and register
D4 Evidence resolves     D9 Fluency
D5 Walk                  D10 Siblings
```

</details>

## One cycle: the CLI 1.0.10 build plan

The build after the 1.0.10 audit ran as a handoff-plan set. Its session map (abridged;
the [system page](../gs-admin-toolchain/README.md) traces the PRs):

| Session | Repo | Items | Waits for the adopt decision? | Depends on |
|---|---|---|---|---|
| E1 | plugin | CP-2 to CP-5 | no | — |
| V1 | plugin | CP-6 | no | E1 (same branch) |
| E2 | plugin | CP-1, CP-7 | yes | E1 merged |
| F1 | gs-fortress | CP-8 | no | — |
| B1 | the owner | CP-9, the upstream memo | no | — |

The plan froze four contracts, among them the plugin's measured read surface.

## What this shows

| The job | Where superfriends does it | Evidence |
|---|---|---|
| **Decision log** | Dated rulings in each plan; a dated line for every tier, deferral and verdict; a session ledger per plan | 91 findings; 2 handoff sets |
| **Architecture principles** | Eight rules, each tied to a mechanism, most to the incident behind them | 14 cited findings |
| **Dependency map** | A frozen-contracts section in every plan: each shared interface, its version, and what may not change | 4 contracts in the 1.0.10 plan |
| **Change control** | One-way flow from feature to `dev` to `main`, a one-commit release strip, tags only after a person's merge | 9 releases, 23 merged PRs |
| **Agent evaluation** | The other role verifies against a proven build, with the pass bar stated before measuring | 84 of 91 findings verified |
| **Agent escalation** | Sessions stop on a contract change or an unmerged dependency; intake reports and never acts | the dashed steps above |

## Proof

| Commits | Release tags | Merged PRs | Skills (covered here) | Lines in the four skills | Resolver tests |
|---:|---:|---:|---:|---:|---:|
| 76 | 9 | 23 | 10 (4) | 1,877 | 6 cases |

<details>
<summary><b>Every number with the command that reproduces it</b></summary>

Measured 2026-10-06 at `origin/main` (`1bd3309`), run from the folder holding the clone.
The full table is in [proof/stats.md](proof/stats.md).

| Measure | Value | How to check |
|---|---|---|
| Findings through dev-loop in the system's three repos | 91 (35 + 25 + 31) | per repo in [the system page's proof](../gs-admin-toolchain/proof/stats.md) |
| Past findings the dev-loop rules cite | 14 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/dev-loop/SKILL.md \| grep -oE 'F-[0-9]+' \| sort -u \| wc -l` |
| Commits that name the finding that drove them | 11 | `git -C gs-admin-superfriends log 1bd3309 --format=%s \| grep -cE 'F-[0-9]+'` |
| gs-fortress build kickoffs written as handoff-plan sets | 2 | `git -C gs-fortress grep -l '^## Session map' ff5ff42 -- ledger/reports/ \| wc -l` |
| Frozen contracts in the 1.0.10 build plan | 4 | see [gs-fortress's proof](../gs-fortress/proof/stats.md) |
| Release tags | 9 | `git -C gs-admin-superfriends tag --merged 1bd3309 \| wc -l` |
| Merged pull requests | 23, none from anyone else | `gh pr list -R BradleyDB/gs-admin-superfriends --state merged --limit 2000 --json number --jq length` |
| Lines in the four skills (SKILL.md and README.md) | 1,877 | see [proof/stats.md](proof/stats.md) |
| Design questions asked of every outside PR | 10 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/external-pr-intake/SKILL.md \| grep -cE '^- [*][*]D[0-9]+ '` |
| Handoff-home resolver test cases | 6 | `git -C gs-admin-superfriends show 1bd3309:plugins/superfriends/skills/handoff-plan/scripts/test-handoff-home.sh \| grep -cE '^ *run "'` |
| Commits | 76, 2026-06-27 to 2026-10-06, 19 active days | `git -C gs-admin-superfriends rev-list --count 1bd3309` |

</details>

## Trade-offs

- **Prose can't be unit-tested.** So a tester runs every changed skill for real and
  records the walk, and dev-utils pins a hash of the skill text.
- **No findings log of its own.** A skill problem is logged where it surfaced, and the
  fixing commit names it. No CI; a local pre-push hook guards `main`.
- **team-loop is unproven.** No repo runs it yet; its CLI half is tested only against a
  fake `gh`.

## What's private and why

superfriends is personal infrastructure: the skill text carries machine paths and
references to other private repos, and the repo holds unrelated utilities and reference
material that isn't mine to publish. The public tool these skills build is
[gs-superadmin](https://github.com/BradleyDB/gs-admin-cli-docs), whose history shows the
loop's handoffs and verdicts. I'm happy to rerun any number here live in a walkthrough.
