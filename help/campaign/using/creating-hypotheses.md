---
title: Creating hypotheses
seo-title: Creating hypotheses
description: Creating hypotheses
seo-description: 
page-status-flag: never-activated
uuid: b3b7fe2b-ab76-42e7-8a35-e47a7c0211f6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 170d88ea-dfcc-47a9-be52-5d1971174041
index: y
internal: n
snippet: y
---

# Creating hypotheses{#creating-hypotheses}

There are various possibilities for creating/linking hypotheses to a campaign offer or delivery:

* Via the **Measurement hypotheses** folder by creating a new hypothesis based on an existing template and linking it to an existing delivery.
* Via the **Edit** > **Measurement** tab in a campaign.
* Via the **Measurement** option of a delivery created from a campaign.

Hypotheses can only be calculated once the marketing campaign has been launched and recipients have received the delivery. If the hypothesis is based on an offer proposition, the latter needs to at least be presented and still be active. Offer and delivery hypotheses are created via the **Measurement hypotheses** folder and are based on a hypothesis template. However, it is possible to reference a hypothesis directly in the delivery or the campaign before the campaign starts. In this case, the hypotheses will be calculated automatically once the marketing campaign is launched, based on execution settings (for more on this, refer to [Hypothesis template execution settings](../../campaign/using/creating-hypotheses.md#hypothesis-template-execution-settings)).

## Creating a hypothesis on the fly on a delivery {#creating-a-hypothesis-on-the-fly-on-a-delivery}

To create a hypothesis on an existing delivery, apply the following process:

>[!NOTE]
>
>This operation is only possible for pending deliveries.

1. In the Adobe Campaign tree, go to **Campaign management > Measurement hypotheses**.
1. Click the **New** button or right-click on the list of hypotheses and select **New** in the drop-down list.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. In the hypothesis window, select a previously created template (refer to [Hypothesis templates](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   The hypothesis context as it was defined in the selected model is displayed in the window.

   >[!NOTE]
   >
   >Settings defined in the template and not visible at this step are also kept in the memory and reassigned to the hypothesis in progress.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Select the delivery for which you want to create a hypothesis.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. You can personalize your hypothesis by editing the **General**, **Transactions** and **Scope** tabs. For more on this, refer to [Creating a hypothesis model](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-model).
1. Start the hypothesis by clicking **Start**.

   A workflow is automatically created to perform the measurement. The name is automatically defined depending on the hypothesis configuration.

   >[!CAUTION]
   >
   >You can access this if you have checked the **Keep execution workflow** box.  
   >This option must be activated for debugging purposes only, in case of error while running the hypothesis. Workflows generated automatically are saved in the **Administration** > **Production** > **Objects created automatically** > **Campaign workflows** folder in the Adobe Campaign explorer.  
   >In addition, workflows generated automatically must not be modified. Any eventual modification would not be taken into account elsewhere for later calculations.  
   >If you have checked this option, delete the workflow after it has executed.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Once calculation is complete, measurement indicators are updated automatically.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. If necessary, change the settings and re-start the hypothesis.

## Referencing a hypothesis in a campaign delivery {#referencing-a-hypothesis-in-a-campaign-delivery}

You can reference a hypothesis in a marketing campaign before it is started. In this case, the hypothesis will be launched automatically once the delivery is sent, based on the execution settings defined in the hypothesis template. To create a hypothesis in a delivery, apply the following process:

1. Depending on your needs, you can create one or more **Delivery** type templates, as described in [Creating a hypothesis model](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-model)
1. Create a marketing campaign and targeting workflows.
1. In the delivery window, click the **Delivery measurement** icon.
1. Select the hypothesis template (the query configured in the model is displayed in the hypothesis window).

   The hypothesis will be calculated automatically once the campaign is finished, based on the dates configured in the model (refer to [Hypothesis template execution settings](../../campaign/using/creating-hypotheses.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Adding a default hypothesis to deliveries for a campaign {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

You can directly reference a hypothesis at campaign level. In this case, the hypothesis will be automatically linked to all the deliveries created in the campaign. To do this:

1. Go to the **Edit** tab of the campaign.
1. In the measurement section, click the **Default hypotheses** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Click **Add** and select a hypothesis template.

   ![](assets/response_hypothesis_instance_creation_011.png)

   A hypothesis based on this template will now be referenced by default in each new delivery for the campaign.

   ![](assets/response_hypothesis_instance_creation_012.png)

The hypothesis results can be viewed in the **General** and **Reactions** tabs of the hypothesis (refer to [Hypothesis tracking](../../campaign/using/hypothesis-tracking.md))

For more information, you can also refer to [Example: creating a hypothesis linked to a delivery](../../campaign/using/creating-hypotheses.md#example--creating-a-hypothesis-linked-to-a-delivery).

## Creating a hypothesis on an offer {#creating-a-hypothesis-on-an-offer}

Creating a hypothesis on an offer proposition is similar to creating an on the fly delivery hypothesis. The hypothesis can be executed as long as the offer is active. The calculation period is based on the offer proposition date. When the hypothesis lets you link a recipient to a purchase, the status of the offer proposition likely to be accepted can be changed automatically (for more on this, refer to [Transactions](../../campaign/using/creating-hypotheses.md#transactions)).

1. Create one or more **Offer** type models as described in [Creating a hypothesis model](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-model).
1. Go to the **Campaign management > Measurement hypotheses** node.
1. Create an **Offers** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   The query created in the model appears in the window.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Choose the offer for which you want to create a hypothesis.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Refine the query if necessary.
1. Click **Start** to run the hypothesis.
1. The hypothesis results can be viewed in its **General** and **Reactions** tabs (refer to [Hypothesis tracking](../../campaign/using/hypothesis-tracking.md)).

   Hypotheses made on an offer are referenced in the **Measurement** tab.

   ![](assets/response_hypothesis_instance_offer_007.png)

   If the **Update offer proposition status** option was enabled in the hypothesis template, the status of the offer proposition is changed automatically, thereby providing feedback on the impact of the campaign (for more on this, refer to [Transactions](../../campaign/using/creating-hypotheses.md#transactions)).

## Example: creating a hypothesis linked to a delivery {#example--creating-a-hypothesis-linked-to-a-delivery}

In this example, we want to create a hypothesis linked to a delivery. This hypothesis will be based on the model created previously (refer to [Example: creating a hypothesis template on a delivery](../../campaign/using/creating-hypotheses.md#example--creating-a-hypothesis-template-on-a-delivery)). We will then refine the query inherited from the model to make a hypothesis on a specific article of the purchase table.

1. Create a campaign and a delivery (For more on this, refer to [Creating a campaign](../../campaign/using/creating-hypotheses.md#creating-a-campaign)).

   In our example, we will use a direct mail type delivery.

1. Configure a seed address: the previously created hypothesis template was configured to take a control group into account in the reaction results.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >For more information, refer to [Defining a control group](../../campaign/using/creating-hypotheses.md#defining-a-control-group).

1. Open the **Direct mail delivery** and click the **Delivery measurement** icon, then click **Add**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Choose the previously created hypothesis template from the drop-down list.

   ![](assets/response_hypothesis_delivery_example_004.png)

   The query created in the model is displayed.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Click **Edit query...** and refine the query by entering the product that the hypothesis will concern.

   ![](assets/response_hypothesis_delivery_example_006.png)

   You can check that the hypothesis is linked to the delivery in the **Edit** > **Measurement** tab of the campaign.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Launch your targeting workflow and run the necessary checks until the campaign is finished (for more on this, refer to [Starting a delivery](../../campaign/using/creating-hypotheses.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. In the Adobe Campaign tree, go to the **Campaign management > Measurement hypotheses** node to check the indicators calculated by the hypothesis.

   ![](assets/response_hypothesis_delivery_example_010.png)
