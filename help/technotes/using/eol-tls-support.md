---
product: campaign
title: Finalización del servicio de soporte para TLS 1.0 y 1.1
description: Finalización del servicio de soporte para TLS 1.0 y 1.1
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: ee7c85f94fc03f6cfca8da11ddea5ebd32d0b2b4
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# Finalización del servicio de soporte para TLS 1.0 y 1.1{#eol-tls-support}

![](../../assets/v7-only.svg)

Adobe ya no es compatible con sistemas de usuarios y sistemas cliente que no son compatibles con el protocolo Transport Layer Security (TLS) 1.2. Si continúa utilizando versiones anteriores de TLS, podría perder el acceso a todos los productos y servicios de Adobe.

## ¿Por qué veo esta página?

Si ve el siguiente mensaje: **Esta página no se puede mostrar**, esto significa que las aplicaciones de Adobe, la página web o el servicio al que intenta acceder requieren una conexión de red más segura con su navegador web, sistema operativo o aplicación. Es obligatorio usar **TLS 1.2** para la comunicación de red segura y el intercambio de datos entre los sistemas de los usuarios y las aplicaciones de Adobe y los servicios web.

Adobe tiene compatibilidad obsoleta con versiones inferiores de TLS (incluidos TLS 1.0 y 1.1). Para obtener información técnica sobre el protocolo TLS 1.2, consulte [Preguntas frecuentes](#faq).

## ¿Qué puedo hacer para reanudar el servicio?

Los navegadores web modernos admiten TLS 1.2. Al actualizar el navegador, podrá acceder a estas aplicaciones y servicios.

Puede descargar e instalar uno de los siguientes exploradores populares:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Si utiliza otro explorador, asegúrese de que sea compatible con TLS 1.2.

Los marcos de aplicaciones y sistemas operativos también deben admitir TLS 1.2. Si la actualización del explorador no resuelve el problema, asegúrese de que el equipo cumpla los requisitos del sistema enumerados en [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

## Preguntas frecuentes{#faq}

* **¿Qué es Seguridad de capa de transporte (TLS)?**

   [Seguridad de la capa de transporte](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) es un protocolo de seguridad que proporciona privacidad e integridad de datos entre dos aplicaciones de comunicación. Se implementa ampliamente para exploradores web y otras aplicaciones que requieren que los datos se intercambien de forma segura a través de una red.

   Según la especificación del protocolo, TLS incluye dos capas, el protocolo de registro TLS y el protocolo de enlace TLS. El protocolo Record proporciona seguridad de conexión. El protocolo de protocolo de enlace permite que el servidor y el cliente se autentiquen mutuamente y negocien algoritmos de codificación y claves criptográficas antes del intercambio de datos.

* **¿Cuáles son las consecuencias?**

   Los estándares de cumplimiento de seguridad de Adobe requieren la desaprobación de protocolos más antiguos a partir de mayo de 2018 y exigen el uso de TLS 1.2 como versión actualizada. Si su sistema no es compatible con TLS 1.2, el acceso a algunas aplicaciones y servicios de Adobe está restringido.

* **¿Cómo le afecta TLS?**

   Solo puede interactuar con algunas aplicaciones y servicios de Adobe a través de una conexión de red segura. TLS ayuda a garantizar que la conexión entre su explorador y estas aplicaciones y servicios web sea segura y fiable.

   A medida que se lanzan nuevos exploradores y sistemas operativos, los estándares de seguridad se actualizan para garantizar niveles más altos de privacidad e integridad de los datos. Sin embargo, las versiones anteriores de estos navegadores o sistemas operativos no se actualizan para incluir los estándares más recientes.

   A medida que aumenta el nivel aceptable de seguridad, estas versiones y aplicaciones de navegador antiguas y menos seguras se quedan atrás.

   Para poder conectarse con sitios seguros, actualice el sistema operativo y las versiones del explorador.

* **¿TLS es vulnerable a los hackers?**

   Se han documentado ataques contra TLS 1.0 usando un método de codificación anterior y las versiones anteriores son más vulnerables que TLS 1.2. Para obtener más información, consulte Ataques contra TLS/SSL.

* **¿Por qué Adobe desactiva la compatibilidad con TLS 1.0 y 1.1?**

   Adobe tiene estándares de seguridad que requieren deshabilitar la compatibilidad con protocolos más antiguos. Uno de estos estándares garantiza el cumplimiento de la Industria de Tarjetas de Pago (PCI). El servidor de adaptación PCI es un conjunto de estándares de seguridad que requieren que las organizaciones acepten, procesen, almacenen o transmitan información de tarjetas de crédito para mantener un entorno seguro.

   El cumplimiento de PCI exige el uso de TLS 1.1 o superior a partir de mayo de 2018.

* **¿Por qué el Adobe impone el uso de TLS 1.2 en lugar de permitir TLS 1.1 o TLS 1.0?**

   La mayoría de las solicitudes de aplicaciones de Adobe y servicios web se originan en sistemas de usuario compatibles con TLS 1.2, con poco tráfico de sistemas TLS 1.1.

   Adobe ha migrado a TLS 1.2, por lo que se accede a sus aplicaciones y servicios web de forma más segura.

* **¿Cuál es la última fecha en que puedo utilizar una versión anterior de TLS?**

   Adobe anima a los usuarios a abandonar rápidamente las versiones anteriores para evitar estar expuestos a vulnerabilidades de seguridad. Para obtener más información, póngase en contacto con el Servicio de atención al cliente de Adobe o con su gestor de éxito de clientes.

* **¿Qué mensaje de error aparece si utilizo un explorador que no está configurado para TLS 1.2?**

   Depende del explorador que esté usando. Todos los navegadores mencionados en [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md) están configuradas para utilizar TLS 1.2. Si utiliza un explorador o una versión que no aparezca en la lista, actualice el explorador.

   Adobe no controla los mensajes de error generados por la capa de comunicaciones SSL. El navegador genera estos mensajes antes de conectarse a las aplicaciones y servicios de Adobe. Este es un ejemplo de error que se puede producir con Internet Explorer 11 en Windows 7:

   ![](assets/do-not-translate/page-not-displayed.png)

   TLS 1.2 está habilitado en Internet Explorer 11 de forma predeterminada, pero si está desactivado, puede activarlo. En este caso, active TLS 1.2 desde el cuadro de diálogo de configuración avanzada en lugar de utilizar otras opciones. También se pueden producir otros errores, como los siguientes:

   * No se puede conectar al servicio
   * Servicio no disponible
   * Error en la conexión
