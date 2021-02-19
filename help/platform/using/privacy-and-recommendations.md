---
solution: Campaign Classic
product: campaign
title: Privacidad y consentimiento
description: Más información sobre Privacidad y consentimiento
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 100%

---


# Privacidad y consentimiento{#privacy-and-recommendations}

## Recomendaciones generales {#general-recommendations}

Adobe Campaign es una potente herramienta para recopilar y procesar cantidades extremadamente grandes de datos, incluida información personal e información confidencial. Por eso, la privacidad debe administrarse cuidadosamente.

* Use la información personal de forma responsable y ética.

* Absténgase de enviar correos electrónicos no solicitados, notificaciones push y mensajes SMS (&quot;spam&quot;). Adobe cree firmemente en los principios del marketing autorizado para fomentar la lealtad y el valor de tiempo de vida del cliente; por lo tanto, Adobe prohíbe estrictamente el uso de Adobe Campaign para la entrega de mensajes no solicitados.

Tómese el tiempo necesario para ver la [Lista de control de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html) y conocer los elementos clave que debe comprobar en materia de seguridad y privacidad.

### Normas de privacidad {#privacy-regulations}

Para gestionar correctamente la privacidad y administrar los datos personales, siga la legislación aplicable a la región o regiones en las que opera. Estas normas incluyen lo siguiente:
* [RGPD](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Reglamento General de Protección de Datos de Europa)
* [DPA](https://www.gov.uk/data-protection) (aplicación del RGPD en el Reino Unido)
* [Directiva europea sobre privacidad y comunicaciones electrónicas](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (ley estadounidense que establece las reglas y requisitos de los correos electrónicos comerciales)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (Ley de Privacidad del Consumidor de California)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Ley de Protección de Datos Personales de Tailandia)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (Ley General de Protección de Datos de Brasil): entrará en vigencia a partir del 16 de agosto de 2020

>[!NOTE]
>
>Para obtener más información sobre cómo se aplican el RGPD, la CCPA, la PDPA y la LGPD a Adobe Campaign, consulte [esta página](../../platform/using/privacy-management.md#privacy-management-regulations).

### Privacidad de Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign forma parte de las soluciones de Adobe Experience Cloud. La forma en que se gestiona la privacidad en Campaign obedece a los principios generales de Experience Cloud, como los siguientes:

* **Información que se recopila al utilizar Adobe Experience Cloud**

   Como compañía que utiliza las soluciones de Adobe Experience Cloud, puede elegir qué información desea recopilar y enviar a su cuenta de Adobe Experience Cloud. Algunos ejemplos de los tipos de información que se pueden recopilar son la actividad de navegación web, las direcciones IP, la información de ubicación de dispositivos móviles, las tasas de éxito de una campaña, los artículos comprados o colocados en el carro de compras, etc.

   >[!NOTE]
   >
   >Al igual que con todos los productos de Adobe, Campaign recopila información sobre los usuarios de la aplicación y del sitio web. Para obtener más información sobre esto, consulte la Política de privacidad de [Adobe](https://www.adobe.com/es/privacy/policy.html).

* **Uso de Adobe Experience Cloud para recopilar información**

   * Las soluciones de Adobe Experience Cloud utilizan cookies y tecnologías similares, como señalizaciones web (también conocidas como etiquetas o píxeles), para permitirle recopilar información. Para obtener más información sobre las cookies y las capacidades de seguimiento con Adobe Campaign, consulte [esta sección](#tracking-capabilities).
   * También puede utilizar las tecnologías de Adobe Experience Cloud en sus aplicaciones móviles. Para obtener más información sobre la entrega de envíos móviles con Campaign, consulte [Canal de SMS](../../delivery/using/sms-channel.md) y[Canal de aplicaciones móviles](../../delivery/using/about-mobile-app-channel.md).

* **Opciones de privacidad de los usuarios sobre el uso de Adobe Experience Cloud**

   Adobe le pide que proporcione políticas de privacidad a sus clientes que describan lo siguiente:

   * Sus prácticas en cuanto a privacidad en relación con Adobe Experience Cloud
   * Cómo pueden los usuarios definir sus preferencias para la recopilación o el uso de su información en conexión con Adobe Experience Cloud

   >[!NOTE]
   >
   >Al igual que con todos los productos de Adobe, los usuarios de Campaign pueden optar por compartir información recopilada sobre ellos a través de aplicaciones y sitios web. Para obtener más información sobre esto, consulte las [Preguntas frecuentes sobre la información de uso de Adobe Experience Cloud](https://www.adobe.com/es/privacy/experience-cloud-usage-info-faq.html).

Para obtener más información sobre la privacidad de Adobe Experience Cloud, consulte [esta página](https://www.adobe.com/es/privacy/marketing-cloud.html).

## Datos personales y personas {#personal-data}

Al administrar la privacidad, es importante definir qué datos deben manejarse con cuidado y quién debe hacerlo.
* Los **datos personales** son información que puede identificar directa o indirectamente a un individuo.
* Los **datos personales confidenciales** son información relacionada con la raza, las opiniones políticas, las creencias religiosas, los antecedentes penales, la información genética, los datos de salud, las preferencias sexuales, la información biométrica, y la afiliación a sindicatos.

Al integrar la Campaign con otras soluciones de Experience Cloud en las que las audiencias se pueden transferir de un sistema a otro, como [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager o el servicio principal de personas](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md)o con otras soluciones a través de [conectores de CRM ](../../platform/using/crm-connectors.md), debe prestar especial atención a la protección de datos personales.

La [legislación principal](#privacy-regulations) hace referencia a las diferentes entidades que administran los datos de la siguiente manera:
* Un **controlador de datos** es una autoridad que determina los medios y el propósito de recopilar, utilizar y compartir datos personales.
* Un **procesador de datos** es cualquier persona o parte que recopila, utiliza o comparte datos personales según lo indicado por el controlador de datos.
* Se entiende por **sujeto de datos** toda persona viva cuyos datos personales se recopilen, utilicen o compartan y que pueda identificarse, directa o indirectamente, por referencia a dichos datos personales.

Por lo tanto, como compañía que recopila y comparte datos personales, usted es el controlador de datos, sus clientes son los sujetos de datos y Adobe Campaign actúa como un procesador de datos al tratar sus datos personales como usted lo indica. Tenga en cuenta que, como controlador de datos, es su responsabilidad gestionar la relación con los temas de datos, como al administrar [solicitudes de privacidad](#privacy-requests).

### Ejemplo de uso {#use-case-scenario}

Para ilustrar cómo interactúan las distintas personas, se muestra un ejemplo de uso de la experiencia del cliente de RGPD de alto nivel.

En este ejemplo, una compañía aérea es el cliente de Adobe Campaign. Esta compañía es el **Controlador de datos** y todos los clientes de la compañía son los **Sujetos de datos**. Laura en este caso particular es cliente de la compañía aérea.

Estas son las distintas personalidades utilizadas en este ejemplo:

* **Laura** es el **Sujeto de datos**. Es el destinatario que recibe los mensajes de la compañía aérea. Laura es una viajera frecuente, pero puede decidir en algún momento que no quiere publicidad personalizada o mensajes de marketing de la compañía aérea. En ese caso le pide a la compañía aérea (según su proceso) que borre su número de viajero frecuente.

* **Anne** es el **Controlador de datos** en la compañía de aerolíneas. Recibe la solicitud de Laura, recupera los ID útiles solicitados para identificar al sujeto de datos y envía la solicitud por Adobe Campaign.

* **Adobe Campaign** es el **procesador de datos**.

![](assets/privacy-gdpr-flow.png)

Este es el flujo general para este ejemplo de uso:

1. El **sujeto de datos** (Laura) envía una solicitud de RGPD al **Controlador de datos** por correo electrónico, atención al cliente o un portal web.

1. El **controlador de datos** (Anne) envía la solicitud de RGPD a Campaign a través de la interfaz o mediante una API.

1. Una vez que el **procesador de datos** (Adobe Campaign) recibe la información, toma medidas para la solicitud del RGPD y envía una respuesta o confirmación al **controlador de datos** (Anne).

1. A continuación, el **controlador de datos** (Anne) revisa la información y la envía de vuelta al **sujeto de datos** (Laura).

## Adquisición de datos {#data-acquisition}

Adobe Campaign le permite recopilar datos, incluida la información personal y confidencial. Por lo tanto, es esencial que reciba y supervise el consentimiento de sus destinatarios.

* Los destinatarios siempre deben aceptar recibir comunicaciones. Para ello, siga atendiendo las solicitudes de exclusión lo más rápido posible y verifique el consentimiento a través de un proceso de doble inclusión. Para obtener más información sobre esto, consulte [Creación de un formulario de suscripción con doble adhesión](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* No importe listas fraudulentas ni utilice direcciones semilla para comprobar que el archivo cliente no se está utilizando de forma fraudulenta. Para obtener más información sobre esto, consulte [Acerca de las direcciones semilla](../../delivery/using/about-seed-addresses.md).
* A través de la administración de derechos y consentimiento, puede rastrear las preferencias de sus destinatarios, así como administrar quién dentro de su organización puede acceder a qué datos. Para obtener más información, consulte [esta sección](#consent).
* Facilite y administre las solicitudes de privacidad de sus destinatarios. Para obtener más información, consulte [esta sección](#privacy-requests).

## Administración de la privacidad {#privacy-management}

La administración de la privacidad se refiere a todos los procesos y herramientas que pueden ayudarle a cumplir con las regulaciones de privacidad (RGPD, CCPA, etc.). Obtenga información general sobre qué es la administración de la privacidad en [esta página](https://helpx.adobe.com/es/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign le ofrece varios conjuntos de funciones dedicadas a la administración de la privacidad:
* administración de consentimiento, retención de datos y funciones de usuario. Consulte [esta sección](#consent).
* Solicitudes de privacidad (derecho de acceso y derecho a ser olvidado). Consulte [esta sección](#privacy-requests).
* Exclusión para la venta de información personal (específica de la CCPA). Consulte [esta sección](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

Las principales funcionalidades de privacidad en Campaign y un ejemplo de las personas implicadas se presentan en [esta sección](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-faq.html?lang=es#getting-started).

### Consentimiento, retención y funciones {#consent}

En principio, Adobe Campaign ofrece funcionalidades importantes que son esenciales para la privacidad:

* **Gestión del consentimiento**: A través del proceso de administración de suscripciones, puede administrar las preferencias de sus destinatarios y rastrear qué destinatarios han elegido qué tipo de suscripciones. Para obtener más información sobre esto, consulte [Acerca de las suscripciones](../../delivery/using/about-services-and-subscriptions.md).
* **Retención de datos**: Todas las tablas de registro estándar incorporadas tienen períodos de retención preestablecidos, lo que generalmente limita su almacenamiento de datos a 6 meses o menos. Se pueden configurar períodos de retención adicionales con flujos de trabajo. Para obtener más información, póngase en contacto con los consultores o administradores técnicos de Adobe.
* **Administración de derechos**: Adobe Campaign permite administrar los derechos asignados a los distintos operadores de campaña a través de diferentes funciones generadas previamente o personalizadas. Esto le permite administrar qué persona de su compañía puede acceder, modificar o exportar diferentes tipos de datos. Para obtener más información sobre esto, consulte [Acerca de la administración de acceso](../../platform/using/access-management.md).

Para obtener más información sobre estas funciones y cómo administrarlas en Adobe Campaign, consulte [esta sección](../../platform/using/privacy-management.md#consent-retention-roles).

### Solicitudes de privacidad {#privacy-requests}

Adobe Campaign proporciona funciones adicionales que le ayudan a facilitar su preparación como controlador de datos para determinadas solicitudes de privacidad:

* El **derecho de acceso** es el derecho del interesado a obtener del controlador de datos la confirmación de si se están procesando o no los datos personales que les conciernen, dónde y por qué.

* El **derecho al olvido** (solicitud de eliminación) autoriza al sujeto de datos a hacer que el controlador de datos borre sus datos personales.

Las solicitudes de **acceso** y **eliminación** se presentan en [esta sección](../../platform/using/privacy-management.md#right-access-forgotten).

Los pasos de implementación para crear estas solicitudes se detallan en [esta sección](../../platform/using/privacy-requests.md).

## Capacidades de seguimiento {#tracking-capabilities}

### Cookies {#cookies}

Gracias a sus funciones de seguimiento, Adobe Campaign le permite rastrear la navegación de sus destinatarios de envío con tres tipos de cookies: una cookie de sesión y dos cookies permanentes.

* Una cookie **de sesión**: la cookie **nlid** contiene el identificador del correo electrónico enviado al contacto (**broadlogId**) y el identificador de la plantilla de mensaje (**deliveryId**). Se añade cuando el contacto hace clic en una dirección URL incluida en un correo electrónico enviado por Adobe Campaign y le permite hacer un seguimiento de su comportamiento en la web. Esta cookie de sesión se borra automáticamente cuando se cierra el explorador. El contacto puede configurar el explorador para que rechace las cookies.

* Dos cookies **permanentes**:
   * La cookie **UUID** (identificador único universal) se comparte entre las soluciones de Adobe Experience Cloud. Se establece una vez hasta que desaparece del explorador del cliente cuando se genera un nuevo valor. Esta cookie le permite identificar a los usuarios que interactúan con las soluciones de Experience Cloud cuando visitan un sitio web. Puede ser depositada por una página de aterrizaje (para asociar actividades de clientes desconocidas a un destinatario) o por un envío. La descripción de esta cookie está disponible en [esta página](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=es#ec-cookies).
   * La cookie **nllastdelid** (presentada en Campaign Classic 20.3) es una cookie permanente que contiene el **deliveryId** del último envío desde el que el usuario hizo clic en el vínculo. Esta cookie se utiliza, cuando falta la cookie de sesión, para identificar la tabla de seguimiento que se utilizará.

Las regulaciones como el reglamento general de protección de datos (RGPD) establecen que las compañías requieren el acuerdo de los usuarios del sitio web antes de instalar las cookies.

* Debe informar a los usuarios de que sus sitios tienen herramientas de seguimiento web a través de una solicitud de autorización (que llega a través de la página, por ejemplo) con una casilla de verificación para autorizar el uso de cookies o añadir un banner en la parte superior de la primera página que naveguen, etc.
* Las ventanas emergentes deben evitarse, ya que los exploradores suelen bloquearlas.

### Seguimiento de mensajes {#message-tracking}

Adobe Campaign le permite rastrear los correos electrónicos enviados y el comportamiento de los destinatarios de envío: abrir, hacer clic en vínculos, cancelar suscripciones, etc. Para obtener más información sobre esto, consulte [Acerca del seguimiento de mensajes](../../delivery/using/about-message-tracking.md).

Para ello, agregue [vínculos de seguimiento](../../delivery/using/how-to-configure-tracked-links.md) a sus mensajes para medir el impacto del comportamiento de envío y destinatario en la pestaña [Seguimiento](../../delivery/using/delivery-dashboard.md#tracking-logs) del panel de envío. El seguimiento de datos se interpreta en el informe [Seguimiento de indicadores](../../reporting/using/delivery-reports.md#tracking-indicators).

### Seguimiento web {#web-tracking}

Adobe Campaign también le permite supervisar la forma en que los destinatarios exploran el sitio web: inserte etiquetas de seguimiento para recopilar información y medir visitas en páginas de aplicaciones web. Para obtener más información sobre esto, consulte [Seguimiento de una aplicación web](../../web/using/tracking-a-web-application.md).

La configuración del seguimiento web se presenta en [esta sección](../../configuration/using/about-web-tracking.md).

Para administrar aún más el seguimiento, Adobe Campaign le permite mostrar un banner de exclusión para detener el seguimiento de los comportamientos web de los usuarios finales que no desean realizar el seguimiento de comportamiento. Para obtener más información sobre esto, consulte [Exclusión del seguimiento de aplicaciones web](../../web/using/web-application-tracking-opt-out.md).
