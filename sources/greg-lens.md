# Greg lens (LAW): nothing goes to Greg without passing this

Built from the 30+ PRs Greg merged himself between Oct 20 and Nov 5 (zsaadioui/xoompark, author gbessoni). Each fix below is something we shipped and Greg had to change. Catch it first.

## 0. Research before building
- Find the 2–3 products that already do this (Greg names them: EVpin, Pillar, Vaylo, PlugShare, Retention/RB2B, robotaxitracker, Titleman, dcfctracker). Screenshot them. Write down what they do that we don't, and what we'll do better.
- Ask who reads it (fleet, owner, neighbor, industry, Greg on a sales call) and what they do next.
- Mock first, one screen, with real data (see greg-mock-first). Run this list on the mock.

## 1. Value first, gate second
- Open on the results, not a form or an intro (#291).
- Show the top 10, not everything (#291).
- 3 open, the rest blurred behind "Sign up free" (#270, #291). Names or details only for approved members (#272).

## 2. Every list has a filter for every category
- Each category is its own on/off toggle: networks (#300), operators by name (#268).
- No "Other" bucket. Greg: "Other? Einride is an operator".
- Filters scroll and stay usable on a phone (#255).
- The list covers the whole market, not just one source. Count the categories against a competitor before shipping. Greg on /chargers with 7 networks: "Very few networks" (NO-437).

## 3. Say what it is
- Headings name the kind of place first: "Car wash · SOBE Finest", "Parking lot · Jamestown Doral" (#296).
- Plain counts with correct plurals: "1 acre", "1 site" (#276).

## 4. Never leak
- No brands or source names on public pages: no SpotHero/LoopNet/Crexi, no operator names, no "via X" credit (#270, #238, #261).
- No raw data: quote JSON, $0.00, placeholder prices become "Get price" (#270, NO-413).
- Robotaxi depots by general area only: no address, exact point or permit record (#271). Exception: approved members see each depot's address and exact spot (Rinshin, Nov 10, NO-464, xoompark ADR 0003). Everyone else still gets the general area.
- Disclaimers and an independence notice where it names real companies (#238, #261).

## 5. A next step for each reader
- Each reader type gets its own card or CTA: neighbors → curb report, owners → list property, industry → Depot Daily (#290).
- Content split by role (#288 guides by role).
- Sign-up sits where the reader already is, not on another page (#244, #273).
- Track each CTA by placement (GA4 cta_click / form_submit) (#290).

## 6. Show it's real
- Street View or a photo on site details (#267).
- Dates on data ("as of", "last confirmed") and hide stale rows (charger map answer 5).

## 7. Polish he'll notice
- Nothing overlaps on a phone (#276 badge overlap).
- Copy is for autonomous fleets, short and sentence case (#222, #230, #237).
- No abbreviations in anything Greg reads: pages, reports, Slack. Write "San Diego", not "SD". Greg, Nov 5: "stop using abbreviations i dont know what SD listings are?"

## How to use (required)
Before sending Greg anything, go through 0–7. In the handover, list each one as passed / fixed / not relevant. No list means it isn't ready. If you're unsure, fix it, don't ask Greg.

When Greg fixes something himself, add the pattern here with the PR number the same day.
