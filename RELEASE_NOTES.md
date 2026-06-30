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

## v1.0.3 — Top P/L Scale Fix (2026-06-28)

- Fixed the row of P/L values across the top of the chart disappearing after you
  zoom or pan — it now re-renders at the correct tick positions for the current
  view.

## v1.0.2 — Chart & Layout Refinements (2026-06-27)

- Profit/loss shading fixed: the loss area below the zero line is now correctly
  shaded red — including narrow regions such as butterflies — and the
  profit/loss fills extend to the chart edges and stay filled when you zoom or
  pan out.
- The chart x-axis now shows real strike prices instead of fractional values,
  and an empty chart opens on a sensible whole-number price range.
- With no live SPX price, the chart centres on your position's strikes instead
  of pushing it to one side.
- Strategy selection buttons are arranged in two rows to take less horizontal
  space.
- Action buttons moved into the menu bar — File (Load/Save Strategy), Tools
  (Intrinsic Value Calculator, Optimize), Clean Up (Clear Position, Clear All,
  Reset Defaults), and Configuration.
- Tighter spacing above the spread inputs for combo strategies, and a larger
  default window so the full panel (through the POP section) is visible without
  scrolling.

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
