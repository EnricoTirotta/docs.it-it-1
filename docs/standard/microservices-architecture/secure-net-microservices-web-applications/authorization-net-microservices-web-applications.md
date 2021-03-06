---
title: Informazioni sull'autorizzazione in microservizi .NET e applicazioni Web
description: Architettura dei microservizi .NET per le applicazioni .NET in contenitori | Informazioni sull'autorizzazione in microservizi .NET e applicazioni Web
keywords: Docker, microservizi, ASP.NET, contenitore
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cd7be9bc8216aecf85f99a76e859b411a8735b0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Informazioni sull'autorizzazione in microservizi .NET e applicazioni Web

Dopo l'autenticazione, le API Web di ASP.NET Core devono autorizzare l'accesso. Questo processo consente a un servizio di rendere disponibili le API ad alcuni utenti autenticati, ma non a tutti. L'[autorizzazione](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) può essere eseguita in base ai ruoli degli utenti o in base a criteri personalizzati, che possono includere l'analisi delle attestazioni o altre regole euristiche.

Per limitare l'accesso a una route ASP.NET Core MVC è sufficiente applicare un attributo Authorize al metodo di azione (o alla classe del controller, se tutte le azioni del controller richiedono l'autorizzazione), come illustrato nell'esempio seguente:

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Per impostazione predefinita, l'aggiunta di un attributo Authorize senza parametri limita l'accesso agli utenti autenticati per tale controller o azione. Per limitare ulteriormente un'API e renderla disponibile solo per specifici utenti, l'attributo può essere espanso per specificare i criteri o i ruoli richiesti che gli utenti devono soddisfare.

## <a name="implementing-role-based-authorization"></a>Implementazione dell'autorizzazione basata sui ruoli

ASP.NET Core Identity offre funzionalità integrate per i ruoli. Oltre agli utenti, ASP.NET Core Identity archivia informazioni sui diversi ruoli usati dall'applicazione e tiene traccia degli utenti a cui sono assegnati i vari ruoli. Queste assegnazioni possono essere modificate a livello di codice con il tipo RoleManager (che aggiorna i ruoli nell'archiviazione persistente) e il tipo UserManager (che può assegnare utenti a ruoli o annullare l'assegnazione).

Se si esegue l'autenticazione con token di connessione JWT, il middleware di autenticazione del bearer token JWT di ASP.NET Core popolerà i ruoli di un utente in base alle attestazioni di ruolo trovate nel token. Per limitare l'accesso a un'azione o un controller MVC agli utenti con ruoli specifici, è possibile includere un parametro Roles nell'intestazione Authorize, come illustrato nell'esempio seguente:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

In questo esempio, solo gli utenti con i ruoli Administrator o PowerUser possono accedere alle API nel controller ControlPanel (ad esempio, l'esecuzione dell'azione SetTime). L'API ShutDown è ulteriormente limitata in modo da consentire l'accesso solo agli utenti con il ruolo Administrator.

Per richiedere l'appartenenza di un utente a più ruoli, è possibile usare più attributi Authorize, come illustrato nell'esempio seguente:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

In questo esempio, per chiamare API1, un utente deve:

-   Appartenere al ruolo Adminstrator *o* PowerUser *e*

-   Appartenere al ruolo RemoteEmployee *e*

-   Soddisfare un gestore personalizzato per l'autorizzazione CustomPolicy.

## <a name="implementing-policy-based-authorization"></a>Implementazione dell'autorizzazione basata su criteri

È anche possibile scrivere regole di autorizzazione personalizzate usando i [criteri di autorizzazione](https://docs.asp.net/en/latest/security/authorization/policies.html). In questa sezione viene fornita una panoramica. Informazioni più dettagliate sono disponibili online nel [workshop sull'autorizzazione ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

I criteri di autorizzazione personalizzati vengono registrati nel metodo Startup.ConfigureServices mediante il metodo service.AddAuthorization. Questo metodo accetta un delegato che configura un argomento AuthorizationOptions.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Come illustrato nell'esempio, i criteri possono essere associati a diversi tipi di requisiti. Una volta registrati, i criteri possono essere applicati a un'azione o un controller passando il nome del criterio come argomento Policy dell'attributo Authorize (ad esempio, \[Authorize(Policy="EmployeesOnly")\]). I criteri possono avere più requisiti, non solo uno (come illustrato in questi esempi).

Nell'esempio precedente, la prima chiamata AddPolicy è un metodo alternativo per eseguire l'autorizzazione in base al ruolo. Se viene applicato \[Authorize(Policy="AdministratorsOnly")\] a un'API, solo gli utenti con il ruolo Administrator saranno in grado di accedervi.

La seconda chiamata AddPolicy illustra un modo semplice per richiedere la presenza di una determinata attestazione per l'utente. Facoltativamente, il metodo RequireClaim accetta anche i valori previsti per l'attestazione. Se si specificano i valori, il requisito viene soddisfatto solo se l'utente dispone di un'attestazione di tipo corretto e di uno dei valori specificati. Se si usa il middleware di autenticazione del bearer token JWT, tutte le proprietà JWT saranno disponibili come attestazioni utente.

I criterio più interessante illustrato di seguito è nel terzo metodo AddPolicy, perché usa un requisito di autorizzazione personalizzato. Con i requisiti di autorizzazione personalizzati, è possibile avere un notevole controllo sulla modalità di esecuzione dell'autorizzazione. Per garantirne il funzionamento, è necessario implementare questi tipi:

-   Un tipo Requirements che deriva da IAuthorizationRequirement e che contiene campi che specificano i dettagli del requisito. Nell'esempio, si tratta di un campo age per il tipo MinimumAgeRequirement di esempio.

-   Un gestore che implementa AuthorizationHandler&lt;T&gt;, dove T è il tipo di IAuthorizationRequirement che il gestore in grado di soddisfare. Il gestore deve implementare il metodo HandleRequirementAsync, che verifica se un contesto specificato che contiene informazioni sull'utente soddisfa il requisito.

Se l'utente soddisfa il requisito, una chiamata a context.Succeed indicherà che l'utente è autorizzato. Se esistono diversi modi in cui un utente potrebbe soddisfare un requisito di autorizzazione, è possibile creare più gestori.

Oltre a registrare i requisiti dei criteri personalizzati con le chiamate AddPolicy, è inoltre necessario registrare i gestori dei requisiti personalizzati tramite l'inserimento di dipendenze (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Un esempio di un requisito di autorizzazione personalizzato e un gestore per la verifica dell'età di un utente (in base a un'attestazione DateOfBirth) è disponibile nella[documentazione sull'autorizzazione](https://docs.asp.net/en/latest/security/authorization/policies.html) di ASP.NET Core.

## <a name="additional-resources"></a>Risorse aggiuntive

-   **Autenticazione di ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autorizzazione di ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorizzazione basata sui ruoli**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autorizzazione personalizzata basata su criteri**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Indietro] (index.md) [Avanti] (developer-app-secrets-storage.md)
