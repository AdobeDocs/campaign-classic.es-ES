---
product: campaign
title: Creación de tipos de eventos
description: Aprenda a crear tipos de eventos que coincidan con los mensajes transaccionales que desea enviar en Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 16%

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

1. Haga clic en **[!UICONTROL Add]** para crear un valor de enumeración. Puede ser una confirmación de pedido, un cambio de contraseña, un cambio de entrega de pedido, etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Cada tipo de evento debe coincidir con un valor de la enumeración **[!UICONTROL Event type]**.

1. Una vez que se hayan creado los valores de la lista desglosada, cierre la sesión y vuelva a la instancia para que la creación sea eficaz.

>[!NOTE]
>
>Obtenga más información sobre listas desglosadas en [Administración de enumeraciones](../../platform/using/managing-enumerations.md).


