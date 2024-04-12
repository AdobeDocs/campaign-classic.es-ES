---
product: campaign
title: Recomendaciones
description: Recomendaciones
feature: Monitoring
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 11%

---

# Recomendaciones{#recommendations}



Adobe Campaign es un sistema altamente transaccional (base de datos OLTP). Esto significa que la base de datos subyacente se actualizará con frecuencia, lo que provocará una degradación del rendimiento a lo largo del tiempo. Para evitar este tipo de problemas, es necesario realizar un mantenimiento regular de la base de datos.

>[!IMPORTANT]
>
>Una base de datos solo funcionará de forma óptima si se mantiene de forma regular. El mantenimiento automático ofrecido por algunos RDBMS no es suficiente y no reemplaza el mantenimiento a fondo, como para cualquier sistema de administración transaccional de bases de datos relacionales.
>  
>Los procedimientos descritos en este documento son recomendaciones. Los planes de mantenimiento son responsabilidad del administrador de la base de datos, que debe ser su primer contacto en caso de problemas.
