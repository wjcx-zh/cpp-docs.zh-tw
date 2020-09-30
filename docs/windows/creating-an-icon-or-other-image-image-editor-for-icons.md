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
ms.openlocfilehash: bbaa008d8dac74588fc15bfebbc7cb2611260349
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504559"
---
# <a name="how-to-create-an-icon-or-other-image"></a>如何：建立圖示或其他影像

您可以建立新的影像、點陣圖、圖示、游標或工具列，然後使用 **影像編輯器** 自訂其外觀。 您也可以在 [資源範本](./how-to-create-a-resource-script-file.md)之後建立新的點陣圖。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>圖示和游標：顯示裝置的影像資源

圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 (不同的大小和色彩配置)。 資料指標也有作用點，也就是 Windows 用來追蹤其位置的位置。 圖示和游標都會使用 **影像編輯器**來建立和編輯，如同點陣圖和其他影像。

當您建立新的圖示或游標時， **影像編輯器** 會先建立標準類型的影像。 而且一開始會以螢幕 (透明) 色彩填滿影像。 如果影像是游標，則作用點最初是具有座標的左上角 `0,0` 。

根據預設， **影像編輯器** 支援為下表所示的裝置建立其他映射。 您可以在 [ **自訂影像** ] 對話方塊中輸入寬度、高度和色彩計數參數，為其他裝置建立影像。

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

### <a name="create-a-device-image-icon-or-cursor"></a> (圖示或游標) 建立裝置映射

當您建立新的圖示或游標資源時， **影像編輯器** 會先建立特定樣式的影像 (32 ×32、適用于圖示的16色彩，以及32×32、單色表示資料指標) 。 然後，您可以將不同大小和樣式的影像新增至初始圖示或游標，然後視需要針對不同的顯示裝置編輯每個額外的影像。 您也可以從現有的影像類型或在圖形程式中建立的點陣圖使用剪下和貼上作業來編輯影像。

當您在 [影像編輯器](../windows/image-editor-for-icons.md)中開啟圖示或游標資源時，預設會開啟最符合目前顯示裝置的影像。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源腳本](../windows/how-to-create-a-resource-script-file.md)檔。

[ **新增 &lt; 裝置 &gt; 映射類型** ] 對話方塊可讓您建立指定類型的新裝置映射。 若要開啟 [**新增 \<Device> 映射**] 對話方塊，請移至 [功能表**影像**  >  **新增映射類型**]。 下列屬性包括 **目標映射類型** 和 **自訂**。

[ **目標映射類型** ] 屬性會列出可用的映射類型，您可以在其中選取要開啟的映射類型：

:::row:::
   :::column span="":::
      16 x 16、16色 \
      32 x 32、16色 \
      48 x 48、16色 \
      64 x 64、16色 \
      96 x 96、16色
   :::column-end:::
   :::column span="":::
      16 x 16，256色彩 \
      32 x 32、256色彩 \
      48 x 48、256色彩 \
      64 x 64、256色彩 \
      96 x 96、256色彩
   :::column-end:::
   :::column span="":::
      16 x 16、單色 \
      32 x 32、單色 \
      48 x 48、單色 \
      64 x 64、單色 \
      96 x 96、單色
   :::column-end:::
:::row-end:::

> [!NOTE]
> 任何現有的映射都不會顯示在此清單中。

**自**定義屬性會開啟 [**自訂映射**] 對話方塊，您可以在其中使用自訂大小和色彩數目來建立新的影像。

[ **自訂影像** ] 對話方塊可讓您使用自訂大小和色彩數目來建立新的影像。 下列屬性包括：

|屬性|描述|
|---|---|
|**寬度**|提供空間讓您輸入自訂影像的寬度（以圖元為單位） (1-512，2048) 的限制。|
|**高度**|提供空間讓您輸入自訂影像的高度（以圖元為單位） (1-512，2048) 的限制。|
|**色彩**|提供空間讓您選擇自訂影像的色彩數目：2、16或256。|

使用 [ **開啟 &lt; 裝置 &gt; 映射** ] 對話方塊來開啟 c + + 專案中的裝置映射。 它會列出目前資源中的現有裝置映射 (目前資源) 的一部分。 下列屬性包括：

|屬性|描述|
|---|---|
|**目前的影像**|列出資源中包含的映射。 選取您要開啟的映射類型。|

#### <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ **插入資源**]。 如果您的 *.rc* 檔中已經有現有的影像資源，例如資料指標，您可以用滑鼠右鍵按一下 **游標** 資料夾，然後選取 [ **插入資料指標**]。

1. 在 [ [插入資源] 對話方塊](./how-to-create-a-resource-script-file.md)中，選取 [ **圖示** ] 或 [ **游標** ]，然後選擇 [ **新增**]。 若為圖示，此動作會建立一個具有32×32、16色圖示的圖示資源。 針對資料指標，會建立32×32、單色 (2 色彩) 影像。

   如果加號 (**+**) 出現在 [ **插入資源** ] 對話方塊中的影像資源類型旁邊，則表示工具列範本可以使用。 選取加號展開範本清單、選取範本，然後選擇 [ **新增**]。

### <a name="to-add-an-image-for-a-different-display-device"></a>新增不同顯示裝置的影像

1. 移至 [功能表**映射**  >  **新裝置映射**]，或在 [**影像編輯器**] 窗格中按一下滑鼠右鍵，然後選擇 [**新增裝置映射**]。

1. 選取您要新增的映射類型。 您也可以選取 [ **自訂** ] 來建立預設清單中無法使用其大小的圖示。

### <a name="to-copy-a-device-image"></a>複製裝置映射

1. 移至 [功能表**影像**  >  **開啟裝置映射**]，然後從 [目前影像] 清單中選擇影像。 例如，選擇32×32、16色版本的圖示。

1. 將目前顯示的圖示影像複製 (**Ctrl** + **C**) 。

1. 在另一個 [ **影像編輯器** ] 視窗中開啟圖示的不同影像。 例如，開啟16× 16 16 色版本的圖示。

1. 將圖示影像 (**Ctrl** + **V**) 從一個 [**影像編輯器**] 視窗貼到另一個。 如果您要將較大的大小貼入較小的大小，您可以使用圖示控點來調整影像大小。

### <a name="to-delete-a-device-image"></a>刪除裝置映射

當**影像編輯器**中顯示圖示影像時，請移至功能表**影像**  >  **刪除裝置映射**。 當您刪除資源中的最後一個圖示影像時，也會一併刪除資源。

> [!NOTE]
> 當您按下 **Del** 鍵時，就會刪除您在圖示上繪製的影像和色彩，但會保留該圖示，您現在可以重新設計它。 如果您不小心按下**Del**鍵，請按**Ctrl** + **Z**來復原動作。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>在裝置影像中建立透明或反向區域

在 [ [影像編輯器](../windows/image-editor-for-icons.md)] 中，初始圖示或游標影像具有透明屬性。 雖然圖示和游標影像是矩形，但很多都不會出現，因為影像的元件是透明的，而且螢幕上的基礎影像會透過圖示或游標顯示。 當您拖曳圖示時，影像的部分可能會以反轉的色彩顯示。 您可以藉由在 [ [色彩] 視窗](./image-editor-for-icons.md)中設定螢幕色彩和反色來建立此效果。

您套用至圖示和游標的畫面和反向色彩會將衍生影像成形和色彩，或指派反向區域。 色彩表示影像中具有這些屬性的部分。 您可以在 [編輯] 中變更代表螢幕色彩和反色屬性的色彩。 這些變更不會影響應用程式中圖示或游標的外觀。

> [!NOTE]
> 您所看到的對話方塊和功能表命令可能會與 [說明] 中描述的不同 **，視您使用的設定** 或版本而定。 若要變更您的設定，請移至 [功能表**工具**匯  >  **入和匯出設定**]。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

#### <a name="to-create-transparent-or-inverse-regions"></a>建立透明或反向區域

1. 在 [ **色彩** ] 視窗中，選擇 [選取器] **畫面色彩** 或 [ **反色**]。

1. 使用繪圖工具將螢幕或反色套用至您的影像。 如需繪製工具的詳細資訊，請參閱 [使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。

#### <a name="to-change-the-screen-or-inverse-color"></a>變更螢幕或反向色彩

1. 選取 [ **螢幕色彩** 選取器] 或 [ **反色** 選取器]。

1. 從 **[色彩] 視窗**的 [**色彩**] 選擇區中選擇色彩。

   系統會自動為其他選取器指派互補色彩。

   > [!TIP]
   > 如果您按兩下 [ **螢幕色彩** ] 或 [ **反色** ] 選取器，就會出現 [ [自訂色彩選取器] 對話方塊](./image-editor-for-icons.md) 。

### <a name="use-the-256-color-palette"></a>使用256色板

您可以使用 **影像編輯器**，將圖示和游標大小調整為大型的 (64 × 64) ，以及可供選擇的256色色板。 建立資源之後，即會選取裝置影像樣式。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>建立256色圖示或游標

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ **插入資源**]。 如果您的 *.rc* 檔中已經有現有的影像資源，例如資料指標，您可以用滑鼠右鍵按一下 **游標** 資料夾，然後選取 [ **插入資料指標**]。

1. 在 [ [插入資源] 對話方塊](./how-to-create-a-resource-script-file.md)中，選取 [ **圖示** ] 或 [ **游標** ]，然後選擇 [ **新增**]。

1. 移至 [功能表**映射**  >  **新裝置影像**]，然後選取您想要的256色彩影像樣式。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>針對大型圖示從256色板選擇色彩

若要使用256色調色板中的選取範圍來繪製，您需要從 [[色彩] 視窗](./image-editor-for-icons.md)的 [**色彩**] 選擇區中選取色彩。

1. 選取大型圖示或游標，或建立新的大型圖示或游標。

1. 從 **[色彩] 視窗**的 [**色彩**] 選擇區中顯示的256色彩中選擇色彩。

   選取的色彩會**成為 [色彩] 視窗**中 [**色彩**選擇區] 的目前色彩。

   > [!NOTE]
   > 256色彩影像所用的初始調色板符合 Windows API 所傳回的調色板 `CreateHalftonePalette` 。 所有適用于 Windows shell 的圖示都應該使用此選擇區，以防止在調色板實現期間發生閃爍。

### <a name="to-set-a-cursors-hot-spot"></a>設定資料指標的作用點

資料指標的作用點是 Windows 在追蹤游標位置時所指的點。 根據預設，作用點會設定為具有座標的游標左上角 `0,0` 。 [屬性視窗](/visualstudio/ide/reference/properties-window)中的**作用**點屬性會顯示作用點座標。

1. 在 [ [影像編輯器] 工具列](./image-editor-for-icons.md)上，選擇 [ **設定熱點** ] 工具。

1. 選取您要指派為游標作用點的圖元。

   [**屬性**] 視窗中的 [**熱點**] 屬性會顯示新的座標。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要建立點陣圖，並將其儲存為 .gif 或 jpeg

當您建立點陣圖時，影像會以點陣圖格式建立 ( .bmp) 。 不過，您可以將影像儲存為 GIF 或 JPEG 或其他圖形格式。

> [!NOTE]
> 此程式不適用於圖示和資料指標。

1. 移**至功能表檔**[  >  **開啟**]， **File**然後選取 [檔案]。

1. 在 [**新增檔案] 對話方塊**中，選擇**Visual C++** 資料夾，然後在 [**範本**] 方塊中選取 [**點陣圖檔 ( .bmp) **並選取 [**開啟**]。

   點陣圖會在 **影像編輯器**中開啟。

1. 視需要對您的新點陣圖進行變更。

1. 當點陣圖仍在**影像編輯器**中開啟時，請移至**功能表檔**  >  **儲存*檔案名*.bmp As**。

1. 在 [ **另存** 新檔] 對話方塊的 [ **檔案名** ] 方塊中，輸入您要為檔案指定的名稱，以及代表您所要檔案格式的副檔名。 例如， *myfile.gif*。

   > [!NOTE]
   > 您必須建立或開啟專案外部的點陣圖，才能將它另存成另一種檔案格式。 如果您在專案中建立或開啟它，[ **另存** 新檔] 命令將無法使用。 如需詳細資訊，請參閱在 [專案以外的資源指令檔中查看資源 (獨立) ](./how-to-create-a-resource-script-file.md)。

1. 選取 [儲存]。

### <a name="to-convert-an-image-from-one-format-to-another"></a>將影像從某種格式轉換成另一種格式

您可以在 **影像編輯器** 中開啟 GIF 或 JPEG 影像，並將它們儲存為點陣圖。 此外，您還可以開啟點陣圖檔案，然後將它儲存為 GIF 或 JPEG。 您使用的影像不需要屬於專案的一部分，也不能在開發環境中編輯 (請參閱 [獨立的影像編輯](./selecting-an-area-of-an-image-image-editor-for-icons.md)) 。

1. 在 **影像編輯器**中開啟影像。

1. 移**至功能表檔**[  >  **另存*檔案名***]。

1. 在 [ **另存** 新檔] 對話方塊的 [ **檔案名** ] 方塊中，輸入代表所需格式的檔案名和副檔名。

1. 選取 [儲存]。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>將新的影像資源新增至非受控 c + + 專案

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ **插入資源**]。 如果您的 *.rc* 檔中已經有現有的影像資源，例如資料指標，您可以直接以滑鼠右鍵按一下 **游標** 資料夾，然後選取 [ **插入資料指標**]。

1. 在 [ [插入資源] 對話方塊](./how-to-create-a-resource-script-file.md)中，選取您要建立 (**點陣圖**的影像資源類型，例如) 然後選擇 [ **新增**]。

   如果加號 (**+**) 出現在 [ **插入資源** ] 對話方塊中的影像資源類型旁邊，則表示工具列範本可以使用。 選取加號展開範本清單、選取範本，然後選擇 [ **新增**]。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>使用 .NET 程式設計語言將新的影像資源新增至專案

1. 在 **方案總管**中，以滑鼠右鍵按一下專案資料夾 (例如， *windowsapplication1]*) 。

1. 從快捷方式功能表選取 [ **加入**]，然後選擇 [ **加入新專案**]。

1. 在 [ **類別目錄** ] 窗格中，展開 [ **本機專案專案** ] 資料夾，然後選擇 [ **資源**]。

1. 在 [ **範本** ] 窗格中，選擇您想要新增至專案的資源類型。

   資源會新增至 **方案總管** 中的專案，而資源會在 [影像編輯器](../windows/image-editor-for-icons.md)中開啟。 您現在可以使用 **影像編輯器** 中所有可用的工具來修改您的影像。 如需有關將影像加入至 managed 專案的詳細資訊，請參閱 [在設計階段載入圖片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[How to：編輯影像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](./toolbar-editor.md)<br/>
[Creating New Toolbars](./toolbar-editor.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->
