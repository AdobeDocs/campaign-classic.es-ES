---
product: campaign
title: Notas de la versión de Campaign 18.6
description: Notas de la versión 18.6 de Campaign
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Información general
role: Business Practitioner
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 97%

---

# Versión 18.6{#release-18-6}

## Versión 18.6.2: compilación 8949{#release-18-6-3-build-8949}

22 de agosto de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. [actualice a la última versión](../../production/using/build-upgrade.md) o póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidad<br /> </th> 
   <th> Descripción<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Banda de consultas<br /> </td> 
   <td> <p>Cuando varios usuarios de Campaign se conectan con la misma cuenta externa de Teradata de FDA, ahora puede pasar una banda de consulta (pares clave/valor) específica a cada usuario. Cada vez que un usuario de Campaign realiza una consulta en la base de datos de Teradata, Adobe Campaign ahora puede enviar metadatos asociados al usuario. Estos datos, que se componen de una lista de claves y valores, pueden ser utilizados por administradores de Teradata para fines de auditoría o para administrar derechos de acceso, por ejemplo.</p><p>Para obtener más información, consulte la <a href="../../installation/using/external-accounts.md">documentación detallada</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Mejoras**

* Se han mejorado los registros de archivos de correo electrónico, lo que facilita la comprobación de los mensajes de correo electrónico que se han entregado o no se han enviado correctamente a través del archivo BCC. (NEO-10675)
* Se ha corregido un problema que provocaba la visualización de las direcciones IP del equilibrador de carga en lugar de las direcciones IP del cliente en los registros de seguimiento. (NEO-11295)
* Se ha corregido un problema aleatorio que ocasionaba que las propiedades de una entrega se sobrescriban erróneamente. (NEO-11015)
* Se ha corregido un error de sintaxis al ordenar los resultados de las actividades de enriquecimiento. (NEO-11394)
* Se ha corregido un problema que se producía al utilizar campos calculados en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-11382)
* Se ha actualizado Tomcat para evitar la explotación de vulnerabilidades. (NEO-11503)
* Se ha corregido un error con la codificación LATIN1 al utilizar una conexión de FDA con una base de datos PostgreSQL. (NEO-11299)
* Se ha corregido un problema que se producía al utilizar la opción de entrega **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047)
* Se ha corregido un problema posterior a la actualización que impedía la entrega de SMS al utilizar un conector extendido.
* Se mejoró la importación/exportación de paquetes (se han añadido registros y regiones en la interfaz).
* Se ha corregido un problema que mostraba errores no viables en el registro posterior de actualización cuando una actividad de flujo de trabajo **[!UICONTROL Survey answers]** no estaba completamente configurada.

**Evoluciones técnicas**

Banda de consultas

Se utiliza una clave específica (PROXYUSER o PROXYROLE) para asociar un usuario o función de Teradata a un usuario de Campaign. Se ha añadido un nuevo permiso para utilizar este usuario/función de proxy. Debe añadir el derecho al acceso de GRANT CONNECT THROUGH a la cuenta de la base de datos (la definida en la cuenta externa de Teradata).

Se ha añadido una nueva pestaña en las cuentas externas de Teradata. La pestaña **[!UICONTROL Query banding]** incluye las siguientes opciones:

* **[!UICONTROL Active]**: Marque esta casilla para activar la función.
* **[!UICONTROL Default]**: introduzca una banda de consulta predeterminada que se debe utilizar si un usuario no tiene una banda de consulta asociada. Si no se ha definido una banda de consulta predeterminada, los usuarios que no tengan bandas de consulta asociadas no podrán utilizar Teradata.
* **[!UICONTROL Users]**: para cada usuario, especifique una banda de consultas. Puede añadir todos los pares de clave/valor que necesite. Por ejemplo: ‘priority=1;carga de trabajo=high;’

Para obtener más información sobre la banda de consultas, vea esta sección.

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Versión 18.6: compilación 8947{#release-18-6-build-8947}

25 de junio de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. [Actualice a la última versión](../../production/using/build-upgrade.md) o contacte con el [soporte técnico](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidad<br /> </th> 
   <th> Descripción<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Mejoras de seguridad<br /> </td> 
   <td> Se ha añadido una serie de mejoras de seguridad a Campaign Classic. A continuación se enumeran las mejoras y correcciones.<br /> </td> 
  </tr> 
  <tr> 
   <td> Compatibilidad con Windows Server 2016<br /> </td> 
   <td> Adobe Campaign ahora es compatible con Windows Server 2016. Consulte la <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matriz de compatibilidades de Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

decryptString

La función **decryptString** ya no se utiliza. Consulte el artículo [Funciones obsoletas y eliminadas](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html).

Para nuevos clientes, esta función se utiliza ahora solamente para descifrar el ID cifrado del destinatario en las páginas de aterrizaje. Para descifrar contraseñas almacenadas en una cuenta externa, utilice la nueva función **decryptPassword**.

Para los clientes existentes, el comportamiento de esta función no cambia pero recomendamos que utilice **decryptPassword** en lugar de **decryptString**. La opción de compatibilidad con **XtkSecurity_Unsafe_DecryptString** se añade en la mejora y se activa de forma predeterminada, lo que le permite continuar usando la función. Si desea desactivar **decryptString**, desactive la opción.

decryptPassword

Se ha añadido la función **decryptPassword.** Permite descifrar una contraseña almacenada en una cuenta externa. Consulte la documentación de [JSAPI](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html) para obtener más información.

API de archivo

Para las nuevas instalaciones, el acceso a carpetas mediante las API de archivo está limitado a las carpetas **var**, **sftp** y temporales de Adobe Campaign.

Para los clientes existentes, las API de archivo ya no pueden acceder a la carpeta **conf** de Adobe Campaign. La opción de compatibilidad con **XtkSecurity_Disable_JSFileSandboxing** se añade en la actualización y se activa de forma predeterminada, lo que le permite mantener el acceso a las otras carpetas. Si desea limitar el acceso a las carpetas temporales **var**, **sftp** y de Adobe Campaign, desactive la opción.

**Parche**

* Se ha corregido un problema que podría afectar el rendimiento del mensaje transaccional SMS. (NEO-9812)
