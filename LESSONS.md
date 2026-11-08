# LESSONS

- **8.11.2026:** CQ MixPad ignores a bare `input tap` and some buttons (a panel's X) ignore a 90 ms press: `tap` is a
  150 ms held press (`input swipe x y x y 150`).
- **8.11.2026:** CQ MixPad draws its own interface: `uiautomator dump` finds no elements. Macros use coordinates
  measured from screenshots; `sandbox ui` still works for ordinary Android apps.
- **8.11.2026:** In CQ MixPad a press on a strip that is not selected only selects it; open a panel with two presses:
  the strip's name first, then the section (open_*.macro).
- **8.11.2026:** The MixPad IP dialog keeps the last address: clear it (MOVE_END + DEL x20) before typing.
- **8.11.2026:** The emulator's NAT does not pass a UDP stream the desk sends back to the client; the Mac relay
  (cq_mitm --sandbox) plus `adb emu redir add udp:P:P` does. The Mac is 10.0.2.2 inside the emulator.
- **8.11.2026:** Stop the emulator while the Mac records audio (sox): a quiet Mac avoids buffer overruns.
- **8.11.2026:** A value can be shown on CQ MixPad without changing the desk: cq_mitm's `c <hex>` line sends the message
  to MixPad only. Reading what MixPad shows calibrates a scale with zero risk to the desk.
