---
title: "MFC ActiveX 控制項：進階主題 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireError 方法"
  - "MFC ActiveX 控制項, 存取不可見的對話方塊控制項"
  - "MFC ActiveX 控制項, 進階主題"
  - "MFC ActiveX 控制項, 資料庫類別"
  - "MFC ActiveX 控制項, 錯誤碼"
  - "MFC ActiveX 控制項, 參數化屬性"
  - "MFC ActiveX 控制項, 特殊按鍵"
  - "PreTranslateMessage 方法"
  - "ThrowError 方法"
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：進階主題
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文包含進階主題與開發的 ActiveX 控制項相關的。  這些需求包括：  
  
-   [使用在 ActiveX 控制項的資料庫類別](#_core_using_database_classes_in_activex_controls)  
  
-   [實作參數化屬性](#_core_implementing_a_parameterized_property)  
  
-   [在您的 ActiveX 控制項的處理錯誤](#_core_handling_errors_in_your_activex_control)  
  
-   [處理特殊的輸入控制項](#_core_handling_special_keys_in_your_control)  
  
-   [會在執行階段存取的對話方塊控制項](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a> 使用在 ActiveX 控制項的資料庫類別  
 由於 ActiveX 控制項類別是類別庫的一部分，您可以套用相同的程序和規則使用 MFC 資料庫類別的資料庫類別在標準 MFC 應用程式到開發的 ActiveX 控制項。  
  
 如需 MFC 資料庫類別的一般概觀，請參閱 [MFC 資料庫類別 \(ODBC 和 DAO\)](../data/mfc-database-classes-odbc-and-dao.md)。  本文引入 MFC ODBC 類別和 MFC DAO 類別和直接重新命名或的詳細資料。  
  
> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議您在新的專案使用 [OLE DB 樣板](../data/oledb/ole-db-programming.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md) 。  請在維護現有應用程式時再使用 DAO。  
  
##  <a name="_core_implementing_a_parameterized_property"></a> 實作參數化屬性  
 參數化屬性 \(有時稱為屬性陣列\) 是公開值的同質性集合方法做為控制項的單一屬性。  例如，您可以使用參數型屬性公開陣列或字典做為屬性。  使用陣列標記法，在 Visual Basic 中，這個屬性存取:  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/VisualBasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 使用加入屬性精靈實作參數化屬性。  加入屬性精靈將允許控制使用者存取屬性使用上述附註或標準模式的一組實作屬性 Get 和 Set 函式。  
  
 類似方法和屬性，參數型屬性也具有限制允許的參數數目。  在參數型屬性而言，限制為 15 個參數 \(其中一個參數為儲存屬性值已保留供\)。  
  
 下列程序加入參數型屬性，稱為陣列，可以存取為整數的二維陣列。  
  
#### 使用加入屬性精靈，加入參數型屬性  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表上，按一下 **Add** 然後按一下 \[**加入屬性**\]。  
  
5.  在 **Property Name** 方塊中，輸入 `Array`。  
  
6.  在 **Property Type** 方塊中，選取 **short**。  
  
7.  對於 **Implementation** 類型，請按一下 **Get\/Set Methods**。  
  
8.  在 **Get Function** 和 **Set Function** 方塊中，輸入唯一名稱您的 Get 和 Set 函式或接受預設名稱。  
  
9. 將參數，呼叫 `row` \(型別 `short`\)，使用 **Parameter Name** 和 **Parameter Type** 控制。  
  
10. 將第二個參數呼叫 `column` \(型別 `short`\)。  
  
11. 按一下 \[**完成**\]。  
  
### 加入屬性精靈所做的變更。  
 當您將自訂屬性時，加入屬性精靈會對控制項類別標頭 \(。H\) 和實作 \(.CPP\) 檔案。  
  
 下列程式碼行加入至控制項類別。H 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_2.h)]  
  
 這個程式碼會宣告可讓使用者要求特定資料列和資料行，當存取屬性時的兩個函式呼叫 `GetArray` 和 `SetArray` 。  
  
 此外，加入屬性精靈會將下列行加入至控制項分派對應，位於控制項類別實作 \(.CPP\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 最後， `GetArray` 的實作和 `SetArray` 函式加入至 .CPP 檔案結尾。  在大部分情況下，您將修改 Get 函式傳回屬性的值。  這個 Set 函式通常會包含應該執行的程式碼，可能是，在屬性變更前後。  
  
 對於這個屬性很有用，您可以宣告控制項類別的二維陣列成員變數，型別 **short**，到參數化屬性的值。  您可以修改 Get 函式傳回值儲存於適當的資料列和資料行，如所參數，並修改這個 Set 函式更新資料列和資料行參數所參考的值。  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a> 在您的 ActiveX 控制項的處理錯誤  
 如果有錯誤條件在控制項中，您可能需要錯誤向控制項容器報告。  會報告的錯誤兩個方法，根據錯誤發生的情況。  如果錯誤出現在屬性的 Get 或 Set 函式內，或是 OLE Automation 方法的實作中，控制項應呼叫 [COleControl::ThrowError](../Topic/COleControl::ThrowError.md)，向使用者控制項時發生錯誤。  如果在其他時間發生，控制項應呼叫 [COleControl::FireError](../Topic/COleControl::FireError.md)，引發內建錯誤事件。  
  
 表示發生的錯誤類型，控制項必須將錯誤碼對應至 `ThrowError` 或 `FireError`。  錯誤碼是 OLE 狀態碼，有 32 位元值。  如果可能，請在 OLECTL.H 標頭檔定義標準組程式碼選取錯誤碼。  下表摘要說明這些程式碼。  
  
### ActiveX 控制項錯誤碼  
  
|錯誤|說明|  
|--------|--------|  
|**CTL\_E\_ILLEGALFUNCTIONCALL**|不合法的函式呼叫|  
|**CTL\_E\_OVERFLOW**|溢位|  
|**CTL\_E\_OUTOFMEMORY**|記憶體不足|  
|**CTL\_E\_DIVISIONBYZERO**|除數為零|  
|**CTL\_E\_OUTOFSTRINGSPACE**|超出字串空間|  
|**CTL\_E\_OUTOFSTACKSPACE**|堆疊空間不足|  
|**CTL\_E\_BADFILENAMEORNUMBER**|不正確的檔名或數目。|  
|**CTL\_E\_FILENOTFOUND**|找不到檔案|  
|**CTL\_E\_BADFILEMODE**|終結檔案模式|  
|**CTL\_E\_FILEALREADYOPEN**|已開啟的檔案。|  
|**CTL\_E\_DEVICEIOERROR**|裝置 I\/O 錯誤。|  
|**CTL\_E\_FILEALREADYEXISTS**|檔案已經存在|  
|**CTL\_E\_BADRECORDLENGTH**|不正確的資料錄長度|  
|**CTL\_E\_DISKFULL**|磁碟已滿|  
|**CTL\_E\_BADRECORDNUMBER**|不正確的資料錄數目|  
|**CTL\_E\_BADFILENAME**|不正確的檔名|  
|**CTL\_E\_TOOMANYFILES**|許多檔案|  
|**CTL\_E\_DEVICEUNAVAILABLE**|無法取得的裝置|  
|**CTL\_E\_PERMISSIONDENIED**|拒絕的使用權限。|  
|**CTL\_E\_DISKNOTREADY**|尚未就緒的磁碟|  
|**CTL\_E\_PATHFILEACCESSERROR**|路徑\/檔案存取錯誤|  
|**CTL\_E\_PATHNOTFOUND**|路徑找不到|  
|**CTL\_E\_INVALIDPATTERNSTRING**|無效的模式字串|  
|**CTL\_E\_INVALIDUSEOFNULL**|為空的不正確地使用|  
|**CTL\_E\_INVALIDFILEFORMAT**|無效的檔案格式|  
|**CTL\_E\_INVALIDPROPERTYVALUE**|無效的屬性值。|  
|**CTL\_E\_INVALIDPROPERTYARRAYINDEX**|無效的屬性陣列索引|  
|**CTL\_E\_SETNOTSUPPORTEDATRUNTIME**|集合在執行階段不支援|  
|**CTL\_E\_SETNOTSUPPORTED**|不支援的集合 \(唯讀屬性\)|  
|**CTL\_E\_NEEDPROPERTYARRAYINDEX**|須提供屬性陣列索引|  
|**CTL\_E\_SETNOTPERMITTED**|未授與使用權限集合|  
|**CTL\_E\_GETNOTSUPPORTEDATRUNTIME**|取得在執行階段不支援|  
|**CTL\_E\_GETNOTSUPPORTED**|不支援 Get \(唯寫屬性\)|  
|**CTL\_E\_PROPERTYNOTFOUND**|屬性找不到|  
|**CTL\_E\_INVALIDCLIPBOARDFORMAT**|無效的剪貼簿格式。|  
|**CTL\_E\_INVALIDPICTURE**|無效的圖片|  
|**CTL\_E\_PRINTERERROR**|印表機錯誤|  
|**CTL\_E\_CANTSAVEFILETOTEMP**|無法將檔案儲存至 TEMP|  
|**CTL\_E\_SEARCHTEXTNOTFOUND**|搜尋文字找不到|  
|**CTL\_E\_REPLACEMENTSTOOLONG**|取代太長|  
  
 如果需要，請使用 **CUSTOM\_CTL\_SCODE** 巨集定義未由其中一個標準程式碼涵蓋的情況的自訂錯誤碼。  這個巨集的參數必須是介於 1000 和 32767，包含之間的整數。  例如：  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 如果您建立 ActiveX 控制項取代現有 VBX 控制，請定義以 VBX 控制用於確保的相同數字的 ActiveX 控制項錯誤碼錯誤碼相容。  
  
##  <a name="_core_handling_special_keys_in_your_control"></a> 處理特殊的輸入控制項  
 有時您可能想要處理某些按鍵組合以特殊模式;例如，插入新行，它會在按下 ENTER 鍵按下多行文字方塊控制項或是移動編輯控制項中群組之間時，便會向金鑰識別項按下。  
  
 如果 ActiveX 控制項基底類別是 `COleControl`，您可以覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md) 處理訊息，在容器管理這些檔案。  當使用這個技術，永遠傳回 **TRUE** 時，如果您在 `PreTranslateMessage`您覆寫的訊息。  
  
 下列程式碼範例會示範如何處理所有訊息一個可能的方式與方向索引鍵相關。  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 如需處理鍵盤的更多資訊為 ActiveX 控制項連結，請 ActiveX SDK 文件。  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> 會在執行階段存取的對話方塊控制項  
 您可以建立沒有使用者介面並會在執行階段的對話方塊控制項。  如果您將不可在執行階段的 ActiveX 控制項加入至對話方塊並使用 [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) 來存取控制項，控制項不會正確運作。  相反地，您應該使用下列其中一個衍生控制項的物件:  
  
-   使用加入成員變數精靈中，選取 **Control Variable** 然後選取控制項的 ID.  輸入成員變數名稱並選取控制項的包裝函式類別做為 **Control Type**。  
  
     \-或\-  
  
-   宣告區域變數和子類別當做對話方塊項目。  插入類似以下的程式碼 \(`CMyCtrl` 是包裝函式類別，為 `IDC_MYCTRL1` 控制項的 ID\):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)