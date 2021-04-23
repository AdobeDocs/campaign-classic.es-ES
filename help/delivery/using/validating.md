---
solution: Campaign Classic
product: campaign
title: Validación
description: Validación
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '241'
ht-degree: 100%

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
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]**: este modo permite actualizar los broadlogs a través de un archivo externo enviado por el proveedor de servicios. En este caso, se debe utilizar un flujo de trabajo que procese esta información para actualizar el estado del broadlog.

   >[!NOTE]
   >
   >En este caso, el usuario debe cambiar también el estado a **[!UICONTROL Finished]** en cuanto se actualicen los broadlogs.
