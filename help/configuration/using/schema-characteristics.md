---
product: campaign
title: Características del esquema
description: Características del esquema
feature: Custom Resources
role: Data Engineer, Developer
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 4%

---

# Características del esquema{#schema-characteristics}



Las características de un esquema que hace referencia a una tabla existente son las siguientes:

* Adobe Campaign no debe modificar los objetos SQL relativos a las tablas existentes.
* Los nombres de las tablas y columnas deben especificarse explícitamente.
* Los índices deben declararse.

>[!IMPORTANT]
>
>No elimine campos en la tabla de destinatarios integrada, aunque sean inútiles. Esto puede provocar errores de comportamiento en la base de datos de Adobe Campaign.

## Atributo de vista {#the-view-attribute}

Los esquemas de Source aceptan el atributo **view** para el elemento raíz **srcSchema**. Debe utilizarse cuando se manipula Adobe Campaign en tablas personalizadas. El atributo **view=&quot;true&quot;** indica al asistente de actualización de la estructura de la base de datos que ignore este esquema. Por lo tanto, la aplicación no puede sincronizar la tabla, sus columnas y sus índices con el esquema correspondiente.

Cuando este atributo se establece en **true**, el esquema solo se usa para generar consultas SQL con el fin de acceder a los datos de esta tabla.

## Nombres de tablas y columnas {#names-of-tables-and-columns}

Cuando el asistente de actualización de tablas crea las tablas, los nombres de las tablas y columnas se generan automáticamente en función de los nombres de los respectivos esquemas y atributos. Sin embargo, es posible forzar el uso de nombres SQL introduciendo los siguientes atributos:

* **sqltable** dentro del elemento principal del esquema, para especificar la tabla,
* **sqlname** dentro de cada atributo, para especificar las columnas.

**Ejemplo**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

En este ejemplo, si no se hubieran especificado explícitamente los nombres de las tablas y columnas, la aplicación habría utilizado **CusIndividual** para la tabla, **lastName** y **firstName** para las columnas.

En un esquema, es posible rellenar solo parte de las columnas de una tabla existente. El usuario no podrá acceder a las columnas que no se hayan rellenado.

## Campos indexados {#indexed-fields}

Al ordenar los registros de una lista desde la consola del cliente, se obtiene un mejor rendimiento mediante la ordenación en campos indexados. Al declarar un índice en un esquema, la consola muestra los campos indexados con una línea roja debajo de la flecha de criterio de ordenación a la izquierda de la etiqueta de columna, como se muestra a continuación:

![](assets/s_ncs_integration_mapping_index.png)

En un esquema, un índice se define de la siguiente manera:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Por este motivo, es importante declarar los índices existentes de la tabla personalizada en el esquema coincidente.

Se declara implícitamente un índice para cada declaración de clave y vínculo del esquema de origen. La declaración de índice se puede evitar especificando el atributo **noDbIndex=&quot;true&quot;**:

**Ejemplo**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
