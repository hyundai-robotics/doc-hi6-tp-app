
[__SOURCE](README.md)
# ${cont_model} 控制器功能手册 - 教学挂件应用
[__SOURCE](0-about-this-manual/precautions.md)
# 注意事项

{% include file="zh/precautions.md" %}
[__SOURCE](1-intro/README.md)
# 1. 概述

为了很好地理解本手册，您必须具备以下知识。

- [${cont_model} 控制器操作手册 - TP630](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/README?cont_model=${cont_model})

<br>

机器人的各种设置、教学、回放以及各种服务功能作为 ${cont_model} 控制器的基本功能安装。未包含在基本功能中的附加功能或针对特定目的优化的功能作为附加软件单独安装，称为 ${cont_model} 应用程序，而在教学挂件上安装和执行的软件被归类为教学挂件应用程序。
[__SOURCE](2-installation/README.md)
# 2. 安装
[__SOURCE](2-installation/1-preparation.md)
# 2.1 准备

${cont_model} 应用程序安装文件由多个文件组成，如下例所示。
以 Cimon Xpanel，即教导 Pendant 应用程序为例。
将 ${cont_model} 应用程序的安装文件夹复制到 USB 存储器中的以下路径。

/${cont_model}/apps/

![](../_assets/2_1_folder.png)
[__SOURCE](2-installation/2-install.md)
# 2.2 安装

1) 将准备好的 USB 存储器插入教导 pendant。

2) 选择 `服务 - 10:应用 (Service - 10:App)` 菜单。

3) 单击 `[F1:Location]` 按钮，直到标题栏变为 `应用 - USB (App - USB)`。

![](../_assets/2_2_app.png)

<br/>

4) 单击 `[F4:运行] ([F4:run])` 按钮以运行 ${cont_model} 安装程序。

![](../_assets/2_3_installer.png)

<br/>

5) 单击 `[START]` 按钮以继续安装。如果日志底部显示“已完成”，则说明安装已成功完成。

![](../_assets/2_3_installer_b.png)

<br/>

6) 单击 `[EXIT]` 按钮以退出。

7) 单击 `[F1:Location]` 按钮，直到标题栏变为 `应用 - TP (App - TP)`，您可以看到新的 Xpanel 项目。

![](../_assets/2_4_installed.png)

<br/>
[__SOURCE](3-config-run/README.md)
# 3. 配置和运行
[__SOURCE](3-config-run/1-hotkey-startup.md)
# 3.1 热键和执行方式

如果您为常用应用程序分配了热键，那么在任何屏幕上只需按下键即可执行，这非常方便。
选择应用程序并点击`[F2:快捷键] ([F2:hotkey])`按钮。

![](../_assets/3_1_hotkey.png)

<br/>

在热键设置对话框中，按下所需的`Ctrl+1`至`Ctrl+9`，并通过`[ENTER]`键完成设置。

![](../_assets/3_1_hotkey_b.png)

<br/>

如果您通过点击`[F3:启动] ([F3:startup])`切换按钮将启动列更改为启动，则在${cont_model}控制器启动时，该应用程序将自动运行。

如果您再次点击`[F3:启动] ([F3:startup])`按钮，启动列将更改为手动，自动运行被禁用。
[__SOURCE](3-config-run/2-run-switch.md)
# 3.2. 执行和切换

选择应用后，点击`[F4:运行] ([F4:run])`按钮以启动应用。

![](../_assets/3_2_run.png)

<br/>

按住`[SHIFT+R..]`键约一秒钟，以在不关闭应用的情况下切换到TeachPendant主屏幕。

在此屏幕上，您会看到顶部标题栏右侧的![](.../_assets/3_switch_c.png)图标，这意味着后台有多个应用在运行。

![](../_assets/3_3_switch_b.png)

<br/>

再次按`[SHIFT+R..]`键将显示应用切换对话框，选择具有左右箭头的图标并按`[ENTER]`键将应用置于前面。

![](../_assets/3_3_switch_d.png)

<br/>

要退出应用，请使用该应用的退出功能，例如，Xpanel在`主 (Main)`或`Diagnostics`屏幕的右上角有一个退出按钮。

![](../_assets/3_3_exit.png)

<br/>
[__SOURCE](4-sw-relay.md)
# 4. 通过 S 继电器进行监控和控制

嵌入式 PLC 的 S 继电器具有 GETSET_TP_APP 服务，用于监控和控制应用程序的执行状态。 <br>

[3.4 S 继电器](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/en/3-relay/4-sw-relay/README)

[3.4.6 S 继电器 - TP_APP](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/en/3-relay/4-sw-relay/6-slot-tp-app)
<br><br>

这使您能够检查 TP 应用程序的执行状态，或者通过来自 ${cont_model} 控制器外部的 I/O 信号远程运行和切换。

| S 偏移 | 字段    |                   描述                         | 类型 |
| ------ | ------- | ---------------------------------------------- | ---- |
| 0      | 命令    | GETSET_TP_APP (140)                           | s2   |
| 2      | 获取    | 当前 TP 应用的热键编号（1 到 9）              | s2   |
| 4      | 设置    | 读取或控制 TP 应用状态的热键编号（1 到 9）  | s2   |
| 6      | 获取    | 目标 TP 应用当前值的状态<br> (-1=无, 0=未运行, 1=活跃, 2=非活跃) | s2  |
| 8      | 设置    | 控制目标 TP 应用的状态。<br> (0: 无操作, 1: 活跃, 2: 非活跃, 8: 运行, 9: 强制关闭)<br>* 每次值改变时仅执行一次。 | s2 |

<hr/><br/><br/>

例如，假设下面的两个应用正在运行，并在 `S2020` 中设置 140。

* `Xpanel` : `Ctrl+3` （活跃状态）
* `RoboCare` : `Ctrl+4`

如果 `Xpanel` 目前在屏幕前运行，则 `S2022` 的值为 3。

如果我在 `S2024` 中设置 4，那么 `S2026` 的值就是 `RoboCare` 的状态。`RoboCare` 目前正在运行但非活跃，因此 `S2026` 为 2。

如果 `S2028` 的值是非 1 值，将其更改为 1 会将 `Xpanel` 禁用到后台，并将 `RoboCare` 启用到前台。将此值更改为 9 会强制关闭 `RoboCare`。