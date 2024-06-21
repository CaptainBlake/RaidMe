# RaidMe Plugin

## Overview

The `RaidMe` plugin allows players to create a temporary PvP zone around their Tool Cupboard (TC) using the `/raidme` command. Admins have additional commands to list, remove, or wipe all PvP zones. The plugin features configurable zone radius, customizable messages, and automatic cleanup of invalid zones.

## Description

The `RaidMe` plugin provides a unique PvP experience by allowing players to create a temporary PvP zone around their Tool Cupboard (TC). The plugin offers the following commands:

- `/raidme start`: Creates a PvP zone around a designated TC.
- `/raidme remove`: Starts a 180-second timer to remove the PvP zone.
- `/raidme cancel`: Cancels the scheduled removal of your PvP zone.
- `/raidme help`: Displays a list of available commands and their usage.

### How it works

- PvP Zone Creation: Use `/raidme start` to create a PvP zone around your TC.
- Zone Removal: The PvP zone gets removed once the designated TC is destroyed or by using `/raidme remove`.
- Removal Timer: Use `/raidme remove` to start the 180-second removal timer. You must stay within the zone and avoid taking or dealing damage during this period.
- Single Zone Limitation: You can only have one PvP zone active at a time.
- Destructible Buildings: All buildings within the PvP zone can be destroyed.

## Features

- Create a temporary PvP zone around a player's TC.
- Configurable zone radius.
- Customizable messages for entering and leaving the zone.
- Automatic cleanup of invalid zones.
- Admin commands to manage all PvP zones.

## Requirements

This plugin requires the following plugins to be installed:

- [TruePVE](https://umod.org/plugins/true-pve): This plugin is used to manage the PvE environment.
- [ZoneManager](https://umod.org/plugins/zone-manager): This plugin is used to manage the PvP zones.

Please ensure these plugins are installed and properly configured before using the `RaidMe` plugin.

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

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.