---
product: campaign
title: Definición del contenido del correo directo
description: Aprenda a definir el contenido de correo directo
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Direct Mail
role: User
hide: true
hidefromtoc: true
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '176'
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
