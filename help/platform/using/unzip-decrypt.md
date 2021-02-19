---
solution: Campaign Classic
product: campaign
title: Descompresión o descifrado de un archivo
description: Obtenga información sobre cómo descomprimir o descifrar un archivo en Campaign Classic antes de procesarlo.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 100%

---


# Descompresión o descifrado de un archivo {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign permite importar archivos comprimidos o encriptados. Antes de que se puedan leer en una actividad [Data loading (file)](../../workflow/using/data-loading--file-.md), puede definir un procesamiento previo para descomprimir o desencriptar el archivo.

Para poder hacerlo:

1. Utilice el [Panel de control de Campaign](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) para generar un par de claves pública y privada.

   >[!NOTE]
   >
   >Panel de control de Campaign está disponible para todos los clientes alojados en AWS (excepto para los clientes que alojan sus instancias de marketing on-Premise).

1. Si Adobe aloja la instalación de Adobe Campaign, contacte con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para que instalen las herramientas necesarias en el servidor.
1. Si la instalación de Adobe Campaign está in situ: instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

A continuación, puede utilizar los comandos de preprocesamiento deseados en los flujos de trabajo:

1. Añada y configure una actividad **[!UICONTROL File transfer]** en el flujo de trabajo.
1. Añada una actividad **[!UICONTROL Data loading (file)]** y defina el formato de archivo.
1. Marque la opción **[!UICONTROL Pre-process the file]**.
1. Especifique el comando de preprocesamiento que desee aplicar.
1. Añada otras actividades para administrar los datos que provengan del archivo.
1. Guarde y ejecute el flujo de trabajo.

A continuación se muestra un ejemplo en el caso de uso.

**Temas relacionados:**

* [Actividad de carga de datos (archivos)](../../workflow/using/data-loading--file-.md).
* [Comprimir o encriptar un archivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Caso de uso: importación de datos cifrados con una clave generada por el Panel de control de Campaign{#use-case-gpg-decrypt}

En este caso de uso, crearemos un flujo de trabajo para importar datos cifrados en un sistema externo utilizando una clave generada en el Panel de control de Campaign.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#video)

Los pasos para realizar este caso de uso son los siguientes:

1. Utilice el Panel de control de Campaign para generar un par de claves (pública/privada). Encontrará los pasos detallados en la documentación [del](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) Panel de control de Campaign.

   * La clave pública se comparte con el sistema externo, que la utiliza para cifrar los datos que se enviarán a Campaign.
   * Campaign Classic utiliza la clave privada para descifrar los datos cifrados entrantes.

   ![](assets/gpg_generate.png)

1. En el sistema externo, utilice la clave pública descargada del Panel de control de Campaign para cifrar los datos que se van a importar a Campaign Classic.

1. En Campaign Classic, cree un flujo de trabajo para importar los datos cifrados y desencriptarlos con la clave privada que se ha instalado mediante el Panel de control de Campaign. Para ello, crearemos un flujo de trabajo de la siguiente manera:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** actividad: transfiere el archivo de un origen externo a Campaign Classic. En este ejemplo, queremos transferir el archivo desde un servidor SFTP.
   * **[!UICONTROL Data loading (file)]** actividad: carga los datos del archivo en la base de datos y los descifra utilizando la clave privada generada en el Panel de control de Campaign.

1. Abra la actividad **[!UICONTROL File transfer]** y especifique la cuenta externa desde la que desea importar el archivo .gpg cifrado.

   ![](assets/gpg_key_transfer.png)

   Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/file-transfer.md).

1. Abra la actividad **[!UICONTROL Data loading (file)]** y configúrela según sus necesidades. Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/data-loading--file-.md).

   Añada una fase de preprocesamiento a la actividad para descifrar los datos entrantes. Para ello, seleccione la opción **[!UICONTROL Pre-process the file]** y copie y pegue este comando de descifrado en el **[!UICONTROL Command]** campo:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >En este ejemplo, utilizamos la frase de contraseña utilizada de forma predeterminada por Panel de control de Campaign, que es &quot;frase de contraseña&quot;.
   >
   >Si ya ha instalado las claves GPG en su instancia a través de una solicitud a Atención al cliente en el pasado, la frase de contraseña puede haber cambiado y ser diferente de la predeterminada.

1. Haga clic en **[!UICONTROL OK]** para confirmar esta configuración.

1. Ahora puede ejecutar el flujo de trabajo. Una vez ejecutada, puede registrar en los registros de flujo de trabajo que el descifrado se ha ejecutado y que los datos del archivo se han importado.

   ![](assets/gpg_run.png)

## Videotutorial {#video}

Este vídeo muestra cómo utilizar una clave GPG para descifrar datos.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
