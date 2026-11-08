# Momentary updates: Marko's words, first, before any code

## 8.11.2026

> "build a macro which is going to control every aspect of this mixer. It's CQ MixPad. It needs to fire quickly ...
> While it is working, mouse and keyboard interaction are blocked ... Or, if you can build that, this is running CQ
> MixPad in some sandbox, so we can run in parallel. We are not fighting for the mouse and keyboard ... Create a sandbox
> environment for this sort of case ... call it mantra sandbox. So each application ... can be developed and run in the
> sandbox with its own mouse and keyboard."

> "Develop this sandbox mantra as a repository in GitHub, a public one, and let the agent do it in the background."

What v1 is: Android apps in a headless Android emulator (its own screen, its own touch and keys, all through adb), so a
GUI can be driven while Marko keeps his own mouse and keyboard. First app: CQ MixPad (Allen & Heath), for the CQ-12T.
