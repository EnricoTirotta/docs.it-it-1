---
title: 'Procedura: ottenere il valore di una variabile puntatore (Guida per programmatori C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Procedura: ottenere il valore di una variabile puntatore (Guida per programmatori C#)
L'operatore di riferimento indiretto a puntatore consente di ottenere la variabile nella posizione indicata da un puntatore. L'espressione ha il seguente formato, dove `p` è un tipo di puntatore:  
  
```  
*p;  
```  
  
 Non è possibile usare l'operatore di riferimento indiretto unario o un'espressione di qualsiasi altro tipo diverso dal tipo puntatore. Non è inoltre possibile applicarlo a un puntatore [void](../../../csharp/language-reference/keywords/void.md).  
  
 Quando si applica l'operatore di riferimento indiretto a un puntatore [Null](../../../csharp/language-reference/keywords/null.md), il risultato dipende dall'implementazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente si accede a una variabile di tipo `char` usando puntatori di tipi diversi. Si noti che l'indirizzo di `theChar` varia da un'esecuzione all'altra, perché l'indirizzo fisico allocato a una variabile può cambiare.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **Valore di theChar = Z**  
**Indirizzo di theChar = 12F718**  
**Valore di pChar = Z**   
**Valore di pInt = 90**    
## <a name="see-also"></a>Vedere anche  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Espressioni puntatore](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Tipi di puntatori](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipi](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Istruzione fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
