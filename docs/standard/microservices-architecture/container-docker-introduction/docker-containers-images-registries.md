---
title: Contenitori, immagini e registri Docker
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Contenitori, immagini e registri Docker
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
ms.openlocfilehash: 79dccadfba066c673e8ef7ea5eaf1051a434ff3a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a>Contenitori, immagini e registri Docker

Quando uno sviluppatore usa Docker, crea un app o un servizio e crea un pacchetto contenente l'app o il servizio e le relative dipendenze in un'immagine del contenitore. Un'immagine è una rappresentazione statica dell'app o del servizio, della relativa configurazione e delle dipendenze.

Per eseguire l'app o il servizio, si crea un'istanza dell'immagine dell'app per creare un contenitore che verrà eseguito nell'host Docker. I contenitori vengono inizialmente testati in un PC o in un ambiente di sviluppo.

Gli sviluppatori devono archiviare le immagini in un registro, che funge da libreria di immagini e che è necessario per la distribuzione negli agenti di orchestrazione di produzione. Docker mantiene un registro pubblico tramite l'[hub Docker](https://hub.docker.com/). Altri fornitori offrono registri per diverse raccolte di immagini. In alternativa, le aziende possono gestire un registro privato locale per le proprie immagini Docker.

La figura 2-4 mostra la relazione tra le immagini e i registri in Docker con altri componenti. Mostra inoltre le varie offerte dei fornitori per i registri.

![](./media/image5.PNG)

**Figura 2-4**. Tassonomia dei termini e dei concetti di Docker

L'inserimento delle immagini in un registro permette di archiviare bit di applicazioni statici e immutabili, incluse tutte le dipendenze a livello di framework. È quindi possibile creare diverse versioni delle immagini e distribuirle in più ambienti per fornire un'unità di distribuzione coerente.

I registri di immagini privati, ospitati in locale o nel cloud, sono consigliati nei casi seguenti:

-   Le immagini non devono essere condivise pubblicamente per motivi di riservatezza.

-   Si desidera una latenza di rete minima tra le immagini e l'ambiente di distribuzione scelto. Ad esempio, se l'ambiente di produzione è il cloud di Azure, è consigliabile archiviare le immagini nel Registro contenitori di Azure per una latenza di rete minima. Allo stesso modo, se l'ambiente di produzione è ospitato in locale, è consigliabile che il registro Docker Trusted Registry sia disponibile nella stessa rete locale.

>[!div class="step-by-step"]
[Indietro] (docker-terminology.md) [Avanti] (../net-core-net-framework-containers/index.md)
