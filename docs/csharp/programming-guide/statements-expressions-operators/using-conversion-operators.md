---
title: Utilizzo degli operatori di conversione (Guida per programmatori C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a43332df795d853c3060a604360adeaea5e3fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="using-conversion-operators-c-programming-guide"></a>Utilizzo degli operatori di conversione (Guida per programmatori C#)
È possibile utilizzare gli operatori di conversione `implicit`, che sono più facili da utilizzare, o gli operatori di conversione `explicit`, per indicare chiaramente a chiunque legga il codice che si sta convertendo un tipo. In questo argomento vengono illustrati entrambi i tipi di operatore di conversione.  
  
> [!NOTE]
>  Per informazioni sulle conversioni di tipi semplici, vedere [Procedura: convertire una stringa in un numero](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Procedura: convertire una matrice di byte in un Integer](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Procedura: eseguire la conversione tra stringhe esadecimali e tipi numerici](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) o <xref:System.Convert>.  
  
## <a name="example"></a>Esempio  
 Questo è un esempio di un operatore di conversione esplicita. Questo operatore esegue la conversione dal tipo <xref:System.Byte> in un tipo valore denominato `Digit`. Poiché non tutti i byte possono essere convertiti in una cifra, la conversione è esplicita, ovvero è necessario utilizzare un cast, come illustrato nel metodo `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato un operatore di conversione implicita, definendo un operatore di conversione che annulla quello che è stato fatto nell'esempio precedente: esegue la conversione da una classe di valori denominata `Digit` nel tipo integrale <xref:System.Byte>. Poiché qualsiasi cifra può essere convertita in un <xref:System.Byte>, non è necessario imporre agli utenti l'uso di una conversione esplicita.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per C#](../../../csharp/language-reference/index.md)  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Operatori di conversione](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [is](../../../csharp/language-reference/keywords/is.md)
