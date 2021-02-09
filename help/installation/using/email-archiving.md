---
solution: Campaign Classic
product: campaign
title: Almacenamiento de correos electrónicos
description: Almacenamiento de correos electrónicos
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 5fa848d86f951cb9dc40eb7981abea29c1092291
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 3%

---


# Correo electrónico CCO {#email-archiving}

Puede configurar Adobe Campaign para que mantenga una copia de los correos electrónicos enviados desde su plataforma.

Sin embargo, Adobe Campaign no administra los archivos archivados. Le permite enviar los mensajes de su elección a una dirección dedicada, desde donde se pueden procesar y archivar usando un sistema externo.

Para ello, los archivos .eml correspondientes a los correos electrónicos enviados se transfieren a un servidor remoto, como un servidor de correo electrónico SMTP. El destino de archivado es una dirección de correo electrónico CCO (invisible para los destinatarios de envío) que debe especificar.

## Recommendations y limitaciones {#recommendations-and-limitations}

* La función Email BCC es opcional. Compruebe el acuerdo de licencia.
* Para **arquitecturas híbridas y alojadas**, póngase en contacto con el ejecutivo de cuentas para activarla. La dirección de correo electrónico CCO que elija debe proporcionarse al equipo de Adobe que la configurará por usted.
* Para **instalaciones in situ**, siga las pautas a continuación para activarla; consulte las secciones [Activating email BCC (on premise)](#activating-email-archiving--on-premise-) y [Configuring the BCC email address (on premise)](#configuring-the-bcc-email-address--on-premise-).
* Solo puede usar una dirección de correo electrónico CCO.
* Una vez configurada la CCO de correo electrónico, asegúrese de que la función está habilitada en la Plantilla de envíos o en el envío a través de la opción **[!UICONTROL Email BCC]**. Para obtener más información, consulte [esta sección](../../delivery/using/sending-messages.md#archiving-emails).
* Solo se tienen en cuenta los mensajes de correo electrónico enviados correctamente; las devoluciones no.
* El sistema de archiving de correo electrónico cambió con Adobe Campaign 17.2 (compilación 8795). Si ya estaba utilizando el archivado de correo electrónico, debe actualizar manualmente al nuevo sistema CCO de correo electrónico. Para obtener más información sobre esto, consulte la sección [Pasar al nuevo BCC de correo electrónico](#updated-email-archiving-system--bcc-).

## Activación de Email BCC (in situ) {#activating-email-archiving--on-premise-}

Para activar el archivado de correo electrónico CCO cuando Adobe Campaign esté instalado in situ, siga los pasos a continuación.

### Carpeta local {#local-folder}

Para habilitar la transferencia de correos electrónicos enviados a una dirección de correo electrónico de CCO, las copias exactas sin procesar de los correos electrónicos enviados deben guardarse primero como archivos .eml en una carpeta local.

La ruta de la carpeta local debe especificarse en el archivo **config-`<instance>`.xml**, desde la configuración. Por ejemplo:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Es responsabilidad del equipo que implementa el proyecto garantizar que la configuración de seguridad permita el acceso a la carpeta definida a través de los parámetros **dataLogPath**.

La ruta completa es la siguiente: **`<datalogpath>  YYYY-MM-DDHHh`**. La fecha y la hora se configuran según el reloj del servidor MTA (UTC). Por ejemplo:

```
C:\emails\2018-12-02\13h
```

El nombre del archivo de archivo es **`<deliveryid>-<broadlogid>.eml`** cuando el estado de los mensajes de correo electrónico no es **[!UICONTROL Sent]**. Una vez que el estado ha cambiado a **[!UICONTROL Sent]**, el nombre del archivo pasa a ser **`<deliveryid>-<broadlogid>-sent.eml`**. Por ejemplo:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>En una instancia de intermediaria, el directorio de los mensajes de correo electrónico CCO se encuentra en el servidor intermediaria.
>
>El deliveryID y el BroadlogID provienen del servidor intermediaria cuando no se envía el estado de los correos electrónicos. Una vez que el estado ha cambiado a **[!UICONTROL Sent]**, estos ID provienen del servidor de mercadotecnia.

### Parámetros {#parameters}

Una vez definida la ruta de la carpeta local, agregue y edite los siguientes elementos como desee en el archivo **config-`<instance name>.xml`**. Debajo están los valores predeterminados:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato utilizado al comprimir los archivos .eml. Los valores posibles son estos:

   **0**: sin compresión (valor predeterminado)

   **1**: compresión (formato .zip)

* **compressBatchSize**: número de archivos .eml agregados a un archivo (archivo .zip).
* **archiveType**: estrategia de archiving que se utilizará. Los valores posibles son estos:

   **0**: las copias sin procesar de los correos electrónicos enviados se guardan en formato .eml en la carpeta  **** dataLogPathfolder (valor predeterminado). Se guarda una copia de archivado del archivo **`<deliveryid>-<broadlogid>-sent.eml`** en la carpeta **dataLogPath/archives**. La ruta del archivo de correo electrónico enviado se convierte en **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: las copias sin procesar de los correos electrónicos enviados se guardan en formato .eml en la carpeta  **** dataLogPathfolder y se envían a la dirección de correo electrónico de BCC a través de SMTP. Una vez que las copias de correo electrónico se envían a la dirección de BCC, el nombre del archivo de archivo pasa a **`<deliveryid>-<broadlogid>-sent-archived.eml`** y el archivo se mueve a la carpeta **dataLogPath/archives**. La ruta del archivo de correo electrónico enviado y archivado por CCO es **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: número de días que se guardan los archivos .eml para archivarlos. Después de ese retraso, se mueven automáticamente a la carpeta **dataLogPath/archives** para compresión. De forma predeterminada, los archivos .eml caducan pasados dos días.
* **purgeArchivesDelay**: número de días que se guardan los archivos en la  **carpeta dataLogPath/`<archives>`** folder. Después de ese período, se eliminan de forma permanente. La purga comienza cuando se inicia el MTA. De forma predeterminada, se realiza cada siete días.
* **pollDelay**: comprobar la frecuencia (en segundos) de los nuevos correos electrónicos enviados a la carpeta  **** dataLogPathfolder. Por ejemplo, si este parámetro se establece en 60, significa que cada minuto, el proceso de archiving pasa por los archivos .eml dentro de las carpetas **dataLogPath/`<date and time>`**, aplica una purga si es necesario y envía copias de correo electrónico a la dirección de BCC y/o comprime los archivos archivados cuando sea necesario.
* **acquisitionLimit**: número de archivos .eml procesados a la vez antes de que el proceso de archivado se aplique de nuevo según el parámetro  **** pollDelayt. Por ejemplo, si establece el parámetro **acquisitionLimit** en 100 mientras que el parámetro **pollDelay** se establece en 60, se procesarán 100 archivos .eml por minuto.
* **smtpNbConnection**: número de conexiones SMTP a la dirección de correo electrónico de CCO.

Asegúrese de ajustar estos parámetros según el rendimiento de envío de correo electrónico. Por ejemplo, en una configuración en la que el MTA envía 30.000 correos electrónicos por hora, puede establecer el parámetro **pollDelay** en 600, el parámetro **acquisitionLimit** en 5000 y el parámetro **smtpNbConnection** en 2. Significa que, con 2 conexiones SMTP, se enviarán 5000 correos electrónicos a la dirección CCO cada 10 minutos.

## Configuración de la dirección de correo electrónico de CCO (in situ) {#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>Por razones de privacidad, los correos electrónicos CCO deben ser procesados por un sistema de archiving capaz de almacenar información personal (PII) de manera segura.

En el archivo **config-`<instance name>.xml`**, utilice los siguientes parámetros para definir el servidor de correo electrónico SMTP al que se transferirán los archivos almacenados:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archivo de destino de destinatario
* **smtpEnableTLS**: uso de una conexión SMTP segura (protocolo TLS/SSL)
* **smtpRelayAddress**: dirección de retransmisión para usar
* **smtpRelayPort**: puerto de retransmisión para usar

>[!NOTE]
>
>Si utiliza un reenvío SMTP, los cambios realizados en los mensajes de correo electrónico por el reenvío no se tendrán en cuenta en el proceso de archivado.
>
>Además, el relé asigna un estado **[!UICONTROL Sent]** a todos los correos electrónicos, incluidos los que no se envían. Por lo tanto, todos los mensajes se archivan.

## Pasar al nuevo BCC de correo electrónico {#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>El sistema de archivado de correo electrónico (BCC) cambió con Adobe Campaign 17.2 (compilación 8795). Si está actualizando desde una versión anterior y ya estaba utilizando las capacidades de archivado de correo electrónico, debe actualizarse manualmente al nuevo sistema de archivado de correo electrónico (BCC).

Para ello, realice los siguientes cambios en el archivo **`config-<instance>.xml`**:

1. Elimine el parámetro **zipPath** del nodo **`<archiving>`**.
1. Establezca el parámetro **compressionFormat** en **1** si es necesario.
1. Establezca el parámetro **archiveType** en **1**.

Una vez configurado el CCO de correo electrónico, asegúrese de seleccionar la opción **[!UICONTROL Email BCC]** en la Plantilla de envíos o el envío. Para obtener más información, consulte [esta sección](../../delivery/using/sending-messages.md#archiving-emails).

## Prácticas recomendadas de CCO de correo electrónico {#best-practices}

* **Buzón** de direcciones CCO: asegúrese de que tiene suficiente capacidad de recepción para archivar todos los correos electrónicos enviados por la MTA.
* **mutualización** de MTA: la función de archivado de CCO funciona en el nivel MTA. Permite el duplicado de todos los mensajes de correo electrónico enviados por el MTA. Como el MTA se puede mutualizar en varias instancias (dev, test o prod, por ejemplo) o incluso en varios clientes (en un entorno de intermediaria), la configuración de esta función afecta a la seguridad:

   * Si comparte un MTA con varios clientes y uno de ellos tiene activada esta opción, este cliente tendrá acceso a todos los correos electrónicos de los demás clientes que comparten el mismo MTA. Para evitar esta situación, utilice un MTA diferente para cada cliente.
   * Si utiliza el mismo MTA en varias instancias (desarrollo, prueba, prod) para un único cliente, la opción dataLogPath duplicará los mensajes enviados desde las tres instancias.

* **Correos electrónicos por conexión**: El archivo de correo electrónico de CCO funciona al abrir una conexión e intentar enviar todos los correos electrónicos a través de esa conexión. Adobe recomienda comprobar con el contacto técnico interno el número de correos electrónicos aceptados en una conexión determinada. El aumento de este número puede tener un impacto bueno en el rendimiento de CCO.
* **IPs** de envío de CCO: actualmente, los mensajes de correo electrónico CCO no se envían a través de los proxies MTA normales. En su lugar, se abre una conexión directa desde el servidor MTA al servidor de correo electrónico de destino. Esto significa que es posible que necesite agregar direcciones IP adicionales a la lista de permitidos de la red, según la configuración del servidor de correo electrónico.

