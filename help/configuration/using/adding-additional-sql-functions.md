---
product: campaign
title: Adición de funciones SQL adicionales
description: Obtenga información sobre cómo definir funciones SQL adicionales
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Definición de funciones SQL adicionales{#adding-additional-sql-functions}

Adobe Campaign permite al usuario definir **sus propias funciones** que pueden acceder a las funciones SQL, tanto a las que ofrece la base de datos como a las que no están disponibles en la consola. Esto resulta útil para funciones acumuladas (promedio, máximo, suma), por ejemplo, que solo se pueden calcular en el servidor o cuando la base de datos proporciona una forma más sencilla de implementar determinadas funciones, en lugar de escribir &quot;manualmente&quot; la expresión en la consola (por ejemplo, administración de fechas).

Este mecanismo también se puede utilizar si desea utilizar una función SQL de motor de base de datos reciente o poco común, que la consola de Adobe Campaign aún no ofrece.

Una vez añadidas estas funciones, aparecen en el editor de expresiones como otras funciones predefinidas.

>[!IMPORTANT]
>
>Las llamadas de función SQL en la consola ya no se envían de forma natural al servidor. Por lo tanto, el mecanismo descrito aquí se convierte en **la única manera de llamar** en el servidor de funciones SQL no planeado.

## Instalación {#installation}

Las funciones que se van a agregar están en una **Archivo &quot;package&quot; en formato XML**, cuya estructura se detalla en el párrafo siguiente.

Para instalarlo desde la consola, seleccione la **Herramientas/Avanzado/Importar paquete** opciones del menú y, a continuación, la variable **[!UICONTROL Install from file]** y siga las instrucciones del asistente para importar.

>[!IMPORTANT]
>
>Advertencia: incluso si la lista de funciones importadas aparece en el editor de funciones de inmediato, no se podrán utilizar hasta que se haya reiniciado Adobe Campaign.

## Estructura general del paquete a importar {#general-structure-of-package-to-import}

Las funciones que se van a agregar se pueden encontrar en la **archivo &quot;package&quot;** en formato XML. Este es un ejemplo.

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

* El **name**, **namespace** y **etiqueta** son solo con fines informativos. Permiten ver un resumen del paquete en la lista de paquetes instalados (Explorer/Administration/Package management/Installed packages).
* El **buildVersion** y **buildNumber** Los campos de son obligatorios. Deben corresponder al número de servidor al que está conectada la consola. Esta información se encuentra en el cuadro Ayuda/Acerca de.
* Los siguientes bloques, **entidades** y **funclista** son obligatorios. En funcList, los campos &quot;name&quot; y &quot;namespace&quot; son obligatorios, pero su nombre lo decide el usuario y designan la lista de funciones de forma exclusiva.

   Esto significa que si se importa otra lista de funciones con el mismo par de área de nombres/nombre (aquí &quot;cus::myList&quot;), se eliminarán las funciones importadas anteriormente. Por el contrario, si cambia este par espacio de nombres/nombre, la nueva serie de funciones importadas se agregará a la anterior.

* El **grupo** permite especificar el grupo de funciones en el que aparecerán las funciones importadas en el editor de funciones. El atributo @name puede ser un nombre que ya existe (en cuyo caso las funciones se agregarán al grupo considerado) o un nombre nuevo (en cuyo caso aparecerá en un grupo nuevo).
* Recordatorio: posibles valores del atributo @name en la variable `<group>` Los elementos son:

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
>Asegúrese de completar el atributo @label: este es el nombre que se mostrará en la lista de funciones disponibles. Si no escribe nada, el grupo no tendrá nombre. Sin embargo, si escribe un nombre que no sea el nombre existente, el nombre de todo el grupo cambiará.

Si desea agregar funciones a varios grupos diferentes, puede hacer varias `<group>`  Los elementos de se rastrean en la misma lista.

Finalmente, una `<group>` puede contener la definición de una o varias funciones, ese es el propósito del archivo del paquete. El  `<function>`   se detalla en el párrafo siguiente.

## Descriptor de función &lt;function>&lt;/function> {#function-descriptor--function-}

El caso que se presenta aquí es un caso general por el cual deseamos proporcionar la **implementación de funciones**.

A continuación se muestra un ejemplo de una función de &quot;madurez relativa&quot; que, utilizando una edad, indica durante cuántos años se ha considerado que la persona ha madurado.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

El **@name** field hace referencia al nombre de la función y &quot;args&quot; es la lista de parámetros que se muestran en la descripción. En este caso, la función aparece como &quot;relativeMaturity&quot; ( `<age>` )&quot; en la ventana de selección de funciones.

* **ayuda** es el campo que se muestra en la parte inferior de la ventana del editor de expresiones.
* **@display** es un mensaje informativo.

   >[!NOTE]
   >
   >En los atributos @help y @display, la cadena &quot;$1&quot; representa el nombre que se dio en el primer parámetro de función (aquí, &quot;Age&quot;). $2, $3... representarían los siguientes parámetros. En el atributo @body detallado a continuación, $1 designa el valor del argumento pasado a la función durante la llamada.

   >[!NOTE]
   >
   >La descripción debe ser una cadena de caracteres XML válidos: tenga en cuenta el uso de &#39;&lt;&#39; y &#39;>&#39; en lugar de &lt; y >.

* **@type** es el tipo de valor devuelto por la función y es un valor estándar (long, string, byte, datetime...). Si se omite, el servidor determina el mejor tipo entre los tipos disponibles dentro de la expresión que implementa la función.
* **@minArgs** y **maxArgs** designa el número de parámetros (mínimo y máximo) de un parámetro. Por ejemplo, para una función con 2 parámetros, minArgs y maxArgs serán 2 y 2. Para 3 parámetros, más 1 opcional, serán 3 y 4 respectivamente.
* Por último, el **providerPart** proporciona la implementación de la función.

   * El **proveedor** es obligatorio, especifica los sistemas de base de datos para los que se proporciona la implementación. Como se muestra en el ejemplo, cuando la sintaxis de las expresiones o las funciones subyacentes son diferentes, se pueden proporcionar implementaciones alternativas según la base de datos.
   * El **@body** contiene la implementación de la función. Tenga en cuenta: esta implementación debe ser una expresión, en lenguaje de base de datos (no un bloque de código). Según las bases de datos, las expresiones pueden ser subconsultas (&quot;(seleccione la columna de la tabla donde...)&quot;) que devuelvan un solo valor. Por ejemplo, este es el caso en Oracle (la consulta debe escribirse entre corchetes).

   >[!NOTE]
   >
   >Si la función definida solo puede consultar una o dos bases de datos, siempre podemos proporcionar solo las definiciones correspondientes a estas bases de datos.

## Descriptor de la función &#39;Pasar&#39; {#pass-through--function-descriptor}

Un descriptor de función especial es **&quot;pass-through&quot;** , con un sistema de base de datos &quot;proveedor&quot; no especificado. En este caso, la implementación de &quot;cuerpo&quot; solo puede contener una sola llamada a la función con una sintaxis que no dependa de la base de datos utilizada. Mientras tanto, el bloque &quot;ProviderPart&quot; es único.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

En este caso, añadir una función solo sirve para hacer una función de base de datos que no habría estado disponible de forma predeterminada, ahora visible para el cliente.

## Ejemplos {#examples}

Se pueden encontrar más ejemplos de funciones en el paquete predefinido &quot;xtkdatakitfuncList.xml&quot;.
