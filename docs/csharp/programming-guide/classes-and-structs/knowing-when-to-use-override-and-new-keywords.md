---
title: "Sapere quando utilizzare le parole chiave Override e New (Guida per programmatori C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "new (parola chiave) [C#]"
  - "override (parola chiave) [F#]"
  - "polimorfismo [C#], utilizzo di override e new [C#]"
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Sapere quando utilizzare le parole chiave Override e New (Guida per programmatori C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Nel linguaggio C\#, un metodo in una classe derivata può avere lo stesso nome di un metodo in una classe base.  È possibile specificare in che modo avviene l'interazione dei metodi utilizzando le parole chiave [new](../../../csharp/language-reference/keywords/new.md) e [override](../../../csharp/language-reference/keywords/override.md).  Il modificatore `override` *estende* il metodo della classe di base e il modificatore `new` lo *nasconde*.  La differenza è illustrata negli esempi riportati in questo argomento.  
  
 In un'applicazione console, dichiarare le seguenti due classi, `BaseClass` e `DerivedClass`.  `DerivedClass` eredita da `BaseClass`.  
  
```c#  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
  
```  
  
 Nel metodo `Main`, dichiarare le variabili `bc`, `dc` e `bcdc`.  
  
-   `bc` è di tipo `BaseClass` e il suo valore è di tipo `BaseClass`.  
  
-   `dc` è di tipo `DerivedClass` e il suo valore è di tipo `DerivedClass`.  
  
-   `bcdc` è di tipo `BaseClass` e il suo valore è di tipo `DerivedClass`.  Si tratta della variabile a cui prestare attenzione.  
  
 Poiché `bc` e `bcdc` dispongono del tipo `BaseClass`, possono solo accedere direttamente a `Method1`, a meno che non venga utilizzato il cast.  Attraverso la variabile `dc` è possibile accedere sia a `Method1` che a `Method2`.  Nel codice riportato di seguito vengono illustrati le diverse relazioni.  
  
```c#  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
  
```  
  
 Quindi aggiungere il metodo `Method2` seguente a `BaseClass` La firma di questo metodo corrisponde alla firma del metodo `Method2` in `DerivedClass`.  
  
```c#  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
  
```  
  
 Poiché `BaseClass` dispone di un metodo `Method2`, è possibile aggiungere una seconda istruzione di chiamata per le variabili `BaseClass`, `bc` e `bcdc`, come mostrato nel seguente codice.  
  
```c#  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
  
```  
  
 Quando si compila il progetto, l'aggiunta del metodo `Method2` in `BaseClass` genera un avviso.  L'avviso indica che il metodo `Method2` in `DerivedClass` nasconde il metodo `Method2` in `BaseClass`.  Si consiglia di utilizzare la parola chiave `new` nella definizione di `Method2` se si desidera ottenere tale risultato.  In alternativa, è possibile rinominare uno dei metodi `Method2` per risolvere il problema, ma ciò non è sempre pratico.  
  
 Prima di aggiungere `new`, eseguire il programma per verificare l'output prodotto da altre istruzioni di chiamata.  Vengono visualizzati i risultati seguenti.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
  
```  
  
 La parola chiave `new` conserva le relazioni che producono l'output, ma elimina l'avviso.  Le variabili di tipo `BaseClass` continuano ad accedere ai membri di `BaseClass`, mentre la variabile di tipo `DerivedClass` continua ad accedere prima ai membri in `DerivedClass` e in seguito prende in considerazione i membri ereditati da `BaseClass`.  
  
 Per eliminare l'avviso, aggiungere il modificatore `new` alla definizione di `Method2` in `DerivedClass`, come illustrato nel codice seguente.  Il modificatore può essere aggiunto prima o dopo l'oggetto `public`.  
  
```c#  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
  
```  
  
 Eseguire nuovamente il programma per verificare che l'output non sia stato modificato.  Verificare inoltre che l'avviso non venga visualizzato.  Utilizzando `new`, si afferma di essere informati che il membro di cui si sta eseguendo la modifica nasconde un membro ereditato dalla classe di base.  Per ulteriori informazioni su come viene nascosto un nome tramite ereditarietà, vedere [Modificatore new](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Per contrastare questo comportamento agli effetti dell'utilizzo di `override`, aggiungere il seguente metodo a `DerivedClass`.  Il modificatore `override` può essere aggiunto prima o dopo `public`.  
  
```c#  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
  
```  
  
 Aggiungere il modificatore `virtual` alla definizione di `Method1` in `BaseClass`.  Il modificatore `virtual` può essere aggiunto prima o dopo `public`.  
  
```c#  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
  
```  
  
 Ripetere l'esecuzione del progetto.  Si noti soprattutto le ultime due linee dell'output riportato di seguito.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
  
```  
  
 L'utilizzo del modificatore `override` consente a `bcdc` di accedere al metodo `Method1` definito in `DerivedClass`.  In genere si tratta del comportamento previsto nelle gerarchie di ereditarietà.  Si desidera che gli oggetti dotati di valori creati dalla classe derivata utilizzino i metodi definiti nella classe derivata.  Si ottiene questo comportamento utilizzando `override` per estendere il metodo della classe base.  
  
 Il codice seguente include l'esempio completo.  
  
```c#  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
  
```  
  
 Nell'esempio riportato di seguito viene illustrato un comportamento simile in un contesto diverso.  L'esempio definisce tre classi: una classe di base denominata `Car` e due classi derivate da essa, `ConvertibleCar` e `Minivan`.  La classe di base contiene un metodo `DescribeCar`.  Il metodo visualizza una descrizione di base di un'automobile, quindi chiama l'oggetto `ShowDetails` per fornire informazioni aggiuntive.  Ciascuna delle tre classi definisce un metodo `ShowDetails`.  Il modificatore `new` viene utilizzato per definire `ShowDetails` nella classe `ConvertibleCar`.  Il modificatore `override` viene utilizzato per definire `ShowDetails` nella classe `Minivan`.  
  
```c#  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
  
```  
  
 L'esempio verifica che la versione di `ShowDetails` venga chiamata.  Il metodo seguente, `TestCars1`, dichiara un'istanza di ciascuna classe, quindi chiama `DescribeCar` su ciascuna istanza.  
  
```c#  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
  
```  
  
 `TestCars1` produce il seguente output.  Si noti particolarmente i risultati per `car2`, che probabilmente non è quello previsto.  Il tipo dell'oggetto è `ConvertibleCar`, ma `DescribeCar` non accede alla versione di `ShowDetails` definita nella classe `ConvertibleCar` perché tale metodo è dichiarato con il modificatore `new`, non con il modificatore `override`.  Di conseguenza, un oggetto `ConvertibleCar` visualizza la stessa descrizione dell'oggetto `Car`.  Contrapporre i risultati per `car3`, che è un oggetto `Minivan`.  In questo caso, il metodo `ShowDetails` che viene dichiarato nella classe `Minivan` esegue l'override del metodo `ShowDetails` che viene dichiarato nella classe `Car` e la descrizione visualizzata descrive un furgoncino.  
  
```c#  
  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars2` determina la creazione di oggetti con tipo `Car`.  Le istanze dei valori degli oggetti vengono create dalle classi `Car`, `ConvertibleCar` e `Minivan`.  `DescribeCar` viene chiamato su ogni elemento dell'elenco.  Nel codice riportato di seguito viene illustrata la definizione di `TestCars2`.  
  
```c#  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
  
```  
  
 Verrà visualizzato il seguente output.  Si noti che equivale all'output visualizzato da `TestCars1`.  Il metodo `ShowDetails` della classe `ConvertibleCar` non viene chiamato, indipendentemente dal fatto che il tipo di oggetto sia `ConvertibleCar`, come in `TestCars1` oppure `Car`, come in `TestCars2`.  Al contrario, `car3` chiama il metodo `ShowDetails` della classe `Minivan` in entrambi i casi, sia se dispone del tipo `Minivan` o del tipo `Car`.  
  
```c#  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 I metodi `TestCars3` e `TestCars4` completano l'esempio.  Questi metodi chiamano direttamente `ShowDetails`, prima da oggetti dichiarati con tipo `ConvertibleCar` e `Minivan` \(`TestCars3`\), poi da oggetti dichiarati con tipo `Car` \(`TestCars4`\).  Il codice seguente definisce i due metodi .  
  
```c#  
  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
```  
  
 I metodi producono l'output seguente, che corrisponde ai risultati del primo esempio di questo argomento.  
  
```c#  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
  
```  
  
 Nel codice seguente viene illustrato il progetto completo e il relativo output.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
  
```  
  
## Vedere anche  
 [Guida per programmatori C\#](../../../csharp/programming-guide/index.md)   
 [Classi e struct](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Controllo delle versioni con le parole chiave Override e New](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)