---
product: campaign
title: Gestión de acceso
description: Obtenga más información acerca de las prácticas recomendadas de administración de acceso
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 8%

---

# Gestión de acceso {#access-management}



## Operador Webapp

De forma predeterminada, el operador webApp es un administrador. Para mejorar la seguridad, siga estas directrices:

* Reemplace el administrador asignado directamente desde este operador por uno nuevo (puede llamarse &quot;webapp&quot;). Para obtener más información, consulte [esta página](../../platform/using/access-management.md).

* Añada el operador webApp en carpetas (principalmente carpetas de destinatarios) para conceder acceso de lectura y escritura a los destinatarios. Para obtener más información, consulte [esta página](../../platform/using/access-management.md).

* Si utiliza una instancia de varias marcas (o de varias regiones), es posible que desee dividir el acceso de la aplicación web en distintas carpetas de destinatario. Para ello:

   1. Duplicación del operador webApp

   1. Introduzca un nombre para cada duplicado. Por ejemplo: webapp_brand, webapp_brand2, etc.

   1. Duplique una plantilla de aplicación web para tener una plantilla por marca y edite las propiedades para cambiar el operador seleccionando Use a specific account.  Obtenga más información en [esta página](../../web/using/defining-web-forms-properties.md).

## Grupos de seguridad y operadores de administración

Cree suficientes grupos de seguridad para dar derechos suficientes a los operadores y permitirles hacer lo que necesiten, y no más.

No utilice el operador admin (o no lo comparta). Cree un operador por usuario físico (para tener una auditoría/registro precisos). Añada los administradores con nuevos nombres al grupo de administradores. Si no utiliza el operador admin, no lo elimine y no lo deshabilite: este operador se utiliza internamente para ejecutar el procesamiento. Pero puede prohibir su [acceso a la consola del cliente](../../platform/using/access-management.md) y restringir su zona de seguridad (a localhost).

Evite añadir demasiados operadores en el grupo de administradores (o con derechos asignados de administrador). Son operadores muy potentes (pueden realizar todas las sentencias SQL, ejecutar comandos en el servidor, etc.).

Adobe Campaign proporciona tres privilegios de alto nivel mediante [derechos asignados](../../platform/using/access-management.md#named-rights):

* **ADMINISTRACIÓN** (administrador): da acceso a todo y permite hacer de todo, omitiendo todas las comprobaciones de derechos asignados, por lo que incluye los derechos asignados de EJECUCIÓN DE PROGRAMA (createProcess) y SQL

* **EJECUCIÓN DEL PROGRAMA** (createProcess): permite ejecutar programas externos (en el servidor)

* **SQL**: permite ejecutar scripts SQL en la base de datos (para que pueda omitir el modelo de seguridad). Nota: Si necesita realizar cálculos complejos (filtrado, por ejemplo), puede pedir al administrador de la base de datos que cree una función SQL y que los añada a la lista de permitidos. Obtenga más información en [esta página](../../installation/using/scripting-coding-guidelines.md).

* **Concederlos a muy pocos operadores (y de confianza)**
