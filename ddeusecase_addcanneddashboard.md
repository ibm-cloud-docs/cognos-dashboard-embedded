---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-01”

keywords: canned dashboard, application, json

subcollection: cognos-dashboard-embedded
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Adding a canned dashboard to an application
{: #addingcanneddashboard}

You have two options to add dashboards to your application:
1.	You can author dashboard views in advance for use within your application.
2.	You can provide a more free-form dash-boarding tool, to allow your users to do their own exploration of the data in your application.

To create your dashboard specifications during development, use {{site.data.keyword.dynamdashbemb_full}} as follows:
1.	Launch the {{site.data.keyword.dynamdashbemb_short}} test tool, or your own application that uses {{site.data.keyword.dynamdashbemb_short}}.
2.	Create a new dashboard with the *dashboard.createNew()* method.
3.	Add the data sources from your application to the dashboard.
4.	Author the JSON text or dashboard specification with the *dashboardAPI.getSpec()* method.
5.	Save the dashboard specification with its application source code.
6.	At run time, instantiate the dashboard in your app with the *dashboard.openDashboard()* method. Pass the dashboard specification that you created earlier.

By default, the dashboard will be opened in consumption/view mode. The user will be able to explore the dashboard, but not modify it.

If you want to allow your users to edit the dashboard, the use the *dashboardAPI.setMode* method as follows:
```bash
dashboardAPI.MODES.EDIT
```    
{: pre}
Editing allows the dashboard user to access to the authoring tools, and to add, delete, and edit widgets from the dashboard canvas.


