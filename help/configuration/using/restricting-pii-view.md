---
solution: Campaign Classic
product: campaign
title: Restricción de la vista PII
description: Restricción de la vista PII
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---


# Restricción de la vista PII{#restricting-pii-view}

## Información general {#overview}

Algunos clientes necesitan que los usuarios de mercadotecnia puedan acceder a los registros de datos, pero no desean que vean Información de identificación personal (PII), como el nombre, los apellidos o la dirección de correo electrónico. Adobe Campaign propone una forma de proteger la privacidad e impedir que los operadores de campaña habituales utilicen indebidamente los datos.

## Implementación {#implementation}

Se ha agregado un nuevo atributo que se puede aplicar a cualquier elemento o atributo a las esquemas, que complementa el atributo existente **[!UICONTROL visibleIf]**. Este atributo es: **[!UICONTROL accessibleIf]** . Al contener una expresión XTK relacionada con el contexto de usuario actual, puede aprovechar **[!UICONTROL HasNamedRight]** o **[!UICONTROL $(login)]** , por ejemplo.

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

* **[!UICONTROL visibleIf]** :: oculta los campos de los metadatos, por lo que no se puede acceder a ellos desde una vista de esquema, una selección de columnas o un generador de expresiones. Sin embargo, esto no oculta ningún dato, si el nombre del campo se introduce manualmente en una expresión, se mostrará el valor.
* **[!UICONTROL accessibleIf]** :: oculta los datos (reemplazándolos por valores vacíos) de la consulta resultante. Si visibleSi está vacío, obtiene la misma expresión que **[!UICONTROL accessibleIf]**.

Estas son las consecuencias de usar este atributo en la Campaña:

* Los datos no se mostrarán con editor de consultas genérico en la consola,
* Los datos no estarán visibles en las listas de información general ni en la lista de registros (consola).
* Los datos pasarán a ser de sólo lectura en vista detallada.
* Los datos solo se podrán utilizar dentro de filtros (lo que significa que, si se utilizan algunas estrategias de dicotomía, todavía se pueden adivinar los valores).
* Cualquier expresión creada con un campo restringido también se verá restringida: lower(@email) se vuelve tan accesible como @email.
* En un flujo de trabajo, puede agregar la columna restringida a la población objetivo como una columna adicional de la transición, pero los usuarios de Adobe Campaign siguen sin tener acceso a ella.
* Al almacenar la población objetivo en un grupo (lista), las características de los campos almacenados son las mismas que la fuente de datos.
* El código JS no tiene acceso a los datos de forma predeterminada.

## Recomendaciones {#recommendations}

En cada envío, las direcciones de correo electrónico se copian en las tablas **[!UICONTROL broadLog]** y **[!UICONTROL forecastLog]**: como consecuencia, estos campos también deben protegerse.

A continuación se muestra una muestra de la extensión de la tabla de registro para implementarla:

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

