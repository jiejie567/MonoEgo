# Compact result sources

## Camera reference

`camera_reference/scores.csv` contains the compact method-by-sequence table used to generate the reported camera-reference comparison. `all_metrics.json` and `paired_support.json` preserve alignment and paired-support summaries without private filesystem paths or raw recordings.

Odin odometry is used only as a camera reference. MonoTag does not consume it during reconstruction. Metric methods are evaluated after SE(3) alignment; scale-free monocular baselines are additionally evaluated after Sim(3) alignment. Coverage must be read together with error.

## Stationary wrist constellations

`static_wrist/metrics.json` contains the four stationary-sequence precision summaries. RMS displacement and step statistics are descriptive precision measures. They are not absolute anatomical wrist accuracy, and missing observations are not converted into measurements.
