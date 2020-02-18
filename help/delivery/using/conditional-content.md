---
title: Contenido condicional
seo-title: Contenido condicional
description: Contenido condicional
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Contenido condicional{#conditional-content}

Al configurar los campos de contenido condicional, se puede crear una personalización dinámica basada en el perfil del destinatario, por ejemplo. Los bloques de texto o las imágenes se sustituyen cuando se cumple una condición concreta.

## Uso de condiciones en un correo electrónico {#using-conditions-in-an-email}

En el siguiente ejemplo, puede aprender a crear un mensaje personalizado de forma dinámica según el género y los intereses del destinatario.

* Mostrar &quot;Mr.&quot; o &quot;Ms.&quot; según el valor del **[!UICONTROL Gender]** campo (M o F) en el origen de datos,
* Conjunto personalizado de un boletín u ofertas promocionales según los intereses indicados o detectados:

   * Interés 1 -- > Bloque 1
   * Interés 2 -- > Bloque 2
   * Interés 3 -- > Bloque 3
   * Interés 4 -- > Bloque 4

Para crear contenido condicional según el valor de un campo, aplique los pasos siguientes:

1. Haga clic en el icono de personalización y seleccione **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Los elementos de personalización se insertan en el cuerpo del mensaje. Ahora debe configurarlos.

1. A continuación, rellene los parámetros de la expresión **if**.

   Para ello:

   * Select the first element of the expression, **`<field>`**, (by default, this element is highlighted during insertion of the **if** expression) and click the personalization icon to replace it with the test field.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Replace **`<value>`** with the value of the field for which the condition will be satisfied. Este valor debe estar entre comillas.
   * Especifique el contenido que desea que se inserte cuando se cumpla la condición. Este contenido puede consistir en un texto, una imagen, un formulario, un enlace de hipertexto, etc.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Click the **[!UICONTROL Preview]** tab to view the content of the message according to the delivery recipient:

   * Selección de un destinatario para el cual la condición es verdadera:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Selección de un destinatario para el cual la condición no es verdadera:

      ![](assets/s_ncs_user_conditional_content06.png)

Se pueden añadir otros casos y definir contenido diferente según los valores de uno o varios campos. Para ello, utilice **[!UICONTROL Conditional content > Else]** y **[!UICONTROL Conditional content > Else if]**. Estas expresiones se configuran del mismo modo que la expresión **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Para respetar la sintaxis de JavaScript, los caracteres **%> &lt;%** deben eliminarse después de añadir las condiciones **Else** y **Else if**

Click **[!UICONTROL Preview]** and select a recipient to view the conditional content.

![](assets/s_ncs_user_conditional_content08.png)

## Creación de un correo electrónico multilingüe {#creating-multilingual-email}

En el siguiente ejemplo, puede aprender a crear un correo electrónico multilingüe. El contenido se mostrará en un idioma o en otro según el idioma preferido del destinatario.

1. Cree un correo electrónico y seleccione la población objetivo. En este ejemplo, la condición para mostrar una versión o la otra se basa en el valor **Language** del perfil del destinatario. En este ejemplo, estos valores se establecen en **EN**, **FR** y **ES**.
1. In the email HTML content, click the **[!UICONTROL Source]** tab and paste the following code:

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

1. Test email content in the **[!UICONTROL Preview]** tab by selecting recipients with different preferred languages.

   >[!NOTE]
   >
   >Como no se ha definido ninguna versión alternativa en el contenido de correo electrónico, asegúrese de filtrar la población de destino antes de enviar el correo electrónico.
