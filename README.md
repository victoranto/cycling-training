# Cycling Training

A personal cycling coach for [Claude](https://claude.ai), packaged as an open-source plugin. Built for road, gravel and ultra-distance riders who want to get faster and last longer without burning out, and who like to understand *why* they are doing each session.

It speaks your language, uses your units, plans around your real week and your races, keeps the bike first while fitting in the gym, swimming or running, and uses your Strava and Intervals.icu data when they are connected.

> Not a doctor, not a dietitian. This plugin coaches training and on-the-bike fueling. It does not create diets or weight-loss plans, but if you already have a nutrition setup (in your Claude Project or with a dietitian), it works around it instead of against it. Anything medical belongs with a professional.

## Commands

| Command | What it does |
|---|---|
| `/setup` | Checks your connected data, then builds your athlete profile: language, units, FTP, races with A/B/C priority (distance, date, elevation, surface, format, goal), availability, equipment, other sports and preferences. Also updates it later ("new FTP 255"). |
| `/plan-week` | Plans the week around your availability, fatigue and races: key sessions, long ride, other sports, deloads and tapers, with watts, HR and RPE. Can write it to Intervals.icu after you confirm. |
| `/today` | Shows today's planned session as planned, with execution notes and fueling. Only proposes a change when there is a reason: you are tired, ill, short on time, or recovery data is off. |
| `/analyze` | Analyzes a ride or training day (power, HR, RPE, volume, elevation, fueling, load), compares it with the plan and decides the next session. Asks for RPE and what you ate if missing. Ask for a "summary" for a one-screen version. |
| `/time-off` | Registers a period off the bike (travel, season break, no bike, injury or illness), plans around it with the sports you can do, and plans the return to the bike. Closes the period when you are back. |
| `/guide` | Lists what the coach can do, with one line per command, and suggests where to start for your situation. |
| `/fueling` | Builds a fueling plan for a long ride or race: carbs per hour, bottles, sodium, what to carry, where to resupply, before and after, and gut training for key races. |
| `/review` | Reviews the last month (or block, or season): load trends, compliance, intensity, best efforts and W/kg, durability on long rides, progress towards your A race, and what to change next. |

You can also just talk to it ("I'm wrecked, should I still do the intervals?"); Claude picks the right command.

In Claude Code, commands are namespaced: `/victoranto-cycling-coach:setup`, `/victoranto-cycling-coach:today`, and so on.

## How it coaches

- Several metrics together, never one alone: power, heart rate, RPE, volume, elevation and accumulated load.
- Consistency and gradual progression first; volume and intensity do not both go up without a reason.
- Planned deloads, and tapers chosen by race priority.
- FTP is a moving reference, checked against how your sessions actually go; it tells you when to re-test.
- Exact single watts for ERG trainer sessions, ranges outdoors, HR and RPE for bikes without a power meter.
- Nothing is invented: if data is missing, it asks.

The method is backed by the studies listed in [`shared/evidence.md`](shared/evidence.md) (intensity distribution, durability, tapering, FTP validity, load monitoring, strength training and the 2026 UCI position statement on nutrition for cycling).

## Install

### claude.ai (web, desktop and mobile chat)

Requires a paid plan with code execution enabled (Settings > Capabilities).

**From this repository (gets updates):**
1. Go to **Customize > Plugins > Add > Add marketplace**.
2. Enter `https://github.com/victoranto/cycling-training`.
3. Install **Cycling Training**.

**From a zip:**
1. Download `victoranto-cycling-coach-<version>.zip` from [Releases](https://github.com/victoranto/cycling-training/releases).
2. Go to **Customize > Plugins > Add > Upload plugin** and select the zip.

### Claude Code

```
/plugin marketplace add victoranto/cycling-training
/plugin install victoranto-cycling-coach@victoranto
```

### First run

Create a Claude **Project** (for example "Cycling Training"), open a chat inside it and run `/setup`. The project keeps your profile, history and chats together. At the end, `/setup` saves your profile to memory and gives you a block to paste into the project instructions.

## Data sources

| Source | Used for | How |
|---|---|---|
| Strava | Completed rides, streams, zones | Strava connector (read-only) |
| Intervals.icu | Training load, wellness (sleep, HRV, resting HR), planned calendar; writing planned workouts | Through the Stas connector |
| Garmin | Rides and wellness | No direct connector; arrives through Strava or Intervals.icu sync |
| Nothing connected | Everything still works with data you paste or describe | — |

Writing to your calendar is always previewed first and only done after you say yes. Workouts the coach writes to Intervals.icu can then sync to your head unit and trainer apps if you have linked them there.

Your data stays in your own Claude account. Nothing personal is stored in this repository.

## Privacy

The plugin has no servers and sends nothing to the author or to third parties. Read the full [Privacy policy](PRIVACY.md).

## Repository layout

```
.claude-plugin/marketplace.json     marketplace definition
plugins/victoranto-cycling-coach/   the plugin
  .claude-plugin/plugin.json
  skills/<command>/SKILL.md         one folder per command
  skills/<command>/references/      copies of shared/ (generated)
shared/                             the coaching method and evidence (edit here)
scripts/sync-shared.sh              copies shared/ into every skill
scripts/build-zip.sh                builds dist/victoranto-cycling-coach-<version>.zip
```

Edit the method in `shared/`, run `scripts/sync-shared.sh`, and commit both.

## Contributing

Issues and pull requests are welcome, especially from coaches and sports scientists. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Author

**Victor Gonzalez** · [victoranto.com](https://victoranto.com/) · [github.com/victoranto](https://github.com/victoranto)

## License

[CC BY 4.0](LICENSE). Use it, adapt it, share it, commercially or not, as long as you credit the author and link back here. Cited papers belong to their authors and are only summarised and referenced.
