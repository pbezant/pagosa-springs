# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static HTML field guide for Pagosa Springs, Colorado. Three self-contained HTML files — no build tools, no server required. Open directly in a browser (`open index.html`).

## Files

- `index.html` — Landing page; links to the two activity guides
- `fly-fishing.html` — 13 wade fishing spots + 10 fly patterns + fly shop resources
- `hiking.html` — 12 trails (Easy → Expert) + gear guide + local resources

## Styling

All CSS lives in `<style>` blocks inside each file. Never extract to a separate file. Each page has its own `:root` color palette:

- `index.html` — warm parchment/gold (`--dawn`, `--dust`, `--cream`, `--stone`)
- `fly-fishing.html` — river blue / forest (`--river`, `--water`, `--moss`, `--bark`)
- `hiking.html` — forest green / alpine (`--aspen`, `--fern`, `--lichen`, `--forest`)

Typography: Playfair Display (headings), Libre Baskerville (body), DM Mono (labels/metadata) — loaded via Google Fonts CDN.

## Cross-Reference System

Several fishing spots and hiking trails share the same location. Cards on each page link to the matching entry on the other page.

**Anchor ID conventions:**
- Fishing spot cards: `id="spot-01"` through `id="spot-13"` (on `.spot-card` divs in `fly-fishing.html`)
- Hiking trail cards: `id="trail-01"` through `id="trail-12"` (on `.trail-card` divs in `hiking.html`)

**Active cross-references:**

| Fishing Spot | Links to Hiking Trail |
|---|---|
| spot-01 (San Juan Town Park) | trail-01 (San Juan Riverwalk) |
| spot-05 (Piedra Lower Canyon) | trail-05 (Piedra Family) |
| spot-06 (Williams Creek) | trail-10 (Williams Creek Lower) |
| spot-08 (Blanco River) | trail-12 (Blanco Basin) |
| spot-10 (Piedra Upper Trail) | trail-08 (Full Piedra River) |
| spot-11 (Turkey Creek) | trail-07 (Turkey Creek Trail) |

Fishing cards use a `🥾` badge and `.spot-link.xref` links pointing to `hiking.html#trail-XX`.  
Hiking cards use a `🎣` badge and `.trail-link.xref` links pointing to `fly-fishing.html#spot-XX`.

## Google Maps Links

Each card has a directions link. Two link formats are used:
- `maps.google.com/?q=lat,lng` — coordinate-based (most spots)
- `google.com/maps/place/?q=place_id:ChIJ...` — place ID (more accurate for named places)

The "Open in Google Maps" banner buttons link to a general area view at `@37.27,-107.09,11z`. To turn these into an actual saved list, replace with a Google My Maps URL once the shared map is created.

## JavaScript

Only `hiking.html` has a `<script>` block — it powers the interactive elevation profile tooltip in the hero. All other interactivity is CSS-only.
