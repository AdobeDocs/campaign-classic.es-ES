---
product: campaign
title: 'Solución de problemas de canalización '
description: 'Solución de problemas de canalización '
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 92%

---

# Solución de problemas de canalización {#pipeline-troubleshooting}

![](../../assets/common.svg)

**La canalización produce el error “Ninguna tarea corresponde a la máscara pipelined@&lt; instance >”**

La versión de Adobe Campaign Classic no admite la canalización.

1. Compruebe si el [!DNL pipelined] elemento está presente en el archivo de configuración. Si no, significa que no es compatible.
1. Actualización a Campaign 20.3 / [!DNL Gold Standard] 11 o posterior.

**La canalización produce el error &#39;&#39; aurait dû commencer par `[` ou `{` (iRc=16384)&quot;**

No está establecida la opción **NmsPipeline_Config** . En realidad es un error de análisis de JSON.
Establezca la configuración JSON en la opción **NmsPipeline_Config**. Consulte &quot;Opción de enrutamiento&quot; en esta sección.

**La canalización produce el error &quot;el sujeto debe ser una organización o cliente válido&quot;**

La configuración del identificador de organización no es válida.

1. Compruebe que el ID de organización (ImsOrgId) esté establecido en serverConf.xml.
1. Compruebe si un ID de organización vacío en el archivo de configuración de instancia puede anular el predeterminado. Si es así, elimínelo.
1. Compruebe que el ID de organización sea correcto. Para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es){_blank}

**La canalización produce el error &quot;clave no válida&quot;**

El parámetro @authPrivateKey del archivo de configuración de instancia es incorrecto.

1. Compruebe que se haya establecido authPrivateKey.
1. Compruebe que authPrivateKey: empieza con @, termina con = y tiene una longitud de aproximadamente 4000 caracteres.
1. Busque la clave original y verifique que tenga: formato RSA, 4096 bits de longitud y empiece con `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Si es necesario, vuelva a crear la clave y regístrela en Adobe Analytics.
1. Compruebe que la clave se haya codificado en la misma instancia que [!DNL pipelined]. <br>Si es necesario, rehaga la codificación utilizando JavaScript o el flujo de trabajo de ejemplo.

**La canalización produce el error &quot;no se puede leer el token durante la autenticación&quot;**

La clave privada tiene un formato no válido.

1. Ejecute los pasos para el cifrado de claves en esta página.
1. Compruebe que la clave esté encriptada en la misma instancia.
1. Compruebe que authPrivateKey del archivo de configuración coincida con la clave generada. <br>Asegúrese de utilizar OpenSSL para generar el par de claves. PuttyGen, por ejemplo, no genera el formato adecuado.

**La canalización produce el error “ya no se permite obtener el token de acceso”**

Los registros deben ser los siguientes:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Este mensaje de error significa que la autenticación se configura con el OAuth base heredado de Omniture. Consulte la documentación de [Configuración de Adobe I/O para activadores de Adobe Experience Cloud](../../integrations/using/configuring-adobe-io.md) para actualizar la autenticación.

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

**Actualización de instancias de fase de autenticación heredada a autenticación de Adobe IO**

Cambiar la autenticación de integración en la instancia de fase no afectará a la configuración de la instancia de producción. Puede elegir actualizar la instancia de fase y actualizar la autenticación a Adobe IO y probar los activadores en la instancia de fase.

La instancia de producción seguirá utilizando la autenticación heredada y no se verá afectada por este cambio.
