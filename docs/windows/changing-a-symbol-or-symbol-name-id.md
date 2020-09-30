---
title: 如何：管理符號
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 67a5c801c13038e7215473edecc2d41a8f7086e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505724"
---
# <a name="how-to-manage-symbols"></a>如何：管理符號

當您建立新的資源或資源物件時，開發環境會為它指派預設的符號名稱，例如 `IDD_DIALOG1` 。 您可以使用 [屬性視窗](/visualstudio/ide/reference/properties-window) 來變更預設的符號名稱，或變更已與資源相關聯之任何符號的名稱。

針對與單一資源相關聯的符號，您也可以使用 [ **屬性** ] 視窗來變更符號值。 您可以使用 [ [資源符號] 對話方塊](./creating-new-symbols.md) 來變更目前未指派給資源的符號值。

通常所有符號定義都會儲存在中 `Resource.h` 。 不過，您可能需要變更這 Include 檔案名稱，好讓您可以，比方說在相同目錄中處理多個資源檔。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [如何：建立資源](how-to-create-a-resource-script-file.md)。

## <a name="symbol-name-restrictions"></a>符號名稱限制

符號名稱限制如下所示：

- 所有 [符號](symbols-resource-identifiers.md) 在應用程式範圍內都必須是唯一的，以避免標頭檔中的符號定義衝突。

- 符號名稱的有效字元包括 A-Z、a-z、0-9 和底線 ( _ )。

- 符號名稱不能以數位開頭，而且限制為247個字元。

- 符號名稱不能包含空格。

- 符號名稱不區分大小寫，但會保留第一個符號定義的大小寫。

   定義符號的標頭檔是由資源編譯器/編輯器和 C++ 程式用來參考資源檔中定義的資源。 對於只有大小寫不同的兩個符號名稱，C++ 程式會將其視為兩個不同的符號，而資源編譯器/編輯器則會將這兩個名稱視為參考到單一符號。

> [!NOTE]
> 如果您未遵循標準符號名稱配置 (識別碼 * _ [關鍵字] ) ，而您的符號名稱與資源腳本編譯器已知的關鍵字相同，則嘗試建立資源腳本檔將會導致難以診斷的看似隨機錯誤產生。 若要避免這個問題，請遵守標準命名配置。

符號名稱具有描述性前置詞，指出它們所代表的資源或物件種類。 這些描述性前置詞的開頭為文字組合識別碼。 MFC) 程式庫 (MFC 會使用下表所示的符號命名慣例：

|類別|前置詞|使用|
|--------------|------------|---------|
|資源|IDR_、IDD_、IDC_、IDI_、IDB_|快速鍵或功能表 (以及相關或自訂的資源) 、對話方塊、游標、圖示、點陣圖|
|功能表項目|ID_|功能表項目|
|命令|ID_|命令|
|控制項和子視窗|IDC_|控制|
|字串|IDS_|字串資料表中的字串|
|MFC|AFX_|保留給預先定義的 MFC 符號|

### <a name="to-change-a-symbol-name-id"></a>若要變更符號名稱 (識別碼) 

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，選取資源。

1. 在 [ **屬性** ] 視窗中，輸入新的符號名稱，或從 [ **識別碼** ] 方塊中現有符號的清單中選取。

   如果您輸入新的符號名稱，它會自動指派值。

> [!NOTE]
> 您可以使用 [ [資源符號] 對話方塊](./creating-new-symbols.md) 來變更目前未指派給資源的符號名稱。

## <a name="symbol-value-restrictions"></a>符號值限制

符號值可以是以標準方式表示的任何整數，以用於 `#define` 預處理器指示詞。 以下是符號值的一些範例：

```
18
4001
0x0012
-3456
```

資源的符號值（例如快速鍵、點陣圖、游標、對話方塊、圖示、功能表、字串資料表和版本資訊）必須是介於0到32767之間的十進位數，但不能是十六進位。 資源組件 (例如對話方塊控制項或字串資料表中的個別字串) 的符號值可以從 0 到 65,534 或從 -32,768 到 32,767。 如需有關數位範圍的詳細資訊，請參閱 [TN023：標準 MFC 資源](../mfc/tn023-standard-mfc-resources.md)。

資源符號為16位數位。 您可以將它們輸入為帶正負號或不帶正負號，但會在內部使用為不帶正負號的整數，因此負數將會轉換為其對應的正值。

符號值的一些限制如下：

- Visual Studio 開發環境和 MFC 將一些數字範圍用於特殊用途。 MFC 會保留最大顯著性位元的所有數字 (-32,768 到 -1 或 32,768 到 65,534，根據正負號)。

- 您無法使用其他符號字串來定義符號值。 例如，不支援下列符號定義：

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- 您無法使用預處理器宏搭配引數作為值定義。 下列範例不是有效的運算式，不論 `ID` 編譯時期的評估結果為何：

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- 您的應用程式可能具有現有檔案，包含以運算式定義的符號。

### <a name="to-change-a-symbol-value"></a>若要變更符號值

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，選取資源。

1. 在 [ **屬性** ] 視窗中，于 [ **識別碼** ] 方塊中輸入符號名稱，後面接著等號和整數，例如：

    ```
    IDC_EDITNAME=5100
    ```

   下一次儲存專案時，會在符號標頭檔中儲存新值。 在 [識別碼] 方塊中只會顯示符號名稱，而且在驗證之後不會顯示等號和值。

## <a name="change-or-delete-symbols"></a>變更或刪除符號

在 [ [資源符號] 對話方塊](./creating-new-symbols.md)中，您可以編輯或刪除尚未指派給資源或物件的現有符號。

### <a name="to-change-an-unassigned-symbol"></a>變更未指派的符號

1. 在 [ **名稱** ] 方塊中，選取未指派的符號，然後選擇 [ **變更**]。

1. 在 [ **變更符號** ] 對話方塊中提供的方塊中，編輯符號的名稱或值。

> [!NOTE]
> 若要變更指派給資源或物件的符號，您必須使用 [資源編輯器] 或 [ **屬性** ] 視窗。

### <a name="to-delete-an-unassigned-unused-symbol"></a>刪除未指派 (未使用) 的符號

在 [ **資源符號** ] 對話方塊中，選取您要刪除的符號，然後選擇 [ **刪除**]。

> [!NOTE]
> 在資源檔中刪除未使用的符號之前，請確定它不會在程式中的其他位置或在編譯時期包含的資源檔中使用。

## <a name="include-symbols"></a>包含符號

當開發環境第一次讀取另一個應用程式所建立的資源檔時，會將所有包含的標頭檔標示為唯讀。 雖然您可以使用 [ [資源包含] 對話方塊](./how-to-include-resources-at-compile-time.md) 來新增額外的唯讀符號標頭檔。

您可能想要使用唯讀符號定義的其中一個原因是，您想要將它們在數個專案之間共用的符號檔中運用。

當您搭配使用現有資源與符號定義，且這些定義使用運算式而非是簡單的整數來定義符號值，您也可以使用包含的符號檔。 例如：

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

環境會正確解譯這些計算的符號，前題是：

- 計算的符號會放置在唯讀符號檔案。

- 您的資源檔包含已指派這些計算的符號的資源。

- 預期是數值運算式。

> [!NOTE]
> 如果預期字串或數值運算式，則不會評估運算式。

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>在資源檔中包含共用 (唯讀) 符號

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選取 [ [資源包含](./how-to-include-resources-at-compile-time.md)]。

1. 在 [ **唯讀符號** 指示詞] 方塊中，使用 `#include` 編譯器指示詞來指定要保留唯讀符號的檔案。

   請勿呼叫檔案 `Resource.h` ，因為這是主要符號標頭檔通常使用的檔案名。

   > [!NOTE]
   > 您在 [ **唯讀符號** 指示詞] 方塊中輸入的內容，與您輸入時的資源檔完全相同。 請確定您輸入的內容不包含任何拼字或語法錯誤。

   使用 [ **唯讀符號** 指示詞] 方塊，只包含具有符號定義的檔案。 請勿包含資源定義，否則儲存檔案時，將會建立重複的資源定義。

1. 將符號放在您指定的檔案。

   以這種方式包含的檔案中的符號會在您每次開啟資源檔時進行評估，但在您儲存檔案時，不會在磁片上取代這些符號。

1. 選取 [確定]。

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>變更資源符號標頭檔名稱

1. 在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選擇 [ [資源包含](./how-to-include-resources-at-compile-time.md)]。

1. 在 [ **符號標頭檔** ] 方塊中，輸入 include 檔案的新名稱。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[ (符號的資源識別碼) ](symbols-resource-identifiers.md)<br/>
[如何：建立符號](creating-new-symbols.md)<br/>
[預先定義的符號 Id](predefined-symbol-ids.md)<br/>
