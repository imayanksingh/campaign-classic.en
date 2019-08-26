---
title: Implementation steps
seo-title: Implementation steps
description: Implementation steps
seo-description: 
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
---

# Implementation steps{#implementation-steps}

## Configuring Interaction {#configuring-interaction}

>[!NOTE]
>
>The following steps should be performed by an **Administrator** profile and only in design environments.

1. Creating user profiles. For more on this, refer to [Operator profiles](https://helpx.adobe.com/campaign/standard/interaction/using/operator-profiles.html).
1. Creating an offer environment by targeting dimension. For more on this, refer to [Creating an offer environment](https://helpx.adobe.com/campaign/standard/interaction/using/live-design-environments.html#creating-an-offer-environment).
1. Creating typology rules for each environment. For more on this, refer to [Creating and referencing an offer presentation rule](https://helpx.adobe.com/campaign/standard/interaction/using/managing-offer-presentation.html#creating-and-referencing-an-offer-presentation-rule).
1. Creating offer spaces for each environment and configuring rendering functions. For more on this, refer to [Creating offer spaces](https://helpx.adobe.com/campaign/standard/interaction/using/creating-offer-spaces.html).

   >[!NOTE]
   >
   >If the space is defined by a unitary channel on identified mode, you must specify the advanced parameters for this space.

1. Configuring the offer engine for inbound interactions in order to present and update one or several offers.

   The various integration modes are detailed in [About inbound channels](https://helpx.adobe.com/campaign/standard/interaction/using/about-inbound-channels.html).

   >[!NOTE]
   >
   >When a space is created on the inbound Web channel, a configuration is also necessary on the site on which the offer will be displayed.

## Managing the offer catalog {#managing-the-offer-catalog-}

>[!NOTE]
>
>The following steps should be carried out by an **Offer manager**.

1. Creating offer categories in design environments. For more on this, refer to [Creating offer categories](https://helpx.adobe.com/campaign/standard/interaction/using/creating-offer-categories.html).
1. Creating offers in design environments. For more on this, refer to [Creating an offer](https://helpx.adobe.com/campaign/standard/interaction/using/creating-an-offer.html).
1. Approving and publishing offers on one or several spaces in order to make them available on live environments for the delivery manager. For more on this, refer to [Approving and activating an offer](https://helpx.adobe.com/campaign/standard/interaction/using/approving-and-activating-an-offer.html).

## Using the offer catalog {#using-the-offer-catalog-}

>[!NOTE]
>
>The following steps should be performed by a **Delivery manager** profile. They can only edit offers in live environments.

1. Creating a campaign.
1. Referencing an offer in a campaign or a campaign delivery. For more on this, refer to [About outbound channels](https://helpx.adobe.com/campaign/standard/interaction/using/about-outbound-channels.html).
