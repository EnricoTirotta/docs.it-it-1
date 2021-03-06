---
title: -nostdlib (opzioni del compilatore C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dd9d2b6a4a9c774aa339e840ad0020ee39cb10d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (opzioni del compilatore C#)
**-nostdlib** impedisce l'importazione di mscorlib.dll, che definisce l'intero spazio dei nomi di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>Note  
 Usare questa opzione se si vuole definire o creare uno spazio dei nomi e oggetti System personalizzati.  
  
 Se non si specifica **-nostdlib**, mscorlib.dll verrà importata nel programma (equivale a specificare **-nostdlib-**). Specificare **-nostdlib** equivale a specificare **-nostdlib+**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio  
  
1.  Aprire la pagina **Proprietà** del progetto.  
  
2.  Fare clic sulla pagina di proprietà **Compilazione** .  
  
3.  Fare clic su **Avanzate** .  
  
4.  Modificare la proprietà **Ometti riferimenti a libreria standard (mscorlib.dll)** .  
  
 Per informazioni su come impostare questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni del compilatore C#](../../../csharp/language-reference/compiler-options/index.md)
