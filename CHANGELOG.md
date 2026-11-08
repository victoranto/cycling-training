# Changelog

## 0.1.3 - 2026-11-06

- Time off the bike: optional profile status; `/plan-week` and `/today` plan with the sports available, progress new sports conservatively, and plan the return to the bike.
- FTP status (tested or provisional) and next planned test; missed tests are rescheduled, never during time off or on the first rides back.
- Planned workouts in % FTP only when the platform's FTP matches the profile; otherwise absolute watts.
- Weight readings: placeholder values are ignored, reported weigh-ins come first, and W/kg uses a recent average.
- When the profile exists in more than one place and the copies disagree, the coach asks instead of picking one.

## 0.1.2 - 2026-10-27

- Respects an existing nutrition or weight-loss setup (Project, memory or a dietitian) instead of declining; training and fueling advice stays compatible with it.
- Optional yearly distance goal: asked in `/setup`, progress shown in `/review` and `/analyze`, never at the cost of recovery.

## 0.1.1 - 2026-10-27

- Added a privacy policy (`PRIVACY.md`), linked from the READMEs and `plugin.json`.

## 0.1.0 - 2026-10-27

First public version.

- Commands: `/setup`, `/plan-week`, `/today`, `/analyze`, `/fueling`, `/review`.
- Athlete profile with language, units, FTP, A/B/C races, availability, equipment, other sports and preferences.
- Strava and Intervals.icu (via Stas) data sources; calendar writes previewed and confirmed.
- Shared coaching method and 14 cited references.
