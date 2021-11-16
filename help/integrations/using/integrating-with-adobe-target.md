---
product: campaign
title: Trabajar con Adobe Campaign y Adobe Target
description: Obtenga información sobre cómo integrar Adobe Campaign con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: af40fe822c69979a478604595790d4deefd6d5b0
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 32%

---

# Trabajo con Campaign y Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

Utilice Adobe Campaign con Adobe Target para optimizar el contenido del correo electrónico.

Para optimizar el contenido del correo electrónico, puede crear una oferta de redireccionamiento en Adobe Target y, a continuación, utilizar Adobe Campaign para administrar las ofertas de correo electrónico. Por ejemplo, puede mostrar diferentes ofertas para destinatarios hombres y mujeres.

La integración tiene lugar cuando se abre el correo electrónico. Cuando el cliente abre el correo electrónico, se realiza una llamada a Target y aparece una versión dinámica del contenido. El contenido consiste en una imagen estática compatible con todos los navegadores. Target realiza un seguimiento de la reacción a la oferta en el nivel de audiencia o de sesión, y esos datos están disponibles en los informes de Target. [Obtenga más información en la documentación de Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=es).


>[!NOTE]
>
>La integración solo admite imágenes estáticas. El resto del contenido no se puede personalizar.

Adobe Target puede utilizar varios tipos de datos:

* Datos del datamart de Adobe Campaign:
* Segmentos vinculados a la ID de visitante en Adobe Target, si los datos utilizados no están sujetos a limitaciones legales
* Datos de Adobe Target: agente de usuario, dirección IP, datos de geolocalización
