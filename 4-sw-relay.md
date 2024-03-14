# 4. Monitoring and control by S relay

The S Relay of the embedded PLC has the GETSET_TP_APP service to monitor and control the execution status of the app. <br>

[3.4 S relays](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/english/3-relay/4-sw-relay/README)

[3.4.6 S relay - TP_APP](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/english/3-relay/4-sw-relay/6-slot-tp-app)
<br><br>

This allows you to check the execution status of the TP app or to run and switch remotely through the I/O signal from outside the Hi6 controller.


| S offset| field  |                   description                    | type |
| ------- | ------ | ------------------------------------------------ | ---- |
| 0       | command| GETSET_TP_APP (140)                              | s2   |
| 2       | get    | hot-key Number for current TP app (1 to 9)  | s2   |
| 4       | set    | hot-key number (1 to 9) of the TP app to read or control the state | s2 |
| 6       | get    | status of target TP app Current value<br> (-1=none, 0=not running, 1=active, 2=inactive) | s2  |
| 8       | set    | control target TP app status.<br> (0: No action, 1: Active, 2: Inactive, 8: Run, 9: Forced shutdown)<br>* This is done only once every time the value changes. | s2 |

<hr/><br/><br/>

For example, let's say the below 2 apps are running, and set 140 in `S2020`.

* `Xpanel` : `Ctrl+3` (Active state)
* `RoboCare` : `Ctrl+4`

If `Xpanel` is currently running on the front of the screen, the value of `S2022` is 3.

If I set 4 in `S2024`, the value of `S2026` is the state of `RoboCare`. `RoboCare` is currently running but is inactive, so `S2026` is 2.

If the value of `S2028` is a non-1 value, changing it to 1 disables `Xpanel` to the background and `RoboCare` to the front. Changing this value to 9 forces `RoboCare` to shut down.
