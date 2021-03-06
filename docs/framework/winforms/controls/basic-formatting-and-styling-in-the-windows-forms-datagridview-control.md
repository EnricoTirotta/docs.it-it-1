---
title: Formattazione e stile di base nel controllo DataGridView Windows Form
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fa5c240adaaf6512cfbd6b7bd0796bd0983a530
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Formattazione e stile di base nel controllo DataGridView Windows Form
Il `DataGridView` controllo rende più semplice definire l'aspetto delle celle di base e la formattazione di valori di cella. È possibile definire l'aspetto e la formattazione di stili per le singole celle, per le celle in colonne e righe specifiche o per tutte le celle nel controllo impostando le proprietà del `DataGridViewCellStyle` accessibili tramite diversi oggetti `DataGridView` le proprietà del controllo. Inoltre, è possibile modificare gli stili in modo dinamico in base a fattori, ad esempio il valore di cella gestendo il `CellFormatting` evento.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Modificare gli stili dei bordi e delle linee della griglia nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Viene descritto come impostare `DataGridView` le proprietà che definiscono l'aspetto del bordo del controllo e linee di separazione tra le celle.  
  
 [Stili delle celle nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 Viene descritto il `DataGridViewCellStyle` classe e l'interagiscono tra le proprietà di tale tipo per definire la modalità di visualizzazione delle celle nel controllo.  
  
 [Procedura: Impostare stili di cella predefiniti per il controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Viene descritto come utilizzare `DataGridViewCellStyle` proprietà per definire l'aspetto predefinito di celle, righe e colonne specifiche in tutto il controllo.  
  
 [Procedura: Formattare i dati nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Viene descritto come formattare i valori visualizzati nelle celle utilizzando `DataGridViewCellStyle` proprietà.  
  
 [Procedura: Impostare gli stili di carattere e colore nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Viene descritto come utilizzare il `DefaultCellStyle` proprietà da impostare base visualizzare caratteristiche per tutte le celle nel controllo.  
  
 [Procedura: Impostare stili di righe alterne per il controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Viene descritto come creare un effetto registro nel controllo con righe alterne che vengono visualizzate in modo diverso.  
  
 [Procedura: Usare il modello di riga per personalizzare le righe nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Viene descritto come utilizzare il `RowTemplate` proprietà per impostare le proprietà di riga che verranno utilizzate per tutte le righe nel controllo.  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Windows.Forms.DataGridView>  
 Fornisce la documentazione di riferimento per il controllo <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 Fornisce la documentazione di riferimento per la <xref:System.Windows.Forms.DataGridViewCellStyle> classe.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 Fornisce la documentazione di riferimento per il <xref:System.Windows.Forms.DataGridView.CellFormatting> evento.  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 Fornisce la documentazione di riferimento per la <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> proprietà.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Personalizzazione del controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Fornisce argomenti che descrivono come disegnare celle e righe personalizzate di <xref:System.Windows.Forms.DataGridView> e come creare tipi di cella, colonna e riga derivati.  
  
 [Funzionalità di base per colonna, riga e cella nel controllo DataGridView di Windows Form](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Fornisce argomenti che descrivono comunemente usate le proprietà di cella, riga e colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
