---
title: 新增成員變數
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: a8f693345fcb265cf8e97af342c6e0cd539c9001
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215994"
---
# <a name="add-a-member-variable"></a>新增成員變數

您可以使用 [類別檢視] 將成員變數新增至類別。 成員變數可以是用於[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 資料成員變數精靈專用於取得相關資訊，並將該資訊用來在來源檔案的適當位置插入元素。 您可以透過 [[資源檢視]](../windows/how-to-create-a-resource-script-file.md#create-resources) 中的 [[對話方塊編輯器]](../windows/dialog-editor.md)，或透過 [[類別檢視]](/visualstudio/ide/viewing-the-structure-of-code) 新增成員變數。

> [!NOTE]
> 當您設計和實作對話方塊時，也許會發現使用 [對話方塊編輯器] 新增對話方塊控制項，然後實作控制項成員變數的做法更有效率。

**若要使用 [加入成員變數] Wizard 在資源檢視中新增對話方塊控制項的成員變數：**

1. 在 [資源檢視] 中，展開專案節點及對話方塊節點，顯示專案的對話方塊清單。

1. 按兩下您要新增成員變數的對話方塊，在對話方塊編輯器中開啟它。

1. 在對話方塊編輯器中顯示的對話方塊中，以滑鼠右鍵按一下您要新增成員變數的控制項。

1. 在捷徑功能表上，選擇 [新增變數]****，以顯示 [[新增成員變數精靈]](#add-member-variable-wizard)。

   > [!NOTE]
   > [控制項識別碼]**** 中已提供預設值。

1. 在適當的精靈方塊中提供資訊。 如需詳細資訊，請參閱[對話方塊控制項與變數類型](#dialog-box-controls-and-variable-types)。

1. 選取 [完成]****，將定義和實作程式碼新增至專案，然後關閉精靈。

**若要使用 [加入成員變數] Wizard 從類別檢視新增成員變數：**

1. 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，展開專案節點，顯示專案中的類別。

1. 以滑鼠右鍵按一下您要新增變數的類別。

1. 在捷徑功能表上，依序選擇 [新增]****、[新增變數]****，以顯示 [新增成員變數精靈]。

1. 在適當的精靈方塊中提供資訊。 如需詳細資訊，請參閱[新增成員變數精靈](#add-member-variable-wizard)。

1. 選取 [完成]****，將定義和實作程式碼新增至專案，然後關閉精靈。

## <a name="in-this-section"></a>本節內容

- [加入成員變數 wizard](#add-member-variable-wizard)
- [對話方塊控制項與變數類型](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>新增成員變數精靈

此精靈可將成員變數宣告新增至標頭檔。 根據選項而定，此精靈可將程式碼新增至 .cpp 檔案。 在您使用精靈新增了成員變數後，就可以在開發環境中編輯程式碼。

- **存取**

  設定成員變數的存取權。 存取修飾詞是指定其他類別對成員變數所具有之存取權的關鍵字。 如需指定存取權的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。 預設會將成員變數存取層級設定為 **`public`** 。

  - [public](../cpp/public-cpp.md)
  - [受保護](../cpp/protected-cpp.md)
  - [私人](../cpp/private-cpp.md)

- **變數類型**

  設定您要新增的成員變數傳回型別。

  - 若要新增非對話方塊控制項的成員變數，請從可用類型清單中選取。

    如需類型的詳細資訊，請參閱[基本類型](../cpp/fundamental-types-cpp.md)。

    |||
    |-|-|
    |**`char`**|**`short`**|
    |**`double`**|**`unsigned char`**|
    |**`float`**|**`unsigned int`**|
    |**`int`**|**`unsigned long`**|
    |**`long`**||

  - 若要新增對話方塊控制項的成員變數，此方塊會填入針對控制項或值傳回的物件類型。 如果您選取 [控制項]****，則 [變數類型]**** 會指定您在 [控制項識別碼]**** 方塊中選取之控制項的基底類別。 若對話方塊控制項可以包含值，而且您選取 [值]****，則 [變數類型]**** 會為該控制項可包含的值指定適當類型。 如需詳細資訊，請參閱[對話方塊控制項與變數類型](#dialog-box-controls-and-variable-types)。

    此值依 [控制項識別碼]**** 中的選取項目而定，而且無法變更。

- **變數名稱**

  設定您要新增的成員變數名稱。 成員變數通常以根據預設為您提供的識別字串 `m_` 開頭。

- **控制變數**

  表示成員變數會管理具有[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)支援之對話方塊中的控制項。 如需詳細資訊，請參閱 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)。 此選項僅適用於新增至衍生自 [CDialog](../mfc/reference/cdialog-class.md) 之類別的成員變數。 選取此方塊可啟用 [控制項識別碼]**** 和 [控制項類型]**** 選項。

- **控制項識別碼**

  設定您要新增的控制項變數識別碼。 從您要新增成員變數的控制項類型識別碼清單中選取。 此清單只有在選取 [控制變數]**** 方塊時才能使用，而且僅限於已新增至對話方塊的控制項識別碼。 例如，標準 [確定]**** 按鈕的控制項識別碼為 **IDOK**。

  |選項|說明|
  |------------|-----------------|
  |**控制**|控制項類型預設會設定此選項。 它會管理控制項本身，而不是控制項的狀態或內容 (原因是您可能會想要為清單方塊、下拉式方塊或編輯方塊管理這兩項)。|
  |**ReplTest1**|此選項適用於可包含值或顯示狀態的控制項類型，像是編輯方塊或核取方塊。 同時也適用於您可能會管理範圍、內容或狀態的控制項類型。 如需詳細資訊，請參閱[對話方塊控制項與變數類型](#dialog-box-controls-and-variable-types)。|

- **類別**

  指定變數是根據控制項類型或控制項的值。

- **控制項類型**

  設定要新增之控制項的類型。 此方塊無法變更。 例如，按鈕的控制項類型為 **BUTTON**，而下拉式方塊的控制項類型為 **COMBOBOX**。 如需詳細資訊，請參閱[對話方塊控制項與變數類型](#dialog-box-controls-and-variable-types)。

- **最大字元數**

  僅適用於 [變數類型]**** 設定為 [CString](../atl-mfc-shared/reference/cstringt-class.md) 時。 表示控制項可容納的最大字元數。

- **最小值**

  只有在變數類型為 `BOOL` 、 **`int`** 、、、、、、、、 `UINT` **`long`** `DWORD` **`float`** **`double`** `BYTE` **`short`** [COLECurrency](../mfc/reference/colecurrency-class.md)或[CTime](../atl-mfc-shared/reference/ctime-class.md)時才可使用。 表示刻度或日期範圍可接受的最小值。

- **最大值**

  只有在變數類型為 `BOOL` 、 **`int`** 、 `UINT` 、 **`long`** 、 `DWORD` 、 **`float`** **`double`** `BYTE` **`short`** `COLECurrency` `CTime` 、、、、或時才可使用。 表示刻度或日期範圍可接受的最大值。

- **.h 檔案**

  適用於其成員變數需要包裝函式類別的 ActiveX 控制項。 設定要新增類別宣告之標頭檔的名稱。

- **.cpp 檔案**

  適用於其成員變數需要包裝函式類別的 ActiveX 控制項。 設定要新增類別定義之實作檔的名稱。

- **註解**

  提供成員變數之標頭檔中的註解。

## <a name="dialog-box-controls-and-variable-types"></a>對話方塊控制項與變數類型

您可以使用 [[加入成員變數] wizard](#add-member-variable-wizard) ，將成員變數新增至使用 MFC 所建立的對話方塊控制項。 您新增成員變數的控制項類型會決定出現在對話方塊中的選項。

下表說明 MFC 及[對話方塊編輯器](../windows/dialog-editor.md)支援的所有對話方塊控制項類型。 該表也會列出他們的可用類型與值。

|控制|控制項類型|控制變數類型|變數值類型|最小/最大值 (僅限實值型別)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|動畫控制項|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|無；僅限控制項|不適用|
|按鈕|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|無；僅限控制項|不適用|
|核取方塊|CHECK|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|最小值/最大值|
|下拉式方塊|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字元數|
|日期時間選擇器控制項|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|
|編輯方塊|編輯|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 `COleCurrency`|最小值/最大值；某些支援最大字元數|
|熱鍵控制項|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|無；僅限控制項|不適用|
|清單方塊|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字元數|
|清單控制項|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|無；僅限控制項|N/A|
|月曆控制項|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|
|進度控制項|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|無；僅限控制項|不適用|
|Rich Edit 2 控制項|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字元數|
|Rich Edit 控制項|RICHEDIT|`CRichEditCtrl`|`CString`|最大字元數|
|捲軸 (垂直或水平)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|**`int`**|最小值/最大值|
|滑桿控制項|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|**`int`**|最小值/最大值|
|微調控制項|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|無；僅限控制項|不適用|
|索引標籤控制項|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|無；僅限控制項|N/A|
|樹狀控制項|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|無；僅限控制項|N/A|
