---
name: time-off
description: Registers, changes or closes a period off the bike (travel, season break, no bike available, injury or illness) in the athlete profile, then plans around it and plans the return to the bike. Use for /time-off and whenever the athlete says they will be or are off the bike, "me voy de viaje", "no tengo bici", "parón", "estoy lesionado", "me he lesionado", "I'm injured", "I'm traveling for 3 weeks", "vuelvo a la bici el lunes", "ya he vuelto", "ya terminé el parón", "ya me recuperé", "me dieron el alta", "I'm recovered", "I'm back", or changes the dates of a break.
---

# Time off the bike

> Paths in this skill are relative to this skill's own folder
> (the "Base directory for this skill" shown when it loads),
> e.g. `<base>/references/coaching-principles.md`.
> Never resolve them from the plugin root. If a file is missing,
> look inside this skill's folder before continuing; do not skip it.

Manage the temporary "off the bike" status of the athlete profile. This command only handles the status and the transitions; the training rules (what to do meanwhile and how to come back) live in `references/zones-and-sessions.md` (Off the bike and coming back) and are applied by `/plan-week` and `/today`.

Read `references/athlete-profile.md`, `references/zones-and-sessions.md` and `references/coaching-principles.md` (in this skill's folder). Load the profile first; if it does not exist, offer `/setup`.

## Pick the mode

- **Start:** the athlete is, or will be, off the bike and the profile has no active period.
- **Change:** a period exists and the dates, sports or restrictions change (a trip gets longer, the injury gets better). Update only what changed.
- **End:** the athlete says the break or injury is over, or the end date (or the check-in date of an open-ended period) has passed and they confirm. Go to "Coming back". Other commands hand over here, so the athlete can say it anywhere.

## Start

Ask what is missing, in one short message, never as a wizard:

1. **When:** start and end date, or open-ended.
2. **What they can do instead:** running, gym, swimming, hiking, walking, elliptical, rowing, nothing for now.
3. **Should the coach program those sessions,** or only fit them in?
4. **Restrictions**, only if it is an injury or illness: what the athlete says their doctor or physio allows or forbids (for example "no running, no impact", "walking and upper body only"). Record those words as given.

The reason is optional. Never ask for medical details, never name or assess a diagnosis, and never estimate recovery times.

### Injury or illness

- Medical limits come from the athlete's professional, not from the coach. Plan strictly inside the restrictions they report, and do not plan anything for the affected area or activity.
- If the athlete describes pain, symptoms that are new or getting worse, chest symptoms, fainting or anything that sounds acute, stop the training discussion and recommend a professional first (the "not a doctor" rule in `coaching-principles.md`). Register the status only after that, or as "reason not specified".
- If they have not seen anyone and the problem persists, suggest it once, without insisting.
- Illness: no intensity until they feel normal again. The return is gradual, as below.
- An open-ended period is normal for an injury. Ask for a date to check in, not an end date to commit to.

## Save

1. Show the status line as it will be written, in the profile format (`Current status` in `athlete-profile.md`).
2. Save it to memory if available, and give the updated profile block to paste into the Project instructions, as the other commands do. If the profile exists in more than one place and the copies disagree, ask which is right and update every copy.
3. Check what the break touches and say it in a few lines, only what applies:
   - planned workouts in the calendar that fall inside the period (offer to remove them, preview first, never silently);
   - a B or C race in or right after the period (ask whether they still do it; do not decide for them);
   - an FTP test that was planned (it moves to after the return);
   - the A race, only if the break clearly threatens the plan, with one honest sentence.
4. **Ask before planning:** "Do you want me to plan the week with this now?" Run `/plan-week` only on a yes. Do not plan unasked.

## Coming back

1. Confirm the return date, and for an injury ask whether the professional has cleared them to ride. If not cleared, keep the period open and move the check-in date.
2. Remove the `Current status` lines from the profile and save it.
3. If the break lasted more than about 2-3 weeks, or the FTP is old, mark the FTP **provisional** and note the next test (after 2-3 easy rides, never the first ride back).
4. Say the return rules in a few lines (easy Z1-Z2, shorter than before, quality returns when easy rides feel normal) and offer `/plan-week` for the first week back. Ask before planning, as above.

## Output

Short, in the profile's language and units. Show:
- the status line saved (or removed);
- what the break affects (only the items that apply);
- the one question about planning.

Keep it to one screen.
