---
title: Avviso del compilatore CS3024
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ffaf8a8b5c52e793e08ab467621c42ec47b1a29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-warning-cs3024"></a>Avviso del compilatore CS3024
Il tipo di vincolo 'type' non è conforme a CLS.  
  
 Il compilatore genera questo avviso perché l'uso di un tipo non conforme a CLS come vincolo di tipo generico potrebbe impedire al codice scritto in alcuni linguaggi di usare la classe generica.  
  
### <a name="to-eliminate-this-warning"></a>Per eliminare l'avviso  
  
1.  Usare un tipo conforme a CLS per il vincolo di tipo.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente genera l'errore CS3024 in diverse posizioni:  
  
```  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Vincoli sui parametri di tipo](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
