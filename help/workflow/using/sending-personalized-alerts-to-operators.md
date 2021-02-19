---
solution: Campaign Classic
product: campaign
title: Envío de alertas personalizadas a operadores
description: Descubra más información sobre cómo enviar alertas personalizadas a operadores
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 100%

---


# Envío de alertas personalizadas a operadores{#sending-personalized-alerts-to-operators}

En este ejemplo, deseamos enviar una alerta a un operador que contendrá el nombre de los perfiles que abrieron un boletín informativo, pero que no hicieron clic en el vínculo que contenía.

Los campos de nombre y apellido de los perfiles se vinculan a la dimensión de segmentación **[!UICONTROL Recipients]**, mientras que la actividad **[!UICONTROL Alert]** está vinculada al **[!UICONTROL Operator]** de la dimensión de segmentación. Como resultado, no hay ningún campo disponible entre los dos entornos de segmentación para realizar una conciliación y recuperar los campos Nombre y Apellido, y mostrarlos en la actividad de Alerta.

El proceso consiste en crear un flujo de trabajo como se muestra a continuación:

1. Utilice una actividad **[!UICONTROL Query]** para segmentar los datos.
1. Agregue una actividad **[!UICONTROL JavaScript code]** al flujo de trabajo para guardar la población de la consulta en la variable de la instancia.
1. Utilice una actividad **[!UICONTROL Test]** para comprobar el recuento de población.
1. Utilice una actividad **[!UICONTROL Alert]** para enviar una alerta a un operador, según el resultado de la actividad **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Registro de población en la variable de instancia {#saving-the-population-to-the-instance-variable}

Agregue el código siguiente a la actividad **[!UICONTROL JavaScript code]**.

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

1. Haga clic con el botón derecho en la transición saliente desde la actividad **[!UICONTROL Query]** y seleccione **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Haga clic con el botón derecho en la lista y, luego, seleccione **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Los nombres de las dimensiones y los campos de objetivos de consulta se muestran en la lista.

   ![](assets/uc_operator_6.png)

## Prueba del recuento de población {#testing-the-population-count}

Agregue el código siguiente a la actividad **[!UICONTROL Test]** para comprobar si la población objetivo contiene al menos 1 perfil.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Configuración de la alerta {#setting-up-the-alert}

Ahora que la población ha sido añadida a la variable de la instancia con los campos deseados, puede añadir esta información en la actividad **[!UICONTROL Alert]**.

Para ello, añada a la pestaña **[!UICONTROL Source]** el siguiente código:

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
>El comando **[!UICONTROL <%= item.target.recipient.@fieldName %>]** permite agregar uno de los campos que se han guardado en la variable de instancia a través de la actividad **[!UICONTROL JavaScript code]**.\
>Puede agregar tantos campos como desee, siempre que se hayan insertado en el código JavaScript.

![](assets/uc_operator_8.png)

