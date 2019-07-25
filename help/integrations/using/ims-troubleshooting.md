---
title: IMS troubleshooting
seo-title: IMS troubleshooting
description: IMS troubleshooting
seo-description: 
page-status-flag: never-activated
uuid: 92f5be81-6121-4397-94ba-a83a5a19aa7f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 6d18b1bf-70ba-4135-9a18-47635e014f59
index: y
internal: n
snippet: y
---

# IMS troubleshooting{#ims-troubleshooting}

The following troubleshooting tips will help **on-premise** customers solve the most common problems happening when using the IMS integration. For **hosted** customers, please contact Adobe.

**External Account**

There should only be **one** external account with the following settings:

* **Internal Name**: Adobe_Marketing_Cloud
* **Type**: Adobe Marketing Cloud

Delete any duplicate external account that have same the same settings.

**Product Context**

If the external account has a **Product Context** field, check that its value is set to: **dma_campaign_classic**

Make sure your product context is the same for Campaign and Experience Cloud.

For example, if the **Product Context** does not appear, the default product context should be **dma_campaign** in both Campaign and Experience Cloud. If the **Product Context** field appears, the default product context should be **dma_campaign_classic** in both Campaign and Experience Cloud.

**IMS Server URL**

In the Campaign **Adobe Marketing Cloud** external account, check that the **IMS Server URL** is either [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) or [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Make sure both stage and production instances point to the same IMS production end point.

**Association Mask**

* Check that the user trying to login is part of an operator group in the Enterprise Dashboard.
* Check that the **Association Mask** is a prefix of the user's operator group name in the Enterprise Dashboard.
* Make sure there are no white spaces and spelling mistakes. 
* Check that the names of the operator groups in Campaign have not been changed and respect the following syntax: .

**Scope**

Scopes defined in the Campaign external account must be a subset of those provisioned by IMS.

**Callback URL**

The **Callback URL** should be whitelisted and start with "https://". Check that the **Callback URL** is linked to the corresponding instance. For example, the production instance should redirect to the production URL.

**Client ID and secret**

The client ID matches between the Campaign external account and the one provisioned by IMS.

Check that the client secret entered is correct.

**Restart the server**

Restart the server if any changes are made to the above settings in the Campaign external account

**Common types of errors and possible solutions**

* User is redirected to adobe.com page:

  There is a problem with the **Callback URL**. Refer to the previous steps to check the **Callback URL** configuration.

* Message "Login does not have any right matching the expression":

  Refer to the previous steps to check the **Association Mask** and operator groups configuration.

* The user is unable to access the Adobe ID login page:

  Refer to the previous steps to check the scope configuration.
