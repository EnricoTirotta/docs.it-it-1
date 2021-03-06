---
title: '&lt;parametro&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdbb47fcb65273d03d226e13730849170d4345c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt"></a>&lt;parametro&gt;
Specifica il parametro generico quando un tipo dichiarato è un tipo generico.  
  
 \<Serialization >  
\<dataContractSerializer >  
\<declaredTypes > elemento  
\<aggiungere > elemento per \<declaredTypes >  
\<knownType > elemento  
\<parametro > elemento  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|indice|Quando il tipo dichiarato è un tipo generico, specifica il parametro generico che restituirà il tipo conosciuto.|  
|tipo|Stringa che descrive il tipo conosciuto usato per la serializzazione e la deserializzazione.|  
  
## <a name="index-attribute"></a>Attributo index  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|"0"|Primo parametro del tipo generico. Ad esempio, un elenco <xref:System.Collections.Generic.List%601> presenta un solo parametro. Se tale parametro viene usato come tipo dichiarato, impostare l'attributo index su "0".|  
|"1"|Secondo parametro di un tipo generico. Ad esempio, un dizionario <xref:System.Collections.Generic.Dictionary%602> presenta due parametri. Se il tipo conosciuto viene restituito dal secondo parametro, impostare l'attributo index su "1".|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Specifica un tipo conosciuto restituibile da un campo o da una proprietà del tipo dichiarato.|  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]i tipi noti, vedere [tipi conosciuti di contratto dati](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Vedere il [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) per un esempio di utilizzo di questo elemento.  
  
 Questo elemento di configurazione non può avere contemporaneamente entrambi gli attributi. Se si impostano entrambi gli attributi, si verifica un'eccezione <xref:System.Configuration.ConfigurationErrorsException>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Tipi noti di contratto di dati](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
