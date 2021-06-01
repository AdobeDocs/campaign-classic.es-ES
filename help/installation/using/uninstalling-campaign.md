---
product: campaign
title: Desinstalación de Campaign
description: Obtenga información sobre cómo desinstalar Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 30%

---

# Desinstalación de Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Estos procedimientos desinstalarán permanentemente Adobe Campaign. Se perderán todos los datos.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Consulte [esta página](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). No olvide quitar la carpeta de instalación de Campaign.
