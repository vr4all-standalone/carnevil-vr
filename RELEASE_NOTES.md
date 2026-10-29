# CarnEvil VR v0.1.2 — Quest & PC VR

A larger, adjustable VR view with corrected impact alignment. Tested and accepted on Quest 3S.

- **3D strength: 1.25× by default**, adjustable from 1–2× in 0.25 steps.
- **Stereo separation: 1.25× by default**, with 1, 1.25, 1.5, 2, 3, 4 and 5.25× choices.
- **Depth 3D backgrounds remain the default**, with Original available.
- Health and bullet counts scale with 3D strength; the VR menu and tracked guns retain their physical size.
- Native impact sparks now follow scene depth and line up with the laser. Sparks no longer interfere with later aiming rays.
- Gun selection is **Arcade / Zapper**. A previous third-choice setting safely falls back to Arcade.

Existing valid settings and game saves are preserved. New defaults apply to fresh/missing settings; select 1.25× / 1.25× manually if you want to change an existing preference. Native game/audio/pacing libraries remain unchanged from the accepted build.

## Downloads

- `carnevil-vr-quest.apk` — standalone Meta Quest 3/3S.
- `carnevil-vr-pcvr.zip` — Windows OpenXR portable build.
- `carnevil-vr-source.zip` — complete matching source, pinned MAME Git bundle, exact SDL/OpenXR sources, build instructions and licenses.
- `SHA256SUMS.txt` — checksums for all three downloads.

Install the APK over the existing app to retain data. Its internal version is `0.1.2-dev`, Android version code 3; these are the exact APK bytes tested in the headset. No ROM, CHD or other game data is included. Bring your own CarnEvil v1.0.3 files.

The source archive attached above contains the complete buildable mod. GitHub's automatic Source code archives contain the project page only.

Quest 3S visuals, 1.25× / 1.25× view and impact/laser alignment were physically accepted. Windows builds and automated OpenGL tests pass; PCVR headset profiles and full routes remain untested. Depth scenery covers the original camera's visible surfaces, so leaning may expose gaps; wider scenery is unavailable.
