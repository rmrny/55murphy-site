---
name: Document existing AV / electronic gear, not just new purchases
description: For 55murphy-site, capture existing components being relocated (model, status, power/cable needs) — they drive pre-drywall rough-in even though they cost $0
metadata:
  type: feedback
---

When documenting AV, networking, or other electronic systems in `content/selections/`, list **existing gear being relocated** explicitly — model numbers, condition, and power/signal needs — not just new purchases. Treat their requirements as part of pre-drywall rough-in scope.

**Why:** Bob confirmed value of this approach after I documented existing AV gear in both the garage AV rack and the sitting room (Denon AVR-X1300W, Definitive Tech BP-9020 / CS-9040 / ProSub 600, Mackie CR3s, AirPort Express, Polk Atrium 8). A BoM that only lists new purchases hides real rough-in dependencies — outlets at each powered speaker, network drops for HEOS/AirPlay receivers, conduit runs to speaker positions, ventilation if a receiver lives in a cabinet, etc. Renovation drywall closes in a few weeks; missing rough-in for "free" existing gear becomes expensive later.

**How to apply:**
- When the user mentions existing equipment in a room context, prompt for: model, where it'll sit, whether it needs AC power, whether it needs network/signal cabling, whether it's confirmed working.
- Add an **Existing Gear** table to the room's selection doc (see `selections/garage-av-rack.md` Section 4 and `selections/second-floor/sitting.md` AV section for the established pattern).
- List existing gear in budget/BOM at $0 with a note like "Existing relocated gear (model list)" so the cost line stays accurate but the gear is still visible.
- Add corresponding **Rough-In Requirements** entries: outlets near each powered component, network drops, conduit/smurf tube to TBD speaker positions, ventilation if enclosed.
- If a component's status is uncertain ("might be broken"), document it anyway and plan rough-in as if a working replacement of similar form factor will be installed — the rough-in stays valid either way.

Related: [[project_garage_av_rack]] (Denon X1300W + Mackie CR3 pattern), [[feedback_rack_electrical]] (rack outlet standard).
