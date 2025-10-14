---
product: campaign
title: Archivado de correo electrónico
description: Archivado de correo electrónico
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 3%

---

# Configuración del CCO del correo electrónico {#email-archiving}



Puede configurar Adobe Campaign para que conserve una copia de los correos electrónicos enviados desde su plataforma.

Sin embargo, Adobe Campaign no administra los archivos archivados. Esto permite enviar los mensajes que elija a una dirección específica, desde la que se pueden procesar y archivar mediante un sistema externo.

Para ello, los archivos .eml correspondientes a los correos electrónicos enviados se transfieren a un servidor remoto, como un servidor de correo electrónico SMTP. El destino de archivado es una dirección de correo electrónico CCO (invisible para los destinatarios de la entrega) que debe especificar.

## Recomendaciones y limitaciones {#recommendations-and-limitations}

* La capacidad CCO del correo electrónico es opcional. Compruebe el acuerdo de licencia.
* Para **arquitecturas hospedadas e híbridas**, póngase en contacto con su administrador de cuentas para activarlo. La dirección de correo electrónico CCO que elija se debe proporcionar al equipo de Adobe, que la configurará por usted.
* Para **instalaciones in situ**, siga las directrices que se indican a continuación para activarlo; consulte las secciones [Activación del CCO del correo electrónico (local)](#activating-email-archiving--on-premise-) y [Configuración de la dirección de correo electrónico del CCO (local)](#configuring-the-bcc-email-address--on-premise-).
* Solo puede utilizar una dirección de correo electrónico CCO.
* Una vez configurado el correo electrónico CCO, asegúrese de que la función esté habilitada en la plantilla de envíos o en la entrega a través de la opción **[!UICONTROL Email BCC]**. consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}.
* Solo se tienen en cuenta los correos electrónicos enviados correctamente, no las devoluciones.
* El sistema de archivado de correo electrónico cambió con Adobe Campaign 17.2 (compilación 8795). Si ya estaba utilizando el archivado de correo electrónico, debe actualizar manualmente al nuevo sistema de CCO de correo electrónico. Para obtener más información sobre esto, consulte la sección [Traslado al nuevo CCO de correo electrónico](#updated-email-archiving-system--bcc-).

## Activación del CCO del correo electrónico (local) {#activating-email-archiving--on-premise-}

[!BADGE On-Premise e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"}


Para activar el archivado de correo electrónico CCO cuando Adobe Campaign está instalado in situ, siga los pasos a continuación.

### Carpeta local {#local-folder}

Para habilitar la transferencia de correos electrónicos enviados a una dirección de correo electrónico de CCO, las copias sin procesar exactas de los correos electrónicos enviados deben guardarse primero como archivos .eml en una carpeta local.

La ruta de la carpeta local debe especificarse en el archivo **config-`<instance>`.xml**, desde la configuración. Por ejemplo:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Es responsabilidad del equipo que implementa el proyecto garantizar que la configuración de seguridad permita el acceso a la carpeta definida a través de los parámetros **dataLogPath**.

La ruta completa es la siguiente: **`<datalogpath>  YYYY-MM-DDHHh`**. La fecha y la hora se establecen según el reloj del servidor MTA (UTC). Por ejemplo:

```
C:\emails\2018-12-02\13h
```

El nombre del archivo es **`<deliveryid>-<broadlogid>.eml`** cuando el estado de los correos electrónicos no es **[!UICONTROL Sent]**. Una vez que el estado haya cambiado a **[!UICONTROL Sent]**, el nombre de archivo se convierte en **`<deliveryid>-<broadlogid>-sent.eml`**. Por ejemplo:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>En una instancia intermediaria, el directorio de los correos electrónicos de CCO se encuentra en el servidor intermediario.
>
>deliveryID y broadlogID provienen del servidor intermediario cuando no se envía el estado de los correos electrónicos. Una vez que el estado ha cambiado a **[!UICONTROL Sent]**, estos ID provienen del servidor de marketing.

### Parámetros {#parameters}

Una vez definida la ruta de la carpeta local, agregue y edite los siguientes elementos como desee en el archivo **config-`<instance name>.xml`**. A continuación se muestran los valores predeterminados:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato utilizado al comprimir los archivos .eml. Los valores posibles son estos:

  **0**: sin compresión (valor predeterminado)

  **1**: compresión (formato .zip)

* **compressBatchSize**: número de archivos .eml agregados a un archivo (archivo .zip).


* **archivingType**: estrategia de archivado para usar. El único valor posible es **1**. Las copias sin procesar de los correos electrónicos enviados se guardan en formato .eml en la carpeta **dataLogPath** y se envían a la dirección de correo electrónico de la CCO a través de SMTP. Una vez que las copias de correo electrónico se envían a la dirección de CCO, el nombre del archivo de almacenamiento se convierte en **`<deliveryid>-<broadlogid>-sent-archived.eml`** y el archivo se mueve a la carpeta **dataLogPath/archived**. La ruta del archivo de correo electrónico archivado enviado y CCO es entonces **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: número de días que se conservan los archivos .eml para el archivado. Tras ese retraso, se moverán automáticamente a la carpeta **dataLogPath/archived** para su compresión. De forma predeterminada, los archivos .eml caducan al cabo de dos días.
* **purgeArchivesDelay**: el número de días que se guardan los archivos en la carpeta **dataLogPath/`<archives>`**. Después de ese período, se eliminan de forma permanente. La depuración comienza cuando se inicia el MTA. De forma predeterminada, se realiza cada siete días.
* **pollDelay**: frecuencia de comprobación (en segundos) de nuevos correos electrónicos entrantes enviados a la carpeta **dataLogPath**. Por ejemplo, si este parámetro se establece en 60, significa que cada minuto, el proceso de archivado pasa por los archivos .eml dentro de las carpetas **dataLogPath/`<date and time>`**, aplica una depuración si es necesario y envía copias de correo electrónico a la dirección de CCO o comprime los archivos archivados cuando sea necesario.
* **acquisitionLimit**: número de archivos .eml procesados a la vez antes de que el proceso de archivado se aplique de nuevo según el parámetro **pollDelay**. Por ejemplo, si establece el parámetro **acquisitionLimit** en 100 mientras que el parámetro **pollDelay** está establecido en 60, se procesarán 100 archivos .eml por minuto.
* **smtpNbConnection**: número de conexiones SMTP a la dirección de correo electrónico CCO.

Asegúrese de ajustar estos parámetros según el rendimiento de envío de correo electrónico. Por ejemplo, en una configuración en la que el MTA envía 30 000 correos electrónicos por hora, puede establecer el parámetro **pollDelay** en 600, el parámetro **acquisitionLimit** en 5000 y el parámetro **smtpNbConnection** en 2. Esto significa que, con 2 conexiones SMTP, se envían 5000 correos electrónicos a la dirección de CCO cada 10 minutos.

## Configuración de la dirección de correo electrónico CCO (local) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE On-Premise e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"}


>[!IMPORTANT]
>
>Por motivos de privacidad, los correos electrónicos CCO deben procesarse mediante un sistema de archivado capaz de almacenar información de identificación personal (PII) de forma segura.

En el archivo **config-`<instance name>.xml`**, utilice los siguientes parámetros para definir el servidor de correo electrónico SMTP al que se transferirán los archivos almacenados:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archivando destino de destino
* **smtpEnableTLS**: usando una conexión SMTP segura (protocolo TLS/SSL)
* **smtpRelayAddress**: dirección de retransmisión para usar
* **smtpRelayPort**: puerto de retransmisión para usar

>[!NOTE]
>
>Si utiliza una retransmisión SMTP, los cambios realizados en los correos electrónicos por la retransmisión no se tienen en cuenta en el proceso de archivado.
>
>Además, la retransmisión asigna un estado **[!UICONTROL Sent]** a todos los correos electrónicos, incluidos los que no se envían. Por lo tanto, todos los mensajes se archivan.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## Prácticas recomendadas para CCO de correo electrónico {#best-practices}

* **Buzón de direcciones CCO**: asegúrese de que tenga suficiente capacidad de recepción para archivar todos los correos electrónicos enviados por el MTA.
* **Agrupación de MTA**: la característica de archivado de CCO funciona en el nivel de MTA. Permite duplicar todos los correos electrónicos enviados por el MTA. Como el MTA se puede agrupar en varias instancias (desarrollo, prueba o producción por ejemplo) o incluso en varios clientes (en un entorno de intermediario), la configuración de esta función afecta a la seguridad:

   * Si comparte un servidor de correo con varios clientes y uno de ellos tiene esta opción activada, este cliente accederá a todos los correos electrónicos de los demás clientes que compartan el mismo servidor de correo. Para evitar una situación de este tipo, utilice un servidor de correo diferente para cada cliente.
   * Si utiliza el mismo MTA en varias instancias (desarrollo, prueba, prod) para un solo cliente, los mensajes enviados desde las tres instancias se duplicarán mediante la opción dataLogPath.

* **Correos electrónicos por conexión**: el archivado de correo electrónico CCO funciona abriendo una conexión e intentando enviar todos los mensajes de correo electrónico a través de esa conexión. Adobe recomienda consultar con su contacto técnico interno el número de correos electrónicos aceptados en una conexión determinada. El aumento de este número puede tener un gran impacto en el rendimiento de las CCO.
* **IP de envío de CCO**: actualmente, los correos electrónicos de CCO no se envían a través de los proxies de MTA normales. En su lugar, se abre una conexión directa desde el servidor MTA al servidor de correo electrónico de destino. Esto significa que es posible que tenga que agregar direcciones IP adicionales a la lista de permitidos de la red, según la configuración del servidor de correo electrónico.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->