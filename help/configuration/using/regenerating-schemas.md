---
solution: Campaign Classic
product: campaign
title: Regeneración de esquemas
description: Regeneración de esquemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Regeneración de esquemas{#regenerating-schemas}

Al modificar un esquema y guardar las modificaciones, se genera automáticamente el esquema ampliado. Sin embargo, es posible que necesite volver a generar esquemas manualmente para aplicar las modificaciones. Para ello:

1. Seleccione los esquemas que necesita regenerar.
1. Haga clic con el botón derecho y elija **[!UICONTROL Actions > Regenerate selected schemas...]**.
1. Haga clic en **[!UICONTROL OK]** para confirmar e iniciar el proceso.

A continuación, puede comprobar la estructura del esquema generado en las fichas Vista previa y Documentación. Para obtener más información sobre esto, consulte la sección [Principios](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Si necesita forzar la regeneración de todos los esquemas, por ejemplo para resolver determinados problemas de dependencia en los vínculos inversos, puede iniciar el siguiente comando desde el servidor de aplicaciones de Adobe Campaign:
>
>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**
>
>A continuación, debe reiniciar el servidor de aplicaciones de Adobe Campaign y desconectar/reconectar con la consola del cliente.
