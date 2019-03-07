---
title: 如何：建立圖示或其他影像
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 92eac69e6802a824c4b6e107d2ff3393e931a542
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563052"
---
# <a name="how-to-create-an-icon-or-other-image"></a>如何：建立圖示或其他影像

您可以建立新的映像、 點陣圖、 圖示、 游標或工具列中，並用**影像編輯器**以自訂其外觀。 您也可以建立新的點陣圖，模仿[資源範本](../windows/how-to-use-resource-templates.md)。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>圖示和游標：顯示裝置的影像資源

圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 (不同的大小和色彩配置)。 資料指標也會有作用點，位置 Windows 用來追蹤它的位置。 圖示和游標會建立和使用編輯**影像編輯器**，如點陣圖和其他映像。

當您建立新的圖示或游標**影像編輯器**首先會建立一個標準類型的映像。 而且一開始會以螢幕 (透明) 色彩填滿影像。 如果影像是游標，作用點一開始是左上角座標`0,0`。

根據預設，**影像編輯器**支援下表所示的裝置建立額外的映像。 您可以輸入寬度、 高度和色彩計數等參數，以建立其他裝置的映像**自訂映像** 對話方塊。

|色彩|寬度 (像素)|高度 (像素)|
|-----------|----------------------|-----------------------|
|單色|16|16|
|單色|32|32|
|單色|48|48|
|單色|64|64|
|單色|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>建立裝置影像 （圖示或游標）

當您建立新的圖示或游標資源**影像編輯器**特定的樣式 （32 × 32，16 種色彩圖示和 32 × 32，資料指標的單色） 會先建立映像。 然後將映像不同大小和樣式加入初始的圖示或游標，並視需要編輯每個額外的映像，適用於不同的顯示裝置。 您也可以使用剪下和貼上作業，從現有的映像類型，或從圖形程式中建立點陣圖，以編輯映像。

當您開啟中的圖示或游標資源[影像編輯器](../windows/image-editor-for-icons.md)，預設會開啟大部分十分符合目前的顯示裝置的映像。

> [!NOTE]
> 如果您的專案尚未包含.rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

**的新&lt;裝置&gt;映像類型**對話方塊可讓您建立指定類型的新裝置映像。 若要開啟 **新增\<裝置 > 影像**對話方塊中，移至功能表**映像** > **新增影像類型**。 下列的屬性，包括**目標映像類型**並**自訂**。

**目標映像類型**屬性會列出您用來選取映像的可用映像類型您想要開啟的類型：

||||
|-|-|-|
|-16 x 16，16 種色彩|-48 x 48，16 種色彩|-96 x 96，16 種色彩|
|-16 x 16，256 色|-48 x 48，256 色|-96 x 96，256 色|
|-16 x 16，單色|-48 x 48，單色|-96 x 96，單色|
|-32 x 32，16 種色彩|-64 x 64，16 種色彩||
|-32 x 32，256 色|-64 x 64，256 色||
|-32 x 32，單色|-64 x 64，單色||

> [!NOTE]
> 這份清單中，將不會顯示任何現有的映像。

**自訂**屬性會開啟**自訂映像**對話方塊中，您可以在其中建立新的映像使用自訂的大小和色彩數目。

**自訂映像**對話方塊可讓您建立新的映像的自訂大小和色彩數目。 會包含下列屬性：

|屬性|描述|
|---|---|
|[寬度]|提供空間讓您輸入自訂影像的寬度，單位為像素 （1-512，限制為 2048年）。|
|[高度]|提供空間讓您輸入高度的像素為單位 （1-512，限制為 2048年） 的自訂映像。|
|**色彩**|提供空間讓您選擇的自訂映像的色彩數目：2、 16 或 256。|

使用**開啟&lt;裝置&gt;映像**對話方塊中，以開啟 c + + 專案中的 裝置映像。 它會列出目前的資源 （屬於目前的資源的映像） 的現有裝置映像。 是包含下列屬性：

|屬性|描述|
|---|---|
|**目前的映像**|列出資源中包含的映像。 選取您想要開啟的影像類型。|

#### <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在 [資源檢視](/windows/how-to-create-a-resource-script-file#create-resources)，以滑鼠右鍵按一下您 *.rc*檔案，然後選擇**插入資源**。 如果您已經有現有的映像資源您 *.rc*檔案，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。 圖示，此動作會建立具有 32 × 32、 16 色圖示的圖示資源。 資料指標，32 × 32，會建立單色 （2-色彩） 映像。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

### <a name="to-add-an-image-for-a-different-display-device"></a>若要加入不同顯示裝置的影像

1. 移至功能表**映像** > **新的裝置影像**，或以滑鼠右鍵按一下**影像編輯器**窗格，然後選擇 **新裝置映像**。

1. 選取您想要新增的映像的類型。 您也可以選取**自訂**來建立其大小無法使用的預設清單中的圖示。

### <a name="to-copy-a-device-image"></a>若要複製裝置影像

1. 移至功能表**映像** > **開啟裝置影像**並從目前的映像清單中選擇映像。 例如，選擇 32 × 32、 16 色版圖示。

1. 複製目前顯示的圖示的圖像 (**Ctrl**+**C**)。

1. 在另一個開啟不同的映像的圖示**影像編輯器**視窗。 例如，開啟 16 × 16、 16 色版圖示。

1. 貼上圖示的影像 (**Ctrl**+**V**) 從一個**影像編輯器**其他視窗。 如果您將會貼入較小的大小較大的大小，您可以使用圖示控制代碼來調整影像大小。

### <a name="to-delete-a-device-image"></a>若要刪除裝置影像

雖然圖示的影像會顯示在**影像編輯器**，請移至功能表**映像** > **刪除裝置影像**。 當您刪除資源中的最後一個圖示影像時，則也會刪除資源。

> [!NOTE]
> 當您按下**Del**索引鍵，您所繪製的圖示的色彩與影像會刪除但圖示會保留，而且您可以立即重新設計。 如果您按下**Del**不慎按下**Ctrl**+**Z**復原動作。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>若要在裝置影像中建立透明或反向區域

在 [影像編輯器](../windows/image-editor-for-icons.md)，初始的圖示或游標影像具有透明屬性。 圖示和游標影像是矩形，雖然許多不會出現，因為而言是透明的映像的組件，並在螢幕上的基礎映像顯示透過圖示或游標。 當您拖曳圖示時，影像的部分可能會出現反轉的色彩。 您建立這種效果藉由設定螢幕色彩和中的反向色彩[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

套用至圖示的螢幕及反向色彩和資料指標不是圖形色彩衍生的映像就是將反向區域指派。 色彩表示影像的部分，具有這些屬性。 您可以變更，表示在編輯畫面色彩及反向色彩屬性的色彩。 這些變更不會影響您的應用程式中的資料指標之圖示的外觀。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更您的設定，請移至功能表**工具** > **匯入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

#### <a name="to-create-transparent-or-inverse-regions"></a>若要建立透明或反向區域

1. 在 [**色彩**] 視窗中，選擇選取器**螢幕色彩**或**反向色彩**。

1. 適用於反向色彩拖曳至您的映像使用繪圖工具的螢幕。 如需有關繪圖工具的詳細資訊，請參閱 <<c0> [ 使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。

#### <a name="to-change-the-screen-or-inverse-color"></a>若要變更螢幕或反向色彩

1. 選取 **螢幕色彩**選取器或**反向色彩**選取器。

1. 選擇從色彩**色彩**中的調色盤**色彩**視窗。

   其他選取器，會自動指派互補色。

   > [!TIP]
   > 如果您按兩下**螢幕色彩**或**反向色彩**選取器[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)隨即出現。

### <a name="use-the-256-color-palette"></a>使用 256 色調色盤

使用**影像編輯器**、 圖示和游標可以是大小大 (64 × 64) 與 256 色調色盤選擇。 建立資源之後，請選取裝置影像樣式。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>若要建立 256 色圖示或游標

1. 在 [資源檢視](/windows/how-to-create-a-resource-script-file#create-resources)，以滑鼠右鍵按一下您 *.rc*檔案，然後選擇**插入資源**。 如果您已經有現有的映像資源您 *.rc*檔案，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。

1. 移至功能表**映像** > **新的裝置影像**，然後選取您要的 256 色影像樣式。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要從大圖示的 256 色調色盤選擇色彩

若要繪製選取 256 色調色盤中，您必須選取色彩**色彩**中的調色盤[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

1. 選取 大圖示或游標，或建立新的大圖示或游標。

1. 從顯示中的 256 色彩選擇色彩**色彩**中的調色盤**色彩**視窗。

   選取的色彩會變成目前的色彩**色彩**中的調色盤**色彩**視窗。

   > [!NOTE]
   > 256 色的映像所使用的初始調色盤比對所傳回的調色盤`CreateHalftonePalette`Windows API。 適用於 Windows shell 的所有圖示應該都使用這個調色盤來防止重繪閃動期間調色盤實現。

### <a name="to-set-a-cursors-hot-spot"></a>若要設定游標的作用點

資料指標的作用點是點至 Windows 追蹤游標的位置參考。 根據預設，設定作用點游標座標的左上角`0,0`。 **熱點**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)顯示作用點座標。

1. 在 [[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)，選擇**設定作用點**工具。

1. 選取您想要指派為游標的作用點的像素。

   **熱點**中的屬性**屬性**視窗會顯示新的座標。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要建立，並將點陣圖儲存為.gif 或.jpeg

當您建立點陣圖時，格式為點陣圖 (.bmp) 建立映像。 您不過，可以將影像儲存為 GIF 或 JPEG 或其他圖形的格式。

> [!NOTE]
> 此程序不適用於圖示和游標。

1. 移至功能表**檔案** > **Open**，然後選取**檔案**。

1. 在**新的檔案] 對話方塊中**，選擇**Visual c + +** 資料夾，然後選取**點陣圖檔 (.bmp)** 中**範本**方塊，然後選取 [ **開啟**。

   在中開啟點陣圖**影像編輯器**。

1. 視需要進行變更，新的點陣圖。

1. 與仍在中開啟點陣圖**影像編輯器**，請移至功能表**檔案** > **儲存*filename*為.bmp**。

1. 在 [**另存新檔**對話方塊方塊中，輸入您想要提供檔案，代表您要的檔案格式的延伸模組的名稱**檔案名稱**] 方塊中。 例如， *myfile.gif*。

   > [!NOTE]
   > 您必須建立或開啟您專案外的點陣圖，以將它儲存為其他檔案格式。 如果您建立或開啟您的專案內**另存新檔**命令將會無法使用。 如需詳細資訊，請參閱 <<c0> [ 檢視資源在資源指令碼檔案外部的專案 （獨立式）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

1. 選取 [儲存]。

### <a name="to-convert-an-image-from-one-format-to-another"></a>若要將影像轉換成另一種格式

您可以開啟中的 GIF 或 JPEG 影像**影像編輯器**並將它們儲存為點陣圖。 此外，您可以開啟點陣圖檔案，並將它儲存為 GIF 或 JPEG。 您使用的映像不需要在開發環境中編輯專案的一部分 (請參閱[獨立的影像編輯](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md))。

1. 開啟中的映像**影像編輯器**。

1. 移至功能表**檔案** > **儲存*檔名*為**。

1. 在 **另存新檔**對話方塊中，於**檔案名稱**方塊中，輸入檔案名稱和副檔名，表示您想要的格式。

1. 選取 [儲存]。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>若要將新的映像資源新增至未受管理的 c + + 專案

1. 在 [資源檢視](/windows/how-to-create-a-resource-script-file#create-resources)，以滑鼠右鍵按一下您 *.rc*檔案，然後選擇**插入資源**。 如果您已經有現有的映像資源您 *.rc*檔案，例如資料指標，您可以直接以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取您想要建立的映像資源的類型 (**點陣圖**，例如) 然後選擇**新增**。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要將新的映像資源新增至.NET 程式設計語言中的專案

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下專案資料夾 (例如*WindowsApplication1*)。

1. 從捷徑功能表，選取**新增**，然後選擇**加入新項目**。

1. 在 **類別** 窗格中，展開**本機專案項目**資料夾，然後選擇 **資源**。

1. 在 [**範本**] 窗格中，選擇您想要新增至專案的資源類型。

   資源便會加入至您的專案中**方案總管**並在中開啟資源[影像編輯器](../windows/image-editor-for-icons.md)。 您現在可以使用提供的所有工具**影像編輯器**修改您的映像。 如需有關如何將影像加入至 managed 專案的詳細資訊，請參閱[在設計階段載入圖片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：複製影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/desktop/menurc/icons)<br/>
[Cursors](/windows/desktop/menurc/cursors)<br/>-->