---
title: "Accelerator Keys (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator keys"
  - "Image editor [C++], accelerator keys"
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Accelerator Keys (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下為影像編輯器命令預設繫結的快速鍵 \(Accelerator Key\)。  若要變更快速鍵，請按一下 \[**工具**\] 功能表上的 \[**選項**\]，然後在 \[**環境**\] 資料夾底下選擇 \[**鍵盤**\]。  如需詳細資訊，請參閱 [識別及自訂鍵盤快速鍵](../Topic/Identifying%20and%20Customizing%20Keyboard%20Shortcuts%20in%20Visual%20Studio.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 \[說明\] 中描述的有所不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
|Command|索引鍵|描述|  
|-------------|---------|--------|  
|Image.AirBrushTool|CTRL \+ A|使用已選取大小和色彩的噴槍繪製。|  
|Image.BrushTool|CTRL \+ B|使用已選取形狀、大小和色彩的筆刷繪製。|  
|Image.CopyAndOutlineSelection|CTRL \+ SHIFT \+ U|建立一份目前選取範圍的複本，並建立此複本的外框。  如果背景色彩包含在目前的選取範圍內，當您選取[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)時，背景色彩將會排除在外。|  
|Image.DrawOpaque|CTRL \+ J|使目前的選取範圍成為[不透明或透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|  
|Image.EllipseTool|CTRL \+ P|以選取的線條寬度和色彩繪製一個橢圓形。|  
|Image.EraserTool|CTRL \+ SHIFT \+ I|清除影像具有目前的背景色彩的部分。|  
|Image.FilledEllipseTool|CTRL \+ SHIFT \+ ALT \+ P|畫出實心橢圓形。|  
|Image.FilledRectangleTool|CTRL \+ SHIFT \+ ALT \+ R|畫出實心矩形。|  
|Image.FilledRoundRectangleTool|CTRL \+ SHIFT \+ ALT \+ W|畫出實心圓角矩形。|  
|Image.FillTool|CTRL \+ F|填滿某個區域。|  
|Image.FlipHorizontal|CTRL \+ H|水平翻轉影像或選取範圍。|  
|Image.FlipVertical|SHIFT \+ ALT \+ H|垂直翻轉影像或選取範圍。|  
|Image.LargerBrush|CTRL \+ \=|在每一個方向上增加一個像素的筆刷大小。  若要縮小筆刷的大小，請參閱本表格中的 Image.SmallerBrush。|  
|Image.LineTool|CTRL \+ L|以選取的形狀、大小和色彩繪製一條直線。|  
|Image.MagnificationTool|CTRL \+ M|啟動 \[放大\] 工具，可讓您針對影像的特定部分放大。|  
|Image.Magnify|CTRL \+ SHIFT \+ M|在目前的縮放比例與 1:1 縮放比例之間切換。|  
|Image.NewImageType|INSERT|啟動[新增 \<Device\> 影像類型對話方塊](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md)，使用此對話方塊即可建立不同影像類型的影像。|  
|Image.NextColor|CTRL \+ \]<br /><br /> \-或\-<br /><br /> CTRL \+ 向右鍵|將繪圖前景色彩變更成下一個調色盤色彩。|  
|Image.NextRightColor|CTRL \+ SHIFT \+ \]<br /><br /> \-或\-<br /><br /> SHIFT \+ CTRL \+ 向右鍵|將繪圖背景色彩變更成下一個調色盤色彩。|  
|Image.OutlinedEllipseTool|SHIFT \+ ALT \+ P|繪製出帶外框的實心橢圓形。|  
|Image.OutlinedRectangleTool|SHIFT \+ ATL \+ R|繪製出帶外框的實心矩形|  
|Image.OutlinedRoundRectangleTool|SHIFT \+ ALT \+ W|繪製出帶外框的實心圓角矩形。|  
|Image.PencilTool|CTRL \+ I|使用單像素鉛筆繪製。|  
|Image.PreviousColor|CTRL \+ \[<br /><br /> \-或\-<br /><br /> CTRL \+ 向左鍵|將繪圖前景色彩變更成前一個調色盤色彩。|  
|Image.PreviousRightColor|CTRL \+ SHIFT \+ \[<br /><br /> \-或\-<br /><br /> SHIFT \+ CTRL \+ 向左鍵|將繪圖背景色彩變更成前一個調色盤色彩。|  
|Image.RectangleSelectionTool|SHIFT \+ ALT \+ S|選取影像的矩形部分來移動、複製或編輯。|  
|Image.RectangleTool|ATL \+ R|以選取的線條寬度和色彩繪製一個矩形。|  
|Image.Rotate90Degrees|CTRL \+ SHIFT \+ H|旋轉影像或選取範圍 90 度。|  
|Image.RoundedRectangleTool|ALT \+ W|以選取的線條寬度和色彩繪製一個圓角矩形。|  
|Image.ShowGrid|CTRL \+ ALT \+ S|切換像素格線 \(在[格線設定對話方塊](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中選取或清除 \[像素格線\] 選項\)。|  
|Image.ShowTileGrid|CTRL \+ SHIFT \+ ALT \+ S|切換磚狀格線 \(在[格線設定對話方塊](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中選取或清除 \[磚狀格線\] 選項\)。|  
|Image.SmallBrush|CTRL \+ .   \(句號\)|將 \[筆刷\] 大小減少一個像素   \(請參閱本表中的 Image.LargerBrush 和 Image.SmallerBrush\)。|  
|Image.SmallerBrush|CTRL \+ \- \(減號\)|在每一個方向上減少一個像素的筆刷大小。  若要再次擴充筆刷的大小，請參閱本表格中的 Image.LargerBrush。|  
|Image.TextTool|CTRL \+ T|開啟[文字工具對話方塊](../mfc/text-tool-dialog-box-image-editor-for-icons.md)。|  
|Image.UseSelectionAsBrush|CTRL \+ U|使用目前選取的範圍做為筆刷繪製。|  
|Image.ZoomIn|CTRL \+ SHIFT \+ .   \(句號\)<br /><br /> \-或\-<br /><br /> CTRL \+ 向上鍵|增加目前檢視的縮放比例。|  
|Image.ZoomOut|CTRL \+ , \(逗號\)<br /><br /> \-或\-<br /><br /> CTRL \+ 向下鍵|降低目前檢視的縮放比率|  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 None  
  
## 請參閱  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)