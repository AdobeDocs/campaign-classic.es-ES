---
solution: Campaign Classic
product: campaign
title: Solución de problemas de seguimiento
description: Esta sección proporciona preguntas comunes relacionadas con el seguimiento de la configuración y la implementación en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Seguimiento de la solución de problemas {#tracking-troubleshooting}

En esta sección, encontrará preguntas comunes relacionadas con el seguimiento de la configuración y la implementación en Adobe Campaign Classic.

## El flujo de trabajo de seguimiento está fallando {#tracking-workflow-failing}

El flujo de trabajo de seguimiento falla, ¿cómo puedo detectar las líneas dañadas en el archivo de seguimiento?

>[!NOTE]
>
>Disponible solo para Windows

El archivo de registro de seguimiento dañado.../nl6/var/&lt;nombre_instancia>/redir/log/0x0000 log puede detener el flujo de trabajo de seguimiento. Para detectar fácilmente las líneas dañadas y eliminarlas para reanudar el flujo de trabajo de seguimiento, puede utilizar los comandos siguientes.

### Sé en qué archivo se encuentra la línea dañada

En ese caso, las líneas dañadas se pueden encontrar en el archivo 0x0000000000A0000.log, pero el mismo proceso se puede aplicar a un conjunto de archivos, uno por uno.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

A continuación, puede detener el flujo de trabajo de seguimiento, eliminar las líneas dañadas y reiniciar el flujo de trabajo.

### No sé en qué archivo se encuentra la línea dañada

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
   >El retorno de carro se ha agregado antes que el agente de usuario para permitir una mejor lectura y no refleja una representación efectiva.

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
   >Se ha agregado un retorno de carro antes que Agente de usuario para permitir una mejor lectura y no refleja una representación efectiva.

A continuación, puede detener el flujo de trabajo de seguimiento, eliminar las líneas dañadas y reiniciar el flujo de trabajo.

## Los vínculos de seguimiento fallan intermitentemente {#tracking-links-fail-intermittently}

Al intentar acceder a los vínculos de seguimiento, aparece el siguiente mensaje:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. Acceda a la dirección URL &lt;redirect_server>/r/test y compruebe si la solicitud devolvió el número de compilación y el host local.

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

1. Compruebe manualmente si el archivo &lt;deliveryID>.xml existe en el equipo en .../nl6/var/&lt;nombre_de_instancia>/redir/url/&lt;AAAA> directorio (YYYY representa año de envío).

1. Compruebe manualmente si &lt;trackingUrlId> se encuentra en el archivo &lt;deliveryID>.xml.

1. Compruebe la existencia manual de un identificador de registroancha en el envío de entregaID relacionado.

1. Compruebe los permisos de &lt;deliveryID>.xml en .../nl6/var/&lt;nombre_instancia>/redir/url/year directory.

   Deben tener al menos 644 permisos para que Apache pueda leer las direcciones URL de seguimiento para redireccionar el vínculo solicitado.

## ¿Actualizando la opción NmsTracking_Pointer? {#updating-option}

Siga estos pasos al actualizar la opción NmsTracking_Pointer:

1. Detenga el flujo de trabajo de seguimiento.

1. Detenga el servicio trackinglogd.

1. Actualice la opción NmsTracking_Pointer al valor deseado.

1. Reinicie el servicio trackinglogd.

1. Reinicie el flujo de trabajo de seguimiento.

## El seguimiento no parece funcionar con algunos WebMail {#webmail}

Puede personalizar la fórmula de rastreo de clics y especificar una fórmula de seguimiento de Adobe Analytics personalizada.

Este tipo de personalización debe hacerse con precaución para evitar añadir caracteres de salto de línea adicionales. Todos los caracteres de alimentación de línea presentes fuera de la expresión de javascript estarán presentes en la fórmula final.

Este tipo de caracteres de línea extra en la URL de seguimiento dará lugar a problemas en algunos webMail (AOL, GMail, etc.).

**Primer ejemplo:**

* Sintaxis incorrecta

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* Sintaxis correcta

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

Para saber dónde está la alimentación de línea adicional, puede reemplazar la expresión de javascript por una CADENA de cadena fija.

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
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* Sintaxis correcta

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

Para saber dónde está la alimentación de línea adicional, puede reemplazar la expresión de javascript por una CADENA de cadena fija.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## La recuperación de registros de seguimiento es demasiado lenta {#slow-retrieval}

Cuando la instancia no recupera directamente registros de seguimiento sino de un servidor Adobe Campaign Classic distante, los registros se recuperan mediante la llamada SOAP GetTrackingLogs, que se define en el esquema remoteTracking.

Una opción del archivo serverConf.xml le permite establecer el número de registros que se recuperan a la vez mediante este método: logCountPerRequest.

El valor predeterminado de logCountPerRequest es 1000, por lo que en algún caso puede resultar demasiado pequeño. Los valores aceptados deben estar entre 0 y 10.000.

## No se pudieron vincular registros de seguimiento a destinatarios {#link-recipients}

En Adobe Campaign Classic, se supone que una asignación de destino es única en términos de esquema de destinatarios vs esquemas de logs de banda ancha / trackinglog.

![](assets/tracking-troubleshooting.png)

No es posible utilizar varios esquemas de objetivo con el mismo esquema de registro de seguimiento, ya que el flujo de trabajo de seguimiento no podrá conciliar los datos con la identificación de objetivo.

Si no desea utilizar la asignación de destino predeterminada con nms:destinatario, le recomendamos los siguientes métodos:

* Si desea utilizar la dimensión de segmentación personalizada, debe crear un esquema de WideLog/trackingLog personalizado con nms:Broadlog como plantilla (por ejemplo: nms:wideLogRcp, nms:wideLogSvc, etc.).

* Si desea utilizar OOB trackingLogRcp/wideLogRcp, la dimensión de segmentación debe ser nms:destinatario y la dimensión de filtrado puede ser un esquema personalizado.
