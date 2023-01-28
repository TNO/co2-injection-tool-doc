Drawing the network
----------------------------------------------

Network Component
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A valid network consist of at least:

* 1 compressor
* 1 pipe
* 1 hub
* 1 well
* 1 reservoir

There are two types of geometry: a line and a marker.
Compressor, Valve and Reservoir is modelled as a marker; Pipe, Well, and Hub is modelled as a line

Navigator
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: images/networknavigator.png
    :width: 500

* 1. List of components
* 2. Drawing/insert component (line, marker or polygon)
* 3. Edit or Remove component
* 4. Layer selection
* 5. Zoom in/out
* 6. Network validator

Add the component
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Compressor
"""""""""""""""""""""""""
1. Select component from drop down list, for example compressor
2. Click add marker symbol
3. Place the compressor in the desired location

.. image:: images/addcompressor.png
    :width: 500

Pipe
"""""""""""""""""""""""""
1. Select Pipe from drop down list
2. Click add line symbol
3. Start place pipe from compressor
4. End the pipe by clocking the white square end point

.. image:: images/addpipe.png
    :width: 500

Hub
"""""""""""""""""""""""""
1. Select Hub from drop down list
2. Click add line symbol
3. Start place hub from pipe
4. End the hub by clicking the white square end point

.. image:: images/addhub.png
    :width: 500

Well
"""""""""""""""""""""""""
1. Select Well from drop down list
2. Click add line symbol
3. Start place well from hub (since the well is vertical, this is a diagram only)
4. End the well by clicking the white square end point

.. image:: images/addwell.png
    :width: 500

Reservoir
"""""""""""""""""""""""""
1. Select Reservoir from drop down list
2. Click add marker symbol
3. Place the reservoir at the end of the well

.. image:: images/addreservoir.png
    :width: 500

Connect the components
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The components that are placed in the network needs to be connected to each other.
Below you can see how to connect each component.

Compressor to Pipe
""""""""""""""""""""""""""""""""""""""""""""""""""
1. Select compressor
2. Fill the outport of the compressor with pipe's name: pipe1
3. Don't forget to click Save Parameter

.. image:: images/connectcompressor.png
    :width: 500

Pipe to Hub
""""""""""""""""""""""""""""""""""""""""""""""""""
1. Select pipe. Since we already connect comporessor with pipe, the inport is already filled in.
2. Fill the outport of the pipe with hub's name: hub1
3. Don't forget to click Save Parameter

.. image:: images/connectpipehub.png
    :width: 500

Multiple connection
""""""""""""""""""""""""""""""""""""""""""""""""""

You can continue to connect the rest of components (hub, well, reservoir).
It is also possible to have multiple components connected via a Hub.

for example a hub connected to pipe2,well1,well2 (using *comma*)

.. image:: images/multipleconnectionhub.png
    :width: 500

Checking a network
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
You can check the connection using network validation by clicking Check Network.
It is not only checking the network connection, but also if there is missing parameter (we will discuss in the next session)

It will show a popup window regarding number of errors. The full list of errors in shown the console of your browser

.. image:: images/checknetwork.png
    :width: 500

.. image:: images/errorconsole.png
    :width: 500

Here is how to open error console in the Google Chrome

1. Click 3 dots in the right top corner
2. Select More tools
3. Click Developer tools

.. image:: images/developertool.png
    :width: 500

Set component static parameters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can just easily click the component and fill the static parameter field and press Save Parameter

These are the list of required parameters for each component:

Compressor
""""""""""""""""""""""""""""""""""""""""""""""""""
    * None

Reservoir
""""""""""""""""""""""""""""""""""""""""""""""""""
    * Reservoir initial pressure
    * Reservoir parameter in .xlsx file consist of 4 columns (inflowModel, wellNames, PI, tankV)

    .. image:: images/reservoirparameter.png
        :width: 500

Pipe
""""""""""""""""""""""""""""""""""""""""""""""""""
    * Pipe Maximum Pressure (if there is no pressure limit, put value 0)
    * Pipe Table in .xlsx file consist of 5 columns (Flow rate, Inlet Pressure, Inlet enthalpy, Outlet Pressure, Outlet enthalpy)
    * *Note:* The simulator will not do any extrapolation, please make sure the flow rate and pressure range is covered.

    .. image:: images/pipetable.png
        :width: 500

Well
""""""""""""""""""""""""""""""""""""""""""""""""""
    * Well Table in .xlsx file consist of 5 columns (Flow rate, Inlet Pressure, Inlet enthalpy, Outlet Pressure, Outlet enthalpy)
    * *Note:* The simulator will not do any extrapolation, please make sure the flow rate and pressure range is covered.

    .. image:: images/welltable.png
        :width: 500

Hub
""""""""""""""""""""""""""""""""""""""""""""""""""
    * None
