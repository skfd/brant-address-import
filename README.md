# brant-address-import

The **Brant County checkout** of the address-import family — dataset #14 in
the onboarding pass, scaffolded 2026-08-16 by the breadth-first loop (engine
`future-work/multi-city/onboarding-queue.md`), the first city admitted by the
licence-review reopening. Status: **onboarding**. No proposal published, no
uploads made; the config is a first draft for conflation baseline runs.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Brant's `config.toml`,
credentials (`.env.*`, gitignored, from the `.example` files), and — locally,
gitignored — `data/` with the OSM extract and `data/brant/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../brant-address-import
```

Source data: County of Brant civic addressing via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/brant/brant.db`, 19,333 rows / 18,097 numbered at snapshot 61,
2026-08-15 — tracker fresh, daily pulls). Licence: the AGO item is marked
**CC0** (verified 2026-08-16) — ODbL-compatible outright, the family's first
non-OGL green dataset; an optional courtesy note to the county confirming the
marking is the only licensing loose end.

Structural facts (details in config comments): a **single-tier county** whose
PLACE_NAME field is former-township trivia, not a jurisdiction; **1,236 rows
carry no housenumber** (905 of them no address fields at all) — TODO §8's
number-less-rows policy, second consumer; the housenumber comes from
FULL_ADDRESS's leading token to keep the 219 alpha qualifiers ("17A") the
tracker's number column drops; ALL-CAPS street names (TODO §9 gates upload);
**the City of Brantford is a donut hole** in the bbox with its own dataset;
and tiles ride the 5-polygon ward layer (99.98% point-test) after the
settlement fabric repeated Quinte West's 72%-coverage trap.

Entry state probed 2026-08-16 (`onboarding/entry-state-2026-08-16.json`):
**greenfield (CanVec seed)** — 574 of 649 sampled elements are the 2013
`CanvecImports` sweep (loose nodes, `addr:city="County of Brant"`), no wiki
page, no import-tagged changesets, and a light manual trickle since:
**riuri** (addresses near Burford and Vanessa, 2026-08 — active this month),
hoon (buildings + businesses, 2026-01), TheManWithTheYellowHat (address
fixes, 2024). Contact riuri before anything visible; honour the existing
`addr:city="County of Brant"` convention or negotiate a change first.

Before any production upload: wiki proposal page, forum announcement, and
feedback window per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines)
— Toronto's [`IMPORT_PROPOSAL.mediawiki`](https://github.com/skfd/toronto-2-address-import/blob/main/IMPORT_PROPOSAL.mediawiki)
is the template.

MIT licensed.
