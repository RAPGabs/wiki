---
id: telemetry
title: Telemetry(Logging)
---

For logging, we have implemented telemetry using Azure AppInsights sdk.Since our core services are deployed on Azure in form of varios Azure functions and UI is hosted from Azure static bucket hence it is quite resourceful to use AppInsights for logging and telemetry purpose.

Application Insights is an extension of Azure Monitor and provides Application Performance Monitoring (also known as “APM”) features. APM tools are useful to monitor applications from development, through test, and into production in the following ways:

- Proactively understand how an application is performing.
- Reactively review application execution data to determine the cause of an incident.
- In addition to collecting Metrics and application Telemetry data, which describe application activities and health, Application Insights can also be used to collect and store application trace logging data.

The log trace is associated with other telemetry to give a detailed view of the activity. Adding trace logging to existing apps only requires providing a destination for the logs; the logging framework rarely needs to be changed.

Now each resource needs to be connected through the AppInsights using resource specific properties like role,app role,insight keys,etc in order to segregate the loggings between resources so that in case we want to see the logs for any specific resource, we can do so simply by selecting that particular role.

Have a look at below AppInsights resources:

>![AppInsights Connection Graph](../../static/img/docs/diep2/appinsightsconnection.png)
Connection Graph for various services.

>![AppInsights Custom Queries](../../static/img/docs/diep2/customqueries.png)
Custom App role based queries.

>![AppInsights Server Logs](../../static/img/docs/diep2/serverlogs.png)
Server Logs

>![AppInsights UI Logs](../../static/img/docs/diep2/UIservicelogs.png)
UI Logs


### References 
1. AppInsights Documentation- [https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview?tabs=net](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview?tabs=net)

2. AppInsights SDK (NodeJs)- [https://learn.microsoft.com/en-us/azure/azure-monitor/app/nodejs](https://learn.microsoft.com/en-us/azure/azure-monitor/app/nodejs)


