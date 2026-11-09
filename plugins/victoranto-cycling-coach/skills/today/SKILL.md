---
name: today
description: Shows today's planned training session from the athlete's calendar (Intervals.icu via Stas, or the week planned in Claude) exactly as planned, with execution notes and what to eat and drink, and only proposes a change when there is a real reason - the athlete is tired, ill, short on time, or recovery data is off. Use for /today and when the athlete asks "what's my session today", "qué toca hoy", "qué entreno hoy", "should I still do my intervals", or says they are tired before training.
---

# Today's session

Read `references/coaching-principles.md`, `references/athlete-profile.md`, `references/data-sources.md`, `references/zones-and-sessions.md` and `references/fueling-guidelines.md`.

The point of this command is to **show the plan, not to invent a new session every day.** A plan is only useful if it is stable.

## 1. Find today's plan

1. Check that nothing has been completed today already (completed activities for today's date). If a session is already done, say so and offer `/analyze` instead.
2. Read today's planned events from the calendar (Stas / Intervals.icu).
3. If there is no calendar, use the week planned with `/plan-week` in this Project or memory.
4. **If the profile says the athlete is off the bike:** show the planned alternative session (run, gym, swim...) the same way. If nothing is planned, propose one from the sports they can do. If the planned end date (or the check-in date of an open-ended period, such as an injury) has passed, ask whether they are back on the bike. If they say the break is over at any point, or confirm, close the period with `/time-off` before showing a session.
5. **If nothing is planned:** say so plainly. Offer to plan today (a short proposal) or the week (`/plan-week`). Do not silently make up a session and present it as the plan.

## 2. Check whether the plan still fits

Look at, without asking for anything that is already in the data:
- what the athlete said in their message (tired, legs heavy, sick, only 45 minutes, raining, indoor/outdoor, which bike);
- recent load: yesterday and the last few days vs what was planned;
- recovery data if available: sleep, resting HR and HRV against the athlete's own baseline;
- a recent pattern of failed sessions or very high RPE.

If the athlete gave no context and there is no recovery data, ask one short question (how they feel and how much time they have) only if the session is a hard one; for an easy session, just show it.

**Change the session only when a parameter is out**, for example: the athlete reports fatigue, illness or pain; much less time than planned; poor sleep plus elevated resting HR or low HRV; yesterday's load far above plan; repeated failed sessions. Normal day-to-day noise is not a reason.

## 3. Output

**If the plan stands:**
- The session exactly as planned: duration, objective, structure table with watts (+% FTP), HR, RPE. Exact single watts if it is an ERG trainer session; ranges outdoors; HR/RPE if the bike has no power meter.
- Execution notes: one or two concrete cues (for example "if reps 3-4 can't hold 228 W, stop at 3").
- Fueling: before (what and when), during (g/h, bottles, sodium if hot or long), after. For sessions under 75 minutes, keep this to one line.

**If a change is warranted:**
- What was planned, what you propose instead, and why in one or two sentences tied to the specific signals.
- Where the planned key session moves to, if it should be kept this week.
- Ask before writing the change to the calendar (preview first, as in `data-sources.md`). If the athlete prefers to do the original session, respect it and give them the safety cues.

Keep it to one screen. This is read before getting on the bike.
