---
product: campaign
title: Entregas
description: Descubra más información sobre los flujos de trabajo Entregas
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 100%
---

# Entregas{#deliveries}



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
   <td> <span class="uicontrol">Alias cleansing</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Este flujo de trabajo estandariza los valores de enumeración. Se activa cada día a las 3 de la mañana de forma predeterminada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Actualizar la entrega</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Este flujo de trabajo le permite crear la lista de reglas de las calificaciones del correo rechazado, así como la lista de dominios y los MX de la plataforma. Este flujo de trabajo solo funciona si el puerto HTTPS está abierto. Estas listas no se actualizan a menos que se instale el módulo Deliverability.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Este flujo de trabajo es el de mantenimiento de la base de datos: realiza diferentes cálculos a partir de las estadísticas y procesos, y elimina los datos obsoletos de la base de datos según la configuración definida en el asistente de implementación. Se activa cada día a las 4 a. m. de manera predeterminada.</p> <p>Para obtener más información, consulte esta <a href="../../production/using/database-cleanup-workflow.md">página</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpieza de flujos de trabajo en pausa</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Este flujo de trabajo analiza los flujos de trabajo en pausa con opción de gravedad definida en normal y activa las advertencias y notificaciones cuando dichos flujos llevan demasiado tiempo en pausa. Tras un mes, los flujos de trabajo técnicos en pausa se detienen de manera incondicional. De forma predeterminada, se activa todos los lunes a las 5 a. m.</p> <p>Para obtener más información, consulte <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestión de flujos de trabajo en pausa</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notificación de oferta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Este flujo de trabajo implementa las ofertas aprobadas en el entorno en línea, así como todas las categorías incluidas en el catálogo de ofertas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Previsión</span> <br /> </td> 
   <td> <span class="uicontrol">previsión</span> <br /> </td> 
   <td> Este flujo de trabajo analiza las entregadas guardadas en el calendario provisional (crea registros provisionales). Se activa cada día a la 1 de la mañana de forma predeterminada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Seguimiento</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Este flujo de trabajo realiza la recuperación y la consolidación de la información de seguimiento. También garantiza que se recalculen las estadísticas de seguimiento y envío, especialmente las utilizadas por los flujos de trabajo de archivado del Centro de mensajes. De forma predeterminada se activa una vez cada hora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

