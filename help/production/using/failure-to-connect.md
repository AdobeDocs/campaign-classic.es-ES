---
solution: Campaign Classic
product: campaign
title: Error de conexión
description: Error de conexión
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 2cc4ab52f3cbdd00831d0b5104690b7adf6091ce
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# Error de conexión{#failure-to-connect}

Las razones de un problema de conexión pueden ser múltiples y depender de varios contextos.

Puede probar las siguientes pruebas y, si el error de conexión persiste, póngase en contacto con el servicio de soporte técnico de **Adobe Campaign**.



<table> 
 <thead> 
  <tr> 
   <th>Comprobaciones<br /> </th> 
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
   <td>Inicie sesión en el <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. El servidor debe devolver el siguiente tipo de mensaje:

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;AAAA/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
Si no obtiene este resultado, compruebe en la configuración del servidor Web que se tiene en cuenta la integración.</td>
</tr>
  <tr> 
   <td>¿Se ha iniciado el módulo Web de Adobe Campaign?</td> 
   <td>Conéctese a la siguiente URL: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Si obtiene un error de Java de Tomcat:

¿Se realiza correctamente la integración de JAVA? Adobe Campaign requiere un JDK SUN.

Está integrado en la [ruta de archivos de la aplicación]/nl6/customer.sh

* Si obtiene una página en blanco:

¿Se ha iniciado el módulo Web de Adobe Campaign? Debe obtener:

<pre>
nlserver pdumpHH:MM:SS &gt; Servidor de aplicaciones para Adobe Campaign Classic (7.X YY.R build XXX@SHA1) de DD/MM/AAAA[...]web@default (27515) - 55.2 Mb[...]
</pre>

* Si no es así, reinícielo con el siguiente comando:

<pre>        
nlserver inicio web
</pre>
</td>
</tr>
  <tr>
  	<td>Compruebe la configuración general de las zonas de seguridad.</td>
  	<td>Para obtener más información sobre la configuración de zonas de seguridad, consulte [esta sección](../../installation/using/configuring-campaign-server.md#define-security-zones)</td>
  </tr>
 </tbody> 
</table>
