---
solution: Campaign Classic
product: campaign
title: Añadir funciones SQL adicionales
description: Añadir funciones SQL adicionales
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---


# Añadir funciones SQL adicionales{#adding-additional-sql-functions}

## Introducción {#introduction}

Adobe Campaign permite al usuario definir **sus propias funciones** que pueden acceder a funciones SQL, tanto las que ofrece la base de datos como las que no están disponibles en la consola. Esto resulta útil para funciones acumuladas (media, máxima, suma), por ejemplo, que sólo se pueden calcular en el servidor o cuando la base de datos proporciona una manera más fácil de implementar determinadas funciones, en lugar de escribir &quot;manualmente&quot; la expresión en la consola (por ejemplo, administración de fechas).

Este mecanismo también se puede utilizar si desea utilizar una función SQL de motor de base de datos reciente o poco común, que aún no se ofrece en la consola de Adobe Campaign.

Una vez agregadas estas funciones, aparecerán en el editor de expresiones como otras funciones predefinidas.

>[!IMPORTANT]
>
>Las llamadas a funciones SQL en la consola ya no se envían de forma natural al servidor. Por lo tanto, el mecanismo descrito aquí se convierte en **la única manera de llamar a** en el servidor de funciones SQL no planificado.

## Instalación {#installation}

Las funciones que se van a agregar se encuentran en un archivo **&quot;package&quot; en formato XML**, cuya estructura se detalla en el siguiente párrafo.

Para instalarlo desde la consola, seleccione las opciones **Herramientas/Avanzado/Importar paquete** del menú, luego la **[!UICONTROL Install from file]** y siga las instrucciones del asistente de importación.

>[!IMPORTANT]
>
>Advertencia: aunque la lista de funciones importadas aparezca en el editor de funciones inmediatamente, no se podrán utilizar hasta que se haya reiniciado Adobe Campaign.

## Estructura general del paquete para importar {#general-structure-of-package-to-import}

Las funciones que se van a agregar se encuentran en el archivo **&quot;package&quot;** en formato XML. Este es un ejemplo.

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* El **nombre**, **Área de nombres** y **etiqueta** se utilizan únicamente con fines informativos. Permiten vista de un resumen del paquete en la lista de paquetes instalados (Explorer/Administración/Administración de paquetes/paquetes instalados).
* Los campos **buildVersion** y **buildNumber** son obligatorios. Deben corresponder al número de servidor al que está conectada la consola. Esta información se encuentra en el cuadro &quot;Ayuda/Acerca de&quot;.
* Los siguientes bloques, **entidades** y **funclist** son obligatorios. En funcList, los campos &quot;nombre&quot; y &quot;Área de nombres&quot; son obligatorios, pero su nombre queda en manos del usuario para que lo decida y ellos designan de forma exclusiva la lista de la función.

   Esto significa que si se importa otra lista de funciones con el mismo par Área de nombres/nombre (aquí &quot;cus::myList&quot;), se eliminarán las funciones importadas anteriormente. Por el contrario, si cambia este par Área de nombres/nombre, la nueva serie de funciones importadas se agregará a la anterior.

* El elemento **group** permite especificar el grupo de funciones en el que aparecerán las funciones importadas en el editor de funciones. El atributo @name puede ser un nombre que ya existe (en cuyo caso las funciones se agregarán al grupo considerado) o un nuevo nombre (en cuyo caso aparecerá en un nuevo grupo).
* Recordatorio: los valores posibles para el atributo @name en el elemento `<group>` son:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>Asegúrese de completar el atributo @label: es el nombre que se mostrará en la lista de funciones disponibles. Si no escribe nada, el grupo no tendrá un nombre. Sin embargo, si introduce un nombre que no sea el nombre existente, cambiará el nombre de todo el grupo.

Si desea agregar funciones a varios grupos diferentes, puede hacer que varios `<group>` elementos se rastreen en la misma lista.

Finalmente, un elemento `<group>` puede contener la definición de una o varias funciones, es decir, el propósito del archivo del paquete. El `<function>`   se detalla en el siguiente párrafo.

## Descriptor de funciones &lt;function>&lt;/function> {#function-descriptor--function-}

El caso presentado aquí es un caso general en el que deseamos proporcionar la **implementación de funciones**.

A continuación se muestra un ejemplo de una función de &quot;madurez relativa&quot; que, utilizando una edad, indica cuántos años se ha considerado madura a la persona.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

El campo **@name** hace referencia al nombre de la función y &quot;args&quot; es la lista de parámetros que se mostrarán en la descripción. En este caso, la función aparecerá como &quot;relativeMatrity ( `<age>` )&quot; en la ventana de selección de funciones.

* **La** ayuda es el campo que se muestra en la parte inferior de la ventana del editor de expresiones.
* **@** displayis es un mensaje informativo.

   >[!NOTE]
   >
   >En los atributos @help y @display, la cadena &quot;$1&quot; representa el nombre proporcionado en el primer parámetro de función (aquí, &quot;Edad&quot;). $2, $3... representaría los siguientes parámetros. En el atributo @body detallado a continuación, $1 designa el valor del argumento pasado a la función durante la llamada.

   >[!NOTE]
   >
   >La descripción debe ser una cadena de caracteres XML válidos: tenga en cuenta el uso de &#39;&lt;&#39; y &#39;>&#39; en lugar de &lt; y >.

* **@** typeis el tipo de devolución de la función y es un valor estándar (long, string, byte, datetime...). Si se omite, el servidor determina el mejor tipo entre los tipos disponibles dentro de la expresión que implementa la función.
* **@** minArgand  **** maxArgsdesigna el número de parámetros (mínimo y máximo) para un parámetro. Por ejemplo, para una función con 2 parámetros, minArgs y maxArgs serán 2 y 2. Para 3 parámetros, más 1 opcional, serán 3 y 4 respectivamente.
* Finalmente, el elemento **providerPart** proporciona la implementación de la función.

   * El atributo **provider** es obligatorio, especifica los sistemas de base de datos para los que se proporciona la implementación. Como se muestra en el ejemplo, cuando la sintaxis de expresiones o las funciones subyacentes difieren, se pueden proporcionar implementaciones alternativas según la base de datos.
   * El atributo **@body** contiene la implementación de la función. Tenga en cuenta: esta implementación debe ser una expresión, en lenguaje de base de datos (no un bloque de código). Según las bases de datos, las expresiones pueden ser subconsultas (&quot;(seleccionar columna de tabla donde...)&quot;) que devuelven un solo valor. Por ejemplo, este es el caso en Oracle (la consulta debe escribirse entre corchetes).

   >[!NOTE]
   >
   >Si es probable que sólo una o dos bases de datos sean consultadas por la función definida, siempre podemos proporcionar solamente las definiciones correspondientes a estas bases de datos.

## Descriptor de función &#39;Pass-through&#39; {#pass-through--function-descriptor}

Un descriptor de función especial es el bloque **&quot;pass-through&quot;**, con un sistema de base de datos &quot;provider&quot; no especificado. En este caso, la implementación &quot;body&quot; solo puede contener una llamada a una función con una sintaxis que no dependa de la base de datos utilizada. Mientras tanto, el bloque &quot;ProviderPart&quot; es único.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

En este caso, la adición de una función sólo sirve para hacer que una función de base de datos que no hubiera estado disponible de forma predeterminada, ahora visible para el cliente.

## Ejemplos {#examples}

Encontrará más ejemplos de funciones en el paquete predefinido &quot;xtkdatakitfuncList.xml&quot;.
