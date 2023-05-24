---
product: campaign
title: Administración de flujos de trabajo
description: Administración de flujos de trabajo
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---

# Administración de flujos de trabajo{#managing-workflows}



De forma predeterminada, los nuevos flujos de trabajo se basan en una plantilla de flujo de trabajo preconfigurada y basada en una tabla de destinatarios (nms:recipient). Para que se basen automáticamente en la tabla personalizada de destinatarios a los que se hace referencia en la **Nms_DefaultRcpSchema** opción (consulte [Configuración de la interfaz](../../configuration/using/configuring-the-interface.md) ), debe crear una nueva plantilla de flujo de trabajo.

Cree una nueva plantilla a través de **[!UICONTROL Resources > Templates > Workflow templates]** nodo. En las propiedades de la plantilla, las dimensiones proporcionadas coinciden con la tabla de destinatarios externos.

Al basar los nuevos flujos de trabajo en una plantilla creada recientemente, la tabla personalizada se selecciona de forma predeterminada para las dimensiones globales de segmentación y filtrado del flujo de trabajo.

Por lo tanto, todas las actividades utilizadas en el flujo de trabajo utilizan la tabla personalizada sin necesidad de ninguna configuración manual adicional.

Para obtener más información sobre los flujos de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
