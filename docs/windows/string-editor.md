---
title: 字串編輯器 （c + +）
ms.date: 11/04/2016
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
ms.openlocfilehash: 24e4e6ba5b9c2dff1a179bea39830f4a3bbe5879
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702970"
---
# <a name="string-editor-c"></a>字串編輯器 （c + +）

字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。

在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。

字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 (及其他資源)，就能當地語系化應用程式，無須變更原始程式碼。 這種情況下會於手動尋找及取代原始程式檔中的各種字串更為理想。

如需將資源加入 managed 專案 （通用語言執行平台為目標的專案） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說：將 Windows Form 當地語系化](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

使用**字串**編輯器執行下列動作：

## <a name="to-find-a-string-resource-in-the-string-table"></a>若要在字串中尋找的字串資源

您可以搜尋一或多個字串在字串資料表中，並使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)具有**檔案中尋找**命令 (**編輯**功能表) 來尋找所有執行個體的字串符合模式。

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **編輯**功能表上，選取**尋找和取代**，然後選擇**尋找**。

1. 在  **Find What**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找的字串的標題文字 或 資源識別碼。

1. 選取任一**尋找**選項。

1. 選取 **尋找下一個**。

   > [!TIP]
   > 若要搜尋檔案時，請使用規則運算式，使用**檔案中尋找**命令。 輸入的規則運算式比對模式，或選取右邊的按鈕**Find What**方塊，以顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。 如果您使用規則運算式時，務必**使用：規則運算式**選取核取方塊。

## <a name="to-add-or-delete-a-string-resource"></a>若要加入或刪除字串資源

您可以快速地插入或刪除字串資料表使用的項目**字串**編輯器。 新的字串會放在資料表結尾處，並指定下一個可用的識別項。 然後您可以編輯**識別碼**，**值**，或**標題**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)視。

**字串**編輯器可確保您不使用已在使用的識別碼。 如果您選取的識別碼已經在使用中，**字串**編輯器將會通知您，並將指定的泛用的唯一識別碼，例如`IDS_STRING58113`。

### <a name="to-add-a-string-table-entry"></a>若要加入的字串資料表項目

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 字串資料表中按一下滑鼠右鍵，然後選擇 **新的字串**從捷徑功能表。

1. 在 [**字串**編輯器中，選取**識別碼**從 ID] 下拉式清單或類型識別碼直接就地。

1. 編輯**值**，如有必要。

1. 輸入的項目**標題**。

   > [!NOTE]
   > 在 Windows 字串資料表中不允許 null 的字串。 如果您是 null 字串的字串資料表中建立項目，您會收到訊息，要求您 請輸入字串為此資料表項目。

### <a name="to-delete-a-string-table-entry"></a>若要刪除的字串資料表項目

1. 選取您要刪除的項目。

1. 在 **編輯**功能表上，選取**刪除**。

\-或-

 以滑鼠右鍵按一下您想要刪除，然後選擇 的字串**刪除**從捷徑功能表。

\-或-

 按下**刪除**索引鍵。

## <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要將字串移到另一個資源指令碼檔案

1. 在這兩個.rc 檔案開啟字串資料表。 (如需詳細資訊，請參閱 <<c0> [ 檢視資源在資源指令碼檔案外部的專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 以滑鼠右鍵按一下您想要移動，然後選擇 的字串**剪下**從捷徑功能表。

1. 將游標放在目標**字串值編輯器**視窗。

1. 在.rc 檔案中您要移動的字串，以滑鼠右鍵按一下，然後選擇 **貼上**從捷徑功能表。

   > [!NOTE]
   > 如果**識別碼**或**值**移動的字串衝突與現有的**識別碼**或是**值**在目的地檔案中，任一**識別碼**或**值**移動的字串的變更。 如果字串已存在具有相同**識別碼**，則**識別碼**移動的字串的變更。 如果字串已存在具有相同**值**，則**值**移動的字串的變更。

## <a name="to-change-the-properties-of-a-string-resource"></a>若要變更字串資源的屬性

您可以使用就地編輯，若要變更識別碼、 值和標題屬性。

### <a name="to-change-a-string-or-its-identifier"></a>若要變更字串或其識別碼

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您想要編輯，然後按兩下的字串**識別碼**，**值**，或**標題**資料行。 現在您可以：

   - 選取 **識別碼**從**ID 下拉式**清單中或類型`ID`直接就地。

   - 輸入在不同的數字**值**資料行。

   - 輸入中的編輯**標題**資料行。

        > [!NOTE]
        >  您也可以編輯中的字串屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。

### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>若要變更多個字串資源的標題屬性

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 選取您想要變更按住的字串**Ctrl**當您選取每個索引鍵。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要變更屬性的新值。

1. 按 **Enter** 鍵。

## <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>若要加入的字串資源的格式或特殊字元

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 選取您想要修改的字串。

1. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，新增任何標準逸出序列的下面所列中的文字**標題** 方塊中，然後按**Enter**。

   |若要取得此|輸入這|
   |-----------------|---------------|
   | 換行 | \\n |
   | 歸位字元 | \\r |
   | 索引標籤 | \\t |
   | 反斜線 (\\) | \\\\ |
   | ASCII 字元 | \\ddd （八進位標記法） |
   | 警示 （鈴聲） | \\a |

> [!NOTE]
> **字串**編輯器不支援完整的逸出 ASCII 字元。 您只能使用以上所列。

> [!NOTE]
> Windows 不允許建立空的字串資料表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[字串](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[關於字串](/windows/desktop/menurc/about-strings)<br/>
[自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)