---
product: campaign
title: Creación de SMS con Campaign
description: Obtenga información sobre cómo crear SMS con Campaign
feature: SMS
role: User
hide: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
TQID: https://experienceleague.adobe.com/ENt9cwc7OjXcMr5tbkg2f3BxpPBNtVytVTw70NQZPyI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 465
ht-degree: 100%

---

# Creación de una entrega de SMS {#creating-a-sms-delivery}

## Selección del canal de entrega {#selecting-the-delivery-channel}

Para diseñar un envío de SMS nuevo, siga los pasos a continuación:

>[!NOTE]
>
>En la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es){target="_blank"} se exponen conceptos globales sobre la creación de envíos.

1. Cree un nuevo envío, por ejemplo, en el panel de control de envíos.
1. Seleccione la plantilla de envíos **Enviado a móviles (NetSize)** creada anteriormente. Para obtener más información, consulte la sección [Modificación de la plantilla de entrega](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifique su envío con una etiqueta, un código y una descripción. Para obtener más información, consulte esta sección en la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es#create-the-delivery){target="_blank"}.
1. Haga clic en **[!UICONTROL Continue]** para confirmar esta información y mostrar la ventana de configuración de mensajes.

## Definición del contenido del SMS {#defining-the-sms-content}

Para crear el contenido del SMS, siga los pasos a continuación:

1. Introduzca el contenido del mensaje en la sección **[!UICONTROL Text content]** del asistente. Los botones de la barra de herramientas permiten importar, guardar o buscar dentro del contenido. El último botón se utiliza para insertar campos de personalización.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   El uso de los campos de personalización se presenta en la sección [Acerca de la personalización](about-personalization.md).

1. Haga clic en **[!UICONTROL Preview]** en la parte inferior de la página para ver la renderización del mensaje con su personalización. Para iniciar la previsualización, seleccione un destinatario con el botón **[!UICONTROL Test personalization]** de la barra de herramientas. Puede seleccionar un destinatario del público objetivo definido o elegir otro destinatario.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Puede aprobar el mensaje SMS. También puede ver el contenido del SMS en la pantalla del teléfono móvil que aparece a la derecha del editor de contenido. Haga clic en la pantalla y utilice el ratón para desplazarse por el contenido.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Haga clic en el enlace **[!UICONTROL Data loaded]** para ver la información sobre el destinatario.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Los mensajes SMS se limitan a una longitud de 160 caracteres si se utiliza la página de códigos Latin-1 (ISO-8859-1). Si el mensaje se escribe en Unicode, no debe exceder los 70 caracteres. Algunos caracteres especiales pueden afectar la longitud del mensaje. Para obtener más información sobre la longitud del mensaje, consulte la sección [Transliteración de caracteres de SMS](#about-character-transliteration).
   >
   >Cuando hay campos de personalización o campos de contenido condicionados, el tamaño del mensaje varía según el destinatario. La longitud del mensaje debe evaluarse cuando se haya realizado la personalización.
   >
   >Al iniciar el análisis, se comprueba la longitud de los mensajes y se muestra una advertencia en caso de contenidos adicionales.

1. Si utiliza el conector NetSize o un conector SMPP, puede personalizar el nombre del remitente de la entrega. Para obtener más información, consulte [Parámetros avanzados](#advanced-parameters).

## Selección de la población objetivo {#selecting-the-target-population}

En [esta sección](steps-defining-the-target-population.md) se describe el proceso detallado al seleccionar la población objetivo de una entrega.

Para obtener más información sobre el uso de los campos de personalización, consulte [esta sección](about-personalization.md).

Para obtener más información sobre la integración de una lista semilla, consulte [esta página](about-seed-addresses.md).
