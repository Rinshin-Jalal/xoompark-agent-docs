# 04 Build process

Owner: Rinshin. Last verified: 2026-11-19.
Process source: [sources/system-design.md](sources/system-design.md). Code cites are GitHub `main`: xoompark `b0a53e3b`, xoompark-flex `fa530c11`, xoompark-data `e53ed2b3`.

The law: you do not know the design until you can make a test fail for it.

## Which path

- **New feature, new service, or anything that touches money, private data, prod data, or an outside call.** Phase 1 only. Stop. Wait for Rinshin's yes. Then red tests, then feature code.
- **Small fix or copy change.** Session loop below. No Phase 1 intake.
- A tracker that only checks tickets does not write code. It still checks that a PR shows red and green output.

## Phase 1 (then stop)

Write the intake in `SYSTEM.md`. Label every number MEASURED, TARGET, or GUESS. Cover scope, scale, the RPS and storage math, concurrency as a floor (not a pool size), and the component map. For each concept (performance, latency, consistency, recovery, edge, application, database, cache, jobs, calls, security): decide, write a rule, or write `skip:` and the reason. Show the intake. Change nothing until Rinshin says yes.

Reasons go in `docs/adr/` afterwards, not in the intake.

## After yes

1. Fill `SYSTEM.md`: intake, targets, rules. Every rule names its red test, or is marked UNTESTED with a reason.
2. Write `MODULES.md` for the two riskiest modules first. A contract says what it owns, its interface, consistency, failure behavior, and what it must not do. Do not change a contract without an ADR.
3. Red tests live in `tests/red/`. Each names one fault. Plant the fault with a break patch. The test must FAIL with the break and PASS without it. Paste the RED output before feature code. A test that never failed has not shown it can see the fault.
4. Write code until GREEN. Paste GREEN. Never weaken or delete a red test to make a change pass.
5. Open the PR with both outputs. Mark what you could not test UNTESTED. Say which decisions changed. A green run proves the faults you planted, not the signed-in product, not prod, and not a third-party response you faked.

Do not raise a GUESS to MEASURED without a run log. Staging numbers are MEASURED for staging only.

## Where the tests are (checked)

- **xoompark:** `npm test` runs `tests/red/*.test.ts` and `tests/red/*.test.tsx` (`package.json:10`). 158 files sit under `tests/red/`, including break patches. That count is files, not passing tests. This session did not run the suite.
- **xoompark-data:** 252 files under `tests/red/`. `package.json` scripts (lines 6-13) have no `test` script. `SYSTEM.md` names the red test on the rule (`accept_applies_once` at `SYSTEM.md:16`). How to invoke the folder was not found. UNVERIFIED.
- **xoompark-flex:** `tests/red/` has three Tesla files (`tesla-drivers.test.ts`, `tesla-oauth.test.ts`, `tesla-read.test.ts`). The rest are `npm run test:*` (Firebase emulator scripts) and `npm run check:*` in `package.json`. There is no single `npm test`.

## Session loop (small changes)

1. Read `SYSTEM.md` and the `MODULES.md` entry for each module you touch. Flex has no `SYSTEM.md` or `MODULES.md` on `main`. Say so, and don't invent one for a copy fix.
2. List the rules this change affects. Name each rule's red test. If none exists, write one.
3. Inject the fault. Paste RED. Then code. Paste GREEN.
4. Run the suite you can run. If a decision changed, write an ADR and update `SYSTEM.md`.
5. If you cannot test a rule, mark it UNTESTED in the PR and say why.

## App Hosting build

xoompark `SYSTEM.md:2325-2328`: the zip follows `.gitignore` (tracked status does not count), and `next build` type-checks every `.ts` file the tsconfig reaches, tests included. A file that reaches the build must not import an ignored path (`functions/` is ignored in `firebase.json`). The red test is `nothing_in_the_build_imports_an_ignored_file`.

## PR body

Include the red output, the green output, UNTESTED rules, and what the green run did not cover. For anything going to Greg, also include the [05 Greg lens](05-greg-lens.md) list.
