# Home Assistant Blueprints for Ava Pro

Welcome to my Home Assistant blueprints repository!

The following custom Home Assistant blueprints have been created for [Ava Pro](https://github.com/knoop7/Ava) Android voice assistant (check out the [Ava Wiki](https://github.com/knoop7/Ava/wiki) for hardware details and configuration).

These blueprints add the missing functionality found in commercial systems, such as music control, alarms, TODO lists and weather reports, without needing to write complex Jinja2 templates or YAML automations from scratch.

##### **Prerequisites**

Alarms are provided via a separate integration, [Voice Alarms](https://github.com/lone-baggie/voice_alarms). Music control is provided by Music Assistant. Weather reports require a valid weather entity. TODO lists use the standard Home Assistant integration. Most of the blueprints have an optional HTML entry to allow display information on screen if available. I have created a number of [HTML pages](https://github.com/lone-baggie/HTML-views-for-Home-assistant) designed for screens 8” and over.

##### Note

All these blueprints rely on the fact the default naming convention is unchanged on the AVA devices. It must be in the format **domain.device name_entity name** . For Music Assistant playback, the native media player must be disabled in settings.

For example, if the AVA device is called **'portal':**

| Device name | entity name |
| :---- | :---- |
| Physical volume | sensor.portal_physical_volume |
| Browser Display | switch.portal_browser_display |
| Media Player | media_player.portal |

---

## 📋 Blueprint Overview

| Blueprint | Category | Description | Quick Import |
| :---- | :---- | :---- | :---- |
| [**AVA Display the time**](#1-ava-display-the-time) | Display | Displays a clock html via voice control | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Display%2520the%2520time.yaml) |
| [**AVA Read Weather forecast**](#2-ava-read-weather-forecast) | Weather / Voice | Read daily weather forecast, temperature and rain summaries. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Read%2520Weather%2520forecast.yaml) |
| [**AVA Reset when stuck**](#3-ava-reset-when-stuck) | Maintenance | Watchdog blueprint that safely reboots/resets the device if non-responsive. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Reset%2520when%2520stuck.yaml) |
| [**AVA Screen Manager**](#4-ava-screen-manager) | Display | Controls the AVA display screen savers and active browser display. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Screen%2520Manager.yaml) |
| [**AVA Sync Volume Manager**](#5-ava-sync-volume-manager) | Media | Synchronises music assistant media volume with physical volume | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Sync%2520Volume%2520Manager.yaml) |
| [**AVA Todo**](#6-ava-todo) | Utility | Displays and interacts with Home Assistant `todo` list items. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Todo.yaml) |
| [**AVA Touch Trigger html**](#7-ava-touch-trigger-html) | Display / Utility | Triggers HTML display actions via touch events on AVA device. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Touch%2520Trigger%2520html.yaml) |
| [**AVA Turn on screensaver**](#8-ava-turn-on-screensaver) | Display | Triggers screensaver mode via voice control | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Turn%2520on%2520screensaver.yaml) |
| [**AVA display alarm**](#9-ava-display-alarm) | Alarm / Utility | Shows active alarm information on-screen. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520display%2520alarm.yaml) |
| [**AVA music assistant**](#10-ava-music-assistant) | Media | Deep integration with Music Assistant (MASS) for playback & navigation. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520music%2520assistant.yaml) |
| [**Auto ducking volume**](#11-auto-ducking-volume) | Audio / Media | Automatically lowers volume on devices in the same area. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAuto%2520ducking%2520volume.yaml) |
| [**AVA LLM Music Assistant**](#12-ava-llm-music-assistant) | LLM / Media | LLM-assisted integration for Music Assistant playback and control. | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FLLM%2FAVA%2520LLM%2520Music%2520Assistant.yaml) |
| [**AI Search Assist**](#13-ai-search-assist) | LLM / Search | LLM-assisted Internet search tool | [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FLLM%2FAI%2520Search%2520Assist.yaml) |

---

## 🛠️ Blueprints

---

### 1. AVA Display the time

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Display%2520the%2520time.yaml)

**File Path:** `AVA Display the time.yaml`

#### Description

Displays the HTML page via voice control.

---

### 2. AVA Read Weather forecast

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Read%2520Weather%2520forecast.yaml)

**File Path:** `AVA Read Weather forecast.yaml`

#### Description

Pulls daily forecast data from your Home Assistant weather entity and formats it for voice readouts or display via HTML.

#### Features

* Compatible with standard `weather` entities (e.g., Met.no, OpenWeatherMap).  
* Formats temperature, precipitation probability, and general conditions into clean text.

---

### 3. AVA Reset when stuck

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Reset%2520when%2520stuck.yaml)

**File Path:** `AVA Reset when stuck.yaml`

#### Description

A lightweight watchdog automation that monitors connectivity and state updates from Ava. If the device hits an unresponsive state, it issues a graceful reset sequence.

#### Features

* Configurable timeout threshold before triggering recovery.  
* Issues soft reboot

---

### 4. AVA Screen Manager

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Screen%2520Manager.yaml)

**File Path:** `AVA Screen Manager.yaml`

#### Description

Manages browser timeout delays and screensaver

---

### 5. AVA Sync Volume Manager

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Sync%2520Volume%2520Manager.yaml)

**File Path:** `AVA Sync Volume Manager.yaml`

#### Description

Ensures physical volumes are synced to the Music Assistant mediaplayer before music is played.

#### Features

* Requires a physical volume sensor to be present.

---

### 6. AVA Todo

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Todo.yaml)

**File Path:** `AVA Todo.yaml`

#### Description

Home Assistant `to do` list management. Can also display list on screen

#### Features

* Integrates directly with native Home Assistant To-Do lists.  
* Allows adding and item removal.  
* Option to delete the entire list.

---

### 7. AVA Touch screen

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Touch%2520screen%25220.yaml)

**File Path:** `AVA Touch screen.yaml`

#### Description

Uses the screen saver switch as a trigger. If screen saver turned off , it will trigger the quick entry screen on.

---

### 8. AVA Turn on screensaver

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520Turn%2520on%2520screensaver.yaml)

**File Path:** `AVA Turn on screensaver.yaml`

#### Description

Simply turns on the screensaver by voice. Useful when amending device and need to turn the screensavwe back on.

---

### 9. AVA display alarm

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520display%2520alarm.yaml)

**File Path:** `AVA display alarm.yaml`

#### Description

Displays upcoming alarm times. Require [voice alarms](https://github.com/lone-baggie/voice_alarms)

---

### 10. AVA music assistant

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAVA%2520music%2520assistant.yaml)

**File Path:** `AVA music assistant.yaml`

#### Description

Voice control for **Music Assistant** integration in Home Assistant.

#### Features

* Play music by song, artist, album or radio  
* volume control  
* Jump track forward and backwards  
* Play on remote speaker

---

### 11. Auto ducking volume

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FAuto%2520ducking%2520volume.yaml)

**File Path:** `Auto ducking volume.yaml`

#### Description

Automatically dips (ducks) the background audio volume on playing media players in the same area as the AVA device. It also allows another area to be added to allow portable speakers to be included.

---

### 12. AVA LLM Music Assistant

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FLLM%2FAVA%2520LLM%2520Music%2520Assistant.yaml)

**File Path:** `LLM/AVA LLM Music Assistant.yaml`

#### Description

An LLM-assisted version of the AVA Music Assistant blueprint, providing natural language processing for queries and commands related to Music Assistant playback.

---

### 13. AI Search Assist

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flone-baggie%2Fhome-assistant-blueprints%2Fblob%2Fmain%2FLLM%2FAI%2520Search%2520Assist.yaml)

**File Path:** `LLM/AI Search Assist.yaml`

#### Description

An LLM-assisted internet search tool.

---

## 🚀 How to Install

### Option 1: Automatic 1-Click Import (Recommended)

Click any of the **Import Blueprint** badges above. Home Assistant will open the import wizard with the exact blueprint raw path pre-filled.

### Option 2: Manual URL Import

1. In Home Assistant, go to **Settings** -> **Automations & Scenes** -> **Blueprints**.  
2. Click **Import Blueprint** in the bottom right corner.  
3. Paste the URL of the file from this repository.  
4. Click **Import Blueprint**.

---

## 🐞 Issues & Contributions

Found a bug or have a suggestion for improving these blueprints? Please open an issue or submit a pull request on the [GitHub Repository](https://github.com/lone-baggie/home-assistant-blueprints/issues).

---

*Created with ❤️ for the Home Assistant Community.*
