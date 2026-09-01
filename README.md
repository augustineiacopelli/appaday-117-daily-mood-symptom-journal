# 117. Daily Mood and Symptom Journal

A one-minute daily check-in for mood and up to three tracked symptoms, with a running streak and a 30-day trend chart.

**Category:** Health (H)
**Live app:** https://augustineiacopelli.github.io/appaday/appaday-117-daily-mood-symptom-journal/
**Portfolio:** https://augustineiacopelli.github.io/appaday/

## What it does

On first visit, you name one to three symptoms or feelings you want to track alongside your overall mood, and choose for each whether it is rated on a 1 to 10 scale or counted by occurrence. You can log as many entries as you like on a given day: each entry captures a mood rating and a value for every tracked symptom, timestamped to when it was logged. Mood is always required on an entry; each symptom field carries its own "Skip this symptom for this entry" toggle so a symptom can be left out of a specific entry without forcing a zero.

A day's mood and any scale-type symptoms show as the average across that day's entries. Count-type symptoms show as the sum. The check-in card surfaces today's running averages and totals as chips, lists every entry logged so far today with a delete option, and always has a "Log an entry" button available, no daily limit.

A streak badge counts consecutive days with at least one entry, walking backward from today. The trend section charts the last 30 days: mood and scale symptoms plot as daily averages on a shared 1 to 10 left axis (solid lines), count symptoms plot as daily totals on an auto-scaled right axis (dashed lines), since a count can run well past 10. Both axes carry a title naming what they measure and which line style belongs to them, and the legend swatches mirror the solid or dashed stroke so a series is traceable to its axis at a glance. Days without any entry break the line instead of interpolating across the gap.

The settings icon next to the header lets you rename, add, or remove tracked symptoms at any time. Renaming only changes the label shown going forward; every past entry stays exactly as it was logged, since entries are keyed to a stable internal id rather than the display name. Changing a symptom's type after it has history changes how past days are summarized going forward, since aggregation always applies the symptom's current type.

## Tech

Single `index.html` file. Inline CSS and JavaScript, no build step, no frameworks. Chart.js (jsdelivr CDN) draws the trend chart. Fraunces and Karla load from Google Fonts. All persistence is `localStorage`, wrapped in try and catch, split across two keys: one for the tracked symptom list, one for the array of dated entries. No AI integration.

## Design notes

The palette is a calming sage and deep teal built for a health-tracking context, paired with a Fraunces display serif against Karla for body and UI text. The mood line and each symptom line get a distinct, named color so the 30-day chart stays legible without a heavy legend.

## Build standards

Mobile-first from 375px, 44px minimum tap targets throughout, `min-height: 100dvh` on the body, no fixed pixel heights, ASCII-clean source, portfolio backlink in both header and footer.
