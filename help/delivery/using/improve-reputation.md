---
solution: Campaign Classic
product: campaign
title: Mejora de su reputación al utilizar Adobe Campaign Classic
description: Obtenga más información sobre cómo mejorar su reputación al utilizar Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 100%

---


# Mejora de la reputación{#improve-reputation}

Para evitar que los destinatarios se agoten, elimine del destinatario las direcciones de correo electrónico duplicadas. Este paso protege su reputación de envío y garantiza una buena gestión de cuarentena. Adobe Campaign ofrece las herramientas necesarias para implementar estas recomendaciones y evitar el riesgo de ser incluido en la lista de bloqueados por el ISP.

Para evitar la mayor cantidad posible de duplicados, deben llevarse a cabo las siguientes acciones:

* Las importaciones deben configurarse cuidadosamente.
* Preste atención al modificar direcciones de correo electrónico.
* Preste atención durante las importaciones automáticas.
* Los perfiles deben ordenarse en distintas carpetas.

La administración de cuarentena se presenta en [esta sección](../../delivery/using/understanding-quarantine-management.md).

A continuación se encuentran detalles sobre la administración de duplicados y cuarentena.

Tiene la posibilidad de supervisar el volumen de correo electrónico enviado por dirección IP. Se necesita una extensión de esquema para esto. Es necesario ampliar la tabla de broadlogs para añadir el “identificador público” y crear un flujo de trabajo para extraer y mostrar los datos. Póngase en contacto con Adobe si lo necesita.

## Duplicados {#duplicates}

Contar con direcciones de correo electrónico duplicadas puede tener varias consecuencias:

* El mismo mensaje se envía más de una vez. Incluso si Campaign realiza un procedimiento de deduplicación de forma predeterminada antes de la entrega, no hay nada que detenga el mismo mensaje enviado por acciones diferentes que tengan el mismo contenido cuando se divide un destinatario.
* Solicitudes de cancelación de suscripción no aceptadas. Si un destinatario cancela la suscripción después de recibir un mensaje, su perfil duplicado sigue siendo apto para mensajes posteriores.

Además de este paso secundario de los procedimientos de inclusión, esta situación probablemente lleve a los usuarios a considerar los mensajes como no deseados y a activar un procedimiento de inclusión en la lista de bloqueados en el ISP.

Debe ser particularmente prudente al realizar operaciones en la base de datos:

* Las importaciones deben configurarse meticulosamente, en particular al elegir la clave de reconciliación.
* Las direcciones de correo electrónico cambiadas también pueden ser una fuente de duplicados. En particular, dos direcciones con dominios diferentes pueden redirigirse al mismo buzón, por ejemplo, en el caso de una empresa que ha cambiado el nombre y que ha mantenido el dominio anterior durante un periodo determinado: joe.doe@amce-co.com y joe.doe@acme-rebranded.com.
* Las importaciones automáticas, ya sean de listas o de otras bases de datos, son elementos que deben tenerse en cuenta al administrar perfiles. ¿Qué sucede cuando elimina o mueve un perfil en otra partición? Se puede volver a crear en la partición inicial mediante una importación automática, por ejemplo, cuando se realiza una orden de compra.
* El almacenamiento de perfiles en diferentes carpetas se puede implementar mediante vistas en lugar de particiones. De este modo, puede estar seguro de que los perfiles están en la misma partición física y, al mismo tiempo, permite que se muestren y gestionen los derechos adecuados.

De todas maneras, hay casos en los que los duplicados entre las diferentes particiones son normales. Por ejemplo, cuando se envían para terceros o entidades de empresa diferentes, es lógico que la misma persona sea receptora por diferentes motivos. Sin embargo, rara vez se pueden encontrar duplicados dentro de la misma partición.

## Cuarentenas {#quarantines}

Adobe Campaign administra una lista de direcciones en cuarentena. Los destinatarios cuyas direcciones están en cuarentena se excluyen de forma predeterminada durante el análisis de envío: no están segmentados. Una dirección de correo electrónico se puede poner en cuarentena, por ejemplo, cuando el buzón está lleno o si la dirección no existe. De todas maneras, la cuarentena corresponde a las normas específicas que se detallan a continuación.

La administración de cuarentena se presenta en [esta sección](../../delivery/using/understanding-quarantine-management.md).