---
title: 變更符號
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
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
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 7d2890c2d2c05f1ee0309446dfe2de9917f85707
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763982"
---
# <a name="changing-a-symbol"></a>變更符號

當您建立新的資源或資源物件時，開發環境會為其指派預設的符號名稱，例如 IDD_DIALOG1。 您可以使用[屬性 視窗](/visualstudio/ide/reference/properties-window)來變更預設的符號名稱，或變更已與資源相關聯的所有符號的名稱。

單一資源相關聯的符號，您也可以使用**屬性**視窗變更符號值。 您可以使用[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)來變更目前未指派給資源的符號值。 如需詳細資訊，請參閱 <<c0> [ 變更未指定的符號](../windows/changing-unassigned-symbols.md)。

通常所有符號定義會儲存在`Resource.h`。 不過，您可能需要變更這 Include 檔案名稱，好讓您可以，比方說在相同目錄中處理多個資源檔。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="to-change-a-resources-symbol-name-id"></a>若要變更資源的符號名稱 (ID)

1. 在 [資源檢視](../windows/resource-view-window.md)，選取的資源。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **屬性** 視窗中，輸入新的符號名稱，或從現有的符號清單中選取**識別碼** 方塊中。

   如果您輸入新的符號名稱，它會自動指派值。

您可以使用[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)變更目前未指派給資源的符號名稱。 如需詳細資訊，請參閱 <<c0> [ 變更未指定的符號](../windows/changing-unassigned-symbols.md)。

### <a name="symbol-name-restrictions"></a>符號名稱限制

符號名稱限制如下所示：

- 所有[符號](../windows/symbols-resource-identifiers.md)必須是唯一的應用程式範圍內。 這可避免標頭檔中出現衝突的符號定義。

- 符號名稱的有效字元包括 A-Z、a-z、0-9 和底線 ( _ )。

- 符號名稱不能以數字開頭，而且僅限於 247 個字元。

- 符號名稱不能包含空格。

- 符號名稱不區分大小寫，但會保留第一個符號定義的大小寫。 定義符號的標頭檔是由資源編譯器/編輯器和 C++ 程式用來參考資源檔中定義的資源。 對於只有大小寫不同的兩個符號名稱，C++ 程式會將其視為兩個不同的符號，而資源編譯器/編輯器則會將這兩個名稱視為參考到單一符號。

   > [!NOTE]
   > 如果您未遵循下列的標準符號名稱配置 (ID*_[keyword])，而且您的符號名稱剛好與資源指令碼編譯器的已知關鍵字相同，則嘗試建置資源指令碼檔案會造成難以診斷的隨機錯誤產生。 若要避免這個問題，請遵守標準命名配置。

符號名稱具有描述性前置詞，指出它們所代表的資源或物件種類。 這些描述性前置詞的開頭為文字組合識別碼。 Microsoft Foundation Class 程式庫 (MFC) 使用下表所示的符號命名慣例。

|分類|前置詞|使用|
|--------------|------------|---------|
|資源|IDR_ IDD_ IDC_ IDI_ IDB_|快速鍵或功能表 (和相關或自訂資源) 對話方塊游標圖示點陣圖|
|功能表項目|ID_|Menu item|
|命令|ID_|命令|
|控制項和子視窗|IDC_|控制項|
|字串|IDS_|字串資料表中的字串|
|MFC|AFX_|保留給預先定義的 MFC 符號|

## <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>變更指派給單一資源或物件的符號值

1. 在 [資源檢視](../windows/resource-view-window.md)，選取的資源。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **屬性**視窗中，輸入符號名稱，後面接著等號和整數**識別碼**方塊中，例如：

    ```
    IDC_EDITNAME=5100
    ```

下一次儲存專案時，會在符號標頭檔中儲存新值。 在 [ID] 方塊中，只有符號名稱保持可見狀態；在驗證之後，將不會顯示等號和值。

### <a name="symbol-value-restrictions"></a>符號值限制

符號值可以是針對 #define 前置處理器指示詞以正常方式表示的任何整數。 以下是符號值的一些範例：

```
18
4001
0x0012
-3456
```

資源 (加速器、點陣圖、游標、對話方塊、圖示、功能表、字串資料表及版本資訊) 的符號值必須是介於 0 到 32767 的十進位數字 (但是不能為十六進位)。 資源組件 (例如對話方塊控制項或字串資料表中的個別字串) 的符號值可以從 0 到 65,534 或從 -32,768 到 32,767。

資源符號是 16 位元數字。 您可以帶正負號或不帶正負號輸入它們，不過，它們在內部是做為不帶正負號整數使用。 因此負數會轉換成對應的正數。

以下是符號值的一些限制：

- Visual Studio 開發環境和 MFC 將一些數字範圍用於特殊用途。 MFC 會保留最大顯著性位元的所有數字 (-32,768 到 -1 或 32,768 到 65,534，根據正負號)。

- 您無法使用其他符號字串定義符號值。 例如，不支援下列符號定義：

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- 您無法使用具有引數的前置處理器巨集做為值定義。 例如: 

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   不是有效的運算式，無論在編譯階段 `ID` 評估為何種項目。

- 您的應用程式可能具有現有檔案，包含以運算式定義的符號。 如需有關如何納入符號做為唯讀符號的詳細資訊，請參閱 <<c0> [ 使用共用 （唯讀） 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。

如需有關數字範圍的詳細資訊，請參閱[TN023:標準 MFC 資源](../mfc/tn023-standard-mfc-resources.md)。

## <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>變更資源符號標頭檔名稱

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇[Resource Includes](../windows/resource-includes-dialog-box.md)從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

1. 在 **符號標頭檔**方塊中，輸入 include 檔案的新名稱。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[檢視資源符號](../windows/viewing-resource-symbols.md)<br/>
