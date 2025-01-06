---
title: Migración de los operadores de Campaign a Adobe Identity Management System (IMS)
description: Obtenga información sobre cómo migrar operadores de Campaign a Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 2%

---

# Migración de los operadores de Campaign a Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar el modo de autenticación del usuario final de la autenticación nativa de inicio de sesión/contraseña a Adobe Identity Management System (IMS). Todos los operadores deben implementar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} para conectarse a Campaign.

Obtenga más información acerca de esta migración en [esta página](ac-ims.md).

## ¿Qué ha cambiado? {#move-to-ims-changes}

Con Campaign Classic, todos los usuarios normales ya pueden conectarse a la consola del cliente de Adobe Campaign con su Adobe ID, a través del Sistema Identity Management de Adobe (IMS). Sin embargo, las conexiones de usuario y contraseña siguen estando disponibles. Esto ya no se permitirá con Campaign v8.

Además, como parte del esfuerzo por reforzar la seguridad y el proceso de autenticación, la aplicación cliente de Adobe Campaign ahora llama a las API de Campaign directamente mediante el token de cuenta técnica de IMS. La migración para operadores técnicos se detalla en un artículo dedicado, disponible en [esta página](ims-migration.md).

Este cambio ya se aplica en Campaign Classic v7 y será **obligatorio** para pasar a Campaign v8.

El Adobe le ayuda en este esfuerzo de migración. Puede encontrar información detallada sobre el contexto y las directrices paso a paso en el siguiente artículo.

## ¿Se ha visto afectado?{#migrate-ims-impacts}

Este procedimiento se aplica a todos los usuarios de Campaign que aún no se hayan conectado a Campaign con su Adobe ID.

Si los operadores de su organización se conectan a la consola del cliente de Campaign mediante su inicio de sesión/contraseña (también conocido como. (autenticación nativa), se ha visto afectado y debe migrar estos operadores a Adobe IMS como se detalla a continuación.

La migración a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"} es un imperativo de seguridad para que sus entornos sean seguros y estandarizados, ya que la mayoría de las otras soluciones y aplicaciones de Adobe Experience Cloud ya están en IMS.

Este cambio es aplicable a partir de la versión 7.4.1 de Campaign Classic (y las [últimas versiones compatibles con la migración IMS](ac-ims.md#ims-versions)) y es **obligatorio** para pasar a la versión 8 de Adobe Campaign.


## ¿Cómo migrar entornos alojados y de Managed Services? {#ims-migration-procedure}

### Requisitos previos {#ims-migration-prerequisites}

Antes de iniciar el proceso de migración, debe ponerse en contacto con el administrador de transición de Adobe (para los clientes de Managed Services) o con el servicio de atención al cliente de Adobe (para otros clientes alojados), de modo que los equipos técnicos de Adobe puedan migrar los grupos de operadores existentes y los derechos asignados a Adobe Identity Management System (IMS).

### Pasos clave {#ims-migration-steps}

A continuación se enumeran los pasos clave para esta migración:

1. El Adobe actualiza sus entornos a Campaign v7.4.1 (o una [versión compatible con la migración IMS](ac-ims.md#ims-versions)).
1. Después de la actualización, aún puede crear nuevos usuarios con ambos métodos, como usuario nativo o con IMS.
1. El administrador de Campaign interno debe añadir correos electrónicos únicos a todos los usuarios nativos en la consola del cliente de Campaign y confirmar esto al representante de Adobe/Servicio de atención al cliente una vez hecho.  Este paso se detalla en [esta sección](#ims-migration-id).
1. Póngase en contacto con su representante de Adobe o con el Servicio de atención al cliente para fijar una fecha de Adobe y ejecutar la migración automatizada para los usuarios no técnicos (operadores) y los perfiles de producto. Este paso requiere un intervalo de horas sin tiempo de inactividad en ninguno de los servicios.
1. El administrador de Campaign interno valida estos cambios y proporciona una firma. Después de esta migración, ya no debe crear ningún operador adicional que se autentique con este inicio de sesión y contraseña.

También puede migrar sus operadores técnicos a Adobe Developer Console como se detalla en [esta nota técnica](ims-migration.md).

Una vez completada esta migración, confirme con el administrador de transición de Adobe (para usuarios de Managed Services) o con el servicio de atención al cliente de Adobe (para clientes alojados). A continuación, el Adobe marca la migración como completada. A continuación, su entorno está protegido y estandarizado.


## Cómo migrar entornos híbridos y locales {#ims-migration-procedure-on-prem}

A continuación se enumeran los pasos clave para esta migración:

1. Actualice sus entornos a Campaign v7.4.1 (o una [versión compatible con la migración IMS](#ims-versions)).
1. Después de la actualización, aún puede crear nuevos usuarios con ambos métodos, como usuario nativo o con IMS.
1. El administrador interno de Campaign debe configurar Adobe IMS como se detalla en [esta sección](../../integrations/using/configuring-ims.md).
1. A continuación, añada correos electrónicos únicos a todos los usuarios nativos en la consola del cliente de Campaign. Este paso se detalla en [esta sección](#ims-migration-id).
1. Cree usuarios y perfiles de producto en Adobe Admin Console como se detalla en [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Habilite la opción **Conectar con Adobe ID** para todos los operadores.
1. Implemente Adobe IMS para su conexión según se detalla en [esta página](../../integrations/using/implementing-ims.md).

También puede migrar sus operadores técnicos a Adobe Developer Console como se detalla en [esta nota técnica](ims-migration.md).


## Preguntas frecuentes {#ims-migration-faq}

### ¿Cómo se crean usuarios después de la migración? {#ims-migration-native}

El Adobe recomienda crear solo usuarios de IMS después de actualizar a Campaign Classic v7.4.1 (o una [versión compatible con la migración de IMS](#ims-versions)).
A partir de la versión 7.4.1 de Campaign, puede evitar la creación de operadores nativos al actualizar la configuración de la instancia como se detalla en [esta página](impact-ims-migration.md).

Como administrador de Campaign, puede conceder permisos a los usuarios de su organización a través de Adobe Admin Console y la consola del cliente de Campaign. Los usuarios inician sesión en Adobe Campaign con su Adobe ID. Obtenga información sobre cómo configurar permisos con IMS en [Documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=es){target="_blank"}.

### ¿Cómo se agregan correos electrónicos para los usuarios nativos actuales? {#ims-migration-id}

Como administrador de Campaign, debe agregar ID de correo electrónico a todos los usuarios nativos desde la consola del cliente. Para realizar esto, siga los pasos a continuación:

1. Conéctese a la consola del cliente y vaya a **Administración > Administración de acceso > Operadores**.
1. Seleccione el operador que desea actualizar en la lista de operadores.
1. Escriba el correo electrónico del operador en la sección **Puntos de contacto** del formulario del operador.
1. Guarde los cambios.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### ¿Cómo iniciar sesión en Campaign a través de IMS? {#ims-migration-log}

Aprenda a conectarse a Campaign con su Adobe ID en [esta sección](../../integrations/using/implementing-ims.md).

### ¿Habrá un tiempo de inactividad durante esta migración? {#ims-migration-downtime}

Para los clientes alojados y de Managed Services, para finalizar la migración (migrar usuarios y perfiles de producto), el Adobe requiere un intervalo de una hora sin tiempo de inactividad en ninguna instancia (flujos de trabajo, etc.).

Durante este periodo, todos los usuarios de Campaign deben cerrar la sesión y volver a iniciarla con su Adobe ID una vez finalizada la migración a IMS.

El Adobe recomienda encarecidamente que se cierre la sesión de todos los usuarios durante la ventana de migración.

### Los usuarios de mi organización ya están utilizando IMS, ¿aún tengo que realizar la migración de IMS?{#ims-migration-needed}

Esta migración tiene dos aspectos: migración de usuarios finales (además de perfiles de producto) y migración de usuarios técnicos (utilizados en las API de su código personalizado).

Si todos los usuarios (operadores de Campaign) están en IMS, aún debe ponerse en contacto con su representante de Adobe/Asistencia al cliente para planificar la migración de perfiles de producto. También deberá migrar a los usuarios técnicos que pueda haber utilizado en el código personalizado. Obtenga más información en [esta página](ims-migration.md).

### ¿Cómo se puede ver el tipo de autenticación de los operadores?

Obtenga información sobre cómo ver el tipo de autenticación de los operadores en Campaign:

1. Desde **Explorer**, acceda a **Administration** `>` **Access Management** `>` **Operators**.

1. Haga clic con el botón derecho en la fila del encabezado y seleccione el menú **Configurar lista**.

   ![](assets/ims_2.png)

1. Agregar **cuenta deshabilitada** y **tipo de autenticación** como **columnas de salida**.

   ![](assets/ims_1.png)

Ahora puede ver la lista de sus **Operadores** y su **Tipo de autenticación**.

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [Migración de usuarios técnicos a la consola de Adobe Developer](ims-migration.md)
>* [Notas de la versión de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Qué es el sistema Identity Management de Adobe (IMS)](https://helpx.adobe.com/es/enterprise/using/identity.html){target="_blank"}
