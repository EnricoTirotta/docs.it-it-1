---
title: Stringhe interpolate (C#)
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a>Stringhe interpolate (Riferimento per C#)

Vengono usate per la costruzione di stringhe.  Una stringa interpolata è simile a una stringa di modello che contiene *espressioni interpolate*.  Una stringa interpolata restituisce una stringa che sostituisce le espressioni interpolate in essa contenute con le rappresentazioni di stringa. Questa funzionalità è disponibile in C# 6 e versioni successive.

Gli argomenti di una stringa interpolata sono più facili da comprendere rispetto a una [stringa di formato composito](../../../standard/base-types/composite-formatting.md#composite-format-string).  Ad esempio, la stringa interpolata  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
contiene due espressioni interpolate, '{name}' e '{hours: hh}'. La stringa di formato composito equivalente è:

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

La struttura di una stringa interpolata è:  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

dove: 

- *field-width* è un intero con segno che indica il numero di caratteri nel campo. Se è positivo, il campo viene allineato a destra; se è negativo, viene allineato a sinistra. 

- *format-string* è una stringa di formato appropriata per il tipo di oggetto formattato. Ad esempio, per un valore <xref:System.DateTime>, potrebbe essere una stringa di formato data e ora standard come "D" o "d".

> [!IMPORTANT]
> Tra `$` e il simbolo `"` all'inizio della stringa non possono essere presenti spazi vuoti, altrimenti si genera un errore in fase di compilazione.

 È possibile usare una stringa interpolata ovunque sia possibile usare un valore letterale stringa.  La stringa interpolata viene valutata ogni volta che si esegue codice con la stringa interpolata. Ciò consente di separare la definizione e la valutazione di una stringa interpolata.  
  
 Per includere una parentesi graffa ("{" o "}") in una stringa interpolata, digitarne due, ovvero "{{" o "}}".  Per altri dettagli, vedere la sezione Conversioni implicite.  

Se la stringa interpolata contiene altri caratteri con un significato speciale in una stringa interpolata, ad esempio virgolette doppie ("), due punti (:) o virgola (,), è necessario specificare il carattere di escape se si presentano nel testo letterale, oppure inserirli in un'espressione racchiusa tra parentesi se sono elementi del linguaggio inclusi in un'espressione interpolata. Nell'esempio seguente viene specificato il carattere di escape delle virgolette per includerle nella stringa di risultato e si usano le parentesi per delimitare l'espressione `(age == 1 ? "" : "s")` in modo che i due punti non vengano interpretati come l'inizio di una stringa di formato.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

Le stringe interpolate verbatim usano il carattere `$` seguito dal carattere `@`. Per altre informazioni sulle stringhe verbatim, vedere l'argomento relativo a [string](string.md). Il codice seguente è una versione modificata del frammento di codice precedente che usa una stringa interpolata verbatim:

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

È necessario modificare la formattazione perché le stringhe verbatim non rispettano le sequenze di escape `\`.

> [!IMPORTANT]
> Il token `$` deve precedere il token `@` in una stringa interpolata verbatim.


## <a name="implicit-conversions"></a>Conversioni implicite  

Da una stringa interpolata vengono effettuate tre conversioni di tipo implicito:  

1. Conversione di una stringa interpolata in una <xref:System.String>. L'esempio seguente restituisce una stringa in cui le espressioni di stringa interpolata sono state sostituite con le rappresentazioni di stringa. Ad esempio:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Questo è il risultato finale di un'interpretazione della stringa. Tutte le occorrenze delle parentesi graffe doppie ("{{" e "}}") vengono convertite in parentesi graffe singole. 

2. Conversione di una stringa interpolata in una variabile <xref:System.IFormattable> che consente di creare più stringhe risultato con contenuto specifico delle impostazioni cultura da una singola istanza di <xref:System.IFormattable>. Ciò è utile per includere elementi quali i formati numerici e di data corretti per singole impostazioni cultura.  Tutte le occorrenze di parentesi graffe doppie ("{{" e "}}") rimangono tali finché la stringa non viene formattata in modo implicito o esplicito chiamando il metodo <xref:System.Object.ToString>.  Tutte le espressioni di interpolazione contenute vengono convertite in {0}, \{1\} e così via.  

   Nell'esempio seguente viene usata la reflection per visualizzare i membri, nonché i valori di campi e le proprietà di una variabile <xref:System.IFormattable> creata da una stringa interpolata. Viene anche passata la variabile <xref:System.IFormattable> al metodo <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Si noti che la stringa interpolata può essere controllata solo tramite reflection. Se viene passata a un metodo di formattazione delle stringhe, ad esempio <xref:System.Console.WriteLine(System.String)>, gli elementi di formato vengono risolti e viene restituita la stringa risultato. 

3. Conversione di una stringa interpolata in una variabile <xref:System.FormattableString> che rappresenta una stringa di formato composito. Grazie all'esame della stringa di formato composito e del modo in cui viene eseguito il rendering come stringa di risultato, è ad esempio possibile attuare misure di protezione contro attacchi di tipo injection durante la creazione di una query. <xref:System.FormattableString> include anche overload <xref:System.FormattableString.ToString> che consentono di generare stringhe di risultato per <xref:System.Globalization.CultureInfo.InvariantCulture> e <xref:System.Globalization.CultureInfo.CurrentCulture>.  Tutte le occorrenze delle parentesi graffe doppie ("{{" e "}}") rimangono invariate finché non si applica la formattazione.  Tutte le espressioni di interpolazione contenute vengono convertite in {0}, \{1\} e così via.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Specifiche del linguaggio  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Riferimenti per C#](../../../csharp/language-reference/index.md)  
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)
