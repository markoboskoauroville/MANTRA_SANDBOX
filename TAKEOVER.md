# TAKEOVER: Mantra Sandbox

**State 8.11.2026, night: v1 works.** `sandbox` is on the PATH (~/.local/bin/sandbox -> bin/sandbox).

## Where we stopped (8.11.2026)
- AVD `mantra_sandbox` (Pixel 7 hardware, Android 15 google_apis_playstore image already on the Mac), serial
  emulator-5580, headless. Cold boot about 25 s. Marko's own AVD Pixel_7_API_35 untouched.
- CQ MixPad 1.2.2 installed from the real Pixel (`install-from-pixel com.allenheath.minimicro.mixpad`, four split
  APKs), EULA accepted once, landscape. It connects through `cq_mitm.py <desk> --sandbox` on the Mac at 10.0.2.2.
- Macros for CQ MixPad in macros/cqmixpad, about 0.4 s each.
- Used the same night for the CQ scale calibration and the output-processing tour (cq_mixpad_protocol).

## Pending
1. v2 for Mac apps: a macOS VM (Virtualization.framework) needs a ~15 GB IPSW: only with Marko's yes.
2. More CQ MixPad macros: FX tab, CONFIG pages, scenes, sends; a knob macro (slow horizontal swipe).
3. Optional: a Swift viewer (sandbox screen in a window, read only) if Marko wants to watch.
