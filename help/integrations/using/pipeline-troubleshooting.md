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
source-wordcount: '650'
ht-degree: 2%

---


# Solución de problemas de tubería {#pipeline-troubleshooting}

**Se produce un error con el error &quot;Ninguna tarea corresponde a la máscara canalizada@&quot;**

La versión de Adobe Campaign Classic no admite la canalización.

1. Compruebe si el elemento canalizado está presente en el archivo de configuración. Si no, significa que no es compatible.
1. Actualice a la versión 6.11 build 8705 o posterior.

**Falla con &#39;&#39; aurait du y el marcador par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&quot;**

La opción **NmsPipeline_Config** no está establecida. En realidad es un error de análisis de JSON.
Establezca la configuración JSON en la opción **NmsPipeline_Config**. Consulte &quot;Opción de enrutamiento&quot; en esta página.

**La secuencia falla con &quot;el sujeto debe ser una organización o cliente válido&quot;**

La configuración de IMSOrgid no es válida.

1. Compruebe que IMSOrgId está establecido en serverConf.xml.
1. Busque un IMSOrgId vacío en el archivo de configuración de instancia que pueda anular el valor predeterminado. Si es así, elimínelo.
1. Compruebe que IMSOrgId coincide con el cliente del Experience Cloud.

**Error en la canalización con &quot;clave no válida&quot;**

El parámetro @authPrivateKey del archivo de configuración de instancia es incorrecto.

1. Compruebe que se ha establecido authPrivateKey.
1. Compruebe que authPrivateKey: inicios con @, termina con = y tiene una longitud de aproximadamente 4000 caracteres.
1. Busque la clave original y verifique que: en formato RSA, 4096 bits de longitud y inicios con —BEGIN RSA PRIVATE KEY—.
   <br> Si es necesario, vuelva a crear la clave y regístrela en Adobe Analytics. Consulte esta [sección](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Compruebe que la clave se haya codificado en la misma instancia que la canalizada. <br>Si es necesario, rehaga la codificación utilizando el JavaScript o el flujo de trabajo de ejemplo.

**Error al canalizar con &quot;no se puede leer el token durante la autenticación&quot;**

La clave privada tiene un formato no válido.

1. Ejecute los pasos para el cifrado de claves en esta página.
1. Compruebe que la clave está cifrada en la misma instancia.
1. Compruebe que la authPrivateKey del archivo de configuración coincide con la clave generada. <br>Asegúrese de utilizar OpenSSL para generar el par de claves. PuttyGen, por ejemplo, no genera el formato adecuado.

**No se recuperan activadores**

Cuando el proceso canalizado se está ejecutando y no se recuperan activadores:

1. Asegúrese de que el activador está activo en Analytics y está generando eventos.
1. Asegúrese de que el proceso canalizado se está ejecutando.
1. Busque errores en el registro canalizado.
1. Busque errores en la página de estado de canalización. activador-descartado, activador-fracasos debe ser cero.
1. Compruebe que el nombre del activador esté configurado en la **[!UICONTROL NmsPipeline_Config]** opción. Si hay alguna duda, utilice la opción comodín.
1. Compruebe que Analytics tiene un activador activo y está generando eventos. Podría haber un retraso de unas horas después de realizar la configuración en Analytics antes de que esté activa.

**Los Eventos no están vinculados a un cliente**

Cuando algunos eventos no están vinculados a un cliente:

1. Compruebe que el flujo de trabajo de reconciliación se esté ejecutando, si corresponde.
1. Compruebe que el evento contiene un ID de cliente.
1. Realice una consulta en la tabla del cliente con el ID del cliente.
1. Compruebe la frecuencia de la importación del cliente. Los nuevos clientes se importan en Adobe Campaign con un flujo de trabajo.

**Latencia en el procesamiento de eventos**

Cuando la marca de tiempo de Analytics es mucho más antigua que la fecha de creación del evento en Campaña.

Generalmente, un activador puede tardar entre 15 y 90 minutos en iniciar una campaña de marketing. Esto varía según la implementación de la recopilación de datos, la carga en la canalización, la configuración personalizada del activador definido y el flujo de trabajo en Adobe Campaign.

1. Compruebe si el proceso canalizado se ha estado ejecutando.
1. Busque errores en pipelned.log que puedan causar reintentos. Corrija los errores, si corresponde.
1. Compruebe el tamaño de la cola en la página de estado de canalización. Si el tamaño de la cola es grande, mejore el rendimiento del JS.
1. Dado que un retraso parece aumentar con el volumen, configure los activadores en Analytics con menos mensajes.
Anexos

**Cómo utilizar el JavaScript de cifrado de claves**

Ejecute un JavaScript para cifrar la clave privada. Es necesario para la configuración de la canalización.

Este es un ejemplo de código que puede utilizar para ejecutar la función cryptString:

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

En el servidor, ejecute el Javascript:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Copie y pegue la clave codificada de la salida en la consola.