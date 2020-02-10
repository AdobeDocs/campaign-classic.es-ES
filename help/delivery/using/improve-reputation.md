---
title: Mejora de su reputación al utilizar Adobe Campaign Classic
description: Obtenga más información sobre cómo mejorar su reputación al utilizar Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Mejora de la reputación{#improve-reputation}

Para evitar que los destinatarios se agoten, elimine del objetivo las direcciones de correo electrónico duplicadas. Este paso protege su reputación de envío y garantiza una buena gestión de cuarentena. Adobe Campaign ofrece las herramientas necesarias para implementar estas recomendaciones y evitar el riesgo de ser bloqueado por el ISP.

Para evitar la mayor cantidad posible de duplicados, deben llevarse a cabo las siguientes acciones:

* Las importaciones deben configurarse cuidadosamente
* Preste atención al modificar direcciones de correo electrónico
* Prestar atención durante las importaciones automáticas
* Los perfiles deben ordenarse en distintas carpetas

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).

A continuación encontrará detalles sobre la administración de duplicados y cuarentena.

Tiene la posibilidad de supervisar el volumen de correo electrónico enviado por dirección IP. Se necesita una extensión de esquema para esto. Es necesario ampliar la tabla de diarios extendidos para agregar el &quot;identificador público&quot; y crear un flujo de trabajo para extraer y mostrar los datos. Póngase en contacto con Adobe si necesita esto.

## Duplicados {#duplicates}

El tener direcciones de correo electrónico duplicadas puede tener varias consecuencias:

* El mismo mensaje se envía más de una vez. Incluso si Campaign realiza un procedimiento de desduplicación de forma predeterminada antes de enviar, no hay nada que detenga el mismo mensaje enviado por acciones diferentes que tengan el mismo contenido cuando se divide un objetivo.
* Solicitudes de cancelación de suscripción no aceptadas. Si un destinatario cancela la suscripción después de recibir un mensaje, su perfil duplicado seguirá siendo apto para futuros mensajes.

Además de este paso secundario de los procedimientos de inclusión, esta situación probablemente llevará a los usuarios a considerar los mensajes como spam y a activar un procedimiento de lista negra en el ISP.

Debe ser especialmente prudente al realizar operaciones en la base de datos:

* Las importaciones deben configurarse meticulosamente, en particular al elegir la clave de reconciliación.
* Las direcciones de correo electrónico cambiadas también pueden ser una fuente de duplicados. En particular, dos direcciones con dominios diferentes pueden enrutarse al mismo buzón, por ejemplo, en el caso de una empresa que ha cambiado el nombre y que ha mantenido el dominio anterior durante un período de tiempo determinado: joe.doe@amce-co.com y joe.doe@acme-rebranded.com.
* Las importaciones automáticas, ya sean de listas o de otras bases de datos, son elementos que deben tenerse en cuenta al administrar perfiles. ¿Qué sucede cuando elimina o mueve un perfil en otra partición? Se puede volver a crear en la partición inicial mediante una importación automática, por ejemplo, cuando se realiza una orden de compra.
* El almacenamiento de perfiles en diferentes carpetas se puede implementar mediante vistas en lugar de particiones. De este modo, está seguro de que los perfiles están en la misma partición física y, al mismo tiempo, permite que se muestren y gestionen los derechos adecuados.

Hay, en todo caso, casos en los que los duplicados entre las diferentes particiones son normales. Por ejemplo, cuando se envían para terceros o entidades de empresa diferentes, es lógico que la misma persona sea receptora por diferentes motivos. Sin embargo, rara vez es normal encontrar duplicados dentro de la misma partición.

## Cuarantines {#quarantines}

Adobe Campaign administra una lista de direcciones en cuarentena. Los destinatarios cuyas direcciones están en cuarentena se excluyen de forma predeterminada durante el análisis de entrega: no están segmentados. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando la bandeja de entrada está llena o si la dirección no existe. En todos los casos, la cuarentena corresponde a las normas específicas que se detallan a continuación.

Quarantine management is presented in [this section](../../delivery/using/understanding-quarantine-management.md).