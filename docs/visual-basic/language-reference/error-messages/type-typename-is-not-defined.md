---
title: "Tipo &#39; &lt;typename&gt;&#39; non è definito"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords: BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Tipo &#39; &lt;typename&gt;&#39; non è definito
L'istruzione ha fatto riferimento a un tipo che non è stato definito. È possibile definire un tipo in un'istruzione di dichiarazione, ad esempio `Enum`, `Structure`, `Class`, o `Interface`.  
  
 **ID errore:** BC30002  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che la definizione del tipo e il relativo riferimento utilizzano la stessa ortografia.  
  
-   Verificare che la definizione del tipo sia accessibile al riferimento. Ad esempio, se il tipo in un altro modulo è stato dichiarato `Private`, spostare la definizione del tipo di modulo di riferimento o dichiararla `Public`.  
  
-   Verificare che lo spazio dei nomi del tipo non viene ridefinito all'interno del progetto. In tal caso, utilizzare il `Global` (parola chiave) per qualificare completamente il nome del tipo. Ad esempio, se un progetto definisce uno spazio dei nomi denominato `System`, <xref:System.Object?displayProperty=nameWithType> tipo non è possibile accedere a meno che non è completo, con la `Global` (parola chiave): `Global.System.Object`.  
  
-   Se il tipo è definito, ma la libreria di oggetti o una libreria dei tipi in cui è definito, non è registrata [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], fare clic su **Aggiungi riferimento** sul **progetto** menu e quindi selezionare l'oggetto appropriato libreria o dei tipi.  
  
-   Verificare che il tipo è un assembly che fa parte del profilo di .NET Framework di destinazione. Per altre informazioni, vedere [Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Vedere anche  
 [Spazi dei nomi in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Istruzione Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Istruzione Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Istruzione Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Istruzione Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Gestione dei riferimenti in un progetto](/visualstudio/ide/managing-references-in-a-project)
