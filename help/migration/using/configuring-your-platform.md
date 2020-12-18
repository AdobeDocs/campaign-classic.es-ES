---
solution: Campaign Classic
product: campaign
title: Configuración de la plataforma
description: Configuración de la plataforma
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 2%

---


# Configuración de la plataforma{#configuring-your-platform}

Algunos cambios importantes en Adobe Campaign v7 requieren una configuración para garantizar su funcionamiento efectivo. Estos parámetros pueden ser necesarios antes o después de la migración. Los cambios correspondientes y su modo de configuración se presentan en esta sección.

Durante la migración, la tabla **NmsRecipient** se vuelve a generar a partir de la definición de esquemas. Cualquier cambio realizado en la estructura SQL de esta tabla fuera de Adobe Campaign se perderá.

Elementos de ejemplo para comprobar:

* Si ha agregado una columna (o un índice) a la tabla **NmsRecipient** pero no la ha detallado en el esquema, no se guardará.
* El atributo **tablespace** recupera sus valores de forma predeterminada, es decir, los definidos en el asistente de implementación.
* Si ha agregado una vista de referencia a la tabla NmsRecipient, debe eliminarla antes de migrar.

Esta advertencia también afecta a los usuarios de Oracle: si ha agregado la opción **usetimestamptz:1** durante una posactualización (consulte [Husos horarios](../../migration/using/general-configurations.md#time-zones)), se volverán a generar todas las tablas que contengan al menos un campo **fecha+hora**.

## Antes de la migración {#before-the-migration}

Al migrar a Adobe Campaign v7, deben configurarse los siguientes elementos. Estos elementos se deben abordar antes de iniciar el **postupgrade**.

* Husos horarios

   Durante una migración desde una plataforma v5.11, debe especificar la zona horaria que se utilizará durante la posactualización.

   Si desea utilizar el modo &quot;multizona horaria&quot;, consulte la sección [Husos horarios](../../migration/using/general-configurations.md#time-zones).

   Si utiliza Oracle como base de datos, compruebe que los archivos de zona horaria de Oracle se han sincronizado correctamente entre el servidor de aplicaciones y el servidor de base de datos. Para obtener más información sobre esto, consulte la sección [Oracle](../../migration/using/general-configurations.md#oracle).

* Zonas de seguridad

   Por motivos de seguridad, la plataforma Adobe Campaign ya no es accesible de forma predeterminada: debe configurar las zonas de seguridad, lo que requiere la recopilación de las direcciones IP del usuario antes de la migración.

   Para obtener más información, consulte la sección [Seguridad](../../migration/using/general-configurations.md#security).

* Syntax

   Algunas sintaxis en JavaScript pueden aceptarse en las versiones 5.11 y 6.02 y ya no aceptarse en la versión v7 debido al uso de un nuevo intérprete. Para obtener más información, consulte la sección [JavaScript](../../migration/using/general-configurations.md#javascript).

   Del mismo modo, se introduce una nueva sintaxis en Adobe Campaign v7 para reemplazar la sintaxis basada en SQLData. Si utiliza elementos de código con esta sintaxis, debe adaptarlos. Para obtener más información, consulte la sección [SQLData](../../migration/using/general-configurations.md#sqldata).

* Contraseñas

   Debe configurar las contraseñas **Administración** y **Internas**. Para obtener más información, consulte la sección [Contraseñas de usuario](../../migration/using/before-starting-migration.md#user-passwords).

* Estructura de árbol

   Si realiza la migración desde una plataforma v5.11, debe reorganizar las carpetas de estructura de árbol de acuerdo con las normas de Adobe Campaign v6. Para obtener más información, consulte la sección [Estructura de árbol de Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure).

* Interacción

   Si utiliza **Interacción**, debe eliminar todas las referencias de esquema 6.02 que ya no existan en v7. Para obtener más información, consulte la sección [Interacción](../../migration/using/general-configurations.md#interaction).

## Después de la migración {#after-the-migration}

Después de ejecutar **postupgrade**, se deben tener en cuenta los siguientes elementos y se deben llevar a cabo las configuraciones correspondientes.

* Páginas espejo

   El bloque de personalización de página espejo ha cambiado con v6.x. Esta nueva versión mejora la seguridad al acceder a estas páginas.

   Si ha utilizado el bloque de personalización v5 en los mensajes, la visualización de la página espejo fallará. Adobe recomienda encarecidamente utilizar el nuevo bloque de personalización al insertar página espejo en los mensajes.

   Sin embargo, como solución temporal (y como las páginas espejo siguen activas), puede volver al antiguo bloque de personalización para evitar este problema cambiando la opción **[!UICONTROL XtkAcceptOldPasswords]** y establecerla en **[!UICONTROL 1]**. Esto no afectará al uso del nuevo bloque de personalización v6.x.

* Sintaxis

   Si encuentra algún error relacionado con la sintaxis, durante la posactualización debe activar temporalmente la opción **allowSQLInjection** en el archivo **serverConf.xml**, ya que esto le da tiempo para reescribir el código. Una vez adaptado el código, asegúrese de reactivar la seguridad. Para obtener más información sobre esto, consulte la sección [SQLData](../../migration/using/general-configurations.md#sqldata).

* Conflictos

   La migración se realiza a través de una actualización posterior y pueden aparecer conflictos en informes, formularios o aplicaciones Web. Estos conflictos se pueden resolver desde la consola.

   Consulte la sección [Conflictos](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Si ha personalizado la carpeta de instalación, asegúrese de comprobar que se ha actualizado correctamente tras la migración. Para obtener más información, consulte la sección [Tomcat](../../migration/using/general-configurations.md#tomcat).

* Informes

   Todos los informes predeterminados utilizan actualmente el motor de procesamiento v6.x. Si ha agregado código JavaScript a los informes, algunos elementos pueden modificarse.

   Consulte la sección [Informes](../../migration/using/general-configurations.md#reports).

* Aplicaciones web

   Después de la actualización posterior, si tiene problemas para conectarse a sus Aplicaciones web identificadas, debe activar las opciones **allowUserPassword** y **sessionTokenOnly** en el archivo **serverConf.xml**. Recuerde desactivar estas dos opciones. Para obtener más información, consulte la sección [Aplicaciones Web identificadas](../../migration/using/general-configurations.md#identified-web-applications).

   Según el tipo de Aplicaciones web y su configuración, debe realizar manipulaciones adicionales para asegurarse de que funcionan correctamente.

   Consulte la sección [Aplicaciones web](../../migration/using/general-configurations.md#web-applications).

   Si realiza la migración desde una plataforma v5.11, se deben realizar configuraciones adicionales: para obtener más información, consulte la sección [Aplicaciones web](../../migration/using/specific-configurations-in-v5-11.md#web-applications).

* Zonas de seguridad.

   Antes de iniciar el servidor, debe configurar las zonas de seguridad. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#defining-security-zones) y la sección [Seguridad](../../migration/using/general-configurations.md#security).

* Esquemas

   En Red Hat, puede encontrar errores al editar determinados esquemas. Para obtener más información sobre esto, consulte la sección [Red-Hat](../../migration/using/general-configurations.md#red-hat).

* Flujos de trabajo

   Si realiza la migración desde una plataforma v5.11, debe controlar el directorio de tiempo de ejecución de flujos de trabajo. Para obtener más información sobre esto, consulte la sección [Flujos de trabajo](../../migration/using/specific-configurations-in-v5-11.md#workflows).

* Seguimiento

   Si realiza la migración desde una plataforma v5.11, debe configurar el modo de seguimiento. Para obtener más información sobre esto, consulte la sección [Seguimiento](../../migration/using/specific-configurations-in-v5-11.md#tracking).

* Página de inicio

   Si realiza la migración desde una plataforma v6.02, puede definir parámetros adicionales para mantener la página de inicio antigua de v6.02. Para obtener más información sobre esto, consulte [Facilidad de uso: Página de inicio y navegación](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interacción

   Si utiliza **Interacción**, debe ajustar los parámetros después de la migración. Para obtener más información sobre esto, consulte la sección [Interacción](../../migration/using/general-configurations.md#interaction).

