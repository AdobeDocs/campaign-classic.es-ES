---
solution: Campaign Classic
product: campaign
title: Administración de la privacidad
description: Descubra más información sobre la administración de la privacidad
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: 8ff5450cc35153e61048c2671f6d52fbc5ffc5b9
workflow-type: ht
source-wordcount: '891'
ht-degree: 100%

---


# Administración de la privacidad {#privacy-management}

Adobe Campaign ofrece un conjunto de herramientas para que cumpla con las [normas de privacidad](#privacy-management-regulations) (incluye el RGPD, la CCPA, la PDPA y la LGPD).

Estas son las cinco funcionalidades principales que ofrece Adobe Campaign para garantizar la preparación del RGPD y otras normas de privacidad:

![](assets/privacy-gdpr-use-cases.png)

* **Derecho al acceso**

* **Derecho a eliminar**

Para más información, vea [Derecho al acceso y Derecho a ser olvidado](#right-access-forgotten).

* **Administración de consentimientos**

* **Retención de datos**

* **Administración de derechos**

Para obtener más información, consulte [Consentimiento, retención y funciones](#consent-retention-roles).

<!--This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.-->

## Regulaciones sobre administración de la privacidad {#privacy-management-regulations}

Las capacidades de Adobe Campaign le ayudan a cumplir con las siguientes regulaciones:

* **El RGPD (** reglamento general de protección de datos[](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)) es la ley de privacidad de la Unión Europea (UE) que armoniza y moderniza los requisitos de protección de datos de los países de la UE.
* **La CCPA** ([Ley de Privacidad del Consumidor de California](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=)) proporciona a los residentes de California nuevos derechos respecto a su información personal e impone responsabilidades de protección de datos para las entidades que operen en California.
* **La PDPA** ([Ley de Protección de Datos Personales)](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) es la nueva ley de privacidad que armoniza y moderniza los requisitos de protección de datos para Tailandia.
* **La LGPD** ([ley general de protección de datos](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)) entrará en vigor a principios de 2021 para todas las compañías que recopilen o procesen datos personales en Brasil.

Todas estas normativas se aplican a los clientes de Adobe Campaign que poseen datos de sujetos de datos residentes en las regiones o países respectivos antes mencionados (UE, California, Tailandia y Brasil).

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Para obtener más información sobre los datos personales y las distintas entidades que administran los datos (controlador de datos, procesador de datos y sujeto de datos), consulte [Datos personales y personas](../../platform/using/privacy-and-recommendations.md#personal-data).

## Consulte Derecho de acceso y Derecho a ser olvidado{#right-access-forgotten}

Para ayudarle a facilitar su preparación para la privacidad, Adobe Campaign le permite gestionar solicitudes de **acceso** y **eliminación** .

* El **Derecho al acceso** es el derecho que posee el sujeto de datos a obtener la confirmación por parte del controlador de datos de si se están procesando o no datos relacionados con su persona, dónde y con qué propósito. El controlador de datos proporciona una copia de los datos personales de forma gratuita y en formato electrónico.

* El **Derecho a ser olvidado** (solicitud de eliminación, también conocido como eliminación de datos) otorga al sujeto de datos el derecho a que el controlador de datos borre sus datos personales, interrumpa la diseminación de los datos y la posibilidad de que terceros interrumpan el procesamiento de los datos.

Para obtener información sobre cómo crear solicitudes de **acceso** y **eliminación**, y saber cómo las procesa Adobe Campaign, consulte los pasos de [implementación](../../platform/using/privacy-requests.md).

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## Consentimiento, retención y funciones {#consent-retention-roles}

Además de las capacidades más recientes de **Derecho de acceso** y **Derecho al olvido** , Adobe Campaign oferta otras características importantes que son esenciales para la privacidad:

* [Gestión](#consent-management)de consentimiento: Funcionalidad de suscripción para la administración de preferencias
* [Retención](#data-retention)de datos: períodos de retención de datos en todas las tablas de registro estándar, se pueden configurar períodos de retención adicionales con flujos de trabajo
* [Gestión de derechos](#rights-management): acceso a los datos administrado mediante el derecho asignado 

### Gestión de consentimiento {#consent-management}

El consentimiento implica la aceptación por parte del sujeto de datos del procesamiento de los datos personales relacionados con un sujeto de datos. La obtención del consentimiento necesario para ese procesamiento es responsabilidad del controlador de datos. Aunque Adobe Campaign puede proporcionar algunas funciones para ayudar a un cliente a administrar el consentimiento relacionado con el servicio, Adobe no es responsable del consentimiento. Los clientes deben trabajar con sus propios departamentos legales para determinar sus propios procesos y prácticas para cualquier consentimiento necesario.

Las funciones que ayudan a administrar algunos aspectos del consentimiento han sido fundamentales para Adobe Campaign desde el principio. A través del proceso de administración de suscripciones, los clientes pueden rastrear qué destinatarios han elegido qué tipo de suscripciones, ya sean newsletters, promociones diarias o semanales, o cualquier otro tipo de programa de marketing.

![](assets/privacy-consent-management.png)

Para obtener más información sobre la administración de consentimientos, consulte la [documentación detallada](../../delivery/using/managing-subscriptions.md).

Además de las herramientas de administración de consentimientos proporcionadas por Adobe Campaign, puede realizar un seguimiento si el consumidor se ha excluido de la venta de Información personal. Consulte [esta sección](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

### Retención de datos {#data-retention}

Independientemente de la retención, las tablas de registro predeterminadas de Campaign tienen períodos de retención predefinidos, que generalmente limitan el almacenamiento de datos a seis meses o menos.

A continuación se muestran los valores de retención predeterminados para las tablas predeterminadas. Tenga en cuenta que los administradores técnicos de Adobe configuran los ajustes de retención durante la implementación y los valores pueden variar en función de los requisitos de los clientes.

* **Seguimiento consolidado**: 1 año
* **Registros de envío**: 6 meses
* **Registros de seguimiento**: 1 año
* **Envíos eliminados**: 1 semana
* **Importar rechazos**: 6 meses
* **Perfiles de visitante**: 1 mes
* **Propuestas de oferta**: 1 año
* **Eventos**: 1 mes
* **Estadísticas del procesamiento de eventos**: 1 año
* **Eventos archivados**: 1 año
* **Eventos de canalización ignorados**: 1 mes

Y, de manera similar a eliminar, utilizando la funcionalidad estándar de flujo de trabajo, es posible configurar períodos de retención para cualquier tabla personalizada.

Póngase en contacto con los consultores o administradores técnicos de Adobe para obtener más información sobre la retención o si necesita configurar la retención para tablas personalizadas.

### Gestión de derechos {#rights-management}

Adobe Campaign permite administrar los derechos asignados a los distintos operadores de campaña a través de diferentes funciones creadas previamente o personalizadas.

Una ventaja es que permite administrar que empleados dentro de su empresa pueden acceder a distintos tipos de datos. Por ejemplo, puede tener diferentes especialistas en marketing que abarquen los distintos geos y que cada especialista en marketing solo pueda acceder a los datos de su público.

De igual modo, esta funcionalidad también le permite configurar diferentes capacidades para cada usuario, como limitar quién puede enviar envíos, o más relevancia en el caso de la administración de privacidad, que se pueden modificar o exportar datos.

![](assets/privacy-user-management.png)

Para obtener más información sobre la administración de acceso, consulte la [documentación detallada](../../platform/using/access-management.md).