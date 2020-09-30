---
title: '二進位編輯器 (c + +) '
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 078d702232cde49a4666551a8d9fcbb320173450
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503533"
---
# <a name="binary-editor-c"></a>二進位編輯器 (c + +) 

> [!CAUTION]
> 在 **二進位編輯器** 中編輯對話方塊、影像或功能表等資源是很危險的。 不正確的編輯可能會損毀資源，讓它在原生編輯器中無法讀取。

**二進位編輯器**可讓您以十六進位或 ASCII 格式編輯二進位層級的任何資源。 您也可以使用 [[尋找命令]](/visualstudio/ide/reference/find-command) 搜尋 ASCII 字串或十六進位位元組。 只有當您需要對自訂資源或 Visual Studio 環境不支援的資源類型進行查看或變更時，才使用 **二進位編輯器** 。 **二進位編輯器**無法在 Express 版本中使用。

- 若要在新檔案上開啟**二進位編輯器**，請移至 **[功能表檔案**  >  **新**檔]  >  ** **，選取您要編輯的檔案類型，然後選取 [**開啟**] 按鈕旁的下拉箭號，然後選擇 [**使用**  >  **二進位編輯器**開啟]。

- 若要在現有的檔案上開啟**二進位編輯器**，請移**至功能表檔案**  >  **開啟**  >  檔案，選取您要編輯的**檔案，** 然後選取 [**開啟**] 按鈕旁的下拉箭號，然後選擇 [**使用**  >  **二進位編輯器**開啟]。

   ![二進位編輯器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   **二進位編輯器**中顯示之對話方塊的二進位資料

只有特定的 ASCII 值會以 **二進位編輯器** 表示， (0X20 到 0x7E) 。 擴充字元在 **二進位編輯器**的右面板 ASCII 值區段中會顯示為句號。 可列印的字元是從32到126的 ASCII 值。

> [!TIP]
> 使用 **二進位編輯器**時，在許多情況下，您可以按一下滑鼠右鍵，顯示資源特定命令的快捷方式功能表。 可用的命令取決於游標所指項目。 例如，如果您以滑鼠右鍵按一下，並使用選取的十六進位值指向 **二進位編輯器** ，快捷方式功能表會顯示 **剪**下、 **複製**和 **貼** 上命令。

## <a name="how-to"></a>作法

**二進位編輯器**可讓您：

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>開啟 Windows 桌面資源進行二進位編輯

1. 在 [資源檢視] [](how-to-create-a-resource-script-file.md#create-resources)中，選取您要編輯的特定資源檔。

1. 以滑鼠右鍵按一下資源，然後選取 [ **開啟二進位資料**]。

> [!NOTE]
> 如果您使用 **資源檢視** 視窗開啟具有 Visual Studio 無法辨識之格式的資源（例如 RCDATA 或自訂資源），系統就會在 **二進位編輯器**中自動開啟該資源。

### <a name="to-open-a-managed-resource-for-binary-editing"></a>開啟 Managed 資源進行二進位編輯

1. 在 **方案總管**中，選取您要編輯的特定資源檔。

1. 以滑鼠右鍵按一下資源，然後選取 [ **開啟方式**]。

1. 在 [開啟方式] **** 對話方塊中，選擇 [二進位編輯器] ****。

> [!NOTE]
> 您可以使用 [影像編輯器](image-editor-for-icons.md) 和 **二進位編輯器** 來處理 managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

### <a name="to-edit-a-resource"></a>編輯資源

如果您想要在已在另一個編輯器視窗中編輯的資源上使用 **二進位編輯器** ，請先關閉其他編輯器視窗。

1. 選取您要編輯的位元組。

   **Tab**鍵會在**二元編輯器**的十六進位和 ASCII 區段之間移動焦點。 您可以使用 **Page Up** 和 **page Down** 鍵，一次在一個畫面上移動資源。

1. 輸入新值。

   值會立即在十六進位和 ASCII 區段中變更，而焦點會移至行中的下一個值。

> [!NOTE]
> 當您關閉編輯器時， **二進位編輯器** 會自動接受變更。

### <a name="to-find-binary-data"></a>尋找二進位資料

您可以搜尋 ASCII 字串或十六進位位元組。 例如，若要尋找 *hello*，您可以搜尋字串 *Hello* 或其十六進位值 *48 65 6C 6C 6F*。

1. 移至功能表 [**編輯**  >  [尋找](/visualstudio/ide/reference/find-command)]。

1. 在 [ **尋找目標** ] 方塊中，從下拉式清單中選取先前的搜尋字串，或輸入您想要尋找的資料。

1. 選取任何 [ **尋找** ] 選項，然後選擇 [ **尋找下一個]**。

### <a name="to-create-a-new-custom-or-data-resource"></a>建立新的自訂或資料資源

您可以建立新的自訂或資料資源，方法是使用一般資源腳本 ( .rc) 檔案語法，然後以滑鼠右鍵按一下您在 **方案總管** 中的專案，然後選取 [ **資源包含**]，以建立新的自訂或資料資源。

1. [建立 .rc 檔](how-to-create-a-resource-script-file.md) ，其中包含自訂或資料資源。

   您可以在 .rc 檔中，將自訂資料輸入為以 Null 結尾並加上引號的字串，或是十進位、十六進位或八進位格式的整數。

1. 在 **方案總管**中，以滑鼠右鍵按一下專案的 .rc 檔，然後選取 [ **資源包含**]。

1. 在 [ **編譯時間** 指示詞] 方塊中，輸入一個語句，以 `#include` 提供包含您自訂資源的檔案名，例如：

    ```cpp
    #include mydata.rc
    ```

   請確定您輸入的語法和拼字正確。 [ **編譯時間** 指示詞] 方塊的內容會與您輸入時完全一樣地插入至資源腳本檔案。

1. 選取 **[確定]** 以記錄您的變更。

建立自訂資源的另一種方式是將外部檔案匯入為自訂資源，請參閱 [如何：管理資源](./how-to-copy-resources.md)。

> [!NOTE]
> 建立新的自訂或資料資源需要 Win32。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[資源編輯器](resource-editors.md)
