# 06 Brand

Owner: Rinshin. Last verified: 2026-11-19 against GitHub `main` (xoompark `b0a53e3b`, xoompark-flex `fa530c11`).
Rinshin, Nov 19: when the short token list and xoompark `main` disagree on a number, copy the CSS below. Do not blend a third value. On the laptop the same rules also live in `/Users/rinshin/Code/xoompark/CLAUDE.md`. This file is the copy a cloud agent has.

Live check the same day: xoompark.co HTML contains `xp-logo` / `XOOMPARK`. flex.xoompark.co HTML contains `flex-wordmark` / `XoomPark Flex`. First-screen shots, no map request in the HTML: `screenshots/`.

## Use

Sentence case. The name is XoomPark. No "XP", no icon logo. Instrument Sans for text (weight 400, tight tracking on display; 500 on labels and buttons). Geist Mono for the wordmark and small labels. Geist for numbers.

xoompark loads Instrument Sans in `src/components/site/font.ts:4` and applies it on `src/app/layout.tsx:53`. Flex loads it in `src/app/layout.tsx:9`.

## Tokens that match the written rules

Paper `#f6f4ef` is xoompark's page background (`globals.css:4`, `site.module.css:8`). Cards are white. Flex's page background is white `#ffffff` (`globals.css:12` and again `:1044`). Ink `#1b1a18`, secondary `#57534d`, tertiary `#6b665f`, placeholder `#858079` (`globals.css:19-22`). Stone `#ece8e0`. Lines `#e9e4da` and `#d9d3c7` (`globals.css:23-24`, `site.module.css:12-14`). Blue `#2f5bff`, tint `#dfe6ff` (`globals.css:27-28`). Blue on charcoal `#7d98ff` (`site.module.css:16`). Red `#e5484d` for problems (`globals.css:33`, `--now`). Flex's only accent is `#3b7a57` (`globals.css:8` and `:1048`).

Do not use `--accent` in xoompark `globals.css` as the blue. Line 4 sets it to `#afcbff`. Line 105 sets it to `#f3f1ec`. The blue is `--brand`, and `site.module.css:15`.

## Decided 2026-11-19

Copy xoompark `main` for these, even though the short list differs:

- Card shadow is `--shadow-card` (`globals.css:44`), a 0.07 ring plus two short drops. The written `.06` ring is the older line.
- Marketing placeholders use `--ink-3` (`site.module.css:38`). `--ink-4` (`#858079`) stays for disabled text.
- Big headline tracking is `-0.045em` (`.display`, `site.module.css:64`). Section titles stay `-0.035em` (`.xp-display`, `globals.css:176`).
- Secondary buttons are both cream (`.light`) and white (`.ghost`, `.xp-button-ghost`).
- Marketing `.button` is 40px (`site.module.css:69`). The apply submit is 48px (`site.module.css:205`). Copy the control you are matching.

Flex buttons should use the same keys as xoompark (Rinshin, Nov 19). Flex `.button` is still flat (`box-shadow: none`, `globals.css:1083-1091`). That is the gap. New Flex controls use the key CSS below. Do not restyle Flex in a docs change.

Do not copy leftovers that the written rules ban, even where `main` still has them: navy `#14213d` and amber `#c8791a` in Flex `public/marketing/assets/site.css`, and `border-radius: 999px` (file input at `globals.css:1025`, and again from line 116). Flex cards use `--ring` (`globals.css:1051`), a stone line, not the xoompark key shadow.

Shots taken 2026-11-19, first screen, no `maps.googleapis` request: `screenshots/xoompark-home.png`, `screenshots/flex-home.png`, `screenshots/data-auth.png`. The xoompark home still opens on an iso drawing. The Flex home uses an aerial lot photo. Do not add a new iso, or a satellite image on a card, because these shots exist. The nav button on xoompark.co says "XP Flex". New work still says XoomPark Flex, not "XP". The data sign-in tab title is still "Pit Stops for Autonomous Vehicles". The page itself says "Supply workspace".

## Banned

Do not bring back: Uncut, Comfortaa, Satoshi, Montserrat, Inter as the brand face, or the system font as the chosen face. No pills as the button system, no dashed asphalt strip, no iso drawing as the main visual, no coloured top edge on a card, no navy, teal, purple, or a green brand colour on xoompark.co. Flex green is the one exception. No gradient. No big soft blur. The Oct 2 playbook's "green = live, amber = to-do" is history; that file says so.

## Copy from xoompark `main`

Key shadows and the wordmark, `src/app/globals.css`. Paste tokens first; the site module references them.

```css
/* globals.css:19-33, :44, :53-62, :170-171 */
--ink: #1b1a18;
--ink-2: #57534d;
--ink-3: #6b665f;
--ink-4: #858079;
--line: #e9e4da;
--line-strong: #d9d3c7;
--brand: #2f5bff;
--brand-tint: #dfe6ff;
--now: #e5484d;
--shadow-card: 0 0 0 1px rgb(27 26 24 / 0.07), 0 1px 2px 0 rgb(27 26 24 / 0.12), 0 3px 4px -2px rgb(27 26 24 / 0.08);
--key: 0 0 0 1px rgb(27 26 24 / .13), inset 0 -2px 0 0 rgb(27 26 24 / .07), 0 1px 0 0 rgb(27 26 24 / .1), 0 2px 3px -1px rgb(27 26 24 / .16);
--key-hover: 0 0 0 1px rgb(27 26 24 / .18), inset 0 -2px 0 0 rgb(27 26 24 / .07), 0 2px 0 0 rgb(27 26 24 / .1), 0 4px 6px -2px rgb(27 26 24 / .18);
--key-down: 0 0 0 1px rgb(27 26 24 / .18), inset 0 2px 3px 0 rgb(27 26 24 / .16);
--key-down-bg: #f1eee8;
--key-ink: inset 0 -2px 0 0 rgb(0 0 0 / .5), 0 1px 0 0 rgb(27 26 24 / .35), 0 2px 4px -1px rgb(27 26 24 / .35);
--key-ink-hover: inset 0 -2px 0 0 rgb(0 0 0 / .5), 0 2px 0 0 rgb(27 26 24 / .35), 0 4px 6px -2px rgb(27 26 24 / .38);
--key-ink-down: inset 0 2px 4px 0 rgb(0 0 0 / .6);
.xp-logo { font-family: var(--font-geist-mono), monospace; font-size: 1rem; font-weight: 700; letter-spacing: .16em; line-height: 1; }
.xp-logo span { font-size: .5em; vertical-align: top; }
```

Buttons, `site.module.css:69-81`. `.primary` is ink, `.light` is cream, `.ghost` is white. Hover lifts 1px, press sinks 1px. Keys in `globals.css:331-339` (`.xp-key`, `.xp-key-ink`) do the same, and a pressed toggle stays down. Clickable cards: `.xp-tap` lifts 2px (`globals.css:322-324`), `.xp-raised` (`globals.css:326-328`).

## Copy from Flex `main`

```css
/* globals.css:1040-1051, :1065-1074, :1083-1093 */
--ink: #1b1a18;
--ink-2: #57534d;
--ink-3: #6b665f;
--ink-4: #858079;
--paper: #ffffff;
--stone: #ece8e0;
--line: #e9e4da;
--line-2: #d9d3c7;
--accent: #3b7a57;
--red: #e5484d;
--ring: 0 0 0 1px var(--line);
.flex-wordmark { font-family: var(--font-geist-mono), ui-monospace, monospace; font-weight: 700; font-size: 0.875rem; letter-spacing: 0.16em; text-transform: uppercase; color: var(--ink); }
.flex-wordmark sup { font-size: 0.5em; vertical-align: top; }
.button { min-height: 40px; padding: 8px 16px; border-radius: 6px; border: 0; background: var(--ink); color: var(--paper); font-size: 15px; font-weight: 500; box-shadow: none; }
.button.secondary { background: #fff; color: var(--ink); box-shadow: inset 0 0 0 1px var(--line-2); }
```

The wordmark text is `XoomPark Flex` with a top-aligned ®. xoompark's is `XOOMPARK` with a top-aligned ®, via `.xp-logo`.
