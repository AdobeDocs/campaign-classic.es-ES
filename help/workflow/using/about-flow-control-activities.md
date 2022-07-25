---
product: campaign
title: Acerca de las actividades de control de flujo
description: Acerca de las actividades de control de flujo
feature: Workflows
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---

# Actividades de control de flujo en flujos de trabajo{#about-flow-control-activities}

![](../../assets/v7-only.svg)

Las siguientes actividades son actividades de base de datos: su principal tarea es coordinar las demás actividades.

* **Start and End**: permite mostrar los puntos iniciales y finales de un flujo de trabajo. Consulte [Inicio y final](start-and-end.md).
* **Fork**: permite activar todas las transiciones salientes. Consulte la sección [Fork](fork.md).
* **Appointment**: permite esperar a que se finalicen varias tareas a la vez antes de continuar. Consulte la sección [Fork](fork.md).
* **Scheduler**: permite definir un programa de ejecución de flujo de trabajo. Consulte [Programador](scheduler.md).
* **Test**: permite una transición basada en un resultado de prueba. Consulte [Prueba](test.md).
* **Wait**: activa la transición saliente después de un límite de tiempo determinado. Consulte [Esperar](wait.md).
* **Time constraint**: permite pausar una tarea durante un periodo determinado. Consulte [Restricción de tiempo](time-constraint.md).
* **Sub-workflow**: permite ejecutar otro flujo de trabajo. Consulte [Subworkflow](sub-workflow.md).
* **Jumps**: permite implementar transiciones sin vínculos. Consulte [Saltos (puntos iniciales y finales)](jump--start-point-and-end-point-.md).
* **External signal**: permite activar la transición saliente después de recibir una señal externa. Consulte la sección [Señales externas](external-signal.md).
* **Approval**: permite enviar un correo electrónico a un operador o a un grupo de operadores y esperar a que la aprobación continúe con la ejecución. Consulte la sección [Aprobación](approval.md).
* **Alert**: permite enviar una advertencia a un operador o a un grupo de operadores. Consulte la sección [Alerta](alert.md).
* **Task**: permite configurar la ejecución de tareas. Consulte la sección [Tarea](task.md).
