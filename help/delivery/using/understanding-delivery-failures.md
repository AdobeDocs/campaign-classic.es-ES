---
product: campaign
title: Comprensión de los errores de entrega
description: Aprenda a comprender los errores de entrega
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 48%

---

# Comprensión de los errores de entrega{#understanding-delivery-failures}

>[!NOTE]
>
>Encontrará instrucciones detalladas para comprender los errores de entrega en la página [Campaign v8, Comprensión de los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures). Este contenido se aplica tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8 y cubre lo siguiente:
>
>* Tipos y motivos de errores de entrega (grave, leve, ignorado)
>* Errores sincrónicos y asíncronos
>* Calificación del correo rechazado
>* Tipos de error de correo electrónico, notificaciones push y SMS
>* Administración de reintentos y períodos de validez
>* Solución de problemas de envíos comunes
>
>Esta página documenta **la configuración específica de Campaign Classic v7** para la administración de correo de rebote en implementaciones híbridas y locales.

Para obtener conceptos comunes sobre errores de entrega, tipos de error e instrucciones para la solución de problemas, consulte la [documentación de Campaign v8 Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Configuración de correo rechazado {#v7-bounce-mail-config}

Las siguientes opciones de configuración están disponibles para **implementaciones híbridas/on-premise de Campaign Classic v7** para administrar el procesamiento de correos rechazados.

### Configuración del buzón de rechazos {#bounce-mailbox-configuration}

Para instalaciones on-premise, la configuración del buzón de rechazos se detalla en [esta sección](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

La plataforma Adobe Campaign recopila los mensajes de error asíncronos a través del buzón de rechazos y los califica el proceso inMail para enriquecer la lista de reglas de gestión de correo electrónico.

>[!NOTE]
>
>Para los usuarios de Cloud Services administrados de Campaign v8, la configuración del buzón de rechazos la realiza y administra Adobe. No se requiere ninguna configuración.

### Administración de cualificación de correo rechazado {#bounce-mail-qualification-management}

En el caso de instalaciones on-premise e instalaciones alojadas/híbridas que utilizan el servidor de correo de Campaign heredado, cuando se produce un error en el envío de un correo electrónico, el servidor de envío de Adobe Campaign recibe un mensaje de error del servidor de mensajería o del servidor DNS remoto. La lista de errores se compone de cadenas de caracteres incluidas en el mensaje rechazado por el servidor remoto. Los tipos y los motivos del error se asignan a cada mensaje.

Esta lista está disponible a través del nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**. Contiene todas las reglas utilizadas por Adobe Campaign para clasificar los errores de entrega. No es exhaustiva, Adobe Campaign la actualiza regularmente y también la puede administrar el usuario.

![](assets/tech_quarant_rules_qualif.png)

El mensaje rechazado por el servidor remoto en la primera vez que se produjo este tipo de error se muestra en la columna **[!UICONTROL First text]** de la tabla **[!UICONTROL Delivery log qualification]**. Si no se muestra esta columna, haga clic en el botón **[!UICONTROL Configure list]** situado en la parte inferior derecha de la lista para seleccionarla.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtra este mensaje para eliminar el contenido de la variable (como ID, fechas, direcciones de correo electrónico, números de teléfono, etc.) y muestra el resultado filtrado en la columna **[!UICONTROL Text]**. Las variables se reemplazan por **`#xxx#`**, excepto las direcciones que se sustituyen por **`*`**.

Este proceso permite reunir todos los errores del mismo tipo y evitar entradas múltiples para errores similares en la tabla Calificación del registro de envío.

>[!NOTE]
>
>El campo **[!UICONTROL Number of occurrences]** muestra el número de veces que se ha producido el mensaje en la lista. Está limitado a 100 000 incidencias. Si lo desea, puede editar el campo, por ejemplo, para reiniciarlo.

Los correos electrónicos rechazados pueden tener el siguiente estado de calificación:

* **[!UICONTROL To qualify]**: no se pudo calificar el correo rechazado. Se debe asignar la calificación al equipo de entregas para garantizar una capacidad de entrega eficiente de la plataforma. Siempre que no esté clasificado, no se usa el correo rechazado para enriquecer la lista de reglas de gestión de correo electrónico.
* **[!UICONTROL Keep]**: el correo rechazado se ha clasificado y el flujo de trabajo **Actualizar la entrega** lo usará para compararlo con las reglas de gestión de correo electrónico existentes y enriquecer la lista.
* **[!UICONTROL Ignore]**: el MTA de Campaign ignora el correo rechazado, lo que significa que esta devolución nunca hará que la dirección del destinatario se ponga en cuarentena. El flujo de trabajo de **actualización para la entrega** no lo usará y no se enviará a las instancias de cliente.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>En caso de una interrupción de un ISP, los correos electrónicos enviados a través de Campaign se marcan erróneamente como rechazos. Para corregir esto, debe actualizar la calificación de devoluciones. Para obtener más información, consulte [esta página](update-bounce-qualification.md).

### Configuración de reglas de gestión de correo electrónico {#email-management-rules}

Se accede a las reglas de correo a través del nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**. Las reglas de administración de correo electrónico se muestran en la parte inferior de la ventana.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Los parámetros predeterminados de la plataforma se configuran en el asistente de implementación. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md).

Las reglas predeterminadas son las siguientes:

>[!IMPORTANT]
>
>* El servidor de entrega (MTA) debe reiniciarse si se han cambiado los parámetros.
>* La modificación o creación de reglas de administración solo es para usuarios expertos.

#### Correo electrónico entrante {#inbound-email}

Estas reglas contienen las cadenas que pueden devolver los servidores remotos y que permiten calificar el error (**Grave**, **leve** o **ignorado**).

Cuando un mensaje de correo electrónico falla, el servidor remoto devuelve un mensaje de rechazo a la dirección especificada en los parámetros de la plataforma. Adobe Campaign compara el contenido de cada mensaje de rechazo con las cadenas de la lista de reglas y, a continuación, lo asigna a uno de los tres tipos de error.

>[!NOTE]
>
>El usuario puede crear sus propias reglas. Al importar un paquete y al actualizar datos mediante el flujo de trabajo **Refresh for deliverability**, se sobrescriben las reglas creadas por el usuario.

Para obtener más información sobre la calificación de correo rechazado, consulte [esta sección](#bounce-mail-qualification-management).

#### Administración de dominios {#domain-management}

Para instalaciones on-premise, el MTA aplica una sola regla de **Administración de dominios** a todos los dominios.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Se puede elegir si activar o no determinadas normas de identificación y claves de cifrado para comprobar el nombre del dominio como, por ejemplo, **ID de remitente**, **DomainKeys**, **DKIM** y **S/MIME**.
* Los parámetros **SMTP relay** permiten configurar la dirección IP y el puerto de un servidor de transmisión para un dominio determinado. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#smtp-relay).

Si sus mensajes muestran **[!UICONTROL on behalf of]** en la dirección del remitente, asegúrese de no firmar correos electrónicos con **ID de remitente**, que es el estándar de autenticación de correo electrónico propietario obsoleto de Microsoft. Si la opción **[!UICONTROL Sender ID]** está habilitada, desmarque la casilla correspondiente y póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). La capacidad de envío no se ve afectada.

#### Administración de MX {#mx-management}

Para las instalaciones on-premise, se utilizan reglas de administración MX para regular el flujo de correos electrónicos salientes para un dominio específico.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

Estas reglas están disponibles en el asistente de implementación y se pueden personalizar:

* **[!UICONTROL MX Management]**: esta regla se usa para controlar el flujo de correos electrónicos salientes para un dominio. Realiza muestras de los mensajes rechazados y bloquea la entrega a donde corresponda.

* **[!UICONTROL Period]**: lapso de tiempo durante el cual se limitan o bloquean los mensajes.

* **[!UICONTROL Limit]**: el número máximo de mensajes permitidos por período de tiempo.

* **[!UICONTROL Type]**: tipo de error (grave, leve o omitido) utilizado para determinar el comportamiento de envío. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} para ver las definiciones de tipo de error.

Para obtener más información sobre gestión MX, consulte [esta sección](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>Para los usuarios de Cloud Services administrados de Campaign v8, las reglas MX y la administración de flujo de correo electrónico son administradas por Adobe como parte de la infraestructura administrada. Póngase en contacto con el Servicio de atención al cliente de Adobe si necesita ajustar la configuración MX para casos de uso específicos.

## Temas relacionados

* [Comprender los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Documentación de Campaign v8)
* [Estados de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentación de Campaign v8)
* [Administración de cuarentena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentación de Campaign v8)
* [Configuración de cuarentena](understanding-quarantine-management.md) (v7 híbrido/local)
* [Actualizar calificación de devoluciones](update-bounce-qualification.md) (v7 híbrido/local)
* [Configuración de envío de correo electrónico](../../installation/using/email-deliverability.md) (v7 híbrido/local)
* [Implementación de una instancia](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 híbrida/local)
