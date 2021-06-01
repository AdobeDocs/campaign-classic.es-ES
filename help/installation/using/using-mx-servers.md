---
product: campaign
title: Uso de servidores MX con Campaign
description: Descubra cómo funcionan los servidores MX con Adobe Campaign Classic.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# Uso de servidores MX con Campaign {#using-mx-servers}

Descubra cómo funcionan los servidores MX con Adobe Campaign Classic.

## Servidores MX {#mx-servers}

### ¿Qué es un servidor MX?

Un registro de intercambiador de correo (registro MX) es un tipo de registro de recursos en el Sistema de nombres de dominio (DNS) que especifica un servidor de correo responsable de aceptar mensajes de correo electrónico en nombre de un dominio.

### ¿Cómo funciona un servidor MX?

Al enviar un correo electrónico, el servidor de software establece una conexión con el servidor de dominio del destinatario. La comunicación entre los dos servidores utiliza el lenguaje SMTP y un dominio puede tener más de un servidor MX. La conexión a este dominio comenzará desde la prioridad más alta (cifra más pequeña) y otros servidores se denominarán servidores de &quot;copia de seguridad&quot;. Se debe respetar el protocolo de conexión.

### ¿Cómo funciona un servidor MX con Adobe Campaign?

En el protocolo de conexión, se deben respetar las reglas para evitar el spam y el monopolio de los servidores. Los más importantes son los siguientes:

* **Número máximo de conexiones permitidas**: Cuando se respeta este número, las IP no se encuentran en la  de lista de bloqueados y los correos electrónicos no se rechazan debido a conexiones adicionales.
* **Número máximo de mensajes**: Durante la conexión, se debe definir el número de mensajes permitidos para enviarse. Si no se define este número, el servidor enviará tantos como sea posible. Esto hace que el ISP identifique como un remitente del correo no deseado y lo añada a la  de lista de bloqueados.
* **Mensajes por hora**: Para que coincida con su reputación de su empresa, Adobe Campaign controlará el número de correos electrónicos que sus IP pueden enviar por hora. Este sistema le protegerá contra la denegación de correo electrónico o la  lista de bloqueados.

## Invocar correos electrónicos

### ¿Qué es un correo electrónico de devoluciones?

Es el proceso que utiliza Adobe Campaign para procesar errores durante las comunicaciones con el servidor.

### ¿Cómo funciona un correo electrónico de Inbote?

La dirección de error procesa las devoluciones enviadas por los ISP. El proceso analizará diferentes códigos de error SMTP y aplicará la acción correcta según el estándar RegEx.

Por ejemplo, una dirección de correo electrónico tiene un comentario &quot;550 User Unknown&quot; enviado por un ISP. Este código de error lo procesa la dirección de error de Adobe Campaign (dirección de ruta de retorno). Este error se compara con el estándar RegEx y se aplica la regla correcta. El correo electrónico se considera un *rechazo grave* (que coincide con el tipo) y, a continuación, *Desconocido del usuario* (que coincide con el motivo) y se envía a cuarentena después del primer bucle al sistema.

### ¿Cómo lo gestiona Adobe Campaign?

Adobe Campaign administra este proceso con una coincidencia entre un tipo de error y un motivo:

* **[!UICONTROL User Unknown]**: Dirección que es sintácticamente correcta pero no existe. Este error se clasifica como un rechazo grave y se envía a cuarentena dentro del primer error.
* **[!UICONTROL Mailbox full]**: Buzón que ha alcanzado la capacidad máxima. Este error también puede indicar que el usuario ya no utiliza este buzón. Este error se clasifica como una devolución suave y se envía a cuarentena dentro del tercer error y se elimina de la cuarentena después de un periodo de 30 días.
* **[!UICONTROL Inactive User]**: El ISP ha desactivado el buzón de correo debido a un usuario inactivo en los últimos 6 meses. Este error se clasifica como un rebote suave y se envía a cuarentena dentro del tercer error.
* **[!UICONTROL Invalid domain]**: El dominio de la dirección de correo electrónico no existe. Este error se clasifica como un rebote suave y se envía a cuarentena dentro del tercer error.
* **[!UICONTROL Refused]**: El ISP se negó a enviar el correo electrónico a sus usuarios. Este error se clasifica como una devolución suave y no se envía a cuarentena, ya que no está vinculado a la dirección de correo electrónico sino a la reputación de un dominio o dirección IP.

>[!NOTE]
>
>Para obtener más información sobre los tipos y motivos de errores de entrega, consulte esta [sección](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instancia de entrega

Una actualización diaria de las reglas MX y las reglas de devoluciones se administra mediante un flujo de trabajo específico en la instancia de cliente que está conectada al propietario de la instancia de entrega de estas reglas.

Esta actualización diaria se está ejecutando para todos los clientes que desean mantener su instancia actualizada a través de un proceso de transparencia.

Las reglas MX tienen 6 niveles diferentes de rendimiento que se utilizan principalmente durante el proceso de aceleración:

![](assets/mx-rules-throughput.png)

El modo Personalizado es para clientes avanzados que desean establecer sus propias reglas MX. Cuando se activa el modo Personalizado, la instancia de Deliverability no actualiza el cliente, ya que la sincronización se desactiva.

## Ejemplos de rebote

* **Usuario desconocido**  (rechazo grave): 550 5.1.1 ... El usuario es desconocido {mx003}
* **Buzón lleno**  (rechazo suave): 550 5.2.2 Superación de la cuota de usuario
* **Buzón inactivo**  (rechazo suave): 550 5.7.1: Dirección de destinatario rechazada: MailBox inactivo, sin agrupar durante más de 6 meses
* **Dominio no válido**  (devolución suave): Error en la consulta DNS para &quot;ourdan.com&quot;
* **Rechazado**  (devolución suave): Rechazo de correo electrónico entrante (la regla &#39;Feedback_loop_Hotmail&#39; coincide con este rechazo)
* **Inaccesible**  (devolución suave): 421 4.16.55  [TS01]  Mensajes de x.x.x.x aplazados temporalmente debido a quejas excesivas del usuario

**Temas relacionados:**
* [Configuración MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configuración técnica de correo electrónico](../../installation/using/email-deliverability.md)
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic: Recommendations técnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
