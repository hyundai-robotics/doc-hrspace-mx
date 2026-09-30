
[__SOURCE](README.md)
# Hi5/Hi6/Hi7 Controller Function Description - HRSpace4 Extension Model
[__SOURCE](0-about-this-manual/README.md)
# About the Manual

[__SOURCE](0-about-this-manual/precautions.md)
# Precautions

{% include file="en/precautions.md" %}

[__SOURCE](0-about-this-manual/safety-notice.md)
# Safety Cautions

{% include file="en/safety-notice.md" %}

{% hint style="danger" %}
During the execution of a user script, logic errors or unmet execution conditions may cause unexpected robot behavior, potentially resulting in serious injury or death.
{% endhint %}

[__SOURCE](1-preface/README.md)
# 1. Preface

This manual is based on HRSpace v4.9.2 or higher.
[__SOURCE](1-preface/1-about.md)
## 1.1 About the HRSpace4 Extension Models

The HRSpace4 extension model is a DLL library module designed to provide additional extension functions for HRSpace4. This document describes how to use each of the extension models available in HRSpace4.

<table>
<tr>
  <td width='60%'><img src="../_assets/intro/model-prop.png"/></td>
  <td>Some extension models have software library files configured in the model properties dialog. This setting does not require manipulation, so please leave it as is.</td>
</tr>
</table>
[__SOURCE](1-preface/2-prerequisite.md)
## 1.2 Prerequisite

If you are not familiar with the basic functions of HRSpace4, please first read the HRSpace4 Function Manual. (`HRSpace4 Ribbon Menu - Home - Help - Manual`)
[__SOURCE](2-ext-model/README.md)
# 2. Extension Models
[__SOURCE](2-ext-model/1-safety-fence.md)
# 2.1. Safety Fence

The safety fence is an extension model that allows you to quickly create a fence shape by clicking on the desired area with the mouse and precisely adjust the layout by typing coordinate values at the corner positions.

Load the `Jig - Fence` from the library with `Load Model`.

![](../_assets/load-model.png)

![](../_assets/safety-fence/load-model-fence.png)

Nothing appears on the 3D screen yet. Open the `Fence properties` dialog by selecting the `extension properties` from the popup menu for the created model in the tree window. (Or you can click the ![](../_assets/bt-prop.png) button in the model property dialog.)

![](../_assets/popup-menu-ext-prop.png)

![](../_assets/safety-fence/fence-prop.png)

You can input the fence path by clicking the vertex positions with the mouse. First, select a `Snap` value to ensure the vertex coordinates are accurate. In this example, 100mm has been selected. Press and hold the `Start Input` button, then left-click on the grid surface of the 3D screen to define the vertices. A fence will be created between the clicked points. The picture below shows an example of a fence created by clicking seven points.

![](../_assets/safety-fence/fence.png)

Press the `End Input` button to finish inputting the path. The entered coordinate values can be checked in the `FencePath` category of the fence properties and can be modified precisely according to the design.

![](../_assets/safety-fence/fence-path.png)
![](../_assets/safety-fence/fence-path-5y.png)

Double-click the desired coordinate values to modify them, and click the `Apply` button to reflect the changes on the 3D screen.
(Pressing the `Start Input` button again will allow you to re-enter the fence path from the beginning.)

You can modify various fence properties to change the type, height, thickness, wire color, wire gap, and so on. The example below shows the wire-type fence created earlier changed to a glass-type fence. The color of the screen (glass) is red, and the transparency is set to 70% to depict an arc welding cell. (The color of the fence frame can be changed from the `Ribbon Menu - Style`.)

![](../_assets/safety-fence/glass-type.png)

Let's create a door in the open space between the fences. As a child of the existing fence, create one fence using Load Model and rename it.

![](../_assets/safety-fence/rename-door.png)

Open the extension properties of the new fence (door) and press the `Start Input` button. After specifying two coordinates on the grid surface with a left-click of the mouse, press the `End Input` button.

![](../_assets/safety-fence/door-overlap1.png)
->
![](../_assets/safety-fence/door-overlap2.png)

If the pillars of the fence overlap with the pillars of the door, they may appear unnatural, as shown in the upper left image. Remove the checks from the `LeftPillar` and `RightPillar` properties of the fence to eliminate the edge pillars of the fence.

![](../_assets/safety-fence/prop-right-pillar.png)

Modify the extension properties and style of the door to create a similar form to the fence. Finally, input a suitable door opening angle (deg.) in the `DoorOpenAngle` property, and the door will be completed. Now, save the project file.

![](../_assets/safety-fence/prop-door-open-angle.png)
![](../_assets/safety-fence/fence-door-open.png)
[__SOURCE](2-ext-model/2-robot-riser.md)
# 2.2 Robot Riser

The `Robot Riser` is an extension model that allows you to quickly create a robot riser shape of the desired size by entering some key values.

Load the `Jig - Riser` from the library using the model import function.

![](../_assets/load-model.png)

![](../_assets/robot-riser/load-model-riser.png)

A robot robot riser model is created with default parameters. Open the `Riser Properties` dialog for the robot riser by selecting the `extension properties...` from the popup menu for the created model.

![](../_assets/robot-riser/popup-menu-ex-prop.png)
![](../_assets/robot-riser/riser-prop.png)

`Size` properties are provided on the right side of the dialog. When you select the robot type from the `AutoSet` dropdown list box, the property values are automatically set to the appropriate robot riser size.

![](../_assets/robot-riser/drop-list.png)

The higher the robot riser, the larger the area of the lower panel needs to be for stability. If the height of the stand is over 1000mm, checking the `Height>1000mm` checkbox will appropriately set the `WidthBottom` value. (You can also set it manually.)

There is a coordinate system model called `crd` on the top surface of the robot riser. When you load a robot as a child model of this coordinate system, the robot will be installed precisely on the top surface. (Alternatively, you can also drag and drop an already loaded robot from the tree window to `crd` with the left mouse button.)

![](../_assets/robot-riser/robot-on-crd.png)
[__SOURCE](2-ext-model/3-paint.md)
# 2.3. Paint Gun, Paint Work

Using the `PaintGun` and the `PaintWork` extension model, the simulation visually represents the formation of the coating on the surface of the 3D workpiece. It helps to determine whether the coating is not formed in certain areas of the workpiece or is excessively overlapped.

{% hint style="warning" %}
The painting application feature is only available on the Hi5a controller, and it is currently not available on Hi6/Hi7.
{% endhint %}

Let’s assume that a workspace like the one below has been created, and we will add the coating formation function in this state. The workspace has two `YP020` units, each equipped with the paint gun (`tap/bell`). The workpiece (`part`) on the shuttle (`/conveyor/guide`) moves between the robots, and the paint discharged from the two paint guns must form a coating on the surface of this workpiece.

![](../_assets/paint/objective.png)

First, connect the `MxPaintGun.DLL` library to each of the two paint gun models.

1. Open the model property dialog for `/YP020/tap/bell/crd`.
2. Click the ![](../_assets/bt-more.png) button to the right of the model extension input field.
3. Select `/Library/Tool/painting/MxPaintGun.dll`.
4. Click the `OK` button.
5. Apply the same settings for `/YP020_2/tap/bell/crd`.

![](../_assets/paint/model-ex-pathname.png)

Connect the `MxPaintWork.DLL` library to the workpiece model.

1. Open the model property dialog for `/conveyor/guide/part`.
2. Click the ![](../_assets/bt-more.png) button to the right of the model extension input field.
3. Select `/Library/Tool/painting/MxPaintWork.dll`.
4. Click the `OK` button.

Connect the paint gun to be ON/OFF based on the robot's output signal. If, for example, the paint gun is controlled by the `Y12` output signal, create an I/O connection model to connect the `Y12` output of both robots to the `SprayIn` input signal of each paint gun.

![](../_assets/paint/minitp.png)

![](../_assets/paint/ioconn.png)

Now, open the extension property dialog for the paint work item `/conveyor/guide/part`.

![](../_assets/paint/popup-menu-ex-prop.png)
![](../_assets/paint/paint-work-prop.png)

First, you need to specify the guns to be used for painting. Press the `Add gun` button and specify the T paths for the two paint guns as shown below.

Next is the specification regarding the paint faces. A single workpiece can consist of one or more faces. Click on the faces of the workpiece where the painting will be performed using the mouse after pressing the `Ribbon Menu - Home - Parts` button in HRSpace. If the workpiece consists of only one face, you can skip face selection. (If it is an STL file shape, there is only one face.)

![](../_assets/paint/sel-face.png)

Click the `Add sel. Faces` button to register the selected faces, and the number of registered faces will be displayed in the dialog box. Pressing the `Clear` button will remove all registrations. If the mesh of the CAD shape is not sufficiently small, the visual precision of the coating may be reduced when it is formed, so you may want to divide the mesh into smaller pieces before registering faces. Check `sub-div.` and set the length (mm); this will divide the mesh to lengths less than this value. (Note that the smaller the length, the greater the memory consumption and computation time.)

In the case of a single face, checking `auto for single select` allows the registration process to be performed automatically when the HRSpace project is opened. This is a feature you can use if you want to open the project and immediately see the coating formation simulation by pressing the play button.

Before forming the coating, you can adjust the unique material color and transparency of the workpiece by selecting the model and adjusting it in the style group of the ribbon menu.

Open the extension properties of the paint gun `/YP020/tap/bell/crd` and set the painting parameters. The meanings of each property are as follows.

![](../_assets/paint/paint-gun-prop.png)

<table>
<tr>
    <th>Property Name</th>
    <th>Description</th>
    <th>Unit, Range</th>
</tr>
<tr>
    <td>Angle</td>
    <td>The spray angle of the paint. (The angle from the center of the cone to the slope)</td>
    <td>deg</td>
</tr>
<tr>
    <td>Length</td>
    <td>The spray distance of the paint. (The height of the cone)</td>
    <td>mm</td>
</tr>
<tr>
    <td>AmountMax</td>
    <td>The maximum thickness of the coating that can be formed.</td>
    <td>No unit</td>
</tr>
<tr>
    <td>ColorMinUsed</td>
    <td>Whether to use the minimum color.<br>If not checked, ColorMin and OpacityMin will be ignored.</td>
    <td></td>
</tr>
<tr>
    <td>ColorMin</td>
    <td>Minimum color.<br>Set the color to be displayed when the paint thickness is at its minimum using RGB values.</td>
    <td>RGB values 0~255 each</td>
</tr>
<tr>
    <td>OpacityMin</td>
    <td>Minimum opacity. Set the opacity for the minimum paint thickness using RGB values.</td>
    <td>0~1</td>
</tr>
<tr>
    <td>ColorMax</td>
    <td>Maximum color. Set the color to be displayed when the paint thickness is at its maximum (AmountMax) using RGB values.</td>
    <td>RGB values 0~255 each</td>
</tr>
<tr>
    <td>OpacityMax</td>
    <td>Maximum opacity. Set the opacity for the maximum paint thickness (AmountMax) using RGB values.</td>
    <td>0~1</td>
</tr>
</table>

When paint is continuously sprayed at a certain point on the workpiece surface, the thickness data value of that point continuously increases internally. However, once the thickness reaches the `AmountMax` setting, it no longer increases.

The thickness data value of the workpiece surface is expressed in an appropriate color depending on whether the ColorMinUsed property is checked, as shown in the table below.

<table>
<tr>
    <th>ColorMinUsed</th>
    <th>Color Representation</th>
</tr>
<tr>
    <td>Checked,<br>(Minimum color used)</td>
    <td>
    - When the paint thickness is minimum, the color and opacity specified by ColorMin and OpacityMin are used for representation.<br>
    - When the paint thickness is maximum (AmountMax), the color and opacity specified by ColorMax and OpacityMax are used for representation.<br>
    - The color and opacity transition gradually from minimum to maximum thickness.
    </td>
</tr>
<tr>
    <td>Unchecked,<br>(Minimum color not used)</td>
    <td>
    - When the paint thickness is minimum, the unique color and opacity of the workpiece are used for representation.<br>
    - When the paint thickness is maximum (AmountMax), the color and opacity specified by ColorMax and OpacityMax are used for representation.<br>
    - The color and opacity transition gradually from minimum to maximum thickness.
    </td>
</tr>
</table>

Open the extension properties dialog for `/conveyor/guide/part`. To ensure the coating formation occurs only during the simulation, set the execution timing to `Simulation`. If you want the coating formation to occur even when not in simulation, set it to `Always`.

![](../_assets/paint/action-prop.png)

Now that the setup is complete, perform the simulation. When the `Y12` signal becomes ON, the paint gun will turn ON, and the discharge of the paint will be represented as a translucent conical shape of the `ColorMax` color. You will be able to see how the coating forms where the cone overlaps with the workpiece `/conveyor/guide/part`.

![](../_assets/paint/objective-done.png)

When performing the simulation again, click the `Wash out` button in the workpiece's extension properties dialog to clear the coating color applied to the workpiece.
[__SOURCE](2-ext-model/4-path-gen-z.md)
# 2.4. Path Generation Z (PathGenZ)

Based on the shape of the 3D workpiece imported into the workspace, this function automatically generates a zigzag path for the workpiece surface (face).

In general, the robot path for painting operations proceeds in a zigzag shape as shown in the figure below. To conveniently adjust the direction of progress and the distance to the workpiece surface, the `PathGenZ` module is represented as a virtual plane object called the `projection-plane`. This plane can be freely moved and rotated using the `Gizmo` function of HRSpace, just like other HRSpace models.

![](../_assets/path-gen-z/proj-plane.png)

As shown in the figure, each straight path crossing the projection plane is referred to as a stroke, and the distance between strokes is called the pitch. These strokes create a path projected onto the surface of the object like a shadow.
Additionally, for a clean painting operation, there must be waypoint steps outside the edges of the workpiece. The distances between the edge and the waypoint steps are referred to as the `inward-offset` and `outward-offset`, represented as shown in the figure below.

![](../_assets/path-gen-z/offset.png)

Assuming the workspace is prepared as follows: one painting robot (YP020) and one painting workpiece (part) are placed, the tool is set to `tcp1`, and an empty work program (0005.JOB) has been created. The paint gun output signal (`/YP020/Y5`) is connected to the paint gun (bell) attached to the robot to visualize the coating. A T path for the paint gun has been specified for the painting workpiece (part). (For details on the coating visualization settings, refer to Section 2.3.)

![](../_assets/path-gen-z/pathgen-test.png)

First, load the path generation model `{LIBRARY}/PathGen/PathGenZ` into the workspace. Turn on the shift function and position the projection plane parallel to a suitable distance from the workpiece.

![](../_assets/path-gen-z/shift-surface.png)

One workpiece is composed of one or more faces. Press the `Ribbon Menu - Home - Part` button and click on the faces to be painted on the workpiece with the mouse.

![](../_assets/path-gen-z/sel-surface.png)

Open the `Path Generator Z Properties`. Click the `Add work` button and input the T path of the workpiece.

![](../_assets/path-gen-z/add-work.png)

Now, refer to the dialog box and the table below to set the properties in the `Projection-plane` group box, and press the `Apply` button to reflect changes on the 3D screen.

<table>
<tr>
    <th>Property Name</th>
    <th>Description</th>
    <th>Unit, Range</th>
</tr>
<tr>
    <td>Length</td>
    <td>The length of the projection plane (in the vertical direction of the stroke line segment). The path will proceed only this distance. 
(The length of the stroke line segment is considered infinite.)</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>Pitch</td>
    <td>The distance between strokes.</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>In-offset</td>
    <td>Inward-offset<br>Distance between the inward waypoint step and the edge of the workpiece.</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>Out-offset</td>
    <td>Outward-offset<br>Distance between the outward waypoint step and the edge of the workpiece.</td>
    <td>mm<br>>0</td>
</tr>
<tr>
    <td>One-way</td>
    <td>Whether to generate painting paths only in one direction<br>
        <img src="../_assets/path-gen-z/one-way.png">
    </td>
    <td></td>
</tr>
<tr>
    <td>auto</td>
    <td>Whether to perform the Update operation automatically at regular intervals.<br>
        (Turning it On may slow down operation.)</td>
    <td></td>
</tr>
<tr>
    <td>flip x</td>
    <td>Whether to flip the path in the X direction.</td>
    <td></td>
</tr>
<tr>
    <td>flip y</td>
    <td>Whether to flip the path in the Y direction.</td>
    <td></td>
</tr>
</table>

Clicking the `Update` button will project the specified properties and display the strokes projected onto the surface of the workpiece. Adjust the size and direction of the transparent surface using the shift function, and create appropriate projected strokes on the surface of the workpiece by adjusting the stroke width and spacing as properties.

![](../_assets/path-gen-z/strokes.png)

After pressing the Job button, select the work program in the tree view where the steps will be generated. The properties related to step generation are explained in the table below.

![](../_assets/path-gen-z/gen-steps.png)

<table>
<tr>
    <th>Property Name</th>
    <th>Description</th>
    <th>Unit, Range</th>
</tr>
<tr>
    <td>X, Y, Z</td><td>The orthogonal axes of the tool aligned with the direction of paint discharge (perpendicular to the workpiece surface).</td><td></td>
</tr>
<tr>
    <td>inverse</td><td>Whether to set the orthogonal axes of the tool in the opposite direction.</td><td></td>
</tr>
<tr>
    <td>fwd-align</td><td>forward-align<br>Whether to align a different axis from the selected orthogonal axes in X, Y, Z with the forward direction of the TCP.</td><td></td>
</tr>
<tr>
    <td>Step gap</td>
    <td>The minimum distance between steps. The smaller this value, the more steps are created when steps are generated on the curved surface.</td>
    <td>mm>0</td>
</tr>
</table>

From the `Ribbon Menu - Teach Tab` of HRSpace, set the parameters and reference coordinate system for the steps to be created. Especially, take care that the tool number matches the TCP specified for the spray distance of the paint gun. In the example, the tool number is set to 1 since it is `tcp1`.

![](../_assets/path-gen-z/teach-tab.png)

Clicking the `Generate` button will create steps and painting commands in the designated work program.

![](../_assets/path-gen-z/job-generated.png)

If you want to regenerate the work program by adjusting property values, first click the `Clear JOB` button to delete the generated steps, and then click the `Generate` button.
The figure below shows the simulation being performed along with the coating formation explained in Section 2.3.

![](../_assets/path-gen-z/simulation.png)
[__SOURCE](2-ext-model/5-floor-plan.md)
# 2.5. Floor Plan

The floor plan is an extension model that helps facilitate quick placement by mapping a CAD drawing file (.dxf) onto the HRSpace floor.

Load the library's `FloorPlan` via the model import option.

![](../_assets/load-model.png)
![](../_assets/floor-plan/load-floor-plan.png)

No content is visible on the 3D screen yet. Open the floor plan properties dialog by selecting the extension properties from the popup menu of the created model (FloorPlan) in the tree view. (You can also click the ![](../_assets/bt-prop.png) button in the model properties dialog.)

![](../_assets/floor-plan/popup-menu-ext-prop.png)
![](../_assets/floor-plan/bt-prop-in-model-prop.png)

Enter the file path. (Alternatively, you can click the ![](../_assets/bt-more.png) button on the right side of the file path input field to select the file from that location.)

![](../_assets/floor-plan/bt-more-in-prop.png)

Press the `Ok` button.

![](../_assets/floor-plan/bt-ok-in-prop.png)

![](../_assets/floor-plan/progress-in-prop.png)


Once the file loading is complete, information will be displayed in the popup message box.

![](../_assets/floor-plan/msgbox-info.png)

You can check the imported drawing.

![](../_assets/floor-plan/loaded-plan.png)

(If the file size is large, it may take several tens of seconds to load the drawing.)

 
Use the ![](../_assets/bt-gizmo.png) function to move the position of the drawing and align it appropriately with the origin of HRSpace.

![](../_assets/floor-plan/adjust-origin.png)

Perform the placement task by referencing the displayed drawing on the floor.

![](../_assets/floor-plan/layout.png)

 
The floor plan extension model has the following functional limitations.

#### 1. Color Conversion
- The colors of the drawing displayed in HRSpace may not match the original.

<table>
<tr>
  <th>AutoCAD Screen</th>
  <th>HRSpace Screen</th>
</tr>
<tr>
  <td><img src="../_assets/floor-plan/screen-autocad.png"/></td>
  <td><img src="../_assets/floor-plan/screen-hrspace.png"/></td>
</tr>
</table>

#### 2. Text Not Supported
- Text will not be displayed.

<table>
<tr>
  <th>AutoCAD Screen</th>
  <th>HRSpace Screen</th>
</tr>
<tr>
  <td><img src="../_assets/floor-plan/screen-autocad2.png"/></td>
  <td><img src="../_assets/floor-plan/screen-hrspace2.png"/></td>
</tr>
</table>
[__SOURCE](2-ext-model/6-conveyor-sync.md)
# 2.6. Conveyor Sync

- Please read the `Sensor Sync` manual first. 
  * Hi5a Controller Function Manual - Sensor Sync
  * [Hi6 Controller Function Manual - Sensor Sync (Conveyor, Press)](https://hrbook-hrc.web.app/#/view/doc-sensor-sync/en/README?cont_model=Hi6)
  * [Hi7 Controller Function Manual - Sensor Sync (Conveyor, Press)](https://hrbook-hrc.web.app/#/view/doc-sensor-sync/en/README?cont_model=Hi7)

{% hint style="info" %}
The Hi6/Hi7 conveyor synchronization feature is supported starting from HRSpace v4.10.0.
{% endhint %}


The conveyor sync extension model is an extension model in HRSpace that generates the Pulse Count and Limit Switch output of a conveyor and transmits them to the VRC, enabling conveyor synchronization simulation.

Import `conveyor`, `conveyor_CCW (Counterclockwise Curve)`, or `conveyor_CW (Clockwise Curve)` from the external equipment library using `Load Model`.

![](../_assets/load-model.png)
![](../_assets/conv-sync/load-conveyor.png)


## 2.6.1. Extension Properties Dialog

Open the Conveyor Properties dialog by selecting `Extension Properties...` from the pop-up menu for the created model (conveyor) in the tree window. (You can also click the ![](../_assets/bt-prop.png) button in the `Model Properties` dialog.) 

![](../_assets/conv-sync/popup-menu-ext-prop.png)
![](../_assets/conv-sync/bt-prop-in-prop.png)
![](../_assets/conv-sync/conveyor-prop.png)


The roles of each button are as follows:

| Button Name | Role |
|-----------|----------------------------------------------------------|
| `start` | Starts the conveyor. `pulse cnt.` starts to increase. |
| `stop` | Decelerates and stops the conveyor. |
| `reset` | Resets the pulse count and workpiece position to 0, bringing it to a stopped state. It also outputs the `SyncReset` signal as a 500ms single pulse. |
| `put` | Starts moving the workpiece on the conveyor. |
| `J+`/`J-` | Jog buttons that move the conveyor forward or backward when stopped. |
| `CCW`/`CW` | Displayed only for Curve-type conveyors. Selects Counterclockwise (CCW) / Clockwise (CW). |

- By default, the workpiece is a rectangular box shape named `target`. If necessary, adjust the `Model Properties` to set the desired size, height, basic shape, or shape files such as STL. However, the name must remain `target`.


You can configure the properties below in the table at the bottom. Settings are applied only after clicking the `Apply` button, and they can also be configured during operation.

| Property Name |            Description                               |
|-----------|----------------------------------------------------------|
| `Stroke` | Workpiece outfeed position. Re-initialized to position 0 when `target` reaches this point. |
| `Resolution` | Encoder resolution. Set this to the same value calculated and configured automatically in VRC in the procedure below |
| `Speed` | Target speed of the conveyor. |
| `Accel` | Acceleration of the conveyor. |
| `Decel` | Deceleration of the conveyor. |
| `LS position` | Limit switch position. When `target` reaches this point in the forward direction, the `LimitSwitch` signal and `LS` lamp turn on for 300ms.|


## 2.6.2. Conveyor Settings 

Referring to [Sensor Sync Parameter Settings](https://hrbook-hrc.web.app/#/view/doc-sensor-sync/en/3-user-interface/3-3-sensor-sync-parameter?cont_model=Hi7), first set the sync state on the `Sensor Sync Parameter` screen of VTP to `Conveyor`, and set the conveyor type to `Linear` or `Circle`.

![](../_assets/conv-sync/vtp-setup.png)


### Controller Input Connection

The robot controller performs operations in exact synchronization with the position of the workpiece on the conveyor. To achieve this, the robot controller receives the following 3 pieces of information as inputs from the conveyor to estimate the position of the workpiece. (Since the robot controller has 2 input channels, it can connect with up to 2 conveyors.)

- `SyncReset`: Considers the current conveyor pulse input value as workpiece position 0. (1bit)
- `LimitSwitch`: Reference position information of the workpiece (1bit) that turns ON when a workpiece moving along the conveyor activates a limit switch, such as an optical sensor.
- `PulseCount`: Pulse information used to calculate the real-time speed of the conveyor (16bit).


The method of receiving these 3 pieces of information varies depending on the controller model.

- Hi5a Controller
  * Dedicated Conveyor I/F Board (BD585)
- Hi6/Hi7 Controller (Supports 2 methods)
  * Dedicated Conveyor I/F Board (BD641T, BD681)
  * Crevis FnIO Module M5112: Inputted as user input (di, diw).


The conveyor model in the HRSpace virtual space must transmit the above 3 pieces of information to the Virtual Robot Controller (VRC) just like an actual conveyor. The connection method is as follows:


- Dedicated Conveyor I/F Board

  Assign the TPath of the conveyor model to the Pulse Counter item in `Robot Properties - Sync`. It is transferred internally without needing a virtual I/O connection.
  
  ![](../_assets/conv-sync/robot-prop-sync.png)
 

- FnIO Module Method

  Set the assigned signals for `Syncronization reset`, `Limit switch input`, and `Pulse counter input (16bit)` under `Input Signal Assign` group on the `Sensor sync parameter` screen of VTP.

  After creating an `I/O Connection` object in the workspace, open its properties and configure it. Connect the 3 output values of the conveyor model (`SyncReset`, `LimitSwitch`, `PulseCount`) to the respective `di` areas configured in VTP.

  * Important: Since these output values must be transmitted to the VRC at a fast cycle, be sure to check the `Realtime` checkbox.

  ![](../_assets/conv-sync/ioconn.png)


Open the `Sensor Sync` monitoring panel of VTP and verify if the pulse count and speed are displayed identically to those in the Extension Properties dialog. If confirmed, it is connected properly.

![](../_assets/conv-sync/monitor-pane.png)


### Limit Switch and Outfeed Position

- Check the appropriate workpiece outfeed position, then enter the position value into the `Stroke` property.
- Check the appropriate position to place the limit switch, then enter the position value into the `LS position` property.
  * When the workpiece passes the limit switch, check if `Limit Switch Input` in the `Sensor Sync` monitoring panel of VTP momentarily changes to 1 and whether `Entered Workpiece Count` increases.


### Conveyor Angle

Referring to the Sensor Sync manual, perform the automatic conveyor angle setting in the virtual space using VTP. (You can execute this while moving the workpiece using the `J+`, `J-`, or `start`, `stop` buttons in the Conveyor Properties dialog.)


### Encoder Resolution

Referring to the Sensor Sync manual, perform the automatic conveyor encoder resolution setting in the virtual space using VTP. Enter the same value as the configured encoder resolution in the `Resolution` field of the Extension Properties dialog, then click the `Apply` button to reflect it.


### Saving

Once each setting is completed, save the entire HRSpace project.


## 2.6.3. Teaching

Referring to the Sensor Sync manual, teach the conveyor sync operation.
Position the workpiece at a suitable location using the `J+` and `J-` buttons, then perform teaching for the workpiece while the conveyor is stopped.

![](../_assets/conv-sync/teach-3d.png)
![](../_assets/conv-sync/teach-vtp.png)


## 2.6.4. Conveyor Sync Simulation

Initialize the conveyor and workpiece position using the `reset` button, start the conveyor using the `start` button, and dispatch the workpiece from the initial position using the `put` button.
When the taught job is executed, the robot will wait at the `cv.wait` statement (for Hi6/Hi7). Once the workpiece reaches the limit switch position, the robot starts the conveyor sync operation.


## 2.6.5. Ethernet Data Transmission to Actual Hi5a Controller

If you set `Robot Properties - Controller connection` to `ENetHi5`, the `PulseCount` property value and `LimitSwitch` I/O values are also transmitted to the actual Hi5a controller via Ethernet. (Hi6/Hi7 are not supported.)

![](../_assets/conv-sync/sel-vrc.png)
