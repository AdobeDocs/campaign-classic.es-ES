---
product: campaign
title: SpamAssassin
description: Obtenga información sobre cómo configurar la detección de correo no deseado con SpamAssassin
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
TQID: https://experienceleague.adobe.com/nZB19N90xSjDCNnibtwcPBm75SSyxkq1hQxICXCOg2A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 100%

---

# SpamAssassin{#spamassassin}

Adobe Campaign se puede configurar para que funcione con [SpamAssassin](https://spamassassin.apache.org), un servicio de terceros que se utiliza para el filtrado masivo de correo no deseado. Esto le permite puntuar correos electrónicos para determinar si un mensaje corre el riesgo de que las herramientas de filtrado de correo no deseado utilizadas durante la recepción lo consideren como no deseado.

SpamAssassin aprovecha diversas técnicas de detección de correo no deseado para ahorrar tiempo, entre las que se incluyen:

* Detección de correo no deseado basado en DNS y en suma de comprobación incorrecta
* Filtrado bayesiano
* Programas externos
* Listas de bloqueados
* Bases de datos en línea

>[!NOTE]
>
>SpamAssassin debe instalarse y configurarse en el servidor de aplicaciones de Adobe Campaign. Para obtener más información, consulte [esta sección](../../installation/using/configuring-spamassassin.md).
>
>Las reglas que rigen si un elemento es correo no deseado o no se administran mediante SpamAssassin y un administrador con privilegios puede editarlas.

## Uso de SpamAssassin en Campaign {#using-spamassassin}

Una vez que haya creado su envío de correo electrónico y haya definido su contenido, siga los pasos a continuación para evaluar los riesgos.

Para obtener más información sobre la creación y configuración de los servicios de información, consulte [esta sección](about-email-channel.md).

1. Vaya a la pestaña **[!UICONTROL Preview]**.
1. Seleccione un destinatario para obtener una previsualización de la entrega.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Si no selecciona ningún destinatario, no se puede realizar la comprobación de correo no deseado.

1. Un mensaje de advertencia le muestra el resultado de la prueba. Si se detecta un alto nivel de riesgo, se muestra el siguiente mensaje de advertencia:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Haga clic en el vínculo **[!UICONTROL More...]** situado junto a la advertencia.
1. Seleccione la pestaña **[!UICONTROL Anti-spam checking]** .
1. Vaya a la sección **[!UICONTROL Points / Rule / Description]** para ver las causas de este riesgo.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Cada vez que hace clic en **[!UICONTROL Anti-spam checking]**, se llama al servicio SpamAssassin y se vuelve a analizar la detección del mensaje como correo no deseado. Compruebe que ha modificado el contenido antes de volver a ejecutar el análisis de correo no deseado.
