---
solution: Campaign Classic
product: campaign
title: Última versión
description: Última versión de Campaign Classic Notas
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Última versión{#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión Candidate de Campaign Classic**.

Para la versión Gold Standard de Campaign Classic (versión más reciente de GA), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versión 21.1.1: compilación 9277 {#release-21-1-1-build-9277}

_22 de febrero de 2021_

**Mejoras de seguridad**

* Se ha mejorado el mecanismo de autenticación de la consola para optimizar la seguridad. (NEO-26944)



* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-28532)




**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:

* La versión 49 de la API de Salesforce ahora es compatible al utilizar la cuenta externa de Salesforce CRM.

**Funciones obsoletas**

El informe **Technical Deliverability Monitoring** ya no se utiliza.

Obtenga más información en la página [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md).

**Mejoras**

**El servicio de comentarios de correo electrónico (EFS)**  es un servicio escalable que captura los comentarios del MTA mejorado directamente, lo que mejora la precisión de los informes. Esta capacidad se presenta como una versión beta privada y estará disponible de forma progresiva para todos los clientes en futuras versiones.

* Ahora se capturan todas las categorías de comentarios para obtener una creación de informes completa y precisa.
* El cálculo del indicador Entregado ahora se basa en los comentarios en tiempo real del MTA mejorado para mejorar la precisión y la reactividad.
* EFS soluciona el problema de los retrasos con la creación de informes de devoluciones en blanco sincrónicas.

Para obtener más información, consulte la [documentación detallada](../../delivery/using/sending-with-enhanced-mta.md#efs).
Si está interesado en participar en esta versión beta privada, rellene este [formulario](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) y se lo devolveremos.

**Otros cambios**

* La velocidad de transferencia se ha mejorado para los registros de seguimiento grandes mediante la compresión.
* El mapa de calor del flujo de trabajo se ha mejorado para evitar tiempos de espera al ejecutar flujos de trabajo con varias actividades. (NEO-27423).
* Se ha corregido un problema que podía permitir que se presentara una oferta incluso si se pasaba la fecha de finalización. Ahora, Campaign Classic tiene en cuenta la marca de tiempo completa de la fecha de finalización en lugar de solo la fecha. (NEO-27590)



* El vínculo de Google+ se ha eliminado del bloque personalizado **Social network sharing links** .
* Se ha corregido un problema tras la implementación de una corrección de errores en la última versión. Se agregó una comprobación en el nombre de host al conectarse con SSL/TLS, lo que provocó que los envíos SMS fallaran. La verificación del nombre de host se ha deshabilitado para la mayoría de protocolos, como POP3, SMS y HTTP con proxy, y la comprobación de certificado de la cuenta externa SMS se ha mejorado con tres valores (NEO-29581). [Obtenga más información](../../delivery/using/sms-protocol.md#skip-tls)

**Parches**

* Se ha corregido un problema que impedía que los métodos abreviados de teclado Tabulador, Entrar y Escape funcionaran en la nueva pantalla de inicio de sesión.
* Se ha corregido un problema de actualización que provocaba que el nombre de un flujo de trabajo recién creado se reemplazara por el valor predeterminado después de guardar (NEO-26106).
* Se ha corregido un problema que se producía al ejecutar flujos de trabajo en el que se agregaba un nuevo campo como parte de una actividad **Enrichment** anterior a una actividad **Delivery** mediante una asignación de destino **External file**: se agregaron campos no deseados a la asignación de destino **External file** . (NEO-27687)



* Se ha corregido un problema que provocaba que algunos caracteres del código fuente se alteraran al volver a abrir una aplicación web creada y guardada anteriormente. (NEO-27597)



* Se ha corregido un problema que se podía producir al actualizar a una compilación, incluido el nuevo mecanismo de firma para el seguimiento de vínculos (desde la versión 19.1.4 y Campaign 20.2): cuando se asocian varias plantillas a un evento, la actualización puede hacer que se seleccione la plantilla incorrecta al enviar el mensaje transaccional. (NEO-28326)



* Se ha corregido un problema que provocaba que el MTA dejara de responder y no pudiera procesar envíos a menos que se reiniciara. (NEO-27455)



* Se ha corregido un problema en la base de datos MSSQL relacionado con la administración de marcas de tiempo durante operaciones de carga masiva para una columna de tipo datetime.
* Se ha corregido un problema con la consulta de flujo de trabajo al utilizar las funciones xtk Redshift. Los SubDays, SubSeconds, SubMinutes y SubHours ahora aceptan ambos tipos de marca de tiempo Redshift (NEO-24962).
* Se ha corregido un problema que mostraba un mensaje de error de secuencia de comandos al intentar previsualizar un informe con acceso anónimo. (NEO-27081)



* Se ha corregido un problema que podía reducir el uso de memoria en el servidor al realizar el análisis de entrega.
* Se ha corregido un problema que podía impedir que la instancia funcionara al intentar ejecutar consultas complejas específicas.
* Se ha corregido un problema que podía impedir que se ejecutara el flujo de trabajo técnico **Sincronización de páginas de Twitter** . (NEO-28634)



* Se ha corregido un problema que podía mostrar un mensaje de error relacionado con la función decryptPassword al intentar publicar en Twitter mediante la plantilla de envío **Tweet (twitter)**. (NEO-28216)



* Se ha corregido un problema que se producía al utilizar una actividad **Javascript** para realizar una solicitud HTTP en un flujo de trabajo. Después de definir el número de puerto en el nombre del host, la llamada fallaría con el siguiente error (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Se ha corregido un problema que impedía que se enviaran nuevos envíos con personalización de datos de destino.
* Se ha corregido un problema por el cual se producían varios bloqueos en la instancia de marketing que causaban archivos principales.
* Se ha corregido un problema que provocaba que el flujo de trabajo **Tracking** fallara con el siguiente error (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Se ha corregido un problema que se producía al crear y guardar un envío en la pestaña **Targeting &amp; Workflow** de una campaña: la vista previa fallaría con el siguiente error (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Se ha corregido un error que se producía al configurar una cuenta externa entre una instancia de marketing y una instancia de Adobe Campaign Standard o una instancia de intermediario de Campaign Classic y al utilizar la opción &quot;DisableFOH2=1&quot;. Al utilizar la opción &quot;DisableFOH2=1&quot; en la cuenta externa, las conexiones no se cerraban correctamente y se acumulaban, lo que producía el siguiente error (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Se ha corregido un error con SMS cuando se producían problemas de conexión entre el servidor y el proveedor. El elemento secundario MTA deshabilitaría automáticamente la conexión. Adobe Campaign Classic no intentaría conectarse a esta conexión con error mientras no se hubiera iniciado un nuevo elemento secundario.
