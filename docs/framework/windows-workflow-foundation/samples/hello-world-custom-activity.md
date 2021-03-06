---
title: "Attività personalizzata Hello World"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 155726e5cd65c2f31a3205a8d18f662b66fb40e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="hello-world-custom-activity"></a>Attività personalizzata Hello World
In questo esempio vengono illustrate diverse funzionalità chiave di [!INCLUDE[wf](../../../../includes/wf-md.md)], inclusa la modalità di creazione di una semplice attività personalizzata. Alcune delle funzionalità illustrate in questo esempio creano un'attività personalizzata in C# e usano argomenti `in` e `out` (<xref:System.Activities.InArgument> e <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare alla sezione relativa agli [esempi di Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) per .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti gli esempi di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Creazione di un flusso di lavoro nel codice  
 In questo esempio vengono create due attività personalizzate usando codice C#. Entrambe le attività personalizzate ereditano direttamente o indirettamente da <xref:System.Activities.Activity%601> per restituire un solo valore. Il vantaggio dell'utilizzo del valore restituito generico, anziché ereditare dalla classe non generica <xref:System.Activities.Activity> è che alcune attività (ad esempio <xref:System.Activities.Statements.Assign>) sono in grado di accedere al valore restituito quando è usato come parte di un'attività composta.  
  
 AppendString  
 Questa attività eredita da <xref:System.Activities.Activity%601>e usa un'attività <xref:System.Activities.Statements.Assign> che concatena due stringhe.  
  
 Prepend String  
 Questa attività eredita direttamente da <xref:System.Activities.CodeActivity%601>e crea la funzionalità simile all'attività `AppendString` che usa la logica implementata nel codice piuttosto che composta da un'attività preesistente.  
  
 In questo progetto sono inclusi i file seguenti:  
  
 AppendString.cs  
 Attività personalizzata che unisce stringhe. Accetta una stringa e li combina con una stringa letterale "says hello world" per formare un messaggio completo come output.  
  
 PrependString.cs  
 Questa attività premette una stringa predefinita a una stringa di input.  
  
 Sequence1.xaml  
 Flusso di lavoro che usa le attività personalizzate `AppendString` e `PrependString`.  
  
 Program.cs  
 Programma che esegue il flusso di lavoro.  
  
#### <a name="to-use-this-sample"></a>Per usare questo esempio  
  
1.  In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] aprire il file della soluzione HelloWorld.sln.  
  
2.  Per compilare la soluzione, premere CTRL+MAIUSC+B.  
  
3.  Per eseguire la soluzione, premere F5.