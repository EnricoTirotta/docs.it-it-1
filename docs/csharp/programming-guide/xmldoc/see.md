---
title: '&lt;see&gt; (Guida per programmatori C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 959da56269081ebee036c620e535185609c5bff3
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="ltseegt-c-programming-guide"></a>&lt;see&gt; (Guida per programmatori C#)
## <a name="syntax"></a>Sintassi  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametri  
 cref = " `member`"  
 Riferimento a un membro o a un campo disponibile per essere chiamato dall'ambiente di compilazione corrente. Il compilatore controlla che l'elemento di codice specificato esista e passa `member` al nome dell'elemento nel *membro* XML.Place di output tra virgolette doppie (" ").  
  
## <a name="remarks"></a>Note  
 Con il tag \<see> è possibile specificare un collegamento nel testo. Usare [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) per indicare che il testo deve essere inserito in una sezione Vedere anche. Usare l'[attributo cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) per creare collegamenti ipertestuali interni alle pagine della documentazione per gli elementi di codice.  
  
 Compilare con [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) per elaborare i commenti relativi alla documentazione in un file.  
  
 Nell'esempio seguente viene illustrato un tag \<see> all'interno di una sezione di riepilogo.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)  
 [Tag consigliati per i commenti relativi alla documentazione](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
