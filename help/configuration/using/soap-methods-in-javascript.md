---
product: campaign
title: Métodos SOAP en JavaScript
description: Métodos SOAP en JavaScript
audience: configuration
content-type: reference
topic-tags: api
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# Métodos SOAP en JavaScript{#soap-methods-in-javascript}

Es el JavaScript ejecutado en el servidor de Adobe Campaign.

## Métodos estáticos {#static-methods}

Se accede a los métodos SOAP estáticos invocando un método en el objeto que representa el esquema. Los esquemas son propiedades de objetos &quot;namespace&quot;. Estas áreas de nombres son variables globales, por lo tanto, las variables xtk o nms representan las áreas de nombres correspondientes

El siguiente ejemplo invoca el método estático PostEvent del esquema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos no estáticos {#non-static-methods}

Para utilizar métodos SOAP no estáticos, es necesario recuperar primero una entidad mediante los métodos &quot;get&quot; o &quot;create&quot; en los esquemas correspondientes.

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

* Consulte en la tabla de destinatarios con una operación &quot;get&quot;:

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

* Consulte en la tabla de destinatarios con una operación &quot;select&quot;:

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
