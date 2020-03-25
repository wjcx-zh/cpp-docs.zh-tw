---
title: 如何：使用繪圖工具
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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214379"
---
# <a name="how-to-use-a-drawing-tool"></a>如何：使用繪圖工具

**影像編輯器**具有手繪的圖形和抹除工具，全都以相同的方式工作。 您可以選取工具，並視需要[選取 [前景和背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)] 和 [大小和形狀選項]。 接著，您可以將指標移至影像，然後按一下或拖曳來繪製和清除。

## <a name="drawing-tools"></a>繪圖工具

您可以從 [**影像編輯器**] 工具列或 [**影像**] 功能表中選取 [繪製工具]。 當您選取 [**橡皮擦**工具]、[**筆刷**工具] 或 [**噴槍**] 工具時，選項選取器會顯示該工具的選項。

> [!TIP]
>  當您將游標移到 [[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)上的按鈕上方時，就會出現工具提示。 這些秘訣可協助您識別這裡所述的特定按鈕。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>若要從影像編輯器工具列選取並使用繪圖工具

1. 選取 [**影像編輯器**] 工具列上的按鈕。

   - 當您按下滑鼠左鍵時，**橡皮擦**工具會以目前的背景色彩在影像上繪製。

      > [!TIP]
      > 不使用**橡皮擦**工具，您可能會發現使用其中一種繪圖工具以背景色彩繪製會比較方便。

   - **鉛筆**工具會以一個圖元的常數寬度繪製手繪。

   - **筆刷**工具具有各種不同的形狀和大小。

   - **噴槍**工具會在筆刷的中央隨機分配色彩圖元。

1. 如有必要，請選取 [色彩] 和 [筆刷]：

   - 在 [[色彩] 調色板](../windows/colors-window-image-editor-for-icons.md)中，選取滑鼠左鍵以選取前景色彩，或使用滑鼠右鍵選取背景色彩。

   - 在 [[選項] 選取器](../windows/toolbar-image-editor-for-icons.md)中，選取代表您要使用之筆刷的圖形。

1. 指向影像上您想要開始繪製或繪製的位置。 指標會根據您選取的工具變更圖形。

1. 按下滑鼠左鍵（針對前景色彩）或滑鼠右鍵（針對背景色彩），並在繪製時按住此按鈕。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>若要從 [影像] 功能表選取並使用繪圖工具

1. 移至 功能表 **影像** > **工具**。

1. 在串聯式子功能表上，選擇您想要使用的工具。

## <a name="lines-or-closed-figures"></a>線條或封閉的圖形

用於繪製線條和封閉圖形的**影像編輯器**工具，全都以相同的方式執行：您將插入點放在某個點，然後拖曳至另一個位置。 就行而言，這些點都是端點。 針對已關閉的圖形，這些點是矩形周框的相反角落。

線條會以目前筆刷選取範圍所決定的寬度繪製，而框住的圖形則會以目前寬度選取範圍所決定的寬度繪製。 如果您按下滑鼠左鍵，或在目前的背景色彩中，按下滑鼠右鍵，就會以目前的前景色彩繪製線條和所有圖形。

### <a name="to-draw-a-line"></a>繪製線條

1. 使用 [[影像編輯器 工具列](../windows/toolbar-image-editor-for-icons.md)或 [移至功能表**影像**]> **工具**]，然後選擇 [**線條**] 工具。

1. 如有必要，請選取 [色彩] 和 [筆刷]：

   - 在 [[色彩] 調色板](../windows/colors-window-image-editor-for-icons.md)中，選取滑鼠左鍵以選取前景色彩，或使用滑鼠右鍵選取背景色彩。

   - 在 [[選項] 選取器](../windows/toolbar-image-editor-for-icons.md)中，選取代表您要使用之筆刷的圖形。

1. 將指標放在行的起始點。

1. 將拖曳至線條的端點。

### <a name="to-draw-a-closed-figure"></a>繪製封閉的圖形

1. 使用 **影像編輯器** 工具列或 移至功能表**影像** > **工具**，然後選取 **封閉圖形** 工具。

   「**封閉圖形**」工具會依照其各自按鈕的指示來建立圖形。

1. 如有必要，請選取 [色彩] 和 [線條寬度]。

1. 將指標移至您要繪製圖形之矩形區域的一個角落。

1. 將指標拖曳至對角的邊角。

## <a name="custom-brushes"></a>自訂筆刷

自訂筆刷是指影像的矩形部分，您可以在其中一個**影像編輯器**的現成筆刷中取得和使用。 您可以在選取範圍上執行的所有作業，也可以對自訂筆刷執行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>從影像的一部分建立自訂筆刷

1. 選取您要用於筆刷的影像部分。

1. 按住**Shift**鍵，選擇選取範圍並將其拖曳到影像中，或移至功能表**影像** > **使用選取專案做為筆刷**。

   您的選取專案會成為自訂筆刷，可將選取範圍中的色彩分散到影像中。 選取的複本會沿著拖曳路徑向左。 拖曳的速度愈慢，就會產生更多的複本。

   > [!NOTE]
   > 選取 [**使用選取專案做為筆刷**] 而不先選取影像的一部分，將會使用整個影像做為筆刷。 使用自訂筆刷的結果也會取決於您選取的是不[透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

自訂筆刷中符合目前背景色彩的圖元通常是透明的：它們不會在現有的影像上繪製。 您可以變更此行為，讓背景色彩圖元在現有影像上繪製。

您可以使用自訂筆刷（例如戳記或樣板）來建立不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要以背景色彩繪製自訂筆刷圖形

1. 選取不透明或透明背景。

1. 將背景色彩設為您要繪製的色彩。

1. 將自訂筆刷放在您想要繪製的位置。

1. 選取滑鼠右鍵。 自訂筆刷的任何不透明區域都會以背景色彩繪製。

### <a name="to-double-or-halve-the-custom-brush-size"></a>若要加倍或可以藉減半自訂筆刷大小

按下正負**號**（ **+** ）鍵，以將筆刷大小或**減號**（ **-** ）按鍵可以藉減半。

### <a name="to-cancel-the-custom-brush"></a>取消自訂筆刷

按**Esc**或選擇另一個繪圖工具。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
