# CarnEvil VR

## Downloads

- [Quest APK](https://github.com/vr4all-standalone/carnevil-vr/releases/latest/download/carnevil-vr-quest.apk)
- [Windows PCVR](https://github.com/vr4all-standalone/carnevil-vr/releases/latest/download/carnevil-vr-pcvr.zip)
- [Complete matching source](https://github.com/vr4all-standalone/carnevil-vr/releases/latest/download/carnevil-vr-source.zip)
- [SHA256 checksums](https://github.com/vr4all-standalone/carnevil-vr/releases/latest/download/SHA256SUMS.txt)

Supply your own supported game files. The named source download includes the port, full pinned MAME bundle, patches and dependency sources. GitHub's automatic source ZIP contains this project page.


<!-- overseer-20261028-update -->
Prepared version **0.1.3**, Android code **4**. Publication of this update is being prepared; this text does not claim it has been published.

The Quest setup screen now uses the wide purple VR4ALL launch panel, with file/access status, help and a manual **Play** button. It enters VR automatically once the real game-file checks pass; returning from Quit or an error leaves Play available without a duplicate automatic launch.

The Arcade gun's body and complete grip follow logical player identity across hand swaps: P1 red / P2 blue. Grey screws, metal and lens details keep their original materials; other gun choices retain their appearance. Displayed **Gun angle** is -30..30 degrees in one-degree steps. New displayed 0 uses the old physical -10-degree pose consistently for the model, muzzle, laser, aiming and menu pointer. Every legacy saved angle resets to displayed 0 once; a persistent migration marker preserves later adjustments and other saved preferences.

This update has fresh software tests and Windows/Quest builds. Its APK was installed in place and matched the candidate hash; the new setup, colors and angle behavior have not been physically observed in a headset. Earlier accepted gameplay features remain separate historical evidence.

Complete matching source is `carnevil-vr-source.zip`, including the pinned MAME bundle, full patch stack, exact SDL/OpenXR sources, manifests and licenses. See [build instructions](docs/BUILD.md) and [this update](docs/release-notes-0.1.3.md).
<!-- /overseer-20261028-update -->

VR4ALL port of CarnEvil v1.0.3 using MAME 0.289, with an independently paced OpenXR host for Quest 3/3S and Windows. Native characters/models are reconstructed in stereo. Background scenery has a saved Original / Depth 3D option. Boot and operator diagnostics use their native raster image on a panel.

**Experimental:** the user confirms working immersive Quest startup, corrected vertical aim and laser alignment, substantially better visuals, smooth gameplay audio and good scenery depth. Cumulative native-time pacing sustains approximately 100% speed in the measured live stage, with no SDL audio shortages after startup. The final background, laser occlusion, P2 join, muzzle flash and smoke were physically confirmed by the user on Quest 3S. Comfort and complete route coverage are pending. See [validation](docs/validation.md).

## Downloads and local builds

[Download CarnEvil VR](https://github.com/vr4all-standalone/carnevil-vr/releases/latest) from the VR4ALL release page. Choose `carnevil-vr-quest.apk`, `carnevil-vr-pcvr.zip` or the complete buildable `carnevil-vr-source.zip`; `SHA256SUMS.txt` covers all three. No game data is included. This package prepares v0.1.3 (Android version 0.1.3 / code 4). The older accepted v0.1.2 release retains its internal `0.1.2-dev` label/code3.

The earlier accepted view-tuning build is the published v0.1.2 (`0.1.2-dev`, Android code3); its immutable artifacts and older v0.1.0 assets remain preserved. Packagers accept `--version` and `--output-dir` to keep candidates separate. The public repository page documents the mod; its complete matching source is the attached source archive, including the pinned MAME bundle and exact dependencies.

Install `carnevil-vr-quest.apk` using ADB or the local VR4ALL development profile. Allow game file access on the setup screen, and keep the Touch controllers awake. Use these owned files:

```text
Download/carnevil.zip
Download/carnevil/carnevil.chd
```

Keep the ZIP packed. Its three members are `carnevil1_9.u32`, `sound102.u95`, and `486_carnevil.u96`. The matching CHDv5 overall SHA1 is `5cffb0de63ad36eb01c5951bab04d3f8a9e23e16`. No NAOMI BIOS is needed. Setup checks actual ROM CRC32/SHA1 hashes, disk identity, map bounds and metadata bounds. Full disk integrity requires `chdman verify -i <carnevil.chd>`.

On PC, extract the ZIP, enable your PC OpenXR runtime, connect the headset and run `Run CarnEvil VR.cmd`. Put equivalent files under `roms/` beside the executable, or use `launch-pcvr.ps1 -RomDirectory D:\MyRoms`. Settings, NVRAM and disk differences are stored separately in `userdata/`. The source game files are never intentionally modified.

## Controls

| Control | Action |
| --- | --- |
| A / X, solo | Start or continue P1 / join P2, including native credit insertion |
| Either trigger, solo | Transfer the single active gun to that hand and shoot |
| Both players joined | P1 left / P2 right by default; reversible in settings |
| B / Y | Pump/reload; either hand works in solo |
| Left Menu | Pause and purple VR4ALL settings |
| Left stick click | Recenter |
| Right stick click | Toggle laser |
| Grip, then stick up/down | World size |
| Grip, then stick left/right | Gun size |

Squeeze grip with the stick at rest first; the stronger axis controls sizing. Settings persist on release. Reload modes are button, shoot off-screen and point off-screen. Recoil, flash and haptics follow native accepted-shot counts. Empty pulls produce no firing feedback.

Both labelled controllers appear at startup until the first Start or trigger pull. How to play restores the same button-anchored controller instructions used by the reference ports. Each hand's Start follows the current player assignment. Start is gated until native game readiness; P2 joining requires native P1 acknowledgement and both tracked controllers. A held Start retains its original player across a join or layout change, including long presses for native continue behavior.

The menu includes Resume, Recenter, Gun, Gun angle, Reload, Two players, Laser, four Haptics levels, World size, Panel distance, Background, 3D strength, Stereo separation, Wider view, How to play, Service and two-step Quit. Wider view is unavailable. Native weapon extraction is not established; The Gun selector offers Arcade and Zapper only; legacy third-choice settings fall back to Arcade.

**Background:** Depth 3D is the default, reconstructing the game's supplied scenery depth as a stereo surface. **Background → Original** remains available, and an explicitly saved choice is respected. Models and scenery share the laser/shot intersection. Constant or unusable depth automatically keeps the original presentation. Native nearest-depth masks are preserved in both modes to prevent models/HUD leaking through reserved background strips. The source describes only surfaces visible from the arcade camera: leaning can expose gaps, with the original image behind them. It does not provide a complete 360° environment. See [background evidence](docs/background-feasibility.md).

**View options retained from accepted v0.1.2:** **3D strength** makes the scene fill more of your view: 1–2× in 0.25 steps. **Stereo separation** adjusts binocular depth independently: 1, 1.25, 1.5, 2, 3, 4 or 5.25×. Both save separately and default to 1.25× as requested after the larger-view trial. Valid saved choices are preserved; 1× remains available. Try strength1.25× first, then tune separation if desired. Models and either background mode use the same transform; shot coordinates and laser endpoints follow it. Health/ammo HUD scales with 3D strength too; the VR menu and tracked guns keep their physical size. This enlarges the existing camera image; it does not capture wider scenery. High separation brings geometry closer and can exaggerate depth. In v0.1.2 testing, the user physically accepted the larger view/HUD and confirmed impact sparks line up with the laser at1.25× /1.25×. TeraBurst's calibrated defaults are game-specific and are not copied.

Native hit sparks now resolve the world surface at their original camera position and follow its view transform. The two exact CarnEvil1.0.3 player-effect textures are recognized; health/ammo/text and other HUD stay flat and follow 3D strength independently of stereo separation. Sparks no longer intercept subsequent aiming rays. Native sensor quantization and the game's own sampling remain separate limits.

Launch uses the shared VR4ALL image for three seconds of focused, presented headset time. Start and trigger input are blocked during that splash; the normal controller instructions follow it. Wider view remains unavailable because scenery outside the original image/depth is not supplied by this game.

Service: stick moves, trigger/A/X selects, B/Y backs out. For native Gun Calibration/Input Test, click the right stick to enable gun testing: triggers and pumps then reach the native guns, and A/X sends native Start (cancel calibration). Click again for menu controls. The VR menu’s “Service controls” row provides the same toggle on controllers without stick clicks. Diagnostics uses fixed P1/P2 hand assignment from settings. Quest Quit returns to setup; choose Play manually for another session.

PC bindings include Touch, Index, Vive and Windows Mixed Reality. Index uses A/B and left trackpad force for settings. Vive/WMR use Menu for Start (left short press), hold left Menu for settings, and trackpad click for pump. Vive uses the runtime recenter function. These profiles have not all been physically tested.

Gun models: Arcade and Zapper. No usable native player weapon model has been found in the sampled capture/extraction work. The old Custom option has been removed at the user's request; an old saved third choice safely uses Arcade.

## Build from source

The complete source archive contains the port, a verified `engine-source.bundle` for the pinned MAME commit, and exact SDL/OpenXR source snapshots under `source-deps/`, with SHA256 manifests. `build-engine.ps1` restores the bundle and applies the exported patches. The source in this working checkout has those dependencies in external build caches; pass their paths explicitly here.

Required tools: MSYS2 MinGW64 GCC/make and MAME dependencies, Git, Python 3.12+, CMake/Ninja, Android SDK platform 36.1/build-tools 36.0.0, NDK 29.0.14206865 and JDK 21. Gradle 9.4.1 is verified by the wrapper’s SHA256. Android targets ARM64/API 29 and checks the native ARM64 DRC factory; it refuses to package a C-backend-only engine.

```powershell
./tools/build-quest.ps1 -MsysRoot D:/msys64 -PythonPath C:/Python312/python.exe `
  -WorkRoot D:/build/carnevil -AndroidSdk D:/AndroidSdk -JavaHome D:/jdk-21 `
  -CMakePath C:/Tools/cmake/bin/cmake.exe -NinjaPath C:/Tools/ninja.exe
```

Use a dedicated compiler cache path without spaces. First Gradle assembly needs its normal dependency downloads; `-Offline` works after they are cached. The script creates a local development signing key in ignored `private/` if absent. Preserve that key to update the same installed app without replacing it. It contains no production signing credentials.

For Windows, run `tools/build-engine.ps1` with `-Platform Windows` and the same Msys/Python arguments. Configure this project with CMake/Ninja and MinGW GCC, then build. Build `source-deps/OpenXR-SDK` with `DYNAMIC_LOADER=ON` and `BUILD_API_LAYERS=OFF` for the loader DLL. `tools/package.py --help` lists the engine, host, loader and toolchain paths used to assemble the portable build and resolve its MinGW runtime DLLs.

```powershell
python -m unittest discover -s tests -v
cmake --build build/host-ninja
ctest --test-dir build/host-ninja --output-on-failure
```

GPU replay tests require NumPy, Pillow and ModernGL; see `tools/compare_captures.py` for paired native/C++ image measurements. Build products, owned data, captures and signing keys are ignored. [Credits](CREDITS.md), `LICENSE`, `licenses/`, and original source notices identify the reused components.


Previous publication verified: [v0.1.2](https://github.com/vr4all-standalone/carnevil-vr/releases/tag/v0.1.2) was published publicly. All four downloads and GitHub digests match the prepared bytes. The attached source snapshot is e6fe71e; these later publication notes do not replace its immutable release assets.
