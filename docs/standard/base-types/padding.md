---
title: Aggiunta di spaziatura interna alle stringhe in .NET
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea903c1f950e7c226e043c1fa7276a66126b2512
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="padding-strings-in-net"></a>Aggiunta di spaziatura interna alle stringhe in .NET
Usare uno dei metodi <xref:System.String> riportati di seguito per creare una nuova stringa costituita da una stringa originale a cui vengono aggiunti caratteri iniziali o finali fino a una lunghezza totale specificata. Il carattere di riempimento può essere costituito da spazi o da un carattere specificato e di conseguenza viene visualizzato allineato a destra o sinistra.  
  
|Nome metodo|Usa|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Aggiunge caratteri iniziali a una stringa fino a ottenere una lunghezza totale specificata.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Aggiunge caratteri finali a una stringa fino a ottenere una lunghezza totale specificata.|  
  
## <a name="padleft"></a>PadLeft  
 Il metodo <xref:System.String.PadLeft%2A?displayProperty=nameWithType> crea una nuova stringa concatenando un numero sufficiente di caratteri di riempimento iniziali a una stringa originale per ottenere una lunghezza totale specificata. Il metodo <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> usa spazi vuoti come carattere di riempimento e il metodo <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> consente di specificare il proprio carattere di riempimento.  
  
 Nell'esempio di codice seguente viene usato il metodo <xref:System.String.PadLeft%2A> per creare una nuova stringa di venti caratteri. L'esempio visualizza "`--------Hello World!`" nella console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 Il metodo <xref:System.String.PadRight%2A?displayProperty=nameWithType> crea una nuova stringa concatenando un numero sufficiente di caratteri di riempimento finali a una stringa originale per ottenere una lunghezza totale specificata. Il metodo <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> usa spazi vuoti come carattere di riempimento e il metodo <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> consente di specificare il proprio carattere di riempimento.  
  
 Nell'esempio di codice seguente viene usato il metodo <xref:System.String.PadRight%2A> per creare una nuova stringa di venti caratteri. L'esempio visualizza "`Hello World!--------`" nella console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operazioni di base su stringhe](../../../docs/standard/base-types/basic-string-operations.md)
