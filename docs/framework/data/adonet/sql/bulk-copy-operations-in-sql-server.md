---
title: Operazioni di copia di massa in SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6efca83c6d3157e7fc4ff0e49ad32cab7cee9251
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operazioni di copia di massa in SQL Server
Microsoft SQL Server include una popolare utilità della riga di comando denominata **bcp** per rapidamente la copia di massa file di grandi dimensioni in tabelle o viste nei database di SQL Server. La classe <xref:System.Data.SqlClient.SqlBulkCopy> consente di scrivere soluzioni di codice gestito che offrono funzionalità simili. Esistono altri metodi per caricare dati in una tabella SQL Server (ad esempio con l'istruzione INSERT) ma <xref:System.Data.SqlClient.SqlBulkCopy> offre prestazioni molto più vantaggiose.  
  
 La classe <xref:System.Data.SqlClient.SqlBulkCopy> consente di scrivere dati solo su tabelle SQL Server. Tuttavia l'origine dati non si limita a SQL Server ed è possibile usare qualsiasi origine i cui dati possano essere caricati in un'istanza <xref:System.Data.DataTable> oppure letti con un'istanza <xref:System.Data.IDataReader>.  
  
 Con la classe <xref:System.Data.SqlClient.SqlBulkCopy> è possibile eseguire le seguenti operazioni:  
  
-   Copia di massa singola  
  
-   Più copie di massa  
  
-   Copia bulk all'interno di una transazione  
  
> [!NOTE]
>  Quando si utilizza .NET Framework versione 1.1 o precedente (che non supporta il <xref:System.Data.SqlClient.SqlBulkCopy> classe), è possibile eseguire SQL Server Transact-SQL **BULK INSERT** istruzione tramite il <xref:System.Data.SqlClient.SqlCommand> oggetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Creazione di esempi di copia di massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Vengono descritte le tabelle usate negli esempi di copia di massa e vengono forniti gli script SQL per la creazione di tabelle nel database AdventureWorks.  
  
 [Singole operazioni di copia di massa](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Viene descritto come eseguire una copia di massa singola di dati in un'istanza di SQL Server usando la classe <xref:System.Data.SqlClient.SqlBulkCopy> e come eseguire la copia di massa con istruzioni Transact-SQL e con la classe <xref:System.Data.SqlClient.SqlCommand>.  
  
 [Più operazioni di copia di massa](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Viene descritto come eseguire più copie di massa di dati in un'istanza di SQL Server usando la classe <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 [Transazioni e operazioni di copia bulk](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Viene descritto come eseguire una copia bulk all'interno di una transazione e come eseguire il commit e il rollback della transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server e ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](http://go.microsoft.com/fwlink/?LinkId=217917)
