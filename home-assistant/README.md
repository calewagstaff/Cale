# Buckeye Home (Home Assistant dashboard)

A dark, phone-first dashboard with scarlet accents, built for this house's real devices.

**Needs, from HACS → Frontend:** [Mushroom](https://github.com/piitaya/lovelace-mushroom) and [card-mod](https://github.com/thomasloven/lovelace-card-mod).

| Tab | What's on it |
|---|---|
| **Home** | Greeting with how many lights are on and the back door status, status chips, quick actions (All off, Lock door, Talk, Type), an **On now** list that shows only what's on, and a card for each of the 14 rooms |
| **Rooms** | Every control grouped by room: dimmers, fan speeds, TVs, switches and the back door lock |
| **More** | Internet, iPhone battery, lock battery and keypad, an **Offline devices** list, and the assistant |

## How to use it

- **Room cards (Home):** tap to turn that room's lights on or off. Hold to open the Rooms tab. Each card shows live status, like `78%`, `2 of 3 on` or `Light on · Fan 66%`, and lights up scarlet when anything in the room is on.
- **Tiles (Rooms):** tap to toggle, slide to dim or change fan speed, hold for details.
- **On now:** a one-tap way to turn off whatever's on. It hides itself when everything is off.
- **Offline devices:** appears on the More tab only when something drops off the network.

## What changed from the previous version

- 17 tabs became 3. The 14 single-room pages are gone, because most held a single switch. Room cards now act directly, and the Rooms tab has every detailed control on one page.
- One style block per tab themes every card inside it, instead of a separate `card_mod` on each card.
- The custom bottom nav bar is gone. Home Assistant's own tabs stay visible at the top of every page.
- Live status on every room card, plus the **On now** and **Offline devices** lists.

## Install

1. Make sure Mushroom and card-mod are installed.
2. Open the dashboard and go to **✏️ Edit → ⋮ → Raw configuration editor**. Replace everything there with [`dashboard.yaml`](dashboard.yaml), then **Save**.

## Changing it

- **Accent color:** find-and-replace `#e51c32`, and `229, 28, 50` (the same color in RGB).
- **Add a light to the All off button and the light count:** add it to the `entity_id` list under **All off**, and to the `lights` list in the greeting at the top.
- **Add a device to On now / Offline devices:** add it to that card's `entities` list.
