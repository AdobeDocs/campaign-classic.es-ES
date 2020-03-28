---
title: Uso del servidor SFTP
seo-title: Uso del servidor SFTP
description: Uso del servidor SFTP
seo-description: null
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
translation-type: ht
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# Uso del servidor SFTP{#sftp-server-usage}

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
* Las IP públicas desde las que intente iniciar la conexión SFTP deben estar en la lista blanca de la instancia de Campaign. Puede solicitar que se añadan direcciones IP a la lista blanca a través de un [ticket de asistencia](https://support.neolane.net).

>[!CAUTION]
>
>Si utiliza su propio servidor SFTP, en la medida de lo posible, asegúrese de seguir las recomendaciones mencionadas.

## Solución de problemas del servidor SFTP {#sftp-server-troubleshooting}

En la sección siguiente se muestra la información que se debe verificar y proporcionar al servicio de asistencia de Adobe a través de un [vale de ayuda](https://support.neolane.net) cuando encuentre algún problema de conexión con servidores SFTP alojados por Adobe.

1. Compruebe que la instancia esté ejecutándose. Para ello, abra el navegador y luego realice una llamada **[!UICONTROL GET]** en el punto final de la instancia **[!UICONTROL /r/test]**:

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

1. Compruebe que la IP pública desde la que intenta iniciar la conexión SFTP sea la que indicó al servicio de asistencia de Adobe para que la incluyera en la lista blanca.
1. Si utiliza una autenticación basada en contraseña, es posible que la contraseña haya caducado (las contraseñas tienen un periodo de validez de 90 días). Por lo tanto, recomendamos utilizar una autenticación basada en claves (consulte [Prácticas recomendadas del servidor SFTP](#sftp-server-best-practices)).
1. Si utiliza una autenticación basada en claves, compruebe que la clave que está utilizando sea la misma que indicó al servicio de asistencia de Adobe para la configuración de la instancia.
1. Si utiliza FileZilla o una herramienta de FTP equivalente, indique los detalles de conexión en el ticket de asistencia.

