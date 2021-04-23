---
solution: Campaign Classic
product: campaign
title: Estados de entrega
description: Obtenga más información sobre los estados disponibles en su panel de entregas.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
translation-type: ht
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: ht
source-wordcount: '629'
ht-degree: 100%

---

# Estados de entrega {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

Una vez que realizada una entrega, el panel de entregas muestra un estado que le permite monitorizar si la entrega se ha realizado correctamente. Los estados posibles se detallan en la sección siguiente.

![](assets/delivery-status.png)

Para obtener más información sobre los diferentes errores de entrega que pueden surgir y cómo resolverlos, consulte [esta página](../../delivery/using/understanding-delivery-failures.md).

**Temas relacionados:**

* [Panel de entregas](../../delivery/using/delivery-dashboard.md)
* [Solución de problemas de entregas](../../delivery/using/delivery-troubleshooting.md)
* [Acerca de la capacidad de la entrega](../../delivery/using/about-deliverability.md)

## Lista de estados de entrega {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Estado<br /> </th> 
   <th> Definiciones y soluciones<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Enviado<br /> </td> 
   <td> La entrega se envió correctamente al proveedor de mensajes (pero es posible que el destinatario no lo haya recibido).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorado<br /> </td> 
   <td> No se realizó la entrega al destinatario debido a un error con su dirección. Se lo incluyó en una lista de bloqueados o en cuarentena, no se proporcionó o está duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Error<br /> </td> 
   <td> La entrega no ha podido llegar al destinatario debido a una dirección no válida o a que la bandeja de entrada estaba llena. También puede estar relacionado con un problema con los bloques de personalización, ya que pueden generar errores cuando los esquemas no coinciden con la asignación de entregas. Consulte <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">Comprensión de los errores de entrega</a><br /> </td> 
  </tr>
  <tr> 
   <td> Pendiente<br /> </td> 
   <td> la entrega está listo para enviarse y se va a procesar mediante el servidor de entrega (MTA). Consulte <a href="#pending-status" target="_blank">Estado pendiente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> No aplicable<br /> </td> 
   <td> El servidor (MTA) tuvo en cuenta la entrega, pero no lo procesó.<br /> </td> 
  </tr>  
  <tr> 
   <td> Entrega cancelada<br /> </td> 
   <td> Un operador ha cancelado la entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> El proveedor de servicios lo tiene en cuenta<br /> </td> 
   <td> El proveedor de servicios SMS recibió el envío.<br /> En el caso de instalaciones hospedadas o híbridas, si se ha actualizado al servidor de correo <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank"> </a>mejorado, el mensaje se ha retransmitido correctamente desde Campaign al servidor de correo mejorado.</td> 
  </tr> 
  <tr> 
   <td> Se ha recibido en dispositivos móviles<br /> </td> 
   <td> El destinatario recibió el SMS en su dispositivo móvil.<br /> </td> 
  </tr>
  <tr> 
   <td> Enviado al proveedor de servicios<br /> </td> 
   <td> Se realizó la entrega al proveedor de servicios SMS, pero no se ha recibido todavía.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Preparado<br /> </td> 
   <td> El estado de intermediario se utiliza solo para conectores externos como el canal móvil. Sigue al estado “Pendiente” y es el conector externo que determina el estado siguiente.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para aprender a optimizar la entrega de los correos electrónicos de Adobe Campaign, consulte [esta sección](../../delivery/using/about-deliverability.md). Para profundizar en la capacidad de entrega, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).

## Estado pendiente {#pending-status}

Después de confirmar la entrega, puede ver que el estado del mismo es **[!UICONTROL Pending]**. Este estado significa que el proceso de ejecución está esperando a que estén disponibles algunos recursos.

El estado **[!UICONTROL Pending]** puede significar en primer lugar que la entrega se ha programado y está pendiente hasta la fecha determinada. Para obtener más información, consulte la sección [Programación de entregas](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Si la entrega no se realiza y su estado sigue siendo **[!UICONTROL Pending]**, puede deberse a uno de los siguientes motivos:

* Puede que el MTA (Agente de Transferencia de Mensajes), que ejecuta módulos y procesos en el servidor de entrega y que administra la entrega por correo electrónico, no se haya iniciado o que sea necesario reiniciarlo.

   Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

   >[!NOTE]
   >
   >Esta operación se puede realizar con un modelo de alojamiento **on-premise** o **híbrido** con acceso al servidor de Campaign (consulte [modelos de alojamiento](../../installation/using/hosting-models.md)).

   1. Compruebe que los módulos `mta@<instance>` se inicien en los servidores MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Si el MTA no aparece en la lista, inícielo con el siguiente comando:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Sustituya `<INSTANCENAME>` con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La entrega puede estar utilizando una afinidad no configurada en el servidor remitente.

   En este caso, compruebe la configuración de la administración de tráfico (afinidad de IP) y utilice el campo **[!UICONTROL Managing affinities with IP addresses]** para relacionar las entregas al MTA que administra la afinidad. Para obtener más información sobre las afinidades, consulte [esta sección](../../installation/using/configure-delivery-settings.md).

* Cuando se ejecutan demasiadas campañas, el estado de la entrega permanece en estado Pendiente.

   El límite de campañas simultáneas se define en la opción **[!UICONTROL NmsOperation_LimitConcurrency]**. El valor predeterminado es 10.

   Obtenga más información sobre las opciones en [esta página](../../installation/using/configuring-campaign-options.md).


**Temas relacionados:**

* [Registros de entrega e historial](#delivery-logs-and-history)
* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Tipos y motivos de errores de entrega](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
