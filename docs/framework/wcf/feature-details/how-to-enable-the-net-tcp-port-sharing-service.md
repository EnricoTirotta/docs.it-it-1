---
title: 'Procedura: attivare il servizio di condivisione delle porte Net.TCP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Procedura: attivare il servizio di condivisione delle porte Net.TCP
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usa un servizio di Windows denominato Servizio di condivisione porte Net.TCP per facilitare la condivisione delle porte TCP tra più processi. Il servizio viene installato come parte di [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ma, per motivi di sicurezza, non viene attivato per impostazione predefinita e deve quindi essere attivato manualmente al primo utilizzo. In questo argomento viene illustrato come configurare il servizio di condivisione delle porte Net TCP usando lo snap-in MMC (Microsoft Management Console).  
  
 Dopo aver abilitato il servizio di condivisione porta Net. TCP e avviarlo manualmente, vedere [procedura: configurare un servizio WCF di utilizzare la condivisione delle porte](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) per informazioni su come configurare il servizio per l'utilizzo di questo servizio.  
  
 Per un esempio che utilizza la condivisione delle porte net.tcp://, vedere il [esempio di condivisione porta Net. TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Per attivare il servizio di condivisione delle porte Net.TCP tramite MMC  
  
1.  Dal menu Start, aprire la Console di gestione dei servizi aprendo una finestra del prompt dei comandi e digitando `services.msc` o aprendo Esegui e digitando `services.msc` nella casella Apri.  
  
2.  Nel **nome** colonna dell'elenco di servizi, fare doppio clic su di **servizio di condivisione porte Net. TCP**e selezionare **proprietà** dal menu.  
  
3.  Per abilitare l'avvio manuale del servizio, nel **proprietà** finestra selezionare il **generale** scheda e il **tipo di avvio** casella selezionare manuale e quindi fare clic su **Applicare**.  
  
4.  Per avviare il servizio, nell'area di stato del servizio, fare clic su di **avviare** pulsante. Lo stato del servizio dovrebbe ora essere "Avviato".  
  
5.  Per tornare all'elenco dei servizi, fare clic su di **OK**e uscire dalla Console di MMC.  
  
## <a name="example"></a>Esempio  
  
## <a name="see-also"></a>Vedere anche  
 [Condivisione delle porte Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Configurazione del servizio di condivisione delle porte Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
