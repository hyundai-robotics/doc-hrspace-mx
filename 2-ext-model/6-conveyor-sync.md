# 2.6. 컨베이어 동기화 (Conveyor Sync)

-	"센서 동기" 기능 사용 방법을 먼저 숙지해주십시오. 
  *	Hi5a 제어기 기능설명서 - 센서 동기
  * [Hi6 제어기 기능설명서 - 센서 동기(컨베이어, 프레스)](https://hrbook-hrc.web.app/#/view/doc-sensor-sync/ko/README?cont_model=Hi6)
  * [Hi7 제어기 기능설명서 - 센서 동기(컨베이어, 프레스)](https://hrbook-hrc.web.app/#/view/doc-sensor-sync/ko/README?cont_model=Hi7)

컨베이어 동기화 확장모델은 HRSpace 에서 컨베이어의 Pulse와 Limit Switch 값을 생성하여, VRC 또는 Ethernet 시뮬레이터에 값을 전달, 컨베이어 동기화 시뮬레이션이 가능 하도록 도와줄 수 있는 확장 모델입니다.

모델 불러오기로 라이브러리의 외부설비에서 `Conveyor(직선)` 또는, `conveyor_CCW(반시계 방향 원형)` 또는, `conveyor_CW(시계방향 원형)`를 불러옵니다.

![](../_assets/load-model.png)
![](../_assets/conv-sync/load-conveyor.png)

MXConveyor 확장을 지정한 모델의 TPath를 `로봇 속성-동기`의 펄스 카운터 항목에 지정합니다.

![](../_assets/conv-sync/robot-prop-sync.png)
 

트리창에 생성된 모델(FloorPlan)에 대해 팝업 메뉴에서 확장 속성을 선택하여 컨베이어 속성 대화상자를 여십시오. (모델 속성 대화상자에서, ![](../_assets/bt-prop.png) 버튼을 클릭해도 됩니다.) 

![](../_assets/conv-sync/popup-menu-ext-prop.png)
![](../_assets/conv-sync/bt-prop-in-prop.png)
![](../_assets/conv-sync/conveyor-prop.png)
 

속성 대화상자의 `START`를 클릭하면 컨베이어 동작이 시작됩니다.
`put` 버튼을 클릭하면, Target의 동작이 시작됩니다.


## 2.6.1. 컨베이어의 동작

![](../_assets/conv-sync/concept.png)


## 2.6.2. Hi5a 제어기로의 데이터 전달 

`PulseCount` 특성 값과 `LimitSwitch` I/O 값은 로봇 속성의 제어기 연결 설정에 따라 가상제어기 또는 이더넷으로 연결된 제어기로 전달됩니다.

![](../_assets/conv-sync/sel-vrc.png)


전달된 값은 센서 동기 화면에서 모니터링 할 수 있습니다. (Hi5a 제어기의 "센서 동기" 사용방법을 참조해 주세요)

![](../_assets/conv-sync/monitor-pane.png)
