---
product: campaign
title: Configuración de red
description: Conozca las directrices de comunicación del sistema
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 3%

---

# Configuración de red{#network-configuration}



## Comunicación entre procesos {#communication-between-processes}

Algunos procesos de la aplicación necesitan comunicarse con otros o acceder a la LAN y a Internet. Esto significa que algunos puertos TCP deben estar abiertos para estos procesos.

Utilice el puerto integrado de Apache Tomcat como prioridad (8080 de forma predeterminada) para las comunicaciones internas entre los distintos servidores de aplicaciones de una plataforma Adobe Campaign.

### Servidor de envío {#delivery-server}

Para el servidor de entrega (**mta de nlserver**), los puertos siguientes deben estar abiertos:

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
   <td> Tráfico SMTP para difusión por correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (dominio)<br /> </td> 
   <td> Servidores DNS<br /> </td> 
   <td> Consultas DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (puerto predeterminado)<br /> </td> 
   <td> Pasarela SMS<br /> </td> 
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

Para el proceso de recuperación de correo entrante (**nlserver inMail**), los puertos siguientes deben estar abiertos:

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
   <td> Tráfico POP3 para recoger mensajes de rechazo.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Servidor de correo interno<br /> </td> 
   <td> Tráfico SMTP para enviar los mensajes de rebote restantes que no procesan automáticamente las reglas predefinidas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor de aplicaciones {#application-server}

Para el servidor de aplicaciones (**nlserver web**), los puertos siguientes deben estar abiertos:

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
   <td> Tráfico HTTP o HTTPS (incluido para la oferta de envío).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Cuando varios servidores de aplicaciones de una plataforma de Adobe Campaign necesitan comunicarse entre sí, se recomienda utilizar el puerto del servidor Apache Tomcat (predeterminado: 8080) en lugar del puerto HTTP del servidor web con el que se llevó a cabo la integración del módulo de redirección. Esto significa que el puerto debe abrirse entre estos servidores.

### Estado de envío de SMS {#sms-delivery-status}

Para rastrear envíos de SMS (**nlserver sms**), el siguiente puerto debe estar abierto:

<table> 
 <tbody> 
  <tr> 
   <td> Puertos<br /> </td> 
   <td> Destino<br /> </td> 
   <td> Comentarios<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (puerto predeterminado)<br /> </td> 
   <td> Pasarela SMS<br /> </td> 
   <td> Consulta el estado de la cola de envíos administrada por la puerta de enlace de SMS NetSize [opción].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Cliente enriquecido {#rich-client}

Para el cliente enriquecido de Adobe Campaign (**nlclient**), los puertos siguientes deben estar abiertos:

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
   <td> Tráfico de SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Acceso a base de datos {#database-access}

Todos los componentes que utilicen la base de datos deben poder conectarse a ella. Este es el caso de la mayoría de los componentes, con la excepción del servidor de redirección, que puede funcionar solo, y del cliente ligero Win32, que utiliza HTTP (o HTTPS) únicamente para comunicarse con el servidor de aplicaciones.

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
   <td> Servidor de base de datos<br /> </td> 
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

Además, ciertos componentes deben ser accesibles desde la Internet pública para que se puedan ver las campañas de correo electrónico ejecutadas directamente desde Adobe Campaign. Esto significa que algunos puertos deben estar abiertos para los componentes.

### Servidor de redirección {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Ubicación<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> En cualquier sitio. Cada clic en un vínculo rastreado genera una solicitud HTTP en el servidor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Servidor web externo {#external-web-server}

Este servidor aloja formularios web, páginas espejo, etc. Los puertos siguientes deben estar abiertos:

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Ubicación<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> En cualquier sitio. Necesario cuando los formularios web se administran directamente desde la plataforma de Adobe Campaign o cuando se utilizan páginas espejo.<br /> </td> 
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

La integración entre Adobe Campaign y Adobe Experience Manager requiere la apertura de varios puertos si la instalación es &quot;on-premise&quot;. Para obtener más información sobre la configuración de esta integración, consulte [documentación detallada](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Puerto de escucha<br /> </td> 
   <td> Descripción<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM Conexión de la a Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Conexión de Adobe Campaign AEM a instancias de "creación" y "publicación" de. AEM Los puertos que se van a abrir pueden diferir de los puertos predeterminados, según la configuración de la aplicación de la que se haya hecho la configuración de la.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Ancho de banda {#bandwidth}

Otro parámetro clave de la configuración de red a tener en cuenta. Casi siempre es saliente y tiene mucha demanda durante las difusiones por correo electrónico. Estos son algunos ejemplos de configuraciones basadas en nuestra experiencia:

* 1 Mb/s para 10.000 correos electrónicos por hora (tamaño medio de 30 Kb)
* 8 a 10 Mb/s para 100.000 correos electrónicos por hora (tamaño medio de 30 Kb)

Si tiene restricciones en términos de ancho de banda, es posible programar campañas para que se ejecuten durante la noche cuando la demanda sea menor.
