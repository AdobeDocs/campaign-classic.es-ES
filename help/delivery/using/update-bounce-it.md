---
product: campaign
title: Actualizar la calificación de devoluciones después de la interrupción de Italia Online
description: Aprenda a actualizar la calificación de devolución después de la interrupción de Italia Online
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 26%

---

# Actualización de devoluciones duras incorrectas después de la interrupción de Italia Online {#update-bounce-italia}

![](../../assets/common.svg)

## Contexto{#outage-context}

Desde el 22 de enero (hora local), Italia Online ha sufrido una interrupción que ha provocado varios retrasos y ha rechazado los correos electrónicos. El servicio comenzó a reanudarse con capacidad limitada el 26 de enero.

Los dominios afectados son: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** y **blu.it**.

Este problema ocurrió del 22/1/2023 al 26/1/2023, pero la mayoría de las cuarentenas erróneas ocurrieron el 26 de enero.

Más información en la comunicación oficial [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como devoluciones. Esto no solo afecta al Adobe, sino a todos los que tratan de recibir correos electrónicos en Italia Online.

Los síntomas son:

* **Rechazos de aplazamiento** con el mensaje `452 requested action aborted: try again later` se están observando: se vuelven a intentar automáticamente y no es necesario realizar ninguna acción. Deben mejorar a medida que el ISP recupera la capacidad completa.

* **Rechazos graves** con el mensaje `550 <email address> recipient rejected` han sido devueltos por el ISP el 26 de enero, entre las 8:00 y las 2:00 h, hora local, para evitar que los remitentes sigan sobrecargando sus servidores. Como confirmó Italia Online Postmaster, no se trata de devoluciones realmente duras, por lo que recomendamos anular la cuarentena de todas las direcciones de correo electrónico que se excluyeron el 26 de enero de 2023 debido a ese mensaje.

## Proceso de actualización{#outage-update}

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones [en esta página](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
