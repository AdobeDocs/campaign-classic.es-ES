---
product: campaign
title: Líneas de comandos
description: Líneas de comandos
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Líneas de comandos{#command-lines}

![](../../assets/v7-only.svg)

Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. En implementaciones alojadas en Adobe, estos comandos solo se pueden ejecutar mediante Adobe.

## Crear una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar utilizando líneas de comandos, con la sintaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para la variable `[lang]` parameter)

El comando **nlserver config -addinstance:instance1/demo&#42;/eng** permite crear una instancia denominada **instance1** en inglés con la demostración de máscara DNS&#42;.

## Declarar una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos utilizando la siguiente sintaxis:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para la variable **`[rdbms]`** parámetro:

* **postgresql**: para PostgreSQL,
* **oracle**: para el Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para el motor DB2.

El siguiente comando configura la variable **demostración** instancia con el servidor de tipo SQL conocido como **base6**, vinculado al **campaign** cuenta y **password** en el **dbsrv** servidor:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
