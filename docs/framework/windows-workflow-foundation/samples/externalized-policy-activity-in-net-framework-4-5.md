---
title: "Attività ExternalizedPolicy in .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9dc86cd8ff3cce31e67c146e099f70181ad1e33a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Attività ExternalizedPolicy in .NET Framework 4.5
Questo esempio viene illustrato come l'attività ExternalizedPolicy4 consenta l'esecuzione esistente [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> oggetti [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 4.5) direttamente tramite il motore regole di business che viene fornito in WF 3.5. Usando questa attività, è possibile aprire ed eseguire un oggetto <xref:System.Workflow.Activities.Rules.RuleSet> esistente di WF 3.5. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WF 3.5 motore regole di business inclusi come parte di Windows Workflow Foundation, vedere [Introduzione al motore regole di Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=166079). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]migrazione di regole per [!INCLUDE[wf1](../../../../includes/wf1-md.md)] in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], leggere le indicazioni migrazione [materiale sussidiario sulla migrazione](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="projects-in-this-sample"></a>Progetti di questo esempio  
  
|Nome progetto|Descrizione|File principali|  
|-|-|-|  
|ExternalizedPolicy4|Contiene l'attività ExternalizedPolicy4 e la relativa finestra di progettazione di WF 4.5.|**Externalizedpolicy4**: definizione di attività.<br /><br /> **Externalizedpolicy4designer**: finestra di progettazione personalizzata per l'attività ExternalizedPolicy4. Usa l'editor delle regole (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) dal motore per le regole di WF 3.5.|  
|ImperativeCodeClientSample|Applicazione client di esempio che configura ed esegue un flusso di lavoro tramite un'applicazione ExternalizedPolicy4 e il codice C# imperativo (non viene usata alcuna finestra di progettazione).|**ApplyDiscount**: File con [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definizioni delle regole.<br /><br /> **Cs**: tipo che rappresenta un ordine del cliente. Le regole vengono applicate agli oggetti di questo tipo.<br /><br /> **Program.cs**: configura ed esegue un flusso di lavoro che dispone di un'attività Policy4 per applicare le regole definite in ApplyDiscount alle istanze degli oggetti Order.<br /><br /> App.config: file di configurazione con il percorso del file delle regole.|  
|DesignerClientSample|Applicazione client di esempio che configura ed esegue un flusso di lavoro tramite un'applicazione ExternalPolicy4 nella finestra di progettazione di [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1**: flusso di lavoro sequenza che usa un'attività Policy4 per eseguire valutazioni delle regole.<br /><br /> **Program.cs**: esegue un'istanza del flusso di lavoro definito in Sequence1.|  
  
## <a name="the-externalizedpolicy4-activity"></a>Attività ExternalizedPolicy4  
 L'attività ExternalizedPolicy4 è un oggetto <xref:System.Activities.NativeActivity> che consente l'esecuzione degli oggetti <xref:System.Workflow.Activities.Rules.RuleSet> di WF 3.5 all'interno dei flussi di lavoro di WF 4.5. L'esempio seguente è una definizione semplificata del modello a oggetti pubblico dell'attività.  
  
```  
public class ExternalizedPolicy4Activity<TResult>: CodeActivity  
{  
    public string RulesFilePath   
  
    public string RuleSetName           
  
    [RequiredArgument]  
    public InArgument<T> TargetObject   
  
    [RequiredArgument]  
    public OutArgument<T> ResultObject   
  
    public OutArgument<ValidationErrorCollection> ValidationErrors   
}  
```  
  
|Proprietà|Descrizione|  
|-|-|  
|RuleSetFilePath|Percorso del file <xref:System.Workflow.Activities.Rules.RuleSet> di .NET Framework 3.5 da valutare quando viene eseguita l'attività.|  
|RuleSetName|Nome dell'oggetto <xref:System.Workflow.Activities.Rules.RuleSet> da usare all'interno del file con estensione rules.|  
|TargetObject|Oggetto nel quale gli oggetti <xref:System.Workflow.Activities.Rules.Rule> vengono valutati rispetto all'oggetto <xref:System.Workflow.Activities.Rules.RuleSet>.|  
|ResultObject|Oggetto risultante dopo aver applicato le regole (ad esempio le regole vengono applicate rispetto all'argomento di input e il risultato viene archiviato nell'argomento Result).|  
|ValidationError|Elenco di errori di convalida restituiti dal motore per le regole di WF 3.5 quando si convalida l'oggetto <xref:System.Workflow.Activities.Rules.RuleSet> rispetto all'oggetto di destinazione prima dell'esecuzione.|  
  
## <a name="externalizedpolicy4-activity-designer"></a>ActivityDesigner di ExternalizedPolicy4  
 La finestra di progettazione ExternalizedPolicy4 consente di configurare un'attività per usare un oggetto RuleSet esistente senza scrivere codice. È sufficiente impostare il percorso in cui si trova il file con estensione rules e specificare il nome dell'oggetto <xref:System.Workflow.Activities.Rules.RuleSet> che si desidera usare. Consente inoltre di modificare l'oggetto <xref:System.Workflow.Activities.Rules.RuleSet>. Dopo aver compilato la soluzione, è disponibile nella casella degli strumenti nella sezione Microsoft.Samples.Activities.Rules. La finestra di progettazione consente di selezionare un file con estensione rules e un oggetto <xref:System.Workflow.Activities.Rules.RuleSet>. Quando il **modifica RuleSet** pulsante WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> viene visualizzato. Questa finestra di dialogo è l'editor delle regole di WF 3.5 rieseguito nell'host e viene usata per visualizzare e modificare le regole eseguite dall'attività ExternalizedPolicy4.  
  
## <a name="policy4-and-externalpolicy4"></a>Policy4 e ExternalPolicy4  
 Il [attività Policy in .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) attività consente di creare ed eseguire un set di regole di .NET Framework 3.5 in un flusso di lavoro di WF 4.5. L'oggetto <xref:System.Workflow.Activities.Rules.RuleSet> è serializzato inline nella definizione XML dell'attività Policy4. Nell'esempio ExternalizedPolicy4 viene illustrato come usare un oggetto <xref:System.Workflow.Activities.Rules.RuleSet> esterno esistente (contenuto in un file con estensione rules).  
  
## <a name="using-this-sample"></a>Utilizzo dell'esempio  
 Per eseguire questo esempio non è necessaria alcuna configurazione particolare. Aprire la soluzione in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e premere F5 per eseguire l'applicazione.  
  
 In questo esempio sono contenute due applicazioni client: ImperativeCodeClientSample e DesignerClientSample. Nel client ImperativeCodeClientSample viene illustrato come configurare ed eseguire l'attività ExternalizedPolicy4 tramite il codice imperativo C#. In DesignerClientSample viene illustrato come configurare ed eseguire l'attività ExternalizedPolicy4 tramite la finestra di progettazione.  
  
#### <a name="to-run-the-imperativecodeclientsample-application"></a>Per eseguire l'applicazione ImperativeCodeClientSample  
  
1.  In [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] aprire il file della soluzione Policy4sample.sln.  
  
2.  In **Esplora**, fare doppio clic su di **ImperativeCodeClientSample** del progetto e quindi selezionare **imposta come progetto di avvio**.  
  
3.  Per eseguire il progetto, premere CTRL+F5.  
  
#### <a name="to-run-the-designerclientsample-application"></a>Per eseguire l'applicazione DesignerClientSample  
  
1.  In [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] aprire il file della soluzione Policy4sample.sln.  
  
2.  In **Esplora**, fare doppio clic su di **DesignerClientSample** del progetto e quindi selezionare **imposta come progetto di avvio**.  
  
3.  Per compilare il progetto, premere CTRL+MAIUSC+B.  
  
4.  Premere CTRL+F5 per eseguire il progetto.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare alla sezione relativa agli [esempi di Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) per .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti gli esempi di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
