---
title: 'Procedura: Creare file e directory nello spazio di memorizzazione isolato'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf6295e7d58d03e7b4bf4e0a00cfc509d289e071
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Procedura: Creare file e directory nello spazio di memorizzazione isolato
Dopo aver ottenuto uno spazio di memorizzazione isolato, è possibile creare directory e file per l'archiviazione dei dati. All'interno di un archivio i nomi di file e directory vengono specificati rispetto alla radice del file system virtuale.  
  
 Per creare una directory, usare il metodo di istanza <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>. Se si specifica una sottodirectory di una directory che non esiste, vengono create entrambe le directory. Se si specifica una directory che esiste già, il metodo restituisce risultati senza creare una directory e non viene generata alcuna eccezione. Tuttavia, se si specifica un nome di directory che contiene caratteri non validi, viene generata un'eccezione <xref:System.IO.IsolatedStorage.IsolatedStorageException>.  
  
 Per creare un file, utilizzare il metodo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>.  
  
 Nel sistema operativo Windows i nomi di file e directory dello spazio di memorizzazione isolato non fanno distinzione tra maiuscole e minuscole. Di conseguenza, se si crea un file denominato `ThisFile.txt` e quindi un altro file denominato `THISFILE.TXT`, viene creato un solo file. Il nome del file mantiene le maiuscole e minuscole originali ai fini della visualizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente mostra come creare file e directory in uno spazio di memorizzazione isolato.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Spazio di memorizzazione isolato](../../../docs/standard/io/isolated-storage.md)
