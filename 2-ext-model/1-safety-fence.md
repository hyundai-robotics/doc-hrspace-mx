# 2.1. Safety Fence

The safety fence is an extended model that allows you to quickly create a fence shape by clicking on the desired area with the mouse and precisely adjust the layout by typing coordinate values at the corner positions.

Load the `Jig - Fence` from the library with Load Model.

![](../_assets/load-model.png)

![](../_assets/safety-fence/load-model-fence.png)

Nothing appears on the 3D screen yet. Open the safety fence property dialog by selecting the extended properties from the popup menu for the created model in the tree window. (Or you can click the ![](../_assets/bt-prop.png) button in the model property dialog.)

![](../_assets/popup-menu-ext-prop.png)

![](../_assets/safety-fence/fence-prop.png)

You can input the fence path by clicking the vertex positions with the mouse. First, select a snap value to ensure the vertex coordinates are accurate. In this example, 100mm has been selected. Press and hold the `Start Input` button, then left-click on the grid surface of the 3D screen to define the vertices. A fence will be created between the clicked points. The picture below shows an example of a fence created by clicking seven points.

![](../_assets/safety-fence/fence.png)

Press the `End Input` button to finish inputting the path. The entered coordinate values can be checked in the `FencePath` category of the fence properties and can be modified precisely according to the design.

![](../_assets/safety-fence/fence-path.png)
![](../_assets/safety-fence/fence-path-5y.png)

Double-click the desired coordinate values to modify them, and click the `Apply` button to reflect the changes on the 3D screen.
(Pressing the `Start Input` button again will allow you to re-enter the fence path from the beginning.)

You can modify various fence properties to change the type, height, thickness, wire color, spacing, and so on. The example below shows the wire-type fence created earlier changed to a glass-type fence. The color of the screen (glass) is red, and the transparency is set to 70% to depict an arc welding cell. (The color of the fence frame can be changed from the `Ribbon Menu - Style`.)

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