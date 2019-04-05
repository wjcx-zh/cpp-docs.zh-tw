---
title: 字串編輯器 （c + +）
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
ms.openlocfilehash: 47d5835356863383b32baffc4475e01a652e9856
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037181"
---
# <a name="string-editor-c"></a>字串編輯器 （c + +）

字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。

在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。

字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 (及其他資源)，就能當地語系化應用程式，無須變更原始程式碼。 這種情況下會於手動尋找及取代原始程式檔中的各種字串更為理想。

> [!NOTE]
> Windows 不允許建立空的字串資料表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。

## <a name="how-to"></a>如何

**字串值編輯器**可讓您：

### <a name="to-find-a-string-resource-in-the-string-table"></a>若要在字串中尋找的字串資源

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 移至功能表**編輯** > **尋找和取代**，然後選擇**尋找**。

1. 在  **Find What**方塊中，從下拉式清單中，選取先前的搜尋字串或輸入您想要尋找的字串的標題文字 或 資源識別碼。

1. 選取任一**尋找**選項，然後選取**尋找下一個**。

> [!TIP]
> 若要使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)搜尋檔案，當使用**檔案中尋找**命令**編輯**功能表。
>
> 輸入的規則運算式比對模式，或選取右邊的按鈕**Find What**方塊，以顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。
>
> 如果您使用規則運算式時，務必**使用：規則運算式**選取核取方塊。

### <a name="to-add-or-delete-a-string-resource"></a>若要加入或刪除字串資源

您可以快速地插入或刪除字串資料表使用的項目**字串值編輯器**。 新的字串會放在資料表結尾處，並指定下一個可用的識別項。 您可以編輯**識別碼**，**值**，或**標題**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)視。

**字串值編輯器**可確保您不使用已在使用的識別碼。 如果您選取的識別碼已經在使用中，**字串值編輯器**會通知您，然後指派一個泛用的唯一識別碼，例如`IDS_STRING58113`。

#### <a name="to-add-a-string-table-entry"></a>若要加入的字串資料表項目

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 字串資料表中按一下滑鼠右鍵，然後選擇 **新的字串**。

1. 在 **字串值編輯器**，選取**識別碼**從**識別碼**下拉式清單或輸入*識別碼*直接就地。

1. 編輯**值**，如有必要。

1. 輸入的項目**標題**。

   > [!NOTE]
   > Windows 字串資料表中不得包含 null 的字串。 如果您是 null 字串的字串資料表中建立項目，您會收到訊息，詢問是否要**請輸入字串，此資料表項目的**。

#### <a name="to-delete-a-string-table-entry"></a>若要刪除的字串資料表項目

選取您想要刪除，然後執行下列其中一項的項目：

- 移至功能表**編輯** > **刪除**。

- 以滑鼠右鍵按一下要刪除，然後選擇 字串**刪除**。

- 按下**刪除**索引鍵。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要將字串移到另一個資源指令碼檔案

1. [在這兩個.rc 檔案開啟字串資料表](../windows/how-to-create-a-resource-script-file.md)。

1. 以滑鼠右鍵按一下要移動，然後選擇 字串**剪下**。

1. 將游標放在目標**字串值編輯器**視窗。

1. 在  *.rc*您想要移動的字串，以滑鼠右鍵按一下並選擇的檔案**貼上**。

> [!NOTE]
> 如果**識別碼**或**值**移動的字串衝突與現有的**識別碼**或是**值**在目的地檔案中，可能是該**識別碼**或**值**移動的字串的變更。

### <a name="to-change-the-properties-of-a-string-resource"></a>若要變更字串資源的屬性

您可以使用就地編輯來變更**識別碼**，**值**，並**標題**屬性。

> [!NOTE]
>  您也可以編輯中的字串屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。

#### <a name="to-change-a-string-or-its-identifier"></a>若要變更字串或其識別碼

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要編輯，然後按兩下的字串**識別碼**，**值**，或**標題**資料行，則您可以：

   - 選取 **識別碼**從**識別碼**下拉式清單或輸入*識別碼*直接就地。

   - 輸入在不同的數字**值**資料行。

   - 輸入中的編輯**標題**資料行。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>若要變更多個字串資源的標題屬性

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要變更按住的字串**Ctrl**當您選取每個索引鍵。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要變更屬性的新值。

1. 按 **Enter** 鍵。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>若要加入的字串資源的格式或特殊字元

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](how-to-create-a-resource-script-file.md#create-resources)。

1. 選取您想要修改的字串。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，新增任何的標準逸出序列中的文字下列**標題**方塊，然後按**Enter**。

   |若要取得此...|輸入此...|
   |-----------------|---------------|
   | 換行 | \\n |
   | 歸位字元 | \\r |
   | 索引標籤 | \\t |
   | 反斜線 (\\) | \\\\ |
   | ASCII 字元 | \\ddd （八進位標記法） |
   | 警示 （鈴聲） | \\a |

   > [!NOTE]
   > **字串值編輯器**不支援完整的逸出 ASCII 字元。 您只能使用以上所列。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->