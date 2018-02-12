---

copyright:
  years: 2018
lastupdated: "2018-01-19"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Updating data source information

When you open an existing dashboard asset, the underlying data source may have changed since the dashboard specification was last saved. Possible changes are:
-	New credentials, for example a changed password, for accessing the data source.
-	New columns are added to the data source.

The *dashboardAPI.getSpec()* method returns all definitions of data source that were previously passed in to *dashboardAPI.addSources()*  calls. To allow your embedding app to update these data source module definitions, you must use the *updateModuleDefinitions()* method before you open the saved dashboard specification. This method takes two parameters:
-	Old dashboard specification
-	Data source updater callback function

The callback function is passed in the list of module ids, and is responsible for returning a list of the updated data source definitions. This list of updated data source definitions has the same format as being in the *addSources()* method. In turn, use the *updateModuleDefinitions()* method to return the updated dashboard specification. You can use this updated dashboard specification then in the *openDashboard()* call.

Example flow of how to open a dashboard:

![opendashboardflow](/images/opendashboardflow.svg "Open a dashboard flow")
