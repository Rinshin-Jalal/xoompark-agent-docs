# 03 Environments and deploys

Owner: Rinshin. Last verified: 2026-11-19, against GitHub `main` (xoompark `b0a53e3b`, xoompark-flex `fa530c11`, xoompark-data `e53ed2b3`).

## Three apps

| App | GitHub | Domain | Firebase project | App Hosting backend |
|---|---|---|---|---|
| XoomPark OS | zsaadioui/xoompark | xoompark.co | `xoompark-ec53e` (`.firebaserc:3`, `apphosting.yaml:16`) | `xoompark` (`firebase.json:43`). `minInstances: 1`, 1024 MiB (`apphosting.yaml:4-5`) |
| Staging for that repo | same | not the public site | `xoompark-b7c5a` | `xoompark-nextjs` (`firebase.json:54`). Overrides in `apphosting.xoompark-nextjs.yaml:1-2` and project id at line 16. `minInstances: 0` |
| XP Flex | zsaadioui/xoompark-flex | flex.xoompark.co | `xoompark-flex` (`firebase/.firebaserc:3`, `apphosting.yaml:23`) | `xp-flex-prod` (`firebase.json:3`). `minInstances: 1` (`apphosting.yaml:9`). Hosted URL also in `apphosting.yaml:45` |
| Data | Rinshin-Jalal/xoompark-data | data.xoompark.co | `xoompark-ec53e` (`.firebaserc:3`, `apphosting.yaml:17`) | `xoompark-data` (`firebase.json:11`). `minInstances: 0`, 1024 MiB (`apphosting.yaml:4-6`) |

xoompark and xoompark-data share prod project `xoompark-ec53e`. Flex is its own project. The sourcing database id on that prod project is `aggregated` (xoompark `src/lib/firebaseAdmin.ts:84`). Bookings and users stay on the default database (comment at `firebaseAdmin.ts:80`). This session did not open Firestore, so the backup and PITR state is not re-checked here.

`firebase.json` in xoompark and xoompark-data lists `functions` under `apphosting.ignore`. App Hosting zips by gitignore rules, and `next build` type-checks tests too. A file in that zip must not import an ignored path (xoompark `SYSTEM.md:2325-2328`).

## Local env on the laptop (project id only)

Checked 2026-11-19. Values of `NEXT_PUBLIC_FIREBASE_PROJECT_ID` only:

- xoompark `.env.local` → `xoompark-b7c5a` (staging)
- xp-flex `.env.local` → `xoompark-flex`
- xoompark-data `.env.local` → `xoompark-b7c5a` (staging). Rinshin, Nov 19: it had been `xoompark-ec53e`. The eight public Firebase client fields were switched to the staging web app in `apphosting.xoompark-nextjs.yaml`. No admin service-account variable is set in that file, so Admin uses this project id (`src/lib/firebaseAdmin.ts:39-44` on data `main`).

A cloud agent has no `.env.local`. Do not create one that points at `xoompark-ec53e`. `scripts/fb-fix/resolve-project.ts:9-10` treats `xoompark-ec53e` as prod and `xoompark-b7c5a` as dev.

`apphosting.yaml` also holds public client config and secret *names*. Do not copy key values into docs or chat.

## Who deploys

Only the Ops session deploys xoompark.co, data.xoompark.co, flex.xoompark.co, Firebase rules, and functions. This agent does not. See [01 Hard rules](01-hard-rules.md).

Ops waits until merged PRs have piled up, checks for a build already in flight, ships one deploy per app, curls the page, and updates Linear. There is no auto-deploy described in the three `main` trees this session. An older note (NO-478, Nov 10) said the `xoompark` backend was not connected to GitHub. That was not re-checked in the Firebase console on Nov 19.

## Build-order gotcha

The data enrich job's Cloud Scheduler deadline was 120s (MEASURED, xoompark-data `SYSTEM.md:236` and `:354`). A longer run is about 125s, and the scheduler cancels the request at its deadline. Ops raises that deadline to 300s **before** the deploy that lengthens the run (`SYSTEM.md:236`, `:350`). A secret named in `apphosting.yaml` must already exist and be granted to the backend, or the build fails (xoompark `apphosting.yaml:195` for one example). This session did not read the live scheduler job.

## How to tell what is live

Curl the page. On 2026-11-19:

- `curl -sI https://xoompark.co/` → HTTP/2 200, `server: envoy`, `x-fah-adapter: nextjs-14.0.21`. The HTML contains `xp-logo` and `XOOMPARK`.
- `curl -sI https://flex.xoompark.co/` → HTTP/2 200, same adapter. The HTML contains `flex-wordmark` and `XoomPark Flex`.
- `curl -sI https://data.xoompark.co/` → HTTP/2 307 to `/auth`, `cache-control: private, no-store`.

Those headers do not include a git commit. A 200 does not prove live equals `main`. The laptop deploy folders `workspace/xp-main-deploy` and `workspace/xoompark-data-deploy` were at the same SHAs as `origin/main` on Nov 18 23:19 IST. That is the folder, not the rollout.

Do not load a page that draws the Google map unless Rinshin OKs that call. Prefer `curl -sI`, or a localhost server.
