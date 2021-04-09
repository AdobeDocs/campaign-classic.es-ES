---
solution: Campaign Classic
product: campaign
title: Configuración de envío de campaña
description: Obtenga información sobre cómo configurar la configuración de Entrega de campañas
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 3%

---

# Configurar las opciones de envío {#delivery-settings}

Los parámetros de envío deben configurarse en la carpeta **serverConf.xml**.

* **Configuración** de DNS: especifique el dominio de entrega y las direcciones IP (o host) de los servidores DNS utilizados para responder a consultas DNS de tipo MX realizadas por el módulo MTA a partir de  **`<dnsconfig>`** entonces.

   >[!NOTE]
   >
   >El parámetro **nameServers** es esencial para una instalación en Windows. Para una instalación en Linux, debe dejarse vacía.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

También puede realizar las siguientes configuraciones según sus necesidades y configuraciones: configure un [SMTP relay](#smtp-relay), adapte el número de [MTA child processes](#mta-child-processes), [Manage outbound SMTP traffic](#managing-outbound-smtp-traffic-with-affinities).

## Retransmisión SMTP {#smtp-relay}

El módulo MTA actúa como agente de transferencia de correo nativo para la difusión SMTP (puerto 25).

Sin embargo, es posible reemplazarlo por un servidor de transmisión si la política de seguridad lo requiere. En ese caso, el rendimiento global será el de transmisión (siempre que el rendimiento del servidor de transmisión sea inferior al de Adobe Campaign).

En este caso, estos parámetros se establecen configurando el servidor SMTP en la sección **`<relay>`** . Debe especificar la dirección IP (o el host) del servidor SMTP utilizado para transferir el correo y su puerto asociado (25 de forma predeterminada).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Este modo operativo implica serias limitaciones en las entregas, ya que puede reducir en gran medida el rendimiento debido al rendimiento intrínseco del servidor de transmisión (latencia, bandwith...). Además, la capacidad para clasificar los errores de envío sincrónico (detectados mediante el análisis del tráfico SMTP) será limitada y el envío no será posible si el servidor de transmisión no está disponible.

## Procesos secundarios de MTA {#mta-child-processes}

Es posible controlar el número de procesos secundarios (maxSpareServers de forma predeterminada 2) para optimizar el rendimiento de difusión según la potencia de CPU de los servidores y los recursos de red disponibles. Esta configuración se debe realizar en la sección **`<master>`** de la configuración de MTA de cada equipo individual.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulte también [Optimización de envío de correo electrónico](../../installation/using/email-deliverability.md#email-sending-optimization).

## Administrar tráfico SMTP saliente con afinidades {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configuración de afinidad debe ser coherente de un servidor a otro. Le recomendamos que se ponga en contacto con Adobe para la configuración de afinidad, ya que los cambios de configuración deben replicarse en todos los servidores de aplicaciones que ejecuten el MTA.

Puede mejorar el tráfico SMTP saliente mediante afinidades con direcciones IP.

Para ello, siga los siguientes pasos:

1. Introduzca las afinidades en la sección **`<ipaffinity>`** del archivo **serverConf.xml**.

   Una afinidad puede tener varios nombres diferentes: para separarlos, utilice el carácter **;**.

   Ejemplo:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Para ver los parámetros relevantes, consulte el archivo **serverConf.xml** .

1. Para habilitar la selección de afinidad en las listas desplegables, debe añadir los nombres de afinidad en la enumeración **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Las enumeraciones se detallan en [este documento](../../platform/using/managing-enumerations.md).

   A continuación, puede seleccionar la afinidad que desea utilizar, como se muestra a continuación para las tipologías:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >También puede consultar [Configuración del servidor de envío](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Temas relacionados**
* [Configuraciones técnicas de correo electrónico](email-deliverability.md)
* [Uso de servidores MX con Campaign](using-mx-servers.md)
* [Configuración del CCO del correo electrónico](email-archiving.md)
