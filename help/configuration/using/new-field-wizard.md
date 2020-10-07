---
title: Asistente para nuevo campo
seo-title: Asistente para nuevo campo
description: Asistente para nuevo campo
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 5%

---


# Asistente para nuevo campo{#new-field-wizard}

Un asistente al que se puede acceder mediante **[!UICONTROL Tools > Advanced > Add new fields]** permite agregar uno o varios campos a una tabla de la base de datos.

Al validar el asistente se actualiza el esquema de extensión de la tabla que se va a ampliar y se inicia la secuencia de comandos SQL para modificar la estructura física de la base de datos.

Este asistente tiene la ventaja de agregar rápidamente un campo sin necesidad de conocer la estructura de un esquema de datos.

La principal desventaja es la limitación de los datos y las propiedades que se van a ampliar.

Las pantallas del asistente contienen los siguientes pasos:

1. La primera página permite introducir el nombre del esquema que se va a ampliar y la Área de nombres del esquema de extensión en el que se guardarán las modificaciones:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La página siguiente permite especificar las propiedades del campo que se va a agregar.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Para confirmar los cambios, haga clic en el **[!UICONTROL Finish]** botón .

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

