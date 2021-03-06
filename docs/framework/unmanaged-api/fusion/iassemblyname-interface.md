---
title: Interfaccia IAssemblyName
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
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 902ad9f67d06306e79666f0e10d85bdb9c65c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblyname-interface"></a>Interfaccia IAssemblyName
Fornisce metodi per la descrizione e l'utilizzo di un'identità univoca di assembly.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo Clone](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|Crea una copia superficiale di questo `IAssemblyName` oggetto.|  
|[Metodo Finalize](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|Questo consente `IAssemblyName` oggetto per rilasciare risorse ed eseguire altre operazioni di pulizia prima che venga chiamato il distruttore.|  
|[Metodo GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|Ottiene il nome leggibile dell'assembly a cui fa riferimento questo `IAssemblyName` oggetto.|  
|[Metodo GetName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|Ottiene il nome semplice non crittografato dell'assembly a cui fa riferimento questo `IAssemblyName` oggetto.|  
|[Metodo GetProperty](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|Ottiene un puntatore alla proprietà a cui fa riferimento specificato `PropertyId`.|  
|[Metodo GetVersion](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|Ottiene le informazioni sulla versione per l'assembly a cui fa riferimento questo `IAssemblyName` oggetto.|  
|[Metodo IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|Determina se un oggetto `IAssemblyName` è uguale all'oggetto `IAssemblyName`, in base ai flag di confronto specificati.|  
|[Metodo SetProperty](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|Imposta il valore della proprietà a cui fa riferimento specificato `PropertyId`.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Fusion. h  
  
 **Versioni di .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Interfaccia IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
