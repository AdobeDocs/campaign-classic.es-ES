---
title: Bloques personalizados
seo-title: Bloques personalizados
description: Bloques personalizados
seo-description: null
page-status-flag: never-activated
uuid: f9867f8d-f6ce-4a5f-b6b4-fd8056d28576
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: e68d1435-70e6-479e-a347-9ff9f9f11b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa9e4ddc716809b96e259acd1137a0c24ef68fee
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 72%

---


# Bloques personalizados{#personalization-blocks}

Los bloques personalizados son dinámicos, personalizados y contienen un procesamiento específico que puede insertar en las entregas. Por ejemplo, puede añadir un logotipo, un mensaje de saludo o un vínculo a una página espejo. Consulte [Inserción de bloques de personalización](#inserting-personalization-blocks).

>[!NOTE]
>
>Personalization blocks are also available from the **[!UICONTROL Digital Content Editor (DCE)]** . Para obtener más información, consulte [esta página](../../web/using/editing-content.md#inserting-a-personalization-block).

Personalization blocks are accessed via the **[!UICONTROL Resources > Campaign Management > Personalization blocks]** node of the Adobe Campaign explorer. Hay varios bloques disponibles de forma predeterminada (consulte [Bloques de personalización predeterminados](#out-of-the-box-personalization-blocks)).

Tiene la posibilidad de definir nuevos bloques que le permitan optimizar la personalización de las entregas. Para obtener más información sobre esto, consulte [Definición de bloques de personalización personalizados](#defining-custom-personalization-blocks).

## Inserción de bloques personalizados {#inserting-personalization-blocks}

Para insertar un bloque personalizado en un mensaje, siga los pasos a continuación:

1. En el editor de contenido del asistente de envío, haga clic en el icono de campo personalizado y seleccione el menú **[!UICONTROL Include]**.
1. Select a personalization block from the list (the list displays the 10 last used blocks), or click the **[!UICONTROL Other...]** menu to access the full list.

   ![](assets/s_ncs_user_personalized_block01.png)

1. The **[!UICONTROL Other...]** menu gives access to all the out-of-the-box and custom personalization blocks (see [Out-of-the-box personalization blocks](#out-of-the-box-personalization-blocks) and [Defining custom personalization blocks](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. A continuación, el bloque personalizado se inserta como una secuencia de comandos. Se adapta automáticamente al perfil de destinatario cuando se genera la personalización.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Haga clic en la pestaña **[!UICONTROL Preview]** y seleccione un destinatario para ver la personalización.

   ![](assets/s_ncs_user_personalized_block04.png)

Se puede incluir el código fuente de un bloque personalizado en el contenido de envío. Para ello, seleccione **[!UICONTROL Include the HTML source code of the block]** al seleccionarlo.

![](assets/s_ncs_user_personalized_block05.png)

El código fuente HTML se inserta en el contenido de envío. Por ejemplo, el bloque personalizado **[!UICONTROL Greetings]** se muestra de la siguiente manera:

![](assets/s_ncs_user_personalized_block06.png)

## Ejemplo de bloques personalizados {#personalization-blocks-example}

En este ejemplo, se crea un correo electrónico en el que se utilizan bloques personalizados para permitir que el destinatario vea la página espejo, compartir el boletín informativo en redes sociales y cancelar la suscripción a futuros envíos.

Para ello, es necesario insertar los siguientes bloques personalizados:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Para obtener más información sobre la generación de páginas de reflejo, consulte [Generación de la página de reflejo](../../delivery/using/sending-messages.md#generating-the-mirror-page).

1. Cree una nueva entrega o abra una entrega de tipo correo electrónico ya existente.
1. En el asistente de envío, haga clic en **[!UICONTROL Subject]** para editar el asunto del mensaje y escriba un asunto.
1. Inserte los bloques personalizados en el cuerpo del mensaje. Para ello, haga clic en el contenido del mensaje, haga clic en el icono de campo personalizado y seleccione el menú **[!UICONTROL Include]**.
1. Seleccione el primer bloque que desee insertar. Reinicie el procedimiento para incluir los otros dos bloques.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Haga clic en la pestaña **[!UICONTROL Preview]** para ver el resultado personalizado. Se debe seleccionar un destinatario para mostrar el mensaje de dicho destinatario.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Confirme que el contenido del bloque se muestra correctamente.

## Bloques personalizados preestablecidos {#out-of-the-box-personalization-blocks}

De forma predeterminada, hay disponibles una lista de bloques personalizados que ayudan a personalizar el contenido del mensaje.

>[!NOTE]
>
>La lista de bloques personalizados depende de los módulos y las opciones que se hayan instalado en la instancia.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]**: inserta los saludos con el nombre del destinatario. Ejemplo: &quot;Hola John Doe&quot;.
* **[!UICONTROL Insert logo]**: inserta un logotipo preestablecido que se haya definido al configurar la instancia.
* **[!UICONTROL Powered by Adobe Campaign]** :: inserta el logotipo &quot;Powered by Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** :: inserta la dirección URL de la página espejo, lo que permite a los diseñadores de Envíos comprobar el vínculo.

   >[!NOTE]
   >
   >Para obtener más información sobre la generación de páginas de reflejo, consulte [Generación de la página de reflejo](../../delivery/using/sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]**: inserta un vínculo a la página espejo: &quot;Si no puede ver este mensaje correctamente, haga clic aquí&quot;.
* **[!UICONTROL Unsubscription link]** :: inserta un vínculo que permite cancelar la suscripción de todos los envíos (lista de bloques).
* **[!UICONTROL Formatting function for proper nouns]** :: genera la función **[!UICONTROL toSmartCase]** Javascript, que cambia la primera letra de cada palabra a mayúscula. Este bloque debe insertarse en el código fuente de la entrega, entre las etiquetas **`<script>...</script>`**.

   En el ejemplo siguiente, se utiliza la función para sustituir el elemento de “Encabezado” por “Nuevo encabezado” con letras mayúsculas en cada palabra:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** :: inserta una URL de suscripción (consulte [Acerca de servicios y suscripciones](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** :: inserta un vínculo de suscripción. El vínculo se ha definido al configurar la instancia.
* **[!UICONTROL Registration link (with referrer)]** :: inserta un vínculo de suscripción que permite identificar el visitante y el envío. El vínculo se ha definido al configurar la instancia.

   >[!NOTE]
   >
   >Este bloque se puede utilizar en envíos dirigidos solamente a visitantes.

* **[!UICONTROL Registration confirmation]** :: inserta un vínculo que permite confirmar la suscripción.
* **[!UICONTROL Social network sharing links]**:  : inserta botones que permiten al destinatario compartir un vínculo al contenido de la página espejo con el cliente de correo electrónico, Facebook, Twitter, Google+ y LinkedIn (consulte [Marketing viral: enviar a un amigo](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** y **[!UICONTROL Notification style]** : genere código que dé formato a un correo electrónico con estilos HTML predefinidos. These blocks must be inserted in the source code of the delivery, in the **[!UICONTROL ...]** section, into **`<style>...</style>`** tags.
* **[!UICONTROL Offer acceptance URL in unitary mode]** :: inserta una URL que permite establecer una oferta de interacción en **[!UICONTROL Accepted]** (consulte [esta sección](../../interaction/using/offer-analysis-report.md)).

## Definición de bloques personalizados propios {#defining-custom-personalization-blocks}

You can define new personalization fields to be inserted from the personalized field icon via the **[!UICONTROL Include...]** menu. Estos campos se definen en bloques personalizados.

Para crear un bloque personalizado, vaya al explorador y aplique los pasos siguientes:

1. Haga clic en el **[!UICONTROL Resources > Campaign Management > Personalization blocks]** nodo.
1. Haga clic con el botón derecho en la lista de bloques y seleccione **[!UICONTROL New]** .
1. Rellene la configuración del bloque personalizado:

   ![](assets/s_ncs_user_personalized_block.png)

   * Introduzca la etiqueta del bloque. Esta etiqueta se muestra en la ventana de inserción del campo personalizado.
   * Select **[!UICONTROL Visible in the customization menus]** to make this block accessible from the personalization field insertion icon.
   * If necessary, select **[!UICONTROL The content of the personalization block depends upon the format]** to define two separate blocks for emails in HTML format and those in text format.

      A continuación, se muestran dos pestañas en la sección inferior de este editor (contenido HTML y contenido de texto) para definir los contenidos correspondientes.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Introduzca el contenido (en HTML, texto, JavaScript, etc.) de los bloques de personalización y haga clic en **[!UICONTROL Save]** .
