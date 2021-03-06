---
title: "&#39; &lt;classname&gt;&#39; non è conforme a CLS perché l'interfaccia &#39;&lt; InterfaceName&gt;&#39; implements non è conforme a CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1f0d1e1f54b6b667431ceae2e346a4118c5b1a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39; &lt;classname&gt;&#39; non è conforme a CLS perché l'interfaccia &#39;&lt; InterfaceName&gt;&#39; implements non è conforme a CLS
Una classe o interfaccia è contrassegnata come `<CLSCompliant(True)>` quando deriva da o implementa un tipo contrassegnato come `<CLSCompliant(False)>` o non è contrassegnata.  
  
 Per una classe o un'interfaccia è compatibile con il [indipendenza del linguaggio e componenti indipendenti dal linguaggio](../../../standard/language-independence-and-language-independent-components.md) (CLS), la gerarchia di ereditarietà deve essere conforme. Ciò significa che ogni tipo da cui eredita, direttamente o indirettamente, deve essere conforme. Analogamente, se una classe implementa una o più interfacce, esse devono essere tutte conformi nelle relative gerarchie di ereditarietà.  
  
 Quando <xref:System.CLSCompliantAttribute> viene applicato a un elemento di programmazione, il parametro `isCompliant` dell'attributo viene impostato su `True` o `False` per indicare la conformità o la non conformità. L'impostazione predefinita per questo parametro non è disponibile, quindi è necessario specificare un valore.  
  
 Se a un elemento non viene applicato <xref:System.CLSCompliantAttribute> , l'elemento non sarà considerato conforme.  
  
 Per impostazione predefinita, si tratta di un messaggio di avviso. Per informazioni su come nascondere gli avvisi o considerarli come errori, vedere [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID errore:** BC40029  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Se è necessaria la conformità a CLS, definire il tipo all'interno di uno schema di implementazione o una gerarchia di ereditarietà diversi.  
  
-   Se è necessario che questo tipo resti all'interno dello schema di implementazione o della gerarchia di ereditarietà corrente, rimuovere <xref:System.CLSCompliantAttribute> dalla relativa definizione o contrassegnarlo come `<CLSCompliant(False)>`.  
  
 
