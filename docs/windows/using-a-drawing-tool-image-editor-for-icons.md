---
title: HOW TO：使用繪圖工具
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
ms.openlocfilehash: 7b362749c9a5cb1c7ec77e5cac8625aa7eb260f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037785"
---
# <a name="how-to-use-a-drawing-tool"></a>HOW TO：使用繪圖工具

**影像編輯器**徒手畫的繪圖和清除所有運作方式仍相同的工具。 您選取的工具，而如果有必要，請[選取前景和背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)和大小和形狀的選項。 然後將指標移至映像並按一下或拖曳來繪製及清除。

## <a name="drawing-tools"></a>繪圖工具

您可以選取繪圖工具**影像編輯器**工具列或**映像**功能表。 當您選取**橡皮擦**工具**筆刷**工具，或**噴槍**選項選取器 工具，會顯示該工具的選項。

> [!TIP]
>  當您將游標停留在按鈕上時，會出現工具提示[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)。 這些提示可幫助您識別以下提及的按鈕。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>選取並使用提供的影像編輯器 工具列上的繪圖工具

1. 在 [選取] 按鈕**影像編輯器**工具列。

   - **橡皮擦**工具內目前的背景色彩與影像的繪製，當您按下滑鼠左的按鈕。

      > [!TIP]
      > 而不是使用**橡皮擦**工具，您可能會發現它更方便地與其中一個繪圖工具的背景色彩繪製。

   - **鉛筆**工具手繪繪製一個像素的固定寬度。

   - **筆刷**工具有各種形狀和大小。

   - **噴槍**工具隨機色彩周圍散佈像素的筆刷的中心。

1. 如有必要，選取 色彩和筆刷：

   - 在 [色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，選取 選取前景色彩的滑鼠左的按鈕或滑鼠右鍵以選取 背景色彩。

   - 在 [選項選取器](../windows/toolbar-image-editor-for-icons.md)，選取代表您想要使用的筆刷的形狀。

1. 指向您要在繪製的影像上繪製位置。 根據您所選取的工具指標變更形狀。

1. 按下滑鼠左的按鈕 （適用於的前景色彩） 或 （適用於背景色彩），以滑鼠右鍵按鈕並按住不動做為您繪製。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>選取並使用 [影像] 功能表的繪圖工具

1. 移至功能表**映像** > **工具**。

1. 在階層式 子功能表中，選擇您想要使用的工具。

## <a name="lines-or-closed-figures"></a>線條或封閉的圖形

**影像編輯器**繪製線條和封閉的圖形所有工具運作方式相同： 您將插入點放在一個點，並拖曳到另一個。 線條，這些點會是端點。 封閉圖形，這些點會是相反的邊角的矩形。

寬度取決於目前的筆刷選取範圍，以繪製線條，而且已框架處理的數字會繪製取決於目前的寬度選取範圍的寬度。 線條和所有數字，做為外框和填滿，會繪製在目前的前景色彩如果按下滑鼠左的按鈕，或目前的背景色彩如果按下滑鼠右按鈕。

### <a name="to-draw-a-line"></a>若要繪製一條線

1. 使用[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)，或移至功能表**映像**> **工具**，然後選擇 [**列**工具。

1. 如有必要，選取 色彩和筆刷：

   - 在 [色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，選取 選取前景色彩的滑鼠左的按鈕或滑鼠右鍵以選取 背景色彩。

   - 在 [選項選取器](../windows/toolbar-image-editor-for-icons.md)，選取代表您想要使用的筆刷的形狀。

1. 將指標放在直線的起點。

1. 拖曳以直線的端點。

### <a name="to-draw-a-closed-figure"></a>若要繪製封閉的圖表

1. 使用**影像編輯器**工具列或功能表前往**映像** > **工具**，然後選取**封閉圖形繪製**工具。

   **封閉圖形繪製**工具建立圖形，在其個別的按鈕上所示。

1. 如有必要，選取 色彩和線條寬度。

1. 將指標移至您要在其中繪製圖表的矩形區域的其中一個角落。

1. 將指標拖曳至 對角的角落。

## <a name="custom-brushes"></a>自訂筆刷

自訂筆刷是您挑選並使用類似的其中一個映像的矩形部分**影像編輯器**的現成的筆刷。 您可以在 選取項目執行的所有作業，您可以都執行以及自訂筆刷。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要建立自訂筆刷從映像的一部分

1. 選取您想要使用的筆刷的映像的一部分。

1. 保存**Shift**向下鍵，選取範圍中選擇和拖曳影像，或移至功能表**映像** > **將選取範圍當做筆刷**。

   您的選取項目會成為自訂筆刷可將選取範圍中的色彩分散到映像。 選取範圍的複本會保留在拖曳的路徑。 您將拖曳的速度變慢，進行更多的複本。

   > [!NOTE]
   > 選取**使用選取範圍當做筆刷**沒有先選取影像的部分會使用整個映像當做筆刷。 使用自訂筆刷的結果也取決於您是否選取了[不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

在 自訂筆刷符合目前的背景色彩的像素通常是透明： 透過現有的映像，他們不繪製。 您可以變更此行為，使背景色彩的像素蓋過現有的映像。

您可以使用像是戳記或樣板的自訂筆刷來建立不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要繪製自訂筆刷形狀中的背景色彩

1. 選取的不透明或透明背景。

1. 設定您要在其中繪製的色彩的背景色彩。

1. 將自訂的筆刷您要繪製的位置。

1. 選取滑鼠右按鈕。 任何自訂的筆刷的不透明的區域會繪製背景的色彩。

### <a name="to-double-or-halve-the-custom-brush-size"></a>按兩下，或自訂的筆刷的大小則為一半

按下**加號**(**+**) 索引鍵的兩倍筆刷的大小，或有**減號**(**-**) 減半的索引鍵.

### <a name="to-cancel-the-custom-brush"></a>若要取消的自訂筆刷

按下**Esc**或選擇另一個繪圖工具。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[HOW TO：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[HOW TO：編輯映像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[HOW TO：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>