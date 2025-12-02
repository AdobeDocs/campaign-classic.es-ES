---
product: campaign
title: Regenerar esquemas
description: Aprenda a regenerar esquemas de Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 2%

---

# Regenerar esquemas{#regenerating-schemas}

Al modificar un esquema y guardar las modificaciones, el esquema ampliado se genera automáticamente. Sin embargo, es posible que deba regenerar los esquemas manualmente para aplicar modificaciones. Para ello, haga lo siguiente:

1. Seleccione los esquemas que debe regenerar.
1. Haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]**
1. Haga clic en **[!UICONTROL OK]** para confirmar e iniciar el proceso.

A continuación, puede comprobar la estructura del esquema generado en las pestañas Preview y Documentation. Para obtener más información, consulte la sección [Principios](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Si necesita forzar la regeneración de todos los esquemas, por ejemplo para solucionar ciertos problemas de dependencia en los vínculos inversos, puede iniciar el siguiente comando desde el servidor de aplicaciones de Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;nombre_instancia>` -force`
>
>A continuación, debe reiniciar el servidor de aplicaciones de Adobe Campaign y desconectar/volver a conectar con la consola del cliente.
