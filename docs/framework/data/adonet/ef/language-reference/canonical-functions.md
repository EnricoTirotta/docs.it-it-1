---
title: Funzioni canoniche
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="canonical-functions"></a>Funzioni canoniche
Contenuto della sezione vengono illustrate le funzioni canoniche supportate da tutti i provider di dati e che possono essere usate da tutte le tecnologie di query. Le funzioni canoniche non possono essere estese da un provider.  
  
 Queste funzioni canoniche vengono convertite nella funzionalità dell'origine dati corrispondente per il provider. In questo modo è possibile esprimere le chiamate alle funzioni con un formato comune per tutte le origini dati.  
  
 Poiché queste funzioni canoniche sono indipendenti dalle origini dati, i relativi tipi di argomento e tipi restituiti sono definiti in termini di tipi nel modello concettuale. Alcune origini dati potrebbero tuttavia non supportare tutti i tipi nel modello concettuale.  
  
 Quando si usano funzioni canoniche in una query [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la funzione appropriata viene chiamata nell'origine dati.  
  
 Per tutte le funzioni canoniche sono specificati in modo esplicito sia il comportamento in caso di input null che le condizioni di errore. I provider dell'archivio devono essere conformi a tale comportamento, ma questo comportamento non viene applicato da [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
 Per gli scenari LINQ, le query eseguite sul [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] comportano il mapping di metodi CLR ai metodi nell'origine dati sottostante. I metodi CLR sono mappati alle funzioni canoniche, pertanto un set di metodi specifico può essere mappato correttamente indipendentemente dall'origine dati.  
  
## <a name="canonical-functions-namespace"></a>Spazio dei nomi delle funzioni canoniche  
 Lo spazio dei nomi per le funzioni canoniche è <xref:System.Data.Metadata.Edm>. Lo spazio dei nomi <xref:System.Data.Metadata.Edm> viene incluso automaticamente in tutte le query. Se tuttavia viene importato un altro spazio dei nomi contenente una funzione con lo stesso nome di una funzione canonica (nello spazio dei nomi <xref:System.Data.Metadata.Edm>), è necessario specificare lo spazio dei nomi.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzioni di aggregazione canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 Vengono illustrate le funzioni canoniche [!INCLUDE[esql](../../../../../../includes/esql-md.md)] di aggregazione.  
  
 [Funzioni matematiche canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 Vengono illustrate le funzioni canoniche [!INCLUDE[esql](../../../../../../includes/esql-md.md)] matematiche.  
  
 [Funzioni stringa canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 Vengono illustrate le funzioni canoniche [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per i valori stringa.  
  
 [Funzioni data e ora canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 Vengono illustrate le funzioni canoniche [!INCLUDE[esql](../../../../../../includes/esql-md.md)] di data e ora.  
  
 [Funzioni bit per bit canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 Vengono illustrate le funzioni canoniche [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit per bit.  
  
 [Funzioni spaziali](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 Vengono illustrate le funzioni canoniche spaziali di [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Altre funzioni canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 Vengono illustrate le funzioni non classificate come bit per bit, di data e ora, per i valori stringa, matematiche o di aggregazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Riferimento a Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Mapping di funzioni canoniche del modello concettuale a funzioni SQL Server](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [Funzioni definite dall'utente](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
