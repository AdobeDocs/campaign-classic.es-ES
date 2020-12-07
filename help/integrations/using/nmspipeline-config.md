---
solution: Campaign Classic
product: campaign
title: Configuración de la integración
description: Configuración de la integración
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '373'
ht-degree: 100%

---


# Opción de canalización NmsPipeline_Config {#nmspipeline_config}

Una vez que la autenticación funcione, [!DNL pipelined] puede recuperar los eventos y procesarlos. Solo procesa activadores configurados en Adobe Campaign e ignora al resto. El activador debe haberse generado desde Analytics y haber sido transferido a la canalización de antemano.
La opción también se puede configurar con un comodín para capturar todos los activadores independientemente del nombre.

La configuración de los activadores se realiza en una opción, en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. El nombre de la opción es **[!UICONTROL NmsPipeline_Config]**. El tipo de datos es &quot;texto largo&quot; en formato JSON.

Este ejemplo especifica dos activadores.

Pegue el código JSON de esta plantilla en el valor de la opción. Asegúrese de quitar los comentarios.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
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

Este segundo ejemplo detecta todos los activadores.

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

>[!NOTE]
>
>El valor UID [!DNL Trigger] de un nombre de desencadenador específico en la interfaz de Analytics se encuentra como parte de los parámetros de cadena de consulta de URL en la interfaz Activadores. El UID triggerType se pasa al flujo de datos de la canalización y el código se puede escribir en pipeline.JS para asignar el UID de activador a una etiqueta fácil de usar que se pueda almacenar en la columna Nombre del activador en el esquema pipelineEvents.

## El parámetro de consumidor {#consumer-parameter}

La canalización funciona con un modelo de &quot;proveedor y consumidor&quot;. Puede haber muchos consumidores en la misma cola. Los mensajes se &quot;consumen&quot; únicamente para un consumidor individual. Cada consumidor obtiene su propia &quot;copia&quot; de los mensajes.

El parámetro &quot;Consumidor&quot; identifica la instancia como uno de estos consumidores. Es la identidad de la instancia que llama a la canalización. Puede rellenarla con el nombre de la instancia. El servicio de canalización realiza un seguimiento de los mensajes recuperados por cada consumidor. El uso de diferentes consumidores para diferentes instancias garantiza que todos los mensajes se envíen a cada instancia.

## Cómo configurar la opción Canalización {#configure-pipeline-option}

Añada o edite los activadores de Experience Cloud en la matriz &quot;activadores&quot;; no edite el resto.
Asegúrese de que JSON sea válido con la ayuda de este [sitio web](http://jsonlint.com/).

* &quot;nombre&quot; es el ID del desencadenador. Un comodín &quot;*&quot; captura todos los activadores.
* &quot;Consumidor&quot; es cualquier cadena única que identifica de forma exclusiva la instancia de nlserver. Normalmente puede ser el nombre de la instancia. Para varios entornos (dev/stage/prod), asegúrese de que sea único para cada uno de ellos para que cada instancia obtenga una copia del mensaje.
* [!DNL Pipelined] también admite el tema &quot;alias&quot;.

Reinicie [!DNL pipelined] después de realizar los cambios.
