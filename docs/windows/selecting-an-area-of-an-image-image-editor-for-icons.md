---
title: 如何：編輯影像
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: 6d973ad444f719b905af5a33e47ef28f4895111f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447298"
---
# <a name="how-to-edit-an-image"></a>如何：編輯影像

您可以使用 [選取工具] 來定義要剪下、複製、清除、調整大小、反轉或移動之影像的區域。 您可以使用**矩形選取**工具來定義和選取影像的矩形區域。 使用**不規則的選取**工具，您可以針對剪下、複製或其他作業，繪製您想要選取之區域的手繪外框。

> [!NOTE]
> 請參閱[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)中的**矩形選取**和**不規則的選取**工具，或在**影像編輯器**工具列上查看與每個按鈕相關聯的工具提示。

您也可以從選取專案建立自訂筆刷。 如需詳細資訊，請參閱[建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

## <a name="how-to"></a>作法

若要編輯影像，請參閱如何：

### <a name="to-select-an-image"></a>若要選取影像

1. 使用 **影像編輯器** 工具列或 移至功能表**影像** > **工具**，然後選擇您想要的 選取 工具。

1. 將插入點移至您想要選取之影像區域的一個角落。 當插入點在影像上方時，會出現交叉線線。

1. 將插入點拖曳至您想要選取之區域的反角。 矩形會顯示要選取的圖元。 矩形內的所有圖元（包括在矩形底下）都會包含在選取專案中。

1. 放開滑鼠按鈕。 選取範圍框線會括住選取的區域。

#### <a name="to-select-an-entire-image"></a>若要選取整個映射

選取目前選取範圍以外的影像。 選取框線會變更焦點，並再次包含整個影像。

### <a name="to-edit-parts-of-an-image"></a>編輯影像的元件

您可以在[選取](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)範圍上執行標準編輯作業，不論選取範圍是整個影像或只是其中一部分。 因為**影像編輯器**會使用**windows 剪貼**簿，所以您可以在**影像編輯器**和 Windows 的其他應用程式之間傳送影像。

此外，您可以調整選取專案的大小，不論其包含整個影像或只是元件。

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>若要剪下目前的選取範圍，並將其移至剪貼簿

移至功能表 **編輯** > **剪**下。

#### <a name="to-copy-the-selection"></a>複製選取專案

1. 將指標放在選取範圍框線內或其中的任何位置，但調整大小控點除外。

1. 按住**Ctrl**鍵，將選取專案拖曳到新的位置。 原始選取範圍的區域不變。

1. 若要將選取範圍複製到影像中的目前位置，請選取選取游標外部。

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>將剪貼簿內容貼到影像中

1. 移至功能表 [**編輯** > **貼**上]。

   [剪貼簿] 內容（以選取框線括住）會出現在窗格的左上角。

1. 將指標放在選取框線內，並將影像拖曳至影像上的所需位置。

1. 若要將影像錨定在其新位置，請選取選取範圍外框的外部。

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>刪除目前的選取範圍，而不將其移至剪貼簿

移至功能表 **編輯** > **刪除**。

   選取範圍的原始區域會以目前的背景色彩填滿。

> [!NOTE]
> 在 [**資源檢視**] 視窗中按一下滑鼠右鍵，即可存取**剪**下、**複製**、**貼**上和**刪除**命令。

#### <a name="to-move-the-selection"></a>若要移動選取範圍

1. 將指標放在選取範圍框線內或其中的任何位置，但調整大小控點除外。

1. 將選取專案拖曳至其新位置。

1. 若要將影像中的選取範圍錨定在其新位置，請選取選取範圍外框以外的專案。

如需使用選取專案繪製的詳細資訊，請參閱[建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-flip-an-image"></a>若要翻轉影像

您可以翻轉或旋轉影像，以建立原始的鏡像影像、關閉影像的倒置，或一次將影像旋轉至右側90度。

- 若要水準翻轉影像（鏡像影像），請移至 [功能表] [**影像**] > [**水準翻轉**]。

- 若要垂直翻轉影像（關閉倒置），請移至 [功能表] [**影像**] > [**垂直翻轉**]。

- 若要旋轉影像90度，請移至 [功能表**影像**] > **旋轉90度**。

   > [!NOTE]
   > 您也可以使用這些命令的[快速鍵（快捷方式）鍵](../windows/accelerator-keys-image-editor-for-icons.md)，或從快捷方式功能表存取命令（在**影像編輯器**中選取影像外）。

### <a name="to-resize-an-image"></a>若要調整影像大小

**影像編輯器**在調整影像大小時的行為，取決於您[選取](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)的是整個影像，或只是其中一部分。

當選取範圍只包含影像的一部分時，**影像編輯器**會刪除資料列或資料行，並以目前的背景色彩填滿空出的區域，以縮小選取範圍。 它也可以藉由複製資料列或圖元的資料行來延展選取範圍。

當選取範圍包含整個影像時，**影像編輯器**會縮小和伸展影像，或裁剪並擴充影像。

有兩種機制可調整影像大小：調整大小控點和[屬性視窗](/visualstudio/ide/reference/properties-window)。 您可以拖曳調整大小控點來變更影像全部或部分的大小。 您可以拖曳的調整大小控點是實線。 您無法拖曳空心的控點。 使用 [**屬性**] 視窗來調整整個影像的大小，而不是選取的元件。

![點陣圖上的調整大小控點](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
調整大小控點

> [!NOTE]
> 如果您已在 [[方格設定] 對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)中選取 [**磚方格**] 選項，則會將 [貼齊] 調整為下一個磚格線。 如果只選取 [**圖元方格**] 選項（預設設定），則將 [調整大小] 貼齊至下一個可用的圖元。

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>使用 [屬性] 視窗調整整個影像的大小

1. 開啟您想要變更其屬性的映射。

1. 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [**寬度**] 和 [**高度**] 方塊中，輸入您想要的維度。

   如果您要增加影像的大小，**影像編輯器**會將影像向右、向下或兩者延伸，並以目前的背景色彩填滿新的區域。 影像不會伸展。

   如果您縮短影像的大小，**影像編輯器**會裁剪右側或下邊緣的影像，或兩者。

   > [!NOTE]
   > 您可以使用 [**寬度**] 和 [**高度**] 屬性來調整整個影像的大小，而不是調整部分選取範圍。

#### <a name="to-crop-or-extend-an-entire-image"></a>裁剪或擴充整個影像

1. 選取整個映射。

   如果目前已選取影像的一部分，而您想要選取整個影像，請選取目前選取範圍框線外影像上的任何位置。

1. 拖曳調整大小控點，直到影像大小正確為止。

一般來說，**影像編輯器**會在您移動調整大小控點的大小時，裁剪或放大影像。 如果您在移動調整大小控點時按住**Shift**鍵，**影像編輯器**會縮小或伸展影像。

#### <a name="to-shrink-or-stretch-an-entire-image"></a>壓縮或延展整個影像

1. 選取整個映射。

   如果目前已選取影像的一部分，而您想要選取整個影像，請在目前選取範圍框線以外的影像上選取任何位置。

1. 按住**Shift**鍵並拖曳調整大小控點，直到影像大小正確為止。

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>縮小或延展影像的一部分

1. 選取您要調整大小之影像的部分。 如需詳細資訊，請參閱[選取影像的區域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖曳其中一個調整大小控點，直到選取範圍正確為止。

### <a name="to-edit-an-image-outside-of-a-project"></a>編輯專案外的影像

您可以在開發環境中開啟和編輯影像，就像在任何圖形應用程式中一樣，例如開啟點陣圖進行獨立編輯。 您使用的影像不需要是 Visual Studio 專案的一部分。

1. 移至 **功能表** 檔案 > **開啟**。

1. 在 [**檔案類型**] 方塊中，選取 [**所有**檔案]。

1. 找出並開啟您想要編輯的映射。

### <a name="to-change-image-properties"></a>變更影像屬性

您可以使用[屬性視窗](/visualstudio/ide/reference/properties-window)來設定或修改影像的屬性。

1. 在**影像編輯器**中開啟影像。

1. 在 [**屬性**] 視窗中，變更影像的任何或所有屬性。

   |屬性|描述|
   |--------------|-----------------|
   |**色彩**|指定影像的色彩配置。 選取 [**單色**]、[ **16**] 或 [ **256**] 或 [**真色彩**]。<br/><br/>如果您已使用16色調色板繪製影像，則選取 [**單色**] 會對影像中的色彩造成黑色和白色的替換。 不一定會維持對比：例如，紅色和綠色的相鄰區域都會轉換成黑色。|
   |**檔名**|指定影像檔案的名稱。<br/><br/>根據預設，Visual Studio 會指派基底檔案名，方法是移除預設資源識別碼（IDB_BITMAP1）中的前四個字元（"IDB_"），然後新增適當的延伸模組。 在此範例中，影像的檔案名會是*BITMAP1 .bmp*。 您可以將它重新命名為*MYBITMAP1。*|
   |**高度**|設定影像的高度（以圖元為單位）。 預設值為48。<br/><br/>影像已裁剪，或在現有影像下方加入了空格。|
   |**識別碼**|設定資源的識別碼。<br/><br/>針對影像，Microsoft Visual Studio 預設會指派數列中的下一個可用識別碼： IDB_BITMAP1、IDB_BITMAP2 等等。 圖示和游標會使用類似的名稱。|
   |**調色**|變更色彩屬性。<br/><br/>按兩下以選取色彩，並顯示 [[自訂色彩選取器] 對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 在適當的文字方塊中輸入 RGB 或 HSL 值，以定義色彩。|
   |**SaveCompressed**|指出影像是否為壓縮格式。 這個屬性是唯讀的。<br/><br/>Visual Studio 不允許您以壓縮格式儲存影像，因此針對在 Visual Studio 中建立的任何影像，此屬性將會是**False**。 如果您在 Visual Studio 中開啟壓縮的影像（在另一個程式中建立），此屬性將會是**True**。 如果您使用 Visual Studio 儲存壓縮的影像，它將會解壓縮，而此屬性會還原為**False**。|
   |**寬度**|設定影像的寬度（以圖元為單位）。 點陣圖的預設值是48。<br/><br/>影像會裁剪，或將空格新增至現有影像的右邊。|

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[圖示影像編輯器](../windows/image-editor-for-icons.md)<br/>
[如何：建立圖示或其他影像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：使用繪圖工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用色彩](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>