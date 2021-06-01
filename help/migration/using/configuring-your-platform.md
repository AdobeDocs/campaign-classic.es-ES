---
product: campaign
title: Configuración de la plataforma
description: Configuración de la plataforma
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 2%

---

# Configuración de la plataforma{#configuring-your-platform}

Algunos cambios importantes en Adobe Campaign v7 requieren una configuración para garantizar su funcionamiento efectivo. Estos parámetros pueden ser necesarios antes o después de la migración. En esta sección se presentan los cambios correspondientes y su modo de configuración.

Durante la migración, la tabla **NmsRecipient** se vuelve a generar a partir de la definición de esquemas. Se perderá cualquier cambio realizado en la estructura SQL de esta tabla fuera de Adobe Campaign.

Ejemplo de elementos para comprobar:

* Si ha añadido una columna (o un índice) a la tabla **NmsRecipient** pero no la ha detallado en el esquema, esto no se guardará.
* El atributo **tablespace** recupera sus valores de forma predeterminada, es decir, los definidos en el asistente de implementación.
* Si ha añadido una vista de referencia a la tabla NmsRecipient , debe eliminarla antes de migrar.

Esta advertencia también afecta a los usuarios de Oracle: si ha añadido la opción **usetimestamptz:1** durante una actualización (consulte [Husos horarios](../../migration/using/general-configurations.md#time-zones)), se vuelven a generar todas las tablas que contengan al menos un campo **date+time**.

## Antes de la migración {#before-the-migration}

Al migrar a Adobe Campaign v7, deben configurarse los siguientes elementos. Estos elementos deben tratarse antes de iniciar **postupgrade**.

* Zonas horarias

   Durante la migración desde una plataforma v5.11, debe especificar la zona horaria que se utilizará después de la actualización.

   Si desea utilizar el modo &quot;zona horaria múltiple&quot;, consulte la sección [Zonas horarias](../../migration/using/general-configurations.md#time-zones).

   Si utiliza Oracle como base de datos, compruebe que los archivos de zona horaria de Oracle se hayan sincronizado correctamente entre el servidor de aplicaciones y el servidor de base de datos. Para obtener más información, consulte la sección [Oracle](../../migration/using/general-configurations.md#oracle) .

* Zonas de seguridad

   Por motivos de seguridad, ya no se puede acceder a la plataforma Adobe Campaign de forma predeterminada: debe configurar las zonas de seguridad, lo que requiere la recopilación de las direcciones IP del usuario antes de la migración.

   Para obtener más información, consulte la sección [Seguridad](../../migration/using/general-configurations.md#security).

* Sintaxis

   Algunas sintaxis en JavaScript pueden aceptarse en las versiones 5.11 y 6.02 y ya no pueden aceptarse en la versión v7 debido al uso de un nuevo intérprete. Para obtener más información, consulte la sección [JavaScript](../../migration/using/general-configurations.md#javascript) .

   Del mismo modo, se introduce una nueva sintaxis en Adobe Campaign v7 para reemplazar la sintaxis basada en SQLData. Si utiliza elementos de código con esta sintaxis, debe adaptarlos. Para obtener más información, consulte la sección [SQLData](../../migration/using/general-configurations.md#sqldata).

* Contraseñas

   Debe configurar las contraseñas **Admin** y **Internal**. Para obtener más información, consulte la sección [Contraseñas de usuario](../../migration/using/before-starting-migration.md#user-passwords) .

* Estructura de árbol

   Si migra desde una plataforma v5.11, debe reorganizar las carpetas de estructura de árbol según las normas de Adobe Campaign v6. Para obtener más información, consulte la sección [Estructura de árbol de Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interacción

   Si utiliza **Interaction**, debe eliminar todas las referencias de esquema de la versión 6.02 que ya no existan en la versión 7. Para obtener más información, consulte la sección [Interacción](../../migration/using/general-configurations.md#interaction) .

## Después de la migración {#after-the-migration}

Después de ejecutar **postupgrade**, se deben tener en cuenta los siguientes elementos y llevar a cabo las configuraciones correspondientes.

* Páginas espejo

   El bloque de personalización de páginas espejo ha cambiado con la versión 6.x. Esta nueva versión mejora la seguridad al acceder a estas páginas.

   Si ha utilizado el bloque personalizado v5 en los mensajes, la visualización de la página espejo fallará. Adobe recomienda encarecidamente utilizar el nuevo bloque personalizado al insertar una página espejo en los mensajes.

   Sin embargo, como solución temporal (y como las páginas espejo aún están activas), puede volver al antiguo bloque personalizado para evitar este problema cambiando la opción **[!UICONTROL XtkAcceptOldPasswords]** y configurarla en **[!UICONTROL 1]**. Esto no afecta al uso del nuevo bloque personalizado v6.x.

* Sintaxis

   Si se producen errores relacionados con la sintaxis, durante la actualización posterior debe activar temporalmente la opción **allowSQLInjection** en el archivo **serverConf.xml**, ya que le da tiempo de reescribir el código. Una vez adaptado el código, asegúrese de reactivar la seguridad. Para obtener más información, consulte la sección [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Conflictos

   La migración se realiza a través de una actualización posterior y es posible que los conflictos aparezcan en informes, formularios o aplicaciones web. Estos conflictos se pueden resolver desde la consola.

   Consulte la sección [Conflictos](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Si ha personalizado la carpeta de instalación, asegúrese de que está correctamente actualizada después de la migración. Para obtener más información, consulte la sección [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Informes

   Todos los informes listos para usar actualmente utilizan el motor de renderización v6.x. Si ha añadido código JavaScript a los informes, es posible que algunos elementos se modifiquen.

   Consulte la sección [Informes](../../migration/using/general-configurations.md#reports) .

* Aplicaciones web

   Después de la actualización, si tiene problemas para conectarse a sus aplicaciones web identificadas, debe activar las opciones **allowUserPassword** y **sessionTokenOnly** en el archivo **serverConf.xml**. Recuerde desactivar estas dos opciones. Para obtener más información, consulte la sección [Aplicaciones web identificadas](../../migration/using/general-configurations.md#identified-web-applications) .

   Según el tipo de aplicaciones web y su configuración, debe realizar manipulaciones adicionales para asegurarse de que funcionan correctamente.

   Consulte la sección [Web applications](../../migration/using/general-configurations.md#web-applications).

   Si se migra desde una plataforma v5.11, se deben realizar configuraciones adicionales: para obtener más información, consulte la sección [Web applications](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Zonas de seguridad.

   Antes de iniciar el servidor, debe configurar las zonas de seguridad. Para obtener más información, consulte [esta sección](../../installation/using/security-zones.md) y la sección [Seguridad](../../migration/using/general-configurations.md#security).

* Esquemas

   En Red Hat, puede encontrar errores al editar determinados esquemas. Para obtener más información, consulte la sección [Red-Hat](../../migration/using/general-configurations.md#red-hat).

* Flujos de trabajo

   Si migra desde una plataforma v5.11, debe controlar el directorio de tiempo de ejecución de flujos de trabajo. Para obtener más información, consulte la sección [Flujos de trabajo](../../migration/using/specific-configurations-in-v5-11.md#workflows) .

* Seguimiento

   Si migra desde una plataforma v5.11, debe configurar el modo de seguimiento. Para obtener más información, consulte la sección [Seguimiento](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Página de inicio

   Si migra desde una plataforma v6.02, puede definir parámetros adicionales para mantener la página principal antigua desde v6.02. Para obtener más información, consulte la [Facilidad de uso: Página de inicio y sección de navegación](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interacción

   Si utiliza **Interaction**, debe ajustar los parámetros después de la migración. Para obtener más información, consulte la sección [Interacción](../../migration/using/general-configurations.md#interaction) .
