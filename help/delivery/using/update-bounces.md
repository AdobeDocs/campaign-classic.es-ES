---
product: campaign
title: Actualización de la calificación de devoluciones después de una interrupción del ISP
description: Obtenga información sobre cómo actualizar la calificación de devoluciones después de una interrupción del ISP
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 100%

---

# Actualización de estado de devoluciones graves incorrectas después de una interrupción ISP {#update-bounces}



## Contexto{#update-bounce-context}

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como rechazos.

Los problemas globales en Apple o Gmail, por ejemplo, pueden causar que algunos mensajes de correo electrónico enviados a direcciones de correo electrónico válidas de Apple o Gmail se devuelvan incorrectamente como direcciones de correo electrónico no válidas por parte de los servidores ISP con las siguientes respuestas de rechazo:

* “550 5.1.1 &#39;dirección de correo electrónico&#39;: la búsqueda del usuario se ha realizado correctamente, pero no se ha encontrado ningún registro de usuario”.

* “Se ha rechazado el destinatario 550 &#39;dirección de correo electrónico&#39;”

Tenga en cuenta que si el aplazamiento devuelve un error con el mensaje “452 acción solicitada anulada: inténtelo de nuevo más tarde” se están observando, se vuelven a intentar automáticamente y no se necesitan acciones. Deben mejorar a medida que el ISP recupera la capacidad completa.

>[!NOTE]
>
>Puede consultar el panel del estado de Apple System en [esta página](https://www.apple.com/es/support/systemstatus/){_blank}.
>
>Puede consultar el Tablero de estado de Google Workspace en [esta página](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.
>

## Impacto{#update-bounce-impact}

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como devoluciones.

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, consulte las instrucciones a continuación.

## Proceso de actualización{#update-bounce-update}

Deberá ejecutar una consulta en la tabla de cuarentena para filtrar todos los destinatarios afectados, de Apple por ejemplo, que incluyen las direcciones @icloud.com, @me.com y @mac.com, que se hayan visto potencialmente afectados por la interrupción para que se puedan eliminar de la lista de cuarentena y se puedan incluir en futuros envíos de correo electrónico de Campaign.

En función del periodo de tiempo del problema y la ISP, se indican a continuación las directrices recomendadas para esta consulta.

* Para entornos de Campaign con información de regla de correo electrónico entrante en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)** contiene “Momen_Code10_InvalidRecipient”
   * **Dominio de correo electrónico (@domain)** igual a domain1.com O **Dominio de correo electrónico (@domain)** igual a domain2.com O **Dominio de correo electrónico (@domain)** igual a domain3.com
   * **Actualizar estado (@lastModified)** en o después de DD/MM/AAAA HH:MM:SS AM
   * **Actualizar estado (@lastModified)** en DD/MM/AAAA HH:MM:SS PM

* Para entornos de Campaign con información de respuesta de rechazo SMTP en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **Texto de error (texto de cuarentena)** contiene “550-5.1.1” Y **Texto de error (texto de cuarentena)** contiene “support.ISP.com”

     donde “support.ISP.com” puede ser: “support.apple.com” o “support.google.com”, por ejemplo

   * **Actualizar estado (@lastModified)** en o después de DD/MM/AAAA HH:MM:SS AM
   * **Actualizar estado (@lastModified)** en DD/MM/AAAA HH:MM:SS PM


Una vez que tenga la lista de destinatarios afectados, puede aplicarles un estado **[!UICONTROL Valid]** para que el flujo de trabajo **[!UICONTROL Database cleanup]** los elimine de la lista de cuarentena, o simplemente elimínelos de la tabla.

**Temas relacionados:**
* [Comprensión de los errores de entrega](understanding-delivery-failures.md)
* [Clasificación del correo rechazado](understanding-delivery-failures.md#bounce-mail-qualification)
