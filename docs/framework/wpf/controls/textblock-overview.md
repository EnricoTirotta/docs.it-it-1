---
title: Cenni preliminari sul controllo TextBlock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 404f5677bca0df45d4f7dbf689a297499b36bbab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="textblock-overview"></a>Cenni preliminari sul controllo TextBlock
Il <xref:System.Windows.Controls.TextBlock> controllo fornisce il supporto di testo flessibile per [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazioni. L'elemento è destinato principalmente a scenari [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] di base che non richiedono più di un paragrafo di testo. Supporta un numero di proprietà che consentono un controllo preciso della presentazione, ad esempio <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, e <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Contenuto di testo può essere aggiunti mediante la <xref:System.Windows.Controls.TextBlock.Text%2A> proprietà. Se usato in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], il contenuto tra tag di apertura e di chiusura viene aggiunto in modo implicito come testo dell'elemento.  
  
 Oggetto <xref:System.Windows.Controls.TextBlock> elemento può essere implementato in poche parole con [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 Analogamente, l'utilizzo del <xref:System.Windows.Controls.TextBlock> elemento nel codice è relativamente semplice.  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Controls.Label>
