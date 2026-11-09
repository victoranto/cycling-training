# Cycling Training

A personal cycling coach for road, gravel and ultra-distance riders.

## Install

In Claude Code:

```
/plugin install victoranto-cycling-coach --marketplace victoranto/cycling-training
```

On claude.ai: Customize > Plugins > Add > Add marketplace, and enter `https://github.com/victoranto/cycling-training`.

## Use it

Not sure what to do? Ask `/guide`. Start with `/setup` inside a Claude Project to build your athlete profile and races. Then use `/plan-week` to plan your week, `/today` before training, `/analyze` after a ride, `/time-off` when you go off the bike (travel, break, injury) and when you are back, `/fueling` before a long ride or race, and `/review` at the end of the month. You can also talk to it in plain language and it picks the right command.

## Data

The plugin reads your training from the Strava connector and from Intervals.icu through the Stas connector when you have connected them, and writes planned workouts to Intervals.icu only after you confirm. Your profile is kept in your own Claude account (memory and project instructions). The plugin stores nothing itself and sends nothing anywhere else.

[Privacy policy](https://github.com/victoranto/cycling-training/blob/main/PRIVACY.md)

Not medical or dietary advice.

By Victor Gonzalez (https://victoranto.com/) · CC BY 4.0 · https://github.com/victoranto/cycling-training
