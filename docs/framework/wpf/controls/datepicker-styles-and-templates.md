---
title: DatePicker stili e modelli
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4683ebd66afb2d4ac5bfa615336787c4006b4335
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker-styles-and-templates"></a>DatePicker stili e modelli
In questo argomento vengono descritti gli stili e modelli per il <xref:System.Windows.Controls.DatePicker> controllo. È possibile modificare il valore predefinito <xref:System.Windows.Controls.ControlTemplate> per fornire al controllo un aspetto univoco. Per altre informazioni, vedere [Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Parti del controllo DatePicker  
 La tabella seguente elenca le parti denominate la <xref:System.Windows.Controls.DatePicker> controllo.  
  
|Parte|Tipo|Descrizione|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|La radice del controllo.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Il pulsante che apre e chiude il <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Casella di testo che consente di immettere una data.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|La finestra popup per il <xref:System.Windows.Controls.DatePicker> controllo.|  
  
## <a name="datepicker-states"></a>Stati del controllo DatePicker  
 Nella tabella seguente sono elencati gli stati visivi per la <xref:System.Windows.Controls.DatePicker> controllo.  
  
|Nome VisualState|Nome VisualStateGroup|Descrizione|  
|-|-|-|  
|Normale|CommonStates|Lo stato predefinito.|  
|Disabilitato|CommonStates|Il <xref:System.Windows.Controls.DatePicker> è disabilitato.|  
|Valido|ValidationStates|Il controllo Usa il <xref:System.Windows.Controls.Validation> classe e <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `false`.|  
|InvalidFocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo ha lo stato attivo.|  
|InvalidUnfocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo non è attivo.|  
  
## <a name="datepickertextbox-parts"></a>Parti di DatePickerTextBox  
 La tabella seguente elenca le parti denominate la <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controllo.  
  
|Parte|Tipo|Descrizione|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|L'elemento che contiene il testo iniziale di <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Un elemento visivo che può contenere un <xref:System.Windows.FrameworkElement>. Il testo del <xref:System.Windows.Controls.TextBox> viene visualizzato in questo elemento.|  
  
## <a name="datepickertextbox-states"></a>Stati di DatePickerTextBox  
 Nella tabella seguente sono elencati gli stati visivi per la <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controllo.  
  
|Nome VisualState|Nome VisualStateGroup|Descrizione|  
|-|-|-|  
|Normale|CommonStates|Lo stato predefinito.|  
|Disabilitato|CommonStates|Il <xref:System.Windows.Controls.Primitives.DatePickerTextBox> è disabilitato.|  
|MouseOver|CommonStates|Il puntatore del mouse è posizionato il <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|L'utente non è possibile modificare il testo di <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Con stato attivo|FocusStates|Il controllo ha lo stato attivo.|  
|Con stato non attivo|FocusStates|Il controllo non ha lo stato attivo.|  
|Limite massimo|WatermarkStates|Il controllo Visualizza il testo iniziale.  Il <xref:System.Windows.Controls.Primitives.DatePickerTextBox> si trova nello stato quando l'utente non è il testo immesso o selezionato una data.|  
|Unwatermarked|WatermarkStates|L'utente ha immesso il testo nel <xref:System.Windows.Controls.Primitives.DatePickerTextBox> o seleziona una data nel <xref:System.Windows.Controls.DatePicker>.|  
|Valido|ValidationStates|Il controllo Usa il <xref:System.Windows.Controls.Validation> classe e <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `false`.|  
|InvalidFocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo ha lo stato attivo.|  
|InvalidUnfocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo non è attivo.|  
  
## <a name="datepicker-controltemplate-example"></a>Esempio di ControlTemplate DatePicker  
 Nell'esempio seguente viene illustrato come definire un <xref:System.Windows.Controls.ControlTemplate> per il <xref:System.Windows.Controls.DatePicker> controllo.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 L'esempio precedente usa una o più delle seguenti risorse.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Per l'esempio completo, vedere [Esempio di applicazione di stili con ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Stili e modelli di Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Personalizzazione dei controlli](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Applicazione di stili e modelli](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
