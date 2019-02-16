---
title: 二進位編輯器 （c + +）
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
ms.openlocfilehash: 2a3ff3d89c809f57ea3ddbd70d5664fc8d13cec4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320818"
---
# <a name="binary-editor-c"></a>二進位編輯器 （c + +）

> [!WARNING]
> **二進位編輯器**不適用於 Express 版本。

二進位編輯器允許您在二進位層級，以十六進位或 ASCII 格式編輯任何資源。 您也可以使用 [[尋找命令]](/visualstudio/ide/reference/find-command) 搜尋 ASCII 字串或十六進位位元組。 您應該使用**二進位**編輯器，您需要檢視或次要時，才會變更為自訂資源 」 或 「 不支援的 Visual Studio 環境的資源類型。

若要開啟 **二進位編輯器**，先選擇**檔案** > **新增** > **檔案**從主功能表中，選取您想要編輯，然後選取旁邊的向下箭號的檔案**開放**按鈕，然後選擇**開啟** > **二進位編輯器**。

> [!CAUTION]
> 在二進位編輯器中編輯諸如對話方塊、影像或功能表等資源，是很危險的事。 不正確的編輯可能會損毀資源，讓它在原生編輯器中無法讀取。

![二進位編輯器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
二進位編輯器中所顯示之對話方塊的二進位資料

二進位編輯器中只會表示特定 ASCII 值 (0x20 到 0x7E)。 擴充字元會在二進位編輯器的 [ASCII 值] 區段 (右窗格) 中顯示為句號。 「可列印」字元是 ASCII 值 32 到 126。

> [!TIP]
> 在使用時**二進位**編輯器，在許多情況下，您可以按一下滑鼠右鍵以顯示資源特定命令的捷徑功能表。 可用的命令取決於游標所指項目。 例如，如果您按一下指向時**二進位**含有所選十六進位值編輯器中，快顯功能表會顯示**剪下**，**複製**，和**貼上**命令。

## <a name="how-to"></a>操作說明

**二進位**編輯器可讓您：

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>開啟 Windows 桌面資源進行二進位編輯

1. 在 [[資源檢視]](../windows/resource-view-window.md)中，選取您要編輯的特定資源檔。

1. 以滑鼠右鍵按一下資源，然後從捷徑功能表按一下 [開啟二進位資料]  。

   > [!NOTE]
   > 如果您使用[資源檢視](../windows/resource-view-window.md)視窗開啟，Visual Studio 無法辨識格式 （例如 RCDATA 或自訂資源），該資源的資源會自動以開啟**二進位**編輯器。

### <a name="to-open-a-managed-resource-for-binary-editing"></a>開啟 Managed 資源進行二進位編輯

1. 在 [**方案總管] 中**，選取您想要編輯的特定資源檔。

1. 以滑鼠右鍵按一下資源，然後從捷徑功能表選擇 [開啟方式]  。

1. 在 [開啟方式]  對話方塊中，選擇 [二進位編輯器] 。

   > [!NOTE]
   > 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

> [!NOTE]
> 如果您想要使用**二進位**編輯器已經在另一個編輯器視窗中，編輯的資源上先關閉其他編輯器視窗。

### <a name="to-edit-a-resource"></a>編輯資源

1. 選取您想要編輯的位元組。

   ** 索引標籤**鍵將焦點移十六進位和 ASCII 區段之間**二進位**編輯器。 您可以使用**Page Up**並**Page down 鍵**金鑰一次移動一個螢幕的資源。

1. 輸入新值。

   值會立即變更十六進位和 ASCII 區段中，焦點會轉移至行中的下一個值。

   > [!NOTE]
   > **二進位**編輯器會接受變更的自動關閉編輯器時。

### <a name="to-find-binary-data"></a>若要尋找二進位資料

您可以搜尋 ASCII 字串或十六進位位元組。 例如，若要尋找"Hello"，您可以搜尋字串"Hello"或"48 65 6C 6c 6F 」 （十六進位的對等）。

1. 從**編輯**功能表上，選擇[尋找](/visualstudio/ide/reference/find-command)。

1. 在  **Find What**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找的資料。

1. 選取任一**尋找**選項，然後選擇**尋找下一個**。

### <a name="to-create-a-new-custom-or-data-resource"></a>建立新的自訂或資料資源

您可以藉由將資源放在包含該檔案使用一般資源指令碼 (.rc) 檔語法，個別檔案中，然後以滑鼠右鍵按一下您的專案中建立新的自訂或資料資源**方案總管 中**，然後按一下**資源包括**快顯功能表。

1. [建立 .rc 檔](../windows/how-to-create-a-resource-script-file.md) ，其中包含自訂或資料資源。

   您可以在 .rc 檔中，將自訂資料輸入為以 Null 結尾並加上引號的字串，或是十進位、十六進位或八進位格式的整數。

1. 在 **方案總管**中，以滑鼠右鍵按一下專案的 .rc 檔，然後按一下捷徑功能表中的 [資源包含]  。

1. 在 **編譯時間指示詞**方塊中，輸入`#include`陳述式，為包含您的自訂資源檔案的名稱。 例如: 

    ```cpp
    #include mydata.rc
    ```

   請確定您輸入的語法和拼字正確。 [編譯時期指示詞]  方塊的內容會完全依照您的輸入插入資源指令碼檔。

1. 選取 **確定**來記錄您的變更。

另一種建立自訂資源的方式是匯入外部檔案作為自訂資源。 如需詳細資訊，請參閱 [匯入及匯出資源](../windows/how-to-import-and-export-resources.md)。

> [!NOTE]
> 建立新的自訂或資料資源需要 Win32。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)