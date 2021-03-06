---
title: Esecuzione di operazioni in batch (WCF Data Services)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65bf6bfd0bd437848137506605a958f5f2e8d750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="batching-operations-wcf-data-services"></a>Esecuzione di operazioni in batch (WCF Data Services)
Il [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] supporta l'elaborazione delle richieste di batch un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-servizio basato su. Per ulteriori informazioni, vedere [OData: elaborazione Batch](http://go.microsoft.com/fwlink/?LinkId=186075). In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ogni operazione che utilizza il <xref:System.Data.Services.Client.DataServiceContext>, ad esempio l'esecuzione di una query o salvare le modifiche, i risultati di una richiesta separata inviati al servizio dati. Per mantenere un ambito logico per i set di operazioni, è possibile definire in modo esplicito batch operativi. Ciò garantisce che tutte le operazioni nel batch vengono inviati al servizio dati in una singola richiesta HTTP, consente al server di elaborare le operazioni in modo atomico e riduce il numero di round trip al servizio dati.  
  
## <a name="batching-query-operations"></a>Invio in batch di operazioni di query  
 Per eseguire più query in un unico batch, è necessario creare ogni query del batch come istanza separata della classe <xref:System.Data.Services.Client.DataServiceRequest%601>. Quando si crea una richiesta di query in questo modo, la query stessa viene definita come URI a cui vengono applicate le regole per l'indirizzamento di risorse. Per ulteriori informazioni, vedere [accesso alle risorse del servizio dati](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Le richieste di query in batch vengono inviate al servizio dati quando viene chiamato il metodo <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> contenente gli oggetti della richiesta di query. Questo metodo restituisce un oggetto <xref:System.Data.Services.Client.DataServiceResponse> corrispondente a una raccolta di oggetti <xref:System.Data.Services.Client.QueryOperationResponse%601> che rappresentano risposte a singole query incluse nel batch, ognuna delle quali contiene una raccolta di oggetti restituiti dalla query o informazioni sull'errore. Quando una singola operazione di query inclusa nel batch ha esito negativo, le informazioni sull'errore vengono restituite nell'oggetto <xref:System.Data.Services.Client.QueryOperationResponse%601> per l'operazione non riuscita e le operazioni rimanenti vengono comunque eseguite. Per ulteriori informazioni, vedere [procedura: eseguire query in un Batch](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Le query in batch possono inoltre essere eseguite in modo asincrono. Per ulteriori informazioni, vedere [operazioni asincrone](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Invio in batch dell'operazione SaveChanges  
 Quando si chiama il <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> (metodo), tutte le modifiche richieste per il contesto di tracce vengono convertite in operazioni basate su REST che vengono inviate come il [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] servizio. Per impostazione predefinita, queste modifiche non vengono inviate in un unico messaggio di richiesta. Per richiedere di essere inviato tutte le modifiche in una singola richiesta, è necessario chiamare il <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> (metodo) e includere un valore di <xref:System.Data.Services.Client.SaveChangesOptions.Batch> nel <xref:System.Data.Services.Client.SaveChangesOptions> enumerazione fornito al metodo.  
  
 È inoltre possibile salvare modifiche in batch in modo asincrono. Per ulteriori informazioni, vedere [operazioni asincrone](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Libreria client WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
