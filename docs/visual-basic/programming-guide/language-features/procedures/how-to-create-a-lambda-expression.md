---
title: "How to: Create a Lambda Expression (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Lambda Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Un'*espressione lambda* è una funzione o una subroutine che non ha un nome.  È possibile utilizzare un'espressione lambda ogni volta che è valido un tipo delegato.  
  
### Per creare una funzione di espressione lambda a riga singola  
  
1.  In qualsiasi situazione in cui potrebbe essere utilizzato un tipo delegato, digitare la parola chiave `Function`, come nell'esempio seguente:  
  
     `Dim add1 =`   `Function`  
  
2.  Tra parentesi, direttamente dopo `Function`, digitare i parametri della funzione.  Notare che non viene specificato un nome dopo `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Dopo l'elenco dei parametri, digitare una sola espressione come corpo della funzione.  Il valore che l'espressione darà come risultato è il valore restituito alla funzione chiamante.  Non utilizzare una clausola `As` per specificare il tipo restituito.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     L'espressione lambda viene chiamata passando un argomento integer.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  In alternativa, si raggiunge lo stesso risultato come illustrato nell'esempio seguente:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### Per creare una subroutine di espressione lambda a riga singola  
  
1.  In qualsiasi situazione in cui potrebbe essere utilizzato un tipo delegato, digitare la parola chiave `Sub`, come nell'esempio seguente:  
  
     `Dim add1 =`   `Sub`  
  
2.  Tra parentesi, direttamente dopo `Sub`, digitare i parametri della subroutine.  Notare che non viene specificato un nome dopo `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Dopo l'elenco di parametri, digitare una singola istruzione come corpo della subroutine.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     L'espressione lambda viene chiamata passando un argomento string.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### Per creare una funzione di espressione lambda su più righe  
  
1.  In qualsiasi situazione in cui potrebbe essere utilizzato un tipo delegato, digitare la parola chiave `Function`, come nell'esempio seguente:  
  
     `Dim add1 =`   `Function`  
  
2.  Tra parentesi, direttamente dopo `Function`, digitare i parametri della funzione.  Notare che non viene specificato un nome dopo `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Premere INVIO.  L'istruzione `End Function` viene aggiunta automaticamente.  
  
4.  Nel corpo della funzione aggiungere il codice seguente per creare un'espressione e restituire il valore.  Non utilizzare una clausola `As` per specificare il tipo restituito.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     L'espressione lambda viene chiamata passando un argomento integer.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### Per creare una subroutine di espressione lambda su più righe  
  
1.  In qualsiasi situazione in cui potrebbe essere utilizzato un tipo delegato, digitare la parola chiave `Sub`, come nell'esempio seguente:  
  
     `Dim add1 =`   `Sub`  
  
2.  Tra parentesi, direttamente dopo `Sub`, digitare i parametri della subroutine.  Notare che non viene specificato un nome dopo `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Premere INVIO.  L'istruzione `End Sub` viene aggiunta automaticamente.  
  
4.  Nel corpo della funzione aggiungere il codice seguente che deve essere eseguito quando viene richiamata la subroutine.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     L'espressione lambda viene chiamata passando un argomento string.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## Esempio  
 Un utilizzo comune delle espressioni lambda è definire una funzione che può essere passata come argomento per un parametro il cui tipo è `Delegate`.  Nell'esempio riportato di seguito, il metodo <xref:System.Diagnostics.Process.GetProcesses%2A> restituisce una matrice dei processi in esecuzione sul computer locale.  Il metodo <xref:System.Linq.Enumerable.Where%2A> della classe <xref:System.Linq.Enumerable> richiede un delegato `Boolean` come argomento.  L'espressione lambda nell'esempio viene utilizzata a questo scopo.  Restituisce `True` per ogni processo che dispone di un solo thread e quelli selezionati in `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 L'esempio precedente è equivalente al codice seguente, scritto in sintassi [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## Vedere anche  
 <xref:System.Linq.Enumerable>   
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)