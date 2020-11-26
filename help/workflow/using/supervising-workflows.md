---
solution: Campaign Classic
product: campaign
title: Supervisión de flujos de trabajo
description: Descubra cómo supervisar flujos de trabajo de campañas
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 100%

---


# Supervisión de flujos de trabajo{#supervising-workflows}

Este caso de uso detalla la creación de un flujo de trabajo que permite monitorizar el estado de un conjunto de flujos de trabajo que están “en pausa”, “detenidos” o “con errores”.

Su objetivo es:

* Utilizar un flujo de trabajo para monitorizar un grupo de flujos de trabajo empresariales.
* Enviar un mensaje a un supervisor a través de una actividad de “envío”.

Para monitorizar el estado de un conjunto de flujos de trabajo, se debe seguir estos pasos:

1. Cree el flujo de trabajo de monitorización.
1. Escriba el código JavaScript para determinar si los flujos de trabajo están en pausa, detenidos o con errores.
1. Cree la actividad **[!UICONTROL Test]**.
1. Prepare la plantilla de envío.

>[!NOTE]
>
>Además del flujo de trabajo, Campaign **Mapa de calor de flujo de trabajo** permite analizar los detalles que se están ejecutando actualmente. Para obtener más información, consulte [la sección dedicada](../../workflow/using/heatmap.md).
>
>Para obtener más información sobre cómo **monitorizar la ejecución de los flujos de trabajo**, consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md).

## Paso 1: Creación del flujo de trabajo de monitorización {#step-1--creating-the-monitoring-workflow}

La carpeta de flujo de trabajo que se va a monitorizar es **“CustomWorkflows”** almacenada en el nodo **Administration > Production > Technical workflows.** Esta carpeta contiene un conjunto de flujos de trabajo empresariales.

El **flujo de trabajo de monitorización** se almacena en la raíz de la carpeta de flujos de trabajo técnicos. La etiqueta utilizada es **“Monitoring”**.

El esquema siguiente muestra la secuencia de actividades:

![](assets/uc_monitoring_workflow_overview.png)

Este flujo de trabajo consta de:

* una actividad **“Start”** (inicio).
* una actividad **“JavaScript code”** (código JavaScript) responsable de analizar la carpeta de flujos de trabajo empresariales.
* una actividad **“Test”** (prueba) para realizar una entrega al supervisor o reiniciar el flujo de trabajo.
* una actividad **“Delivery”** (envío) responsable del diseño del mensaje.
* una actividad **“Wait”** (espera) que controla los tiempos de posible cliente entre las iteraciones del flujo de trabajo.

## Paso 2: Escritura de JavaScript {#step-2--writing-the-javascript}

La primera parte del código JavaScript consiste en una consulta **(queryDef)** que permite identificar los flujos de trabajo con los estados “en pausa” (@state == 13), “error” (@error == 1) o “detenido” (@state == 20).

El **nombre interno** de la carpeta del flujo de trabajo a monitorizar se presenta en la siguiente condición:

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

La segunda parte del código JavaScript permite **mostrar un mensaje para cada flujo de trabajo** en función del estado recuperado durante la consulta.

>[!NOTE]
>
>Las cadenas creadas deben cargarse en las variables de evento del flujo de trabajo.

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## Paso 3: Creación de la actividad “Test”{#step-3--creating-the--test--activity}

La actividad “Prueba” permite determinar si una entrega debe ser realizado o si el flujo de trabajo de monitorización debe ejecutar otro ciclo en función de la actividad “Espera”

Se realiza una entrega al supervisor **si al menos una de las tres variables de evento “vars.strWorkflowError”, “vars.strWorkflowPaused” o “vars.strWorkflowStop” es válida.**

![](assets/uc_monitoring_workflow_test.png)

La actividad “Espera” se puede configurar para reiniciar el flujo de trabajo de monitorización a intervalos regulares. Para este caso de uso, **el tiempo de espera se establece en una hora**.

![](assets/uc_monitoring_workflow_attente.png)

## Paso 4: Preparación de una entrega {#step-4--preparing-the-delivery}

La actividad “Envío” se basa en una **plantilla de envío** almacenada en el nodo **Recursos > Plantillas > Plantillas de envío.**

Esta plantilla debe incluir:

* **la dirección de correo electrónico del supervisor**.
* **Contenido HTML** para insertar texto personalizado.

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   Las tres variables declaradas (WF_Stop, WF_Paused, WF_Error) coinciden con las tres variables de evento de flujo de trabajo.

   Estas variables deben declararse en la pestaña **Variables** de las propiedades de la plantilla de envío.

   Para recuperar **el contenido de las variables de evento de flujo de trabajo**, se debe declarar las variables específicas para la entrega que se desea inicializar con los valores que devuelve el código JavaScript.

   La plantilla de envío tiene el siguiente contenido:

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

Una vez creada y aprobada la plantilla, se debe configurar la actividad **Envío** para:

* vincular la actividad “Envío” a la plantilla de envío creada anteriormente.
* vincular las variables de evento del flujo de trabajo a las específicas de la plantilla de envío.

Haga doble clic en la actividad de **Envío** y seleccione las siguientes opciones:

* Envío: seleccione **Nuevo, creado desde plantilla** y seleccione la plantilla de envío creada previamente.
* Para los campos **Destinatarios y Contenido**, seleccione **Especificado en la entrega**.
* Acción que quiere ejecutar: seleccione **Preparación e inicio**.
* Anule la selección de la opción **Procesamiento de errores**.

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* Vaya a la pestaña **Script** de la actividad **Envío**, añada tres variables de **cadena de caracteres** a través del menú del campo de personalización.

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   Las tres variables declaradas son:

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

Cuando se inicia este flujo de trabajo de monitorización, envía el siguiente resumen al destinatario:

![](assets/uc_monitoring_workflow_mailfinal.png)

