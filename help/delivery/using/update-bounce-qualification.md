---
solution: Campaign Classic
product: campaign
title: Actualización de la calificación de devoluciones después de una interrupción del ISP
description: Obtenga información sobre cómo actualizar la calificación de devoluciones después de una interrupción del ISP.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 9260b467119475e9e0352b6e521d6f2ca426165c
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 59%

---

# Actualizar devoluciones duras incorrectas después de la interrupción de Apple {#update-bounce-qualification.md}

## Contexto

El 26 de abril de 2021, un problema global en Apple provocó que algunos mensajes de correo electrónico enviados a direcciones de correo electrónico válidas de Apple se devolvieran incorrectamente como direcciones de correo electrónico no válidas por parte de servidores de Apple con la siguiente respuesta de rechazo:  &quot;550 5.1.1 &#39;dirección de correo electrónico&#39;: la búsqueda del usuario se ha realizado correctamente, pero no se ha encontrado ningún registro de usuario&quot;.

Este problema ocurrió el 26 de abril y duró de 7 a. m. a 1 p. m. hora del Este.

>[!NOTE]
>
>Puede consultar el Panel de estado del sistema de Apple en [esta página](https://www.apple.com/support/systemstatus/).

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como rechazos.

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema de , o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones a continuación.

## Proceso de actualización

Deberá ejecutar una consulta en la tabla de cuarentena para filtrar todos los destinatarios de Apple, que incluyen @icloud.com, @me.com, @mac.com, que se hayan visto potencialmente afectados por la interrupción de modo que puedan ser eliminados de la lista de cuarentena e incluidos en futuros envíos de correo electrónico de Campaign.

En función del periodo de tiempo del problema, se indican a continuación las directrices recomendadas para esta consulta.

>[!IMPORTANT]
>
>Estas fechas/horas se basan en la zona horaria estándar del este (EST). Ajuste la zona horaria de la instancia.

* Para instancias de Campaign con información de respuesta de rechazo SMTP en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)**  contiene &quot;éxito de búsqueda del usuario pero no se ha encontrado ningún registro del usuario&quot; Y el texto del  **error (texto de cuarentena)**  contiene &quot;support.apple.com&quot;
   * **Estado de la actualización (@lastModified)** el 26/4/2021 a las 07:00:00 h, o después.
   * **Estado de la actualización (@lastModified)** el 26/4/2021 o antes de las 01:00:00 PM

* Para instancias de Campaign con información de regla de correo electrónico entrante en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)** contiene “Momen_Code10_InvalidRecipient”
   * **Dominio de correo electrónico (@domain)**  igual a icloud.com&quot; O dominio de correo electrónico (@domain) igual a me.com&quot; O dominio de correo electrónico (@domain) igual a mac.com&quot;
   * **Estado de la actualización (@lastModified)** el 26/4/2021 a las 07:00:00 h, o después.
   * **Estado de la actualización (@lastModified)** el 26/4/2021 o antes de las 01:00:00 PM

Una vez que tenga la lista de destinatarios afectados, puede aplicarles un estado **[!UICONTROL Valid]** para que el flujo de trabajo **[!UICONTROL Database cleanup]** los elimine de la lista de cuarentena, o simplemente elimínelos de la tabla.

**Temas relacionados:**
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
* [Clasificación del correo rechazado](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
