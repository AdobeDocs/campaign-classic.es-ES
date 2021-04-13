---
solution: Campaign Classic
product: campaign
title: Ingesta de segmentos de Adobe Experience Platform en Campaign
description: Aprenda a incorporar audiencias de Adobe Experience Platform en Campaign Classic.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 9b3254c16eed784846db87d27f9f5de009dafdc3
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Ingesta de segmentos de Adobe Experience Platform en Campaign {#destinations}

Para ingerir Adobe Experience Platform en Campaign y utilizarlos en sus flujos de trabajo, primero debe conectar Adobe Campaign as a Adobe Experience Platform **Destination** y configurarlo con el segmento a exportar.

Una vez configurado el destino, los datos se exportan a su ubicación de almacenamiento y deberá crear un flujo de trabajo dedicado en Campaign Classic para ingerirlos.

## Conectar Adobe Campaign como destino

En Adobe Experience Platform, para configurar una conexión con Adobe Campaign, seleccione una ubicación de almacenamiento para los segmentos exportados. Estos pasos también le permiten seleccionar los segmentos que desea exportar y especificar campos XDM adicionales que incluir.

Para obtener más información, consulte la [Documentación de destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

Una vez configurado el destino, Adobe Experience Platform crea un archivo .txt o .csv delimitado por tabuladores en la ubicación de almacenamiento proporcionada. Esta operación se programa y realiza una vez cada 24 horas.

Ahora puede configurar un flujo de trabajo de Campaign Classic para introducir el segmento en Campaign.

## Creación de un flujo de trabajo de importación en Campaign Classic

Una vez configurado el Campaign Classic como destino, debe crear un flujo de trabajo dedicado para importar el archivo que ha exportado Adobe Experience Platform.

Para ello, debe añadir y configurar una actividad **[!UICONTROL File transfer]** . Para obtener más información sobre cómo configurar esta actividad, consulte [esta sección](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

A continuación, puede crear el flujo de trabajo según sus necesidades (actualice la base de datos con los datos del segmento, envíe envíos multicanal al segmento, etc.)

Por ejemplo, el flujo de trabajo siguiente descarga diariamente el archivo desde su ubicación de almacenamiento y, a continuación, actualiza la base de datos de Campaign con los datos del segmento.

![](assets/rtcdp-workflow.png)
