---
product: campaign
title: Configuración de canalización
description: Obtenga información sobre cómo configurar la canalización para la integración Campaign - Triggers
feature: Triggers
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: ht
source-wordcount: '833'
ht-degree: 100%

---

# Configuración de canalización {#configuring-pipeline}

Los parámetros de autenticación como el ID de cliente, la clave privada y el extremo de autenticación se configuran en los archivos de configuración de instancia.

La lista de activadores que se van a procesar se configura en una opción en formato JSON.

Los activadores se utilizan para la segmentación mediante un flujo de trabajo de campaña que envía correos electrónicos. La campaña se configura de modo que un cliente que tenga ambos eventos desencadenadores reciba un correo electrónico.

## Requisitos previos {#prerequisites}

Antes de iniciar esta configuración, compruebe que dispone de:

* Un proyecto de Adobe Developer
* Un ID de organización válido: para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/es/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Un acceso para desarrolladores para su organización
* Una configuración de activadores válida en Adobe Analytics

Se requiere la autenticación, ya que la canalización está alojada en Adobe Experience Cloud. Utiliza una autenticación que es compatible a través de un proyecto de Adobe Developer.

## Paso 1: Crear/actualizar su proyecto de Adobe Developer {#creating-adobe-io-project}

Debe habilitar su organización con tokens de cuenta de Adobe Developer para la integración de los activadores.

Aprenda a crear su cuenta técnica de Adobe en [esta página](../../integrations/using/oauth-technical-account.md). Tenga en cuenta que debe seleccionar **[!UICONTROL Adobe Analytics]** al añadir la API a la credencial de Adobe Developer.

## Paso 2: Configuración de la opción de canalización {#configuring-nmspipeline}

Una vez configurada la autenticación, la canalización recuperará los eventos. Solo procesará los activadores configurados en Adobe Campaign. El activador debe haberse generado desde Adobe Analytics y se debe haber insertado en la canalización, que solo procesará los activadores configurados en Adobe Campaign.

La opción también se puede configurar con un comodín para capturar todos los activadores independientemente del nombre.

1. En Adobe Campaign, acceda al menú de opciones en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** en la **[!UICONTROL Explorer]**.

1. Seleccione la opción **[!UICONTROL NmsPipeline_Config]**.

1. En el campo **[!UICONTROL Value (long text)]**, puede pegar el siguiente código JSON, que especifica dos activadores. Asegúrese de quitar los comentarios.

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

### Establecer el parámetro de consumidor {#consumer-parameter}

La canalización funciona como un modelo de proveedor y consumidor. Los mensajes se consumen únicamente para un consumidor individual: cada consumidor obtiene su propia copia de los mensajes.

El parámetro **Consumidor** identifica la instancia como uno de estos consumidores. La identidad de la instancia llamará a la canalización. Puede rellenarla con el nombre de instancia que se encuentra en la página de monitorización de la consola de cliente.

El servicio de canalización realiza un seguimiento de los mensajes recuperados por cada consumidor. El uso de diferentes consumidores para diferentes instancias permite asegurarse de que todos los mensajes se envíen a cada instancia.

### Recomendaciones de opciones de canalización {#pipeline-option-recommendation}

Para configurar la opción Canalización, debe seguir estas recomendaciones:

* Añadir o editar activadores en **[!UICONTROL Triggers]**.
* Asegúrese de que el JSON sea válido. 
* El parámetro **Nombre** corresponde al ID del activador. El comodín &quot;*&quot; capturará todos los activadores.
* El parámetro **Consumidor** corresponde al nombre de la instancia o aplicación que realiza la llamada.
* el proceso `pipelined` también admite el tema “alias”.
* Siempre debe reiniciar el proceso `pipelined` después de realizar cambios.

## (opcional) Paso 3: Configuración adicional {#step-optional}

Puede cambiar algunos parámetros internos según sus requisitos de carga, pero asegúrese de probarlos antes de aplicarlos en su entorno de producción.

La lista de parámetros opcionales es:

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

El proceso `pipelined` debe iniciarse automáticamente.

Para ello, establezca el elemento `<`pipelined`>` en el archivo de configuración como autostart=&quot;true&quot;:

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
* Compruebe los registros de conexión de canalización en `pipelined.log`.
* Compruebe la conexión y si se reciben los pings. Los clientes alojados pueden utilizar la Monitorización desde la consola de cliente.
