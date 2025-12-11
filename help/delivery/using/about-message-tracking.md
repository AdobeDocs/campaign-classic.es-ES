---
product: campaign
title: Introducción al seguimiento
description: Obtenga más información sobre las directrices generales para el seguimiento en Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: ht
source-wordcount: '1267'
ht-degree: 100%

---

# Introducción al seguimiento de mensajes {#get-started-tracking}

>[!IMPORTANT]
>
>Para obtener **instrucciones generales de seguimiento** que se aplican tanto a Campaign Classic v7 como a Campaign v8, consulte la [documentación de seguimiento de mensajes de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [Configurar vínculos rastreados](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Configuración de las opciones de seguimiento de URL](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Seguimiento de vínculos personalizados ](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Acceso a los registros de seguimiento](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Seguimiento de pruebas](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Seguimiento de informes](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**Esta página solo documenta las características de seguimiento específicas de Campaign Classic v7**, principalmente para implementaciones híbridas y locales.

## Características de seguimiento

### Configuración del seguimiento {#configure-tracking}

Para **implementaciones híbridas/locales** de la versión 7 de Campaign Classic, debe configurar el seguimiento en el nivel de instancia antes de utilizarlo.

>[!NOTE]
>
>Para Managed Cloud Services de Campaign v8, la configuración de seguimiento la realiza Adobe.

**Principio de funcionamiento**

Antes de usar el seguimiento, primero debe configurarlo para su instancia. La configuración debe realizarse en los servidores de aplicaciones de Adobe Campaign y en los servidores web.

En Campaign, hay dos tipos de seguimiento:

* **Seguimiento web**: este modo permite rastrear las visitas a las páginas de tu sitio web
* **Seguimiento de mensajes**: este modo permite rastrear los envíos de mensajes y el comportamiento de los destinatarios

El modo de seguimiento se selecciona durante la instalación. Para instalaciones locales, la configuración de seguimiento debe definirse en el nivel de instancia. [Obtenga más información](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de seguimiento**

Para configurar el seguimiento, la instancia debe declararse y registrarse en los servidores de seguimiento. El servidor de seguimiento se utiliza para registrar y recuperar información sobre las direcciones URL en las que hacen clic los destinatarios.

Para instalaciones locales, el servidor de seguimiento suele ser un servidor web que ejecuta la aplicación web de Adobe Campaign. La URL del servidor de seguimiento debe definirse en la configuración de la instancia. [Obtenga más información](../../installation/using/deploying-an-instance.md#tracking-server)

**Guardado del seguimiento**

Una vez configurado el seguimiento y completadas las direcciones URL, se debe registrar el servidor de seguimiento. El registro permite a Adobe Campaign guardar información de seguimiento y proporcionar informes y estadísticas sobre las actividades rastreadas.

Para instalaciones locales, la información de seguimiento se almacena en la base de datos y se recupera a través de flujos de trabajo técnicos. El flujo de trabajo técnico de **seguimiento** procesa y almacena los datos de seguimiento recopilados del servidor de redirección. [Más información](../../installation/using/deploying-an-instance.md#saving-tracking)

### Seguimiento de aplicaciones web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**El seguimiento de aplicaciones web es específico de la versión 7 de Campaign Classic** y no está disponible en la versión 8 de Campaign.

**Seguimiento de una aplicación web**

También puede rastrear y medir visitas en páginas de aplicación web con etiquetas de seguimiento. Esta funcionalidad se puede utilizar para todos los tipos de aplicaciones web, como formularios y páginas de destino. [Obtenga más información](../../web/using/tracking-a-web-application.md)

**Exclusión del seguimiento de aplicaciones web**

La exclusión del seguimiento de aplicaciones web le permite detener el seguimiento de los comportamientos web de los usuarios finales que excluyen el seguimiento de comportamiento. Puede incluir la capacidad de mostrar un banner en aplicaciones web o páginas de destino para permitir que los usuarios puedan excluirse. [Obtenga más información](../../web/using/web-application-tracking-opt-out.md)

## Solución de problemas de seguimiento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Las siguientes sugerencias para la solución de problemas se aplican a **implementaciones híbridas/locales de Campaign Classic v7**. Parte de la información también se puede aplicar a las implementaciones locales de Campaign v8. Para Managed Cloud Services de Campaign v8, póngase en contacto con su representante de Adobe para obtener ayuda.

Para ver los pasos básicos de solución de problemas de seguimiento en Campaign v8, consulte [Seguimiento de solución de problemas en la documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Comprobaciones básicas {#basic-checks}

**Compruebe que el proceso trackinglogd se está ejecutando**

Este proceso lee la memoria compartida del IIS/servidor web y escribe los registros de redirección.

Puede acceder a ella desde la página principal seleccionando la pestaña Monitorización en la instancia. También puede ejecutar el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver pdump`

Si el proceso trackinglogd no aparece en la lista, inícielo con el siguiente comando en la instancia: `<user>@<instance>:~$ nlserver start trackinglogd`

**Compruebe que el flujo de trabajo técnico de seguimiento se ha estado ejecutando recientemente**

Puede localizar el flujo de trabajo técnico de seguimiento en las carpetas Administración > Producción > Flujos de trabajo técnicos.

### Solución de problemas avanzada {#advanced-troubleshooting}

+++El flujo de trabajo de seguimiento da errores

>[!NOTE]
>
>Disponible solo para Windows

El archivo de registro de seguimiento dañado .../nl6/var/&lt;nombre_instancia>/redir/log/0x0000 log puede detener el flujo de trabajo de seguimiento. Para detectar fácilmente las líneas dañadas y eliminarlas para reanudar el flujo de trabajo de seguimiento, puede utilizar los comandos siguientes.

**Sé en qué archivo se encuentra la línea dañada**

En ese caso, las líneas dañadas se pueden encontrar en el archivo 0x00000000000A0000.log, pero el mismo proceso se puede aplicar a un conjunto de archivos, uno por uno.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

A continuación, puede parar el flujo de trabajo de seguimiento, eliminar las líneas dañadas y reiniciar el flujo de trabajo.

**No sé en qué archivo se encuentra la línea dañada**

1. utilice la siguiente línea de comandos para proteger todos los archivos de seguimiento.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. El comando lista todas las líneas dañadas. Por ejemplo:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >El retorno de carro se ha añadido antes del agente de usuario para permitir una mejor lectura y no refleja una representación efectiva.

1. Ejecute un comando grep para buscar el archivo correspondiente.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Busque el registro defectuoso con el nombre de archivo y el número de línea. Por ejemplo:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Se ha añadido un retorno de carro antes del agente de usuario para permitir una mejor lectura y no refleja una representación efectiva.

A continuación, puede parar el flujo de trabajo de seguimiento, eliminar las líneas dañadas y reiniciar el flujo de trabajo.

+++

+++Los vínculos de seguimiento dan error intermitentemente

Al intentar acceder a los vínculos de seguimiento, aparece el siguiente mensaje:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Acceda a la dirección URL &lt;redirection_server>/r/test y compruebe si la solicitud devolvió el número de compilación y el host local.

1. Compruebe la configuración de spareServer en el archivo serverConf.xml para el servidor de seguimiento. Esta configuración debe estar en modo de redirección.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Compruebe manualmente si el archivo &lt;deliveryID>.xml existe en el equipo en el directorio .../nl6/var/&lt;nombre_instancia>/redir/url/&lt;YYYY> (YYYY representa el año de envío).

1. Compruebe manualmente si &lt;trackingUrlId> se encuentra en el archivo &lt;deliveryID>.xml.

1. Compruebe la existencia manual de un ID de registro de banda ancha en el envío de deliveryID relacionado.

1. Compruebe los permisos de &lt;deliveryID>.xml en el directorio .../nl6/var/&lt;nombre_instancia>/redir/url/year.

   Deben tener al menos 644 permisos para que Apache pueda leer las direcciones URL de seguimiento para redireccionar el vínculo solicitado.

+++

+++Actualizando la opción NmsTracking_Pointer

Siga estos pasos al actualizar la opción NmsTracking_Pointer:

1. Pare el flujo de trabajo de seguimiento.

1. Pare el servicio trackinglogd.

1. Actualice la opción NmsTracking_Pointer al valor deseado.

1. Reinicie el servicio trackinglogd.

1. Reinicie el flujo de trabajo de seguimiento.

+++

+++El seguimiento no funciona con algunos WebMail

Puede personalizar la fórmula de rastreo de clics y especificar una fórmula de seguimiento de Adobe Analytics personalizada.

Este tipo de personalización debe hacerse con precaución para evitar añadir caracteres de salto de línea adicionales. Todos los caracteres de salto de línea presentes fuera de la expresión de JavaScript estarán presentes en la fórmula final.

Este tipo de caracteres de salto de línea adicionales en la URL de seguimiento dará lugar a problemas en algunos webMail (AOL, GMail, etc.).

**Primer ejemplo:**

* Sintaxis incorrecta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Sintaxis correcta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Para saber dónde está el salto de línea adicional, puede reemplazar la expresión de JavaScript por una CADENA de cadena fija.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Segundo ejemplo**

* Sintaxis incorrecta

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Sintaxis correcta

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Para saber dónde está el salto de línea adicional, puede reemplazar la expresión de JavaScript por una CADENA de cadena fija.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++La recuperación de registros de seguimiento es demasiado lenta

Cuando la instancia no recupera directamente registros de seguimiento, sino de un servidor Adobe Campaign Classic distante, los registros se recuperan mediante la llamada SOAP GetTrackingLogs, que se define en el esquema remoteTracking.

Una opción del archivo serverConf.xml le permite establecer el número de registros que se recuperan a la vez mediante este método: logCountPerRequest.

El valor predeterminado de logCountPerRequest es 1000, por lo que en algún caso puede resultar demasiado pequeño. Los valores aceptados deben estar entre 0 y 10 000.

+++

+++No se han podido vincular registros de seguimiento a destinatarios

En Adobe Campaign Classic, se supone que una asignación de destino es única en términos de esquema de destinatarios frente a esquemas de registros de banda ancha/seguimiento.

![](assets/tracking-troubleshooting.png)

No es posible utilizar varios esquemas de segmentación con el mismo esquema de registro de seguimiento, ya que el flujo de trabajo de seguimiento no podrá reconciliar los datos con el ID de segmentación.

Si no desea utilizar la asignación de destinatario predeterminada con nms:recipient, le recomendamos los siguientes métodos:

* Si desea utilizar la dimensión de segmentación personalizada, debe crear un esquema de broadLog/trackingLog personalizado con nms::broadlog como plantilla (por ejemplo: nms:broadLogRcp, nms:broadLogSvc, etc.).

* Si desea utilizar OOB trackingLogRcp/broadLogRcp, la dimensión de segmentación debe ser nms::recipient y la dimensión de filtrado puede ser un esquema personalizado.

+++
