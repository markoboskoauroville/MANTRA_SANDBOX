# CQ MixPad macros (Allen & Heath CQ MixPad 1.2.2 for Android, in the Mantra Sandbox)

Screen: landscape 2400x1080 (`sandbox landscape`). CQ MixPad ignores a bare tap: every `tap` is a held press (150 ms).
Its interface is drawn by itself (no Android views), so `sandbox ui` finds nothing: macros use coordinates, measured
from screenshots 8.11.2026. Strips on a layer, left to right: `x=414`, `644`, `876`, `1108`, `1339`.

| macro | does | example |
|---|---|---|
| connect_sandbox | start screen: Other... -> 10.0.2.2 (cq_mitm.py --sandbox on the Mac) -> Connect | `sandbox run macros/cqmixpad/connect_sandbox.macro` |
| tab_config / tab_processing / tab_fader / tab_fx / tab_home | top tabs | |
| layer_in1_5 / layer_in6_10 / layer_stin_fx / layer_outputs / layer_dca | left-hand layer buttons | |
| open_gate / open_peq / open_comp / open_gain | open a strip's panel (Processing tab) | `... open_peq.macro x=644` |
| close_panel | the X of an open panel | |
| fader | drag a strip's fader from its handle y to a new y (0 dB = 844, +10 = 812, -10 = 882, -20 = 900, -40 = 932, off = 948) | `... fader.macro x=414 from=846 to=882` |

Reading values: `sandbox shot` and crop; or (faster, exact) inject a message to MixPad only with cq_mitm's `c <hex>` line
and read what MixPad shows (the calibration method of cq_mixpad_protocol).
