# How this system learns

**Every problem I hit becomes a new capability or a lasting safeguard, and every result is measured. Here is what changed since the last publish.**

<table><tr>
<td align="center" width="25%"><h2>8</h2>capabilities shipped since the 2026-10-06 publish</td>
<td align="center" width="25%"><h2>6</h2>lessons learned, each traced to its root cause</td>
<td align="center" width="25%"><h2>4 of 6</h2>of those lessons are built into code, not just written down</td>
<td align="center" width="25%"><h2>85.9%</h2>of verified fixes passed an independent tester the first time</td>
</tr></table>

> [!IMPORTANT]
> **Every lesson gets built in.** When something goes wrong, I find the root cause and add a safeguard so it can't quietly happen again: a rule, a step every session performs, or code that refuses it.

## In 30 seconds

- **Built:** email engagement dashboards whose health signals catch a program that runs but sends nothing (they caught a live one while being built), Power List coverage in the dependency reports, and a CLI audit that now finds by itself what two audits found by hand.
- **Learned:** a retrospective across a project's sessions surfaced 15 recurring problems in its first run, and each one now has a fix plan.
- **Measured:** 85.9% of verified fixes pass an independent tester the first time, and when a fix fails twice, the rule forces a redesign.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../assets/gs-admin-toolchain-learning-dark.svg">
  <img alt="Since the last publish, newest first. Oct 18: The pages showed what the system does, not whether it gets better; built: This page: every number re-runs from its command. Oct 17: Lessons were lost between one session and the next, where a one-session retro can't see; built: project-introspect: a retro across every session. Oct 15: A journey program can look healthy while doing nothing: it takes in participants and sends nothing, and the vendor's analytics show one program at a time; built: Engagement dashboards with health signals; they caught a live program failing silently. Oct 15: Two audits in a row found the same four things by hand; built: An audit that finds those four things itself. Oct 12: An urgent fix had to be cherry-picked around work parked on dev; built: Long-lived branches; dev stays shippable. Oct 12: Every fix batch triggered another full code review; built: One code review per release. Oct 11: A round's checks lived in free prose that nothing could read; built: Checks recorded as states at every handoff. Oct 7: The reports missed journeys whose participants come from a Power List; built: Reports follow Power List journeys (v0.43.4)." src="../assets/gs-admin-toolchain-learning-light.svg">
</picture>

## What I built, and what it solved

| Shipped | The problem it solved |
|---|---|
| **repo-showcase refresh mode: this page**<br><sub>Added · 2026-10-18</sub> | The pages showed what the system does, not whether it gets better<br>**→ 51 numbers back-filled at the last publish, each with its command** |
| **project-introspect: a retro across every session of a project**<br><sub>Added · 2026-10-17</sub> | Lessons were lost between one session and the next, where a one-session retro can't see<br>**→ 15 recurring problems found in its first run, each with a fix plan** |
| **Email engagement dashboards that catch silent failures**<br><sub>Added · 2026-10-15</sub> | A journey program can look healthy while doing nothing: it takes in participants and sends nothing, and the vendor's analytics show one program at a time<br>**→ Caught a live program doing exactly that while the dashboards were being built** |
| **The CLI audit finds by itself what the last two audits found by hand**<br><sub>Added · 2026-10-15</sub> | Two audits in a row found the same four things by hand |
| **Long-lived feature branches beside main and dev**<br><sub>Added · 2026-10-12</sub> | An urgent fix had to be cherry-picked around work parked on dev |
| **dev-loop: one code review per release, one home per rule**<br><sub>Simplified · 2026-10-12</sub> | Every fix batch triggered another full code review<br>**→ first-pass rate held: 84.5% → 85.9%** |
| **A handoff records the round's checks as states, not prose**<br><sub>Added · 2026-10-11</sub> | A round's checks lived in free prose that nothing could read |
| **Dependency reports follow Power List journeys**<br><sub>Added · 2026-10-07</sub> | The reports missed journeys whose participants come from a Power List |

<details>
<summary><b>The story behind each one</b></summary>

#### repo-showcase refresh mode: this page <sub>2026-10-18</sub>

**The problem.** The 2026-10-06 pages showed what the system does, not whether it gets better: their trend measures had no baseline value<br>
**What I built.** Freezes a before (every repo at a commit id, plus the retro run and the transcripts it read), re-runs the same commands at each refresh, appends the results to proof/metrics.csv and renders this page from them.<br>
**What it did.** 51 numbers back-filled at the 2026-10-06 commits from history the repos already held, each beside its command; the first-pass rate at baseline is 84.5%.

#### project-introspect: a retro across every session of a project <sub>2026-10-17</sub>

**The problem.** Superfriends issue #31: a multi-session project lost the most at the gaps between sessions (context missing, decisions re-argued, facts re-derived), which a one-session retro cannot see<br>
**What I built.** Reads every session of a project in a date window, finds the problems that recur and the gaps at each handoff with session and turn citations. The second release added a fix plan with typed dependencies, a triage mode (one question per problem) and a session map, after the first real run's output said nothing about what changes where or in what order.<br>
**What it did.** recurring problems it surfaced in its first run, each with a fix plan: 15<br>
**What its first run found.** 51 sessions read; 15 problems that recurred across them; 29 fixes proposed, landing in superfriends skills (13), global instructions (3), plugin repo (7), memory (5), user settings (1).

#### Email engagement dashboards that catch silent failures <sub>2026-10-15</sub>

**The problem.** A program that takes in participants but sends nothing looks like it is working, and the vendor's own analytics show one email program at a time, so nobody compares them<br>
**What I built.** A read-only skill that compares every email program at once. Health signals flag a program that is running but not doing anything, such as bringing in participants with no emails going out, a failure that is hard to spot otherwise. A dashboard is a self-contained page, not a pile of CSVs: it refreshes with one command and publishes a leaders' copy to a shared folder, so the numbers stay current and shareable. It was on the dev branch at the baseline and reached main in v0.54.0. v0.56.2 made customer lists current on every refresh (F-548) and hardened locks and resume after the release-gate review; v0.56.3 is polish from its verdict round.<br>
**What it did.** while it was being built, the health view caught a live program that took in participants and sent nothing

#### The CLI audit finds by itself what the last two audits found by hand <sub>2026-10-15</sub>

**The problem.** Audit-1.0.12, change-plan item CP-8 (F-026): four things the 1.0.11 and 1.0.12 audits found by hand<br>
**What I built.** A new impact-checklist item for commands with per-version facts, a report of description-only catalog changes, a walk comparing the issue ledger with the plugin's recorded verdicts, and a comparison against the last audited CLI version. The plugin side of the 1.0.12 adoption shipped inside gs-admin-cli-docs v0.56.2.

#### Long-lived feature branches beside main and dev <sub>2026-10-12</sub>

**The problem.** The gs-admin-cli-docs 0.43.4 hotfix had to be cherry-picked around a multi-session program sitting on dev<br>
**What I built.** Finding numbers unique across branches, a catch-up verb that merges dev in and resolves the bus by rule, and a landing check before the branch merges; dev stays shippable. dev-utils v0.7.1 only re-pins a test; the dev-loop skill documents the branches in release-2026-10-17.

#### dev-loop: one code review per release, one home per rule <sub>2026-10-12</sub>

**The problem.** The dev-utils 0.7.0 retro over rounds 17 to 25 (F-034 to F-059)<br>
**What I changed.** A later fix batch is judged by its tester round, not another code review; each rule lives in one place with a judge before a new mechanism's first handoff; a repeat of a known defect class reopens its entry.<br>
**What it didn't break.** findings verified with no failed fix: 84.5% → 85.9% (all three buses; the window also holds work before this change)

#### A handoff records the round's checks as states, not prose <sub>2026-10-11</sub>

**The problem.** A round's checks lived only in the builder's free-prose handoff comment, worded differently each round, so nothing could read them (dev-utils IDEAS, 2026-10-10)<br>
**What I built.** dev-utils writes a token-keyed Checks line (battery, CI, review, walk) at every handoff, declared per repo in the bus header; the dev-loop skill documents it.

#### Dependency reports follow Power List journeys <sub>2026-10-07</sub>

**The problem.** F-487: the reports returned no journeys for an object most programs read through a Power List, and wrongly said Power Lists had no CLI surface<br>
**What I built.** deps-report and email-report now resolve journey programs whose participants come from a Power List, naming the objects, connection and fields each list reads. Shipped as a hotfix from main, ahead of the unreleased dashboard work on dev.

#### How the learning loop itself grew

1. Fix the reported instance · _always_
2. A rule carries the incident behind it · _in use_
3. Judge the class, not the instance; two failed fixes force a redesign · _in use_
4. Single-session retro: /introspect fixes the instructions a session ran under · _in use_
5. **Cross-session retro: /project-introspect finds what recurs and what's lost between sessions** · _new · 2026-10_
6. **Retros feed a measured refresh of this page** · _new · 2026-10_

</details>

## Lessons learned, and the safeguards they added

When something went wrong, I traced it to its root cause and added a safeguard so it can't quietly happen again.

| What went wrong | The safeguard | Came back? |
|---|---|---|
| An audit read a stale copy of the repo | The watcher fetches the repo itself | No, in the two audits since |
| A fix could be verified on the wrong build | A canary token proves which build was tested |  |
| One defect took five rounds of fixes | Two failed fixes force a redesign | Caught: 5 of 6 twice-failed fixes carry the redesign |
| Private plans reached a public branch | A script decides where a plan may live |  |
| One code review used half a session's budget | Verifiers batched by file |  |
| Seven decisions asked in one batch | One decision per question | Yes, in 13 of 51 sessions (retro 2026-10-17) |

<details>
<summary><b>The root cause behind each one</b></summary>

| What went wrong | Root cause: the class, not the instance | The safeguard, in full |
|---|---|---|
| An audit read a stale copy of the plugin repo (2026-09-22) | Inputs trusted without checking freshness | The watcher fetches the repo from GitHub itself (gs-fortress 0.6.0) (code refuses it) |
| A fix could be verified against a different build than the one that shipped | A verdict with no proof of what was tested | Canary token: the tester proves which build it loaded, or gives no verdict; dev-utils refuses a stale token (code refuses it) |
| One mechanism took five finding numbers and five rounds | Fixing instances, not the defect class | Two failed fixes require a Redesign: line; dev-utils refuses the flip without one (code refuses it) |
| A handoff set reached a public dev branch | Treated the release strip as a privacy boundary | A resolver script decides where a plan may live; tests cover every exit path (code refuses it) |
| One verifier per review finding used up over half a session's budget | Cost of a fan-out never measured | Verifiers batched by file, finders on a cheaper model (a written rule) |
| Seven decisions asked as one batched list, every option recommended | Asks shaped for the asker, not the decider | One decision per question; a recommendation checked against the record first (a written rule) |

</details>

## Measured over time

<table><tr>
<td align="center" width="50%"><h2>84.5% → 85.9%</h2>Findings verified with no failed fix, 2026-10-06 → 2026-10-18</td>
<td align="center" width="50%"><h2>15.5% → 14.1%</h2>Fixed findings reopened at least once, 2026-10-06 → 2026-10-18</td>
</tr></table>

Measures from session transcripts count **surviving sessions only**: Claude Code deletes a transcript 30 days after it was last modified, and sessions of excluded repos are left out.

<details>
<summary><b>Every measure, at every refresh</b></summary>

Each column is one measurement, at the commits its snapshot names. Rates count all history up to that commit; the line under a rate covers only what happened since the column before.

| Measure | Why it shows learning | 2026-10-06<br><sub>baseline-2026-10</sub> | 2026-10-18<br><sub>pre-retro-2026-10-18</sub> |
|---|---|---:|---:|
| Findings verified with no failed fix | Builders get it right more often | 84.5% | 85.9%<br><sub>86.9% of 107 since</sub> |
| Fixed findings reopened at least once | Fewer fixes fail their verdict | 15.5% | 14.1%<br><sub>13.0% of 108 since</sub> |
| Findings with two or more failed fixes | Instance-fixing dies out | 2 | 6 |
| Days from vendor release to first shipped fix (latest release) | The loop gets faster without dropping a gate | 9 (CLI 1.0.10) | 9 (CLI 1.0.10) |
| Turns before a session's first edit (median) | Sessions stop re-deriving what the last one knew | – | 49 |
| Tool errors per 100 tool calls | Fewer avoidable mistakes | – | 2.6 |

| Vendor release | Published | First fix shipped in | Days |
|---|---|---|---:|
| CLI 1.0.6 | 2026-07-17 | 0.25.0 | 11 |
| CLI 1.0.7 | 2026-07-29 | 0.27.0 | 1 |
| CLI 1.0.8 | 2026-08-12 | 0.31.1 | 3 |
| CLI 1.0.9 | 2026-08-21 | 0.36.1 | 14 |
| CLI 1.0.10 | 2026-09-17 | 0.43.0 | 9 |

</details>

## A lesson that traveled across repos

**A verdict needs proof of what was tested (L-2):** **gs-admin-superfriends**: dev-loop: a tester proves which build it loaded before any verdict → **dev-utils**: handoff mints the canary token and refuses a stale one → **gs-fortress**: the close-out writes the execution record from the PR and tag; nobody types it

<sub>The commit dates do not run in this order: dev-loop lived outside git until it moved into the superfriends repo on its first commit shown here, a month after dev-utils first shipped the token. Git cannot show which came first, so the order is the idea's, not the commits'.</sub>

<details>
<summary><b>What each capability could do then, and can do now</b></summary>

| Capability | 2026-10-06 | Now | What changed it |
|---|---|---|---|
| Agent evaluation | A separate AI tester judges every fix against a token-proven build | Same, and the first-pass rate is now measured: 85.9% | this refresh |
| Learning across sessions | One session's retro at a time | A retro across a project's sessions, with problems tracked by fingerprint across runs | project-introspect |
| Decision log | Adopt/defer decisions, recommendation kept apart from decision | Same; the releases audited since wait on a decision | vendor releases since |

</details>

<details>
<summary><b>How every number here is reproduced</b></summary>

Every number on this page is a row of [proof/metrics.csv](proof/metrics.csv): the date it describes, the snapshot (the commit ids it was measured at), the series, the value and the command that reproduces it. Rows are only ever appended; a changed definition starts a new series.

| Series | Unit | Definition |
|---|---|---|
| `bus.verified.v1` | count | findings whose heading says VERIFIED, live bus + archive |
| `bus.first-pass.v1` | count | VERIFIED findings with no failed-fix verdict (below) |
| `bus.fixed.v1` | count | findings with at least one Fix: note |
| `bus.reopened.v1` | count | findings with at least one failed-fix verdict |
| `bus.reopened-2plus.v1` | count | findings with two or more failed-fix verdicts |
| `bus.reopened-2plus-redesigned.v1` | count | of those, findings that carry a Redesign: line |
| `first-pass-rate.v1` | % | sum of bus.first-pass over sum of bus.verified, all repos with a bus, all history to that commit |
| `reopen-rate.v1` | % | sum of bus.reopened over sum of bus.fixed, same scope |
| `reopened-2plus.v1` | count | sum of bus.reopened-2plus, same scope |
| `reopened-2plus-redesigned.v1` | count | sum of bus.reopened-2plus-redesigned, same scope |
| `vendor.published.v1` | date | the vendor release's publish date, as its audit report records it |
| `vendor.shipped-as.v1` | version | the first product release the ledger's execution line names for that vendor release |
| `vendor.shipped-on.v1` | date | the date of that release's tag |
| `days-release-to-ship.v1` | days | vendor.shipped-on minus vendor.published |
| `gap-stated.v1` | count | lines of the baseline page carrying the gap's quoted words (1 = stated there) |
| `hop-date.v1` | date | commit date of a lesson's hop into a repo |
| `releases-since-baseline.v1` | count | release tags reachable from the released branch now but not from its baseline commit |
| `sessions.v1` | count | in-scope sessions in the project-introspect run: sessions whose transcript folder belongs to a refused repo, and sessions the owner dropped, are left out |
| `orientation-turns.median.v1` | turns | median turns before a session's first file edit, in-scope sessions with an edit |
| `retries-per-session.v1` | mean | retried tool calls per in-scope session (render_turnlog signals) |
| `repeated-reads-per-session.v1` | mean | files read again unchanged, per in-scope session |
| `tool-errors-per-100-calls.v1` | rate | tool errors per 100 tool calls, in-scope sessions |
| `recurring-problems.v1` | count | problems the run found in two or more in-scope sessions (union of their proposals' recurrence lists) |
| `problem-sessions.v1` | count | in-scope sessions in which a problem recurs (union of its proposals' recurrence lists); subject is the problem id |

A failed-fix verdict is a `Verdict:` line saying REOPENED or back to OPEN, or a `Reopened` note whose first 60 characters name a tester; one handoff token in one finding counts once. Transcript series come from a project-introspect run preserved with its snapshot, over surviving sessions only, and only from sessions of the repos shown here; the transcripts stay private. The baseline is what each repo's released branch held at the commit its page measured.

</details>
