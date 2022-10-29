# 4. S 릴레이에 의한 모니터링과 제어

내장 PLC의 S 릴레이에는 앱 실행상태를 모니터링하고 제어하는 GETSET_TP_APP 서비스가 있습니다. <br>

[3.4 S 릴레이](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/korean/3-relay/4-sw-relay/README)

[3.4.6 S 릴레이 - TP_APP](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/korean/3-relay/4-sw-relay/6-slot-tp-app)
<br><br>
이를 이용하면 Hi6제어기 외부에서 I/O 신호를 통해 TP 앱의 실행상태를 확인하거나 원격 실행, 전환을 할 수 있습니다.


| S offset| field  | 설명                                              | type |
| ------- | ------ | ------------------------------------------------- | ---- | 
| 0       | command| GETSET_TP_APP (140)                               | s2   |
| 2       | get    | 현재 TP app의 단축키 번호 (1~9)                    | s2   |
| 4       | set    | 상태를 읽거나 제어할 대상 TP app의 단축키 번호 (1~9) | s2   |
| 6       | get    | 대상 TP app의 상태 현재값<br>(-1=없음, 0=미실행, 1=활성, 2=비활성) | s2   |
| 8       | set    | 대상 TP app 상태 제어<br>(0:동작없음, 1:활성, 2:비활성, 8: 실행, 9:강제종료)<br>* 값이 변할 때마다 1번씩만 수행됨.  | s2   |

<hr/><br/><br/>

예를 들어 아래 2개의 앱이 실행되고 있다고 가정합시다.

* Xpanel : Ctrl+3 \(활성상태\)
* RoboCare : Ctrl+4

현재 화면 전면에 Xpanel이 실행되고 있다면, sw960 값은 3입니다.

sw961에 4를 설정하면 sw962의 값은 RoboCare의 상태입니다. RoboCare는 현재 실행되고 있지만 비활성상태이므로 sw962는 2입니다.

sw962의 값이 1이 아닌 값일 때, 이를 1로 변경하면 Xpanel이 백그라운드로 비활성화되고 RoboCare가 전면으로 활성화됩니다. 이 값을 9로 변경하면 RoboCare는 강제종료됩니다.
