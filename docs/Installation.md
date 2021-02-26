# Configuration

- [Configuration](#configuration)
  - [Configure PLC Connection](#configure-plc-connection)
    - [Configure Databus](#configure-databus)
    - [Configure S7 Connector](#configure-s7-connector)
  - [Configure Data Service](#configure-data-service)
    - [Configure the adapter](#configure-the-adapter)
    - [Configure an asset with variables](#configure-an-asset-with-variables)
    - [Configure an aspect](#configure-an-aspect)
- [Configure Performance Insight](#configure-performance-insight)
    - [Configure a dashboard](#configure-a-dashboard)
    - [Configure widgets](#configure-widgets)
		
## Configure PLC Connection

To read data from the PLC and provide the data, we will use S7 Connector to establish connection with the PLC via OPC UA.
The S7 Connector sends the data to the Databus, where the Data Service app can collect what is needed.
In order to build this infrastructure, these apps must be configured properly:

- Databus
- S7 Connector

### Configure Databus

In your IEM open the Databus and launch the configurator.

Add a user with this topic:
`"ie/#"`

![ie_databus_user](graphics/IE_Databus_User.PNG)

![ie_databus](graphics/IE_Databus.PNG)

Deploy the configuration.

### Configure S7 Connector

In your IEM open the S7 Connector and launch the configurator.

Add a data source:

![S7 Connector Data Source](graphics/S7_Connector_Data_Source.PNG)

Add needed tags:

![s7_connector_config](graphics/S7_Connector_Configuration.PNG)

Edit the settings:

![s7_connector_settings](graphics/S7_Connector_Settings.PNG)

Hint: Username and password should be the same for all system apps, e.g. "edge" / "edge".

Deploy and start the project.

## Configure Data Service

In your IED Web UI open the app Data Service.

Hint: If an error screen appears saying "...unauthorized...", please restart the Data Service app, wait a moment and try again to open it.

### Configure the adapter

On the left bar click the icon "Adapters" and choose the SIMATIC S7 Connector (MQTT).

Click the edit icon on the right to open the adapter configuration.

![data_service_adapter](graphics/Data_Service_Adapter.PNG)

Add the missing entries for username and password (again "edge"/"edge") and save it.

![data_service_adapter_config](graphics/Data_Service_Adapter_Config.PNG)

Hint: Sometimes the Data Service app must be restarted, to take over the adapter changes.

### Configure an asset with variables

On the left bar click the icon "Assets & Connectivity". For the "edge" asset you can add child assets as needed.

Choose "Create first variable" or "Add variable" on the right side to add tags.

![data_service_assets](graphics/Data_Service_Assets.PNG)

![data_service_variable](graphics/Data_Service_Variable.PNG)

To change the storage time period, klick on the link below the asset:

![data_service_retention](graphics/Data_Service_Retention.PNG)

### Configure an aspect

Choose the register "Aspects" to create a new aspect by clicking "Create first aspect" or "Add aspect".

![data_service_aspect](graphics/Data_Service_Aspect.PNG)

Hint: An aspect can include several variables, but each variable can only be assigned to one aspect.

![data_service_aspects](graphics/Data_Service_Aspects.PNG)

## Configure Performance Insight

In your IED Web UI open the app Performance Insight.

![performance_insight_icon](graphics/Performance_Insight_Icon.png)

Hint: When opening the application for the first time a lincese message might pop up. Just accept the message and start using the application

### Configure a dashboard

On the main panel the dashboard overview will show the option to create a new dashboard (operating at the highest hirerchical level configured in data service)

![performance_insight_create_dashboard](graphics/Performance_Insight_Create_Dashboard.png)

Insert a dashboard name and select the time frame that should be display per default for all signals

![performance_insight_config_dashboard](graphics/Performance_Insight_Config_Dashboard.png)

### Configure widgets

The first widget to be added is a single value display (with Min, Avg and Max Values) for the produced bottles (with good and bad quality)

![performance_insight_value_widget](graphics/Performance_Insight_Value_Widget.png)

The second widget is a gauge display for the actual tank level

![performance_insight_gauge_widget](graphics/Performance_Insight_Gauge_Widget.png)

The third widget is a diagram display for the actual tank temperature

![performance_insight_diagram_widget](graphics/Performance_Insight_Diagram_Widget.png)

The last widget is a calculated KPI for the production quality

![performance_insight_kpi_calculation](graphics/Performance_Insight_KPI_Calculation.png)

This quality production KPI is shwon using a gauge widget with warning and alarm thresholds

![performance_insight_kpi_gauge_widget](graphics/Performance_Insight_KPI_Gauge_Widget.png)