---
product: campaign
title: Alerta
description: Alerta
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 21698e85-7b58-4bde-bbd2-0ee06ac90307
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 100%

---

# Alerta{#alert}

Una actividad de **Alert** envía un mensaje a un grupo de operadores. Funciona del mismo modo que una actividad de aprobación, pero no se espera ninguna respuesta en este caso.

![](assets/edit_alerte.png)

Una alerta no es persistente y, por lo tanto, no es visible desde la consola. Los operadores del grupo asignado deben tener una dirección de correo electrónico completa para recibir la notificación. La configuración de esta actividad es similar a la de una **Approval**. La plantilla de entrega predeterminada utilizada para alertar a los operadores es &#39;alertAssignee&#39;.
