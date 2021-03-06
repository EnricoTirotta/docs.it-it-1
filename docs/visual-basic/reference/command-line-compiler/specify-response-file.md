---
title: '@ (specificare il file di risposta) (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ced258713983ded06fa70cb65d56071b41cdc75b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="-specify-response-file-visual-basic"></a>@ (specificare il file di risposta) (Visual Basic)
Specifica un file che contiene le opzioni del compilatore e il file di codice sorgente da compilare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argomenti  
 `response_file`  
 Obbligatorio. Un file che elenca le opzioni del compilatore o file di codice sorgente da compilare. Racchiudere il nome del file tra virgolette ("") se contiene uno spazio.  
  
## <a name="remarks"></a>Note  
 Il compilatore elabora le opzioni del compilatore e i file del codice sorgente specificati in un file di risposta come se fossero stati specificati nella riga di comando.  
  
 Per specificare più di un file di risposta in una compilazione, è possibile specificare più opzioni di file di risposta, ad esempio le operazioni seguenti.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 In una risposta file, più opzioni del compilatore e i file del codice sorgente possono essere visualizzati in una sola riga. Specifica una singola opzione del compilatore deve essere presente una riga (non può estendersi su più righe). File di risposta possono contenere commenti che iniziano con la `#` simbolo.  
  
 È possibile combinare le opzioni specificate nella riga di comando con le opzioni specificate in uno o più file di risposta. Il compilatore elabora le opzioni di comando quando vengono rilevate. Di conseguenza, gli argomenti della riga di comando possono eseguire l'override opzioni elencate in precedenza nel file di risposta. Al contrario, le opzioni in un file di risposta ignorano le opzioni elencate in precedenza nella riga di comando o in altri file di risposta.  
  
 Visual Basic fornisce tale file si trova nella stessa directory del file Vbc.exe. Tale file è incluso per impostazione predefinita, a meno che il `/noconfig` viene utilizzata l'opzione. Per ulteriori informazioni, vedere [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  Il `@` opzione non è disponibile all'interno dell'ambiente di sviluppo di Visual Studio; è disponibile solo durante la compilazione dalla riga di comando.  
  
## <a name="example"></a>Esempio  
 Le righe seguenti sono da un file di risposta di esempio.  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `@` opzione con il file di risposta denominato `File1.rsp`.  
  
```  
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilatore della riga di comando di Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Esempi di righe di comando di compilazione](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
