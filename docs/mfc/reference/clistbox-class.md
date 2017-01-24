---
title: "CListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListBox 類別"
  - "清單方塊"
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供視窗清單方塊的功能。  
  
## 語法  
  
```  
class CListBox : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CListBox::CListBox](../Topic/CListBox::CListBox.md)|建構 `CListBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CListBox::AddString](../Topic/CListBox::AddString.md)|將字串加入至清單方塊。|  
|[CListBox::CharToItem](../Topic/CListBox::CharToItem.md)|提供自訂 `WM_CHAR` 的覆寫處理沒有字串的主控描繪清單方塊。|  
|[CListBox::CompareItem](../Topic/CListBox::CompareItem.md)|呼叫由架構判斷新項目的位置 \(排序的主控描繪清單方塊。|  
|[CListBox::Create](../Topic/CListBox::Create.md)|建立視窗清單方塊並將其附加至 `CListBox` 物件。|  
|[CListBox::DeleteItem](../Topic/CListBox::DeleteItem.md)|呼叫框架，當使用者從主控描繪清單方塊中的項目。|  
|[CListBox::DeleteString](../Topic/CListBox::DeleteString.md)|從清單方塊刪除項目的字串。|  
|[CListBox::Dir](../Topic/CListBox::Dir.md)|將檔名，磁碟機或兩者都是從目前的目錄加入至清單方塊。|  
|[CListBox::DrawItem](../Topic/CListBox::DrawItem.md)|呼叫框架，其在主控描繪清單方塊的視覺外觀變更。|  
|[CListBox::FindString](../Topic/CListBox::FindString.md)|在  清單方塊中的字串。|  
|[CListBox::FindStringExact](../Topic/CListBox::FindStringExact.md)|尋找符合指定之字串的第一個清單方塊字串。|  
|[CListBox::GetAnchorIndex](../Topic/CListBox::GetAnchorIndex.md)|擷取目前錨點項目之以零起始的索引在清單方塊中。|  
|[CListBox::GetCaretIndex](../Topic/CListBox::GetCaretIndex.md)|確定有焦點矩形在多重選取清單方塊中項目的索引。|  
|[CListBox::GetCount](../Topic/CListBox::GetCount.md)|傳回的字串數目。在清單方塊中。|  
|[CListBox::GetCurSel](../Topic/CListBox::GetCurSel.md)|傳回目前所選取的字串之以零起始的索引在清單方塊中。|  
|[CListBox::GetHorizontalExtent](../Topic/CListBox::GetHorizontalExtent.md)|傳回在像素的寬度清單方塊可水平捲動。|  
|[CListBox::GetItemData](../Topic/CListBox::GetItemData.md)|傳回 32 位元的值與清單方塊項目。|  
|[CListBox::GetItemDataPtr](../Topic/CListBox::GetItemDataPtr.md)|傳回指向清單方塊項目。|  
|[CListBox::GetItemHeight](../Topic/CListBox::GetItemHeight.md)|決定高度在清單方塊中的項目。|  
|[CListBox::GetItemRect](../Topic/CListBox::GetItemRect.md)|會在目前顯示，傳回清單方塊項目的週框 \(Bounding Rectangle\)。|  
|[CListBox::GetListBoxInfo](../Topic/CListBox::GetListBoxInfo.md)|擷取項目數量的每個資料行。|  
|[CListBox::GetLocale](../Topic/CListBox::GetLocale.md)|擷取清單方塊的地區設定識別項。|  
|[CListBox::GetSel](../Topic/CListBox::GetSel.md)|傳回清單方塊項目的選取狀態。|  
|[CListBox::GetSelCount](../Topic/CListBox::GetSelCount.md)|傳回在多重選取清單方塊中目前選取的字串數目。|  
|[CListBox::GetSelItems](../Topic/CListBox::GetSelItems.md)|傳回目前在清單方塊中選取之字串的索引。|  
|[CListBox::GetText](../Topic/CListBox::GetText.md)|將清單方塊項目緩衝區。|  
|[CListBox::GetTextLen](../Topic/CListBox::GetTextLen.md)|在清單方塊中項目的位元組傳回長度。|  
|[CListBox::GetTopIndex](../Topic/CListBox::GetTopIndex.md)|傳回第一個可見的字串索引在清單方塊中。|  
|[CListBox::InitStorage](../Topic/CListBox::InitStorage.md)|預先配置記憶體區塊清單方塊項目和字串的。|  
|[CListBox::InsertString](../Topic/CListBox::InsertString.md)|在特定位置插入字串在清單方塊中。|  
|[CListBox::ItemFromPoint](../Topic/CListBox::ItemFromPoint.md)|傳回清單方塊項目索引最接近的點。|  
|[CListBox::MeasureItem](../Topic/CListBox::MeasureItem.md)|呼叫框架，其在主控描繪清單方塊建立判斷清單方塊維度。|  
|[CListBox::ResetContent](../Topic/CListBox::ResetContent.md)|清除清單方塊中的所有項目。|  
|[CListBox::SelectString](../Topic/CListBox::SelectString.md)|搜尋並選取單一選取清單方塊中的字串。|  
|[CListBox::SelItemRange](../Topic/CListBox::SelItemRange.md)|選取或取消選取字串的範圍在多重選取清單方塊中的。|  
|[CListBox::SetAnchorIndex](../Topic/CListBox::SetAnchorIndex.md)|設定多重選取清單方塊中的錨定開始擴充選取範圍。|  
|[CListBox::SetCaretIndex](../Topic/CListBox::SetCaretIndex.md)|設定焦點矩形中的項目或進行多重選取清單方塊中的指定索引處的。|  
|[CListBox::SetColumnWidth](../Topic/CListBox::SetColumnWidth.md)|設定多欄的清單方塊中的資料行寬度。|  
|[CListBox::SetCurSel](../Topic/CListBox::SetCurSel.md)|選取清單方塊中的字串。|  
|[CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md)|設定的寬度 \(以像素為清單方塊可水平捲動。|  
|[CListBox::SetItemData](../Topic/CListBox::SetItemData.md)|將 32 位元的值與清單方塊項目。|  
|[CListBox::SetItemDataPtr](../Topic/CListBox::SetItemDataPtr.md)|將指標清單方塊項目。|  
|[CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md)|設定高度在清單方塊中的項目。|  
|[CListBox::SetLocale](../Topic/CListBox::SetLocale.md)|將清單方塊的地區設定識別項。|  
|[CListBox::SetSel](../Topic/CListBox::SetSel.md)|選取或取消選取多重選取清單方塊中的清單方塊項目。|  
|[CListBox::SetTabStops](../Topic/CListBox::SetTabStops.md)|設定清單方塊的定位停駐點 \(Tab Stop\) 位置。|  
|[CListBox::SetTopIndex](../Topic/CListBox::SetTopIndex.md)|將第一個可見的字串之以零起始的索引在清單方塊中。|  
|[CListBox::VKeyToItem](../Topic/CListBox::VKeyToItem.md)|提供自訂 `WM_KEYDOWN` 的覆寫處理為清單方塊。 **LBS\_WANTKEYBOARDINPUT** 樣式集合。|  
  
## 備註  
 清單方塊會顯示項目清單，例如檔名，則使用者可以檢視並選取 。  
  
 在單一選取清單方塊，使用者只能選取一個項目。  在多重選取的清單方塊，項目範圍可選取。  當使用者選取某項目時，它會反白顯示，而清單方塊傳送通知訊息至父視窗。  
  
 您可以建立一個清單方塊從對話方塊範本或直接在您的程式碼。  直接建立它， `CListBox` 建構物件，然後呼叫 [建立](../Topic/CListBox::Create.md) 成員函式建立視窗清單方塊控制項並將它附加至 `CListBox` 物件。  使用清單方塊中的  對話方塊樣板宣告，在您的對話方塊類別的清單方塊變數，然後使用 `DDX_Control` 在您的對話方塊類別的 `DoDataExchange` 函式連接成員變數加入至控制項。  \(這會自動為您執行，當您將控制變數設定為您的對話方塊類別\)。  
  
 語法結構可以是從 `CListBox`從衍生之類別中的程序。  提供衍生類別的建構函式和呼叫 **建立** 從建構函式中呼叫。  
  
 如果您要處理的視窗清單方塊所傳送的通知訊息給它的父 [CDialog](../../mfc/reference/cdialog-class.md)\(通常是從衍生的類別\)，將訊息對應 \(Message Map 輸入和訊息處理常式成員函式來為每則訊息的父類別。  
  
 每個訊息對應 \(Message Map 輸入的格式如下:  
  
 `ON_Notification( id, memberFxn )`  
  
 其中 `id` 指定清單方塊傳送控制項的子視窗 ID 告知和 `memberFxn` 是您撰寫處理告知父代成員函式的名稱。  
  
 父的函式原型 \(Prototype\) 如下:  
  
 `afx_msg void memberFxn( );`  
  
 下列可能的訊息對應項目並將它們傳送至父控制項描述清單:  
  
-   **ON\_LBN\_DBLCLK** 使用者按兩下清單方塊中的字串。  具有 [LBS\_NOTIFY](../../mfc/reference/list-box-styles.md) 樣式只的清單方塊會傳送通知訊息。  
  
-   **ON\_LBN\_ERRSPACE** 清單方塊無法配置足夠的記憶體以滿足要求。  
  
-   **ON\_LBN\_KILLFOCUS** 清單方塊失去輸入焦點。  
  
-   **ON\_LBN\_SELCANCEL** 目前清單方塊選取項目移除。  在清單方塊中有 **LBS\_NOTIFY** 樣式時，這項資訊只傳送。  
  
-   在清單方塊中選取範圍已變更的**ON\_LBN\_SELCHANGE** 。  如果 [CListBox::SetCurSel](../Topic/CListBox::SetCurSel.md) 成員函式，變更選取項目會告知不會傳送訊息。  這個告知只適用於有 **LBS\_NOTIFY** 樣式的清單方塊。  **LBN\_SELCHANGE** 通知訊息為多重選取清單方塊中傳送，每當使用者按方向鍵，即使，選取範圍不會變更。  
  
-   **ON\_LBN\_SETFOCUS** 清單方塊接收輸入焦點。  
  
-   **ON\_WM\_CHARTOITEM** 沒有字串的主控描繪清單方塊 `WM_CHAR` 接收訊息。  
  
-   具有 **LBS\_WANTKEYBOARDINPUT** 樣式的**ON\_WM\_VKEYTOITEM** A 清單方塊 `WM_KEYDOWN` 接收訊息。  
  
 如果您在對話方塊內的 `CListBox` 物件 \(透過對話方塊資源\)，自動終結 `CListBox` 物件，在使用者關閉對話方塊時。  
  
 如果您在視窗內的 `CListBox` 物件，您可能需要 `CListBox` 終結物件。  如果您在堆疊上建立物件， `CListBox` 自動終結。  您可以使用 **new** 函式，建立。 `CListBox` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結它，當使用者關閉父視窗時。  
  
 如果您在 `CListBox` 配置物件的任何記憶體，請覆寫 `CListBox` 解構函式處理組態。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 CTRLTEST](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)