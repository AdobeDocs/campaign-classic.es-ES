---
product: campaign
title: Prácticas recomendadas de importación y exportación
description: Obtenga más información acerca las prácticas recomendadas que seguir al importar o exportar datos
feature: Data Management
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
TQID: https://experienceleague.adobe.com/fHl4uUPkoQ48OuUI41YMFQK6J6X6YiIjERUeNKM0904
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 543
ht-degree: 99%

---

# Prácticas recomendadas de importación y exportación {#import-export-best-practices}



Tenga cuidado y siga las sencillas reglas detalladas debajo, ya que le pueden ayudar a garantizar la coherencia de los datos en la base de datos y a evitar errores comunes durante la actualización o las exportaciones de datos.

## Uso de plantillas de flujo de trabajo {#using-import-templates}

La mayoría de los flujos de trabajo destinados a la importación de datos deben contener las siguientes actividades: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]** y **[!UICONTROL Update data]**.

El uso de plantillas de flujo de trabajo facilita la preparación de importaciones similares y garantiza la coherencia de los datos en la base de datos.

En muchos proyectos, las importaciones se crean sin actividad de **[!UICONTROL Deduplication]** porque los archivos utilizados en el proyecto no tienen duplicados. Los duplicados aparecen en ocasiones al importar archivos diferentes. En este caso, la deduplicación resulta difícil. Por lo tanto, la deduplicación es una buena precaución en todos los flujos de trabajo de importación.

No dé por hecho que los datos entrantes son coherentes y correctos, o que el departamento de TI o el supervisor de Adobe Campaign se pueden encargar de ello. Durante el proyecto, tenga en cuenta la limpieza de los datos. Deduplique, reconcilie y mantenga la coherencia al importar datos.

Un ejemplo de una plantilla de flujo de trabajo genérica diseñada para importar datos está disponible en el [Ejemplo: Plantilla de flujo de trabajo para importar la sección datos](../../platform/using/creating-import-export-templates.md).

## Uso de formatos de archivo plano {#using-flat-file-formats}

El formato más eficaz para las importaciones es un archivo plano. Los archivos planos se pueden importar en modo masivo a nivel de base de datos.

Por ejemplo:

* Separador: tabulación o punto y coma
* Primera línea con encabezados
* Sin delimitador de cadenas
* Formato de fecha:`YYYY/MM/DD HH:mm:SS`

Ejemplo de archivo para importar:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Uso de compresión {#using-compression}

Utilice archivos comprimidos para importar y exportar cuando sea posible. GZIP es compatible de forma predeterminada. Puede añadir preprocesamiento al importar archivos o posprocesamiento al extraer datos, respectivamente, en las actividades de flujo de trabajo **[!UICONTROL Load file]** y **[!UICONTROL Extract file]**.

**Temas relacionados:**

* [Actividad de carga de datos (archivos)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html?lang=es){target="_blank"}
* [Actividad de extracción de datos (archivo)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=es){target="_blank"}.

## Importación en modo Delta {#importing-in-delta-mode}

Las importaciones regulares deben realizarse en modo delta. Esto significa que solo se envían datos modificados o nuevos a Adobe Campaign, en lugar de toda la tabla de una sentada.

Las importaciones completas deben utilizarse únicamente para la carga inicial.

## Mantenimiento de coherencia {#maintaining-consistency}

Para mantener la coherencia de los datos en la base de datos de Adobe Campaign, siga los principios siguientes:

* Si los datos importados coinciden con una tabla de referencia de Adobe Campaign, se deben reconciliar con esa tabla en el flujo de trabajo. Los registros que no coinciden deben ser rechazados.
* Asegúrese de que los datos importados siempre estén **&quot;normalizados&quot;** (correo electrónico, número de teléfono, dirección de correo directo) y que esta normalización sea fiable y no cambie con los años. Si no es así, es probable que algunos duplicados aparezcan en la base de datos y, como Adobe Campaign no proporciona herramientas para establecer correspondencias &quot;difusas&quot;, resulta muy difícil administrarlos y eliminarlos.
* Los datos transaccionales deben tener una clave de reconciliación y se deben reconciliar con los datos existentes para evitar la creación de duplicados.
* **Importación de archivos relacionados en orden**. Si la importación está compuesta por varios archivos que dependen unos de otros, el flujo de trabajo debe asegurar que los archivos se importen en el orden correcto. Si un archivo falla, los demás archivos no se importan.
* **Deduplique**, reconcilie y mantenga la coherencia al importar datos.
