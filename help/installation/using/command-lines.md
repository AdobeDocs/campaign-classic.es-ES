---
product: campaign
title: Líneas de comandos
description: Líneas de comandos
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# Líneas de comandos{#command-lines}



Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. Para implementaciones alojadas por el Adobe, estos comandos solo se pueden ejecutar por el Adobe.

## Creación de una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar mediante líneas de comandos con la sintaxis:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para el parámetro `[lang]`)

El comando **nlserver config -addinstance:instance1/demo&#42;/eng** le permite crear una instancia denominada **instance1** en inglés con la demostración de máscara DNS&#42;.

## Declarar una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos mediante la siguiente sintaxis:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para el parámetro **`[rdbms]`**:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,

El siguiente comando configura la instancia **demo** con el servidor de tipo SQL conocido como **base6**, vinculado a la cuenta **campaign** y su **contraseña** en el servidor **dbsrv**:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
