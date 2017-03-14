+++
author = "Justin Zimmerman"
date = "2013-10-24T08:41:16-04:00"
description = "Visualize incident reporting for local municipalities."
keywords = ["JavaScript", "GIS"]
tags = ["JavaScript", "GIS"]
title = "Visualizing Map Service Usage"
topics = ["JavaScript", "GIS"]
type = "post"

+++

I recently developed a [JavaScript web application](http://75.151.252.249/RichlandHeatmap/) to visualize incident reporting for a local municipality collecting [Stormwater Incident Reports](http://75.151.252.249/RichlandServiceRequest/).

![Richland Service Request](/img/richlandheatmap.png)

The idea behind this application, will be to determine the usage of the reporting system, and to additionally determine "Problem Areas" for further corrective action planning.

### Importance of Dynamic Display

One of the most important considerations for determining areas, is to determine the scale. The scale the data is viewed at can change the data is interpreted.

![Small Scale](/img/smallscale.png)

Small scale cannot accurately depict areas.

![Large Scale](/img/largescale.png)

Large scale does not allow for a focused approach to specific areas.

![Just Right](/img/justright.png)

Just right. This scale provides a few areas that are easily identifiable.

### Errors

Be mindful of particular input errors. These include multiple responses from a single resident, which can skew how the data is depicted.

### How can I make this?

The [ArcGIS Solutions](http://solutions.arcgis.com/) are full of templates that can be modified for your use. I prefer to check out their [GitHub](https://github.com/Esri) account for all the latest templates.
