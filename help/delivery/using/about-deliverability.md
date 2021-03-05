---
solution: Campaign Classic
product: campaign
title: Acerca de la capacidad de envío en Campaign
description: Conozca las prácticas recomendadas sobre la capacidad de entrega
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 95%

---


# Acerca de la capacidad de la entrega{#about-deliverability}

**La capacidad de entrega consiste en medir el éxito de las campañas que llegan a la bandeja de entrada de los destinatarios sin rebotar o marcadas como correo no deseado.**

Adobe Campaign ofrece herramientas para hacer un seguimiento de la capacidad de envío de su plataforma. Esta sección también resalta los principios principales que debe tener en cuenta al administrar y optimizar la capacidad de entrega.

## Configuración {#configuration}

Esta función está disponible a través de un paquete dedicado en Adobe Campaign. Para utilizarlo, este paquete debe estar instalado. Una vez finalizado, reinicie el servidor para que el paquete se tenga en cuenta.
* Para los clientes alojados e híbridos, el servicio de asistencia técnica y los consultores de Adobe configuran la **supervisión de la entrega** en su instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

* Para las instalaciones on-premise, debe instalar el **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paquete a través del **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menú. Para obtener más información, consulte [Instalación de paquetes integrados de Campaign](../../installation/using/installing-campaign-standard-packages.md).

En Adobe Campaign, **Deliverability monitoring** se administra mediante el flujo de trabajo **[!UICONTROL Refresh for deliverability]**. El flujo de trabajo se instala de manera predeterminada en todas las instancias y le permite inicializar la lista de reglas de cualificación de correos rechazados, la lista de dominios y la lista de MX. Una vez que se ha instalado el paquete **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, este flujo de trabajo se ejecuta todas las noches para actualizar regularmente la lista de reglas y permite administrar de forma activa la capacidad de envío de la plataforma.

## Contexto {#background}

La capacidad de envío de correo electrónico presenta un desafío importante para los especialistas en marketing, independientemente de si están enviando unos pocos miles de mensajes o varios miles de millones. Uno de cada cinco mensajes nunca llega a la bandeja de entrada o al destinatario deseado.

Cuando se clasifica como “problema técnico” para el departamento de informática, la capacidad de envío de correo electrónico sigue siendo mayor en el programa de marketing. Esto se debe a que los especialistas en marketing más experimentados reconocen que aunque muchos de sus elementos son de naturaleza técnica, la capacidad de envío es en última instancia un problema de negocio con importantes implicaciones en los ingresos.

Tenga en cuenta el embudo de los correos electrónicos de marketing. La capacidad de envío determina el número de mensajes recibidos, lo que a su vez afecta cada fase subsiguiente del canal. Menos correos electrónicos recibidos supone menos aperturas, menos clics y menos conversiones. **Para las empresas con una gran base de datos, la diferencia entre una capacidad de envío media y alta podría significar literalmente entre cientos de miles y millones de dólares en ingresos.**

![](assets/deliverability_overview_1.png)

Al conformarse con una capacidad de envío media (80 %), los especialistas en marketing se están perdiendo la oportunidad de aprovechar una cantidad importante de conversiones (y de dinero).

¿Qué es exactamente la capacidad de envío de correo electrónico? ¿Y cómo pueden los vendedores mejorar los porcentajes de envío para ensanchar la parte ancha del embudo y mejorar los resultados de sus campañas de correo electrónico?

La capacidad de envío de correo electrónico hace referencia al conjunto de características que determinan la capacidad de un mensaje para llegar a su destino a través de una dirección de correo electrónico personal, en poco tiempo y con la calidad esperada en términos de contenido y formato. Estas características se dividen en cuatro categorías principales: calidad de datos, mensaje y contenido, infraestructura de envío y reputación. Juntas forman la base del éxito de un programa de envío de correo electrónico. Esta información general describe los cuatro fundamentos del éxito de la entrega de correos electrónicos y ofrece recomendaciones para llegar a la bandeja de entrada e impulsar unos mayores ingresos de los programas de marketing por correo electrónico.

<!--![](assets/deliverability_overview_2.png)-->
