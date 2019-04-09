---
title: HOW TO：使用色彩
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
ms.openlocfilehash: c424d2e613c51f901def13c4bf42a066797cc65c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034140"
---
# <a name="how-to-work-with-color"></a>HOW TO：使用色彩

**影像編輯器**包含許多功能，特別是處理和自訂色彩。 您可以設定前景或背景色彩、 繫結的區域填滿色彩，或選取要做為目前的前景或背景色彩的影像上的色彩。 您可以使用上的工具[影像編輯器 工具列](../windows/toolbar-image-editor-for-icons.md)以及中的色彩調色盤**色彩**視窗建立映像。

所有的色彩，單色和 16 色影像所示**色彩**中的調色盤**色彩**視窗。 16 個標準色彩，以及您可以建立您自己自訂的色彩。 色彩調色盤中的任何變更會立即變更映像中對應的色彩。

當使用 256 色圖示和游標影像**色彩**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)用。 如需詳細資訊，請參閱 <<c0> [ 建立 256 色圖示或游標](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。

也可以建立全彩映像。 不過，則為 true 的色彩範例不會出現在中的完整調色盤**色彩**視窗; 它們只會出現在前景或背景色彩指示器區域。 使用所建立，則為 true 的色彩**自訂色彩選取器** 對話方塊。

您可以儲存在磁碟上的 自訂的色彩調色盤，並視需要重新載入。 您最近使用的色彩調色盤會儲存在登錄中，並自動載入 下一次啟動 Visual Studio。

**色彩**視窗有兩個部分：

- **色彩調色盤**，即表示您可以使用的色彩的色彩範例陣列。 您可以選取當您使用圖形工具，請選擇前景和背景色彩的範例。

- **色彩指示器**，其中顯示的前景和背景色彩和螢幕及反向色彩選取器。

   ![色彩視窗](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **色彩**視窗

> [!NOTE]
> **螢幕色彩**並**反向色彩**工具僅適用於圖示和游標。

您可以使用**色彩**視窗，其中[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)。

- 若要顯示**色彩**] 視窗中，以滑鼠右鍵按一下**影像編輯器**窗格，然後選擇 [**顯示色彩視窗**，或移至功能表[映像](../windows/image-menu-image-editor-for-icons.md) > **顯示色彩視窗**。

- 若要隱藏**色彩** 視窗中，取消釘選 （未使用時，此動作將允許自動隱藏視窗） 視窗，或選取**關閉** 按鈕。

**色彩**調色盤一開始會顯示 16 個標準色彩。 顯示色彩，您也可以建立您自己自訂的色彩。 然後，您可以儲存並載入自訂的調色盤。

**自訂色彩選取器**對話方塊可讓您自訂的色彩，您使用映像具有下列屬性：

|屬性|描述|
|--------------------------|--------------------------|
|**漸層色彩顯示**|變更所選取之色彩的值。<br/><br/>十字形狀放入您想要變更，並向上或向下移動滑桿來變更的亮度或色彩的 RGB 值的色彩。|
|**亮度列**|設定您在中選取之色彩的亮度**漸層色彩顯示** 方塊中。<br/><br/>選取並拖曳白色箭號，更高的亮度列向上或向下的鍵小於。 **色彩**方塊會顯示您所選取的色彩和您所設定的明暗度的效果。|
|**色彩**|列出您要定義之色彩的色調 （色彩轉輪值）。 值範圍從 0 到 240，其中 0 是紅色、 60 是黃色，120 是綠色、 180 是青色、 200 表示 「 洋紅、 240 是藍色。|
|**色調**|列出您要定義之色彩的色調 （色彩轉輪值）。 值範圍從 0 到 240，其中 0 是紅色、 60 是黃色，120 是綠色、 180 是青色、 200 表示 「 洋紅、 240 是藍色。|
|**六**|指定您要定義之色彩的濃度值。 飽和度是色彩的在指定的色調量。 值範圍從 0 到 240。|
|**亮度**|列出您要定義之色彩的亮度 （亮度）。 值範圍從 0 到 240。|
|**紅色**|指定您要定義之色彩的紅色值。 值範圍從 0 到 255 之間。|
|**綠色**|指定您要定義之色彩的綠色值。 值範圍從 0 到 255 之間。|
|**藍色**|指定您要定義之色彩的藍色值。 值範圍從 0 到 255 之間。|

您可以儲存及載入**色彩**包含自訂的色彩的色板。 根據預設，**色彩**啟動 Visual Studio 時，會自動載入最近使用的調色盤。

> [!TIP]
> 由於**影像編輯器**沒有任何方法來還原預設**色彩**調色盤，您應該儲存預設**色彩**調色盤的名稱，例如*以 standard.pal*或是*default.pal*以便您可以輕易地還原預設設定。

使用 **載入調色盤色彩**對話方塊中，將特殊的調色盤，以便使用在 c + + 專案中，使用下列屬性：

|屬性|描述|
|-----------------|-----------------|
|**查詢**|指定您想要用來尋找檔案或資料夾的位置。<br/><br/>選取箭頭以選擇其他位置，或選取 [移至上一層] 工具列上的資料夾圖示。|
|**檔案名稱**|提供空間讓您輸入您想要開啟的檔案名稱。<br/><br/>若要快速尋找您先前已開啟的檔案，如果有的話，在下拉式清單中，選取的檔案名稱。<br/><br/>如果您要搜尋的檔案，您可以使用星號 （*） 做為萬用字元。 例如，您可以輸入\*。\*以查看所有檔案的清單。 您也可以例如輸入檔案的完整路徑*C:\My Documents\MyColorPalette.pal*或是 *\\\NetworkServer\MyFolder\MyColorPalette.pal*。|
|**檔案類型**|列出要顯示檔案的類型。<br/><br/>調色盤 (*.pal) 是預設的檔案類型的色彩調色盤。|

## <a name="how-to"></a>如何

### <a name="to-select-foreground-or-background-colors"></a>若要選取前景或背景色彩

除了**橡皮擦**，在工具**影像編輯器**工具列繪製以目前前景或背景色彩時您分別按滑鼠左鍵或右鍵。

- 若要選取前景色彩，使用滑鼠左鍵，選取 在您想要的色彩**色彩**調色盤。

- 若要選取背景色彩，以滑鼠右鍵，選取 在您想要的色彩**色彩**調色盤。

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>若要使用的色彩填滿影像的封閉的區域

**影像編輯器**提供**填滿**工具以便填滿任何包含與目前的繪圖色彩或目前的背景色彩的影像區域。

### <a name="to-use-the-fill-tool"></a>若要使用的填滿工具

1. 使用**影像編輯器**工具列或功能表前往**映像** > **工具**，然後選取**填滿**工具。

1. 如有必要，請選擇 繪製的色彩。 在 [色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，選取 選取前景色彩的滑鼠左的按鈕或滑鼠右鍵以選取 背景色彩。

1. 移動**填滿**工具，以您想要填滿的區域。

1. 選取左邊或右邊的滑鼠按鈕，即可分別使用的前景色彩或背景色彩填滿。

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>若要挑選其他位置使用的映像中的色彩

**選取色彩**，或色彩揀選工具建立映像上的任何色彩背景色彩，取決於您按左或右滑鼠按鍵的目前的前景色彩。 若要取消**選取色彩**工具，請選擇另一個工具。

1. 使用**影像編輯器**工具列或功能表前往**映像** > **工具**，然後選取**選取色彩**工具。

1. 選取您想要從映像中挑選的色彩。

   > [!NOTE]
   > 您挑選一種色彩之後,**影像編輯器**予以最近使用的工具。

1. 繪製前景色彩，或滑鼠右按鈕的背景色彩，使用滑鼠左鍵。

### <a name="to-choose-the-background"></a>若要選擇背景

當您移動或複製的選取項目，從映像時，任何像素選取範圍中符合目前的背景色彩的是，根據預設，透明，它們不會遮住的目標位置中的像素為單位。

您可以從透明背景 （預設值） 的不透明背景，來回切換。 當您使用選項工具 中，**透明背景**並**不透明的背景**選項會出現在**選項**上的選取器**影像編輯器**工具列。

![背景選項&#45;不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "背景選項&#45;不透明或透明")<br/>
**透明及不透明的選項**上**影像編輯器工具列**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>若要切換透明及不透明背景

在 **影像編輯器**工具列上，選取**選項**選取器，然後選擇適當的背景：

- **不透明背景 (O)**:現有的映像會隱藏的選取範圍的所有組件。

- **透明背景 (T)**:現有的映像會顯示符合目前的背景色彩選取範圍的組件。

> [!TIP]
> 捷徑，在**映像**功能表上，選取或清除**繪製不透明**。

當選取範圍已變更影像的哪些部分而言是透明的作用中時，您可以變更背景色彩。

### <a name="to-invert-the-colors-in-a-selection"></a>若要在選取範圍色彩對換

**影像編輯器**提供便利的方式，可反轉選取的映像的組件中的色彩，讓您知道映像會如何顯示以反轉的色彩。

若要反轉目前選取範圍的色彩，請移至功能表**映像** > **色彩對換**。

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>若要自訂或變更色彩調色盤的色彩

1. 移至功能表**映像** > **調整色彩**。

1. 在 [**自訂色彩選取器**對話方塊方塊中，適當的文字方塊中輸入 RGB 或 HSL 值定義的色彩或選擇在色彩**漸層色彩顯示**] 方塊中。

1. 移動滑桿，以設定光度**亮度**列。

1. 許多自訂色彩會被遞色。 如果您想最接近遞色色彩的純色，按兩下**色彩** 方塊中。

   如果您稍後決定要遞色的色彩，移動滑桿**亮度**列，或移動中的交叉線**漸層色彩顯示**方塊，再以還原遞色。

1. 選取 **確定**若要新增新的色彩。

### <a name="to-save-a-custom-colors-palette"></a>若要儲存自訂色彩調色盤

1. 移至功能表**映像** > **儲存調色盤**。

1. 瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。

1. 選取 [儲存]。

### <a name="to-load-a-custom-colors-palette"></a>若要載入自訂色彩調色盤

1. 移至功能表**映像** > **載入調色盤**。

1. 在 **載入色彩調色盤**對話方塊方塊中，瀏覽至正確的目錄，然後選取您想要載入的調色盤。 **色彩**調色盤會以.pal 副檔名儲存。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[HOW TO：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[HOW TO：編輯映像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[HOW TO：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
