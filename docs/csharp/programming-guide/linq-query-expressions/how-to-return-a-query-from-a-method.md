---
title: "Procedura: ottenere una query da un metodo (Guida per programmatori C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "il metodo restituisce una query [C#]"
  - "query [LINQ in C#], il metodo restituisce una query"
  - "query (espressioni) [LINQ in C#], il metodo restituisce una query"
ms.assetid: 9d6f20a7-f085-44cf-9df3-71948255ec68
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Procedura: ottenere una query da un metodo (Guida per programmatori C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

In questo esempio viene illustrato come restituire una query da un metodo come valore restituito e come parametro `out`.  
  
 Una query deve contenere un tipo di <xref:System.Collections.IEnumerable> o <xref:System.Collections.Generic.IEnumerable%601> o un tipo derivato quale <xref:System.Linq.IQueryable%601>.  Qualsiasi valore restituito o parametro `out` di un metodo che restituisce una query deve pertanto contenere anche quel tipo.  Se un metodo materializza una query in un tipo <xref:System.Collections.Generic.List%601> o <xref:System.Array> concreto, verranno restituiti i risultati della query anziché la query stessa.  Una variabile di query restituita da un metodo può ancora essere composta o modificata.  
  
## Esempio  
 Nell'esempio seguente il primo metodo restituisce una query come valore restituito, mentre il secondo metodo restituisce una query come parametro `out`.  In entrambi casi, viene restituita una query e non vengono restituiti i risultati della query.  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-a-query-from-a-method_1.cs)]  
  
## Compilazione del codice  
  
-   Creare un progetto [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] destinato a .NET Framework versione 3.5 o successiva.  Per impostazione predefinita, il progetto include un riferimento a System.Core.dll e una direttiva `using` per lo spazio dei nomi System.Linq.  
  
-   Sostituire la classe con il codice dell'esempio.  
  
-   Premere F5 per compilare ed eseguire il programma.  
  
-   Premere un tasto per chiudere la finestra della console.  
  
## Vedere anche  
 [Espressioni di query LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)