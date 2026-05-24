---
title: Garage AV / Network Rack
---

# Garage AV / Network Rack — Build Specification

**Location:** Garage (wall-mounted enclosed rack)
**Primary function:** AirPlay 2 audio playback through existing AV receiver, plus home network distribution
**Outdoor zone:** Patio/deck (single all-weather speaker)
**Prepared:** May 23, 2026
**Status:** For new-construction rough-in and equipment relocation/install

> The garage rack houses **both** the AV receiver and the garage network switch / patch panel. This supersedes the 10" 6U garage cabinet shown in earlier revisions of [[networking|Networking & Cameras]] — the receiver depth (14.75") requires a 23.6" deep enclosure.

-----

## 1. System Overview

This is an **existing, working setup being relocated** into the new construction. A wall-mounted, enclosed 12U network cabinet in the garage houses the AV receiver and network gear. The receiver gets audio wirelessly via AirPlay 2, delivered to an Apple AirPort Express acting as a network-attached AirPlay 2 receiver. The AirPort Express feeds the receiver’s analog input over a 3.5mm-to-RCA cable. The receiver drives a single all-weather speaker in stereo for one outdoor (patio/deck) area.

Because the cabinet is an enclosed metal enclosure (effectively a Faraday cage) and sits in an unconditioned, dust-prone space, the two design priorities are **active thermal management** and a **fully wired network connection** to the AirPort Express (no reliance on Wi-Fi inside the box).

-----

## 2. Equipment Status Legend

- **[EXISTING]** — current gear being relocated from the present setup; no purchase required.
- **[NEW]** — to be purchased for this build.
- **[TRACKED]** — covered in the separate equipment tracker; shown here only for rack layout/wiring context.

-----

## 3. Enclosure

|Item            |Specification                                                                        |Status   |
|----------------|-------------------------------------------------------------------------------------|---------|
|Type            |Wall-mount enclosed network cabinet                                                  |**[NEW]**|
|Model           |NavePoint 12U, deep version                                                          |         |
|Usable height   |12U (~21”)                                                                           |         |
|**Depth**       |**23.6” (600mm)** — required; the 17.7”/450mm version is too shallow for the receiver|         |
|Door            |Lockable tempered glass (perforated/honeycomb preferred for airflow)                 |         |
|Side panels     |Removable, lockable                                                                  |         |
|Built-in cooling|2× fan (top-mounted exhaust)                                                         |         |
|Mounting        |19” EIA-310 rails                                                                    |         |


> **Depth rationale:** The receiver is 14.75” deep and needs ~3–4” of additional clearance behind it for connectors and cable bend radius. A 450mm cabinet provides only ~14.2” usable mounting depth and will not close. The 600mm cabinet is mandatory.

-----

## 4. Equipment Housed in Rack

|Equipment         |Model                                |Size (W × H × D)     |Weight|Rack space    |Status        |Notes                                                                                   |
|------------------|-------------------------------------|---------------------|------|--------------|--------------|----------------------------------------------------------------------------------------|
|AV receiver       |Onkyo TX-SR606                       |17.1” × 6.9” × 14.75”|~25 lb|~4U (on shelf)|**[EXISTING]**|Relocate. **Fanless / passive cooling only** — runs hot, known heat-sensitive HDMI board|
|AirPlay 2 receiver|Apple AirPort Express A1392 (2nd gen)|~3.85” square        |<1 lb |On small shelf|**[EXISTING]**|Relocate. AirPlay 2 capable after firmware update                                       |
|Network switch    |see equipment tracker                |19”, 1U              |—     |1U            |**[TRACKED]** |Specced in separate doc; reserve 1U here                                                |
|Patch panel       |see equipment tracker                |19”, 1U              |—     |1U            |**[TRACKED]** |Specced in separate doc; reserve 1U here                                                |

-----

## 5. Outdoor Speaker Zone (Patio / Deck)

|Item      |Detail                                                                         |Status                   |
|----------|-------------------------------------------------------------------------------|-------------------------|
|Speaker   |Polk Audio Atrium 8 SDI (×1)                                                   |**[EXISTING]** — relocate|
|Coverage  |One outdoor area (patio/deck)                                                  |                         |
|Mode      |**Single-speaker stereo** (SDI single/dual switch set to single-speaker stereo)|                         |
|Electrical|8 ohm nominal, 10–125W, 91 dB sensitivity                                      |                         |
|Amp match |Onkyo 90W/ch sits comfortably under the 125W rating — good headroom            |                         |
|Mounting  |Polk Speed-Lock bracket (included with speaker)                                |**[EXISTING]**           |

**Why one speaker works:** The Atrium 8 SDI’s single/dual input switch + dual-tweeter array lets one speaker reproduce full stereo. For a single patio/deck area, one unit in stereo mode is the intended use — no second speaker required.

**Wiring (one speaker carries both channels):**

- Onkyo **Front L** (+/–) → speaker **Left** terminals
- Onkyo **Front R** (+/–) → speaker **Right** terminals
- Single **16/4 (4-conductor)** run from rack to patio carries both channels.

**Receiver settings:**

- Use **Front L/R** outputs only (main zone).
- Speaker config: **2.0** (no center/surround/sub).
- Listening mode: **Stereo** (so AirPlay audio plays straight through the fronts).

-----

## 6. New Purchases (Bill of Materials)

*Existing gear (receiver, AirPort Express, speaker) is NOT listed here — see Sections 4 & 5. The switch and patch panel are tracked in the separate equipment doc.*

|Qty      |Item                                                    |Purpose / Spec                                                                          |Status   |
|---------|--------------------------------------------------------|----------------------------------------------------------------------------------------|---------|
|1        |NavePoint 12U enclosed cabinet, 23.6” deep              |Enclosure (see Section 3)                                                               |**[NEW]**|
|1        |**AC Infinity CLOUDPLATE T7** (or equiv.)               |1U thermostat-controlled rack fan. Primary active cooling for the fanless receiver.     |**[NEW]**|
|1        |Heavy-duty vented rack shelf, ~15–17” deep, 50+ lb rated|Supports the receiver (no rack ears — must sit on a shelf).                             |**[NEW]**|
|1        |Small vented shelf, 1U, ~10” deep                       |Holds the AirPort Express.                                                              |**[NEW]**|
|1        |Rackmount PDU, 1U, 6–8 outlet, surge protected          |Powers receiver, AirPort Express, cooling fan.                                          |**[NEW]**|
|1        |RCA (red/white) → 3.5mm cable, 1–2 ft                   |AirPort Express audio out → receiver analog input.                                      |**[NEW]**|
|1        |Cat6 patch cable, short                                 |Switch → AirPort Express Ethernet port. **Critical for AirPlay 2 inside the metal box.**|**[NEW]**|
|As needed|Cat6 patch cables                                       |Patch panel → switch terminations.                                                      |**[NEW]**|
|1 run    |16/4 outdoor/in-wall-rated speaker wire (14/4 if >50 ft)|Rack → patio speaker. Direct-burial rated for any buried section.                       |**[NEW]**|
|1 pack   |M6 cage nuts + screws                                   |Mounting hardware (backup to cabinet-supplied).                                         |**[NEW]**|
|Optional |1U brush/cable entry panel, blank panels                |Cable management and airflow control.                                                   |**[NEW]**|

-----

## 7. Rack Elevation (bottom → top)

```
12U  ┌─────────────────────────────────┐
11U  │  (open — fan exhaust headroom)  │
10U  │                                 │
 9U  │  PDU (1U)            [NEW]      │
 8U  │  Patch panel (1U)  [TRACKED]    │
 7U  │  Network switch (1U)[TRACKED]   │
 6U  │  Small shelf — AirPort [EXIST]  │
 5U  │  (open — heat gap)              │
 4U  │  AC Infinity CLOUDPLATE [NEW]   │
 3U  │  ┌─ Onkyo TX-SR606 [EXISTING]┐  │
 2U  │  │  (on vented shelf)        │  │
 1U  │  └── vented shelf [NEW] ─────┘  │
     └─────────────────────────────────┘
```

**Placement logic:** Heaviest item (receiver) low for wall-mount stability. Active cooler directly above it. A heat gap above that. Light, cooler-running network gear up top. Top fans exhaust through the remaining open U’s.

-----

## 8. Signal & Network Path

```
[Phone / Mac / iPad]
      │  (AirPlay 2 over home network)
      ▼
[Network switch] ──Ethernet──► [AirPort Express A1392]   (existing)
                                      │  3.5mm → RCA (analog)
                                      ▼
                               [Onkyo TX-SR606]           (existing)
                                      │  Front L + Front R
                                      ▼
                          [Polk Atrium 8 SDI — patio]     (existing, single-speaker stereo)
```

-----

## 9. AirPort Express Configuration (Critical)

The cabinet blocks Wi-Fi, so the AirPort Express must be wired:

1. Connect the AirPort Express’s Ethernet port to the network switch.
1. In **AirPort Utility**, set **Wireless Mode → Off** (Wi-Fi is unusable inside the metal cabinet and not needed).
1. Set **Router Mode → Off (Bridge Mode)**.
1. Confirm firmware is current (7.8+) so AirPlay 2 is enabled.
1. Connect the 3.5mm audio out to the receiver’s analog input; select that input on the receiver.

AirPlay 2 streams to the AirPort Express over Ethernet with Wi-Fi disabled — confirmed supported behavior.

-----

## 10. New-Construction Rough-In Requirements

Address these **before drywall** while the wall is open:

### Structural

- [ ] **Plywood backer board** (3/4”) or solid blocking between studs at the cabinet location. Loaded cabinet can total **80–100+ lb** on the wall — do not rely on drywall anchors alone.
- [ ] Confirm mounting height and clearance for the **glass door swing** and **side-panel removal**.

### Electrical

- [ ] **Dedicated 20A quad receptacle** behind/inside the cabinet footprint on its own circuit (standard for all racks). Isolates the rack from garage power tools/compressors and provides spare outlets for service/test gear.
- [ ] Position the quad so the PDU cord reaches without blocking airflow/fan exhaust.

### Low-Voltage / Data

- [ ] **Ethernet home runs (Cat6)** to the rack, terminated at the patch panel — size for current devices plus spares.
- [ ] **Speaker wire run to patio:** one **16/4** (or 14/4 for long pulls) outdoor/in-wall-rated run from the rack to the patio speaker location. Direct-burial rated for any buried section.
- [ ] **Future-proofing:** pull an **extra conductor pair or run conduit** to the patio in case the zone is later expanded to a true L/R pair or a second outdoor zone.
- [ ] **Conduit / smurf tube** (1”) from the cabinet to the attic/central low-voltage point for future pulls.
- [ ] Low-voltage cable entry into the cabinet via top/bottom knockouts; plan a brush panel.

### Environmental (garage-specific)

- [ ] Prefer an **interior (conditioned-adjacent) wall** over an exterior wall to reduce summer heat load.
- [ ] Keep the cabinet out of direct sun through windows/garage door.
- [ ] If the garage regularly exceeds ~95°F, the thermostat fan is essential; consider a higher-capacity fan kit.

-----

## 11. Installation Notes

- The receiver has **no rack ears** — it rests on the vented shelf, not bolted to rails.
- Set the **CLOUDPLATE thermostat** to engage early (~85–90°F) given the heat-sensitive receiver and garage swings.
- Verify the cabinet’s built-in fans **exhaust out the top**, working with (not against) the CLOUDPLATE.
- Leave the planned **open U’s** unobstructed — they’re part of the cooling design.
- Dress cables to the sides/rear so they don’t block the receiver’s top/side vents.
- On the Polk speaker, confirm the **single/dual switch is set to single-speaker stereo** before closing up the patio wiring.
- Label patch panel ports and the AirPort Express’s switch port for future service.

-----

## 12. Quick Reference — Key Specs

|                             |Value                                                          |
|-----------------------------|---------------------------------------------------------------|
|Cabinet depth required       |23.6” (600mm)                                                  |
|Receiver footprint           |17.1”W × 6.9”H × 14.75”D, ~25 lb                               |
|Receiver rack height         |~4U                                                            |
|Min. shelf depth for receiver|~15”                                                           |
|Estimated total loaded weight|80–100+ lb (verify backing)                                    |
|Outdoor speaker              |Polk Atrium 8 SDI, 8 ohm, 10–125W, 91 dB, single-speaker stereo|
|Patio speaker run            |16/4 (14/4 if >50 ft), outdoor/in-wall rated                   |