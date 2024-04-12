---
product: campaign
title: Métodos SOAP en JavaScript
feature: Configuration, Instance Settings
description: Métodos SOAP en JavaScript
role: Data Engineer, Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# Métodos SOAP en JavaScript{#soap-methods-in-javascript}

JavaScript ejecutado en el servidor de Adobe Campaign.

## Métodos estáticos {#static-methods}

Se accede a los métodos SOAP estáticos invocando un método en el objeto que representa el esquema. Los esquemas son propiedades de objetos &quot;namespace&quot;. Estas áreas de nombres son variables globales, por lo que, por ejemplo, las variables xtk o nms representan las áreas de nombres correspondientes

En el ejemplo siguiente se invoca el método PostEvent estático del esquema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos no estáticos {#non-static-methods}

Para utilizar métodos SOAP no estáticos, primero es necesario recuperar una entidad utilizando los métodos &quot;get&quot; o &quot;create&quot; en los esquemas correspondientes.

En el ejemplo siguiente se invoca el método ExecuteQuery del esquema &quot;xtk:queryDef&quot;:

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
