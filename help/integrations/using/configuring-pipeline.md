---
title: Configuración de la integración
seo-title: Configuración de la integración
description: Configuración de la integración
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---


# Configuración de canalización {#configuring-pipeline}

Los parámetros de autenticación como el ID de cliente, la clave privada y el extremo de autenticación se configuran en los archivos de configuración de instancia.
La lista de activadores que se van a procesar se configura en una opción. Está en formato JSON.
El activador se procesa inmediatamente con el código Javascript. Se guarda en una tabla de base de datos sin ningún otro procesamiento en tiempo real.
Los activadores se utilizan para la segmentación mediante un flujo de trabajo de campaña que envía correos electrónicos. La campaña se configura de modo que un cliente que tenga ambos eventos desencadenadores reciba un correo electrónico.

## Requisitos previos {#prerequisites}

El uso [!DNL Experience Cloud Triggers] en Campaña requiere:

* Adobe Campaign versión 6.11 compilación 8705 o posterior.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select o Standard.

Las configuraciones de requisitos previos son:

* Creación de un archivo de clave privada y luego la creación de la aplicación oAuth registrada con esa clave.
* Configuración de los activadores en Adobe Analytics.

La configuración de Adobe Analytics está fuera del ámbito de este documento.

Adobe Campaign requiere la siguiente información de Adobe Analytics:

* Nombre de la aplicación oAuth.
* El valor de IMSOrgId, identificador del cliente Experience Cloud.
* Nombres de los activadores configurados en Analytics.
* Nombre y formato de los campos de datos que se van a conciliar con la base de datos de Marketing.

Parte de esta configuración es un desarrollo personalizado y requiere lo siguiente:

* Conocimientos prácticos sobre análisis de JSON, XML y Javascript en Adobe Campaign.
* Conocimientos prácticos de las API QueryDef y Writer.
* Nociones de trabajo de cifrado y autenticación mediante claves privadas.

>[!NOTE]
>
>Como la edición del código JS requiere habilidades técnicas, no lo intente sin la comprensión adecuada. <br>Los activadores se guardan en una tabla de base de datos. Por lo tanto, los operadores de marketing pueden utilizar los datos de activación de forma segura en flujos de trabajo de segmentación.

## Archivos de autenticación y configuración {#authentication-configuration}

Se requiere autenticación porque la canalización está alojada en Adobe Experience Cloud.
Si el servidor de Marketing está alojado en la empresa, cuando inicia sesión en Pipeline, debe autenticarse para tener una conexión segura.
Utiliza un par de claves públicas y privadas. Este proceso es la misma función que un usuario/contraseña, solo más seguro.

### IMSOrgId {#imsorgid}

IMSOrgId es el identificador del cliente en Adobe Experience Cloud.
Configúrelo en el archivo serverConf.xml de instancia, bajo el atributo IMSOrgId.
Ejemplo:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Generación de claves {#key-generation}

La clave es un par de archivos. Está en formato RSA y tiene una longitud de 4096 bytes. Se puede generar con una herramienta de código abierto como OpenSSL. Cada vez que se ejecuta la herramienta, se genera una nueva clave de forma aleatoria.
Para mayor comodidad, los pasos se enumeran a continuación:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Ejemplo de archivo private_key.pem:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Ejemplo de archivo public_key.pem:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Las claves no deben ser generadas por PuttyGen, OpenSSL es la mejor opción.

### Creación automática de clientes en Adobe Experience Cloud {#oauth-client-creation}

Es necesario crear una aplicación de tipo JWT iniciando sesión en Adobe Analytics en la cuenta de organización correcta en **[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Legacy Oath application]**.

Siga estos pasos:

1. Seleccione el **[!UICONTROL Service Account (JWT Assertion)]**.
1. Introduzca el **[!UICONTROL Application Name]**.
1. Registre el **[!UICONTROL Public key]**.
1. Seleccione el activador **[!UICONTROL Scopes]**.

   ![](assets/triggers_5.png)

1. Haga clic en **[!UICONTROL Create]** y compruebe el **[!UICONTROL Application ID]** y **[!UICONTROL Application Secret]** creado.

   ![](assets/triggers_6.png)

### Registro del nombre de la aplicación en Adobe Campaign Classic {#application-name-registration}

El ID de aplicación del cliente oAuth creado debe configurarse en Adobe Campaign. Puede hacerlo editando el archivo de configuración de instancia en el elemento canalizado, específicamente el atributo appName.

Ejemplo:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Cifrado clave {#key-encription}

Para ser utilizado por canalizaciones, la clave privada debe estar cifrada. La codificación se realiza mediante la función cryptString Javascript y debe realizarse en la misma instancia que la canalizada.

En esta [página](../../integrations/using/pipeline-troubleshooting.md)hay disponible un ejemplo de cifrado de clave privada con JavaScript.

La clave privada cifrada debe estar registrada en Adobe Campaign. Puede hacerlo editando el archivo de configuración de instancia en el elemento canalizado, específicamente el atributo authPrivateKey.

Ejemplo:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### inicio automático de proceso canalizado {#pipelined-auto-start}

El proceso de tuberías debe iniciarse automáticamente.
Para ello, establezca el elemento en el archivo de configuración en autostart=&quot;true&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Reinicio del proceso canalizado {#pipelined-restart}

También se puede iniciar manualmente mediante la línea de comandos:

```
nlserver start pipelined@instance
```

Se requiere un reinicio para que los cambios surtan efecto:

```
nlserver restart pipelined@instance
```

En caso de errores, busque errores en la salida estándar (si ha empezado manualmente) o en el archivo de registro canalizado. Consulte la sección Resolución de problemas de este documento para obtener más información sobre la resolución de problemas.

### Opciones de configuración de tuberías {#pipelined-configuration-options}

| Opción | Descripción |
|:-:|:-:|
| appName | ID de la aplicación OAuth (ID de aplicación) registrada en Adobe Analytics (donde se cargó la clave pública): Administración > Administración de usuarios > Aplicación de juramento heredado. Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL para obtener &quot;tokens de puerta de enlace&quot;. <br> Valor predeterminado: https://api.omniture.com |
| authPrivateKey | Clave privada (parte pública cargada en Adobe Analytics (consulte esta sección). AES cifrado con la opción XtkSecretKey: xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Deshabilitar la autenticación (la conexión sin tokens de puerta de enlace solo es aceptada por algunos extremos de canalización de desarrollo) |
| discoverPipelineEndpoint | URL para descubrir el extremo de los servicios de tubería que se va a usar para este inquilino. Valor predeterminado: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | El período entre 2 volcados del estado interno del proceso en var/INSTANCE/pipelined.json estado interno también está disponible a petición en http://INSTANCE/pipelined/status (puerto 7781). |
| forcePipelineEndpoint | Deshabilitar el descubrimiento de PipelineServicesEndpoint y forzarlo |
| monitorServerPort | El proceso canalizado escucha en este puerto para proporcionar el estado interno del proceso en http://INSTANCE/pipelined/status (puerto 7781). |
| punteroFlushMessageCount | Cuando se procesa este número de mensajes, los desplazamientos se guardan en la base de datos. El valor predeterminado es 1000 |
| punteroFlushPeriodSec | Después de este período, los desplazamientos se guardarán en la base de datos. El valor predeterminado es 5 (segundos) |
| processingJSThwords | Número de mensajes de procesamiento de subprocesos dedicados con conectores JS personalizados. El valor predeterminado es 4 |
| processingThwords | Número de mensajes de procesamiento de subprocesos dedicados con código integrado. El valor predeterminado es 4 |
| tryPeriodSec | Retraso entre reintentos (si hay errores de procesamiento). El valor predeterminado es 30 (segundos) |
| reintentarValiditySec | Descartar el mensaje si no se procesa correctamente después de este período (demasiados reintentos). El valor predeterminado es 300 (segundos) |
