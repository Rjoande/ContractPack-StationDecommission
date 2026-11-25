# Contract Pack: Station Decommission

An add-on for [Contract Pack: Bases and Stations](https://github.com/linuxgurugamer/KerbinSpaceStation)
(KerbinSpaceStation) for Kerbal Space Program.

Bases and Stations lets you launch, crew, resupply and evacuate space stations, but
never asks you to get rid of one. This pack adds the missing end of the life cycle:
once a station has been in orbit for at least one Kerbin year, you may be asked to
evacuate it and deorbit it. When the station is gone, the "Launch a station"
contract of Bases and Stations becomes available again for that body.

## Requirements

- Kerbal Space Program 1.8.1 - 1.12.x
- [Contract Configurator](https://github.com/jrossignol/ContractConfigurator) 1.30 or later
- [Contract Pack: Bases and Stations](https://github.com/linuxgurugamer/KerbinSpaceStation) 3.7 or later
- ModuleManager (already required by the packs above)

The contract is wrapped in `:NEEDS[ContractPacks/KerbinSpaceStation]`, so the pack is
inert if Bases and Stations is not installed.

## Installation

Copy the `StationDecommission` folder into `GameData/ContractPacks/` so that you end
up with `GameData/ContractPacks/StationDecommission/StationDecommission.cfg`.

## The contract

**Decommission the space station orbiting X**

- Offered for a vessel of type *Station* with crew capacity, not landed, whose
  mission elapsed time is over one Kerbin year (426 days). Stations that already
  have another active Bases and Stations contract are not eligible.
- Step 1: leave nobody aboard the station.
- Step 2: deorbit and destroy the station.
- Rewards: 50,000 funds plus 5,000 per crew seat, and a little reputation.
  25,000 funds advance, 25,000 funds penalty on failure.
- Deadline: 500 days after acceptance. At most one active at a time.
- Like most Bases and Stations contracts, generation is gated by the shared
  `randomRoll` of the group, so it is not offered every time.

## Known limitations

These come from how Contract Configurator and KSP work, not from this pack:

- Tourists are not counted as crew by the evacuation check, so a station with only
  tourists aboard counts as evacuated. Bring them home first anyway.
- Terminating the station from the Tracking Station also counts as "destroyed".
  Nobody is stopping you, but where is the fun in that?
- The station age is its mission elapsed time. When vessels dock, KSP keeps the
  timer of the dominant vessel, so a station assembled in several launches may be
  younger than its oldest module.
- If the fragment carrying the root part survives re-entry and lands intact, the
  station is not "destroyed" and the contract cannot complete.

## Localization

Strings live in `Localization/en-us.cfg` and `Localization/it-it.cfg`. To add a
language, copy `en-us.cfg`, rename the inner node to your language code and
translate the values. Keep the `@/...` placeholders as they are.

## License

MIT. See [`LICENSE`](LICENSE). Bases and Stations is Copyright (c) severedsolo 2015,
maintained by linuxgurugamer, MIT licensed.
