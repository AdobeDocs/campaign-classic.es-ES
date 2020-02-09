---
title: Duplicación de entornos
seo-title: Duplicación de entornos
description: Duplicación de entornos
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Duplicación de entornos{#duplicating-environments}

## Introducción {#introduction}

### Información general {#overview}

>[!CAUTION]
>
>Si no tiene acceso al servidor y a la base de datos (entornos alojados), no podrá realizar los procedimientos que se describen a continuación. Póngase en contacto con Adobe.

Para utilizar Adobe Campaign es necesario instalar y configurar uno o varios entornos: desarrollo, ensayo, preproducción, producción, etc.

Cada entorno contiene una instancia de Adobe Campaign y cada instancia de Adobe Campaign está vinculada a una o varias bases de datos. El servidor de aplicaciones puede ejecutar uno o varios procesos: casi todos ellos tienen acceso directo a la base de datos de instancias.

Esta sección detalla los procesos que se aplicarán para duplicar un entorno de Adobe Campaign, es decir, para restaurar un entorno de origen a un entorno de destino, lo que resulta en dos entornos de trabajo idénticos.

Para ello, siga los siguientes pasos:

1. Cree una copia de las bases de datos en todas las instancias del entorno de origen,
1. Restaure estas copias en todas las instancias del entorno de destino,
1. Ejecute la secuencia de comandos de cauterización **nms:congelinstance.js** en el entorno de destino antes de iniciarla.

   Este proceso no afecta a los servidores ni a su configuración.

   >[!NOTE]
   >
   >En el contexto de Adobe Campaign, una **cauterización** combina acciones que le permiten detener todos los procesos que interactúan con el exterior: registros, seguimiento, envíos, flujos de trabajo de campañas, etc.\
   >Este paso es necesario para evitar enviar mensajes varias veces (una desde el entorno nominal y otra desde el entorno duplicado).

   >[!CAUTION]
   >
   >Un entorno puede contener varias instancias. Cada instancia de Adobe Campaign está sujeta a un contrato de licencia. Compruebe el contrato de licencia para ver cuántos entornos puede tener.\
   >El procedimiento siguiente le permite transferir un entorno sin afectar al número de entornos e instancias que ha instalado.

### Antes de empezar {#before-you-start}

>[!CAUTION]
>
>Recomendamos encarecidamente ejecutar una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destino antes de iniciar el proceso de transferencia. De este modo, si se produce un problema, podrá restaurar las copias de seguridad y volver a la configuración inicial.

Para que este proceso funcione, los entornos de origen y destino deben tener el mismo número de instancias, el mismo propósito (instancia de marketing, instancia de entrega) y configuraciones similares. La configuración técnica debe cumplir los requisitos previos del software. Los mismos componentes deben instalarse en ambos entornos.

## Implementación {#implementation}

### Procedimiento de transferencia {#transfer-procedure}

Esta sección le ayudará a comprender los pasos necesarios para transferir un entorno de origen a un entorno de destino mediante un estudio de caso: nuestro objetivo aquí es restaurar un entorno de producción (**prod** instance) a un entorno de desarrollo (**dev** instance) para trabajar en un contexto lo más cercano posible a la plataforma &#39;live&#39;.

Los siguientes pasos deben realizarse con sumo cuidado: es posible que algunos procesos sigan en curso cuando se copian las bases de datos del entorno de origen. La cauterización (paso 3 a continuación) evita que los mensajes se envíen dos veces y mantiene la coherencia de los datos.

>[!CAUTION]
>
>* El siguiente procedimiento es válido en lenguaje PostgreSQL. Si el lenguaje SQL es diferente (Oracle, por ejemplo), las consultas SQL deben adaptarse.
>* Los siguientes comandos se aplican en el contexto de una instancia de **prod** y una instancia de **dev** en PostgreSQL.
>



### Paso 1: Realizar una copia de seguridad de los datos del entorno de origen (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiar las bases de datos

Comience copiando todas las bases de datos del entorno de origen. La operación depende del motor de la base de datos y es responsabilidad del administrador de la base de datos.

En PostgreSQL, el comando es:

```
pg_dump mydatabase > mydatabase.sql
```

### Paso 2: Exportar la configuración del entorno de destino (dev) {#step-2---export-the-target-environment-configuration--dev-}

La mayoría de los elementos de configuración son diferentes para cada entorno: cuentas externas (fuentes intermedias, enrutamiento, etc.), opciones técnicas (nombre de plataforma, DatabaseId, direcciones de correo electrónico y direcciones URL predeterminadas, etc.).

Antes de guardar la base de datos de origen en la base de datos de destino, debe exportar la configuración del entorno de destino (dev). Para ello, exporte el contenido de estas dos tablas: **xtkoption** y **nmsextaccount**.

Esta exportación permite mantener la configuración de desarrollo y actualizar únicamente los datos de desarrollo (flujos de trabajo, plantillas, aplicaciones web, destinatarios, etc.).

Para ello, realice una exportación de paquetes para los dos elementos siguientes:

* Exporte la tabla **xtk:option** a un archivo &#39;options_dev.xml&#39;, sin los registros con los siguientes nombres internos: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; y &#39;NmsBroadcast_RegexRules&#39;.
* En un archivo &#39;extaccount_dev.xml&#39;, exporte la tabla **nms:extAccount** para todos los registros cuyo ID no sea 0 (@id &lt;> 0).

Compruebe que el número de opciones/cuentas exportadas es igual al número de líneas que se van a exportar en cada archivo.

>[!NOTE]
>
>El número de líneas que exportar en una exportación de paquete es de 1000 líneas. Si el número de opciones o cuentas externas es superior a 1000, debe realizar varias exportaciones.
> 
>Para obtener más información, consulte [esta sección](../../platform/using/working-with-data-packages.md#exporting-packages).

### Paso 3: Detenga el entorno de destino (dev) {#step-3---stop-the-target-environment--dev-}

Debe detener los procesos de Adobe Campaign en todos los servidores de entorno de destino. Esta operación depende del sistema operativo.

Puede detener todos los procesos, o solo los que escriben en la base de datos.

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
>En Windows, el proceso **webmdl** puede seguir activo sin afectar a otras operaciones.

También puede comprobar que no hay procesos del sistema en ejecución.

Para ello, utilice el proceso siguiente:

* En Windows: abra el Administrador **de tareas** y compruebe que no hay procesos **nlserver.exe** .
* En Linux: ejecutar **ps aux| grep nlserver** y compruebe que no hay procesos **nlserver** .

### Paso 4: Restaure las bases de datos en el entorno de destino (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Para restaurar las bases de datos de origen en el entorno de destino, utilice el siguiente comando:

```
psql mydatabase < mydatabase.sql
```

### Paso 5: Cauterización del entorno de destino (dev) {#step-5---cauterize-the-target-environment--dev-}

Para evitar errores de funcionamiento, los procesos vinculados al envío de entregas y la ejecución del flujo de trabajo no deben ejecutarse automáticamente cuando se activa el entorno de destino.

Para ello, ejecute el siguiente comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Paso 6: compruebe la cauterización {#step-6---check-cauterization}

1. Compruebe que la única pieza de entrega es la que tiene el ID establecido en 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Compruebe que la actualización del estado de entrega es correcta:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Compruebe que la actualización de estado del flujo de trabajo es correcta:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Paso 7: Reinicie el proceso Web del entorno de destino (dev) {#step-7---restart-the-target-environment-web-process--dev-}

En el entorno de destino, vuelva a iniciar los procesos de Adobe Campaign para todos los servidores.

>[!NOTE]
>
>Antes de reiniciar Adobe Campaign en el entorno de **desarrollo** , puede aplicar un procedimiento de seguridad adicional: solo inicie el módulo **web** .
>  
>Para ello, edite el archivo de configuración de su instancia (**config-dev.xml**) y luego agregue el carácter &quot;_&quot; antes de las opciones autoStart=&quot;true&quot; para cada módulo (mta, stat, etc.).

Ejecute el siguiente comando para iniciar el proceso Web:

```
nlserver start web
```

Utilice el siguiente comando para comprobar que solo se ha iniciado el proceso web:

```
nlserver pdump
```

Compruebe que el acceso a las funciones de la consola de cliente.

### Paso 8: Importar opciones y cuentas externas en el entorno de destino (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>Sólo el proceso Web debe iniciarse en este paso. Si no es así, detenga otros procesos en ejecución antes de continuar

Por encima de todo, compruebe los valores de varias líneas de los archivos antes de realizar la importación (por ejemplo: &#39;NmsTracking_Pointer&#39; para la tabla de opciones y las cuentas de entrega o de abastecimiento intermedio para la tabla de cuenta externa)

Para importar la configuración desde la base de datos de entorno de destino (dev):

1. Abra la consola de administración de la base de datos y purgue las cuentas externas (tabla nms:extAccount) cuyo ID no sea 0 (@id &lt;> 0).
1. En la consola de Adobe Campaign, importe el paquete options_dev.xml creado anteriormente mediante la funcionalidad de importación de paquetes.

   Compruebe que las opciones se hayan actualizado en el **[!UICONTROL Administration > Platform > Options]** nodo.

1. En la consola de Adobe Campaign, importe extaccount_dev.xml creado anteriormente mediante la funcionalidad de paquetes de importación

   Compruebe que las bases de datos externas se hayan importado en la **[!UICONTROL Administration > Platform > External accounts]** .

### Paso 9: Reinicie todos los procesos y cambie los usuarios (dev) {#step-9---restart-all-processes-and-change-users--dev-}

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

Cambie los usuarios para encontrar los usuarios que ya existían en la plataforma dev.
