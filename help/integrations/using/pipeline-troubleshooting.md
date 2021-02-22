---
solution: Campaign Classic
product: campaign
title: Configuración de la integración
description: Configuración de la integración
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 100%

---


# Solución de problemas de canalización {#pipeline-troubleshooting}

**La canalización produce el error “Ninguna tarea corresponde a la máscara pipelined@&lt; instance >”**

La versión de Adobe Campaign Classic no admite la canalización.

1. Compruebe si el [!DNL pipelined] elemento está presente en el archivo de configuración. Si no, significa que no es compatible.
1. Actualice a Campaign 20.3 o Gold Standard 11.

**La canalización produce el error &#39;&#39; aurait dû commencer par `[` ou `{` (iRc=16384)&quot;**

No está establecida la opción **NmsPipeline_Config** . En realidad es un error de análisis de JSON.
Establezca la configuración JSON en la opción **NmsPipeline_Config**. Consulte &quot;Opción de enrutamiento&quot; en esta sección.

**La canalización produce el error &quot;el sujeto debe ser una organización o cliente válido&quot;**

La configuración del identificador de organización no es válida.

1. Compruebe que IMSOrgId esté establecido en serverConf.xml.
1. Busque un IMSOrgId vacío en el archivo de configuración de instancia que pueda anular el valor predeterminado. Si es así, elimínelo.
1. Compruebe que IMSOrgId coincida con el cliente de Experience Cloud.

**La canalización produce el error &quot;clave no válida&quot;**

El parámetro @authPrivateKey del archivo de configuración de instancia es incorrecto.

1. Compruebe que se haya establecido authPrivateKey.
1. Compruebe que authPrivateKey: empieza con @, termina con = y tiene una longitud de aproximadamente 4000 caracteres.
1. Busque la clave original y verifique que tenga: formato RSA, 4096 bits de longitud y empiece con -----BEGIN RSA PRIVATE KEY-----.
   <br> Si es necesario, vuelva a crear la clave y regístrela en Adobe Analytics.
1. Compruebe que la clave se haya codificado en la misma instancia que [!DNL pipelined]. <br>Si es necesario, rehaga la codificación utilizando JavaScript o el flujo de trabajo de ejemplo.

**La canalización produce el error &quot;no se puede leer el token durante la autenticación&quot;**

La clave privada tiene un formato no válido.

1. Ejecute los pasos para el cifrado de claves en esta página.
1. Compruebe que la clave esté encriptada en la misma instancia.
1. Compruebe que authPrivateKey del archivo de configuración coincida con la clave generada. <br>Asegúrese de utilizar OpenSSL para generar el par de claves. PuttyGen, por ejemplo, no genera el formato adecuado.

**No se recuperaron activadores**

Cuando el [!DNL pipelined] proceso se está ejecutando y no se recuperan los activadores:

1. Asegúrese de que el activador este activo en Analytics y generando eventos.
1. Asegúrese de que el [!DNL pipelined] proceso se esté ejecutando.
1. Busque errores en el [!DNL pipelined] registro.
1. Busque errores en la página de estado [!DNL pipelined]. Activador descartado, fallas del activador fracasos deben estar en cero.
1. Compruebe que el nombre del activador esté configurado en la opción **[!UICONTROL NmsPipeline_Config]**. Si hay alguna duda, utilice la opción comodín.
1. Compruebe que Analytics tenga un activador activo y esté generando eventos. Antes de que la configuración esté activa podría haber un retraso de unas horas en Analytics.

**Los Eventos no están vinculados a un cliente**

Cuando algunos eventos no están vinculados a un cliente:

1. compruebe que el flujo de trabajo de reconciliación se esté ejecutando, si corresponde.
1. Compruebe que el evento contenga un ID de cliente.
1. Realice una consulta en la tabla del cliente con el ID del cliente.
1. Compruebe la frecuencia de la importación del cliente. Los clientes nuevos se importan en Adobe Campaign con un flujo de trabajo.

**Latencia en el procesamiento de eventos**

Cuando la marca de tiempo de Analytics es mucho más antigua que la fecha de creación del evento en Campaign.

Generalmente, un activador puede tardar entre 15 y 90 minutos en iniciar una campaña de marketing. Esto varía según la implementación de la recopilación de datos, la carga en la canalización, la configuración personalizada del activador definido y el flujo de trabajo en Adobe Campaign.

1. Compruebe si el proceso [!DNL pipelined] se ejecutado.
1. Busque errores en pipelined.log que puedan causar reintentos. Corrija los errores, si corresponde.
1. Compruebe el tamaño de la cola en la página [!DNL pipelined] de estado. Si el tamaño de la cola es grande, mejore el rendimiento del JS.
1. Dado que un retraso parece aumentar con el volumen, configure los activadores en Analytics con menos mensajes.
