---
title: Instance Completion Action
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fa2eb347bc69a89545e6145154306f012e23490
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="instance-completion-action"></a>Instance Completion Action
Il **Instance Completion Action** proprietà dell'archivio di istanze del flusso di lavoro SQL consente di specificare se i dati e i metadati delle istanze del flusso di lavoro vengono eliminati dal database di persistenza dopo il completamento delle istanze. I valori consentiti per questa proprietà sono **DeleteAll** e **DeleteNothing**. Nell'elenco seguente vengono descritte queste opzioni:  
  
-   **DeleteAll (impostazione predefinita).** Se il valore della proprietà viene impostato su DeleteAll, i dati e i metadati delle istanze del flusso di lavoro vengono eliminati dal database di persistenza dopo il completamento delle istanze.  
  
-   **DeleteNothing.** Se il valore della proprietà viene impostato su DeleteNothing, i dati e i metadati delle istanze del flusso di lavoro vengono mantenuti nel database di persistenza anche dopo il completamento delle istanze.  
  
    > [!CAUTION]
    >  Il mantenimento delle informazioni sullo stato delle istanze dopo il relativo completamento comporta l'aumento delle dimensioni del database di persistenza. Se le dimensioni del database aumentano, le operazioni del database eseguite dal sottosistema di persistenza richiedono più tempo, pertanto è necessario eliminare periodicamente le informazioni sullo stato delle istanze dal database di persistenza affinché i servizi vengano eseguiti in base alle proprie esigenze di prestazione.
