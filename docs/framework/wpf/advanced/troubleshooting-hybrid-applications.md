---
title: Risoluzione dei problemi relativi ad applicazioni ibride
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a23f439b9b14d16a5440fa3b757b972304fdfa3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="troubleshooting-hybrid-applications"></a>Risoluzione dei problemi relativi ad applicazioni ibride
<a name="introduction"></a> Questo argomento illustra alcuni problemi comuni che possono verificarsi durante la creazione di applicazioni che usano tecnologie sia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], sia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Sovrapposizione di controlli  
 I controlli potrebbero sovrapporsi in maniera imprevista. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usa un HWND separato per ogni controllo. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa un HWND per tutto il contenuto in una pagina. Questa differenza di implementazione provoca comportamenti di sovrapposizione imprevisti.  
  
 Un controllo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ospitato in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] viene sempre visualizzato sopra il contenuto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]il contenuto ospitato un <xref:System.Windows.Forms.Integration.ElementHost> verrà visualizzato un controllo in corrispondenza dell'ordine z del <xref:System.Windows.Forms.Integration.ElementHost> controllo. È possibile sovrapporre <xref:System.Windows.Forms.Integration.ElementHost> controlli, ma l'hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenuto non combinare o interagire.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Child Property  
 Il <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classi possono ospitare solo un singolo controllo o elemento figlio. Per ospitarne più di uno, è necessario usare un contenitore come contenuto figlio. Ad esempio, è possibile aggiungere [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controlli pulsante e casella di controllo per un <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> controllare e quindi assegnare il pannello da un <xref:System.Windows.Forms.Integration.WindowsFormsHost> del controllo <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> proprietà. Tuttavia, è possibile aggiungere i controlli pulsante e casella di controllo separatamente allo stesso <xref:System.Windows.Forms.Integration.WindowsFormsHost> controllo.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Ridimensionamento  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hanno modelli di ridimensionamento diversi. Alcune trasformazioni di ridimensionamento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hanno valore per i controlli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], ma non tutte. Ad esempio, è possibile ridimensionare un controllo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] fino a 0, ma se si prova a riportare lo stesso controllo su un valore diverso da 0, le dimensioni del controllo rimarranno invariate. Per altre informazioni, vedere [Considerazioni sul layout per l'elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adattatore  
 È possibile confusione quando si utilizza il <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classi, perché includono un contenitore nascosto. Sia il <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classi dispongono di un contenitore nascosto, chiamato un *adapter*, utilizzato per ospitare il contenuto. Per il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, l'adapter deriva il <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> classe. Per il <xref:System.Windows.Forms.Integration.ElementHost> (controllo), l'adapter deriva il <xref:System.Windows.Controls.DockPanel> elemento. I riferimenti all'adattatore presenti in altri argomenti sull'interoperabilità alludono a tale contenitore.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Annidamento  
 Nidificazione di un <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento all'interno di un <xref:System.Windows.Forms.Integration.ElementHost> controllo non è supportato. Nidificazione di un <xref:System.Windows.Forms.Integration.ElementHost> controllo all'interno di un <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento inoltre non è supportato.  
  
<a name="focus"></a>   
## <a name="focus"></a>Stato attivo  
 Lo stato attivo funziona in maniera diversa in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Per questo motivo, in un'applicazione ibrida possono verificarsi problemi relativi allo stato attivo. Ad esempio, se si dispone dello stato attivo all'interno di un <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento e ridurre al minimo e ripristino della pagina o visualizzare una finestra di dialogo modali, attivo all'interno di <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento potrebbe andare perso. Il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento ha ancora lo stato attivo, ma il controllo all'interno non consentito.  
  
 Lo stato attivo influisce anche sulla convalida dei dati. Funzionamento della convalida un <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, ma non funziona come premere tab per uscire il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, o tra due diversi <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementi.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapping di proprietà  
 Alcuni mapping di proprietà richiedono un'interpretazione estensiva per integrare implementazioni dissimili tra le tecnologie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. I mapping di proprietà consentono al codice di rispondere alle modifiche apportate ai tipi di carattere, ai colori e ad altre proprietà. In generale, i mapping di proprietà funzionano rimanendo in ascolto di eventi *Property*Changed o chiamate On*Property*Changed e impostando le proprietà adeguate sul controllo figlio o sul relativo adattatore. Per altre informazioni, vedere [Mapping di proprietà di Windows Form e WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Proprietà relative al layout nel contenuto ospitato  
 Quando il <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> o <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> proprietà viene assegnato, diverse proprietà relative al layout del contenuto ospitato vengono impostate automaticamente. La modifica di queste proprietà di contenuto può determinare comportamenti di layout imprevisti.  
  
 Il contenuto ospitato è ancorato per riempire il <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> padre. Per abilitare questo comportamento di riempimento, durante l'impostazione della proprietà figlio vengono impostate varie proprietà. La tabella seguente elenca le proprietà del contenuto impostate dal <xref:System.Windows.Forms.Integration.ElementHost> e <xref:System.Windows.Forms.Integration.WindowsFormsHost> classi.  
  
|Classe host|Proprietà di contenuto|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Non impostare queste proprietà direttamente sul contenuto ospitato. Per altre informazioni, vedere [Considerazioni sul layout per l'elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Applicazioni di navigazione  
 Le applicazioni di navigazione potrebbero non mantenere lo stato dell'utente. Il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento ricrea i propri controlli quando viene utilizzata in un'applicazione di navigazione. Ricreazione di controlli figlio si verifica quando l'utente si sposta dalla pagina che ospita il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento e quindi restituisce a esso. Qualsiasi contenuto digitato dall'utente andrà perduto.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Interoperabilità del ciclo di messaggi  
 Quando si usano i cicli di messaggi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], i messaggi potrebbero essere elaborati in modo diverso dal previsto. Il <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metodo viene chiamato dal <xref:System.Windows.Forms.Integration.WindowsFormsHost> costruttore. Questo metodo aggiunge un filtro messaggi al ciclo di messaggi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Questo filtro chiama il <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metodo se un <xref:System.Windows.Forms.Control?displayProperty=nameWithType> era la destinazione del messaggio e converte o invia il messaggio.  
  
 Se si visualizza un <xref:System.Windows.Window> in un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ciclo di messaggi con <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, non è possibile digitare un valore a meno che non si chiama il <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metodo. Il <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metodo accetta un <xref:System.Windows.Window> e aggiunge un <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, che reindirizza i messaggi relativi alla chiave per la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ciclo di messaggi. Per altre informazioni, vedere [Architettura di input per l'interoperabilità tra Windows Form e WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Opacità e sovrapposizione  
 La <xref:System.Windows.Interop.HwndHost> classe non supporta la sovrapposizione. Ciò significa che l'impostazione di <xref:System.Windows.UIElement.Opacity%2A> proprietà il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento non ha alcun effetto e non ci sarà fusione con altri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] in cui <xref:System.Windows.Window.AllowsTransparency%2A> impostato su `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 L'eliminazione non corretta delle classi può determinare una perdita di risorse. Nelle applicazioni ibride, assicurarsi che il <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classi vengono eliminate o potrebbero verificarsi perdite di risorse. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Elimina <xref:System.Windows.Forms.Integration.ElementHost> controlli quando non modale <xref:System.Windows.Forms.Form> padre verrà chiuso. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Elimina <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementi quando l'applicazione viene arrestato. È possibile visualizzare un <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento in un <xref:System.Windows.Window> in un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ciclo di messaggi. In questo caso, è possibile che il codice non riceva notifica della chiusura dell'applicazione.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Abilitazione degli stili di visualizzazione  
 Gli stili di visualizzazione [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] di un controllo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] potrebbero non essere abilitati. Il <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metodo viene chiamato nel modello per un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dell'applicazione. Sebbene questo metodo non venga chiamato per impostazione predefinita, se si usa [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] per creare un progetto si otterranno gli stili di visualizzazione [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] per i controlli, se è disponibile la versione 6.0 di Comctl32.dll. È necessario chiamare il <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metodo prima che vengano creati gli handle nel thread. Per altre informazioni, vedere [Procedura: Abilitare stili di visualizzazione in un'applicazione ibrida](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Controlli con licenza  
 I controlli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] con licenza che mostrano all'utente in una finestra di messaggio le informazioni relative alla licenza potrebbero determinare comportamenti imprevisti in un'applicazione ibrida. Alcuni controlli con licenza visualizzano una finestra di dialogo in risposta alla creazione di handle. Ad esempio, un controllo con licenza potrebbe informare l'utente che è richiesta una licenza oppure che sono consentiti ancora tre usi del controllo a scopo di valutazione.  
  
 Il <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento deriva dal <xref:System.Windows.Interop.HwndHost> classe e l'handle del controllo figlio viene creato all'interno di <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metodo. Il <xref:System.Windows.Interop.HwndHost> non consente messaggi da elaborare nella classe di <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> (metodo), ma la visualizzazione di una finestra di dialogo fa sì che i messaggi da inviare. Per abilitare questo scenario di gestione delle licenze, chiamare il <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metodo sul controllo prima di assegnarlo come il <xref:System.Windows.Forms.Integration.WindowsFormsHost> figlio dell'elemento.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Designer  
 È possibile progettare contenuto WPF usando [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. Le sezioni seguenti elencano alcuni problemi comuni che possono verificarsi durante la creazione di applicazioni ibride con [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>Proprietà BackColorTransparent ignorata in fase di progettazione  
 Il <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> proprietà potrebbe non funzionare come previsto in fase di progettazione.  
  
 Se un controllo WPF non è presente su un elemento padre visibile, il runtime WPF ignora il <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> valore. Il motivo che <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> può essere ignorato perché <xref:System.Windows.Forms.Integration.ElementHost> oggetto viene creato in un apposito <xref:System.AppDomain>. Tuttavia, quando si esegue l'applicazione, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funziona come previsto.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Visualizzazione dell'elenco errori della fase di progettazione quando viene eliminata la cartella obj  
 Se la cartella obj viene eliminata, viene visualizzato l'elenco errori della fase di progettazione.  
  
 Quando si progetta utilizzando <xref:System.Windows.Forms.Integration.ElementHost>, Progettazione Windows Form vengono utilizzati file generati nella cartella di Debug o Release all'interno della cartella del progetto obj. Se si eliminano questi file, viene visualizzato l'elenco errori della fase di progettazione. Per risolvere questo problema, ricompilare il progetto. Per altre informazioni, vedere [Errori in fase di progettazione in Progettazione Windows Form](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost e IME  
 I controlli WPF ospitato in un <xref:System.Windows.Forms.Integration.ElementHost> attualmente non supportano il <xref:System.Windows.Forms.Control.ImeMode%2A> proprietà. Passa a <xref:System.Windows.Forms.Control.ImeMode%2A> verrà ignorata dai controlli ospitati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Interoperabilità in WPF Designer](http://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Architettura di input per l'interoperabilità tra Windows Form e WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Procedura: Abilitare stili di visualizzazione in un'applicazione ibrida](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [Considerazioni sul layout per l'elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Mapping di proprietà di Windows Form e WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Errori in fase di progettazione in Progettazione Windows Form](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Migrazione e interoperabilità](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
