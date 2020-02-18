---
title: Acerca de la edición de esquema
seo-title: Acerca de la edición de esquema
description: Acerca de la edición de esquema
seo-description: null
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Acerca de la edición de esquema{#about-schema-edition}

Adobe Campaign utiliza esquemas de datos para:

* Definir el modo en que los objetos de datos de la aplicación están vinculados a las tablas de bases de datos subyacentes.
* Definir vínculos entre los diferentes objetos de datos dentro de la aplicación de Campaign.
* Definir y describir los campos individuales incluidos en cada objeto.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte el modelo [de datos de](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)Campaign Classic.

## Ampliación o creación de esquemas {#extending-or-creating-schemas}

Para agregar un campo o índice u otro elemento a uno de los esquemas de datos principales de Campaign, como la tabla de destinatarios (nms:destinatario), debe ampliar ese esquema. Para obtener más información sobre esto, consulte la sección [Ampliación de un esquema](../../configuration/using/extending-a-schema.md) .

Para agregar un tipo de datos completamente nuevo que no exista de forma predeterminada en Adobe Campaign (por ejemplo, una tabla de contratos), puede crear un esquema personalizado directamente. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

Una vez que haya ampliado o creado un esquema en el que trabajar, lo mejor es definir los elementos de contenido XML en el mismo orden en el que aparecen a continuación.

## Enumeraciones {#enumerations}

Las enumeraciones se definen primero, antes del elemento principal del esquema. Permiten mostrar valores en una lista para restringir las opciones que el usuario tiene para un campo determinado.

Ejemplo:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Al definir campos, puede utilizar esta enumeración de la misma manera:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>También puede utilizar enumeraciones administradas por el usuario (normalmente en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) para especificar los valores de un campo determinado. Se trata de enumeraciones globales efectivas y una mejor opción si la enumeración puede utilizarse fuera del esquema específico en el que está trabajando.

Para obtener más información sobre las enumeraciones, consulte las secciones [Enumeraciones](../../configuration/using/schema-structure.md#enumerations) y [`<enumeration>` elementos](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## Índice {#index}

Los índices son los primeros elementos declarados en el elemento principal del esquema.

Pueden ser únicos o no y hacer referencia a uno o varios campos.

Ejemplos:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

El atributo **xpath** apunta al campo del esquema que desea indexar.

>[!IMPORTANT]
>
>Es importante recordar que las ganancias de rendimiento de lectura de la consulta SQL proporcionadas por los índices también incluyen una visita de rendimiento al escribir registros. Por lo tanto, los índices deben utilizarse con precaución.

Para obtener más información sobre índices, consulte la sección Campos [](../../configuration/using/database-mapping.md#indexed-fields) indizados.

## Teclas {#keys}

Cada tabla debe tener al menos una clave, y a menudo se establece automáticamente en el elemento principal del esquema mediante el uso del atributo **@autopk=true** establecido en &quot;true&quot;.

La clave principal también se puede definir mediante el atributo **interno** .

Ejemplo:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

En este ejemplo, en lugar de permitir que el atributo **@autopk** cree una clave principal predeterminada con el nombre &quot;id&quot;, especificamos nuestra propia clave principal &quot;homeId&quot;.

>[!IMPORTANT]
>
>Al crear un nuevo esquema o durante una ampliación de esquema, se debe mantener el mismo valor de secuencia de clave principal (@pkSequence) para todo el conjunto.

Para obtener más información sobre las claves, consulte la sección [Administración de claves](../../configuration/using/database-mapping.md#management-of-keys) .

## Atributos (campos) {#attributes--fields-}

Los atributos permiten definir los campos que conforman el objeto de datos. Puede utilizar el **[!UICONTROL Insert]** botón de la barra de herramientas de edición de esquema para colocar plantillas de atributos vacías en el XML donde se encuentra el cursor. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_2.png)

La lista completa de atributos está disponible en la sección de [`<attribute>` elementos](../../configuration/using/elements-and-attributes.md#attribute--element) . Estos son algunos de los atributos más utilizados:

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

   Para ver una tabla con las asignaciones de los tipos de datos generados por Adobe Campaign para los distintos sistemas de administración de bases de datos, consulte la sección [Asignación de los tipos de datos](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) de Adobe Campaign/DBMS.

Para obtener más información sobre cada atributo, consulte la sección Descripción [del](../../configuration/using/elements-and-attributes.md#attribute-description) atributo.

### Ejemplos {#examples}

Ejemplo de definición de un valor predeterminado:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Ejemplo de uso de un atributo común como plantilla para un campo también marcado como obligatorio:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Ejemplo de un campo calculado que está oculto mediante el atributo **@advanced** :

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Ejemplo de un campo XML también almacenado en un campo SQL y que tiene un atributo **@dataPolicy** .

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Aunque la mayoría de los atributos están vinculados según una cardinalidad 1-1 a un campo físico de la base de datos, no es el caso de los campos XML o los campos calculados.\
>Un campo XML se almacena en un campo memo (&quot;mData&quot;) de la tabla.\
>Sin embargo, un campo calculado se crea dinámicamente cada vez que se inicia una consulta, por lo que sólo existe en la capa aplicativa.

## Vínculos {#links}

Los vínculos son algunos de los últimos elementos del elemento principal del esquema. Definen cómo se relacionan todos los distintos esquemas de la instancia entre sí.

Los vínculos se declaran en el esquema que contiene la clave **** externa de la tabla a la que está vinculado.

Hay tres tipos de cardinalidad: 1-1, 1-N y N-N. Es el tipo 1-N que se utiliza de forma predeterminada.

### Ejemplos {#examples-1}

Ejemplo de un vínculo 1-N entre la tabla del destinatario (esquema predeterminado) y una tabla de transacciones personalizadas:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Ejemplo de un vínculo 1-1 entre un esquema personalizado &quot;Car&quot; (en el espacio de nombres &quot;cus&quot;) y la tabla de destinatarios:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Ejemplo de una unión externa entre la tabla del destinatario y una tabla de direcciones basada en la dirección de correo electrónico y no en una clave principal:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Aquí &quot;xpath-dst&quot; corresponde a la clave principal en el esquema de destino y &quot;xpath-src&quot; corresponde a la clave externa en el esquema de origen.

## Audit trail {#audit-trail}

Un elemento útil que puede desear incluir en la parte inferior del esquema es un elemento de seguimiento (pista de auditoría).

Utilice el ejemplo siguiente para incluir campos relacionados con la fecha de creación, el usuario que creó los datos, la fecha y el autor de la última modificación de todos los datos de la tabla:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Actualización de la estructura de la base de datos {#updating-the-database-structure}

Una vez que los cambios se hayan completado y guardado, cualquier cambio que pueda afectar a la estructura SQL debe aplicarse a la base de datos. Para ello, utilice el asistente para la actualización de la base de datos.

![](assets/schemaextension_getting_started_3.png)

Para obtener más información sobre esto, consulte la sección [Actualización de la estructura](../../configuration/using/updating-the-database-structure.md) de la base de datos.

>[!NOTE]
>
>Cuando las modificaciones no afectan a la estructura de la base de datos, sólo es necesario volver a generar esquemas. Para ello, seleccione los esquemas que desea actualizar, haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]** . For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

