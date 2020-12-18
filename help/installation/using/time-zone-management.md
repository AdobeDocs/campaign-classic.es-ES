---
solution: Campaign Classic
product: campaign
title: Administración de husos horarios
description: Administración de husos horarios
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---


# Administración de husos horarios{#time-zone-management}

## Principio de funcionamiento {#operating-principle}

Adobe Campaign permite expresar fechas en función de su zona horaria: esto permite a los usuarios internacionales trabajar en distintos husos horarios en todo el mundo. Cada país que utiliza la misma instancia puede administrar la ejecución de campañas, el seguimiento, el archivo, etc. según la hora local.

Para permitir el uso de la plataforma Adobe Campaign a escala internacional, todas las fechas utilizadas por los sistemas deben estar vinculadas a una zona horaria. Una fecha cuyo huso horario se conozca puede importarse en cualquier otra zona horaria, o sin importar el huso horario.

Adobe Campaign permite almacenar fechas y horas en formato UTC (hora universal coordinada). Cuando se exponen los datos, se convierten en la fecha y hora locales del operador. La conversión se realiza automáticamente cuando la base de datos está configurada en UTC (consulte [Configuration](#configuration)). Si la base de datos no está configurada en UTC, la información sobre la zona horaria de las fechas en la plataforma se almacena en una opción.

Las principales funcionalidades de la plataforma con respecto a la administración de huso horario son: importar/exportar datos y administración de operadores y flujos de trabajo. El **concepto de herencia** está disponible para importaciones/exportaciones o Flujos de trabajo. De forma predeterminada, están configuradas para el huso horario del servidor de la base de datos, aunque puede redefinir nuevos husos horarios para un flujo de trabajo e incluso para una sola actividad.

**Los** operadores pueden modificar los husos horarios durante la  **configuración del** envío y pueden especificar el huso horario concreto en el que se ejecutará el envío.

>[!IMPORTANT]
>
>Si la base de datos no administra varios husos horarios, para todas las manipulaciones de filtrado de datos, las consultas SQL deben ejecutarse en el huso horario del servidor de la base de datos.

Cada operador de Adobe Campaign está vinculado a un huso horario: esta información se configura en su perfil. Para obtener más información sobre esto, consulte [este documento](../../platform/using/access-management.md).

Cuando la plataforma de Adobe Campaign no requiere la administración de huso horario, puede mantener un modo de almacenamiento en formato local con un huso horario vinculado específico.

## Recomendaciones {#recommendations}

Los husos horarios combinan varias realidades: la expresión podrá indicar un desfase temporal constante con la fecha UTC, o las horas de una región que pueden cambiar dos veces al año (horario de verano).

Por ejemplo, en postgreSQL, el comando **SET TIME ZONE &#39;Europe/Paris&#39;;** tendrá en cuenta los tiempos de verano e invierno: la fecha se expresará en UTC+1 o UTC+2 según la hora del año.

Sin embargo, si utiliza el comando **SET TIME ZONE 0200;**, el intervalo de tiempo siempre será UTC+2.

## Configuración {#configuration}

El modo de almacenamiento de fechas y horas se selecciona durante la creación de la base de datos (consulte [Creación de una nueva instancia](#creating-a-new-instance)). En el caso de una migración, las horas vinculadas a las fechas se convierten en fechas y horas locales (consulte [Migración](#migration)).

Desde un punto de vista técnico, existen dos maneras de almacenar información de tipo **Date+time** en la base de datos:

1. MARCA DE HORA CON formato DE ZONA DE HORA: el motor de base de datos almacena las fechas en UTC. Cada sesión abierta tendrá un huso horario y las fechas se convertirán según él.
1. Formato local + zona horaria local: todas las fechas se almacenan en el formato local (sin gestión de intervalo de tiempo) y se les asigna una sola zona horaria. El huso horario se almacena en la opción **WdbcTimeZone** de la instancia de Adobe Campaign y se puede cambiar mediante el menú **[!UICONTROL Administration > Platform > Options]** del árbol.

>[!IMPORTANT]
>
>Tenga en cuenta que esta modificación puede provocar problemas de coherencia y sincronización de los datos.

### Creación de una nueva instancia {#creating-a-new-instance}

Para que varios usuarios internacionales trabajen en la misma instancia, debe configurar husos horarios al crear la instancia para administrar los husos horarios entre países. Durante la creación de instancias, seleccione el modo de administración de fecha y hora en la sección **[!UICONTROL Time zone]** de la etapa de configuración de la base de datos.

Active la opción **[!UICONTROL UTC database (date fields with time zone)]** para almacenar todos los datos con fechas y horas en formato UTC (campos SQL y campos XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Si utiliza **Oracle**, los archivos de zona horaria (.dat) de las capas de cliente de Oracle deben ser compatibles con los archivos de zonas horarias instalados en el servidor.

Si la base de datos no es UTC, puede seleccionar uno de los husos horarios ofrecidos en la lista desplegable. También puede utilizar el huso horario del servidor o seleccionar la opción UTC (hora universal coordinada).

![](assets/install_wz_unselect_utc_option.png)

Cuando se selecciona la opción **[!UICONTROL UTC Database (date fields with time zone)]**, los campos SQL se almacenan en formato TIMESTAMP WITH TIMEZONE.

De lo contrario, se almacenan en el formato local y deberá seleccionar el huso horario que se aplicará a la base de datos.

### Migración {#migration}

Al migrar a una versión anterior (sin administración de huso horario), deberá definir el modo de almacenamiento de fecha en la base de datos.

Para garantizar la compatibilidad con las herramientas externas que tienen acceso a la base de datos de Adobe Campaign, los campos SQL de tipo **Date+time** permanecen almacenados en formato local de forma predeterminada.

Los campos XML que contienen fechas ahora se almacenan en UTC. Durante la carga, los campos que no están en formato UTC se convierten automáticamente mediante el huso horario de los servidores. Esto significa que todos los campos XML se convertirán progresivamente al formato UTC.

Para utilizar una instancia existente, agregue la opción **WdbcTimeZone** e introduzca la zona horaria de la instancia.

>[!IMPORTANT]
>
>Asegúrese de que el valor correcto esté configurado para la opción WdbcTimeZone: los cambios que se realicen posteriormente pueden dar lugar a incoherencias.

Ejemplo de valores posibles:

* Europa/París,
* Europa/Londres,
* América/Nueva York, etc.

   Estos valores se toman de la base de datos tz (Olson). Para obtener más información, consulte [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

