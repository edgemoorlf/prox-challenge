# Source Material Inventory

A page-level map of `files/`. Not a digest of the technical content — a map of where
things are and what form they take.

## Method

Every page was rendered to PNG at 100 DPI and looked at. Classification is from the
rendered image, not from text extraction.

The `Visual-only` flag was then **verified**, not estimated: for each page carrying
values or labels, the page's text layer was searched for those exact strings. A page is
flagged `Yes` when the information on it is unrecoverable from the text layer alone —
either the characters are absent entirely (outlined vector art, raster screenshots,
photos) or the characters survive but their meaning is positional (a callout label whose
only job is to point at a specific socket).

## Summary

**Total pages: 51** — `owner-manual.pdf` 48, `quick-start-guide.pdf` 2, `selection-chart.pdf` 1.

In `owner-manual.pdf`, PDF page number equals the printed page number (cover = 1).

### Count by primary content type

| Type | Count |
|---|---|
| mixed | 30 |
| labeled-diagram | 10 |
| prose | 4 |
| decision-matrix | 4 |
| table | 1 |
| schematic | 1 |
| parts-list | 1 |
| photo | 0 |
| **Total** | **51** |

No page was left UNCLEAR.

### Pages flagged visual-only — 37 of 51 (73%)

- **`owner-manual.pdf` (34):** 6, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 19, 20, 21, 22,
  23, 24, 25, 26, 27, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 45, 47
- **`quick-start-guide.pdf` (2):** 1, 2
- **`selection-chart.pdf` (1):** 1

Three findings worth carrying into design:

1. **`selection-chart.pdf` has a zero-character text layer.** The entire process-selection
   matrix is one raster image. Text extraction returns nothing at all.
2. **`quick-start-guide.pdf` is effectively textless.** Page 2's text layer is 60
   characters — a footer and a logo. All four cable-setup procedures are outlined vector
   art. Page 1 yields scattered part labels but none of the six numbered steps.
3. **The duty-cycle clock graphics on pages 19, 23, and 29 are raster.** None of their
   amperage or percentage values appear in those pages' text layer. The same values *do*
   exist in extractable form in the page 7 specification table, so the manual as a whole
   does not lose them — but any pipeline that answers a duty-cycle question from pages 19
   or 29 without reading the image is reading blanks.

The inverse also held in one place worth noting: the page 7 specification tables are fully
present in the text layer, including every duty-cycle pair. That page looked like an image
and is not one.

---

## owner-manual.pdf

| Page | Type | What is on it | Visual-only |
|---|---|---|---|
| 1 | mixed | Cover: title block, product photo, save-manual notice, unpacking warning | No |
| 2 | mixed | Table of contents, warning-symbol definitions table, start of general safety list | No |
| 3 | prose | Fume and gas safety, arc ray safety — numbered lists with two hazard pictograms | No |
| 4 | prose | Electrical safety and fire safety — numbered lists | No |
| 5 | prose | Welder use and care, maintenance, gas cylinder safety | No |
| 6 | mixed | Grounding, extension and replacement cord rules; symbology table pairing machine icons with their meanings | **Yes** |
| 7 | table | Three specification tables — MIG, TIG, Stick — at 120V and 240V | No |
| 8 | labeled-diagram | Front panel controls, callouts to knobs, buttons, LCD, power switch, and each socket | **Yes** |
| 9 | labeled-diagram | Interior controls, callouts to wire feed mechanism, spool, tensioner, and internal sockets | **Yes** |
| 10 | mixed | Wire spool setup steps 1–5 with power switch, door latch, and 1–2 lb spool loading illustrations | **Yes** |
| 11 | mixed | Spool setup steps 6–11 with exploded 10–12 lb spool stack, unwind-direction arrow, tensioner release | **Yes** |
| 12 | labeled-diagram | Feed roller change sequence A–D with groove-size markings for solid-core and flux-cored | **Yes** |
| 13 | mixed | Gun cable connector correct/incorrect insertion comparison, and DCEN flux-cored polarity setup illustration | **Yes** |
| 14 | mixed | DCEP solid-core polarity setup, then gas cylinder, regulator, and hose connection sequence | **Yes** |
| 15 | mixed | Wire threading steps 18–23 with hold-wire, idler arm latch, and nozzle/contact tip illustrations | **Yes** |
| 16 | mixed | Danger notice, power input socket, cold wire feed switch and wire protrusion illustrations | **Yes** |
| 17 | mixed | Drive tension test against wood block, then optional spool gun setup diagram | **Yes** |
| 18 | mixed | Basic wire welding intro prose, PPE pictograms, keep-tip-clear warning illustration | No |
| 19 | mixed | Duty cycle explanation, two rated duty cycle clock graphics, weld setup and ground clamp illustrations | **Yes** |
| 20 | mixed | Power cord steps, control panel diagram, and LCD screenshots for polarity/gas, diameter/thickness, auto weld | **Yes** |
| 21 | mixed | Optional settings list with five LCD screenshots, and shielding gas asphyxiation warning | **Yes** |
| 22 | labeled-diagram | Bead types, gun angle diagrams for fillet and butt joints, push/drag angle, CTWD illustration | **Yes** |
| 23 | mixed | Overheat warning screen, duty cycle reminder graphics, shutdown and storage sequence illustrations | **Yes** |
| 24 | labeled-diagram | TIG setup — cable connection diagram for torch, ground, foot pedal, and gas, with four steps | **Yes** |
| 25 | mixed | TIG shielding gas connection sequence, and rear panel power input illustration | **Yes** |
| 26 | mixed | Tungsten electrode sharpening and TIG torch assembly, with exploded torch diagram | **Yes** |
| 27 | labeled-diagram | Stick setup — cable connection diagram and rear panel power input illustration | **Yes** |
| 28 | mixed | Basic TIG/Stick intro prose, PPE pictograms, keep-tip-clear warning illustration | No |
| 29 | mixed | TIG and Stick duty cycle explanation, four rated duty cycle clock graphics, weld setup illustrations | **Yes** |
| 30 | mixed | TIG procedure steps, control panel diagram, LCD screenshots for gas, diameter/thickness, amperage | **Yes** |
| 31 | mixed | TIG optional settings screenshots, then welding technique steps 10–19 and post-use checklist | **Yes** |
| 32 | mixed | Stick procedure steps, control panel diagram, LCD screenshots for electrode type, diameter/thickness, amperage | **Yes** |
| 33 | mixed | Stick optional settings screenshots, arc ignition steps, and post-use checklist | **Yes** |
| 34 | mixed | Strike test procedure with good/poor weld illustrations, and weld cleaning tool diagram | **Yes** |
| 35 | labeled-diagram | Wire weld penetration cross-sections and six example bead diagrams, each with its correction | **Yes** |
| 36 | mixed | Wire weld penetration profiles, bend at joint, slag coat, weld not adhering — images with cause/solution lists | **Yes** |
| 37 | mixed | Wire weld porosity, spatter, crooked bead, burn-through — bead images with cause/solution lists | **Yes** |
| 38 | labeled-diagram | Stick weld penetration cross-sections and seven example bead photographs, each with its correction | **Yes** |
| 39 | mixed | Stick weld penetration profiles, weld not adhering, bend at joint — images with cause/solution lists | **Yes** |
| 40 | mixed | Stick weld slag, porosity, crooked bead, spatter, burn-through — bead images with cause/solution lists | **Yes** |
| 41 | mixed | Maintenance checklist, MIG nozzle and contact tip cleaning, LCD screen cover replacement diagrams | No |
| 42 | decision-matrix | MIG/flux-cored troubleshooting table — problem, possible causes, likely solutions | No |
| 43 | decision-matrix | Troubleshooting table continued — no power, dark LCD, no arc ignition, porosity | No |
| 44 | decision-matrix | TIG/Stick troubleshooting table — problem, possible causes, likely solutions | No |
| 45 | schematic | Full wiring schematic — PFC, IGBT stages, MCU board, LCD, remote board, fans, sockets | **Yes** |
| 46 | parts-list | Numbered parts list, 61 entries, with repair and liability disclaimer | No |
| 47 | labeled-diagram | Exploded assembly diagram, every component keyed to a part number from page 46 | **Yes** |
| 48 | prose | Limited 90-day warranty terms and company address | No |

## quick-start-guide.pdf

| Page | Type | What is on it | Visual-only |
|---|---|---|---|
| 1 | mixed | Six illustrated quick-start steps — cables, spool, nozzle/tip, feed tension, unplug, settings — plus two warnings | **Yes** |
| 2 | labeled-diagram | Four cable setup panels — Stick, MIG, Flux-Cored, TIG — each numbered against a machine illustration | **Yes** |

## selection-chart.pdf

| Page | Type | What is on it | Visual-only |
|---|---|---|---|
| 1 | decision-matrix | "How to Choose a Welder" — six questions routing to FCAW/MIG/Stick/TIG, a MIG-vs-flux-cored comparison table, and a duty cycle example | **Yes** |
