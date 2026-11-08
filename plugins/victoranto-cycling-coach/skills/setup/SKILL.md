---
name: setup
description: First-time setup and profile updates for the Cycling Training coach. Checks connected data sources (Strava, Stas/Intervals.icu, Garmin), then builds the athlete profile step by step - language, units, FTP, races with A/B/C priority, availability, equipment, other sports, preferences - and saves it. Use when the athlete runs /setup, says "configurar", "set up my coach", "update my profile / actualizar ficha", reports a new FTP, weight, race, schedule or time off the bike, or when any other Cycling Training command finds no profile.
---

# Setup

Build (or update) the athlete profile that every other Cycling Training command depends on. Read `references/coaching-principles.md`, `references/athlete-profile.md` and `references/data-sources.md` first.

## Two modes

- **Full setup** (no profile exists, or the athlete asks for it): run all steps below.
- **Update** ("update my profile", "new FTP 255", "I added a race", "off the bike for 3 weeks", "actualizar ficha"): change only what the athlete names, show the changed lines, save, done. Do not re-run the whole wizard.
- In either mode, if you find the profile in more than one place and the copies disagree (for example a different race goal in memory and in the Project instructions), show both values, ask which is right, and update every copy.

## Before the questions

1. **Project check.** If the chat is not inside a Claude Project, recommend creating one first (for example "Cycling Training"), because the profile, history and chats then stay together. Tell them how: create a Project in Claude, open a new chat inside it and run `/setup` again. If they prefer to continue here, continue.
2. **Connections (step 0).** Check which data sources are available in this chat: Strava, Stas (Intervals.icu). Tell the athlete in one short table what is connected, what each one is for, and what is missing:
   - Strava: reads completed rides.
   - Stas: reads training load, wellness and the Intervals.icu calendar, and writes planned workouts to Intervals.icu.
   - Garmin: no direct connector; data arrives through Strava or Intervals.icu if those syncs are on.
   If something useful is missing, explain in one line how to connect it (Claude's connector settings) and that it is optional. Do not block setup on it.
3. **Prefill.** If Strava or Stas are connected, read what you can (FTP, weight, zones, recent volume, planned races) so you only ask for what is missing or needs confirming.

## The questions

Ask everything at the start, in short blocks, one block per message, waiting for the answer before the next. Offer tappable options when the interface supports multiple-choice questions; otherwise list the options inline. Skip any question already answered by prefill, but show the prefilled value so the athlete can correct it. Keep each block to 3-5 questions.

**Block 1 - Language and athlete**
- Which language should the coach use? (from now on, reply in it)
- Units: metric or imperial?
- Age, current weight (used only for W/kg).
- Years riding and longest event or ride done.

**Block 2 - Performance**
- Current FTP, and how and when it was measured: recent 20' test / ramp / app estimate / don't know.
- Max HR or threshold HR, if known.
- Own zones configured in Intervals.icu or Strava, or use the default Coggan zones?
If FTP is unknown, an app estimate or older than ~8 weeks, mark it **provisional** in the profile and note that the first planned week will include a test.

**Block 3 - Races** (this block matters most; explain before asking)
First explain the priorities in a few lines:
- **A - main goal:** the season builds towards it, with a 1-2 week taper. Ideally one, at most two.
- **B - important:** you want to do it well; 2-4 lighter days before, the plan keeps going.
- **C - training race:** used as a hard session or a rehearsal; trained through.

Then ask how many races are planned and, for each one:
1. Name and date
2. Distance and elevation gain
3. Surface: road, gravel or mixed
4. Format: sportive, race, self-supported ultra, stages/multi-day, and any time limit
5. Goal: finish, a target time, a position
6. Priority A/B/C (offer to propose one if unsure)
7. Optional: link or GPX of the route

Then ask, as optional: do they want a yearly distance goal (for example 5,000 km this year)? If yes, ask which riding counts (road, gravel, indoor/virtual) and, if Strava is connected, show the distance done so far this year. Make clear it is for motivation and will not push junk kilometres into the plan.

If they have no races yet, plan by goals (raise FTP, endurance) until they choose one. Propose priorities if theirs look unbalanced (for example three A races) and explain why in one sentence.

**Block 4 - Availability and equipment**
- Days and hours per week; which day allows the long ride.
- When they move indoors, and which trainer and app (MyWhoosh, Zwift, ...).
- Bikes, and which have a power meter.
- HR sensor: chest, arm or wrist.

**Block 5 - Other activities**
- What else they do: gym, swimming, running, hiking, other.
- How often and on which days.
- Should the coach program those sessions, or only fit them around the bike?
- Any time off the bike coming up (travel, season break, no bike)? If so, when, and what can they do instead? (The reason is optional; never ask for medical details.)

**Block 6 - Preferences**
- Coach tone: gentle, direct, very demanding.
- Write planned sessions to Intervals.icu via Stas? (only offer if Stas is connected; every write is still previewed and confirmed)
- Injuries, pain or limitations to keep in mind.

## Close

1. Show the complete profile using the template in `references/athlete-profile.md` and ask the athlete to confirm or correct it.
2. Save it: to Claude's memory if memory is available, and give the full profile block, ready to copy, to paste into the Project instructions. Say plainly if memory is not available so they know the pasted block is what persists.
3. Start with something useful right away: offer the first week (`/plan-week`), with an FTP test in it if FTP is unknown or stale.

Never put the athlete's data anywhere public, and never ask for passwords, account numbers or ID documents.
