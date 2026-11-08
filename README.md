# Mantra Sandbox

**GUI apps driven in a sandbox with their own screen, touch and keys, never on the owner's screen.**

Marko, 8.11.2026: *"run CQ MixPad in some sandbox, so we can run in parallel. We are not fighting for the mouse and
keyboard ... Create a sandbox environment for this sort of case ... call it mantra sandbox. So each application ... can be
developed and run in the sandbox with its own mouse and keyboard."*

## v1: Android apps in a headless emulator
- AVD `mantra_sandbox`, made from the Pixel 7 / Android 15 system image already installed in the Android SDK (no
  download). It runs with `-no-window -no-audio -no-boot-anim` on its own adb serial `emulator-5580`.
- All input goes through adb (`input` held presses, swipes, text, keys). The Mac's mouse and keyboard are never used,
  and nothing appears on the Mac's screen. Screenshots come from `screencap`.
- Macros are plain text files. All the steps of a macro run in **one** `adb shell` call, so a macro of ten taps takes
  about 0.4 s.

## The command
```
sandbox create                      make the AVD (copies the Pixel 7 AVD's hardware config, not its data)
sandbox start | stop | status       boot headless (about 25 s cold), kill, state
sandbox install a.apk [b.apk ...]   install (several files = one split app)
sandbox install-from-pixel <pkg>    pull an installed app's APKs from the real phone over adb (LAN/cable) and install
sandbox launch <pkg>                start an app;  sandbox landscape | portrait
sandbox shot [file.png]             screenshot (default ~/.mantra_sandbox/shot.png)
sandbox tap X Y [ms]                a held press (150 ms; some apps ignore a bare tap)   sandbox qtap X Y  (bare tap)
sandbox swipe X1 Y1 X2 Y2 [ms]      sandbox drag ...   sandbox type "text"   sandbox key <code>
sandbox ui [word]                   uiautomator dump: elements with text/description and their centres
sandbox run <file.macro> [k=v ...]  run a macro; ${k} in the file is replaced by v
sandbox redir udp|tcp <port>        forward that Mac port into the sandbox
sandbox adb <args>                  any adb command on the sandbox
```
Macro steps, one per line (`#` comments): `tap X Y [ms]`, `qtap X Y`, `swipe X1 Y1 X2 Y2 [ms]`, `drag ...`,
`type TEXT`, `key CODE`, `sleep MS`, `text "Label"` (tap the element with that text: one ui dump, then the batch goes
on), `shot FILE`, `include OTHER.macro`.

## Networking
The emulator sits behind its own NAT: it reaches the LAN, and the Mac is `10.0.2.2` from inside. A desk or service that
streams UDP back to its client (like the CQ mixer) needs a relay on the Mac and a `sandbox redir udp <port>` into the
emulator. CQ_MIXPAD_MANTRA's `tools/cq_mitm.py <desk-ip> --sandbox` does both.

## First app: CQ MixPad (Allen & Heath) for the CQ-12T
`macros/cqmixpad/` (see its README): connect through the relay, tabs, layers, open gain/gate/PEQ/compressor panels,
close, faders. On 8.11.2026 the sandbox was used to calibrate the desk's frequency, time, ratio and width scales and to
tour the output processing, without touching the Mac's mouse once (repo cq_mixpad_protocol).

## v2 (not built): Mac apps
A macOS virtual machine (Apple's Virtualization.framework) would give Mac apps the same: own screen, own input. It
needs a macOS restore image (IPSW, about 15 GB), so it waits for Marko's yes (save-sim-data).

## Rules
- Nothing in this repository is secret: no keys, tokens or passwords; examples use LAN addresses only.
- One version number, whole (`VERSION`); one branch, `main`.
