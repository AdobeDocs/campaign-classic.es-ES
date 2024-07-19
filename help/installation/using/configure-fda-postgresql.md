---
product: campaign
title: Configuración del acceso a PostgreSQL
description: Obtenga información sobre cómo configurar el acceso a PostgreSQL
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 10%

---

# Configuración del acceso a PostgreSQL {#configure-fda-postgresql}



Utilice la opción Campaign **Acceso de datos federados** (FDA) para procesar la información almacenada en una base de datos PostgreSQL externa.

## Configuración de PostgreSQL {#postgresql-configuration}

Primero debe instalar Libpq. Libpq permite a los programas cliente enviar consultas al servidor back-end PostgreSQL y recibir los resultados de estas consultas.

Siga los pasos a continuación para configurar el acceso a [!DNL PostgreSQL]:

* Para CentOS, ejecute el siguiente comando `sudo apt-get -y install libpq-dev`.

* Para Linux, ejecute el siguiente comando `yum install postgresql-devel`.

* Para Windows, Libpq se implementa mediante `libpq.dll`, que se incluye en la instalación de Adobe Campaign.

En Adobe Campaign, puede configurar su cuenta externa [!DNL PostgreSQL]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#postgresql-external).

## Cuenta externa de PostgreSQL {#postgresql-external}

>[!NOTE]
>
> PostgreSQL está disponible en CentOS 7 y 6.

Debe crear una cuenta externa [!DNL PostgreSQL] para conectar la instancia de Campaign a la base de datos externa [!DNL PostgreSQL].

1. En la campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL PostgreSQL, Greenplum] de la lista desplegable **[!UICONTROL Type]**.

   ![](assets/postgresql_1.png)

1. Configure la autenticación de cuenta externa **[!UICONTROL PostgreSQL]**:

   * **[!UICONTROL Server]**: URL del servidor [!DNL PostgreSQL].

   * **[!UICONTROL Account]**: nombre del usuario.

   * **[!UICONTROL Password]**: contraseña de cuenta de usuario.

   * **[!UICONTROL Database]**: nombre de la base de datos (opcional).

   * **[!UICONTROL Working schema]**: nombre de su esquema de trabajo. [Más información](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: zona horaria establecida en [!DNL PostgreSQL]. [Más información](https://www.postgresql.org/docs/7.2/timezones.html)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Haga clic en **[!UICONTROL Save]** cuando finalice la configuración.

El conector admite las siguientes opciones:

| Opción | Descripción |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Espera máxima de conexión, en segundos. <br>Para obtener más información, consulte [Documentación de PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Número de segundos de inactividad tras los cuales TCP debe enviar un mensaje keepalive al servidor. <br>Para obtener más información, consulte [Documentación de PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Número de segundos después de los cuales se debe retransmitir el mensaje TCP keepalive no reconocido por el servidor.  <br>Para obtener más información, consulte [Documentación de PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Número de keepalives TCP que se pueden perder antes de que la conexión del cliente al servidor se considere muerta. <br>Para obtener más información, consulte [Documentación de PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
