---
title: Uso del servidor SFTP
description: Obtenga más información sobre las prácticas recomendadas y la solución de problemas del servidor SFTP.
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8198c4aa6eccc0cbb5de4712ebdd8000783b615c
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 64%

---


# Prácticas recomendadas y solución de problemas del servidor SFTP {#sftp-server-usage}

## Prácticas recomendadas del servidor SFTP {#sftp-server-best-practices}

Al administrar archivos y datos para fines de ETL, estos archivos se almacenan en un servidor SFTP alojado proporcionado por Adobe. Este SFTP está diseñado para ser un espacio de almacenamiento temporal en el que se puede controlar la retención y eliminación de archivos.

Si no se utiliza o supervisa correctamente, este espacio puede ocupar rápidamente el espacio físico disponible en el servidor y provocar que los archivos se trunquen en cargas posteriores. Si el espacio se satura, puede activarse una depuración automática que borraría los archivos más antiguos del almacenamiento SFTP.

Para evitar estos problemas, Adobe recomienda seguir las prácticas recomendadas a continuación.

>[!NOTE]
>
>Si la instancia está alojada en AWS, puede supervisar el almacenamiento del servidor SFTP con el [Panel de control](https://docs.adobe.com/content/help/es-ES/control-panel/using/sftp-management/sftp-storage-management.html) de Campaign Classic.
>
>Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta sección](https://docs.adobe.com/content/help/es-ES/control-panel/using/faq.html#ims-org-id) .

* Las capacidades del tamaño del servidor varían según la licencia. En cualquier caso, mantenga la menor cantidad de datos posible y mantenga los datos solamente durante el tiempo necesario (15 días es el límite máximo de tiempo).
* Utilice autenticación basada en claves en lugar de autenticación mediante contraseña para evitar la caducidad de la contraseña (las contraseñas tienen un periodo de validez de 90 días). Además, la autenticación basada en claves permite generar claves múltiples, por ejemplo al administrar varias entidades. Por el contrario, la autenticación mediante contraseña requiere que comparta la contraseña con todas las entidades que esté administrando.

   El formato de clave admitido es SSH-2 RSA 2048. Las claves se pueden generar con herramientas como PyTTY (Windows) o ssh-keygen (Unix). Debe proporcionar la clave pública al equipo de asistencia de Adobe a través de un [vale de asistencia](https://support.neolane.net) para que se cargue en el servidor de Campaign.

* Utilice flujos de trabajo para eliminar correctamente los datos (administrar la retención de flujos de trabajo que consuman datos).
* Utilice lotes en sus cargas por SFTP y sus flujos de trabajo.
* Gestionar errores/excepciones.
* Inicie sesión ocasionalmente en el SFTP para comprobar directamente lo que sucede allí.
* Recuerde que la gestión de discos SFTP es responsabilidad principalmente suya.
* De forma predeterminada, todas las carpetas que cree se encuentran en modo de lectura y escritura solo para su identificador. Cuando cree carpetas a las que Campaign requiera tener acceso, asegúrese de configurarlas con derechos de lectura y escritura para todo el grupo. De lo contrario, es posible que, por motivos de seguridad, los flujos de trabajo no puedan crear o eliminar archivos que se ejecuten con un identificador diferente dentro del mismo grupo.
* Las direcciones IP públicas desde las que intenta iniciar la conexión SFTP deben agregarse a la lista de permitidos en la instancia de Campaña. Añadir direcciones IP a la lista de permitidos se puede solicitar mediante un ticket [de asistencia](https://support.neolane.net).

>[!CAUTION]
>
>Si utiliza su propio servidor SFTP, en la medida de lo posible, asegúrese de seguir las recomendaciones mencionadas.

## Problemas de conexión con el servidor SFTP alojado en Adobe {#sftp-server-troubleshooting}

En la sección siguiente se muestra la información que se debe verificar y proporcionar al servicio de asistencia de Adobe a través de un [vale de ayuda](https://support.neolane.net) cuando encuentre algún problema de conexión con servidores SFTP alojados por Adobe.

1. Compruebe que la instancia esté ejecutándose. To do this, open your browser, then make a **[!UICONTROL GET]** call on the instance **[!UICONTROL /r/test]** endpoint:

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

   Si el puerto no está abierto, asegúrese de abrir las conexiones salientes de su lado y vuelva a intentarlo. Si sigue teniendo problemas de conexión, comparta la salida del comando con el equipo de asistencia de Adobe.

1. Compruebe que la IP pública desde la que intenta iniciar la conexión SFTP es la que ha proporcionado a la asistencia técnica de Adobe para la lista de permitidos.
1. Si utiliza una autenticación basada en contraseña, es posible que la contraseña haya caducado (las contraseñas tienen un periodo de validez de 90 días). Por lo tanto, recomendamos utilizar una autenticación basada en claves (consulte [Prácticas recomendadas del servidor SFTP](#sftp-server-best-practices)).
1. Si utiliza una autenticación basada en claves, compruebe que la clave que está utilizando sea la misma que indicó al servicio de asistencia de Adobe para la configuración de la instancia.
1. Si utiliza FileZilla o una herramienta de FTP equivalente, indique los detalles de conexión en el ticket de asistencia.

## Error &quot;No se pudo resolver el nombre de host&quot;

Esta sección proporciona información sobre las comprobaciones y acciones que se deben realizar al obtener el error &quot;No se pudo resolver el nombre de host&quot; después de conectarse al servidor FTP desde el Campaign Classic.

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

1. Solucionar problemas de configuración **del servidor** DNS:

   1. Compruebe si el nombre del servidor se ha agregado al servidor DNS local.
   1. Si es así, ejecute el siguiente comando en el servidor de Adobe Campaign para obtener la dirección IP:

      `nslookup <server domain name>`

      Esto confirma que el servidor FTP funciona y se puede acceder a él desde el servidor de aplicaciones de Adobe Campaign.

1. Solucionar problemas de registros **de sesión**:

   1. En el flujo de trabajo, haga clic con el botón doble en la actividad de transferencia [de](../../workflow/using/file-transfer.md) archivos.
   1. Vaya a la **[!UICONTROL File Transfer]** ficha y haga clic en **[!UICONTROL Advanced Parameters]**.
   1. Marque la opción **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Vaya a la auditoría del flujo de trabajo y compruebe si los registros muestran el error &#39;No se pudo resolver el nombre de host&#39;.

1. Si el servidor SFTP está alojado por Adobe, compruebe si la IP se agrega a la lista de permitidos poniéndose en contacto con el Servicio de atención al cliente.

   De lo contrario, validar:

   * La contraseña no contiene &#39;@&#39;. Error de conexión si hay &#39;@&#39; en la contraseña.
   * No hay problemas con el cortafuegos que puedan obstaculizar la comunicación entre el servidor de aplicaciones de Adobe Campaign y el servidor SFTP.
   * Ejecute comandos tracert y telnet desde el servidor de campaña al sftp para ver si hay algún problema de conexión.
   * No hay problemas con el protocolo de comunicación.
   * El puerto está abierto.
