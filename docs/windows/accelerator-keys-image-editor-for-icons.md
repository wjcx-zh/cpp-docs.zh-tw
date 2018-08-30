---
title: 快速鍵 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf65c4ab55861a5588c27484db604a8e7008b96d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200722"
---
# <a name="accelerator-keys-image-editor-for-icons"></a>快速鍵 (圖示影像編輯器)

以下是預設繫結至索引鍵的影像編輯器命令的快速鍵。 若要變更的快速鍵，請按一下**選項**上**工具**功能表，然後選擇 **鍵盤**下**環境**資料夾。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

|命令|按鍵|描述|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|使用所選的大小和色彩的噴槍繪製。|
|Image.BrushTool|**Ctrl** + **B**|使用選取的形狀、 大小和色彩的筆刷繪製。|
|Image.CopyAndOutlineSelection|**Ctrl** + **Shift** + **U**|建立一份目前選取範圍的複本，並建立此複本的外框。 如果目前的選取範圍中包含的背景色彩，將不會包含有[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)選取。|
|Image.DrawOpaque|**Ctrl** + **J**|可能會使目前的選取範圍[不透明或透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|
|Image.EllipseTool|**Ctrl** + **P**|繪製橢圓形使用選取的線條寬度和色彩。|
|Image.EraserTool|**Ctrl** + **Shift** + **I**|清除 （使用目前的背景色彩） 的映像的一部分。|
|Image.FilledEllipseTool|**Ctrl** + **Shift** + **Alt** + **P**|畫出實心橢圓形。|
|Image.FilledRectangleTool|**Ctrl** + **Shift** + **Alt** + **R**|畫出實心矩形。|
|Image.FilledRoundRectangleTool|**Ctrl** + **Shift** + **Alt** + **W**|畫出實心圓角矩形。|
|Image.FillTool|**Ctrl** + **F**|填滿某個區域。|
|Image.FlipHorizontal|**Ctrl** + **H**|水平翻轉影像或選取範圍。|
|Image.FlipVertical|**Shift**+ **Alt** + **H**|垂直翻轉影像或選取範圍。|
|Image.LargerBrush|**Ctrl 鍵** + **=**|在每一個方向上增加一個像素的筆刷大小。 若要縮小筆刷的大小，請參閱本表格中的 Image.SmallerBrush。|
|Image.LineTool|**Ctrl** + **L**|以選取的形狀、大小和色彩繪製一條直線。|
|Image.MagnificationTool|**Ctrl** + **M**|啟動**Magnify**工具，可讓您放大您的映像的特定區段。|
|Image.Magnify|**Ctrl** + **Shift** + **M**|在目前的縮放比例與 1:1 縮放比例之間切換。|
|Image.NewImageType|**插入**|會啟動[的新\<裝置 > 影像類型對話方塊](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)與您可以建立不同的映像類型的影像。|
|Image.NextColor|**Ctrl** + **]**<br /><br /> -或-<br /><br /> **Ctrl** + **向右箭頭**|將繪圖前景色彩變更成下一個調色盤色彩。|
|Image.NextRightColor|**Ctrl** + **Shift** + **]**<br /><br /> -或-<br /><br /> **Shift** + **Ctrl** + **向右箭頭**|將繪圖背景色彩變更成下一個調色盤色彩。|
|Image.OutlinedEllipseTool|**Shift** + **Alt** + **P**|繪製出帶外框的實心橢圓形。|
|Image.OutlinedRectangleTool|**Shift** + **Alt** + **R**|繪製出帶外框的實心矩形|
|Image.OutlinedRoundRectangleTool|**Shift** + **Alt** + **W**|繪製出帶外框的實心圓角矩形。|
|Image.PencilTool|**Ctrl** + **I**|使用單像素鉛筆繪製。|
|Image.PreviousColor|**Ctrl** + **[**<br /><br /> -或-<br /><br /> **Ctrl** + **向左鍵**|將繪圖前景色彩變更成前一個調色盤色彩。|
|Image.PreviousRightColor|**Ctrl** + **Shift** + **[**<br /><br /> -或-<br /><br /> **Shift** + **Ctrl** + **向左鍵**|將繪圖背景色彩變更成前一個調色盤色彩。|
|Image.RectangleSelectionTool|**Shift** + **Alt** + **S**|選取要移動、 複製或編輯之影像的矩形部分。|
|Image.RectangleTool|ATL + R|繪製矩形，以使用選取的線條寬度和色彩。|
|Image.Rotate90Degrees|**Ctrl** + **Shift** + **H**|旋轉影像或選取範圍 90 度。|
|Image.RoundedRectangleTool|**Alt** + **W**|繪製以選取的線條寬度和色彩的圓角矩形。|
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|切換像素格線 (選取或清除**像素格線**選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|
|Image.ShowTileGrid|**Ctrl** + **Shift** + **Alt** + **S**|切換磚狀格線 (選取或清除**磚狀格線**選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|
|Image.SmallBrush|**Ctrl** + **.** （句點）|減少**筆刷**一個像素大小。 (請參閱本表中的 Image.LargerBrush 和 Image.SmallerBrush)。|
|Image.SmallerBrush|**Ctrl**  +  **-** （減號）|在每一個方向上減少一個像素的筆刷大小。 若要再次擴充筆刷的大小，請參閱本表格中的 Image.LargerBrush。|
|Image.TextTool|**Ctrl** + **T**|會開啟[文字工具對話方塊](../windows/text-tool-dialog-box-image-editor-for-icons.md)。|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|使用目前選取的範圍做為筆刷繪製。|
|Image.ZoomIn|**Ctrl** + **Shift** + **。** （句點）<br /><br /> -或-<br /><br /> **Ctrl** + **向上鍵**|增加目前檢視的縮放比例。|
|Image.ZoomOut|**Ctrl** + **，** （逗號）<br /><br /> -或-<br /><br /> **Ctrl** + **向下箭號**|降低目前檢視的縮放比率|

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)