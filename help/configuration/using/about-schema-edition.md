---
solution: Campaign Classic
product: campaign
title: Acerca de la edición de esquema
description: Introducción a la edición de esquema
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 9%

---


# Acerca de la edición de esquema{#about-schema-edition}

Adobe Campaign emplea esquemas de datos para:

* Definir el modo en que los objetos de datos de la aplicación están vinculados a las tablas de bases de datos subyacentes.
* Definir vínculos entre los diferentes objetos de datos dentro de la aplicación de Campaign.
* Definir y describir los campos individuales incluidos en cada objeto.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte [esta sección](https://helpx.adobe.com/es/campaign/kb/acc-datamodel.html).

## Ampliación o creación de esquemas {#extending-or-creating-schemas}

Para añadir un campo, índice u otro elemento a uno de los esquemas de datos principales de Campaign, como la tabla de destinatarios (nms:recipient), debe ampliar ese esquema. Para obtener más información, consulte la sección [Ampliación de un esquema](../../configuration/using/extending-a-schema.md) .

Para añadir un tipo de datos completamente nuevo que no exista de forma predeterminada en Adobe Campaign (por ejemplo, una tabla de contratos), puede crear un esquema personalizado directamente. Para obtener más información, consulte la sección [Esquemas de datos](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_1.png)

Una vez que haya ampliado o creado un esquema para trabajar, la práctica recomendada es definir sus elementos de contenido XML en el mismo orden en que aparecen a continuación.

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

Al definir campos, puede utilizar esta enumeración de la siguiente manera:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>También puede utilizar enumeraciones administradas por el usuario (normalmente en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) para especificar los valores de un campo determinado. Se trata de enumeraciones globales eficaces y una mejor opción si la enumeración puede utilizarse fuera del esquema específico en el que está trabajando.

Para obtener más información sobre las enumeraciones, consulte las secciones [Enumerations](../../configuration/using/schema-structure.md#enumerations) y [`<enumeration>` element](../../configuration/using/schema/enumeration.md) .

## Índice {#index}

Los índices son los primeros elementos declarados en el elemento principal del esquema.

Pueden ser únicos o no, y hacen referencia a uno o más campos.

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

Para obtener más información sobre índices, consulte la sección [Campos indexados](../../configuration/using/database-mapping.md#indexed-fields) .

## Claves {#keys}

Cada tabla debe tener al menos una clave y, a menudo, se establece automáticamente en el elemento principal del esquema mediante el atributo **@autopk=true** establecido en &quot;true&quot;.

La clave principal también se puede definir utilizando el atributo **internal**.

Ejemplo:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

En este ejemplo, en lugar de permitir que el atributo **@autopk** cree una clave principal predeterminada denominada &quot;id&quot;, especificamos nuestra propia clave principal &quot;householdId&quot;.

>[!IMPORTANT]
>
>Al crear un nuevo esquema o durante una ampliación de esquema, se debe mantener el mismo valor de secuencia de clave principal (@pkSequence) para todo el conjunto.

Para obtener más información sobre las claves, consulte la sección [Administración de claves](../../configuration/using/database-mapping.md#management-of-keys) .

## Atributos (campos) {#attributes--fields-}

Los atributos permiten definir los campos que conforman el objeto de datos. Puede utilizar el botón **[!UICONTROL Insert]** de la barra de herramientas de edición de esquema para soltar plantillas de atributos vacías en el XML donde se encuentra el cursor. Para obtener más información, consulte la sección [Esquemas de datos](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_2.png)

La lista completa de atributos está disponible en la sección [`<attribute>` element](../../configuration/using/schema/attribute.md) . Estos son algunos de los atributos más utilizados:

* **@advanced**
* **@dataPolicy**
* **@por defecto**
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

   Para ver una tabla con las asignaciones para los tipos de datos generados por Adobe Campaign para los diferentes sistemas de administración de bases de datos, consulte la sección [Mapping the types of Adobe Campaign/DBMS data](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) .

Para obtener más información sobre cada atributo, consulte la sección [Descripción del atributo](../../configuration/using/schema/attribute.md).

### Ejemplos {#examples}

Ejemplo de definición de un valor predeterminado:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Ejemplo de uso de un atributo común como plantilla para un campo también marcado como obligatorio:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Ejemplo de un campo calculado que está oculto con el atributo **@advanced** :

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Ejemplo de un campo XML también almacenado en un campo SQL y que tiene un atributo **@dataPolicy**.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Aunque la mayoría de los atributos están vinculados según una cardinalidad 1-1 a un campo físico de la base de datos, este no es el caso de los campos XML o los campos calculados.\
>Un campo XML se almacena en un campo memo (&quot;mData&quot;) de la tabla.\
>Sin embargo, un campo calculado se crea dinámicamente cada vez que se inicia una consulta, por lo que solo existe en la capa aplicativa.

## Vínculos {#links}

Los vínculos son algunos de los últimos elementos del elemento principal del esquema. Definen cómo se relacionan todos los distintos esquemas de la instancia entre sí.

Los vínculos se declaran en el esquema que contiene la **clave externa** de la tabla a la que están vinculados.

Hay tres tipos de cardinalidad: 1-1, 1-N y N-N. Es el tipo 1-N que se utiliza de forma predeterminada.

### Ejemplos {#examples-1}

Ejemplo de un vínculo 1-N entre la tabla de destinatarios (esquema predeterminado) y una tabla de transacciones personalizadas:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Ejemplo de un vínculo 1-1 entre un esquema personalizado &quot;Car&quot; (en el espacio de nombres &quot;cus&quot;) y la tabla de destinatarios:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Ejemplo de un vínculo externo entre la tabla de destinatarios y una tabla de direcciones basada en la dirección de correo electrónico y no en una clave principal:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Aquí &quot;xpath-dst&quot; corresponde a la clave principal en el esquema de destino y &quot;xpath-src&quot; corresponde a la clave externa en el esquema de origen.

## Pista de auditoría {#audit-trail}

Un elemento útil que puede querer incluir en la parte inferior del esquema es un elemento de seguimiento (pista de auditoría).

Utilice el ejemplo siguiente para incluir campos relacionados con la fecha de creación, el usuario que creó los datos, la fecha y el autor de la última modificación para todos los datos de la tabla:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Actualización de la estructura de la base de datos {#updating-the-database-structure}

Una vez completados y guardados los cambios, cualquier cambio que pueda afectar a la estructura SQL debe aplicarse a la base de datos. Para ello, utilice el asistente de actualización de la base de datos.

![](assets/schemaextension_getting_started_3.png)

Para obtener más información, consulte la sección [Actualización de la estructura de la base de datos](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Cuando las modificaciones no afectan a la estructura de la base de datos, solo es necesario volver a generar los esquemas. Para ello, seleccione los esquemas que desea actualizar, haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]** . Para obtener más información, consulte la sección [Regeneración de esquemas](../../configuration/using/regenerating-schemas.md) .

