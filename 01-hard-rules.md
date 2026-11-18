# 01 Hard rules

Owner: Rinshin. Last verified: 2026-11-19.
Code checked on GitHub `main` that day: xoompark `b0a53e3b`, xoompark-flex `fa530c11`, xoompark-data `e53ed2b3` (`git ls-remote` matched the local `origin/main` of each).

You are changing an app repo, or you were told to read this pack. You do not have the laptop's memory, Slack, Linear, or `.env.local`. These rules still apply.

## Do not ship from this session

- **Deploys are Ops only.** Never run `firebase deploy`, `npm run deploy`, or an App Hosting rollout. xoompark `README.md:79` and `README.md:90` still say to deploy functions and Firestore rules. Do not follow them.
- After a merge, stop at: `merged, ready to deploy: PR #N`. Ops ships one deploy per app for the merged pile, after checking no build is already in flight, then curls the page.
- **Commits and pushes only when asked in this session.** Never commit a secret. Keys stay in `.env.local` or Secret Manager. Do not paste them into chat, docs, or PRs.
- **Slack: a draft only, never send.** Lowercase, short. If this agent cannot reach Slack, put the draft in the handover.
- **Linear:** update the ticket in the same turn the status changes. Close it only when the change is live. If this agent cannot reach Linear, say so.

## Money, data, outside calls

- **No paid or metered call** unless Rinshin OKs that exact spend in that turn. That includes Google Places, a browser load of a page that draws the Google map, Apollo, and treg. Check with tests and `curl` against localhost. (Rinshin, Nov 5, NO-445.)
- **Prod data.** The sourcing database id is `aggregated` (`src/lib/firebaseAdmin.ts:84` in xoompark, overridable by `FIRESTORE_AGGREGATED_DATABASE_ID`). Insert-only. Dry-run first, back up before writing, and wait for Rinshin's OK. A spot-load `--write` also needs a fresh read, `--expect=<the approved count>`, and `create()` only (xoompark-data `docs/adr/0007-spot-load.md`). Run a data `--write` only after that change is already live (xoompark-data `SYSTEM.md:339`).
- **Fresh `main` before any `--write`.** Rinshin, Nov 19: this is a hard rule. There is no code guard. Check `git rev-parse HEAD` against `origin/main` and refuse the write if the checkout is behind or dirty with the script you are about to run.
- **XoomPark OS outreach** (brokers, owners, fleets) needs Greg's OK for that batch, through Rinshin, before anything is approved or queued. "Do mails" means XP Flex only. (Rinshin, Nov 17, NO-402.)
- A bounce marks that contact only. It does not pause sending. A stop of all sending needs Rinshin to ask. (Rinshin, Nov 12, NO-381/NO-402.)
- "Send today" means new emails only. Follow-ups wait at least 4 business days. Changing a follow-up date needs Rinshin to say so. (Rinshin, Nov 5, NO-402.)

## How to work

- Say only what you checked. If someone said it, name them.
- Say what "verified" means before you start (a test, a curl, a log). A green check proves one thing: say what it did not prove.
- Nothing goes to Greg (mock, PR, link, page, video, report, or a Slack draft about a feature) until it has passed [05 Greg lens](05-greg-lens.md).
- New features, and anything that touches money, private data, prod data, or an outside call: follow [04 Build process](04-build-process.md) and wait for Rinshin's yes before feature code. Small fixes use that doc's session loop.
- Look: [06 Brand](06-brand.md). Do not copy an old branch, a `/lab` page, or a mock from before Oct 20 2026.
- On a laptop, a new worktree goes in `/Users/rinshin/Code/xoompark/worktrees/<repo>-<task>`, never inside the repo. A cloud agent branches in its clone and does not create a worktree inside the repo.
