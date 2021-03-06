---
title: "Proprietà nei controlli Windows Form che supportano le linee guida per l'accesso facilitato"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 967b4a0e883338c756aceef37d11edecfb978527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Proprietà nei controlli Windows Form che supportano le linee guida per l'accesso facilitato
Controlli della casella degli strumenti standard di Windows Form supportano molte delle linee guida di accessibilità, inclusi l'esposizione dello stato attivo e l'esposizione di elementi dello schermo.  
  
## <a name="planning-ahead-for-accessibility"></a>Pianificazione dell'accesso facilitato  
 Proprietà dei controlli è utilizzabile per supportare altre linee guida di accessibilità, come illustrato nella tabella seguente. Inoltre, utilizzare i menu per fornire accesso alle funzionalità del programma.  
  
|Proprietà del controllo|Considerazioni per l'accessibilità|  
|----------------------|--------------------------------------|  
|AccessibleDescription|La descrizione viene segnalata agli strumenti di accessibilità, ad esempio gli screen reader. Gli strumenti per l'accessibilità sono dispositivi e programmi specializzati che consentono agli utenti con disabilità di usare i computer in modo più efficace.|  
|AccessibleName|Il nome che verrà segnalato agli strumenti di accessibilità.|  
|AccessibleRole|Viene descritto l'utilizzo dell'elemento nell'interfaccia utente.|  
|TabIndex|Crea un percorso di navigazione sensibile nel form. È importante per i controlli senza etichette intrinseche, ad esempio caselle di testo che precede nell'ordine di tabulazione all'etichetta associata.|  
|Testo|Usare il carattere "&" per creare le chiavi di accesso. Utilizzando i tasti di scelta fa parte di accesso da tastiera documentato alle funzionalità.|  
|Dimensione carattere|Se le dimensioni del carattere non sono regolabile, quindi deve essere impostato su 10 punti o superiori. Dopo aver impostata la dimensione dello stesso tipo di carattere, tutti i controlli aggiunti in seguito al form avranno le stesse dimensioni.|  
|Forecolor|Se questa proprietà è impostata sul valore predefinito, le preferenze dell'utente colore verranno usate nel form.|  
|Backcolor|Se questa proprietà è impostata sul valore predefinito, le preferenze dell'utente colore verranno usate nel form.|  
|BackgroundImage|Omettere questa proprietà per rendere più leggibile il testo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione Windows ad Accesso facilitato](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
