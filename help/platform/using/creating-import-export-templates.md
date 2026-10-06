---
product: campaign
title: Creación de plantillas de importación y exportación
description: Obtenga información sobre cómo crear plantillas de importación y exportación en Campaign
feature: Templates
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
TQID: 'https://experienceleague.adobe.com/KV2jYphvbknvGlfCH0k7QPdfPCAWgwg-X67ICvPmADo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%
---
# Creación de plantillas de importación y exportación {#creating-import-export-templates}



Las plantillas de importación y exportación se almacenan en el directorio **[!UICONTROL Resources > Templates > Job templates]** del árbol de Adobe Campaign.

De forma predeterminada, hay tres plantillas de importación y una plantilla de exportación en este directorio. No deben modificarse.

* La plantilla nativa **[!UICONTROL Import denylist]** ya está configurada para importar una lista de direcciones de correo electrónico que se incluyeron a la de lista de bloqueados.

* Las plantillas **[!UICONTROL New text import]** y **[!UICONTROL New text export]** permiten configurar una importación o exportación desde cero.

![](assets/s_ncs_user_export_wizard_template_create.png)

Puede duplicarlas para crear sus propias plantillas o crear una nueva plantilla a través del menú **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

El proceso para configurar una plantilla es el mismo que el que se presenta en estas secciones:

* [Configuración de un trabajo de importación](../../platform/using/executing-import-jobs.md)
* [Configuración de un trabajo de exportación](../../platform/using/executing-export-jobs.md)
