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

Press the [Ok] button.

![](../_assets/floor-plan/bt-ok-in-prop.png)

![](../_assets/floor-plan/progress-in-prop.png)


Once the file loading is complete, information will be displayed in the popup message box.

![](../_assets/floor-plan/msgbox-info.png)

You can check the imported drawing.

![](../_assets/floor-plan/loaded-plan.png)

(If the file size is large, it may take several tens of seconds to load the drawing.)

 
Use the ![](../_assets/bt-shift.png) function to move the position of the drawing and align it appropriately with the origin of HRSpace.

![](../_assets/floor-plan/adjust-origin.png)

Perform the placement task by referencing the displayed drawing on the floor.

![](../_assets/floor-plan/layout.png)

 
The floor plan extension model has the following functional limitations.

1. Color Conversion
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

2. Text Not Supported
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