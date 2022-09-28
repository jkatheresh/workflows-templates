Search Okta System logs and upload logs into a REST endpoint

Okta Workflows makes it easy to automate identity processes at scale – without writing code. Use if-this-then-that logic, Okta’s pre-built connector library, and the ability to connect to any publicly available API to enable anyone to innovate with Okta. Workflows templates provide flow builders with pre-built, configurable flows for common identity automation use cases. Flogrammers can download and use the templates as-is, or modify them for their organization’s unique needs. In this tutorial, we’ll go through the process of using a template to create a set of flows. For additional information on Okta Workflows, see this page: Okta Workflows

Use Case Overview

Okta administrators sometimes get requested to selective filtering off Okta System logs for "User Behaviours" see this page: Behaviour Detection and feed the data into a SIEM endpoints or custom REST endpoint. 

Okta has got a detailed documentation on exporting Okta log data, see this page: Exporting Okta Log Data

Note: This blog focuses on uploading logs into a custom API REST endpoint (POST) where existing available integrations is not sufficient.

Workflow Structure

The processing logic is as following,

[main] Get Syslogs - This flow computes the date filter and passes a custom log filter query (debugContext.debugData.behaviors co "UNKNOWN") to Okta Search System Logs card to stream log results.

[helper] Post Syslogs - This flow processes the streamed record from main flow (Get Syslogs), where it extracts the required data from Okta System logs to load the records into a table (CustomSyslog) and also posts to a web hook endpoint.

You can download this workflow from this page : 

Pre-Requirements

A Okta tenant

Okta Workflows enabled within the Okta tenant

Webhook/REST endpoint for loading data

References

https://help.okta.com/wf/en-us/Content/Topics/Workflows/connector-reference/okta/actions/searchsystemlogs.htm

https://help.okta.com/oie/en-us/Content/Topics/Reports/syslog-filters.htm
