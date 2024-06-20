# RaidMe Plugin

## Overview

The `RaidMe` plugin allows players to create a temporary PvP zone around their Tool Cupboard (TC) using the `/raidme` command. Admins have additional commands to list, remove, or wipe all PvP zones. The plugin features configurable zone radius, customizable messages, and automatic cleanup of invalid zones.

## Features

- Create a temporary PvP zone around a player's TC.
- Configurable zone radius.
- Customizable messages for entering and leaving the zone.
- Automatic cleanup of invalid zones.
- Admin commands to manage all PvP zones.

## Installation

1. Download the `RaidMe.cs` file.
2. Place the file into your `oxide/plugins` directory.
3. Restart your server or use the `oxide.reload RaidMe` command to load the plugin.

## Configuration

The default configuration is automatically created when the plugin is first loaded. You can modify the configuration file located at `oxide/config/RaidMe.json`.

### Default Configuration

```json
{
  "RaidZoneBaseRadius": 40.0,
  "RaidZoneMinRadius": 30.0,
  "RaidZoneMaxRadius": 80.0,
  "RaidZoneRadiusMultiplier": 1.0,
  "RaidZoneExclusionBaseRadius": 100.0,
  "RaidZoneExclusionMinRadius": 50.0,
  "RaidZoneExclusionMaxRadius": 300.0,
  "RaidZoneExclusionRadiusMultiplier": 1.0,
  "ZoneDeactivationDelay": 180.0,
  "MarkerColor": "#FF0000",
  "MarkerAplha": 0.4,
  "MarkerSize": 0.75
}
```
## Permissions

- `raidme.use` - Required to use the `/raidme` command.
- `raidme.admin` - Required to use the admin commands.

## Commands

### Player Commands

- `/raidme start` - Create a PvP zone around a TC you own.
- `/raidme remove` - Schedule the removal of the PvP zone around your TC after the configured delay.
- `/raidme cancel` - Cancel the scheduled removal of the PvP zone around your TC.
- `/raidme help` - Display the help message.

### Admin Commands

- `/raidmeadmin list` - List all PvP zones.
- `/raidmeadmin remove` - Remove the PvP zone in which you are standing.
- `/raidmeadmin wipe` - Remove all PvP zones.
- `/raidmeadmin help` - Display the help message.

## Data Management

The plugin saves and loads data automatically. The data is stored in the `oxide/data/RaidMe.json` file.

### Data Format

- `RaidZoneList`: List of active PvP zones.
- `TcMapMarker`: List of map markers for the TCs.

## Hooks

### `OnPlayerAttack(BasePlayer attacker, HitInfo info)`

- Cancels the removal timer if the attacker or target is within a PvP zone.

### `OnExitZone(string zoneID, BasePlayer player)`

- Cancels the removal timer if the player exits their PvP zone.

### `OnEntityKill(BaseNetworkable entity)`

- Removes the PvP zone if the TC is destroyed.

## Development

### Variables and Constants

- `PermissionUse`: Permission string for player commands.
- `PermissionAdmin`: Permission string for admin commands.
- `DataFileName`: Name of the data file.
- `TcSearchRadius`: Search radius for finding TCs.

### Configuration

- `RaidZoneBaseRadius`: Base radius for the PvP zone.
- `RaidZoneMinRadius`: Minimum radius for the PvP zone.
- `RaidZoneMaxRadius`: Maximum radius for the PvP zone.
- `RaidZoneRadiusMultiplier`: Multiplier for the PvP zone radius.
- `RaidZoneExclusionBaseRadius`: Base radius for the exclusion zone.
- `RaidZoneExclusionMinRadius`: Minimum radius for the exclusion zone.
- `RaidZoneExclusionMaxRadius`: Maximum radius for the exclusion zone.
- `RaidZoneExclusionRadiusMultiplier`: Multiplier for the exclusion zone radius.
- `ZoneDeactivationDelay`: Delay before the PvP zone is deactivated.
- `MarkerColor`: Color of the map marker.
- `MarkerAplha`: Alpha transparency of the map marker.
- `MarkerSize`: Size of the map marker.

### Functions

- `CreateRaidMeZone(BasePlayer player, BuildingPrivlidge tc)`: Creates a PvP zone around the specified TC.
- `RemoveRaidMeZone(BasePlayer player)`: Schedules the removal of the PvP zone around the player's TC.
- `CancelRemoveTimer(BasePlayer player)`: Cancels the removal timer for the player's PvP zone.
- `WipeAllZones(BasePlayer player)`: Removes all PvP zones.

### Helpers

- `TryGetValidTc(BasePlayer player, out BuildingPrivlidge playerTc)`: Attempts to find a valid TC for the player.
- `FindValidTc(BasePlayer player)`: Finds a valid TC for the player.
- `RemoveZone(ulong tcOwner)`: Removes the PvP zone for the specified player.
- `CreateMapMarker(BuildingPrivlidge tc)`: Creates a map marker for the specified TC.
- `RemoveInvalidZones()`: Removes invalid PvP zones.
- `RemoveGlobalMarkers()`: Removes all global map markers.
- `PlaceMapMarkers()`: Places map markers for all active TCs.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.