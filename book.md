# Hi6 Robot Controller Function Manual - Teach Pendant App

{% hint style="warning" %}
The information presented in this manual is the property of HD Hyundai Robotics.

The manual may neither be copied, in part or in full, nor redistributed without prior written consent from HD Hyundai Robotics.

It may neither be provided to any third party nor used for any other purposes.



HD Hyundai Robotics reserves the right to modify this document without prior notification.



**Copyright ⓒ 2024 by HD Hyundai Robotics**
{% endhint %}
# 1. Overview

In order to understand this manual well, you must have the following knowledge.

- [Basic Operation of Hyundai Hi6 Robot Controller](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/english-tp630/README)

<br>

Various settings, teaching, playback, and various service functions of the robot are installed as basic functions of the Hi6 controller. Additional functions that are not included in the basic function or functions optimized for a specific purpose are separately installed as add-on software, which is called the Hi6 app, and the software installed and executed on the Teach Pendant is classified as the Teach Pendant app.
# 2. Installation
# 2.1 Preparation

The Hi6 app installation file consists of several files, as shown in the example below.
Let me take Cimon Xpanel, the Teach Pendant app, as an example.
Copy the installation folder of the Hi6 app to the path below in USB memory.

/hi6/apps/

![](../_assets/2_1_folder.png)

# 2.2 Install

1) Install the prepared USB memory into the Teach Pendant.

2) Select the `Service - 10:App` menu.

3) Click the `[F1:Location]` button until the title bar becomes `App - USB`.

![](../_assets/2_2_app.png)

<br/>

4) Click the `[F4:run]` button to run the hi6 installer.

![](../_assets/2_3_installer.png)

<br/>

5) Click the `[START]` button to proceed with the installation. If it says Completed at the bottom of the log, the installation has completed successfully.

![](../_assets/2_3_installer_b.png)

<br/>

6) Click the `[EXIT]` button to exit.

7) Click the `[F1:Location]` button until the title bar becomes `App - TP`, you can see the new Xpanel item.

![](../_assets/2_4_installed.png)

<br/>
# 3. Configuration and run
# 3.1 hotkey and execution way

If you assign a hotkey to a frequently used app, it is convenient because it can be executed only by pressing key on any screen.
Select the app and click the `[F2:hotkey]` button.

![](../_assets/3_1_hotkey.png)

<br/>

In the hotkey setting dialog box, press the desired `Ctrl+1` through `Ctrl+9` and complete the setting with the `[ENTER]` key.

![](../_assets/3_1_hotkey_b.png)

<br/>

If you change the startup column to boot by clicking the `[F3:startup]` toggle button, the app will automatically run when the Hi6 controller boots.

If you click the `[F3:startup]` button once again, the startup column changes to manual and auto-run is disabled.
# 3.2. execution and switching

After selecting the app, click the `[F4:run]` button to launch the app.

![](../_assets/3_2_run.png)

<br/>

Press and hold the `[SHIFT+R..]` key for about a second to switch to the TeachPendant main screen without shutting down the app.

On this screen, you see the ![](.../_assets/3_switch_c.png) icon on the right side of the top title bar, which means there is more than one app running in the background.

![](../_assets/3_3_switch_b.png)

<br/>

Once again, pressing the `[SHIFT+R..]` key will display the app switch dialog box, select the icon with the left/right arrow and press the `[ENTER]` key to bring the app to the front.

![](../_assets/3_3_switch_d.png)

<br/>

To exit an app, use the exit feature of that app, for example, Xpanel has a exit button in the upper right corner of the `Diagnostics` screen.

![](../_assets/3_3_exit.png)

<br/>
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
