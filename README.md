# OPRA mirror

This repository serves a copy of [OPRA (Open Profiles for Revealing Audio)](https://github.com/opra-project/OPRA), the community-maintained directory of headphone information and equalizer compensation curves. The profiles belong to their credited authors; OPRA collects and distributes them.

The mirror copies only OPRA's `dist/database_v1.jsonl`, without artwork or other assets. It serves a macOS music player that ships an offline snapshot and, while its online lookup is on, checks this mirror at most once every seven days. Commercial apps should serve their own copy instead of fetching OPRA's GitHub distribution or Roon's mirror at run time.

## Updates

Run **Actions > Mirror OPRA > Run workflow** once to populate `dist/`. After that it runs every Monday at 04:23 UTC, and can also be run manually. Scheduled workflows run from the default branch; GitHub may delay scheduled runs or disable them after extended repository inactivity, so check the Actions page if the mirror stops updating.

The workflow downloads to a temporary file, validates every nonblank line with Python's standard library, requires vendor, product and EQ records, and commits only when the data or its license note changed. Failed downloads or validation leave the previous committed copy intact. Only the official `actions/checkout` action is used; the other steps run shell and Python already on GitHub's runner.

The mirror's URL is:

```
https://raw.githubusercontent.com/davidelarocca/opra-mirror/main/dist/database_v1.jsonl
```

## License

The mirrored manufacturer, product and EQ data is OPRA's, licensed under [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/). It is copied without modification. The workflow writes this attribution and license link to `dist/LICENSE.md` beside the data. Credit each profile's author when presenting or applying a profile, and follow [OPRA's attribution guidance](https://github.com/opra-project/OPRA#how-is-this-repository-licensed).

The mirror does not change the authorship or license of any profile. Upstream source: [OPRA's database distribution](https://github.com/opra-project/OPRA/tree/main/dist).
