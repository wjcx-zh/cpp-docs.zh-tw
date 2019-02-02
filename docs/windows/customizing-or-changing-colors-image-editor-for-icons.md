---
title: 自訂或變更色彩 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560279"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>自訂或變更色彩 (圖示影像編輯器)

**映像**編者[色彩調色盤](../windows/colors-window-image-editor-for-icons.md)一開始會顯示 16 個標準色彩。 顯示色彩，您也可以建立您自己自訂的色彩。 您可以接著[儲存及載入自訂的調色盤](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)。

**自訂色彩選取器**對話方塊可讓您自訂映像您使用的色彩。 會包含下列屬性：

|屬性|描述|
|---|---|
|**漸層色彩顯示**|變更所選取之色彩的值。 您想要變更的位置是色彩十字形狀。 然後移動滑桿向上或向下變更的明暗度或色彩的 RGB 值。|
|**亮度列**|設定您在中選取之色彩的亮度**漸層色彩顯示** 方塊中。 選取並拖曳白色箭號，更高的亮度列向上或向下的鍵小於。 **色彩**方塊會顯示您所選取的色彩和您所設定的明暗度的效果。|
|**Color**|列出您要定義之色彩的色調 （色彩轉輪值）。 值範圍從 0 到 240，其中 0 是紅色、 60 是黃色，120 是綠色、 180 是青色、 200 表示 「 洋紅、 240 是藍色。|
|**Hue**|列出您要定義之色彩的色調 （色彩轉輪值）。 值範圍從 0 到 240，其中 0 是紅色、 60 是黃色，120 是綠色、 180 是青色、 200 表示 「 洋紅、 240 是藍色。|
|**Sat**|指定您要定義之色彩的濃度值。 飽和度是色彩的在指定的色調量。 值範圍從 0 到 240。|
|**Lum**|列出您要定義之色彩的亮度 （亮度）。 值範圍從 0 到 240。|
|**紅色**|指定您要定義之色彩的紅色值。 值範圍從 0 到 255 之間。|
|**綠色**|指定您要定義之色彩的綠色值。 值範圍從 0 到 255 之間。|
|**Blue**|指定您要定義之色彩的藍色值。 值範圍從 0 到 255 之間。|

## <a name="to-change-colors-on-the-colors-palette"></a>變更調色盤上的色彩

1. 從**映像**功能表上，選擇**調整色彩**。

1. 在 [**自訂色彩選取器**對話方塊方塊中，適當的文字方塊中輸入 RGB 或 HSL 值定義的色彩或選擇在色彩**漸層色彩顯示**] 方塊中。

1. 移動滑桿，以設定光度**亮度**列。

1. 許多自訂色彩會被遞色。 如果您想最接近遞色色彩的純色，按兩下**色彩** 方塊中。

   如果您稍後決定要遞色的色彩，移動滑桿**亮度**列，或移動中的交叉線**漸層色彩顯示**方塊，再以還原遞色。

1. 選取 **確定**若要新增新的色彩。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[影像功能表](../windows/image-menu-image-editor-for-icons.md)<br/>
[色彩視窗](../windows/colors-window-image-editor-for-icons.md)