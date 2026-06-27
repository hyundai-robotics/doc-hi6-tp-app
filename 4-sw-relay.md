# 4. 通过 S 继电器的监控和控制

嵌入式 PLC 的 S 继电器具有 GETSET_TP_APP 服务，以监控和控制应用程序的执行状态。 <br>

[3.4 S 继电器](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/zh/3-relay/4-sw-relay/README?cont_model=${cont_model})

[3.4.6 S 继电器 - TP_APP](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/zh/3-relay/4-sw-relay/6-slot-tp-app?cont_model=${cont_model})
<br><br>

这使您能够检查 TP 应用程序的执行状态，或通过来自 ${cont_model} 控制器外部的 I/O 信号远程运行和切换。

| S 偏移量| 字段  |                   描述                    | 类型 |
| ------- | ------ | ------------------------------------------------ | ---- |
| 0       | 命令| GETSET_TP_APP (140)                              | s2   |
| 2       | 获取    | 当前 TP 应用的热键编号 (1 到 9)  | s2   |
| 4       | 设置    | 要读取或控制状态的 TP 应用的热键编号 (1 到 9) | s2 |
| 6       | 获取    | 目标 TP 应用当前值的状态<br> (-1=无, 0=未运行, 1=激活, 2=非激活) | s2  |
| 8       | 设置    | 控制目标 TP 应用的状态。<br> (0: 无操作, 1: 激活, 2: 非激活, 8: 运行, 9: 强制关闭)<br>* 该操作仅在每次值变化时执行一次。 | s2 |

<hr/><br/><br/>

例如，假设下面的 2 个应用程序正在运行，并在 `S2020` 中设置 140。

* `Xpanel` : `Ctrl+3` (激活状态)
* `RoboCare` : `Ctrl+4`

如果 `Xpanel` 当前在屏幕前运行，则 `S2022` 的值为 3。

如果我在 `S2024` 中设置 4，则 `S2026` 的值为 `RoboCare` 的状态。 `RoboCare` 目前正在运行但处于非激活状态，因此 `S2026` 为 2。

如果 `S2028` 的值不是 1，将其更改为 1 将 `Xpanel` 禁用到后台，并将 `RoboCare` 移到前台。将此值更改为 9 将强制 `RoboCare` 关闭。