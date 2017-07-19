#################
QField User Guide
#################

**************
Basic workflow
**************

Opening a project
=================

To open a project, touch the :menuselection:`Menu button --> open`. This will open a file
browser window. Navigate the device filesystem to the location of the project, then select
the project and touch `open`.

Important: QGIS only has permission to modify files in folders that it owns. This means that
project files should be placed as sub-folders of the `/Android/data/ch.opengis.qfield/files`
folder on the internal device memory or SD card. Other data locations will display, but
digitizing new features will not be possible.


Project modes
============

QField has two primary modes: browsing map data, and digitizing new data. To switch
modes, touch the :menuselection:`Menu button --> mode` and then select Browse or Digitize.


Identify features
=================

A tap on a feature will identify it. Touch a feature on the identify window to see all
attribute data associated with that feature. Pressing the device back button will close the
identify window.

*QField shows the primary attribute in the initial identify window, and only shows all data
in the more detailed window. For example, contour data might show the ID of the contour,
rather than the height of the contour. To show the desired attribute instead, set the 
`Map tip display text` field in QGIS to the primary field you want to view. Additionally,
open the layer attribute table in QGIS and view it in Form View by clicking the small toolbar
button at the bottom right of the window. In the left panel click on the drop down arrow and
select the desired field for display.*

Maybe put the above in a separate page so I can go into a lot of detail on exactly how to set
it up.


Exceptions to identified layers
-------------------------------

Often it is not required to be able to query every layer. Some layers are only present as
basemap and their attributes are not of interest.

You can manage this layerlist in QGIS desktop in :menuselection:`Project --> Project Properties --> Identify Layers`
and uncheck the base layers.


GPS
===

A short press on the GPS button will turn on the GPS and center to the current location
once positioning information is available.

A long press on the GPS button will show the positioning menu.

Inside the positioning menu you can turn on the positioning display which will show the
current coordinates which are reprojected into the project CRS along with precision information.

.. note::
    If you see WGS 84 lat/lon information instead of information in your project CRS,
    you probably have no signal yet.
    

Using external GNSS-Reciever
----------------------------

It is possible to provide a mock location from a separate android app to QField.
There are several options for this, one of them is `Android NTRIP Client 
<http://lefebure.com/software/android-ntripclient/>`_.

To use this you have to `enable mock locations on your Android device 
<https://www.youtube.com/watch?v=v1eRHmMiRJQ>`_.


Digitize
========

To start digitizing new features `Switch modes`_ to Digitize. The software will switch from
Browse mode to Digitize mode, and a black crosshair will appear at the center of the map
window. A new button will also appear below the blue GPS button. This button switches the
digitize crosshair between being locked to the current GPS fix location or allowing free
placement.

To digitize features in a layer, first select the desired layer from the layers list
in the left hand panel. QField will add appropriate editing buttons to the bottom right of the
map window based on the layer type.

FIXME add a current image?

FIXME Pretty sure this is wrong: "A new combobox will appear next to the menu button which lists the layers
available for digitizing."


Points
------

To create a new point feature at a location on the map, navigate the crosshair in the center
of the screen to the desired location by dragging the map window, and click the pencil at the
lower right of the screen to confirm the creation of a new point feature. To create a new
point feature at the current GPS fix location instead, touch the black button below the blue
GPS button to lock the crosshair to the current location, and then click the pencil icon.


Lines and polygons
------------------

Creating new line and polygon features is similar to creating new point features. Either
navigate the crosshair in the center of the screen to the desired start of the line or polygon,
or touch the black button to use the current GPS fix location. Touch the pencil icon to place
the first point on the line or polygon boundary. Continue adding points to the line or boundary
by moving the map window or the location of the GPS receiver and touching the plus icon to add
additional points. When finished digitizing, touch the disk icon to save the captured line or
polygon feature.


Attribute form
--------------

After digitizing a geometry, QField will then display the the layer attributes form
(unless this is suppressed during project setup in QGIS) and the user will be asked to
enter the attributes for the new feature. Enter appropriate information into the layer
attributes form, and touch the disk icon to save the captured feature and attribute data.

The form which appears allows entering attribute values for the new feature. The checkboxes
at the right of every attribute allow for remembering each attribute individually. If checked,
these values will be used by default for the next feature created.


Delete Features
===============

Deleting features is only possible in digitize mode. To delete a feature, identify it by
touching the feature on the map window, then touch the trash icon next to the feature in the
sidebar.


Edit Features
=============

CHECKME: Editing feature locations or boundaries is not currently possible, thougha ttribute
data can be edited after feature creation. To edit feature attributes, identify the
feature by touching it on the map window, then touch the feature on the sidebar. This will
display the detailed attributes window. Touch the pencil icon to begin editing attributes. 
When finished, touch the disk icon to save.