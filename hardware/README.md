# Hardware release

## Current recommended print: REV5

Use [REV5 files](wrist_constellation_REV5/) for the two-part wrist fixture with
two circumferential rubber-band grooves and no magnet holes. The v4 magnetic
design below is historical, not the default print.

- Print the two REV5 STL halves at original scale.
- Use [matching left/right marker strips](wrist_constellation_REV5/REV5_groove_fit_connected_strips_A4.pdf), at 100% / actual size, with fit-to-page disabled.
- Apply soft foam inside to accommodate different wrist sizes. Keep mating
  surfaces clear and the rigid halves fully seated; do not force the shell open.
- Place one rubber band in each groove to hold the halves together. Bands must
  not cover markers. Fit should be stable and comfortable; stop if painful or numb.
- Recalibrate the physical constellation after assembly or sticker changes.
  The supplied REV5 nominal JSON files are CAD starting points, not measured
  calibration. Small/large black-square sizes are 21.5/30.75 mm.

![REV5 marker placement](wrist_constellation_REV5/REV5_fit_preview.png)

`wrist_constellation_v4/` retains the older magnetic design for historical reference only. Use REV5 for the current print.

The root-level sheets in `marker_layouts/` are older layouts; use the matching REV5 PDF above for the current shell. Print at 100% / actual size and measure the black squares. Nominal JSON is not a substitute for calibrating the assembled constellation.

`marker_layouts/calibrated_release/` contains the measured rigid constellation geometry used for the reported final wrist experiments. These files reproduce that particular assembled pair of fixtures; they are not universal replacements for calibrating a newly printed and assembled fixture. Marker IDs and corner coordinates are unchanged from the experiment configuration, while local absolute source paths have been removed for anonymous release.

`charuco_A4.pdf` is the camera-calibration target. Intrinsics are valid only for the same lens, focus, resolution, crop, stabilization, and camera mode used during calibration.
