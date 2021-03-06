---
title: Checked e Unchecked (Riferimenti per C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a>Checked e Unchecked (Riferimenti per C#)
È possibile eseguire istruzioni C# in contesti verificati o non verificati. In un contesto verificato l'overflow aritmetico genera un'eccezione. In un contesto non verificato l'overflow aritmetico viene ignorato e il risultato è troncato.  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md) Specificare il contesto verificato.  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specificare il contesto non verificato.  
  
 Se né `checked` né `unchecked` vengono specificati, il contesto predefinito dipende da fattori esterni, ad esempio le opzioni del compilatore.  
  
 Le operazioni seguenti sono interessate dal controllo di overflow:  
  
-   Espressioni che usano gli operatori predefiniti seguenti su tipi integrali:  
  
     `++` `--` - (unario)   `+` -   `*` `/`  
  
-   Conversioni numeriche esplicite tra tipi integrali.  
  
 L'opzione del compilatore [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) consente di specificare il contesto verificato o non verificato per tutte le istruzioni aritmetiche su interi che non rientrano in modo esplicito nell'ambio di una parola chiave `checked` o `unchecked`.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per C#](../../../csharp/language-reference/index.md)  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Parole chiave di C#](../../../csharp/language-reference/keywords/index.md)  
 [Parole chiave per le istruzioni](../../../csharp/language-reference/keywords/statement-keywords.md)
