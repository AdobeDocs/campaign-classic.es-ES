---
solution: Campaign Classic
product: campaign
title: Cálculo de indicador
description: Cálculo de indicador
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '2972'
ht-degree: 100%

---

# Cálculo de indicador {#indicator-calculation}

## Actividades del usuario {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aperturas<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Suma de todos los @totalClicks con una clave principal de URL igual a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Suma de todos los @totalClicks con un tipo de URL que equivale a “clic de correo electrónico”.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transacciones<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Suma de todos los @totalClicks con un tipo de URL igual a “Transacción”.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Este informe se basa en la tabla **[!UICONTROL Consolidated tracking]** (nms:trackingStats). Esta tabla de acumulados se utiliza por motivos de rendimiento al mostrar los informes, en lugar de la tabla **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp), y no se calcula en tiempo real. La tabla se genera unos minutos después de recuperar los “logs” de seguimiento. Si los indicadores están actualizados, los resultados son los mismos que para los indicadores del informe **indicadores de seguimiento.** El indicador @totalclicks expresa el número total de clics durante un periodo de 5 minutos.

## Rechazos y no entregables {#non-deliverables-and-bounces-1}

**Desglose por tipo de error**

Este informe se basa en la tabla **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número total de mensajes procesados<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Suma de mensajes con un estado igual a “Listo”, “Enviado” o “Fallido”.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Usuario desconocido<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Usuario desconocido”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inaccesible <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Inaccesible”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rechazado<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Rechazado”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio inválido<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Dominio inválido”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Cuenta deshabilitada<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Cuenta deshabilitada”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Bandeja de entrada llena<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Recuento de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “Bandeja de entrada llena”.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Errores<br /> </td> 
   <td> @value<br /> </td> 
   <td> Número de mensajes fallidos para este tipo de error.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="Valor del tipo de error")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contribución<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de errores de este tipo comparado con el número total de mensajes de error.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de errores de este tipo comparado con el número total de mensajes procesados.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Desglose por dominio**

La segunda parte del informe detalla el desglose de los mensajes fallidos por dominio de Internet, a diferencia del tipo de error. La fórmula vinculada al indicador de **error** (@value) en este caso es: Count(@status=2 y @domain=&quot;Valor del nombre de dominio&quot;), es decir, un recuento de todos los mensajes con un estado fallido para este dominio.

## Navegadores {#browsers-1}

Este informe se basa en la tabla **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Estadísticas globales**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitantes<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Número total de destinatarios objetivo para este navegador que hicieron clic en una entrega al menos una vez.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Vistas de la página<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Número total de clics en los vínculos de la entrega utilizando este navegador, para todas las entregas.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de uso<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de visitantes para este navegador comparado con el número total de visitantes.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Estadísticas por navegador**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasa de uso<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Porcentaje del número de visitantes por día que usan este explorador comparados con el número de visitantes medidos en el día con la mayor cantidad de visitas.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa global<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de visitantes para esta versión comparados con el número total de visitantes contabilizados en todos los navegadores.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Peso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de visitantes para esta versión comparados con el número total de visitantes que utilizan este explorador.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Difusión en redes sociales {#sharing-to-social-networks-1}

Este informe se basa en las tablas **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) y **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número de mensajes que desea enviar<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Número total de mensajes procesados durante el análisis de entregas.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Número de envíos correctos<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensajes procesados correctamente <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Correo electrónico<br /> </td> 
   <td> @email<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “correo electrónico”.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “facebook”.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “twitter”.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “delicious”.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “digg”.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “google”.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Suma de todos los @totalClicks para los que la categoría URL es igual a “linkedin”.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Difusiones**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Número de difusiones<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Número total de mensajes compartidos en esta red social.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valor del tipo de red social",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Porcentaje del número de difusiones en esta red social en comparación con el número total de difusiones.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de difusión<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Número de difusiones en esta red en comparación con el número de mensajes que se van a enviar.<br /> </td> 
   <td> @forward/@totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Aperturas**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Cantidad de aperturas <br /> </td> 
   <td> @open<br /> </td> 
   <td> Número total de líneas de seguimiento en la tabla de seguimiento web.<br /> </td> 
   <td> Recuento<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Porcentaje del número de aperturas de esta red social en comparación con el número total de aperturas.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de aperturas<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Número de aperturas en esta red social en comparación con el número total de mensajes que se van a enviar.<br /> </td> 
   <td> @open/@totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Estadísticas de actividades de difusión {#statistics-on-sharing-activities-1}

Este informe se basa en las tablas **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) y **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nuevos contactos<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Recuento de los visitantes vinculados a un destinatario.<br /> </td> 
   <td> Fórmula: count(@id)<br /> Filter: @Recipi-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperturas<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Recuento de @ids con un tipo de dirección URL igual a “Abierta”<br /> </td> 
   <td> count(Iif([url/@type]=2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Difusiones<br /> </td> 
   <td> @shared<br /> </td> 
   <td> Categoría URL incluida en 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'<br /> Count of all @totalClicks con una categoría de URL que es igual a "email", "facebook", "twitter", "delicious", "digg", "google" o "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (“correo electrónico”, “facebook”, “twitter”, “delicious”, “digg”, “google”, “linkedin”), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sistemas operativos {#operating-systems-1}

Este informe se basa en la tabla **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Estadísticas globales**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitantes<br /> </td> 
   <td> @totalVisitors/@days<br /> </td> 
   <td> Promedio diario del número total de destinatarios objetivo por el sistema operativo que hicieron clic en una entrega al menos una vez.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Páginas visitadas<br /> </td> 
   <td> @totalPages/@days<br /> </td> 
   <td> Promedio diario del número total de clics en los vínculos de envíos por sistema operativo para todas las entregas.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de uso<br /> </td> 
   <td> -<br /> </td> 
   <td> Desglose de visitantes por sistema operativo comparado con la cantidad total de visitantes.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Estadísticas por sistema operativo**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasa de uso<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Porcentaje del número de visitantes por día en este sistema operativo comparados con el número de visitantes medidos en el día con la mayor cantidad de visitas.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa global<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de visitantes por versión comparados con el número total de visitantes en todos los sistemas operativos.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa relativa<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje de visitantes por versión comparados con el número total de visitantes que utiliza este sistema operativo.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Seguimiento de suscripciones {#subscription-tracking-1}

Este informe se basa en la tabla **[!UICONTROL Services]** (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Registrados<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Cantidad de personas registradas el día anterior.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Suscripciones<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> Recuento de suscripciones (@action = 1) el día anterior.<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Bajas<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> Recuento de bajas (action = 0) el día anterior.<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolución<br /> </td> 
   <td> -<br /> </td> 
   <td> Número de suscripciones menos número de bajas. La tasa se calcula en relación al número total de suscriptores.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fidelidad<br /> </td> 
   <td> -<br /> </td> 
   <td> Tasa de fidelidad del suscriptor para el periodo relacionado.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicadores de seguimiento {#tracking-indicators-1}

Este informe se basa en las tablas **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) y **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Mensajes que se van a enviar<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Recuento del número de broadLogs después del análisis del objetivo.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Correctos<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Recuento de mensajes para los que el campo “Dirección semilla” es igual a “No” y con un estado igual a “Tenido en cuenta por el proveedor de servicios”, “Enviado” o “Recibido en el teléfono móvil”.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperturas distintas sobre la población contactada<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolación del número de aperturas distintas de todos los correos electrónicos en función de la cantidad de aperturas distintas de correos electrónicos en formato html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Suma de aperturas sobre la población contactada<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolación del número total de aperturas para todos los correos electrónicos en función del número total de aperturas de correos electrónicos en formato html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics en el vínculo de baja de suscripción<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Recuento de todas las @ids con una categoría URL igual a “Exclusión”.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics en el vínculo a la página espejo<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Recuento de todas las @ids con una categoría URL igual a “Página espejo”.<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Estimación de reenvíos<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Diferencia entre la cantidad de personas distintas y la cantidad de destinatarios diferentes que hicieron clic en el correo electrónico al menos una vez.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Envíos<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Recuento de mensajes para los que el campo “Dirección semilla” es igual a “No” y con un estado igual a “Tenido en cuenta por el destinatario”, “Enviado” o “Recibido en el teléfono móvil”.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Reclamaciones<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Recuento de los mensajes con un estado igual a "error" y un motivo igual a "dirección en la lista de bloqueados".<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperturas<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Recuento de @broadLog-ids en todos los “logs” de seguimiento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Recuento distintivo de @broadLog-ids con un tipo de URL igual a “clic en el correo electrónico”.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reacciones sin procesar<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje del número de destinatarios que hicieron clic en una entrega al menos una vez comparado con el número de destinatarios que abrió una entrega al menos una vez.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Distintos clics sobre la población contactada<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Recuento de todas las @source-ids con una categoría de URL igual a “clic en el correo electrónico”.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics acumulados<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Cuenta todas las @ids con una categoría URL igual a “clic en el correo electrónico”.<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics del destinatario<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Cantidad distintiva de @broadLog-ids con un tipo de dirección URL igual a “clic en el correo electrónico”.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reacciones estimada<br /> </td> 
   <td> -<br /> </td> 
   <td> Proporción del número de destinatarios que hizo clic en una entrega al menos una vez comparada con la estimación de destinatarios que abrieron la entrega al menos una vez.<br /> </td> 
   <td> porcentaje(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Páginas visitadas<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Recuento de todas las @ids con un tipo de URL igual a “Web” o “Transacción”.<br /> </td> 
   <td> count(Iif([url/@type]=4 or [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transacciones<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Recuento de todas las @ids con un tipo de URL igual a “Transacción”.<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cantidad total<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Suma de webTrackingLog/@amounts con un tipo de URL igual a “Transacción”.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cantidad media de transacciones<br /> </td> 
   <td> -<br /> </td> 
   <td> Proporción de la cantidad total comparada con el número de transacciones.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Elementos<br /> </td> 
   <td> @article<br /> </td> 
   <td> Suma de webTrackingLog/@articles con un tipo de URL igual a “Transacción”.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Número promedio de elementos por transacción<br /> </td> 
   <td> -<br /> </td> 
   <td> Proporción del número de elementos comparada con el número de transacciones.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Cantidad media por mensaje<br /> </td> 
   <td> -<br /> </td> 
   <td> Proporción de la cantidad total comparada con el número de mensajes que se van a enviar.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> Correo electrónico<br /> </td> 
   <td> @email<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “correo electrónico”.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “facebook”.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “twitter”.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “delicious”.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “digg”.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “google”.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Suma de todos los @totalClicks con una categoría URL igual a “linkedin”.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL y flujos de clics {#urls-and-click-streams-1}

Este informe se basa en la tabla **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reacción<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Proporción del número de destinatarios objetivo que hicieron clic en una entrega al menos una vez comparada con la estimación de destinatarios objetivo que abrieron una entrega al menos una vez.<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics distintos<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Proporción de la cantidad de personas distintas que hicieron clic en una entrega al menos una vez en comparación con la cantidad de mensajes enviados correctamente.<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics acumulados<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Proporción del número total de clics de destinatarios objetivo en comparación con la cantidad de mensajes enviados correctamente.<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Recuento de todos los @totalClicks con una clave principal de URL diferente de 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Porcentaje del número de clics comparado con el número total de clics acumulados.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Resumen de entregas {#delivery-summary-1}

Este informe se basa en la tabla **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Población inicial<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Número total de destinatarios a quienes se realizó la entrega.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensajes rechazados a causa de una regla<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Número de direcciones ignoradas durante el análisis de acuerdo con las reglas de tipología: dirección no especificada, en cuarentena, en lista de bloqueados, etc.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Mensajes que se van a enviar<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Número total de mensajes que se van a enviar tras el análisis de envío.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Correctos<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensajes procesados correctamente.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Errores<br /> </td> 
   <td> @error<br /> </td> 
   <td> Número total de errores acumulados durante las entregas y el procesamiento automático de rechazos.<br /> </td> 
   <td> sum([indicadores/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuevas cuarentenas<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Número de direcciones en cuarentena tras una entrega fallido (usuario desconocido, dominio no válido).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Clics activos {#hot-clicks-1}

Este informe se basa en las tablas Envío (nms:delivery) y **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Este informe muestra el contenido del mensaje (HTML o texto) con el porcentaje de clics en los vínculos, por cada vínculo. Los vínculos de baja de bloques personalizados y los vínculos de páginas espejo se tienen en cuenta en el total de clics acumulados, pero no se visualizan en el informe.

## Estadísticas de seguimiento {#tracking-statistics-1}

Este informe se basa en la tabla **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transacciones<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Suma de todos los @totalClicks con un tipo de URL igual a “Transacción”.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Suma de todos los @totalClicks con un tipo de URL igual a “clic en el correo electrónico”.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Apertura<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Suma de todos los @totalClicks con una clave principal de URL igual a 1<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Estadísticas de entrega {#delivery-statistics-1}

Este informe se basa en la tabla **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Correos electrónicos procesados<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Número total de mensajes con estado igual a “Preparado”, “Enviado” o “Fallido”.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Entrega<br /> </td> 
   <td> @success<br /> </td> 
   <td> Número de mensajes procesados correctamente.<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Rechazos graves<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Número total de mensajes con un estado igual a “Fallido” y un motivo igual a “Usuario desconocido”.<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Rechazos leves<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Total de todos los mensajes con un estado igual a “Fallido” y un motivo igual a “inaccesible”, “bandeja de entrada llena”, “dominio no válido”, “cuenta desactivada”, “no conectado” o “rechazado”.<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperturas<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Número total de @broadLog-ids en los “logs” de seguimiento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Número total de @source-ids en las que la categoría URL es igual a “clic en el correo electrónico”.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Bajas<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Número total de @ids con una categoría URL igual a “Exclusión”.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Desglose de aperturas {#breakdown-of-opens-1}

Este informe se basa en las tablas **Envíos** (nms:delivery) y **“Logs” de seguimiento** (nms:trackingLogRcp).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etiqueta</strong> <br /> </th> 
   <th> <strong>Nombre del campo</strong> <br /> </th> 
   <th> <strong>Descripción del indicador</strong> <br /> </th> 
   <th> <strong>Fórmula de cálculo del indicador</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aperturas<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Suma de todas las @id con una clave principal de URL igual a 1 (apertura). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Otros indicadores {#other-indicators}

El indicador **Enviado** (@sent), al que se accede a través de **Envíos (nms:delivery) > Indicadores**, corresponde al número total de SMS enviados al proveedor de servicios. Este indicador solo se utiliza para envíos SMS y no debe utilizarse para otros tipos de envíos (no confundirlo con los indicadores **@success** y **@processed**).

## Sincronización de indicadores {#indicator-synchronization}

Si observa desincronizaciones o incoherencia en determinados indicadores, seleccione la entrega en el explorador de Adobe Campaign, haga clic con el botón derecho y elija **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Aperturas de seguimiento {#tracking-opens-}

Para que Adobe Campaign detecte las aperturas del mensaje, el destinatario debe bajar las imágenes del correo electrónico. Los correos electrónicos HTML con varias partes o alternativos incluyen una imagen de 0 píxeles que permite detectar qué mensajes se han abierto. Dado que los mensajes en formato de texto no incluyen imágenes, es imposible detectar si se han abierto o no. Los valores calculados basados en las aperturas de mensajes siempre son estimaciones debido al margen del error relacionado con la visualización de la imagen.

## Personas y destinatarios objetivo {#targeted-persons---recipients}

En algunos informes, Adobe Campaign distingue entre personas objetivo y destinatarios objetivo.

Los destinatarios objetivo son todos los destinatarios a los que se dirige la entrega.

El número de personas incluye destinatarios objetivo además de todas las personas a las que se reenvía el correo electrónico. Cada vez que se abre o se hace un clic en un explorador nuevo (donde no se ha abierto el mensaje aún), se añade otra persona a las estadísticas.

Por ejemplo, si recibe un correo electrónico (enviado por Adobe Campaign) en su trabajo y lo abre o hace clic en él, esto cuenta como un destinatario objetivo (por ejemplo, destinatario=1, persona=1). Si reenvía este correo electrónico a dos amigos, el número de destinatarios objetivo sigue siendo igual a uno, mientras que el número de personas es igual a tres. El valor 3 coincide con cada apertura o clic en un explorador nuevo.
