---
title: 資源編輯器（C++）
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
ms.openlocfilehash: 5f12b126db7c0e040f06640d3ecd201007d73968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167884"
---
# <a name="resource-editors-c"></a>資源編輯器（C++）

資源編輯器是建立或修改包含在 Visual Studio 專案中之資源的特殊環境。 Visual Studio 資源編輯器會共用技術和介面，協助您快速輕鬆地建立及修改應用程式資源。 資源編輯器可讓您在適當的編輯器中檢視和編輯資源以及預覽資源。

當您建立或開啟資源時，適當的編輯器會自動開啟。

> [!NOTE]
> 因為 managed 專案不使用資源腳本檔案，所以您必須從**方案總管**開啟資源。 您可以使用[影像編輯器](../windows/image-editor-for-icons.md)和[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

|使用...|編輯...|
|----------------|----------------|
|[快速鍵編輯器](../windows/accelerator-editor.md)|Visual Studio C++專案中的快速鍵對應表。|
|[二進位編輯器](binary-editor.md)|Visual C++、Visual Basic 或 Visual C# 專案的二進位資料資訊和自訂資源。|
|[對話方塊編輯器](../windows/dialog-editor.md)|Visual Studio C++專案中的對話方塊。|
|[影像編輯器](../windows/image-editor-for-icons.md)|Visual C++、Visual Basic 或 Visual C# 專案的點陣圖、圖示、游標和其他影像檔。|
|[功能表編輯器](../windows/menu-editor.md)|Visual Studio C++專案中的功能表資源。|
|[功能區編輯器](../mfc/ribbon-designer-mfc.md)|MFC 專案中的功能區資源。|
|[字串編輯器](../windows/string-editor.md)|Visual Studio C++專案中的字串資料表。|
|[工具列編輯器](../windows/toolbar-editor.md)|Visual Studio C++專案中的工具列資源。 [**工具列編輯器**] 是**影像編輯器**的一部分。|
|[版本資訊編輯器](../windows/version-information-editor.md)|Visual Studio C++專案中的版本資訊。|

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱[如何：建立資源](../windows/how-to-create-a-resource-script-file.md)。

## <a name="view-and-edit-resources"></a>查看和編輯資源

每個資源類型都有該資源類型特有的資源編輯器。 您可以使用相關聯的編輯器來重新排列、調整大小、加入控制項和功能，或修改資源的各個層面。 您也可以使用[文字格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)和[二進位格式](../windows/opening-a-resource-for-binary-editing.md)來編輯資源。

某些資源類型是個別的檔案，可以用各種方式匯入和使用;其中包括點陣圖、圖示、游標、工具列和 html 檔案。 這類資源具有檔案名和[資源識別碼](../windows/symbols-resource-identifiers.md)。 其他（例如對話方塊、功能表和 Win32 專案中的字串資料表）只存在於資源腳本（.rc）檔案或資源範本（.rct）檔案的一部分。

您也可以在專案外部編輯資源，而不需開啟專案，請參閱[如何：建立資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

> [!NOTE]
> 您可以使用 [**屬性**] 視窗來修改資源的屬性。

- 若要編輯資源的屬性，請在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下您要編輯的資源，然後選擇 [**屬性**]。  然後，在 [屬性視窗](/visualstudio/ide/reference/properties-window)中，變更資源的屬性。

- 若要復原對資源的屬性所做的變更，請確定您的資源焦點在**資源檢視**，然後從 [**編輯**] 功能表中選擇 [**復原**]。

### <a name="win32-resources"></a>Win32 資源

您可以在 [[資源檢視](how-to-create-a-resource-script-file.md#create-resources)] 窗格中存取 Win32 資源。

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在資源編輯器中查看 Win32 資源

1. 移至功能表**視圖** > **其他 Windows** > **資源檢視**。

1. 如果 [**資源檢視**] 視窗不是最上方的視窗，請選取 [**資源檢視**] 索引標籤，將其帶到頂端。

1. 從 [**資源檢視**] 中，展開包含您想要查看之資源的專案資料夾。 例如，如果您想要查看對話方塊資源，請展開 [**對話方塊]** 資料夾。

1. 按兩下資源，例如**IDD_ABOUTBOX**。

   資源會在適當的編輯器中開啟。 例如，針對對話資源，資源會在**對話方塊編輯器**中開啟。

#### <a name="to-delete-an-existing-win32-resource"></a>若要刪除現有的 Win32 資源

1. 在**資源檢視**中，展開資源類型的節點。

1. 以滑鼠右鍵按一下您想要刪除的資源，然後選擇 [**刪除**]。

> [!TIP]
> 當您在專案之外的文件視窗中開啟 .rc 檔案時，也可以使用這個方法。

### <a name="managed-project-resources"></a>受控專案資源

因為 managed 專案不使用資源腳本檔案，所以您必須從**方案總管**開啟資源。 使用[影像編輯器](../windows/image-editor-for-icons.md)和[二進位編輯器](binary-editor.md)來處理 managed 專案中的資源檔。 您想要編輯的任何受管理資源都必須連結資源，而且 Visual Studio 資源編輯器不支援編輯內嵌資源。

- 若要在資源編輯器中查看 managed 資源，請在**方案總管**中，按兩下資源（例如*Bitmap1*），然後在適當的編輯器中開啟資源。

- 若要刪除現有的受控資源，請在**方案總管**中，以滑鼠右鍵按一下您想要刪除的資源，然後選擇 [**刪除**]。

## <a name="preview-resources"></a>預覽資源

預覽您的資源，讓您不需要開啟圖形資源即可加以流覽。 在編譯後，預覽也適用于可執行檔，因為資源識別碼會變更為數位。 因為這些數值識別碼通常不會提供足夠的資訊，所以預覽資源可協助您快速識別它們。

下列資源類型提供視覺化版面配置預覽：點陣圖、對話方塊、圖示、功能表、游標、工具列

下列資源不提供視覺化預覽：快速鍵、資訊清單、字串表、版本資訊

> [!NOTE]
> 若要預覽資源，需要 Win32。

### <a name="to-preview-resources"></a>預覽資源

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)或文件視窗中，選取您的資源，例如， **IDD_ABOUTBOX**。

1. 在 [屬性視窗](/visualstudio/ide/reference/properties-window)中，選取 **屬性頁** 按鈕。

   > [!TIP]
   > 使用快捷方式，移至功能表**視圖** > **屬性頁**。

   資源的**屬性**頁隨即開啟，顯示該資源的預覽。 您可以使用**向上**箭號和**向下**鍵，在**資源檢視**或文件視窗中流覽樹狀目錄控制項。 **屬性**頁會保持開啟狀態，並顯示具有焦點且可以預覽的任何資源。

## <a name="requirements"></a>需求

None

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
