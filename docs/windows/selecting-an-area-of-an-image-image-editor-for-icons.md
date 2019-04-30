---
title: HOW TO：編輯映像
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387940"
---
# <a name="how-to-edit-an-image"></a>HOW TO：編輯映像

您可以使用 選取工具來定義您想要剪下、 複製、 清除、 調整大小、 反轉，或移動之影像的區域。 具有**矩形選取範圍**工具，您可以定義，並選取影像的矩形區域。 具有**不規則的選取項目**工具，您可以繪製徒手畫的外框範圍，您想要選取剪下、 複製或其他作業。

> [!NOTE]
> 請參閱**矩形選取範圍**並**不規則的選取項目**工具所示[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)或檢視上每個按鈕相關聯的工具提示**影像編輯器**工具列。

您也可以從選取項目建立自訂筆刷。 如需詳細資訊，請參閱 <<c0> [ 建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

## <a name="how-to"></a>如何

若要編輯映像，請參閱 < 如何：

### <a name="to-select-an-image"></a>若要選取的映像

1. 使用**影像編輯器**工具列或功能表前往**映像** > **工具**，然後選擇您要的選取範圍工具。

1. 將插入點移至您想要選取的影像區域的其中一個角落。 出現十字型游標停留在影像上時。

1. 將插入點拖曳到相反邊角，您想要選取的區域中。 矩形會顯示將選取的像素為單位。 在矩形中，包括矩形下方的所有像素會包含在選取項目。

1. 放開滑鼠按鈕。 選取框線包圍選取的區域。

#### <a name="to-select-an-entire-image"></a>若要選取整個影像

選取目前選取範圍外的影像。 選取框線焦點變更，並再次包含整個影像。

### <a name="to-edit-parts-of-an-image"></a>若要編輯影像部分範圍

您可以執行標準的編輯作業： 剪下、 複製、 清除和移動 — 上[選取項目](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)，不論選取範圍是整個影像或加入其中。 因為**影像編輯器**會使用**Windows 剪貼簿**，您可以在傳輸之間的映像**影像編輯器**和 Windows 的其他應用程式。

此外，您可以調整大小選項，是否包含整個映像或只是其中一部分。

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>剪下目前的選取範圍，並將它移到剪貼簿

移至功能表**編輯** > **剪下**。

#### <a name="to-copy-the-selection"></a>若要複製的選取項目

1. 選取框線內或的任何位置將指標放在其上，除了調整大小控點。

1. 按住**Ctrl**金鑰，您將選取項目拖曳至新位置。 原始的選取範圍的區域不會變更。

1. 將選取範圍複製到映像，在其目前的位置，選取 選擇資料指標之外。

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要將剪貼簿內容貼到映像

1. 移至功能表**編輯** > **貼上**。

   剪貼簿內容，括住選取範圍框線中，會出現在窗格的左上角。

1. 選取框線內將指標放在與映像上，將影像拖曳到想要的位置。

1. 若要錨定在其新位置的映像，請選取外部選取框線。

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要刪除目前選取範圍，而不將它移到剪貼簿

移至功能表**編輯** > **刪除**。

   目前的背景色彩填滿選取範圍的原始區域。

> [!NOTE]
> 您可以存取**剪下**，**複製**，**貼上**，以及**刪除**命令，以滑鼠右鍵按一下**資源檢視**  視窗。

#### <a name="to-move-the-selection"></a>移動選取範圍

1. 選取框線內或的任何位置將指標放在其上，除了調整大小控點。

1. 將選取項目拖曳至其新位置。

1. 若要錨定在其新位置的映像中的選取範圍，請選取 選取範圍框線外。

如需有關繪製選取範圍的詳細資訊，請參閱[建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-flip-an-image"></a>若要翻轉影像

您可以翻轉或旋轉影像來建立原始的鏡像映像、 倒置映像，或向右影像 90 度旋轉一次。

- 要水平翻轉影像 （鏡像映像），請移至功能表**映像** > **水平翻轉**。

- 若要垂直翻轉影像 （要上下顛倒），請移至功能表**映像** > **垂直翻轉**。

- 若要將影像旋轉 90 度，移至功能表**映像** > **旋轉 90 度**。

   > [!NOTE]
   > 您也可以使用[快速鍵 （捷徑）](../windows/accelerator-keys-image-editor-for-icons.md)這些命令或從捷徑功能表存取命令 (select 時在映像，在外部**影像編輯器**)。

### <a name="to-resize-an-image"></a>若要調整影像大小

行為**影像編輯器**雖然調整影像大小取決於您是否曾[選](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)只是部分或整個影像。

選取範圍包含只有部分映像，當**影像編輯器**縮小選取範圍，藉由刪除資料列或資料行的像素為單位，並以目前的背景色彩填滿空出的區域。 它也可以複製資料列或資料行的像素為單位，以延伸選取範圍。

當選取範圍包含整個映像**影像編輯器**是壓縮和映像，會自動縮放或裁剪，並將它擴充。

有兩種機制來調整影像大小： 調整大小控點並[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您拖曳調整大小控點，若要變更的所有大小或影像的一部分。 您可以拖曳調整大小控點是純色。 您無法將拖曳空心的控制代碼。 使用**屬性**視窗重新調整整個影像，未選取的組件。

![縮放控點上的點陣圖](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
調整大小控點

> [!NOTE]
> 如果您有**圖格的格線**中選取選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然後調整大小貼齊至下一個並排顯示格線。 如果只有**像素格線**選項是選取 （預設值），調整大小貼齊至下一個可用的像素。

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要調整整個影像使用 [屬性] 視窗的大小

1. 開啟您想要變更其屬性的影像。

1. 在**寬度**並**高度**方塊[屬性 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要的尺寸。

   如果您要增加的映像的大小**影像編輯器**延伸到右方時，向下、 影像或兩者，並使用目前的背景色彩填滿新的區域。 映像不會自動縮放。

   如果縮短映像的大小**影像編輯器**裁切的右邊緣或下邊緣，或兩者上的映像。

   > [!NOTE]
   > 您可以使用**寬度**並**高度**只整個調整影像大小，不是用來調整大小部分選取的屬性。

#### <a name="to-crop-or-extend-an-entire-image"></a>若要裁剪或擴充整個影像

1. 選取整個影像。

   如果目前選取的映像的一部分，而且您想要選取整個影像，選取目前選取範圍框線外面的映像上的任何位置。

1. 拖曳調整大小控點，直到的影像是正確的大小。

通常**影像編輯器**裁切或放大映像，當您調整所移動的縮放控點。 如果您按住**Shift**鍵移動的縮放控點，**影像編輯器**縮小或延伸影像。

#### <a name="to-shrink-or-stretch-an-entire-image"></a>若要縮小或延伸整個影像

1. 選取整個影像。

   如果目前選取的映像的一部分，而且您想要選取整個影像，選取目前選取範圍框線外面的映像上的任何位置。

1. 按住**Shift**鍵並拖曳調整大小控點，直到映像的正確大小。

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>若要縮小或拉長影像的一部分

1. 選取您想要調整大小的映像的一部分。 如需詳細資訊，請參閱 <<c0> [ 選取影像的區域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖曳調整大小控點，直到選取範圍是正確的大小。

### <a name="to-edit-an-image-outside-of-a-project"></a>若要編輯專案外的影像

您可以開啟和編輯在開發環境中的映像，就如同在任何圖形應用程式，例如開啟獨立編輯的點陣圖。 您使用的映像不需要 Visual Studio 專案的一部分。

1. 移至功能表**檔案** > **開啟**。

1. 在 **類型的檔案**方塊中，選取**的所有檔案**。

1. 找出並開啟您想要編輯映的像。

### <a name="to-change-image-properties"></a>若要變更影像屬性

您可以設定或修改的映像使用的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。

1. 開啟中的映像**影像編輯器**。

1. 在 [**屬性**] 視窗中，變更您的映像的任何或所有屬性。

   |屬性|描述|
   |--------------|-----------------|
   |**色彩**|指定影像的色彩配置。 選取 **單色**， **16**，或**256**，或**True 色彩**。<br/><br/>如果您已繪製具有 16 色調色盤的映像，請選取**單色**映像會造成的黑白色彩的替代項目。 對比永遠不會保留： 例如，相鄰的紅色和綠色的區域都會轉換為黑色。|
   |**檔案名稱**|指定影像檔的名稱。<br/><br/>根據預設，Visual Studio 指派給基底的檔名，藉由移除前四個字元 ("IDB_") 建立的預設資源識別元 (IDB_BITMAP1)，並新增適當的擴充功能。 在此範例中的映像的檔案名稱會是*BITMAP1.bmp*。 您可以將它重新命名*MYBITMAP1.bmp*。|
   |[高度]|設定影像的高度 （以像素為單位）。 預設值是 48。<br/><br/>則會裁剪影像，或空格會加入現有的映像的下方。|
   |**ID**|設定資源的識別碼。<br/><br/>映像，Microsoft Visual Studio 中，根據預設，會指派下一個可用的識別項，在一系列：IDB_BITMAP1、 IDB_BITMAP2，等等。 類似的名稱會用於圖示和游標。|
   |**Palette**|變更色彩屬性。<br/><br/>按兩下，以選取色彩，並顯示[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 在適當的文字方塊中輸入 RGB 或 HSL 值定義的色彩。|
   |**SaveCompressed**|指出影像是否以壓縮格式。 這個屬性是唯讀的。<br/><br/>Visual Studio 不允許您將影像儲存在壓縮的格式，因此 Visual Studio 中建立任何映像，這個屬性會**False**。 如果您在 Visual Studio 中開啟 （在其他程式中建立） 的壓縮映像，這個屬性會 **，則為 True**。 如果您儲存使用 Visual Studio 的壓縮映像時，它將會是未壓縮和此屬性將會還原回**False**。|
   |[寬度]|設定影像的寬度 （以像素為單位）。 點陣圖的預設值是 48。<br/><br/>則會裁剪影像，或現有的映像的右邊加入空白。|

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>