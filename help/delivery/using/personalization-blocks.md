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
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Bloques personalizados{#personalization-blocks}

Los bloques personalizados son dinámicos, personalizados y contienen un procesamiento específico que puede insertar en los envíos. Por ejemplo, puede añadir un logotipo, un mensaje de saludo o un enlace a una página espejo. Consulte [Inserción de bloques](#inserting-personalization-blocks)de personalización.

>[!NOTE]
>
>Personalization blocks are also available from the **[!UICONTROL Digital Content Editor (DCE)]** . Para obtener más información, consulte [esta página](../../web/using/editing-content.md#inserting-a-personalization-block).

Personalization blocks are accessed via the **[!UICONTROL Resources > Campaign Management > Personalization blocks]** node of the Adobe Campaign explorer. Hay varios bloques disponibles de forma predeterminada (consulte Bloques [](#out-of-the-box-personalization-blocks)de personalización predeterminados).

Tiene la posibilidad de definir nuevos bloques que le permitan optimizar la personalización de los envíos. Para obtener más información sobre esto, consulte [Definición de bloques](#defining-custom-personalization-blocks)de personalización personalizados.

## Inserción de bloques personalizados {#inserting-personalization-blocks}

Para insertar un bloque personalizado en un mensaje, siga los pasos a continuación:

1. In the content editor of the delivery wizard, click the personalized field icon and select the **[!UICONTROL Include]** menu.
1. Select a personalization block from the list (the list displays the 10 last used blocks), or click the **[!UICONTROL Other...]** menu to access the full list.

   ![](assets/s_ncs_user_personalized_block01.png)

1. El **[!UICONTROL Other...]** menú proporciona acceso a todos los bloques de personalización predeterminados y personalizados (consulte Bloques [de personalización](#out-of-the-box-personalization-blocks) listos para usar y [Definición de bloques](#defining-custom-personalization-blocks)de personalización personalizados).

   ![](assets/s_ncs_user_personalized_block02.png)

1. A continuación, el bloque personalizado se inserta como una secuencia de comandos. Se adapta automáticamente al perfil de destinatario cuando se genera la personalización.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Click the **[!UICONTROL Preview]** tab and select a recipient to view the personalization.

   ![](assets/s_ncs_user_personalized_block04.png)

Se puede incluir el código fuente de un bloque personalizado en el contenido de envío. Para ello, seleccione **[!UICONTROL Include the HTML source code of the block]** al seleccionarlo.

![](assets/s_ncs_user_personalized_block05.png)

El código fuente HTML se inserta en el contenido de envío. For example, the **[!UICONTROL Greetings]** personalization bloc displays as below:

![](assets/s_ncs_user_personalized_block06.png)

## Ejemplo de bloques personalizados {#personalization-blocks-example}

En este ejemplo, se crea un correo electrónico en el que se utilizan bloques personalizados para permitir que el destinatario vea la página espejo, compartir el boletín informativo en redes sociales y cancelar la suscripción a futuros envíos.

Para ello, es necesario insertar los siguientes bloques personalizados:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Para obtener más información sobre la generación de páginas de reflejo, consulte [Generación de la página](../../delivery/using/sending-messages.md#generating-the-mirror-page)de reflejo.

1. Cree un nuevo envío o abra un envío de tipo correo electrónico ya existente.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Inserte los bloques personalizados en el cuerpo del mensaje. To do this, click in the message content, click the personalized field icon and select the **[!UICONTROL Include]** menu.
1. Seleccione el primer bloque que desee insertar. Reinicie el procedimiento para incluir los otros dos bloques.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Click the **[!UICONTROL Preview]** tab to view the personalization result. Se debe seleccionar un destinatario para mostrar el mensaje de dicho destinatario.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Confirme que el contenido del bloque se muestra correctamente.

## Bloques personalizados preestablecidos {#out-of-the-box-personalization-blocks}

De forma predeterminada, hay disponibles una lista de bloques personalizados que ayudan a personalizar el contenido del mensaje.

>[!NOTE]
>
>La lista de bloques personalizados depende de los módulos y las opciones que se hayan instalado en la instancia.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** :: inserta saludos con el nombre del destinatario. Ejemplo: &quot;Hola John Doe&quot;.
* **[!UICONTROL Insert logo]** :: inserta un logotipo incorporado que se ha definido al configurar la instancia.
* **[!UICONTROL Powered by Adobe Campaign]** :: inserta el logotipo &quot;Powered by Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** :: inserta la dirección URL de la página reflejada, lo que permite a los diseñadores de envíos comprobar el vínculo.

   >[!NOTE]
   >
   >Para obtener más información sobre la generación de páginas de reflejo, consulte [Generación de la página](../../delivery/using/sending-messages.md#generating-the-mirror-page)de reflejo.

* **[!UICONTROL Link to mirror page]** :: inserta un vínculo a la página reflejada: &quot;Si no puede ver este mensaje correctamente, haga clic aquí&quot;.
* **[!UICONTROL Unsubscription link]** :: inserta un vínculo que permite cancelar la suscripción de todas las entregas (lista negra).
* **[!UICONTROL Formatting function for proper nouns]** :: genera la función **[!UICONTROL toSmartCase]** Javascript, que cambia la primera letra de cada palabra a mayúscula. This block must be inserted in the source code of the delivery, into **`<script>...</script>`** tags.

   En el ejemplo siguiente, la función se utiliza para reemplazar el elemento &quot;My header&quot; por &quot;My new header&quot; con letras en mayúsculas en cada palabra:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** :: inserta una URL de suscripción (consulte [Acerca de los servicios y las suscripciones](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** :: inserta un vínculo de suscripción. que se ha definido al configurar la instancia.
* **[!UICONTROL Registration link (with referrer)]** :: inserta un vínculo de suscripción que permite identificar al visitante y la entrega. El enlace se ha definido al configurar la instancia.

   >[!NOTE]
   >
   >Este bloque se puede utilizar en envíos dirigidos solamente a visitantes.

* **[!UICONTROL Registration confirmation]** :: inserta un vínculo que permite confirmar la suscripción.
* **[!UICONTROL Social network sharing links]** :: inserta botones que permiten al destinatario compartir un vínculo al contenido de la página reflejada con el cliente de correo electrónico, Facebook, Twitter, Google + y LinkedIn (consulte [Mercadotecnia viral: a un amigo](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** y **[!UICONTROL Notification style]** : genere código que dé formato a un correo electrónico con estilos HTML predefinidos. These blocks must be inserted in the source code of the delivery, in the **[!UICONTROL ...]** section, into **`<style>...</style>`** tags.
* **[!UICONTROL Offer acceptance URL in unitary mode]** :: inserta una dirección URL que permite establecer una oferta de interacción en **[!UICONTROL Accepted]** (consulte [esta sección](../../interaction/using/offer-analysis-report.md)).

## Definición de bloques personalizados propios {#defining-custom-personalization-blocks}

You can define new personalization fields to be inserted from the personalized field icon via the **[!UICONTROL Include...]** menu. Estos campos se definen en bloques personalizados.

Para crear un bloque personalizado, vaya al explorador y aplique los pasos siguientes:

1. Haga clic en el **[!UICONTROL Resources > Campaign Management > Personalization blocks]** nodo.
1. Right-click the list of blocks and select **[!UICONTROL New]** .
1. Rellene la configuración del bloque personalizado:

   ![](assets/s_ncs_user_personalized_block.png)

   * Introduzca la etiqueta del bloque. Esta etiqueta se muestra en la ventana de inserción del campo personalizado.
   * Select **[!UICONTROL Visible in the customization menus]** to make this block accessible from the personalization field insertion icon.
   * If necessary, select **[!UICONTROL The content of the personalization block depends upon the format]** to define two separate blocks for emails in HTML format and those in text format.

      A continuación, se muestran dos pestañas en la sección inferior de este editor (contenido HTML y contenido de texto) para definir los contenidos correspondientes.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Enter the content (in HTML, text, JavaScript, etc.) of the personalization block(s) and click **[!UICONTROL Save]** .
