---
product: campaign
title: Resolución de problemas
description: Resolución de problemas
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%

---

# Resolución de problemas{#troubleshooting}



En caso de error, debe asegurarse de que los siguientes elementos estén correctamente configurados:

* **Cuentas externas**

   En **[!UICONTROL Administration > Platform > External accounts]**, asegúrese de que las siguientes cuentas externas SFTP están configuradas correctamente. Su consultor debe configurar en Adobe Experience Cloud los servidores SFTP mencionados.

   * **[!UICONTROL importSharedAudience]** : Cuenta SFTP específica para la importación de audiencias.
   * **[!UICONTROL exportSharedAudience]** : Cuenta SFTP específica para la exportación de audiencias.

* **Fuente de datos AMC**

   En **[!UICONTROL Administration > Platform > AMC Data sources]**, compruebe que la fuente de datos AMC esté correctamente configurada.

Al importar una audiencia o compartirla mediante el servicio principal Personas, puede que falten algunos datos. Solo se transfieren los registros cuya ID (“ID de visitante” o “ID declarada”) se haya podido conciliar con la dimensión del perfil. Las ID de los segmentos del servicio principal Personas que no reconozca Adobe Campaign no se importan.
