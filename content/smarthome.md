---
title: Smart Home Plan
---

# Smart Home Plan - 55 Murphy Rd

## Design Principles

1. **Physical switches always work** — smart control is secondary, never the only way to operate a light or device
2. **Shelly relays behind the switch** — smart relays install inside the junction box behind a standard momentary switch
3. **Home Assistant is the hub** — all smart devices route through HA for unified control, automation, and HomeKit integration
4. **WiFi on dedicated IoT VLAN** — all smart devices on HAL (VLAN 40, 2.4GHz), isolated from personal and business networks
5. **Zigbee for sensors** — battery-powered sensors use Zigbee mesh (no WiFi dependency, no cloud dependency)

---

## How Shelly + Momentary Switches Work

```
Line (hot) ──→ Shelly Relay ──→ Load (light/fan)
                    ↑
            Momentary switch
            (spring-loaded, returns to center)

Press switch → pulse to Shelly → toggles relay → light on/off
HA / app / voice → command to Shelly → toggles relay → light on/off
WiFi down → switch still toggles Shelly locally → lights always work
```

- Shelly installs behind the switch plate inside the junction box
- Physical switch is a **momentary/retractive rocker** — looks like a normal switch but springs back to center
- Shelly controls the actual relay that powers the light
- HA communicates with Shelly over WiFi for automations, schedules, and remote control
- **No cloud required** — Shelly and HA communicate locally on the LAN

---

## Electrical Requirements for Contractor

These must be communicated to the electrician during rough-in:

- [ ] **Neutral wire in every switch box** — Shelly relays require neutral. Code should mandate this in new construction, but confirm explicitly
- [ ] **Deep junction boxes** — minimum 2.5" depth at all switch locations to fit the Shelly behind the momentary switch
- [ ] **Momentary/retractive rocker switches** — specify at all locations (not standard toggle or decora on/off). These spring back to center position after press
- [ ] **Label all circuits** — contractor to label both ends of every run at panel and switch box
- [ ] **Single-pole home runs** — avoid daisy-chaining switches where possible. Clean home runs make Shelly wiring simpler
- [ ] **3-way circuits** — for hallways/stairs with two switch locations, run both switches to the same box where the Shelly will live, or use Shelly at the fixture with both switches as inputs

---

## Shelly Device Selection

### Recommended Models

| Model | Type | Channels | Price | Use Case |
|-------|------|----------|-------|----------|
| [Shelly Dimmer Gen4 US](https://us.shelly.com/products/shelly-dimmer2) | TRIAC dimmer | 1 | $49.99 | Dimmable overhead lights (RAB wafers) |
| [Shelly 1 Mini Gen3](https://us.shelly.com/products/shelly-1-mini-gen3) | On/off relay | 1 | $12.89 | Non-dimmable circuits (exhaust fans, exterior) |
| [Shelly 2PM Gen3](https://us.shelly.com/collections/relays) | On/off relay | 2 | $15.42 | 2-gang non-dimmable (fan+light combos where fan is separate) |

**Overhead lighting:** All RAB WFRX-6D wafer downlights use TRIAC/ELV dimming at 120V. Every overhead light gets a **Shelly Dimmer Gen4** — no extra dimming wire needed, standard 120V circuit.

**Momentary switch dimming behavior:**
- Short press → toggle on/off (returns to last brightness)
- Long press and hold → ramp brightness up/down
- Release → holds at current level
- HA/app → set any brightness level directly

**Non-dimmable circuits** (exhaust fans, exterior on/off lights, outlets) use the cheaper **Shelly 1 Mini Gen3** relays.

### Per-Location Mapping

| # | Location | Type | Shelly Model | Notes |
|---|----------|------|-------------|-------|
| | **First Floor — Dimmable** | | | |
| 1 | Living Room | Dimmable | Dimmer Gen4 | Overhead RAB wafers |
| 2 | Kitchen Overhead | Dimmable | Dimmer Gen4 | Main ceiling RAB wafers |
| 3 | Kitchen Decorative | Dimmable | Dimmer Gen4 | Pendants / accent |
| 4 | Dining Room | Dimmable | Dimmer Gen4 | Overhead |
| 5 | Dining Decorative | Dimmable | Dimmer Gen4 | Accent / chandelier |
| 6 | Bedroom / Playroom | Dimmable | Dimmer Gen4 | Fan-wired box (fan capped) |
| 7 | Tara's Office | Dimmable | Dimmer Gen4 | |
| 8 | Foyer / Mudroom / Corridor | Dimmable | Dimmer Gen4 | Single zone, possible 3-way |
| 9 | Bedroom | Dimmable | Dimmer Gen4 | Fan-wired box (fan capped) |
| 10 | Bathroom (1st floor) | Dimmable | Dimmer Gen4 | |
| 11 | Bob's Office | Dimmable | Dimmer Gen4 | |
| | **Second Floor — Dimmable** | | | |
| 12 | Primary Bedroom | Dimmable | Dimmer Gen4 | Fan-wired box (fan capped) |
| 13 | Primary Bathroom | Dimmable | Dimmer Gen4 | |
| 14 | Primary Closet | Dimmable | Dimmer Gen4 | |
| 15 | Sitting Room | Dimmable | Dimmer Gen4 | |
| 16 | Bathroom (shared) | Dimmable | Dimmer Gen4 | |
| 17 | Kids Room - Alice | Dimmable | Dimmer Gen4 | Fan-wired box (fan capped) |
| 18 | Kids Room - Bobby | Dimmable | Dimmer Gen4 | Fan-wired box (fan capped) |
| | **Fan Circuits — Capped for Future Use** | | | |
| 19 | Bedroom / Playroom fan | On/off | 1 Mini Gen3 | Wired, capped at ceiling |
| 20 | Bedroom fan | On/off | 1 Mini Gen3 | Wired, capped at ceiling |
| 21 | Primary Bedroom fan | On/off | 1 Mini Gen3 | Wired, capped at ceiling |
| 22 | Kids Room - Alice fan | On/off | 1 Mini Gen3 | Wired, capped at ceiling |
| 23 | Kids Room - Bobby fan | On/off | 1 Mini Gen3 | Wired, capped at ceiling |
| | **Non-Dimmable (On/Off Relay)** | | | |
| 24 | Bathroom fan + vanity (1st floor) | On/off | 2PM Gen3 (Ch1: fan, Ch2: vanity) | 3-gang line voltage box + separate LV box for sensor |
| 25 | Primary Bath fan + vanity | On/off | 2PM Gen3 (Ch1: fan, Ch2: vanity) | 3-gang line voltage box + separate LV box for sensor |
| 26 | Shared Bath fan + vanity | On/off | 2PM Gen3 (Ch1: fan, Ch2: vanity) | 3-gang line voltage box + separate LV box for sensor |
| 27 | Outdoor Bathroom fan + light | On/off | 2PM Gen3 (Ch1: fan, Ch2: light) | 2-gang |
| 28 | Front Porch | On/off | 1 Mini Gen3 | Exterior |
| 29 | Rear Deck | On/off | 1 Mini Gen3 | Exterior |
| 30 | Utility Room | On/off | 1 Mini Gen3 | |
| 31 | Garage | On/off | 1 Mini Gen3 | |
| 32 | Cabana | On/off | 1 Mini Gen3 | |

### Shelly Quantity Summary

| Model | Qty | Unit Price | Total |
|-------|-----|-----------|-------|
| Shelly Dimmer Gen4 US (18 dimmable zones) | 18 | $49.99 | $899.82 |
| Shelly 2PM Gen3 (3 bathrooms + outdoor bath) | 4 | $15.42 | $61.68 |
| Shelly 1 Mini Gen3 (5 fan + 4 on/off) | 9 | $12.89 | $116.01 |
| **Total** | **31** | | **$1,077.51** |

> This is an estimate. Final count depends on the electrical plan (E101/E102/E103) which has not been drawn yet. Some locations may have additional switch legs that would need additional Shellys.

---

## Momentary Switches

**Selected: [Legrand Radiant TM870STM](https://www.legrand.us/wiring-devices/designer-switches-and-outlets/radiant-momentary-contact-switch/p/tm870stmwcc6)** — ~$23 each

| Spec | Detail |
|------|--------|
| Model | TM870STMWCC6 (white) |
| Rating | 15A / 120V |
| Type | Single-pole momentary contact, spring-return |
| Style | Decora / designer rocker |
| Colors | White, black, light almond, ivory |

**Estimated switch cost:** 33 switches (18 dimmable + 5 fan + 10 on/off) × $23 = **~$759**

Available at [Legrand.us](https://www.legrand.us/wiring-devices/designer-switches-and-outlets/radiant-momentary-contact-switch/p/tm870stmwcc6), [Amazon](https://www.amazon.com/TM870STMWCC10-Disposal-Momentary-Decorator-Switches/dp/B001H1EP7K), Walmart, and lighting retailers.

---

## Zigbee Devices (via Home Assistant)

Battery-powered sensors and devices that don't need WiFi. These mesh through each other and communicate through a USB Zigbee coordinator plugged into the HA box.

### Zigbee Coordinator

| Device | Price | Notes |
|--------|-------|-------|
| Sonoff ZBDongle-P (CC2652P) | ~$25 | USB stick, plugs into HA box, Zigbee 3.0 |

### Presence Sensors (PoE — DIY Build)

ESPHome-based presence sensors mounted in junction boxes behind blank plates. mmWave reads through drywall/plastic. PoE-powered from the unmanaged IoT switch in the utility room rack. Cat6A runs from each bathroom to the patch panel.

**BOM per sensor:**

| Component | Price | Source |
|-----------|-------|--------|
| ESP32 PoE board (Olimex ESP32-POE or WT32-ETH01) | ~$18 | |
| HiLink LD2450 mmWave (zone tracking) | ~$7 | |
| HiLink LD2412 mmWave (still presence) | ~$6 | |
| LTR390 light sensor (LUX/UV) | ~$3 | |
| **Per unit total** | **~$34** | |

**Firmware:** ESPHome — reference [Apollo R PRO-1 config](https://github.com/ApolloAutomation/R_PRO-1)

| Qty | Location | Connection |
|-----|----------|-----------|
| 1 | 1st floor bathroom (junction box, blank plate) | PoE via IoT switch |
| 1 | Primary bathroom (junction box, blank plate) | PoE via IoT switch |
| 1 | Shared bathroom (junction box, blank plate) | PoE via IoT switch |

**3 units total: ~$102**

### Zigbee Sensors (Battery — Wireless)

| Device | Qty (est.) | Location | Purpose |
|--------|-----------|----------|---------|
| Leak sensors | 5 | Under kitchen sink, pantry sink, laundry, both water heaters | Water leak detection → HA alert |
| Door/window sensors | 6-10 | Entry doors, garage, select windows | Open/close status for automations |
| Motion sensors (PIR) | 3-5 | Hallways, mudroom, stairs | Automation triggers (auto-lights, passing through) |
| Temperature/humidity | 2-3 | Laundry, utility room | Monitor humidity/temp |

> Zigbee devices are purchased as-needed after HA is set up. No wiring or network ports required.

---

## Smoke / CO Detection

Hardwired interconnected smoke/CO detectors per code. **No smart integration** — standard units.

HA monitors for alarms via a DIY sound detection sensor that listens for the siren tone and triggers notifications/automations (flash lights, send alert, etc.).

**DIY siren listener:**

| Component | Price | Purpose |
|-----------|-------|---------|
| ESP8266 D1 Mini | ~$3 | MCU, WiFi, ESPHome |
| KY-038 sound sensor module | ~$2 | Microphone + analog output |
| **Total** | **~$5** | |

Mount near a smoke detector. ESPHome monitors sound level — spike above threshold triggers HA automation. [Community guide](https://peyanski.com/diy-smart-sound-sensor-for-home-automation/).

## Water Leak Detection & Shutoff

| Device | Model | Qty | Price | Purpose |
|--------|-------|-----|-------|---------|
| Leak sensor | [Aqara Water Leak Sensor](https://www.amazon.com/Aqara-11LM-SJCGQ-Water-Sensor/dp/B07D39MSZS) | 5 | ~$15 ea / ~$75 | Kitchen sink, pantry sink, laundry, both water heaters |
| Shutoff valve | [Aqara Valve Controller T1](https://us.aqara.com/products/valve-controller-t1) | 1 | ~$70 | Main water line — auto-close on leak detection |

Both are Zigbee 3.0 and integrate natively with HA via the Zigbee coordinator. The Aqara Valve Controller T1 clamps onto existing ball valves (DN15/DN20/DN25) — no plumbing changes needed. Also supports Matter over bridge.

**Automation:** Leak sensor triggers → HA closes Aqara valve → sends critical push notification (bypasses DND) → flashes lights.

## Garage Door Openers

| Device | Model | Qty | Price | Purpose |
|--------|-------|-----|-------|---------|
| Controller | [Ratgdo v32](https://ratcloud.llc/products/ratgdo32) | 2 | ~$45 ea | Wired to opener control board, full door control |

Ratgdo wires directly into the garage door opener's logic board. Provides door position (percentage), obstruction sensor status, light control, and lock — all via ESPHome over WiFi on HAL (VLAN 40). No separate door sensor needed.

**Per door:** position tracking, open/close/stop, obstruction alerts, light toggle, lock control.
**Automations:** Auto-close after timeout, phone notification if left open, notify on obstruction.

---

## Smart Appliances (Already Planned)

These are on the IoT VLAN (HAL) and integrate with HA via their respective cloud services or local APIs.

| Device | Connection | Integration |
|--------|-----------|-------------|
| LG HVAC (5 mini-split zones) | WiFi (HAL) | LG ThinQ → HA |
| LG Smart Washer | WiFi (HAL) | LG ThinQ → HA |
| LG Smart Dryer | WiFi (HAL) | LG ThinQ → HA |
| LG Smart Fridge (kitchen) | WiFi (HAL) | LG ThinQ → HA |
| Samsung Fridge (cabana) | WiFi (HAL) | SmartThings → HA |

---

## Home Assistant Setup

| Component | Detail |
|-----------|--------|
| Hardware | **Proxmox VM** on existing hypervisor (10.10.11.20) |
| VM Resources | 2 vCPU, 4GB RAM, 32GB disk (adjust as needed) |
| Network | Wired GbE on VLAN 40 (IoT), via unmanaged PoE switch on core switch port 20 |
| Zigbee | [Sonoff ZBDongle-P](https://www.amazon.com/SONOFF-Universal-Assistant-Zigbee2MQTT-Coordinator/dp/B09KXTCMSC) (~$25) — USB passthrough from Proxmox to HA VM |
| Integrations | Shelly, Scrypted (cameras + doorbells), LG ThinQ, SmartThings, ESPHome |
| Notifications | HA Companion App (iOS/Android) — push via Apple/Google, works remotely |
| Access | Web UI accessible from Home (VLAN 10) and Business (VLAN 20) via firewall rule |

### Doorbell Notifications

Reolink doorbells → Scrypted (10.10.11.201) → Home Assistant → Companion App → phones

| Step | How |
|------|-----|
| Doorbell press | Reolink doorbell sends event via ONVIF to Scrypted |
| Scrypted → HA | Scrypted integration exposes doorbell press as HA event |
| HA automation | Triggers on doorbell event, sends notification with camera snapshot |
| HA → phones | Companion app receives push notification with image via Apple/Google push |

> **Works remotely.** Push notifications are delivered via Apple (iOS) and Google (Android) push services — no VPN required for receiving alerts. Remote dashboard access uses WireGuard VPN to reach HA on its local IP.

### Notification Types

| Event | Notification | Priority |
|-------|-------------|----------|
| Doorbell ring | Snapshot + "Someone at [door name]" | Normal |
| Water leak detected | "Leak detected at [location] — shutting off water" | Critical (bypasses DND) |
| Smoke/CO siren detected | "Alarm sounding — check house" | Critical (bypasses DND) |
| Garage left open | "Garage door open for 15+ min — Close?" (actionable) | Normal |
| Garage obstruction | "Garage door obstruction detected" | High |

---

## Automation Ideas (Post-Install)

- **Arrival/departure** — auto-lock doors, arm cameras, adjust HVAC when everyone leaves
- **Morning routine** — gradually turn on lights at wake time, adjust HVAC
- **Motion-activated lights** — hallways, stairs, mudroom turn on with motion, off after timeout
- **Bathroom fan auto-run** — humidity sensor triggers exhaust fan, auto-off when humidity drops
- **Leak detection** — immediate phone notification + shut off water (if smart valve added later)
- **Bedtime** — all lights off, doors locked, cameras armed, HVAC night mode
- **Laundry done** — notification when washer/dryer cycle completes

---

## Budget Summary

### Contractor-Furnished & Installed

| Category | Cost |
|----------|------|
| Legrand Radiant momentary switches (33) | ~$759 |
| **Contractor total** | **~$759** |

### Owner-Furnished, Contractor-Installed

| Category | Cost |
|----------|------|
| Shelly Dimmer Gen4 US (18 units) | ~$900 |
| Shelly 2PM Gen3 (4 units) | ~$62 |
| Shelly 1 Mini Gen3 (9 units) | ~$116 |
| **Owner-furnished / contractor-installed total** | **~$1,078** |

### Owner-Furnished & Installed (Post-Construction)

| Category | Cost |
|----------|------|
| DIY presence sensors (3x ESP32+mmWave) | ~$102 |
| Sonoff ZBDongle-P (Zigbee coordinator) | ~$25 |
| Aqara Water Leak Sensors (5) | ~$75 |
| Aqara Valve Controller T1 (water shutoff) | ~$70 |
| Ratgdo v32 (2x garage doors) | ~$90 |
| DIY siren listener (ESP8266 + KY-038) | ~$5 |
| **Owner total (post-construction)** | **~$367** |

### Smart Home Summary

| Category | Responsibility | Cost |
|----------|---------------|------|
| Momentary switches (33) | Contractor furnished + installed | ~$759 |
| Shelly devices (31) | Owner furnished, contractor installed | ~$1,078 |
| Sensors, shutoff valve, garage, HA | Owner furnished + installed | ~$367 |
| **Grand total smart home** | | **~$2,204** |

> This is separate from the networking budget ($3,175). Smart home devices are owner-provided and installed after construction is complete.

---

## Open Decisions

- [x] ~~Momentary switch brand/model~~ — Legrand Radiant TM870STM (~$23 ea)
- [x] ~~Smart locks~~ — standard deadbolts, no smart integration
- [x] ~~Smart garage door~~ — Shelly 1 Mini Gen3 wired to opener relay
- [x] ~~Smoke/CO~~ — hardwired standard, HA listens for siren via microphone
- [x] ~~Home Assistant hardware~~ — Proxmox VM on existing hypervisor
- [x] ~~Zigbee sensors~~ — Aqara ecosystem (leak sensors, valve controller, door sensors)
- [x] ~~Smart water shutoff~~ — Aqara Valve Controller T1
- [x] ~~Siren detection~~ — DIY ESP8266 + KY-038 sound sensor
- [ ] Confirm Shelly count after electrical plans (E101/E102/E103) are finalized
- [ ] Motorized window shades (TBD — if yes, need power in header during framing)
- [ ] EV charger smart integration (VLAN 40)
