---
product: campaign
title: Estructura del esquema
description: Estructura del esquema
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 12%

---

# Estructura del esquema{#schema-structure}

![](../../assets/v7-only.svg)

La estructura básica de un `<srcschema>` es el siguiente:

```
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

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Permita utilizar el siguiente contenido XML para ilustrar la estructura de un esquema de datos:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Con su esquema de datos correspondiente:

```
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

Los elementos **`<attribute>`** y **`<element>`** que siguen al elemento principal permiten definir las ubicaciones y los nombres de los elementos de datos en la estructura XML.

En nuestro esquema de ejemplo, estos son:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Deben respetarse las siguientes normas:

* Cada **`<element>`** y **`<attribute>`** debe identificarse por su nombre a través de la variable **name** atributo.

   >[!IMPORTANT]
   >
   >El nombre del elemento debe ser conciso, preferiblemente en inglés, e incluir solo caracteres autorizados de acuerdo con las reglas de nomenclatura XML.

* Solo **`<element>`** Los elementos pueden contener **`<attribute>`** elementos y **`<element>`** elementos de la estructura XML.
* Un **`<attribute>`** elemento debe tener un nombre único dentro de un **`<element>`**.
* El uso de **`<elements>`** en cadenas de datos multilínea se recomienda.

## Tipos de datos {#data-types}

El tipo de datos se introduce mediante la variable **type** en la variable **`<attribute>`** y **`<element>`** elementos.

Una lista detallada está disponible en la descripción del [`<attribute>` element](../../configuration/using/schema/attribute.md) y [`<element>` element](../../configuration/using/schema/element.md)).

Cuando este atributo no se rellena, **string** es el tipo de datos predeterminado a menos que el elemento contenga elementos secundarios. Si es así, solo se utiliza para estructurar los elementos de forma jerárquica (**`<location>`** en nuestro ejemplo).

Los esquemas admiten los siguientes tipos de datos:

* **string**: cadena de caracteres. Ejemplos: un nombre, un pueblo, etc.

   El tamaño se puede especificar mediante la variable **length** (opcional, valor predeterminado &quot;255&quot;).

* **booleano**: Campo booleano. Ejemplo de valores posibles: true/false, 0/1, sí/no, etc.
* **byte**, **short**, **long**: enteros (1 byte, 2 bytes, 4 bytes). Ejemplos: edad, número de cuenta, número de puntos, etc.
* **double**: número de coma flotante de precisión doble. Ejemplos: precio, tasa, etc.
* **date**, **datetime**: fechas y fechas + horas. Ejemplos: fecha de nacimiento, fecha de compra, etc.
* **datetimenotz**: fecha + hora sin datos de zona horaria.
* **timespan**: duraciones. Ejemplo: antigüedad.
* **memo**: campos de texto largos (varias líneas). Ejemplos: una descripción, un comentario, etc.
* **uuid**: campos &quot;identificador único&quot; para admitir un GUID (solo compatible con Microsoft SQL Server).

   >[!NOTE]
   >
   >Para contener un **uuid** en motores que no sean Microsoft SQL Server, la función &quot;newuuid()&quot; debe añadirse y completarse con su valor predeterminado.

Este es un ejemplo de esquema con los tipos introducidos:

```
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
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Cadena<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 si Unicode)<br /> </td> 
   <td> VARCHAR (EL CARÁCTER VARCHAR ESTABLECE UNICODE si Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR si Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
   <td> NUMÉRICA(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
   <td> NUMÉRICA(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Corto<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicada<br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTE<br /> </td> 
   <td> FLOTE<br /> </td> 
   <td> DOBLE<br /> </td> 
   <td> FLOTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Largo<br /> </td> 
   <td> ENTERO<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> ENTERO<br /> </td> 
   <td> ENTERO<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NÚMERO(20)<br /> </td> 
   <td> NUMÉRICA(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Fecha<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> MARCA DE TIEMPO<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Tiempo<br /> </td> 
   <td> TIEMPO<br /> </td> 
   <td> FLOTE<br /> </td> 
   <td> TIEMPO<br /> </td> 
   <td> TIEMPO<br /> </td> 
   <td> FLOTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> MARCA DE TIEMPO<br /> </td> 
   <td> MARCA DE TIEMPO<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> FECHA<br /> </td> 
   <td> MARCA DE TIEMPO<br /> </td> 
   <td> MARCA DE TIEMPO<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> PRECISIÓN DOBLE<br /> </td> 
   <td> FLOTE<br /> </td> 
   <td> FLOTE<br /> </td> 
   <td> DOBLE<br /> </td> 
   <td> FLOTE<br /> </td> 
  </tr> 
  <tr> 
   <td> Nota<br /> </td> 
   <td> TEXTO<br /> </td> 
   <td> CLOB (NCLOB si Unicode)<br /> </td> 
   <td> CLOB (CLOB CHARACTER SET UNICODE if Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT si Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGEN<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Propiedades {#properties}

La variable **`<elements>`** y **`<attributes>`** los elementos del esquema de datos se pueden enriquecer con varias propiedades. Puede rellenar una etiqueta para describir el elemento actual.

### Etiquetas y descripciones {#labels-and-descriptions}

* La variable **label** permite introducir una descripción breve.

   >[!NOTE]
   >
   >La etiqueta está asociada al idioma actual de la instancia.

   **Ejemplo**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   La etiqueta se puede ver desde el formulario de entrada de la consola del cliente de Adobe Campaign:

   ![](assets/d_ncs_integration_schema_label.png)

* La variable **desc** permite introducir una descripción larga.

   La descripción se puede ver desde el formulario de entrada en la barra de estado de la ventana principal de la consola del cliente de Adobe Campaign.

   >[!NOTE]
   >
   >La descripción está asociada al idioma actual de la instancia.

   **Ejemplo**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Valores predeterminados {#default-values}

La variable **default** permite definir una expresión que devuelve un valor predeterminado en la creación de contenido.

El valor debe ser una expresión compatible con el lenguaje XPath. Para obtener más información, consulte [Referencia con XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Ejemplo**:

* Fecha actual: **default=&quot;GetDate()&quot;**
* Contador: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   En este ejemplo, el valor predeterminado se construye utilizando la concatenación de una cadena y llamando a la función **ContadorValor** con un nombre de contador libre. El número devuelto se incrementa en uno en cada inserción.

   >[!NOTE]
   >
   >En la consola del cliente de Adobe Campaign, la variable **[!UICONTROL Administration>Counters]** se utiliza para administrar los contadores.

Para vincular un valor predeterminado a un campo, puede utilizar la variable `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : permite rellenar previamente el campo con un valor predeterminado al crear entidades. El valor no es un valor SQL predeterminado.

`<sqldefault>` : permite tener un valor añadido al crear un campo. Este valor aparece como un resultado SQL. Durante una actualización de esquema, solo los registros nuevos se verán afectados por este valor.

### Enumeraciones {#enumerations}

#### Enumeración libre {#free-enumeration}

La variable **userEnum** property permite definir una enumeración libre para memorizar y mostrar los valores introducidos mediante este campo. La sintaxis es la siguiente:

**userEnum=&quot;name of enumeration&quot;**

El nombre dado a la enumeración puede elegirse libremente y compartirse con otros campos.

Estos valores se muestran en una lista desplegable del formulario de entrada:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>En la consola del cliente de Adobe Campaign, la variable **[!UICONTROL Administration > Enumerations]** se utiliza para administrar las enumeraciones.

#### Establezca la enumeración {#set-enumeration}

La variable **enum** permite definir una enumeración fija que se utiliza cuando se conoce de antemano la lista de valores posibles.

La variable **enum** hace referencia a la definición de una clase de enumeración rellenada en el esquema fuera del elemento principal.

Las enumeraciones permiten al usuario seleccionar un valor de una lista desplegable en lugar de introducir el valor en un campo de entrada normal:

![](assets/d_ncs_integration_schema_enum.png)

Ejemplo de una declaración de enumeración en el esquema de datos:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Se declara una enumeración fuera del elemento principal mediante la variable **`<enumeration>`** elemento.

Las propiedades de la enumeración son las siguientes:

* **baseType**: tipo de datos asociados a los valores,
* **label**: descripción de la enumeración,
* **name**: nombre de la enumeración,
* **default**: valor predeterminado de la enumeración.

Los valores de enumeración se declaran en la variable **`<value>`** con los siguientes atributos:

* **name**: nombre del valor almacenado internamente,
* **label**: etiqueta mostrada a través de la interfaz gráfica.

#### enumeración dbenum {#dbenum-enumeration}

* La variable **dbenum** la propiedad permite definir una enumeración cuyas propiedades son similares a las del **enum** propiedad.

   Sin embargo, la variable **name** no almacena el valor internamente, almacena un código que le permite ampliar las tablas correspondientes sin modificar su esquema.

   Los valores se definen mediante la variable **[!UICONTROL Administration>Enumerations]** nodo .

   Esta enumeración se utiliza para especificar la naturaleza de las campañas, por ejemplo.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Ejemplo {#example}

A continuación, se muestra un ejemplo de esquema con las propiedades rellenadas:

```
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

La variable **unbound** con el valor &quot;true&quot; permite rellenar un elemento de colección.

**Ejemplo**: definición de **`<group>`** elemento de colección en el esquema.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Con proyección del contenido XML:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Referencia con XPath {#referencing-with-xpath}

El lenguaje XPath se utiliza en Adobe Campaign para hacer referencia a un elemento o atributo perteneciente a un esquema de datos.

XPath es una sintaxis que permite localizar un nodo en el árbol de un documento XML.

Los elementos se designan por su nombre y los atributos se designan por el nombre precedido del carácter “@”.

**Ejemplo**:

* **@email**: selecciona el correo electrónico,
* **location/@city**: selecciona el atributo &quot;city&quot; en la sección **`<location>`** element
* **../@email**: selecciona la dirección de correo electrónico del elemento principal del elemento actual
* **grupo`[1]/@label`**: selecciona el atributo &quot;label&quot; que es el secundario del primero **`<group>`** elemento de colección
* **grupo`[@label='test1']`**: selecciona el atributo &quot;label&quot; que es el elemento secundario de la variable **`<group>`** y contiene el valor &quot;test1&quot;

>[!NOTE]
>
>Se agrega una restricción adicional cuando la ruta cruza un subelemento. En este caso, la siguiente expresión debe colocarse entre corchetes:
>
>* **location/@city** no sea válido; utilice **`[location/@city]`**
>* **`[@email]`** y **@email** son equivalentes

>


También es posible definir expresiones complejas, como las siguientes operaciones aritméticas:

* **@gender+1**: agrega 1 al contenido del **sexo** atributo,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: crea una cadena tomando el valor de la dirección de correo electrónico añadida a la fecha de creación entre paréntesis (para el tipo de cadena, ponga la constante entre comillas).

Se han añadido funciones de alto nivel a las expresiones para enriquecer el potencial de este idioma.

Puede acceder a la lista de funciones disponibles a través de cualquier editor de expresiones de la consola del cliente de Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Ejemplo**:

* **GetDate()**: devuelve la fecha actual
* **Year(@created)**: devuelve el año de la fecha contenida en el atributo &quot;created&quot;.
* **GetEmailDomain(@email)**: devuelve el dominio de la dirección de correo electrónico.

## Creación de una cadena mediante la cadena de cálculo {#building-a-string-via-the-compute-string}

A **Cadena de caracteres** es una expresión XPath que se utiliza para construir una cadena que representa un registro de una tabla asociada al esquema. **Cadena de caracteres** se utiliza principalmente en la interfaz gráfica para mostrar la etiqueta de un registro seleccionado.

La variable **Cadena de caracteres** se define mediante la variable **`<compute-string>`** en el elemento principal del esquema de datos. Un **expr** contiene una expresión XPath para calcular la visualización.

**Ejemplo**: cálculo de cadena de la tabla de destinatarios.

```
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
>Si el esquema no contiene una Compute string, una Compute string se rellena de forma predeterminada con los valores de la clave principal del esquema.
