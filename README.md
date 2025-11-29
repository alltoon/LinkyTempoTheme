# 🎨 Linky Tempo Theme for Home Assistant

[![French Version](https://img.shields.io/badge/Documentation-Français-blue?style=for-the-badge&logo=france)](README_fr.md)
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

A lightweight theme designed specifically for the Home Assistant **Energy Dashboard**. It replaces the default graph colors with the official color code of the **EDF Tempo** offer (Blue, White, Red).

![Dashboard Preview](https://github.com/alltoon/LinkyTempoTheme/raw/main/preview.png)

## What this theme does

This theme does not change the overall appearance of your Home Assistant (which remains light or dark according to your preferences). It only acts on:

1.  **The Energy Dashboard palette:** The first 6 electricity sources take the exact colors of Tempo (Off-Peak/Peak Blue, White, Red).
2.  **The theme is not magic:** It complements the LinkyTempo integration: `https://github.com/alltoon/LinkyTempo`

## Installation

### Option 1: Via HACS (Recommended)

1.  Open **HACS** in Home Assistant.
2.  Go to the **Frontend** tab.
3.  Click on the menu (3 dots in the top right) > **Custom repositories**.
4.  Add the URL of this repository: `https://github.com/alltoon/LinkyTempoTheme`.
5.  Category: **Theme**.
6.  Click "Add", search for "Linky Tempo Theme" in the list and install it.

### Option 2: Manual

1.  Create a `linky_tempo.yaml` file in the `themes/` folder of your Home Assistant configuration.
2.  Copy the content of the `themes/linky_tempo.yaml` file from this repository into it.

## Activation

For Home Assistant to take the theme into account, you must follow these two steps:

### 1. Declare the themes folder
Open your `/config/configuration.yaml` file and make sure these lines are present:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

***Note:*** If you have just added this line, restart Home Assistant.

### 2. Select the theme

Each user must activate the theme on their profile:

- Click on your Username (at the bottom left of the sidebar).

- In the Theme section, **select** Linky Tempo Theme.

## Energy Dashboard Configuration (VERY IMPORTANT)

The Energy Dashboard assigns colors in the order the sources arrive (the 1st source takes color 1, the 2nd takes color 2, etc.).

For the colors to match the correct tariff periods, you must strictly follow this order of addition:

1. Go to Settings > Dashboards > Energy.

2. In the "Electricity grid" section, delete your current sources (trash can icon).

Add them again one by one in this precise order:

| Order | Sensor to add                | Color that will be displayed |
|-------|------------------------------|------------------------------|
| 1     | 🔵 `..._bleu_heures_creuses`   | Dark Blue                    |
| 2     | 🔵 `..._bleu_heures_pleines`   | Light Blue                   |
| 3     | ⚪️ `..._blanc_heures_creuses`  | Gray / White                 |
| 4     | ⚪️ `..._blanc_heures_pleines`  | Light Gray                   |
| 5     | 🔴 `..._rouge_heures_creuses`  | Dark Red                     |
| 6     | 🔴 `..._rouge_heures_pleines`  | Light Red                    |

Refresh your page `(F5)` or `(cmd + R)`. Your graphs are now in Tempo colors! 🎉

## Links

Designed for the integration: [Linky Tempo](https://github.com/alltoon/LinkyTempo) for Home Assistant.
