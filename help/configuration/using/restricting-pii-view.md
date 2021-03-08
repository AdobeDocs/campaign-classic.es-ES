---
solution: Campaign Classic
product: campaign
title: Restricción de la vista PII
description: Restricción de la vista PII
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---


# Restringir vista de IP{#restricting-pii-view}

## Información general {#overview}

Algunos clientes necesitan que los usuarios de marketing puedan acceder a los registros de datos, pero no desean que vean información de identificación personal (PII), como nombre, apellido o dirección de correo electrónico. Adobe Campaign propone una forma de proteger la privacidad e impedir que los operadores de campaña habituales utilicen incorrectamente los datos.

## Implementación {#implementation}

Se ha añadido a los esquemas un nuevo atributo que se puede aplicar a cualquier elemento o atributo, que complementa el atributo existente **[!UICONTROL visibleIf]** . Este atributo es: **[!UICONTROL accessibleIf]** . Cuando contiene una expresión XTK relacionada con el contexto de usuario actual, puede aprovechar **[!UICONTROL HasNamedRight]** o **[!UICONTROL $(login)]** , por ejemplo.

Puede encontrar una muestra de una extensión de esquema de destinatario que muestra este uso a continuación:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Las propiedades principales son:

* **[!UICONTROL visibleIf]** : oculta los campos de los metadatos, por lo que no se puede acceder a ellos desde una vista de esquema, una selección de columnas o un generador de expresiones. Sin embargo, esto no oculta ningún dato, si el nombre del campo se introduce manualmente en una expresión, el valor aparecerá.
* **[!UICONTROL accessibleIf]** : oculta los datos (reemplazándolos por valores vacíos) de la consulta resultante. Si visibleIf está vacío, obtiene la misma expresión que **[!UICONTROL accessibleIf]** .

Estas son las consecuencias de utilizar este atributo en Campaign:

* Los datos no se mostrarán mediante el editor de consultas genérico de la consola.
* Los datos no serán visibles en las listas de información general ni en la lista de registros (consola).
* Los datos pasarán a ser de solo lectura en la vista detallada.
* Los datos solo se pueden utilizar dentro de filtros (lo que significa que, al usar algunas estrategias de dicotomía, aún puede adivinar los valores).
* Cualquier expresión creada con un campo restringido también se verá restringida: lower(@email) se vuelve tan accesible como @email.
* En un flujo de trabajo, puede añadir la columna restringida a la población objetivo como una columna adicional de la transición, pero sigue siendo inaccesible para los usuarios de Adobe Campaign.
* Al almacenar la población de destino en un grupo (lista), las características de los campos almacenados son las mismas que la fuente de datos.
* El código JS no puede acceder a los datos de forma predeterminada.

## Recomendaciones {#recommendations}

En cada envío, las direcciones de correo electrónico se copian en las tablas **[!UICONTROL broadLog]** y **[!UICONTROL forecastLog]** : como consecuencia, estos campos también deben protegerse.

A continuación se muestra un ejemplo de la extensión de la tabla de registro para implementar esto:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Esta restricción se aplica a los usuarios no técnicos: un usuario técnico, con permisos relacionados, podrá recuperar datos. Por lo tanto, este método no es 100% seguro.

