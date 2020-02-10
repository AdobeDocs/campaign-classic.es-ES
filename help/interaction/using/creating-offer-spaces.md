---
title: Creación de espacios de oferta
seo-title: Creación de espacios de oferta
description: Creación de espacios de oferta
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Creación de espacios de oferta{#creating-offer-spaces}

La creación del espacio de ofertas sólo se puede realizar mediante un **technical administrator** con acceso a la subcarpeta del espacio de oferta. Los espacios de ofertas solo se pueden crear en el entorno de diseño y se duplican automáticamente en el entorno interactivo durante la aprobación de la oferta.

El contenido del catálogo de ofertas se configura en los espacios de oferta. By default, the content can include the following fields: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** and **[!UICONTROL Text content]**. La secuencia de campos se configura en el espacio de oferta.

Los parámetros avanzados permiten especificar una clave de identificación de contacto (que puede estar formada por varios elementos, el campo de nombre y de correo electrónico al mismo tiempo, por ejemplo). Para obtener más información sobre esto, consulte la sección [Presentación de una oferta](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) identificada.

La renderización HTML o XML se crea mediante una función de renderización. La secuencia de los campos definidos en la función de renderización debe ser idéntica a la secuencia configurada en el contenido.

![](assets/offer_space_create_009.png)

Para crear un grupo de operadores nuevo, siga el proceso a continuación:

1. Go to the list of offer spaces and click **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Seleccione el canal que desee utilizar y cambie la etiqueta del espacio de oferta.

   ![](assets/offer_space_create_002.png)

1. Check the **[!UICONTROL Enable unitary mode]** box if one of the following cases applies to you:

   * Se utiliza la interacción con el centro de mensajes
   * Se utiliza el modo unitario de interacción (interacciones entrantes)

1. Vaya a la **[!UICONTROL Content field]** ventana y haga clic en **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Vaya al **[!UICONTROL Content]** nodo y seleccione los campos en el siguiente orden: **[!UICONTROL Title]**, entonces **[!UICONTROL Image URL]**, luego **[!UICONTROL HTML content]**, luego **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Check the **[!UICONTROL Required]** box to make each field mandatory.

   >[!NOTE]
   >
   >Esta configuración se utiliza en la vista previa y ofrece espacios de oferta no válidos al publicar si falta uno de los elementos obligatorios en la oferta en cuestión. Sin embargo, si una oferta ya está en directo en un espacio de oferta, estos criterios no se tienen en cuenta.

   ![](assets/offer_space_create_005.png)

1. Haga clic en **[!UICONTROL Edit functions]** para crear una función de procesamiento.

   Estas funciones se utilizan para generar representaciones de oferta en un espacio de oferta. Existen varios formatos posibles: HTML o texto para interacciones salientes y XML para interacciones entrantes.

   ![](assets/offer_space_create_006.png)

1. Vaya a la **[!UICONTROL HTML rendering]** ficha y seleccione **[!UICONTROL Overload the HTML rendering function]**.
1. Inserte la función de renderización.

   ![](assets/offer_space_create_007.png)

Si es necesario, se puede sobrecargar las funciones de renderización XML para las interacciones entrantes. También se puede sobrecargar las funciones de renderización de texto y HTML para las interacciones salientes. For more on this, refer to [About inbound channels](../../interaction/using/about-inbound-channels.md).

## Estados de propuesta de oferta {#offer-proposition-statuses}

Una propuesta de oferta puede tener varios estados en función de las interacciones con la población de destino. La interacción viene con un conjunto de valores que pueden aplicarse a la propuesta de oferta a lo largo de su ciclo de vida. Sin embargo, se debe configurar la plataforma para que el estado cambie cuando se cree y acepte la propuesta de oferta.

>[!NOTE]
>
>El estado de la propuesta de oferta no se actualiza inmediatamente. Se lleva a cabo mediante el flujo de trabajo de seguimiento, que se activa cada hora.

### Lista de estado {#status-list}

La interacción viene con los siguientes valores que pueden utilizarse para calificar el estado de una propuesta de oferta:

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

Estos valores no se aplican de forma predeterminada: tienen que configurarse.

>[!NOTE]
>
>El estado de una propuesta de oferta se cambia automáticamente a “Presented” si la oferta está vinculada a una envío con el estado “Sent”.

### Configuración del estado cuando se crea la propuesta {#configuring-the-status-when-the-proposition-is-created}

Cuando el motor de interacción crea una propuesta de oferta, su estado cambia, ya sea una interacción entrante o saliente. The choice between these two values depends on the way the offer spaces were configured in the **[!UICONTROL Design]** environment

Para cada espacio, se puede configurar el estado que se desee aplicar cuando se cree una propuesta, según la información que se desee mostrar en los informes de oferta.

Para ello, utilice el proceso siguiente:

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Seleccione el estado que desea aplicar a la propuesta cuando se cree.

   ![](assets/offer_update_status_001.png)

### Configuración del estado cuando se acepta la propuesta {#configuring-the-status-when-the-proposition-is-accepted}

Una vez aceptada la propuesta de oferta, se puede utilizar uno de los valores proporcionados de forma predeterminada para configurar el nuevo estado de la propuesta. La actualización es efectiva cuando un destinatario hace clic en un vínculo de la oferta, lo cual llama al motor de interacción.

Para ello, utilice el proceso siguiente:

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Seleccione el estado que desea aplicar a la propuesta cuando se acepte.

   ![](assets/offer_update_status_002.png)

**Interacción entrante**

The **[!UICONTROL Storage]** tab lets you define statuses for **proposed** and **accepted** offer propositions only. Para la interacción entrante, el estado de las propuestas de oferta debe especificarse directamente en la dirección URL para llamar al motor de oferta, en lugar de a través de la interfaz. De este modo, se puede especificar qué estado aplicar en otros casos, por ejemplo si se rechaza una propuesta de oferta.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Por ejemplo, la propuesta (identificador **40004**) que coincide con la oferta de **Home insurance** mostrada en el sitio **Neobank** contiene la siguiente dirección URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

As soon as a visitor clicks the offer, and therefore the URL, the **[!UICONTROL Accepted]** status (value **3**) is applied to the proposition and the visitor is redirected to a new page of the **Neobank** site to take out the insurance contract.

>[!NOTE]
>
>Si se desea especificar otro estado en la dirección URL (por ejemplo, si se rechaza una propuesta de oferta), se debe utilizar el valor correspondiente al estado deseado. Ejemplo: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; y así sucesivamente.
>
>Statuses and their values can be retrieved in the **[!UICONTROL Offer propositions (nms)]** data schema. Para obtener más información, consulte [esta página](../../configuration/using/data-schemas.md).

**Interacción saliente**

In case of an outbound interaction, you can automatically apply the **[!UICONTROL Interested]** status to an offer proposition when the delivery contains a link. Simplemente añada el valor **_urlType=&quot;11&quot;** al enlace:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Vista previa de oferta por espacio {#offer-preview-per-space}

En esta pestaña, se puede ver las ofertas para las que el destinatario es elegible mediante un método elegido. En el siguiente ejemplo, el destinatario es elegible para las tres propuestas de oferta por correo electrónico.

![](assets/offer_space_overview_002.png)

Si un destinatario no es elegible para ninguna oferta, esto se muestra en la vista previa.

![](assets/offer_space_overview_001.png)

La vista previa puede omitir los contextos cuando están restringidos a un espacio. This is the case when the interaction schema has been extended to add fields referenced in a space using an inbound channel (for more on this, refer to [Extension example](../../interaction/using/extension-example.md)).
