---
title: Envío de alertas personalizadas a operadores
seo-title: Envío de alertas personalizadas a operadores
description: Envío de alertas personalizadas a operadores
seo-description: null
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 60%

---


# Envío de alertas personalizadas a operadores{#sending-personalized-alerts-to-operators}

En este ejemplo, deseamos enviar una alerta a un operador que contendrá el nombre de los perfiles que abrieron un boletín informativo, pero que no hicieron clic en el vínculo que contenía.

The profiles&#39; first and last name fields are linked to the **[!UICONTROL Recipients]** targeting dimension, whereas the **[!UICONTROL Alert]** activity is linked to the **[!UICONTROL Operator]** targeting dimension. Como resultado, no hay ningún campo disponible entre los dos entornos de segmentación para realizar una conciliación y recuperar los campos Nombre y Apellido, y mostrarlos en la actividad de Alerta.

El proceso consiste en crear un flujo de trabajo como se muestra a continuación:

1. Use a **[!UICONTROL Query]** activity to target data.
1. Add a **[!UICONTROL JavaScript code]** activity into the workflow to save the population form the query to the instance variable.
1. Utilice una actividad **[!UICONTROL Test]** para comprobar el recuento de población.
1. Utilice una actividad **[!UICONTROL Alert]** para enviar una alerta a un operador, según el resultado de la actividad **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Registro de población en la variable de instancia {#saving-the-population-to-the-instance-variable}

Add the code below into the **[!UICONTROL JavaScript code]** activity.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Asegúrese de que el código Javascript corresponde con la información de su flujo de trabajo:

* La etiqueta **[!UICONTROL queryDef schema]** debe corresponder al nombre de la dimensión de segmentación utilizado en la actividad de consulta.
* La etiqueta **[!UICONTROL node expr]** debe corresponder al nombre de los campos que se desea recuperar.

![](assets/uc_operator_3.png)

Para recuperar dicha información, siga los pasos siguientes:

1. Right-click the outbound transition from the **[!UICONTROL Query]** ativity, then select **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Right-click the list, then select **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Los nombres de las dimensiones y los campos de objetivos de consulta se muestran en la lista.

   ![](assets/uc_operator_6.png)

## Prueba del recuento de población {#testing-the-population-count}

Add the code below into the **[!UICONTROL Test]** activity to check if the targeted population contains at least 1 profile.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Configuración de la alerta {#setting-up-the-alert}

Now that the population has been added into the instance variable with the desired fields, you can add these information into the **[!UICONTROL Alert]** activity.

To do this, add into the **[!UICONTROL Source]** tab the code below:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>The **[!UICONTROL <%= item.target.recipient.@fieldName %>]** command lets you add one of the fields that have been saved to the instance variable through the **[!UICONTROL JavaScript code]** activity.\
>Puede agregar tantos campos como desee, siempre que se hayan insertado en el código JavaScript.

![](assets/uc_operator_8.png)

