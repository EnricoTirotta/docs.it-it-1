---
title: ICorDebugILFrame Interface1
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
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Rappresenta uno stack frame del codice Microsoft intermediate language (MSIL). Questa interfaccia è una sottoclasse dell'interfaccia ICorDebugFrame.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo CanSetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Ottiene un valore che indica se è sicuro impostare il puntatore all'istruzione alla posizione di offset specificata.|  
|[Metodo EnumerateArguments](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Ottiene un enumeratore per gli argomenti nel frame.|  
|[Metodo EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Ottiene un enumeratore per le variabili locali nel frame.|  
|[Metodo GetArgument](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Ottiene il valore dell'argomento specificato in questo stack frame MSIL.|  
|[Metodo GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Ottiene il valore del puntatore all'istruzione e un valore di combinazione bit per bit che descrive la modalità in cui è stato ottenuto il valore del puntatore all'istruzione.|  
|[Metodo GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Ottiene il valore della variabile locale specificata in questo stack frame MSIL.|  
|[Metodo GetStackDepth](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Non implementato.|  
|[Metodo GetStackValue](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Non implementato.|  
|[Metodo SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Imposta il puntatore all'istruzione alla posizione di offset specificata nel codice MSIL.|  
  
## <a name="remarks"></a>Note  
 Il `ICorDebugILFrame` è un'interfaccia ICorDebugFrame specializzata. Viene utilizzato per il frame di codice MSIL o per just-in-time (JIT) i frame compilati. I frame compilato tramite JIT implementano sia la `ICorDebugILFrame` interfaccia e l'interfaccia ICorDebugNativeFrame.  
  
> [!NOTE]
>  Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, Cordebug. H  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
