# Configuration

- [Configure PLC Connection](#configure-plc-connection)
  - [Configure Databus](#configure-databus)
- [Configure Performance Insight](#configure-performance-insight)
  - [Configure OPC UA Connector](#configure-OPC-UA-connector)
- [Configure IIH Essentials](#configure-IIH-Essentials)
  - [Configure the connector](#configure-the-connector)
  - [Configure an asset with variables](#configure-an-asset-with-variables)
- [Configure Performance Insight](#configure-performance-insight)
    - [Configure a dashboard](#configure-a-dashboard)
    - [Configure widgets](#configure-widgets)
    - [Configure KPIs](#configure-KPIs)
		
# Configure PLC Connection

To read data from the PLC and provide the data, we will use OPC UA Connector to establish connection with the PLC .
The OPC UA Connector sends the data to the Databus, where the Data Service app can collect what is needed. The Performance Insight app is extremely dependent on a properly configured data service app.
In order to build this infrastructure, these apps must be configured properly:

- OPC UA Connector
- Databus
- Data Service
- Performance Insight

 <p align="center"><kbd><img src="graphics/performanceinsight.PNG"/></kbd></p>

## Configure Databus

In your IEM open the Databus and launch the configurator.

Add a user with this topic:
`"ie/#"`

<p align="center"><kbd><img src="graphics/DatabusAdduser.PNG"/></kbd></p>

<p align="center"><kbd><img src="graphics/Databusconfiguration.PNG" /></kbd></p>

Deploy the configuration.

## Configure OPC UA Connector

In your IEM open the OPC UA Connector and launch the configurator.

Add a data source:

<p align="center"><kbd><img src="graphics/Addsource.PNG" /></kbd></p>

Add needed tags:

<p align="center"><kbd><img src="graphics/OPCUA_ADDTAGS.PNG" /></kbd></p>

Edit the settings:

<p align="center"><kbd><img src="graphics/OPCUASETTINGS.PNG" /></kbd></p>

Hint: Username and password should be the same for all system apps, e.g. "edge" / "edge".

Deploy and start the project.

# Configure IIH Essentials

In your IED Web UI open the app IIH Essentials.

Hint: If an error screen appears saying "...unauthorized...", please restart the IIH Essentials app, wait a moment and try again to open it.

## Configure the connector

On the left bar click the icon "Connectors" and choose the OPC UA Connector (MQTT).

In the settings for the connector click the edit icon on the right to open the connector configuration.

<p align="center"><kbd><img src="graphics/opcuaconnector.PNG" /></kbd></p>

Add the missing entries for name (OPC UA Connector) username and password (again "edge"/"edge") and use databus settings should be deactivated and save it.

<p align="center"><kbd><img src="graphics/opcuaadapterdetails.PNG" /></kbd></p>

Hint: Sometimes the Data Service app must be restarted, to take over the connector changes.

## Configure an asset with variables

On the left bar click the icon "Assets & Connectivity". For the "edge" asset you can add child assets as needed.

Choose "Add variable" or "Multiple variables" on the right side to add tags.

The required tank application variables are: tank level, tank temperature, produced bottles and faulty bottles.

<p align="center"><kbd><img src="graphics/assestsandconnect.png"/></kbd></p>

<p align="center"><kbd><img src="graphics/Addvariables.PNG" /></kbd></p>

# Configure Performance Insight

In your IED Web UI open the app Performance Insight.

<p align="center"><kbd><img src="graphics/Logo.PNG" /></kbd></p>

Hint: When opening the application for the first time a lincese message might pop up (no relationship to IE Hub). Just accept the message and start using the application

## Configure a dashboard

On the my plant panel the dashboard overview will show the option to Add a new dashboard (operating at the highest hirerchical level configured in data service)

<p align="center"><kbd><img src="graphics/Assets dashboard.PNG" /></kbd></p>

Insert a dashboard name and select the time period that should be display per default for all signals

<p align="center"><kbd><img src="graphics/Adddashboard.PNG" /></kbd></p>

## Configure widgets

When configuring a widget, Performance Insight offers the following types:

<p align="center"><kbd><img src="graphics/widget types.PNG" /></kbd></p>

The standard widget configuration has to select some parameters

<p align="center"><kbd><img src="graphics/Parameter of INSIGHT.PNG" /></kbd></p>

The following steps are to define details and display options 

In case of a Gauge Widget an additional dialog will appear with the display boundaries parametrization

<p align="center"><kbd><img src="graphics/Detail Insight.PNG" /></kbd></p>

The first widget is a gauge display for the actual production quality (with its respective warning and alarming levels)

<p align="center"><kbd><img src="graphics/Quality insight.PNG" /></kbd></p>

Several widgets have been configured as single value display (with Min, Avg and Max Values)

<p align="center"><kbd><img src="graphics/Tempfaultvalues.PNG" /></kbd></p>

Another configured widget is a diagram display for the actual tank level

<p align="center"><kbd><img src="graphics/Performance_Insight_Diagram_Widget.png" /></kbd></p>

The last used widget on this application example is a Gantt diagram. The first step is to configure a status mapping

<p align="center"><kbd><img src="graphics/Machinestatus.PNG" /></kbd></p>

Afterwards the Widget has to be added. The Gantt Overview will be displayed on the dashboard

<p align="center"><kbd><img src="graphics/performance-insight-gantt-overview.png" /></kbd></p>

By clicking the detailed view icon, a detailed Gantt diagram will be shown (more visible data)

<p align="center"><kbd><img src="graphics/performance-insight-gantt-detail-view.png" /></kbd></p>

## Configure KPIs

Additional values (also named KPIs) can be calculated out of the existing variables.

In order to calculate the production quality a KPI instance to be created 

<p align="center"><kbd><img src="graphics/KPI instance.PNG" /></kbd></p>

This quality production KPI has been displayed using a gauge widget (frist widget mentioned). KPI has been instanced within a widget

<p align="center"><kbd><img src="graphics/editkpi.PNG" /></kbd></p>
