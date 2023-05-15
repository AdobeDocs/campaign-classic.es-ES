---
product: campaign
title: Recomendaciones
description: Recomendaciones
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Recomendaciones{#recommendations}



Adobe Campaign es un sistema altamente transaccional (base de datos OLTP). Esto significa que la base de datos subyacente se actualizará con frecuencia, lo que provoca una degradación del rendimiento a lo largo del tiempo. Para evitar este tipo de problema, es necesario realizar un mantenimiento regular de la base de datos.

>[!IMPORTANT]
>
>Una base de datos solo funcionará de forma óptima si se mantiene de forma regular. El mantenimiento automático ofrecido por algunos RDBMS no es suficiente y no sustituye el mantenimiento en profundidad, como ocurre con los sistemas de gestión transaccional de bases de datos relacionales.
>  
>Los procedimientos descritos en este documento son recomendaciones. Los planes de mantenimiento son responsabilidad del administrador de la base de datos, que debe ser su primer contacto en caso de problemas.
