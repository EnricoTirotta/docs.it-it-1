---
title: -appconfig (opzioni del compilatore C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (opzioni del compilatore C#)
L'opzione **-appconfig** del compilatore consente a un'applicazione C# di specificare il percorso del file di configurazione (app.config) dell'applicazione di un assembly per Common Language Runtime (CLR) in fase di associazione degli assembly.  
  
## <a name="syntax"></a>Sintassi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argomenti  
 `file`  
 Obbligatorio. Il file di configurazione dell'applicazione che contiene le impostazioni di associazione degli assembly.  
  
## <a name="remarks"></a>Note  
 L'opzione **-appconfig** può essere usata anche in scenari avanzati nei quali un assembly deve fare riferimento allo stesso tempo alla versione di .NET Framework e a quella di .NET Framework per Silverlight di un particolare assembly di riferimento. Ad esempio, una finestra di progettazione XAML scritta in Windows Presentation Foundation (WPF) potrebbe fare riferimento al desktop WPF, per l'interfaccia utente della finestra di progettazione, e al subset di WPF incluso in Silverlight. Lo stesso assembly della finestra di progettazione deve accedere a entrambi gli assembly. Per impostazione predefinita, i riferimenti separati provocano un errore del compilatore, poiché l'associazione di assembly considera uguali i due assembly.  
  
 L'opzione **-appconfig** del compilatore consente di specificare il percorso del file app.config che disabilita il comportamento predefinito tramite un tag `<supportPortability>`, come illustrato nell'esempio seguente.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Il compilatore passa il percorso del file alla logica di associazione degli assembly di CLR.  
  
> [!NOTE]
>  Se si usa Microsoft Build Engine (MSBuild) per compilare l'applicazione, è possibile impostare l'opzione **-appconfig** del compilatore aggiungendo un tag di proprietà al file con estensione csproj. Per usare il file app.config già impostato nel progetto, aggiungere un tag di proprietà `<UseAppConfigForCompiler>` al file con estensione csproj e impostarne il valore su `true`. Per specificare un file app.config diverso, aggiungere un tag di proprietà `<AppConfigForCompiler>` e impostarne il valore sul percorso del file.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra un file app.config che consente a un'applicazione di fare riferimento all'implementazione di .NET Framework e di .NET Framework per Silverlight per qualsiasi assembly di .NET Framework presente in entrambe le implementazioni. L'opzione **-appconfig** del compilatore specifica il percorso di questo file app.config.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<supportPortability> Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md) (Elemento <supportPortability>)  
 [Opzioni del compilatore C# in ordine alfabetico](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
