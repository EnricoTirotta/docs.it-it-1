---
title: Comando dotnet sln - Interfaccia della riga di comando di .NET Core
description: Il comando dotnet-sln rappresenta un'opzione comoda per aggiungere, rimuovere ed elencare i progetti in un file di soluzione.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: deb66ff52074630616c7be47f1a9751246db501d
ms.sourcegitcommit: 70dcc89737127e4d5f20500242409b687e51b07e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>nome

`dotnet sln`: consente di modificare un file di soluzione .NET Core.

## <a name="synopsis"></a>Riepilogo

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Descrizione

Il comando `dotnet sln` offre un modo pratico per aggiungere, rimuovere ed elencare i progetti in un file di soluzione.

## <a name="commands"></a>Comandi:

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Aggiunge uno o più progetti più al file di soluzione. I [criteri GLOB](https://en.wikipedia.org/wiki/Glob_(programming)) sono supportati nei terminali basati su Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Rimuove uno o più progetti dal file di soluzione. I [criteri GLOB](https://en.wikipedia.org/wiki/Glob_(programming)) sono supportati nei terminali basati su Unix/Linux.

`list`

Elenca tutti i progetti in un file di soluzione.

## <a name="arguments"></a>Argomenti

`SOLUTION_NAME`

File di soluzione da usare. Se non specificato, il comando ne cerca uno nella directory corrente. Se sono presenti più file di soluzione nella directory, è necessario specificarne uno.

## <a name="options"></a>Opzioni

`-h|--help`

Stampa una breve guida per il comando.

## <a name="examples"></a>Esempi

Aggiungere un progetto C# a una soluzione:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Rimuovere un progetto C# da una soluzione:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Aggiungere più progetti C# a una soluzione:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Rimuovere più progetti C# da una soluzione:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Aggiungere più progetti C# a una soluzione usando un criterio GLOB:

`dotnet sln todo.sln add **/*.csproj`

Rimuovere più progetti C# da una soluzione usando un criterio GLOB:

`dotnet sln todo.sln remove **/*.csproj`
