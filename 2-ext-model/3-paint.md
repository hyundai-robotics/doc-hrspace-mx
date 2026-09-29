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
