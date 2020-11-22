---
solution: Campaign Classic
product: campaign
title: Comportamiento de JSP
description: Comportamiento de JSP
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# Comportamiento de JSP{#jsp-behavior}

Si ciertos trabajos **jsp** no se ejecutan correctamente, debe forzarlos a volver a compilarlos.

Para ello, introduzca los siguientes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Los trabajos **jsp** se regeneran la próxima vez que se conecte.
