---
product: campaign
title: Configuración de envío de campaña
description: Obtenga información sobre cómo configurar las opciones de entrega de Campaign
feature: Installation, Channel Configuration
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 7%

---

# Configuración del envío {#delivery-settings}



Los parámetros de envío deben configurarse en la carpeta **serverConf.xml**.

* **Configuración de DNS**: especifique el dominio de entrega y las direcciones IP (o host) de los servidores DNS utilizados para responder a consultas DNS de tipo MX realizadas por el módulo MTA a partir de **`<dnsconfig>`**.

  >[!NOTE]
  >
  >El parámetro **nameServers** es esencial para una instalación en Windows. Para una instalación en Linux, debe dejarse vacío.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

También puede realizar las siguientes configuraciones según sus necesidades y configuraciones: configurar una [retransmisión SMTP](#smtp-relay), adaptar el número de [procesos secundarios de MTA](#mta-child-processes), [Administrar tráfico SMTP saliente](#managing-outbound-smtp-traffic-with-affinities).

## retransmisión SMTP {#smtp-relay}

El módulo MTA actúa como agente de transferencia de correo nativo para la difusión SMTP (puerto 25).

Sin embargo, es posible reemplazarlo por un servidor de transmisión si la directiva de seguridad lo requiere. En ese caso, el rendimiento global será el de retransmisión (siempre que el rendimiento del servidor de retransmisión sea inferior al de Adobe Campaign).

En este caso, estos parámetros se establecen configurando el servidor SMTP en la sección **`<relay>`**. Debe especificar la dirección IP (o host) del servidor SMTP utilizado para transferir correo y su puerto asociado (25 de forma predeterminada).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Este modo operativo implica serias limitaciones en las entregas, ya que puede reducir en gran medida el rendimiento debido al rendimiento intrínseco del servidor de transmisión (latencia, ancho de banda...). Además, la capacidad para clasificar los errores de envío sincrónico (detectados mediante el análisis del tráfico SMTP) estará limitada y el envío no será posible si el servidor de retransmisión no está disponible.

## Procesos secundarios de MTA {#mta-child-processes}

Es posible controlar el número de procesos secundarios (maxSpareServers de forma predeterminada 2) para optimizar el rendimiento de difusión según la potencia de CPU de los servidores y los recursos de red disponibles. Esta configuración se debe realizar en la sección **`<master>`** de la configuración de MTA en cada equipo individual.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulte también [Optimización de envío de correo electrónico](../../installation/using/email-deliverability.md#email-sending-optimization).

## Administrar el tráfico SMTP saliente con afinidades {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configuración de afinidad debe ser coherente de un servidor a otro. Le recomendamos que se ponga en contacto con el Adobe de para obtener información sobre la configuración de afinidad, ya que los cambios de configuración deben replicarse en todos los servidores de aplicaciones que ejecuten el MTA.

Puede mejorar el tráfico SMTP saliente mediante afinidades con direcciones IP.

Para ello, siga los siguientes pasos:

1. Escriba las afinidades en la sección **`<ipaffinity>`** del archivo **serverConf.xml**.

   Una afinidad puede tener varios nombres diferentes: para separarlos, use el carácter **;**.

   Ejemplo:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Para ver los parámetros relevantes, consulte el archivo **serverConf.xml**.

1. Para habilitar la selección de afinidad en las listas desplegables, debe agregar los nombres de afinidad en la enumeración **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Las enumeraciones se detallan en [este documento](../../platform/using/managing-enumerations.md).

   A continuación, puede seleccionar la afinidad que desea utilizar, como se muestra a continuación para las tipologías:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >También puede consultar [Configuración del servidor de entrega](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Temas relacionados**
* [Configuraciones técnicas de correo electrónico](email-deliverability.md)
* [Uso de servidores MX con Campaign](using-mx-servers.md)
* [Configuración del CCO del correo electrónico](email-archiving.md)
