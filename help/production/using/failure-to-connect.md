---
solution: Campaign Classic
product: campaign
title: Error de conexión
description: Error de conexión
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 85fae38f864b031f069058dae79ce6753dc4bf03
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# Error de conexión{#failure-to-connect}

Las razones de un problema de conexión pueden ser múltiples y depender de varios contextos.

Puede probar las siguientes pruebas y, si el error de conexión persiste, póngase en contacto con el **soporte técnico de Adobe Campaign**.



<table> 
<thead> 
<tr> 
<th>Cheques<br /> </th> 
<th>Resolución<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>¿Tiene acceso a Internet desde su equipo?</td> 
<td>Compruebe que puede conectarse a sitios web en Internet (por ejemplo). Si no puede conectarse, el problema está en su equipo. Póngase en contacto con el administrador del sistema.</td>
</tr>
<tr> 
<td>¿Puede conectarse al servidor que aloja Adobe Campaign a través de otro servicio?</td> 
<td>Conectarse al servidor a través de SSH o por cualquier otro medio. Si esto no es posible, la compañía del host tiene un problema. Póngase en contacto con el administrador del sistema.</td>
</tr>
<tr> 
<td>¿Responde el servidor Web?</td> 
<td>Conéctese a la URL de acceso al servidor de Adobe Campaign mediante un explorador Web: <b>http(s):// &lt;urlserver&gt;</b>. Si no responde, el servidor web se detiene en el equipo. Póngase en contacto con el administrador del sistema de la compañía del host para reiniciar el servicio.</td>
</tr>
<tr> 
<td>¿Se ha integrado correctamente Adobe Campaign?</td> 
<td>Inicie sesión en el <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. El servidor debe devolver el siguiente tipo de mensaje: &lt;redir status='OK' date='AAAA/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
Si no obtiene este resultado, compruebe en la configuración del servidor Web que se tiene en cuenta la integración.</td>
</tr>
<tr> 
<td>Conéctese a la siguiente URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si obtiene un error de Java de Tomcat, compruebe si la integración de JAVA se realiza correctamente. Está integrado en el archivo [ruta de la aplicación]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conéctese a la siguiente URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si obtiene una página en blanco, compruebe si se ha iniciado el módulo Web de Adobe Campaign. El comando nlserver pdump debe devolver Application Server para Adobe Campaign Classic (7.X YY.R build XXX@SHA1) de DD/MM/AAAA. Si no es así, reinicie el módulo con el comando nlserver inicio web</td>
</tr>
<tr>
<td>Compruebe la configuración general de las zonas de seguridad.</td>
<td>Para obtener más información sobre la configuración de zonas de seguridad, consulte <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>esta sección.</a></td>
</tr>
<tr>
<td>El comando nlserver pdump devuelve <b>Sin tareas</b></td>
<td>Debe reiniciar toda la aplicación de Adobe Campaign. Para ello, utilice el siguiente comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
