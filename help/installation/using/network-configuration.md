---
solution: Campaign Classic
product: campaign
title: Configuración de red
description: Conozca las directrices de comunicación del sistema
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---


# Configuración de red{#network-configuration}

## Comunicación entre procesos {#communication-between-processes}

Ciertos procesos de la aplicación necesitan comunicarse con otros o acceder a la LAN e Internet. Esto significa que algunos puertos TCP deben estar abiertos para estos procesos.

Utilice el puerto integrado Apache Tomcat como prioridad (8080 de forma predeterminada) para las comunicaciones internas entre los distintos servidores de aplicaciones de una plataforma Adobe Campaign.

### Servidor de envío {#delivery-server}

Para el servidor envío (**nlserver mta**), deben abrirse los puertos siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> Tráfico SMTP para retransmisión por correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (dominio)<br /> </td> 
   <td> Servidores DNS<br /> </td> 
   <td> CONSULTAS DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (puerto predeterminado)<br /> </td> 
   <td> Puerta de enlace SMS<br /> </td> 
   <td> Se utiliza para enviar tráfico SMS al enrutador SMS NetSize [opción].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Servidor de estadísticas<br /> </td> 
   <td> Acceso al servidor de estadísticas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Correo entrante {#inbound-mail}

Para el proceso de recuperación de correo entrante (**nlserver enMail**), deben abrirse los puertos siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Servidor de correo interno<br /> </td> 
   <td> Tráfico POP3 para recoger mensajes de devolución.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Servidor de correo interno<br /> </td> 
   <td> Tráfico SMTP para enviar los mensajes de devolución restantes que las reglas predefinidas no procesan automáticamente.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicaciones {#application-server}

Para el servidor de aplicaciones (**nlserver web**), deben abrirse los puertos siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> Tráfico HTTP o HTTPS (incluida la oferta de entregabilidad).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Cuando varios servidores de aplicaciones de una plataforma de Adobe Campaign necesitan comunicarse entre sí, recomendamos el uso del puerto del servidor Apache Tomcat (de forma predeterminada: 8080) en lugar del puerto HTTP del servidor web con el que se llevó a cabo la integración del módulo de redirección. Esto significa que el puerto debe estar abierto entre estos servidores.

### Estado del envío SMS {#sms-delivery-status}

Para rastrear envíos SMS (**nlserver sms**), debe estar abierto el siguiente puerto:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (puerto predeterminado)<br /> </td> 
   <td> Puerta de enlace SMS<br /> </td> 
   <td> Consulta el estado de la cola de envíos administrada por la puerta de enlace SMS de NetSize [opción].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cliente enriquecido {#rich-client}

Para el cliente enriquecido de Adobe Campaign (**nlclient**), deben abrirse los puertos siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Servidor de aplicaciones<br /> </td> 
   <td> Tráfico SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acceso a la base de datos {#database-access}

Todos los componentes que utilicen la base de datos deben poder conectarse a ella. Este es el caso de la mayoría de los componentes, a excepción del servidor de redirección, que puede funcionar solo, y del cliente ligero Win32, que utiliza HTTP (o HTTPS) sólo para comunicarse con el servidor de aplicaciones.

Los puertos predeterminados son los siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Tipo de base de datos<br /> </td> 
   <td> Puerto (predeterminado)<br /> </td> 
   <td> Destino<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Servidor de bases de datos<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acceso externo {#external-access}

Además, ciertos componentes deben ser accesibles desde Internet para que se puedan ver las campañas de correo electrónico ejecutadas directamente desde Adobe Campaign. Esto significa que algunos puertos deben estar abiertos para los componentes.

### Servidor de redirección {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Ubicación<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> En cualquier parte. Cada clic en un vínculo rastreado genera una solicitud HTTP en el servidor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor Web externo {#external-web-server}

Este servidor aloja Formularios web, páginas espejo, etc. Es necesario abrir los puertos siguientes:

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Ubicación<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> En cualquier parte. Necesario cuando los Formularios web se administran directamente desde la plataforma Adobe Campaign o cuando se utilizan páginas espejo.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicaciones interno (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Ubicación<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Todos los equipos que ejecutan el cliente ligero o el cliente enriquecido.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integración con Adobe Experience Manager {#integration-with-adobe-experience-manager}

La integración entre Adobe Campaign y Adobe Experience Manager requiere abrir varios puertos si la instalación está &quot;in situ&quot;. Para obtener más información sobre la configuración de esta integración, consulte la [documentación detallada](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Descripción<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Conexión AEM a Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Conexión de Adobe Campaign a AEM instancias de "creación" y "publicación". Los puertos que se van a abrir pueden diferir de los puertos predeterminados, según la configuración de AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Ancho de banda {#bandwidth}

Otro parámetro clave de la configuración de red que se debe tener en cuenta. Es casi siempre saliente y muy demandado durante las retransmisiones de correo electrónico. Estos son algunos ejemplos de configuraciones basadas en nuestra experiencia:

* 1 Mb/s por 10.000 correos electrónicos por hora (tamaño medio de 30 Kb)
* 8 a 10 Mb/s por 100.000 correos electrónicos por hora (tamaño medio de 30 Kb)

Si tiene restricciones en términos de ancho de banda, es posible programar campañas para que se ejecuten durante la noche cuando la demanda sea menor.
