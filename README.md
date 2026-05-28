# Snapmaker U1: Optimized Settings
*A streamlined Klipper integration for Spoolman, designed for efficiency and filament tracking.*

## Why use this?
This project provides a robust bridge between **Klipper** and **Spoolman**, allowing for automatic spool tracking, persistent selection across reboots, and multi-tool support (T0–T3) for the Snapmaker U1.

## Technical Highlights
* **Persistent Spool Memory**: Leverages Klipper's `[save_variables]` to remember which spool is loaded on which tool, even after a power cycle.
* **Multi-Tool Synchronization**: Custom macros for `T0`, `T1`, `T2`, and `T3` automatically update the active spool in Spoolman when a tool change occurs.
* **Automated State Restoration**: Includes a delayed initialization sequence (`RESTORE_SELECTED_SPOOLS`) to ensure the printer state matches the physical reality upon startup.
* **Clean & Modular Config**: The Spoolman logic is isolated into a dedicated `spoolman_multi_tool.cfg`, making it easy to include in your main `printer.cfg` without cluttering your primary configuration.

## Installation

### 0. Reference Guide
This builds upon the foundations laid in the [U1 Spoolman Guide](https://github.com/unlucio/U1-klipper-configs/blob/main/spoolman/README.md). Make sure your printer is in advanced mode before following these steps.

### 1. Deploy Spoolman
The included Docker configuration handles the backend.
1. Navigate to the `spoolman/` directory.
2. Run `docker-compose up -d`.
3. Access the web interface at `http://<your-ip>:7912`.

### 2. Klipper Configuration
1. Add `[include config/custom/spoolman_multi_tool.cfg]` to your `printer.cfg`.
2. Verify that your `variables.cfg` path matches the one defined in the macro file.

## Included Files
* **`spoolman/docker-compose.yml`**: The container for the Spoolman database and API.
* **`config/custom/spoolman_multi_tool.cfg`**: The core Klipper macros for active spool management and persistence.
* **`.gitignore`**: Pre-configured to keep local database and environment secrets out of version control.

## Credits & Resources
* **[unlucio/U1-klipper-configs](https://github.com/unlucio/U1-klipper-configs)**: The original inspiration and source for the multi-tool configuration logic.
* **[Spoolman](https://github.com/Donkie/Spoolman)**: The backend filament tracking system.

---
*Note: This configuration was developed for a Snapmaker U1 multi-tool setup but can be adapted for any Klipper-based toolchanger or IDEX machine.*
