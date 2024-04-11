---
product: campaign
title: Descompresión o descifrado de un archivo
description: Obtenga información sobre cómo descomprimir o descifrar un archivo en Campaign antes de procesarlo
feature: Workflows, Encryption
badge-v8: label="También se aplica a la versión 8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 89%

---


# Descompresión o descifrado de un archivo {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign permite importar archivos comprimidos o encriptados. Antes de que se puedan leer en una actividad [Data loading (file)](../../workflow/using/data-loading-file.md), puede definir un procesamiento previo para descomprimir o desencriptar el archivo.

>[!IMPORTANT]
>
>No puede descomprimir archivos comprimidos de más de 4 Gb.

Para poder hacerlo:

1. Utilice el [Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=es#decrypting-data) para generar un par de claves pública y privada para permitir el descifrado de archivos.

   >[!NOTE]
   >
   >Todos los usuarios administradores pueden acceder al Panel de control. Los pasos para otorgar acceso de administrador a un usuario se detallan en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=es#discover-control-panel).
   >
   >Tenga en cuenta que la instancia debe alojarse en AWS y actualizarse con la [última versión de GA](../../rn/using/rn-overview.md). Aprenda a comprobar su versión en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=es).

1. Si la instalación de Adobe Campaign está in situ: instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

   Si Adobe aloja la instalación de Adobe Campaign, contacte con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para que instalen las herramientas necesarias en el servidor.

A continuación, puede utilizar los comandos de preprocesamiento deseados en los flujos de trabajo:

1. Añada y configure una actividad **[!UICONTROL File transfer]** en el flujo de trabajo.
1. Añada una actividad **[!UICONTROL Data loading (file)]** y defina el formato de archivo.
1. Marque la opción **[!UICONTROL Pre-process the file]**.
1. Seleccione el comando de preprocesamiento que desee aplicar.
1. Añada otras actividades para administrar los datos que provengan del archivo.
1. Guarde y ejecute el flujo de trabajo.

A continuación se muestra un ejemplo en el caso de uso.

**Temas relacionados:**

* [Actividad de carga de datos (archivos)](../../workflow/using/data-loading-file.md).
* [Compresión o cifrado de un archivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Caso de uso: importación de datos cifrados con una clave generada por el Panel de control {#use-case-gpg-decrypt}

En este caso de uso, crearemos un flujo de trabajo para importar datos cifrados en un sistema externo utilizando una clave generada en el Panel de control.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#video)

Los pasos para realizar este caso de uso son los siguientes:

1. Utilice el Panel de control para generar un par de claves (pública/privada). Encontrará los pasos detallados en la documentación [del](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=es#decrypting-data) Panel de control.

   * La clave pública se comparte con el sistema externo, que la utiliza para cifrar los datos que se enviarán a Campaign.
   * Campaign Classic utiliza la clave privada para descifrar los datos cifrados entrantes.

   ![](assets/gpg_generate.png)

1. En el sistema externo, utilice la clave pública descargada del Panel de control para cifrar los datos que se van a importar a Campaign Classic.

1. En Campaign Classic, cree un flujo de trabajo para importar los datos cifrados y desencriptarlos con la clave privada que se ha instalado mediante el Panel de control. Para ello, crearemos un flujo de trabajo de la siguiente manera:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** actividad: transfiere el archivo de un origen externo a Campaign Classic. En este ejemplo, queremos transferir el archivo desde un servidor SFTP.
   * **[!UICONTROL Data loading (file)]** actividad: carga los datos del archivo en la base de datos y los descifra utilizando la clave privada generada en el Panel de control.

1. Abra la actividad **[!UICONTROL File transfer]** y especifique la cuenta externa desde la que desea importar el archivo .gpg cifrado.

   ![](assets/gpg_key_transfer.png)

   Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/file-transfer.md).

1. Abra la actividad **[!UICONTROL Data loading (file)]** y configúrela según sus necesidades. Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/data-loading-file.md).

   Añada una fase de preprocesamiento a la actividad para descifrar los datos entrantes. Para ello, seleccione la **[!UICONTROL Pre-process the file]** , luego seleccione **[!UICONTROL Decrypt]** desde el **[!UICONTROL Command]** lista desplegable:

   ![](assets/gpg_load.png)

   >[!NOTE]
   >
   >Si es necesario modificar los comandos disponibles, puede ponerse en contacto con [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para ajustar la configuración de preProcessCommand.
   >
   >Si está trabajando con una implementación híbrida, puede configurar estos comandos directamente desde el archivo de configuración del servidor (serverConf.xml). [Obtenga información sobre cómo configurar comandos de preprocesamiento en el archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md#preprocesscommand)

1. Haga clic en **[!UICONTROL OK]** para confirmar esta configuración.

1. Ahora puede ejecutar el flujo de trabajo. Una vez ejecutada, puede registrar en los registros de flujo de trabajo que el descifrado se ha ejecutado y que los datos del archivo se han importado.

   ![](assets/gpg_run.png)

## Tutorial en vídeo {#video}

Este vídeo muestra cómo utilizar una clave GPG para descifrar datos.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
