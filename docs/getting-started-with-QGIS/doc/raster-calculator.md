# GIS Processing
[Home](../README.md)

Index
* [Raster Calculator](#raster-calculator)
* [Raster Calculator Tool](#raster-calculator-tool)
* [Examples](#examples)

[Read the QGIS Docs](https://docs.qgis.org/testing/en/docs/user_manual/working_with_raster/raster_analysis.html)<br>
The raster calculations are a critical component any GIS software. QGIS provides access to this capability from a raster calculator. Two slightly different calculators are availiable; the Processing Toolbox Raster Calculator and the Raster Menu Raster Calculator.

## Raster Calculator
The Raster Calculator that is accessed from the Raster Menu provides a quick access to the raster bands availiable to the calculator from your map, a list of operators, a text box for building your expression, and a section for parameters of your output raster.

![Raster Calculator](../images/raster-menu-calculator.png)

To build your expression you can either type your expression directly into the expression box, click on the raster bands and operator buttons, or a combination of typing and clicking to populate your expression [see examples](#examples).  

## Raster Calculator Tool

The Raster Calculator tool that is accessed from the Processing Toolbox is within the Raster Analysis group. This tool offers very similar functionality to the calculator accessed from the Raster Menu but is organized differently. It can be used to a create a temporary raster, and can be chained with other tools in either the Graphical Modeler or Python.

![Raster Calculator Tool](../images/raster-calculator-tool.png)

Convienently this tool also allows the designation of a reference raster to derive the output file projection, extent, and cell size.

## Examples
1. Expression creating an elevation mask with a single channel raster DEM called mydem <br>

    ```
    (mydem@1>=1100)*1
    ```
    In this example the conditional statement within brackets is either evaluated as 1 (True) or 0 (False) and is subsequently multiplied by one. The result would be a raster with a value of 1 for pixel values greater than or equal to 1100, and values of 0 for pixel values less than 1100.

2. Expressions can also be used to find overlapping conditions between rasters <br>
    ```
    ("mydem@1"> 1600 AND "forest_cover@1">40)*1
    ```
    In this example the expression uses the raster values from a DEM and a raster of forest cover to create a raster that can show areas over 1600 meters that have a forest cover greater than 40 percent.

3. Expressions can also be used to perform arithmetic calculations between multiple raster files and/or bands. 
    ```
    (("mydem@1">1600)+1) * "forest_cover@1"/100
    ```
    This example might be a portion of a habitat model where habitat value is proportional to forest cover percent and habitat over 1600 meters is valued twice as much as habitat less than 1600 meters.
---

[Back to Top](#gis-processing)
