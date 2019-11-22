---
title: MFC ActiveX 控制項：進階主題
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: 9f1fa862a30a83cbda049fc63bac6c33a101587b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305376"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控制項：進階主題

本文涵蓋與開發 ActiveX 控制項相關的 advanced 主題。 它們包括：

- [在 ActiveX 控制項中使用資料庫類別](#_core_using_database_classes_in_activex_controls)

- [執行參數化屬性](#_core_implementing_a_parameterized_property)

- [處理您的 ActiveX 控制項中的錯誤](#_core_handling_errors_in_your_activex_control)

- [處理控制項中的特殊按鍵](#_core_handling_special_keys_in_your_control)

- [存取執行時間中不可見的對話方塊控制項](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

##  <a name="_core_using_database_classes_in_activex_controls"></a>在 ActiveX 控制項中使用資料庫類別

因為 ActiveX 控制項類別是類別庫的一部分，所以您可以套用相同的程式和規則，以便在標準 MFC 應用程式中使用資料庫類別來開發使用 MFC 資料庫類別的 ActiveX 控制項。

如需 MFC 資料庫類別的一般總覽，請參閱[Mfc 資料庫類別（DAO 和 ODBC）](../data/mfc-database-classes-odbc-and-dao.md)。 本文同時介紹 MFC ODBC 類別和 MFC DAO 類別，並將您導向到其中一項的更多詳細資料。

> [!NOTE]
> DAO 受到 Office 2013 的支援。 DAO 3.6 是最後的版本，被視為已淘汰。 視覺C++環境和嚮導不支援 dao （雖然包含 dao 類別，但您仍然可以使用它們）。 Microsoft 建議您針對新專案使用 [OLE DB 樣板](../data/oledb/ole-db-programming.md)或是 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。 您應該只在維護現有的應用程式時使用 DAO。

##  <a name="_core_implementing_a_parameterized_property"></a>執行參數化屬性

參數化屬性（有時稱為屬性陣列）是一種方法，可將值的同質集合公開為控制項的單一屬性。 例如，您可以使用參數化屬性，將陣列或字典公開為屬性。 在 Visual Basic 中，這類屬性會使用陣列標記法來存取：

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

使用 [加入屬性] Wizard 來執行參數化屬性。 [加入屬性] Wizard 會藉由加入一對 Get/Set 函式來執行屬性，以允許控制項使用者使用上述標記法或標準方式來存取屬性。

與方法和屬性類似，參數化屬性也會限制允許的參數數目。 在參數化屬性的情況下，限制為15個參數（其中一個參數保留用來儲存屬性值）。

下列程式會新增名為 Array 的參數化屬性，其可存取為整數的二維陣列。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>若要使用加入屬性 Wizard 加入參數化屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

1. 在 [**屬性名稱**] 方塊中，輸入 `Array`。

1. 在 [**屬性類型**] 方塊中，選取 [ **short**]。

1. 針對 [**執行**類型]，按一下 [**取得/設定方法**]。

1. 在 [**取得**函式] 和 [**設定函數**] 方塊中，輸入 Get 和 set 函數的唯一名稱，或接受預設名稱。

9. 使用**參數名稱**和**參數類型**控制項加入參數，稱為資料*列*（類型*short*）。

10. 新增名為*column*的第二個參數（類型*short*）。

11. 按一下 [完成]。

### <a name="changes-made-by-the-add-property-wizard"></a>新增屬性 Wizard 所做的變更

當您加入自訂屬性時，[新增屬性] Wizard 會對控制項類別標頭（進行變更。H）和實（。CPP）檔案。

下列幾行會加入至控制項類別。H 檔案：

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

此程式碼會宣告兩個稱為 `GetArray` 和 `SetArray` 的函式，可讓使用者在存取屬性時要求特定的資料列和資料行。

此外，[新增屬性] Wizard 會將下列幾行新增至控制項類別實（中的 [控制] 分派對應）。CPP）檔案：

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最後，`GetArray` 和 `SetArray` 函式的實作用會加入至的結尾。CPP 檔案。 在大部分的情況下，您將修改 Get 函式以傳回屬性的值。 Set 函式通常會包含應在屬性變更之前或之後執行的程式碼。

若要讓這個屬性很有用，您可以在控制項類別中宣告**short**類型的二維陣列成員變數，以儲存參數化屬性的值。 接著，您可以修改 Get 函式，以傳回儲存在適當資料列和資料行的值（如參數所指示），並修改 Set 函數來更新資料列和資料行參數所參考的值。

##  <a name="_core_handling_errors_in_your_activex_control"></a>處理您的 ActiveX 控制項中的錯誤

如果控制項中發生錯誤狀況，您可能需要向控制項容器報告錯誤。 有兩種方法可以報告錯誤，視發生錯誤的情況而定。 如果錯誤發生在屬性的 Get 或 Set 函式內，或在 OLE Automation 方法的執行中，則控制項應呼叫[COleControl：： ThrowError](../mfc/reference/colecontrol-class.md#throwerror)，以向控制項使用者表示發生錯誤。 如果錯誤發生在任何其他時間，控制項應呼叫[COleControl：： FireError](../mfc/reference/colecontrol-class.md#fireerror)，這會引發 stock 錯誤事件。

若要指出發生的錯誤類型，控制項必須將錯誤碼傳遞給 `ThrowError` 或 `FireError`。 錯誤碼是具有32位值的 OLE 狀態碼。 可能的話，請從 OLECTL 中定義的一組標準代碼來選擇錯誤碼。H 標頭檔。 下表摘要說明這些代碼。

### <a name="activex-control-error-codes"></a>ActiveX 控制項錯誤碼

|錯誤|描述|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|不合法的函式呼叫|
|CTL_E_OVERFLOW|溢位|
|CTL_E_OUTOFMEMORY|記憶體不足|
|CTL_E_DIVISIONBYZERO|除數為零|
|CTL_E_OUTOFSTRINGSPACE|字串空間用盡|
|CTL_E_OUTOFSTACKSPACE|堆疊空間用盡|
|CTL_E_BADFILENAMEORNUMBER|不正確的檔名或數目|
|CTL_E_FILENOTFOUND|找不到檔案|
|CTL_E_BADFILEMODE|不正確的檔案模式|
|CTL_E_FILEALREADYOPEN|檔案已經開啟|
|CTL_E_DEVICEIOERROR|裝置 I/O 錯誤|
|CTL_E_FILEALREADYEXISTS|檔案已經存在|
|CTL_E_BADRECORDLENGTH|不正確的資料錄長度|
|CTL_E_DISKFULL|磁片已滿|
|CTL_E_BADRECORDNUMBER|不正確的資料錄數目|
|CTL_E_BADFILENAME|錯誤的檔案名|
|CTL_E_TOOMANYFILES|檔案太多|
|CTL_E_DEVICEUNAVAILABLE|裝置無法使用|
|CTL_E_PERMISSIONDENIED|權限遭拒|
|CTL_E_DISKNOTREADY|磁碟未就緒|
|CTL_E_PATHFILEACCESSERROR|路徑/檔案存取錯誤|
|CTL_E_PATHNOTFOUND|找不到路徑|
|CTL_E_INVALIDPATTERNSTRING|無效的模式字串|
|CTL_E_INVALIDUSEOFNull|不正確使用 Null|
|CTL_E_INVALIDFILEFORMAT|不正確檔案格式|
|CTL_E_INVALIDPROPERTYVALUE|不正確屬性值|
|CTL_E_INVALIDPROPERTYARRAYINDEX|不正確屬性陣列索引|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Set|
|CTL_E_SETNOTSUPPORTED|不支援 Set (唯讀屬性)|
|CTL_E_NEEDPROPERTYARRAYINDEX|須提供屬性陣列索引|
|CTL_E_SETNOTPERMITTED|不允許使用 Set|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Get|
|CTL_E_GETNOTSUPPORTED|不支援 Get (唯寫屬性)|
|CTL_E_PROPERTYNOTFOUND|找不到屬性|
|CTL_E_INVALIDCLIPBOARDFORMAT|不正確剪貼簿格式|
|CTL_E_INVALIDPICTURE|不正確圖片|
|CTL_E_PRINTERERROR|圖片錯誤|
|CTL_E_CANTSAVEFILETOTEMP|無法將檔案儲存至 TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|找不到搜尋文字|
|CTL_E_REPLACEMENTSTOOLONG|取代文字太長|

如有必要，請使用 CUSTOM_CTL_SCODE 宏來定義不是由其中一個標準代碼所涵蓋之條件的自訂錯誤碼。 這個宏的參數應該是介於1000和32767（含）之間的整數。 例如：

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

如果您要建立 ActiveX 控制項來取代現有的 VBX 控制項，請使用 VBX 控制項用來確保錯誤碼相容的相同數值，定義您的 ActiveX 控制項錯誤碼。

##  <a name="_core_handling_special_keys_in_your_control"></a>處理控制項中的特殊按鍵

在某些情況下，您可能會想要以特殊方式處理特定的按鍵組合;例如，在多行文字方塊控制項中按下 ENTER 鍵時插入新行，或在按下方向索引鍵識別碼時，于編輯控制項群組之間移動。

如果您的 ActiveX 控制項的基類是 `COleControl`的，您可以覆寫[CWnd：:P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage)來處理訊息，然後容器才會處理它們。 使用這項技術時，如果您在 `PreTranslateMessage`的覆寫中處理訊息，一律會傳回**TRUE** 。

下列程式碼範例示範處理與方向索引鍵相關之任何訊息的可能方式。

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

如需處理 ActiveX 控制項鍵盤介面的詳細資訊，請參閱 ActiveX SDK 檔。

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>存取執行時間中不可見的對話方塊控制項

您可以建立沒有使用者介面，而且在執行時間不會出現的對話方塊控制項。 如果您在執行時間 ActiveX 控制項將不可見的加入對話方塊，並使用[CWnd：： GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)存取控制項，控制項將無法正常運作。 相反地，您應該使用下列其中一種方法來取得代表控制項的物件：

- 使用 [加入成員變數] Wizard，選取 [**控制項變數**]，然後選取控制項的識別碼。 輸入成員變數名稱，然後選取控制項的包裝函式類別做為**控制項類型**。

     -或-

- 將區域變數和子類別宣告為對話方塊專案。 插入類似下列的程式碼（`CMyCtrl` 是包裝函式類別，IDC_MYCTRL1 是控制項的識別碼）：

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
