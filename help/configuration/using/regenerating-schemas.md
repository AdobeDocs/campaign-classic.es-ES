---
title: Regeneración de esquemas
seo-title: Regeneración de esquemas
description: Regeneración de esquemas
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# Regeneración de esquemas{#regenerating-schemas}

Al modificar un esquema y guardar las modificaciones, se genera automáticamente el esquema ampliado. Sin embargo, es posible que necesite volver a generar esquemas manualmente para aplicar las modificaciones. Para ello:

1. Seleccione los esquemas que necesita regenerar.
1. Haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Haga clic en **[!UICONTROL OK]** para confirmar e iniciar el proceso.

A continuación, puede comprobar la estructura del esquema generado en las fichas Vista previa y Documentación. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Si necesita forzar la regeneración de todos los esquemas, por ejemplo para resolver determinados problemas de dependencia en los vínculos inversos, puede iniciar el siguiente comando desde el servidor de aplicaciones de Adobe Campaign:
>
>**nlserver config -postupgrade -instance:`&lt;nombre_instancia>&#39; -force**
>
>A continuación, debe reiniciar el servidor de aplicaciones de Adobe Campaign y desconectar/reconectar con la consola del cliente.
