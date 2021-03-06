---
title: 'Procedura: Localizzare un''applicazione'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ed8ee8b8bfd9c3d6dadfedad8889af10a86466
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-localize-an-application"></a>Procedura: Localizzare un'applicazione
Questa esercitazione spiega come creare un'applicazione localizzata usando lo strumento LocBaml.  
  
> [!NOTE]
>  Lo strumento LocBaml non è un'applicazione di produzione. Viene presentato come esempio in cui vengono usate alcune delle API di localizzazione e illustra come scrivere uno strumento di localizzazione.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Panoramica  
 Questo documento offre un approccio graduale alla localizzazione di un'applicazione. Innanzitutto viene preparata l'applicazione in modo che sia possibile estrarre il testo da convertire. Dopo la conversione del testo, il testo convertito verrà incluso in una nuova copia dell'applicazione originale.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Requisiti  
 Nel corso di questa discussione verrà usato [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], un compilatore eseguito dalla riga di comando.  
  
 Inoltre, verrà spiegato come usare un file di progetto. Per istruzioni su come usare [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] e file di progetto, vedere [compilare e distribuire](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Tutti gli esempi di questa discussione usano en-US (inglese-Stati Uniti) come impostazioni cultura. In questo modo è possibile eseguire i passaggi degli esempi senza installare un'altra lingua.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Creare un'applicazione di esempio  
 In questo passaggio viene preparata l'applicazione per la localizzazione. Negli esempi di [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] viene fornito un esempio HelloApp che verrà usato per gli esempi di codice in questa discussione. Se si desidera usare questo esempio, scaricare il [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i file dal [strumento LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Sviluppare l'applicazione fino al punto in cui si vuole iniziare la localizzazione.  
  
2.  Specificare la lingua di sviluppo nel file di progetto in modo che [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] possa generare un assembly principale e un assembly satellite (un file con estensione .resources.dll) in cui includere le risorse della lingua di sistema. Il file di progetto nell'esempio HelloApp è HelloApp.csproj. In questo file la lingua di sviluppo viene identificata come segue:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Aggiungere gli UID ai file [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Gli UID vengono usati per rilevare le modifiche apportate ai file e per identificare gli elementi da convertire. Per aggiungere gli UID ai file, eseguire **updateuid** sul file di progetto:  
  
     **msbuild /t:updateuid helloapp.csproj**  
  
     Per verificare che si non mancanti o duplicati degli Uids, eseguire **checkuid**:  
  
     **msbuild /t:checkuid helloapp.csproj**  
  
     Dopo aver eseguito **updateuid**, i file devono contenere UID. Ad esempio, il file Pane1.xaml di HelloApp dovrebbe includere quanto segue:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Creare l'assembly satellite per le risorse della lingua di sistema  
 Dopo aver configurato l'applicazione per generare un assembly satellite per le risorse della lingua di sistema, è necessario compilare l'applicazione. Viene generato l'assembly principale dell'applicazione, nonché l'assembly satellite per le risorse della lingua di sistema richiesto da LocBaml per la localizzazione. Per compilare l'applicazione:  
  
1.  Compilare HelloApp per creare [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **msbuild helloapp.csproj**  
  
2.  L'assembly principale dell'applicazione appena creato, HelloApp.exe, viene inserito nella cartella seguente:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  L'assembly satellite per le risorse della lingua di sistema appena creato, HelloApp.resources.dll, viene inserito nella cartella seguente:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Compilare lo strumento LocBaml  
  
1.  Tutti i file necessari per compilare LocBaml si trovano negli esempi in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Scaricare il [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] i file dal [strumento LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Eseguire il file di progetto (LocBaml.csproj) per compilare lo strumento dalla riga di comando:  
  
     **msbuild locbaml.csproj**  
  
3.  Passare alla directory Bin\Release per trovare il file eseguibile appena creato (locbaml.exe). Esempio: C:\LocBaml\Bin\Release\locbaml.exe  
  
4.  Le opzioni che è possibile specificare quando si esegue LocBaml sono le seguenti:  
  
    -   **analizzare** o **-p:** analizza Baml, risorse, o [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] per generare un file con estensione csv o txt.  
  
    -   **generare** o **-g** genera un file binario localizzato utilizzando un file convertito.  
  
    -   **out** o **-o** {*directoryfile*] **:** nome file di Output.  
  
    -   **impostazioni cultura** o **- cul** {*delle impostazioni cultura*] **:** internazionali degli assembly di output.  
  
    -   **conversione** o **- trans** {*Translation. csv*] **:** file tradotto o localizzato.  
  
    -   **asmpath** o **- asmpath:** {*directoryfile*] **:** se il [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] codice contiene controlli personalizzati, è necessario specificare il  **asmpath** all'assembly del controllo personalizzato.  
  
    -   **nologo:** non visualizza loghi o informazioni sul copyright.  
  
    -   **verbose:** visualizza le informazioni sulla modalità dettagliata.  
  
    > [!NOTE]
    >  Se è necessario un elenco delle opzioni quando si esegue lo strumento, digitare **LocBaml.exe** e premere INVIO.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Usare LocBaml per analizzare un file  
 Ora che è stato creato lo strumento LocBaml, è possibile usarlo per analizzare HelloApp.resources.dll ed estrarre il contenuto testuale che verrà localizzato.  
  
1.  Copiare LocBaml.exe nella cartella bin\debug dell'applicazione in cui è stato creato l'assembly principale dell'applicazione.  
  
2.  Per analizzare il file dell'assembly satellite e archiviare l'output come file CSV, usare il comando seguente:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Se il file di input, HelloApp.resources.dll, non è nella stessa directory di LocBaml.exe, spostare uno dei file in modo che entrambi siano nella stessa directory.  
  
3.  Quando si esegue LocBaml per analizzare i file, l'output è costituito da sette campi delimitati da virgole (file CSV) o da tabulazioni (file TXT). Di seguito viene visualizzato il file CSV analizzato per HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   I campi di sette sono:  
  
   1.  **Nome BAML**. Il nome della risorsa BAML rispetto all'assembly satellite per la lingua di origine.  
  
   2.  **Chiave di risorsa**. L'identificatore della risorsa localizzata.  
  
   3.  **Categoria**. Tipo di valore. Vedere [commenti e gli attributi di localizzazione](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Leggibilità**. Se il valore può essere letto da un localizzatore. Vedere [commenti e gli attributi di localizzazione](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modificabilità**. Se il valore può essere modificato da un localizzatore. Vedere [commenti e gli attributi di localizzazione](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Commenti**. Descrizione aggiuntiva del valore per determinarne la modalità di localizzazione. Vedere [commenti e gli attributi di localizzazione](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Valore**. Il valore di testo da convertire nelle impostazioni cultura desiderate.  
  
   La tabella seguente mostra come viene eseguito il mapping di questi campi ai valori delimitati del file CSV:  
  
   |Nome BAML|Chiave di risorsa|Categoria|Leggibilità|Modificabilità|Commenti|Valore|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignora|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|nessuno|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|nessuno|TRUE|TRUE||Goodbye World|
  
   Si noti che tutti i valori per il **commenti** campo non contengono valori; se un campo non dispone di un valore, è vuoto. Si noti inoltre che l'elemento nella prima riga non è né leggibile né modificabile e presenta "Ignora" come relativo **categoria** valore, che indica che il valore non è localizzabile.  
  
4.  Per facilitare l'individuazione di elementi localizzabili nei file analizzati, in particolare nei file di grandi dimensioni, è possibile ordinare o filtrare gli elementi per **categoria**, **leggibilità**, e **modificabilità**. Ad esempio, è possibile escludere i valori non leggibili e non modificabili.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Convertire il contenuto localizzabile  
 Usare gli strumenti disponibili per convertire il contenuto estratto. Un metodo efficace consiste nello scrivere le risorse in un file CSV e visualizzarle in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], apportando le modifiche alla conversione nell'ultima colonna (valore).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Usare LocBaml per generare un nuovo file resources.dll  
 Il contenuto identificato analizzando HelloApp.resources.dll con LocBaml è stato convertito e deve essere reinserito nell'applicazione originale. Utilizzare il **generare** o **-g** opzione per generare un nuovo. i file resources.  
  
1.  Usare la sintassi seguente per generare un nuovo file HelloApp.resources.dll. Contrassegnare le impostazioni cultura come en-US (/cul:en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    >  Se il file di input Hello.csv non è presente nella stessa directory del file eseguibile LocBaml.exe, spostare uno dei file in modo che entrambi siano nella stessa directory.  
  
2.  Sostituire il file HelloApp.resources.dll precedente nella directory C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll con il file HelloApp.resources.dll appena creato.  
  
3.  Ora "Hello World" e "Goodbye World" possono essere convertiti nell'applicazione.  
  
4.  Per eseguire la conversione in una lingua diversa, usare le impostazioni cultura della lingua in cui si sta eseguendo la conversione. L'esempio seguente mostra come eseguire la conversione in lingua francese canadese:  
  
     **LocBaml.exe genera HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr-autorità di certificazione**  
  
5.  Nello stesso assembly dell'assembly principale dell'applicazione, creare una nuova cartella specifica per le impostazioni cultura dove ospitare il nuovo assembly satellite. Per la lingua francese canadese, la cartella sarà fr-CA.  
  
6.  Copiare l'assembly satellite generato nella nuova cartella.  
  
7.  Per testare il nuovo assembly satellite, è necessario modificare le impostazioni cultura con cui verrà eseguita l'applicazione. Questa operazione può essere eseguita in due modi:  
  
    -   Modificare le impostazioni internazionali del sistema operativo (**avviare** &#124; **Pannello di controllo** &#124; **Internazionali e della lingua**).  
  
    -   Aggiungere il codice seguente al file App.xaml.cs nell'applicazione:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Alcuni suggerimenti per l'uso di LocBaml  
  
-   Tutti gli assembly dipendenti che definiscono i controlli personalizzati devono essere copiati nella directory locale di LocBaml o installati in Global Assembly Cache. È un passaggio necessario perché l'API di localizzazione deve avere accesso agli assembly dipendenti quando legge [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Se l'assembly principale è firmato, anche la DLL di risorse generata deve essere firmata per poter essere caricata.  
  
-   La versione della DLL di risorsa localizzata deve essere sincronizzata con l'assembly principale.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Argomenti successivi  
 A questo punto dovrebbero essere state acquisite le conoscenze di base sull'uso dello strumento LocBaml.  Si dovrebbe essere in grado di creare un file che contiene UID. Usando lo strumento LocBaml, si dovrebbe essere in grado di analizzare un file per estrarre il contenuto localizzabile e, dopo la conversione del contenuto, generare un file resources.dll che inserisce il contenuto convertito. Questo argomento non include tutti i dettagli, ma offre le informazioni necessarie per usare LocBaml per la localizzazione delle applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Globalizzazione per WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Cenni preliminari sull'utilizzo del layout automatico](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
