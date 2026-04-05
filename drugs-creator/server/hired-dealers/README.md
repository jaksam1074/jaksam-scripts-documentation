# Hired Dealers

Hired Dealers are NPC dealers that players can hire through the **Trap Phone** to passively sell drugs in territories they own

Players need to own a [territory](../territories/) to hire a dealer in it. Each dealer can be stocked with drugs, and will autonomously sell them over time, accumulating earnings that the player can collect

The system includes a **heat** mechanic: each sale increases the dealer's heat, which raises the chance of the dealer being arrested or robbed. Heat decays over time

## Trap Phone

The Trap Phone is a usable inventory item (`trap_phone`) that opens the management UI. From it, players can:

- Hire and fire dealers in owned territories
- Stock dealers with drugs
- Collect earnings
- View dealer notifications (sales, arrests, robberies, territory lost, out of stock)
- Request meetups to interact with a dealer in-game
- View territory information
- Toggle corner selling (if enabled)

The item must be registered in your framework's item list - see the [Installation](../../installation.md) page for the item definition.

## Configuration

All hired dealers settings (pricing, sell intervals, max dealers, heat system, acceptable drugs) are managed through the in-game `/drugscreator` menu