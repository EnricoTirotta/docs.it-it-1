---
title: 'Procedura: raggruppare controlli RadioButton Windows Form in modo che funzionino come set'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Procedura: raggruppare controlli RadioButton Windows Form in modo che funzionino come set
Windows Form <xref:System.Windows.Forms.RadioButton> i controlli sono progettati per consentire agli utenti una scelta tra due o più impostazioni di cui solo uno può essere assegnato a una routine o un oggetto. Ad esempio, un gruppo di <xref:System.Windows.Forms.RadioButton> controlli che visualizzano dei vettori di pacchetto per un ordine, ma solo uno dei vettori verrà utilizzato. Pertanto un solo <xref:System.Windows.Forms.RadioButton> alla volta può essere selezionato, anche se fa parte di un gruppo funzionale.  
  
 Gruppo di pulsanti di opzione trascinandoli all'interno di un contenitore, ad esempio un <xref:System.Windows.Forms.Panel> (controllo), un <xref:System.Windows.Forms.GroupBox> controllo o un form. Tutti i pulsanti di opzione che vengono aggiunti direttamente a un form costituiscono un gruppo. Per aggiungere gruppi separati, è necessario inserirli all'interno di pannelli o caselle di gruppo. Per ulteriori informazioni su pannelli o caselle di gruppo, vedere [Cenni preliminari sul controllo Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) o [Cenni preliminari sul controllo GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Per raggruppare controlli RadioButton come impostato in modo indipendente da altri set (funzione)  
  
1.  Trascinare un <xref:System.Windows.Forms.GroupBox> o <xref:System.Windows.Forms.Panel> controllo il **Windows Form** scheda la **della casella degli strumenti** nel form.  
  
2.  Disegnare <xref:System.Windows.Forms.RadioButton> ai controlli di <xref:System.Windows.Forms.GroupBox> o <xref:System.Windows.Forms.Panel> controllo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.RadioButton>  
 [Panoramica sul controllo RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [Panoramica sul controllo Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Panoramica sul controllo GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Panoramica sul controllo CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Controllo RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
