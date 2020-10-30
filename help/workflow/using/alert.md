---
title: Alerta
seo-title: Alerta
description: Alerta
seo-description: null
page-status-flag: never-activated
uuid: caf39f7b-67e0-4ede-b477-5ac9afdee7c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 7cf01a80-1fef-4093-a60a-8ddba62a2464
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '85'
ht-degree: 100%

---


# Alerta{#alert}

Una actividad de **Alert** envía un mensaje a un grupo de operadores. Funciona del mismo modo que una actividad de aprobación, pero no se espera ninguna respuesta en este caso.

![](assets/edit_alerte.png)

Una alerta no es persistente y, por lo tanto, no es visible desde la consola. Los operadores del grupo asignado deben tener una dirección de correo electrónico completa para recibir la notificación. La configuración de esta actividad es similar a la de una **Approval**. La plantilla de entrega predeterminada utilizada para alertar a los operadores es &#39;alertAssignee&#39;.
