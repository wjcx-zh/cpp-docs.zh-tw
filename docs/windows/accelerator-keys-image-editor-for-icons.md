---
title: 快速鍵（C++圖示影像編輯器）
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 867c7d2c217b5efb832654a7863e834a4351c126
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167572"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>快速鍵（C++圖示影像編輯器）

以下是預設系結至索引鍵之影像編輯器命令的快速鍵。 若要變更快速鍵，請移至 功能表**工具** > **選項**，然後選擇 **環境** 資料夾下的 **鍵盤**。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更您的設定，請移至功能表**工具** > 匯**入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

|Command|索引鍵|描述|
|-------------|----------|-----------------|
|AirBrushTool|**Ctrl** + **A**|使用具有所選大小和色彩的噴槍繪製。|
|Image.BrushTool|**Ctrl** + **B**|使用具有所選形狀、大小和色彩的筆刷繪製。|
|CopyAndOutlineSelection|**Ctrl** + **Shift** + **U**|建立一份目前選取範圍的複本，並建立此複本的外框。 如果背景色彩包含在目前的選取範圍內，則會在您選取 [[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)] 時予以排除。|
|Image.DrawOpaque|**Ctrl** + **J**|使目前的選取範圍成為不[透明或透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|
|Image.EllipseTool|**Ctrl** + **P**|以選取的線條寬度和色彩繪製橢圓形。|
|EraserTool|**Ctrl** + **Shift** + **I**|清除影像的一部分（具有目前的背景色彩）。|
|Image.FilledEllipseTool|**Ctrl** + **Shift** + **Alt** + **P**|畫出實心橢圓形。|
|Image.FilledRectangleTool|**Ctrl** + **Shift** + **Alt** + **R**|畫出實心矩形。|
|FilledRoundRectangleTool|**Ctrl** + **Shift** + **Alt** + **W**|畫出實心圓角矩形。|
|Image.FillTool|**Ctrl** + **F**|填滿某個區域。|
|Image.FlipHorizontal|**Ctrl** + **H**|水平翻轉影像或選取範圍。|
|Image.FlipVertical|**Shift**+ **Alt** + **H**|垂直翻轉影像或選取範圍。|
|Image.LargerBrush|**Ctrl** +  **=**|在每一個方向上增加一個像素的筆刷大小。 若要縮小筆刷的大小，請參閱本表格中的 Image.SmallerBrush。|
|Image.LineTool|**Ctrl** + **L**|以選取的形狀、大小和色彩繪製一條直線。|
|Image.MagnificationTool|**Ctrl** + **M**|啟動**放大**工具，可讓您放大影像的特定區段。|
|Image.Magnify|**Ctrl** + **Shift** + **M**|在目前的縮放比例與 1:1 縮放比例之間切換。|
|Image.NewImageType|**插入**|啟動[新的 \<裝置 > 映射類型 對話方塊](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)，您可以在其中建立不同映射類型的映射。|
|Image.NextColor|**Ctrl** +  **]**<br /><br /> - 或 -<br /><br /> **Ctrl** + **向右箭**號|將繪圖前景色彩變更成下一個調色盤色彩。|
|Image.NextRightColor|**Ctrl** + **Shift** +  **]**<br /><br /> - 或 -<br /><br /> **Shift** + **Ctrl** + **向右箭**號|將繪圖背景色彩變更成下一個調色盤色彩。|
|Image.OutlinedEllipseTool|**Shift** + **Alt** + **P**|繪製出帶外框的實心橢圓形。|
|Image.OutlinedRectangleTool|**Shift** + **Alt** + **R**|繪製出帶外框的實心矩形|
|OutlinedRoundRectangleTool|**Shift** + **Alt** + **W**|繪製出帶外框的實心圓角矩形。|
|Image.PencilTool|**Ctrl** + **I**|使用單像素鉛筆繪製。|
|Image.PreviousColor|**Ctrl** +  **[**<br /><br /> - 或 -<br /><br /> **Ctrl** + **向左鍵**|將繪圖前景色彩變更成前一個調色盤色彩。|
|Image.PreviousRightColor|**Ctrl** + **Shift** +  **[**<br /><br /> - 或 -<br /><br /> **Shift** + **Ctrl** + **向左鍵**|將繪圖背景色彩變更成前一個調色盤色彩。|
|Image.RectangleSelectionTool|**Shift** + **Alt** + **S**|選取要移動、複製或編輯之影像的矩形部分。|
|Image.RectangleTool|ATL + R|以選取的線條寬度和色彩繪製矩形。|
|Image.Rotate90Degrees|**Ctrl** + **Shift** + **H**|旋轉影像或選取範圍 90 度。|
|Image.RoundedRectangleTool|**Alt** + **W**|以選取的線條寬度和色彩繪製圓角矩形。|
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|切換圖元格線（選取或清除 [[方格設定] 對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)中的 [**圖元格線**] 選項）。|
|Image.ShowTileGrid|**Ctrl** + **Shift** + **Alt** + **S**|切換磚方格（選取或清除 [[方格設定] 對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)中的 [**磚格線**] 選項）。|
|Image.SmallBrush|**Ctrl** +  **.** (句號)|將**筆刷**大小縮減為一個圖元。 (請參閱本表中的 Image.LargerBrush 和 Image.SmallerBrush)。|
|Image.SmallerBrush|**Ctrl** +  **-** （減號）|在每一個方向上減少一個像素的筆刷大小。 若要再次擴充筆刷的大小，請參閱本表格中的 Image.LargerBrush。|
|Image.TextTool|**Ctrl** + **T**|開啟 [[文字工具] 對話方塊](../windows/text-tool-dialog-box-image-editor-for-icons.md)。|
|UseSelectionAsBrush|**Ctrl** + **U**|使用目前選取的範圍做為筆刷繪製。|
|Image.ZoomIn|**Ctrl** + **Shift** +  **。** (句號)<br /><br /> - 或 -<br /><br /> **Ctrl** + **向上箭**號|增加目前檢視的縮放比例。|
|Image.ZoomOut|**Ctrl** +  **、** （逗號）<br /><br /> - 或 -<br /><br /> **Ctrl** + **向下鍵**|降低目前檢視的縮放比率|

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
