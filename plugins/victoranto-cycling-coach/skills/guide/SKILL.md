---
name: guide
description: Lists what the Cycling Training coach can do, with one line per command and a suggestion of where to start for this athlete. Use for /guide and whenever the athlete asks "qué puedo hacer", "qué comandos hay", "ayuda", "por dónde empiezo", "what can you do", "what commands are there", "help", or seems lost.
---

# Guide

> Paths in this skill are relative to this skill's own folder
> (the "Base directory for this skill" shown when it loads),
> e.g. `<base>/references/coaching-principles.md`.
> Never resolve them from the plugin root. If a file is missing,
> look inside this skill's folder before continuing; do not skip it.

Read `references/commands.md` (in this skill's folder). Optionally read `references/athlete-profile.md` (same folder) to find the profile. This command only informs: it does not plan, analyze or change anything.

## 1. Look for the profile

Load it if it exists (memory or Project), without asking questions. Use its language and units. If there is none, reply in the language of the athlete's message.

## 2. Reply

Show the commands from `commands.md`, one line each: the command, what it does, and when to use it. Translate to the athlete's language. Do not add commands that are not in the list, and never invent features.

Put first, under **Start here**, the one or two that fit the athlete now:
- No profile: `/setup`.
- An active period off the bike in the profile, or past its end or check-in date: `/time-off` and `/today`.
- A race within about 3 weeks: `/plan-week` and `/fueling`.
- Otherwise, a ride finished recently and not analyzed: `/analyze`; if it is the start of the week: `/plan-week`; else `/today`.

If you cannot tell, do not guess: show the plain list.

Finish with one line: they can also write in plain language ("I'm wrecked, should I still do the intervals?", "me voy de viaje 2 semanas") and Claude picks the right command.

Keep it to one screen.
