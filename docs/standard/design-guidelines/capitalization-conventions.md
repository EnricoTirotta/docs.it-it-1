---
title: Convenzioni per l'utilizzo di maiuscole e minuscole
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b36f230c9a5f8653f3e252d26fe6464bb9cac4bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="capitalization-conventions"></a>Convenzioni per l'utilizzo di maiuscole e minuscole
Le linee guida fornite in questo capitolo impostano un metodo semplice per l'utilizzo di maiuscolo e minuscono che, quando applicato in modo coerente, rende di facile lettura gli identificatori per i tipi, membri, e parametri.  
  
## <a name="capitalization-rules-for-identifiers"></a>Regole per gli identificatori  
 Per differenziare le parole in un identificatore, convertire in maiuscolo la prima lettera di ogni parola nell'identificatore. Non utilizzare caratteri di sottolineatura per differenziare le parole o a tale scopo, in qualsiasi punto negli identificatori. Esistono due modi appropriati in maiuscolo gli identificatori, a seconda dell'utilizzo dell'identificatore:  
  
-   Pascal
  
-   camel
  
 La convenzione PascalCasing, utilizzata per tutti gli identificatori, ad eccezione dei nomi di parametro, converte in maiuscolo il primo carattere di ogni parola (inclusi gli acronimi su due lettere), come illustrato negli esempi seguenti:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Un caso speciale viene effettuato per gli acronimi con due lettere in cui entrambe le lettere sono in maiuscolo, come illustrato nel seguente identificatore:  
  
 `IOStream`  
  
 La convenzione camelCasing, utilizzata solo per i nomi di parametro, converte in maiuscolo il primo carattere di ogni parola eccetto la prima parola, come illustrato negli esempi seguenti. Come viene inoltre mostrato nell'esempio, gli acronimi di due lettere che iniziano un identificatore con convenzione camel sono entrambe minuscole.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ SI** utilizzare la convenzione Pascal per tutti i membri, tipo e spazio dei nomi pubblici composta da più parole.  
  
 **✓ SI** utilizzare camel per i nomi di parametro.  
  
 Nella tabella seguente descrive le regole di utilizzo delle maiuscole per diversi tipi di identificatori.  
  
|Identificatore|Maiuscole e minuscole|Esempio|  
|----------------|------------|-------------|  
|Spazio dei nomi|Convenzione Pascal|`namespace System.Security { ... }`|  
|Tipo|Convenzione Pascal|`public class StreamReader { ... }`|  
|Interfaccia|Convenzione Pascal|`public interface IEnumerable { ... }`|  
|Metodo|Convenzione Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Proprietà|Convenzione Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|event|Convenzione Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Campo|Convenzione Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Valore enum|Convenzione Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametro|Convenzione camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Le parole composte con iniziale maiuscole e termini comuni  
 La maggior parte dei termini composti vengono considerati come singole parole per scopi di lettere maiuscole/minuscole.  
  
 **X non** tutte iniziali maiuscole nella cosiddette parole composte di forma chiusa.  
  
 Queste sono le parole composte scritte come una parola singola, ad esempio endpoint. Allo scopo di linee guida di maiuscole e minuscole, considerare una parola composta di forma chiusa come una singola parola. Utilizzare il dizionario corrente per determinare se una parola composta è scritta in forma chiusa.  
  
|Convenzione Pascal|Convenzione camel|non|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>Distinzione fra maiuscole e minuscole  
 Ai linguaggi che possono essere eseguiti sul CLR Common Language Runtime non è richiesto di supportare la distinzione maiuscole/minuscole, anche se alcuni lo fanno. Anche se il linguaggio lo supporta, altri linguaggi che potrebbero accedere il framework, potrebbero non supportarlo. Le API che sono accessibili dall'esterno, pertanto, non possono basarsi solo su maiuscole e minuscole per distinguere tra due nomi nello stesso contesto.  
  
 **X non** presupporre che tutti i linguaggi di programmazione facciano distizione tra maiuscole e minuscole. Non lo fanno. I nomi non possono differire solo in maiuscole e minuscole.  
  
 *Parti © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *State ristampate dall'autorizzazione di Pearson Education, Inc. da [linee guida: convenzioni, idiomi e modelli per le librerie .NET di riutilizzabile, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina e Brad Abrams, pubblicato il 22 ottobre 2008 di Addison-Wesley Professional come parte della serie di sviluppo di Microsoft Windows.*  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)  
 [Convenzioni di denominazione](../../../docs/standard/design-guidelines/naming-guidelines.md)
