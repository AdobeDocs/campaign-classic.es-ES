---
product: campaign
title: Lista de comprobación de seguridad y privacidad
description: Obtenga más información acerca de los elementos clave para comprobar la seguridad y la privacidad
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 17%

---

# Lista de comprobación de seguridad y privacidad{#get-started-security-privacy}



Esta sección presenta los elementos clave para comprobar la seguridad y la privacidad. Algunas configuraciones solo las pueden realizar los clientes locales.

## Privacidad

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

La configuración y protección de la privacidad es un elemento clave de la optimización de la seguridad. Estas son algunas prácticas recomendadas seguir con respecto a la privacidad:

* Proteja su PII de cliente usando HTTPS en lugar de HTTP
* Utilice la restricción de la vista PII para proteger la privacidad y evitar que se utilicen los datos de forma indebida.
* Asegúrese de que las contraseñas cifradas estén restringidas.
* Proteja las páginas que puedan contener información personal, como páginas espejo, aplicaciones web, etc.

[Más información](../../installation/using/privacy.md)

## Gestión de acceso

<img src="assets/do-not-localize/icon_access.svg" width="60px">

La administración del acceso es una parte importante del refuerzo de la seguridad. Estas son algunas de las prácticas recomendadas principales:

* Crear suficientes grupos de seguridad
* Compruebe que cada operador tiene los derechos de acceso adecuados
* Evite utilizar el operador admin y evite tener demasiados operadores en el grupo admin

[Más información](../../installation/using/access-management.md)

## Directrices de script y código

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Al desarrollar en Adobe Campaign (flujos de trabajo, Javascript, JSSP, etc.), siga siempre estas directrices:

* **Secuencias de comandos**: intente evitar las instrucciones SQL, use funciones parametrizadas en lugar de concatenaciones de cadenas, evite la inyección de SQL al agregar funciones SQL para usar en la lista de permitidos.

* **Proteger el modelo de datos**: use derechos asignados para limitar las acciones de los operadores y agregue filtros de sistema (sysFilter)

* **Agregar captchas en aplicaciones web**: aprenda a agregarlos en sus páginas de aterrizaje públicas y páginas de suscripción.

[Más información](../../installation/using/scripting-coding-guidelines.md)

## Red, base de datos y SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Una cosa muy importante que hay que comprobar al implementar un tipo de arquitectura On-Premise es la configuración de red.

También es imperativo que siga la seguridad del motor de la base de datos.

[Más información](../../installation/using/network-database.md)


## Configuración del servidor

<img src="assets/do-not-localize/icon_server.svg" width="60px">

La configuración debe realizarse en todos los servidores. Los archivos de configuración son del tipo **serverConf.xml** y **`config-<instance>.xml`**. Estos son los elementos clave que deben verificarse:

* **Zonas de seguridad**: configure zonas de seguridad para que tengan en cuenta directamente las direcciones IP de los clientes de un proxy.

* **Protección de carga de archivos**: limite los tipos de archivos que se pueden cargar en el servidor de Adobe Campaign mediante un nuevo atributo uploadAllowList. Se puede utilizar en el archivo de configuración del servidor.

* **Retransmisión**: ajuste la configuración de retransmisión desactivando las reglas de retransmisión para módulos o aplicaciones que no se usen.

* **Protección de conexión saliente** y **Restricción de comandos** (del lado del servidor)

* También puede añadir encabezados HTTP adicionales, activar checkIPConsistent, enableTLS, sessionTimeOutSec, etc. Consulte la [documentación de configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md) y la [descripción del archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md) para obtener más información.

[Más información](../../installation/using/server-configuration.md)

## Configuración del servidor web

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Se deben seguir varias prácticas recomendadas al configurar el servidor web (Apache/IIS):

* Deshabilitar la versión y las cifras SSL antiguas
* Quitar el método TRACE
* Quitar el titular
* Limitar el tamaño de la consulta para evitar que se carguen archivos importantes

[Más información](../../installation/using/web-server-configuration.md)
