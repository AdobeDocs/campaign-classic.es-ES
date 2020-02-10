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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Validación{#validating}

Los conceptos globales al validar una entrega se presentan en [esta sección](../../delivery/using/steps-validating-the-delivery.md).

El archivo de salida de una entrega de correo directo se genera durante el análisis de la entrega. El contenido del archivo depende de las columnas de salida seleccionadas (consulte el archivo [Extracción](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase de análisis se detalla en [Análisis de la entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

El archivo se genera durante la fase de análisis; sin embargo, la información sobre los destinatarios (es decir, “logs” de envío) no se actualiza. Así se puede cancelar este trabajo sin correr ningún riesgo.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. Un mensaje de confirmación permite iniciar el envío.

La confirmación del envío inicia la extracción de datos en el archivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the wizard and look at the delivery logs via the **[!UICONTROL Delivery]** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

Existen dos modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo predeterminado): en este modo de función, todos los logs se actualizan cuando el operador confirma el envío (su estado pasa de &#39;Entrega pendiente&#39; a &#39;Enviado&#39;) y la entrega se establece automáticamente en **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :: este modo le permite actualizar los logs de banda ancha mediante un archivo externo enviado por el proveedor de servicios. En este caso, se debe utilizar un flujo de trabajo que procese esta información para actualizar el estado del broadlog.

   >[!NOTE]
   >
   >In this case, the delivery&#39;s status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
