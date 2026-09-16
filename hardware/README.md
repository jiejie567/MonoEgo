# Hardware release

`wrist_constellation_v4/` contains the final two-part, no-Velcro magnetic wrist-fixture design used for the release. The combined STL is provided for inspection; the two half files are the intended separately printable parts. Magnet selection, polarity, retention, skin clearance, and mechanical safety must be checked by the builder.

`marker_layouts/` contains left/right printable marker sheets and their corresponding nominal constellation JSON files. Print PDFs at 100% / actual size, disable fit-to-page, and verify every black square with a ruler. The physical assembled constellation should be calibrated before quantitative capture; nominal JSON is not a substitute for that step.

`marker_layouts/calibrated_release/` contains the measured rigid constellation geometry used for the reported final wrist experiments. These files reproduce that particular assembled pair of fixtures; they are not universal replacements for calibrating a newly printed and assembled fixture. Marker IDs and corner coordinates are unchanged from the experiment configuration, while local absolute source paths have been removed for anonymous release.

`charuco_A4.pdf` is the camera-calibration target. Intrinsics are valid only for the same lens, focus, resolution, crop, stabilization, and camera mode used during calibration.
