---
title: （c + +） 圖示影像編輯器
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: dd7da76d3df68fa63c87f64610524accfd4302ef
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041545"
---
# <a name="image-editor-for-icons-c"></a>（c + +） 圖示影像編輯器

當您在 選取影像檔 （例如.ico、.bmp、.png） 時**方案總管**，影像會在中開啟**影像編輯器**中開啟程式碼檔案的相同方式**程式碼編輯器**. 當**影像編輯器**索引標籤作用中時，您會看到與許多工具可用來建立和編輯映像的工具列。 點陣圖、 圖示和游標，以及您可以編輯中使用的命令的 GIF 或 JPEG 格式的映像**映像**功能表，然後在工具**影像編輯器**工具列。

圖形化的資源是您定義應用程式的映像。 您可以繪製徒手，或使用形狀繪製。 您可以選取組件的編輯、 翻轉或調整其大小的影像，或您可以從選取的組件的映像建立自訂筆刷，並使用筆刷繪製。 您可以定義映像的屬性，將影像儲存在不同的格式，將映像轉換成另一種格式。

> [!NOTE]
> 使用**影像編輯器**，您可以檢視 32 位元映像，但無法加以編輯。

您也可以使用**影像編輯器**並[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器不支援編輯內嵌的資源。

除了建立新的圖形化資源，您可以[匯入現有的映像](../windows/how-to-copy-resources.md#import-and-export-resources)進行編輯，然後將它們新增至您的專案。 您也可以開啟和編輯映像，並不屬於專案，以供[獨立的影像編輯](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)。

如需**影像編輯器**，請參閱如何[建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)，[編輯映像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)，[使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)， [使用色彩](../windows/working-with-color-image-editor-for-icons.md)，並[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)。

> [!NOTE]
> 免費下載**Visual Studio 影像庫**，其中包含許多動畫、 點陣圖和圖示，您可以使用您的應用程式中。 如需如何下載程式庫的詳細資訊，請參閱[Visual Studio 影像庫](/visualstudio/designers/the-visual-studio-image-library)。

## <a name="image-menu"></a>影像功能表

**映像**時才會顯示功能表**影像編輯器**之後，有可用於編輯映像的色板，和設定的命令**影像編輯器**視窗選項。 此外，使用裝置映像的命令可使用圖示和游標時。

|命令|描述|
|---|---|
|**色彩對換**|反轉色彩。|
|**水平翻轉**|水平翻轉影像或選取範圍。|
|**垂直翻轉**|垂直翻轉影像或選取範圍。|
|**旋轉 90 度**|旋轉影像或選取範圍 90 度。|
|**顯示色彩視窗**|會開啟**色彩**視窗中，您可以在其中選擇要使用映像的色彩。|
|**將選取範圍當做筆刷**|可讓您建立自訂筆刷從映像的一部分。<br/><br/>您的選取項目會成為自訂筆刷可將選取範圍中的色彩分散到映像。 選取範圍的複本會保留在拖曳的路徑。 您將拖曳的速度變慢，進行更多的複本。|
|**複製和外框的選取項目**|建立一份目前選取範圍的複本，並建立此複本的外框。<br/><br/>如果目前的選取範圍中包含的背景色彩，將不會包含當您透明選取。
|**調整色彩**|會開啟**自訂色彩選取器**，可讓您自訂映像您使用的色彩。|
|**載入調色盤**|會開啟**載入色彩調色盤** 對話方塊中，可讓您載入先前儲存到.pal 檔案的調色盤色彩。|
|**儲存調色盤**|將儲存色板色彩.pal 檔案。|
|**繪製不透明**|選取時，會使目前的選取範圍不透明。<br/><br/>清除時，讓目前的選取範圍透明化。|
|**工具列編輯器**|會開啟[新增工具列資源對話方塊](../windows/new-toolbar-resource-dialog-box.md)。|
|**格線設定**|會開啟**格線設定**對話方塊中，您可以在此指定映像的方格。|
|**新的映像類型**|會開啟[的新\<裝置 > 影像類型對話方塊](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)。<br/><br/>單一的圖示資源可以包含不同大小的數個映像和 windows 可以使用適當的圖示大小取決於要如何顯示。 新的裝置類型不會修改大小的圖示，但而是會建立新的映像中的圖示。 僅適用於圖示和游標。|
|**目前的圖示/游標影像類型**|會開啟子功能表會列出前九個可用資料指標或圖示的映像。 在子功能表上的最後一個命令**詳細**，開啟[開放\<裝置 > 影像對話方塊](../windows/open-device-image-dialog-box-image-editor-for-icons.md)。|
|**刪除映像類型**|刪除選取的裝置映像。|
|**工具**|啟動子功能表，其中包含從提供的所有工具**影像編輯器**工具列。|

**格線設定**對話方塊可讓您指定格線設定映像，並顯示格線內編輯影像。 格線可用於編輯映像，但不會儲存為映像本身的一部分。

|屬性|描述|
|---|---|
|**像素格線**|有選取時，會顯示方格，以解決每一個像素**影像編輯器**。<br/><br/>方格會出現只在 4 × 和較高的解析度。|
|**磚狀格線**|選取時，會顯示一個方格，周圍區塊中的像素**影像編輯器**格線間距值所指定。|
|**寬度**|指定每個圖格區塊的寬度。<br/><br/>繪製點陣圖包含定期排列的多個映像時，此屬性相當實用。|
|**高度**|指定每個圖格區塊的高度。<br/><br/>繪製點陣圖包含定期排列的多個映像時，此屬性相當實用。|

## <a name="toolbar"></a>工具列

**影像編輯器**工具列包含工具，繪圖、 繪圖、 輸入文字、 消除及操作檢視。 它也包含選項選取器，與中，您可以選取使用各項工具的選項。 例如，您可以選擇不同的筆刷寬度、 縮放因素和線條樣式。

上提供的所有工具**影像編輯器**工具列是也可以從功能表**映像** > **工具**。 若要使用**影像編輯器**工具列並**選項**選取器中，選取 工具或您想要的選項。

![影像編輯器工具列](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
**影像編輯器**工具列

> [!TIP]
> 將游標停留在工具列按鈕時，就會出現工具提示。 這些提示可協助您識別每個按鈕的功能。

因為有許多種繪圖工具可從[鍵盤](../windows/accelerator-keys-image-editor-for-icons.md)，可能會很有用隱藏**影像編輯器**工具列。

- 若要顯示或隱藏**影像編輯器**工具列上，移至功能表**檢視** > **工具列**，然後選擇 **影像編輯器**。

> [!NOTE]
> 這個工具列中的項目都會出現時的映像檔無法使用從目前的專案或方案未在中開啟**影像編輯器**。

### <a name="option-selector"></a>選項選取器

具有**選項**選取器，您可以指定一條線、 筆刷筆劃和更多功能的寬度。 上的圖示**選項**選取器按鈕變更，視哪一種工具而定，您已選取。

![繪製&#45;影像編輯器工具列上的形狀選取器](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
**選項**上的選取器**影像編輯器**工具列

### <a name="text-tool"></a>文字工具

使用**文字工具**對話方塊中，將文字加入至資料指標、 點陣圖或圖示的資源。

若要存取此對話方塊中，開啟**影像編輯器**並移至功能表**映像** > **工具**，然後選取**文字工具**命令。

> [!TIP]
> 您可以以滑鼠右鍵按一下**文字工具**對話方塊，即可存取預設的捷徑功能表，其中包含一份標準的 Windows 命令。

開啟**文字工具字型**對話方塊來變更字型、 樣式或資料指標字型的大小。 變更會套用至中顯示的文字**文字**區域。

若要存取此對話方塊中，選取**字型**按鈕**文字工具** 對話方塊。 可用的屬性如下：

|屬性|描述|
|---|---|
|**字型**|列出可用的字型。|
|**字型樣式**|列出指定的字型的可用樣式。|
|**大小**|列出指定的字型的可用點數大小。|
|**範例**|顯示文字會如何出現具有指定的字型設定的範例。|
|**指令碼**|列出可用的語言指令碼，針對指定的字型。<br/><br/>當您選取不同的語言指令碼時，字元集的語言可用來建立多國語言的文件。|

#### <a name="to-change-the-font-of-text-on-an-image"></a>若要變更的映像上的文字的字型

以下是文字的如何將文字新增至 Windows 應用程式中的圖示和操作您字型的範例。

1. 建立 c + + Windows Forms 應用程式。 如需詳細資訊，請參閱[如何：建立 Windows Form 應用程式](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90))。 *App.ico*檔案預設會新增至您的專案。

1. 在 **方案總管**，按兩下檔案*app.ico*。 **影像編輯器**隨即開啟。

1. 移至功能表**映像** > **工具**，然後選取**文字工具**。

1. 在 [**文字工具**] 對話方塊中，輸入*c + +* 空的文字區域中。 此文字會出現在可調整大小的方塊的左角*app.ico*中**影像編輯器**。

1. 在 **影像編輯器**，將可調整大小的方塊拖曳到中央*app.ico*以改善文字的可讀性。

1. 在 [**文字工具**對話方塊中，選取**字型**] 按鈕。

1. 在 [**文字工具字型**] 對話方塊中：

   - 選取  **Times New Roman**從清單中所列的可用字型**字型**清單方塊。

   - 選取 **粗體**從清單中列出可用的字型樣式**字型樣式**清單方塊。

   - 選取  **10**從可用的點中所列的大小**大小**清單方塊。

   - 選擇 [確定] 。 **文字工具字型**對話方塊會關閉，而新的字型設定將套用到您的文字。

1. 選擇**關閉**上**文字工具** 對話方塊。 可調整您在文字周圍方塊會從消失**影像編輯器**。

文字區域會顯示為資源的一部分顯示的文字。 一開始，此區域是空的。

> [!NOTE]
> 如果**透明背景**已經設定，只有文字會放入映像。 如果**不透明背景**設定周框，填滿背景色彩，將會放置文字的背景。

## <a name="window-panes"></a>視窗窗格

**影像編輯器**視窗會顯示兩個映像，以分隔列分隔的兩個窗格檢視。 您可隨意地拖曳分隔列，以變更窗格的相對大小。 現用窗格會顯示選取框線。

一個檢視是實際的大小和其他 6 個預設放大係數會放大。 這兩個窗格中的檢視會自動更新，其中一個窗格中的任何變更會立即顯示在其他。 兩個窗格，方便您處理您的映像，您可以區分個別像素為單位，並且，在此同時，觀察 映像的 實際大小 檢視您的工作影響的放大檢視。

左的窗格會使用最多所需的空間 (最多一半**映像**視窗) 來顯示 1:1 縮放比例的預設檢視您的映像。 右窗格會顯示預設的 6:1 縮放比例縮小映像。 您可以變更每個窗格使用縮放比例**Magnify**工具**影像編輯器**工具列或使用的快速鍵。

您可以放大的較小的窗格**影像編輯器**視窗，並使用兩個窗格顯示的大型影像的不同區域。 您可以選取窗格內選擇它。

您可以變更窗格的相對大小的指標放在分割列上，並將在分割列移至右或向左。 在分割列可以移動到任一端，如果您想要使用一個窗格。

如果**影像編輯器**窗格放大 4 倍以上，您可以顯示分隔映像中的個別像素的像素格線。

### <a name="to-change-the-magnification-factor"></a>若要變更縮放比例

根據預設，**影像編輯器**在實際大小] 與 [實際大小的 6 倍在右窗格中檢視的左窗格中顯示的檢視。 縮放比例倍數 （如在工作區底部的 [狀態] 列所示） 是映像的實際大小和顯示的大小之間的比例。 預設的因數為 6，範圍是從 1 到 10。

1. 選取 **影像編輯器**窗格中您想要變更其縮放比例。

1. 在 **影像編輯器**工具列上，選取右邊的箭號**Magnify**工具，並在子功能表中選取縮放比例：**1 X**， **2 X**， **6 X**，或**8 X**。

   > [!NOTE]
   > 若要選取以外所列的縮放比例**Magnify**工具中，使用的快速鍵。

### <a name="to-display-or-hide-the-pixel-grid"></a>若要顯示或隱藏像素格線

針對所有**影像編輯器**4 或更高的縮放比例的窗格，您可以顯示分隔映像中的個別像素格線。

1. 移至功能表**映像** > **格線設定**。

1. 選取 [**像素格線**顯示方格中，或清除此方塊可隱藏方格] 核取方塊。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>

<!--[Icons](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)-->