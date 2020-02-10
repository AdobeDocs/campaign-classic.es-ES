---
title: Campaña
seo-title: Campaña
description: Campaña
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0d687b57f75b432547baef57021b716a8ce37ad4

---


# Campaña{#campaign}

Los flujos de trabajo detallados a continuación se instalan con
				el módulo **Campaign** de forma predeterminada. Para obtener más información sobre este módulo, consulte esta [sección](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Estos flujos de trabajo DEBEN iniciarse para que los procesos de campaña se ejecuten a nivel de campaña.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etiqueta</strong><br /> </td> 
   <td> <strong>Nombre
								 interno</strong><br /> </td> 
   <td> <strong>Descripción</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Cálculo</span> de coste <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span><br /> </td> 
   <td> Este flujo de trabajo inicia el cálculo de las líneas de gastos y de costes sobre presupuestos, planes, programas, campañas, envíos y tareas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Pedidos y alertas</span><br /> </td> 
   <td> <span class="uicontrol">stockMgt</span><br /> </td> 
   <td> Este flujo de trabajo inicia el cálculo de existencias en las líneas de pedido y administra los umbrales de alertas de advertencia.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos en envíos en campañas</span><br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span><br /> </td> 
   <td> Este flujo de trabajo activa los envíos aprobados e inicia el posprocesado del proveedor de servicios para un envío externo. También envía notificaciones de aprobación y recordatorios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos</span> de campaña <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span><br /> </td> 
   <td> Este flujo de trabajo administra los trabajos de las campañas de marketing (inicia los objetivos, la extracción de archivos, etc.). También crea flujos de trabajo relacionados con campañas recurrentes y periódicas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Trabajos en proveedores</span> de servicios <br /> </td> 
   <td> <span class="uicontrol">providerMgt</span><br /> </td> 
   <td> Este flujo de trabajo comienza a procesar el proveedor (correo electrónico al enrutador y posprocesado) una vez que se aprueban los envíos. <br /> </td> 
  </tr> 
 </tbody> 
</table>

