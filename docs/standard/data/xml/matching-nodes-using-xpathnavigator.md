---
title: Corrispondenza di nodi utilizzando XPathNavigator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06849e20386f0eecb55fdf906f78896828b9946e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a>Corrispondenza di nodi utilizzando XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fornisce il metodo <xref:System.Xml.XPath.XPathNavigator.Matches%2A> per determinare se un nodo corrisponde a un'espressione XPath. Il metodo <xref:System.Xml.XPath.XPathNavigator.Matches%2A> accetta un'espressione XPath come input e restituisce un oggetto <xref:System.Boolean> che indica se il nodo corrente corrisponde all'espressione XPath o all'oggetto <xref:System.Xml.XPath.XPathExpression> compilato fornito.  
  
## <a name="matching-nodes"></a>Corrispondenza di nodi  
 Il metodo <xref:System.Xml.XPath.XPathNavigator.Matches%2A> restituisce `true` se il nodo corrente corrisponde all'espressione XPath specificata. Ad esempio, nel seguente esempio di codice, il metodo <xref:System.Xml.XPath.XPathNavigator.Matches%2A> restituirà `true` se il nodo corrente è l'elemento `b` e se l'elemento `b` presenta un attributo `c`.  
  
> [!NOTE]
>  Il metodo <xref:System.Xml.XPath.XPathNavigator.Matches%2A> non influisce sullo stato del tipo <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Elaborazione di dati XML con il modello di dati XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Selezionare dati XML con XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Valutare espressioni XPath con XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Tipi di nodo riconosciuti con le query XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Query e spazi dei nomi XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Espressioni XPath compilate](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
