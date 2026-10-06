---
product: campaign
title: Creación de tipos de eventos
description: Aprenda a crear tipos de eventos que coincidan con los mensajes transaccionales que desea enviar en Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
TQID: 'https://experienceleague.adobe.com/WfR-CUGmR3XeEQgBwd22RZPpSMF0Gja-7GewIIIxWug'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 100%
---
# Creación de tipos de eventos {#creating-event-types}



Para asegurarse de que cada evento se pueda cambiar a un mensaje personalizado, primero debe crear **tipos de eventos**.

Al [crear una plantilla de mensaje](../../message-center/using/creating-the-message-template.md), debe seleccionar el tipo de evento que coincida con el mensaje que desea enviar.

>[!IMPORTANT]
>
>Debe crear tipos de eventos antes de poder utilizarlos en plantillas de mensajes.

Para crear tipos de eventos que Adobe Campaign procesará, siga los pasos a continuación:

1. Inicie sesión en la **instancia de control**.

1. Vaya a la carpeta **[!UICONTROL Administration > Platform > Enumerations]** del árbol.

1. Seleccione **[!UICONTROL Event type]** en la lista.

1. Haga clic en **[!UICONTROL Add]** para crear un valor de enumeración. Puede ser una confirmación de pedido, cambio de contraseña o de envío de pedido, etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Cada tipo de evento coincide con un valor de enumeración **[!UICONTROL Event type]**.

1. Una vez que se hayan creado los valores de la lista desglosada, cierre la sesión y vuelva a la instancia para que la creación sea eficaz.

>[!NOTE]
>
>Obtenga más información sobre cómo **trabajar con listas desglosadas** en la [documentación de la versión 8 de Adobe Campaign (consola)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.



