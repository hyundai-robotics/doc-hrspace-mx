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