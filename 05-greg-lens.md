# 05 Greg lens

Owner: Rinshin. Last verified: 2026-11-19.
Source of the checks: [sources/greg-lens.md](sources/greg-lens.md). It was built from PRs Greg merged and had to change (zsaadioui/xoompark, author gbessoni, Oct 20–Nov 5). The examples below are from handovers and the rejected list, not from a new read of Slack.

Nothing goes to Greg until this list is in the handover. Each check is **passed**, **fixed**, or **not relevant**. No list means it is not ready. If you are unsure, fix it. Do not ask Greg.

## Before building

Look at 2–3 products that already do it. Write what they do and what we do better. Name the reader and what they do next. Mock one screen with real data, then run the checks on the mock. When Greg sends a competitor's material, lay our screen beside their whole product at intake and say the gap. (Rinshin, Nov 18, on PR #465.)

## The 7 checks

1. **Value first, gate second.** Open on the results, not a form. Show the top 10. Three open, the rest behind sign-up. Names only for approved members. (His fixes: #291, #270, #272.)
2. **A filter for every category.** Each category is its own on/off control. No "Other" bucket. Usable on a phone. The list covers the market, not one source. (#300, #268, #255.)
3. **Say what it is.** Headings are "kind · name" ("Parking lot · …"). Plain counts, right plurals. (#296, #276.)
4. **Never leak.** No brand, source, operator, address, or raw price on a public page. `$0.00` and placeholders become "Get price". Robotaxi depots are a general area for everyone else; approved members see the address (Rinshin, Nov 10, NO-464, xoompark ADR 0003). A disclaimer where a real company is named. (#270, #238, #261, #271.)
5. **A next step for each reader.** The action sits where the reader already is. Track the click. (#290, #288, #244.)
6. **Show it's real.** A photo on the place. A date on the data ("as of"). Hide stale rows. (#267.)
7. **Phone polish.** Nothing overlaps. Sentence case. No abbreviation he would have to decode ("San Diego", not "SD"). (Greg, Nov 5. #276, #222.)

## Passed

1. **Magic Charge pages, xoompark PR #440, merged Nov 16.** Handover `TASKS/magic-charge/handover.md` (Nov 16) lists all 7: value first passed (the demo and the cost before the form), the "Other" bucket fixed into named choices, kind · name passed, no leaked sources, a next step per reader, "show it's real" not relevant on a labelled preview, polish passed at 360–1440. No Magic Charge line is in the rejected list. This session did not re-read Slack for Greg's own reply, and did not re-check that the pages are still unchanged on `main`.
2. **Flex plate-check video "Whose car is that?"** Rinshin, Nov 11, recorded in `marketing/content/linkedin-flex-ev-bays/script.md:7-9`: it was posted, and Greg liked it. The shape he liked is one manager, one moment, whole screens, before then after. There is no written 7-check list for that video in the files read here.
3. **XP Flex sibling brand, xoompark-flex PR #47, merged 2026-11-09** (commit `6cd7f48`). This is the look that replaced the rejected Flex pages below. On 2026-11-19 the live home HTML contains `flex-wordmark` and "XoomPark Flex". No Greg quote accepting PR #47 was found this session.

## Failed

1. **NO-438 Flex landing, Nov 5.** A handover marked the lens passed, including a satellite photo as proof. Rinshin then rejected, in order: pages that ask you to read instead of showing; iso drawings as the main visual ("too much cartoony"); the pill buttons, mixed chips, dashed strip and small grey cards; an Overpass "sign" rebrand; coloured top edges on tiles. **Fix that shipped:** PR #47. One system with xoompark.co, Flex green as the only accent, white page, real screens, no coloured edge. Do not swap a font onto an old layout.
2. **NO-489 fleet page, Nov 12.** A bare map was "like Zillow". A tiny map with option cards hid the filters. Later rejects: an "approximate area" circle on every card, satellite photos on the cards, a "sourced for …" badge repeated on every card, and a "not on the map yet" placeholder section. **Fix:** build a fleet page on `/search`'s frame (map, panel, chips, filters, numbered pins, cards, details), scoped to that fleet's sourced sites, filters visible. "Not Zillow" means the content (only what we sourced, one choice each), not a stripped page. Real address and a pin on the map. No imagery on the cards. No repeated badge. No fleet or city name hard-coded. If an address is unclear, find it and place the site. Use the numbers Greg sent. The dollar figures from that page are not copied here.
3. **NO-464 depot address list, Nov 9, and NO-491 tracker, Nov 12.** The list had two filter rows, "kind · operator" headings and two-line cells. **Fix:** one search box, one row of chips, one value per column, a Download CSV button. The tracker was built on the `/search` frame and felt like an overlay of it. **Fix:** `/search` is for picking a site. A tracker is for reading and comparing. Study the reference he shared, mock first, then build.

When Greg fixes something himself, add the pattern here with the PR number the same day.
