# Case studies: governed AI tooling for a SaaS admin platform

Most of this work lives in private repositories, so these pages show it instead: what each
problem was, what I built, the principles behind it, and numbers that each come with the
command that reproduces them. No code is reproduced here, and no employer, customer or
tenant is named.

## Start here: the system

### [The gs-admin toolchain](gs-admin-toolchain/README.md)

**Keeping an AI admin co-pilot correct as its vendor CLI changes.** Four repositories,
designed to work together:

- a public plugin that lets an AI agent administer a live SaaS tenant behind approval prompts;
- a release watch that audits every new version of the vendor's CLI;
- the builder/tester process the changes go through;
- a small CLI that does that process's bookkeeping.

The page shows how one vendor release moves through all four in 12 numbered steps, with a
person deciding at three of them. It also covers the design principles the repos share,
one real release traced end to end through public PRs and tags, and how the system maps
to decision logs, architecture principles, dependency maps, change control, and agent
evaluation and escalation.

This is the page to read if you read one. The pages below go deeper on two of its parts.

## Deep dives

| Page | What it shows | Role in the system |
|---|---|---|
| [gs-fortress](gs-fortress/README.md): change control for a vendor CLI an agent depends on | A release watch that audits each upstream version against a 13-item impact checklist, recommends adopt or defer, and keeps the permanent decision ledger | Steps 2–4 and 12: watch, assess, close out; it also holds the ledger behind my step-5 decision |
| [dev-utils](dev-utils/README.md): the mechanical half of an AI build loop | A tested CLI that keeps the books for builder/tester AI sessions, so the models spend their effort on judgment, not bookkeeping | Steps 8 and 11: hand-offs and tags |

The fourth repo, the plugin itself, is public:
[gs-admin-cli-docs](https://github.com/BradleyDB/gs-admin-cli-docs) (the gs-superadmin
plugin). That's the place to read the code. The process skills (superfriends) are private
and described on the system page.

## How to read the numbers

Every figure on these pages sits beside the command that produced it, and each command
names the exact commit it measured. The full tables are in each page's `proof/` folder. For
the public repo, you can rerun them yourself. For the private ones, I'm happy to rerun any of
them live in a walkthrough.
