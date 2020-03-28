---
title: Espera
seo-title: Espera
description: Espera
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Espera{#wait}

Una actividad **Wait** activa su transición después de un retraso de tiempo de entre unos segundos y varios meses. Una tarea de espera no bloquea la ejecución de otras tareas; el flujo de trabajo puede ejecutar tareas en paralelo mientras esta tarea está pendiente.

Puede introducir la etiqueta y esperar el tiempo utilizando el editor, como en el ejemplo siguiente:

![](assets/edit_wait.png)

En el campo **[!UICONTROL Duración]**, el valor se puede expresar en la unidad que elija: (según la configuración regional del operador):

* Si no se especifica la configuración regional: **s** para segundos, **m** para minutos, **h** para horas, **d** para días, **y** para años. En el momento de la aprobación, el valor se convierte automáticamente en la unidad más legible.

   La unidad predeterminada es el día (**d**).

* Mientras que si, por ejemplo, la configuración regional se establece en &quot;Francés&quot;: **s** para segundos, **mn** para minutos, **h** para horas, **j** para días, **m** para meses, **a** para años. En el momento de la aprobación, el valor se convierte automáticamente a la unidad más legible, como en el ejemplo anterior **90s** se convirtió a **1mn 30s**.

   La unidad predeterminada es el día (**d**).

