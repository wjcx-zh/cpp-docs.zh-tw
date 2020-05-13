---
title: 字串編輯器 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370232"
---
# <a name="string-editor-c"></a>字串編輯器 (C++)

字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。

在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。

字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 (及其他資源)，就能當地語系化應用程式，無須變更原始程式碼。 這種情況比手動查找和替換原始檔中的各種字串更可取。

> [!NOTE]
> Windows 不允許創建空字串表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。

## <a name="how-to"></a>作法

**字串編輯器**讓您能夠:

### <a name="to-find-a-string-resource-in-the-string-table"></a>在字串表中尋找字串資源

1. 通過按兩下資源[檢視中](how-to-create-a-resource-script-file.md#create-resources)的圖示打開字串表。

1. 跳到選單 **「編輯** > **搜尋和取代**」並選擇 **「尋找」**。

1. 在「**尋找什麼」** 框中,從下拉清單中選擇以前的搜尋字串,或鍵入要查找的字串的標題文本或資源標識符。

1. 選擇任何 **「尋找」** 選項,然後選擇 **「尋找下一步**」 。

> [!TIP]
> 要在搜尋檔案時使用[正則表示式](/visualstudio/ide/using-regular-expressions-in-visual-studio),請使用 **「編輯」** 選單**中的「在檔案中尋找」** 命令。
>
> 鍵入正規表示式以符合模式或選擇「**尋找什麼」** 框右側的按鈕以顯示常規搜尋表達式的清單。 從清單中選擇表示式時,該表示式將取代為「**尋找什麼」** 框中的搜尋文字。
>
> 如果使用正則運算式,請確保選擇了 **"使用:正則運算式**"複選框。

### <a name="to-add-or-delete-a-string-resource"></a>新增或移除字串資源

您可以使用**字串編輯器**快速將條目插入或刪除到字串表中。 新字串放在表的末尾,並給出下一個可用標識碼。 您可以根據需要在[「屬性」 視窗中](/visualstudio/ide/reference/properties-window)編輯**ID、****值**或**標題**屬性。

**字串編輯器**確保不使用已在使用的識別碼。 如果選擇已在使用的識別碼,**字串編輯器**將通知您,然後配置一般的唯一`IDS_STRING58113`ID,例如 。

#### <a name="to-add-a-string-table-entry"></a>新增字串表項目

1. 通過按兩下資源[檢視中](how-to-create-a-resource-script-file.md#create-resources)的圖示打開字串表。

1. 右鍵按一下字串表並選擇 **「新建字串**」。

1. 在**字串編輯器**中,從**ID**下拉清單中選擇**ID**或直接鍵入正確的*ID。*

1. 如有必要,編輯**值**。

1. 鍵入**標題**的項目 。

   > [!NOTE]
   > Windows 字串表中不允許使用空字串。 如果在字串表中建立一個空字串的項目,您會收到一條訊息,要求您**為此表格目輸入字串**。

#### <a name="to-delete-a-string-table-entry"></a>刪除字串表條目

選擇要刪除的項目,並執行以下操作之一:

- 跳到選單 **「編輯** > **刪除**」 。

- 右鍵按一下要刪除的字串,然後選擇 **「刪除**」。

- 按 **"刪除**"鍵。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>將字串從資源文稿檔案移至另一個資源文稿檔案

1. [開啟兩個 .rc 檔案中的字串表](../windows/how-to-create-a-resource-script-file.md)。

1. 右鍵按一下字串以移動並選擇 **「剪切**」 。

1. 將游標放在目標**字串編輯器**視窗中。

1. 在要移動到*的 .rc*檔中,右鍵按下並選擇 **「貼上**」。

> [!NOTE]
> 如果移動字串的**ID**或**值**與目標檔中的現有**ID**或**值**衝突,則該**ID**或行動字串**的值**將發生更改。

### <a name="to-change-the-properties-of-a-string-resource"></a>變更字串資源屬性

可以使用就地編輯來更改**ID、****值**和**標題**屬性。

> [!NOTE]
> 您還可以在[「屬性」視窗中](/visualstudio/ide/reference/properties-window)編輯字串的屬性。

#### <a name="to-change-a-string-or-its-identifier"></a>變更字串或其識別碼

1. 通過按兩下資源[檢視中](how-to-create-a-resource-script-file.md#create-resources)的圖示打開字串表。

1. 選擇要編輯的字串,然後按兩下**ID、****值**或**標題**欄,然後您可以:

   - 從**ID**下拉清單中選擇**ID,** 或直接鍵入正確的*ID。*

   - 在 **"值"** 列中鍵入其他數位。

   - 在 **「標題」** 欄中鍵入編輯。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>變更多個字串資源的標題屬性

1. 通過按兩下資源[檢視中](how-to-create-a-resource-script-file.md#create-resources)的圖示打開字串表。

1. 在選擇每個字串時按住**Ctrl**鍵,選擇要更改的字串。

1. 在["屬性"視窗中](/visualstudio/ide/reference/properties-window),為要更改的屬性鍵入新值。

1. 按 **Enter**。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>加入字串資源加入格式或特殊字元

1. 通過按兩下資源[檢視中](how-to-create-a-resource-script-file.md#create-resources)的圖示打開字串表。

1. 選擇要修改的字串。

1. 在[「屬性」 視窗中](/visualstudio/ide/reference/properties-window),將下面列出的任何標準轉義序列新增到 **「標題」** 框中的文字,然後按**Enter**。

   |為了得到這個...|鍵入此...|
   |-----------------|---------------|
   | 新行 | \\n |
   | 歸位字元 | \\R |
   | 索引標籤 | \\t |
   | 反斜線 (\\) | \\\\ |
   | ASCII 字元 | \\dd(八度表示法) |
   | 警示(鈴) | \\a |

   > [!NOTE]
   > **字串編輯器**不支援完整的轉義 ASCI 字元集。 您只能使用上面列出的那些。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)
[字串](/windows/win32/menurc/strings)<br/>
[關於字串](/windows/win32/menurc/about-strings)<br/>
[自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
