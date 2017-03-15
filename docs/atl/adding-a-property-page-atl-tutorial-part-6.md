---
title: "加入屬性頁 (ATL 教學課程，第 6 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 加入屬性頁 (ATL 教學課程，第 6 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性頁會實作為不同的 COM 物件，它們就必須共用。  在這個步驟中，您將執行下列工作將屬性頁加入至控制項:  
  
-   建立資源屬性頁  
  
-   加入程式碼以建立和管理屬性頁  
  
-   將屬性頁加入至控制項  
  
## 建立資源屬性頁  
 若要將屬性頁加入至控制項，請使用 ATL 加入類別精靈。  
  
#### 將屬性頁  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下多邊形。  
  
2.  在捷徑功能表中按一下 \[加入\]，然後按一下 \[加入類別\]。  
  
3.  從範本、選取的 \[**ATL 屬性頁**\] 並按一下 \[**新增**\] 清單。  
  
4.  在 ATL 屬性頁精靈出現時，請輸入 `PolyProp` 做為 \[**簡短**\] 名稱。  
  
5.  按一下 \[**字串**\] 開啟 \[**字串**\] 網頁和輸入 \[**\_&Polygon**\] 做為 \[**標題**\]。  
  
     屬性頁的 \[**標題**\] 是出現在該頁面上的  索引標籤的字串。  \[**文件字串**\] 是屬性架構在狀態列或工具提示使用將的描述。  請注意標準屬性框目前並未使用這個字串，因此，您可以將其保留預設內容。  當您時不會產生 \[**說明檔**\] ，所以，請刪除該文字方塊中輸入。  
  
6.  按一下 ， \[**完成**\]，而且屬性頁將建立物件。  
  
 下列三個檔案建立:  
  
|檔案|描述|  
|--------|--------|  
|PolyProp.h|包含 C\+\+ 類別 `CPolyProp`，實作屬性頁。|  
|PolyProp.cpp|包含 PolyProp.h 檔案。|  
|PolyProp.rgs|將屬性註冊頁面物件的註冊指令碼。|  
  
 下列程式碼變更也會進行:  
  
-   新的屬性頁加入至物件的 Polygon.cpp 輸入對應。  
  
-   `PolyProp` 類別加入至 Polygon.idl 檔案。  
  
-   新的註冊指令碼檔 PolyProp.rgs 加入至專案資源。  
  
-   對話方塊範本加入至屬性頁的專案資源。  
  
-   您指定的屬性加入字串資源字串資料表。  
  
 現在加入欄位要出現在  屬性頁。  
  
#### 將欄位加入至屬性頁  
  
1.  在 \[方案總管\] 中，按兩下 Polygon.rc 資源檔。  這樣會開啟 \[資源檢視\]。  
  
2.  在 \[資源檢視\] 中，展開  對話方塊節點並且按兩下 IDD\_POLYPROP。  請注意出現的對話方塊空白 \(除了告訴您插入您的控制項在這裡的標籤。  
  
3.  選取該標籤並將藉由修改 \[**屬性**\] 視窗的 \[**字幕**\] 讀取文字 `框:` 。  
  
4.  調整方塊標籤，以便調整文字的大小。  
  
5.  在標籤右邊從工具箱拖曳該編輯控制項。  
  
6.  最後，使用 \[屬性\] 視窗中，變更編輯控制項的 \[**ID**\] 至 `IDC_SIDES` 。  
  
 此完成建立屬性頁資源的處理序 \(Process\)。  
  
## 加入程式碼以建立和管理屬性頁  
 現在您已經建立屬性頁資源，您必須撰寫實作程式碼。  
  
 首先， \[**套用**\] ，當按下按鈕，請將 `CPolyProp` 類別設定邊數在物件上。  
  
#### 若要修改套用請函式設定邊數  
  
1.  使用下列程式碼取代 PolyProp.h 的 `Apply` 函式:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 屬性頁可以擁有多個用戶端一次就會附加至其中，因此， `Apply` 函式迴圈並呼叫每個用戶端的 `put_Sides` 具有從編輯方塊要擷取的值。  您可以使用 [CComQIPtr](../atl/reference/ccomqiptr-class.md) 類別，則在每個物件的 `QueryInterface` 從 **IUnknown** 介面的 `IPolyCtl` 介面 \(儲存在 `m_ppUnk` 陣列\)。  
  
 程式碼會檢查設定 `Sides` 屬性實際運作。  如果失敗，則程式碼會顯示從 **IErrorInfo** 介面的訊息方塊錯誤詳細資料。  通常，容器要求物件 **ISupportErrorInfo** 介面則先呼叫 `InterfaceSupportsErrorInfo` ，判斷物件是否支援將錯誤資訊。  您可以略過這項工作。  
  
 [CComPtr](../atl/reference/ccomptr-class.md) 透過自動處理計數的參考來協助您，因此，您不需要呼叫介面中的 `Release` 。  `CComBSTR` 協助您 `BSTR` 的處理，因此，您不需要執行最後的 `SysFreeString` 呼叫。  您也可以使用其中一個各種字串轉換為類別，因此，如果需要，您也可以轉換 `BSTR` \(這就是為什麼 `USES_CONVERSION` 巨集是在函式的開頭\)。  
  
 您也需要設定  屬性頁的記錄變更旗標表示應該啟用 \[**套用**\] 按鈕。  當使用者變更 \[**邊界**\] 編輯方塊中的值，就會發生這種情形。  
  
#### 處理套用按鈕  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下 CPolyProp 並按一下 \[**屬性**\] 在捷徑功能表上的 。  
  
2.  在 \[屬性\] 視窗中，按一下 \[**事件**\] 圖示。  
  
3.  展開 \[事件清單的 `IDC_SIDES` 節點。  
  
4.  選取的 `EN_CHANGE`，然後從下拉式功能表右邊，按一下 \[**\<Add\> OnEnChangeSides**\]。  `OnEnChangeSides` 處理常式宣告加入至 Polyprop.h 和處理常式實作 Polyprop.cpp。  
  
 接下來，您將會修改這個處理常式。  
  
#### 修改 OnEnChangeSides 方法  
  
1.  將 Polyprop.cpp 的下列程式碼加入至 `OnEnChangeSides` 方法 \(刪除任何程式碼精靈將其中\):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 當 **WM\_COMMAND** 資訊傳送 `IDC_SIDES` 控制項， **EN\_CHANGE** 告知`OnEnChangeSides` 會呼叫。  `OnEnChangeSides` 然後呼叫 `SetDirty` ，而且成功指示屬性頁的 `TRUE` 現在已經變更，而且應該啟用 \[**套用**\] 按鈕。  
  
## 將屬性頁加入至控制項  
 ATL 加入類別精靈，而 ATL 屬性頁精靈不會自動將屬性頁加入至您的控制項，，因為可能會在專案的多個控制項。  您必須將項目加入至控制項的屬性。  
  
#### 將屬性頁  
  
1.  開啟 PolyCtl.h 並將這一行加入屬性對應:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 控制項的屬性對應現在看起來就像這樣:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 您可以加入了哪些屬性頁 CLSID 的 `PROP_PAGE` 巨集，，不過，如果您使用 `PROP_ENTRY` 巨集如下所示， `Sides` 屬性值也會儲存，當控制項儲存時。  
  
 使用巨集的三個參數是屬性描述、屬性的 DISPID 和有屬性屬性頁的 CLSID。  這個方法很有用，例如，，如果您將控制項載入到 Visual Basic 並設定邊數在設計階段。  由於邊數儲存，，當您重新載入您的 Visual Basic 專案，邊數將會還原。  
  
## 建置和測試控制項  
 現在請建立該控制項並將其插入 ActiveX 控制項測試容器。  在測試容器，請在功能表上，按一下 \[**編輯**\]\[**PolyCtl 類別物件**\]。  屬性頁隨即出現，按一下 \[**多邊形**\] 索引標籤。  
  
 \[**套用**\] 按鈕一開始會停用。  開始輸入在 \[**邊界**\] 方塊中的值，並 \[**套用**\] 按鈕將會變成可用狀態。  在您完成輸入值之後，請按一下 \[**套用**\] 按鈕。  控制項顯示變更和 \[**套用**\] 按鈕已停用。  輸入無效值的嘗試。  您會看到訊息方塊包含錯誤描述您從 `put_Sides` 函式的集合。  
  
 接下來，您將在 Web 網頁中將您的控制項。  
  
 [回到步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [在 &#91;步驟 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)