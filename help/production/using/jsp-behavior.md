---
product: campaign
title: Comportamiento de JSP
description: Comportamiento de JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# Comportamiento de JSP{#jsp-behavior}

Si ciertos trabajos **jsp** no se ejecutan correctamente, debe obligarlos a volver a compilar.

Para ello, introduzca los siguientes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Los trabajos **jsp** se regeneran la próxima vez que se conecte.
