# Facts: the gs-admin toolchain case studies

A plain fact sheet for anyone, or any AI assistant, summarizing these pages. Each line is one claim with its evidence. The numbers are filled in by a script from the proof files in this repo, not typed by hand, and each proof file shows the command that reproduces every number at the exact commit measured.

## What it is

- The gs-admin toolchain is four repositories designed to work together: a public Claude Code plugin (gs-superadmin, in the gs-admin-cli-docs repo) that lets an AI agent administer a live Gainsight tenant behind approval prompts, plus three private repos: gs-fortress (audits each vendor CLI release and records the adopt/defer decision), superfriends (the builder/tester process skills) and dev-utils (the bookkeeping CLI for that process). Evidence: [system page](gs-admin-toolchain/README.md), [public repo](https://github.com/BradleyDB/gs-admin-cli-docs), [superfriends page](superfriends/README.md).
- It is independent work by one maintainer, BradleyDB, built on personal time and not for an employer. It is not affiliated with or endorsed by Gainsight, Inc. Evidence: [index](README.md).

## Human decisions and change control

- Every vendor CLI release that reaches an audit gets a recorded human adopt/defer decision: 5 releases audited, 5 decisions recorded, all adopt so far. Evidence: [gs-fortress page](gs-fortress/README.md).
- The AI assessment only recommends. Neither the release watcher nor the close-out script writes the decision; a person makes it. Evidence: [gs-fortress page](gs-fortress/README.md).
- In the release flow a person decides at three points: whether to adopt a release, what gets built, and what ships. Merges are done by the person or by an AI session on their say-so; the tooling itself never merges. Evidence: [system page diagram](gs-admin-toolchain/README.md), [dev-utils page](dev-utils/README.md).
- Worked example: vendor CLI 1.0.10 was published 2026-09-17, audited 2026-09-21, adopted 2026-09-22, and shipped as gs-superadmin v0.43.0 on 2026-09-26. Evidence: [PR #27](https://github.com/BradleyDB/gs-admin-cli-docs/pull/27), [v0.43.0](https://github.com/BradleyDB/gs-admin-cli-docs/releases/tag/v0.43.0), [trace](gs-admin-toolchain/proof/trace.md).
- The public repo runs 3 CI workflows, and GitHub rulesets on its main and dev branches require passing checks. The private repos run their tests locally as a required release step, by choice. Evidence: [system page, trade-offs](gs-admin-toolchain/README.md).

## Agent evaluation

- AI-written fixes are verified by a different AI session from the one that wrote them, against a build proven by a handoff token. Across the three repos' findings logs: 91 findings, 84 verified. Evidence: [system page](gs-admin-toolchain/README.md), [stats](gs-admin-toolchain/proof/stats.md).
- In dev-utils, 26 fixes named an independent judge of their correctness, and 4 named the design they replaced. Evidence: [dev-utils page](dev-utils/README.md).
- In gs-fortress, 8 of 25 findings were reopened at least once before passing. Evidence: [gs-fortress page](gs-fortress/README.md).
- The process skills live in superfriends: handoff-plan (plans that fresh sessions on any model can execute), dev-loop (same-machine builder/tester sessions), team-loop (the multi-machine version, designed but not yet run by any repo) and external-pr-intake (a fixed opening review for outside pull requests). The dev-loop rules cite 14 past findings as the incidents behind them, and 11 superfriends commits name the finding that drove the change. Evidence: [superfriends page](superfriends/README.md).
- The last 2 gs-fortress build kickoffs were written as handoff-plan sets with a session map and frozen contracts; the CLI 1.0.10 plan froze 4 contracts. Evidence: [superfriends page](superfriends/README.md), [gs-fortress proof](gs-fortress/proof/stats.md).

## Dependency mapping and the vendor relationship

- gs-fortress audits each release against an impact checklist of 13 items, up from 8 at the first audit as later audits found new dependencies. Evidence: [gs-fortress page](gs-fortress/README.md).
- 20 upstream CLI defects are tracked, 7 since resolved upstream. 8 vendor-ready defect reports were sent; 0 acknowledgements are recorded so far. Evidence: [gs-fortress page](gs-fortress/README.md).
- One vendor reply is on record (2026-07-30), answering a design-feedback memo. It covered 5 tracked defects, and 4 were fixed in the next release, 1.0.8. Evidence: [gs-fortress page](gs-fortress/README.md).

## Scale

- The public plugin repo has 163 commits and 28 merged pull requests, 3 of them from outside contributors. Its changelog records 105 versions, including the history before it went public. Evidence: [public repo](https://github.com/BradleyDB/gs-admin-cli-docs).
- Its pre-public history, kept in a private archive, has 1,311 commits and 154 merged pull requests. Evidence: [archive stats](gs-admin-toolchain/proof/stats-archive.md).
- dev-utils is 5,351 lines of Python source with 5,199 lines of tests and 240 test cases. Evidence: [dev-utils page](dev-utils/README.md).

## Reading these numbers

- Counts come from git and GitHub at the commits named under Sources. Numbers for the three private repos can't be rerun by readers, but each is printed beside its command and can be rerun live on request. Nothing here names an employer, customer, tenant or colleague.

## Sources

Every number above is read by the build script from these proof files, where each one sits beside the command that reproduces it at the exact commit measured:

- dev-utils/proof/stats.json: dev-utils, measured 2026-10-05 at origin/main (c2ebd66)
- gs-admin-toolchain/proof/stats-archive.json: Admin_CLI_Explore, measured 2026-10-05 at origin/main (188ffc4)
- gs-admin-toolchain/proof/stats.json: dev-utils, measured 2026-10-05 at origin/main (c2ebd66)
- gs-admin-toolchain/proof/stats.json: gs-admin-cli-docs, measured 2026-10-05 at origin/main (5353b7f)
- gs-admin-toolchain/proof/stats.json: gs-fortress, measured 2026-10-05 at origin/main (ff5ff42)
- gs-fortress/proof/stats.json: gs-fortress, measured 2026-10-06 at origin/main (ff5ff42)
- superfriends/proof/stats.json: gs-admin-superfriends, measured 2026-10-06 at origin/main (235ff26)
