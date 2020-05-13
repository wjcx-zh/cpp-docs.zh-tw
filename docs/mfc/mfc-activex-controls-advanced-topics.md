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
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364632"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控制項：進階主題

本文介紹與開發 ActiveX 控件相關的高級主題。 其中包括：

- [在 ActiveX 控制項中使用資料庫類別](#_core_using_database_classes_in_activex_controls)

- [實現參數化屬性](#_core_implementing_a_parameterized_property)

- [處理 ActiveX 控制檔中的錯誤](#_core_handling_errors_in_your_activex_control)

- [處理控制檔中的特殊金鑰](#_core_handling_special_keys_in_your_control)

- [存取執行時不可見的對話框控制元件](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>在 ActiveX 控制項中使用資料庫類別

由於 ActiveX 控件類是類庫的一部分,因此可以應用相同的過程和規則,用於在標準 MFC 應用程式中使用資料庫類來開發使用 MFC 資料庫類的 ActiveX 控件。

有關 MFC 資料庫類的概述,請參閱[MFC 資料庫類 (DAO 和 ODBC)。](../data/mfc-database-classes-odbc-and-dao.md) 本文介紹了 MFC ODBC 類和 MFC DAO 類,並指導您瞭解這兩個類的更多詳細資訊。

> [!NOTE]
> 通過 Office 2013 支援 DAO。 DAO 3.6 是最終版本,它被視為過時版本。 視覺化C++環境和精靈不支援DAO(儘管包含DAO類,您仍可以使用它們)。 Microsoft 建議您將[OLE DB 範本](../data/oledb/ole-db-programming.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用於新專案。 您只應在維護現有應用程式時使用 DAO。

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>實現參數化屬性

參數化屬性(有時稱為屬性陣列)是一種將值的同質集合公開為控制項的單個屬性的方法。 例如,可以使用參數化屬性將陣列或字典公開為屬性。 在 Visual Basic 中,使用陣列表示法存取此類屬性:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

使用添加屬性嚮導實現參數化屬性。 "添加屬性精靈"通過添加一對 Get/Set 函數來實現該屬性,這些函數允許控制件使用者使用上述表示法或標準方式存取該屬性。

與方法和屬性類似,參數化屬性也限制允許的參數數。 對於參數化屬性,限制為 15 個參數(保留一個參數用於存儲屬性值)。

以下過程添加了一個參數化屬性,稱為 Array,可以作為整數的二維陣組進行訪問。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>使用新增屬性精靈新增參數化屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

1. 在 **「屬性名稱」** 框`Array`中, 鍵入 。

1. 在 **「屬性類型」** 框中,選擇 **「短**」。。

1. 對於**實現**類型,按一下 **「獲取/設置方法**」。

1. 在 **「獲取函數**和**設定函數」** 框中,為獲取和設定函數鍵入唯一名稱或接受預設名稱。

1. 使用**參數名稱**和**參數類型**控制項添加參數,稱為*行*(鍵入*短*)。

1. 添加第二個參數,稱為*列*(鍵入*短*)。

1. 按一下 [完成] 。

### <a name="changes-made-by-the-add-property-wizard"></a>新增屬性精靈所做的變更

添加自定義屬性時,"添加屬性嚮導"會更改控制項類標頭 (。H) 和實現 (.CPP)檔。

以下行將新增到控制項類別 。H 檔:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

此代碼聲明兩個調用`GetArray`的函`SetArray`數 ,允許使用者在訪問屬性時請求特定的行和列。

此外,添加屬性嚮導將以下行添加到位於控制項類實現 () 中的控制項調度映射中。CPP) 檔案:

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最後,將和`GetArray``SetArray`函數的實現添加到的末尾。CPP 檔。 在大多數情況下,您將修改 Get 函數以返回屬性的值。 Set 函數通常包含應在屬性更改之前或之後執行的代碼。

為使此屬性有用,可以在控制項類(類型**short)** 中聲明二維陣組成員變數以儲存參數化屬性的值。 然後,您可以修改 Get 函數以返回存儲在正確的行和列中的值(如參數所示),並修改 Set 函數以更新列和列參數引用的值。

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>處理 ActiveX 控制檔中的錯誤

如果控制項中發生錯誤條件,您可能需要向控制容器報告錯誤。 有兩種方法可以報告錯誤,具體取決於發生錯誤的情況。 如果錯誤發生在屬性的獲取或設置函數中,或在 OLE 自動化方法的實現中發生,則控件應調用[COleControl::throwError](../mfc/reference/colecontrol-class.md#throwerror),該錯誤應向控件使用者發出錯誤已發生信號。 如果錯誤發生在任何其他時間,控件應調用[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror),這將觸發庫存錯誤事件。

要指示已發生的錯誤類型,控制項必須將錯誤代碼傳遞給`ThrowError`或`FireError`。 錯誤代碼是 OLE 狀態代碼,具有 32 位值。 如果可能,請從 OLECTL 中定義的標準代碼集中選擇錯誤代碼。H 頭檔。 下表總結了這些代碼。

### <a name="activex-control-error-codes"></a>ActiveX 控制錯誤代碼

|錯誤|描述|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|非法函數呼叫|
|CTL_E_OVERFLOW|溢位|
|CTL_E_OUTOFMEMORY|記憶體不足|
|CTL_E_DIVISIONBYZERO|除零|
|CTL_E_OUTOFSTRINGSPACE|字串空間用盡|
|CTL_E_OUTOFSTACKSPACE|堆疊空間用盡|
|CTL_E_BADFILENAMEORNUMBER|不正確的檔名或數目|
|CTL_E_FILENOTFOUND|找不到檔案|
|CTL_E_BADFILEMODE|不正確的檔案模式|
|CTL_E_FILEALREADYOPEN|檔案已經開啟|
|CTL_E_DEVICEIOERROR|裝置 I/O 錯誤|
|CTL_E_FILEALREADYEXISTS|檔案已經存在|
|CTL_E_BADRECORDLENGTH|不正確的資料錄長度|
|CTL_E_DISKFULL|磁碟已滿|
|CTL_E_BADRECORDNUMBER|不正確的資料錄數目|
|CTL_E_BADFILENAME|檔案名錯誤|
|CTL_E_TOOMANYFILES|檔案太多|
|CTL_E_DEVICEUNAVAILABLE|裝置無法使用|
|CTL_E_PERMISSIONDENIED|使用權限被拒|
|CTL_E_DISKNOTREADY|磁碟未就緒|
|CTL_E_PATHFILEACCESSERROR|路徑/檔案存取錯誤|
|CTL_E_PATHNOTFOUND|找不到路徑|
|CTL_E_INVALIDPATTERNSTRING|無效的模式字串|
|CTL_E_INVALIDUSEOFNULL|不合法使用 NULL|
|CTL_E_INVALIDFILEFORMAT|不合法的檔案格式|
|CTL_E_INVALIDPROPERTYVALUE|不合法屬性值|
|CTL_E_INVALIDPROPERTYARRAYINDEX|無效屬性陣列索引|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Set|
|CTL_E_SETNOTSUPPORTED|不支援 Set (唯讀屬性)|
|CTL_E_NEEDPROPERTYARRAYINDEX|須提供屬性陣列索引|
|CTL_E_SETNOTPERMITTED|不允許使用 Set|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Get|
|CTL_E_GETNOTSUPPORTED|不支援 Get (唯寫屬性)|
|CTL_E_PROPERTYNOTFOUND|找不到屬性|
|CTL_E_INVALIDCLIPBOARDFORMAT|無效剪貼簿格式|
|CTL_E_INVALIDPICTURE|無效圖片|
|CTL_E_PRINTERERROR|圖片錯誤|
|CTL_E_CANTSAVEFILETOTEMP|無法儲存檔案到 TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|找不到搜尋文字|
|CTL_E_REPLACEMENTSTOOLONG|取代文字太長|

如有必要,請使用CUSTOM_CTL_SCODE宏為標準代碼中未涵蓋的條件定義自定義錯誤代碼。 此宏的參數應介於 1000 和 32767 之間的整數(包括)。 例如：

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

如果要創建 ActiveX 控制項以取代現有的 VBX 控制項,請使用 VBX 控制項使用相同的數值定義 ActiveX 控制項錯誤代碼,以確保錯誤代碼相容。

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>處理控制檔中的特殊金鑰

在某些情況下,您可能希望以特殊方式處理某些擊鍵組合;例如,在多行文本框控件中按下 ENTER 鍵時插入新行,或在按下方向鍵 ID 時在一組編輯控制件之間移動。

如果 ActiveX 控件的基`COleControl`類為 ,則可以重寫[CWnd::PreTranslateMessage,](../mfc/reference/cwnd-class.md#pretranslatemessage)在容器處理消息之前處理它們。 使用此技術時,如果在重寫 中處理消息,則始終`PreTranslateMessage`返回**TRUE。**

以下代碼示例演示了處理與方向鍵相關的任何消息的可能方法。

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

有關為 ActiveX 控件處理鍵盤介面的詳細資訊,請參閱 ActiveX SDK 文件。

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>存取執行時不可見的對話框控制元件

您可以建立沒有使用者介面並在執行時不可見的對話方塊控制項。 如果在運行時將不可見的 ActiveX 控件添加到對話方塊中,並使用[CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)訪問該控制項,則該控制項將不能正常工作。 相反,應使用以下技術之一來獲取表示控制項的物件:

- 使用"添加成員變數嚮導",選擇 **"控制變數**",然後選擇控制件的 ID。 輸入成員變數名稱,然後選擇控制項的包裝類別為**控制項型態**。

     -或-

- 將局部變數和子類聲明為對話框項。 插入代碼類似於以下內容(`CMyCtrl`包裝類別,IDC_MYCTRL1是控制項的 ID):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
