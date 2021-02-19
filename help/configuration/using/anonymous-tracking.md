---
solution: Campaign Classic
product: campaign
title: Seguimiento anónimo
description: Seguimiento anónimo
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# Seguimiento anónimo{#anonymous-tracking}

Adobe Campaign le permite vincular la información recopilada sobre los Seguimientos web a un destinatario cuando éstos exploran el sitio de forma anónima. Cuando un usuario explora las páginas etiquetadas de su sitio web, esta información de navegación se recopila para que una vez que hace clic en un mensaje de correo electrónico enviado por Adobe Campaign, se identifique y la información se vincule automáticamente.

>[!IMPORTANT]
>
>La configuración de seguimientos anónimos en un sitio web puede generar déclencheur en la recopilación de una cantidad significativa de registros de seguimiento, afectando así el funcionamiento de la base de datos. Configúrelo con cuidado.\
>Los registros de seguimiento se guardan en la base de datos hasta que se purgan los datos de seguimiento. Utilice el asistente de implementación para configurar la frecuencia de purga. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar el Seguimiento web anónimo en la instancia, deben configurarse los siguientes elementos:

* El parámetro **trackWebVisitors** del elemento **redirección** del archivo **serverConf.xml** del servidor de seguimiento debe configurarse en &#39;**true**&#39; para colocar una cookie permanente (**uid230**) en los exploradores de usuarios de Internet desconocidos que visitan el sitio.
* El modo **Seguimiento web anónimo** debe estar seleccionado en la pantalla de configuración de seguimiento del asistente de implementación.

   ![](assets/webtracking_anonymous_set.png)

* Los formularios web y encuestas deben publicarse y ejecutarse en el servidor de seguimiento. La opción coincidente debe estar seleccionada en el asistente de implementación.

   ![](assets/webtracking_publication_set_for_webapps.png)

