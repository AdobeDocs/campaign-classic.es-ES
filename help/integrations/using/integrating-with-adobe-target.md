---
product: campaign
title: Uso de Adobe Campaign y Adobe Target
description: Obtenga información acerca de cómo integrar Adobe Campaign con Adobe Target
feature: Target Integration
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 209
ht-degree: 100%

---

# Uso de Campaign y Target{#integrating-with-adobe-target}



Utilice Adobe Campaign con Adobe Target para optimizar el contenido del correo electrónico.

Para optimizar el contenido del correo electrónico, puede crear una oferta de redireccionamiento en Adobe Target y, a continuación, utilizar Adobe Campaign para administrar las ofertas de correo electrónico. Por ejemplo, puede mostrar diferentes ofertas para destinatarios hombres y mujeres.

La integración tiene lugar cuando se abre el correo electrónico. Cuando el cliente abre el correo electrónico, se realiza una llamada a Target y aparece una versión dinámica del contenido. El contenido consiste en una imagen estática compatible con todos los navegadores. Target realiza el seguimiento de la reacción a la oferta en el nivel de público o de sesión, y esos datos están disponibles en los informes de Target. [Obtenga más información en la documentación de Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=es).


>[!NOTE]
>
>La integración solo admite imágenes estáticas. El resto del contenido no se puede personalizar.

Adobe Target puede utilizar varios tipos de datos:

* Datos del datamart de Adobe Campaign:
* Segmentos vinculados a la ID de visitante en Adobe Target, si los datos utilizados no están sujetos a limitaciones legales
* Datos de Adobe Target: agente de usuario, dirección IP, datos de geolocalización
