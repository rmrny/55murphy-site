---
title: Garage AV / Network Rack
---

# Garage AV / Network Rack — Build Specification

**Location:** Garage (wall-mounted enclosed rack)
**Primary function:** AirPlay 2 audio playback through existing AV receiver, plus home network distribution
**Audio zones:** Main Zone → patio/deck speaker; Zone 2 → garage bookshelf monitors
**Prepared:** May 23, 2026
**Status:** For new-construction rough-in and equipment relocation/install

> The garage rack houses **both** the AV receiver and the garage network switch / patch panel. This supersedes the 10" 6U garage cabinet shown in earlier revisions of [[networking|Networking & Cameras]] — the 6U/10" plan was too small once the receiver, AirPort Express, and shelf were added.

-----

## 1. System Overview

This is an **existing, working setup being relocated** into the new construction. A wall-mounted, enclosed 12U network cabinet in the garage houses the AV receiver and network gear. The receiver gets audio wirelessly via AirPlay 2, delivered to an Apple AirPort Express acting as a network-attached AirPlay 2 receiver. The AirPort Express feeds the receiver’s analog input over a 3.5mm-to-RCA cable.

The Denon drives two audio zones:

- **Main Zone (speaker-level, Front L/R):** a single Polk Atrium 8 SDI on the patio/deck, run in single-speaker stereo mode.
- **Zone 2 (line-level, RCA pre-out):** a pair of Mackie CR3 powered bookshelf monitors sitting on a shelf next to the rack for music playback in the garage itself.

Because the cabinet is an enclosed metal enclosure (effectively a Faraday cage) and sits in an unconditioned, dust-prone space, the two design priorities are **adequate passive/exhaust ventilation** and a **fully wired network connection** to the AirPort Express (no reliance on Wi-Fi inside the box).

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
|Model           |NavePoint 12U                                                                        |         |
|Usable height   |12U (~21”)                                                                           |         |
|**Depth**       |**17.7” (450mm)** — fits the Denon (13.31” deep) with adequate clearance             |         |
|Door            |Lockable tempered glass (perforated/honeycomb preferred for airflow)                 |         |
|Side panels     |Removable, lockable                                                                  |         |
|Built-in cooling|2× fan (top-mounted exhaust)                                                         |         |
|Mounting        |19” EIA-310 rails                                                                    |         |


> **Depth rationale:** The Denon AVR-X1300W is 13.31” deep. A 450mm cabinet provides ~14.2” usable mounting depth, leaving roughly an inch behind the receiver for connectors and cable bend radius. The receiver sits on a shelf (not bolted to rails), so cabling can drop into the open space below.

-----

## 4. Equipment Housed in Rack

|Equipment         |Model                                |Size (W × H × D)     |Weight|Rack space    |Status        |Notes                                                                                   |
|------------------|-------------------------------------|---------------------|------|--------------|--------------|----------------------------------------------------------------------------------------|
|AV receiver       |Denon AVR-X1300W                     |17.1” × 5.94” × 13.31”|~18.75 lb|~4U (on shelf)|**[EXISTING]**|Relocate. 7.2-ch, 80W/ch. Has its own internal cooling vents — leave top clearance.      |
|AirPlay 2 receiver|Apple AirPort Express A1392 (2nd gen)|~3.85” square        |<1 lb |On small shelf|**[EXISTING]**|Relocate. AirPlay 2 capable after firmware update                                       |
|Network switch    |see equipment tracker                |19”, 1U              |—     |1U            |**[TRACKED]** |Specced in separate doc; reserve 1U here                                                |
|Patch panel       |see equipment tracker                |19”, 1U              |—     |1U            |**[TRACKED]** |Specced in separate doc; reserve 1U here                                                |

-----

## 5. Audio Zones

### 5a. Main Zone — Outdoor Speaker (Patio / Deck)

|Item      |Detail                                                                         |Status                   |
|----------|-------------------------------------------------------------------------------|-------------------------|
|Speaker   |Polk Audio Atrium 8 SDI (×1)                                                   |**[EXISTING]** — relocate|
|Coverage  |One outdoor area (patio/deck)                                                  |                         |
|Mode      |**Single-speaker stereo** (SDI single/dual switch set to single-speaker stereo)|                         |
|Electrical|8 ohm nominal, 10–125W, 91 dB sensitivity                                      |                         |
|Amp match |Denon 80W/ch sits comfortably under the 125W rating — good headroom            |                         |
|Mounting  |Polk Speed-Lock bracket (included with speaker)                                |**[EXISTING]**           |

**Why one speaker works:** The Atrium 8 SDI’s single/dual input switch + dual-tweeter array lets one speaker reproduce full stereo. For a single patio/deck area, one unit in stereo mode is the intended use — no second speaker required.

**Wiring (one speaker carries both channels):**

- Denon **Front L** (+/–) → speaker **Left** terminals
- Denon **Front R** (+/–) → speaker **Right** terminals
- Single **16/4 (4-conductor)** run from rack to patio carries both channels.

**Receiver settings (Main Zone):**

- Use **Front L/R** speaker outputs.
- Speaker config: **2.0** (no center/surround/sub).
- Listening mode: **Stereo** (so AirPlay audio plays straight through the fronts).

### 5b. Zone 2 — Garage Bookshelf Monitors

|Item      |Detail                                                                                  |Status                   |
|----------|----------------------------------------------------------------------------------------|-------------------------|
|Speakers  |Mackie CR3 — 3” Creative Reference multimedia monitors (pair, powered)                  |**[EXISTING]** — relocate|
|Type      |Active 2-way nearfield monitors — built-in amplification, no external amp required      |                         |
|Inputs    |RCA L/R (rear), 1/4” TRS L/R (rear), 1/8” stereo aux (front)                            |                         |
|Output    |50W total system power, 3" woofer + 0.75" tweeter                                       |                         |
|Coverage  |Music playback inside the garage (near-rack listening)                                  |                         |
|Location  |On a shelf/workbench within ~6 ft of the AV cabinet — short RCA run, no in-wall pull    |                         |
|Power     |One AC outlet at the CR3 location (the right/active monitor houses the amp + power)     |                         |

**Wiring:**

- Denon **Zone 2 PRE OUT L/R** (RCA) → Mackie CR3 active monitor **RCA L/R** input.
- Short RCA cable run (3–6 ft) from the back of the rack to the CR3 shelf.
- Mackie-supplied speaker cable connects the active (right) monitor to the passive (left) monitor.

**Receiver settings (Zone 2):**

- Menu → **Zone 2 Setup → Volume Level** → leave at **Variable** so the AVR controls CR3 volume directly (CR3’s own knob can stay at a useful reference position).
- Zone 2 source can be set independently from Main Zone, or both zones can play the same source.

**Why this configuration:** The CR3s are *powered* monitors with their own amp — they require a **line-level** signal, not speaker-level. The Denon’s Zone 2 pre-out provides exactly that, and the variable-level setting lets the AVR remote control garage music volume without touching the speakers.

-----

## 6. New Purchases (Bill of Materials)

*Existing gear (receiver, AirPort Express, Polk Atrium 8, Mackie CR3 pair) is NOT listed here — see Sections 4 & 5. The switch and patch panel are tracked in the separate equipment doc.*

|Qty      |Item                                                    |Purpose / Spec                                                                          |Status   |
|---------|--------------------------------------------------------|----------------------------------------------------------------------------------------|---------|
|1        |NavePoint 12U enclosed cabinet, 17.7” (450mm) deep      |Enclosure (see Section 3)                                                               |**[NEW]**|
|1        |Heavy-duty vented rack shelf, ~14–15” deep, 50+ lb rated|Supports the receiver (no rack ears — must sit on a shelf).                             |**[NEW]**|
|1        |Small vented shelf, 1U, ~10” deep                       |Holds the AirPort Express.                                                              |**[NEW]**|
|1        |Rackmount PDU, 1U, 6–8 outlet, surge protected          |Powers receiver and AirPort Express.                                                    |**[NEW]**|
|1        |RCA (red/white) → 3.5mm cable, 1–2 ft                   |AirPort Express audio out → receiver analog input.                                      |**[NEW]**|
|1        |RCA stereo cable (L/R), 3–6 ft                          |Denon Zone 2 PRE OUT → Mackie CR3 RCA input.                                            |**[NEW]**|
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
 9U  │  (open — heat gap)              │
 8U  │  PDU (1U)            [NEW]      │
 7U  │  Patch panel (1U)  [TRACKED]    │
 6U  │  Network switch (1U)[TRACKED]   │
 5U  │  Small shelf — AirPort [EXIST]  │
 4U  │  ┌─ Denon AVR-X1300W [EXIST]─┐  │
 3U  │  │                           │  │
 2U  │  │  (on vented shelf)        │  │
 1U  │  └── vented shelf [NEW] ─────┘  │
     └─────────────────────────────────┘
```

**Placement logic:** Heaviest item (receiver) low for wall-mount stability. A heat gap above the receiver lets its top vents breathe. Light, cooler-running network gear above the gap. Top fans exhaust through the remaining open U’s.

-----

## 8. Signal & Network Path

```
[Phone / Mac / iPad]
      │  (AirPlay 2 over home network)
      ▼
[Network switch] ──Ethernet──► [AirPort Express A1392]   (existing)
                                      │  3.5mm → RCA (analog)
                                      ▼
                               [Denon AVR-X1300W]         (existing)
                                      │
                ┌─────────────────────┴─────────────────────┐
                │ Main Zone                                 │ Zone 2
                │ Front L/R (speaker level)                 │ Pre-out L/R (RCA, line-level)
                ▼                                           ▼
   [Polk Atrium 8 SDI — patio]                  [Mackie CR3 pair — garage shelf]
   (existing, single-speaker stereo)            (existing, powered monitors)
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
- [ ] **Outlet at the CR3 shelf location** — the Mackie active monitor needs one standard 120V outlet within reach of its AC cord. This can come off the same rack circuit if the shelf is adjacent, or off a nearby general garage circuit.

### Low-Voltage / Data

- [ ] **Ethernet home runs (Cat6)** to the rack, terminated at the patch panel — size for current devices plus spares.
- [ ] **Speaker wire run to patio:** one **16/4** (or 14/4 for long pulls) outdoor/in-wall-rated run from the rack to the patio speaker location. Direct-burial rated for any buried section.
- [ ] **Future-proofing:** pull an **extra conductor pair or run conduit** to the patio in case the zone is later expanded to a true L/R pair or a second outdoor zone.
- [ ] **Conduit / smurf tube** (1”) from the cabinet to the attic/central low-voltage point for future pulls.
- [ ] Low-voltage cable entry into the cabinet via top/bottom knockouts; plan a brush panel.

### Environmental (garage-specific)

- [ ] Prefer an **interior (conditioned-adjacent) wall** over an exterior wall to reduce summer heat load.
- [ ] Keep the cabinet out of direct sun through windows/garage door.
- [ ] If the garage regularly exceeds ~95°F, add a thermostat-controlled rack fan (e.g. AC Infinity CLOUDPLATE T7) — the cabinet’s built-in top fans alone may not be enough.

-----

## 11. Installation Notes

- The receiver has **no rack ears** — it rests on the vented shelf, not bolted to rails.
- Verify the cabinet’s built-in fans **exhaust out the top** so warm air from the receiver vents upward and out.
- Leave the planned **open U’s** unobstructed — they’re part of the cooling design.
- Dress cables to the sides/rear so they don’t block the receiver’s top/side vents.
- On the Polk speaker, confirm the **single/dual switch is set to single-speaker stereo** before closing up the patio wiring.
- For the CR3 monitors: confirm **Zone 2 Volume Level = Variable** in the Denon menu, set the CR3’s rear-panel volume knob to ~50% (12 o’clock), then use the AVR remote / Main Zone app for day-to-day volume.
- Label patch panel ports and the AirPort Express’s switch port for future service.

-----

## 12. Quick Reference — Key Specs

|                             |Value                                                          |
|-----------------------------|---------------------------------------------------------------|
|Cabinet depth required       |17.7” (450mm)                                                  |
|Receiver footprint           |17.1”W × 5.94”H × 13.31”D, ~18.75 lb                           |
|Receiver rack height         |~4U (3.5U on a vented shelf)                                   |
|Min. shelf depth for receiver|~14”                                                           |
|Estimated total loaded weight|80–100+ lb (verify backing)                                    |
|Outdoor speaker (Main Zone)  |Polk Atrium 8 SDI, 8 ohm, 10–125W, 91 dB, single-speaker stereo|
|Garage monitors (Zone 2)     |Mackie CR3 pair, powered, RCA line-level from Zone 2 pre-out   |
|Patio speaker run            |16/4 (14/4 if >50 ft), outdoor/in-wall rated                   |
|CR3 outlet                   |One 120V receptacle at the CR3 shelf location                  |