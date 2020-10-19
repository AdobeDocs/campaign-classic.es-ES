---
title: SpamAssassin
description: Obtenga información sobre cómo configurar la detección de correo no deseado con SpamAssassin
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 88%

---


# SpamAssassin{#spamassassin}

## Acerca de SpamAssassin {#about-spamassassin}

Adobe Campaign se puede configurar para que funcione con [SpamAssassin](https://spamassassin.apache.org), un servicio de terceros que se utiliza para el filtrado masivo de correo no deseado. Esto le permite puntuar correos electrónicos para determinar si un mensaje corre el riesgo de que las herramientas de filtrado de correo no deseado utilizadas durante la recepción lo consideren como no deseado.

SpamAssassin aprovecha diversas técnicas de detección de correo no deseado para ahorrar tiempo, entre las que se incluyen:

* Detección de correo no deseado basado en DNS y en suma de comprobación incorrecta
* Filtrado bayesiano
* Programas externos
* listas de bloqueados
* Bases de datos en línea

>[!NOTE]
>
>SpamAssassin debe instalarse y configurarse en el servidor de aplicaciones de Adobe Campaign. Para obtener más información, consulte [esta sección](../../installation/using/configuring-spamassassin.md).
>
>Las reglas que rigen si un elemento es correo no deseado o no se administran mediante SpamAssassin y un administrador con privilegios puede editarlas.

## Uso de SpamAssassin {#using-spamassassin}

Una vez que haya creado su envío de correo electrónico y haya definido su contenido, siga los pasos a continuación para evaluar los riesgos.

Para obtener más información sobre la creación y configuración de los servicios de información, consulte [esta sección](../../delivery/using/about-email-channel.md).

1. Vaya a la pestaña **[!UICONTROL Preview]**.
1. Seleccione un destinatario para obtener una previsualización de la entrega.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Si no selecciona ningún destinatario, no se puede realizar la comprobación de correo no deseado.

1. Un mensaje de advertencia le muestra el resultado de la prueba. Si se detecta un alto nivel de riesgo, se muestra el siguiente mensaje de advertencia:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Click the **[!UICONTROL More...]** link next to the warning.
1. Seleccione la pestaña **[!UICONTROL Anti-spam checking]** .
1. Go to the **[!UICONTROL Points / Rule / Description]** section to view the reasons for this risk.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Cada vez que hace clic en **[!UICONTROL Anti-spam checking]**, se llama al servicio SpamAssassin y se vuelve a analizar la detección del mensaje como correo no deseado. Compruebe que ha modificado el contenido antes de volver a ejecutar el análisis de correo no deseado.
