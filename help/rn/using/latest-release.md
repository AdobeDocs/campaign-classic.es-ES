---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 27%

---

# Último lanzamiento {#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## Versión 7.4.3, compilación 9394 {#release-7-4-3}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}

_16 de marzo de 2026_

>[!CAUTION]
>
> La actualización de la consola de cliente es obligatoria.

### Mejoras de seguridad {#security-7-4-3}

* Para mantener una seguridad, estabilidad y conformidad óptimas, Debian se ha actualizado a la versión 13 y PostgreSQL a la versión 17. Consulte la [matriz de compatibilidad](compatibility-matrix.md).

### Correcciones {#fixes-7-4-3}

* Se ha corregido un problema en el cual el componente de código de barras permitía un parámetro de altura sin límites, lo que podría provocar una vulnerabilidad de seguridad. (NEO-89984)
* Se ha corregido un problema en el cual a los campos de enumeración de las listas creadas mediante flujos de trabajo les faltaban atributos de nombre temporales, lo que provocaba que se mostraran etiquetas de enumeración incorrectas o en blanco en la interfaz. (NEO-91158)
* Se ha corregido un problema por el cual las estadísticas de entrega no se volvían a calcular completamente para algunos envíos, lo que afectaba especialmente a los indicadores de éxito. (NEO-88106)
* Se corrigió un problema en el cual la preparación de la entrega fallaba con errores de personalización al utilizar campos targetData en flujos de trabajo con actividades de anulación de duplicación. (NEO-87693)
* Se ha corregido un problema en el cual la concatenación de campos de cadena de un solo carácter con otras cadenas fallaba en PostgreSQL 15 debido a los requisitos de conversión de tipos. (NEO-88028)
* Se ha corregido un problema en el cual los registros de seguimiento de las campañas de colaboración en Distributed Marketing no se escribían en la base de datos debido a una discrepancia entre los ID de entrega principales y secundarios. (NEO-86836)
* Se ha corregido un problema por el cual los registros de envío mostraban mensajes como cancelados aunque se hubieran enviado correctamente, lo que afectaba especialmente a los envíos con programación de olas. (NEO-78933)
* Se corrigió un problema en el cual el flujo de trabajo de limpieza de la base de datos no depuraba los datos de forma eficaz, lo que podría afectar al rendimiento. (NEO-76439)

