---
title: 如何:使用繪圖工具
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359846"
---
# <a name="how-to-use-a-drawing-tool"></a>如何:使用繪圖工具

**圖像編輯器**具有徒手繪圖和可重複使用的工具,這些工具的工作方式相同。 選擇該工具,並在必要時[選擇前景和背景顏色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)以及大小和形狀選項。 然後,將指標移動到圖像,然後單擊或拖動以繪製和擦除。

## <a name="drawing-tools"></a>繪圖工具

您可以從 **「影像編輯器」** 工具列或 **「圖像」** 選單選擇繪圖工具。 當您選擇**橡皮擦**工具、**畫筆**工具或**噴槍**工具時,選項選擇器將顯示該工具的選項。

> [!TIP]
> 將游標懸停在[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)上的按鈕上時,將顯示工具提示。 這些提示將幫助您確定此處提及的特定按鈕。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>從影像編輯器工具列中選擇與使用繪圖工具

1. 在**影像編輯器工具**列上選擇按鈕。

   - 按下滑鼠左鍵時,「**橡皮擦」** 工具使用當前背景顏色在圖像上繪製。

      > [!TIP]
      > 您可以使用其中一個繪圖工具在背景顏色中繪製,而不是使用**橡皮擦**工具。

   - **鉛筆**工具以一個圖元的恆定寬度徒手繪製。

   - **畫筆**工具具有各種形狀和大小。

   - **噴槍**工具隨機分佈畫筆中心周圍的顏色圖元。

1. 如有必要,請選擇顏色和畫筆:

   - 在["顏色"調色板](../windows/colors-window-image-editor-for-icons.md)中,選擇滑鼠左鍵以選擇前景顏色或滑鼠右鍵以選擇背景顏色。

   - 在[選項選擇器](../windows/toolbar-image-editor-for-icons.md)中,選擇表示要使用的筆刷筆的形狀。

1. 指向要開始繪製或繪畫的圖像上的位置。 指標會根據您選擇的工具更改形狀。

1. 按滑鼠左鍵(對於前景顏色)或滑鼠右鍵(對於背景顏色),並在繪製時按住它。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>從影像選單中選擇與使用繪圖工具

1. 跳到選單**影像** > **工具**。

1. 在級聯子功能表上,選擇要使用的工具。

## <a name="lines-or-closed-figures"></a>線或封閉數字

用於繪製線條和閉合圖形**的圖像編輯器**工具的工作方式都相同:將插入點放在一個點,然後拖動到另一個點。 對於行,這些點是端點。 對於閉合圖,這些點是與圖形相界的矩形的相反角。

線條以當前畫筆選擇確定的寬度繪製,框架圖形以當前寬度選擇確定的寬度繪製。 如果按滑鼠左鍵,則線條和所有圖形(框架和填充)以當前前景顏色繪製,如果按右滑鼠按鈕,則以當前背景顏色繪製。

### <a name="to-draw-a-line"></a>繪製線條

1. 使用[影像編輯器'工具列](../windows/toolbar-image-editor-for-icons.md)或轉到'**影像**> **工具**"選單並選擇 **'工具"** 工具。

1. 如有必要,請選擇顏色和畫筆:

   - 在["顏色"調色板](../windows/colors-window-image-editor-for-icons.md)中,選擇滑鼠左鍵以選擇前景顏色或滑鼠右鍵以選擇背景顏色。

   - 在[選項選擇器](../windows/toolbar-image-editor-for-icons.md)中,選擇表示要使用的筆刷筆的形狀。

1. 將指標放在線的起始點。

1. 拖動到行的終結點。

### <a name="to-draw-a-closed-figure"></a>繪製封閉

1. 使用**影像編輯器工具**列或轉**到圖像** > **工具**功能選單並選擇 **「閉合圖形繪圖**」工具。

   **"閉合圖"繪圖**工具可按其各自按鈕上所示創建圖形。

1. 如有必要,選擇顏色和線條寬度。

1. 將指標移動到要繪製圖形的矩形區域的一個角。

1. 將指標拖動到對角對角。

## <a name="custom-brushes"></a>自訂筆刷

自定義畫筆是圖像的矩形部分,您像**圖像編輯器**的現成畫筆一樣拾取和使用。 您可以對所選內容執行所有操作,也可以在自定義畫筆上執行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>從影像的一部分建立自訂筆刷

1. 選擇要用於畫筆的圖像部分。

1. 按住**Shift**鍵,在選擇中選擇並將其拖動到圖像中,或轉到菜單 **「圖像** > **使用選擇作為畫筆**」。

   您的選擇將成為自定義畫筆,用於在整個圖像中分佈所選內容中的顏色。 所選內容的副本沿拖動路徑保留。 拖動得越慢,製作的副本就越多。

   > [!NOTE]
   > 選擇「**使用選擇作為畫筆**,而不首先選擇影像的一部分」將使用整個影像作為畫筆。 使用自訂筆的結果還取決於您選擇了[「不透明」或「透明」背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

自定義筆式與當前背景顏色匹配的圖元通常透明:它們不在現有圖像上繪製。 您可以更改此行為,以便背景色像素在現有圖像上繪製。

您可以使用自定義畫筆(如圖章或模具)來創建不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>以背景顏色繪製自訂筆形狀

1. 選擇不透明或透明背景。

1. 將背景顏色設定為要繪製的顏色。

1. 將自定義畫筆放置在要繪製的位置。

1. 選擇滑鼠右鍵。 自定義畫筆的任何不透明區域都以背景顏色繪製。

### <a name="to-double-or-halve-the-custom-brush-size"></a>讓自訂筆大小翻倍或減半

按**加號**(**+**) 鍵將畫筆大小翻倍,或按**減號**(**-**) 鍵將其減半。

### <a name="to-cancel-the-custom-brush"></a>取消自訂筆刷

按**Esc**或選擇其他繪圖工具。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何:建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何:編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何:使用顏色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[加速器鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
