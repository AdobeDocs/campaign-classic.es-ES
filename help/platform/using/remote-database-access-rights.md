---
title: Acceso a una base de datos externa
seo-title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Derechos de acceso a bases de datos remotas {#remote-database-access-rights}

En primer lugar, para que el usuario pueda llevar a cabo operaciones en una base de datos externa a través de FDA, el último debe tener un derecho específico en Adobe Campaign.

1. Seleccione el **[!UICONTROL Administration > Access Management > Named Rights]** nodo en el explorador de Adobe Campaign.
1. Cree un nuevo derecho especificando la etiqueta elegida.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

   * **user** corresponde al nombre del usuario en la base de datos externa.
   * **base** corresponde al nombre de la base de datos externa.
   * **server** corresponde al nombre del servidor de base de datos externo.

      >[!NOTE]
      >
      >La parte **:base** es opcional en Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

A continuación, para procesar los datos contenidos en una base de datos externa, el usuario de Adobe Campaign debe tener al menos derechos de escritura en la base de datos para poder crear tablas de trabajo. Adobe Campaign los elimina automáticamente.

En general, son necesarios los siguientes derechos:

* **CONEXIÓN**: conexión con la base de datos remota,
* **LECTURA DE Datos**: acceso de sólo lectura a tablas que contienen datos de clientes,
* **LECTURA DE MetaDatos**: acceso a los catálogos de datos del servidor para obtener la estructura de la tabla,
* **CARGA**: carga masiva en tablas de trabajo (requerido cuando se trabaja en colecciones y uniones),
* **CREACIÓN/ELIMINACIÓN** de **TABLA/ÍNDICE/PROCEDIMIENTO/FUNCIÓN**,
* **EXPLICACIÓN** (recomendado): para controlar el rendimiento en caso de problemas,
* **ESCRITURA DE Datos** (según el escenario de integración).

>[!NOTE]
>
>El administrador de la base de datos debe hacer coincidir estos derechos con los derechos específicos de cada motor de base de datos. Para obtener más información, consulte [Derechos específicos de RDBMS](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).