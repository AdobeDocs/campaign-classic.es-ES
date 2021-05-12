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
translation-type: ht
source-git-commit: 718b490d48c6cfabdb24ab18dffb6db664f2a46c
workflow-type: ht
source-wordcount: '427'
ht-degree: 100%

---

# Actualizar devoluciones graves incorrectas después de la interrupción de Apple {#update-bounce-qualification.md}

## Contexto

El 26 de abril de 2021, un problema global en Apple provocó que los servidores de Apple devolvieran incorrectamente algunos mensajes de correo electrónico enviados a direcciones de correo electrónico válidas de Apple por ser direcciones de correo electrónico no válidas y con la siguiente respuesta de rebote: &quot;550 5.1.1 &#39;dirección de correo electrónico&#39;: la búsqueda del usuario se ha realizado correctamente, pero no se ha encontrado ningún registro de usuario&quot;.

Este problema ocurrió el 26 de abril, desde las 07:00 h a las 13:00 h EST.

>[!NOTE]
>
>Puede consultar el panel del estado de Apple System en [esta página](https://www.apple.com/es/support/systemstatus/).

En caso de interrupción de un ISP, los correos electrónicos enviados a través de Campaign no se pueden enviar correctamente a su destinatario: estos correos electrónicos se marcarán erróneamente como devoluciones.

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones a continuación.

## Proceso de actualización

Deberá ejecutar una consulta en la tabla de cuarentena para filtrar todos los destinatarios de Apple, que incluyen @icloud.com, @me.com y @mac.com, que se hayan visto potencialmente afectados por la interrupción para que se puedan eliminar de la lista de cuarentena y se puedan incluir en futuros envíos de correo electrónico de Campaign.

En función del periodo de tiempo del problema, se indican a continuación las directrices recomendadas para esta consulta.

>[!IMPORTANT]
>
>Estas fechas/horas se basan en la zona horaria estándar del este (EST). Ajuste la zona horaria de la instancia.

* Para instancias de Campaign con información de respuesta de rechazo SMTP en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto de error (texto de cuarentena)** contiene &quot;la búsqueda del usuario se ha realizado correctamente, pero no se ha encontrado ningún registro de usuario&quot; Y **el texto de error (texto de cuarentena)** contiene &quot;support.apple.com&quot;
   * **Estado de la actualización (@lastModified)** el 26 de abril de 2021 a las 07:00:00 h, o después
   * **Estado de la actualización (@lastModified)** el 26 de abril de 2021 a las 13:00:00 h, o antes

* Para instancias de Campaign con información de regla de correo electrónico entrante en el campo **[!UICONTROL Error text]** de la lista de cuarentena:

   * **El texto del error (texto de cuarentena)** contiene “Momen_Code10_InvalidRecipient”
   * **Dominio de correo electrónico (@domain)** igual a icloud.com O **dominio de correo electrónico (@domain)** igual a me.com O **dominio de correo electrónico (@domain)** igual a mac.com
   * **Estado de la actualización (@lastModified)** el 26 de abril de 2021 a las 07:00:00 h, o después
   * **Estado de la actualización (@lastModified)** el 26 de abril de 2021 a las 13:00:00 h, o antes

Una vez que tenga la lista de destinatarios afectados, puede aplicarles un estado **[!UICONTROL Valid]** para que el flujo de trabajo **[!UICONTROL Database cleanup]** los elimine de la lista de cuarentena, o simplemente elimínelos de la tabla.

**Temas relacionados:**
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
* [Clasificación del correo rechazado](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
