---
title: Cómo utilizar los datos de flujo de trabajo
seo-title: Cómo utilizar los datos de flujo de trabajo
description: Cómo utilizar los datos de flujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bb35d2ae2d40aaef3bb381675d0c36ffb100b242
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 49%

---


# Cómo utilizar los datos de flujo de trabajo{#how-to-use-workflow-data}

## Actualización de la base de datos {#updating-the-database}

Todos los datos recopilados pueden utilizarse para actualizar la base de datos o en las entregas. Por ejemplo, puede enriquecer las opciones de personalización del contenido del mensaje (incluir el número de los contratos en el mensaje, especificar el carro de la compra medio en el último año, etc.) o detallar la población objetivo (enviar un mensaje a los cotitulares del contrato, dirigirse a los 1000 mejores suscriptores de los servicios en línea, etc.). Estos datos también se pueden exportar o archivar en una lista.

### Listas y actualizaciones directas {#lists-and-direct-updates}

Los datos de la base de datos de Adobe Campaign y de las listas existentes pueden actualizarse mediante dos actividades específicas:

* La actividad **[!UICONTROL List update]** permite almacenar tablas de trabajo en una lista de datos.

   Puede seleccionar una lista existente o crearla. En este caso, se calculan el nombre y, posiblemente, la carpeta de registros.

   ![](assets/s_user_create_list.png)

   Consulte [Actualización de listas](../../workflow/using/list-update.md).

* La actividad **[!UICONTROL Update data]** realiza una actualización en masa de los campos de la base de datos.

   Para obtener más información, consulte [Actualización de datos](../../workflow/using/update-data.md).

### Gestión de suscripciones y bajas {#subscription-unsubscription-management}

Para obtener información sobre las suscripciones y las bajas de destinatarios de un servicio informativo a través de un flujo de trabajo, consulte [Servicios de suscripción](../../workflow/using/subscription-services.md).

## Envío a través de un flujo de trabajo {#sending-via-a-workflow}

### Actividad de envío {#delivery-activity}

La actividad de envío aparece detallada en [Envío](../../workflow/using/delivery.md).

### Enriquecimiento y establecimiento de objetivos de las entregas {#enriching-and-targeting-deliveries}

Los envíos pueden procesar datos de flujos de trabajo para personalizar el contenido o dentro del marco de selección de la población objetivo.

Por ejemplo, en el marco de una entrega de correo postal, puede incluir los datos adicionales, tomados de la manipulación de datos llevada a cabo en el flujo de trabajo, en el archivo de extracción:

![](assets/s_advuser_add_data_postal_mail.png)

Además de los campos personalizados habituales, puede añadir campos personalizados desde las fases del flujo de trabajo al contenido de la entrega. Los datos adicionales definidos en las actividades de flujo de trabajo se pueden conservar y se puede conceder acceso a ellos desde el asistente de envío, como se muestra en el ejemplo siguiente, para definir el nombre del archivo de salida dentro del marco de la distribución de correo postal:

![](assets/s_advuser_using_additional_data.png)

Los datos contenidos en la tabla de flujo de trabajo se identifican con su nombre: siempre se compone del vínculo **targetData.** Para obtener más información, consulte [Datos de destinatario](../../workflow/using/data-life-cycle.md#target-data).

Dentro del marco de una entrega de correo electrónico, los campos personalizados también pueden utilizar datos de la extensión de grupo objetivo realizada en las fases del flujo de trabajo de objetivos, como se muestra en el ejemplo siguiente:

![](assets/s_advuser_add_data_email.png)

Si se especifica un código de segmento en una actividad de objetivo, se añade a una columna específica de la tabla de flujo de trabajo y se ofrece junto con los campos personalizados. To display all personalization fields, click the **[!UICONTROL Target extension > Other...]** link accessible via the personalization button.

![](assets/s_advuser_segment_code_select.png)

## Exportación de datos {#exporting-data}

### Comprimir o encriptar un archivo {#zipping-or-encrypting-a-file}

Adobe Campaign permite exportar archivos comprimidos o encriptados. When defining an export through a **[!UICONTROL Data extraction (file)]** activity, you can define a post-processing to zip or to encrypt the file.

Para poder hacerlo:

1. Instale un par de claves GPG para su instancia mediante el Panel [de control](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >El Panel de control está disponible para todos los clientes alojados en AWS (excepto para los clientes que hospedan sus instancias de marketing in situ).

1. Si la instalación de Adobe Campaign está alojada en Adobe, póngase en contacto con el servicio de atención al cliente de Adobe para instalar las utilidades necesarias en el servidor.
1. Si la instalación de Adobe Campaign está in situ, instale la utilidad que desee utilizar (por ejemplo: GPG, GZIP) así como las claves necesarias (clave de cifrado) en el servidor de aplicaciones.

A continuación, puede utilizar comandos o código en la **[!UICONTROL Script]** ficha de la actividad o en una **[!UICONTROL JavaScript code]** actividad. A continuación se muestra un ejemplo en el caso de uso.

**Temas relacionados:**

* [Descompresión o desencriptado de un archivo antes de procesarlo](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [actividad](../../workflow/using/extraction--file-.md)de extracción de datos (archivo).

### Caso de uso: Codificación y exportación de datos mediante una clave instalada en el Panel de control {#use-case-gpg-encrypt}

En este caso de uso, crearemos un flujo de trabajo para cifrar y exportar datos mediante una clave instalada en el Panel de control.

Los pasos para realizar este caso de uso son los siguientes:

1. Genere un par de claves GPG (público/privado) utilizando una utilidad GPG, luego instale la clave pública en el Panel de control. Encontrará pasos detallados en la documentación [del Panel](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)de control.

1. En Campaign Classic, cree un flujo de trabajo para exportar los datos y exportarlos con la clave privada que se ha instalado mediante el Panel de control. Para ello, crearemos un flujo de trabajo de la siguiente manera:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** actividad: En este ejemplo, queremos ejecutar una consulta para destinatario de los datos de la base de datos que queremos exportar.
   * **[!UICONTROL Data extraction (file)]** actividad: Extrae los datos en un archivo.
   * **[!UICONTROL JavaScript code]** actividad: Codifica los datos que se van a extraer.
   * **[!UICONTROL File transfer]** actividad: Envía los datos a un origen externo (en este ejemplo, un servidor SFTP).

1. Configure la **[!UICONTROL Query]** actividad para destinatario de los datos deseados de la base de datos. Para obtener más información, consulte [esta sección](../../workflow/using/query.md).

1. Abra la **[!UICONTROL Data extraction (file)]** actividad y configúrela según sus necesidades. Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Abra la **[!UICONTROL JavaScript code]** actividad y copie y pegue el comando siguiente para cifrar los datos que desee extraer.

   >[!IMPORTANT]
   >
   >Asegúrese de reemplazar el valor de la **huella** del comando por la huella digital de la clave pública instalada en el Panel de control.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch -yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Abra la **[!UICONTROL File transfer]** actividad y especifique el servidor SFTP al que desea enviar el archivo. Los conceptos globales sobre cómo configurar la actividad están disponibles en [esta sección](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Ahora puede ejecutar el flujo de trabajo. Una vez ejecutado, el destinatario de datos por la consulta se exportará al servidor SFTP en un archivo .gpg cifrado.

   ![](assets/gpg-sftp-encrypt.png)
