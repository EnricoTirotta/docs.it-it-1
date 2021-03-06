---
title: "Utilizzo dell'attività Switch con tipi personalizzati"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61485a59ae3af17bef58c0fccbe062c8b9171a34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Utilizzo dell'attività Switch con tipi personalizzati
In questo esempio viene descritto come consentire a un'attività <xref:System.Activities.Statements.Switch%601> di valutare un tipo complesso definito dall'utente in fase di esecuzione. Nei linguaggi di programmazione procedurali più tradizionali, un [passare](http://go.microsoft.com/fwlink/?LinkId=180521) istruzione seleziona una logica di esecuzione in base alla valutazione condizionale di una variabile. Tradizionalmente, un'istruzione `switch` agisce su un'espressione che può essere valutata staticamente. Ad esempio, in C# ciò significa che sono supportati solo tipi primitivi, quali <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, e tipi di enumerazione.  
  
 Per abilitare il passaggio in una classe personalizzata, è necessario implementare la logica per valutare valori di tipo complesso personalizzato in fase di esecuzione. In questo esempio viene illustrato come abilitare il passaggio su un tipo complesso personalizzato denominato `Person`.  
  
-   Nella classe personalizzata `Person` un attributo <xref:System.ComponentModel.TypeConverter> viene dichiarato con il nome dell'oggetto <xref:System.ComponentModel.TypeConverter> personalizzato.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Nella classe personalizzata `Person` viene eseguito l'override delle classi <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A>.  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   Viene implementata una classe personalizzata <xref:System.ComponentModel.TypeConverter> che esegue la conversione di un'istanza della classe personalizzata in una stringa e una stringa in un'istanza di una classe personalizzata.  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 In questo esempio sono inclusi i file seguenti:  
  
-   **Person**: definisce la `Person` classe.  
  
-   **Personconverter**: il convertitore di tipi per la `Person` classe.  
  
-   **Sequence**: un flusso di lavoro che passa il `Person` tipo.  
  
-   **Program.cs**: la funzione principale che esegue il flusso di lavoro.  
  
#### <a name="to-use-this-sample"></a>Per usare questo esempio  
  
1.  Caricare Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Per compilare la soluzione, premere CTRL+MAIUSC+B.  
  
3.  Premere CTRL + F5 per eseguire l'esempio.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare alla sezione relativa agli [esempi di Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) per .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti gli esempi di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Vedere anche  
 [Libreria di attività incorporata](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
