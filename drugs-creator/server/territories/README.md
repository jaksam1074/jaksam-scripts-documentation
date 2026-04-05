# Territories

Territories are polygon-based zones that can be owned and contested by gangs or jobs. The faction with the most points above the configured threshold becomes the territory owner

Factions can earn points through:
- **Drug sales** within the territory (all selling methods)
- **Kills** (optional, configurable via in-game menu)
- **External scripts** via the [giveTerritoryPoints](give-territory-points.md) export

Territory ownership provides benefits such as higher drug sale prices, reduced police alert chances, and access to the [Hired Dealers](../hired-dealers/) system

The system also supports **hot zones** - randomly selected territories that receive temporary bonus multipliers - and **point decay** over configurable intervals

All territory configuration (zones, thresholds, factions, hot zones, decay) is managed through the in-game `/drugscreator` menu
