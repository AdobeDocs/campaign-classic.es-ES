---
product: campaign
title: Recomendaciones
description: Recomendaciones
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Recomendaciones{#recommendations}

![](../../assets/v7-only.svg)

Adobe Campaign is a highly transactional system (OLTP database). Esto significa que la base de datos subyacente se actualizará con frecuencia, lo que provoca una degradación del rendimiento a lo largo del tiempo. Para evitar este tipo de problema, es necesario realizar un mantenimiento regular de la base de datos.

>[!IMPORTANT]
>
>A database will only perform optimally if it is maintained on a regular basis. The automatic maintenance offered by some RDBMS is not sufficient and does not replace in-depth maintenance, as for any relational database transactional management systems.
>  
>Los procedimientos descritos en este documento son recomendaciones. Maintenance plans are the responsibility of your database administrator, who must be your first contact in case of problems.
