<div align="center">

# MonoEgo
**Monocular Metric Egocentric Demonstration Capture with Passive Wrist Constellations and Sparse Workstation Anchors**

<a href="https://anyverse.com/"><img src="docs/images/anyverse-dynamics-logo.png" width="280" alt="Anyverse Dynamics"></a>

[MonoTag SLAM code](https://github.com/jiejie567/EgoMono) · [Hardware](hardware/README.md) · [Results](results/README.md)

</div>

English | [中文](README_CN.md)

MonoEgo records human operations with a head-mounted RGB camera, two passive wrist fixtures and known-size workstation markers. Offline reconstruction produces metric camera and wrist-fixture trajectories from the same image stream.

The fixtures need no battery, IMU or radio. Video and geometric observations share one image clock, avoiding separate tracker-to-video synchronization. Camera and wrist-constellation calibration are still required.

This repository contains hardware, compact experimental results and representative demonstrations. Processing code lives in [EgoMono / MonoTag SLAM](https://github.com/jiejie567/EgoMono). Both repositories are currently private release preparations.

<p align="center"><img src="figures/fig1_teaser_integrated_v5.png" width="800" alt="MonoEgo capture system"></p>

## From recording to trajectories

<p align="center"><img src="docs/images/workflow.png" width="850" alt="Calibration, recording and offline reconstruction"></p>

1. Print and assemble the fixtures and markers; verify physical dimensions.
2. Calibrate camera intrinsics and rigid wrist-marker geometry.
3. Record unchanged RGB video.
4. Run marker-constrained MonoTag reconstruction and optional hand estimation.
5. Inspect validity, trajectories and map events before exporting data.

Known marker dimensions provide metric information. Repeated views constrain scale and map consistency. Offline matching can recover earlier or short-gap poses when sufficient evidence exists. Appearance-edited RGB remains a separate derived product and never feeds back into localization.

## What's included

- [Printable hardware](hardware/README.md): magnetic wrist fixtures, marker sheets and ChArUco target.
- [Example calibrated layouts](hardware/marker_layouts/calibrated_release/): geometry of the specific tested fixtures, not a substitute for calibrating a new assembly.
- [Result sources](results/README.md): camera-reference and stationary-wrist summaries.
- [Representative videos](videos/): stationary-fixture demonstrations with ORB features and trajectories.
- [Processing code](https://github.com/jiejie567/EgoMono): calibration, capture, reconstruction, replay and optional export.

## Hardware

<p align="center"><img src="hardware/wrist_constellation_v4/strap_magnetic_no_velcro_preview.png" width="800" alt="Two-part magnetic wrist fixture: assembly, separated halves and magnet-pocket contact faces"></p>

Two-part magnetic wrist fixture, without Velcro. Download the printable [half A](hardware/wrist_constellation_v4/strap_half_A_magnetic_no_velcro.stl) and [half B](hardware/wrist_constellation_v4/strap_half_B_magnetic_no_velcro.stl), or inspect the [combined STL](hardware/wrist_constellation_v4/strap_band_magnetic_no_velcro_print.stl).

The tested setup uses a WN-L2406K397L global-shutter module, a 2.3 mm f/1.8 M12 lens and 1920 × 1080 recording at 90 FPS. Reconstruction uses measured intrinsics, not nominal field of view.

Reported capture-side cost was below US$100, excluding the recorder, replacement lens, offline compute, small fasteners and consumables, labour and shipping. This is not the cost of a complete recording and processing system.

Print at actual size, disable fit-to-page, and measure the black square rather than the white paper. Check magnet retention, polarity and skin clearance before wearing.

## Representative videos

### Moving camera, stationary wrist fixtures

[SW-02 video](videos/SW-02_english_orb_trajectories.mp4)

<p align="center"><img src="videos/SW-02_preview_0300.png" width="720" alt="SW-02 stationary wrist test"></p>

[SW-04 video](videos/SW-04_english_orb_trajectories.mp4)

These examples test whether camera motion appears as motion of a stationary fixture. They measure positional precision, not full dynamic hand-motion accuracy.

## Experimental scope

Camera motion is compared against Odin multisensor odometry as a reference. Metric error uses SE(3) alignment; Sim(3) results are separate because that alignment removes global scale error. Read error together with tracking coverage.

Across four stationary-wrist recordings, per-side RMS scatter was approximately 1.26–2.69 mm. This does not establish equivalent anatomical or dynamic accuracy. See [result sources](results/README.md) for the protocol and tables.

Raw indoor recordings, private screen content, machine-local paths and learned weights are excluded. The unblurred company-video review is not uploaded here.

## Getting started

Follow the [Ubuntu installation guide](https://github.com/jiejie567/EgoMono/blob/main/docs/INSTALL.md). Start with SLAM and geometric wrist observations; learned hand inference and training-format export are optional.

## License

Original hardware, layouts, figures, result tables and documentation use [CC BY 4.0](LICENSE.md). Attribute **MonoEgo — Anyverse Dynamics** and indicate changes. Third-party material retains its original license. The company logo is excluded; no trademark or endorsement rights are granted.

Companion code uses GPL-3.0 because it includes modified ORB-SLAM3. Model and dataset terms still apply separately.
