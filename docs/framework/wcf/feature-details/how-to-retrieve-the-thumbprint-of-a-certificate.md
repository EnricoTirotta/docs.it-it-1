---
title: 'Procedura: recuperare l''identificazione personale di un certificato'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f6d00d31023aa8d6dbfec4a8306f1cb9da17c74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Procedura: recuperare l'identificazione personale di un certificato
Quando si scrive un'applicazione [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] che usa un certificato X.509 per l'autenticazione, è spesso necessario specificare le attestazioni trovate nel certificato. È, ad esempio, necessario fornire un'attestazione di identificazione personale in caso di utilizzo dell'enumerazione <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> nel metodo <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> . La ricerca del valore dell'attestazione richiede due passaggi. Aprire innanzitutto lo snap-in MMC (Microsoft Management Console) per i certificati. Per informazioni, vedere [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Quindi, come descritto qui, cercare un certificato appropriato e copiarne l'identificazione personale o gli altri valori di attestazione.  
  
 Se si sta usando un certificato per l'autenticazione del servizio, è importante notare il valore della colonna **Rilasciato a** (la prima colonna nella console). Quando si usa SSL (Secure Sockets Layer) come protezione del trasporto, una dei primi controlli eseguiti consiste nel confrontare l'URI (Uniform Resource Identifier) dell'indirizzo di base di un servizio con il valore **Rilasciato a** . I valori devono corrispondere o il processo di autenticazione viene interrotto.  
  
 È inoltre possibile usare lo strumento Makecert.exe di [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK per creare certificati temporanei da usare solo durante lo sviluppo. Per impostazione predefinita, tale certificato non viene tuttavia emesso da un'autorità di certificazione e non può essere usato a scopo di produzione. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Procedura: creare certificati temporanei da usare durante lo sviluppo](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Per recuperare l'identificazione personale di un certificato  
  
1.  Aprire lo snap-in MMC (Microsoft Management Console) per i certificati. Per informazioni, vedere [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Nel riquadro sinistro della finestra **Radice console** fare clic su **Certificati (computer locale)**.  
  
3.  Fare clic sulla cartella **Personale** per espanderla.  
  
4.  Fare clic sulla cartella **Certificati** per espanderla.  
  
5.  Nell'elenco dei certificati notare l'intestazione **Scopi designati** . Cercare un certificato che riporti **Autenticazione client** come scopo designato.  
  
6.  Fare doppio clic sul certificato.  
  
7.  Nella finestra di dialogo **Certificati** fare clic sulla scheda **Dettagli** .  
  
8.  Scorrere l'elenco di campi e fare clic su **Identificazione personale**.  
  
9. Copiare i caratteri esadecimali dalla casella. Se questa identificazione personale viene usata nel codice per `X509FindType`, rimuovere gli spazi tra i numeri esadecimali. Ad esempio, l'identificazione personale "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d che 42 77 a3 2a 7b" nel codice deve essere specificata come "a909502dd82ae41433e6f83886b00d4277a32a7b".  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Procedura: Configurare una porta con un certificato SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Procedura: Visualizzare certificati con lo snap-in MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Procedura: Creare certificati temporanei da usare durante lo sviluppo](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
