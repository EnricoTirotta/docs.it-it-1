---
title: Metodo ICorRuntimeHost::CreateDomainEx
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
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a2a577e1bd8765c7359e521b007bea943de7a984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a>Metodo ICorRuntimeHost::CreateDomainEx
Crea un dominio applicazione. Il chiamante riceve un puntatore a interfaccia di tipo <xref:System._AppDomain>, a un'istanza di tipo <xref:System.AppDomain?displayProperty=nameWithType>. Questo metodo consente al chiamante di passare un'istanza di IAppDomainSetup per configurare le funzionalità aggiuntive dell'oggetto restituito <xref:System._AppDomain> istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pwzFriendlyName`  
 [in] Parametro facoltativo utilizzato per assegnare un nome descrittivo per il dominio. Questo nome descrittivo può essere visualizzato nelle interfacce utente, ad esempio i debugger per identificare il dominio.  
  
 `pSetup`  
 [in] Un puntatore a interfaccia facoltativo di tipo `IAppDomainSetup`, ottenuto da una chiamata al [ICorRuntimeHost:: CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metodo.  
  
 `pIdentityArray`  
 [in] Matrice facoltativa di puntatori a `IIdentity` istanze che rappresentano evidenze mappate tramite criteri di sicurezza per stabilire un set di autorizzazioni. Un `IIdentity` oggetto può essere ottenuto chiamando il [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metodo.  
  
 `pAppDomain`  
 [out] Un puntatore a interfaccia di tipo <xref:System._AppDomain> a un'istanza di <xref:System.AppDomain?displayProperty=nameWithType> che può essere utilizzato per controllare ulteriormente il dominio.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|L'operazione è riuscita.|  
|S_FALSE|Impossibile completare l'operazione.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Se un metodo restituisce E_FAIL, common language runtime (CLR) non è più utilizzabile nel processo. Le chiamate successive a qualsiasi API di hosting restituiranno HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.|  
  
## <a name="remarks"></a>Note  
 `CreateDomainEx`estende le funzionalità di [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) consentendo al chiamante di passare un `IAppDomainSetup` istanza con i valori delle proprietà per configurare il dominio applicazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Mscoree. H  
  
 **Libreria:** inclusa come risorsa in MSCorEE.dll  
  
 **Versione di .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [Metodo CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [Interfaccia ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
