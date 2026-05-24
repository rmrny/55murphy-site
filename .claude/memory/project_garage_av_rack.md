---
name: Garage AV / Network Rack
description: 12U garage cabinet housing Denon AVR-X1300W + network switch/patch panel, two audio zones (patio + Mackie CR3s) — supersedes earlier 6U Tecmojo plan
metadata:
  type: project
---

Garage AV / Network Rack build spec at `content/selections/garage-av-rack.md`. Updated 2026-05-24 with corrected receiver model (Denon AVR-X1300W, not Onkyo) and addition of Mackie CR3s as Zone 2.

**System purpose:** AirPlay 2 audio to two zones via existing Denon AVR-X1300W:
- Main Zone (speaker level) → single Polk Atrium 8 SDI on patio/deck
- Zone 2 (RCA pre-out, line-level) → Mackie CR3 powered bookshelf monitors on shelf near the rack for garage music

Plus home network distribution. All AV gear is existing, being relocated.

**Key design decisions (current):**
- **Enclosure: NavePoint 12U, 17.7"/450mm deep** — downsized from 600mm once we corrected the receiver model. Denon AVR-X1300W is 13.31" deep (vs Onkyo's 14.75"), so 450mm now has adequate clearance.
- **No active rack cooling needed** — Denon has its own internal cooling vents and isn't the heat-sensitive design the Onkyo was. Dropped the AC Infinity CLOUDPLATE T7. Kept as conditional fallback in the doc if garage exceeds ~95°F.
- **Garage switch + patch panel live inside this same cabinet** (1U each, [TRACKED] in spec but [[project_55murphy]] BOM tracks them under Networking). Closes the "garage switch location" open decision in `networking.md`.
- **AirPort Express wired-only** — cabinet is a Faraday cage; Wi-Fi disabled, Ethernet from switch, bridge mode. Still needed because the AVR-X1300W has AirPlay 1 only (AirPlay 2 was never added to the X1300W — first hit the X1400H and later).
- **Single-speaker stereo (patio)** — Polk Atrium 8 SDI has dual-tweeter array and single/dual switch; one unit reproduces full stereo for the single patio zone. 16/4 (or 14/4 if >50 ft) outdoor/in-wall-rated, direct-burial for buried portion.
- **Zone 2 → Mackie CR3** — CR3s are *powered* monitors (built-in amp), so they need line-level RCA from the Denon's Zone 2 pre-out, not speaker-level. Set Zone 2 Volume Level = Variable so the AVR controls CR3 volume. Short RCA run, no in-wall pull needed since CR3s sit near the rack.

**Existing gear (relocate, $0):** Denon AVR-X1300W, Apple AirPort Express A1392 (2nd gen, AirPlay 2 capable), Polk Atrium 8 SDI, Mackie CR3 pair.

**New purchases (~$356):** 12U NavePoint cabinet (450mm), vented shelves, 1U PDU, RCA/3.5mm + RCA stereo cables, 16/4 speaker wire, brush panel/cage nuts.

**Rough-in items:**
- 3/4" plywood backer at cabinet location (loaded 80–100+ lb)
- Dedicated 120V outlet behind/inside cabinet footprint
- Additional 120V outlet at the CR3 shelf location (powered monitors need their own AC)
- 1" conduit/smurf tube from cabinet to attic for future pulls
- 16/4 outdoor-rated speaker run from rack to patio (direct-burial for any buried segment)
- Cat6 home runs terminated at the rack patch panel
- Prefer interior (conditioned-adjacent) wall over exterior; keep out of direct sun

**Why this matters for [[project_55murphy]]:** The garage AV rack consolidates AV + network in one wall cavity, which simplifies rough-in. It also resets the garage switch decision from "TBD location" to "inside the 12U cabinet."

**How to apply:** When discussing the garage switch, patch panel, or any garage low-voltage rough-in, treat the 12U NavePoint cabinet as the single home for that gear. Two powered-equipment outlets are needed (rack + CR3 shelf), not just one. If the receiver model ever comes up again, it's the **Denon AVR-X1300W** — an earlier revision incorrectly listed Onkyo TX-SR606.
