---
name: plan-week
description: Plans the athlete's training week (or next block) around their real availability, fatigue, recent training and A/B/C races, with the bike as the priority and gym, swimming, running or hiking fitted in. Produces a day-by-day table with watts, HR and RPE, the expected load versus last week, deload and taper decisions, and can write the week to Intervals.icu after confirmation. Use for /plan-week and whenever the athlete asks what to do this week or next, to plan, reschedule or rebuild their week, "planifica la semana", "qué hago esta semana", or shares their availability for the coming days.
---

# Plan the week

Read `references/coaching-principles.md`, `references/athlete-profile.md`, `references/data-sources.md`, `references/zones-and-sessions.md` and, for long rides, `references/fueling-guidelines.md`. Use `references/evidence.md` when you need to justify a choice.

## 1. Inputs

- **Profile.** Load it. If missing, offer `/setup`; if the athlete wants a plan anyway, ask for the minimum (FTP, availability, main goal) in one message.
- **Availability this week.** If the athlete did not give it, ask in one message: which days, how long, indoor or outdoor, any day off. Do not invent a schedule.
- **History.** At least the last 2-4 weeks (6-8 for a new block): load and its trend, what was planned vs done, last hard session and how it went, long-ride length, other activities, sleep/HRV/resting HR if available.
- **Existing calendar.** Read the planned events for the week. Sessions the athlete or Intervals.icu changed manually are respected unless the athlete says otherwise.

## 2. Decide

0. **Off the bike?** If the profile has a current off-bike period that covers the week, plan it with the sports available and the rules in `zones-and-sessions.md` (Off the bike and coming back). If the period ends this week, plan the return rides.
1. **Where the week sits:** base, build, specific, deload, taper or race week, relative to the A race and any B/C races in or near the week. For a race-containing week, explicitly choose no taper / light taper / full taper from the race priority (see `zones-and-sessions.md`).
2. **Deload check:** 3-4 loading weeks done, or persistent fatigue signals → deload, and say why.
3. **Key sessions:** pick 1-2 quality bike sessions (and the long ride). Everything else is Z2, strength/mobility, other activities or rest.
4. **Progression:** load roughly +5-10 % on a loading week, and never raise volume and intensity together without saying why.
5. **Other activities:** place them with the rules in `zones-and-sessions.md` (no heavy legs the day before the key session or long ride; easy swim as recovery). If the athlete wants them programmed, give their sessions too; otherwise just place them.
6. **Fit reality:** if not everything fits, cut Z2 before the key session, and the key session before rest.
7. **FTP:** if a test is due or FTP is provisional (`zones-and-sessions.md`), include it on a fresh day, never during time off the bike or on the first rides back. If a planned test was missed, move it to the next fresh day.

## 3. Output

Reply in the profile's language and units.

1. One line on what kind of week this is and why (for example "Build week 3 of 3; deload next week").
2. A table: day · session · duration · objective · intensity (watts with % FTP, HR, RPE; exact watts for ERG trainer sessions, ranges outdoors, HR/RPE on bikes without power).
3. Detail for each key session: warm-up, main set, recoveries, cool-down, and fueling if > 90 min.
4. One line of expected load vs last week (and why it moves).
5. Warnings: deload due, FTP test due, taper starting, conflicts with other activities.

Keep it to what the athlete needs this week. Do not include future weeks unless asked.

## 4. Writing to Intervals.icu (optional)

If Stas is connected and the profile says to write sessions (or the athlete asks):
1. Preview the whole week with `dry_run: true` and show it.
2. Write only after an explicit yes. Structured sessions need a real workout structure (steps with durations and targets), not prose.
3. Read the calendar back and confirm what was written. If something failed, say exactly what.
Never overwrite sessions changed manually without asking.
