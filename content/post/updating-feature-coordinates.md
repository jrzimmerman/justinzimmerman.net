+++
author = "Justin Zimmerman"
date = "2015-05-08T08:45:13-04:00"
description = "Updating feature coordinates with python."
keywords = ["Python", "ESRI", "GIS", "ArcGIS", "Coordinates"]
tags = ["Python", "GIS"]
title = "Updating Feature Coordinates With Python"
topics = ["Python", "GIS"]
type = "post"

+++

I was asked to update the location of manhole points with new survey data. Traditionally this is a long task, dragging the old manholes to their new locations.

Before we assume how it would be so much easier to just delete the old data, and import the new data. First we have to consider all the attribute information associated with the data, sure we can join based on the Manhole ID but what happens when we have to worry about attachments?

 > Luckily, python makes this an easy task.

Example: You have a feature class called ‘Manholes’ that has 500 point features. You received a new XY table that has updated locations for 103 points. Update the point locations by doing the following:

[1.] Add point feature class and the Table as a dbf/event(updated xy) layer to ArcMap and do a 'Field join' based on a unique identifier, ours is the Manhole ID field, this will join the data from the table permanently to the feature.

[2.] Open attribute table of the feature class and select the records/features which should move to updated XY locations.

[3.] Right click on the Shape column and open Field Calculator.

[4.] In the Field Calculator select Python Parser. Check Show Codeblock

Copy following script in the Pre-Logic Script Code window

    def XYsetVALUE( shape, X_value, Y_value):
    point = shape.getPart(0)
    point.X = X_value
    point.Y = Y_value
    return point

In the window below 'Shape=' copy following:

    XYsetVALUE ( !SHAPE!, !X_COORD!, !Y_COORD! )

Here you will need to modify <code>!X\_COORD!</code> and <code>!Y\_COORD!</code> to match the names of your coordinate columns.

E.g. If the name of the column containing X coordinate values is 'POINT_X' and that of Y coordinte values is 'POINT_Y' the script would be

    XYsetVALUE ( !SHAPE!, !POINT_X!, !POINT_Y! )

In my case it was <code>XYsetVALUE ( !SHAPE!, !X!, !Y! )</code>

[5.] Click ok

[6.] Now right click on the OLD XY and Calculate Geometry for XY and the updated XY will be calculated.
