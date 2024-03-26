---
product: campaign
title: Duplicación de entornos
description: Duplicación de entornos
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 3%

---

# Duplicación de entornos{#duplicating-environments}



## Introducción {#introduction}

### Información general {#overview}

>[!IMPORTANT]
>
>Si no tiene acceso al servidor y a la base de datos (entornos alojados), no podrá realizar los procedimientos que se describen a continuación. Póngase en contacto con el Adobe.

El uso de Adobe Campaign requiere la instalación y configuración de uno o más entornos: desarrollo, prueba, preproducción, producción, etc.

Cada entorno contiene una instancia de Adobe Campaign y cada instancia de Adobe Campaign está vinculada a una o más bases de datos. El servidor de aplicaciones puede ejecutar uno o más procesos: casi todos tienen acceso directo a la base de datos de instancias.

Esta sección detalla los procesos que se deben aplicar para duplicar un entorno de Adobe Campaign, es decir, restaurar un entorno de origen en un entorno de destino, lo que da como resultado dos entornos de trabajo idénticos.

Para ello, siga los siguientes pasos:

1. Crear una copia de las bases de datos en todas las instancias del entorno de origen.
1. Restaurar estas copias en todas las instancias del entorno de destino.
1. Ejecute el **nms:congelaciónInstance.js** script de cauterización en el entorno de destino antes de iniciarlo.

   Este proceso no afecta a los servidores ni a su configuración.

   >[!NOTE]
   >
   >En el contexto de Adobe Campaign, una **cauterización** combina acciones que permiten detener todos los procesos que interactúan con el exterior: registros, seguimiento, envíos, flujos de trabajo de la campaña, etc.\
   >Este paso es necesario para evitar enviar mensajes varias veces (una vez desde el entorno nominal y otra desde el entorno duplicado).

   >[!IMPORTANT]
   >
   >Un entorno puede contener varias instancias. Cada instancia de Adobe Campaign está sujeta a un contrato de licencia. Compruebe el acuerdo de licencia para ver cuántos entornos puede tener.\
   >El siguiente procedimiento le permite transferir un entorno sin afectar al número de entornos e instancias que ha instalado.

### Antes de comenzar {#before-you-start}

>[!IMPORTANT]
>
>Se recomienda encarecidamente ejecutar una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destino antes de iniciar el proceso de transferencia. De este modo, si se produce un problema, podrá restaurar las copias de seguridad y volver a la configuración inicial.

Para que este proceso funcione, los entornos de origen y destino deben tener el mismo número de instancias, el mismo propósito (instancia de marketing, instancia de envío) y configuraciones similares. La configuración técnica debe cumplir con los requisitos previos del software. Se deben instalar los mismos componentes en ambos entornos.

## Implementación {#implementation}

### Procedimiento de transferencia {#transfer-procedure}

Esta sección le ayudará a comprender los pasos necesarios para transferir un entorno de origen a un entorno de destino mediante un caso práctico: nuestro objetivo aquí es restaurar un entorno de producción (**picar** ) a un entorno de desarrollo (**dev** ) para trabajar en un contexto lo más cercano posible a la plataforma &quot;en directo&quot;.

Los siguientes pasos deben realizarse con mucho cuidado: es posible que algunos procesos aún estén en curso cuando se copian las bases de datos del entorno de origen. La cauterización (paso 3 a continuación) evita que los mensajes se envíen dos veces y mantiene la coherencia de los datos.

>[!IMPORTANT]
>
>* El siguiente procedimiento es válido en lenguaje PostgreSQL. Si el lenguaje SQL es diferente (Oracle, por ejemplo), las consultas SQL deben adaptarse.
>* Los comandos siguientes se aplican en el contexto de una **picar** instancia y una **dev** en PostgreSQL.
>

### Paso 1: Realizar una copia de seguridad de los datos del entorno de origen (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiar las bases de datos

Comience copiando todas las bases de datos de entorno de origen. La operación depende del motor de base de datos y es responsabilidad del administrador de la base de datos.

En PostgreSQL, el comando es:

```
pg_dump mydatabase > mydatabase.sql
```

### Paso 2: Exportación de la configuración del entorno de destino (dev) {#step-2---export-the-target-environment-configuration--dev-}

La mayoría de los elementos de configuración son diferentes para cada entorno: cuentas externas (intermediario, enrutamiento, etc.), opciones técnicas (nombre de plataforma, DatabaseId, direcciones de correo electrónico y URL predeterminadas, etc.).

Antes de guardar la base de datos de origen en la base de datos de destino, debe exportar la configuración del entorno de destino (dev). Para ello, exporte el contenido de estas dos tablas: **xtkoption** y **nmsextaccount**.

Esta exportación permite mantener la configuración de desarrollo y actualizar solo los datos de desarrollo (flujos de trabajo, plantillas, aplicaciones web, destinatarios, etc.).

Para ello, realice una exportación de paquetes para los dos elementos siguientes:

* Exporte el **xtk:opción** en un archivo options_dev.xml, sin los registros con los siguientes nombres internos: &quot;WdbcTimeZone&quot;, &quot;NmsServer_LastPostUpgrade&quot; y &quot;NmsBroadcast_RegexRules&quot;.
* En un archivo &quot;extaccount_dev.xml&quot;, exporte el **nms:extAccount** para todos los registros cuyo ID no sea 0 (@id &lt;> 0).

Compruebe que el número de opciones/cuentas exportadas sea igual al número de líneas que se exportarán en cada archivo.

>[!NOTE]
>
>El número de líneas que se van a exportar en una exportación de paquete es de 1000 líneas. Si el número de opciones o cuentas externas es superior a 1000, debe realizar varias exportaciones.
> 
>Para obtener más información, consulte [esta sección](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Cuando se exporta la tabla nmsextaccount, las contraseñas relacionadas con las cuentas externas (por ejemplo, contraseñas para intermediario, ejecución del centro de mensajes, SMPP, IMS y otras cuentas externas) no se exportan. Asegúrese de tener acceso a las contraseñas correctas por adelantado, ya que es posible que sea necesario volver a introducirlas después de que las cuentas externas se importen de nuevo en el entorno.

### Paso 3: Detener el entorno de destino (dev) {#step-3---stop-the-target-environment--dev-}

Debe detener los procesos de Adobe Campaign en todos los servidores del entorno de destino. Esta operación depende del sistema operativo.

Puede detener todos los procesos o sólo los que escriben en la base de datos.

Para detener todos los procesos, utilice los siguientes comandos:

* En Windows:

  ```
  net stop nlserver6
  ```

* En Linux:

  ```
  /etc/init.d/nlserver6 stop
  ```

Utilice el siguiente comando para comprobar que se han detenido todos los procesos:

```
nlserver pdump
```

>[!NOTE]
>
>En Windows, la variable **webmdl** El proceso puede seguir activo sin afectar a otras operaciones.

También puede comprobar que no hay procesos del sistema en ejecución.

Para ello, utilice el proceso siguiente:

* En Windows: abra el **Administrador de tareas** y compruebe que no hay **nlserver.exe** procesos.
* En Linux: ejecute el **ps aux | grep nlserver** y compruebe que no hay ninguna **nlserver** procesos.

### Paso 4: Restauración de las bases de datos en el entorno de destino (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Para restaurar las bases de datos de origen en el entorno de destino, utilice el siguiente comando:

```
psql mydatabase < mydatabase.sql
```

### Paso 5: Cauterización del entorno de destino (dev) {#step-5---cauterize-the-target-environment--dev-}

Para evitar errores de funcionamiento, los procesos vinculados a la entrega de entregas y la ejecución del flujo de trabajo no deben ejecutarse automáticamente cuando se active el entorno de destino.

Para ello, ejecute el siguiente comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Paso 6: Comprobar la cauterización {#step-6---check-cauterization}

1. Compruebe que la única parte de la entrega sea aquella cuyo ID esté establecido en 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Compruebe que la actualización del estado de entrega sea correcta:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Compruebe que la actualización del estado del flujo de trabajo sea correcta:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Paso 7: Reinicio del proceso web del entorno de destino (dev) {#step-7---restart-the-target-environment-web-process--dev-}

En el entorno de destino, reinicie los procesos de Adobe Campaign para todos los servidores.

>[!NOTE]
>
>Antes de reiniciar Adobe Campaign en **dev** entorno, puede aplicar un procedimiento de seguridad adicional: inicie el **web** solo módulo.
>  
>Para ello, edite el archivo de configuración de la instancia (**config-dev.xml**) y, a continuación, añada el carácter &quot;_&quot; antes de las opciones autoStart=&quot;true&quot; para cada módulo (mta, stat, etc.).

Ejecute el siguiente comando para iniciar el proceso web:

```
nlserver start web
```

Utilice el siguiente comando para comprobar que solo se ha iniciado el proceso web:

```
nlserver pdump
```

Compruebe que funciona el acceso a la consola del cliente.

### Paso 8: Importación de opciones y cuentas externas en el entorno de destino (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>En este paso solo debe iniciarse el proceso web. Si no es así, detenga otros procesos en ejecución antes de continuar

Sobre todo, compruebe los valores de varias líneas de los archivos antes de importarlos (por ejemplo: &quot;NmsTracking_Pointer&quot; para la tabla de opciones y las cuentas de envío o intermediarias para la tabla de cuentas externas)

Para importar la configuración desde la base de datos del entorno de destino (dev):

1. Abra Admin Console de la base de datos y purgue las cuentas externas (tabla nms:extAccount) cuyo ID no sea 0 (@id &lt;> 0).
1. En la consola de Adobe Campaign, importe el paquete options_dev.xml creado anteriormente mediante la funcionalidad de importación de paquetes.

   Compruebe que las opciones se hayan actualizado en la **[!UICONTROL Administration > Platform > Options]** nodo.

1. En la consola de Adobe Campaign, importe el archivo extaccount_dev.xml creado anteriormente mediante la funcionalidad de importación de paquetes

   Compruebe que las bases de datos externas se hayan importado realmente en el **[!UICONTROL Administration > Platform > External accounts]** .

### Paso 9: Reinicio de todos los procesos y cambio de usuarios (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Para iniciar los procesos de Adobe Campaign, utilice los siguientes comandos:

* En Windows:

  ```
  net start nlserver6
  ```

* En Linux:

  ```
  /etc/init.d/nlserver6 start
  ```

Utilice el siguiente comando para comprobar que se han iniciado los procesos:

```
nlserver pdump
```

Cambie de usuario para buscar los que ya existían en la plataforma de desarrollo.
