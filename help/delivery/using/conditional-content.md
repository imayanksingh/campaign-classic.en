---
title: Conditional content
seo-title: Conditional content
description: Conditional content
seo-description: 
page-status-flag: never-activated
uuid: a62d4bef-3795-461f-ab78-2878a688e078
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 909066c1-c423-4cd8-8b17-6235439a55c0
index: y
internal: n
snippet: y
---

# Conditional content{#conditional-content}

By configuring conditional content fields, you can create dynamic personalization based on the recipient's profile for example. Text blocks and/or images are replaced when a particular condition is satisfied.

## Using conditions in an email {#using-conditions-in-an-email}

In the example below, you will learn how to create a message, dynamically personalized on the recipient's gender and interests.

* Display showing "Mr." or "Ms." according to the value of the **Gender** field (M or F) in the data source,
* Personalized assembly of a newsletter or promotional offers according to the interests indicated or detected:

    * Interest 1 -- > Block 1
    * Interest 2 -- > Block 2
    * Interest 3 -- > Block 3
    * Interest 4 -- > Block 4

To create conditional content according to the value of a field, apply the following steps:

1. Click the personalization icon and select **Conditional content > If**.

   ![](assets/s_ncs_user_conditional_content02.png)

   The personalization elements are inserted in the message body. You must now configure them.

1. Next, fill in the parameters of the **if** expression.

   To do this:

    * Select the first element of the expression, ** `<field>`**, (by default, this element is highlighted during insertion of the **if** expression) and click the personalization icon to replace it with the test field.
    
      ![](assets/s_ncs_user_conditional_content03.png)

    * Replace ** `<value>`** with the value of the field for which the condition will be satisfied. This value must be in quotation marks.
    * Specify the content to be inserted when the condition is satisfied. This could consist of text, an image, a form, a hypertext link, etc.
    
      ![](assets/s_ncs_user_conditional_content04.png)

1. Click the **Preview** tab to view the content of the message according to the delivery recipient:

    * Selecting a recipient for which the condition is true:
    
      ![](assets/s_ncs_user_conditional_content05.png)

    * Selecting a recipient for which the condition is not true:
    
      ![](assets/s_ncs_user_conditional_content06.png)

You can add other cases and define different content according to the values of one or more fields. To do this, use **Conditional content > Else** and **Conditional content > Else if**. These expressions are configured in the same way as the **if** expression.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>To respect JavaScript syntax, the **%> <%** characters must be deleted after adding **Else** and **Else if** conditions.

Click **Preview** and select a recipient to view the conditional content.

![](assets/s_ncs_user_conditional_content08.png)

## Creating multilingual email {#creating-multilingual-email}

In the example below, you will learn how to create a multilingual email. Content will display in one language or the other depending on the recipient's prefered language.

1. Create an email and select the target population. In this example, the condition to display one version or the other will be based on the **Language** value of the recipient's profile. In this example, these values are set to **EN**, **FR**, **ES**.
1. In the email HTML content, click the **Source** tab and paste the following code:

   ```
   
   <% if (language == "EN" ) { %> 
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %> 
   <% if (language == "FR" ) { %> 
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %> 
    <% if (language == "ES" ) { %> 
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %> 
   ```

1. Test email content in the **Preview** tab by selecting recipients with different preferred languages.

   >[!NOTE]
   >
   >As no alternative version has been defined in the email content, make sure to filter target population before sending the email.
