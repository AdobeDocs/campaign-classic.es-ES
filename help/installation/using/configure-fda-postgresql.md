---
product: campaign
title: Configuración del acceso a PostgreSQL
description: Obtenga información sobre cómo configurar el acceso a PostgreSQL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 11%

---

# Configuración del acceso a PostgreSQL {#configure-fda-postgresql}



Uso de Campaign **Acceso de datos federado** (FDA) para procesar información almacenada en una base de datos PostgreSQL externa.

## Configuración PostgreSQL {#postgresql-configuration}

Primero debe instalar Libpq. Libpq permite a los programas cliente enviar consultas al servidor back-end PostgreSQL y recibir los resultados de estas consultas.

Siga los pasos a continuación para configurar el acceso a [!DNL PostgreSQL]:

* Para CentOS, ejecute el siguiente comando `sudo apt-get -y install libpq-dev`.

* Para Linux, ejecute el siguiente comando `yum install postgresql-devel`.

* Para Windows, Libpq se implementa mediante `libpq.dll` que se incluye en la instalación de Adobe Campaign.

En Adobe Campaign, puede configurar la [!DNL PostgreSQL] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#postgresql-external).

## Cuenta externa PostgreSQL {#postgresql-external}

>[!NOTE]
>
> PostgreSQL está disponible en CentOS 7 y 6.

Debe crear un [!DNL PostgreSQL] cuenta externa para conectar la instancia de Campaign con el [!DNL PostgreSQL] base de datos externa.

1. Desde campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL PostgreSQL, Greenplum] de la variable **[!UICONTROL Type]** lista desplegable.

   ![](assets/postgresql_1.png)

1. Configure las variables **[!UICONTROL PostgreSQL]** autenticación de cuenta externa:

   * **[!UICONTROL Server]**: URL del [!DNL PostgreSQL] servidor.

   * **[!UICONTROL Account]**: Nombre del usuario.

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**: Nombre de la base de datos (opcional).

   * **[!UICONTROL Working schema]**: Nombre del esquema de trabajo. [Más información](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Zona horaria definida en [!DNL PostgreSQL]. [Más información](https://www.postgresql.org/docs/7.2/timezones.html)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Haga clic en **[!UICONTROL Save]** cuando la configuración haya finalizado.

El conector admite las siguientes opciones:

| Opción | Descripción |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Espera máxima de la conexión, en segundos. <br>Para obtener más información, consulte [Documentación PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Número de segundos de inactividad tras los cuales el TCP debe enviar un mensaje de mantenimiento activo al servidor. <br>Para obtener más información, consulte [Documentación PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Número de segundos después de los cuales se debe retransmitir el mensaje TCP keeplive no reconocido por el servidor.  <br>Para obtener más información, consulte [Documentación PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Número de mantenimiento TCP que se puede perder antes de que la conexión del cliente con el servidor se considere muerta. <br>Para obtener más información, consulte [Documentación PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
