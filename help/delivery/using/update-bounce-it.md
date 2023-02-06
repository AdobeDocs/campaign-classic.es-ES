---
product: campaign
title: Actualizar la calificación de devoluciones después de la interrupción de Italia Online
description: Aprenda a actualizar la calificación de devolución después de la interrupción de Italia Online
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 0e6a46e4a0575fa5a300a952a6bb134f3426172e
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 18%

---

# Actualización de devoluciones duras incorrectas después de la interrupción de Italia Online {#update-bounce-italia}

![](../../assets/common.svg)

## Contexto{#outage-context}

Desde el 22 de enero (hora local), Italia Online ha sufrido una interrupción que ha provocado varios retrasos y ha rechazado los correos electrónicos. El servicio comenzó a reanudarse con capacidad limitada el 26 de enero.

Los dominios afectados son: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** y **blu.it**.

Este problema ocurrió del 22/1/2023 al 26/1/2023, pero la mayoría de las cuarentenas erróneas ocurrieron el 26 de enero.

Más información en la comunicación oficial [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

Como en la mayoría de los casos en los que se produce una interrupción en un ISP, algunos correos electrónicos enviados a través de Campaign se marcaron erróneamente como rechazos. Esto no solo impactó en el Adobe, sino que todos los que intentaban recibir correo electrónico fueron enviados a Italia Online durante la interrupción del servicio.

Los síntomas fueron:

* **Rechazos de aplazamiento** con el mensaje `452 requested action aborted: try again later` : se reintentaron automáticamente y no se necesitan acciones.

* **Rechazos graves** con el mensaje `550 <email address> recipient rejected` han sido devueltos por el ISP el 26 de enero, entre las 8:00 y las 2:00 h, hora local, para evitar que los remitentes sigan sobrecargando sus servidores. Como confirmó Italia Online Postmaster, no se trata de devoluciones realmente duras, por lo que recomendamos anular la cuarentena de todas las direcciones de correo electrónico que se excluyeron el 26 de enero de 2023 debido a ese mensaje.

## Proceso de actualización{#outage-update}

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones [en esta página](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
