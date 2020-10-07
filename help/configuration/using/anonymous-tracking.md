---
title: Seguimiento anónimo
seo-title: Seguimiento anónimo
description: Seguimiento anónimo
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 7%

---


# Seguimiento anónimo{#anonymous-tracking}

Adobe Campaign le permite vincular la información recopilada sobre los Seguimientos web a un destinatario cuando éstos exploran el sitio de forma anónima. Cuando un usuario explora las páginas etiquetadas de su sitio web, esta información de navegación se recopila para que una vez que hace clic en un mensaje de correo electrónico enviado por Adobe Campaign, se identifique y la información se vincule automáticamente.

>[!IMPORTANT]
>
>La configuración de seguimientos anónimos en un sitio web puede desencadenar la recopilación de una cantidad significativa de registros de seguimiento, afectando así el funcionamiento de la base de datos. Configúrelo con cuidado.\
>Los registros de seguimiento se guardan en la base de datos hasta que se purgan los datos de seguimiento. Utilice el asistente de implementación para configurar la frecuencia de purga. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar el Seguimiento web anónimo en la instancia, deben configurarse los siguientes elementos:

* El parámetro **trackWebVisitors** del elemento de **redirección** del archivo **serverConf.xml** del servidor de seguimiento debe configurarse en &#39;**true**&#39; para colocar una cookie permanente (**uuid230**) en los exploradores de usuarios de Internet desconocidos que visiten el sitio.
* El modo Seguimiento web **** anónimo debe estar seleccionado en la pantalla de configuración de seguimiento del asistente de implementación.

   ![](assets/webtracking_anonymous_set.png)

* Los formularios web y encuestas deben publicarse y ejecutarse en el servidor de seguimiento. La opción coincidente debe estar seleccionada en el asistente de implementación.

   ![](assets/webtracking_publication_set_for_webapps.png)

