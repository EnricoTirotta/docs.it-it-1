---
title: Utilizzo della varianza nei delegati (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 435591d69e67c4fc4be8e781c5f63e025c71a8cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-visual-basic"></a>Utilizzo della varianza nei delegati (Visual Basic)
Quando si assegna un metodo a un delegato, *covarianza* e *controvarianza* offrono flessibilità per la corrispondenza di un tipo delegato con una firma di metodo. La covarianza consente a un metodo di avere un tipo restituito più derivato di quello definito nel delegato. La controvarianza consente un metodo con tipi di parametro meno derivati rispetto a quelli del tipo delegato.  
  
## <a name="example-1-covariance"></a>Esempio 1: covarianza  
  
### <a name="description"></a>Descrizione  
 In questo esempio viene illustrato in che modo si possono usare i delegati con i metodi che hanno tipi restituiti derivati dal tipo restituito nella firma del delegato. Il tipo di dati restituito da `DogsHandler` è di tipo `Dogs`, che deriva dal tipo `Mammals` definito nel delegato.  
  
### <a name="code"></a>Codice  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a>Esempio 2: controvarianza  
  
### <a name="description"></a>Descrizione  
 In questo esempio viene illustrato in che modo si possono usare i delegati con i metodi che hanno parametri di un tipo che rappresentano tipi di base del tipo di parametro della firma del delegato. Con la controvarianza è possibile usare un solo gestore eventi anziché gestori separati. Ad esempio, è possibile creare un gestore eventi che accetta un parametro di input `EventArgs` e usarlo con un evento `Button.MouseClick` che invia un tipo `MouseEventArgs` come parametro e anche con un evento `TextBox.KeyDown` che invia un parametro `KeyEventArgs`.  
  
### <a name="code"></a>Codice  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Varianza nei delegati (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [Utilizzo della varianza per i delegati generici Func e Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
