---
product: campaign
title: Administración de husos horarios
description: Administración de husos horarios
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# Administración de husos horarios{#time-zone-management}

## Principio de funcionamiento {#operating-principle}

Adobe Campaign permite expresar fechas en función de su huso horario: esto permite a los usuarios internacionales trabajar en todo el mundo en diferentes zonas horarias. Cada país que utiliza la misma instancia puede administrar la ejecución de campañas, el seguimiento, el archivado, etc. según la hora local.

Para permitir el uso de la plataforma Adobe Campaign a escala internacional, todas las fechas utilizadas por los sistemas deben poder vincularse a una zona horaria. Por lo tanto, una fecha cuya zona horaria se conozca se puede importar en cualquier otra zona horaria o independientemente de la zona horaria.

Adobe Campaign permite almacenar fechas y horas en formato UTC (hora universal coordinada). Cuando se exponen los datos, estos se convierten a la fecha y hora locales del operador. La conversión se realiza automáticamente cuando la base de datos está configurada en UTC (consulte [Configuration](#configuration)). Si la base de datos no está configurada en UTC, la información sobre la zona horaria de las fechas en la plataforma se almacena en una opción.

Las principales funcionalidades de la plataforma con respecto a la administración de huso horario son: importar/exportar datos y administración de operadores y flujos de trabajo. El **concepto de herencia** está disponible para importaciones/exportaciones o flujos de trabajo. De forma predeterminada, están configuradas para la zona horaria del servidor de la base de datos, aunque puede redefinir nuevas zonas horarias para un flujo de trabajo e incluso para una sola actividad.

**** Los operadores pueden modificar las zonas horarias durante la  **configuración de la** entrega y pueden especificar el huso horario en el que se ejecutará la entrega.

>[!IMPORTANT]
>
>Si la base de datos no administra varias zonas horarias, para todas las manipulaciones del filtrado de datos, las consultas SQL deben ejecutarse en la zona horaria del servidor de la base de datos.

Cada operador de Adobe Campaign está vinculado a una zona horaria: esta información está configurada en su perfil. Para obtener más información, consulte [este documento](../../platform/using/access-management.md).

Cuando la plataforma Adobe Campaign no requiere administración de huso horario, puede mantener un modo de almacenamiento en formato local con un huso horario vinculado específico.

## Recomendaciones {#recommendations}

Las zonas horarias combinan varias realidades: la expresión puede describir un lapso de tiempo constante con la fecha UTC, o las horas de una región que pueden cambiar dos veces al año (horario de verano).

Por ejemplo, en postgreSQL, el comando **SET TIME ZONE &#39;Europe/Paris&#39;;** tendrá en cuenta los tiempos de verano e invierno: la fecha se expresará en UTC+1 o UTC+2 según la hora del año.

Sin embargo, si utiliza el comando **SET TIME ZONE 0200;**, el retraso siempre será UTC+2.

## Configuración {#configuration}

El modo de almacenamiento de fechas y horas está seleccionado durante la creación de la base de datos (consulte [Creación de una nueva instancia](#creating-a-new-instance)). En caso de una migración, las horas vinculadas a las fechas se convierten en fechas y horas locales (consulte [Migración](#migration)).

Desde un punto de vista técnico, existen dos maneras de almacenar la información de tipo **Date+time** en la base de datos:

1. MARCA DE TIEMPO CON formato DE ZONA HORARIA: el motor de base de datos almacena fechas en UTC. Cada sesión abierta tendrá un huso horario y las fechas se convertirán según él.
1. Formato local + zona horaria local: todas las fechas se almacenan en el formato local (sin administración de retraso) y se les asigna una sola zona horaria. La zona horaria se almacena en la opción **WdbcTimeZone** de la instancia de Adobe Campaign y se puede cambiar mediante el menú **[!UICONTROL Administration > Platform > Options]** del árbol.

>[!IMPORTANT]
>
>Tenga en cuenta que esta modificación puede provocar problemas de coherencia y sincronización de los datos.

### Creación de una nueva instancia {#creating-a-new-instance}

Para que varios usuarios internacionales trabajen en la misma instancia, debe configurar las zonas horarias al crear la instancia para administrar los desfases horarios entre países. Durante la creación de instancias, seleccione el modo de administración de fecha y hora en la sección **[!UICONTROL Time zone]** de la fase de configuración de la base de datos.

Marque la opción **[!UICONTROL UTC database (date fields with time zone)]** para almacenar todos los datos con fechas y horas en formato UTC (campos SQL y campos XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Si utiliza **Oracle**, los archivos de zona horaria (.dat) de las capas de cliente de Oracle deben ser compatibles con los archivos de zonas horarias instalados en el servidor.

Si la base de datos no es UTC, puede seleccionar una de las zonas horarias ofrecidas en la lista desplegable. También puede utilizar la zona horaria del servidor o seleccionar la opción UTC (hora universal coordinada).

![](assets/install_wz_unselect_utc_option.png)

Cuando se selecciona la opción **[!UICONTROL UTC Database (date fields with time zone)]**, los campos SQL se almacenan en formato TIMESTAMP WITH TIMEZONE .

De lo contrario, se almacenan en el formato local y debe seleccionar la zona horaria que desea aplicar a la base de datos.

### Migración {#migration}

Al migrar a una versión anterior (sin administración de huso horario), deberá definir el modo de almacenamiento de fechas en la base de datos.

Para garantizar la compatibilidad con herramientas externas que tienen acceso a la base de datos de Adobe Campaign, los campos SQL de tipo **Date+time** se almacenan en formato local de forma predeterminada.

Los campos XML que contienen fechas ahora se almacenan en UTC. Durante la carga, los campos que no están en formato UTC se convierten automáticamente mediante la zona horaria de los servidores. Esto significa que todos los campos XML se convertirán progresivamente al formato UTC.

Para utilizar una instancia existente, añada la opción **WdbcTimeZone** e introduzca la zona horaria de la instancia.

>[!IMPORTANT]
>
>Asegúrese de que el valor correcto esté configurado para la opción WdbcTimeZone : los cambios realizados posteriormente pueden dar lugar a incoherencias.

Ejemplo de valores posibles:

* Europa/París,
* Europa/Londres,
* América/Nueva York, etc.

   Estos valores se toman de la base de datos tz (Olson). Para obtener más información, consulte [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
