---
solution: Campaign Classic
product: campaign
title: Asistente para nuevo campo
description: Asistente para nuevo campo
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---


# Asistente para nuevo campo{#new-field-wizard}

Un asistente al que se puede acceder mediante **[!UICONTROL Tools > Advanced > Add new fields]** permite agregar uno o más campos a una tabla de la base de datos.

Al validar el asistente se actualiza el esquema de extensión de la tabla que se va a ampliar y se inicia la secuencia de comandos SQL para modificar la estructura física de la base de datos.

Este asistente tiene la ventaja de agregar rápidamente un campo sin necesidad de conocer la estructura de un esquema de datos.

La principal desventaja es la limitación de los datos y las propiedades que se van a ampliar.

Las pantallas del asistente contienen los siguientes pasos:

1. La primera página permite introducir el nombre del esquema que se va a ampliar y la Área de nombres del esquema de extensión en el que se guardarán las modificaciones:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La página siguiente permite especificar las propiedades del campo que se va a agregar.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Para confirmar los cambios, haga clic en el botón **[!UICONTROL Finish]**.

En nuestro ejemplo, se crea automáticamente un archivo de extensión llamado &quot;cus:destinatario&quot; y se ejecuta la secuencia de comandos SQL correspondiente:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>De forma predeterminada, los campos agregados se declaran con la propiedad **user** (con el valor &quot;true&quot;). Esto le permite mostrar y editar el campo en el formulario de entrada del esquema extendido mediante un control de tipo &quot;treeEdit&quot; (consulte Formulario de entrada).

