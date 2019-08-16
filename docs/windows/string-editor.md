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
ms.openlocfilehash: 996e5f132e5cfa33c39c4cc3ddbeb692f41925bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514724"
---
# <a name="string-editor-c"></a>字串編輯器 (C++)

字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。

在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。

字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 (及其他資源)，就能當地語系化應用程式，無須變更原始程式碼。 這種情況比手動尋找和取代原始檔中的各種字串更為理想。

> [!NOTE]
> Windows 不允許建立空的字串資料表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。

## <a name="how-to"></a>如何

**字串編輯器**可讓您:

### <a name="to-find-a-string-resource-in-the-string-table"></a>尋找字串資料表中的字串資源

1. 按兩下 [string] 資料表中的圖示, 即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 移至功能表 [**編輯** > ] [**尋找和取代**], 然後選擇 [**尋找**]。

1. 在 [**尋找目標**] 方塊中, 從下拉式清單中選取先前的搜尋字串, 或輸入您想要尋找之字串的標題文字或資源識別碼。

1. 選取任何 [**尋找**] 選項, 然後選取 [**尋找下一個]** 。

> [!TIP]
> 若要在搜尋檔時使用[正則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio), 請使用 [**編輯**] 功能表中的 [檔案**中尋找**] 命令。
>
> 輸入正則運算式以符合模式, 或選取 [**尋找目標**] 方塊右邊的按鈕, 以顯示一般搜尋運算式的清單。 當您從這個清單中選取運算式時, 它會取代為 [**尋找目標**] 方塊中的搜尋文字。
>
> 如果您使用正則運算式, 請務必**使用:[正**則運算式] 核取方塊已選取。

### <a name="to-add-or-delete-a-string-resource"></a>若要新增或刪除字串資源

您可以使用 [**字串編輯器**], 快速地將專案插入或刪除到字串資料表中。 新的字串會放在資料表的結尾, 並提供下一個可用的識別碼。 您可以視需要編輯[屬性視窗](/visualstudio/ide/reference/properties-window)中的 [**識別碼**]、[**值**] 或 [**標題**] 屬性。

[**字串編輯器**] 會確保您不會使用已在使用中的識別碼。 如果您選取已在使用中的識別碼,**字串編輯器**將會通知您, 然後指派一般唯一識別碼 (例如`IDS_STRING58113`)。

#### <a name="to-add-a-string-table-entry"></a>若要加入字串資料表專案

1. 按兩下 [string] 資料表中的圖示, 即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 以滑鼠右鍵按一下字串資料表, 然後選擇 [**新字串**]。

1. 在 [**字串編輯器**] 中, 從 [**識別碼**] 下拉式清單中選取**識別碼**, 或直接在 [就地] 中輸入*識別碼*。

1. 視需要編輯此**值**。

1. 輸入**標題**的專案。

   > [!NOTE]
   > Windows 字串資料表中不允許 Null 字串。 如果您在字串資料表中建立具有 null 字串的專案, 您會收到一則訊息, 要求您**輸入此資料表專案的字串**。

#### <a name="to-delete-a-string-table-entry"></a>若要刪除字串資料表專案

選取您想要刪除的專案, 然後執行下列其中一項動作:

- 移至功能表 [**編輯** > ] [**刪除**]。

- 以滑鼠右鍵按一下要刪除的字串, 然後選擇 [**刪除**]。

- 按下**Delete**鍵。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>將字串從一個資源腳本檔案移至另一個

1. [開啟兩個 .rc 檔中的字串資料表](../windows/how-to-create-a-resource-script-file.md)。

1. 以滑鼠右鍵按一下要移動的字串, 然後選擇 [**剪**下]。

1. 將游標放在 [目標**字串編輯器**] 視窗中。

1. 在您要移動字串的 *.rc*檔中, 按一下滑鼠右鍵並選擇 [**貼**上]。

> [!NOTE]
> 如果移動字串的**識別碼**或**值**與目的地檔案中現有的**識別碼**或**值**衝突, 則該**識別碼**或移動字串的**值**都會變更。

### <a name="to-change-the-properties-of-a-string-resource"></a>變更字串資源的屬性

您可以使用就地編輯來變更 [**識別碼**]、[**值**] 和 [**標題**] 屬性。

> [!NOTE]
>  您也可以在[屬性視窗](/visualstudio/ide/reference/properties-window)中編輯字串的屬性。

#### <a name="to-change-a-string-or-its-identifier"></a>若要變更字串或其識別碼

1. 按兩下 [string] 資料表中的圖示, 即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要編輯的字串, 然後按兩下 [**識別碼**]、[**值**] 或 [**標題**] 資料行, 您就可以:

   - 從 [**識別碼**] 下拉式清單中選取**識別碼**, 或直接在 [就地] 中輸入*識別碼*。

   - 在 [**值**] 資料行中輸入不同的數位。

   - 在 [**標題**] 資料行中輸入編輯。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>變更多個字串資源的 caption 屬性

1. 按兩下 [string] 資料表中的圖示, 即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要變更的字串, 方法是按住**Ctrl**鍵並選取每一個。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中, 為您要變更的屬性輸入新的值。

1. 按 **Enter** 鍵。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>將格式或特殊字元加入至字串資源

1. 按兩下 [string] 資料表中的圖示, 即可開啟[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您要修改的字串。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中, 將下面列出的任何標準逸出序列新增至 [**標題**] 方塊中的文字, 然後按**enter**鍵。

   |若要取得此 。|輸入此 。|
   |-----------------|---------------|
   | 換行 | \\位 |
   | 歸位字元 | \\r |
   | 索引標籤 | \\而已 |
   | 反斜線 (\\) | \\\\ |
   | ASCII 字元 | \\ddd (八進位標記法) |
   | 警示 (鐘) | \\為 |

   > [!NOTE]
   > **字串編輯器**不支援完整的轉義 ASCI 字元集。 您只能使用上述所列的版本。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)
[字串](/windows/win32/menurc/strings)<br/>
[關於字串](/windows/win32/menurc/about-strings)<br/>
[自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)