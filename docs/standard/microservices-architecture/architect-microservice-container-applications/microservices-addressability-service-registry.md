---
title: "Indirizzabilità dei microservizi e registro del servizio"
description: "Architettura dei microservizi .NET per le applicazioni .NET in contenitori | Indirizzabilità dei microservizi e registro del servizio"
keywords: Docker, microservizi, ASP.NET, contenitore
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc26b22d18d460fe6870da7360d73368e20f71d2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Indirizzabilità dei microservizi e registro del servizio

Ad ogni microservizio viene associato un nome univoco (URL) usato per risolverne il percorso. I microservizi, infatti, devono essere indirizzabili ovunque vengano eseguiti. Se è necessario pensare su quale computer è in esecuzione un determinato microservizio, qualcosa non va. Analogamente al processo con cui il DNS risolve un URL in un determinato computer, il microservizio deve avere un nome univoco in modo che la sua posizione corrente sia facilmente individuabile. I microservizi, quindi, devono avere nomi indirizzabili che li rendono indipendenti dall'infrastruttura su cui sono in esecuzione. Deve esserci inoltre un'interazione tra il modo in cui il servizio viene distribuito e quello in cui viene individuato: deve essere quindi presente un [registro del servizio](http://microservices.io/patterns/service-registry.html). In caso di errore in un computer, il servizio registro deve essere in grado di indicare dove è in esecuzione il servizio.

Lo [schema del registro del servizio](http://microservices.io/patterns/service-registry.html) è un componente essenziale per l'individuazione del servizio. Il registro è costituito invece da un database contenente i percorsi di rete delle istanze del servizio. Il registro del servizio, quindi, deve essere sempre aggiornato e altamente disponibile. I client possono memorizzare nella cache i percorsi di rete ottenuti dal registro del servizio. Queste informazioni, tuttavia, diventano presto obsolete e i client non riescono più a individuare le istanze del servizio. È per questo motivo che il registro del servizio è costituito da un cluster di server che usano un protocollo di replica per mantenere la coerenza.

In alcuni ambienti di distribuzione dei microservizi (denominati cluster e illustrati in una sezione successiva), l'individuazione del servizio è una procedura predefinita. Nell'ambiente di un servizio contenitore di Azure, ad esempio, Kubernetes e DC/OS con Marathon possono gestire le procedure di registrazione e annullamento della registrazione delle istanze del servizio. Eseguono inoltre un proxy su ogni cluster host che svolge il ruolo di router di individuazione sul lato server. Un altro esempio è Azure Service Fabric, che offre un registro del servizio tramite il servizio di denominazione predefinito.

Osservare come sia presente una certa sovrapposizione tra il registro del servizio e lo schema API Gateway, altro aspetto che contribuisce a risolvere il problema. Il [proxy inverso di Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy), ad esempio, è un tipo di implementazione di API Gateway basato sul servizio di denominazione di Service Fabric e semplifica la risoluzione degli indirizzi dei servizi interni.

## <a name="additional-resources"></a>Risorse aggiuntive

-   **Chris Richardson. Pattern: Service registry (Schema: Service registry)**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0. The Service Registry (Auth0. Registro del servizio)**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Service discovery (Individuazione del servizio)**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Precedente] (maintain-microservice-apis.md) [Successivo] (microservice-based-composite-ui-shape-layout.md)
