---
solution: Campaign Classic
product: campaign
title: Entregas
description: Descubra más información sobre los flujos de trabajo Entregas
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 7cd76b5a31ed9fc0e64a650316ea29293c628233
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---


# Envíos{#deliveries}

Los flujos de trabajo detallados a continuación se instalan con el módulo **Envíos** de forma predeterminada.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Reporting aggregates</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Este flujo de trabajo actualiza los agregados que se utilizan en los informes. Se activa cada día a la 2 de la mañana de forma predeterminada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturación</span> <br /> </td> 
   <td> <span class="uicontrol">facturación</span> <br /> </td> 
   <td> Este flujo de trabajo envía el informe de actividad del sistema al operador “facturación” por correo electrónico. De forma predeterminada, se activa el día 25 de cada mes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Facturación (perfiles activos)</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>Este flujo de trabajo cuenta la cantidad de perfiles activos. Se activa cada noche a la 1 a. m. de forma predeterminada.</p> <p>Un “<strong>perfil</strong>” es un registro de información (por ejemplo, un registro de la tabla nmsRecipient o una tabla externa que contiene una ID de cookie, ID de cliente, ID móvil u otra información relacionada con un canal determinado) que representa a un cliente final, a un cliente potencial o a un contacto. La facturación solo abarca los perfiles que están “activos”. Un perfil se considera “activo” si este ha recibido comunicaciones o mensajes en los últimos 12 meses a través de cualquier canal.</p> <p>Los canales de Facebook y Twitter no se tienen en cuenta.</p> <p>Puede obtener una vista general del <span class="uicontrol">Number of active profiles</span> en el menú <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Campaign Management</span> &gt; <span class="uicontrol">Customer metrics</span>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Alias cleansing</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Este flujo de trabajo estandariza los valores de enumeración. Se activa cada día a la 3 de la mañana de forma predeterminada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Este flujo de trabajo le permite crear la lista de reglas de los atributos del correo rechazado, así como la lista de dominios y los MX de la plataforma. Este flujo de trabajo solo funciona si el puerto HTTPS está abierto. Estas listas no se actualizan a menos que se instale el módulo Deliverability.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Este flujo de trabajo es el del mantenimiento de la base de datos: realiza diferentes cálculos en las estadísticas y procesos y elimina los datos obsoletos de la base de datos según la configuración definida en el asistente de implementación. Se activa cada día a las 4 a. m. de manera predeterminada.</p> <p>Para obtener más información, consulte esta <a href="../../production/using/database-cleanup-workflow.md">página</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Paused workflows cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Este flujo de trabajo analiza los flujos de trabajo en pausa con opción de gravedad definida en normal y activa las advertencias y notificaciones cuando dichos flujos llevan demasiado tiempo en pausa. Tras un mes, los flujos de trabajo técnicos en pausa se detienen de manera incondicional. De forma predeterminada, se activa todos los lunes a las 5 a. m.</p> <p>Para obtener más información, consulte <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestión de flujos de trabajo en pausa</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Offer notification</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Este flujo de trabajo implementa las ofertas aprobadas en el entorno en línea, así como todas las categorías incluidas en el catálogo de ofertas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Previsión</span> <br /> </td> 
   <td> <span class="uicontrol">previsión</span> <br /> </td> 
   <td> Este flujo de trabajo analiza las entregas guardados en el calendario provisional (crea registros provisionales). Se activa cada día a la 1 de la mañana de forma predeterminada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Seguimiento</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Este flujo de trabajo realiza la recuperación y la consolidación de la información de seguimiento. También garantiza que se recalculen las estadísticas de seguimiento y envío, especialmente las utilizadas por los flujos de trabajo de archivado del Centro de mensajes. De forma predeterminada se activa una vez cada hora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

