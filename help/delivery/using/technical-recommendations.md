---
solution: Campaign Classic
product: campaign
title: Recomendaciones técnicas para mejorar la capacidad de entrega con Adobe Campaign Classic
description: Descubra las técnicas, configuraciones y herramientas que puede utilizar para mejorar la tasa de entrega con Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '2427'
ht-degree: 100%

---


# Recomendaciones técnicas{#technical-recommendations}

A continuación se enumeran varias técnicas, configuraciones y herramientas que puede utilizar para mejorar la tasa de entrega.

## Configuración {#configuration}

### DNS inverso {#reverse-dns}

Adobe Campaign comprueba si se ha proporcionado un DNS inverso para una dirección IP y que este señala correctamente a la dirección IP.

Un punto importante de la configuración de red es garantizar que se haya definido un DNS inverso correcto para cada una de las direcciones IP de los mensajes salientes. Esto significa que para una dirección IP determinada, existe un registro DNS inverso (registro PTR) con un bucle DNS (registro A) que corresponde con la dirección IP inicial.

La elección de dominio del DNS inverso influye al tratar con determinados ISP. AOL, en particular, solo acepta bucles de comentarios con una dirección del mismo dominio que el DNS inverso (consulte [Bucle de comentarios](#feedback-loop)).

Hay una herramienta disponible para verificar la configuración de un dominio: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### Reglas MX {#mx-rules}

Las reglas MX (Mail eXchanger) son las reglas que administran la comunicación entre un servidor emisor y un servidor receptor.

Más precisamente, se utilizan para controlar la velocidad a la que el MTA de Campaign (Agente de transferencia de mensajes) envía correos electrónicos a cada dominio de correo electrónico o ISP individual (por ejemplo, hotmail.com, comcast.net). Estas reglas generalmente se basan en los límites que publican los ISP (por ejemplo, no incluir más de 20 mensajes por cada conexión SMTP).

Para obtener más información sobre gestión MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) es un protocolo de codificación que se puede utilizar para asegurar la conexión entre dos servidores de correo electrónico y proteger el contenido de un correo electrónico evitar que lo lean destinatarios no previstos.

## Autenticación {#authentication}

### SPF {#spf}

SPF (Entorno de políticas de remitentes) es un estándar de autenticación de correo electrónico que permite al propietario de un dominio especificar qué servidores de correo electrónico pueden enviar correos electrónicos en nombre de ese dominio. Este estándar utiliza el dominio en el encabezado “Return-Path” del correo electrónico (también denominado la dirección “Envelope From”).

Hay una herramienta disponible para verificar un registro SPF: [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

El SPF es una técnica que, a su vez, permite asegurarse de que el nombre de dominio utilizado en un mensaje de correo electrónico no sea falso. Cuando se recibe un mensaje de un dominio, se consulta el servidor DNS del dominio. La respuesta es un breve registro (el registro SPF) que muestra los servidores autorizados para enviar correos electrónicos desde este dominio. Si asumimos que solo el propietario del dominio tiene la posibilidad de cambiar este registro, podemos considerar que esta técnica no permite que la dirección del remitente sea falsa, al menos no la parte a la derecha de la “@”.

En la [especificación RFC 4408](https://www.rfc-editor.org/info/rfc4408) final, se utilizan dos elementos del mensaje para determinar el dominio considerado como remitente: Dominio especificado por el comando SMTP “HELO” (o “EHLO”) y el dominio especificado por la dirección del encabezado “Return-Path” (o “MAIL FROM”), que también es la dirección de rechazo. Las diferentes consideraciones permiten tener en cuenta solo uno de estos valores; se recomienda que ambos orígenes especifiquen el mismo dominio.

La comprobación del SPF ofrece una evaluación de la validez del dominio del remitente:

* **None**: No se pudo realizar ninguna evaluación,
* **Neutral**: El dominio que se consulta no activa la evaluación,
* **Pass**: El dominio se considera auténtico,
* **Fail**: El dominio es falso y el mensaje se debe rechazar,
* **SoftFail**: Es probable que el dominio sea falso, pero el mensaje no se debe rechazar únicamente como consecuencia de este resultado,
* **TempError**: Un error temporal detuvo la evaluación. El mensaje se puede rechazar,
* **PermError**: Los registros del SPF del dominio no son válidos.

Cabe señalar que el proceso para tener en cuenta los registros realizados al nivel de los servidores DNS puede tardar hasta 48 horas. Este retardo depende de la frecuencia con que se actualicen las cachés DNS de los servidores receptores.

### DKIM {#dkim}

>[!IMPORTANT]
>
>Para instalaciones hospedadas o híbridas, si ha actualizado a [MTA mejorado](../../delivery/using/sending-with-enhanced-mta.md), este crea la firma de autenticación de correo electrónico DKIM para todos los mensajes con todos los dominios.

La autenticación DKIM (DomainKeys Identified Mail) es un sucesor de SPF y utiliza criptografía de clave pública que permite al servidor de correo electrónico receptor verificar que un mensaje fue enviado por la persona o entidad por la que afirma que fue enviado, y si el contenido del mensaje se alteró entre el momento en que se envió originalmente (y “firmado” por DKIM) y la hora en que se recibió. Este estándar suele utilizar el dominio en el encabezado “De” o “Remitente”. Para asegurar el nivel de seguridad del DKIM, 1024b es el tamaño de codificación según las prácticas recomendadas. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores.

DKIM surge a partir de una combinación de los principios de autenticación de DomainKeys, Yahoo! y Cisco Mail, y se utiliza para comprobar la autenticidad del dominio del remitente y garantizar la integridad del mensaje.

DKIM sustituye la autenticación por **DomainKeys**.

El uso de DKIM requiere algunos requisitos previos:

* **Security**: el cifrado es un elemento clave del DKIM y para asegurar el nivel de seguridad del DKIM desde la primavera de 2013, el tamaño de cifrado recomendado es de 1024 bits. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM menores.
* **Reputation**: la reputación se basa en la dirección IP o en el dominio, pero el selector menos transparente de DKIM también es un elemento clave a tener en cuenta. La elección del selector es importante: evite mantener el “predeterminado” que podría utilizar cualquier persona y, por lo tanto, tiene una reputación baja. Debe implementar un selector diferente para las **retention vs. acquisition communications** y para la autenticación.
* **Adobe Campaign option declaration**: en Adobe Campaign, la clave privada DKIM se basa en un dominio y un selector DKIM. Actualmente no es posible crear múltiples claves privadas para el mismo dominio/subdominio con distintos selectores. No se puede definir qué dominio/subdominio de selector se debe utilizar para la autenticación en ninguna plataforma o en el correo electrónico. La plataforma selecciona una de las claves privadas, lo que significa que la autenticación tiene una mayor probabilidad de fallo.

>[!NOTE]
>
>* Si ha configurado DomainKeys para la instancia de Adobe Campaign, solo debe seleccionar **dkim** en las [Reglas de administración de dominios](../../delivery/using/understanding-delivery-failures.md#domain-management). Si no, siga los mismos pasos de configuración (clave privada/pública) que para DomainKeys.
>* No es necesario activar DomainKeys y DKIM para el mismo dominio, ya que DKIM es una versión mejorada de DomainKeys.
>* Los siguientes dominios actualmente validan DKIM: AOL, Gmail.


### DMARC {#dmarc}

DMARC (Autenticación de mensajes, creación de informes y conformidad basados en dominio) es la forma más reciente de autenticación por correo electrónico y se basa en la autenticación SPF y DKIM para determinar si un correo electrónico pasa o falla. DMARC es única y útil de dos maneras muy importantes:

* Conformidad: permite al remitente indicar a los ISP qué hacer con cualquier mensaje que no se autentique (por ejemplo: no aceptarlo).
* Creación de informes: proporciona al remitente un informe detallado que muestra todos los mensajes en los que se ha producido un error en la autenticación DMARC, junto con el dominio “De” y la dirección IP utilizadas para cada uno. Esto permite que una empresa identifique el correo electrónico legítimo que falla en la autenticación y necesita algún tipo de “corrección” (por ejemplo: añadir direcciones IP a su registro SPF), así como las fuentes y la prevalencia de intentos de phishing en sus dominios de correo electrónico.

DMARC puede aprovechar los informes generados por [250ok](https://250ok.com/).

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## Bucle de comentarios {#feedback-loop}

Un bucle de comentarios funciona declarando al nivel del ISP una dirección de correo electrónico determinada para un rango de direcciones IP utilizadas para enviar mensajes. El ISP se envía a este buzón de correo, de manera similar a lo que se hace para los mensajes rechazados, aquellos mensajes cuyos destinatarios notifiquen como correo no deseado. La plataforma debe configurarse para bloquear futuros entregas a los usuarios que envíen quejas. Es importante no volver a ponerse en contacto con ellos aunque no hayan utilizado el vínculo de exclusión adecuado. Estas quejas son el motivo principal por el que un ISP añade una dirección IP a una lista de bloqueados. En función del ISP, una tasa de quejas de alrededor del 1 % resulta en el bloqueo de una dirección IP.

Actualmente se está elaborando un estándar para definir el formato de los mensajes de bucle de comentarios: el [Abuse Feedback Reporting Format (ARF)](https://tools.ietf.org/html/rfc6650).

La implementación de un bucle de comentarios para una instancia requiere:

* Un buzón dedicado a la instancia, que puede ser el buzón de rechazos
* Direcciones IP de entrega dedicadas a la instancia

La implementación de un bucle de comentarios sencillo en Adobe Campaign utiliza la función de mensaje rechazado. El buzón de comentarios se utiliza como buzón de rechazos y se define una regla para detectar estos mensajes. Las direcciones de correo electrónico de los destinatarios que notificaron el mensaje como correo no deseado se añaden a la lista de cuarentena.

* Cree o modifique una regla de correo rechazado, **Feedback_loop**, en **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** con el motivo **Refused** y el tipo **Hard**.
* Si se ha definido un buzón especialmente para el bucle de comentarios, defina los parámetros para acceder a él mediante la creación de una nueva cuenta de correos rechazados externa en **[!UICONTROL Administration > Platform > External accounts]**.

El mecanismo está operativo inmediatamente para procesar las notificaciones de quejas. Para asegurarse de que esta regla funciona correctamente, puede desactivar temporalmente las cuentas para que no recopilen estos mensajes y, a continuación, comprobar manualmente el contenido del buzón del bucle de comentarios. En el servidor, ejecute los siguientes comandos:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Si está obligado a utilizar una dirección de bucle de comentarios única para varias instancias, debe:

* Reproducir los mensajes recibidos en tantos buzones como instancias haya,
* Hacer que cada instancia recopile un buzón de correo,
* Configure las instancias para que solo procesen los mensajes que les corresponda: la información de la instancia se incluye en el encabezado Message-ID de los mensajes que envía Adobe Campaign y, por lo tanto, también se ubica en los mensajes del bucle de comentarios. Sencillamente especifique el parámetro **checkInstanceName** en el archivo de configuración de instancia (de forma predeterminada, la instancia no se verifica y esto puede provocar que la dirección se ponga en cuarentena indebidamente):

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

El servicio de capacidad de entregas de Adobe Campaign administra la suscripción a los servicios de bucle de comentarios para los siguientes ISP: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## Cancelación de suscripción a una lista {#list-unsubscribe}

### Acerca de la cancelación de la suscripción a una lista {#about-list-unsubscribe}

La adición de un encabezado SMTP denominado **List-Unsubscribe** es obligatoria para garantizar una gestión óptima de la entrega.

Este encabezado puede utilizarse como alternativa al icono “Notificar como correo no deseado”. Se muestra como un vínculo para darse de baja en la interfaz de correo electrónico.

El uso de esta función ayuda a proteger la reputación, y los comentarios se ejecutan como una baja.

>[!NOTE]
>
>Esta función está disponible desde la versión 6831.

Para utilizar la cancelación de la suscripción a una lista, debe introducir una línea de comandos similar a la siguiente:

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>El ejemplo anterior se basa en la tabla de destinatarios. Si la implementación de la base de datos se realiza desde otra tabla, asegúrese de volver a redactar la línea de comandos con la información correcta.

La siguiente línea de comandos se puede utilizar para crear una **List-Unsubscribe** dinámica:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com y Microsoft Outlook son compatibles con este método y en su interfaz está disponible directamente un botón de cancelación de la suscripción. Esta técnica reduce las tasas de quejas.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

Puede implementar **List-Unsubscribe**:

* añadiendo directamente la línea de comandos en la plantilla de entrega, consulte [esta sección](#adding-a-command-line-in-a-delivery-template),
* o creando una regla de tipología: consulte [esta sección](#creating-a-typology-rule).

### Adición de una línea de comandos en una plantilla de entrega {#adding-a-command-line-in-a-delivery-template}

La línea de comandos debe añadirse en la sección adicional del encabezado SMTP del correo electrónico.

Esta adición se puede realizar en cada correo electrónico o en plantillas de entrega existentes. También puede crear una nueva plantilla de distribución que incluya esta función.

### Crear una regla de tipología {#creating-a-typology-rule}

La regla debe contener la secuencia que genera la línea de comandos y debe incluirse en el encabezado del correo electrónico.

>[!NOTE]
>
>Se recomienda crear una regla de tipología: la funcionalidad List-Unsubscribe se añade automáticamente en cada correo electrónico.

1. Cancelación de suscripción a una lista: &lt;mailto:unsubscribe@domain.com>

   Al hacer clic en el vínculo **unsubscribe** se abre el cliente de correo electrónico predeterminado del usuario. Esta regla de tipología debe añadirse en una tipología utilizada para crear correo electrónico.

1. Cancelación de suscripción a una lista: `<https://domain.com/unsubscribe.jsp>`

   Al hacer clic en el vínculo **unsubscribe**, se redirige al usuario a su formulario de cancelación de suscripción.

   Ejemplo:

   ![](assets/s_tn_del_unsubscribe_param.png)

## Optimización del correo electrónico {#email-optimization}

### SMTP {#smtp}

SMTP (Protocolo simple de transferencia de correo) es un estándar de Internet para la transmisión de correos electrónicos.

Los errores de SMTP que no están marcados por una regla se enumeran en la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]**. Estos mensajes de error se interpretan de forma predeterminada como errores leves no accesibles. Los errores más comunes deben identificarse y se debe añadir una regla correspondiente en **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** si desea calificar correctamente los comentarios de los servidores SMTP. Sin esto, la plataforma realiza reintentos innecesarios (en caso de usuarios desconocidos) o pone incorrectamente en cuarentena a los destinatarios tras un número determinado de pruebas.

### IP dedicadas {#dedicated-ips}

Adobe proporciona una estrategia IP dedicada para cada cliente con una IP de aumento para crear una reputación y optimizar el rendimiento de la entrega.

## Certificación de IP {#ip-certification}

La certificación de IP es un programa de prácticas de envío que garantiza que los correos electrónicos se reciban sin ser bloqueados por los filtros antispam u otros sistemas de bloqueo de correo electrónico.

Actualmente dos proveedores ofrecen certificación IP: Return Path y Certified Senders Alliance.

Los remitentes certificados se añaden a las lista de permitidos de correo electrónico que utilizan los proveedores de buzones de correo globales y las empresas de seguridad de correo electrónico. Las lista de permitidos comerciales se basan en un sistema que permite al remitente saltarse los filtros de correo no deseado o recibir puntos graduales al entrar en el sistema.

El programa [Return Path Certification](https://www.validity.com/products/returnpath/certification/) ofrece una serie de ventajas, entre las que se incluyen las siguientes:

* Un aumento mensurable en la ubicación de las bandejas de entrada en los principales proveedores de buzones de correo como Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru y más.
* Reputación y tratamiento favoritos en filtros críticos como Cloudmark, SpamAssassin y Cisco Ironport.
* Un equipo de cumplimiento dedicado a la monitorización las 24 horas del día, los 7 días de la semana, con alertas de seguridad y trabajando con usted a través de la resolución de cualquier compromiso.
* Datos del proveedor de buzones de correo que ofrecen información detallada sobre KPI, ubicación y rendimiento de certificación.
* Calentamiento de IP simplificado y más rápido, que incluye una reputación y reconocimiento más sólidos al migrar u obtener una nueva dirección IP.

La certificación [Certified Senders Alliance](https://certified-senders.org/certification-process/) ofrece, entre otras ventajas:

* Certificación de remitentes de correos electrónicos comerciales que pueden cumplir con estándares de alta calidad.
* Entrega y capacidad de entrega mejorados de correos electrónicos comerciales para aumentar la tasa de colocación en la bandeja de entrada y reducir el filtrado de correo no deseado.
* Protección contra los riesgos jurídicos y financieros cumpliendo plenamente las normas jurídicas.
* Protección de la reputación mediante advertencias tempranas de la Oficina de Quejas de la CSA e informes diarios de trampas de correos no deseados.

Los ISP son libres de utilizar estos servicios y el número de ISP puede variar según la lista de permitidos.

Sin embargo, debido a que cada vez más ISP crean sus filtros antispam en función del comportamiento de cada propietario de la bandeja de entrada en lugar de analizar el contenido del mensaje en sí, el uso de la certificación IP no puede ser una garantía de colocación en la bandeja de entrada o incluso de entrega.
