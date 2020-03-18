---
title: 如何：建立圖示或其他影像
ms.date: 02/15/2019
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
ms.openlocfilehash: 046b7e0070d95f5d17b3240884db76533f1c6ccd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443909"
---
# <a name="how-to-create-an-icon-or-other-image"></a>如何：建立圖示或其他影像

您可以建立新的影像、點陣圖、圖示、游標或工具列，然後使用**影像編輯器**來自訂其外觀。 您也可以在[資源範本](../windows/how-to-use-resource-templates.md)之後建立新的點陣圖。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>圖示和游標：顯示裝置的影像資源

圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 (不同的大小和色彩配置)。 資料指標也有作用點，也就是 Windows 用來追蹤其位置的位置。 圖示和游標都會使用**影像編輯器**來建立和編輯，如同點陣圖和其他影像。

當您建立新的圖示或游標時，**影像編輯器**會先建立標準類型的影像。 而且一開始會以螢幕 (透明) 色彩填滿影像。 如果影像是游標，則作用點一開始是左上角，座標 `0,0`。

根據預設，**影像編輯器**支援針對下表所示的裝置建立其他映射。 您可以在 [**自訂影像**] 對話方塊中輸入寬度、高度和色彩計數等參數，為其他裝置建立影像。

|Color|寬度 (像素)|高度 (像素)|
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

### <a name="create-a-device-image-icon-or-cursor"></a>建立裝置影像（圖示或游標）

當您建立新的圖示或游標資源時，**影像編輯器**會先以特定樣式建立影像（32×32、圖示為16色，以及32×32、單色用於游標）。 接著，您可以將不同大小和樣式的影像新增至初始圖示或游標，並視需要針對不同的顯示裝置編輯每個額外的影像。 您也可以從現有的影像類型或在圖形程式中建立的點陣圖使用剪下和貼上作業來編輯影像。

當您在[影像編輯器](../windows/image-editor-for-icons.md)中開啟圖示或游標資源時，預設會開啟最符合目前顯示裝置的影像。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源腳本](../windows/how-to-create-a-resource-script-file.md)檔。

[**新增 &lt;裝置&gt; 映射類型**] 對話方塊，可讓您建立指定類型的新裝置映射。 若要開啟 [**新增 \<裝置 > 映射**] 對話方塊，請移至 [功能表] [**映射**] > [**新增映射類型**]。 包含的下列屬性包括 [**目標映射類型**] 和 [**自訂**]。

[**目標映射類型**] 屬性會列出可用的映射類型，您可以在其中選取您要開啟的映射類型：

||||
|-|-|-|
|-16 x 16，16色|-48 x 48、16色|-96 x 96、16色|
|-16 x 16，256色彩|-48 x 48、256色彩|-96 x 96、256色彩|
|-16 x 16、單色|-48 x 48、單色|-96 x 96、單色|
|-32 x 32、16色|-64 x 64、16色||
|-32 x 32、256色彩|-64 x 64、256色彩||
|-32 x 32、單色|-64 x 64、單色||

> [!NOTE]
> 任何現有的映射都不會顯示在這份清單中。

**自訂**屬性會開啟 [**自訂影像**] 對話方塊，您可以在其中建立具有自訂大小和色彩數目的新影像。

[**自訂影像**] 對話方塊可讓您建立具有自訂大小和色彩數目的新影像。 其中包含下列屬性：

|屬性|描述|
|---|---|
|**寬度**|提供空間讓您輸入自訂影像的寬度（以圖元為單位）（1-512，限制為2048）。|
|**高度**|提供空間讓您輸入自訂影像的高度（以圖元為單位）（1-512，限制為2048）。|
|**色彩**|提供空間讓您選擇自訂影像的色彩數目：2、16或256。|

使用 [**開啟 &lt;裝置&gt; 影像**] 對話方塊，即可在專案中C++開啟裝置影像。 它會列出目前資源中的現有裝置映射（屬於目前資源的影像）。 其中包含下列屬性：

|屬性|描述|
|---|---|
|**目前的影像**|列出資源中包含的映射。 選取您想要開啟的映射類型。|

#### <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc*檔，然後選擇 [**插入資源**]。 如果您的 *.rc*檔中已經有現有的影像資源（如資料指標），您可以用滑鼠右鍵按一下**游標**資料夾，然後選取 [**插入資料指標**]。

1. 在 [[插入資源] 對話方塊](../windows/add-resource-dialog-box.md)中，選取 [**圖示**] 或 [**游標**]，然後選擇 [**新增**]。 針對圖示，此動作會建立具有32×32、16色圖示的圖示資源。 若是資料指標，則會建立32×32、單色（2色彩）影像。

   如果 [**插入資源**] 對話方塊中影像資源類型旁出現一個加號（ **+** ），表示工具列範本可以使用。 選取加號展開範本清單，選取範本，然後選擇 [**新增**]。

### <a name="to-add-an-image-for-a-different-display-device"></a>新增不同顯示裝置的影像

1. 移至 [功能表] [**影像**] > [**新裝置影像**]，或在 [**影像編輯器**] 窗格中按一下滑鼠右鍵，然後選擇 [**新增裝置映射**]。

1. 選取您想要新增的映射類型。 您也可以選取 [**自訂**]，建立預設清單中無法使用其大小的圖示。

### <a name="to-copy-a-device-image"></a>複製裝置影像

1. 移至 [功能表] [**影像**] > **開啟 [裝置影像**]，然後從 [目前影像] 清單中選擇影像。 例如，選擇32×32、16色版本的圖示。

1. 複製目前顯示的圖示影像（**Ctrl**+**C**）。

1. 在另一個 [**影像編輯器**] 視窗中，開啟不同的圖示影像。 例如，開啟16× 16 16 色的圖示版本。

1. 將圖示影像（**Ctrl**+**V**）從一個 [**影像編輯器**] 視窗貼入另一個。 如果您要將較大的大小貼入較小的大小，可以使用圖示控點來調整影像大小。

### <a name="to-delete-a-device-image"></a>若要刪除裝置映射

當**影像編輯器**中顯示圖示影像時，請移至 功能表 **影像** > **刪除裝置影像**。 當您刪除資源中的最後一個圖示映射時，也會一併刪除資源。

> [!NOTE]
> 當您按下**Del**鍵時，您在圖示上繪製的影像和色彩會被刪除，但仍會保留圖示，而您現在可以重新加以設計。 如果您誤按下**Del**鍵，請按**Ctrl**+**Z**來復原動作。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>在裝置影像中建立透明或反向區域

在[影像編輯器](../windows/image-editor-for-icons.md)中，初始圖示或游標影像具有透明屬性。 雖然圖示和游標影像是矩形，但許多都不會出現，因為影像的某些部分是透明的，而且螢幕上的基礎影像會顯示整個圖示或游標。 當您拖曳圖示時，影像的某些部分可能會以反轉的色彩顯示。 您可以藉由在 [[色彩] 視窗](../windows/colors-window-image-editor-for-icons.md)中設定螢幕色彩和反色色彩來建立此效果。

您套用至圖示和游標的螢幕和反向色彩，會將衍生影像成形並色彩，或指派反向區域。 色彩表示具有這些屬性的影像部分。 在編輯時，您可以變更代表螢幕顏色和反色屬性的色彩。 這些變更不會影響應用程式中圖示或游標的外觀。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更您的設定，請移至功能表**工具** > 匯**入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

#### <a name="to-create-transparent-or-inverse-regions"></a>建立透明或反向區域

1. 在 [**色彩**] 視窗中，選擇 [選取器**畫面色彩**] 或 [**反色**]。

1. 使用繪圖工具將螢幕或反轉色彩套用至您的影像。 如需繪圖工具的詳細資訊，請參閱[使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。

#### <a name="to-change-the-screen-or-inverse-color"></a>變更螢幕或反色

1. 選取 [**螢幕色彩**選取器] 或 [**反色**] 選取器。

1. 從 **[色彩] 視窗**中的 [**色彩**] 調色板選擇色彩。

   系統會自動為其他選取器指派互補色彩。

   > [!TIP]
   > 如果您按兩下 [**螢幕色彩**] 或 [**反色**] 選取器，就會出現 [[自訂色彩選取器] 對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。

### <a name="use-the-256-color-palette"></a>使用 256-color 調色板

使用**影像編輯器**，圖示和游標可以調整大小為大（64×64），並提供可供選擇的256色調色板。 建立資源之後，會選取裝置影像樣式。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>建立256色圖示或游標

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc*檔，然後選擇 [**插入資源**]。 如果您的 *.rc*檔中已經有現有的影像資源（如資料指標），您可以用滑鼠右鍵按一下**游標**資料夾，然後選取 [**插入資料指標**]。

1. 在 [[插入資源] 對話方塊](../windows/add-resource-dialog-box.md)中，選取 [**圖示**] 或 [**游標**]，然後選擇 [**新增**]。

1. 移至 [功能表] [**影像**] > [**新裝置影像**]，然後選取您想要的256色彩影像樣式。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>從 256-color 調色板選擇大圖示的色彩

若要使用 256-color 調色板的選取專案進行繪製，您必須從 [[色彩] 視窗](../windows/colors-window-image-editor-for-icons.md)中的 [**色彩**] 調色板選取色彩。

1. 選取大型圖示或游標，或建立新的大型圖示或游標。

1. 從 **[色彩] 視窗**的 [**色彩**] 調色板中顯示的256色彩選擇色彩。

   選取的色彩會成為 [**色彩] 視窗**中 [**色彩**] 調色板的目前色彩。

   > [!NOTE]
   > 256色彩影像所使用的初始調色板，符合 `CreateHalftonePalette` Windows API 傳回的調色板。 所有適用于 Windows shell 的圖示都應該使用此調色板，以避免在調色板實現期間發生閃爍。

### <a name="to-set-a-cursors-hot-spot"></a>若要設定游標的作用點

游標的作用點是指視窗用來追蹤游標位置的重點。 根據預設，作用點會設定為游標的左上角，其座標為 `0,0`。 [屬性視窗](/visualstudio/ide/reference/properties-window)中的 [**作用點**] 屬性會顯示作用點座標。

1. 在 [[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)上，選擇 [**設定熱點**] 工具。

1. 選取您想要指派為游標作用點的圖元。

   [**屬性**] 視窗中的 [**作用點**] 屬性會顯示新的座標。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>建立和儲存點陣圖為 .gif 或 jpeg

當您建立點陣圖時，會以點陣圖格式（.bmp）建立影像。 不過，您可以將影像儲存為 GIF 或 JPEG，或使用其他圖形格式。

> [!NOTE]
> 此程式不適用於圖示和游標。

1. 移至 **功能表** 檔案 > **開啟**，**然後選取** 檔案。

1. 在 [**新增檔案] 對話方塊**中，選擇 **[ C++視覺效果**] 資料夾，然後選取 [**範本**] 方塊中的 [**點陣圖檔案（.bmp）** ]，然後選取 [**開啟**]。

   點陣圖會在**影像編輯器**中開啟。

1. 視需要對您的新點陣圖進行變更。

1. 當點陣圖仍然在**影像編輯器**中開啟時，移至 [**功能表]** [檔案] > [**將*檔案名*儲存為**]。

1. 在 [**另存**新檔] 對話方塊中，輸入您要授與檔案的名稱，以及在 [**檔案名**] 方塊中代表所需檔案格式的副檔名。 例如， *myfile.txt*。

   > [!NOTE]
   > 您必須在專案之外建立或開啟點陣圖，才能將它儲存為另一種檔案格式。 如果您在專案中建立或開啟它，將無法使用 [**另存**新檔] 命令。 如需詳細資訊，請參閱[在專案之外的資源腳本檔案中查看資源（獨立式）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

1. 選取 [儲存]。

### <a name="to-convert-an-image-from-one-format-to-another"></a>若要將影像從一種格式轉換成另一種格式

您可以在**影像編輯器**中開啟 GIF 或 JPEG 影像，並將其儲存為點陣圖。 此外，您也可以開啟點陣圖檔案，並將它儲存為 GIF 或 JPEG。 您使用的影像不需要是專案的一部分，即可在開發環境中進行編輯（請參閱[獨立映射編輯](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)）。

1. 在**影像編輯器**中開啟影像。

1. 移**至功能表檔案** > [**另存*檔案名*** ]。

1. 在 [**另存**新檔] 對話方塊的 [**檔案名**] 方塊中，輸入代表所需格式的檔案名和副檔名。

1. 選取 [儲存]。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>將新的影像資源加入非受控C++專案

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc*檔，然後選擇 [**插入資源**]。 如果您的 *.rc*檔中已經有現有的影像資源（例如游標），您只要以滑鼠右鍵按一下**游標**資料夾，然後選取 [**插入游標**] 即可。

1. 在 [[插入資源] 對話方塊](../windows/add-resource-dialog-box.md)中，選取您想要建立的映射資源類型（例如**點陣圖**），然後選擇 [**新增**]。

   如果 [**插入資源**] 對話方塊中影像資源類型旁出現一個加號（ **+** ），表示工具列範本可以使用。 選取加號展開範本清單，選取範本，然後選擇 [**新增**]。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要以 .NET 程式設計語言將新的影像資源加入至專案

1. 在**方案總管**中，以滑鼠右鍵按一下專案資料夾（例如， *windowsapplication1*）。

1. 從快捷方式功能表中，**選取 [新增]** ，然後選擇 [**加入新專案**]。

1. 在 [**類別**] 窗格中，展開 [**本機專案**專案] 資料夾，然後選擇 [**資源**]。

1. 在 [**範本**] 窗格中，選擇您想要新增至專案的資源類型。

   資源會在**方案總管**中新增至您的專案，而資源會在[影像編輯器](../windows/image-editor-for-icons.md)中開啟。 您現在可以使用**影像編輯器**中所有可用的工具來修改映射。 如需將影像加入至 managed 專案的詳細資訊，請參閱[在設計階段載入圖片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->