---
product: campaign
title: Importación y exportación de datos mediante flujos de trabajo
description: Obtenga información sobre cómo importar y exportar datos mediante flujos de trabajo en Campaign
feature: Data Management, Workflows
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Importación y exportación de datos mediante flujos de trabajo {#import-export-workflows}



## Recopilación de datos {#collecting-data-workflows}

Los flujos de trabajo pueden ser una forma útil de automatizar algunos de los procesos de importación. Tanto si se importan datos desde un archivo local como desde un SFTP, puede utilizar flujos de trabajo para estandarizar los procedimientos de gestión de datos.

### Uso de datos de una lista: Leer lista {#using-data-from-a-list--read-list}

Los datos enviados en un flujo de trabajo pueden provenir de listas, por lo que los datos se han preparado y estructurado previamente.

Esta lista puede haberse creado directamente en Adobe Campaign o importado mediante la opción **[!UICONTROL Import a list]**. Para obtener más información sobre esta opción, consulte esta [página](../../platform/using/about-generic-imports-exports.md).

Para obtener más información sobre el uso de la actividad de la lista de lectura en un flujo de trabajo, consulte [esta página](../../workflow/using/read-list.md).

### Carga de datos desde un archivo {#loading-data-from-a-file}

Los datos procesados en un flujo de trabajo se pueden extraer de un archivo estructurado para que se puedan importar en Adobe Campaign.

Puede encontrar una descripción de la actividad de datos de carga en la sección [Data loading (file)](../../workflow/using/data-loading-file.md).

Ejemplo de archivo estructurado para importar:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Una vez recopilados los datos, puede utilizarlos en sus flujos de trabajo, por ejemplo para enriquecer una entrega o actualizar la base de datos. Para obtener más información, consulte [esta página](../../workflow/using/how-to-use-workflow-data.md).

## Exportación de datos {#exporting-data-via-a-workflow}

Los flujos de trabajo pueden ser una forma útil de automatizar algunos de los procesos de exportación o de exportar conjuntos de datos precisos después de usar algunas de las actividades disponibles de administración de datos para transformar sus datos.

Las operaciones de exportación se realizan mediante una **[!UICONTROL Data extraction (file) activity]**. Para obtener más información sobre cómo configurar y utilizar la actividad, consulte [esta página](../../workflow/using/extraction-file.md).
