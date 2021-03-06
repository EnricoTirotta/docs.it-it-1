---
title: Enumerazione CorAssemblyFlags
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
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 059d896842c285bb071a25990ae9178c34ab802a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="corassemblyflags-enumeration"></a>Enumerazione CorAssemblyFlags
Contiene valori che descrivono i metadati applicati alla compilazione di un assembly.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`afPublicKey`|Indica che il riferimento all'assembly contiene la chiave pubblica completa, senza hash.|  
|`afPA_None`|Indica che l'architettura del processore non è specificata.|  
|`afPA_MSIL`|Indica che l'architettura del processore è neutra (PE32).|  
|`afPA_x86`|Indica che l'architettura del processore x86 (PE32).|  
|`afPA_IA64`|Indica che l'architettura del processore Itanium (PE32 +).|  
|`afPA_AMD64`|Indica che l'architettura del processore AMD X64 (PE32 +).|  
|`afPA_ARM`|Indica che l'architettura del processore ARM (PE32).|  
|`afPA_NoPlatform`|Indica che l'assembly è un assembly di riferimento. ovvero, si applica a qualsiasi architettura, ma non è possibile eseguire su qualsiasi architettura. Di conseguenza, il flag è identico `afPA_Mask`.|  
|`afPA_Specified`|Indica che i flag di architettura del processore devono essere propagati ad il `AssemblyRef` record.|  
|`afPA_Mask`|Maschera che descrive l'architettura del processore.|  
|`afPA_FullMask`|Specifica che la descrizione dell'architettura del processore è inclusa.|  
|`afPA_Shift`|Indica un numero di spostamenti nei flag di architettura del processore da e verso l'indice.|  
|`afEnableJITcompileTracking`|Indica il valore corrispondente di <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> del <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Indica il valore corrispondente di <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> del <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Indica che l'assembly può essere reindirizzato in fase di esecuzione a un assembly da un server di pubblicazione diverso.|  
|`afContentType_Mask`|Maschera che descrive il tipo di contenuto.|  
|`afContentType_Default`|Indica il tipo di contenuto predefinito.|  
|`afContentType_WindowsRuntime`|Indica il [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo di contenuto.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorHdr. H  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
