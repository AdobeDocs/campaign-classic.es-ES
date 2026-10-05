---
product: campaign
title: Campaña
description: Campaña
feature: Workflows
hide: true
topic-tags: technical-workflows
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
source-wordcount: '166'
ht-degree: 100%
---

# Campaña{#campaign}



Los flujos de trabajo detallados a continuación se instalan con el módulo **Campaign** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Estos flujos de trabajo DEBEN iniciarse para que los procesos de campaña se ejecuten a nivel de campaña.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcular coste</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Este flujo de trabajo inicia el cálculo de las líneas de gastos y de costes sobre presupuestos, planes, programas, campañas, envíos y tareas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Valores: Pedidos y alertas</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Este flujo de trabajo inicia el cálculo de existencias en las líneas de pedido y administra los umbrales de alertas de advertencia.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos enviados en campañas</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Este flujo de trabajo activa los envíos aprobados e inicia el posprocesado del proveedor de servicios para un envío externo. También envía notificaciones de aprobación y recordatorios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos en campaña</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Este flujo de trabajo administra los trabajos de las campañas de marketing (inicia la segmentación, la extracción de archivos, etc.). También crea flujos de trabajo relacionados con campañas recurrentes y periódicas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos con proveedores de servicios</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> Este flujo de trabajo comienza a procesar el proveedor (correo electrónico al enrutador y posprocesado) una vez que se aprueban las entregas. <br /> </td> 
  </tr> 
 </tbody> 
</table>

