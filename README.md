# CARLA VR for ARHUD

---

## Overview

This repository extends the [CARLA Driving Simulator](https://carla.org/) (v0.10.0) with a Virtual Reality interface, enabling immersive driving experiments. 
The module is structured as a self-contained submodule to ensure modularity and prevent conflicts with the base CARLA installation.

---

> **Note:** The following folders are excluded from this repository for size or licensing reasons and must be sourced separately (see [Excluded Assets](#excluded-assets)):
> - `Config-build`
> - `Config`
> - `Localization`
> - `Material`
> - `Textures`

---

## Requirements

- Follow Carla Build instructions https://carla-ue5.readthedocs.io/en/latest/build_windows_ue5/
- The following plugins must be installed in your UE5.5 project:

| Plugin | Source |
|---|---|
| OpenXR | Built-in UE5 plugin — enable in Plugins menu |
| Joystick Plugin | [github.com/JaydenMaalouf/JoystickPlugin](https://github.com/JaydenMaalouf/JoystickPlugin) |
| Actuate Motion Scripts | Available via Marketplace / manual install |
| Meta VR Plugin | Meta Developer Portal |
| VR Starter Package | Epic Games Marketplace |

---

## Installation

### 1. Clone as submodule into CARLA

```bash
cd <CARLA_ROOT>/Unreal/CarlaUnreal/Content/Carla/
git submodule add https://github.com/LeonardoVezzani/Carla_ARHUD_VR.git CarlaVR
git submodule update --init --recursive
```

### 2. Install plugins

Clone or copy each required plugin into your UE5.5 project's `Plugins/` folder, then re-generate project files:

```bash
# Example for JoystickPlugin
git clone https://github.com/JaydenMaalouf/JoystickPlugin.git <UE_PROJECT>/Plugins/JoystickPlugin
```

Enable all plugins from **Edit → Plugins** in the Unreal Editor.

### 3. Add the experiment map

For full paper experiment replication, download the map from:

> [FAB Marketplace — Map Asset](https://www.fab.com/listings/4898e707-7855-404b-af0e-a505ee690e68)

Place it under:

```
<CARLA_ROOT>/Unreal/CarlaUnreal/Content/Carla/Map/
```

---

## Rendering Configuration

For stable VR performance, apply the following settings in **Project Settings → Rendering**:

- ✅ Enable **Virtual Textures** (`r.VT.Enable=1`)
- ⬇️ Lower **Texture Resolution** as needed
- ⬇️ Reduce **LOD Pool Size** (`r.MaxAnisotropy=4`, reduce `r.FoliageFarCull`)
- 🎮 Set rendering quality to **Medium** or **High** depending on your GPU

Recommended baseline: `sg.PostProcessQuality=1`, `sg.ShadowQuality=1`, `sg.TextureQuality=1`.
Tweak as needed.
---

## Launch

Once the repo is cloned and plugins are installed, open the VR entry level:

```
/Game/Carla/CarlaVR/VR_MainMenu/VR_MainMenu_Level
```

Press **Play in VR Preview** or package the project for standalone VR execution.
Make sure parameters passed from the menu to the Game Mode are actually present in the indicated folders.

---

---

## License

To be determined upon paper acceptance. All rights reserved in the interim.
