---
title: Setup stages
seo-title: Setup stages
description: Setup stages
seo-description: 
page-status-flag: never-activated
uuid: 0b37b513-1d61-4d3e-bf22-49061f56850f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: c12cff9f-02f8-4533-9c36-edbed4e6f1f0
index: y
internal: n
snippet: y
---

# Setup stages{#setup-stages}

The basic principle is the insertion of web tracking tags in certain pages of your website.

There are two types of tags:

* **WEB**: this tag tells you if the page has been visited,
* **TRANSACTION**: operates like a Web tag, but with the possibility of adding information on the business volume generated, for example (transaction amount, number of items purchased, etc.).

Apply the following steps to set up these tags:

1. Identify the pages you wish to track and determine their type (WEB or TRANSACTION).
1. Determine which additional information you wish to collect, and extend the **nms:webTrackingLog** schema with the description of this information. By default, this schema can store the transaction amounts and number of items per transaction.
1. Creating the web tracking tags. There are two ways of doing this:

    * Insert the URLs corresponding to these pages in your Adobe Campaign platform, then generate and extract the associated web-tracking tags (from the **Campaign execution>Resources>Web tracking tags** node of the client console). 
    * Create the web-tracking tags yourself in "on-the-fly creation" mode: the URLs corresponding to these pages will be automatically inserted in your Adobe Campaign platform.

1. Add these tags statically or dynamically in the pages you wish to track.

   >[!NOTE]
   >
   >All WEB-type tags can be added as they are to the pages of your site. TRANSACTION tags must be modified or added dynamically in order to contain the additional information (amount, items, etc.).

**Example**:

```

<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>

```
