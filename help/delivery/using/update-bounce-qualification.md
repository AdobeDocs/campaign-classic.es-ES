---
solution: Campaign Classic
product: campaign
title: Actualizar la calificación de devoluciones después de una interrupción del ISP
description: Obtenga información sobre cómo actualizar la calificación de devoluciones después de una interrupción del ISP.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---


# Actualizar la calificación de devoluciones después de una interrupción del ISP {#update-bounce-qualification.md}

## Contexto

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como rechazos.

En diciembre de 2020, un problema global en Gmail resultó en que algunos mensajes de correo electrónico enviados a direcciones de correo electrónico de Gmail válidas fueran rechazados incorrectamente como direcciones de correo electrónico no válidas por servidores de Gmail con la siguiente respuesta de rechazo: *&quot;550-5.1.1 La cuenta de correo electrónico a la que intentó llegar no existe.&quot;*

Google ha declarado que los cortes y interrupciones de Gmail que causaron este problema empezaron el 14 de diciembre a las 6:55 AM y terminaron a las 6:09PM EST el 15 de diciembre. Nuestro análisis de datos también mostró un pico muy corto en los rebotes de Gmail a las 2:06AM EST del 16 de diciembre, la mayoría ocurrió el 15 de diciembre entre las 2:00 pm EST y las 6:30 pm EST.

>[!NOTE]
>
>Puede consultar el Tablero de estado de Google Workspace en [esta página](https://www.google.com/appsstatus#hl=en&amp;v=status).


Por lógica de gestión de devoluciones estándar, Adobe Campaign agregó automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y eliminando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema de Gmail, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones a continuación.

## Proceso de actualización

Deberá ejecutar una consulta en la tabla de cuarentena para filtrar todos los destinatarios de Gmail (u otro ISP) que se hayan visto potencialmente afectados por la interrupción para que se puedan eliminar de la lista de cuarentena e incluirlos en futuros envíos de correo electrónico de Campaign.

En función del intervalo de tiempo del incidente, a continuación se indican las directrices recomendadas para esta consulta.

>[!IMPORTANT]
>
>Estas fechas/horas se basan en la zona horaria estándar del este (EST). Ajuste la zona horaria de la instancia.

* Para instancias de Campaign con información de respuesta de rechazo SMTP en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)**  contiene &quot;550-5.1.1 La cuenta de correo electrónico que intentó alcanzar no existe&quot; Y el texto del  **error (texto de cuarentena)**  contiene &quot;support.google.com&quot; **
   * **Estado de la actualización (@lastModified)** en o después del 14/12/2020 6:55:00 AM
   * **Estado de la actualización (@lastModified)** el 16/12/2020 o antes de esa fecha 6:00:00 AM

* Para instancias de Campaign con información de regla de correo electrónico entrante en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)**  contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio de correo electrónico (@domain)**  igual a &quot;gmail.com&quot; O dominio de correo electrónico (@domain) igual a &quot;googlemail.com&quot;
   * **Estado de la actualización (@lastModified)** en o después del 14/12/2020 6:55:00 AM
   * **Estado de la actualización (@lastModified)** el 16/12/2020 o antes de esa fecha 6:00:00 AM

Una vez que tenga la lista de destinatarios afectados, puede establecerlos en un estado de **[!UICONTROL Valid]** para que el flujo de trabajo **[!UICONTROL Database cleanup]** los elimine de la lista de cuarentena o simplemente elimínelos de la tabla.

**Temas relacionados:**
* [Comprender los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Clasificación del correo rechazado](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)

