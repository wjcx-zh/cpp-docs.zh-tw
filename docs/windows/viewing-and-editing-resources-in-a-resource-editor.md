---
title: 檢視和編輯資源在資源編輯器 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
ms.openlocfilehash: 02ab58d37f3f188c3d65740b218cb9b2ac799714
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742657"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor-c"></a>檢視和編輯資源在資源編輯器 （c + +）

每個資源類型都有**資源**專屬於該資源類型的編輯器。 您可以重新排列、 調整大小、 新增控制項和功能，或修改其資源使用相關聯的編輯器的外觀。 您也可以編輯中的資源[文字格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)並[二進位格式](../windows/opening-a-resource-for-binary-editing.md)。

某些資源類型是個別的檔案，可以匯入和使用各種方式;這些包括點陣圖、 圖示、 游標、 工具列和 html 檔案。 這類資源的檔案名稱和[資源識別元](../windows/symbols-resource-identifiers.md)。 其他項目，例如對話方塊、 功能表和 Win32 專案中的字串資料表存在於只為一部分的資源指令碼 (.rc) 檔或資源範本 (.rct) 檔。

> [!NOTE]
> 資源的屬性[可以使用 [屬性] 視窗來修改](../windows/changing-the-properties-of-a-resource.md)。

## <a name="win32-resources"></a>Win32 資源

您可以存取中的 Win32 資源[資源檢視](../windows/resource-view-window.md)窗格。

### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在資源編輯器中檢視的 Win32 資源

1. 選取 [**資源檢視**從**檢視**功能表。

1. 如果**資源檢視**] 視窗不是最上層視窗中，選取**資源檢視**將它顯示在頂端的索引標籤。

1. 從**資源檢視**，展開包含您想要檢視的資源的專案的資料夾。 例如，如果您想要檢視的對話方塊資源，依序展開 **] 對話方塊**資料夾。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 比方說，按兩下資源**IDD_ABOUTBOX**。

   資源會在適當的編輯器中開啟。 比方說，對話方塊資源的資源內，開啟 **] 對話方塊**編輯器。

   您也可以[檢視 （資源指令碼）.rc 檔中的資源，而不需要開啟任何專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

### <a name="to-delete-an-existing-win-32-resource"></a>若要刪除現有的 Win 32 資源

1. 在 [**資源檢視**，依序展開 [資源類型的節點。

2. 以滑鼠右鍵按一下您想要刪除，然後選擇 [的資源**刪除**從捷徑功能表。

   > [!NOTE]
   > 您可以刪除資源，當您在專案外部的文件視窗中開啟.rc 檔時，請使用相同的捷徑功能表命令。

## <a name="resources-in-managed-projects"></a>在 Managed 專案中的資源

因為 managed 的專案不使用資源指令碼檔案，您必須開啟您的資源**方案總管] 中**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器不支援編輯內嵌的資源。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>若要在資源編輯器中檢視受管理的資源

在 [**方案總管**，按兩下資源，例如**Bitmap1.bmp**。

   資源會在適當的編輯器中開啟。

### <a name="to-delete-an-existing-managed-resource"></a>若要刪除現有的受控的資源

在 [**方案總管**，以滑鼠右鍵按一下您想要刪除，然後選擇 [的資源**刪除**快顯功能表中。

## <a name="changing-the-properties-of-resources"></a>變更資源的屬性

### <a name="to-edit-the-properties-of-a-resource"></a>編輯資源的屬性

1. 在 [[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下您想要編輯，然後選擇的資源**屬性**從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，變更您的資源的屬性。

### <a name="to-undo-a-change-made-to-the-properties-of-a-resource"></a>若要復原資源的屬性所做的變更

1. 請確定您的資源的焦點**資源檢視**。

1. 選擇**恢復**從**編輯**功能表。

## <a name="previewing-resources"></a>預覽資源

預覽您的資源，可讓您檢視圖形化的資源，而不需要開啟它們。 預覽功能也適用於可執行檔的資源識別元變更為 [數字，因為編譯它們後。 通常這些數值識別項未提供足夠的資訊，因為預覽的資源可協助您快速找出它們。

您可以預覽的下列資源類型的視覺化配置：

- Bitmap

- 對話方塊

- 圖示

- 功能表

- Cursor

- 工具列

視覺預覽函式不適用於加速器、 資訊清單、 字串資料表及版本資訊資源。

### <a name="to-preview-resources"></a>若要預覽資源

1. 在 [資源檢視](../windows/resource-view-window.md)或 [文件] 視窗中，選取您的資源，例如**IDD_ABOUTBOX**。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 [[屬性 視窗](/visualstudio/ide/reference/properties-window)，選取**屬性頁**] 按鈕。

   \-或-

   在 **檢視**功能表上，選取**屬性頁**。

   **屬性頁**資源隨即開啟並顯示該資源的預覽。 然後您可以使用**向上**並**向下**方向鍵可瀏覽樹狀目錄控制項中**資源檢視**或文件視窗。 **屬性頁**會保持開啟，並顯示任何有焦點，而且可預覽的資源。

> [!NOTE]
> 若要預覽資源需要 Win32。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[如何：在專案外開啟資源指令碼檔 (獨立式)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[資源編輯器](../windows/resource-editors.md)