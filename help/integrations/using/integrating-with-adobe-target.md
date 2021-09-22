---
product: campaign
title: Integración con Adobe Target
description: Integración con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 91%

---

# Integración con Adobe Target{#integrating-with-adobe-target}

![](../../assets/v7-only.svg)

La integración entre Adobe Campaign y Adobe Target (Classic y Standard) en Adobe Experience Cloud le permite incluir una oferta de Adobe Target en una entrega por correo electrónico de Adobe Campaign.

El principio operativo es el siguiente: cuando un destinatario abre un correo electrónico enviado a través de Adobe Campaign, una llamada a Adobe Target le permite mostrar una versión dinámica del contenido. Esta versión dinámica se calcula según las reglas especificadas previamente al crear el correo electrónico.

Obtenga más información sobre la integración de Adobe Campaign y Adobe Target con [estas cuatro sugerencias y trucos](https://business.adobe.com/content/dam/dx/us/en/products/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>La integración solo admite imágenes estáticas. El resto del contenido no se puede personalizar.

Adobe Target puede utilizar varios tipos de datos:

* Datos del datamart de Adobe Campaign:
* Segmentos vinculados a la ID de visitante en Adobe Target, si los datos utilizados no están sujetos a limitaciones legales
* Datos de Adobe Target: agente de usuario, dirección IP, datos de geolocalización

>[!NOTE]
>
>También puede encontrar información sobre la integración entre Adobe Campaign y Adobe Target en [las páginas de ayuda de Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=es).
