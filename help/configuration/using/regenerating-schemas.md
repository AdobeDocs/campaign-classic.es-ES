---
product: campaign
title: Regenerar esquemas
description: Aprenda a regenerar esquemas de Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: 'https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
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
