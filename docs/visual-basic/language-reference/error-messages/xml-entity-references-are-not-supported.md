---
title: "XML entity references are not supported | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31180"
  - "bc31180"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31180"
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML entity references are not supported
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un riferimento all'entità \(ad esempio, `©`\) non definito nella specifica XML 1.0 è incluso come valore per un valore letterale XML.  Solo `&`, `"`, `<`, `>` e i riferimenti all'entità XML `'` sono supportati nei valori letterali XML.  
  
 **ID errore:** BC31180  
  
### Per correggere l'errore  
  
-   Rimuovere il riferimento all'entità non supportato.  
  
## Vedere anche  
 [XML Literals and the XML 1.0 Specification](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)