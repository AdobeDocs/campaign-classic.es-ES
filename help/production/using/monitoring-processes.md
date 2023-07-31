---
product: campaign
title: Monitorización de procesos
description: Obtenga información sobre cómo monitorizar los procesos de Campaign
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3623'
ht-degree: 1%

---

# Monitorización de procesos{#monitoring-processes}


El servidor de aplicaciones y el servidor de redirección (**tracking**) se puede monitorizar de forma manual o automática.

## Monitorización manual {#manual-monitoring}

Para acceder a la página de monitorización de procesos de Adobe Campaign, vaya a **[!UICONTROL Monitoring]** y haga clic en la pestaña **[!UICONTROL Overview]** vínculo.

![](assets/d_ncs_monitoring.png)

La página mostrada permite ver el estado de la instancia conectada, es decir:

* información sobre la instancia: versión, nombre, motor de base de datos, paquetes instalados, indicadores de sistema de servidor,
* la lista de procesos que faltan y la información de ejecución (fecha de inicio, PID, etc.),
* una vista de los flujos de trabajo y las entregas.

Las formas adicionales de monitorizar los procesos de Campaign se presentan en [esta página](../../production/using/monitoring-guidelines.md).

### Diario de registro {#log-journal}

Para mostrar el diario de registro relacionado con un proceso, haga clic en el proceso, **mta** por ejemplo, seleccione **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### Indicadores del sistema {#system-indicators}

Examine la lista de indicadores del sistema para mostrar información sobre la máquina, como su memoria física y virtual, los procesos activos y el espacio disponible en disco. Los indicadores son diferentes para los sistemas operativos Linux y Windows. Vaya a la **[!UICONTROL Instance Monitoring]** y haga clic en la **[!UICONTROL Display]** para abrir la lista de indicadores.

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**: indicador específico de **Centro de mensajes**. [Más información](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**: información sobre la memoria física (RAM).

  **[!UICONTROL Current value]**: consumo de memoria actual.

  **[!UICONTROL Max Value]**: cantidad total de memoria instalada.

  **[!UICONTROL Available]**: cantidad de memoria disponible.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el consumo de memoria alcanza el 80 % de la cantidad total.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el consumo de memoria alcanza el 90 % de la cantidad total.

  Si la variable **[!UICONTROL Warning]** y **[!UICONTROL Alert]** Cuando se muestran los indicadores, puede solucionar el problema añadiendo RAM al equipo en el que está instalado el servidor de Adobe Campaign. También puede decidir instalar el servidor de Adobe Campaign en un equipo dedicado.

* **[!UICONTROL Swap Memory]**: información relacionada con la memoria virtual que coincide con un archivo de paginación: un área del disco duro que Windows utiliza como si fuera RAM.

  **[!UICONTROL Current value]**: consumo real de memoria.

  **[!UICONTROL Max Value]**: cantidad total de memoria.

  **[!UICONTROL Available]**: cantidad de memoria disponible.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el consumo de memoria alcanza el 80 % de la cantidad total.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el consumo de memoria alcanza el 90 % de la cantidad total.

  Si la variable **[!UICONTROL Warning]** y **[!UICONTROL Alert]** Cuando se muestran los indicadores, puede resolver el problema aumentando el tamaño del archivo exchange en la configuración avanzada de Windows.

* **[!UICONTROL Disk XXX]**: información acerca de los lectores de equipos.

  **[!UICONTROL Current value]**: espacio en disco utilizado realmente.

  **[!UICONTROL Max Value]**: capacidad total del disco.

  **[!UICONTROL Available]**: espacio en disco disponible.

  **[!UICONTROL Used]**: porcentaje de disco utilizado.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el espacio disponible en disco alcanza el 80 % de la capacidad total.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el espacio disponible en disco alcanza el 90 % de la capacidad total.

* **[!UICONTROL Number of processes too old]**: información sobre los procesos de Adobe Campaign que han estado activos durante más de un día.

  **[!UICONTROL Current value]**: número de procesos activos actualmente.

  **[!UICONTROL Max Value]**: número máximo de procesos autorizados (1).

  **[!UICONTROL Alert]**: este indicador se muestra si el número de procesos es igual a 1.

  Si la variable **[!UICONTROL Alert]** Si se muestra el indicador, puede ser que el proceso en cuestión esté bloqueado por el motor de base de datos SQL o que esté atascado en un bucle infinito. El **perro guardián** El proceso proporcionado por Adobe Campaign reinicia automáticamente todos los procesos todos los días y le permite resolver este problema. Sin embargo, también puede detener el proceso en cuestión usted mismo para forzar el reinicio.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**: indicador específico de **Centro de mensajes**. Consulte [esta sección](../../message-center/using/additional-configurations.md#monitoring-thresholds) para obtener más información.

* **[!UICONTROL Load average (1/5/15 minutes)]**: información sobre la carga, es decir, la tasa de uso del procesador por parte de los procesos que se ejecutan en el equipo durante el último minuto, cinco minutos o quince minutos

  **[!UICONTROL Current value]**: carga real de la máquina.

  **[!UICONTROL Max value]**: carga máxima de uso de los procesos en la máquina

  **[!UICONTROL Warning]**: este indicador se muestra cuando la carga alcanza el 80 % del valor máximo autorizado en el último minuto, cinco minutos o quince minutos.

  **[!UICONTROL Alert]**: este indicador se muestra cuando la carga alcanza el 90 % del valor máximo autorizado del último minuto, cinco minutos o quince minutos.

* **[!UICONTROL Memory]**  información relativa a la memoria física (RAM).

  **[!UICONTROL Current value]**: consumo real de memoria.

  **[!UICONTROL Max Value]**: cantidad total de memoria instalada.

  **[!UICONTROL Available]**: cantidad de memoria disponible.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el consumo de memoria alcanza el 80 % de la cantidad total.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el consumo de memoria alcanza el 90 % de la cantidad total.

  Si la variable **[!UICONTROL Warning]** y **[!UICONTROL Alert]** Cuando se muestran los indicadores, puede solucionar el problema añadiendo RAM al equipo en el que está instalado el servidor de Adobe Campaign. También puede decidir instalar el servidor de Adobe Campaign en un equipo dedicado.

* **[!UICONTROL Swap Memory]**: información relacionada con la memoria virtual que coincide con un archivo de paginación: un área del disco duro que Windows utiliza como si fuera RAM.

  **[!UICONTROL Current value]**: consumo real de memoria.

  **[!UICONTROL Max Value]**: cantidad total de memoria.

  **[!UICONTROL Available]**: cantidad de memoria disponible.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el consumo de memoria alcanza el 80 % de la cantidad total.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el consumo de memoria alcanza el 90 % de la cantidad total.

  Si la variable **[!UICONTROL Warning]** y **[!UICONTROL Alert]** Cuando se muestran los indicadores, puede resolver el problema aumentando el tamaño del archivo exchange.

* **[!UICONTROL Core Files]**: información sobre los archivos generados tras el bloqueo de un proceso de Adobe Campaign. Estos archivos permiten diagnosticar los motivos del bloqueo.

  **[!UICONTROL Current Value]**: número de archivos existentes.

  **[!UICONTROL Max Value]**: número máximo de archivos autorizados (1).

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de archivos está cerca de 1.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de archivos es igual a 1.

  Cuando falta un proceso debido a un bloqueo, se muestra en rojo en la lista de procesos y el sistema lo reinicia automáticamente **perro guardián** proceso proporcionado por Adobe Campaign.

* **[!UICONTROL Number of shared memory segments]**: información sobre los segmentos de memoria compartidos por todos los procesos de Adobe Campaign.

  **[!UICONTROL Current value]**: número de segmentos de memoria que se están utilizando actualmente.

  **[!UICONTROL Max Value]**: número máximo de segmentos de memoria autorizados (2).

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de segmentos de memoria alcanza 1.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de segmentos de memoria alcanza 2.

* **[!UICONTROL Number of processes too old]**: información sobre los procesos que han estado activos durante más de un día.

  **[!UICONTROL Current value]**: número de procesos activos actualmente.

  **[!UICONTROL Max Value]**: número máximo de procesos autorizados.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de procesos alcanza el 80 % del umbral autorizado.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de procesos alcanza el 90 % del umbral autorizado.

* **[!UICONTROL File Handles]**: información sobre los descriptores de archivo, es decir, el número de archivos abiertos por proceso.

  **[!UICONTROL Current value]**: número actual de descriptores de archivo.

  **[!UICONTROL Max Value]**: número máximo de descriptores de archivo autorizados por el sistema operativo.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de descriptores de archivo autorizados alcanza el umbral del 80 %.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de descriptores de archivo autorizados alcanza el umbral del 90 %.

* **[!UICONTROL Processes]**: información sobre los procesos de la máquina.

  **[!UICONTROL Current value]**: número de procesos activos actualmente.

  **[!UICONTROL Max Value]**: número máximo de procesos autorizados.

  **[!UICONTROL Active Processes]**: número de procesos activos.

  **[!UICONTROL Inactive Processes]**: número de procesos inactivos.

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de procesos autorizados alcanza el umbral del 80 %.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de procesos autorizados alcanza el umbral del 90 %.

* **[!UICONTROL Zombie Processes]**: información sobre los procesos que se han detenido, pero que aún tienen un identificador de proceso (PID) y permanecen visibles en la tabla de proceso.

  **[!UICONTROL Current value]**: número de procesos zombi que están activos actualmente.

  **[!UICONTROL Max Value]**: número máximo de procesos zombi autorizados (2).

  **[!UICONTROL Warning]**: este indicador se muestra cuando el número de procesos zombis se acerca a 2.

  **[!UICONTROL Alert]**: este indicador se muestra cuando el número de procesos zombis alcanza 2.

#### Personalizar indicadores {#customized-indicators}

Adobe Campaign permite personalizar los indicadores, tal como se detalla a continuación:

1. Crear un **.sh** y asígnele un nombre **[!UICONTROL cust_indicators.sh]** .
1. Añada los indicadores personalizados a este archivo. Por ejemplo:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   o

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Guarde el archivo en. **[!UICONTROL usr/local/neolane/nl6]** carpeta.

Adobe Campaign llama a este archivo.

## Informes SMTP {#smtp-reports}

Los informes de monitorización de envíos SMTP están integrados en la plataforma de Adobe Campaign. Se puede acceder a ellas a través de la consola o mediante el acceso a la Web.

Estos informes muestran las estadísticas de envío SMTP y los errores SMTP por dominio. Para acceder a ellos, el operador debe tener **Administration** derechos.

Se agrupan en **Monitorización** > &#39;Monitorización SMTP&#39;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* La información relacionada con el control SMTP solo está disponible si se ha activado el canal de correo electrónico.
>* El **[!UICONTROL SMTP sending statistics]** solo se ofrecen si el servidor de estadísticas se inicia en la instancia.
>

### Estadísticas de envío SMTP {#smtp-sending-statistics}

El **[!UICONTROL SMTP sending statistics]** Este informe permite controlar la actividad del servidor. Muestra una síntesis de cada uno de los equipos.

![](assets/smtp_stats_report.png)

La lista de indicadores de este informe se muestra debajo del gráfico.

1. Número total de mensajes enviados.
1. Representa mensajes de entrada/salida:

   * Línea azul: mensajes listos para enviar que llegaron al Shaper, es decir, la última etapa antes de enviar SMTP (coincide con los datos entrantes).

   * Línea verde: los mensajes enviados correctamente (coincide con los datos salientes).

   * Línea roja: mensajes abandonados por el Formador, devueltos al **mta** (coincide con los datos rechazados en esta recuperación).

   Estos valores se expresan en número de mensajes por hora.

1. Representa dos colas del Shaper:

   * Blue curve: cola de mensajes activos. Estos mensajes se enviarán lo antes posible.

   * Curva de Kaki: la cola &quot;diferida&quot;. Estos mensajes no se pueden devolver por el momento debido a la restricción o porque no hay ninguna conexión disponible con el destino. Los reintentos se realizarán cada 5 segundos, 10 segundos, 20 segundos, 40 segundos, 2 minutos, etc. para el definido **MaxAgeSec** tiempo antes de ser abandonado.

1. Este gráfico muestra un detalle de los mensajes abandonados (curva roja en el segundo gráfico): muestra la proporción de mensajes abandonados sin reintentos (malva) en comparación con los mensajes cuyo envío falló (rojo). Esto permite ver la proporción de mensajes que no se han procesado dentro del periodo concedido debido a limitaciones del servidor de estadísticas (regulación) o a la no disponibilidad del servidor remoto.
1. Conexiones SMTP abiertas o en proceso de apertura.
1. Estimación del número de **mtachild**.

>[!NOTE]
>
>Este informe está relacionado con el estado del componente Formador de tráfico de correo electrónico.

### Errores de SMTP por dominio {#smtp-errors-per-domain}

Este informe permite ver los errores de entrega, durante un periodo establecido, desglosados por dominio.

>[!NOTE]
>
>El **minConnectionsToLog**, **minErrorsToLog** y **minMessagesToLog** opciones del **serverConf.xml** define los umbrales por encima de los cuales se tienen en cuenta las estadísticas de conexión.

![](assets/smtp_error_report.png)

La lista de indicadores para este informe se muestra debajo de la tabla.

* El **Dominio** contiene el nombre del dominio al que se envían los mensajes (o el nombre de dominio real, yahoo.com para yahoo.fr por ejemplo),
* El **Cnx** La columna muestra el número de conexiones SMTP abiertas para este dominio.
* El **Enviado** corresponde al número de mensajes enviados a este dominio,
* El **Volumen** muestra el volumen de mensajes que se han intentado enviar a este dominio (valor aproximado),
* El **Errores** muestra un indicador de volumen de errores en este dominio durante el periodo,
* El **Última respuesta** muestra el último mensaje de respuesta SMTP recibido para este dominio,
* El **Fecha** muestra la fecha de la última respuesta SMTP recibida para este dominio.

>[!NOTE]
>
>Los valores mostrados en **Cnx**, **Enviado**, y **Volumen** se calculan con respecto al periodo seleccionado en la variable **[!UICONTROL Period]** field.

Haga clic en un nombre de dominio para ver sus errores.

Se clasifican por PublicId: este identificador corresponde a una dirección IP compartida por varios mta de Adobe Campaign detrás de un enrutador. El servidor de estadísticas utiliza este identificador para memorizar las estadísticas de conexión y envío entre este punto de inicio y el servidor de destino.

![](assets/smtp_error_report_details.png)

El **[!UICONTROL Owner of domain]** Este campo permite agrupar varios nombres de dominio con la misma etiqueta. En la vista de informe inicial, todos los nombres de dominio MX se asociarán a este propietario.

Haga clic en un identificador PublicId para ver más detalles.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>El porcentaje de errores se representa mediante dos gráficos. La primera es una barra de progreso horizontal sobre un fondo negro. El segundo gráfico es cronológico. El periodo seleccionado se divide en doce intervalos de tiempo, cada uno de los cuales se representa mediante una barra de progreso vertical. En ambas representaciones, si no se ha detectado ningún error, la barra es negra. El color de la barra depende del porcentaje de errores encontrados (amarillo, luego naranja y, por último, rojo). El color gris significa que no se ha encontrado ningún volumen de datos significativo. Es posible mostrar el porcentaje exacto de errores colocando el cursor en el gráfico.

>[!NOTE]
>
>Para obtener más información sobre los errores de SMTP y su administración en Adobe Campaign, consulte [esta sección](../../installation/using/email-deliverability.md).

## Informe de facturación {#billing-report}

El **[!UICONTROL Billing]** Un flujo de trabajo técnico envía el informe de actividad del sistema al operador &quot;facturación&quot; por correo electrónico. Se activa de forma predeterminada el día 25 de cada mes en la instancia de Marketing.

El flujo de trabajo técnico se encuentra en una subcarpeta del siguiente nodo: **Administration** > **Producción** > **Flujos de trabajo técnicos**.

![](assets/billing.png)

Una vez que el flujo de trabajo se inicie cada 25 días del mes, el operador de facturación recibirá el siguiente informe en su bandeja de entrada.

![](assets/billing_2.png)

Las siguientes métricas están disponibles para realizar un seguimiento de las entregas:

* **[!UICONTROL Start date]** : Fecha de inicio del envío. Tenga en cuenta que puede ser anterior a la fecha &quot;desde&quot; del informe.
* **[!UICONTROL Label]** : etiqueta del envío. Las entregas que tienen menos de 100 mensajes para enviar se consideran demasiado pequeños y, por lo tanto, se acumulan por fecha de inicio, en cuyo caso la etiqueta muestra el número de acumulados, por ejemplo,. [Suma de 3 pequeños envíos].
* **[!UICONTROL Total volume]** : Volumen total de bytes transferidos para la entrega.
* **[!UICONTROL Avg volume]** : Volumen promedio de bytes transferidos. Este es el resultado de la siguiente fórmula **(volumen total/mensajes)**, que es la base de cálculo del **[!UICONTROL Multiplier]** métrica.
* **[!UICONTROL Messages]** : número de mensajes enviados. Esto incluye tanto los mensajes enviados correctamente como los reintentos (después de la recepción de un mensaje de rechazo del servidor contactado).
* **[!UICONTROL Multiplier (x)]** : el valor del multiplicador se deduce del volumen promedio de los mensajes.
* **[!UICONTROL Count]** : Resultado de la multiplicación de los mensajes y el multiplicador.

## Monitorización automática {#automatic-monitoring}

Adobe Campaign ofrece varios métodos de monitorización automática, que se presentan a continuación.

### Línea de comando {#command-line}

Comando

**monitor nlserver**

Permite enumerar un conjunto de indicadores en los módulos de Adobe Campaign y en el sistema.

Genera resultados en un formato XML fácilmente procesable.

Este comando también se puede ejecutar con la variable **-falta** , que enumera los procesos que faltan en esta instancia cuando los archivos de configuración dicen que deben ejecutarse.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Información publicada por el servidor {#information-published-by-the-server}

#### /r/test {#r-test}

El **http(s)://`<application>`/r/test** se utiliza para probar el servidor de redirección. Se recomienda utilizar este mismo método para probar los servidores frontales utilizados para el seguimiento. Esta página también se puede utilizar para probar un Dispatcher de carga.

Muestra una línea como esta en formato XML:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Frecuencia**: esta prueba no utiliza ninguna carga y por lo tanto se puede ejecutar muy a menudo (por ejemplo, una vez cada segundo).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Esta **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  funciona del mismo modo que su homólogo de red: prueba una consulta completa que pasa por apache/tomcat/web module/database y se carga en el cliente. Si todo funciona correctamente, devuelve el valor &quot;OK&quot;. Se recomienda ejecutar esta prueba en equipos con acceso a las bases de datos (mta y encuestas, por ejemplo).

**Uso**: se debe pasar un token de sesión asociado con el inicio de sesión de un operador como argumento para iniciar sesión de forma remota (consulte la sugerencia en [Supervisión automática mediante scripts de Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

Por ejemplo:

![](assets/ncs_monitoring_ping.png)

El nombre del operador y el inicio de sesión deben configurarse previamente en la consola del cliente de Adobe Campaign con derechos de base de datos.

![](assets/ncs_operators_rights_01.png)

**Frecuencia**: esta es una prueba que utiliza muy poco ancho de banda. Por lo tanto, se puede ejecutar con bastante frecuencia, aunque no más de una vez por minuto.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Se trata de una prueba para comprobar que un operador puede acceder al servidor de Adobe Campaign a través de una página web; la misma página web que la accedida a través de los menús de la consola del cliente. Puede llamar a esta página desde sus herramientas de vigilancia (Tivoli, Nagios, etc.).

![](assets/ncs_monitoring_web.png)

**Uso**: se debe utilizar como argumento un token de sesión asociado con un inicio de sesión del operador que le permite conectarse a la instancia (consulte la sugerencia en [Supervisión automática mediante scripts de Adobe Campaign](#automatic-monitoring-via-adobe-campaign-scripts)).

El operador y su inicio de sesión deben configurarse previamente en la consola del cliente de Adobe Campaign con los derechos y restricciones de base de datos adecuados.

**Frecuencia**: se trata de una prueba de servidor completa y no necesita ejecutarse con frecuencia (puede realizarse una vez cada diez minutos, por ejemplo).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

Esta **jsp** representa el punto de entrada de las API de aplicaciones de Adobe Campaign. Por lo tanto, puede proporcionar un seguimiento detallado de la aplicación. También se puede utilizar para monitorizar los servicios web de Adobe Campaign. Se utiliza en nuestros scripts de monitorización, pero tenga en cuenta que solo es para usuarios avanzados.

### Monitorización basada en tipos de implementación {#monitoring-based-on-deployment-types}

Adobe Campaign habilita varias configuraciones de implementación (para obtener más información, consulte [esta sección](../../installation/using/hosting-models.md)). En esta sección se detallan las distintas técnicas de monitorización automática que se deben aplicar según el tipo de instalación.

<table> 
 <thead> 
  <tr> 
   <th> Tipo de implementación </th> 
   <th> Monitorización </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Independiente </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> y <span class="uicontrol">/nl/jsp/monitor.jsp</span> en el servidor de Adobe Campaign</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Estándar </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> y <span class="uicontrol">/nl/jsp/ping.jsp</span> en los servidores frontales</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> en el servidor de aplicaciones</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Empresa </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> y <span class="uicontrol">/nl/jsp/ping.jsp</span> en los servidores frontales</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> y <span class="uicontrol">/nl/jsp/monitor.jsp</span> en el servidor de aplicaciones</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Intermediario </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> en el servidor de aplicaciones</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Supervisión automática mediante scripts de Adobe Campaign {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign puede proporcionar una herramienta de monitorización de instancias (netreport) que le permite enviar un informe por correo electrónico con respecto a las anomalías detectadas.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Esta herramienta se puede utilizar para monitorizar las instancias, pero Adobe Campaign no la admite. Póngase en contacto con el administrador de Campaign para obtener más información.

### Elementos necesarios {#required-elements}

Se requieren las siguientes precauciones previas a la instalación para el control automático:

* Debe tener el **netreport.tgz** (Instalación de Linux) o **netreport.zip** archivos (instalación de Windows),
* Le recomendamos encarecidamente que no instale la monitorización en la máquina a monitorizar,
* debe instalarse en un equipo con un JRE o un JDK,
* en Linux, la máquina a monitorizar debe tener el **bc** paquete. Para obtener más información, consulte [esta sección](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Procedimiento de instalación {#installation-procedure}

El procedimiento de instalación es el siguiente:

1. En la consola, cree un nuevo operador si es necesario (el usuario de &quot;monitorización&quot; ya existe), pero no asigne ningún derecho.
1. Ejecute la extracción del archivo.
1. Lea el **readme** archivo.
1. Actualice el **netconf.xml** archivo de configuración.
1. Actualice el **netreport.bat** (Windows) o **netreport.sh** (Linux).

### Configuración del archivo netconf.xml {#configuring-the-netconf-xml-file}

El archivo de configuración XML contiene los siguientes elementos:

* [Elemento &quot;Properties&quot;](#properties--element)
* [Elemento &quot;Instance&quot;](#instance--element)
* [Elemento &quot;Host&quot;](#host--element)
* [Subelementos](#sub-elements)

Este es un ejemplo de configuración:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>Puede especificar varias configuraciones añadiendo un sufijo a la variable **netconf.xml** por ejemplo, **netconf-dev.xml**, **netconf-prod.xml**, etc. A continuación, especifique la configuración que se utilizará para ejecutar netreport en **netreport.bat** o **netreport.sh** archivos al agregar **$JAVA_HOME/bin/java netreport dev** o **@%JAVA_HOME%binjava netreport prod** por ejemplo.

>[!IMPORTANT]
>
>Para el **control** para que funcione, la máquina en la que se ejecuta netreport debe estar en una zona de seguridad que se encuentre en **sessionTokenOnly** modo. Si no se ha especificado ninguna máscara IP de confianza para este operador, la zona de seguridad también debe estar en **allowEmptyPassword** y **allowUserPassword** modo.

#### Elemento &quot;Properties&quot; {#properties--element}

Este elemento se utiliza para rellenar la configuración de correos electrónicos, por ejemplo:

* **mailServer**: servidor SMTP utilizado para enviar correos electrónicos (por ejemplo, smtp.domain.net).
* **mailFrom**: dirección de correo electrónico del remitente del informe (por ejemplo, monitoring@domain.net).
* **recipientList**: la lista de direcciones de correo electrónico de los destinatarios de monitorización. Las direcciones deben estar separadas por comas (sin espacios).
* &#39;**noche**&#39; (opcional) se utiliza para evitar el envío de correos electrónicos entre el periodo de tiempo especificado. En su lugar, los datos se consolidan y se envía un correo electrónico con la actividad de la noche después de la hora de finalización (7:00 de forma predeterminada).
* El **buildRange** sub-element (opcional) permite especificar un número mínimo y máximo de compilación. Se generará un error para todos los equipos cuyo número de compilación no esté dentro de este intervalo

  ```
  <buildRange minimum="0000" maximum="9999"/>
  ```

* Puede añadir un **`<sla>`** (opcional) subelemento en el **propiedades** Elemento. Se generará un archivo de registro cada vez que se ejecute netreport. El nombre del archivo contiene el nombre de la configuración y la fecha y hora, por ejemplo **dev_06_12_13_16_47_05.tmp**. El archivo contiene la siguiente información: nombre de instancia, nombre del equipo, nivel de gravedad, (de 0 a 3, de menos crítico a más crítico), fecha (formato de marca de tiempo), tiempo transcurrido (en milisegundos) entre la consulta y la respuesta, servicio utilizado (http, ncs, ncsex, redir). Esta información está separada por marcas de tabulación y saltos de línea al final de cada servicio.

>[!NOTE]
>
>El **persiststHtmlFile** con el valor &quot;true&quot; en **`<property>`** se utiliza para registrar el último estado de monitorización en el archivo **netreport.md**. Este archivo se guarda en el directorio de instalación.

#### Elemento &quot;Instance&quot; {#instance--element}

Este elemento permite agrupar varios equipos (hosts) en la misma instancia. Los nombres de instancia aparecen en la primera parte del correo electrónico de monitorización. Puede hacer clic en el nombre de una instancia para acceder a los detalles de cada equipo.

```
instance name="instance-name" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: nombre de instancia que aparecerá en la primera parte del correo electrónico.
* **recipientList** (opcional): permite enviar un informe de monitorización por correo electrónico con respecto a una instancia en particular.

#### Elemento &quot;Host&quot; {#host--element}

Este elemento configura la monitorización de un servidor determinado en el host, es decir,

* **name**: nombre de la máquina que se va a monitorizar.
* **alias** (opcional): nombre de la máquina supervisada tal como aparecerá en el informe.
* **sessionToken**: proporciona autenticación de inicio de sesión mediante un token de sesión autorizado.

  Para configurar el token de sesión, seleccione la **control** en la consola de Adobe Campaign. En el **Derechos de acceso** , especifique las direcciones IP de los equipos autorizados para supervisar esta instancia. A continuación, podrá conectarse a la página de monitorización desde esos equipos mediante el **control** y sin necesidad de especificar una contraseña.

  ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (opcional): permite ordenar los errores para que se muestren por nivel de gravedad. Los valores posibles son &quot;0&quot; (se muestran todos los niveles), &quot;1&quot; (solo se muestran los errores altos y críticos) y &quot;2&quot; (solo se muestran los errores críticos). Si no se proporciona este atributo, se muestran todos los niveles de error.
* **filter** (opcional): permite excluir ciertos errores de flujo de trabajo, por ejemplo **filter=&quot;wkf;wkf1&quot;**. Las etiquetas de flujo de trabajo deben separarse con punto y coma.

#### Subelementos {#sub-elements}

* **tcp**: comprueba si el servidor está activo o caído. Debe introducir un número de puerto.
* **http**: comprueba que el servidor web existe (el servidor de aplicaciones está operativo).
* **ncs**: comprueba los procesos en la instancia introducida en el atributo &quot;instancia&quot; (errores de flujo de trabajo, uso de memoria, etc.). El **incluido** (obligatorio) le da la opción de mostrar los procesos inactivos (valores &quot;true&quot; o &quot;false&quot;).
* **redir**: comprueba el seguimiento.

En la mayoría de los casos, solo la variable **ncs** y **redir** se pueden conservar los subelementos.

En cualquier caso, ciertos nodos se pueden sobrecargar en los subelementos (por ejemplo, el nodo ) **port=75** para sobrecargar el puerto utilizado para la conexión http, ncs o redir):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

En el **ncs**, **redir** y **http** subelementos, se puede añadir la variable **isSecure** attribute (opcional) para elegir si desea utilizar o no el protocolo https (valores &quot;true&quot; o &quot;false&quot;). Si no se proporciona este atributo, se utiliza el protocolo http.

### Configuración del archivo netreport.bat o netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Para configurarlo, edite este archivo e indique en qué directorio está instalado JRE o JDK.

### Iniciar la monitorización {#launching-monitoring}

Para iniciar la monitorización, ejecute el **netreport.bat** o **netreport.sh** a intervalos regulares mediante un script. Se envía un informe después de la primera ejecución y, a continuación, solo en caso de cambio de estado.

### Prueba de monitorización {#testing-monitoring}

Para probar la monitorización, ejecute el **netreport.bat** o **netreport.sh** archivo.

Se envía un correo electrónico a los destinatarios especificados en la variable **recipientList** de la **netconf.xml** archivo.
