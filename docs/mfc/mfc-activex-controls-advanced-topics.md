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
ms.openlocfilehash: df71e2e59763644bd4aefb5d3e3afa46f82f538a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392709"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 控制項：進階主題

本文章涵蓋開發 ActiveX 控制項相關的進階的主題。 它們包括：

- [使用 ActiveX 控制項中的資料庫類別](#_core_using_database_classes_in_activex_controls)

- [實作參數化的屬性](#_core_implementing_a_parameterized_property)

- [在您的 ActiveX 控制項中處理錯誤](#_core_handling_errors_in_your_activex_control)

- [處理控制項中的特殊按鍵](#_core_handling_special_keys_in_your_control)

- [在執行階段則看不見的存取對話方塊控制項](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

##  <a name="_core_using_database_classes_in_activex_controls"></a> 使用 ActiveX 控制項中的資料庫類別

由於 ActiveX 控制項類別是類別庫的一部分，您可以套用相同的程序和規則使用標準的 MFC 應用程式開發使用 MFC 資料庫類別的 ActiveX 控制項中的資料庫類別。

MFC 資料庫類別的一般概觀，請參閱 < [MFC 資料庫類別 （DAO 和 ODBC）](../data/mfc-database-classes-odbc-and-dao.md)。 本文將介紹 MFC ODBC 類別和 MFC DAO 類別，並將您導向上的更多詳細資料。

> [!NOTE]
>  視覺效果C++環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您改用[OLE DB 樣板](../data/oledb/ole-db-programming.md)或是[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO，在維護現有的應用程式。

##  <a name="_core_implementing_a_parameterized_property"></a> 實作參數化的屬性

參數化的屬性 （有時稱為屬性的陣列） 是一種方法公開為控制項的單一屬性的值同質集合。 例如，您可以使用參數化的屬性公開的陣列或做為屬性的字典。 在 Visual Basic 中，這類屬性會使用陣列標記法來存取：

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

您可以使用 [新增屬性精靈] 來實作參數化的屬性。 加入屬性精靈藉由新增一組允許控制項使用者存取使用上述的標記法屬性的 Get/Set 函式，或以標準方式來實作屬性。

類似於方法和屬性，參數化屬性也會有允許的參數數目限制。 在參數化屬性的情況下，限制為 15 個參數 （使用一個參數保留供儲存屬性值）。

下列程序，將參數化的屬性，稱為陣列，可以存取為整數的二維陣列。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>若要加入參數化的屬性，使用 [新增屬性精靈]

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

1. 在 **屬性名稱**方塊中，輸入`Array`。

1. 在 **屬性的型別**方塊中，選取**簡短**。

1. 針對**實作**類型，按一下**Get/Set 方法**。

1. 在 **取得函式**並**設定函式**方塊中，輸入為 Get 和 Set 函式的唯一名稱，或接受預設名稱。

9. 新增名為的參數*資料列*(型別*簡短*)，並使用**參數名稱**並**參數型別**控制項。

10. 新增第二個參數，呼叫*資料行*(型別*簡短*)。

11. 按一下 [ **完成**]。

### <a name="changes-made-by-the-add-property-wizard"></a>所做的變更加入屬性精靈

當您新增自訂屬性時，加入屬性精靈 進行變更的控制項類別的標頭檔 (。H） 和實作 (。CPP) 檔案。

下列幾行加入的控制項類別。H 檔案：

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

此程式碼會宣告兩個呼叫的函式`GetArray`和`SetArray`可讓使用者存取屬性時，要求特定資料列和資料行。

此外，加入屬性精靈 會加入下列幾行控制項分派對應，位於控制項類別實作 (。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最後，實作`GetArray`和`SetArray`函式會新增至結尾。CPP 檔案。 在大部分情況下，您將修改 Get 函式來傳回屬性的值。 Set 函式通常會包含執行、 之前或之後的屬性變更的程式碼。

針對此屬性才能發揮作用中，您可以宣告在控制項類別中，類型的二維陣列成員變數**簡短**來儲存參數化屬性的值。 然後，您可以修改 Get 函式，以傳回儲存在適當的資料列與資料行的值，如參數，所指示，並修改 Set 函式來更新資料列和資料行參數所參考的值。

##  <a name="_core_handling_errors_in_your_activex_control"></a> 在您的 ActiveX 控制項中處理錯誤

如果控制項中發生錯誤狀況，您可能需要的控制項容器中報告錯誤。 有兩種方法來報告錯誤，請根據錯誤發生的情況。 如果發生錯誤的屬性中取得或設定函式，或在 OLE Automation 方法的實作，控制項應該呼叫[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)，哪一個訊號，來控制使用者所發生的錯誤。 如果在其他任何時候，就會發生錯誤，控制項應該呼叫[colecontrol:: Fireerror](../mfc/reference/colecontrol-class.md#fireerror)，它就會引發內建的錯誤事件。

若要指出已發生之錯誤的種類，控制項必須傳遞錯誤代碼`ThrowError`或`FireError`。 錯誤碼是 OLE 狀態碼，有 32 位元值。 可能的話，請選擇錯誤的程式碼從一組標準的 OLECTL 中定義的代碼。H 標頭檔。 下表摘要說明這些程式碼。

### <a name="activex-control-error-codes"></a>ActiveX 控制項錯誤碼

|錯誤|描述|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|不合法的函式呼叫|
|CTL_E_OVERFLOW|溢位|
|CTL_E_OUTOFMEMORY|記憶體不足|
|CTL_E_DIVISIONBYZERO|除數為零|
|CTL_E_OUTOFSTRINGSPACE|超出字串空間|
|CTL_E_OUTOFSTACKSPACE|用完堆疊空間|
|CTL_E_BADFILENAMEORNUMBER|不正確的檔名或數目|
|CTL_E_FILENOTFOUND|找不到檔案|
|CTL_E_BADFILEMODE|不正確的檔案模式|
|CTL_E_FILEALREADYOPEN|檔案已經開啟|
|CTL_E_DEVICEIOERROR|裝置 I/O 錯誤|
|CTL_E_FILEALREADYEXISTS|檔案已經存在|
|CTL_E_BADRECORDLENGTH|不正確的資料錄長度|
|CTL_E_DISKFULL|磁碟已滿|
|CTL_E_BADRECORDNUMBER|不正確的資料錄數目|
|CTL_E_BADFILENAME|不正確的檔案名稱|
|CTL_E_TOOMANYFILES|檔案太多|
|CTL_E_DEVICEUNAVAILABLE|裝置無法使用|
|CTL_E_PERMISSIONDENIED|權限遭拒|
|CTL_E_DISKNOTREADY|磁碟未就緒|
|CTL_E_PATHFILEACCESSERROR|路徑/檔案存取錯誤|
|CTL_E_PATHNOTFOUND|找不到路徑|
|CTL_E_INVALIDPATTERNSTRING|無效的模式字串|
|CTL_E_INVALIDUSEOFNULL|使用 NULL 無效|
|CTL_E_INVALIDFILEFORMAT|無效的檔案格式|
|CTL_E_INVALIDPROPERTYVALUE|無效的屬性值|
|CTL_E_INVALIDPROPERTYARRAYINDEX|無效的屬性陣列索引|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Set|
|CTL_E_SETNOTSUPPORTED|不支援 Set (唯讀屬性)|
|CTL_E_NEEDPROPERTYARRAYINDEX|須提供屬性陣列索引|
|CTL_E_SETNOTPERMITTED|不允許使用 Set|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|在執行階段不支援 Get|
|CTL_E_GETNOTSUPPORTED|不支援 Get (唯寫屬性)|
|CTL_E_PROPERTYNOTFOUND|找不到屬性|
|CTL_E_INVALIDCLIPBOARDFORMAT|無效的剪貼簿格式|
|CTL_E_INVALIDPICTURE|無效的圖片|
|CTL_E_PRINTERERROR|圖片錯誤|
|CTL_E_CANTSAVEFILETOTEMP|無法將檔案儲存至 TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|找不到搜尋文字|
|CTL_E_REPLACEMENTSTOOLONG|取代文字太長|

如有必要，使用 CUSTOM_CTL_SCODE 巨集來定義自訂錯誤碼未涵蓋的條件由其中一個標準的程式碼。 這個巨集的參數應為介於 1000年之間的整數到 32767 之間，內含。 例如: 

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

如果您要建立 ActiveX 控制項來取代現有的 VBX 控制項，定義您 ActiveX 控制項錯誤碼與 VBX 控制項用來確保錯誤碼相容的數字值相同。

##  <a name="_core_handling_special_keys_in_your_control"></a> 處理控制項中的特殊按鍵

在某些情況下您可能想要處理特定按鍵組合以特殊方式;比方說，插入新行，在多行文字方塊中按下 ENTER 鍵時方塊控制項，或編輯的群組之間移動控制項時方向性金鑰已按下的識別碼。

如果您的 ActiveX 控制項的基底類別是`COleControl`，您可以覆寫[cwnd:: Pretranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage)容器處理它們之前處理訊息。 在使用這項技術時，一律會傳回**真**如果您的覆寫中處理訊息`PreTranslateMessage`。

下列程式碼範例示範可能的方式來處理與方向的索引鍵相關的任何訊息。

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

如需有關處理 ActiveX 控制項的鍵盤介面的詳細資訊，請參閱 ActiveX SDK 文件。

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> 在執行階段則看不見的存取對話方塊控制項

您可以建立沒有任何使用者介面，而且無法在執行階段的對話方塊控制項。 如果您看不在執行階段的 ActiveX 控制項新增至對話方塊並使用[CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem)存取控制項，控制項將無法正常運作。 相反地，您應該使用其中一個下列技巧來取得物件，表示控制項：

- 使用 加入成員變數精靈，選取**控制變數**，然後選取 控制項的 id。 輸入成員變數的名稱，然後選取做為控制項的包裝函式類別**的控制項型別**。

     -或-

- 為對話方塊中的項目宣告的本機變數和子類別。 插入程式碼，如下所示 (`CMyCtrl`是包裝函式類別，IDC_MYCTRL1 是控制項的 ID):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
