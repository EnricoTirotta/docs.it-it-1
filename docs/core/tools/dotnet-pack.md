---
title: Comando dotnet pack - Interfaccia della riga di comando di .NET Core
description: Il comando dotnet pack consente di creare pacchetti NuGet per il progetto .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 28cd05db0643097a7271fd0488354846598ba493
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-pack"></a>dotnet pack

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>nome

`dotnet pack`: comprime il codice in un pacchetto NuGet.

## <a name="synopsis"></a>Riepilogo

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Descrizione

Il comando `dotnet pack` consente di compilare il progetto e creare pacchetti NuGet. Il risultato di questo comando è un pacchetto NuGet. Se l'opzione `--include-symbols` è presente, viene creato un altro pacchetto contenente i simboli di debug.

Le dipendenze NuGet del progetto compresso vengono aggiunte al file con estensione *nuspec*, in modo da poter essere risolte durante l'installazione del pacchetto. I riferimenti da progetto a progetto non sono inseriti all'interno del progetto. Attualmente è necessario disporre di un pacchetto per ogni progetto se sono presenti dipendenze da progetto a progetto.

Per impostazione predefinita, `dotnet pack` compila prima il progetto. Se si vuole evitare questo comportamento, passare l'opzione `--no-build`. Questo può essere utile negli scenari di compilazione di integrazione continua (CI, Continuous Integration), in cui si sa che il codice è stato compilato in precedenza.

È possibile aggiungere proprietà MSBuild al comando `dotnet pack` per il processo di compressione. Per altre informazioni, vedere [NuGet metadata properties](csproj.md#nuget-metadata-properties) (Proprietà dei metadati NuGet) e [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) (Informazioni di riferimento sulla riga di comando di MSBuild). La sezione [Esempi](#examples) illustra come usare l'opzione di MSBuild /p per due diversi scenari.

## <a name="arguments"></a>Argomenti

`PROJECT`

Progetto da comprimere. Può essere un percorso a un [file csproj](csproj.md) o a una directory. Se omesso, per impostazione predefinita viene usata la directory corrente.

## <a name="options"></a>Opzioni

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definisce la configurazione di compilazione. Il valore predefinito è `Debug`.

`--force` Forza la risoluzione di tutte le dipendenze, anche se l'ultimo ripristino ha avuto esito positivo. Ciò equivale a eliminare il file *project.assets.json*.

`-h|--help`

Stampa una breve guida per il comando.

`--include-source`

Include i file di origine nel pacchetto NuGet. I file di origine sono inclusi nella cartella `src` del pacchetto `nupkg`.

`--include-symbols`

Genera i simboli `nupkg`.

`--no-build`

Non compila il progetto prima della compressione.

`--no-dependencies`

Ignora i riferimenti da progetto a progetto e ripristina solo il progetto radice.

`--no-restore`

Non esegue un ripristino implicito quando si esegue il comando.

`-o|--output <OUTPUT_DIRECTORY>`

Inserisce i pacchetti compilati nella directory specificata.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Specifica il runtime di destinazione per cui ripristinare i pacchetti. Per un elenco degli identificatori di runtime (RID, Runtime Identifier), vedere il [catalogo RID](../rid-catalog.md).

`-s|--serviceable`

Imposta il flag utilizzabile dai servizi nel pacchetto. Per altre informazioni, vedere [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing) (Blog .NET: .NET 4.5.1 supporta gli aggiornamenti della sicurezza Microsoft per le librerie NuGet di .NET).

`--version-suffix <VERSION_SUFFIX>`

Definisce il valore della proprietà MSBuild `$(VersionSuffix)` nel progetto.

`-v|--verbosity <LEVEL>`

Imposta il livello di dettaglio del comando. I valori consentiti sono `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definisce la configurazione di compilazione. Il valore predefinito è `Debug`.

`-h|--help`

Stampa una breve guida per il comando.

`--include-source`

Include i file di origine nel pacchetto NuGet. I file di origine sono inclusi nella cartella `src` del pacchetto `nupkg`.

`--include-symbols`

Genera i simboli `nupkg`.

`--no-build`

Non compila il progetto prima della compressione.

`-o|--output <OUTPUT_DIRECTORY>`

Inserisce i pacchetti compilati nella directory specificata.

`-s|--serviceable`

Imposta il flag utilizzabile dai servizi nel pacchetto. Per altre informazioni, vedere [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing) (Blog .NET: .NET 4.5.1 supporta gli aggiornamenti della sicurezza Microsoft per le librerie NuGet di .NET).

`--version-suffix <VERSION_SUFFIX>`

Definisce il valore della proprietà MSBuild `$(VersionSuffix)` nel progetto.

`-v|--verbosity <LEVEL>`

Imposta il livello di dettaglio del comando. I valori consentiti sono `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

---

## <a name="examples"></a>Esempi

Comprimere il progetto nella directory corrente:

`dotnet pack`

Comprimere il progetto `app1`:

`dotnet pack ~/projects/app1/project.csproj`
    
Comprimere il progetto nella directory corrente e inserire i pacchetti risultanti nella cartella `nupkgs`:

`dotnet pack --output nupkgs`

Comprimere il progetto nella directory corrente e inserirlo nella cartella `nupkgs`, ignorando il passaggio relativo alla compilazione:

`dotnet pack --no-build --output nupkgs`

Con il suffisso della versione del progetto configurato come `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` nel file con estensione *csproj*, comprimere il progetto corrente e aggiornare la versione del pacchetto risultante con il suffisso specificato:

`dotnet pack --version-suffix "ci-1234"`

Impostare la versione del pacchetto su `2.1.0` con la proprietà MSBuild `PackageVersion`:

`dotnet pack /p:PackageVersion=2.1.0`

Comprimere il progetto per un [framework di destinazione](../../standard/frameworks.md) specifico:

`dotnet pack /p:TargetFrameworks=net45`
