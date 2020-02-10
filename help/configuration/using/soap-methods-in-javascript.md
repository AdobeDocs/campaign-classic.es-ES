---
title: Métodos SOAP en JavaScript
seo-title: Métodos SOAP en JavaScript
description: Métodos SOAP en JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Métodos SOAP en JavaScript{#soap-methods-in-javascript}

JavaScript ejecutado en el servidor de Adobe Campaign.

## Métodos estáticos {#static-methods}

Se accede a los métodos SOAP estáticos invocando un método en el objeto que representa el esquema. Los esquemas son propiedades de objetos &#39;namespace&#39;. Estos espacios de nombres son variables globales; por ejemplo, las variables xtk o nms representan los espacios de nombres correspondientes

El ejemplo siguiente invoca el método PostEvent estático del esquema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos no estáticos {#non-static-methods}

Para utilizar métodos SOAP no estáticos, primero es necesario recuperar una entidad mediante los métodos &quot;get&quot; o &quot;create&quot; en los esquemas correspondientes.

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

* Consulta en la tabla del destinatario con una operación &quot;get&quot;:

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

* Consulta en la tabla del destinatario con una operación de &quot;selección&quot;:

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

* Escritura de datos en la tabla del destinatario:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```

