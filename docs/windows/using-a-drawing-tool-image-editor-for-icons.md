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
ms.openlocfilehash: 46ba1f1057484f2b5b1e1286482d80fd96312caf
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502926"
---
# <a name="how-to-use-a-drawing-tool"></a>如何：使用繪圖工具

**影像編輯器**中的繪圖和清除工具都是以相同的方式運作。 您可以選取工具，如有必要，請 [選取前景和背景色彩](./image-editor-for-icons.md) ，以及大小和圖形選項。 然後，將指標移至影像，然後按一下或拖曳以進行繪製和清除。

## <a name="drawing-tools"></a>繪圖工具

您可以從 [ **影像編輯器** ] 工具列或 [ **影像** ] 功能表選取 [繪圖工具]。 當您選取 **橡皮擦** 工具、 **筆刷** 工具或 **噴槍** 工具時，選項選取器會顯示該工具的選項。

> [!TIP]
> 當您將游標停留在 [ [影像編輯器] 工具列](./image-editor-for-icons.md)上的按鈕上時，就會出現工具提示。 這些秘訣可協助您識別此處所述的特定按鈕。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>若要從影像編輯器工具列選取和使用繪圖工具

1. 選取 [ **影像編輯器** ] 工具列上的按鈕。

   - 當您按下滑鼠左鍵時， **橡皮擦** 工具會使用目前的背景色彩來繪製影像。

      > [!TIP]
      > 與其使用 **橡皮擦** 工具，您可能會發現，使用其中一個繪圖工具以背景色彩繪製會更方便。

   - **鉛筆**工具會以一個圖元的常數寬度繪製手繪。

   - **筆刷**工具具有各種不同的形狀和大小。

   - **噴槍**工具會在筆刷中央隨機分配色彩圖元。

1. 如有必要，請選取色彩和筆刷：

   - 在 [ [色彩](./image-editor-for-icons.md)選擇區] 中，選取滑鼠左鍵選取前景色彩，或選取滑鼠右鍵以選取背景色彩。

   - 在 [ [選項選取器](./image-editor-for-icons.md)] 中，選取代表您要使用之筆刷的圖形。

1. 指向影像上您想要開始繪製或繪製的位置。 指標會根據您選取的工具而變更圖形。

1. 按下滑鼠左鍵 (的前景色彩) 或滑鼠右鍵 (的背景色彩) ，然後在繪製時按住滑鼠左鍵。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>從 [影像] 功能表選取並使用繪圖工具

1. 移至功能表**影像**  >  **工具**。

1. 在串聯式子功能表上，選擇您想要使用的工具。

## <a name="lines-or-closed-figures"></a>線條或封閉圖形

用來繪製線條和封閉圖的 **影像編輯器** 工具都是以相同的方式運作：將插入點放在某個點，然後拖曳到另一個點。 若為線條，這些點即為端點。 對於封閉的圖形而言，這些點是圖形周框的相對角落。

線條是以目前的筆刷選取範圍所決定的寬度繪製，而框架圖形則是以目前寬度選取範圍所決定的寬度繪製。 如果您按下滑鼠左鍵，以目前的前景色彩繪製線條和所有圖形，如果按下滑鼠右鍵，則會以目前的背景色彩繪製。

### <a name="to-draw-a-line"></a>繪製線條

1. 使用 [[影像編輯器] 工具列](./image-editor-for-icons.md)或 [移至] 功能表**影像** >  **工具**，然後選擇 [**線條**] 工具。

1. 如有必要，請選取色彩和筆刷：

   - 在 [ [色彩](./image-editor-for-icons.md)選擇區] 中，選取滑鼠左鍵選取前景色彩，或選取滑鼠右鍵以選取背景色彩。

   - 在 [ [選項選取器](./image-editor-for-icons.md)] 中，選取代表您要使用之筆刷的圖形。

1. 將指標放在行的起點。

1. 拖曳至該行的端點。

### <a name="to-draw-a-closed-figure"></a>繪製封閉的圖形

1. 使用 [**影像編輯器**] 工具列或 [移至] 功能表**影像**  >  **工具**，然後選取**封閉的繪圖**工具。

   **封閉的繪圖**工具會建立其各自按鈕上所指出的圖形。

1. 如有必要，請選取 [色彩] 和 [線條寬度]。

1. 將指標移至您要在其中繪製圖的矩形區域的一個角落。

1. 將指標拖曳至對角的邊角。

## <a name="custom-brushes"></a>自訂筆刷

自訂筆刷是您所挑選影像的矩形部分，並如同 **影像編輯器**的其中一個現成筆刷一樣使用。 您可以在選取專案上執行的所有作業，也可以在自訂筆刷上執行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>從影像的一部分建立自訂筆刷

1. 選取您要用於筆刷的影像部分。

1. 按住**Shift**鍵，選擇選取範圍，然後將它拖曳到影像上，或移至功能表**影像**  >  **使用選取專案作為筆刷**。

   您的選取範圍會成為自訂筆刷，可將選取範圍內的色彩分散至影像。 選取專案的複本會保留在拖曳路徑中。 您拖曳的速度愈慢，就會產生更多的複本。

   > [!NOTE]
   > 選取 [ **使用選取專案作為筆刷** ]，但不先選取影像的一部分，將會使用整個影像作為筆刷。 使用自訂筆刷的結果也會取決於您選取的是不 [透明或透明背景](./image-editor-for-icons.md)。

自訂筆刷中符合目前背景色彩的圖元通常是透明的：它們不會在現有影像上繪製。 您可以變更此行為，讓背景色彩圖元可以在現有影像上進行繪製。

您可以使用自訂筆刷（例如戳記或樣板）來建立不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>在背景色彩中繪製自訂筆刷形狀

1. 選取不透明或透明背景。

1. 將背景色彩設定為您想要繪製的色彩。

1. 將自訂筆刷放在您想要繪製的位置。

1. 選取滑鼠右鍵。 自訂筆刷的任何不透明區域都會以背景色彩繪製。

### <a name="to-double-or-halve-the-custom-brush-size"></a>若要加倍或可以藉減半自訂筆刷大小

按 **加號** (**+**) 鍵以將筆刷大小加倍，或按 **減號** () 索引 **-** 鍵來可以藉減半它。

### <a name="to-cancel-the-custom-brush"></a>取消自訂筆刷

按下 **Esc** 鍵或選擇其他繪圖工具。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[How to：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
