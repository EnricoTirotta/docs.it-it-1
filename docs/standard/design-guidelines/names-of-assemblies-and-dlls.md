---
title: Nomi di assembly e DLL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f74c37821d730ec8dcaa74763967c662bafd6699
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="names-of-assemblies-and-dlls"></a>Nomi di assembly e DLL
Un assembly è l'unità di distribuzione e l'identità per i programmi di codice gestito. Anche se l'assembly possono estendersi su uno o più file, in genere un assembly esegue il mapping uno a uno con una DLL. Pertanto, in questa sezione descrive solo DLL convenzioni di denominazione, che è quindi possono eseguire il mapping alle convenzioni di denominazione di assembly.  
  
 **✓ SI** scegliere nomi per l'assembly DLL che suggeriscono di grandi blocchi di funzionalità, ad esempio System. Data.  
  
 Nomi di assembly e DLL non sono necessario che corrispondano ai nomi di spazio dei nomi, ma è consigliabile seguire il nome dello spazio dei nomi, la denominazione degli assembly. Una buona regola pratica viene assegnato un nome della DLL in base al prefisso comune degli spazi dei nomi contenuti nell'assembly. Ad esempio, un assembly con due spazi dei nomi `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, potrebbe essere chiamato `MyCompany.MyTechnology.dll`.  
  
 **Provare a ✓** denominazione DLL in base al modello seguente:  
  
 `<Company>.<Component>.dll`  
  
 dove `<Component>` contiene uno o più clausole separati da punti. Ad esempio:  
  
 `Litware.Controls.dll`.  
  
 *Parti © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *State ristampate dall'autorizzazione di Pearson Education, Inc. da [linee guida: convenzioni, idiomi e modelli per le librerie .NET di riutilizzabile, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina e Brad Abrams, pubblicato il 22 ottobre 2008 di Addison-Wesley Professional come parte della serie di sviluppo di Microsoft Windows.*  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)  
 [Convenzioni di denominazione](../../../docs/standard/design-guidelines/naming-guidelines.md)
