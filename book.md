
[__SOURCE](README.md)
# ${cont_model} 제어기 기능설명서 - Teach Pendant 앱(App)


[__SOURCE](0-about-this-manual/precautions.md)
# 사전 주의사항

{% include file="ko/precautions.md" %}

[__SOURCE](1-intro/README.md)
# 1. 개요

본 설명서를 잘 이해하기 위해서는 아래의 지식을 갖추고 있어야 합니다.

- [${cont_model} 제어기 조작 설명서 - TP630](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/ko-tp630/README?cont_model=${cont_model})


로봇의 각종 설정과 교시, 재생, 다양한 서비스 기능들은 ${cont_model} 제어기의 기본 기능으로서 탑재되어 있습니다. 기본 기능에 포함되지 않은 부가적인 기능들, 혹은 특정 용도에 최적화된 기능들이 별도로 설치하는 부가 소프트웨어로 제공되기도 하는데 이를 ${cont_model} 앱(App)이라고 하며, 이 중 티치펜던트에 설치되어 실행되는 소프트웨어를 Teach Pendant 앱으로 분류합니다. 

[__SOURCE](2-installation/README.md)
# 2. 설치


[__SOURCE](2-installation/1-preparation.md)
# 2.1 준비

${cont_model} 앱의 설치파일은 아래의 예와 같이 몇 개의 파일로 구성되어 있습니다.

티치펜던트 앱인 Cimon Xpanel을 예로 들어 설명하겠습니다.

${cont_model} 앱의 설치 폴더를 USB메모리의 아래 경로에 복사해 넣으십시오. 

/hi6/apps/

![](../_assets/2_1_folder.png)


[__SOURCE](2-installation/2-install.md)
# 2.2 설치

1) 준비한 USB 메모리를 티치펜던트에 장착합니다.

2) "서비스 - 10:App" 메뉴를 선택합니다.

3) 제목 막대가 App - USB가 될 때까지 \[F1:위치\] 버튼을 클릭합니다.

![](../_assets/2_2_app.png)

<br/>

4) \[F4: run\] 버튼을 클릭해 App installer를 실행합니다.

![](../_assets/2_3_installer.png)

<br/>

5) \[START\] 버튼을 클릭하면 설치가 진행됩니다. log 제일 하단에 Completed. 라고 표시되면 설치가 정상적으로 완료된 것입니다.

![](../_assets/2_3_installer_b.png)

<br/>

6) \[EXIT\] 버튼을 클릭해 종료합니다.

7) 제목 막대가 App - TP가 될 때까지 \[F1:위치\] 버튼을 클릭합니다. Xpanel 항목이 새로 생긴 것을 볼 수 있습니다.

![](../_assets/2_4_installed.png)

<br/>        

[__SOURCE](3-config-run/README.md)
# 3. 설정과 실행


[__SOURCE](3-config-run/1-hotkey-startup.md)
# 3.1 단축키(hotkey)와 실행방식

자주 사용하는 앱에는 단축키를 할당하면, 어떤 화면에서든 키조작만으로 실행할 수 있어 편리합니다.
앱을 선택한 후, \[F2:hotkey\] 버튼을 클릭합니다.

![](../_assets/3_1_hotkey.png)

<br/>

hotkey setting 대화상자에서 원하는 Ctrl+1 ~ Ctrl+9 중 원하는 단축키를 누른 후 \[ENTER\] 키로 설정을 완료하십시오.

![](../_assets/3_1_hotkey_b.png)

<br/>

\[F3:startup\] 버튼을 클릭하여 startup 열을 boot로 변경하면, ${cont_model} 제어기가 부팅할 때 앱이 자동으로 실행합니다.

다시 한번 \[F3:startup\] 버튼을 클릭하면 startup 열이 manual로 변경되면서 자동실행이 해제됩니다.

[__SOURCE](3-config-run/2-run-switch.md)
# 3.2. 실행과 전환

앱을 선택한 후, \[F4:run\] 버튼을 클릭하면, 해당 앱이 실행됩니다.

![](../_assets/3_2_run.png)

<br/>

앱을 종료하지 않은 채로 티치펜던트 본 화면으로 전환하려면 \[shift+R..\] 키를 1초 정도 길게 누르십시오.

본 화면에서 상단 제목막대의 우측에 ![](../_assets/3_3_switch_c.png) 아이콘이 보입니다. 이것은 백그라운드에 1개 이상의 앱이 실행되고 있다는 의미입니다.

![](../_assets/3_3_switch_b.png)

<br/>

다시 한번 \[shift+R..\] 키를 누르면 앱 전환 대화상자가 나타나는데, 화살표 좌/우 키로 아이콘을 선택한 후 \[ENTER\] 키를 누르면 해당 앱이 전면으로 나타나게 됩니다.

![](../_assets/3_3_switch_d.png)

<br/>

앱을 종료하려면 해당 앱의 종료 기능을 사용하십시오. 예를 들어 Xpanel은 `메인화면` 혹은 `진단` 화면의 우상단에 종료 버튼이 있습니다.

![](../_assets/3_3_exit.png)

<br/>

[__SOURCE](4-sw-relay.md)
# 4. S 릴레이에 의한 모니터링과 제어

내장 PLC의 S 릴레이에는 앱 실행상태를 모니터링하고 제어하는 GETSET_TP_APP 서비스가 있습니다. <br>

[3.4 S 릴레이](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/ko/3-relay/4-sw-relay/README?cont_model=${cont_model})

[3.4.6 S 릴레이 - TP_APP](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/ko/3-relay/4-sw-relay/6-slot-tp-app?cont_model=${cont_model})
<br><br>
이를 이용하면 ${cont_model}제어기 외부에서 I/O 신호를 통해 TP 앱의 실행상태를 확인하거나 원격 실행, 전환을 할 수 있습니다.


| S offset| field  | 설명                                              | type |
| ------- | ------ | ------------------------------------------------- | ---- | 
| 0       | command| GETSET_TP_APP (140)                               | s2   |
| 2       | get    | 현재 TP app의 단축키 번호 (1~9)                    | s2   |
| 4       | set    | 상태를 읽거나 제어할 대상 TP app의 단축키 번호 (1~9) | s2   |
| 6       | get    | 대상 TP app의 상태 현재값<br>(-1=없음, 0=미실행, 1=활성, 2=비활성) | s2   |
| 8       | set    | 대상 TP app 상태 제어<br>(0:동작없음, 1:활성, 2:비활성, 8: 실행, 9:강제종료)<br>* 값이 변할 때마다 1번씩만 수행됨.  | s2   |

<hr/><br/><br/>

예를 들어 아래 2개의 앱이 실행되고 있고, S2020에 140을 설정했다고 가정합시다.

* Xpanel : Ctrl+3 \(활성상태\)
* RoboCare : Ctrl+4

현재 화면 전면에 Xpanel이 실행되고 있다면, S2022의 값은 3입니다.

S2024에 4를 설정하면 S2026의 값은 RoboCare의 상태입니다. RoboCare는 현재 실행되고 있지만 비활성상태이므로 S2026은 2입니다.

S2028의 값이 1이 아닌 값일 때, 이를 1로 변경하면 Xpanel이 백그라운드로 비활성화되고 RoboCare가 전면으로 활성화됩니다. 이 값을 9로 변경하면 RoboCare는 강제종료됩니다.
