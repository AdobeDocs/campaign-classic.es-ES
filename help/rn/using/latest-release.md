---
solution: Campaign Classic
product: campaign
title: Última versión
description: Última versión de Campaign Classic Notas
feature: Información general
role: Profesional empresarial
level: Principiante
translation-type: tm+mt
source-git-commit: d1796224df95663c39fa5975e88c03a923c94878
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 98%

---


# Última versión{#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión Candidate de Campaign Classic**.

Para la versión Gold Standard de Campaign Classic (versión más reciente de GA), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versión 21.1.1 - Compilación 9277 {#release-21-1-1-build-9277}

_22 de febrero de 2021_

**Mejoras de seguridad**

* Se ha mejorado el mecanismo de autenticación de la consola para optimizar la seguridad. (NEO-26944)
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-28532)

**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:

* La versión 49 de la API de Salesforce ahora se admite al usar la cuenta externa de CRM de Salesforce.

**Funciones obsoletas**

El informe de **monitorización de la capacidad de envío técnico** está obsoleto.

Obtenga más información en la página [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md).

**Mejoras**

**El servicio de comentarios de correo electrónico (EFS)** es un servicio escalable que captura los comentarios del servidor de correo mejorado directamente, lo que mejora la precisión de la creación de informes. Esta capacidad se presenta como una versión beta privada y estará disponible de forma progresiva para todos los clientes en futuras versiones.

* Ahora se capturan todas las categorías de comentarios para obtener una creación de informes completa y precisa.
* El cálculo del indicador Entregado ahora se basa en los comentarios en tiempo real del servidor de correo mejorado para mejorar la precisión y la reactividad.
* EFS soluciona el problema de los retrasos con la creación de informes de devoluciones síncronas suaves.

Para obtener más información, consulte la [documentación detallada](../../delivery/using/sending-with-enhanced-mta.md#efs).
Si desea participar en esta versión beta privada, rellene este [formulario](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) y le responderemos.

**Otros cambios**

* La velocidad de transferencia se ha mejorado para registros de seguimiento grandes mediante compresión.
* El mapa de calor del flujo de trabajo se ha mejorado para evitar tiempos de espera al ejecutar flujos de trabajo con varias actividades. (NEO-27423).
* Se ha corregido un problema que podía permitir que se presentara una oferta aunque se pasara la fecha de finalización. Ahora, Campaign Classic tiene en cuenta la marca de tiempo completa de la fecha de finalización en lugar de solo la fecha. (NEO-27590)
* El vínculo de Google+ se ha eliminado del bloque de personalización **Vínculos compartidos de redes sociales**.
* Se ha corregido un problema tras la implementación de una corrección de errores en la última versión. Se ha añadido una comprobación en el nombre del host al conectarse mediante SSL/TLS, lo que provocó que los envíos SMS dieran error. La verificación del nombre de host se ha desactivado para la mayoría de los protocolos, como POP3, SMS y HTTP con proxy, y la comprobación del certificado de la cuenta externa SMS se ha mejorado con tres valores (NEO-29581). [Obtenga más información](../../delivery/using/sms-protocol.md#skip-tls)

**Parches**

* Se ha corregido un problema que impedía que las combinaciones de teclas Tab, Enter y Escape funcionaran en la nueva pantalla de inicio de sesión.
* Se ha corregido un problema de actualización que provocaba que el nombre de un flujo de trabajo recién creado se reemplazara por el valor predeterminado después de guardar (NEO-26106).
* Se ha corregido un problema que se producía al ejecutar flujos de trabajo en el que se agregaba un nuevo campo como parte de una actividad de **Enriquecimiento** anterior a una actividad de **Envío** mediante una asignación de destino de **archivo externo**: se han agregado campos no deseados a la asignación de destino de **archivo externo**. (NEO-27687)
* Se ha corregido un problema que provocaba que algunos caracteres del código fuente se alteraran al volver a abrir una aplicación web previamente creada y guardada. (NEO-27597)
* Se ha corregido un problema que se podía producir al actualizar a una compilación, incluido el nuevo mecanismo de firma para el seguimiento de vínculos (desde la compilación 19.1.4 y la Campaign 20.2): cuando se asocian varias plantillas a un evento, la actualización puede hacer que se seleccione una plantilla incorrecta al enviar el mensaje transaccional. (NEO-28326)
* Se ha corregido un problema que provocaba que el servidor de correo dejara de responder y no pudiera procesar envíos a menos que se reiniciara. (NEO-27455)
* Se ha corregido un problema en la base de datos MSSQL relacionado con la administración de marcas de tiempo durante las operaciones de carga masiva de una columna de tipo datetime.
* Se ha corregido un problema de consulta del flujo de trabajo al usar las funciones xtk de Redshift. Los SubDays, SubSeconds, SubMinutes y SubHours ahora aceptan ambos tipos de marcas de tiempo de Redshift (NEO-24962).
* Se ha corregido un problema que mostraba un mensaje de error de secuencia de comandos al intentar la previsualización de un informe con acceso anónimo. (NEO-27081)
* Se ha corregido un problema que podía reducir el uso de memoria en el servidor al realizar el análisis del envío.
* Se ha corregido un problema que podía impedir que la instancia funcionara al intentar ejecutar consultas complejas específicas.
* Se ha corregido un problema que podía impedir que se ejecutara el flujo de trabajo técnico **Sincronización de páginas de Twitter**. (NEO-28634)
* Se ha corregido un problema que podía mostrar un mensaje de error relacionado con la función decryptPassword al intentar publicar en Twitter mediante la plantilla de envíos de **tuits (Twitter)**. (NEO-28216)
* Se ha corregido un problema que se producía al utilizar una actividad **JavaScript** para realizar una petición HTTP en un flujo de trabajo. Después de definir el número de puerto en el nombre del host, la llamada generaría el siguiente error (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Se ha corregido un problema que impedía que se enviaran nuevos envíos con personalización de datos de destino (NEO-30323).
* Se ha corregido un problema en el cual se producían varios bloqueos en la instancia de marketing que causaban archivos principales.
* Se ha corregido un problema que ocasionaba que el flujo de trabajo de **Seguimiento** diera el siguiente error (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Se ha corregido un problema que se producía al crear y guardar un envío en la pestaña **Segmentación y flujo de trabajo** de una campaña: la previsualización daría el siguiente error (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Se ha corregido un error que se producía al configurar una cuenta externa entre una instancia de marketing y una instancia de Adobe Campaign Standard o una instancia intermediaria de Campaign Classic y al utilizar la opción &quot;DisableFOH2=1&quot;. Cuando se utilizaba la opción &quot;DisableFOH2=1&quot; en la cuenta externa, las conexiones no se cerraban correctamente y se acumulaban, lo que daba como resultado el siguiente error (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Se ha corregido un error con SMS cuando se producían problemas de conexión entre el servidor y el proveedor. El elemento secundario del servidor de correo desactivaría automáticamente la conexión. Adobe Campaign Classic no intentaría conectarse a esta conexión con error mientras no se hubiera iniciado un nuevo elemento secundario.
