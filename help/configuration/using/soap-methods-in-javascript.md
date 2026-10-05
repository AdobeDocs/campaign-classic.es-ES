---
product: campaign
title: Métodos SOAP en JavaScript
feature: Configuration, Instance Settings
description: Métodos SOAP en JavaScript
role: Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
TQID: 'https://experienceleague.adobe.com/pIvm36kXpJEzeG4mugpR-7kAQDJpyJ2YFXp4S9J7lUw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%
---
# Métodos SOAP en JavaScript{#soap-methods-in-javascript}

Este es el JavaScript ejecutado en el servidor de Adobe Campaign.

## Métodos estáticos {#static-methods}

Se accede a los métodos de SOAP estáticos invocando un método en el objeto que representa el esquema. Los esquemas son propiedades de objetos &quot;namespace&quot;. Estas áreas de nombres son variables globales, por lo que, por ejemplo, las variables xtk o nms representan las áreas de nombres correspondientes

El ejemplo siguiente invoca el método PostEvent estático del esquema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos no estáticos {#non-static-methods}

Para utilizar métodos SOAP no estáticos, primero es necesario recuperar una entidad utilizando los métodos &quot;get&quot; o &quot;create&quot; en los esquemas correspondientes.

El ejemplo siguiente invoca el método ExecuteQuery del esquema &quot;xtk:queryDef&quot;:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Ejemplos {#examples}

* Realice una consulta en la tabla de destinatarios con una operación &quot;get&quot;:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Realice una consulta en la tabla de destinatarios con una operación &quot;seleccionar&quot;:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Escritura de datos en la tabla de destinatarios:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
