---
title: Networking Requirements
---

# Networking Requirements - 55 Murphy Rd

## VLAN Architecture

| VLAN ID | Name       | Subnet          | Purpose                                      |
|---------|------------|-----------------|----------------------------------------------|
| 1       | Management | 10.10.10.0/24   | Switch/AP management, UCG-Ultra               |
| 10      | Home       | 10.10.10.0/24   | Personal devices, phones, tablets, streaming   |
| 20      | Business   | 10.10.20.0/24   | Bob's office, Tara's office, datacenter gear   |
| 30      | Cameras    | 10.10.30.0/24   | PoE cameras only, isolated, no internet        |
| 40      | IoT        | 10.10.40.0/24   | Home Assistant, smart devices, HVAC controls   |
| 50      | Datacenter | 10.10.11.0/24   | Existing server infrastructure (migrate later) |
| 60      | Guest      | 10.10.60.0/24   | Internet-only, no access to any internal VLAN (solar hub, guest WiFi) |
| 70      | Internal   | 10.10.70.0/24   | No internet, local-only (printers, etc.)       |

> **Note:** Datacenter VLAN keeps existing 10.10.11.0/24 subnet to avoid re-addressing all servers. Can be migrated to 10.10.50.0/24 later.

---

## Speed Requirements

- **All wired devices:** 2.5 GbE minimum
- **Cable standard:** Cat6A (future-proofs all runs)

---

## Existing Equipment (Reuse)

| Device                        | Model        | Role                  | Ports / Specs              |
|-------------------------------|-------------|----------------------|----------------------------|
| Ubiquiti Cloud Gateway Ultra  | UCG-Ultra   | Router / Controller  | 1x WAN, 1x LAN (GbE) - **bottleneck, see note** |
| Ubiquiti U6+ AP               | U6+         | Indoor WiFi 6        | 1x GbE PoE, 2x2 dual-band |
| Ubiquiti U7 Outdoor           | U7-Outdoor  | Exterior WiFi 7      | 1x 2.5GbE PoE              |
| Ubiquiti U7 In-Wall           | U7-IW       | In-wall WiFi 7       | 1x 2.5GbE uplink + 4x GbE switch |
| TP-Link unmanaged switches    | Various     | **REPLACING** - no VLAN support, no 2.5GbE |       |

> **UCG-Ultra note:** The UCG-Ultra LAN port is only 1 GbE. It will bottleneck inter-VLAN routing at gigabit. Consider upgrading to a [Cloud Gateway Max](https://store.ui.com/us/en/products/ucg-max) (2.5GbE) or [Dream Machine Pro Max](https://store.ui.com/us/en/products/udm-pro-max) (10GbE + 2.5GbE) to match the 2.5G/10G switching fabric.

---

## Equipment Needed (New Purchases)

### Core Switch - Utility Room (1U rack mount)

**Recommended: [UniFi Switch Pro Max 24 PoE](https://store.ui.com/us/en/products/usw-pro-max-24-poe)** — $799

| Spec              | Detail                                                    |
|-------------------|-----------------------------------------------------------|
| Ports             | 8x 2.5GbE PoE++ + 16x GbE (8 PoE+, 8 PoE++)             |
| Uplinks           | 2x 10G SFP+                                               |
| PoE Budget        | 400W                                                       |
| Switching         | 112 Gbps, Layer 3                                          |
| Features          | Etherlighting, VLAN, IGMP, RSTP, LAG                       |

The 8x 2.5GbE ports handle your high-speed wired drops (offices, APs, trunk to garage, servers). The 16x GbE ports handle cameras and lower-speed devices. SFP+ uplink connects to the gateway.

### Garage / Cabana Switch

**Recommended: [UniFi Switch Flex 2.5G PoE](https://store.ui.com/us/en/products/usw-flex-2-5g-8-poe)** — $199

| Spec              | Detail                                                    |
|-------------------|-----------------------------------------------------------|
| Ports             | 8x 2.5GbE PoE++                                           |
| Uplink            | 1x 10GbE RJ45/SFP+ combo                                  |
| Form Factor       | Compact, can be powered by PoE+++ or AC adapter            |

All 8 ports are 2.5GbE with PoE++ — handles cameras, outdoor AP, and cabana drops at full speed. The 10G combo uplink future-proofs the trunk run from the utility room.

### Additional Access Point

**Recommended: [UniFi U7 Pro](https://store.ui.com/us/en/products/u7-pro)** — $189

| Spec              | Detail                                                    |
|-------------------|-----------------------------------------------------------|
| WiFi              | WiFi 7, tri-band (2.4 + 5 + 6 GHz)                        |
| Streams           | 6 spatial streams, 9.3 Gbps aggregate                      |
| Uplink            | 2.5GbE PoE                                                 |
| Capacity          | 300+ concurrent devices                                    |

Place on 2nd floor for full-house coverage. The existing U6+ (GbE only) can be repositioned or kept as a backup.

### Network Rack

**Utility room cavity:** 2'5" deep (29") × 2'7" wide (31") with 4' additional pull-out space for rear access.

**Selected: [StarTech 4POSTRACK42](https://www.amazon.com/StarTech-com-4-Post-42U-Mobile-Open-Frame-Server-Rack/dp/B00HVKOPBW)** — ~$356

| Spec              | Detail                                                    |
|-------------------|-----------------------------------------------------------|
| Size              | 42U, 20.5" wide frame, 6'7" tall                          |
| Depth             | Adjustable 22" - 40" (set to ~22" for cavity fit)          |
| Capacity          | 1,320 lbs                                                  |
| Mobility          | Casters included — rolls in/out of cavity                  |
| Ceiling clearance | 6'7" rack in 8' ceiling = 17" clearance                    |
| Standard          | EIA-RS-310C compliant, 19" rack mount                      |

**Cavity fit:** 20.5" frame in 31" opening = 5" clearance per side for cable runs. Rails set to ~22" keeps the frame under 29" deep. Roll out into the 4' pull space (6'5" total) for rear access and servicing.

**Rack layout (42U):**

```
┌──────────────────────────────────────────────────┐
│ U1  │ 24-port Cat6A Keystone Patch Panel         │ 1U
├─────┼────────────────────────────────────────────┤
│ U2  │ UniFi Pro Max 24 PoE (Core Switch)         │ 1U
├─────┼────────────────────────────────────────────┤
│ U3  │ 1U Shelf: UCG-Ultra Gateway                │ 1U
├─────┼────────────────────────────────────────────┤
│ U4  │ 1U Shelf: Solar Panel Hub                   │ 1U
├─────┼────────────────────────────────────────────┤
│ U5  │░░░░░░░░ AIRFLOW GAP ░░░░░░░░░░░░░░░░░░░░░│ 1U
├─────┼────────────────────────────────────────────┤
│ U6  │ 1U Shelf: GMKTEC K12 (Hub) + OWC Drive    │ 1U
├─────┼────────────────────────────────────────────┤
│ U7  │                                            │
│ U8  │                                            │
│ U9  │                                            │
│ U10 │                                            │
│ U11 │     SPARE (9U)                             │
│ U12 │                                            │
│ U13 │                                            │
│ U14 │                                            │
│ U15 │                                            │ 9U
├─────┼────────────────────────────────────────────┤
│ U16 │                                            │
│ U17 │     (6U clearance for Proxmox R5)          │
│ U18 │     Ryzen 5 5600X / 64GB / RTX 2070S       │
│ U19 │                                            │
│ U20 │                                            │
│ U21 │                                            │ 6U
├─────┼────────────────────────────────────────────┤
│ U22 │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│ U23 │▓▓ 2U Shelf ── Proxmox (R5 on side) ▓▓▓▓▓▓│ 2U  (lightest)
├─────┼────────────────────────────────────────────┤
│ U24 │                                            │
│ U25 │     (6U clearance for TrueNAS R5)          │
│ U26 │     Ryzen 7 5800XT / 32GB / HBA            │
│ U27 │                                            │
│ U28 │                                            │
│ U29 │                                            │ 6U
├─────┼────────────────────────────────────────────┤
│ U30 │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│ U31 │▓▓ 2U Shelf ── TrueNAS (R5 on side) ▓▓▓▓▓▓│ 2U  (mid)
├─────┼────────────────────────────────────────────┤
│ U32 │                                            │
│ U33 │     (6U clearance for Unraid R5)           │
│ U34 │     Ryzen 5 3600 / 32GB / RX 5500          │
│ U35 │                                            │
│ U36 │                                            │
│ U37 │                                            │ 6U
├─────┼────────────────────────────────────────────┤
│ U38 │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│ U39 │▓▓ 2U Shelf ── Unraid (R5 on side) ▓▓▓▓▓▓▓│ 2U  (heaviest)
├─────┼────────────────────────────────────────────┤
│ U40 │░░░░░░░░ AIRFLOW GAP ░░░░░░░░░░░░░░░░░░░░░│ 1U
├─────┼────────────────────────────────────────────┤
│ U41 │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│ U42 │▓▓ 2U Shelf ── EcoFlow Delta 3 + UPS #1 ▓▓│ 2U  (heaviest)
└─────┴────────────────────────────────────────────┘
```

**Power chain:**
- Wall: **dedicated 20A quad receptacle on its own circuit** behind the rack cavity (standard for all racks)
- EcoFlow Delta 3 + Amazon Basics UPS #1 (U41-42, bottom shelf)
- EcoFlow → power strip → switch, gateway, Hub
- Amazon Basics → TrueNAS, Proxmox, Unraid

**Shelf accessories:**

| Item | Qty | Est. Cost | Link |
|------|-----|-----------|------|
| NavePoint 2U Heavy Duty Vented Cantilever Shelf (18" deep) | 4 | ~$30 ea | [NavePoint](https://navepoint.com/navepoint-2u-heavy-duty-vented-cantilever-shelf-18-460mm-deep/) |
| NavePoint 1U Shelf (for GMKTEC + small gear) | 1 | ~$20 | [NavePoint](https://navepoint.com/19-inch-cantilever-shelf-1u-with-14-depth-ral9003-signal-white/) |

Each 2U shelf holds 110 lbs — R5 loaded is ~25 lbs, well within capacity.

### Cable & Termination

| Item                          | Qty  | Est. Cost  |
|-------------------------------|------|------------|
| Cat6A bulk cable (1000ft)     | 2    | ~$180 ea   |
| 24-port Cat6A keystone patch panel | 1 | ~$40      |
| Cat6A keystone jacks          | 50   | ~$60       |
| 2-gang wall plates            | 12   | ~$25       |
| 1-gang wall plates            | 10   | ~$15       |
| Cat6A patch cables (various)  | 30   | ~$50       |

> Upgraded from Cat6 to **Cat6A** to support 10GbE on all runs. Marginal cost increase, significant future-proofing.

---

## Camera VLAN (VLAN 30) - 7 Cameras (+1 spare port)

| #  | Location              | Model                        | Type     | PoE  | Cable Run To  | Est. Cost |
|----|-----------------------|------------------------------|----------|------|---------------|-----------|
| 1  | Front door            | [Reolink Video Doorbell PoE](https://reolink.com/us/product/reolink-video-doorbell-poe/) | Doorbell | Yes | Utility room | $110 |
| 2  | Back door             | [Reolink Video Doorbell PoE](https://reolink.com/us/product/reolink-video-doorbell-poe/) | Doorbell | Yes | Utility room | $110 |
| 3  | Mudroom door          | [Reolink Video Doorbell PoE](https://reolink.com/us/product/reolink-video-doorbell-poe/) | Doorbell | Yes | Utility room | $110 |
| 4  | Pool area             | [Reolink RLC-811A](https://reolink.com/product/rlc-811a/) (4K bullet, 5x zoom) | Exterior | Yes | Utility room | $122 |
| 5  | Side of house         | Reolink RLC-810A (4K bullet, 4mm) | Exterior | Yes | Utility room | *owned* |
| 6  | Garage interior       | [Reolink RLC-1240A](https://reolink.com/product/rlc-1240a/) (12MP dome, 121° FOV) | Interior | Yes | Garage switch | $140 |
| 7  | Cabana interior       | [Reolink RLC-520A](https://reolink.com/product/rlc-520a/) (5MP dome) | Interior | Yes | Garage switch | $47  |
| 8  | Front yard / driveway | [Reolink RLC-811A](https://reolink.com/product/rlc-811a/) (4K bullet, 5x zoom) | Exterior | Yes | Utility room | $122 |

**Camera total: $761** (8 cameras, 1 owned)

**Camera PoE port count:** 6 on core switch + 2 on garage switch = 8 used

**Reolink camera specs:**

| Model | Resolution | Night Vision | Weather | Detection | Audio |
|-------|-----------|-------------|---------|-----------|-------|
| Video Doorbell PoE | 5MP (2K+) | IR, 180° diagonal | IP65 | Person/package | Two-way |
| RLC-810A | 8MP (4K) | 100ft IR | IP67 | Person/vehicle/animal | Recording |
| RLC-811A | 8MP (4K) | 100ft IR + color spotlight | IP67 | Person/vehicle/animal | Two-way + siren |
| RLC-520A | 5MP | 100ft IR | IP67 | Person/vehicle/animal | Recording |
| RLC-1240A | 12MP | 100ft IR + color spotlight | IP67/IK10 | Person/vehicle/animal | Two-way |

**Firewall rules:** VLAN 30 blocked from internet. Allow VLAN 30 -> Scrypted (10.10.11.201) only.

> All cameras are PoE (802.3af) and work with Scrypted for HomeKit/Home Assistant integration. No Reolink NVR needed — Scrypted handles recording and smart detection.

---

## Business VLAN (VLAN 20) - Wired Drops

| Location           | Floor | Drops | Devices                              |
|--------------------|-------|-------|--------------------------------------|
| Bob's Office       | 1st   | 2     | Workstation, VoIP/printer             |
| ~~Tara's Office~~  | ~~2nd~~| ~~2~~ | *Moved to Home VLAN*                   |
| Utility Room       | 1st   | 2     | Datacenter uplink, spare               |

**Business port count:** 4 wired drops (tagged VLAN 20)

---

## IoT / Home Assistant VLAN (VLAN 40)

| Device Category          | Count (est.) | Connection | Notes                           |
|--------------------------|-------------|------------|----------------------------------|
| Home Assistant hub       | 1           | Wired      | Dedicated drop in utility room    |
| LG mini-split HVAC       | 5 zones     | WiFi       | LG ThinQ, needs internet access   |
| LG smart washer           | 1           | WiFi       | 2nd floor laundry                 |
| LG smart dryer            | 1           | WiFi       | 2nd floor laundry                 |
| LG smart fridge (kitchen) | 1           | WiFi       | 1st floor kitchen                 |
| Samsung fridge (cabana)   | 1           | WiFi       | Garage annex                      |
| Smart switches/dimmers    | 10-20       | WiFi/Zigbee| Throughout house (via HA)         |
| Smart locks               | 2-3         | WiFi/Zigbee| Front, rear, garage entry         |
| Smart doorbell            | 1           | WiFi       | Front porch                       |
| Leak sensors              | 3-5         | Zigbee     | Under sinks, near water heaters   |
| Smoke/CO detectors        | TBD         | WiFi/Zigbee| Code-required locations           |

**IoT wired port count:** 1 (Home Assistant hub). Everything else is WiFi on IoT SSID.

> **Tip:** Use a Zigbee coordinator (like Sonoff ZBDongle-P) plugged into the Home Assistant box. Zigbee devices stay off WiFi entirely and mesh through each other.

---

## Home VLAN (VLAN 10) - Personal Devices

| Location            | Floor | Drops | Devices                              |
|---------------------|-------|-------|--------------------------------------|
| Living Room         | 1st   | 2     | TV/streaming, game console            |
| Primary Bedroom     | 2nd   | 1     | TV/streaming                          |
| Kids Room - Alice   | 2nd   | 1     | Future use                            |
| Kids Room - Bobby   | 2nd   | 1     | Future use                            |
| Tara's Office       | 1st   | 2     | Workstation, secondary device          |
| Cabana              | Ext   | 1     | Streaming/entertainment               |

**Home wired port count:** 8 drops + all personal WiFi devices

---

## Port Count Summary

### Core Switch (Utility Room) - Pro Max 24 PoE

**2.5GbE PoE++ Ports (1-8)** — high-speed devices

| Port | VLAN  | Assignment                              | Speed  |
|------|-------|-----------------------------------------|--------|
| 1    | 20    | Bob's Office - workstation              | 2.5GbE |
| 2    | 20    | Bob's Office - secondary                | 2.5GbE |
| 3    | 10    | Tara's Office - workstation             | 2.5GbE |
| 4    | 10    | Tara's Office - secondary               | 2.5GbE |
| 5    | 50    | TrueNAS - onboard RTL8125 (Datacenter)  | 2.5GbE |
| 6    | Trunk | Uplink to garage switch                 | 2.5GbE |
| 7    | Trunk | U7 Pro AP - 2nd floor (PoE)             | 2.5GbE |
| 8    | Trunk | U7 In-Wall AP (PoE)                     | 2.5GbE |

**GbE Ports (9-24)** — cameras, servers, lower-speed devices

| Port  | VLAN  | Assignment                              | Speed |
|-------|-------|-----------------------------------------|-------|
| 9-14  | 30    | Cameras (PoE) - front door, back door, mudroom, pool, side, driveway | GbE |
| 15    | 10    | Living Room - primary                   | GbE   |
| 16    | 10    | Living Room - secondary                 | GbE   |
| 17    | 10    | Primary Bedroom                         | GbE   |
| 18    | 10    | Kids Room - Alice                       | GbE   |
| 19    | 10    | Kids Room - Bobby                       | GbE   |
| 20    | 40    | Unmanaged PoE switch (IoT expansion)    | GbE   |
| 21    | 20    | TrueNAS - add-in I226-V (Business)      | GbE   |
| 22    | 50    | Proxmox - add-in I226-V (Datacenter)    | GbE   |
| 23    | 50    | Unraid - add-in I226-V (Datacenter)     | GbE   |
| 24    | 50    | Hub / GMKTEC K12 (Datacenter)           | GbE   |

**SFP+ Uplinks (10G)**

| Port   | Assignment                               |
|--------|------------------------------------------|
| SFP+ 1 | UCG-Ultra / Gateway uplink               |
| SFP+ 2 | Spare                                    |

**Total used: 24 / 24 ports + 1 SFP+ = 0 spare (1 SFP+ spare)**

> All servers connect to the core switch at 2.5GbE or GbE. No separate 10G aggregation switch needed. Windows Server is a Proxmox VM — uses Proxmox's NIC via bridged networking.

### IoT PoE Switch (Utility Room) - Unmanaged (Existing)

Uplink from core switch port 20 (VLAN 40). All ports are IoT VLAN.

| Port | Assignment                              |
|------|-----------------------------------------|
| 1    | Uplink from core switch (port 20)       |
| 2    | Home Assistant hub                      |
| 3    | Apollo R PRO-1 - 1st floor bathroom (PoE) |
| 4    | Apollo R PRO-1 - Primary bathroom (PoE) |
| 5    | Apollo R PRO-1 - Shared bathroom (PoE)  |
| 6+   | Spare (future IoT PoE devices)          |

### Garage Switch - Flex 2.5G PoE

| Port | VLAN  | Assignment                    | Speed  |
|------|-------|-------------------------------|--------|
| 1    | 30    | Camera - Garage exterior (PoE)| 2.5GbE |
| 2    | 30    | Camera - Cabana/backyard (PoE)| 2.5GbE |
| 3    | 10    | Cabana entertainment drop     | 2.5GbE |
| 4    | Trunk | U7 Outdoor AP (PoE)           | 2.5GbE |
| 5-8  | --    | Spare                         | 2.5GbE |
| 10G  | Trunk | Uplink to core switch         | 10GbE  |

**Total used: 4 / 8 ports + 10G uplink = 4 spare**

---

## WiFi SSID Plan

| SSID              | VLAN | Band     | Notes                                 |
|-------------------|------|----------|---------------------------------------|
| Murphy-Home       | 10   | 2.4+5GHz | Personal devices, phones, tablets      |
| Murphy-Business   | 20   | 5GHz     | Work laptops, printers                 |
| Murphy-IoT        | 40   | 2.4GHz   | Smart devices, HVAC, appliances        |
| Murphy-Guest      | 60   | 2.4+5GHz | Internet only, fully isolated           |

> Cameras are PoE only - no WiFi SSID needed for VLAN 30.

---

## AP Placement

| AP               | Location                | Covers                                        |
|------------------|------------------------|-----------------------------------------------|
| U7 In-Wall       | 1st Floor - Office     | Office, kitchen, living room, pantry           |
| U7 Pro           | 2nd Floor - Hallway    | Bedrooms, offices, laundry, bathrooms          |
| U7 Outdoor       | Garage annex / exterior| Cabana, deck, driveway, yard                   |
| U6+ (backup)     | Reposition as needed   | Fallback for dead spots, or repurpose elsewhere |

> **Decision needed:** The U7 In-Wall has 4 built-in switch ports. Consider placing it in the office wall plate to provide wired ports there without running 2 extra cables. That would reduce core switch usage by 2 ports.

---

## Cable Run Summary

| From             | To                | Runs | Type  | Distance (est.) |
|------------------|-------------------|------|-------|-----------------|
| Utility room     | Bob's Office      | 2    | Cat6A | ~30ft           |
| Utility room     | Living Room       | 2    | Cat6A | ~40ft           |
| Utility room     | Front door (doorbell) | 1 | Cat6A | ~40ft          |
| Utility room     | Back door (doorbell)  | 1 | Cat6A | ~35ft          |
| Utility room     | Mudroom door (doorbell)| 1 | Cat6A | ~20ft         |
| Utility room     | Pool area (cam)   | 1    | Cat6A | ~50ft           |
| Utility room     | Side of house (cam)| 1   | Cat6A | ~45ft           |
| Utility room     | Front yard/driveway (cam)| 1 | Cat6A | ~50ft         |
| Utility room     | 1st FL AP location| 1    | Cat6A | ~25ft           |
| Utility room     | 2nd FL hallway AP | 1    | Cat6A | ~40ft           |
| Utility room     | Tara's Office     | 2    | Cat6A | ~30ft           |
| Utility room     | Primary Bedroom   | 1    | Cat6A | ~50ft           |
| Utility room     | Kids Alice        | 1    | Cat6A | ~40ft           |
| Utility room     | Kids Bobby        | 1    | Cat6A | ~40ft           |
| Utility room     | Garage (trunk)    | 1    | Cat6A | ~60ft           |
| Garage switch    | Garage interior (cam) | 1 | Cat6A | ~15ft          |
| Garage switch    | Cabana interior (cam) | 1 | Cat6A | ~25ft          |
| Garage switch    | Cabana drop       | 1    | Cat6A | ~20ft           |
| Garage switch    | U7 Outdoor AP     | 1    | Cat6A | ~20ft           |

| Utility room     | 1st FL bathroom (sensor) | 1 | Cat6A | ~25ft          |
| Utility room     | 2nd FL primary bath (sensor) | 1 | Cat6A | ~45ft        |
| Utility room     | 2nd FL shared bath (sensor) | 1 | Cat6A | ~40ft         |

**Total cable runs: 25**
**Estimated cable needed: ~1,300 ft** (runs + slack + termination waste)

---

## Shopping List

### Contractor-Provided (patch panel to outlets)

| Item | Qty | Est. Cost |
|------|-----|-----------|
| Cat6A bulk cable (1000ft) | 2 | ~$360 |
| 24-port Cat6A keystone patch panel | 1 | ~$40 |
| Cat6A keystone jacks | 50 | ~$60 |
| Wall plates (1-gang & 2-gang) | 22 | ~$40 |
| **Subtotal - Contractor** | | **~$500** |

### Owner-Provided

#### Networking Equipment

| Item | Qty | Est. Cost | Link |
|------|-----|-----------|------|
| UniFi Switch Pro Max 24 PoE | 1 | $799 | [Ubiquiti Store](https://store.ui.com/us/en/products/usw-pro-max-24-poe) |
| UniFi Switch Flex 2.5G PoE | 1 | $199 | [Ubiquiti Store](https://store.ui.com/us/en/products/usw-flex-2-5g-8-poe) |
| UniFi U7 Pro AP (WiFi 7) | 1 | $189 | [Ubiquiti Store](https://store.ui.com/us/en/products/u7-pro) |
| Intel I226-V 2.5GbE NIC (PCIe x1) | 3 | ~$75 | [Amazon](https://www.amazon.com/2-5GBase-T-Network-Adapter-Ethernet-Controller/dp/B0BNHWZBCC) |
| **Subtotal - Networking** | | **$1,262** | |

#### Rack & Accessories

| Item | Qty | Est. Cost | Link |
|------|-----|-----------|------|
| StarTech 42U 4-Post Open Frame Rack w/ Casters | 1 | ~$356 | [StarTech](https://www.amazon.com/StarTech-com-4-Post-42U-Mobile-Open-Frame-Server-Rack/dp/B00HVKOPBW) |
| NavePoint 2U HD Vented Cantilever Shelf (18" deep) | 4 | ~$120 | [NavePoint](https://navepoint.com/navepoint-2u-heavy-duty-vented-cantilever-shelf-18-460mm-deep/) |
| NavePoint 1U Cantilever Shelf (14" deep) | 1 | ~$20 | [NavePoint](https://navepoint.com/19-inch-cantilever-shelf-1u-with-14-depth-ral9003-signal-white/) |
| Cat6A patch cables (various lengths) | 30 | ~$50 | |
| **Subtotal - Rack** | | **~$546** | |

> **Garage rack:** The garage switch and patch panel live inside the 12U NavePoint AV cabinet — see [[garage-av-rack|Garage AV / Network Rack]] for the full enclosure spec, cooling, rack elevation, and rough-in requirements. The earlier 6U Tecmojo / 10" patch-panel plan was dropped because the 6U/10" form factor couldn't fit the receiver, AirPort Express, and shelf.

#### Cameras (Reolink PoE)

| Item | Qty | Est. Cost | Link |
|------|-----|-----------|------|
| Reolink Video Doorbell PoE (5MP) | 3 | $330 | [Reolink](https://reolink.com/us/product/reolink-video-doorbell-poe/) |
| Reolink RLC-811A (4K bullet, 5x zoom, outdoor) | 2 | $244 | [Reolink](https://reolink.com/product/rlc-811a/) |
| Reolink RLC-1240A (12MP dome, garage) | 1 | $140 | [Reolink](https://reolink.com/product/rlc-1240a/) |
| Reolink RLC-520A (5MP dome, cabana) | 1 | $47 | [Reolink](https://reolink.com/product/rlc-520a/) |
| **Subtotal - Cameras** | **7** | **$761** | |

### Summary

| Category | Responsibility | Cost |
|----------|---------------|------|
| Cabling & termination | Contractor | ~$500 |
| Networking equipment | Owner | $1,262 |
| Rack & accessories | Owner | ~$546 |
| Cameras (Reolink) | Owner | $761 |
| **Owner total** | | **~$2,569** |
| **Contractor total** | | **~$500** |
| **Grand total** | | **~$3,069** |

> Garage AV rack hardware (12U NavePoint cabinet, PDU, shelves, cabling) is tracked separately under [[../bom/index#garage-av--audio|BOM → Garage AV / Audio]] and totals **~$356**.

### Already Own

| Item                    | Status          | Limitation |
|------------------------|-----------------|------------|
| UCG-Ultra              | Router/controller | **1GbE LAN — bottleneck for 2.5G/10G fabric** |
| U6+ AP                 | Indoor WiFi 6 backup | GbE uplink only (not 2.5GbE) |
| U7 Outdoor AP          | Exterior AP - ready | 2.5GbE uplink — good |
| U7 In-Wall AP          | In-wall AP - ready | 2.5GbE uplink — good |
| Scrypted NVR           | Running on 10.10.11.201 | Ready |
| Reolink RLC-810A       | 4K bullet camera - owned | Assign to side yard (4mm lens) |
| EcoFlow Delta 3 (1024Wh/1800W) | Portable power station / UPS | Primary UPS for utility room rack |
| Amazon Basics 800VA UPS | 3 units owned | Garage, office, overflow |

> **Gateway upgrade consideration:** The UCG-Ultra's 1GbE LAN port will be the bottleneck for the entire network. All inter-VLAN traffic routes through the gateway. Options:
> - **[Cloud Gateway Max](https://store.ui.com/us/en/products/ucg-max)** (~$299) — 2.5GbE LAN, good match for the 2.5G switch fabric
> - **[Dream Machine Pro Max](https://store.ui.com/us/en/products/udm-pro-max)** (~$499) — 10GbE + 2.5GbE, 1U rack mount, built-in NVR storage, full IDS/IPS

---

## Open Decisions

- [ ] Confirm utility room as network closet / home run location
- [ ] Gateway upgrade: keep UCG-Ultra (1GbE bottleneck) vs Cloud Gateway Max ($299) vs Dream Machine Pro Max ($499)?
- [x] ~~Camera brand/model~~ — Reolink PoE (3x Doorbell, 2x RLC-810A, 2x RLC-520A)
- [ ] U7 In-Wall placement - office wall (saves cable runs) vs dedicated?
- [ ] Home Assistant hardware (RPi, mini PC, or VM on Proxmox?)
- [ ] Zigbee coordinator model for HA
- [ ] Smart switch/dimmer brand (Lutron Caseta, Inovelli, etc.)
- [ ] Smart lock brand (Yale, Schlage, August?)
- [ ] EV charger in garage - needs dedicated circuit, possibly VLAN 40 for smart charging
- [x] ~~Garage switch location - plan mounting spot, route cables behind wall, rough in receptacle for Flex switch power~~ — switch + patch panel housed in 12U garage AV cabinet, see [[garage-av-rack|Garage AV / Network Rack]]
- [x] ~~10G NICs~~ — dropped 10G plan, going all 2.5GbE with Intel I226-V add-in cards ($75 total)
