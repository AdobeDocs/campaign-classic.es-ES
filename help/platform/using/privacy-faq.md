---
solution: Campaign Classic
product: campaign
title: Privacidad y consentimiento
description: Más información sobre Privacidad y consentimiento
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: ht
source-wordcount: '797'
ht-degree: 100%

---


# Preguntas más frecuentes sobre Privacidad {#privacy-faq}

Estas son algunas de las preguntas más frecuentes sobre Privacidad y consentimiento al usar Adobe Campaign.

## Términos clave {#key-terms}

### ¿Cuáles son los términos clave sobre la privacidad?

Los elementos que se enumeran a continuación vinculan los términos y conceptos clave relacionados con la privacidad y el consentimiento en Adobe Campaign:

* [Regulaciones sobre administración de la privacidad](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Datos personales y personas](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Consulte Derecho de acceso y Derecho a ser olvidado](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consentimiento, retención y funciones](../../platform/using/privacy-management.md#consent-retention-roles)

## Preparación de las regulaciones de privacidad {#privacy-regulations-readiness}

### ¿Cuál es la sugerencia de Adobe Campaign para cumplir con las regulaciones de privacidad más recientes?

Adobe no proporciona asesoramiento legal. Debe trabajar con su propio asesor legal para asegurarse de que está tomando todas las medidas necesarias para cumplir con las normas de privacidad RGPD, CCPA, PDPA, LGPD o cualquier otra norma legal aplicable.

**Preparación para las solicitudes de acceso a datos y eliminación**

* Identifique el proceso para recibir/responder a las solicitudes del sujeto de datos, incluido el nombramiento de un punto de contacto de privacidad.

* Revise los distintos datos de cliente almacenados en Adobe Campaign y determine identificadores únicos (probablemente habrá más de uno).

* Determine la directiva de validación/autenticación y el proceso para la confirmación de identidad del sujeto de datos.

* Asegúrese de que la respuesta del sujeto de datos sea fácil de entender.

**Consideración del consentimiento**

* Enumere y actualice según sea necesario, todos los puntos de contacto para la captura de datos del RGPD (es decir, considere el idioma, el mecanismo para el consentimiento y los registros de consentimientos).

* Asegúrese de que todos los correos electrónicos de marketing incluyan los vínculos de cancelación de suscripción.

* Evalúe la estrategia global de marketing por correo electrónico para determinar las implementaciones específicas de cada ubicación geográfica.

**Comprensión de los datos**

* Revise todos los orígenes de captura e importación de datos en las que los datos fluyen a Adobe Campaign y documente los campos que se utilizan para las actividades de marketing.

* Quite los atributos de datos que no se utilicen de la base de datos de Adobe Campaign.

* Utilice los datos disponibles en Adobe Campaign para comprobar la calidad de la captura y ofrecer a sus destinatarios experiencias más personalizadas.

* Revise y actualice los permisos de acceso a los datos para garantizar que los usuarios de Adobe Campaign puedan aprovechar por completo solo los datos necesarios para ejecutar sus campañas, pero no acceder a ningún dato aparte de esto.

* Asegúrese de que cada usuario de Adobe Campaign tenga los derechos de acceso adecuados para realizar las tareas necesarias, pero no tenga ningún otro derecho para realizar tareas adicionales.

## Mantenimiento de la participación del usuario {#preserve-user-engagement}

### ¿Cómo pueden obtener consentimiento los controladores de datos con un impacto mínimo en la participación del usuario?

En los casos en que se necesite el consentimiento para determinadas actividades de marketing, el consentimiento del consumidor deberá estar activo (es decir, no habrá silencio como casillas de verificación o de aprobación), no agrupado y puede no estar condicionado a la oferta de los servicios.

Puede incluso haber casos en los que sea necesario actualizar ciertos consentimientos para poder seguir utilizando datos a partir de ahora.

Los especialistas en marketing deben adoptar estos requisitos de consentimiento mejorados como un verdadero indicador de la implicación y lealtad con la marca, así como de la satisfacción y la confianza de los clientes.

## Administración del consentimiento {#manage-consent}

### ¿Cómo pueden los controladores de datos administrar el consentimiento en Adobe Campaign?

Adobe Campaign ya ofrece capacidades para administrar el consentimiento en más niveles que la mayoría de los expertos en marketing mediante campos de datos personalizados o a través de uno o más servicios.

Los expertos en marketing deben consultar con el asesor legal para obtener instrucciones sobre cómo proceder y luego aprovechar las capacidades ya integradas en Adobe Campaign.

Por ejemplo: ampliar el modelo de datos en Adobe Campaign para rastrear no solo si las personas han elegido participar, sino también la marca de tiempo de la inclusión y algún tipo de indicador que capture el ámbito preciso del consentimiento.

## Eliminación de datos {#data-deletion}

### ¿Qué datos pueden eliminar los controladores de datos en Adobe Campaign en respuesta a una solicitud del cliente de un sujeto de datos?

Se eliminarán todos los datos asociados al sujeto de datos, incluidas las tablas predeterminadas y las personalizadas.

Técnicamente, se eliminarán todos los datos vinculados al sujeto de datos con `integrity="own"` .

Como controlador de datos, tiene la opción de personalizarlos cambiando la integridad de los vínculos definidos en los esquemas de datos (por ejemplo, si tiene una justificación comercial para no eliminar determinados datos).

### ¿En qué afecta a los informes cuando se eliminan entregas y registros de seguimiento?

Los informes de Adobe Campaign se basan en indicadores calculados a partir de los datos agregados de entregas y registros de seguimiento. Como resultado, la eliminación de los registros individuales no debería afectar a las métricas de los informes.

## Volver a importar datos {#re-import-data}

### ¿Debo tener en cuenta la posibilidad de volver a importar los datos más adelante?

A menudo en Adobe Campaign, el registro se carga desde una fuente de datos externos.

Como controlador de datos, deberá asegurarse de que cuando reciba una solicitud de eliminación, elimine todos los datos necesarios sobre el sujeto de datos de todos los sistemas.

## Volver a adherirse {#opt-in-again}

### ¿Puede un sujeto de datos, cuyos datos se han borrado de Adobe Campaign, adherirse nuevamente más adelante?

Es posible que un sujeto de datos vuelva a incluirse o se añada como un nuevo destinatario después de que sus datos se hayan borrado de Adobe Campaign.

Puede utilizar la pista de auditoría que detalla cuándo se realizó la eliminación anterior y cuándo se creó el nuevo destinatario.