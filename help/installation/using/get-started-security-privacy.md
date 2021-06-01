---
product: campaign
title: Introducción a la seguridad y la privacidad
description: Obtenga más información sobre los elementos clave para comprobar la seguridad y la privacidad.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 24%

---

# Introducción a la seguridad y la privacidad {#get-started-security-privacy}

Esta sección le muestra los elementos clave que debe comprobar en relación con la seguridad y la privacidad. Algunas configuraciones solo pueden realizarlas los clientes locales.

## Privacidad

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configuración y el endurecimiento de la privacidad son elementos clave de la optimización de la seguridad. Estas son algunas prácticas recomendadas a seguir con respecto a la privacidad:

* Proteja su PII de cliente usando HTTPS en lugar de HTTP
* Utilice la restricción de la vista PII para proteger la privacidad y evitar que se utilicen los datos de forma indebida.
* Asegúrese de que las contraseñas cifradas estén restringidas.
* Proteja las páginas que puedan contener información personal, como páginas espejo, aplicaciones web, etc.

[Más información](../../installation/using/privacy.md)

## Gestión de acceso

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La gestión del acceso es una parte importante del refuerzo de la seguridad. Estas son algunas de las prácticas recomendadas principales:

* Crear suficientes grupos de seguridad
* Compruebe que cada operador tenga los derechos de acceso adecuados
* Evite utilizar el operador de administrador y evite tener demasiados operadores en el grupo de administración

[Más información](../../installation/using/access-management.md)

## Directrices de script y código

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Cuando desarrolle en Adobe Campaign (flujos de trabajo, JavaScript, JSSP, etc.), siga siempre estas directrices:

* **Secuencias de comandos**: Intente evitar las declaraciones SQL, utilice funciones parametrizadas en lugar de concatenaciones de cadenas, evite la inyección de SQL al añadir funciones SQL para usar en la lista de permitidos.

* **Proteja el modelo** de datos: usar derechos asignados para limitar las acciones de operadores, agregar filtros de sistema (sysFilter)

* **Añadir captchas en aplicaciones** web: obtenga información sobre cómo añadir captchas en las páginas de aterrizaje y de suscripción públicas.

[Más información](../../installation/using/scripting-coding-guidelines.md)

## Red, base de datos y SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa muy importante que debe comprobar al implementar un tipo de arquitectura local es la configuración de red.

También es imprescindible que siga la seguridad del motor de la base de datos.

[Más información](../../installation/using/network-database.md)

## Configuración del servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configuración debe realizarse en todos los servidores. Los archivos de configuración son del tipo **serverConf.xml** y **`config-<instance>.xml`**. Estos son los elementos clave que deben verificarse:

* **Zonas** de seguridad: Configure las zonas de seguridad para que tengan en cuenta directamente las direcciones IP de los clientes de un proxy.

* **Protección** de carga de archivos: limitar los tipos de archivos que se pueden cargar en el servidor de Adobe Campaign mediante un nuevo atributo uploadAllowList . Se puede utilizar en el archivo de configuración del servidor.

* **Transmisión**: ajuste la configuración de relé desactivando las reglas de transmisión para los módulos o aplicaciones no utilizados.

* **Protección de conexión** saliente y restricción de  **comandos**  (lado del servidor)

* También puede agregar encabezados HTTP adicionales, activar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte la [documentación de configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md) y la [Descripción del archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md) para obtener más información.

[Más información](../../installation/using/server-configuration.md)

## Configuración del servidor web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Se deben seguir varias prácticas recomendadas al configurar el servidor web (Apache/IIS):

* Desactive las versiones y cifrados de SSL anteriores
* Eliminación del método del TRACE
* Quitar el banner
* Limitar el tamaño de la consulta para evitar que se carguen archivos importantes

[Más información](../../installation/using/web-server-configuration.md)
