# Buckeye Home (Home Assistant dashboard)

A dark dashboard with scarlet accents. Each tab is a full-width panel wrapped in a `custom:mod-card`, and the cards rearrange into 1 to 4 columns to fit a phone, tablet or wall panel.

**Needs [card-mod](https://github.com/thomasloven/lovelace-card-mod)**: in HACS go to **Frontend**, search for card-mod, download it, and reload the browser.

| Tab | What's on it |
|---|---|
| **Home** | Who's home, weather, Good morning / Good night buttons, the lights you use most, the thermostat, locks, garage and alarm |
| **Lights** | Every light, grouped by room, with brightness sliders on the main ones |
| **Climate** | Thermostat with mode and fan buttons, room temperatures, a 24-hour graph, fans |
| **Security** | Locks, garage, alarm keypad, door and window sensors, camera feeds |
| **Media** | TV remote, speaker volume sliders |

Tap a section heading on the Home tab to jump to its full tab.

## Install (about 5 minutes)

1. **Make the dashboard.** In Home Assistant go to **Settings → Dashboards → + Add dashboard → New dashboard from scratch**. Name it `Home` and set the URL to `dashboard-home`. (The heading links use that URL. If you pick a different one, find-and-replace `/dashboard-home/` in the file.)
2. **Paste the YAML.** Open the new dashboard, click **✏️ (Edit) → ⋮ → Raw configuration editor**, delete what's there, paste in all of [`dashboard.yaml`](dashboard.yaml), and click **Save**.
3. **Use your own devices.** The file uses example names like `light.kitchen`. Any card showing a yellow "Entity not available" box needs its name changed:
   - Find your real names under **Settings → Devices & services → Entities**.
   - Change them in the raw editor (find-and-replace is quickest), or click the card in edit mode and pick the right device from the list.
   - Delete cards for things you don't have, such as an alarm or cameras.
4. **Optional extras.** [`helpers.yaml`](helpers.yaml) contains the **Good morning** and **Good night** scripts, the **All lights** group, and the "lights on" counter. Copy each part into `configuration.yaml` / `scripts.yaml`, then restart Home Assistant. Or leave them out and delete those cards.

## Example names to replace

| Kind | Example names in the file |
|---|---|
| People | `person.cale`, `person.partner` |
| Weather | `weather.forecast_home` (the default weather integration; usually right as-is) |
| Lights | `light.living_room`, `light.living_room_lamp`, `light.tv_backlight`, `light.kitchen`, `light.kitchen_island`, `light.under_cabinet`, `light.bedroom`, `light.kids_room`, `light.nightlight`, `light.porch`, `light.backyard`, `light.driveway` |
| Switches | `switch.coffee_maker` |
| Climate | `climate.thermostat`, `fan.bedroom_fan`, `fan.living_room_fan` |
| Temperature sensors | `sensor.indoor_temperature`, `sensor.indoor_humidity`, `sensor.outdoor_temperature`, `sensor.living_room_temperature`, `sensor.bedroom_temperature`, `sensor.kids_room_temperature` |
| Security | `lock.front_door`, `lock.back_door`, `cover.garage_door`, `alarm_control_panel.home_alarm` |
| Door/motion sensors | `binary_sensor.front_door`, `binary_sensor.back_door`, `binary_sensor.garage_side_door`, `binary_sensor.living_room_window`, `binary_sensor.hallway_motion` |
| Cameras | `camera.front_door`, `camera.backyard` |
| Media | `media_player.living_room_tv`, `media_player.kitchen_speaker`, `media_player.bedroom_speaker` |
| From `helpers.yaml` | `light.all_lights`, `sensor.lights_on_count`, `script.good_morning`, `script.good_night` |

## Tips

- **Make it the default:** in **Settings → Dashboards**, select it and choose **Set as default**, so it opens first on every device.
- **Rearrange cards:** move whole sections up or down in the YAML. Order on screen follows the file.
- **Wall tablet:** open the Home Assistant app in kiosk or full-screen mode.
- Requires Home Assistant 2025.1 or newer, plus card-mod.
- Colors live in the `card_mod` block at the top of each tab. Change `#bb0000` to change the accent.
