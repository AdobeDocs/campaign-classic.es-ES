---
product: campaign
title: Ejemplos de código JavaScript en flujos de trabajo
description: Estos ejemplos muestran cómo se puede utilizar código JavaScript en un flujo de trabajo
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '1768'
ht-degree: 100%

---

# Ejemplos de código JavaScript en flujos de trabajo{#javascript-in-workflows}

![](../../assets/v7-only.svg)

Estos ejemplos muestran cómo se puede utilizar el código JavaScript en un flujo de trabajo:

* [Escribir en la base de datos](#write-example)
* [Consultar la base de datos](#read-example)
* [Activación de un flujo de trabajo mediante un método estático SOAP](#trigger-example)
* [Interacción con la base de datos mediante un método SOAP no estático](#interact-example)

[Más información](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=es) acerca de los métodos SOAP estáticos y no estáticos.

En estos ejemplos se utiliza la extensión ECMAScript para XML (E4X). Con esta extensión, puede combinar llamadas de JavaScript y primitivas XML en el mismo script.

Para probar estos ejemplos, siga estos pasos:

1. Cree un flujo de trabajo y añada estas actividades al flujo de trabajo:
   1. Actividad de inicio
   1. Actividad de código JavaScript
   1. Actividad final

   [Más información](building-a-workflow.md) acerca de la creación de flujos de trabajo.

1. Añada el código JavaScript a una actividad. [Más información](advanced-parameters.md).
1. Guarde el flujo de trabajo.
1. Pruebe los ejemplos:
   1. Inicie el flujo de trabajo. [Más información](starting-a-workflow.md).
   1. Abra el historial. [Más información](monitoring-workflow-execution.md#displaying-logs).

## Ejemplo 1: escribir en la base de datos{#write-example}

Para escribir en la base de datos, puede utilizar el método estático `Write` en el esquema `xtk:session`:

1. Componga una solicitud de escritura en XML.

1. Escriba el registro:

   1. Llame al método `Write` en el esquema `xtk:session`.

      >[!IMPORTANT]
      > Si utiliza Adobe Campaign v8, le recomendamos que utilice el mecanismo de ensayo con las API de **Ingesta** y **Actualización/eliminación de datos** para el método `Write` en una tabla de Snowflake. [Más información](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=es){target=&quot;_blank&quot;}.

   1. Pase el código XML como argumento para la solicitud de escritura.

### Paso 1: componer una solicitud de escritura

Puede añadir, actualizar y eliminar registros.

#### Inserción de un registro

Como la operación `insert` es la predeterminada, no es necesario especificarla.

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

#### Actualización de un registro

Utilice la operación `_update`. [Más información](../../configuration/using/data-oriented-apis.md).

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

#### Eliminación de un registro

Utilice el método `DeleteCollection`. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=es).

Especifique esta información:

* El esquema de la tabla que se va a modificar
* La cláusula `where` necesaria para identificar el registro que se va a actualizar, en forma de elemento XML

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

Llame al método no estático `Write` en el esquema `xtk:session`:

```javascript
xtk.session.Write(myXML)
```

No se devuelve ningún valor para este método.

Añada el código completo a una actividad de código JavaScript en el flujo de trabajo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Este vídeo muestra cómo escribir en la base de datos:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Ejemplo 2: consultar la base de datos{#read-example}

Para consultar la base de datos, puede utilizar el método de instancia no estático `xtk:queryDef`:

1. Componga una consulta en XML.
1. Cree un objeto de consulta.
1. Ejecute la consulta.

### Paso 1: componer una consulta

Especifique el código XML para una entidad `queryDef`.

Sintaxis:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Especifique esta información:

* El esquema de la tabla que se va a leer
* La operación
* Las columnas que se van a devolver, en una cláusula `select`
* Las condiciones, en una cláusula `where`
* Los criterios de filtrado, en una cláusula `orderBy`

Puede utilizar estas operaciones:

| Operación | Resultado |
| --- | --- |
| `select` | Se devuelven cero o más elementos como una colección. |
| `getIfExists` | Se devuelve un elemento. Si no existe ningún elemento de coincidencia, se devuelve un elemento vacío. |
| `get` | Se devuelve un elemento. Si no existe ningún elemento de coincidencia, se devuelve un error. |
| `count` | El número de registros coincidentes se devuelve en forma de elemento con un atributo `count`. |

Escriba las cláusulas `select`, `where` y `orderBy` como elementos XML:

* Cláusula `select`

   Especifique las columnas que desea devolver. Por ejemplo, para seleccionar el nombre y el apellido de la persona, escriba este código:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Con el esquema `nms:recipient`, los elementos se devuelven en este formulario:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* Cláusula `where`

   Para especificar condiciones, utilice una cláusula `where`. Por ejemplo, para seleccionar los registros ubicados en la carpeta **Aprendizaje**, puede escribir este código:

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

* Cláusula `orderBy`

   Para ordenar el conjunto de resultados, especifique la cláusula `orderBy` como elemento XML con el atributo `sortDesc`. Por ejemplo, para ordenar los apellidos en orden de subida, puede escribir este código:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Paso 2: crear un objeto de consulta

Para crear una entidad a partir del código XML, utilice el método `create(`*`content`*`)`:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefije el método `create(`*`content`*`)` con el esquema de la entidad que se va a crear.

El argumento *`content`* es de cadena y opcional. Este argumento contiene el código XML que describe la entidad.

### Paso 3: ejecutar la consulta

Siga estos pasos:

1. Llame al método `ExecuteQuery` en la entidad `queryDef`:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Procese los resultados:
   1. Itere en los resultados de la operación `select`, utilizando una construcción de bucle.
   1. Pruebe los resultados utilizando la operación `getIfExists`.
   1. Haga un recuento de los resultados usando la operación `count`.

#### Resultados de una operación `select`

Todas las coincidencias se devuelven como una colección:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Para iterar en los resultados, utilice el bucle `for each`:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

El bucle incluye una variable de destinatario local. Para cada destinatario que se devuelve en la colección de destinatarios, se imprime el correo electrónico del destinatario. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=es) acerca de la función `logInfo`.

#### Resultados de una operación `getIfExists`

Cada coincidencia se devuelve como un elemento:

```xml
<recipient id="52,378,079">
```

Si no hay coincidencia, se devuelve un elemento vacío:

```xml
<recipient/>
```

Puede hacer referencia al nodo de clave principal; por ejemplo, el atributo `@id`:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultado de una operación `get`

Se devuelve una coincidencia como elemento:

```xml
<recipient id="52,378,079">
```

Si no hay coincidencia, se devuelve un error.

>[!TIP]
>
>Si sabe que hay una coincidencia, use la operación `get`. De lo contrario, utilice la operación `getIfExists`. Si usa esta práctica recomendada, los errores revelarán problemas inesperados. Si usa la operación `get`, no utilice la instrucción `try…catch`. El problema se gestiona mediante el proceso de gestión de errores del flujo de trabajo.

#### Resultado de una operación `count`

Se devuelve un elemento con el atributo `count`:

```xml
<recipient count="200">
```

Para utilizar el resultado, consulte el atributo `@count`:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Para la operación `select`, añada este código a una actividad de código JavaScript en el flujo de trabajo:

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

Como la operación `select` es la predeterminada, no es necesario especificarla.

Este vídeo muestra cómo leer desde la base de datos:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Activación de un flujo de trabajo {#trigger-example}

Puede activar flujos de trabajo mediante programación, por ejemplo, en flujos de trabajo técnicos o para procesar información que un usuario haya introducido en una página de aplicación web.

La activación del flujo de trabajo funciona mediante el uso de eventos. Puede usar estas funciones para eventos:

* Para publicar un evento, puede utilizar el método estático `PostEvent`. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=es).
* Para recibir un evento, puede usar la actividad **[!UICONTROL External signal]**. [Más información](external-signal.md).

Puede activar flujos de trabajo de diferentes maneras:

* Puede activar un flujo de trabajo en línea, es decir, desde el script principal de una actividad **[!UICONTROL JavaScript code]**.
* Puede activar un flujo de trabajo al finalizar otro:
   * Añada un script a la actividad **[!UICONTROL End]** del flujo de trabajo inicial.
   * Añada la actividad **[!UICONTROL External signal]** al principio del flujo de trabajo de destinatario.

      Al finalizar el flujo de trabajo inicial, se publica un evento. La transición saliente se activa y las variables de evento se rellenan. A continuación, el flujo de trabajo de destinatario recibe el evento.

      >[!TIP]
      >
      >Como práctica recomendada, cuando añada un script a una actividad, escriba el nombre de la actividad entre guiones dobles, por ejemplo, `-- end --`. [Más información](workflow-best-practices.md) acerca de las prácticas recomendadas del flujo de trabajo.

Sintaxis del método `PostEvent`:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

En este ejemplo, al finalizar el flujo de trabajo, se pasa un texto corto a la actividad de **señal** del flujo de trabajo **wkfExampleReceiver**:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Como el último parámetro está establecido en `false`, el flujo de trabajo **wkfExampleReceiver** se activa cada vez que se completa el flujo de trabajo inicial.

Cuando activa flujos de trabajo, tenga en cuenta estos principios:

* El comando `PostEvent` se ejecuta de forma asíncrona. El comando se coloca en la cola del servidor. El método se devuelve después de que se publique el evento.
* Se debe iniciar el flujo de trabajo de destinatario. De lo contrario, se escribe un error en el archivo de registro.
* Si el flujo de trabajo de destinatario está suspendido, el comando `PostEvent` se pone en cola hasta que se reanuda el flujo de trabajo.
* La actividad que se ha activado no requiere que una tarea esté en curso.

Este vídeo muestra cómo utilizar métodos de API estáticos:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Este vídeo muestra cómo activar flujos de trabajo:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interacción con la base de datos {#interact-example}

Estos ejemplos muestran cómo realizar estas acciones:

* Utilice los métodos `get` y `create` en esquemas para utilizar métodos SOAP no estáticos
* Creación de métodos que realicen consultas SQL
* Utilice el método `write` para insertar, actualizar y eliminar registros

Siga estos pasos:

1. Defina la consulta:

   * Recupere una entidad utilizando el método `create` en el esquema correspondiente; por ejemplo, el esquema `xtk:workflow`. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=es).
   * Utilice el método `queryDef` para emitir una consulta SQL.

1. Ejecute la consulta utilizando el método `ExecuteQuery`. [Más información](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=es).

   Utilice el bucle `for each` para recuperar los resultados.

### Sintaxis del método `queryDef` con una cláusula `select`

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

### Método `Create`

#### Ejemplo 1: seleccionar registros y escribir en el historial

Los nombres internos de los flujos de trabajo ubicados en la carpeta **wfExamples** están seleccionados. Los resultados se ordenan por nombre interno, en orden de subida, y se escriben en el historial.

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

Se seleccionan el nombre, el apellido, el correo electrónico y el ID de todos los destinatarios que se llamen Chris Smith. Los resultados se ordenan por correo electrónico, en orden de subida, y se escriben en el historial. Se usa una operación `delete` para eliminar los registros seleccionados.

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

#### Ejemplo 3: seleccionar registros y escribir en el historial

En este ejemplo, se utiliza un método no estático. El correo electrónico y el año de nacimiento de todos los destinatarios cuya información se almacena en la carpeta **1234** y cuyo nombre de dominio de correo electrónico comience por “adobe” están seleccionados. Los resultados se ordenan por fecha de nacimiento en orden de bajada. El correo electrónico de los destinatarios se escribe en el historial.

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

### Método `Write`

Puede insertar, actualizar y eliminar registros. Puede usar el método `Write` en cualquier esquema de Adobe Campaign. Como este método es estático, no es necesario crear un objeto. Puede utilizar estas operaciones:

* La operación `update`
* La operación `insertOrUpdate`, con el argumento `_key` para identificar el registro que se va a actualizar

   Si no especifica la carpeta **Destinatarios** y existe una coincidencia, el registro se actualiza en cualquier subcarpeta. De lo contrario, el registro se crea en la carpeta raíz **Destinatarios**.

* La operación `delete`

>[!IMPORTANT]
> Si utiliza Adobe Campaign v8, le recomendamos que utilice el mecanismo de ensayo con las API de **Ingesta** y **Actualización/eliminación de datos** para el método `Write` en una tabla de Snowflake. [Más información](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=es){target=&quot;_blank&quot;}.

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

En este ejemplo se combina un método estático y uno no estático.

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

* [Ejemplos de llamadas SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=es)
* Métodos:
   * [Create](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=es)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=es)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=es)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=es)
   * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=es)
* [función logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=es)
