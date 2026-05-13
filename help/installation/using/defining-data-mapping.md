---
product: campaign
title: Definición de asignación de datos externos
description: Obtenga información sobre cómo asignar datos en una base de datos externa
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
TQID: https://experienceleague.adobe.com/9mE5BjrDg-E4FDyFFL0GVAVPof0rlSSOlzyj2zk21ag
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 91%

---

# Definición de asignación de datos externos {#defining-data-mapping}



Adobe Campaign le permite definir la asignación en los datos de una tabla externa.

Para ello, una vez que se haya creado el esquema de la tabla externa, debe crear una nueva asignación de envío para utilizar los datos de esta tabla como objetivo de envío.

Para ello, siga los siguientes pasos:

1. Cree una nueva asignación de envíos y elija la dimensión de segmentación, como por ejemplo el esquema que acaba de crear.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique los campos donde se almacena la información de envío (apellidos, nombre, correo electrónico, dirección, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique los parámetros para el almacenamiento de información, incluido el sufijo de los esquemas de extensión para que se puedan identificar fácilmente.

   ![](assets/wf_new_mapping_define_names.png)

   Puede elegir si desea almacenar las exclusiones (**excludelog**), con mensajes (**broadlog**) o en una tabla independiente.

   También puede elegir si desea administrar el seguimiento para esta asignación de envíos (**trackinglog**).

1. A continuación, seleccione las extensiones que se van a tener en cuenta. El tipo de extensión depende de los parámetros y opciones de la plataforma (consulte el contrato de licencia).

   ![](assets/wf_new_mapping_define_extensions.png)

   Haga clic en el botón **[!UICONTROL Save]** para iniciar la creación de la asignación de entrega: todas las tablas vinculadas se crean automáticamente en función de los parámetros seleccionados.
