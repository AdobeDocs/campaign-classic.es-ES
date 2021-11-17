---
product: campaign
title: Ejemplos de código JavaScript en flujos de trabajo
description: Estos ejemplos muestran cómo se puede utilizar código JavaScript en un flujo de trabajo
audience: workflow
content-type: reference
topic-tags: advanced-management
source-git-commit: fa3a3e1801738928876734aa42342f0a5b49e320
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 2%

---

# Ejemplos de código JavaScript en flujos de trabajo{#javascript-in-workflows}

![](../../assets/common.svg)

Estos ejemplos muestran cómo se puede utilizar el código JavaScript en un flujo de trabajo:

* [Escribir en la base de datos](#write-example)
* [Consultar la base de datos](#read-example)
* [Déclencheur de un flujo de trabajo mediante un método estático SOAP](#trigger-example)
* [Interaccione con la base de datos mediante un método SOAP no estático](#interact-example)

[Más información](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) acerca de los métodos SOAP estáticos y no estáticos.

En estos ejemplos se utiliza la extensión ECMAScript para XML (E4X). Con esta extensión, puede combinar llamadas de JavaScript y primitivas XML en la misma secuencia de comandos.

Para probar estos ejemplos, siga estos pasos:

1. Cree un flujo de trabajo y añada estas actividades al flujo de trabajo:
   1. Actividad de inicio
   1. Actividad de código JavaScript
   1. Actividad final

   [Más información](building-a-workflow.md) acerca de la creación de flujos de trabajo.

1. Agregue el código JavaScript a una actividad . [Más información](advanced-parameters.md).
1. Guarde el flujo de trabajo.
1. Pruebe los ejemplos:
   1. Inicie el flujo de trabajo. [Más información](starting-a-workflow.md).
   1. Abra el diario. [Más información](monitoring-workflow-execution.md#displaying-logs).

## Ejemplo 1: escribir en la base de datos{#write-example}

Para escribir en la base de datos, puede utilizar la variable estática `Write` en el `xtk:session` esquema:

1. Componer una solicitud de escritura en XML.

1. Escriba el registro:

   1. Llame a la función `Write` en el `xtk:session` esquema.

      >[!IMPORTANT]
      > Si utiliza Adobe Campaign v8, le recomendamos que utilice el mecanismo de ensayo con la variable **Ingesta** y **Actualización/eliminación de datos** API para `Write` en una tabla de Snowflake. [Más información](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Pase el código XML como argumento para la solicitud de escritura.

### Paso 1: componer una solicitud de escritura

Puede agregar, actualizar y eliminar registros.

#### Insertar un registro

Porque la variable `insert` es la operación predeterminada, no es necesario especificarla.

Especifique esta información como atributos XML:

* El esquema de la tabla que se va a modificar
* Los campos de tabla que se van a rellenar

Ejemplo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Actualizar un registro

Utilice la variable `_update` operación. [Más información](../../configuration/using/data-oriented-apis.md).

Especifique esta información como atributos XML:

* El esquema de la tabla que se va a modificar
* Los campos de tabla que se van a actualizar
* El argumento clave necesario para identificar el registro que se va a actualizar

Ejemplo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Eliminar un registro

Utilice la variable `DeleteCollection` método. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Especifique esta información:

* El esquema de la tabla que se va a modificar
* La variable `where` cláusula necesaria para identificar el registro que se va a actualizar, en forma de elemento XML

Ejemplo:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Paso 2: escribir el registro

Llame a la función no estática `Write` en el `xtk:session` esquema:

```javascript
xtk.session.Write(myXML)
```

No se devuelve ningún valor para este método.

Agregue el código completo a una actividad JavaScript code en el flujo de trabajo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Este vídeo muestra cómo escribir en la base de datos:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Ejemplo 2: consulta de la base de datos{#read-example}

Para consultar la base de datos, puede utilizar el `xtk:queryDef` método de instancia:

1. Componer una consulta en XML.
1. Cree un objeto de consulta.
1. Ejecute la consulta.

### Paso 1: componer una consulta

Especifique el código XML para un `queryDef` entidad.

Sintaxis:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Especifique esta información:

* Esquema de la tabla que se va a leer.
* La operación
* Las columnas que se van a devolver, en un `select` cláusula
* Las condiciones, en un `where` cláusula
* Los criterios de filtrado, en un `orderBy` cláusula

Puede utilizar estas operaciones:

| Operación | Resultado |
| --- | --- |
| `select` | Se devuelven cero o más elementos como una colección. |
| `getIfExists` | Se devuelve un elemento. Si no existe ningún elemento de coincidencia, se devuelve un elemento vacío. |
| `get` | Se devuelve un elemento. Si no existe ningún elemento de coincidencia, se devuelve un error. |
| `count` | El número de registros coincidentes se devuelve en forma de elemento con un `count` atributo. |

Escriba el `select`, `where`y `orderBy` como elementos XML:

* `select` cláusula

   Especifique las columnas que desea devolver. Por ejemplo, para seleccionar el nombre y los apellidos de la persona, escriba este código:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Con la variable `nms:recipient` esquema, los elementos se devuelven en este formulario:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` cláusula

   Para especificar condiciones, utilice un `where` cláusula. Por ejemplo, para seleccionar los registros ubicados en la variable **Capacitación** , puede escribir este código:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Cuando combine varias expresiones, utilice el operador booleano en la primera expresión. Por ejemplo, para seleccionar todas las personas que se llamen Isabel García, puede escribir este código:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` cláusula

   Para ordenar el conjunto de resultados, especifique la variable `orderBy` como elemento XML con la variable `sortDesc` atributo. Por ejemplo, para ordenar los apellidos en orden ascendente, puede escribir este código:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Paso 2: crear un objeto de consulta

Para crear una entidad a partir del código XML, utilice la variable `create(`*`content`*`)` método:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefijo de `create(`*`content`*`)` con el esquema de la entidad que se va a crear.

La variable *`content`* es un argumento de cadena y es opcional. Este argumento contiene el código XML que describe la entidad.

### Paso 3: ejecutar la consulta

Siga estos pasos:

1. Llame a la función `ExecuteQuery` en el `queryDef` entidad:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Procese los resultados:
   1. Iterar sobre los resultados del `select` , utilizando una construcción de bucle.
   1. Pruebe los resultados utilizando la variable `getIfExists` operación.
   1. Haga un recuento de los resultados usando la variable `count` operación.

#### Resultados de una `select` operation

Todas las coincidencias se devuelven como una colección:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Para iterar los resultados, utilice la variable `for each` bucle:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

El bucle incluye una variable de destinatario local. Para cada destinatario que se devuelve en la colección de destinatarios, se imprime el correo electrónico del destinatario. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) acerca de `logInfo` función.

#### Resultados de una `getIfExists` operation

Cada coincidencia se devuelve como un elemento:

```xml
<recipient id="52,378,079">
```

Si no hay coincidencia, se devuelve un elemento vacío:

```xml
<recipient/>
```

Puede hacer referencia al nodo de clave principal; por ejemplo, la variable `@id` atributo:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultado de una `get` operation

Se devuelve una coincidencia como elemento:

```xml
<recipient id="52,378,079">
```

Si no hay coincidencia, se devuelve un error.

>[!TIP]
>
>Si sabe que hay una coincidencia, use la variable `get` operación. De lo contrario, utilice el `getIfExists` operación. Si usa esta práctica recomendada, los errores revelarán problemas inesperados. Si usa la variable `get` , no utilice la función `try…catch` instrucción. El problema se gestiona mediante el proceso de gestión de errores del flujo de trabajo.

#### Resultado de una `count` operation

Un elemento con la variable `count` se devuelve el atributo:

```xml
<recipient count="200">
```

Para utilizar el resultado, consulte la `@count` atributo:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Para la variable `select` Agregue este código a una actividad JavaScript code en el flujo de trabajo:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Porque la variable `select` es la operación predeterminada, no es necesario especificarla.

Este vídeo muestra cómo leer desde la base de datos:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Déclencheur de un flujo de trabajo {#trigger-example}

Puede déclencheur de flujos de trabajo mediante programación, por ejemplo, en flujos de trabajo técnicos o para procesar información que un usuario haya introducido en una página de aplicación web.

La activación del flujo de trabajo funciona mediante el uso de eventos. Puede usar estas funciones para eventos:

* Para anunciar un evento, puede utilizar la variable estática `PostEvent` método. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Para recibir un evento, puede usar la variable **[!UICONTROL External signal]** actividad. [Más información](external-signal.md).

Puede déclencheur de flujos de trabajo de diferentes maneras:

* Puede crear un déclencheur de un flujo de trabajo en línea, es decir, desde la secuencia de comandos principal de un **[!UICONTROL JavaScript code]** actividad.
* Puede crear un déclencheur de un flujo de trabajo al finalizar otro:
   * Agregue una secuencia de comandos de inicialización a la **[!UICONTROL End]** actividad del flujo de trabajo inicial.
   * Agregue la variable **[!UICONTROL External signal]** actividad al principio del flujo de trabajo de target.

      Al finalizar el flujo de trabajo inicial, se anuncia un evento. La transición saliente se activa y las variables de evento se rellenan. A continuación, el flujo de trabajo de destino recibe el evento.

      >[!TIP]
      >
      >Como práctica recomendada, cuando agregue una secuencia de comandos a una actividad, escriba el nombre de la actividad en guiones dobles, por ejemplo, `-- end --`. [Más información](workflow-best-practices.md) acerca de las prácticas recomendadas del flujo de trabajo.

Sintaxis de la variable `PostEvent` método:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

En este ejemplo, al finalizar el flujo de trabajo, se pasa un texto corto al **señal** actividad de **wkfExampleReceiver** flujo de trabajo:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Porque el último parámetro está establecido en `false`, el **wkfExampleReceiver** el flujo de trabajo se activa cada vez que se completa el flujo de trabajo inicial.

Cuando déclencheur flujos de trabajo, tenga en cuenta estos principios:

* La variable `PostEvent` se ejecuta asincrónicamente. El comando se coloca en la cola del servidor. El método se devuelve después de que se anuncie el evento.
* Se debe iniciar el flujo de trabajo de destino. De lo contrario, se escribe un error en el archivo de registro.
* Si el flujo de trabajo de destino está suspendido, la variable `PostEvent` se pone en cola hasta que se reanuda el flujo de trabajo.
* La actividad activada no requiere que una tarea esté en curso.

Este vídeo muestra cómo utilizar métodos de API estáticos:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Este vídeo muestra cómo déclencheur flujos de trabajo:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interaccione con la base de datos {#interact-example}

Estos ejemplos muestran cómo realizar estas acciones:

* Utilice la variable `get` y `create` métodos en esquemas para utilizar métodos SOAP no estáticos
* Crear métodos que realicen consultas SQL
* Utilice la variable `write` método para insertar, actualizar y eliminar registros

Siga estos pasos:

1. Defina la consulta:

   * Recupere una entidad utilizando la variable `create` en el esquema correspondiente (por ejemplo, la variable `xtk:workflow` esquema. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Utilice la variable `queryDef` para emitir una consulta SQL.

1. Ejecute la consulta utilizando el `ExecuteQuery` método. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Utilice la variable `for each` para recuperar los resultados.

### Sintaxis de la variable `queryDef` método con un `select` cláusula

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` method

#### Ejemplo 1: seleccionar registros y escribir en el diario

Los nombres internos de los flujos de trabajo ubicados en la variable **wfExamples** están seleccionadas. Los resultados se ordenan por nombre interno, en orden ascendente, y se escriben en el diario.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Ejemplo 2: eliminar registros

Se seleccionan el nombre, los apellidos, el correo electrónico y el ID de todos los destinatarios que se llamen Chris Smith. Los resultados se ordenan por correo electrónico, en orden ascendente, y se escriben en el diario. A `delete` para eliminar los registros seleccionados.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Ejemplo 3: seleccionar registros y escribir en el diario

En este ejemplo, se utiliza un método no estático. El correo electrónico y el año de nacimiento de todos los destinatarios cuya información se almacena en la variable **1234** y cuyo nombre de dominio de correo electrónico comience por &quot;adobe&quot; están seleccionados. Los resultados se ordenan por fecha de nacimiento en orden descendente. El correo electrónico de los destinatarios se escribe en el diario.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` method

Puede insertar, actualizar y eliminar registros. Puede usar la variable `Write` en cualquier esquema de Adobe Campaign. Como este método es estático, no es necesario crear un objeto. Puede utilizar estas operaciones:

* La variable `update` operation
* La variable `insertOrUpdate` con la función `_key` argumento para identificar el registro que se va a actualizar

   Si no especifica la variable **Destinatarios** carpeta, si existe una coincidencia, el registro se actualiza en cualquier subcarpeta. De lo contrario, el registro se crea en la raíz **Destinatarios** carpeta.

* La variable `delete` operation

>[!IMPORTANT]
> Si utiliza Adobe Campaign v8, le recomendamos que utilice el mecanismo de ensayo con la variable **Ingesta** y **Actualización/eliminación de datos** API para `Write` en una tabla de Snowflake. [Más información](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

#### Ejemplo 1: insertar o actualizar un registro

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Ejemplo 2: eliminar registros

En este ejemplo se combina un método estático y un método no estático.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

Este vídeo muestra cómo utilizar métodos API no estáticos:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

Este vídeo muestra un ejemplo del uso de un método de API no estático en un flujo de trabajo:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Temas relacionados

* [API orientadas a datos](../../configuration/using/data-oriented-apis.md)
* [Plantillas y scripts de JavaScript](javascript-scripts-and-templates.md)
* [Métodos SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentación de API

* [Ejemplos de llamadas SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Métodos:
   * [Crear](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Escritura](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo, función](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)