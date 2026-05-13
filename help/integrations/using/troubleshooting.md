---
product: campaign
title: Resolución de problemas
description: Resolución de problemas
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: a8512b64-d668-4084-b4f0-34baa899e306
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 100%

---

# Resolución de problemas{#troubleshooting}



En caso de error, debe asegurarse de que los siguientes elementos estén correctamente configurados:

* **Cuentas externas**

  En **[!UICONTROL Administration > Platform > External accounts]**, asegúrese de que las siguientes cuentas externas SFTP están configuradas correctamente. Su consultor debe configurar en Adobe Experience Cloud los servidores SFTP mencionados.

   * **[!UICONTROL importSharedAudience]** : Cuenta SFTP específica para la importación de públicos.
   * **[!UICONTROL exportSharedAudience]** : Cuenta SFTP específica para la exportación de públicos.

* **Fuente de datos AMC**

  En **[!UICONTROL Administration > Platform > AMC Data sources]**, compruebe que la fuente de datos AMC esté correctamente configurada.

Puede ocurrir que falten algunos datos al compartir un público mediante Experience Cloud Audience o al importarlo. Solo se transfieren los registros cuya ID (“ID de visitante” o “ID declarada”) se haya podido reconciliar con la dimensión del perfil. Los ID de los segmentos no reconocidos por Adobe Campaign no se importan.
