---
title: Validación
seo-title: Validación
description: Validación
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 92%

---


# Validación{#validating}

Los conceptos globales al validar una entrega se presentan en [esta sección](../../delivery/using/steps-validating-the-delivery.md).

El archivo de salida de una entrega de correo directo se genera durante el análisis de la entrega. El contenido del archivo depende de las columnas de salida seleccionadas (consulte [Archivo de extracción](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase de análisis se detalla en [Análisis de la entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

El archivo se genera durante la fase de análisis; sin embargo, la información sobre los destinatarios (es decir, “logs” de envío) no se actualiza. Así se puede cancelar este trabajo sin correr ningún riesgo.

Compruebe el resultado del análisis y el contenido del archivo de salida antes de hacer clic en **[!UICONTROL Confirm delivery]**. Un mensaje de confirmación permite iniciar la entrega.

La confirmación de la entrega inicia la extracción de datos en el archivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

A continuación, puede cerrar el asistente y ver los “logs” de envío a través de la pestaña **[!UICONTROL Delivery]**, a la que se puede acceder a través de los detalles de envío.

Se puede configurar el modo de recuperación de “logs” de envío desde la pestaña **[!UICONTROL Analysis]** de las propiedades de envío.

Existen dos modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo predeterminado): en este modo de función, todos los broadlogs se actualizan cuando el operador confirma la entrega (su estado pasa de “Envío pendiente” a “Enviado”) y la entrega se establece automáticamente como **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :: este modo le permite actualizar los logs de banda ancha mediante un archivo externo enviado por el proveedor de servicio. En este caso, se debe utilizar un flujo de trabajo que procese esta información para actualizar el estado del broadlog.

   >[!NOTE]
   >
   >En este caso, el usuario debe cambiar también el estado a **[!UICONTROL Finished]** en cuanto se actualicen los broadlogs.
