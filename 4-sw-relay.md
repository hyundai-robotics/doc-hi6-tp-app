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