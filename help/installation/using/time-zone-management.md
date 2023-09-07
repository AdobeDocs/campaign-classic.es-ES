---
product: campaign
title: Administración de husos horarios
description: Administración de husos horarios
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 3%

---

# Administración de husos horarios{#time-zone-management}



## Principio de funcionamiento {#operating-principle}

Adobe Campaign permite expresar las fechas en función de su huso horario, lo que permite a los usuarios internacionales trabajar en todo el mundo en diferentes husos horarios. Cada país que utilice la misma instancia puede administrar la ejecución de campañas, el seguimiento, el archivado, etc. según la hora local.

Para permitir el uso de la plataforma Adobe Campaign a escala internacional, todas las fechas utilizadas por los sistemas deben poder vincularse a una zona horaria. Por lo tanto, una fecha cuya zona horaria se conozca puede importarse en cualquier otra zona horaria o independientemente de esta.

Adobe Campaign permite almacenar fechas y horas en formato UTC (hora universal coordinada). Cuando se exponen datos, se convierten a la fecha y hora locales del operador. La conversión se realiza automáticamente cuando la base de datos está configurada en UTC (consulte [Configuración](#configuration)). Si la base de datos no está configurada en UTC, la información sobre la zona horaria de las fechas en la plataforma se almacena en una opción.

Las principales funcionalidades de la plataforma en relación con la administración de husos horarios son: importación/exportación de datos y administración de operadores y flujos de trabajo. El **concepto de herencia** está disponible para importaciones/exportaciones o flujos de trabajo. De forma predeterminada, se configuran para la zona horaria del servidor de la base de datos; sin embargo, se pueden redefinir nuevas zonas horarias para un flujo de trabajo e incluso para una sola actividad.

**Operadores** puede modificar las zonas horarias durante **configuración de envío** y puede especificar el huso horario concreto en el que se ejecutará la entrega.

>[!IMPORTANT]
>
>Si la base de datos no administra varias zonas horarias, para todas las manipulaciones de filtrado de datos, las consultas SQL deben ejecutarse en la zona horaria del servidor de la base de datos.

Cada operador de Adobe Campaign está vinculado a una zona horaria: esta información se configura en su perfil. Para obtener más información, consulte [este documento](../../platform/using/access-management.md).

Si la plataforma Adobe Campaign no requiere administración de huso horario, puede mantener un modo de almacenamiento en formato local con una zona horaria vinculada específica.

## Recomendaciones {#recommendations}

Los husos horarios combinan varias realidades: la expresión puede describir un intervalo de tiempo constante con la fecha UTC o las horas de una región que pueden cambiar dos veces al año (hora de verano).

Por ejemplo, en postgreSQL, la variable **ESTABLECER ZONA HORARIA &#39;Europa/París&#39;;** El comando tendrá en cuenta los horarios de verano e invierno: la fecha se expresa en UTC+1 o UTC+2 según la época del año.

Sin embargo, si usa la variable **ESTABLECER ZONA HORARIA 0200;** , el retardo siempre será UTC+2.

## Configuración {#configuration}

El modo de almacenamiento de fechas y horas se selecciona durante la creación de la base de datos (consulte [Creación de una nueva instancia](#creating-a-new-instance)). En caso de migración, las horas vinculadas a las fechas se convierten en fechas y horas locales (consulte ). [Migración](#migration)).

Desde un punto de vista técnico, hay dos formas de almacenar **Fecha+hora** escriba información en la base de datos:

1. TIMESTAMP WITH TIMEZONE format: el motor de base de datos almacena las fechas en UTC. Cada sesión abierta tendrá una zona horaria y las fechas se convertirán según ella.
1. Formato local + zona horaria local: todas las fechas se almacenan en formato local (sin administración de intervalo de tiempo) y se les asigna una sola zona horaria. La zona horaria se almacena en **WdbcTimeZone** de la instancia de Adobe Campaign y se puede cambiar mediante la opción **[!UICONTROL Administration > Platform > Options]** menú del árbol.

>[!IMPORTANT]
>
>Tenga en cuenta que esta modificación puede provocar problemas de sincronización y coherencia de datos.

### Creación de una nueva instancia {#creating-a-new-instance}

Para que varios usuarios internacionales trabajen en la misma instancia, debe configurar las zonas horarias al crear la instancia para administrar los desfases temporales entre países. Durante la creación de la instancia, seleccione el modo de administración de fecha y hora en la **[!UICONTROL Time zone]** de la fase de configuración de la base de datos.

Compruebe la **[!UICONTROL UTC database (date fields with time zone)]** opción para almacenar todos los datos con fechas y horas en formato UTC (campos SQL y campos XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Si está utilizando **Oracle**, los archivos de huso horario (.dat) de las capas de cliente de Oracle deben ser compatibles con los archivos de huso horario instalados en el servidor.

Si la base de datos no es UTC, puede seleccionar una de las zonas horarias ofrecidas en la lista desplegable. También puede utilizar la zona horaria del servidor o seleccionar la opción UTC (Hora Universal Coordinada).

![](assets/install_wz_unselect_utc_option.png)

Si la variable **[!UICONTROL UTC Database (date fields with time zone)]** Si se selecciona la opción, los campos SQL se almacenan en formato TIMESTAMP WITH TIMEZONE.

De lo contrario, se almacenan en el formato local y deberá seleccionar la zona horaria que desee aplicar a la base de datos.

### Migración {#migration}

Al migrar a una versión anterior (sin administración de zona horaria), deberá definir el modo de almacenamiento de fecha en la base de datos.

Para garantizar la compatibilidad con herramientas externas que acceden a la base de datos de Adobe Campaign, la variable **Fecha+hora** Los campos SQL de tipo permanecen almacenados en formato local de forma predeterminada.

Los campos XML que contienen fechas ahora se almacenan en UTC. Durante la carga, los campos que no están en formato UTC se convierten automáticamente utilizando la zona horaria de los servidores. Esto significa que todos los campos XML se convertirán progresivamente al formato UTC.

Para utilizar una instancia existente, añada la variable **WdbcTimeZone** e introduzca la zona horaria de la instancia.

>[!IMPORTANT]
>
>Asegúrese de que esté configurado el valor correcto para la opción WdbcTimeZone: los cambios realizados más adelante pueden provocar incoherencias.

Ejemplo de valores posibles:

* Europa/París,
* Europa/Londres,
* América/Nueva_York, etc.

  Estos valores se toman de la base de datos tz (Olson). Para obtener más información, consulte [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## base de datos de oracle y zona horaria del servidor

Para la base de datos principal, Campaign utiliza la zona horaria del servidor para establecer la zona horaria de sesión en la conexión de base de datos. La opción &quot;WdbcTimeZone&quot; no tiene ningún impacto. Por lo tanto, la zona horaria del servidor debe coincidir con la de la base de datos principal utilizada por Campaign. Si no puede cambiar la zona horaria del servidor, la utilizada por Campaign puede anularse configurando la variable de entorno TZ en customer.sh.