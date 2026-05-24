---
name: Garage AV / Network Rack
description: 12U garage cabinet housing existing Onkyo receiver + network switch/patch panel, drives single patio speaker — supersedes earlier 6U Tecmojo plan
metadata:
  type: project
---

Garage AV / Network Rack build spec at `content/selections/garage-av-rack.md` (2026-05-23).

**System purpose:** AirPlay 2 audio to single outdoor (patio/deck) speaker via existing Onkyo TX-SR606, plus home network distribution. Existing gear being relocated into new construction.

**Key design decisions:**
- **Enclosure: NavePoint 12U, 23.6"/600mm deep** — supersedes the 10" 6U Tecmojo cabinet that was in earlier networking.md revisions. The Onkyo receiver is 14.75" deep so the 450mm/17.7" version won't close.
- **Active thermal management required** — receiver is fanless and heat-sensitive. Spec'd AC Infinity CLOUDPLATE T7 (thermostat-controlled) with thermostat engaging at ~85–90°F. Open U's left between hot/cool gear are intentional cooling design — don't pack.
- **Garage switch + patch panel live inside this same cabinet** (1U each, [TRACKED] in spec but [[project_55murphy]] BOM tracks them under Networking). Closes the "garage switch location" open decision in [[networking.md]].
- **AirPort Express wired-only** — cabinet is a Faraday cage; Wi-Fi disabled, Ethernet from switch, bridge mode. AirPlay 2 over Ethernet is confirmed supported.
- **Single-speaker stereo** — Polk Atrium 8 SDI has dual-tweeter array and single/dual switch; one unit reproduces full stereo for the single patio zone. 16/4 (or 14/4 if >50 ft) outdoor/in-wall-rated, direct-burial for buried portion.

**Existing gear (relocate, $0):** Onkyo TX-SR606, Apple AirPort Express A1392 (2nd gen, AirPlay 2 capable after 7.8+ firmware), Polk Atrium 8 SDI.

**New purchases (~$488):** 12U NavePoint cabinet, CLOUDPLATE T7, vented shelves, 1U PDU, RCA/3.5mm cable, 16/4 speaker wire, brush panel/cage nuts.

**Rough-in items (added to decisions.md item G as contractor clarification):**
- 3/4" plywood backer at cabinet location (loaded 80–100+ lb)
- Dedicated 120V outlet behind/inside cabinet footprint
- 1" conduit/smurf tube from cabinet to attic for future pulls
- 16/4 outdoor-rated speaker run from rack to patio (direct-burial for any buried segment)
- Cat6 home runs terminated at the rack patch panel
- Prefer interior (conditioned-adjacent) wall over exterior; keep out of direct sun

**Why this matters for [[project_55murphy]]:** The garage AV rack consolidates AV + network in one wall cavity, which simplifies rough-in and removes the second cabinet the earlier networking.md plan had. It also resets the garage switch decision from "TBD location" to "inside the 12U cabinet."

**How to apply:** When discussing the garage switch, patch panel, or any garage low-voltage rough-in, treat the 12U NavePoint cabinet as the single home for that gear. The BOM total shifts: networking subtotal drops $106 (no Tecmojo, no 10" patch panel), AV section adds ~$488.
