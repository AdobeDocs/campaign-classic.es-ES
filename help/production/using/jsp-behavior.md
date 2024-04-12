---
product: campaign
title: Comportamiento de JSP
description: Comportamiento de JSP
feature: Monitoring
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 29%

---

# Comportamiento de JSP{#jsp-behavior}



Si es cierto **jsp** los trabajos no se ejecutan correctamente, debe forzarlos a volver a compilar.

Para ello, introduzca los siguientes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

El **jsp** los trabajos se regeneran la próxima vez que se conecte.
