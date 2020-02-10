---
title: Administración de flujos de trabajo
seo-title: Administración de flujos de trabajo
description: Administración de flujos de trabajo
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Administración de flujos de trabajo{#managing-workflows}

De forma predeterminada, los nuevos flujos de trabajo se basan en una plantilla de flujo de trabajo preconfigurada y basada en una tabla de destinatarios (nms:destinatario). Para que se basen automáticamente en la tabla personalizada de destinatarios a los que se hace referencia en la opción **Nms_DefaultRcpSchema** (consulte [Configuración de la sección de interfaz](../../configuration/using/configuring-the-interface.md) ), debe crear una nueva plantilla de flujo de trabajo.

Cree una nueva plantilla a través del **[!UICONTROL Resources > Templates > Workflow templates]** nodo. En las propiedades de la plantilla, las dimensiones proporcionadas coinciden con la tabla de destinatarios externos.

Al basar los nuevos flujos de trabajo en una plantilla creada recientemente, la tabla personalizada se seleccionará de forma predeterminada para las dimensiones de filtrado y objetivo global del flujo de trabajo.

Todas las actividades utilizadas en el flujo de trabajo utilizarán la tabla personalizada sin necesidad de ninguna configuración manual adicional.

Para obtener más información sobre los flujos de trabajo, consulte [esta sección](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

