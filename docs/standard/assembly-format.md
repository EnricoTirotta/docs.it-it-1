---
title: Formato dei file di assembly .NET
description: Informazioni sul formato dei file di assembly .NET, usato per descrivere e contenere le app e le librerie .NET.
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d219a584f2f5521fc3b0fd00ab037a8e486c9050
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="net-assembly-file-format"></a>Formato dei file di assembly .NET

.NET definisce un formato di file binario, "assembly", che viene usato per descrivere completamente e contenere i programmi .NET. Gli assembly vengono usati per i programmi, nonché per tutte le librerie dipendenti. Un programma .NET può essere eseguito come uno di più assembly, senza altri elementi necessari, oltre all'implementazione di .NET appropriata. Le dipendenze native, incluse le API del sistema operativo, rappresentano una problematica separata e non sono contenute nel formato di assembly .NET, anche se a volte vengono descritte con questo formato (ad esempio, WinRT).

> Ogni componente CLI usa metadati specifici per dichiarazioni, implementazioni e riferimenti. Quindi, i metadati specifici di un componente sono indicati come metadati del componente e il componente risultante viene definito come autodescrittivo, in base alla specifica ECMA 335 I.9.1 relativa a componenti e assembly.

Il formato è completamente specificato e standardizzato come [ECMA 335](http://www.ecma-international.org/publications/standards/Ecma-335.htm). Tutti i compilatori e runtime .NET usano questo formato. La presenza di un formato binario documentato e aggiornato di rado richiede rappresenta uno dei principali vantaggi, probabilmente un requisito, in termini di interoperabilità. Il formato è stato aggiornato in modo sostanziale per l'ultima volta nel 2005 (.NET 2.0) per supportare generics e architettura del processore.

Il formato è indipendente dalla CPU e dal sistema operativo. È stato usato come parte delle implementazioni di .NET che usano molti chip e CPU. Anche se è basato su Windows, il formato può essere implementato in qualsiasi sistema operativo. Il motivo per cui è considerato la scelta migliore per l'interoperabilità del sistema operativo è il fatto che la maggior parte dei valori vengono archiviati in formato little endian. Non presenta un'affinità specifica alle dimensioni del puntatore del computer, ad esempio 32 bit o 64 bit.

Il formato di assembly .NET offre anche una descrizione accurata della struttura di un programma o una libreria specifica. Descrive i componenti interni di un assembly, in particolare i riferimenti e i tipi di assembly e la relativa struttura interna. Gli strumenti o le API sono in grado di leggere ed elaborare queste informazioni per la visualizzazione o per prendere decisioni a livello di codice.

## <a name="format"></a>Formato

Il formato binario .NET è basato sul formato di [file PE](http://en.wikipedia.org/wiki/Portable_Executable) di Windows. Di fatto le librerie di classi .NET sono compatibili ai file PE di Windows e appaiono a prima vista come librerie a collegamento dinamico (DLL) o file eseguibili di applicazione (EXE) di Windows. Questa è una caratteristica molto utile in Windows, poiché le librerie possono essere mascherate da file binari eseguibili nativi e ricevere lo stesso trattamento (ad esempio, il carico del sistema operativo e gli strumenti PE).

![Intestazioni di assembly](./media/assembly-format/assembly-headers.png)

Intestazioni di assembly da ECMA 335 II.25.1, struttura del formato di file di runtime.

## <a name="processing-the-assemblies"></a>Elaborazione degli assembly

È possibile scrivere strumenti o API per elaborare gli assembly. Le informazioni sugli assembly consentono di prendere decisioni a livello di codice in fase di runtime, riscrivere gli assembly, inserire IntelliSense di API in un editor e generare documentazione. <xref:System.Reflection?displayProperty=nameWithType> e [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) sono due esempi di strumenti usati di frequente per questo scopo.
