# Athlete profile

Nothing about the athlete is assumed. Everything personal lives in their profile, which `/setup` creates and every other command reads.

## Where the profile lives

Look for it in this order:
1. The Claude Project's instructions (a block starting with `## Cycling Training profile`).
2. Claude's memory (the project's memory if the chat is inside a Project).
3. The current conversation.

If no profile exists, or key fields are missing for what was asked (FTP, availability, A race), say so in one line and offer `/setup`. For a quick question you can still help with what you have, stating what you assumed.

When values change (new FTP, new weight, new race, different availability), update the profile: save it to memory if memory is available, and give the athlete the updated block to paste into the Project instructions. Always use the most recent FTP. For weight, use a recent average, not a single reading (see `data-sources.md`).

If the profile exists in more than one place (Project instructions, memory, a document) and the copies disagree, for example two different goals for the same race, do not pick one silently. Ask the athlete which is right, then update every copy.

## Profile template

Keep the profile compact. Use this structure:

```markdown
## Cycling Training profile
Updated: YYYY-MM-DD

**Preferences**
- Language: …            - Units: metric | imperial
- Coach tone: gentle | direct | very demanding
- Write sessions to calendar: yes (via Stas → Intervals.icu) | no
- Injuries / limitations: …

**Athlete**
- Age: …   Weight: … (for W/kg only)
- Riding experience: … years · longest event: …

**Performance**
- FTP: … W (method: 20' test | ramp | app estimate | unknown · date: … · status: tested | provisional) · W/kg: …
- Next FTP test: … (if planned)
- Max HR / threshold HR: … (or unknown)
- Zones: Coggan default | own zones in Intervals/Strava

**Yearly distance goal** (optional)
- … km (or mi) in YYYY · counts: road, gravel, indoor (as the athlete chose) · or "none"

**Races** (A = season goal, full taper · B = important, short taper · C = training race)
| Priority | Name | Date | Distance | Elevation | Surface | Format / cut-off | Goal |
|---|---|---|---|---|---|---|---|

**Availability**
- Weekly: … (days, hours, long-ride day)
- Indoor season: from … to … · trainer + app: …

**Equipment**
- Bikes: … (which have a power meter)
- HR sensor: chest | arm | wrist

**Other activities**
- … (what, how often, which days) · coach programs them | coach only fits them in

**Current status** (optional, temporary; remove when it ends)
- Off the bike: from … to … (or open-ended, with a check-in date) · reason: travel | break | no bike | injury/illness | not specified · doing instead: running | gym | swimming | hiking | …
- Restrictions (injury/illness only): as the athlete reports them from their doctor or physio, in their own words

Registered and closed with `/time-off`.

**Connected sources**
- Strava: yes/no · Stas (Intervals.icu): yes/no · Garmin: via Strava/Intervals sync
```

A wrist HR sensor is less reliable on the bike: when the profile says wrist, lean more on RPE and power.

FTP status is **provisional** when it comes from an app estimate, an old test or a guess. Keep it marked provisional until a test is done, and plan one (`zones-and-sessions.md`).

The reason for time off the bike is optional. Never ask for medical details; if the athlete mentions pain or injury, the "not a doctor" rule in `coaching-principles.md` applies.
