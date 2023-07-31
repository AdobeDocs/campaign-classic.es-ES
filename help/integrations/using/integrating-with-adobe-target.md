---
product: campaign
title: Uso de Adobe Campaign y Adobe Target
description: Obtenga información acerca de cómo integrar Adobe Campaign con Adobe Target
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '210'
ht-degree: 100%

---

# Uso de Campaign y Target{#integrating-with-adobe-target}



Utilice Adobe Campaign con Adobe Target para optimizar el contenido del correo electrónico.

Para optimizar el contenido del correo electrónico, puede crear una oferta de redireccionamiento en Adobe Target y, a continuación, utilizar Adobe Campaign para administrar las ofertas de correo electrónico. Por ejemplo, puede mostrar diferentes ofertas para destinatarios hombres y mujeres.

La integración tiene lugar cuando se abre el correo electrónico. Cuando el cliente abre el correo electrónico, se realiza una llamada a Target y aparece una versión dinámica del contenido. El contenido consiste en una imagen estática compatible con todos los navegadores. Target realiza el seguimiento de la reacción a la oferta en el nivel de audiencia o de sesión, y esos datos están disponibles en los informes de Target. [Obtenga más información en la documentación de Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=es).


>[!NOTE]
>
>La integración solo admite imágenes estáticas. El resto del contenido no se puede personalizar.

Adobe Target puede utilizar varios tipos de datos:

* Datos del datamart de Adobe Campaign:
* Segmentos vinculados a la ID de visitante en Adobe Target, si los datos utilizados no están sujetos a limitaciones legales
* Datos de Adobe Target: agente de usuario, dirección IP, datos de geolocalización
