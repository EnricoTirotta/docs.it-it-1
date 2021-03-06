---
title: "Attività RangeEnumeration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc793d57718dbc68f304d3eb5031a9fa96b00cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="rangeenumeration-activity"></a>Attività RangeEnumeration
In questo esempio viene illustrato come creare un'attività personalizzata che scorre una raccolta di numeri. Nella tabella seguente sono indicati in dettaglio i file principali inclusi nell'esempio.  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|RangeEnumeration.cs|Definisce un'attività personalizzata denominata `RangeEnumeration` che esegue l'override della classe <xref:System.Activities.NativeActivity> e riproduce un ciclo continuo di una serie di numeri.|  
|RangeEnumerationSample.cs|Applicazione client che usa l'attività `RangeEnumeration` per scorrere una raccolta di numeri.|  
  
 Nella tabella seguente sono indicate in dettaglio le proprietà dell'attività `RangeEnumeration`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|Start|Integer da cui iniziare il ciclo.|  
|Interrompi|Integer in corrispondenza del quale arrestare il ciclo.|  
|Passaggio|Specifica la durata di ogni iterazione.|  
|Corpo|Specifica il codice da eseguire durante ogni iterazione.|  
  
#### <a name="to-use-this-sample"></a>Per usare questo esempio  
  
1.  In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] aprire il file della soluzione RangeEnumeration.sln.  
  
2.  Per compilare la soluzione, premere CTRL+MAIUSC+B.  
  
3.  Per eseguire la soluzione, premere CTRL+F5.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare alla sezione relativa agli [esempi di Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) per .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti gli esempi di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`