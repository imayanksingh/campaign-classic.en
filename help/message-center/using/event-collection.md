---
title: Event collection
seo-title: Event collection
description: Event collection
seo-description: 
page-status-flag: never-activated
uuid: fe601f3d-477f-4a93-8a9c-ad907a9ca15e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: ec9b81b7-93a3-4e99-ae79-2b00e66cc8fa
index: y
internal: n
snippet: y
---

# Event collection{#event-collection}

Events generated by the information system can be collected using two modes:

* calls to SOAP methods let you push events in Adobe Campaign: the PushEvent method lets you send one event at a time, the PushEvents method lets you send several at once. Refer to [Event description](../../message-center/using/event-description.md).
* creating a workflow lets you recover events by importing files or via an SQL gateway (with the **Federated Data Access** option).

Once they are collected, events are broken down - by technical workflows - between real time and batch queues of the execution instances, while waiting to be linked to a message template.

![](assets/messagecenter_events_queues_001.png)
