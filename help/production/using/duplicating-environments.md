---
product: campaign
title: Duplicación de entornos
description: Duplicación de entornos
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 2%

---

# Duplicación de entornos{#duplicating-environments}

## Introducción {#introduction}

### Información general {#overview}

>[!IMPORTANT]
>
>Si no tiene acceso al servidor y a la base de datos (entornos alojados), no podrá realizar los procedimientos que se describen a continuación. Póngase en contacto con el Adobe.

El uso de Adobe Campaign requiere la instalación y configuración de uno o varios entornos: desarrollo, prueba, preproducción, producción, etc.

Cada entorno contiene una instancia de Adobe Campaign y cada instancia de Adobe Campaign está vinculada a una o más bases de datos. El servidor de aplicaciones puede ejecutar uno o más procesos: casi todos ellos tienen acceso directo a la base de datos de instancias.

Esta sección detalla los procesos que se deben aplicar para duplicar un entorno de Adobe Campaign, es decir, para restaurar un entorno de origen a un entorno de destino, lo que resulta en dos entornos de trabajo idénticos.

Para ello, siga los siguientes pasos:

1. Cree una copia de las bases de datos en todas las instancias del entorno de origen.
1. Restaure estas copias en todas las instancias del entorno de destino,
1. Ejecute el script de cauterización **nms:frozenInstance.js** en el entorno de destino antes de iniciarlo.

   Este proceso no afecta a los servidores ni a su configuración.

   >[!NOTE]
   >
   >En el contexto de Adobe Campaign, una **cauterización** combina acciones que le permiten detener todos los procesos que interactúan con el exterior: registros, seguimiento, envíos, flujos de trabajo de campaña, etc.\
   >Este paso es necesario para evitar enviar mensajes varias veces (una desde el entorno nominal y otra desde el entorno duplicado).

   >[!IMPORTANT]
   >
   >Un entorno puede contener varias instancias. Cada instancia de Adobe Campaign está sujeta a un contrato de licencia. Compruebe el acuerdo de licencia para ver cuántos entornos puede tener.\
   >El procedimiento siguiente le permite transferir un entorno sin afectar al número de entornos y instancias que ha instalado.

### Antes de comenzar {#before-you-start}

>[!IMPORTANT]
>
>Se recomienda ejecutar una copia de seguridad completa de las bases de datos para todas las instancias de los entornos de origen y destino antes de iniciar el proceso de transferencia. De este modo, si se produce un problema, podrá restaurar las copias de seguridad y volver a la configuración inicial.

Para que este proceso funcione, los entornos de origen y de destino deben tener el mismo número de instancias, el mismo propósito (instancia de marketing, instancia de entrega) y configuraciones similares. La configuración técnica debe cumplir con los requisitos previos del software. Los mismos componentes deben estar instalados en ambos entornos.

## Implementación {#implementation}

### Procedimiento de transferencia {#transfer-procedure}

Esta sección le ayudará a comprender los pasos necesarios para transferir un entorno de origen a un entorno de destino mediante un caso práctico: nuestro objetivo aquí es restaurar un entorno de producción (**prod** instancia) a un entorno de desarrollo (**dev** instancia) para que funcione en un contexto lo más cercano posible a la plataforma &quot;en directo&quot;.

Los siguientes pasos deben realizarse con bueno cuidado: es posible que algunos procesos estén en curso cuando se copien las bases de datos del entorno de origen. La cauterización (paso 3 a continuación) evita que los mensajes se envíen dos veces y mantiene la coherencia de los datos.

>[!IMPORTANT]
>
>* El siguiente procedimiento es válido en lenguaje PostgreSQL. Si el lenguaje SQL es diferente (Oracle, por ejemplo), las consultas SQL deben adaptarse.
>* Los siguientes comandos se aplican en el contexto de una instancia **prod** y una instancia **dev** en PostgreSQL.

>



### Paso 1: Realizar una copia de seguridad de los datos del entorno de origen (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiar las bases de datos

Comience copiando todas las bases de datos del entorno de origen. La operación depende del motor de la base de datos y es responsabilidad del administrador de la base de datos.

En PostgreSQL, el comando es:

```
pg_dump mydatabase > mydatabase.sql
```

### Paso 2: Exportación de la configuración del entorno de destino (dev) {#step-2---export-the-target-environment-configuration--dev-}

La mayoría de los elementos de configuración son diferentes para cada entorno: cuentas externas (intermediario, enrutamiento, etc.), opciones técnicas (nombre de plataforma, DatabaseId, direcciones de correo electrónico y direcciones URL predeterminadas, etc.).

Antes de guardar la base de datos de origen en la base de datos de destino, debe exportar la configuración del entorno de destino (dev). Para ello, exporte el contenido de estas dos tablas: **xtkoption** y **nmsextaccount**.

Esta exportación permite mantener la configuración de desarrollo y actualizar solo los datos de desarrollo (flujos de trabajo, plantillas, aplicaciones web, destinatarios, etc.).

Para ello, realice una exportación de paquetes para los dos elementos siguientes:

* Exporte la tabla **xtk:option** a un archivo &#39;options_dev.xml&#39;, sin los registros con los siguientes nombres internos: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; y &#39;NmsBroadcast_RegexRules&#39;.
* En un archivo extaccount_dev.xml, exporte la tabla **nms:extAccount** para todos los registros cuyo ID no sea 0 (@id &lt;> 0).

Compruebe que el número de opciones/cuentas exportadas sea igual al número de líneas que se exportan en cada archivo.

>[!NOTE]
>
>El número de líneas que se exportan en una exportación de paquetes es de 1000 líneas. Si el número de opciones o cuentas externas es superior a 1000, debe realizar varias exportaciones.
> 
>Para obtener más información, consulte [esta sección](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Cuando se exporta la tabla nmsextaccount, las contraseñas relacionadas con las cuentas externas (por ejemplo, contraseñas para Mid-sourcing, Message Center Execution, SMPP, IMS y otras cuentas externas) no se exportan. Asegúrese de tener acceso a las contraseñas correctas con antelación, ya que es posible que tengan que volver a introducirse después de importar las cuentas externas de nuevo en el entorno.

### Paso 3: Detenga el entorno de destino (dev) {#step-3---stop-the-target-environment--dev-}

Debe detener los procesos de Adobe Campaign en todos los servidores de entorno de destino. Esta operación depende del sistema operativo.

Puede detener todos los procesos o solo los que escriben en la base de datos.

Para detener todos los procesos, utilice los siguientes comandos:

* En Windows:

   ```
   net stop nlserver6
   ```

* En Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Utilice el siguiente comando para comprobar que todos los procesos se han detenido:

```
nlserver pdump
```

>[!NOTE]
>
>En Windows, el proceso **webmdl** puede seguir activo sin afectar a otras operaciones.

También puede comprobar que no hay procesos del sistema en ejecución.

Para ello, utilice el proceso siguiente:

* En Windows: abra el **Task manager** y compruebe que no haya procesos **nlserver.exe**.
* En Linux: ejecute los **ps aux | grep nlserver** y compruebe que no hay procesos **nlserver**.

### Paso 4: Restaurar las bases de datos en el entorno de destino (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Para restaurar las bases de datos de origen en el entorno de destino, utilice el siguiente comando:

```
psql mydatabase < mydatabase.sql
```

### Paso 5: Cauterizar el entorno de destino (dev) {#step-5---cauterize-the-target-environment--dev-}

Para evitar errores de funcionamiento, los procesos vinculados a la entrega de envíos y la ejecución del flujo de trabajo no deben ejecutarse automáticamente cuando se activa el entorno de destino.

Para ello, ejecute el siguiente comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Paso 6: Compruebe la cauterización {#step-6---check-cauterization}

1. Compruebe que la única parte de la entrega sea la que tiene el ID establecido en 0:

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

### Paso 7: Reinicio del proceso web (dev) del entorno de destino {#step-7---restart-the-target-environment-web-process--dev-}

En el entorno de destino, reinicie los procesos de Adobe Campaign para todos los servidores.

>[!NOTE]
>
>Antes de reiniciar Adobe Campaign en el entorno **dev**, puede aplicar un procedimiento de seguridad adicional: inicie solo el módulo **web**.
>  
>Para ello, edite el archivo de configuración de su instancia (**config-dev.xml**) y, a continuación, agregue el carácter &quot;_&quot; antes de las opciones autoStart=&quot;true&quot; para cada módulo (mta, stat, etc.).

Ejecute el siguiente comando para iniciar el proceso web:

```
nlserver start web
```

Utilice el siguiente comando para comprobar que solo se ha iniciado el proceso web:

```
nlserver pdump
```

Compruebe que el acceso a las funciones de la consola del cliente.

### Paso 8: Importar opciones y cuentas externas en el entorno de destino (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Solo el proceso web debe iniciarse en este paso. Si no es así, detenga otros procesos en ejecución antes de continuar

Por encima de todo, compruebe los valores de varias líneas de los archivos antes de importarlos (por ejemplo: &quot;NmsTracking_Pointer&quot; para la tabla de opciones y las cuentas de entrega o intermediario para la tabla de cuenta externa)

Para importar la configuración desde la base de datos de entorno de destino (dev):

1. Abra la consola de administración de la base de datos y depure las cuentas externas (tabla nms:extAccount) cuyo ID no sea 0 (@id &lt;> 0).
1. En la consola de Adobe Campaign, importe el paquete options_dev.xml creado anteriormente mediante la funcionalidad del paquete de importación.

   Compruebe que las opciones se hayan actualizado en el nodo **[!UICONTROL Administration > Platform > Options]**.

1. En la consola de Adobe Campaign, importe extaccount_dev.xml creado anteriormente mediante la funcionalidad del paquete de importación

   Compruebe que las bases de datos externas se hayan importado en **[!UICONTROL Administration > Platform > External accounts]** .

### Paso 9: Reiniciar todos los procesos y cambiar usuarios (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Para iniciar los procesos de Adobe Campaign, utilice los siguientes comandos:

* En Windows:

   ```
   net start nlserver6
   ```

* En Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Utilice el siguiente comando para comprobar que los procesos se inician:

```
nlserver pdump
```

Cambie usuarios para encontrar los usuarios que ya existían en la plataforma dev.
