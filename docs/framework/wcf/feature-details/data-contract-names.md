---
title: Nomi di contratto dati
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56744318e6ea29350fd02d1cb35e49e566894a23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-names"></a>Nomi di contratto dati
Talvolta un client e un servizio non condividono gli stessi tipi. Possono comunque passarsi dati a condizione che i contratti dati siano equivalenti su entrambi i lati. [Equivalenza dei contratti dati](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md) è basato sul contratto dati e i nomi dei membri di dati, e pertanto in cui viene fornito un meccanismo per eseguire il mapping di tipi e membri di tali nomi. In questo argomento vengono illustrate le regole per denominare i contratti dati, nonché il comportamento predefinito dell'infrastruttura [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] quando si creano nomi.  
  
## <a name="basic-rules"></a>Regole di base  
 Le regole di base sulla denominazione di contratti dati sono le seguenti:  
  
-   Un nome di contratto dati completo è costituito da uno spazio dei nomi e da un nome.  
  
-   I membri dati hanno solo nomi, ma non spazi dei nomi.  
  
-   Nell'elaborazione di contratti dati, l'infrastruttura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applica la distinzione tra maiuscole e minuscole sia agli spazi dei nomi che ai nomi di contratto dati e di membro dati.  
  
## <a name="data-contract-namespaces"></a>Spazi dei nomi di contratto dati  
 Uno spazio dei nomi di contratto dati prende il formato di un URI (Uniform Resource Identifier). L'URI può essere assoluto o relativo. Per impostazione predefinita, ai contratti dati per un particolare tipo viene assegnato uno spazio dei nomi che proviene dallo spazio dei nomi CLR (Common Language Runtime) di quel tipo.  
  
 Per impostazione predefinita, qualsiasi spazio dei nomi CLR specificato (nel formato *CLR*) viene eseguito il mapping allo spazio dei nomi "http://schemas.datacontract.org/2004/07/Clr.Namespace". Per eseguire l'override di questa impostazione predefinita, applicare l'attributo <xref:System.Runtime.Serialization.ContractNamespaceAttribute> all'intero modulo o assembly. In alternativa, per controllare lo spazio dei nomi di contratto dati per ogni tipo, impostare la proprietà <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> di <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
> [!NOTE]
>  Lo spazio dei nomi "http://schemas.microsoft.com/2003/10/Serialization" è riservato e non può essere utilizzato come spazio dei nomi di contratto dati.  
  
> [!NOTE]
>  Non è possibile eseguire l'override dello spazio dei nomi predefinito nei tipi di contratto dati che contengono dichiarazioni `delegate`.  
  
## <a name="data-contract-names"></a>Nomi di contratto dati  
 Il nome predefinito di un contratto dati per un determinato tipo è il nome di quel tipo. Per eseguire l'override dell'impostazione predefinita, impostare la proprietà <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> di <xref:System.Runtime.Serialization.DataContractAttribute> su un nome alternativo. Le regole speciali per i tipi generici vengono descritte in "Nomi di contratto dati per tipi generici" più avanti in questo argomento.  
  
## <a name="data-member-names"></a>Nomi di membro dati  
 Il nome predefinito di un membro dati per un campo o una proprietà specifici è il nome di quel campo o di quella proprietà. Per eseguire l'override dell'impostazione predefinita, impostare la proprietà <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> di <xref:System.Runtime.Serialization.DataMemberAttribute> su un valore alternativo.  
  
### <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrato come eseguire l'override del comportamento di denominazione predefinito dei contratti dati e dei membri dati.  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>Nomi di contratto dati per tipi generici  
 Per determinare i nomi di contratto dati per tipi generici, esistono regole speciali. Le regole consentono di evitare collisioni dei nomi di contratto dati tra due generics chiusi dello stesso tipo generico.  
  
 Per impostazione predefinita, nome del contratto dati per un tipo generico è il nome del tipo, seguito dalla stringa "Of", seguito da nomi di contratto dati dei parametri generici, seguiti da un *hash* calcolato utilizzando gli spazi dei nomi del contratto di dati i parametri generici. Un hash è il risultato di una funzione matematica che funge da "impronta digitale" che identifica in modo univoco un blocco di dati. Quando tutti i parametri generici sono tipi primitivi, l'hash viene omesso.  
  
 Vedere, ad esempio, i tipi nell'esempio seguente:  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 In questo esempio, il tipo `Drawing<Square,RegularRedBrush>` ha il nome di contratto dati "DrawingOfSquareRedBrush5HWGAU6h", dove "5HWGAU6h" è un hash degli spazi dei nomi "urn:shapes" e "urn:default". Il tipo `Drawing<Square,SpecialRedBrush>` ha il nome di contratto dati "DrawingOfSquareRedBrushjpB5LgQ_S", dove "jpB5LgQ_S" è un hash degli spazi dei nomi "urn:shapes" e "urn:special". Si noti che se non viene utilizzato l'hash, i due nomi sarebbero identici e si verificherebbe una collisione.  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>Personalizzazione dei nomi di contratto dati per i tipi generici  
 I nomi di contratto dati generati per i tipi generici, come descritto prima, talvolta sono inaccettabili. Si potrebbe ad esempio sapere in anticipo che non si verificheranno collisioni di nomi e si potrebbe volere rimuovere l'hash. In questo caso, è possibile utilizzare la proprietà <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> dell'attributo `DataContractAttribute` per specificare un modo diverso di generare nomi. È possibile utilizzare numeri tra parentesi graffe all'interno della proprietà `Name` per fare riferimento a nomi di contratto dati dei parametri generici. 0 si riferiscono al primo parametro, 1 si riferisce al secondo e così via. È possibile utilizzare un simbolo cancelletto (#) tra parentesi graffe per fare riferimento all'hash. È possibile utilizzare ogni riferimento più volte o non utilizzarlo affatto.  
  
 Ad esempio, il tipo `Drawing` generico precedente avrebbe potuto essere dichiarato come illustrato nell'esempio seguente.  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 In questo caso, il tipo `Drawing<Square,RegularRedBrush>` ha il nome di contratto dati "Drawing_using_RedBrush_brush_and_Square_shape". Si noti che, poiché nella proprietà <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> è presente un segno "{#}", l'hash non è parte del nome, pertanto il tipo è esposto a collisioni di nomi. Il tipo `Drawing<Square,SpecialRedBrush>`, ad esempio, avrebbe esattamente lo stesso nome di contratto dati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [Uso di contratti di dati](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Equivalenza dei contratti di dati](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Nomi di contratto di dati](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Controllo delle versioni dei contratti di dati](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
