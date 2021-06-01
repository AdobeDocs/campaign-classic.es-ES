---
product: campaign
title: Lista de informes
description: Lista de informes
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 100%

---

# Lista de informes{#list-of-reports}

## Informes sobre entregas {#reports-on-deliveries}

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para más información sobre el contenido de estos informes, consulte [esta sección](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Esquema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Actividades del usuario (recipientActivity)<br /> </td> 
   <td> Desglose de aperturas, clics y transacciones por periodo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendimiento de entrega (throughput)<br /> </td> 
   <td> Gráficos de rendimiento de entrega, en mensajes por hora y Mbits/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Errores y rechazos (errors)<br /> </td> 
   <td> Rechazos y no entregables por motivo y por dominio.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de seguimiento (deliveryFeedback)<br /> </td> 
   <td> Resumen de indicadores clave para el seguimiento del comportamiento de los destinatarios.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de seguimiento (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicadores de seguimiento de una entrega a una aplicación móvil.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Navegadores (browserStatistics)<br /> </td> 
   <td> Estadísticas en los navegadores utilizados por los destinatarios que hicieron clic en los mensajes.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Difusión en redes sociales (deliveryForward)<br /> </td> 
   <td> Actividad de difusión en redes y estadísticas de apertura de correos.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics activos (hoturls)<br /> </td> 
   <td> Muestra el mensaje y las tasas de clic superpuestas.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Informe de hipótesis (deliveryHypothesis)<br /> </td> 
   <td> Muestra el resumen de medidas sobre la hipótesis de entrega.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estadísticas de entrega (statisticsPerDelivery)<br /> </td> 
   <td> Estadísticas (mensajes procesados, mensajes enviados, rechazos graves, rechazos leves, clics, bajas de suscripción) por dominio del correo electrónico.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estadísticas de actividad de difusión (forwardActivities)<br /> </td> 
   <td> Análisis de actividades de difusión, aperturas y suscripciones por periodo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estadísticas de seguimiento (trackingStatistics)<br /> </td> 
   <td> Informe de tasas de apertura, clics y transacciones.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de envíos (deliverySending)<br /> </td> 
   <td> Resumen de indicadores de entrega: destino, exclusión y mensajes enviados.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de entrega (deliveryStatistics)<br /> </td> 
   <td> Tabla de resumen de los envíos seleccionados: Objetivos, exclusiones y mensajes enviados.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Sistemas operativos (osStatistics)<br /> </td> 
   <td> Estadísticas sobre los sistemas operativos utilizados por los destinatarios que hicieron clic en un mensaje.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de reacción (deliveryFeedbackSocial)<br /> </td> 
   <td> Tasa de reacción a los envíos y desglose de reacciones.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL y clics de rendimiento (topUrlDelivery)<br /> </td> 
   <td> Las URL más reactivas y las secuencias de clics asociadas.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Informes sobre campañas {#reports-on-campaigns}

Los informes sobre campañas hacen referencia a los datos de la tabla **nms:operation**.

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para más información sobre el contenido de estos informes, consulte [esta sección](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Actividades del usuario (operationRecipientActivity)<br /> </td> 
   <td> Desglose de aperturas, clics y transacciones por un periodo, depende de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendimiento de entrega (operationThroughput)<br /> </td> 
   <td> Gráficos de rendimiento de entrega, en correos por hora y Mbits/s, dependen de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Gastos de campaña (budgetOperationExpenses)<br /> </td> 
   <td> Muestra en detalle los elementos de la línea de campaña, depende de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errores y rechazos (operationErrors)<br /> </td> 
   <td> Rechazos y no entregables por motivo y dominio, dependen de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploración de las líneas de coste (budgetExplorerOperation)<br /> </td> 
   <td> Análisis descriptivo de las líneas de coste, depende de MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de seguimiento (operationFeedback)<br /> </td> 
   <td> Información general sobre los indicadores clave de seguimiento: Las aperturas, los clics y las transacciones dependen de la campaña.<br /> </td> 
  </tr> 
  <tr> 
   <td> Difusión en las redes sociales (operationForward)<br /> </td> 
   <td> Actividad de difusión y estadísticas de apertura de correo electrónico, dependen de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Informe de hipótesis (operationHypothesis)<br /> </td> 
   <td> Muestra el resumen de las mediciones de hipótesis para los envíos de campaña, depende de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Estadísticas de actividad de difusión (forwardActivityOpt)<br /> </td> 
   <td> Análisis de actividades de difusión en redes, aperturas y suscripciones por periodo, depende de Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de entrega (operationStatistics)<br /> </td> 
   <td> Gráfico de resumen de los envíos de la campaña: Objetivos, exclusiones y mensajes enviados.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendimiento de URL y clics (operationTopUrlDelivery)<br /> </td> 
   <td> La mayoría de las URL más reactivas y las secuencias de clics asociadas dependen de Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Informes sobre servicios {#reports-on-services}

Los informes sobre servicios hacen referencia a los datos de la tabla **nms:service**.

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para obtener más información sobre el contenido de estos informes, consulte las guías relacionadas.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Adquisiciones de seguidores (socialAcquisitionsByWebapp)<br /> </td> 
   <td> ¿Qué aplicaciones web permiten las posibles adquisiciones? Depende del complemento de marketing social.<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose de suscripciones (mobileAppDistribution)<br /> </td> 
   <td> Desglose de las suscripciones activas por aplicación móvil, depende del complemento del canal de aplicaciones móviles.<br /> </td> 
  </tr> 
  <tr> 
   <td> Seguimiento de suscripciones (subscriptionsProgress)<br /> </td> 
   <td> Evolución de las suscripciones a los servicios de información<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de reacción (socialReactionRate)<br /> </td> 
   <td> ¿Cuáles son las tasas de reacción de los últimos envíos? Depende del complemento de marketing social.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasa de reacción (mobileAppReactivityRate)<br /> </td> 
   <td> Tasa de reacción de los envíos más recientes, depende del complemento del canal de aplicaciones móviles.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Informes de presupuesto {#budget-reports}

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para más información sobre el contenido de estos informes, consulte [esta sección](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Esquema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Costes vinculados a los programas (budgetProgramCost)<br /> </td> 
   <td> Desglose de los costes de los programas.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolución del presupuesto (budgetEvolution)<br /> </td> 
   <td> Evolución de los costes del presupuesto por nivel de compromiso.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolución acumulada del presupuesto (budgetCumulativeEvolution)<br /> </td> 
   <td> Evolución de los costes presupuestarios acumulados desglosados por nivel.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploración de las líneas de coste (budgetExplorerBudget)<br /> </td> 
   <td> Análisis descriptivo de las líneas de coste.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploración de las líneas de coste (budgetExplorer)<br /> </td> 
   <td> Análisis descriptivo de las líneas de coste.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploración de las líneas de coste (budgetExplorerPlan)<br /> </td> 
   <td> Análisis descriptivo de las líneas de coste.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploración de las líneas de coste (budgetExplorerProgram)<br /> </td> 
   <td> Análisis descriptivo de las líneas de coste.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de los presupuestos (budget)<br /> </td> 
   <td> Resumen de los costes, las categorías de gastos y los presupuestos principales.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Informes sobre simulaciones {#reports-on-simulations}

Los informes sobre simulaciones hacen referencia a los datos de la tabla **nms:simulation**.

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para obtener más información sobre el contenido de estos informes, consulte las guías relacionadas.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detalle de las exclusiones de simulación (dlvSimuLossesDetail)<br /> </td> 
   <td> Tabla detallada de todas las causas de la exclusión.<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose de ofertas por rango (offerSimulationRanking)<br /> </td> 
   <td> Desglose de las ofertas de la simulación, por rango.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de la simulación (dlvSimuLossesSummary)<br /> </td> 
   <td> Resumen de los volúmenes y las exclusiones de simulación.<br /> </td> 
  </tr> 
  <tr> 
   <td> Estadísticas de coincidencia (dlvSimuOverlapping)<br /> </td> 
   <td> Volúmenes de coincidencia de destino de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumen de exclusiones debidas a la simulación (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabla de exclusiones debidas a la simulación.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Informes de aplicaciones Web {#reports-on-web-applications}

Los informes de aplicaciones Web hacen referencia a los datos de la tabla **nms:WebApp**.

Los informes integrados proporcionados por Adobe Campaign se pueden encontrar en la siguiente tabla.

Para más información sobre el contenido de estos informes, consulte [esta sección](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentación (surveyDictionary)<br /> </td> 
   <td> La descripción de la estructura del estudio depende del complemento Administrador de encuestas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Principal (surveyProperties)<br /> </td> 
   <td> Propiedades de encuesta<br /> </td> 
  </tr> 
  <tr> 
   <td> Desglose de respuestas (surveyDistribution)<br /> </td> 
   <td> Desglose de las respuestas a las preguntas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Otros informes de ootb {#other-ootb-reports}

También se incluyen los siguientes informes. Para más información al respecto, consulte el documento sobre la funcionalidad a la hacen referencia.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta y nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
   <td> <strong>Esquema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Análisis de ofertas (offerAnalysis)<br /> </td> 
   <td> Análisis de ofertas por fecha y canal, depende del complemento de Interacción.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> Eficiencia del remarketing (remarketingEffect)<br /> </td> 
   <td> Medición de la eficiencia de remarketing<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Historial de posibles adquisiciones en redes sociales (socialVisitorStatistics)<br /> </td> 
   <td> Historial de las posibles adquisiciones en Twitter y Facebook, depende del complemento de marketing social.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> Seguimiento de propuestas recientes (recentPropositions)<br /> </td> 
   <td> Seguimiento de propuestas en tiempo real<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
