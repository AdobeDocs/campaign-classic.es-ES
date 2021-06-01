---
product: campaign
title: Uso del servidor SFTP
description: Obtenga más información sobre las prácticas recomendadas y la solución de problemas del servidor SFTP.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 99%

---

# Prácticas recomendadas y solución de problemas del servidor SFTP {#sftp-server-usage}

## Recomendaciones globales del servidor SFTP {#global-recommendations}

Al administrar archivos y datos para fines de ETL, estos archivos se almacenan en un servidor SFTP alojado proporcionado por Adobe. Asegúrese de seguir las recomendaciones siguientes cuando utilice servidores SFTP.

* Utilice autenticación basada en claves en lugar de autenticación mediante contraseña para evitar la caducidad de la contraseña (las contraseñas tienen un periodo de validez de 90 días). Además, la autenticación basada en claves permite generar claves múltiples, por ejemplo al administrar varias entidades. Por el contrario, la autenticación mediante contraseña requiere que comparta la contraseña con todas las entidades que esté administrando.

   El formato de clave admitido es SSH-2 RSA 2048. Las claves se pueden generar con herramientas como PyTTY (Windows) o ssh-keygen (Unix). Debe proporcionar la clave pública al equipo de soporte de Adobe a través del [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para que se cargue en el servidor de Campaign.

* Utilice lotes en sus cargas por SFTP y sus flujos de trabajo.

* Gestionar errores/excepciones.

* De forma predeterminada, todas las carpetas que cree se encuentran en modo de lectura y escritura solo para su identificador. Cuando cree carpetas a las que Campaign requiera tener acceso, asegúrese de configurarlas con derechos de lectura y escritura para todo el grupo. De lo contrario, es posible que, por motivos de seguridad, los flujos de trabajo no puedan crear o eliminar archivos que se ejecuten con un identificador diferente dentro del mismo grupo.

* Las IP públicas desde las que intente iniciar la conexión SFTP se deben incluir a la lista de permitidos de la instancia de Campaign. Añadir direcciones IP a la lista de permitidos se puede solicitar mediante el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Prácticas recomendadas de uso de la base de datos {#sftp-server-best-practices}

Los servidores SFTP están diseñados para ser espacios de almacenamiento temporal en los que se puede controlar la retención y eliminación de archivos.

Si no se utiliza o supervisa correctamente, estos espacios pueden ocupar rápidamente el espacio físico disponible en el servidor y provocar que los archivos se trunquen en cargas posteriores. Si el espacio se satura, puede activarse una depuración automática que borraría los archivos más antiguos del almacenamiento SFTP.

Para evitar estos problemas, Adobe recomienda seguir las prácticas recomendadas a continuación.

>[!NOTE]
>
>Si la instancia está alojada en AWS, puede monitorizar el almacenamiento del servidor SFTP con el [Panel de control](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html) de Campaign Classic. Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=es).
>
>Todos los usuarios administradores pueden acceder al Panel de control de Campaign. Los pasos para otorgar acceso de administrador a un usuario se detallan en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=es#discover-control-panel).
>
>Tenga en cuenta que la instancia debe actualizarse con la última compilación de [Gold Standard](../../rn/using/gs-overview.md) o [de GA (21.1)](../../rn/using/latest-release.md). Aprenda a comprobar su versión en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* Las capacidades del tamaño del servidor varían según la licencia. En cualquier caso, mantenga la menor cantidad de datos posible y mantenga los datos solamente durante el tiempo necesario (15 días es el límite máximo de tiempo).

* Utilice flujos de trabajo para eliminar correctamente los datos (administrar la retención de flujos de trabajo que consuman datos).

* Inicie sesión ocasionalmente en el SFTP para comprobar directamente lo que sucede allí.

* Recuerde que la gestión de discos SFTP es responsabilidad principalmente suya.

## Uso del servidor SFTP externo {#external-SFTP-server}

Si utiliza su propio servidor SFTP, en la medida de lo posible, asegúrese de seguir las recomendaciones mencionadas.

Además, al especificar en Campaign Classic una ruta a un servidor SFTP externo, la sintaxis de la ruta difiere según el sistema operativo del servidor SFTP:

* Si el servidor SFTP está en **Windows**, utilice siempre una ruta relativa.
* Si su servidor STP está en **Linux**, utilice siempre una ruta relativa al inicio (comenzando con &quot;~/&quot;) o una ruta absoluta (comenzando con &quot;/&quot;).

## Problemas de conexión con el servidor SFTP alojado en Adobe {#sftp-server-troubleshooting}

En la sección siguiente, se muestra la información que se debe verificar y proporcionar al equipo de soporte de Adobe a través del [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) cuando encuentre algún problema de conexión con servidores SFTP alojados por Adobe.

1. Compruebe que la instancia se esté ejecutando. Para ello, abra el navegador y luego realice una llamada **[!UICONTROL GET]** en el punto final de la instancia **[!UICONTROL /r/test]**:

   ```
   https://instanceUrl/r/test
   ```

   Si la instancia se está ejecutando, debe obtener este tipo de respuesta:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   En cualquier caso, indique la respuesta del comando en el ticket de asistencia.

1. Compruebe si el puerto saliente 22 se abre en el sitio desde el que intenta iniciar la conexión SFTP. Para ello, utilice el siguiente comando:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >La herramienta Netcat permite gestionar fácilmente las conexiones de red en varios sistemas operativos (consulte [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Si el puerto no está abierto, asegúrese de abrir las conexiones salientes de su lado y vuelva a intentarlo. Si sigue teniendo problemas de conexión, comparta la salida del comando con[el equipo de servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

1. Compruebe que la IP pública desde la que intenta iniciar la conexión SFTP sea la que indicó al servicio de asistencia de Adobe para que la incluyera en la lista de permitidos.
1. Si utiliza una autenticación basada en contraseña, es posible que la contraseña haya caducado (las contraseñas tienen un periodo de validez de 90 días). Por lo tanto, recomendamos utilizar una autenticación basada en claves (consulte [Prácticas recomendadas del servidor SFTP](#sftp-server-best-practices)).
1. Si utiliza una autenticación basada en claves, compruebe que la clave que está utilizando sea la misma que indicó al [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para la configuración de la instancia.
1. Si utiliza FileZilla o una herramienta de FTP equivalente, indique los detalles de conexión en el ticket de asistencia.

## Error &quot;No se pudo resolver el nombre de host&quot;

Esta sección proporciona información sobre las comprobaciones y acciones que se deben realizar al obtener el error &quot;No se pudo resolver el nombre de host&quot; después de conectarse al servidor FTP desde Campaign Classic.

El historial de flujo de trabajo muestra los siguientes registros:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Este error se produce al intentar conectar el servidor FTP desde un flujo de trabajo y descargar los archivos desde el servidor, mientras aún puede conectarse mediante FTP mediante FileZilla o WinSCP.

Este error indica que el nombre de dominio del servidor FTP no se pudo resolver correctamente. Para solucionar problemas, haga lo siguiente:

1. Solucionar problemas **de configuración del servidor DNS**:

   1. Compruebe si el nombre del servidor se ha agregado al servidor DNS local.
   1. Si es así, ejecute el siguiente comando en el servidor de Adobe Campaign para obtener la dirección IP:

      `nslookup <server domain name>`

      Esto confirma que el servidor FTP funciona y se puede acceder a él desde el servidor de aplicaciones de Adobe Campaign.

1. Solucionar problemas **de registros de sesión**:

   1. En el flujo de trabajo, haga clic con el botón doble en la actividad de [transferencia de archivos](../../workflow/using/file-transfer.md).
   1. Vaya a la pestaña **[!UICONTROL File Transfer]** y haga clic en **[!UICONTROL Advanced Parameters]**.
   1. Marque la opción **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Vaya al flujo de trabajo Audit y compruebe si los registros muestran el error ‘No se pudo resolver el nombre de host’.

1. Si el servidor SFTP está alojado por Adobe, compruebe si la IP se agrega a la lista de permitidos poniéndose en contacto con el Servicio de atención al cliente.

   De lo contrario, valide lo siguiente:

   * La contraseña no contiene &#39;@&#39;. Error de conexión si hay &#39;@&#39; en la contraseña.
   * No hay problemas con el firewall que puedan obstaculizar la comunicación entre el servidor de aplicaciones de Adobe Campaign y el servidor SFTP.
   * Ejecute los comandos tracert y telnet desde el servidor de campaña al sftp para ver si hay algún problema de conexión.
   * No hay problemas con el protocolo de comunicación.
   * El puerto está abierto.
