
[__SOURCE](README.md)
# Hi5/Hi6/Hi7 제어기 기능설명서 - HRSpace4 확장 모델

[__SOURCE](0-about-this-manual/README.md)
# 이 설명서에 대하여


[__SOURCE](0-about-this-manual/precautions.md)
# 사전 주의사항

{% include file="ko/precautions.md" %}

[__SOURCE](0-about-this-manual/safety-notice.md)
# 안전 주의 사항

{% include file="ko/safety-notice.md" %}

[__SOURCE](1-preface/README.md)
# 1. 개요

HRSpace v4.9.2 이상을 기준으로 설명합니다.

[__SOURCE](1-preface/1-about.md)
## 1.1 HRSpace4 확장모델에 대하여

HRSpace4 확장모델은 HRSpace4에 부가적인 확장 기능을 제공하기 위한 DLL 라이브러리 모듈입니다. 이 설명서는 HRSpace4에서 사용할 수 있는 각 확장모델들의 사용방법을 설명합니다.

<table>
<tr>
  <td width='60%'><img src="../_assets/intro/model-prop.png"/></td>
  <td>일부 확장 모델은 모델 속성 대화상자에 소프트웨어 라이브러리 파일이 설정되어 있습니다. 이 설정은 조작할 필요 없으므로 그대로 두십시오.</td>
</tr>
</table>

[__SOURCE](1-preface/2-prerequisite.md)
## 1.2 사전 지식

HRSpace4의 기본기능에 익숙하지 않은 분은 먼저 HRSpace4의 기능설명서를 숙지하십시오. (`HRSpace4 주메뉴 - 홈 - 도움말 - 설명서`)

[__SOURCE](2-ext-model/README.md)
# 2. 확장 모델


[__SOURCE](2-ext-model/1-safety-fence.md)
# 2.1. 안전펜스 (Safety Fence)


안전펜스는 원하는 영역에 마우스를 클릭하여 신속하게 펜스 형상을 만들고, 모서리 위치에 좌표값을 타이핑하여 정밀하게 레이아웃을 조정할 수 있는 확장 모델입니다.

모델 불러오기로 라이브러리의 `Jig - Fence`를 불러옵니다.
     
![](../_assets/load-model.png)

![](../_assets/safety-fence/load-model-fence.png)

3D화면에는 아직 아무 것도 나타나지 않습니다. 트리창에 생성된 모델에 대해 팝업 메뉴에서 확장 속성을 선택하여 안전펜스 속성 대화상자를 여십시오. (혹은 모델 속성 대화상자에서, ![](../_assets/bt-prop.png) 버튼을 클릭해도 됩니다.)
 
![](../_assets/popup-menu-ext-prop.png)


![](../_assets/safety-fence/fence-prop.png)

마우스로 꼭지점 위치들을 클릭하여 펜스 경로를 입력할 수 있습니다. 우선 꼭지점의 좌표값을 정확히 하기 위한 snap 값을 선택하십시오. 이 예에서는 100mm를 선택했습니다.
`Start Input` 버튼을 눌러 놓고, 마우스로 3D 화면의 grid 표면에 꼭지점들을 좌버튼 클릭하십시오. 클릭한 지점들 사이에 펜스가 생성됩니다. 아래 그림은 7개의 지점을 클릭하여 펜스를 생성한 예입니다.

![](../_assets/safety-fence/fence.png)

`End Input` 버튼을 누르면, 경로 입력이 종료됩니다. 입력된 좌표값들은 펜스 속성의 `FencePath` 범주에서 확인하고, 설계에 맞게 정밀 수정할 수 있습니다.

![](../_assets/safety-fence/fence-path.png)
![](../_assets/safety-fence/fence-path-5y.png)

원하는 좌표값을 더블 클릭하여 수정한 후, `Apply` 버튼을 클릭하면 3D화면에 반영됩니다.
(`Start Input` 버튼을 다시 누르면, 펜스경로를 처음부터 재입력하게 됩니다.)

다양한 펜스 속성들을 수정하여 펜스의 타입, 높이, 두께, 철망의 색상, 간격 등을 변경할 수 있습니다. 아래 예는 아까 생성한 철망 타입의 펜스를 유리 타입으로 변경한 예입니다. 스크린(유리)의 색상은 붉은 색, 투명도를 70%로 하여, 아크 용접 셀을 묘사했습니다. (펜스 프레임의 색상은 `리본 메뉴 - 스타일`에서 변경할 수 있습니다.)

![](../_assets/safety-fence/glass-type.png)

펜스 사이 열린 공간에 출입문을 만들어 봅시다. 기존 펜스의 자식으로서 모델 불러오기로 펜스 1개를 생성하고 이름을 변경합니다.

![](../_assets/safety-fence/rename-door.png)

새 펜스(출입문)의 확장 속성을 열고 `Start Input` 버튼을 누르십시오. 마우스 좌클릭으로 grid 표면에 2개의 좌표를 지정한 후, `End Input` 버튼을 누르십시오.

![](../_assets/safety-fence/door-overlap1.png)
->
![](../_assets/safety-fence/door-overlap2.png)

펜스의 기둥과 출입문의 기둥이 겹치면 위 좌측 그림처럼 부자연스럽게 보일 수 있습니다. 펜스의 `LeftPillar`, `RightPillar` 속성의 체크를 제거하여 펜스의 가장자리 기둥을 제거하십시오.

![](../_assets/safety-fence/prop-right-pillar.png)

출입문의 확장 속성과 스타일을 수정하여, 펜스와 유사한 형태로 만드십시오. 마지막으로 `DoorOpenAngle` 속성에 적당한 문 열림 각도(deg.)를 입력하면 출입문이 완성됩니다. 이제 프로젝트 파일을 저장하십시오.

![](../_assets/safety-fence/prop-door-open-angle.png)
![](../_assets/safety-fence/fence-door-open.png)


[__SOURCE](2-ext-model/2-robot-riser.md)
# 2.2 로봇 보고대 (Robot Riser)


로봇 보고대는 몇 가지 주요 수치를 입력하여 원하는 크기의 보고대 형상을 신속하게 만들 수 있는 확장 모델입니다. 

모델 불러오기로 라이브러리의 `Jig - Riser`를 불러옵니다.

![](../_assets/load-model.png)

![](../_assets/robot-riser/load-model-riser.png)

디폴트 파라미터로 로봇 보고대 모델이 생성됩니다. 생성된 모델에 대해 팝업 메뉴에서 확장 속성을 선택하여 보고대 속성 대화상자를 여십시오.

![](../_assets/robot-riser/popup-menu-ex-prop.png)
![](../_assets/robot-riser/riser-prop.png)

대화상자 우측에 크기 속성들이 제공됩니다. `AutoSet` 드롭다운 리스트 박스에서 로봇 타입을 선택하면 그에 맞는 보고대 크기로 속성값들이 자동 설정됩니다.

![](../_assets/robot-riser/drop-list.png)
 
보고대가 높을수록 안정성을 위해 하단 판넬의 면적이 커야 합니다. 보고대 높이가 1000mm이상일 경우, `Height>1000mm` 체크박스를 켜면 `WidthBottom` 값이 적절히 설정됩니다. (수작업으로 설정해도 됩니다.)

보고대 상단 표면에는 `crd`라는 이름의 좌표계 모델이 있습니다. 이 좌표계의 자식 모델로서 로봇을 불러오기 하면, 상단 표면에 정확히 로봇이 설치됩니다. (혹은, 트리창에서 이미 불러온 로봇을 마우스 왼쪽 버튼으로 드래그하여 `crd`에 드롭해도 됩니다.)

![](../_assets/robot-riser/robot-on-crd.png)

[__SOURCE](2-ext-model/3-paint.md)
# 2.3. 도장 건 (Paint Gun), 도장 작업물 (Paint Work)


도장 건과 도장 작업물 확장 모델을 이용하면, 시뮬레이션 중 3D 작업물 표면에 도막이 형성되는 모습이 시각적으로 표현됩니다. 작업물의 일부 영역에 도막이 형성되지 않거나 지나치게 중첩되어 형성되는지 여부를 판단하는데 도움을 줍니다.

{% hint style="warning" %}
도장 응용 기능은 Hi5a 제어기에서만 제공되며, Hi6/Hi7 에서는 현재 제공되지 않습니다.
{% endhint %}


아래와 같은 작업공간이 작성되어 있다고 가정하고, 이 상태에서 도막 형성 기능을 추가해봅시다. 작업공간에는 YP020 2대가 각각 도장건(`tap/bell`)을 장착한 상태로 설치되어 있습니다. 셔틀(`/conveyor/guide`) 위의 작업물(`part`)이 로봇들 사이로 이동하게 되고, 2개의 도장건에서 토출된 도료는 이 작업물 표면에 도막으로 형성되어야 합니다.

![](../_assets/paint/objective.png)
 
우선, 2개의 도장 건 모델 각각에 `MxPaintGun.DLL` 라이브러리를 연결시키십시오.

1. `/YP020/tap/bell/crd`의 모델 속성 대화상자를 엽니다.
2. 모델확장 입력칸 우측의 ![](../_assets/bt-more.png) 버튼을 클릭합니다.
3. `/Library/Tool/painting/MxPaintGun.dll`을 선택합니다.
4. `확인` 버튼을 클릭합니다.
5. `/YP020_2/tap/bell/crd`에 대해서도 같은 설정을 합니다.

![](../_assets/paint/model-ex-pathname.png)

작업물 모델에 `MxPaintWork.DLL` 라이브러리를 연결시키십시오.

1. `/conveyor/guide/part`의 모델 속성 대화상자를 엽니다.
2. 모델확장 입력칸 우측의 ![](../_assets/bt-more.png) 버튼을 클릭합니다.
3. `/Library/Tool/painting/MxPaintWork.dll`을 선택합니다.
4. `확인` 버튼을 클릭합니다.


로봇의 출력신호에 따라, 도장 건이 ON/OFF되도록 연결합니다. 아래 JOB의 예와 같이 `Y12` 출력신호로 도장 건을 제어한다고 하면, I/O 연결 모델을 만들어, 두 로봇의 `Y12` 출력을 각 도장건의 `SprayIn` 입력신호로 연결시킵니다.

![](../_assets/paint/minitp.png)

![](../_assets/paint/ioconn.png)

이제 도장 작업물인 `/conveyor/guide/part`에 대해 확장 속성 대화상자를 엽니다.

![](../_assets/paint/popup-menu-ex-prop.png)
![](../_assets/paint/paint-work-prop.png)


먼저, 도장작업을 할 건들을 지정해줘야 합니다. `Add gun` 버튼을 눌러, 아래와 같이 2개의 도장 건의 T경로를 지정해줍니다.

다음은 도장 면에 대한 지정입니다. 하나의 작업물은 한 개 이상의 face로 구성됩니다. HRSpace의 `리본 메뉴 - 홈 - 부분` 버튼을 누른 후, 작업물에서 도장 작업을 수행할 face들을 마우스로 클릭해 선택하십시오. 만일 단 1개의 face만을 포함하는 작업물이라면 face 선택은 생략할 수 있습니다. (STL 파일 형상이면, face가 1개입니다.)

![](../_assets/paint/sel-face.png)

`Add sel. Faces` 버튼을 클릭하면, 선택된 face들이 등록되며, 등록된 face 개수가 대화상자에 표시됩니다. `Clear` 버튼을 누르면 등록이 모두 제거됩니다. 만일 CAD 형상의 mesh가 충분히 작지 않다면 도막이 형상화될 때 시각적인 정교함이 떨어지기 때문에, face 등록 전 mesh를 잘게 나누는 절차를 수행할 수 있습니다. `sub-div.`를 체크하고 길이(mm)를 설정하면, 이 길이 이하로 mesh를 나누어 줍니다. (길이를 작게 할수록 메모리 소모와 연산시간이 길어지므로 유의하십시오.)

Face가 1개인 경우는 `auto for single select`를 체크해 두면, HRSpace 프로젝트가 열릴 때 등록 절차가 자동으로 수행됩니다. 프로젝트를 열고 바로 재생버튼을 눌러 도막 형성 시뮬레이션을 보고 싶은 경우 사용할 수 있는 기능입니다.

도막을 형성하기 전 작업물의 고유한 재질 색상과 투명도는 모델을 선택하고 리본메뉴의 스타일 그룹에서 조정하면 됩니다.

도장 건 `/YP020/tap/bell/crd` 의 확장 속성을 열어, 도장 파라미터를 설정해줍니다. 각 속성의 의미는 다음 표와 같습니다.

![](../_assets/paint/paint-gun-prop.png)


<table>
<tr>
    <th>속성명</th>
    <th>설명</th>
    <th>단위, 범위</th>
</tr>
<tr>
    <td>Angle</td>
    <td>도료의 분사 각도.(원뿔의 중심에서 빗면까지의 각도)</td>
    <td>deg</td>
</tr>
<tr>
    <td>Length</td>
    <td>도료의 분사 거리. (원뿔의 높이)</td>
    <td>mm</td>
</tr>
<tr>
    <td>AmountMax</td>
    <td>도막이 형성되는 두께의 최대값.</td>
    <td>단위 없음</td>
</tr>
<tr>
    <td>ColorMinUsed</td>
    <td>최소 색상을 사용할 지 여부.<br>체크하지 않으면, ColorMin, OpacityMin은 무시된다.</td>
    <td></td>
</tr>
<tr>
    <td>ColorMin</td>
    <td>최소 색상.<br>도료 두께가 최소일 때 표현할 색상을 RGB값으로 설정.</td>
    <td>RGB값 각각 0~255</td>
</tr>
<tr>
    <td>OpacityMin</td>
    <td>최소 불투명도. 도료 두께가 최소일 때 표현할 불투명도를 RGB값으로 설정.</td>
    <td>0~1</td>
</tr>
<tr>
    <td>ColorMax</td>
    <td>최대 색상. 도료 두께가 최대(AmountMax)일 때 표현할 색상을 RGB값으로 설정.</td>
    <td>RGB값 각각 0~255</td>
</tr>
<tr>
    <td>OpacityMax</td>
    <td>최대 불투명도. 도료 두께가 최대(AmountMax)일 때 표현할 불투명도를 RGB값으로 설정.</td>
    <td>0~1</td>
</tr>
</table>


작업물 표면의 어느 지점에 도료를 계속 분사하면 해당 지점의 두께 데이터 값이 내부적으로 계속 증가합니다. 하지만 두께가 AmountMax 설정값에 도달하면 더 이상 증가하지 않습니다.

작업물 표면의 두께 데이터 값에 따라 적절한 색상으로 표현되는데, ColorMinUsed 속성의 체크여부에 따라 아래 표와 같이 2가지 방식 중 하나가 적용됩니다.

<table>
<tr>
    <th>ColorMinUsed</th>
    <th>색상 표현</th>
</tr>
<tr>
    <td>체크된 경우,<br>(최소색상 사용)</td>
    <td>
    - 도료 두께가 최소일 때는 ColorMin, OpacityMin으로 지정한 색상, 불투명도로 표현.<br>
    - 도료 두께가 최대(AmountMax)일 때는 ColorMax, OpacityMax로 지정한 색상, 불투명도로 표현.<br>
    - 두께가 최소~최대로 변해가면서 색상, 불투명도가 서서히 변해감.
    </td>
</tr>
<tr>
    <td>체크되지 않은 경우,<br>(최소색상 미사용)</td>
    <td>
    - 도료 두께가 최소일 때는 작업물 고유의 색상, 불투명도로 표현.<br>
    - 도료 두께가 최대(AmountMax)일 때는 ColorMax, OpacityMax로 지정한 색상, 불투명도로 표현.<br>
    - 두께가 최소~최대로 변해가면서 색상, 불투명도가 서서히 변해감.
    </td>
</tr>
</table>

`/conveyor/guide/part`에 대해 확장속성 대화상자를 엽니다. 시뮬레이션 중에만 도막형성이 수행되도록 하려면 실행시점을 `시뮬레이션`으로 설정하십시오. 시뮬레이션 중이 아닐 때도 도막형성이 수행되도록 하려면 `항상`으로 설정하십시오.

![](../_assets/paint/action-prop.png)


이제 설정이 끝났으므로 시뮬레이션을 수행하십시오. `Y12` 신호가 ON이 되면, 도장 건이 ON되면서 도료의 토출이 `ColorMax` 색상의 반투명한 원추형상으로 표현됩니다. 원추가 작업물 `/conveyor/guide/part` 와 겹쳐지는 부분에 도막이 형성되는 모습을 볼 수 있습니다.

![](../_assets/paint/objective-done.png)

시뮬레이션을 다시 수행할 때는, 작업물의 확장속성 대화상자에서 `Wash out` 버튼을 클릭하여 작업물에 입혀진 도막 색상을 클리어하십시오.

[__SOURCE](2-ext-model/4-path-gen-z.md)
# 2.4. 경로 자동 생성 Z (PathGenZ)


작업 공간으로 불러온 3D 작업물의 형상을 기반으로, 작업물 표면(face)에 대한 지그재그(zig-zag) 형태의 경로를 자동으로 생성해주는 기능입니다.

일반적으로 도장 작업의 로봇경로는 아래 그림과 같이 지그재그 형태로 진행하게 됩니다. 진행방향과 작업물 표면에 대한 거리 등을 편리하게 조정하기 위해, `PathGenZ` 모듈은 `투영면(projection-plane)`이라는 가상의 평면물체의 형태로 표현됩니다. 이 평면은 다른 HRSpace 모델과 마찬가지로 HRSpace의 시프트 기능을 이용하여 마우스로 자유롭게 이동, 회전시킬 수 있습니다.

![](../_assets/path-gen-z/proj-plane.png)

그림에서 보인 바와 같이, 투영면을 횡단하는 각각의 직선 경로를 획, 즉 `스트로크(stroke)`라고 하며, 스트로크 간의 간격을 `피치(pitch)`라고 합니다. 이 스트로크들을 물체 표면에 그림자처럼 투영되어 경로를 만듭니다.
또한, 깨끗한 도장작업을 위해서는 작업물 가장자리 바깥쪽으로 경유점 스텝들이 있어야 합니다. 가장자리와 경유점 스텝 간의 거리를 아래 그림처럼, `진입 방향 옵셋(inward-offset)`과 `진출 방향 옵셋(outward-offset)`이라고 합니다.

 ![](../_assets/path-gen-z/offset.png)

작업 공간이 아래와 같이 준비되어 있다고 가정합시다. 도장 로봇 1대(YP020)와 도장 작업물(part) 한 개가 배치되어 있고, 툴은 tcp1으로 설정되어 있으며, 빈 작업 프로그램(0005.JOB)이 생성되어 있습니다. 도막이 가시화되도록 도장 건 출력신호(`/YP020/Y5`)가 로봇에 장착된 도장 건(bell)에 연결되어 있습니다. 도장 작업물(part)에는 도장 건의 T경로가 지정되어 있습니다. (도막 가시화 설정에 대해서는 2.3절을 참고하십시오.)

![](../_assets/path-gen-z/pathgen-test.png)

먼저 작업 공간에 경로 자동 생성 모델 `{LIBRARY}/PathGen/PathGenZ`를 불러옵니다. 시프트 기능을 켜고 투영면의 위치와 방향을 작업물에서 적당히 떨어진 곳에 평행하게 배치합니다.

![](../_assets/path-gen-z/shift-surface.png)

하나의 작업물은 한 개 이상의 face로 구성됩니다. HRSpace의 `리본 메뉴 - 홈 - 부분` 버튼을 누른 후, 작업물에서 도장 작업을 수행할 face들을 마우스로 클릭해 선택하십시오.

![](../_assets/path-gen-z/sel-surface.png)

PathGenZ에 대해 확장 속성을 여십시오. `Add work` 버튼을 클릭하고 작업물의 T경로를 입력합니다. 
 
![](../_assets/path-gen-z/add-work.png)

이제 `Projection-plane 그룹 박스`에 있는 속성들을 대화상자의 그림과 아래 표를 참고하여 설정하면서, `Apply` 버튼을 눌러 3D 화면에 반영하십시오. 

<table>
<tr>
    <th>속성명</th>
    <th>설명</th>
    <th>단위, 범위</th>
</tr>
<tr>
    <td>Length</td>
    <td>투영면의 길이 (스트로크 선분의 수직방향). 이 길이만큼만 경로가 진행됩니다. 
(스트로크 선분의 길이는 무한한 것으로 간주됩니다.)</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>Pitch</td>
    <td>Stroke 간 간격</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>In-offset</td>
    <td>Inward-offset<br>진입 경유 스텝과 작업물 가장자리 간의 거리</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>Out-offset</td>
    <td>Outward-offset<br>진출 경유 스텝과 작업물 가장자리 간의 거리</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>One-way</td>
    <td>단 방향으로 도장 경로를 생성할 지 여부<br>
        <img src="../_assets/path-gen-z/one-way.png">
    </td>
    <td></td>
</tr>
<tr>
    <td>auto</td>
    <td>Update 동작을 주기적으로 자동으로 수행할 지 여부.<br>
        (On 시키면 조작이 더뎌질 수 있습니다.)</td>
    <td></td>
</tr>
<tr>
    <td>Flip x</td>
    <td>X 방향으로 경로를 뒤집을 지 여부</td>
    <td></td>
</tr>
<tr>
    <td>Flip y</td>
    <td>Y 방향으로 경로를 뒤집을 지 여부</td>
    <td></td>
</tr>
</table>

`Update` 버튼을 클릭하면 설정한 속성이 반영되면서 작업물 표면에 투영된 스트로크가 나타납니다. 투명면의 크기와 방향을 시프트 기능으로 조정하고, 스트로크 진행 폭과 간격을 속성으로 조정하면서 작업물 표면에 적절한 투영 스트로크를 만드십시오.

![](../_assets/path-gen-z/strokes.png)

Job 버튼을 누른 후, 스텝들을 생성할 작업 프로그램을 트리 창에서 선택합니다. 스텝 생성에 관련된 속성은 아래 표에서 설명하고 있습니다.

![](../_assets/path-gen-z/gen-steps.png)

<table>
<tr>
    <th>속성명</th>
    <th>설명</th>
    <th>단위, 범위</th>
</tr>
<tr>
    <td>X, Y, Z</td><td>도료 토출 방향(작업물 표면에 수직)과 일치시킬 툴의 직교 축</td><td></td>
</tr>
<tr>
    <td>inverse</td><td>툴의 직교 축을 반대 방향으로 할 지 여부</td><td></td>
</tr>
<tr>
    <td>fwd-align</td><td>forward-align<br>X, Y, Z에서 선택한 직교 축과는 다른 한 축을 TCP의 진행 방향으로 정렬할 지 여부</td><td></td>
</tr>
<tr>
    <td>Step gap</td>
    <td>스텝간의 최소 간격. 곡면 상에 스텝이 생성될 때, 이 값이 작을수록 많은 스텝이 만들어집니다.</td>
    <td>mm>0</td>
</tr>
</table>

HRSpace의 `리본 메뉴 - 교시 탭`에서, 생성할 스텝들의 파라미터와 기준 좌표계를 설정하십시오. 특히 툴 번호는 도장 건의 스프레이 거리에 지정한 TCP와 일치하도록 유의해야 합니다. 예제에서는 `tcp1`이므로 툴 번호는 1로 지정했습니다.

![](../_assets/path-gen-z/teach-tab.png)

`Generate` 버튼을 클릭하면 지정한 작업 프로그램에 스텝들과 도장 명령문이 생성됩니다.

![](../_assets/path-gen-z/job-generated.png)

속성 값을 조정하여 작업 프로그램을 다시 생성하고 싶다면, 먼저 `Clear JOB` 버튼을 클릭하여 생성된 스텝을 삭제한 후 `Generate` 버튼을 클릭하십시오.
아래 그림은 2.3 절에 설명한 도막 형성과 함께 시뮬레이션이 수행되는 모습을 보여주고 있습니다.

![](../_assets/path-gen-z/simulation.png)

[__SOURCE](2-ext-model/5-floor-plan.md)
# 2.5. 바닥도면 (Floor Plan)

바닥도면은 HRSpace 바닥에 CAD의 도면파일(.dxf)을 매핑하여, 신속한 배치 작업을 도와줄 수 있는 확장 모델입니다.

모델 불러오기로 라이브러리의 `FloorPlan`을 불러옵니다.

![](../_assets/load-model.png)
![](../_assets/floor-plan/load-floor-plan.png)

3D화면에는 아직 아무 것도 나타나지 않습니다. 트리창에 생성된 모델(FloorPlan)에 대해 팝업 메뉴에서 확장 속성을 선택하여 바닥도면 속성 대화상자를 여십시오. (혹은 모델 속성 대화상자에서, ![](../_assets/bt-prop.png) 버튼을 클릭해도 됩니다.)

![](../_assets/floor-plan/popup-menu-ext-prop.png)
![](../_assets/floor-plan/bt-prop-in-model-prop.png)

파일 경로를 입력해줍니다. (혹은 파일 경로 입력란 우측의 ![](../_assets/bt-more.png) 버튼을 클릭해서 해당 위치의 파일을 선택해도 됩니다.)

![](../_assets/floor-plan/bt-more-in-prop.png)

[Ok] 버튼을 눌러줍니다.

![](../_assets/floor-plan/bt-ok-in-prop.png)

![](../_assets/floor-plan/progress-in-prop.png)


파일 로딩이 완료되면, 팝업 된 메시지 박스에 정보가 출력됩니다.

![](../_assets/floor-plan/msgbox-info.png)

불러들인 도면을 확인 할 수 있습니다.

![](../_assets/floor-plan/loaded-plan.png)

(파일의 용량이 크면 도면을 불러들이는 데에 수십 초가 걸릴 수도 있습니다.)

 
![](../_assets/bt-shift.png) 기능을 사용하여 도면의 위치를 이동하여, 도면의 위치를 HRSpace의 원점과 적절히 일치시킵니다.

![](../_assets/floor-plan/adjust-origin.png)

바닥에 전시된 도면을 참고하며 배치 작업을 수행 합니다.

![](../_assets/floor-plan/layout.png)

 
바닥도면 확장모델은 다음과 같은 기능상 제약이 있습니다.

1. 색상 변환
- HRSpace에 표시되는 도면의 색상이 원본과 일치하지 않을 수 있습니다.

<table>
<tr>
  <th>AutoCAD 화면</th>
  <th>HRSpace 화면</th>
</tr>
<tr>
  <td><img src="../_assets/floor-plan/screen-autocad.png"/></td>
  <td><img src="../_assets/floor-plan/screen-hrspace.png"/></td>
</tr>
</table>

2. Text 미지원
- Text는 표시되지 않습니다.

<table>
<tr>
  <th>AutoCAD 화면</th>
  <th>HRSpace 화면</th>
</tr>
<tr>
  <td><img src="../_assets/floor-plan/screen-autocad2.png"/></td>
  <td><img src="../_assets/floor-plan/screen-hrspace2.png"/></td>
</tr>
</table>

[__SOURCE](2-ext-model/6-conveyor-sync.md)
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
