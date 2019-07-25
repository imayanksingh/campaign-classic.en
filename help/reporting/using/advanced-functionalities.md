---
title: Advanced functionalities
seo-title: Advanced functionalities
description: Advanced functionalities
seo-description: 
page-status-flag: never-activated
uuid: 7010e2c4-2f7b-4898-876f-32ffe23ace90
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
audience: reporting
discoiquuid: 0677d144-0716-4196-88fc-cd278130dc3d
index: y
internal: n
snippet: y
---

# Advanced functionalities{#advanced-functionalities}

## Adding a script {#adding-a-script}

### Script activity {#script-activity}

This activity enables you to process data and easily create complex queries that don't enable SQL language.

Simply enter your query in the script window.

The **Texts** tab enables you to define text strings. They may then be used with the following syntax: **$(Identifier)**. For more on using texts, refer to [Adding a header and a footer](../../reporting/using/advanced-functionalities.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We do NOT recommend using JavaScript code to create aggregates.

To create a history of your report, add the following line to your JavaScript query in order to save your archived data:

```
if( ctx.@_historyId.toString().length == 0 )
```

Otherwise current data will be displayed.

### External script {#external-script}

It's possible to use an external script that will be executed on the server and/or client side. To do this:

1. Edit the report properties and click the **Scripts**.
1. Click **Add** and select the script to be referenced.
1. Then select the execution mode.

   If you add several scripts, use the arrows of the toolbar to define their execution sequence.

   ![](assets/reporting_custom_js.png)

## Calling up another report {#calling-up-another-report}

### Jump activity {#jump-activity}

A jump is like a transition without an arrow: it lets you go from one activity to another or access another report.