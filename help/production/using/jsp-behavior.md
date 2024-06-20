---
product: campaign
title: Comportamiento de JSP
description: Comportamiento de JSP
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 36%

---

# Comportamiento de JSP{#jsp-behavior}



Si es cierto **jsp** los trabajos no se ejecutan correctamente, debe forzarlos a volver a compilar.

Para ello, introduzca los siguientes comandos:

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

El **jsp** los trabajos se regeneran la próxima vez que se conecte.
