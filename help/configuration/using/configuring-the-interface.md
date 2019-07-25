---
title: Configuring the interface
seo-title: Configuring the interface
description: Configuring the interface
seo-description: 
page-status-flag: never-activated
uuid: 4c38cfe7-e830-4586-b562-40d322eb70e8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: d79ec492-f033-43f9-b752-17662d5fa33e
index: y
internal: n
snippet: y
---

# Configuring the interface{#configuring-the-interface}

To view and dialog with the new recipient table in the Adobe Campaign interface, apply the following steps:

* Create a new form to edit the content of the new recipient table.
* Enter a new type in the folder of the explorer tree.
* Create a new web application to access the custom table via the Adobe Campaign home page.

Adobe Campaign uses a "Nms_DefaultRcpSchema" global variable to dialog with the default recipient database (nms:recipient). This variable therefore needs to be altered.

1. Go to the **Administration>Platform>Options** node of the explorer.
1. Change the value of the **Nms_DefaultRcpSchema** variable with the name of the schema which matches the external recipient table (in this case: cus:individual).
1. Save changes.

## Creating a new form {#creating-a-new-form-}

Creating a new form will enable you to view and edit the data of the external recipient table.

>[!CAUTION]
>
>The name of the form must be identical to the name of the schema which it concerns.

1. Go to the **Administration > Configuration > Input forms** node of the explorer.
1. Create a new **xtk:form** type **form** file.
1. Describe all the monitorings and fields which you need depending on your table template.

   >[!NOTE]
   >
   >To find out more about **form** type files, refer to [this page](../../configuration/using/identifying-a-form.md).

   In our current example, the **form** file must be based on the **cus:individual** schema and therefore have the following layout:

   ```
   
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
       
   ```

1. Save the creation.

## Creating a new type of folder in the navigation hierarchy {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Go to the **Administration>Configuration>Navigation hierarchies** node.
1. Create a new **xtk:navtree** type **navtree** document.
1. Describe all the monitorings and fields which you need depending on your table template.

   >[!NOTE]
   >
   >For more on **navtree** type files, refer to [this page](../../configuration/using/about-navigation-hierarchy.md).

   In the current example, the **navtree** file must be based on the **cus:individual** schema and therefore have the following form:

   ```
   
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
       
   ```

1. Save the creation.
