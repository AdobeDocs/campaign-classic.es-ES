---
product: campaign
title: Configuración de la canalización
description: Obtenga información sobre cómo configurar la canalización para la integración de Campaign con Déclencheur
feature: Triggers
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 62%

---

# Configuración de la canalización {#configuring-pipeline}

Los parámetros de autenticación como el ID de cliente, la clave privada y el extremo de autenticación se configuran en los archivos de configuración de instancia.

La lista de déclencheur que se van a procesar se configura en una opción en formato JSON.

Los activadores se utilizan para la segmentación mediante un flujo de trabajo de campaña que envía correos electrónicos. La campaña se configura de modo que un cliente que tenga ambos eventos desencadenadores reciba un correo electrónico.

## Requisitos previos {#prerequisites}

Antes de iniciar esta configuración, compruebe lo siguiente:

* Un proyecto de Adobe Developer
* Un ID de organización válido: para encontrar el ID de organización, consulte [esta página](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Un acceso para desarrolladores para su organización
* Una configuración de déclencheur válida en Adobe Analytics

## Archivos de autenticación y configuración {#authentication-configuration}

Se requiere la autenticación ya que la canalización está alojada en Adobe Experience Cloud. Utiliza un par de claves públicas y privadas. Este proceso tiene la misma función que un usuario/contraseña, pero es más seguro. La autenticación es compatible con el Marketing Cloud a través del proyecto de Adobe Developer.

## Paso 1: Crear/actualizar su proyecto de Adobe Developer {#creating-adobe-io-project}

Para los clientes alojados, colabore con su representante de Adobes/Servicio de atención al cliente para permitir a su organización utilizar los tokens de cuenta de Adobe Developer para la integración de Déclencheur.

Para clientes on-premise/híbridos, consulte la [Configuración del Adobe I/O para Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) página. Tenga en cuenta que debe seleccionar **[!UICONTROL Adobe Analytics]** al agregar la API a la credencial de Adobe Developer.

## Paso 2: Configurar la opción de canalización {#configuring-nmspipeline}

Una vez configurada la autenticación, la canalización recuperará los eventos. Solo procesará los activadores configurados en Adobe Campaign. El déclencheur debe haberse generado desde Adobe Analytics y se debe haber insertado en la canalización, que solo procesará los déclencheur configurados en Adobe Campaign.

La opción también se puede configurar con un comodín para capturar todos los activadores independientemente del nombre.

1. En Adobe Campaign, acceda al menú de opciones en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** en la **[!UICONTROL Explorer]**.

1. Seleccione la opción **[!UICONTROL NmsPipeline_Config]**.

1. En el campo **[!UICONTROL Value (long text)]**, puede pegar el siguiente código JSON, que especifica dos activadores. Debe asegurarse de eliminar los comentarios.

   ```json
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

   ```json
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

### Definición del parámetro de consumidor {#consumer-parameter}

La canalización funciona como un modelo de proveedor y consumidor. Los mensajes se consumen únicamente para un consumidor individual: cada consumidor obtiene su propia copia de los mensajes.

El parámetro **Consumidor** identifica la instancia como uno de estos consumidores. La identidad de la instancia llamará a la canalización. Puede rellenarla con el nombre de instancia que se encuentra en la página de monitorización de la consola de cliente.

El servicio de canalización realiza un seguimiento de los mensajes recuperados por cada consumidor. El uso de diferentes consumidores para diferentes instancias permite asegurarse de que todos los mensajes se envíen a cada instancia.

### Recomendaciones de opciones de canalización {#pipeline-option-recommendation}

Para configurar la opción Canalización, debe seguir estas recomendaciones:

* Añadir o editar déclencheur en **[!UICONTROL Triggers]**.
* Asegúrese de que el JSON sea válido.
* El **Nombre** corresponde al ID de déclencheur. El comodín &quot;*&quot; capturará todos los activadores.
* El **Consumidor** parameter corresponde al nombre de la instancia o aplicación que realiza la llamada.
* el `pipelined`process también admite el tema &quot;alias&quot;.
* Siempre debe reiniciar `pipelined`procesar después de realizar cambios.

## Paso 3: Configuración opcional {#step-optional}

Puede cambiar algunos parámetros internos según los requisitos de carga, pero asegúrese de probarlos antes de aplicarlos al entorno de producción.

La lista de parámetros opcionales es la siguiente:

| Opción | Descripción |
|:-:|:-:|
| appName(Legacy) | AppID de la aplicación OAuth registrada en la aplicación heredada de Oath donde se cargó la clave pública. Para obtener más información, consulte [esta página](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint(Legacy) | URL para obtener los tokens de la puerta de enlace. Predeterminado: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | La clave privada, la parte pública cargada en la aplicación heredada de Oath, AES cifrada con la opción XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Deshabilite la autenticación, la conexión sin tokens de puerta de enlace solo la aceptan algunos extremos de canalización de desarrollo. |
| discoverPipelineEndpoint | URL para encontrar el extremo de los servicios de canalización que se va a usar para este inquilino. Predeterminado: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | También se puede acceder a petición al período entre dos volcados del proceso de estado interno en ```var/INSTANCE/pipelined.json.```<br> aquí: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Deshabilite la detección de PipelineServicesEndpoint para forzarla |
| monitorServerPort | El proceso de canalización escuchará en este puerto para proporcionar el proceso de estado interno aquí: ```http://INSTANCE:PORT/pipelined/status```. <br>El valor predeterminado es 7781 |
| pointerFlushMessageCount | Cuando se procesa este número de mensajes, los desplazamientos se guardan en la base de datos. <br> El valor predeterminado es 1000 |
| pointerFlushPeriodSec | Después de este período, los desplazamientos se guardan en la base de datos. <br>El valor predeterminado es 5 (segundos) |
| processingJSThreads | Número de mensajes de procesamiento de los subprocesos dedicados con conectores JS personalizados. <br> El valor predeterminado es 4 |
| processingThreads | Número de mensajes de procesamiento de los subprocesos dedicados con código integrado. <br>El valor predeterminado es 4 |
| retryPeriodSec | Retraso entre reintentos si hay errores de procesamiento. <br>El valor predeterminado es 30 (segundos) |
| retryValiditySec | Descarte el mensaje si no se procesa correctamente después de este período (demasiados reintentos). <br>El valor predeterminado es 300 (segundos) |

### Inicio automático de proceso de canalización {#pipelined-process-autostart}

El `pipelined` El proceso de debe iniciarse automáticamente.

Para ello, configure el `<`canalizado`>` en el archivo de configuración a autostart=&quot;true&quot;:

```sql
 <pipelined autoStart="true" ... "/>
```

### Reinicio del proceso de canalización {#pipelined-process-restart}

Se requiere reiniciar para que los cambios surtan efecto:

```sql
nlserver restart pipelined@instance
```

## Paso 4: Validación {#step-validation}

Para validar la configuración de la canalización para el aprovisionamiento, siga los pasos a continuación:

* Asegúrese de que el proceso de `pipelined` se esté ejecutando.
* Compruebe la `pipelined.log` para registros de conexión de canalización.
* Compruebe la conexión y si se reciben los pings. Los clientes alojados pueden utilizar la Monitorización desde la consola de cliente.
