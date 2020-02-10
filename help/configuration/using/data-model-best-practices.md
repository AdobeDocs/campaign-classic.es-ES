---
title: Uso de la tabla Destinatarios de Adobe Campaign Classic
description: Descubra cómo utilizar la tabla de destinatarios lista para usar en Adobe Campaign Classic al diseñar su modelo de datos.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Prácticas recomendadas del modelo de datos{#data-model-best-practices}

A continuación se detallan algunas prácticas recomendadas que deben seguirse al diseñar el modelo de datos mediante tablas grandes y combinaciones complejas.

* Cuando utilice tablas de destinatarios personalizados adicionales, asegúrese de que tiene una tabla de registro dedicada para cada asignación de entrega.
* Reduzca el número de columnas, en particular identificándolas como no utilizadas.
* Optimice las relaciones del modelo de datos evitando las uniones complejas, como las uniones en varias condiciones o en varias columnas.
* Para las claves de unión, utilice siempre datos numéricos en lugar de cadenas de caracteres.
* Reduzca al máximo la profundidad de la retención de registros. Si necesita un historial más profundo, puede agregar cálculos y/o administrar tablas de registro personalizadas para almacenar un historial más grande.

Para ver prácticas recomendadas más detalladas sobre cómo optimizar el diseño de la base de datos para volúmenes más grandes, consulte Prácticas recomendadas del modelo de datos de [Campaign Classic](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).
