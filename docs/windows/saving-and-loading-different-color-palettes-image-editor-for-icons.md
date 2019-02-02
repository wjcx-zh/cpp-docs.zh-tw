---
title: 儲存及載入不同的調色盤 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560266"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>儲存及載入不同的調色盤 (圖示影像編輯器)

您可以儲存及載入**色彩**包含色板[自訂色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。 (根據預設，**色彩**啟動 Visual Studio 時，會自動載入最近使用的調色盤。)

> [!TIP]
> 由於**映像**編輯器沒有任何方法來還原預設**色彩**調色盤，您應該儲存預設**色彩**調色盤的名稱，例如*以 standard.pal*或是*default.pal*以便您可以輕易地還原預設設定。

使用 **載入調色盤色彩**載入特殊的調色盤，以便在 c + + 專案中使用的對話方塊。 會包含下列屬性：

|屬性|描述|
|---|---|
|**查看**|指定您想要用來尋找檔案或資料夾的位置。 選取箭頭以選擇其他位置，或選取 [移至上一層] 工具列上的資料夾圖示。|
|**檔案名稱**|提供空間讓您輸入您想要開啟的檔案名稱。 若要快速尋找您先前已開啟的檔案，如果有的話，在下拉式清單中，選取的檔案名稱。<br/><br/>如果您要搜尋的檔案，您可以使用星號 （*） 做為萬用字元。 例如，您可以輸入\*。\*以查看所有檔案的清單。 您也可以輸入檔案，比方說，C:\My Documents\MyColorPalette.pal 的完整路徑或\\\NetworkServer\MyFolder\MyColorPalette.pal。|
|**檔案類型**|列出要顯示檔案的類型。 調色盤 (*.pal) 是預設的檔案類型的色彩調色盤。|

## <a name="to-save-a-custom-colors-palette"></a>若要儲存自訂色彩調色盤

1. 從**映像**功能表上，選擇**儲存調色盤**。

1. 瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。

1. 選取 [儲存]。

## <a name="to-load-a-custom-colors-palette"></a>若要載入自訂色彩調色盤

1. 從**映像**功能表上，選擇**載入調色盤**。

1. 在 **載入色彩調色盤**對話方塊方塊中，瀏覽至正確的目錄，然後選取您想要載入的調色盤。 **色彩**調色盤會以.pal 副檔名儲存。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)