---
title: 'Procedura: esplorare i dati con il controllo BindingNavigator Windows Form'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Procedura: esplorare i dati con il controllo BindingNavigator Windows Form
L'introduzione del controllo <xref:System.Windows.Forms.BindingNavigator> in Windows Form consente agli sviluppatori di fornire agli utenti finali un'interfaccia utente di navigazione e modifica di dati semplice nei form che creano.  
  
 <xref:System.Windows.Forms.BindingNavigator> è un controllo <xref:System.Windows.Forms.ToolStrip> con pulsanti preconfigurati per la navigazione al primo, ultimo, successivo e precedente record in un set di dati e fornisce anche i pulsanti per aggiungere ed eliminare i record. L'aggiunta di pulsanti al controllo <xref:System.Windows.Forms.BindingNavigator> è facile perché si tratta di un controllo <xref:System.Windows.Forms.ToolStrip>.  Vedere anche [Procedura: Aggiungere i pulsanti Carica, Salva e Annulla al controllo BindingNavigator Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Per ogni pulsante del controllo <xref:System.Windows.Forms.BindingNavigator> esiste un membro corrispondente del componente <xref:System.Windows.Forms.BindingSource> che fornisce consente la stessa funzionalità a livello di codice. Il pulsante <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>, ad esempio, corrisponde al metodo <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> del componente <xref:System.Windows.Forms.BindingSource>, il pulsante <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> corrisponde al metodo <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> e così via. Di conseguenza, l'abilitazione del controllo <xref:System.Windows.Forms.BindingNavigator> per navigare tra i record di dati risulta facile quanto impostare la proprietà <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> nel componente <xref:System.Windows.Forms.BindingSource> appropriato del form.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Per configurare il controllo BindingNavigator  
  
1.  Aggiungere un componente <xref:System.Windows.Forms.BindingSource> denominato `bindingSource1` e due controlli <xref:System.Windows.Forms.TextBox> denominati `textBox1` e `textBox2`.  
  
2.  Associare `bindingSource1` ai dati e i controlli textbox a `bindingSource1`. A tale scopo, incollare il codice seguente nel form e chiamare `LoadData` dal costruttore del form o dal metodo di gestione eventi <xref:System.Windows.Forms.Form.Load>.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Aggiungere un controllo <xref:System.Windows.Forms.BindingNavigator> denominato `bindingNavigator1` al form.  
  
4.  Impostare la proprietà <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> per `bindingNavigator1` su `bindingSource1`. È possibile farlo con la finestra di progettazione o nel codice.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente è l'esempio completo dei passaggi elencati in precedenza.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Riferimenti agli assembly System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
 Per informazioni sulla compilazione di questo esempio dalla riga di comando per [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vedere [Compilazione dalla riga di comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Compilazione dalla riga di comando con csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). È anche possibile compilare questo esempio in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] incollando il codice in un nuovo progetto.  Vedere anche [Procedura: Compilare ed eseguire un esempio di codice Windows Form completo con Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Controllo BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Controllo ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
