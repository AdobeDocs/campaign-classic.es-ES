---
title: Acerca de la capacidad de entrega en Adobe Campaign Classic
description: Obtenga más información sobre la administración de la capacidad de entrega en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Acerca de la capacidad del envío{#about-deliverability}

Adobe Campaign ofrece un cierto número de herramientas para rastrear el rendimiento de la entrega de su plataforma. Esta sección también resalta los principios principales que debe tener en cuenta al administrar y optimizar la capacidad de entrega.

## Configuración {#configuration}

Esta función está disponible a través de un paquete dedicado en Adobe Campaign. Para utilizarlo, este paquete debe estar instalado. Una vez finalizado, reinicie el servidor para que el paquete se tenga en cuenta.
* Para los clientes alojados e híbridos, el servicio de asistencia técnica y los consultores de Adobe configuran la supervisión **de la** entrega en su instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

* Para las instalaciones in situ, debe instalar el **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paquete a través del menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Para obtener más información sobre esto, consulte [Instalación de paquetes](../../installation/using/installing-campaign-standard-packages.md)estándar de Campaign Classic.

En Adobe Campaign Classic, la supervisión **de la** entrega se gestiona mediante el **[!UICONTROL Refresh for deliverability]** flujo de trabajo. Se instala de forma predeterminada en todas las instancias y le permite inicializar la lista de reglas de calificación de correo de devolución, la lista de dominios y la lista de MX. Una vez instalado el **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paquete, este flujo de trabajo se ejecuta todas las noches para actualizar regularmente la lista de reglas y le permite administrar de forma activa la capacidad de entrega de la plataforma.

## Contexto {#background}

La capacidad de envío de correo electrónico presenta un desafío importante para los especialistas en marketing, independientemente de si están enviando unos pocos miles de mensajes o varios miles de millones. Uno de cada cinco mensajes nunca llega a la bandeja de entrada o al destinatario deseado.

Cuando se clasifica como “problema técnico” para el departamento de informática, la capacidad de envío de correo electrónico sigue siendo mayor en el programa de marketing. Esto se debe a que los especialistas en marketing más experimentados reconocen que aunque muchos de sus elementos son de naturaleza técnica, la capacidad de envío es en última instancia un problema de negocio con importantes implicaciones en los ingresos.

Tenga en cuenta el embudo de los correos electrónicos de marketing. La capacidad de envío determina el número de mensajes recibidos, lo que a su vez afecta cada fase subsiguiente del canal. Menos correos electrónicos recibidos supone menos aperturas, menos clics y menos conversiones. **Para las empresas con una gran base de datos, la diferencia entre una capacidad de envío media y alta podría significar literalmente entre cientos de miles y millones de dólares en ingresos.**

![](assets/deliverability_overview_1.png)

Al conformarse con una capacidad de envío media (80 %), los especialistas en marketing se están perdiendo la oportunidad de aprovechar una cantidad importante de conversiones (y de dinero).

¿Qué es exactamente la capacidad de envío de correo electrónico? ¿Y cómo pueden los vendedores mejorar los porcentajes de envío para ensanchar la parte ancha del embudo y mejorar los resultados de sus campañas de correo electrónico?

La capacidad de envío de correo electrónico hace referencia al conjunto de características que determinan la capacidad de un mensaje para llegar a su destino a través de una dirección de correo electrónico personal, en poco tiempo y con la calidad esperada en términos de contenido y formato. Estas características se dividen en cuatro categorías principales: calidad de datos, mensaje y contenido, infraestructura de envío y reputación. Juntas forman la base del éxito de un programa de envío de correo electrónico. Esta información general describe los cuatro fundamentos del éxito del envío de correos electrónicos y ofrece recomendaciones para llegar a la bandeja de entrada e impulsar unos mayores ingresos de los programas de marketing por correo electrónico.

![](assets/deliverability_overview_2.png)
