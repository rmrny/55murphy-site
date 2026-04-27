---
name: 55 Murphy Rd renovation site
description: Quartz static site for renovation decisions, selections, BOM, and schedules — shared with partner Tara
type: project
---

Home renovation project at 55 Murphy Rd, Port Monmouth NJ. Riordan Family (Bob + Tara). Contractor is Brendan Corrigan / Jersey Shore Contracting Services. Proposal $660,164.

**Site structure (Quartz v4, GitHub Pages):**
- Homepage is decision-focused dashboard, not a flat link list
- Decisions hub tracks open items with urgency tiers
- BOM page tracks all owner purchases room-by-room with Kohler 40% trade discount
- Selections organized by floor (first-floor/, second-floor/, garage-exterior/)
- Every room now has a selection page — no more "Not Yet Started" rooms
- Technical reference (networking, smart home) is separated from decision content
- `reference/` folder is gitignored for local-only docs (PDFs, tile notes, takeoffs, cabinet BOM CSV)
- LaTeX plugin removed to avoid $ sign rendering issues in price tables

**Key design decisions made:**
- All bathroom fixtures: Kohler, Vibrant Brushed Moderne Brass (2MB) finish — except outdoor bath which is Brushed Nickel (BN)
- Flooring: AquaGuard Performance Cocoa Waterproof Laminate, 2,975 SF including cabana
- Interior doors: 2-Panel Top Round, Hollow Core — 32x80 interior, 24x80 closet
- Door hardware: Orger Octagonal Crystal Knob, Antique Bronze Vintage Rosette (Privacy/Passage)
- No ERV — exhaust fans + outside air openings (decided against, April 2026)
- No motorized window shades (decided against, April 2026)
- Kitchen sink: Kraus Workstation 32" KWU110-32/PGM Gunmetal PVD
- Tile schedule has 15% waste factor on all quantities
- Windows: white vinyl interior/exterior, manufacturer TBD (Andersen was placeholder)

**Kitchen cabinets (selected April 2026):**
- Base cabinets: Port & Bell Anna Caramel Harvest (ValuePlus) — stained birch, shaker
- Wall cabinets: Port & Bell Anna Snow White (ValueMax) — white painted, shaker, 42"H
- Supplier: Home Surplus (Keyport grab & go, or 7-day order)
- Full BOM with SKUs in kitchen.md and CSV at reference/Cabinets/55murphy-cabinet-bom.csv
- Island: east side (microwave base, 3-drawer, trash pullout), west side (4x BH18 + filler)
- Cove crown molding (LCV48 x5, ~18 LF)
- **Quoted:** Home Surplus QUO92860 — $10,315 total ($9,675 + tax), expires 05/25/2026. $5,785 under $16,100 allowance.
- Note: quote SKUs differ from selections in some places (site selections are correct, quote is budget placeholder)

**Kitchen appliances (updated April 2026):**
- Microwave changed from Frigidaire OTR to LG MSER2090S countertop ($240) in island base
- Range hood added: Thor Kitchen ARH36T 36" wall mount ($899, 550 CFM)
- Cooktop: Frigidaire Professional 36" Induction (confirm 48" base needed for 36" cooktop)

**Bathroom accessories (selected April 2026):**
- Vanity lights: Allen + Roth Meredith Gold — 2-light ($70) in primary & kids bath, 3-light ($80) in 1st floor bath
- Mirrors: Moon Mirror Dual Arch 24x36 (primary, $190 ea), Mercer41 Margulies Arch (kids, $140/pair), Moon Mirror Scalloped 22x30 (1st floor, $160), QueenFun Silver 24x32 (outdoor, $80)

**Countertops & shelving (selected April 2026):**
- Pantry: Hardwood Reflections Acacia shelving ($21/LF, 3 walls) + Acacia counter 10ft x 25"D ($450, cut to 66")
- Laundry: 2 Acacia pieces — one 10ft piece for upper, pantry cutoff for lower (6" height difference)
- Bob's office: Acacia 6ft x 39"D ($400) on Flexispot E7 Plus 4-leg frame ($500), 5x IKEA SEKTION 24x24x30 bases ($240 ea)
- Tara's office: refinished butcher block from Bob's current desk

**Exterior doors (selected April 2026):**
- Masonite 6-Panel Primed Steel 36x80 ($200 ea) for mud room, garage, cabana, outdoor bath
- Front entry, kitchen door, foyer French door, garage overhead still TBD

**Bathroom numbering:**
- Bathroom 1 = Second floor (has tub, Avec K-25830, shared/kids)
- Bathroom 2 = First floor (has shower)
- Primary Bath = Second floor master
- Outdoor Bath = Garage annex

**Tile assignments:**
- Bath 1 tub surround: Viva Antic Verde
- Bath 2 shower walls: Nara Blanco
- Primary shower walls: Albatross Sky
- Primary shower floor: Nolita Bianco
- All bathroom floors: Antico White 40x40
- Outdoor bath floor+shower: Aurelio Azul Hexagon
- Outdoor bath walls: Bright White Ice Subway
- Cabana baseboard: Bright White Ice Subway
