---
solution: Campaign Classic
product: campaign
title: Desinstalación de Campaign
description: Obtenga información sobre cómo desinstalar la Campaña
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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

Consulte [esta página](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). No olvide quitar la carpeta de instalación de la Campaña.
