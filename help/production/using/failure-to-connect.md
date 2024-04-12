---
product: campaign
title: Error de conexión
description: Error de conexión
feature: Monitoring
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 4%

---

# Error de conexión{#failure-to-connect}



Las razones de un problema de conexión pueden ser múltiples y depender de varios contextos.

Puede probar las siguientes pruebas y, si el error de conexión persiste, póngase en contacto con el [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Cheques<br /> </th> 
<th>Resolución<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>¿Tiene acceso a Internet desde el equipo?</td> 
<td>Compruebe que puede conectarse a sitios web en Internet (por ejemplo). Si no puede conectarse, el problema está en su equipo. Póngase en contacto con el administrador del sistema.</td>
</tr>
<tr> 
<td>¿Puede conectarse al servidor que aloja Adobe Campaign a través de otro servicio?</td> 
<td>Conéctese al servidor a través de SSH o por cualquier otro medio. Si no es posible, la empresa de acogida tiene un problema. Póngase en contacto con el administrador del sistema.</td>
</tr>
<tr> 
<td>¿Responde el servidor web?</td> 
<td>Conéctese a la URL de acceso del servidor de Adobe Campaign mediante un explorador web: <b>http(s):// &lt;urlserver&gt;</b>. Si no responde, el servidor web se detiene en el equipo. Póngase en contacto con el administrador del sistema de la compañía host para reiniciar el servicio.</td>
</tr>
<tr> 
<td>¿Se ha integrado correctamente Adobe Campaign?</td> 
<td>Inicie sesión en: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. El servidor debe devolver el siguiente tipo de mensaje: &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
Si no obtiene este resultado, compruebe en la configuración del servidor web que se tiene en cuenta la integración.:MM:</td>
</tr>
<tr> 
<td>Conéctese a la siguiente dirección URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Si se produce un error de Java de Tomcat, compruebe si la integración de JAVA se realiza correctamente. Está integrado en el archivo [ruta de aplicación]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Conéctese a la siguiente dirección URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Si obtiene una página en blanco, compruebe si el módulo web de Adobe Campaign está iniciado. El comando nlserver pdump debe devolver Application Server para Adobe Campaign Classic (7.X YY.R build XXX@SHA1) de DD/MM/YYYY. Si no, reinicie el módulo con el comando nlserver start web</td>
</tr>
<tr>
<td>Compruebe la configuración general de las zonas de seguridad.</td>
<td>Para obtener más información sobre la configuración de las zonas de seguridad, consulte <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>esta sección.</a></td>
</tr>
<tr>
<td>El comando nlserver pdump devuelve <b>Sin tareas</b></td>
<td>Debe reiniciar toda la aplicación de Adobe Campaign. Para ello, utilice el siguiente comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
