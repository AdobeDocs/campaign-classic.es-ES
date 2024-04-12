---
product: campaign
title: Desinstalación de Campaign
description: Obtenga información sobre cómo desinstalar Campaign
feature: Installation
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 2%

---

# Desinstalación de Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>Estos procedimientos desinstalarán Adobe Campaign de forma permanente. Se perderán todos los datos.

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

Consulte esta sección [página](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Recuerde eliminar la carpeta de instalación de Campaign.
