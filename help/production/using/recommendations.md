---
title: Recomendaciones
seo-title: Recomendaciones
description: Recomendaciones
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 3%

---


# Recomendaciones{#recommendations}

Adobe Campaign es un sistema altamente transaccional (base de datos OLTP). Esto significa que la base de datos subyacente se actualizará con frecuencia, lo que provocará una degradación del rendimiento a lo largo del tiempo. Para evitar este tipo de problemas, es necesario realizar un mantenimiento regular de la base de datos.

>[!CAUTION]
>
>Una base de datos sólo tendrá un rendimiento óptimo si se mantiene con regularidad. El mantenimiento automático ofrecido por algunos RDBMS no es suficiente y no sustituye el mantenimiento a fondo, como ocurre con los sistemas de gestión de transacciones de bases de datos relacionales.
>  
>Los procedimientos descritos en este documento son recomendaciones. Los planes de mantenimiento son responsabilidad del administrador de la base de datos, que debe ser su primer contacto en caso de problemas.

