---
title: Líneas de comandos
seo-title: Líneas de comandos
description: Líneas de comandos
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%

---


# Líneas de comandos{#command-lines}

Las siguientes líneas de comandos requieren la capacidad de acceder al servidor de aplicaciones. Para implementaciones alojadas en Adobe, estos comandos solo se pueden ejecutar mediante Adobe.

## Creación de una instancia {#creating-an-instance}

La creación de instancias se puede ejecutar mediante líneas de comandos, con la sintaxis:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(donde **eng** y **fra** son valores posibles para el `[lang]` parámetro)

El comando **nlserver config -addinstance:instance1/demo*/eng** permite crear una instancia denominada **instance1** en inglés con la demostración de máscara DNS*.

## Declaración de una base de datos {#declaring-a-database}

Puede asociar una base de datos existente con una instancia desde la línea de comandos mediante la siguiente sintaxis:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Los siguientes valores son posibles para el **`[rdbms]`** parámetro:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para el motor DB2.

El siguiente comando configura la instancia de **demostración** con el servidor de tipo SQL conocido como **base6**, vinculado a la cuenta de **campaña** y a su **contraseña** en el servidor **dbsrv** :

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

