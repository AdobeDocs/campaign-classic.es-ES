---
product: campaign
title: Definición del contenido del correo directo
description: Aprenda a definir el contenido de correo directo
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Direct Mail
role: User
hide: true
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
TQID: https://experienceleague.adobe.com/LybEpDwVDNAGQg5CA2nZ3IkNoyHFiYvNuKm-VXYW4s4
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
workflow-type: tm+mt
source-wordcount: 176
ht-degree: 100%

---

# Definición del contenido de correo directo{#defining-the-direct-mail-content}

## Archivo de extracción {#extraction-file}

El nombre del archivo que contiene los datos extraídos se define en el campo **[!UICONTROL File]**. El botón situado a la derecha del campo permite utilizar campos personalizados para crear el nombre del archivo.

De forma predeterminada, el archivo de extracción se crea y se almacena en el servidor. Puede guardarlo en el equipo. Para ello, marque la **[!UICONTROL Download the generated file after the analysis of the delivery]**. En este caso, es necesario indicar la ruta de acceso al directorio de almacenamiento local así como al nombre de archivo.

![](assets/s_ncs_user_mail_delivery_local_file.png)

Para una entrega de correo directo, el contenido de la extracción se define en el vínculo **[!UICONTROL Edit the extraction file format...]**.

![](assets/s_ncs_user_mail_delivery_format_link.png)

Este vínculo le permite acceder al asistente de extracción y definir la información (columnas) que se va a exportar en el archivo de salida.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

Es posible insertar una URL personalizada en el archivo de extracción. Para obtener más información, consulte [esta sección](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>Este asistente incluye los pasos del asistente de exportación detallados en la sección [Introducción](../../platform/using/executing-export-jobs.md).
