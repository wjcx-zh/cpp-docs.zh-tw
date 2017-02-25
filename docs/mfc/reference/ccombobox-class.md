---
title: "CComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBox 類別"
  - "下拉式方塊, CComboBox objects"
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 下拉式方塊的功能。  
  
## 語法  
  
```  
class CComboBox : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComboBox::CComboBox](../Topic/CComboBox::CComboBox.md)|建構 `CComboBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComboBox::AddString](../Topic/CComboBox::AddString.md)|將字串加入至的結尾顯示於下拉式方塊的清單方塊中的  清單中，或是在清單方塊中排序的位置會 **CBS\_SORT** 樣式的。|  
|[CComboBox::Clear](../Topic/CComboBox::Clear.md)|刪除 \(\) 清除目前的選取範圍，如果有的話，在編輯控制項。|  
|[CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md)|呼叫由架構判斷新清單項目的相對位置 \(排序的主控描繪下拉式方塊。|  
|[CComboBox::Copy](../Topic/CComboBox::Copy.md)|複製目前的選取範圍，如果有的話，在 **CF\_TEXT** 格式的剪貼簿上。|  
|[CComboBox::Create](../Topic/CComboBox::Create.md)|建立下拉式方塊並將其附加至 `CComboBox` 物件。|  
|[CComboBox::Cut](../Topic/CComboBox::Cut.md)|刪除 \(\) 剪下目前的選取範圍，如果有的話，在編輯控制項及複製到 \[剪貼簿\] 上的刪除的文字。 **CF\_TEXT** 格式。|  
|[CComboBox::DeleteItem](../Topic/CComboBox::DeleteItem.md)|呼叫框架，在清單項目從一個主控描繪下拉式方塊刪除。|  
|[CComboBox::DeleteString](../Topic/CComboBox::DeleteString.md)|刪除下拉式方塊的清單方塊中的字串。|  
|[CComboBox::Dir](../Topic/CComboBox::Dir.md)|將檔案名稱的清單加入至下拉式方塊的清單方塊。|  
|[CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md)|呼叫框架，發生於主控描繪的下拉式方塊的視覺外觀變更。|  
|[CComboBox::FindString](../Topic/CComboBox::FindString.md)|尋找在下拉式方塊的清單方塊包含指定前置詞的第一個字串。|  
|[CComboBox::FindStringExact](../Topic/CComboBox::FindStringExact.md)|尋找第一個清單方塊字串 \(在下拉式方塊\) 符合指定的字串。|  
|[CComboBox::GetComboBoxInfo](../Topic/CComboBox::GetComboBoxInfo.md)|擷取有關 `CComboBox` 物件的相關資訊。|  
|[CComboBox::GetCount](../Topic/CComboBox::GetCount.md)|擷取集合中的項目數目下拉式方塊的清單方塊中的。|  
|[CComboBox::GetCueBanner](../Topic/CComboBox::GetCueBanner.md)|取得下拉式方塊控制項中顯示的提示文字。|  
|[CComboBox::GetCurSel](../Topic/CComboBox::GetCurSel.md)|擷取目前選取之項目的索引，如果有的話，在下拉式方塊的清單方塊。|  
|[CComboBox::GetDroppedControlRect](../Topic/CComboBox::GetDroppedControlRect.md)|擷取一個下拉式清單方塊中的可見 \(來源\) 下拉清單方塊的螢幕座標。|  
|[CComboBox::GetDroppedState](../Topic/CComboBox::GetDroppedState.md)|判斷一個下拉式清單方塊中的清單方塊中是否為可見 \(卸除向下\)。|  
|[CComboBox::GetDroppedWidth](../Topic/CComboBox::GetDroppedWidth.md)|擷取下拉式方塊的下拉式清單方塊部分的最小允許的寬度。|  
|[CComboBox::GetEditSel](../Topic/CComboBox::GetEditSel.md)|取得目前選取範圍的開始和結束字元位置在下拉式方塊可編輯控制項。|  
|[CComboBox::GetExtendedUI](../Topic/CComboBox::GetExtendedUI.md)|判斷下拉式方塊是否有預設使用者介面或擴充的使用者介面。|  
|[CComboBox::GetHorizontalExtent](../Topic/CComboBox::GetHorizontalExtent.md)|傳回在像素的寬度下拉式方塊的清單方塊部分可水平捲動。|  
|[CComboBox::GetItemData](../Topic/CComboBox::GetItemData.md)|擷取由應用程式所提供的 32 位元值與指定的下拉式方塊項目。|  
|[CComboBox::GetItemDataPtr](../Topic/CComboBox::GetItemDataPtr.md)|擷取與指定的下拉式方塊項目中應用程式所提供的 32 位元指標。|  
|[CComboBox::GetItemHeight](../Topic/CComboBox::GetItemHeight.md)|擷取高度在下拉式方塊中的清單項目。|  
|[CComboBox::GetLBText](../Topic/CComboBox::GetLBText.md)|從下拉式方塊的清單方塊取得字串。|  
|[CComboBox::GetLBTextLen](../Topic/CComboBox::GetLBTextLen.md)|取得字串的長度是在下拉式方塊的清單方塊中的。|  
|[CComboBox::GetLocale](../Topic/CComboBox::GetLocale.md)|擷取下拉式方塊的地區設定識別項。|  
|[CComboBox::GetMinVisible](../Topic/CComboBox::GetMinVisible.md)|取得可見項目的最小數字在目前的下拉式方塊的下拉式清單中。|  
|[CComboBox::GetTopIndex](../Topic/CComboBox::GetTopIndex.md)|傳回第一個可見項目的索引在下拉式方塊的清單方塊部分中。|  
|[CComboBox::InitStorage](../Topic/CComboBox::InitStorage.md)|預先配置記憶體區塊項目和字串在下拉式方塊的清單方塊部分。|  
|[CComboBox::InsertString](../Topic/CComboBox::InsertString.md)|字串插入下拉式方塊的清單方塊。|  
|[CComboBox::LimitText](../Topic/CComboBox::LimitText.md)|限制使用者可輸入下拉式方塊的編輯控制項文字的長度。|  
|[CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md)|呼叫由架構會設定下拉式方塊的大小，發生於主控描繪的下拉式方塊中建立。|  
|[CComboBox::Paste](../Topic/CComboBox::Paste.md)|貼上剪貼簿中的資料至編輯控制項會在目前游標位置。  資料，只有在剪貼簿中 **CF\_TEXT** 格式，其中包含的資料插入。|  
|[CComboBox::ResetContent](../Topic/CComboBox::ResetContent.md)|從下拉式方塊的清單方塊和編輯控制項中移除所有項目。|  
|[CComboBox::SelectString](../Topic/CComboBox::SelectString.md)|在  下拉式方塊的清單方塊中的字串，而且，如果找到字串，選取清單方塊中的字串並複製字串至編輯控制項。|  
|[CComboBox::SetCueBanner](../Topic/CComboBox::SetCueBanner.md)|設定根據下拉式方塊控制項中所顯示的提示文字。|  
|[CComboBox::SetCurSel](../Topic/CComboBox::SetCurSel.md)|選取下拉式方塊的清單方塊中的字串。|  
|[CComboBox::SetDroppedWidth](../Topic/CComboBox::SetDroppedWidth.md)|將下拉式方塊的下拉式清單方塊部分的最小允許的寬度。|  
|[CComboBox::SetEditSel](../Topic/CComboBox::SetEditSel.md)|選取下拉式方塊中編輯控制項的字元。|  
|[CComboBox::SetExtendedUI](../Topic/CComboBox::SetExtendedUI.md)|針對具有 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 樣式的下拉式方塊中所選取的預設使用者介面或擴充的使用者介面。|  
|[CComboBox::SetHorizontalExtent](../Topic/CComboBox::SetHorizontalExtent.md)|設定的寬度 \(以下拉式方塊的清單方塊部分可水平捲動。|  
|[CComboBox::SetItemData](../Topic/CComboBox::SetItemData.md)|將 32 位元的值與在下拉式方塊中指定的項目。|  
|[CComboBox::SetItemDataPtr](../Topic/CComboBox::SetItemDataPtr.md)|將 32 位元指標與在下拉式方塊中指定的項目。|  
|[CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md)|設定高度在下拉式方塊中的清單項目或下拉式方塊的編輯控制項 \(或靜態文字部分的高度 \(以像素為單位\)。|  
|[CComboBox::SetLocale](../Topic/CComboBox::SetLocale.md)|將下拉式方塊的地區設定識別項。|  
|[CComboBox::SetMinVisibleItems](../Topic/CComboBox::SetMinVisibleItems.md)|設定可看見的最小數目目前在下拉式方塊的下拉式清單中。|  
|[CComboBox::SetTopIndex](../Topic/CComboBox::SetTopIndex.md)|呼叫下拉式方塊的清單方塊部分會顯示具有指定索引的項目上。|  
|[CComboBox::ShowDropDown](../Topic/CComboBox::ShowDropDown.md)|顯示或隱藏具有 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 樣式下拉式方塊的清單方塊。|  
  
## 備註  
 下拉式方塊包含清單方塊再加上靜態控制項或編輯控制項。  當使用者在控制項旁邊時，選取  下拉箭號控制項的清單方塊部分可能會始終顯示或只能被關閉。  
  
 目前選取的項目 \(如果有的話\) 在清單方塊中的靜態或編輯控制項中顯示。  此外，如果，下拉式方塊的下拉式清單樣式，使用者可以輸入文字的字元清單中某個項目，然後，清單方塊，則為，如果可見，會反白顯示之初始字元的下一個項目。  
  
 下表比較三個下拉式方塊 [樣式](../../mfc/reference/combo-box-styles.md)。  
  
|樣式|何時是清單方塊可見?|靜態或編輯控制項?|  
|--------|----------------|---------------|  
|簡易|永遠|Edit|  
|下拉式清單|會維持向下|Edit|  
|下拉式清單|會維持向下|Static|  
  
 您可以建立一 `CComboBox` 物件從對話方塊範本或直接在您的程式碼。  在這兩種情況下，請先呼叫建構 `CComboBox` 物件的 `CComboBox` ;然後呼叫 [建立](../Topic/CComboBox::Create.md) 成員函式來建立控制項並將它附加至 `CComboBox` 物件。  
  
 如果您要管理 Windows 下拉式方塊所傳送的通知訊息給它的父 `CDialog`\(通常是從衍生的類別\)，將訊息對應 \(Message Map 輸入和訊息處理常式成員函式來為每則訊息的父類別。  
  
 每個訊息對應 \(Message Map 輸入的格式如下:  
  
 **ON\_**告知**\(**`id`**,**`memberFxn`**\)**  
  
 其中 `id` 指定傳送下拉式方塊控制項的子視窗 ID 告知和 `memberFxn` 是您撰寫處理告知父代成員函式的名稱。  
  
 父的函式原型 \(Prototype\) 如下:  
  
 **afx\_msg** `void` `memberFxn` **\(**\);  
  
 某些通知傳送命令無法預測。  特別是， **CBN\_SELCHANGE** 告知可能在 **CBN\_CLOSEUP** 通知之前和之後發生任一種。  
  
 可能的訊息對應 \(Message Map 輸入如下:  
  
-   **ON\_CBN\_CLOSEUP** \(Windows 3.1 \(含\) 以後版本\)。下拉式方塊的清單方塊已關閉。  這個告知訊息也不會具有 [CBS\_SIMPLE](../../mfc/reference/combo-box-styles.md) 樣式的下拉式方塊傳送。  
  
-   **ON\_CBN\_DBLCLK** 使用者按兩下下拉式方塊的清單方塊中的字串。  這個告知資訊會 **CBS\_SIMPLE** 樣式的下拉式方塊只傳送。  對於 [CBS\_DROPDOWN](../../mfc/reference/combo-box-styles.md) 或 [CBS\_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) 樣式的下拉式方塊，因為 \(double\-click\) 隱藏清單方塊中，按兩下，不會發生。  
  
-   **ON\_CBN\_DROPDOWN** 下拉式方塊的清單方塊會卸除向下 \(可見\)。  這個告知訊息可以針對 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 樣式的下拉式方塊時才會發生。  
  
-   **ON\_CBN\_EDITCHANGE** 使用者採取可能已經修改過在下拉式方塊可編輯控制項部分文字的動作。  不同於 **CBN\_EDITUPDATE** 訊息，在 Windows 中，更新螢幕之後，這個訊息傳送。  如果下拉式方塊具有 **CBS\_DROPDOWNLIST** 樣式，則不會傳送訊息。  
  
-   **ON\_CBN\_EDITUPDATE** 下拉式方塊的編輯控制項區段會顯示修改後的文字。  這就會傳送通知訊息，在控制項已格式化文字之後，但是，在顯示文字之前。  如果下拉式方塊具有 **CBS\_DROPDOWNLIST** 樣式，則不會傳送訊息。  
  
-   **ON\_CBN\_ERRSPACE** 下拉式方塊無法配置足夠的記憶體以符合特定需求。  
  
-   **ON\_CBN\_SELENDCANCEL** \(Windows 3.1 \(含\) 以後版本\)。表示是否應該取消使用者選取的項目。  使用者按一下項目然後按一下另一個視窗或控制項隱藏下拉式方塊的清單方塊。  這就會傳送通知訊息，在 **CBN\_CLOSEUP** 通知訊息表示前者應該忽略使用者選取的項目。  **CBN\_SELENDCANCEL** 或 **CBN\_SELENDOK** 就會傳送通知訊息，即使 **CBN\_CLOSEUP** 通知訊息不會傳送 \(在具有 **CBS\_SIMPLE** 樣式的下拉式方塊的情況下\)。  
  
-   **ON\_CBN\_SELENDOK** 使用者選取項目然後按 ENTER 鍵或按一下向下鍵隱藏下拉式方塊的清單方塊。  這就會傳送通知訊息，在 **CBN\_CLOSEUP** 訊息表示前者應該將使用者的選取有效的。  **CBN\_SELENDCANCEL** 或 **CBN\_SELENDOK** 就會傳送通知訊息，即使 **CBN\_CLOSEUP** 通知訊息不會傳送 \(在具有 **CBS\_SIMPLE** 樣式的下拉式方塊的情況下\)。  
  
-   **ON\_CBN\_KILLFOCUS** 下拉式方塊失去輸入焦點。  
  
-   **ON\_CBN\_SELCHANGE** 在下拉式方塊的清單方塊的選取項目會變更因為按一下清單方塊或選取項目變更時的使用者使用方向鍵。  在處理這個訊息時，下拉式方塊的編輯控制項的文字可以 `GetLBText` 或其他類似的函式才會擷取。  `GetWindowText` 無法使用。  
  
-   **ON\_CBN\_SETFOCUS** 下拉式方塊接收輸入焦點。  
  
 如果您在對話方塊內的 `CComboBox` 物件 \(透過對話方塊資源\)，自動終結 `CComboBox` 物件，在使用者關閉對話方塊時。  
  
 如果您內嵌在另一個視窗物件中有一個 `CComboBox` 物件，所以您不需要終結它。  如果您在堆疊上建立物件， `CComboBox` 自動終結。  您可以使用 **new** 函式，建立。 `CComboBox` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結此物件終結時， Windows 下拉式方塊。  
  
 **Note** ，如果您想要處理 `WM_KEYDOWN` 和 `WM_CHAR` 訊息，您必須將子類別下拉式方塊的編輯和清單方塊控制項，從 `CEdit` 和 `CListBox`衍生類別並將這些訊息的處理常式加入至衍生類別。  如需詳細資訊， [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;Q174667](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q174667) 請參閱和 [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)