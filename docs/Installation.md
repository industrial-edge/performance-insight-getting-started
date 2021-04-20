# Configuration

- [Configure PLC Connection](#configure-plc-connection)
  - [Configure Databus](#configure-databus)
  - [Configure S7 Connector](#configure-s7-connector)
- [Configure Data Service](#configure-data-service)
  - [Configure the adapter](#configure-the-adapter)
  - [Configure an asset with variables](#configure-an-asset-with-variables)
- [Configure Performance Insight](#configure-performance-insight)
    - [Configure a dashboard](#configure-a-dashboard)
    - [Configure widgets](#configure-widgets)
		
# Configure PLC Connection

To read data from the PLC and provide the data, we will use S7 Connector to establish connection with the PLC via OPC UA.
The S7 Connector sends the data to the Databus, where the Data Service app can collect what is needed.
In order to build this infrastructure, these apps must be configured properly:

- Databus
- S7 Connector

## Configure Databus

In your IEM open the Databus and launch the configurator.

Add a user with this topic:
`"ie/#"`

![ie_databus_user](graphics/IE_Databus_User.PNG)

![ie_databus](graphics/IE_Databus.PNG)

Deploy the configuration.

## Configure S7 Connector

In your IEM open the S7 Connector and launch the configurator.

Add a data source:

![S7 Connector Data Source](graphics/S7_Connector_Data_Source.PNG)

Add needed tags:

![s7_connector_config](graphics/S7_Connector_Configuration.PNG)

Edit the settings:

![s7_connector_settings](graphics/S7_Connector_Settings.PNG)

Hint: Username and password should be the same for all system apps, e.g. "edge" / "edge".

Deploy and start the project.

# Configure Data Service

In your IED Web UI open the app Data Service.

Hint: If an error screen appears saying "...unauthorized...", please restart the Data Service app, wait a moment and try again to open it.

## Configure the adapter

On the left bar click the icon "Adapters" and choose the SIMATIC S7 Connector (MQTT).

Click the edit icon on the right to open the adapter configuration.

![data_service_adapter](graphics/Data_Service_Adapter.PNG)

Add the missing entries for username and password (again "edge"/"edge") and save it.

![data_service_adapter_config](graphics/Data_Service_Adapter_Config.PNG)

Hint: Sometimes the Data Service app must be restarted, to take over the adapter changes.

## Configure an asset with variables

On the left bar click the icon "Assets & Connectivity". For the "edge" asset you can add child assets as needed.

Choose "Create first variable" or "Add variable" on the right side to add tags.

The required tank application variables are: tank level, tank temperature, produced bottles and faulty bottles.

![data_service_assets](graphics/Data_Service_Assets.PNG)

![data_service_variable](graphics/Data_Service_Variable.PNG)

# Configure Performance Insight

In your IED Web UI open the app Performance Insight.

![performance_insight_icon](graphics/Performance_Insight_Icon.png)

Hint: When opening the application for the first time a lincese message might pop up (no relationship to IE Hub). Just accept the message and start using the application

## Configure a dashboard

On the main panel the dashboard overview will show the option to create a new dashboard (operating at the highest hirerchical level configured in data service)

![performance_insight_create_dashboard](graphics/Performance_Insight_Create_Dashboard.png)

Insert a dashboard name and select the time frame that should be display per default for all signals

![performance_insight_config_dashboard](graphics/Performance_Insight_Config_Dashboard.png)

## Configure widgets

When configuring a widget, Performance Insight offers the following types:

![performance_insight_widgets](graphics/Performance_Insight_Widgets.png)

The standard widget configuration has to define some details

![performance_insight_define_details](graphics/Performance_Insight_Define_Details.png)

The following steps are: select parameters and define display options 

![performance_insight_select_parameter](graphics/Performance_Insight_Select_Parameter.png)

![performance_insight_general_display](graphics/Performance_Insight_General_Display.png)

![performance_insight_gauge_display](graphics/Performance_Insight_Gauge_Display.png)

The first widget is a gauge display for the actual production quality (with its respective warning and alarming levels)

![performance_insight_gauge_widget](graphics/Performance_Insight_Gauge_Widget.png)

Several widgets have been configured as single value display (with Min, Avg and Max Values)

![performance_insight_value_widget](graphics/Performance_Insight_Value_Widget.png)

The last widget is a diagram display for the actual tank level

![performance_insight_diagram_widget](graphics/Performance_Insight_Diagram_Widget.png)

In order to calculate the production quality a KPI type has been defined

![performance_insight_kpi_calculation](graphics/Performance_Insight_KPI_Calculation.png)

This quality production KPI has been displayed using a gauge widget (frist widget mentioned). KPI has been instanced within a widget

![performance_insight_kpi_gauge_widget](graphics/Performance_Insight_KPI_Gauge_Widget.png)