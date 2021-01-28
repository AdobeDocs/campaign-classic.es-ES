---
solution: Campaign Classic
product: campaign
title: Configuración y protocolo del conector SMS
description: Obtenga más información sobre el conector de SMS y cómo configurarlo.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: ht
source-git-commit: 96ad3208c792efb47097768bc779bec59d9ca313
workflow-type: ht
source-wordcount: '2745'
ht-degree: 100%

---


# Solución de problemas de SMS {#troubleshooting-sms}

## Conflicto entre diferentes cuentas externas {#external-account-conflict}

Si la instancia tiene varias cuentas externas SMS, debe comprobar que los problemas no son causados por un conflicto entre cuentas externas.

Adobe Campaign trata las cuentas externas como entidades no relacionadas.

Si tiene varias cuentas, siga este procedimiento para aislar la cuenta externa que causa problemas:

1. Deshabilite todas las cuentas externas.
1. Habilite una cuenta externa.
1. Trate de reproducir el problema.
1. Si el problema inicial no aparece siempre, realice una cantidad razonable de intentos antes de concluir.
1. Si el problema no aparece con esa única cuenta, desactívela y vuelva a empezar en el paso 2 de la cuenta siguiente.

Una vez que ha comprobado cada cuenta individualmente, existen dos escenarios posibles:

* **El problema apareció en una o varias cuentas**

   En este caso, puede aplicar otros procedimientos de resolución de problemas en cada cuenta de forma individual. Es mejor desactivar otras cuentas al diagnosticar una cuenta para reducir el tráfico de red y la cantidad de registros.

* **El problema no aparecía cuando solo una cuenta estaba activa en cualquier momento**

   Tiene un conflicto entre cuentas. Como se mencionó anteriormente, Adobe Campaign trata las cuentas individualmente, pero el proveedor puede tratarlas como una sola cuenta.

   * Utilice diferentes combinaciones de inicio de sesión y contraseña entre todas las cuentas.
Tendrá que ponerse en contacto con el proveedor para diagnosticar conflictos potenciales de su parte.

   * Algunas de las cuentas externas comparten la misma combinación de inicio de sesión y contraseña.
El proveedor no tiene forma de saber de qué cuenta externa proviene el `BIND PDU`, por lo que trata todas las conexiones de las cuentas múltiples como una sola. Es posible que hayan enrutado MO y SR de manera aleatoria a las dos cuentas, lo que causa problemas.
Si el proveedor admite varios códigos cortos para la misma combinación de inicio de sesión y contraseña, tendrá que preguntarle dónde colocar ese código corto en el `BIND PDU`. Tenga en cuenta que esta parte de información debe colocarse dentro de `BIND PDU` y no en `SUBMIT_SM`, ya que `BIND PDU` es el único lugar que permitirá enrutar los MO correctamente.
Consulte la sección [Información en cada tipo de PDU](../../delivery/using/sms-protocol.md#information-pdu) anterior para saber qué campo está disponible en `BIND PDU`, generalmente se añade el código corto en `address_range`, pero eso requiere asistencia especial del proveedor. Póngase en contacto con ellos para saber cómo esperan enrutar varios códigos cortos de forma independiente.
Adobe Campaign admite el manejo de varios códigos cortos en la misma cuenta externa.

## Problema con la cuenta externa en general {#external-account-issues}

* Investigue si el conector se ha cambiado recientemente y quién lo ha cambiado (compruebe las Cuentas externas como grupo).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Investigue (en el directorio/postupgrade) si el sistema se ha actualizado y cuándo
* Investigue si algún paquete que afecte a SMS pudo haberse actualizado recientemente (/var/log/dpkg.log).

## Problema con el intermediario (alojado){#issue-mid-sourcing}

* Si el problema se produce en un entorno de intermediario, asegúrese de que el envío y los registros generales se hayan creado y actualizado correctamente en el servidor intermediario. Si ese no es el caso, este no es un problema de SMS.

* Si todo funciona en el servidor central y los SMS se envían correctamente, pero la instancia de marketing no se actualiza correctamente, es posible que tenga un problema de sincronización intermedia.

## Problema al conectarse al proveedor {#issue-provider}

* Si el `BIND PDU` devuelve un código `command_status` distinto de cero, pida al proveedor más información.

* Compruebe que la red está configurada correctamente para que la conexión TCP se pueda establecer con el proveedor.

* Pida al proveedor que compruebe que ha agregado correctamente las IP a la lista de permitidos de la instancia de Adobe Campaign.

* Compruebe la configuración de la **Cuenta externa**. Pregunte al proveedor el valor de los campos.

* Si la conexión es correcta, pero inestable, consulte la sección [Problema con conexiones inestables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Si los problemas de conexión son difíciles de diagnosticar, una captura de red puede proporcionar información. Asegúrese de que la captura de red se ejecuta simultáneamente mientras que el problema aparece para que se pueda analizar de forma eficaz. También debe anotar la hora exacta en la que aparece el problema.

## Problemas con una conexión inestable {#issues-unstable-connection}

Una conexión se considera inestable si se produce alguna de las siguientes situaciones:

* La conexión dura menos de 1 hora. Las conexiones de transmisores de Adobe Campaign Classic son una excepción debido a la forma en que funciona el MTA de Adobe Campaign Classic.

* El proveedor envía `UNBIND PDU`s.

* `enquire_link` agota el tiempo de espera, ya sea en el lado de Adobe Campaign o en el del proveedor. Puede ver `ENQUIRE_LINK_RESP` con un código de error distinto de cero en ese caso.

* Hay muchas `BIND PDU`. No debe haber más de unas pocas durante un día, según la cantidad de conexiones. Más de una PDU BIND por hora debería llamar su atención.

Para solucionar los problemas de estabilidad de la conexión:

* Las conexiones inestables rara vez son la causa principal, a menudo es el resultado de otro problema que desencadena una desconexión. La prioridad es encontrar la causa raíz.

* Habilite seguimientos detallados del SMPP. Los necesitará para ver que está ocurriendo cuando la conexión re reinicie. 

* Si el proveedor envía `BIND PDU`, algo podría estar mal. Pregunte al proveedor por qué se envía `UNBING`.

* Realizar una captura de red es, a veces, la única manera de ver cómo se cierra la conexión.

* Si el proveedor cierra las conexiones enviando un `TCP FIN` o un `TCP RST packet`, pida más información a su proveedor.

* Si el proveedor cierra la conexión después de enviar un error limpio como `DELIVER_SM_RESP` con un código de error, deberá corregir su conector, de lo contrario eso impedirá que se transmitan otros tipos de mensajes y activará la limitación de MTA. Esto es especialmente importante en el modo transceptor, donde el cierre de la conexión afecta tanto a MT como SR.

## Problema al enviar un mensaje MT (SMS regular enviado a un usuario final){#issue-MT}

* Compruebe que la conexión es estable. Una conexión SMPP debe permanecer activa durante al menos 1 hora de forma continua, excepto para los transmisores de Adobe Campaign Classic. Consulte la sección [Problema con conexiones inestables](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Si al reiniciar el MTA hace que el envío de MT vuelva a funcionar por un período de tiempo corto, es probable que tenga un estrangulamiento debido a una conexión inestable. Consulte la sección [Problema con conexiones inestables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Compruebe que el registro general está presente y en el estado correcto con las fechas correctas. Si no es así, podría tratarse de un problema de envíos o de preparación de envíos.

* Compruebe que el MTA procesa realmente el mensaje. Si no es así, podría no ser un problema de SMS.

* Compruebe que el conector SMS está vinculado con el equipo del proveedor. Pídale información al proveedor para asegurarse de que todos los sistemas se comunican correctamente. Consulte `BIND_TRANSMITTER` y `BIND_TRANSCEIVER PDU` para obtener información sobre el proceso de vinculación. Es posible que deba habilitar los seguimientos del SMPP para la correcta resolución de problemas.

* Con los seguimientos del SMPP activados, compruebe que `SUBMIT_SM PDU` contiene la información correcta.

* Compruebe que el proveedor responde con un `SUBMIT_SM_RESP PDU` con un valor &quot;OK&quot; (código 0). Asegúrese de que la PDU llega con un retraso razonable: cualquier valor superior a 1 segundo debe ser consultado con el proveedor, normalmente llega en menos de 100 ms.

* Si todos estos pasos funcionan, puede estar seguro de que el problema está en el lado del proveedor. Tendrán que solucionar el problema en su plataforma.

* Si funciona pero el rendimiento es inconsistente, intente ajustar la ventana de envío y reducir el rendimiento de MT. Tendrá que trabajar con el proveedor para ajustarlo. Adobe Campaign puede enviar mensajes muy rápidamente, por lo que pueden surgir problemas de rendimiento en el equipo del proveedor.

## MT están duplicados (el mismo SMS se envía varias veces seguidas){#duplicated-MT}

Los duplicados suelen deberse a reintentos. Es normal tener duplicados al reintentar mensajes, en su lugar debe intentar solucionar la causa raíz de los reintentos.

* Si ve duplicados enviados exactamente con 60 segundos de diferencia, probablemente sea un problema en el proveedor, no envían un `SUBMIT_SM_RESP` lo suficientemente rápido.

* Si ve muchos `BIND/UNBIND`, tiene una conexión inestable. Consulte la sección [Problema con conexiones inestables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) para obtener soluciones antes de intentar resolver los problemas de mensajes duplicados.

Reducción de la cantidad de duplicados cuando hay un reintento:

* Reduzca la ventana de envío. La ventana de envío debe ser lo suficientemente grande como para cubrir la latencia de `SUBMIT_SM_RESP`. Su valor representa la cantidad máxima de mensajes que se pueden duplicar si se produce un error mientras la ventana está llena.

## Problema al procesar SR (recibos de envíos) {#issue-process-SR}

* Necesitará los seguimientos del SMPP activados para realizar cualquier tipo de resolución de problemas de SR.

* Compruebe que el `DELIVER_SM PDU` proviene del proveedor y que está bien formado.

* Compruebe que Adobe Campaign responde con un `DELIVER_SM_RESP PDU` correcto de manera oportuna. En Adobe Campaign Classic, esto garantiza que el SR se ha insertado en la tabla `providerMsgId` para que el proceso de SMS lo procese de forma diferida.

Si el `DELIVER_SM PDU` no se reconoce correctamente, debe comprobar lo siguiente:

* Consulte las expresiones regulares (regex) relacionadas con la extracción de ID y el procesamiento de errores en la **Cuenta externa**. Es posible que tenga que validarlas con el contenido de `DELIVER_SM PDU`.

* Compruebe que los errores están correctamente registrados en la tabla `broadLogMsg`.

Si el `DELIVER_SM PDU` lo ha reconocido el conector SMPP extendido de Adobe Campaign Classic, pero el archivo broadLog no se actualiza correctamente, compruebe el proceso de reconciliación de ID descrito en la sección [Coincidencia de las entradas de MT, SR y broadlog](../../delivery/using/sms-protocol.md#matching-mt).

Si ha corregido todo, pero algunos SR no válidos siguen en los búferes del proveedor, puede omitirlos con la opción Número de confirmación de ID no válido. Debe utilizarse con cuidado y restablecerse a 0 lo antes posible después de que los búferes estén limpios.

## Problema al procesar MO (y lista de no permitidos/respuesta automática){#issue-process-MO}

* Habilite los seguimientos del SMPP durante las pruebas. Si no habilita TLS, debe realizar una captura de red al solucionar problemas de MO para comprobar que las PDU contienen la información correcta y tienen el formato adecuado.

* Al capturar tráfico de red o analizar los seguimientos del SMPP, asegúrese de capturar toda la conversación con el MO y su mensaje MT de respuesta si se configura una respuesta.

* Si el MO (`DELIVER_SM PDU`) no aparece en los seguimientos, el problema está en el lado del proveedor. Tendrán que resolver problemas en su plataforma.

* Si aparece `DELIVER_SM PDU`, compruebe que Adobe Campaign lo ha reconocido con un `DELIVER_SM_RESP PDU` (código 0) correcto. Este RESP garantiza que Adobe Campaign ha aplicado toda la lógica de procesamiento (respuesta automática y permitir/denegar lista de bloqueados). Si no es el caso, busque un mensaje de error en los registros de proceso de los SMS.

* Si las respuestas automáticas están habilitadas, compruebe que `SUBMIT_SM` se haya enviado al proveedor. Si no es así, se garantiza que encontrará un mensaje de error en los registros de proceso de los SMS.

* Si el `SUBMIT_SM MT PDU` que contiene la respuesta se encuentra en los seguimientos, pero el SMS no llega al teléfono móvil, tendrá que ponerse en contacto con el proveedor para obtener ayuda sobre la resolución de problemas.

## Problema durante la preparación del envío sin excluir destinatarios en cuarentena (en cuarentena por la función de respuesta automática) {#issue-delivery-preparation}

* Compruebe que el formato del número de teléfono es exactamente el mismo en la tabla de cuarentenas y en el registro de envíos. Si no es así, consulte esta [sección](../../delivery/using/sms-protocol.md#automatic-reply) si tiene problemas con el prefijo más del formato del número de teléfono internacional.

* Compruebe los códigos cortos. Las exclusiones pueden producirse si el código corto del destinatario es el mismo que se define en la cuenta externa o si está vacío (vacío = cualquier código abreviado). Si solo se utiliza un código corto para toda la instancia de Adobe Campaign, es más fácil dejar vacíos todos los campos de **código corto**.

## Problemas de codificación {#encoding-issues}

**Paso 1: Ponerse en contacto con el proveedor**

Póngase en contacto con ellos y vea qué les pasa. Deberían poder decirle si el problema es suyo o de Adobe Campaign. Si el problema es de Adobe Campaign, deben poder indicarle exactamente qué campo es incorrecto.

**Paso 2: Saber qué hay en el mensaje**

Unicode permite muchas variantes para caracteres similares y Adobe Campaign no puede manejarlos todos.

El origen más común de los problemas es un copia y pega desde un procesador de textos, que cambia los caracteres habituales a versiones tipográficamente correctas: los espacios cambian a espacios sin saltos, las comillas dobles cambian a comillas de apertura y cierre, los signos menos cambian a varios tipos de guiones, etc.

No copie y pegue el mensaje durante la prueba, escríbalo siempre directamente en la interfaz.

Con hexadecimal, puede distinguir entre caracteres similares. Una L minúscula, una I mayúscula, O, 0, todos los diferentes tipos de comillas, codificaciones no latinas o incluso distintos tipos de espacios pueden verse igual o incluso no mostrarse.

Para convertir unicode a hexadecimal, puede utilizar herramientas en línea como el sitio web [Convertidor de código Unicode](https://r12a.github.io/app-conversion/). Escriba el texto, asegúrese de que no haya PII como números de teléfono y haga clic en **Convertir**. Verá los valores hexadecimales en la parte inferior (zona UTF-32).

Al abrir tickets por problemas de codificación, ya sea con el proveedor o con la asistencia de Adobe Campaign, siempre incluya una versión hexadecimal de lo que escribe y lo que ve.

**Paso 3: Saber lo que debe enviar**

Determine la codificación que espera usar y busque en línea su tabla de caracteres. Compruebe que los caracteres que desea enviar están disponibles en la página de código de destinatario. Compruebe que el campo `data_coding` es correcto y coincide con lo que usted y el proveedor esperan.

**Paso 4: Saber lo que realmente ha enviado**

Necesitará la salida de depuración del conector para ver exactamente qué bytes envía al proveedor. Los problemas de codificación aparecen en `SUBMIT_SM PDU`, por lo que asegúrese de registrarlos. Envíe mensajes muy distintos que sean fáciles de encontrar en el registro.

Envíe diferentes tipos de caracteres especiales al realizar pruebas. Por ejemplo, la codificación GSM7 tiene caracteres extendidos que son muy distintos en su forma hexadecimal; son fáciles de identificar, ya que no aparecen en ninguna otra codificación.

## Elementos que se deben incluir al comunicar sobre un problema de SMS {#element-include}

Siempre que busque ayuda sobre un problema de SMS, ya sea abriendo una entrada de asistencia en Adobe Campaign, al proveedor de SMS o cualquier tipo de comunicación sobre el tema, necesitará incluir la siguiente información para asegurarse de que esté debidamente clasificado. Los problemas debidamente clasificados son la clave para que se resuelvan más rápido.

* **Active los** mensajes SMPP detallados cuando aparezca el problema. La mayoría de los problemas de SMS son imposibles de resolver sin esto.

* Si el problema está relacionado con el tráfico de SMS, póngase en contacto primero con el proveedor. Su plataforma es más adecuada para un diagnóstico eficiente de los problemas de tráfico SMS en tiempo real.

* Incluya una descripción breve pero objetiva del problema.

* Incluya una descripción del resultado esperado.

* Incluya los comentarios del proveedor.

* Incluya registros relevantes o capturas de red. Al realizar capturas, asegúrese de reproducir el problema durante la captura.

* Si incluye registros, seguimientos o capturas, indique la ubicación exacta en el archivo cuando aparezca el problema.

* Si hace referencia a mensajes, PDU o registros, indique claramente su marca de tiempo para facilitar su búsqueda.

* Intente reproducir el problema en un entorno de prueba. Si no está seguro de un ajuste, pruébelo en el entorno de prueba y compruebe el resultado con los seguimientos del SMPP. Generalmente es mejor informar de problemas replicados en entornos de prueba que informar directamente de los problemas en entornos de producción.

* Incluya cualquier cambio o ajuste realizado en la plataforma. Además, incluya cualquier cambio que el proveedor pueda haber realizado de su parte.

### Captura de red {#network-capture}

No siempre se necesita una captura de red, por lo general los mensajes del SMPP detallados son suficientes. Estas son algunas directrices que le ayudarán a determinar si es necesaria una captura de red:

* Problemas de conexión, pero los mensajes detallados no muestran ningún `BIND_RESP PDU`.

* Desconexiones inexplicables sin mensaje de error, el comportamiento habitual del conector cuando detecta un error de protocolo de nivel bajo.

* El proveedor se queja del proceso de desvinculación/desconexión.

* Problemas de codificación en los campos TLV opcionales.

* Se sospecha que el tráfico se mezcla entre diferentes conexiones.

En todas las demás situaciones, intente analizar primero los mensajes SMPP detallados y solicite una captura de red solo si falta información en los registros detallados.

En algunos casos, no es necesario capturar el tráfico de red. Estas son las situaciones más comunes:

* TLS habilitado: Por definición, el tráfico TLS está cifrado para que no se pueda capturar.

* Problemas de rendimiento: Los registros contienen toda la información necesaria para rastrear los problemas de rendimiento.

* Problemas de temporización (`retry timing`, periodo de `enquire_link`, límite de rendimiento, etc.)

* Análisis y procesamiento de SR: Los registros detallados proporcionan mucho más contexto y una mejor presentación.

* Procesamiento de MO (respuestas automáticas, cuarentena).

* Errores que no implican tráfico SMPP real: Preparación de envíos, problemas de API de centros de mensajes, problemas de flujo de trabajo, etc.

## Activación de los seguimientos del SMPP {#enabling-smpp-traces}

El nuevo conector admite el registro extendido mediante seguimientos: SMPP. Los seguimientos aparecen en el registro MTA, no en la salida estándar.

**Activación por cuenta externa (método preferido)**

1. En la **Cuenta externa**, marque **Habilitar los seguimientos detallados del SMPP en el archivo de registro**.
1. Espere 10 minutos para que el servidor vuelva a cargar las cuentas externas.

Debería estar activo ahora.

**Habilitar en la configuración**

En el archivo `config-instance.xml`, establezca los siguientes parámetros:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Comprobación de la cantidad de conexiones abiertas en un contenedor {#open-connections}

Para comprobar la cantidad de conexiones abiertas en un contenedor, puede utilizar este comando:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Esto indicará la cantidad de conexiones abiertas para un puerto determinado. Aquí estamos usando el puerto 3600.

El resultado debe ser el siguiente:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 conexiones abiertas para el proceso sms y 2 por mta secundaria con 5 subconexiones.
