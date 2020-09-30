---
title: 如何：使用色彩
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
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
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: 3c9134fde9053f57f8848a37b1442728f6111c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502945"
---
# <a name="how-to-work-with-color"></a>如何：使用色彩

**影像編輯器**包含許多專門處理和自訂色彩的功能。 您可以設定前景或背景色彩、以色彩填滿系結區域，或選取影像上的色彩以做為目前的前景或背景色彩。 您可以使用 [ [影像編輯器] 工具列](./image-editor-for-icons.md) 上的工具，以及 [ **色彩** ] 視窗中的 [色彩] 選擇區來建立影像。

單色和16色影像的所有色彩會顯示**在 [色彩] 視窗**的 [**色彩**選擇區] 中。 除了16種標準色彩，您還可以建立自己的自訂色彩。 變更調色板中的任何色彩，會立即變更影像中的對應色彩。

使用256色彩圖示和游標影像時，會使用[屬性視窗](/visualstudio/ide/reference/properties-window)中的 [**色彩**] 屬性。 如需詳細資訊，請參閱 [建立256色彩圖示或游標](./creating-an-icon-or-other-image-image-editor-for-icons.md)。

True-也可以建立色彩影像。 不過，[ **色彩** ] 視窗的完整調色板中不會出現 true 色彩範例;它們只會出現在前景或背景色彩指標區域中。 您可以使用 [ **自訂色彩選取器** ] 對話方塊來建立真正的色彩。

您可以將自訂顏色調色板儲存在磁片上，並視需要重載。 您最近使用的色彩調色板會儲存在登錄中，並在您下次開始 Visual Studio 時自動載入。

[ **色彩** ] 視窗有兩個部分：

- 色彩 **選擇區，這**是代表您可以使用之色彩的色彩範例陣列。 當您使用圖形工具時，可以選取範例來選擇前景和背景色彩。

- **色彩指標**，顯示幕幕和反向色彩的前景和背景色彩和選取器。

   ![色彩視窗](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **色彩** 視窗

> [!NOTE]
> **螢幕色彩**和**反色**工具僅適用于圖示和資料指標。

您可以使用 [ **色彩** ] 視窗搭配 [ [影像編輯器] 工具列](./image-editor-for-icons.md)。

- 若要顯示 [**色彩**] 視窗，請在 [**影像編輯器**] 窗格中按一下滑鼠右鍵，然後選擇 [**顯示色彩視窗]**，或移至 [功能表[影像](./image-editor-for-icons.md)  >  **顯示色彩] 視窗**。

- 若要隱藏 [ **色彩** ] 視窗，請將視窗取消釘選 (此動作可讓視窗在不使用時自動隱藏) 或選取 [ **關閉** ] 按鈕。

[ **色彩** ] 調色板一開始會顯示16個標準色彩。 使用顯示的色彩，您也可以建立自己的自訂色彩。 然後，您可以儲存及載入自訂的調色盤。

[ **自訂色彩選取器** ] 對話方塊可讓您使用下列屬性為影像自訂色彩：

|屬性|描述|
|--------------------------|--------------------------|
|**漸層色彩顯示**|變更所選色彩的值。<br/><br/>將十字線定位至您要變更的色彩，並將滑杆向上或向下移動，以變更色彩的亮度或 RGB 值。|
|**亮度列**|針對您在 [漸層 **色彩顯示** ] 方塊中選取的色彩設定亮度。<br/><br/>選取並拖曳白色箭號，以取得更高的亮度或更低的亮度。 [ **色彩** ] 方塊會顯示您所選取的色彩，以及您設定的亮度效果。|
|**色彩**|列出您所定義色彩 (色彩滾輪值) 的色調。 值的範圍是從0到240，其中0為紅色、60為黃色、120為綠色、180為青色、200為洋紅，而240為藍色。|
|**Hue**|列出您所定義色彩 (色彩滾輪值) 的色調。 值的範圍是從0到240，其中0為紅色、60為黃色、120為綠色、180為青色、200為洋紅，而240為藍色。|
|**濃度**|指定您要定義之色彩的飽和度值。 飽和度是指定之色調的色彩數量。 值的範圍是從0到240。|
|**亮度**|列出您所定義色彩的亮度 (亮度) 。 值的範圍是從0到240。|
|**紅色**|指定您要定義之色彩的紅色值。 值的範圍是從0到255。|
|**綠色**|指定您要定義之色彩的綠色值。 值的範圍是從0到255。|
|**藍色**|指定您要定義之色彩的藍色值。 值的範圍是從0到255。|

您可以儲存和載入包含自訂色彩的 **色彩** 選擇區。 依預設，當您開始 Visual Studio 時，會自動載入最近使用的 **色彩** 選擇區。

> [!TIP]
> 由於**影像編輯器**沒有還原預設**色彩**選擇區的方法，因此您應該將預設**色彩**選擇區儲存在名稱（例如*standard pal*或 default.aspx） *default.pal*下，如此您就可以輕鬆地還原預設設定。

使用 [ **載入** 選擇區色彩] 對話方塊，載入要在 c + + 專案中使用下列屬性的特殊調色板：

|屬性|描述|
|-----------------|-----------------|
|**Look in**|指定您要尋找檔案或資料夾的位置。<br/><br/>選取箭號以選擇另一個位置，或選取工具列上的資料夾圖示來向上移動層級。|
|**檔案名稱**|提供空間讓您輸入要開啟的檔案名。<br/><br/>若要快速尋找您先前開啟的檔案，請在下拉式清單中選取檔案名（如果有的話）。<br/><br/>如果您要搜尋檔案，您可以使用星號 ( * ) 作為萬用字元。 例如，您可以輸入， \* \* 以查看所有檔案的清單。 您也可以輸入檔案的完整路徑，例如*C:\My Documents\MyColorPalette.pal*或* \\ \NetworkServer\MyFolder\MyColorPalette.pal*。|
|[檔案類型]****|列出要顯示的檔案類型。<br/><br/>調色板 ( * pal) 是調色板的預設檔案類型。|

## <a name="how-to"></a>作法

### <a name="to-select-foreground-or-background-colors"></a>選取前景或背景色彩

除了 **橡皮擦**以外，[ **影像編輯器** ] 工具列上的工具會在您分別按下滑鼠左鍵或右鍵時，使用目前的前景或背景色彩來繪製。

- 若要選取前景色彩，請使用滑鼠左鍵，在 [ **色彩** 選擇區] 中選取您想要的色彩。

- 若要選取具有滑鼠右鍵的背景色彩，請在 [ **色彩** 選擇區] 中選取您想要的色彩。

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>使用色彩填滿影像的限定區域

**影像編輯器**會提供**填滿**工具，以使用目前的繪圖色彩或目前的背景色彩來填滿任何封閉的影像區域。

### <a name="to-use-the-fill-tool"></a>使用填滿工具

1. 使用 [**影像編輯器**] 工具列或 [移至] 功能表**影像**  >  **工具**，然後選取 [**填滿**] 工具。

1. 如有必要，請選擇 [繪製色彩]。 在 [ [色彩](./image-editor-for-icons.md)選擇區] 中，選取滑鼠左鍵選取前景色彩，或選取滑鼠右鍵以選取背景色彩。

1. 將 [ **填滿** ] 工具移至您要填滿的區域。

1. 選取左右滑鼠左鍵，分別填入前景色彩或背景色彩。

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>從影像中挑選要在其他位置使用的色彩

[ **選取色彩**] 或 [色彩取貨] 工具會根據您是否按下滑鼠左鍵或滑鼠右鍵，讓影像上的任何色彩成為目前的前景色彩或背景色彩。 若要取消 [ **選取色彩** ] 工具，請選擇另一個工具。

1. 使用 [**影像編輯器**] 工具列或 [移至] 功能表**影像**  >  **工具**，然後選取 [**選取色彩**] 工具。

1. 選取您要從影像中挑選的色彩。

   > [!NOTE]
   > 在您挑選色彩之後， **影像編輯器** 會重新開機最近使用的工具。

1. 使用滑鼠左鍵來繪製前景色彩，或使用滑鼠右鍵作為背景色彩。

### <a name="to-choose-the-background"></a>選擇背景

當您移動或複製影像中的選取專案時，選取範圍中符合目前背景色彩的任何圖元預設都是透明的，而且不會在目標位置中混淆圖元。

您可以從透明背景切換 (預設) 為不透明的背景，然後再切換回來。 當您使用 [選取] 工具時，[**影像編輯器**] 工具列上的**選項**選取器中會顯示**透明背景**和不**透明的背景**選項。

![背景選項 &#45; 不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "背景選項 &#45; 不透明或透明")<br/>
**影像編輯器工具列**上的**透明和不透明選項**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>在透明和不透明背景之間切換

在 [ **影像編輯器** ] 工具列上，選取 **選項** 選取器，然後選擇適當的背景：

- 不**透明的背景 (O) **：選取專案的所有部分都會遮蔽現有的影像。

- **透明背景 (T) **：現有的影像會顯示符合目前背景色彩之選取範圍的部分。

> [!TIP]
> 針對快速鍵，請在 [ **影像** ] 功能表上選取或清除 [ **繪製不透明**]。

您可以變更背景色彩，同時選取的效果會變更影像的哪些部分是透明的。

### <a name="to-invert-the-colors-in-a-selection"></a>若要反轉選取範圍中的色彩

**影像編輯器**提供一個便利的方式，讓您在影像的選取部分中反轉色彩，讓您可以分辨影像如何以反轉的色彩顯示。

若要在目前的選取範圍中反轉色彩，請移至功能表**影像**的  >  **色彩**。

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>自訂或變更色彩調色板上的色彩

1. 移至功能表**影像**  >  **調整色彩**。

1. 在 [ **自訂色彩選取器** ] 對話方塊中，于適當的文字方塊中輸入 RGB 或 HSL 值來定義色彩，或在 [漸層 **色彩顯示** ] 方塊中選擇色彩。

1. 藉由移動 **亮度** 列上的滑杆來設定亮度。

1. 許多自訂色彩會被遞色。 如果您想要最接近遞色色彩的純色，請按兩下 [ **色彩** ] 方塊。

   如果您稍後決定要遞色色彩，請移動 **亮度** 列上的滑杆，或再次移動漸層 **色彩顯示** 方塊中的交叉線，以還原遞色。

1. 選取 **[確定]** 以新增新的色彩。

### <a name="to-save-a-custom-colors-palette"></a>若要儲存自訂色彩調色盤

1. 移至功能表**影像**  >  **儲存調色板**。

1. 瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。

1. 選取 [儲存]。

### <a name="to-load-a-custom-colors-palette"></a>若要載入自訂色彩調色盤

1. 移至 [功能表**影像**  >  **載入元件**]。

1. 在 [ **載入色彩** 選擇區] 對話方塊中，流覽至正確的目錄，然後選取您要載入的調色板。 **色彩** 調色板會以 pal 副檔名儲存。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[How to：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
