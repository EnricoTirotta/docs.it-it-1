---
title: "Tipi di enumerazione (Guida per programmatori C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "flag di bit [C#]"
  - "Linguaggio C#, enum"
  - "enumerazioni [C#]"
  - "enum [C#]"
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipi di enumerazione (Guida per programmatori C#)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Un tipo di enumerazione \(anche denominato enumerazione o enum\) offre un modo efficiente per definire un insieme di costanti integrali denominate che possono essere assegnate a una variabile.  Si presupponga ad esempio di dover definire una variabile il cui valore rappresenterà un giorno della settimana.  Ci sono solo sette valori significativi che la variabile potrà mai archiviare.  Per definire tali valori, è possibile utilizzare un tipo di enumerazione, dichiarato tramite la parola chiave [enum](../../csharp/language-reference/keywords/enum.md).  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 Per impostazione predefinita, il tipo sottostante di ogni elemento dell'enumerazione è [int](../../csharp/language-reference/keywords/int.md).  È possibile specificare un altro tipo numerico integrale utilizzando i due punti, come mostrato nell'esempio precedente.  Per un elenco completo dei tipi possibili, vedere [enum \(Riferimenti per C\#\)](../../csharp/language-reference/keywords/enum.md).  
  
 È possibile verificare i valori numerici sottostanti eseguendo il cast al tipo sottostante, come illustrato di seguito.  
  
```c#  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 I seguenti sono i vantaggi dell'utilizzo di un enum invece di un tipo numerico:  
  
-   Si specifica in modo chiaro per il codice client quali sono i valori validi per la variabile.  
  
-   In [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)], IntelliSense elenca i valori definiti.  
  
 Quando non si specificano valori per gli elementi nell'elenco di enumeratori, i valori vengono incrementati automaticamente di 1.  Nell'esempio precedente, `Days.Sunday` ha un valore 0, `Days.Monday` ha un valore 1 e così via.  Quando si crea un nuovo oggetto `Days`, questo avrà un valore predefinito di `Days.Sunday` \(0\) se non si assegna un valore in modo esplicito.  Quando si crea un enum, selezionare il valore predefinito più logico e assegnarvi un valore di zero.  In tal modo tutti gli enum avranno quel valore predefinito se non è stato loro assegnato un valore in modo esplicito al momento della creazione.  
  
 Se la variabile `meetingDay` è di tipo `Days`, è possibile assegnare \(senza un cast esplicito\) solo uno dei valori definiti da `Days`.  E se il giorno della riunione cambia, è possibile assegnare un nuovo valore da `Days` a `meetingDay`:  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  È possibile assegnare qualsiasi valore intero arbitrario a `meetingDay`.  Ad esempio, questa riga di codice non produce un errore: `meetingDay = (Days) 42`.  Tuttavia, questa impostazione non è consigliabile perché l'aspettativa implicita è che una variabile enum contenga solo uno dei valori definiti dal tipo enum.  L'assegnazione di un valore arbitrario a una variabile di un tipo di enumerazione introduce un rischio elevato di errori.  
  
 È possibile assegnare qualsiasi valore agli elementi nell'elenco di enumeratori di un tipo di enumerazione ed è inoltre possibile utilizzare valori calcolati:  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## Tipi di enumerazione come flag di bit  
 È possibile utilizzare un tipo di enumerazione per definire flag di bit, che consentono a un'istanza del tipo di enumerazione di archiviare qualsiasi combinazione dei valori definiti nell'elenco di enumeratori  \(chiaramente, alcune combinazioni potrebbero non essere significative o consentite nel codice del programma\).  
  
 Un enum di flag di bit viene creato applicando l'attributo <xref:System.FlagsAttribute?displayProperty=fullName> e definendo in modo appropriato i valori in modo che sia possibile eseguirvi operazioni bit per bit `AND`, `OR`, `NOT` e `XOR`.  In un enum di flag di bit, includere una costante denominata con un valore di zero che indica che non sono impostati flag. Non fornire a un flag un valore di zero se non per indicare che non sono impostati flag.  
  
 Nell'esempio seguente, viene definita un'altra versione dell'enum `Days`, denominato `Days2`.  `Days2` dispone dell'attributo `Flags` e a ogni valore viene assegnata la successiva maggiore potenza di 2.  In questo modo è possibile creare una variabile `Days2` il cui valore è `Days2.Tuesday` e `Days2.Thursday`.  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 Per impostare un flag su un enum, utilizzare l'operatore `OR` bit per bit come mostrato nell'esempio seguente:  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 Per determinare se un flag specifico è impostato, utilizzare l'operatore `AND` bit per bit come mostrato nell'esempio seguente:  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 Per ulteriori informazioni sugli aspetti da considerare quando si definiscono tipi di enumerazione con l'attributo <xref:System.FlagsAttribute?displayProperty=fullName>, vedere <xref:System.Enum?displayProperty=fullName>.  
  
## Utilizzo dei metodi System.Enum per individuare e modificare valori enum  
 Tutti gli enum sono istanze del tipo <xref:System.Enum?displayProperty=fullName>.  Non è possibile derivare nuove classi da <xref:System.Enum?displayProperty=fullName>, ma è possibile utilizzarne i metodi per individuare informazioni e modificare valori in un'istanza dell'enum.  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 Per ulteriori informazioni, vedere la classe <xref:System.Enum?displayProperty=fullName>.  
  
 È inoltre possibile creare un nuovo metodo per un enum tramite un metodo di estensione.  Per ulteriori informazioni, vedere [Procedura: creare un nuovo metodo per un'enumerazione](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).  
  
## Capitoli del libro rappresentati  
 [Ulteriori informazioni sulle variabili](http://go.microsoft.com/fwlink/?LinkId=221230) in [Visual c 2010 iniziale](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Vedere anche  
 <xref:System.Enum?displayProperty=fullName>   
 [Guida per programmatori C\#](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)