# CarnEvil VR v0.1.0 — Quest & PC VR

First public release of CarnEvil VR for standalone Quest 3/3S and Windows OpenXR.

- Stereo characters with tracked lightguns and Depth 3D scenery enabled by default.
- Original background mode remains available.
- Native shot-aligned lasers with solid gun occlusion, recoil, shaped muzzle flash, drifting smoke and adjustable haptics.
- Solo hand switching, P1/P2 joining, reversible hand assignment, three reload modes and native Service controls.
- Shared VR4ALL launch image and controller instructions.
- Gameplay pacing/audio improvements and native per-pixel depth handling for moving floor edges.

The final build was accepted on Quest 3S for visuals/depth, audio, laser alignment/occlusion, P2 joining and flash/smoke. CTest 9/9, Python 32/32 and an independent source-build host check pass. Windows PCVR is built and tested automatically; all headset profiles and game routes are not fully tested.

## Install

Use `carnevil-vr-quest.apk` for Quest, or extract `carnevil-vr-pcvr.zip` for Windows. See the [project page](https://github.com/vr4all-standalone/carnevil-vr#readme) for game-file paths and controls. This APK is byte-identical to the accepted headset build and reports internal version `0.1.0-dev`.

**Bring your own CarnEvil v1.0.3 ROM and CHD. No game data or BIOS is bundled.**

`carnevil-vr-source.zip` is the complete matching buildable source, including the pinned MAME Git bundle and exact SDL/OpenXR dependency sources. Use that file rather than GitHub's automatic source archives for this project-page repository. `SHA256SUMS.txt` covers all three downloads.

Scenery is reconstructed from the arcade camera's available depth; leaning can reveal gaps and wider view is unavailable. Boot/diagnostics remain on a raster panel.
