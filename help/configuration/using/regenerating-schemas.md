---
product: campaign
title: Regenerar esquemas
description: Obtenga información sobre cómo regenerar esquemas de Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# Regenerar esquemas{#regenerating-schemas}

Al modificar un esquema y guardar las modificaciones, el esquema ampliado se genera automáticamente. Sin embargo, es posible que tenga que volver a generar los esquemas manualmente para aplicar las modificaciones. Para ello, haga lo siguiente:

1. Seleccione los esquemas que debe regenerar.
1. Haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Haga clic en **[!UICONTROL OK]** para confirmar e iniciar el proceso.

A continuación, puede comprobar la estructura del esquema generado en las pestañas Preview y Documentation . Para obtener más información, consulte [Principios](../../configuration/using/data-schemas.md#principles) para obtener más información.

>[!NOTE]
>
>Si necesita forzar la regeneración de todos los esquemas, por ejemplo para resolver ciertos problemas de dependencia en los vínculos inversos, puede iniciar el siguiente comando desde el servidor de aplicaciones de Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>A continuación, debe reiniciar el servidor de aplicaciones de Adobe Campaign y desconectar/volver a conectar con la consola del cliente.
