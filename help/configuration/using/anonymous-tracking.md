---
product: campaign
title: Seguimiento anónimo
description: Seguimiento anónimo
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---

# Seguimiento anónimo{#anonymous-tracking}

Adobe Campaign permite vincular información de seguimiento web recopilada a un destinatario cuando este navega por el sitio de forma anónima. Cuando un usuario explora las páginas etiquetadas de su sitio web, esta información de navegación se recopila, de modo que una vez que hace clic en un correo electrónico enviado por Adobe Campaign, se identifica y la información se vincula automáticamente a ellas.

>[!IMPORTANT]
>
>La configuración del seguimiento anónimo en un sitio web puede almacenar en déclencheur la recopilación de una cantidad significativa de registros de seguimiento, lo que afecta al funcionamiento de la base de datos. Configúrelo con cuidado.\
>Los registros de seguimiento se guardan en la base de datos hasta que se depuran los datos de seguimiento. Utilice el asistente de implementación para configurar la frecuencia de depuración. Para obtener más información, consulte [esta sección](../../installation/using/deploying-an-instance.md#purging-data).

Para habilitar el seguimiento web anónimo en la instancia, se deben configurar los siguientes elementos:

* El parámetro **trackWebVisitors** del elemento **redirección** del archivo **serverConf.xml** del servidor de seguimiento debe configurarse como &#39;**true**&#39; para colocar una cookie permanente (**uuid230**) en los navegadores de usuarios de Internet desconocidos que visitan el sitio.
* El modo **Seguimiento web anónimo** debe estar seleccionado en la pantalla de configuración de seguimiento del asistente de implementación.

   ![](assets/webtracking_anonymous_set.png)

* Los formularios web y las encuestas deben publicarse y ejecutarse en el servidor de seguimiento. La opción correspondiente debe estar seleccionada en el asistente de implementación.

   ![](assets/webtracking_publication_set_for_webapps.png)
