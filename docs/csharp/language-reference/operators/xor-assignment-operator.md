---
title: "Operatore ^= (Riferimenti per C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "^=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "^= (operatore) [C#]"
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operatore ^= (Riferimenti per C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Operatore di assegnazione di OR esclusivo.  
  
## Note  
 Un'espressione con il seguente formato:  
  
```  
x ^= y  
```  
  
 viene valutata come  
  
```  
x = x ^ y  
```  
  
 con la differenza che `x` viene valutato solo una volta.  L'[operatore ^](../../../csharp/language-reference/operators/xor-operator.md) esegue un'operazione con OR esclusivo bit per bit sugli operandi integrali e con OR esclusivo logico sugli operandi [bool](../../../csharp/language-reference/keywords/bool.md).  
  
 L'operatore ^\= non può essere sottoposto direttamente a overload; tuttavia, i tipi definiti dall'utente possono eseguire l'overload dell'[operatore^](../../../csharp/language-reference/operators/xor-operator.md) \(vedere [operator](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Esempio  
 [!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## Vedere anche  
 [Riferimenti per C\#](../../../csharp/language-reference/index.md)   
 [Guida per programmatori C\#](../../../csharp/programming-guide/index.md)   
 [Operatori](../../../csharp/language-reference/operators/index.md)