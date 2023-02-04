---
product: campaign
title: Actualización de la calificación de devoluciones después de una interrupción del ISP
description: Obtenga información sobre cómo actualizar la calificación de devoluciones después de una interrupción del ISP
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: 13f730d428861124060146efa26238ceca38bed6
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 36%

---

# Actualizar devoluciones duras incorrectas después de una interrupción del ISP {#update-bounces}

![](../../assets/common.svg)

## Contexto{#update-bounce-context}

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como rechazos.

Los problemas globales en Apple o Gmail, por ejemplo, pueden causar que algunos mensajes de correo electrónico enviados a direcciones de correo electrónico válidas de Apple o Gmail se devuelvan incorrectamente como direcciones de correo electrónico no válidas por parte de los servidores ISP con el rechazo de las siguientes respuestas:

* &quot;550 5.1.1 &#39;dirección de correo electrónico&#39;: la búsqueda del usuario se ha realizado correctamente, pero no se ha encontrado ningún registro de usuario&quot;.

* &quot;Se ha rechazado el destinatario 550 &quot;dirección de correo electrónico&quot;

Tenga en cuenta que si el aplazamiento devuelve un error con el mensaje &quot;452 acción solicitada anulada: inténtelo de nuevo más tarde&quot; se están observando, se vuelven a intentar automáticamente y no se necesitan acciones. Deben mejorar a medida que el ISP recupera la capacidad completa.

>[!NOTE]
>
>Puede comprobar el panel de estado del sistema de Apple en [esta página](https://www.apple.com/es/support/systemstatus/){_blank}.
>
>Puede comprobar el panel de estado del espacio de trabajo de Google en [esta página](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.

## Síntomas{#update-bounce-symptoms}

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como devoluciones.

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, consulte las instrucciones a continuación.

## Proceso de actualización{#update-bounce-update}

Debe ejecutar una consulta en la tabla de cuarentena para filtrar todos los destinatarios afectados (por ejemplo, para Apple, las direcciones que incluyen @icloud.com, @me.com, @mac.com) que se hayan visto potencialmente afectados por la interrupción para que se puedan eliminar de la lista de cuarentena y se incluyan en futuros envíos de correo electrónico de Campaign.

En función del intervalo de tiempo del incidente y del ISP, a continuación se indican las directrices recomendadas para esta consulta.

* Para los entornos de Campaign v8 y Campaign Classic v7 con información de regla de correo electrónico entrante en la sección **[!UICONTROL Error text]** campo de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)** contiene “Momen_Code10_InvalidRecipient”
   * **Dominio de correo electrónico (@domain)** igual a domain1.com OR **Dominio de correo electrónico (@domain)** igual a domain2.com OR **Dominio de correo electrónico (@domain)** igual a domain3.com
   * **Actualizar estado (@lastModified)** en o después de MM/DD/AAAA HH:MM:SS AM
   * **Actualizar estado (@lastModified)** en MM/DD/AAAA HH:MM:SS PM

* Para instancias de Campaign Classic v7 con información de respuesta de rechazo SMTP en la variable **[!UICONTROL Error text]** campo de la lista de cuarentena:

   * **Texto de error (texto de cuarentena)** contiene &quot;550-5.1.1&quot; Y **Texto de error (texto de cuarentena)** contiene &quot;support.ISP.com&quot; &quot;support.ISP.com&quot; puede ser: &quot;support.apple.com&quot; o &quot;support.google.com&quot;, por ejemplo
   * **Actualizar estado (@lastModified)** en o después de MM/DD/AAAA HH:MM:SS AM
   * **Actualizar estado (@lastModified)** en MM/DD/AAAA HH:MM:SS PM


Una vez que tenga la lista de destinatarios afectados, puede aplicarles un estado **[!UICONTROL Valid]** para que el flujo de trabajo **[!UICONTROL Database cleanup]** los elimine de la lista de cuarentena, o simplemente elimínelos de la tabla.

**Temas relacionados:**
* [Comprensión de los errores de entrega](understanding-delivery-failures.md)
* [Clasificación del correo rechazado](understanding-delivery-failures.md#bounce-mail-qualification)
