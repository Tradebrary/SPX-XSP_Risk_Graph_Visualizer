# SPX-XSP Options Visualizer — Release Notes

Release process (each release):
1. Update `APP_VERSION` in `Options_Risk_Graph/OptionsRiskGraphGUI.py` (single source of truth).
2. `python build_all.py` (regenerates `version.iss` + both exes).
3. Compile the installer: `ISCC.exe OptionsRiskGraph.iss` → `installer/OptionsRiskGraphSetup-<version>.exe`.
4. Add an entry below, commit with message `v<version> <summary>` and tag `v<version>`.
5. Create a GitHub Release for the tag and attach the installer exe (and these notes).

The Whop product page links to the permanent **Releases — latest** URL, so the
link never changes between versions.

---

## v1.0.1 — Clean First-Run Experience (2026-06-11)

- Fresh installations now start with an empty broker-accounts list — add your
  own IB/Tastytrade accounts via Configuration (removed internal developer
  account placeholders).

## v1.0.0 — First Stable Release (2026-06-10)

Initial public release.

**Highlights**
- Dual-instrument risk graph: SPX strategies hedged with XSP, with the combined
  P/L at expiration plotted alongside each position.
- 13 strategy types per instrument (single legs, verticals, iron condor,
  condors, butterflies, straddle, strangle, custom 4-leg) plus an optional
  additional XSP hedge position.
- Interactive chart: draggable strike lines, expected-move band, POP, expected
  value, max profit/loss, and BPR statistics.
- Live data from Tastytrade and Interactive Brokers (fetch + streaming with
  stale/fresh price indicators), or offline CSV option chains with bad-data
  detection.
- Strategy optimizer sweeping center/width/quantity with POP / expected value /
  P/L-ratio / weighted targets and BPR & max-loss filters.
- Per-source, per-instrument commission model and slippage handling.
- Whop license-key activation (up to two devices per key, deactivate-to-move),
  installer with bundled User Guide, Quick Start Guide, and legal documents.
- Update notifications: quiet check at startup plus About → Check for Updates,
  pointing to the GitHub download page when a newer version is published.
- User data stored under %APPDATA%\OptionsRiskGraph (survives reinstalls; no
  admin rights needed).
