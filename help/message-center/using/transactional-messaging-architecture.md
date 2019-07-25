---
title: Transactional messaging architecture
seo-title: Transactional messaging architecture
description: Transactional messaging architecture
seo-description: 
page-status-flag: never-activated
uuid: 24677d19-c63c-4483-abd2-fd251e27d24f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
topic-tags: introduction
discoiquuid: 7ed4cdef-adea-44fd-bbf4-ae51d7f92752
index: y
internal: n
snippet: y
---

# Transactional messaging architecture{#transactional-messaging-architecture}

## About execution and control instances {#about-execution-and-control-instances}

In Adobe Campaign, transactional messaging capabilities (also known as Message Center) were designed to support scalability and provide a 24/7 service. It is made up of several instances:

* a control instance, which the message templates are created in,
* one or more execution instances which receive events and deliver messages.

To use these capabilities, Adobe Campaign users log on to the control instance to create transactional message templates, generate the message preview using a seed list, display reports and monitor execution instances.

Execution instances receive events, link them to transactional message templates, and send a personalized message to each recipient.

![](assets/messagecenter_diagram.png)

## Supporting several control instances {#supporting-several-control-instances}

It is possible to share an execution cluster among several control instances. For example, if you manage several specialized stores, you can configure one control instance per brand and link them all to the same execution cluster.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>For more on the necessary configuration, refer to [Using several control instances](../../message-center/using/transactional-messaging-architecture.md#using-several-control-instances).

## Installing instances {#installing-instances}

There are several precautions to take when installing the Transactional message packages. Adobe recommends you to work in a test environment before putting into production. You also need to have a compatible Adobe Campaign license. For more information, please contact your Adobe account executive.

>[!CAUTION]
>
>The control instance and the execution instance(s) must be installed on different machines. They cannot share the same Campaign instance.

If you need to use several channels, you must install and configure related packages before installing Transactional message packages. Refer to [Adding a delivery channel](../../message-center/using/transactional-messaging-architecture.md#adding-a-delivery-channel).

* To install the control instance on your machine, select the **Transactional message control** module.

  ![](assets/messagecenter_install_controlinstance_001.png)

* To install the execution instance on your machine, select the **Transactional message execution** module.

  ![](assets/messagecenter_install_executioninstance_001.png)

## Adding a delivery channel {#adding-a-delivery-channel}

Adding a delivery channel (mobile channel, Mobile App channel, etc.) must be performed before installing the Transactional message package. If you have started a transactional messaging project on the email channel, then decide during the project to add a new channel, you must follow these steps:

1. Install the channel you need, for example the **Mobile channel**, using the package import wizard (**Tools > Advanced > Import package... > Adobe Campaign Package**).
1. Perform a file import (**Tools > Advanced > Import package... > File**), and select the **datakitnms**[Your language]**packagemessageCenter.xml** file.
1. In the **XML content of the data to import**, keep only the delivery template that corresponds to the added channel. For example, if you have added the **Mobile channel**, keep only the **entities** element that corresponds to the **Mobile transactional message** (smsTriggerMessage). If you have added the **Mobile App Channel**, keep only the **iOS transactional message** (iosTriggerMessage) and the **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!CAUTION]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).

## Transactional messaging and push notifications {#transactional-messaging-and-push-notifications}

When combined with Mobile App channel module, transactional messaging enables you to push transactional messages through notifications on mobile devices.

>[!NOTE]
>
>The Mobile App channel is detailed in [this section](../../delivery/using/about-mobile-app-channel.md).

To use transactional message modules with Mobile App Channel, you need to apply the following configurations:

1. Install the **Mobile App Channel** package onto the control and execution instances.
1. Replicate the **Mobile application** type Adobe Campaign service as well as the mobile applications that it contains on the execution instances.

The event must contain the following elements:

* The mobile device ID (**registrationId** for Android and **deviceToken** for iOS). This ID represents the "address" that the notification will be sent to. 
* The link to the mobile application or integration key (**uuid**) which lets you recover connection information specific to the application.
* The channel to which the notification will be sent (**wishedChannel**): 41 for iOS and 42 for Android
* All data useful for personalization

Here is an example of an event that contains this information:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>The creation of message templates remains the same.

## Transactional messaging and LINE {#transactional-messaging-and-line}

Combined with LINE Channel, transactional messages allow you to send real time messages on the LINE app installed in consumer mobile devices. This is used to send the Welcome message when a LINE user adds the brand's page.

To use transactional message module with LINE, the following elements are needed for the configuration on your **marketing** instance and your **execution** instance:

* Install the **LINE Connect** package on both instances.
* Install the **Transactional message control** package on your marketing instance, and the **Transactional message execution** package on the execution instance.
* Create a LINE **external account** and **service** on both instances with identical naming for them to be synchronized. For more information on how to create a LINE external account and service, refer to this [page](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

Then, from the **Explorer**, in **Platform** > **External account**, you need to configure different external accounts on both instances:

1. Create an **External database** external account in your **execution** instance with the following configuration:

   ![](assets/line_config_mc.png)

    * **Label** and **Internal name**: name your external account as needed.
    * **Type**: select **External database**.
    * **Enabled** box must be checked.

   From the **Connection** category:

    * **Type**: select your database server e.g. PostgresSQL.
    * **Server**: enter your database server URL.
    * **Account**: enter your database account.

      >[!NOTE]
      >
      >The database user needs to have read rights on the following tables for FDA connection: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

    * **Password**: enter the password for your database account.
    * **Database**: enter the database name of the execution instance.
    * **Target of an HTTP relay to remote database's account** box must be checked.

1. Create an **External Database** account in your **marketing** instance with the following configuration.

   ![](assets/line_config_mc_1.png)

    * **Label** and **Internal name**: name your external account as needed.
    * **Type**: select **External database**.
    * Enabled box must be checked.

   From the **Connection** category:

    * **Type**: select **HTTP relay to remote Database**.
    * **Server**: enter your campaign's server URL of the execution instance.
    * **Account**: enter the account used to access your execution instance.
    * **Password**: enter the password for the account used to access your execution instance.
    * **Data Source**: enter the following syntax **nms:extAccount:ID of your external database account in the execution instance**.

1. Create an **Execution instance** external account in your **marketing** instance using the following configuration to create the data synchronization workflow:

   ![](assets/line_config_mc_2.png)

    * **Label** and **Internal name**: name your external account as needed.
    * **Type**: select **Execution instance**.
    * Enabled box must be checked.

   From the **Connection** category:

    * **URL**: enter your execution instance's URL.
    * **Account**: enter your account used to access your execution instance.
    * **Password**: enter the password for the account used to access your execution instance.

   From the **Account connection method** category:

    * **Method**: select **Federated Data Access (FDA)**.
    * **FDA account**: select your FDA account from the drop-down.
    * Click the **Create the archiving workflow** button.
    * Click the **Create data synchronization workflow** button to create the LINE data sync workflow.

1. You can now start creating transactional messages. For more on this, refer to this [page](../../message-center/using/introduction.md).
