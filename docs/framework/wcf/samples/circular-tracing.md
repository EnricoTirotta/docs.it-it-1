---
title: Analisi circolare
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4942e7e23b3cddd0f1c5bd3be8195ceeb190ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="circular-tracing"></a>Analisi circolare
Questo esempio illustra l'implementazione di un listener traccia circolare del buffer. Un scenario comune per i servizi in un ambiente di produzione è avere servizi disponibili per lunghi periodi e avere la registrazione analisi attivata a un livello basso. Questi servizi utilizzano molto spazio su disco. Durante la risoluzione dei problemi di un servizio, i dati più recenti del registro di traccia sono attinenti alla risoluzione di un problema. Questo esempio illustra l'implementazione di un listener di traccia circolare del buffer in cui solo tracce più recenti vengono tenute su disco fino al raggiungimento di una quantità configurabile di dati. Questo esempio è basato sul [Introduzione](../../../../docs/framework/wcf/samples/getting-started-sample.md) e include un listener di traccia personalizzata.  
  
> [!NOTE]
>  La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.  
  
 Questo esempio si presuppone che si ha familiarità con la [traccia e registrazione dei messaggi](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) di esempio e di aver letto la documentazione fornita per il [traccia e registrazione dei messaggi](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) esempio.  
  
## <a name="circular-buffer-trace-listener"></a>Listener di traccia circolare del buffer  
 Il concetto alla base dell'implementazione del Listener di traccia circolare del buffer è avere due file in grado di contenere, singolarmente, la metà dei dati totali che si desidera inserire nel registro di traccia. Il listener crea un file e scrive in quel file fino al raggiungimento della metà dei dati totali, a quel punto passa a scrivere sul secondo file. Quando il listener raggiunge il limite per il secondo file - sovrascrive il primo file con le nuove tracce.  
  
 Listener deriva il `XmlWriteTraceListener` e consente i registri da visualizzare con il [strumento Visualizzatore di tracce dei servizi (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Quando si desidera visualizzare il log, i due file possono essere facilmente ricombinati aprendoli contemporaneamente nello strumento Service Trace Viewer. Lo strumento Service Trace Viewer si occupa automaticamente di ordinare le tracce, che verranno visualizzate nell'ordine corretto.  
  
## <a name="configuration"></a>Configurazione  
 Un servizio può essere configurato per utilizzare il Listener di traccia circolare del buffer aggiungendo il codice seguente per un listener e gli elementi di origine. La dimensione massima del file viene specificata impostando l'attributo `maxFileSizeKB` durante la configurazione listener di traccia circolare, come illustrato nell'esempio di codice riportato di seguito.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio  
  
1.  Assicurarsi di avere eseguito la [procedura di installazione singola per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Per eseguire l'esempio in una configurazione a una o più computer, seguire le istruzioni in [esegue gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare alla sezione relativa agli [esempi di Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) per .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti gli esempi di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Vedere anche  
 [Esempi di monitoraggio di AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
