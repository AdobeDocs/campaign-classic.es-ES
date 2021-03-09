---
solution: Campaign Classic
product: campaign
title: Introducción a la seguridad y la privacidad
description: Obtenga más información sobre los elementos clave para comprobar la seguridad y la privacidad.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 45a77d3fc143ab9c6f9f17ab6118f8816254f6fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 20%

---


# Introducción a la seguridad y la privacidad {#get-started-security-privacy}

Esta sección le muestra los elementos clave que debe comprobar en relación con la seguridad y la privacidad.

## Privacidad

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configuración y el endurecimiento de la privacidad son elementos clave de la optimización de la seguridad. Estas son algunas prácticas recomendadas a seguir con respecto a la privacidad:

* Proteja su PII de cliente usando HTTPS en lugar de HTTP
* Utilice la restricción de la vista PII para proteger la privacidad y evitar que se utilicen los datos de forma indebida.
* Asegúrese de que las contraseñas cifradas estén restringidas.
* Proteja las páginas que puedan contener información personal, como páginas espejo, aplicaciones web, etc.

[Puede obtener más información](../../installation/using/privacy.md)

## Gestión de acceso

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La gestión del acceso es una parte importante del refuerzo de la seguridad. Estas son algunas de las prácticas recomendadas principales:

* Crear suficientes grupos de seguridad
* Compruebe que cada operador tenga los derechos de acceso adecuados
* Evite utilizar el operador de administrador y evite tener demasiados operadores en el grupo de administración

[Puede obtener más información](../../installation/using/access-management.md)

## Directrices de secuencias de comandos y codificación

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Al desarrollar en Adobe Campaign (flujos de trabajo, Javascript, JSSP, etc.), siga siempre estas directrices:

* **Secuencias de comandos**: Intente evitar las declaraciones SQL, utilice funciones parametrizadas en lugar de concatenaciones de cadenas, evite la inyección de SQL al añadir funciones SQL para usar en la lista de permitidos.

* **Protección del modelo** de datos: usar derechos asignados para limitar las acciones de operadores, agregar filtros de sistema (sysFilter)

* **Añadir captchas en aplicaciones** web: obtenga información sobre cómo añadir captchas en las páginas de aterrizaje y de suscripción públicas.

[Puede obtener más información](../../installation/using/scripting-coding-guidelines.md)

## Red, base de datos y SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa muy importante que debe comprobar al implementar un tipo de arquitectura local es la configuración de red.

También es imprescindible que siga la seguridad del motor de la base de datos.

[Puede obtener más información](../../installation/using/network-database.md)

## Configuración del servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configuración debe realizarse en todos los servidores. Los archivos de configuración son del tipo **serverConf.xml** y **`config-<instance>.xml`**. Estos son los elementos clave que deben verificarse:

* **Zonas** de seguridad: Configure las zonas de seguridad para que tengan en cuenta directamente las direcciones IP de los clientes de un proxy.

* **Protección** de carga de archivos: limitar los tipos de archivos que se pueden cargar en el servidor de Adobe Campaign mediante un nuevo atributo uploadAllowList . Se puede utilizar en el archivo de configuración del servidor.

* **Transmisión**: ajuste la configuración de relé desactivando las reglas de transmisión para los módulos o aplicaciones no utilizados.

* **Protección de conexión** saliente y restricción de  **comandos**  (lado del servidor)

* También puede agregar encabezados HTTP adicionales, activar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte la [documentación de configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md) y la [Descripción del archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md) para obtener más información.

[Puede obtener más información](../../installation/using/server-configuration.md)

## Configuración del servidor web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Se deben seguir varias prácticas recomendadas al configurar el servidor web (Apache/IIS):

* Deshabilite la versión SSL y las cifras anteriores:
* Elimine el método TRACE:
* Elimine el banner:
* Limite el tamaño de la consulta para evitar que se carguen archivos importantes:

[Puede obtener más información](../../installation/using/web-server-configuration.md)
