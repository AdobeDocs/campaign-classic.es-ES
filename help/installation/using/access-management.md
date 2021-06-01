---
product: campaign
title: Gestión de acceso
description: Obtenga más información sobre las prácticas recomendadas de administración de acceso.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 16%

---

# Gestión de acceso {#access-management}

## Operador de aplicación web

De serie, el operador webApp es un administrador. Para mejorar la seguridad, siga estas directrices:

* Sustituya el derecho asignado de administrador de este operador por uno nuevo (puede llamarse &quot;webapp&quot;). Para obtener más información, consulte [esta página](../../platform/using/access-management.md).

* Agregue el operador webApp en carpetas (principalmente carpetas de destinatarios) para conceder acceso de lectura y escritura a los destinatarios. Para obtener más información, consulte [esta página](../../platform/using/access-management.md).

* Si utiliza una instancia de varias marcas (o de varias geografías), puede que desee dividir el acceso de la aplicación web en distintas carpetas de destinatarios. Para ello:

   1. Duplique el operador webApp

   1. Escriba un nombre para cada duplicado. Por ejemplo: webapp_brand, webapp_brand2, etc.

   1. Duplique una plantilla de aplicación web para tener una plantilla por marca y edite las propiedades para cambiar el operador seleccionando Use a specific account.  Obtenga más información en [esta página](../../web/using/defining-web-forms-properties.md).

## Grupos de seguridad y operadores administrativos

Cree suficientes grupos de seguridad para dar derechos suficientes a los operadores para permitirles hacer lo que necesitan y no más.

No utilice el operador de administrador (o no lo comparta). Cree un operador por usuario físico (para tener una auditoría/registro precisos). Agregue los administradores recién nombrados al grupo de administradores. Si no utiliza el operador de administrador, no lo elimine y no lo deshabilite: este operador se utiliza internamente para ejecutar el procesamiento. Pero puede prohibir su [acceso a la consola del cliente](../../platform/using/access-management.md) y restringir su zona de seguridad (a localhost).

Evite agregar demasiados operadores en el grupo de administración (o con derechos asignados por el administrador). Son operadores muy poderosos (pueden realizar todas las instrucciones SQL, ejecutar comandos en el servidor, etc.).

Adobe Campaign proporciona tres privilegios de alto nivel mediante [derechos asignados](../../platform/using/access-management.md#named-rights):

* **ADMINISTRACIÓN**  (administrador): proporciona acceso a todo y permite hacer todo, evitando todas las comprobaciones de derechos con nombre, por lo que incluye los derechos asignados de EJECUCIÓN DE PROGRAMAS (createProcess) y SQL

* **EJECUCIÓN DE PROGRAMAS**  (createProcess): permite ejecutar programas externos (en el servidor)

* **SQL**: permite ejecutar secuencias de comandos SQL en la base de datos (para que pueda omitir el modelo de seguridad). Nota: Si necesita realizar cálculos complejos (filtrado, por ejemplo), puede pedir al administrador de la base de datos que cree una función SQL y que los añada a la lista de permitidos. Obtenga más información en [esta página](../../installation/using/scripting-coding-guidelines.md).

* **Otorgarlas a muy pocos operadores (y de confianza)**
