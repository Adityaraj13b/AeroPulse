# AeroPulse-X Stitch UI integration

This package applies the approved Stitch visual direction to the working
AeroPulse-X FastAPI dashboard without replacing the API or telemetry logic.

## Files changed

- `static/index.html`
  - Adds the fixed GCS navigation rail, mission header, UTC clock and section
    navigation.
  - Preserves the existing element IDs, API calls, WebSocket connection,
    controls, charts and inline application logic.
- `static/stitch-theme.css`
  - Provides the complete offline GCS visual theme and responsive layouts.
  - Uses no Tailwind, Google Fonts, external images or CDN resources.

## Copy into your local repository

From `C:\Users\ASUS\new\AeroPulse`, copy both files while you are on the
`ui/stitch-redesign` branch:

```powershell
Copy-Item "<extracted-package>\static\index.html" ".\static\index.html" -Force
Copy-Item "<extracted-package>\static\stitch-theme.css" ".\static\stitch-theme.css" -Force
```

Run the dashboard:

```powershell
python run.py
```

Open `http://127.0.0.1:8000`. If port 8000 is occupied, use:

```powershell
python -m uvicorn app.main:app --host 127.0.0.1 --port 8001
```

## Verification

Confirm that these actions still work:

1. Analyze Snapshot
2. Run Mission Replay
3. Start Live Stream
4. Model Validation
5. What-If Mission Profile comparison
6. Hardware sliders and fault controls

## Commit the redesign

```powershell
git status
git add -- static/index.html static/stitch-theme.css docs/STITCH_UI_INTEGRATION.md
git commit -m "Redesign AeroPulse dashboard with Stitch GCS theme"
git push -u origin ui/stitch-redesign
```

## Validation completed

- Existing AeroPulse test suite: 65 tests passed.
- Inline JavaScript syntax validated.
- DOM IDs checked for duplicates.
- No backend Python or model files changed.
