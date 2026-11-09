# Contributing

Thanks for helping make Cycling Training a better coach.

## Good contributions

- Corrections to the method backed by evidence (add the reference to `shared/evidence.md`, summarised in your own words, with a DOI).
- Clearer instructions in a command when Claude misreads them; describe the prompt you used and what went wrong.
- Support for more data sources.
- Translations of the README.

## Rules

- Never commit personal data: no real athlete profiles, rides, health data or credentials.
- Do not add copies of papers or other copyrighted text. Summarise and cite.
- Edit the method in `shared/`, then run `scripts/sync-shared.sh` so every skill gets the update. Commit both.
- Keep instructions in English. The coach replies in the athlete's language.
- When you add, rename or remove a command, update `shared/commands.md` (the list behind `/guide`) and the command table in `README.md`.
- Bump the version in `plugins/victoranto-cycling-coach/.claude-plugin/plugin.json` and add a line to `CHANGELOG.md` for user-visible changes.

## Testing

In Claude Code: `claude plugin validate ./plugins/victoranto-cycling-coach`, then `claude --plugin-dir ./plugins/victoranto-cycling-coach`.
On claude.ai: run `scripts/build-zip.sh` and upload the zip in Customize > Plugins > Add > Upload plugin.

By contributing you agree your contribution is licensed under CC BY 4.0.
