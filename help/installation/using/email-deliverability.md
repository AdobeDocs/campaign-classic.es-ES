---
product: campaign
title: Configuración técnica de correo electrónico
description: Obtenga información sobre cómo configurar Campaign para controlar la salida de las instancias al enviar correos electrónicos
feature: Installation, Deliverability
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '3096'
ht-degree: 13%

---

# Configuraciones técnicas de correo electrónico{#email-deliverability}



## Información general {#overview}

La siguiente sección proporciona una descripción general de la configuración necesaria para controlar la salida de las instancias de Adobe Campaign al enviar correos electrónicos.

>[!NOTE]
>
>Algunas configuraciones solo las puede realizar Adobe para implementaciones alojadas en Adobe, por ejemplo, para acceder a los archivos de configuración del servidor y de la instancia. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Modelos de alojamiento](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md).

Para obtener más información sobre los conceptos y las prácticas recomendadas relacionadas con la capacidad de entrega con Adobe Campaign, consulte esta [sección](../../delivery/using/about-deliverability.md).

Para profundizar en lo que es la capacidad de entrega, incluidas todas las recomendaciones técnicas relativas al envío y la recepción eficientes de correos electrónicos por parte de una plataforma de Adobe, consulte la [Guía de prácticas recomendadas de entrega de Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).

## Principio de funcionamiento {#operating-principle}

Se puede controlar la salida de una o más instancias de Adobe Campaign para restringir el número de correos electrónicos enviados en función de un dominio. Por ejemplo, puede restringir la salida a 20 000 por hora para las direcciones de **yahoo.com**, mientras configura 100 000 mensajes por hora para todos los demás dominios.

La salida de mensajes debe controlarse para cada dirección IP utilizada por los servidores de entrega (**mta**). Varios **mta** desglosados en varios equipos y pertenecientes a distintas instancias de Adobe Campaign pueden compartir la misma dirección IP para la entrega por correo electrónico: es necesario configurar un proceso para coordinar el uso de estas direcciones IP.

Esto es lo que hace el módulo **stat**: reenvía todas las solicitudes de conexión y mensajes que se enviarán a los servidores de correo para un conjunto de direcciones IP. El servidor de estadísticas realiza un seguimiento de las entregas y puede habilitar o deshabilitar las entregas en función de las cuotas establecidas.

![](assets/s_ncs_install_mta.png)

* El servidor de estadísticas (**stat**) está vinculado a una base de Adobe Campaign para cargar su configuración.
* Los servidores de entrega (**mta**) usan un UDP para ponerse en contacto con un servidor de estadísticas que no siempre pertenece a su propia instancia.

### Servidores de envío {#delivery-servers}

El módulo **mta** distribuye mensajes a sus módulos secundarios **mtachild**. Cada **mtachild** prepara los mensajes antes de solicitar una autorización al servidor de estadísticas y enviarlos.

Los pasos son los siguientes:

1. El **mta** selecciona los mensajes aptos y les asigna un **mtachild** disponible.
1. **mtachild** carga toda la información necesaria para crear el mensaje (contenido, elementos de personalización, archivos adjuntos, imágenes, etc.) y reenvía el mensaje al **Administrador de tráfico de correo electrónico**.
1. Tan pronto como el formador de tráfico de correo electrónico reciba la autorización del servidor de estadísticas (**smtp stat**), el mensaje se enviará al destinatario.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Estadísticas y limitaciones del servidor de correo electrónico {#email-server-statistics-and-limitations}

El servidor de estadísticas mantiene las siguientes estadísticas para cada servidor de correo electrónico que recibe mensajes:

* Número de conexiones de punto en el tiempo abiertas,
* Número de mensajes enviados en la última hora,
* Tasa de conexiones correctas/rechazadas,
* Tasa de conexiones a servidores inaccesibles.

Al mismo tiempo, el módulo carga una lista de limitaciones para determinados servidores de correo electrónico:

* Número máximo de conexiones simultáneas,
* Número máximo de mensajes por hora,
* Número máximo de mensajes por conexión.

### Administración de direcciones IP {#managing-ip-addresses}

El servidor de estadísticas puede combinar varias instancias o varios equipos con la misma dirección IP pública. Por lo tanto, no está vinculado a una instancia específica, pero debe ponerse en contacto con una instancia para recuperar las limitaciones por dominio.

Las estadísticas de envío se conservan para cada MX de destino y para cada IP de origen. Por ejemplo, si el dominio de destino tiene 5 MX y la plataforma puede utilizar 3 direcciones IP diferentes, el servidor puede administrar hasta 15 series de indicadores para este dominio.

La dirección IP de origen coincide con la dirección IP pública, es decir, la dirección tal como la ve el servidor de correo electrónico remoto. Esta dirección IP puede ser diferente de la dirección del equipo que hospeda el **mta**, si se proporciona un enrutador NAT. Por este motivo, el servidor de estadísticas usa un identificador que coincide con la IP pública (**publicId**). La asociación entre la dirección local y este identificador se declara en el archivo de configuración **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

## Control de salida de envío {#delivery-output-controlling}

Para enviar mensajes a los servidores de correo electrónico, el componente **Email Traffic Shaper** solicita una conexión desde el servidor de estadísticas. Una vez aceptada la solicitud, se abre la conexión.

Antes de enviar mensajes, el módulo solicita &quot;tokens&quot; del servidor. Generalmente son conjuntos de al menos 10 tokens, lo que reduce el número de consultas al servidor.

El servidor guarda todas las estadísticas relacionadas con las conexiones y envíos. En caso de reinicio, la información se pierde temporalmente: cada cliente mantiene una copia local de sus estadísticas de envío y las devuelve al servidor de forma regular (cada 2 minutos). A continuación, el servidor puede volver a acumular los datos.

Las secciones siguientes describen el procesamiento de un mensaje por el componente **Email Traffic Shaper**.

### Entrega de mensajes {#message-delivery}

Cuando se envía un mensaje, hay 3 resultados posibles:

1. **Éxito**: el mensaje se envió correctamente. Se actualiza el mensaje.
1. **Error del mensaje**: el servidor contactado rechazó el mensaje para el destinatario elegido. Este resultado coincide con los códigos de retorno 550 a 599, pero se pueden definir excepciones.
1. **Error de sesión** (para 5.11 hacia arriba): si el **mta** recibe una respuesta para este mensaje, se abandona el mensaje (consulte [Abandono de mensaje](#message-abandonment)). El mensaje se envía a otra ruta o se establece como pendiente si no hay otras rutas disponibles (consulte [Mensaje pendiente](#message-pending)).

   >[!NOTE]
   >
   >Una **ruta** es una conexión entre Adobe Campaign **mta** y el destino **mta**. El Adobe Campaign **mta** puede elegir entre varias IP de inicio y varias IP de dominio de destino.

### Abandono de mensajes {#message-abandonment}

Los mensajes abandonados se devuelven a **mta** y ya no son administrados por **mtachild**.

El **mta** decide el procedimiento para este mensaje (recuperación, abandono, cuarentena, etc.) según el código de respuesta y las reglas.

### Mensaje pendiente {#message-pending}

Un mensaje queda pendiente cuando llega a la cola activa y no hay rutas disponibles.

Una ruta generalmente se marca como no disponible durante un período de tiempo variable después de un error de conexión. El periodo de indisponibilidad depende de la frecuencia y la edad de los errores.

## Configuración del servidor de estadísticas {#statistics-server-configuration}

El servidor de estadísticas se puede utilizar en varias instancias: debe configurarse de forma independiente de las instancias que lo utilizarán.

Comience por definir la base de datos de Adobe Campaign que alojará la configuración.

### Iniciar configuración {#start-configuration}

De manera predeterminada, el módulo **stat** se inicia para cada instancia. Cuando las instancias se agrupan en el mismo equipo o cuando las instancias comparten la misma dirección IP, se utiliza un único servidor de estadísticas: los demás deben deshabilitarse.

### Definición del puerto del servidor {#definition-of-the-server-port}

De forma predeterminada, el servidor de estadísticas escucha en el puerto 7777. Este puerto se puede modificar en el archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configuración MX {#mx-configuration}

>[!IMPORTANT]
>
>En el caso de instalaciones alojadas o híbridas, si se ha actualizado al [servidor de correo mejorado](../../delivery/using/sending-with-enhanced-mta.md), ya no se utilizan las reglas de rendimiento de envíos **[!UICONTROL MX management]**. El servidor de correo mejorado utiliza sus propias reglas MX que le permiten personalizar el rendimiento por dominio en función de su propia reputación histórica de correo electrónico y de los comentarios en tiempo real procedentes de los dominios a los que envía correos electrónicos.

### Acerca de las reglas MX {#about-mx-rules}

>[!NOTE]
>
>Esta sección y las secciones siguientes solo se aplican a instalaciones on-premise e instalaciones hospedadas/híbridas que utilizan el servidor de correo de Campaign heredado.

Las reglas MX (Mail eXchanger) son las reglas que administran la comunicación entre un servidor emisor y un servidor receptor.

Estas reglas se vuelven a cargar automáticamente cada mañana a las 6 a. m. (hora del servidor) para proporcionar regularmente la instancia de cliente.

Según las capacidades materiales y la política interna, un ISP aceptará un número predefinido de conexiones y mensajes por hora. El sistema ISP puede modificar automáticamente estas variables en función de la reputación de la IP y del dominio de envío. Mediante su plataforma de envío, Adobe Campaign administra más de 150 reglas específicas del ISP y, además, una regla genérica para otros dominios.

El número máximo de conexiones no depende exclusivamente del número de direcciones IP públicas que utiliza el MTA.

Por ejemplo, si ha permitido 5 conexiones en las reglas MX y ha configurado 2 direcciones IP públicas, puede pensar que no puede tener más de 10 conexiones abiertas simultáneamente a este dominio. Esto no es así, en realidad el número máximo de conexiones se refiere a una ruta y a una ruta que combine una de nuestras IP públicas de MTA y una IP pública del MTA del cliente.

En el siguiente ejemplo, el usuario tiene dos direcciones IP públicas configuradas y el dominio es yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

Los registros MX para yahoo.com nos dicen que yahoo.com tiene 3 intercambiadores de correo. Para conectar el intercambiador de correo de pares, el MTA solicita su dirección IP al DNS.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

Para este registro, el usuario puede contactar con 8 direcciones IP de igual a igual. Como el usuario tiene 2 direcciones IP públicas, esto les proporciona 8 * 2 = 16 combinaciones para llegar a los servidores de correo de yahoo.com. Cada una de estas combinaciones se denomina ruta.

El segundo registro MX aparece como:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 de estas 8 direcciones IP ya se usan en mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 y 98.136.217.203). Este registro permite al usuario utilizar 4 direcciones IP nuevas. El tercer registro MX hace lo mismo.

En total, tenemos 16 direcciones IP remotas. En combinación con nuestras 2 IP públicas locales, tenemos 32 rutas para llegar a los servidores de correo de yahoo.com.

>[!NOTE]
>
>Si 2 registros MX hacen referencia a la misma dirección IP, esta cuenta como una ruta en lugar de dos.

A continuación se muestran algunos ejemplos de uso de reglas MX:

![](assets/s_ncs_examples_mx_rules.png)

En el siguiente ejemplo, el usuario tiene un límite de 10 000 mensajes por hora para un dominio determinado, pero la capacidad de rendimiento del MTA es superior a este límite.

En este caso, el tráfico se divide en 12 periodos de 5 minutos para cada hora y el límite real es de 833 mensajes por periodo.

Estos mensajes se envían lo más rápidamente posible.

![](assets/s_ncs_traffic_shaping.png)

### Configuración de la gestión de MX {#configuring-mx-management}

Las reglas que se deben cumplir para MX se definen en el documento **[!UICONTROL MX management]** del nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** del árbol.

Si el documento **[!UICONTROL MX management]** no existe en el nodo, puede crearlo manualmente. Para ello, haga lo siguiente:

1. Cree un nuevo conjunto de reglas de correo.
1. Elija el modo **[!UICONTROL MX management]**.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Escriba **defaultMXRules** en el campo **[!UICONTROL Internal name]**.

Para que se tengan en cuenta los cambios, debe reiniciar el servidor de estadísticas.

Para volver a cargar la configuración sin reiniciar el servidor de estadísticas, use el siguiente comando en el equipo que hospeda el servidor: `nlserver stat -reload`

>[!NOTE]
>
>Esta línea de comandos es preferible a **nlserver restart**. Evita que las estadísticas recopiladas antes del reinicio se pierdan y evita los picos en uso que pueden ir contra las cuotas definidas en las reglas MX.

### Configuración de reglas MX {#configuring-mx-rules}

El documento **[!UICONTROL MX management]** enumera todos los dominios vinculados a una regla MX.

Estas reglas se aplican en secuencia: se aplica la primera regla cuya máscara MX es compatible con el MX de destino.

Los siguientes parámetros disponibles para cada regla son:

* **[!UICONTROL MX mask]**: dominio en el que se aplica la regla. Cada regla define una máscara de dirección para el MX. Por lo tanto, cualquier MX cuyo nombre coincida con esta máscara es elegible. La máscara puede contener &quot;&#42;&quot; y &quot;?&quot; caracteres genéricos.

  Por ejemplo, las siguientes direcciones:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  son compatibles con las siguientes máscaras:

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

  Por ejemplo, para la dirección de correo electrónico foobar@gmail.com, el dominio es gmail.com y el registro MX es:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  En este caso, se utilizará la regla MX `*.google.com`. Como puede ver, la máscara de regla MX no coincide necesariamente con el dominio del correo. Las reglas MX aplicadas para las direcciones de correo electrónico gmail.com serán las que tengan la máscara `*.google.com`.

* **[!UICONTROL Range of identifiers]**: esta opción le permite indicar los intervalos de identificadores (publicID) para los que se aplica la regla. Puede especificar:

   * Un número: la regla solo se aplicará a este publicId,
   * Un rango de números (**number1-number2**): la regla se aplicará a todos los publicIds entre estos dos números.

  >[!NOTE]
  >
  >Si el campo está vacío, la regla se aplica a todos los identificadores.

  Un ID público es un identificador interno de una IP pública que utilizan uno o varios MTA. Estas ID se definen en los servidores MTA del archivo **config-instance.xml**.

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: define el ámbito de las propiedades de esta regla MX. Cuando se selecciona, todos los parámetros se comparten en todas las direcciones IP disponibles en la instancia. Cuando no está marcada, las reglas MX se definen para cada IP. El número máximo de mensajes se multiplica por el número de direcciones IP disponibles.
* **[!UICONTROL Maximum number of connections]**: número máximo de conexiones simultáneas con el dominio del remitente.
* **[!UICONTROL Maximum number of messages]**: número máximo de mensajes que se pueden enviar en una conexión. Cuando los mensajes superan este número, la conexión se cierra y se abre una nueva.
* **[!UICONTROL Messages per hour]**: número máximo de mensajes que se pueden enviar en una hora al dominio del remitente.
* **[!UICONTROL Connection time out]**: umbral de tiempo para conectarse a un dominio.

  >[!NOTE]
  >
  >Windows puede emitir un **tiempo de espera** antes de este umbral, que depende de su versión de Windows.

* **[!UICONTROL Timeout Data]**: tiempo de espera máximo después de enviar contenido de mensaje (sección DATA del protocolo SMTP).
* **[!UICONTROL Timeout]**: tiempo de espera máximo para otros intercambios con el servidor SMTP.
* **[!UICONTROL TLS]**: el protocolo TLS, que permite cifrar envíos de correo electrónico, se puede habilitar de forma selectiva. Para cada máscara MX, están disponibles las siguientes opciones:

   * **[!UICONTROL Default configuration]**: esta es la configuración general especificada en el archivo de configuración serverConf.xml que se aplica.

     >[!IMPORTANT]
     >
     >No se recomienda modificar la configuración predeterminada.

   * **[!UICONTROL Disabled]**: los mensajes se envían sistemáticamente sin cifrado.
   * **[!UICONTROL Opportunistic]**: la entrega de mensajes está cifrada si el servidor receptor (SMTP) puede generar el protocolo TLS.

Ejemplo de configuración:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Para obtener más información sobre el uso de servidores MX con Adobe Campaign, consulte [esta sección](../../installation/using/using-mx-servers.md).

### Administración de formatos de correo electrónico {#managing-email-formats}

Puede definir el formato de los mensajes enviados, de modo que el contenido mostrado se adapte automáticamente según el dominio de la dirección de cada destinatario.

Para ello, vaya al documento **[!UICONTROL Management of email formats]**, que se encuentra en **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Este documento contiene una lista de todos los dominios predefinidos que corresponden a los formatos japoneses administrados por Adobe Campaign. Para obtener más información, consulte la [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=es){target="_blank"}.

![](assets/mail_rule_sets.png)

El parámetro **MIME structure** (Multipurpose Internet Mail Extensions) permite definir la estructura de mensajes que se enviará a los distintos clientes de correo. Hay tres opciones disponibles:

* **Multipart**: el mensaje se envía en formato de texto o HTML. Si no se acepta el formato HTML, el mensaje se podrá mostrar en formato de texto.

  De manera predeterminada, la estructura multipart es **multipart/alternative**, pero se convierte automáticamente en **multipart/related** cuando se agrega una imagen al mensaje. Algunos proveedores esperan el formato **multipart/related** de forma predeterminada, la opción **[!UICONTROL Force multipart/related]** impone este formato incluso si no hay ninguna imagen adjunta.

* **HTML**: se envía un mensaje solo de HTML. Si no se acepta el formato HTML, no se muestra el mensaje.
* **Texto**: se envía un mensaje en formato de solo texto. La ventaja de los mensajes de formato de texto es su tamaño muy pequeño.

Si la opción **[!UICONTROL Image inclusion]** está habilitada, estas se muestran directamente en el cuerpo del correo electrónico. Las imágenes se cargan y los vínculos URL se sustituyen por su contenido.

El mercado japonés usa esta opción especialmente para **Deco-mail**, **Decore Mail** o **Decoration Mail**. Para obtener más información, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=es){target="_blank"}.

>[!IMPORTANT]
>
>Al insertar imágenes en un correo electrónico, su tamaño aumenta considerablemente.

## Configuración del servidor de envío {#delivery-server-configuration}

### Sincronización del reloj {#clock-synchronization}

Los relojes de todos los servidores que componen la plataforma Adobe Campaign (incluida la base de datos) deben sincronizarse y sus sistemas deben establecerse en la misma zona horaria.

### Coordenadas del servidor de estadísticas {#coordinates-of-the-statistics-server}

La dirección del servidor de estadísticas debe proporcionarse en **mta**.

La propiedad **statServerAddress** del elemento **mta** de la configuración le permite especificar la dirección y el número del puerto que se va a utilizar.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Para usar el servidor de estadísticas en el mismo equipo, debe escribir al menos el nombre del equipo con el valor **localhost**:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Si no se rellena este campo, **mta** no se iniciará.

### Lista de direcciones IP para usar {#list-of-ip-addresses-to-use}

La configuración relacionada con la administración del tráfico se encuentra en el elemento **mta/child/smtp** del archivo de configuración.

Para cada elemento **IPAffinity**, debe declarar las direcciones IP que se pueden usar para el equipo.

Ejemplo:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Los parámetros son los siguientes:

* **dirección**: esta es la dirección IP del equipo host de MTA que se va a usar.
* **heloHost**: este identificador representa la dirección IP tal como la verá el servidor SMTP.

* **publicId**: esta información es útil cuando varias **mtas** de Adobe Campaign comparten una dirección IP detrás de un enrutador NAT. El servidor de estadísticas utiliza este identificador para memorizar las estadísticas de conexión y envío entre este punto de inicio y el servidor de destino.
* **weight**: permite definir la frecuencia relativa de uso de la dirección. De forma predeterminada, todas las direcciones tienen un peso igual a 1.

>[!NOTE]
>
>En el archivo serverConf.xml, debe comprobar que una IP corresponde a un único host de ayuda con un identificador único (public_id). No se puede asignar a varios hosts de ayuda, lo que podría provocar problemas de regulación de envíos.

En el ejemplo anterior, con condiciones normales, las direcciones se distribuyen de la siguiente manera:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Si, por ejemplo, la primera dirección no se puede utilizar hacia un MX determinado, los mensajes se enviarán de la siguiente manera:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: permite reservar esta dirección IP para los mensajes de correo electrónico que pertenecen a un dominio específico. Esta es una lista de máscaras que pueden contener uno o más caracteres comodín (&#39;&#42;&#39;). Si no se especifica el atributo, todos los dominios pueden utilizar esta dirección IP.

  Ejemplo: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: excluye una lista de dominios para esta dirección IP. Este filtro se aplica después del filtro **includeDomains**.

  ![](assets/s_ncs_install_mta_ips.png)

## Optimización del envío de correo electrónico {#email-sending-optimization}

La arquitectura interna de Adobe Campaign **mta** tiene un impacto en la configuración para optimizar la entrega de correo electrónico. A continuación se ofrecen algunas sugerencias para mejorar los envíos.

### Ajuste del parámetro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

El parámetro **maxWaitingMessages** indica el número más alto de mensajes preparados de antemano por el **mtachild**. Los mensajes solo se eliminan de esta lista una vez que se han enviado o abandonado.

Este parámetro es muy importante y especialmente crítico si los mensajes no se ordenan por dominio.

Una vez alcanzado el umbral **maxWorkingSetMb** (256), el servidor de entrega detiene el envío de mensajes. El rendimiento disminuirá significativamente hasta que **mtachild** vuelva a iniciarse. Para evitar este problema, puede aumentar el umbral del parámetro **maxWorkingSetMb** o disminuir el umbral del parámetro **maxWaitingMessages**.

El parámetro **maxWorkingSetMb** se calcula empíricamente multiplicando el número máximo de mensajes por el tamaño promedio del mensaje y el resultado por 2,5. Por ejemplo, si un mensaje tiene un tamaño promedio de 50 kB y el parámetro **maxWaitingMessages** equivale a 1.000, la memoria utilizada será de 125 MB como promedio.

### Ajustar el número de equipos {#adjust-the-number-of-mtachild}

El número de niños no debe exceder el número de procesadores en la máquina (aprox. 1000 sesiones). Se recomienda no exceder los 8 **mtachild**. Puede aumentar el número de mensajes por **elemento secundario** (**maxMsgPerChild**) para lograr una vida útil suficiente.
