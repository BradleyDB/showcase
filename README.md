# Case studies: governed AI tooling for a SaaS admin platform

**gs-superadmin lets admins work in a live SaaS tenant through the vendor's CLI, with an approval prompt on every change. These pages show the system that builds and maintains it: how each vendor release is audited, how AI sessions build and check each other's changes, and where a person decides.**

Most of this work lives in private repositories, so these pages show it instead: the
problem, what I built, the principles behind it, and numbers that each come with the
command that reproduces them. No code is reproduced here, and no employer, customer or
tenant is named.

> [!TIP]
> **Start with the system page.** It shows how four repos work together, and it's the one
> to read if you read one.

## The system

### [The gs-admin toolchain →](gs-admin-toolchain/README.md)

Keeping an AI admin co-pilot correct as its vendor's CLI changes underneath it. A public
plugin lets an agent administer a live tenant behind approval prompts. A release watch
audits every new vendor version, a builder/tester loop builds each change, and a small CLI
keeps the loop's books. The page traces one vendor release through all four repos in 12
steps, with a person deciding at three of them.

## Deep dives

| Page | In one line | Its steps in the system |
|---|---|---|
| [gs-fortress →](gs-fortress/README.md) | Audits every vendor CLI release against a 13-item impact checklist and keeps the adopt/defer ledger | 2–4 and 12, plus the ledger behind the human decision at 5 |
| [dev-utils →](dev-utils/README.md) | Keeps the books for AI builder/tester sessions so the models spend their effort on judgment | 8 and 11 |
| [superfriends →](superfriends/README.md) | The process skills: how AI sessions plan a build, hand it off, verify each other's work and release it | 7 and 9, plus the kickoff format at 4 and 6 |

The fourth repo, the plugin itself, is public:
[gs-admin-cli-docs](https://github.com/BradleyDB/gs-admin-cli-docs). That's the place to
read the code.

## Checking the numbers

Numbers last updated 2026-10-06. Each page says when its numbers were measured; counts such
as commits and pull requests keep growing after that.

Every figure sits beside the command that produced it, pinned to the exact commit it
measured, in each page's `proof/` folder. [FACTS.md](FACTS.md) lists the key claims in one
place, with their evidence. For the public repo you can rerun the commands yourself; for
the private ones, I'm happy to rerun any of them live in a walkthrough.

---

© 2026 Bradley Bazhaw. All rights reserved; see [LICENSE](LICENSE). You are welcome to read and link to these pages.
