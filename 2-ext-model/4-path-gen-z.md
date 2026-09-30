# 2.4. 경로 자동 생성 Z (PathGenZ)


작업 공간으로 불러온 3D 작업물의 형상을 기반으로, 작업물 표면(face)에 대한 지그재그(zig-zag) 형태의 경로를 자동으로 생성해주는 기능입니다.

일반적으로 도장 작업의 로봇경로는 아래 그림과 같이 지그재그 형태로 진행하게 됩니다. 진행방향과 작업물 표면에 대한 거리 등을 편리하게 조정하기 위해, `PathGenZ` 모듈은 `투영면(projection-plane)`이라는 가상의 평면물체의 형태로 표현됩니다. 이 평면은 다른 HRSpace 모델과 마찬가지로 HRSpace의 `기즈모` 기능을 이용하여 마우스로 자유롭게 이동, 회전시킬 수 있습니다.

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
