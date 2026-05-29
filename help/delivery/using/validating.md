---
product: campaign
title: Validación
description: Validación
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Direct Mail
hide: true
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
TQID: https://experienceleague.adobe.com/I31u-kAqMRpzti-bOtfYjrGbwvmsfeEPwWU7kCFLzcQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 250
ht-degree: 100%

---

# Validación{#validating}



Los conceptos globales al validar una entrega se presentan en [esta sección](steps-validating-the-delivery.md).

El archivo de salida de una entrega de correo directo se genera durante el análisis de la entrega. El contenido del archivo depende de las columnas de salida seleccionadas (consulte [Archivo de extracción](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase de análisis se detalla en [Análisis de la entrega](steps-validating-the-delivery.md#analyzing-the-delivery).

El archivo se genera durante la fase de análisis; sin embargo, la información sobre los destinatarios (es decir, “logs” de envío) no se actualiza. Así se puede cancelar este trabajo sin correr ningún riesgo.

Compruebe el resultado del análisis y el contenido del archivo de salida antes de hacer clic en **[!UICONTROL Confirm delivery]**. Un mensaje de confirmación permite iniciar la entrega.

La confirmación de la entrega inicia la extracción de datos en el archivo especificado.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

A continuación, puede cerrar el asistente y ver los registros de envío a través de la pestaña **[!UICONTROL Delivery]**, a la que se puede acceder a través de los detalles de envío.

Se puede configurar el modo de recuperación de “logs” de envío desde la pestaña **[!UICONTROL Analysis]** de las propiedades de envío.

Existen dos modos:

* **[!UICONTROL Messages are considered sent after validation]** (modo predeterminado): en este modo de función, todos los broadlogs se actualizan cuando el operador confirma la entrega (su estado pasa de “Envío pendiente” a “Enviado”) y la entrega se establece automáticamente como **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]**: este modo permite actualizar los broadlogs a través de un archivo externo enviado por el proveedor de servicios. En este caso, se debe utilizar un flujo de trabajo que procese esta información para actualizar el estado del broadlog.

  >[!NOTE]
  >
  >En este caso, el usuario debe cambiar también el estado a **[!UICONTROL Finished]** en cuanto se actualicen los broadlogs.
