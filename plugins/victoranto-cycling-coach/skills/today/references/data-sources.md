# Data sources

Use whatever the athlete has connected. If a connector's tools are deferred, load them (for example with a tool search) before deciding they are unavailable. Never invent workouts, metrics, dates or goals.

## Strava (read-only)

Completed activities, streams (power, HR, cadence, speed, altitude), athlete zones, gear and profile. Use it to find the sessions of a date, to compute volume and elevation, and for detail on a single ride.

## Stas → Intervals.icu (read and write)

Stas is an endurance-coaching connector backed by the athlete's Intervals.icu account.

- **Read:** athlete summary (FTP, weight, fitness/fatigue), training history, single-workout detail, wellness (sleep, resting HR, HRV, subjective scores) and the planned calendar.
- **Write:** planned workouts go to the Intervals.icu calendar through Stas (`create_plan_event`). From Intervals.icu they can sync to the athlete's head unit (Garmin, Wahoo) and to apps such as MyWhoosh or Zwift, depending on how the athlete has linked their accounts.
- **Always preview first.** Use `dry_run: true`, show the athlete what will be written, and only write with `dry_run: false` after they say yes. Structured interval sessions need a proper workout structure, not prose only. After writing, read the calendar back to check it matches.
- **Watts in planned workouts.** A workout written in % FTP uses the FTP stored in Intervals.icu and the trainer app. If that FTP differs from the profile's current FTP (for example right after a test), write absolute watts, or have the platform FTP updated first (by the athlete, or through the connector if it allows, after they confirm).
- **Respect manual changes.** If a planned event was last changed by the athlete or in Intervals.icu, do not overwrite it silently; ask first.
- Follow the connector's own tool descriptions for field formats; they take priority over anything here.

At the time of writing there is no standalone Intervals.icu connector in Claude's directory, so Stas is how this plugin writes to Intervals.icu. If the athlete has a different way to reach Intervals.icu, use it with the same preview-then-confirm rule.

## Weight readings

Weight is used for W/kg, so a bad value gives a bad W/kg.
- Some readings are not real weigh-ins: the same round number repeated for weeks (often a platform default), a value that never changes, or a big jump that a second source does not show. Treat them as missing, and tell the athlete once.
- Prefer, in order: weigh-ins the athlete reports, then a smart scale or wearable sync, then the weight in a platform's profile.
- Use a recent average (about 7 days) rather than a single reading, which moves with hydration and time of day.
- If no connected source can store weight, keep the weigh-ins the athlete reports with the profile (memory or Project) and say that is where they live.

## Garmin

There is no Garmin connector in Claude's directory at the time of writing. Garmin data reaches the plugin through Strava or Intervals.icu when the athlete has those syncs enabled. Mention this in `/setup` if the athlete only uses Garmin Connect.

## Nothing connected

Everything still works with data the athlete pastes or describes: duration, distance, elevation, average/normalized power, HR, RPE, intervals, and screenshots. Say which metrics are missing and how that limits the analysis.

## When sources disagree

Strava and Intervals.icu can disagree (different FTP, duplicated or missing activities, different load models). Confirm they describe the same sessions, never count the same ride twice, and tell the athlete about any mismatch that matters.
