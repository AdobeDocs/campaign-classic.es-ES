---
product: campaign
title: Compresión o cifrado de un archivo
description: Obtenga información sobre cómo comprimir o cifrar un archivo en Campaign antes de procesarlo
feature: Data Management, Encryption
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
TQID: https://experienceleague.adobe.com/mnkVYu3ibG6yFi1Zd5q1b1-CnzdheG8xvmM8q92-8vQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 617
ht-degree: 99%

---

# Compresión o cifrado de un archivo {#zipping-or-encrypting-a-file}

Adobe Campaign permite exportar archivos comprimidos o cifrados. Al definir una exportación a través de una actividad **[!UICONTROL Data extraction (file)]**, puede definir un posprocesamiento para comprimir o cifrar el archivo.

Para poder hacerlo:

1. Instale un par de claves GPG para su instancia mediante el [Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=es#encrypting-data).

   >[!NOTE]
   >
   >El Panel de control está restringido a los usuarios administradores y solo está disponible para determinadas versiones de Campaign. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=es)
   >

1. Si Adobe aloja la instalación de Adobe Campaign, contacte con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para que instalen las herramientas necesarias en el servidor.
1. Si la instalación de Adobe Campaign está in situ: instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

A continuación, puede utilizar comandos o código en la pestaña **[!UICONTROL Script]** de la actividad o en una actividad **[!UICONTROL JavaScript code]** . A continuación se muestra un ejemplo en el caso de uso.

**Temas relacionados:**

* [Descomprimir o descifrar un archivo antes de procesarlo](../../platform/using/unzip-decrypt.md)
* [Actividad de extracción de datos (archivo)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=es){target="_blank"}

## Caso de uso: cifrado y exportación de datos con una clave instalada en el Panel de control {#use-case-gpg-encrypt}

En este caso de uso, crearemos un flujo de trabajo para cifrar y exportar los datos con una clave instalada en el Panel de control.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#video)

Los pasos para realizar este caso de uso son los siguientes:

1. genere un par de claves GPG (públicas/privadas) utilizando una utilidad GPG, luego instale la clave pública en Panel de control. Encontrará los pasos detallados en la documentación [del](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=es#encrypting-data) Panel de control.

1. En Campaign Classic, genere un flujo de trabajo para exportar los datos y cifrarlos con la clave privada que se ha instalado mediante el Panel de control. Para ello, crearemos un flujo de trabajo de la siguiente manera:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** actividad: En este ejemplo, queremos ejecutar una consulta para un destinatario de los datos de la base de datos que queremos exportar.
   * **[!UICONTROL Data extraction (file)]** actividad: extrae los datos en un archivo.
   * **[!UICONTROL JavaScript code]** actividad: cifra los datos que se van a extraer.
   * **[!UICONTROL File transfer]** actividad: envía los datos a un origen externo (en este ejemplo, un servidor SFTP).

1. Configure la actividad **[!UICONTROL Query]** para destinatario de los datos deseados de la base de datos. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=es){target="_blank"}.

1. Abra la actividad **[!UICONTROL Data extraction (file)]** y configúrela según sus necesidades. Los conceptos globales sobre cómo configurar la actividad están disponibles en la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=es){target="_blank"}.

   ![](assets/gpg-data-extraction.png)

1. Abra la actividad **[!UICONTROL JavaScript code]** y copie y pegue el comando siguiente para cifrar los datos que desee extraer.

   >[!IMPORTANT]
   >
   >Asegúrese de reemplazar el valor de la **huella** del comando por la huella digital de la clave pública instalada en el Panel de control.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Abra la actividad **[!UICONTROL File transfer]** y especifique el servidor SFTP al que desea enviar el archivo. Los conceptos globales sobre cómo configurar la actividad están disponibles en la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=es){target="_blank"}.

   ![](assets/gpg-file-transfer.png)

1. Ahora puede ejecutar el flujo de trabajo. Una vez ejecutado, el destinatario de datos de la consulta se exportará al servidor SFTP en un archivo .gpg cifrado.

## Tutorial en vídeo {#video}

Este vídeo muestra cómo utilizar una clave GPG para cifrar datos y también está disponible en

>[!VIDEO](https://video.tv.adobe.com/v/41330?captions=spa&quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
