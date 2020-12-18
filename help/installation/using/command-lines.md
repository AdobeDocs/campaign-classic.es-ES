---
solution: Campaign Classic
product: campaign
title: Líneas de comandos
description: Líneas de comandos
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Líneas de comandos{#command-lines}

Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. Para implementaciones alojadas en Adobe, estos comandos solo se pueden ejecutar mediante Adobe.

## Creación de una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar mediante líneas de comandos, con la sintaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para el parámetro `[lang]`)

El comando **nlserver config -addinstance:instance1/demo*/eng** permite crear una instancia denominada **instance1** en inglés con la demostración de máscara DNS*.

## Declaración de una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos mediante la siguiente sintaxis:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para el parámetro **`[rdbms]`**:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para el motor DB2.

El siguiente comando configura la instancia **demo** con el servidor de tipo SQL conocido como **base6**, vinculada a la cuenta **campaña** y su **contraseña** en el servidor **dbsrv**:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

