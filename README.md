# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-23T05:44:48Z
- **Source Commit**: [`bb986996134217a13294d33e3200a4d9855ccd2b`](https://github.com/keunwoochoi/seoulunderground.live/commit/bb986996134217a13294d33e3200a4d9855ccd2b)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23423233639)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: venue map with Leaflet/OSM (PR E) (#127)

* feat: venue map — SVG map with pins + Nominatim geocoding (PR E draft)

- etl/geocode_venues.py: batch-geocode venue addresses via Nominatim (free,
  no API key); 18/72 Seoul venues now have lat/lon
- VenueMap.tsx: pure SVG map — Seoul bounds, Han River polygon, neighborhood
  labels, venue pins from lat/lon; hover tooltip; click pin → switch to card
  view + scroll to venue
- MapPinIcon.tsx: new map pin SVG icon
- App.tsx: venuesViewMode extended to 'card' | 'table' | 'map'; map button
  in view toggle (venues tab only); venue cards get id for scroll-to
- i18n.ts: map_view key (en: Map, ko: 지도, de: Karte)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix(pr-e): replace hand-drawn SVG map with Leaflet + OSM tiles

- Rewrites VenueMap to use Leaflet.js with OpenStreetMap tiles
  (free, no API key, proper rendered map with zoom/pan)
- Fixes type mismatch: Venue.ig_handle is now optional to match App.tsx
- Removes unused pts() function
- Fixes onVenueClick scroll bug: strip leading @ from handle
- Fixes onVenueClick timing: useEffect + venueToScrollTo state instead of setTimeout
- Fixes preferences.ts: getViewModePreference/saveViewModePreference now support 'map'
- Tightens geocode_venues.py exception handling to specific exception types

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat(map): standout pins, in-map popup panel, language-specific tiles

- Pins: changed to bright orange-red (#e85d26) for high visibility
- Click behavior: clicking a pin shows an inline popup panel on the map
  (name, address, subway, IG link, Google Maps link) — no longer navigates
  to venue card
- Language-specific tiles: ko → OSM standard (Korean labels); en/de → Carto
  Voyager (Latin-script labels)
- Popup panel localized via t(lang, key)
- Removes onVenueClick prop and venueToScrollTo state (no longer needed)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix(map): markers missing on page refresh + address localization

Split single map useEffect into two:
- Effect 1: map init + tile layer (deps: [lang])
- Effect 2: marker management (deps: [venues, lang])

Effect 1 ran at mount with empty venues; Effect 2 now correctly fires
when the async venues API response arrives, adding all markers.

Address in the popup panel already uses i18n_data.address_text[lang]
with location_text fallback — confirmed correct for all languages.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat(map): map as overlay toggle + geocoder floor-prefix fix

Map is now an independent toggle above the venue list (card/table always
visible below). Clicking the pin icon in the toolbar shows/hides the map;
the card/table view mode is unaffected.

Removes 'map' from venuesViewMode type — back to 'card' | 'table'.

Also fixes geocode_venues.py: retries with floor/basement prefix stripped
("B1, ", "2F, ", "3층, ") when the first Nominatim attempt fails.
Geocoded oleojazzpub and teddy.valley as a result.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix(map): use VenueMaster locations[0] coords for venues missing lat/lon

39 of 72 masters have lat/lon in locations[0] that were being ignored.
Adds venuesForMap memo that merges master coordinates + i18n address text
into filteredVenues before passing to VenueMap, bringing mapped count
from ~18 to ~39.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

---------

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
