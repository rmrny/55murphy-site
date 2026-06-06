---
title: Mechanical Equipment Schedule
---

# Mechanical Equipment Schedule

> **Sync note:** Technical specs mirror the locked code-side basis in the companion code/permit repo `2026-010_55-Murphy_Port-Monmouth`. **Source of truth:** `docs/55Murphy_EnergyCompliance.md` §10 + `docs/55Murphy_DHW_CutSheetReview.md`. Update here when the code repo locks a change.

Single-condenser multi-zone heat pump basis — locked Rev B 2026-05-29. Supersedes the earlier 2-condenser (house + garage) scheme. **Garage is unconditioned** per current structural scope (2026-06-05 decision); FCU-1 / FCU-2 / ACCU-B removed from schedule. **Proposal HVAC allowance: $40,825**

## Outdoor Heat Pump (LG)

| Tag | Service | Cooling (Btu/h) | Heating @ 17 °F (Btu/h) | Manufacturer | Model | Notes | Status |
|-----|---------|----------------|------------------------|-------------|-------|-------|--------|
| ACCU-A | House (whole) — multi-zone | 54,000 (4.5 ton nominal) | 48,500 @ 17 °F (AHRI cert) | LG Electronics | KUMXB541A | All-electric. AHRI **SEER2 18.5 / HSPF2 9.3** → equivalent SEER 19.9 / HSPF 10.9. Satisfies R408.2.2 More Efficient HVAC package with margin. | SELECTED |

## Indoor Air Handlers (LG, KUMXB541A-compatible)

Ducted air handlers paired with the KUMXB541A multi-zone outdoor. Specific LG indoor model TBD per refrigerant routing design (multi-zone compatibility list).

| Tag | Service | Refrigerant | Cooling (Btu/h) | Manufacturer | Model | Status |
|-----|---------|-------------|----------------|-------------|-------|--------|
| AHU-1 | 2F (Primary BR, Kids Rm 1/2, Baths, Laundry, Sitting, Stair, Walk-In Closet) | R32 | 24,000 (2 ton) | LG Electronics | TBD per multi-zone compatibility | SELECTED |
| AHU-2 | 1F N + Addition (Kitchen, Living, Dining, Play Room, Pantry, Office Rm 17) | R32 | 24,000 (2 ton) | LG Electronics | TBD per multi-zone compatibility | SELECTED |
| AHU-3 | 1F S (Foyer, Guest BR3, Bob's Office, Mud Rm, Utility, Bath23) | R32 | 18,000 (1.5 ton) | LG Electronics | TBD per multi-zone compatibility | SELECTED |

**Indoor:outdoor ratio:** 66k indoor / 54k outdoor = **122%** (within LG multi-zone allowance, typically up to 130%).

**No aux strip heat** — brief shortfall at 99.6% design DB (10.8 °F) accepted as comfort tradeoff per owner direction; <20 hr/year at design DB typical in coastal NJ. Heating coverage 94% at design DB; ~97% expected at Rev C 68 °F setpoint.

## Ventilation

Per-system continuous outside air distribution + local exhausts.

### Continuous OA (per AHU return injection)

| Tag | Source | CFM (continuous) | Manufacturer | Model | Status |
|-----|--------|------------------|-------------|-------|--------|
| OA-1 | AHU-1 (2F) | 60 | Panasonic | FV-1115VKL3 | SELECTED |
| OA-2 | AHU-2 (1F N + Addition) | 60 | Panasonic | FV-1115VKL3 | SELECTED |
| OA-3 | AHU-3 (1F S) | 30 | Panasonic | FV-1115VKL3 | SELECTED |

**Total continuous OA:** 150 CFM ≥ ASHRAE 62.2-2022 required 141.7 CFM ✓.

### Local exhaust (M1505.4)

| Service | CFM | Mode | Notes |
|---------|-----|------|-------|
| Kitchen range hood | ≥100 | Intermittent | M1505.4.4 — required regardless of R303 path. Captured as WS-OI-7. |
| Bath 2 (1F) | ≥50 / 20 cont | Intermittent or continuous | M1505.4.4 |
| Primary Bath (2F) | ≥50 / 20 cont | Intermittent or continuous | M1505.4.4 |
| Bath 2 (2F) | ≥50 / 20 cont | Intermittent or continuous | M1505.4.4 |
| Laundry | per M1502 dryer + M1505.4.4 general | — | Dryer vent + general exhaust |
| Outdoor (cabana) bath | ≥50 | Intermittent | M1507.4 — vent-only (unconditioned, summer-only) |

## Open Decisions (carried)

| Item | Cost | Status |
|------|------|--------|
| ~~ERV Upgrade (centrotherm piping)~~ | ~~$8,500 (piping only — ERV unit owner supplied)~~ | **Not proceeding — REJECTED** |
| Fresh air into 2nd-floor return with MERV30 filter | Included | SELECTED |

## Water Heater

Replaces earlier dual gas tankless cascade scheme (RTGR199N1 × 2). All-electric basis — no IRC Ch 24 fuel-gas scope, no gas service connection to dwelling.

| Tag | Type | Capacity | Manufacturer | Model | Location | Status |
|-----|------|----------|-------------|-------|----------|--------|
| HWH-1 | Hybrid Electric HPWH | 80 gal nominal / 75 gal DOE storage / **88 gal FHR** | Bradford White | AeroTherm G2 **RE2HP8010** | Utility room | SELECTED |

**Efficiency:** UEF 4.00. Satisfies R408.2.3 Reduced Energy Use Service Water Heating (≥2.0 threshold) with margin.

**Distribution:** Hot water recirculation loop with R-3 pipe insulation on ≥3/4" lines per IECC R403.5.2. Recirculation control TBD per developed-length calc (utility room HPWH → 2nd-floor Primary Bath, paired with NSPC §10.15.2.1 100-ft trigger).

**Install requirements (HPWH-specific):**
- Operating ambient ≥37 °F — utility room must stay warm year-round (else unit defaults to electric resistance only)
- Floor drain at HPWH for condensate
- 30 A / 240 V / 2P breaker
- Top-mounted air filter access — ≥24" service clearance above
- Duct-ready intake/exhaust if utility room volume insufficient for HP intake

See `docs/55Murphy_DHW_CutSheetReview.md` in the code repo for full cut-sheet review + alternate-option analysis (gas tankless cascade scored but rejected to preserve all-electric basis).
