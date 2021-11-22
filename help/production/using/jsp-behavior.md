---
product: campaign
title: Comportamiento de JSP
description: Comportamiento de JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# Comportamiento de JSP{#jsp-behavior}

![](../../assets/v7-only.svg)

Si **jsp** los trabajos no se ejecutan correctamente, debe obligarlos a volver a compilar.

Para ello, introduzca los siguientes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

La variable **jsp** los trabajos se regeneran la próxima vez que se conecte.
