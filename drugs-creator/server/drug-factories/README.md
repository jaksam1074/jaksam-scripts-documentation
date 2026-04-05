# Drug Factories

Drug Factories are purchasable interiors where players can produce drugs through a multi-step production process

## Features

- **Purchasing**: players can buy a factory through the in-game menu. Each factory has a configured price and an optional per-player ownership limit
- **Interior**: each factory uses an IPL (e.g. meth lab, coke lab)
- **Production stations**: factories have stations where players perform production steps (mixing, pressing, pouring). Each step consumes input items and produces output items after a configured duration
- **NPC Workers**: station workers can be hired as upgrades, increasing production speed through configurable multipliers. Each station supports multiple upgrade levels with individual costs
- **Stash**: each factory has a private stash for storing ingredients and finished products
- **Whitelist**: factory owners can whitelist other players to grant them access
- **Visitors / Bell**: non-whitelisted players can ring the bell at the factory entrance, and the owner can accept or deny entry
- **Selling**: owners can sell their factory back

## Configuration

All factory settings (prices, stations, production steps, upgrades, stash limits) are managed through the in-game `/drugscreator` menu
