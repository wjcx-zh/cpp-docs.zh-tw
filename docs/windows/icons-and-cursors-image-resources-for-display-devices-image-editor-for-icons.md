---
title: 圖示和游標：顯示裝置 （c + + 圖示影像編輯器） 的影像資源
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 027c3c0380a73c624432bbe45758b3296732949a
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849941"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>圖示和游標：顯示裝置 （c + + 圖示影像編輯器） 的影像資源

圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 (不同的大小和色彩配置)。 此外，游標具有 「 作用點，「 Windows 用來追蹤其位置的位置。 圖示和游標會建立和使用編輯**映像**編輯器中，當點陣圖和其他映像。

當您建立新的圖示或游標**映像**編輯器會先建立一個標準類型的映像。 而且一開始會以螢幕 (透明) 色彩填滿影像。 如果影像是游標，其作用點一開始會在左上角 (座標 0,0)。

根據預設，**映像**編輯器支援下表所示的裝置建立額外的映像。 您可以在 [[自訂影像]](custom-image-dialog-box-image-editor-for-icons.md)對話方塊中輸入寬度、高度和色彩計數等參數，為其他裝置建立影像。

> [!NOTE]
> 使用**影像編輯器**，您可以檢視 32 位元映像，但無法加以編輯。

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

## <a name="create-a-device-image-icon-or-cursor"></a>建立裝置影像 （圖示或游標）

當您建立新的圖示或游標資源**映像**先在特定的樣式 （32 × 32，16 種色彩圖示和 32 × 32，資料指標的單色） 中建立映像的編輯器。 然後將映像不同大小和樣式加入初始的圖示或游標，並視需要編輯每個額外的映像，適用於不同的顯示裝置。 您也可以使用剪下和貼上作業，從現有的映像類型，或從圖形程式中建立點陣圖，以編輯映像。

當您開啟中的圖示或游標資源[影像編輯器](../windows/image-editor-for-icons.md)，預設會開啟大部分十分符合目前的顯示裝置的映像。

### <a name="new-ltdevicegt-image-type-dialog-box"></a>新&lt;裝置&gt;影像類型對話方塊

**的新&lt;裝置&gt;映像類型**對話方塊可讓您建立指定類型的新裝置映像。 若要開啟 **新增\<裝置 > 影像**對話方塊中，選取**新的映像類型**上**映像**功能表。 下列的屬性，包括**目標映像類型**並**自訂**。

#### <a name="target-image-type"></a>目標影像類型

列出可用的映像類型。 選取您想要開啟的映像類型：

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

#### <a name="custom"></a>自訂

會開啟**自訂映像**對話方塊中，您可以在其中建立新的映像使用自訂的大小和色彩數目。

**自訂映像**對話方塊可讓您建立新的映像的自訂大小和色彩數目。 會包含下列屬性：

|屬性|描述|
|---|---|
|[寬度]|提供空間讓您輸入自訂影像的寬度，單位為像素 （1-512，限制為 2048年）。|
|[高度]|提供空間讓您輸入高度的像素為單位 （1-512，限制為 2048年） 的自訂映像。|
|**色彩**|提供空間讓您選擇的自訂映像的色彩數目：2、 16 或 256。|

### <a name="open-ltdevicegt-image-dialog-box"></a>開啟&lt;裝置&gt;影像對話方塊

使用**開啟&lt;裝置&gt;映像**對話方塊中，以開啟 c + + 專案中的 裝置映像。 它會列出目前的資源 （屬於目前的資源的映像） 的現有裝置映像。 是包含下列屬性：

|屬性|描述|
|---|---|
|**目前的映像**|列出資源中包含的映像。 選取您想要開啟的影像類型。|

### <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含.rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。 圖示，此動作會建立具有 32 × 32、 16 色圖示的圖示資源。 資料指標，32 × 32，會建立單色 （2-色彩） 映像。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 選取加號，展開 範本清單中的，選取範本，然後選擇**新增**。

## <a name="add-an-image-for-a-different-display-device"></a>加入不同顯示裝置的映像

1. 在上**映像**功能表上，選取**新的裝置影像**(或以滑鼠右鍵按一下**影像編輯器**窗格，然後選擇 **新裝置映像**從快顯功能表）。

1. 選取您想要新增的映像的類型。 您也可以選取**自訂**來建立其大小無法使用的預設清單中的圖示。

## <a name="copy-a-device-image"></a>複製裝置影像

1. 在上**映像**功能表上，選取**開啟裝置影像**並從目前的映像清單中選擇映像。 例如，選擇 32 × 32、 16 色版圖示。

1. 複製目前顯示的圖示的圖像 (**Ctrl**+**C**)。

1. 在另一個開啟不同的映像的圖示**影像編輯器**視窗。 例如，開啟 16 × 16、 16 色版圖示。

1. 貼上圖示的影像 (**Ctrl**+**V**) 從一個**影像編輯器**其他視窗。 如果您將會貼入較小的大小較大的大小，您可以使用圖示控制代碼來調整影像大小。

## <a name="delete-a-device-image"></a>刪除裝置影像

雖然圖示的影像會顯示在**映像**編輯器中，選取**刪除裝置影像**從**映像**功能表。 當您刪除資源中的最後一個圖示影像時，則也會刪除資源。

   > [!NOTE]
   > 當您按下**Del**索引鍵，映像和您所繪製的圖示色彩會遭到刪除，但會保留圖示; 您可以立即重新設計。 如果您按下**Del**遭，您可以按下**Ctrl**+**Z**復原動作。

## <a name="create-transparent-or-inverse-regions-in-device-images"></a>在裝置影像中建立透明或反向區域

在 [影像編輯器](../windows/image-editor-for-icons.md)，初始的圖示或游標影像具有透明屬性。 圖示和游標影像是矩形，雖然許多不會出現，因為影像的部分是透明的;透過圖示或游標會顯示在螢幕上的基礎映像。 當您拖曳圖示時，影像的部分可能會出現反轉的色彩。 您建立這種效果藉由設定螢幕色彩和中的反向色彩[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

套用至圖示的螢幕及反向色彩和資料指標不是圖形色彩衍生的映像就是將反向區域指派。 色彩表示影像的部分，具有這些屬性。 您可以變更，表示在編輯畫面色彩及反向色彩屬性的色彩。 這些變更不會影響您的應用程式中的資料指標之圖示的外觀。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-transparent-or-inverse-regions"></a>若要建立透明或反向區域

1. 在 **色彩**視窗中，選取**螢幕色彩**選取器或**反向色彩**選取器。

1. 適用於反向色彩拖曳至您的映像使用繪圖工具的螢幕。 如需有關繪圖工具的詳細資訊，請參閱 <<c0> [ 使用繪圖工具](using-a-drawing-tool-image-editor-for-icons.md)。

### <a name="to-change-the-screen-or-inverse-color"></a>若要變更螢幕或反向色彩

1. 選取 **螢幕色彩**選取器或**反向色彩**選取器。

1. 選擇從色彩**色彩**中的調色盤**色彩**視窗。

   其他選取器，會自動指派互補色。

   > [!TIP]
   > 如果您按兩下**螢幕色彩**或**反向色彩**選取器[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)隨即出現。

## <a name="use-the-256-color-palette"></a>使用 256 色調色盤

使用**映像**編輯器、 圖示和游標，則可以是大小大 (64 × 64) 與 256 色調色盤可從中選擇。 建立資源之後，請選取裝置影像樣式。

### <a name="to-create-a-256-color-icon-or-cursor"></a>若要建立 256 色圖示或游標

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**，然後選擇 **新增**。

1. 在 **映像**功能表上，選取**新的裝置影像**。

1. 選取您想要的 256 色影像樣式。

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要從大圖示的 256 色調色盤選擇色彩

若要繪製選取 256 色調色盤中，您必須選取色彩**色彩**中的調色盤[色彩視窗](../windows/colors-window-image-editor-for-icons.md)。

1. 選取 大圖示或游標，或建立新的大圖示或游標。

1. 從顯示中的 256 色彩選擇色彩**色彩**中的調色盤**色彩**視窗。

   選取的色彩會變成目前的色彩**色彩**中的調色盤**色彩**視窗。

   > [!NOTE]
   > 256 色的映像所使用的初始調色盤比對所傳回的調色盤`CreateHalftonePalette`Windows API。 適用於 Windows shell 的所有圖示應該都使用這個調色盤來防止重繪閃動期間調色盤實現。

## <a name="set-a-cursor39s-hot-spot"></a>將游標設定為&#39;s 作用點

資料指標的作用點是點至 Windows 追蹤游標的位置參考。 根據預設，作用點設定為資料指標 （座標 0，0） 的左上角。 **熱點**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)顯示作用點座標。

### <a name="to-set-a-cursors-hot-spot"></a>若要設定游標的作用點

1. 在 [[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)，選擇**設定作用點**工具。

1. 選取您想要指派為游標的作用點的像素。

   **熱點**中的屬性**屬性**視窗會顯示新的座標。

   > [!TIP]
   > 將游標停留在工具列按鈕時，就會出現工具提示。 這些提示可協助您識別每個按鈕的功能。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[影像功能表](../windows/image-menu-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[圖示](/windows/desktop/menurc/icons)<br/>
[游標](/windows/desktop/menurc/cursors)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
