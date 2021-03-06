---
title: Istruzione Namespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a>Istruzione Namespace
Dichiara il nome di uno spazio dei nomi e fa sì che il codice sorgente che segue la dichiarazione deve essere compilato all'interno di tale spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Parti  
 Global  
 Parametro facoltativo. Consente di definire uno spazio dei nomi lo spazio dei nomi radice del progetto. Vedere [gli spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Obbligatorio. Un nome univoco che identifica lo spazio dei nomi. Deve essere un valido identificatore Visual Basic. Per ulteriori informazioni, vedere [nomi di elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Parametro facoltativo. Elementi che costituiscono lo spazio dei nomi. Queste includono, ma non sono limitate a, enumerazioni, strutture, interfacce, classi, moduli, i delegati e altri spazi dei nomi.  
  
 `End Namespace`  
 Termina un `Namespace` blocco.  
  
## <a name="remarks"></a>Note  
 Spazi dei nomi vengono utilizzati come sistema organizzativo. Forniscono un modo per classificare e presentare gli elementi di programmazione che vengono esposti ad altre applicazioni e programmi. Si noti che non è uno spazio dei nomi un *tipo* nel senso che è una classe o struttura, è possibile dichiarare un elemento di programmazione per il tipo di dati di uno spazio dei nomi.  
  
 Tutti gli elementi di programmazione dichiarati dopo un `Namespace` istruzione appartengono allo spazio dei nomi. Visual Basic continua a compilare elementi nello spazio dei nomi dichiarato ultimo finché incontra uno un `End Namespace` istruzione o un'altra `Namespace` istruzione.  
  
 Se uno spazio dei nomi è già definita, anche all'esterno del progetto, è possibile aggiungere elementi di programmazione. A tale scopo, utilizzare un `Namespace` istruzione per indicare a Visual Basic per compilare gli elementi in tale spazio dei nomi.  
  
 È possibile utilizzare un `Namespace` istruzione solo a livello di file o spazio dei nomi. Ciò significa che il *contesto della dichiarazione* per uno spazio dei nomi deve essere un file di origine o un altro spazio dei nomi e non può essere una classe, struttura, modulo, interfaccia o stored procedure. Per altre informazioni, vedere [Contesti delle dichiarazioni e livelli di accesso predefiniti](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 È possibile dichiarare uno spazio dei nomi all'interno di altra. Non è previsto alcun limite strict ai livelli di nidificazione è possibile dichiarare, ma tenere presente che quando l'altro codice accede a elementi dichiarati nello spazio dei nomi più interno, è necessario utilizzare una stringa di qualificazione che contiene tutti i nomi di spazio dei nomi nella gerarchia di annidamento.  
  
## <a name="access-level"></a>Livello di accesso  
 Spazi dei nomi sono trattati come se fossero un `Public` livello di accesso. Uno spazio dei nomi sono accessibili da qualsiasi codice nello stesso progetto, da altri progetti che fanno riferimento al progetto e da qualsiasi assembly compilato dal progetto.  
  
 Gli elementi di programmazione dichiarati a livello di spazio dei nomi, ovvero in uno spazio dei nomi ma non all'interno di qualsiasi altro elemento, possono avere `Public` o `Friend` accesso. Se non viene specificato, il livello di accesso di tale elemento utilizza `Friend` per impostazione predefinita. Gli elementi che è possibile dichiarare il livello di spazio dei nomi includono classi, strutture, moduli, interfacce, enumerazioni e delegati. Per altre informazioni, vedere [Contesti delle dichiarazioni e livelli di accesso predefiniti](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Namespace radice  
 Tutti i nomi di spazio dei nomi nel progetto sono basati su un *spazio dei nomi radice*. Visual Studio assegna il nome del progetto come spazio dei nomi radice predefinito per tutto il codice del progetto. Se, ad esempio, il progetto è denominato `Payroll`, i relativi elementi di programmazione appartengono allo spazio dei nomi `Payroll`. Se si dichiara `Namespace funding`, il nome completo dello spazio dei nomi è `Payroll.funding`.  
  
 Se si desidera specificare uno spazio dei nomi esistente in un `Namespace` istruzione, come nell'esempio di classe di elenco generico, è possibile impostare lo spazio dei nomi radice con un valore null. A tale scopo, fare clic su **le proprietà del progetto** dal **progetto** menu e quindi deselezionare la **spazio dei nomi radice** voce in modo che la casella è vuota. Se non è questo nell'esempio della classe di elenco generico, il compilatore Visual Basic richiederebbe `System.Collections.Generic` come un nuovo spazio dei nomi all'interno di progetto `Payroll`, con il nome completo del `Payroll.System.Collections.Generic`.  
  
 In alternativa, è possibile utilizzare il `Global` (parola chiave) per fare riferimento agli elementi di spazi dei nomi definiti all'esterno del progetto. In questo modo consente di mantenere il nome dello spazio dei nomi radice del progetto. In questo modo si riduce la possibilità di involontariamente unire gli elementi di programmazione a quelli degli spazi dei nomi esistenti. Per ulteriori informazioni, vedere la sezione "Global (parola chiave) in nomi completi" in [spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 Il `Global` parola chiave può essere utilizzata anche in un'istruzione Namespace. Ciò consente di definire uno spazio dei nomi all'esterno dello spazio dei nomi radice del progetto. Per ulteriori informazioni, vedere la sezione "Parola chiave Global in istruzioni Namespace" [spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Risoluzione dei problemi.** Lo spazio dei nomi radice può causare impreviste concatenazioni di spazi dei nomi. Se si fa riferimento a spazi dei nomi definiti all'esterno del progetto, il compilatore Visual Basic può interpretarli come spazi dei nomi annidati nello spazio dei nomi radice. In tal caso, il compilatore non riconosce tutti i tipi che sono stati già definiti negli spazi dei nomi esterno. Per evitare questo problema, impostare lo spazio dei nomi radice per un valore null come descritto in "Radice Namespace" oppure utilizzare il `Global` (parola chiave) per accedere agli elementi di spazi dei nomi esterni.  
  
## <a name="attributes-and-modifiers"></a>Gli attributi e modificatori  
 Non è possibile applicare attributi per uno spazio dei nomi. Un attributo fornisce informazioni per i metadati dell'assembly, che non è significativa per classificatori di origine, ad esempio spazi dei nomi.  
  
 Non è possibile applicare qualsiasi accesso o modificatori di routine o altri modificatori, uno spazio dei nomi. Perché non è un tipo, questi modificatori non sono significativi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente dichiara due spazi dei nomi nidificati l'uno in altro.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente dichiara più spazi dei nomi annidati in una singola riga, ed è equivalente all'esempio precedente.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente accede alla classe definita negli esempi precedenti.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene definito lo scheletro di una nuova classe di elenco generico e lo aggiunge al <xref:System.Collections.Generic?displayProperty=nameWithType> dello spazio dei nomi.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione Imports (tipo e spazio dei nomi .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Nomi di elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
