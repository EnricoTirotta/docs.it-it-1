---
title: 'Procedura: incrementare e decrementare i puntatori (Guida per programmatori C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Procedura: incrementare e decrementare i puntatori (Guida per programmatori C#)
Gli operatori di incremento e decremento `++` e `--` consentono di modificare la posizione del puntatore in base a [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) per un puntatore di tipo pointer-type*. Il formato delle espressioni di incremento e decremento è il seguente:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 È possibile applicare gli operatori di incremento e decremento ai puntatori di qualsiasi tipo, ad eccezione del tipo `void*`.  
  
 Quando si applica l'operatore di incremento a un puntatore di tipo `pointer-type`, si aggiunge [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) all'indirizzo contenuto nella variabile del puntatore.  
  
 Quando si applica l'operatore di decremento a un puntatore di tipo `pointer-type`, si sottrae `sizeof` (`pointer-type`) dall'indirizzo contenuto nella variabile del puntatore.  
  
 Quando l'operazione causa un overflow del dominio del puntatore, non vengono generate eccezioni e il risultato dipende dall'implementazione.  
  
## <a name="example"></a>Esempio  
 Questo esempio mostra come passare da un elemento di una matrice all'altro incrementando il puntatore della dimensione di `int`. A ogni passaggio vengono visualizzati l'indirizzo e il contenuto dell'elemento della matrice.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Valore:0 @ Indirizzo:12860272**  
**Valore:1 @ Indirizzo:12860276**  
**Valore:2 @ Indirizzo:12860280**  
**Valore:3 @ Indirizzo:12860284**  
**Valore:4 @ Indirizzo:12860288**   
## <a name="see-also"></a>Vedere anche  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Espressioni puntatore](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operatori C#](../../../csharp/language-reference/operators/index.md)  
 [Modifica dei puntatori](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Tipi di puntatori](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipi](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Istruzione fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
