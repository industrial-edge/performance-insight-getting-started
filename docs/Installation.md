# Configuration

- [Configure PLC Connection](#configure-plc-connection)
  - [Configure Databus](#configure-databus)
  - [Configure OPC UA Connector](#configure-OPC-UA-connector)
- [Configure IIH Essentials](#configure-IIH-Essentials)
  - [Configure the connector](#configure-the-connector)
  - [Configure an asset with variables](#configure-an-asset-with-variables)
- [Configure Performance Insight](#configure-performance-insight)
 	- [Configure KPIs](#configure-KPIs)
    - [Configure a dashboard](#configure-a-dashboard)
    - [Configure widgets](#configure-widgets)
    
# Configure PLC Connection

To read data from the PLC and provide the data, we will use OPC UA Connector to establish connection with the PLC .
The OPC UA Connector sends the data to the Databus, where the IIH Essentials app can collect what is needed. The Performance Insight app dependd on a configured IIH Essentials structure.
In order to build this infrastructure, these apps must be installed and configured:

- Databus
- OPC UA Connector
- IIH Essentials
- Performance Insight

## Configure Databus

In your IEM open the Databus and launch the configurator.

Add a user with this topic:
`"ie/#"`

<kbd><img src="/docs/graphics/DatabusAdduser.PNG" width="600"></kbd>

<kbd><img src="/docs/graphics/Databusconfiguration.PNG" width="800"></kbd>

Deploy the configuration.

## Configure OPC UA Connector

There are two methods to configure the OPC UA Connector one in the IEM and the other one directly on the Industrial Edge Device.
Both methodes use the Common Configurator.

First open the Common Configurator and add a data source:

<kbd><img src="/docs/graphics/Addsource.PNG" width="700"></kbd>

Add needed tags:

`GDB.process.numberproduced, GDB.numberFaulty, DB_3_Simulation.statTankLevel, GDB.signals.tankSignals.actTemperature`

<kbd><img src="/docs/graphics/addopcuatagspi.PNG"></kbd>

Edit the settings:

<kbd><img src="/docs/graphics/OPCUASETTINGS.PNG" width="600"></kbd>

> Hint: Username and password should be the same for all system apps, e.g. "edge" / "edge".

Deploy and start the project.

# Configure IIH Essentials

In your IED Web UI open the app IIH Essentials.

## Configure the connector

On the left bar click the icon "Settings" and set the Databus settings: username and password (again "edge"/"edge").

<kbd><img src="/docs/graphics/IIH_Essential_Databus.PNG" width="700"></kbd>

On the left bar click the icon "Connectors" and choose the OPC UA Connector.

In the settings for the connector click the edit icon on the right to open the connector configuration.

<kbd><img src="/docs/graphics/IIHessentialsPIOPCUA.PNG" width="800"></kbd>

## Configure an asset with variables

On the left bar click the icon "Manage data". For the asset "edge" you can add child assets as needed.

Choose "Add attribute" right and set the "Source Type" to "Connecter", afterwards it is possible to insert the required tags.

The required tank application variables are: tank level, tank temperature, produced bottles and faulty bottles.

<kbd><img src="/docs/graphics/iihessentialsPIvariables.PNG" width="800"></kbd>

# Configure Performance Insight

In your IED Web UI open the app Performance Insight.

<kbd><img src="/docs/graphics/Logo.PNG" width="150"></kbd>

## Configure KPIs

Within Performance Insight you have the possibility to define and calculate Key Performance Indicators (KPIs). Those are based on user-defined formulas which are mapped to existing variables.

In order to calculate the production quality a KPI instance needs to be created.

Go to the plant tab and access the parameter view on the right hand side.

<kbd><img src="/docs/graphics/KPI_instance.png"></kbd>

Here you can manage the existing variables and KPI instances or create new ones (Note: this isn't the only way to create KPI instances, they can be also created when configuring a widget).

<kbd><img src="/docs/graphics/KPI instance.PNG" width="1000"></kbd>

## Configure a dashboard

On the my plant panel the dashboard overview will show the option to add a new dashboard (operating at the highest hirerchical level configured in IIH Essentials).

<kbd><img src="/docs/graphics/add_dashboard.png"></kbd>

Insert a dashboard name and select the time period that should be display per default for all signals.

<kbd><img src="/docs/graphics/create_dashboard.png"></kbd>

## Configure widgets

When configuring a widget, Performance Insight offers several types.

**Example 1**

Here we create a Gauge widget for the actual production quality (with its respective warning and alarming levels).

<kbd><img src="/docs/graphics/widget-gauge.png" width="600"></kbd>

For the Gauge widget you need to select one parameter. In this case select 'New KPI instance' to create an instance directly.

<kbd><img src="/docs/graphics/create_new_KPI.png" width="600"></kbd>

Configure the KPI instance accordingly and create it.

<kbd><img src="/docs/graphics/KPI_parameters.png" width="600"></kbd>

Now the KPI instance can be used within the widget. Change the aggregation type of this parameter to 'Last'.

<kbd><img src="/docs/graphics/gauge_widget.png" width="300"></kbd>

Finally, switch to 'Details' and define the Gauge limits.

Create the widget.

**Example 2**

Several widgets have been configured as single value display (with Min, Avg and Max Values). 

<kbd><img src="/docs/graphics/Tempfaultvalues.PNG" width="600"></kbd>

To create these widgets, the process is the following: 

<kbd><img src="/docs/graphics/faulty_bottles.png" width="600"></kbd>

Select the numberFaulty parameter and click on Edit to change the aggregation to 'Last'.

<kbd><img src="/docs/graphics/parameters_faulty_bottles.png" width="600"></kbd>

Change the details to match those on the image:
  
<kbd><img src="/docs/graphics/details_faulty_bottles.png" width="700"></kbd>

For the graphic widgets, proceed as following:
- Select the diagram widget and give it a name
- Select the parameter to graph and change the aggregation to 'Last'
- Change the calculation period to 1 minute and name the y axis (include limits if desired)

<kbd><img src="/docs/graphics/details_temperature.png" width="600"></kbd>

**Example 3**

The last used widget on this application example is a Gantt chart.

Therefore, you need to create a dedicated status mapping that can be later used within the Gantt widget configuration. Go to the menu 'Configuration' > 'Status mappings' and create a new mapping.

<kbd><img src="/docs/graphics/process_state.png" width="600"></kbd>

Now you can create the Gantt widget. Go to the menu 'My Plant' and open the dedicated user-defined dashboard to add a new widet.
- Select the Gantt option and give it a name
- Select the parameter (here machine state)
- Select the newly created status mapping

<kbd><img src="/docs/graphics/gantt_details.png" width="600"></kbd>

Create the widget.

<kbd><img src="/docs/graphics/gantt.png" width="700"></kbd>

By clicking on the detailed view icon of the widget, a detailed Gantt diagram will be shown (more visible data).

<kbd><img src="/docs/graphics/detailed_gantt.png"></kbd>
