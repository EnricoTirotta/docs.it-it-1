---
title: Estendere l'effetto cristallo a un'applicazione WPF
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
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad070bca408fc608eb000948c1b942d08f02018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Estendere l'effetto cristallo a un'applicazione WPF
In questo argomento viene illustrato come estendere il fotogramma effetto cristallo[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] nell'area client di un'applicazione [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
> [!NOTE]
>  Questo esempio funziona solo su un computer [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] che esegue Gestione finestre desktop (DWM) con l'effetto cristallo abilitato. Home Basic edition di [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] non supporta la trasparenza effetto cristallo. Le aree che avrebbero una trasparenza effetto cristallo nelle altre versioni di [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] risultano opache.  
  
## <a name="example"></a>Esempio  
 L'immagine seguente illustra il fotogramma effetto cristallo esteso alla barra degli indirizzi di Internet Explorer 7.  
  
 **Internet Explorer con il fotogramma effetto cristallo esteso dietro la barra degli indirizzi.**  
  
 ![IE7 con il fotogramma effetto cristallo esteso dietro la barra degli indirizzi.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 Per estendere il fotogramma effetto cristallo su un'applicazione [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], è necessario accedere a [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] non gestita. L'esempio di codice seguente esegue Platform Invoke (pinvoke) per le due [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] necessarie per estendere il fotogramma all'area client. Ognuna di queste [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] vengono dichiarate in una classe denominata **NonClientRegionAPI**.  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MARGINS  
{  
    public int cxLeftWidth;      // width of left border that retains its size  
    public int cxRightWidth;     // width of right border that retains its size  
    public int cyTopHeight;      // height of top border that retains its size  
    public int cyBottomHeight;   // height of bottom border that retains its size  
};  
  
[DllImport("DwmApi.dll")]  
public static extern int DwmExtendFrameIntoClientArea(  
    IntPtr hwnd,  
    ref MARGINS pMarInset);  
```  
  
```vb  
<StructLayout(LayoutKind.Sequential)>  
        Public Structure MARGINS  
            Public cxLeftWidth As Integer ' width of left border that retains its size  
            Public cxRightWidth As Integer ' width of right border that retains its size  
            Public cyTopHeight As Integer ' height of top border that retains its size  
            Public cyBottomHeight As Integer ' height of bottom border that retains its size  
        End Structure  
  
        <DllImport("DwmApi.dll")>  
        Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer  
        End Function  
```  
  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) è la funzione DWM che estende il fotogramma all'area client. Il metodo accetta due parametri; un punto di controllo di finestra e una struttura [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx). [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) viene usata per indicare a DWM l'ulteriore estensione del fotogramma dell'area client.  
  
## <a name="example"></a>Esempio  
 Per usare la funzione [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx), è necessario ottenere un punto di controllo di finestra. In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l'handle di finestra può essere ottenuto dal <xref:System.Windows.Interop.HwndSource.Handle%2A> proprietà di un <xref:System.Windows.Interop.HwndSource>. Nell'esempio seguente, il frame viene esteso nell'area client nel <xref:System.Windows.FrameworkElement.Loaded> evento della finestra.  
  
```csharp  
void OnLoaded(object sender, RoutedEventArgs e)  
{  
   try  
   {  
      // Obtain the window handle for WPF application  
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;  
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);  
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);  
  
      // Get System Dpi  
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);  
      float DesktopDpiX = desktop.DpiX;  
      float DesktopDpiY = desktop.DpiY;  
  
      // Set Margins  
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();  
  
      // Extend glass frame into client area  
      // Note that the default desktop Dpi is 96dpi. The  margins are  
      // adjusted for the system Dpi.  
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));  
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));  
  
      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);  
      //  
      if (hr < 0)  
      {  
         //DwmExtendFrameIntoClientArea Failed  
      }  
   }  
   // If not Vista, paint background white.  
   catch (DllNotFoundException)  
   {  
      Application.Current.MainWindow.Background = Brushes.White;  
   }  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una semplice finestra in cui il fotogramma viene esteso all'area client. Il frame viene esteso dietro il bordo superiore che contiene i due <xref:System.Windows.Controls.TextBox> oggetti.  
  
```xaml  
<Window x:Class="SDKSample.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Extended Glass in WPF" Height="300" Width="400"   
    Loaded="OnLoaded" Background="Transparent"  
    >  
  <Grid ShowGridLines="True">  
    <DockPanel Name="mainDock">  
      <!-- The border is used to compute the rendered height with margins.  
           topBar contents will be displayed on the extended glass frame.-->  
      <Border Name="topBar" DockPanel.Dock="Top" >  
        <Grid Name="grid">  
          <Grid.ColumnDefinitions>  
            <ColumnDefinition MinWidth="100" Width="*"/>  
            <ColumnDefinition Width="Auto"/>  
          </Grid.ColumnDefinitions>  
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>  
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>  
        </Grid>  
      </Border>  
      <Grid DockPanel.Dock="Top" >  
        <Grid.ColumnDefinitions>  
          <ColumnDefinition/>  
        </Grid.ColumnDefinitions>  
        <TextBox Grid.Column="0" AcceptsReturn="True"/>  
      </Grid>  
    </DockPanel>  
  </Grid>  
</Window>  
```  
  
 Nell'immagine seguente viene illustrato il fotogramma effetto cristallo esteso in un'applicazione [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 **Estensione dell'effetto cristallo a un'applicazione**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **.**  
  
 ![Estensione dell'effetto cristallo a un'applicazione WPF.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gestione finestre desktop](https://msdn.microsoft.com/library/aa969540.aspx)  
 [Panoramica di sfocatura Gestione finestre desktop](https://msdn.microsoft.com/library/aa969537.aspx)  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx)
