---
title: Controllo dell'avvio automatico di Host servizio WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Controllo dell'avvio automatico di Host servizio WCF
È possibile controllare le funzionalità di avvio automatico dell'host del servizio [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (WcfSvcHost.exe) per un progetto Libreria di servizi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] quando si esegue il debug di un altro progetto nella stessa soluzione [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] contenente più progetti.  
  
 A tale scopo, fare doppio clic su di [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] progetto di servizio in **Esplora**, scegliere **proprietà**, fare clic su **opzioni WCF** scheda. Il **avvia Host servizio WCF durante il debug di un altro progetto nella stessa soluzione** casella di controllo è abilitata per impostazione predefinita. È possibile deselezionare la casella in modo che l'host del servizio [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] per questo progetto specifico non venga avviato durante il debug di un altro progetto nella stessa soluzione.  
  
 Questo comportamento non influisce sulle funzionalità di debug con F5 o con l'opzione Aggiungi riferimento al servizio per questo progetto.  
  
 Questa opzione è disponibile per i progetti seguenti:  
  
-   Progetto Libreria di servizi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
-   Progetto Libreria di servizi del flusso di lavoro sequenziale.  
  
-   Progetto Libreria di servizi del flusso di lavoro di una macchina a stati.  
  
-   Progetto Libreria di servizi di diffusione.  
  
## <a name="see-also"></a>Vedere anche  
 [Host del servizio WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
