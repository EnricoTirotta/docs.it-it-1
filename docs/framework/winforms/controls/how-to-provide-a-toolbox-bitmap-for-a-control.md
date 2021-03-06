---
title: 'Procedura: specificare una bitmap nella casella degli strumenti per un controllo'
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
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446e0f830e916e7f4118a7374c66f238a60fda02
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Procedura: specificare una bitmap nella casella degli strumenti per un controllo
Se si desidera disporre è visualizzata un'icona speciale per il controllo di **della casella degli strumenti**, è possibile specificare una particolare immagine utilizzando il <xref:System.Drawing.ToolboxBitmapAttribute>. Questa classe è un *attributo*, un tipo speciale di classe che è possibile allegare ad altre classi. Per altre informazioni sugli attributi, vedere [NOT IN BUILD: Panoramica sugli attributi in Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) per [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] e [Attributi](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) per [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
 Utilizzo di <xref:System.Drawing.ToolboxBitmapAttribute>, è possibile specificare una stringa che indica il percorso e il nome di una bitmap di 16x16 pixel. Questa bitmap viene quindi visualizzata accanto al controllo quando è aggiunta alla **Casella degli strumenti**. È inoltre possibile specificare un <xref:System.Type>, nel qual caso la bitmap associata a tale tipo viene caricata. Se si specificano sia un <xref:System.Type> e una stringa, il controllo ricerca per una risorsa immagine con il nome specificato dal parametro di stringa dell'assembly contenente il tipo specificato per il <xref:System.Type> parametro.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Per specificare una bitmap della casella degli strumenti per il controllo  
  
1.  Aggiungere il <xref:System.Drawing.ToolboxBitmapAttribute> alla dichiarazione di classe del controllo prima di `Class` parola chiave per [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]e sopra la dichiarazione di classe per [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Ricompilare il progetto.  
  
    > [!NOTE]
    >  La bitmap non viene visualizzata nella casella degli strumenti per i controlli e i componenti generati automaticamente. Per visualizzare la bitmap, ricaricare il controllo usando la finestra di dialogo **Scegli elementi della casella degli strumenti**. Per altre informazioni, vedere [Procedura dettagliata: compilare automaticamente la casella degli strumenti con componenti personalizzati](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [Procedura dettagliata: Compilare automaticamente la casella degli strumenti con componenti personalizzati](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Sviluppo di controlli Windows Form in fase di progettazione](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Attributi (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [Attributi](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
