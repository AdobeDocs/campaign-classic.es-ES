---
product: campaign
title: Creación de filtros
description: Obtenga información sobre cómo crear filtros para una tabla personalizada
feature: Profiles, Custom Resources
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 6fad3dac-9af0-4796-adcf-d1de4b255aca
TQID: 'https://experienceleague.adobe.com/o8D1KiuODDNW87aki7q7ZaRU0vNITegmsMRCJ08YUzo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 8%
---
# Creación de filtros{#creating-filters}

Al igual que la tabla de destinatarios integrada proporcionada con Adobe Campaign, la nueva tabla de destinatarios puede recibir un lote de filtros predefinidos.

Estos filtros están disponibles en la ventana de selección de objetivos con las mismas funcionalidades que los segmentos para los destinatarios (mediante formularios de entrada de parámetros, carpetas, etc.).

1. Vaya al nodo **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Cree un nuevo filtro.
1. Introduzca el **[!UICONTROL Label]** del filtro y, a continuación, seleccione el esquema que coincida con la tabla de destinatarios externa en el campo **[!UICONTROL Document type]**.
1. Cree su **[!UICONTROL filtering conditions]** basado en los campos de su esquema.
1. Guarde el filtro.
