---
product: campaign
title: Regenerar esquemas
description: Aprenda a regenerar esquemas de Campaign
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 7%

---

# Regenerar esquemas{#regenerating-schemas}

Al modificar un esquema y guardar las modificaciones, el esquema ampliado se genera automáticamente. Sin embargo, es posible que deba regenerar los esquemas manualmente para aplicar modificaciones. Para ello, haga lo siguiente:

1. Seleccione los esquemas que debe regenerar.
1. Haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clic **[!UICONTROL OK]** para confirmar e iniciar el proceso.

A continuación, puede comprobar la estructura del esquema generado en las pestañas Preview y Documentation. Para obtener más información, consulte [Principios](../../configuration/using/data-schemas.md#principles) sección.

>[!NOTE]
>
>Si necesita forzar la regeneración de todos los esquemas, por ejemplo para solucionar ciertos problemas de dependencia en los vínculos inversos, puede iniciar el siguiente comando desde el servidor de aplicaciones de Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>A continuación, debe reiniciar el servidor de aplicaciones de Adobe Campaign y desconectar/volver a conectar con la consola del cliente.
