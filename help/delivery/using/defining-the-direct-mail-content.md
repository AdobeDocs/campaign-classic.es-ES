---
solution: Campaign Classic
product: campaign
title: Definición del contenido de correo postal
description: Definición del contenido de correo postal
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: ht
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: ht
source-wordcount: '164'
ht-degree: 100%

---


# Definición del contenido de correo postal{#defining-the-direct-mail-content}

## Extracción de archivos {#extraction-file}

El nombre del archivo que contiene los datos extraídos se define en el campo **[!UICONTROL File]**. El botón situado a la derecha del campo permite utilizar campos personalizados para crear el nombre del archivo.

De forma predeterminada, el archivo de extracción se crea y se almacena en el servidor. Puede guardarlo en el equipo. Para ello, marque la **[!UICONTROL Download the generated file after the analysis of the delivery]**. En este caso, es necesario indicar la ruta de acceso al directorio de almacenamiento local así como al nombre de archivo.

![](assets/s_ncs_user_mail_delivery_local_file.png)

Para una entrega de correo postal, el contenido de la extracción se define en el vínculo **[!UICONTROL Edit the extraction file format...]**.

![](assets/s_ncs_user_mail_delivery_format_link.png)

Este vínculo le permite acceder al Asistente de extracción y definir la información (columnas) que se van a exportar en el archivo de salida.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

Es posible insertar una URL personalizada en el archivo de extracción. Para obtener más información, consulte [esta sección](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>Este asistente incluye los pasos del asistente de exportación detallados en la sección [Introducción](../../platform/using/exporting-data.md#export-wizard).
