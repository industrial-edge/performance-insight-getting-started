# Performance Insight application example

This example shows how to use the Industrial Edge App "Performance Insight" to visualize modeled data
- [Performance Insight](#performance-insight)
  - [Description](#description)
    - [Overview](#overview)
    - [General task](#general-task)
  - [Requirements](#requirements)
    - [Prerequisities](#prerequisities)
    - [Used components](#used-components)
    - [TIA project](#tia-project)
  - [Configuration steps](#configuration-steps)
  - [Usage](#usage)
  - [Documentation](#documentation)
  - [Contribution](#contribution)
  - [Licence and Legal Information](#licence-and-legal-information)
  - [Disclaimer](#disclaimer)



## Description

### Overview

This document describes how to get the data from a PLC into the Performance Insight app. The data flow goes from the OPC UA Connector app, going through the databus app and 
being stored as time-series with the IIH Essentials app. The Performance Insight app is extremely dependent on a properly configured IIH Essentials app.


<p align="center"><kbd><img src="docs/graphics/performanceinsight.PNG" /></kbd></p>


### General task

The example reads data from a PLC via the OPC UA connector.
The data is published on the Databus. The IIH Essentials monitors the bus and collect the shopfloor data.
First an adapter, providing datapoints must be assigned and configured.
Afterwards the data structure can be modeled using assets and aspects. See [data-service-how-to](https://github.com/industrial-edge/data-service-configure-s7-adapter-to-collect-data) for further explanation.
This data is collected, saved for individual time periods and transfered for further processing (using Performance Insight).

## Requirements

###  Prerequisities

- Access to an Industrial Edge Management System (IEM)
- Onboarded Industial Edge Device on IEM
- Installed System Configurators for Databus and OPC UA Connector
- Installed System Apps Databus OPC UA Connector
- Installed IIH Essentials
- Installed Performance Insight
- Edge device is connected to PLC
- TIA portal project loaded on PLC (e.g. for filling application)
- HTML5-capable Internet browser

### Used components

- Industrial Edge Management (IEM) V1.14.10 (OS) V1.5.2-4
  - Databus V2.2.0-3
  - Databus Configurator V2.3.1-4
  - OPC UA Connector V2.0.1-0
  - IIH Essentials V1.10
  - Performance Insight V1.16.1
  - Registry Service V1.9.0-0
  - Common Import Converter V2.1.0-2
- Industrial Edge Device V 1.16.1-1-a
- TIA Portal V18
- S7-PLCSIM Advanced V5.0

### TIA Project

The used TIA Portal project can be found in the [miscellenous repository](https://github.com/industrial-edge/miscellaneous/tree/main/tank%20application) and is also used for several further application examples.

## Configuration steps

You can find the further information about the following steps in the [docs](docs/Installation.md)
- Configure PLC Connection (Databus, OPC UA Connector)
- Configure IIH Essentials
- Configure Performance Insight

## Usage

Once the IIH Essentials app is configured and data is availalbe from a running PLC, process data can be collected.
Performance Insight visualizes this data and gives Iata insights (KPIs, metrics, etc.) 

## Documentation

You can find further documentation and help in the following links
  - [Industrial Edge Hub]( https://iehub.eu1.edge.siemens.cloud/#/documentation)
  - [Industrial Edge Forum]( https://forum.mendix.com/link/space/industrial-edge)
  - [Industrial Edge landing page]( https://new.siemens.com/global/en/products/automation/topic-areas/industrial-edge/simatic-edge.html)
  - [Industrial Edge GitHub page]( https://github.com/industrial-edge)
  - [Industrial Edge documentation page]( https://docs.eu1.edge.siemens.cloud/index.html)
## Contribution
Thank you for your interest in contributing. Anybody is free to report bugs, unclear documentation, and other problems regarding this repository in the Issues section. Additionally everybody is free to propose any changes to this repository using Pull Requests.

If you haven't previously signed the [Siemens Contributor License Agreement](https://cla-assistant.io/industrial-edge/) (CLA), the system will automatically prompt you to do so when you submit your Pull Request. This can be conveniently done through the CLA Assistant's online platform. Once the CLA is signed, your Pull Request will automatically be cleared and made ready for merging if all other test stages succeed.

## Licence and Legal Information

Please read the [Legal information](LICENSE.txt).

## Disclaimer

IMPORTANT - PLEASE READ CAREFULLY:

This documentation describes how you can download and set up containers which consist of or contain third-party software. By following this documentation you agree that using such third-party software is done at your own discretion and risk. No advice or information, whether oral or written, obtained by you from us or from this documentation shall create any warranty for the third-party software. Additionally, by following these descriptions or using the contents of this documentation, you agree that you are responsible for complying with all third party licenses applicable to such third-party software. All product names, logos, and brands are property of their respective owners. All third-party company, product and service names used in this documentation are for identification purposes only. Use of these names, logos, and brands does not imply endorsement.
