---
title: 資源編輯器 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: aeeca87ceb5b2c5e54da7087b5020ccbc1c39039
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320805"
---
# <a name="resource-editors-c"></a>資源編輯器 （c + +）

A**資源**編輯器是一個特製化的環境，用於建立或修改 Visual Studio 專案中包含的資源。 Visual Studio 資源編輯器會共用技術和介面，協助您快速輕鬆地建立及修改應用程式資源。 資源編輯器可讓您檢視和編輯適當的編輯器和預覽資源中的資源。

當您建立或開啟資源時，適當的編輯器會自動開啟。

> [!NOTE]
> 因為 managed 的專案不會使用資源指令碼檔案，您必須開啟您的資源**方案總管 中**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

|使用...|編輯...|
|----------------|----------------|
|[快速鍵編輯器](../windows/accelerator-editor.md)|Visual C++ 專案中的快速鍵對應表。|
|[Binary Editor](binary-editor.md)|Visual C++、Visual Basic 或 Visual C# 專案的二進位資料資訊和自訂資源。|
|[對話方塊編輯器](../windows/dialog-editor.md)|Visual C++ 專案中的對話方塊。|
|[Image Editor](../windows/image-editor-for-icons.md)|Visual C++、Visual Basic 或 Visual C# 專案的點陣圖、圖示、游標和其他影像檔。|
|[功能表編輯器](../windows/menu-editor.md)|Visual C++ 專案中的功能表資源。|
|[功能區編輯器](../mfc/ribbon-designer-mfc.md)|MFC 專案中的功能區資源。|
|[字串編輯器](../windows/string-editor.md)|Visual C++ 專案中的字串資料表。|
|[工具列編輯器](../windows/toolbar-editor.md)|Visual C++ 專案中的工具列資源。 工具列編輯器是影像編輯器的一部分。|
|[版本資訊編輯器](../windows/version-information-editor.md)|Visual C++ 專案中的版本資訊。|

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

## <a name="view-and-edit-resources"></a>檢視和編輯資源

每個資源類型都有**資源**專屬於該資源類型的編輯器。 您可以重新排列、 調整大小、 新增控制項和功能，或修改其資源使用相關聯的編輯器的外觀。 您也可以編輯中的資源[文字格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)並[二進位格式](../windows/opening-a-resource-for-binary-editing.md)。

某些資源類型是個別的檔案，可以匯入和使用各種方式;這些包括點陣圖、 圖示、 游標、 工具列和 html 檔案。 這類資源的檔案名稱和[資源識別元](../windows/symbols-resource-identifiers.md)。 其他項目，例如對話方塊、 功能表和 Win32 專案中的字串資料表存在於只為一部分的資源指令碼 (.rc) 檔或資源範本 (.rct) 檔。

資源也可以編輯專案外，請參閱[How to:開啟資源指令碼檔 （獨立式） 在專案外的](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

> [!NOTE]
> 資源的屬性[可以使用 [屬性] 視窗來修改](../windows/changing-the-properties-of-a-resource.md)。

### <a name="to-edit-the-properties-of-a-resource"></a>編輯資源的屬性

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下您想要編輯，然後選擇的資源**屬性**從捷徑功能表。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，變更您的資源的屬性。

### <a name="to-undo-a-change-made-to-the-properties-of-a-resource"></a>若要復原資源的屬性所做的變更

1. 請確定您的資源的焦點**資源檢視**。

1. 選擇**恢復**從**編輯**功能表。

### <a name="win32-resources"></a>Win32 資源

您可以存取中的 Win32 資源[資源檢視](../windows/resource-view-window.md)窗格。

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在資源編輯器中檢視的 Win32 資源

1. 選取 **資源檢視**從**檢視**功能表。

1. 如果**資源檢視** 視窗不是最上層視窗中，選取**資源檢視**將它顯示在頂端的索引標籤。

1. 從**資源檢視**，展開包含您想要檢視的資源的專案的資料夾。 例如，如果您想要檢視的對話方塊資源，依序展開**對話方塊**資料夾。

1. 比方說，按兩下資源**IDD_ABOUTBOX**。

   資源會在適當的編輯器中開啟。 比方說，對話方塊資源的資源內，開啟**對話方塊**編輯器。

   您也可以[檢視 （資源指令碼）.rc 檔中的資源，而不需要開啟任何專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

#### <a name="to-delete-an-existing-win-32-resource"></a>若要刪除現有的 Win 32 資源

1. 在 **資源檢視**，依序展開 資源類型的節點。

1. 以滑鼠右鍵按一下您想要刪除，然後選擇 的資源**刪除**從捷徑功能表。

   > [!NOTE]
   > 您可以刪除資源，當您在專案外部的文件視窗中開啟.rc 檔時，請使用相同的捷徑功能表命令。

### <a name="managed-project-resources"></a>受管理的專案資源

因為 managed 的專案不使用資源指令碼檔案，您必須開啟您的資源**方案總管 中**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器不支援編輯內嵌的資源。

- 若要檢視中的受管理的資源在資源編輯器中，**方案總管**，按兩下資源，例如*Bitmap1.bmp*。

   資源會在適當的編輯器中開啟。

- 若要刪除現有的 managed 的資源，在**方案總管**，以滑鼠右鍵按一下您想要刪除，然後選擇 的資源**刪除**從捷徑功能表。

## <a name="preview-resources"></a>預覽資源

預覽您的資源，可讓您檢視圖形化的資源，而不需要開啟它們。 預覽功能也適用於可執行檔的資源識別元變更為 數字，因為編譯它們後。 通常這些數值識別項未提供足夠的資訊，因為預覽的資源可協助您快速找出它們。

您可以預覽的下列資源類型的視覺化配置：點陣圖、 對話方塊、 圖示、 功能表、 游標、 工具列

視覺預覽函式不會套用至資源：加速器、 資訊清單、 字串資料表名稱和版本資訊

> [!NOTE]
> 若要預覽資源需要 Win32。

### <a name="to-preview-resources"></a>若要預覽資源

1. 在 [資源檢視](../windows/resource-view-window.md)或 [文件] 視窗中，選取您的資源，例如`IDD_ABOUTBOX`。

1. 在 [[屬性 視窗](/visualstudio/ide/reference/properties-window)，選取**屬性頁**] 按鈕。

   > [!TIP]
   > 捷徑，在**檢視**功能表上，選取**屬性頁**。

   **屬性頁**資源隨即開啟並顯示該資源的預覽。 然後您可以使用**向上**並**向下**方向鍵可瀏覽樹狀目錄控制項中**資源檢視**或文件視窗。 **屬性頁**會保持開啟，並顯示任何有焦點，而且可預覽的資源。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源識別項 （符號）](../windows/symbols-resource-identifiers.md)<br/>