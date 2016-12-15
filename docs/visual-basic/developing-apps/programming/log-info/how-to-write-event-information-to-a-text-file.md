---
title: "How to: Write Event Information to a Text File (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "event logs [Visual Studio], writing event information"
  - "text files, writing event information to a text file"
  - "events [Visual Basic], writing event information to a text file"
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Event Information to a Text File (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

È possibile utilizzare gli oggetti `My.Application.Log` e `My.Log` per registrare informazioni sugli eventi che si verificano nell'applicazione.  Nell'esempio riportato di seguito è illustrato l'utilizzo del metodo `My.Application.Log.WriteEntry` per registrare le informazioni di tracciatura in un file di log.  
  
### Per aggiungere e configurare il listener di log del file  
  
1.  Fare clic con il pulsante destro del mouse sul file app.config in **Esplora soluzioni**, quindi scegliere **Apri**.  
  
     \- oppure \-  
  
     Se non è presente alcun file app.config:  
  
    1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
    2.  Nella finestra di dialogo **Aggiungi nuovo elemento**, selezionare **File di configurazione dell'applicazione**.  
  
    3.  Scegliere **Aggiungi**.  
  
2.  Individuare la sezione `<listeners>` nel file di configurazione dell'applicazione.  
  
     La sezione \<listeners\> si trova nella sezione \<source\> con l'attributo del nome "DefaultSource", annidato sotto la sezione \<system.diagnostics\>, a sua volta annidata sotto la sezione \<configuration\> di primo livello.  
  
3.  Aggiungere l'elemento alla sezione `<listeners>`:  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  Individuare la sezione `<sharedListeners>` nella sezione `<system.diagnostics>`, annidata sotto la sezione `<configuration>` di primo livello.  
  
5.  Aggiungere l'elemento alla sezione `<sharedListeners>`:  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Modificare il valore dell'attributo `customlocation` sulla directory di log.  
  
    > [!NOTE]
    >  Per impostare il valore di una proprietà del listener, utilizzare un attributo con lo stesso nome della proprietà e tutte le lettere nel nome scritte in minuscolo.  Ad esempio, gli attributi `location` e `customlocation` consentono di impostare i valori delle proprietà <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> e <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### Per scrivere informazioni sugli eventi nel registro file  
  
-   Utilizzare il metodo `My.Application.Log.WriteEntry` oppure `My.Application.Log.WriteException` per scrivere le informazioni nel registro file.  Per ulteriori informazioni, vedere [Procedura: scrivere messaggi di log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Dopo aver configurato il listener del registro file per un assembly, vengono ricevuti tutti i messaggi che `My.Application.Log` scrive da tale assembly.  
  
## Vedere anche  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Utilizzo dei log applicazione](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)