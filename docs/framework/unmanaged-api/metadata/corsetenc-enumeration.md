---
title: Enumerazione CorSetENC
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f39a1481361377fce3f6b55cf6c7daf8c075ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="corsetenc-enumeration"></a>Enumerazione CorSetENC
Contiene valori usati per influenzare il comportamento durante la generazione di metadati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`MDSetENCOn`|Obsoleta.|  
|`MDSetENCOff`|Obsoleta.|  
|`MDUpdateENC`|Indica che, mentre è possibile aggiornare i metadati, token non può essere spostati.|  
|`MDUpdateFull`|Indica che i token possono essere spostati durante gli aggiornamenti.|  
|`MDUpdateExtension`|Indica che gli aggiornamenti possono essere costituiti solo da aggiunte. Token non possono essere spostati.|  
|`MDUpdateIncremental`|Indica che la compilazione incrementale.|  
|`MDUpdateDelta`|Indica che solo i metadati modificati devono essere salvato.|  
|`MDUpdateMask`|Include `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorHdr. H  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
