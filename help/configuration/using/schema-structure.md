---
product: campaign
title: Explicación de la estructura de esquemas en Adobe Campaign
description: Estructura del esquema
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1511'
ht-degree: 11%

---

# Comprender la estructura de esquema {#schema-structure}

A continuación se describe la estructura básica de un esquema.

## Esquemas de datos  {#data-schema}

Para un(a) `<srcschema>`, la estructura es la siguiente:

```sql
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

El documento XML de un esquema de datos debe contener **`<srcschema>`** el elemento raíz con los atributos **name** y **namespace** para rellenar el nombre del esquema y su área de nombres.

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Utilice el siguiente contenido XML para ilustrar la estructura de un esquema de datos:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Con su esquema de datos correspondiente:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Descripción {#description}

El punto de entrada del esquema es el elemento principal. Es fácil de identificar porque tiene el mismo nombre que el esquema y debe ser el elemento secundario del elemento raíz. La descripción del contenido comienza con este elemento.

En nuestro ejemplo, el elemento principal se representa mediante la siguiente línea:

```
<element name="recipient">
```

Los elementos **`<attribute>`** y **`<element>`** que siguen al elemento principal se utilizan para definir las ubicaciones y los nombres de los elementos de datos en la estructura XML.

En nuestro esquema de ejemplo, estos son:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Se aplican las siguientes reglas:

* Cada **`<element>`** y **`<attribute>`** debe identificarse por su nombre mediante el atributo **name**.

  >[!IMPORTANT]
  >
  >El nombre del elemento debe ser conciso, preferiblemente en inglés, e incluir solo los caracteres permitidos en las reglas de nomenclatura XML.

* Solo los elementos **`<element>`** pueden contener **`<attribute>`** elementos y **`<element>`** elementos en la estructura XML.
* Un elemento **`<attribute>`** debe tener un nombre único dentro de un elemento **`<element>`**.
* Se recomienda el uso de **`<elements>`** en cadenas de datos de varias líneas.

## Tipos de datos {#data-types}

El tipo de datos se ingresa mediante el atributo **type** en los elementos **`<attribute>`** y **`<element>`**.

Hay disponible una lista detallada en la descripción del elemento [`<attribute>` ](../../configuration/using/schema/attribute.md) y el elemento [`<element>` ](../../configuration/using/schema/element.md).

Cuando este atributo no se rellena, **string** es el tipo de datos predeterminado a menos que el elemento contenga elementos secundarios. Si es así, solo se usa para estructurar los elementos jerárquicamente (**`<location>`** elemento en nuestro ejemplo).

Los siguientes tipos de datos son compatibles con los esquemas:

* **cadena**: cadena de caracteres. Ejemplos: un nombre, una ciudad, etc.

  El tamaño se puede especificar mediante el atributo **length** (opcional, valor predeterminado &quot;255&quot;).

* **booleano**: campo booleano. Ejemplo de valores posibles: true/false, 0/1, sí/no, etc.
* **byte**, **corto**, **largo**: enteros (1 byte, 2 bytes, 4 bytes). Ejemplos: una edad, un número de cuenta, una cantidad de puntos, etc.
* **double**: número de punto flotante de precisión doble. Ejemplos: un precio, una tasa, etc.
* **fecha**, **fecha y hora**: fechas y fechas + horas. Ejemplos: una fecha de nacimiento, una fecha de compra, etc.
* **datetimenotz**: fecha y hora sin datos de zona horaria.
* **timespan**: duraciones. Ejemplo: antigüedad.
* **memo**: campos de texto largos (varias líneas). Ejemplos: una descripción, un comentario, etc.
* **uuid**: los campos &quot;uniqueidentifier&quot; admiten un GUID (sólo se admite en Microsoft SQL Server).

  >[!NOTE]
  >
  >Para contener un campo **uuid** en RDBMS que no sea Microsoft SQL Server, se debe agregar y completar la función `the newuuid()` con su valor predeterminado.

Este es un ejemplo de esquema con los tipos introducidos:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Asignación de los tipos de datos de Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

En la tabla siguiente se enumeran las asignaciones para los tipos de datos generados por Adobe Campaign para los distintos sistemas de administración de bases de datos.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Cadena<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 si es Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Corto<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Doble<br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> ENTERO<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Fecha<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Hora<br /> </td> 
   <td> HORA<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> MARCA DE TIEMPO <br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> MARCA DE TIEMPO <br /> </td> 
   <td> FECHA<br /> </td> 
  </tr> 
  <tr> 
   <td> Duración <br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTANTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Nota<br /> </td> 
   <td> TEXTO<br /> </td> 
   <td> CLOB (NCLOB si es Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob <br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Propiedades {#properties}

Los elementos **`<elements>`** y **`<attributes>`** del esquema de datos se pueden enriquecer con varias propiedades. Puede rellenar una etiqueta para describir el elemento actual.

### Etiquetas y descripciones {#labels-and-descriptions}

* La propiedad **label** le permite escribir una breve descripción.

  >[!NOTE]
  >
  >La etiqueta está asociada al idioma actual de la instancia.

  **Ejemplo**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  La etiqueta se muestra en el formulario de entrada de la consola del cliente de Adobe Campaign:

  ![](assets/d_ncs_integration_schema_label.png)

* La propiedad **desc** permite escribir una descripción larga.

  La descripción se muestra en el formulario de entrada en la barra de estado de la ventana principal de la consola del cliente de Adobe Campaign.

  >[!NOTE]
  >
  >La descripción está asociada al idioma actual de la instancia.

  **Ejemplo**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Valores predeterminados {#default-values}

Use la propiedad **default** para definir una expresión que devuelva un valor predeterminado al crear contenido.

El valor debe ser una expresión compatible con el lenguaje XPath. Para obtener más información, consulte [Referencia con XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Ejemplo**:

* Fecha actual: **default=&quot;GetDate()&quot;**
* Contador: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  En este ejemplo, el valor predeterminado se construye usando la concatenación de una cadena y llamando a la función **CounterValue** con un nombre de contador gratuito. El número devuelto se incrementa en uno en cada inserción.

  >[!NOTE]
  >
  >En la consola del cliente de Adobe Campaign, vaya a la carpeta **[!UICONTROL Administration > Counters]** del Explorador para administrar los contadores.

Para vincular un valor predeterminado a un campo, puede usar `<default>` o `<sqldefault>`   field.

`<default>` : permite rellenar previamente el campo con un valor predeterminado al crear entidades. El valor no será un valor SQL predeterminado.

`<sqldefault>` : permite tener un valor agregado al crear un campo. Este valor aparece como un resultado SQL. Durante una actualización de esquema, este valor solo afecta a los registros nuevos.

### Enumeraciones {#enumerations}

#### Abrir enumeración {#free-enumeration}

La propiedad **userEnum** permite definir una enumeración abierta para almacenar y mostrar los valores introducidos mediante este campo.

La sintaxis es la siguiente:

`userEnum="name of enumeration"`

Estos valores se muestran en una lista desplegable del formulario de entrada:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>En la consola del cliente de Adobe Campaign, vaya a la carpeta **[!UICONTROL Administration > Enumerations]** del explorador para administrar las enumeraciones.

#### Establecer enumeración {#set-enumeration}

La propiedad **enum** le permite definir una enumeración fija utilizada cuando se conoce de antemano la lista de valores posibles.

El atributo **enum** hace referencia a la definición de una clase de enumeración rellenada en el esquema fuera del elemento principal.

Las enumeraciones permiten al usuario seleccionar un valor de una lista desplegable en lugar de introducir el valor en un campo de entrada normal:

![](assets/d_ncs_integration_schema_enum.png)

Ejemplo de una declaración de enumeración en el esquema de datos:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Se declara una enumeración fuera del elemento principal mediante el elemento **`<enumeration>`**.

Las propiedades de la enumeración son las siguientes:

* **baseType**: tipo de datos asociados con los valores
* **label**: descripción de la enumeración
* **nombre**: nombre de la enumeración
* **default**: valor predeterminado de la enumeración

Los valores de enumeración se declaran en el elemento **`<value>`** con los atributos siguientes:

* **name**: nombre del valor almacenado internamente
* **label**: etiqueta mostrada en la interfaz gráfica

#### enumeración dbenum {#dbenum-enumeration}

*La propiedad **dbenum** permite definir una enumeración cuyas propiedades son similares a las de la propiedad **enum**.

Sin embargo, el atributo **name** no almacena el valor internamente, sino que almacena un código que permite ampliar las tablas correspondientes sin modificar su esquema.

Esta enumeración se utiliza para especificar la naturaleza de las campañas, por ejemplo.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Ejemplo {#example}

A continuación, se muestra un ejemplo de esquema con las propiedades rellenadas:

```sql
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Colecciones {#collections}

Una colección es una lista de elementos con el mismo nombre y el mismo nivel jerárquico.

El atributo **unbound** con el valor &quot;true&quot; permite rellenar un elemento de colección.

**Ejemplo**: definición del elemento de colección **`<group>`** en el esquema.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Con proyección del contenido XML:

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## Hacer referencia con XPath {#referencing-with-xpath}

El lenguaje XPath se utiliza en Adobe Campaign para hacer referencia a un elemento o atributo perteneciente a un esquema de datos.

XPath es una sintaxis que permite localizar un nodo en el árbol de un documento XML.

Los elementos se designan por su nombre y los atributos se designan por el nombre precedido del carácter “@”.

**Ejemplo**:

* **@email**: selecciona el correo electrónico,
* **location/@city**: selecciona el atributo &quot;city&quot; en el elemento **`<location>`**
* **../@email**: selecciona la dirección de correo electrónico del elemento principal del elemento actual
* **group`[1]/@label`**: selecciona el atributo &quot;label&quot; que es el elemento secundario del primer elemento de colección **`<group>`**
* **group`[@label='test1']`**: selecciona el atributo &quot;label&quot; que es el elemento secundario de **`<group>`** y contiene el valor &quot;test1&quot;

>[!NOTE]
>
>Se añade una restricción adicional cuando la ruta cruza un subelemento. En este caso, la siguiente expresión debe colocarse entre corchetes:
>
>* **ubicación/@city** no es válida; use **`[location/@city]`**
>* **`[@email]`** y **@email** son equivalentes
>

También es posible definir expresiones complejas, como las siguientes operaciones aritméticas:

* **@gender+1**: agrega 1 al contenido del atributo **gender**,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: construye una cadena tomando el valor de la dirección de correo electrónico agregada a la fecha de creación entre paréntesis (para el tipo de cadena, ponga la constante entre comillas).

Se han añadido funciones de alto nivel a las expresiones para enriquecer el potencial de este lenguaje.

Puede acceder a la lista de funciones disponibles a través de cualquier editor de expresiones en la consola del cliente de Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Ejemplo**:

* **GetDate()**: devuelve la fecha actual
* **Year(@created)**: devuelve el año de la fecha contenida en el atributo &quot;created&quot;
* **GetEmailDomain(@email)**: devuelve el dominio de la dirección de correo electrónico

## Creación de una cadena a través de la cadena de cálculo {#building-a-string-via-the-compute-string}

Una **Compute string** es una expresión XPath que se usa para construir una cadena que representa un registro en una tabla asociada con el esquema. **Compute string** se utiliza principalmente en la interfaz gráfica para mostrar la etiqueta de un registro seleccionado.

**Compute string** se define a través del elemento **`<compute-string>`** en el elemento principal del esquema de datos. Un atributo **expr** contiene una expresión XPath para calcular la presentación.

**Ejemplo**: calcule la cadena de la tabla de destinatarios.

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultado de la cadena calculada para un destinatario: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Si el esquema no contiene una Compute string, se rellena una Compute string de forma predeterminada con los valores de la clave principal del esquema.


## Más información

Examine los siguientes vínculos para obtener más información:

* [Introducción a los esquemas](about-schema-reference.md)
* [Asignación de base de datos](database-mapping.md)
* [Administración de vínculos](database-links.md)
* [Administración de claves](database-keys.md)
* [Modelo de datos de Campaign](about-data-model.md)