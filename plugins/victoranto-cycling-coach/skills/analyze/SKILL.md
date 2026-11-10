---
name: analyze
description: Analyzes a completed ride or training day (all sports, bike first) using power, heart rate, RPE, volume, elevation, fueling and accumulated load, compares it with the plan, and decides the next session. Asks for RPE and what was eaten if missing. Offers a one-screen summary mode. Use for /analyze and whenever the athlete just finished training, shares a ride from Strava, Garmin or Intervals.icu, pastes ride data or a screenshot, or says "analiza el entreno", "how did my ride go", "analyze yesterday".
---

# Analyze a session

> Paths in this skill are relative to this skill's own folder
> (the "Base directory for this skill" shown when it loads),
> e.g. `<base>/references/coaching-principles.md`.
> Never resolve them from the plugin root. If a file is missing,
> look inside this skill's folder before continuing; do not skip it.

Read `references/coaching-principles.md`, `references/athlete-profile.md`, `references/data-sources.md`, `references/zones-and-sessions.md` and `references/fueling-guidelines.md` (in this skill's folder).

## Parameters

The athlete can give them in plain language when invoking (for example "/analyze yesterday, RPE 7, 2 gels and a bar"):

| Parameter | Example | If not given |
|---|---|---|
| Date | yesterday, 12 March | Today |
| Sport | bike only | All sessions of that day |
| RPE | RPE 8 | Ask |
| Food and drink during the session | 3 gels, 2 bottles of drink mix | Ask |
| Format | summary, short, brief | Full report |

**Ask first.** If RPE or fueling is missing, ask for both in one short message before analyzing, and wait. With several sessions, ask RPE and intake for each (or one overall if the athlete prefers). If they say they don't remember or took nothing, record that ("no intake") instead of insisting.

## Getting the data

Find every session of the chosen date in the connected sources (Strava, Stas/Intervals.icu): summary, power/HR detail and streams when needed, planned events for plan-vs-done, wellness (sleep, resting HR, HRV), FTP and weight from the profile or the summary. Check both sources describe the same sessions and never double count. If nothing is connected, work from what the athlete pastes and say what is missing.

Use compact tables (Metric | Value | Reading), one per block; prose only for interpretation and the verdict.

## Full report

**0. Day summary** — one row per session: sport, time, duration, load (TSS or equivalent), RPE, planned or not. Total load of the day.

**1. Main session** (usually the bike):
- type, duration, distance, elevation;
- average and normalized power, variability index if irregular;
- IF (NP/FTP) and TSS with the current FTP;
- time in power zones, not just the average;
- average and max HR, HR zone distribution;
- for long rides: power and HR in the last hour vs the first hours (durability).
If the bike had no power meter, use HR, RPE, speed and elevation.

**2. Other sessions** — short table each (gym: main exercises, sets, reps, loads, effort; run: distance, pace, HR; swim/hike: duration, intensity). Say how each affects the next bike session.

**3. Metric coherence:**
- power:HR decoupling on long Z2, and whether HR was high or low for the watts;
- RPE vs what the numbers say (suffering more than the watts justify suggests fatigue or under-recovery);
- plan vs done table.

**4. Load and recovery:** acute vs chronic load and trend (orientation, not alarm); weekly volume and elevation vs previous weeks (volume and intensity not both rising); sleep, resting HR, HRV if available; consecutive loading days and when a deload is due.

**4b. Yearly distance goal** (only if the profile has one): one line with distance so far this year, % done, km per week needed for the rest of the year vs the recent average, and ahead / on track / behind.

**5. Performance** (when data allows): best 5, 20, 60-min efforts vs FTP; W/kg; trends. If efforts consistently beat or miss FTP, flag a re-evaluation.

**6. Fueling:** what was eaten and drunk; estimated carbohydrate g/h and fluids (state it is an estimate); enough, short or excessive for that duration and intensity; whether it may explain late power fade, HR drift or high RPE.

**7. Verdict and next session:**
- 2-3 lines: what went well, what did not, signs of fatigue or progress.
- The next session, concrete: duration, objective, zones/watts, intervals and recoveries, adjusted to state and availability. If a planned session exists, say whether it stands or should change, following the same rule as `/today` (change only for a real reason).
- Explicit warning if the plan should change, the FTP should be re-tested, or a deload is due.

## Summary mode

When the athlete asks for "summary", "short" or "brief", do all the same work but show only (about 20-25 lines):
1. Day table (sessions, duration, load, RPE, planned) with the main bike session's distance, elevation, avg/NP, IF and avg HR.
2. Load and recovery in one line.
3. Fueling in one line (intake, estimated g/h, enough or not).
   If the profile has a yearly distance goal, add one line with progress (done, %, ahead / on track / behind).
4. Verdict in two lines.
5. Next session in one line.
6. `Warning:` line only if there is one (FTP re-test, deload, high decoupling, RPE far above the watts, sources disagree).
End by offering the full report or any section in detail.

## Rules

- Never invent a metric. Analyze with what exists and say what is missing.
- Read-only by default: do not change the calendar unless the athlete asks, and then preview first.
