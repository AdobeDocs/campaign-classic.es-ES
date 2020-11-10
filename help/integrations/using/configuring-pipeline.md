---
title: Configuración de la canalización
description: Obtenga información sobre cómo configurar la canalización
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 2d0d2d4eefc67312e1b9a8edc7ae88def2980ef1
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 20%

---


# Configuración de canalización {#configuring-pipeline}

Los parámetros de autenticación como el ID de cliente, la clave privada y el extremo de autenticación se configuran en los archivos de configuración de instancia.
La lista de activadores que se van a procesar está configurada en una opción en formato JSON.
Los activadores se utilizan para la segmentación mediante un flujo de trabajo de campaña que envía correos electrónicos. La campaña se configura de modo que un cliente que tenga ambos eventos desencadenadores reciba un correo electrónico.

>[!CAUTION]
>
>En caso de implementación híbrida, asegúrese de que la canalización está configurada en una instancia media.

## Requisitos previos {#prerequisites}

Antes de iniciar esta configuración, compruebe que está utilizando:

* Versión mínima de Adobe Campaign 20.3
* Versión de Adobe Analytics Standard

También necesitará:

* Autenticación de proyectos de E/S de Adobe
* un IMSOrgID válido, el identificador del cliente Experience Cloud con Adobe Analytics agregado
* acceso de desarrollador a la organización IMS
* se ha realizado la configuración de activadores en Adobe Analytics

## Archivos de autenticación y configuración {#authentication-configuration}

La autenticación es obligatoria porque la canalización está alojada en el Adobe Experience Cloud.
Utiliza un par de claves públicas y privadas. Este proceso tiene la misma función que un usuario/contraseña, pero es más seguro.
La autenticación es compatible con el Marketing Cloud mediante el proyecto de E/S de Adobe.

## Paso 1: Creación/actualización de un proyecto de E/S de Adobe {#creating-adobe-io-project}

Para los clientes alojados, puede crear un ticket de atención al cliente para permitir a su organización utilizar los tokens de cuenta técnica de E/S de Adobe para la integración de activadores.

Para los clientes locales, consulte la página [Configuración de E/S de Adobe para Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) . Tenga en cuenta que debe seleccionar **[!UICONTROL Adobe Analytics]** al agregar la API a la credencial de E/S de Adobe.

## Paso 2: Configuración de la opción de canalización NmsPipeline_Config {#configuring-nmspipeline}

Una vez configurada la autenticación, la canalización recuperará los eventos. Solo procesará activadores configurados en Adobe Campaign. El activador debe haberse generado desde Adobe Analytics y se debe haber insertado en la canalización, que solo procesará activadores configurados en Adobe Campaign.
La opción también se puede configurar con un comodín para capturar todos los activadores independientemente del nombre.

1. En Adobe Campaign, acceda al menú de opciones en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** en la **[!UICONTROL Explorer]**.

1. Seleccione la opción **[!UICONTROL NmsPipeline_Config]**.

1. En el **[!UICONTROL Value (long text)]** campo, puede pegar el siguiente código JSON, que especifica dos activadores. Debe asegurarse de eliminar los comentarios.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. También puede pegar el siguiente código JSON que captura todos los activadores.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### The Consumer parameter {#consumer-parameter}

La tubería funciona como un proveedor y un modelo de consumidor. Los mensajes se consumen únicamente para un consumidor individual: cada consumidor obtiene su propia copia de los mensajes.

The **Consumer** parameter identifies the instance as one of these consumers. La identidad de la instancia llamará a la canalización. Puede rellenarla con el nombre de instancia que se encuentra en la página de supervisión de la consola de cliente.

El servicio de canalización realiza un seguimiento de los mensajes recuperados por cada consumidor. El uso de diferentes consumidores para diferentes instancias permite asegurarse de que cada mensaje se envía a cada instancia.

### Recomendaciones de opciones de canalización {#pipeline-option-recommendation}

Para configurar la opción Canalización, debe seguir estas recomendaciones:

* Añada o edite activadores en **[!UICONTROL Triggers]**; no debe editar el resto.
* Asegúrese de que el JSON sea válido. Puede utilizar un validador JSON, por ejemplo, consulte este [sitio web](http://jsonlint.com/) .
* &quot;name&quot; corresponde al ID del desencadenador. Un comodín &quot;*&quot; capturará todos los activadores.
* &quot;Consumidor&quot; corresponde al nombre de la instancia o aplicación que realiza la llamada.
* Pipelned también admite el tema &quot;alias&quot;.
* Siempre debe reiniciar la tubería después de realizar cambios.

## Paso 3: Configuración opcional {#step-optional}

Puede cambiar algunos parámetros internos según sus requisitos de carga, pero asegúrese de probarlos antes de ponerlos en producción.

La lista de parámetros opcionales se encuentra a continuación:

| Opción | Descripción |
|:-:|:-:|
| appName(Heredado) | AppID de la aplicación OAuth registrada en la aplicación Legacy Oath donde se cargó la clave pública. Para obtener más información, consulte [esta página](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(Legacy) | URL para obtener tokens de puerta de enlace. Predeterminado: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | La clave privada, parte pública cargada en la aplicación Legacy Oath, AES cifrada con la opción XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Deshabilitar la autenticación, la conexión sin tokens de puerta de enlace solo será aceptada por algunos extremos de canalización de desarrollo. |
| discoverPipelineEndpoint | URL para encontrar el extremo de los servicios de tubería que se va a usar para este inquilino. Predeterminado: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | También se puede acceder a un período entre dos vertederos del proceso de estado interno en el estado ```var/INSTANCE/pipelined.json.```<br> interno a petición aquí: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Deshabilitar la detección de PipelineServicesEndpoint para forzarlo |
| monitorServerPort | El proceso canalizado escuchará en este puerto para proporcionar el proceso de estado interno aquí: ```http://INSTANCE:PORT/pipelined/status```. <br>El valor predeterminado es 7781 |
| pointerFlushMessageCount | Cuando se procesa este número de mensajes, los desplazamientos se guardan en la base de datos. <br> El valor predeterminado es 1000 |
| pointerFlushPeriodSec | Después de este período, los desplazamientos se guardan en la base de datos. <br>El valor predeterminado es 5 (segundos) |
| processingJSThreads | Número de mensajes de procesamiento de los subprocesos dedicados con conectores JS personalizados. <br> El valor predeterminado es 4 |
| processingThreads | Número de mensajes de procesamiento de los subprocesos dedicados con código integrado. <br>El valor predeterminado es 4 |
| retryPeriodSec | Retraso entre reintentos en caso de errores de procesamiento. <br>El valor predeterminado es 30 (segundos) |
| retryValiditySec | Descarte el mensaje si no se procesa correctamente después de este período (demasiados reintentos). <br>El valor predeterminado es 300 (segundos) |

### Inicio automático de proceso de canalización {#pipelined-process-autostart}

El proceso de tuberías debe iniciarse automáticamente.

Para ello, establezca el elemento &lt; canalizado > en el archivo de configuración en autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Reinicio del proceso de canalización {#pipelined-process-restart}

Se requiere reiniciar para que los cambios surtan efecto:

```
nlserver restart pipelined@instance
```

## Paso 4: Validación {#step-validation}

Para validar la configuración de la canalización para el aprovisionamiento, siga los pasos a continuación:

* Make sure the [!DNL pipelined] process is running.
* Compruebe los registros de conexión de canalización en pipelned.log.
* Compruebe la conexión y si se reciben pings. Los clientes alojados pueden utilizar la supervisión desde la consola de cliente.
