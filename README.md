# DayZ Standalone Pterodactyl Egg

## Overview

This Pterodactyl egg allows you to deploy and manage DayZ Standalone dedicated servers with full Steam Workshop mod support, automatic port assignment, and streamlined updates. Designed for use on both Windows and Linux (via Wine/Proton), it's ideal for running survival, PvE, PvP, or custom-modded DayZ communities.

---

## Key Features

- **Automated Server Installation & Updates**
- **Full Steam Workshop Mod Support**
- **Exported DayZ Launcher modlist.html support**
- **Battle-tested mod folder structure**
- **Automatic port assignment (Game/Query ports)**
- **Windows and Linux compatibility (Proton/Wine on Linux)**

---

## Important Usage Notes

### 1. Mod Folder Requirements

- **All mod folder names must be in lowercase and contain no spaces.**
    - Example: `@cf;@dayzexpansion;@trader;`
    - _Do not use uppercase letters, spaces, or folders starting with a number._
- The `-mod` and `-serverMod` startup variables **must match your mod folder names exactly** (including lowercase).
- :warning: **The mod folder auto-convert to lowercase feature is currently NOT working.** This is a known issue.
    - _Until then, manually ensure your mod folders are named in lowercase before starting the server._

### 2. Modlist HTML Support & Steam Account Requirements

- The egg supports using an exported `modlist.html` file from DayZ Launcher for automated mod downloading.
- To use this function:
    - **You must provide a Steam account that owns DayZ** and is set in the server variables.
    - **Steam Guard/2FA must be completely turned OFF** for mod downloading and the `modlist.html` function to work.
    - :exclamation: The Steam credentials are stored in Pterodactyl as plain text—**do NOT use your main account**.
    - _If you do not want to use Steam credentials, set mod downloads to manual and upload mods directly._

### 3. Startup Mods Variable

- The `-mod` and `-serverMod` launch parameters are automatically generated from your `MODIFICATIONS` and `SERVERMODS` egg variables.
- These variables must be **semicolon-separated lists** with correct folder names.
    - Example:
      ```text
      MODIFICATIONS: @cf;@dayzexpansion;@trader;
      SERVERMODS: @servermod;@adminmod;
      ```
- The egg does **not** tolerate mod folders with spaces or uppercase letters in their names.

### 4. Port Assignment

- The **server port and query port are automatically assigned** based on the ports allocated to your server via the Pterodactyl Panel.
- No manual configuration is needed; simply use the values provided in your server details.

---

## Known Issues

- **Mod Folder Lowercase Conversion Not Working:**  
  The `MODS_LOWERCASE` function currently does not convert mod folder/file names to lowercase as intended. Please ensure all mod folders are lowercase before booting the server.
- **Steam Account & 2FA:**  
  Mod downloading from the workshop (`modlist.html` support) **requires** a Steam account with NO Steam Guard/2FA enabled.
- **Do NOT use personal Steam accounts.** Always use a dedicated account for automation.

---

## Quick Setup Steps

1. **Upload the Egg:**  
   Import `egg-day-z-standalone.json` into your Pterodactyl panel.
2. **Configure Variables:**  
   - Set Steam username/password (if mod downloads are needed).
   - Adjust mod lists (`MODIFICATIONS`, `SERVERMODS`).
   - Set any other desired configuration options.
3. **Upload/Configure Mods:**  
   - **Manually ensure all mod folders are lowercase, no spaces.**
   - Place mods in the root directory, or use the `modlist.html` import.
4. **Start the Server:**  
   The server will auto-assign its game and query ports.

---

## Support

For bug reports or support, please contact [BeamHost](https://beamhost.net) or open an issue on our support portal.

---

> **Note:** Always back up your server and mod data before making changes or updates.
