---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a>/codepage (Visual Basic)
Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a>Argomenti  
  
|Termine|Definizione|  
|---|---|  
|`id`|Obbligatorio. Il compilatore Usa la tabella codici specificata da `id` per interpretare la codifica dei file di origine.|  
  
## <a name="remarks"></a>Note  
 Per compilare codice sorgente salvato con una codifica specifica, è possibile utilizzare `/codepage` per specificare la tabella codici da utilizzare. Il `/codepage` opzione si applica a tutti i file di codice sorgente nella compilazione. Per ulteriori informazioni, vedere [codifica dei caratteri in .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 Il `/codepage` opzione non è necessaria se sono stati salvati i file di codice sorgente utilizzando la tabella codici ANSI corrente, Unicode o UTF-8 con una firma. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]Salva tutti i file di codice sorgente con la tabella codici ANSI corrente per impostazione predefinita, a meno che l'utente specifica una codifica diversa nella finestra di **codifica** la finestra di dialogo. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]Usa il **codifica** la finestra di dialogo per aprire il file del codice sorgente salvato con una diversa tabella codici.  
  
> [!NOTE]
>  Il `/codepage` opzione non è disponibile all'interno di [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ambiente di sviluppo; è disponibile solo durante la compilazione dalla riga di comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilatore della riga di comando di Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
