---
title: Privacidad y recomendaciones
seo-title: Privacidad y recomendaciones
description: Privacidad y recomendaciones
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 33bf5c5a08613cf88eaace91b85a76157cac7ba1

---


# Privacidad y recomendaciones{#privacy-and-recommendations}

## Acerca de la privacidad y el consentimiento {#about-privacy-and-consent}

Adobe Campaign es una potente herramienta para recopilar y procesar cantidades extremadamente grandes de datos, incluida información personal. Recomendamos a todos los usuarios de Adobe Campaign trabajar dentro de la legalidad (DPA, CAN-SPAM, Directivas Europeas sobre Privacidad y Comunicaciones electrónicas, GDPR, etc.), hacer un uso responsable y ético de la información personal y abstenerse de enviar correos electrónicos, notificaciones ofensivos y SMS no deseados (“correo no deseado”). Creemos firmemente en los principios del marketing autorizado para fomentar el valor y la lealtad de los clientes y, por lo tanto, prohibimos estrictamente el uso de Adobe Campaign para la entrega de mensajes no solicitados.

Para obtener más información, consulte [Privacidad de Adobe Experience Cloud](https://www.adobe.com/privacy/marketing-cloud.html).

Tómese el tiempo necesario para ver la [Lista de control de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html) y conocer los elementos clave que debe comprobar en materia de seguridad y privacidad.

## Administración de la privacidad {#privacy-management}

El RGPD (Reglamento General de Protección de Datos) es la ley de privacidad de la Unión Europea (UE) que armoniza y moderniza los requisitos de protección de datos. El RGPD se aplica a los clientes de Adobe Campaign que albergan datos de sujetos de datos que residan en la UE.

CCPA (Ley de privacidad del consumidor de California) proporciona a los residentes de California nuevos derechos respecto a su información personal e impone responsabilidades de protección de datos para las entidades que operen en California.

Además de la administración de consentimiento, la configuración de retención de datos y la administración de derechos, proporcionamos, en nuestra función de procesador de datos, capacidades adicionales para ayudarle a facilitar su preparación como controlador de datos para determinadas solicitudes de privacidad.

En este [artículo](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html), conozca cómo Adobe Campaign le ayuda a administrar las distintas funciones clave de privacidad: Derecho de acceso, Derecho a ser olvidado, consentimiento, retención de datos y funciones de usuario. Entérese también de las mejores prácticas recomendadas para ayudarle con el cumplimiento de las normas de privacidad al utilizar el servicio.

## Cookies y funcionalidades de seguimiento {#cookies-and-tracking-capabilities}

Gracias a sus funcionalidades de seguimiento, Adobe Campaign le permite supervisar la navegación de los destinatarios de la entrega en un sitio web. Para ello, Adobe Campaign utiliza cookies de sesión y cookies permanentes.

La Directiva Europea 2009/136/CE sobre &quot;Privacidad y comunicaciones electrónicas&quot; y el Reglamento General de Protección de Datos (GDPR) sostienen que las empresas necesitan el consentimiento de los usuarios de sitios web antes de instalar las cookies. Debe informar a los usuarios de que sus sitios tienen herramientas de seguimiento web a través de una solicitud de autorización (que llega a través de la página, por ejemplo) con una casilla de verificación para autorizar la instalación de cookies o añadir un anuncio en la parte superior de la primera página que naveguen, etc. Las ventanas emergentes se deben evitar debido a que suelen ser bloqueadas por los exploradores.

La configuración del administrador de seguimiento del usuario está disponible para las aplicaciones web y las páginas de destino con un anuncio de exclusión. Consulte [esta página](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign utiliza dos tipos de cookies:

1. Una cookie de sesión (nlid): contiene el identificador del correo electrónico enviado al contacto (broadlogId) y el identificador de la plantilla de mensaje (deliveryId). Se añade cuando el contacto hace clic en una dirección URL incluida en un correo electrónico enviado por Adobe Campaign y le permite hacer un seguimiento de su comportamiento en la web. Esta cookie de sesión se borra automáticamente cuando se cierra el explorador. El contacto puede configurar el explorador para que rechace las cookies.
1. Una cookie permanente (uuid230): permite identificar a los usuarios que interactúan con Adobe Campaign cuando visitan un sitio web. Adobe Campaign utiliza estas cookies para contar el número de clics y estimar la tasa de conversión durante una campaña de marketing. Se coloca cuando el contacto hace clic en un correo electrónico, rellena un formulario en Adobe Campaign o durante la llamada al motor de Inbound Interaction. El usuario puede configurar el navegador para eliminarlo o rechazarlo.

## Integridad de la base de datos {#database-integrity}

Adobe Campaign tiene una amplia variedad de funcionalidades. Por lo tanto, utiliza una estructura de base de datos compleja. La base de datos contiene muchas tablas, campos, vínculos e índices. Algunas tablas intermedias no se muestran en la interfaz. El software crea, elimina o modifica automáticamente ciertos vínculos, campos e índices. Solo las interfaces de Adobe Campaign (interfaz gráfica, programa de importación, módulo de servidor, módulo web, servidores de envío, añadir campo, extensión de base de datos, etc.) pueden modificar el contenido de la base de datos preservando a la vez su integridad.

**Nunca modifique el contenido o la estructura de la base de datos con ninguna otra herramienta que no sea este software**. Estas modificaciones probablemente podrían dañar la base de datos, lo que da como resultado una modificación accidental o pérdida de vínculos, creación de registros o vínculos fantasmas, mensajes de error graves, etc., y dejando sin efecto la garantía y el contrato de asistencia técnica de Adobe Campaign.

En el sistema de Adobe Campaign, toda la información se almacena en la base de datos. La correcta operación del sistema de Adobe Campaign depende de la disponibilidad de estos datos para: módulos web para suscripciones, administración y bajas, pantallas de administración, colas de entrega, mecanismos de optimización de entregas, etc.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign incluye Apache Tomcat, desarrollado por Apache Software Foundation ([https://www.apache.org/](https://www.apache.org/)).
