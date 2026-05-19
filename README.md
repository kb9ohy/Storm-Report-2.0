# OCARC Skywarn Reports 2.0

Storm Report 2.0 is a replacement concept for the Google Form -> Google Sheet -> map workflow.

This first version is a static GitHub Pages app with:

- Mobile-friendly storm report entry
- Required structured coordinates
- Event-specific fields for hail, wind, flooding, power outages, and snow/ice
- Live report map
- Review queue with status changes
- CSV export
- Local browser storage for prototype/demo use

## Why This Is Better Than Forms + Sheets

The report is structured before it reaches the map. That prevents common issues like inconsistent coordinates, blank mapping fields, ambiguous event types, and reports that need manual cleanup before they are usable.

## Current Storage

Reports are currently saved in the browser's `localStorage`. This is intentional for the first build because it lets the interface be tested without a paid or configured backend.

For operational use, replace the storage functions in `app.js` with Firebase, Supabase, or another API:

- `loadReports()`
- `saveReports()`
- `handleSubmit()`
- `updateStatus()`

## Recommended Backend Upgrade

Recommended production path:

1. Add Firebase or Supabase authentication for approved spotters.
2. Save reports to a cloud database instead of local browser storage.
3. Add an admin/review role for net control.
4. Optionally export verified reports to Google Sheets for archive/reporting.
5. Add live subscription updates so all users see new reports immediately.

## Local Testing

Serve the files with any static web server:

```bash
python3 -m http.server 8010 --bind 127.0.0.1
```

Then open:

```text
http://127.0.0.1:8010/
```
