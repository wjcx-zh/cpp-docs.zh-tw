---
title: "CMenu Class | Microsoft Docs"
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
  - "CMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMenu class"
  - "HMENU"
  - "功能表, 基底類別"
  - "功能表, class"
  - "功能表, 建立"
  - "功能表, 管理"
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

視窗 `HMENU`的套件。  
  
## 語法  
  
```  
class CMenu : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMenu::CMenu](../Topic/CMenu::CMenu.md)|建構 `CMenu` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)|附加新項目至這個功能表的尾端。|  
|[CMenu::Attach](../Topic/CMenu::Attach.md)|附加視窗功能表的控制代碼。 `CMenu` 物件。|  
|[CMenu::CheckMenuItem](../Topic/CMenu::CheckMenuItem.md)|將旁邊的核取記號。或在快顯功能表的功能表項目會移除核取記號。|  
|[CMenu::CheckMenuRadioItem](../Topic/CMenu::CheckMenuRadioItem.md)|在  功能表項目旁的  群組中放置一個選項按鈕並從其他功能表項目移除選項按鈕。|  
|[CMenu::CreateMenu](../Topic/CMenu::CreateMenu.md)|建立空的功能表並將它附加至 `CMenu` 物件。|  
|[CMenu::CreatePopupMenu](../Topic/CMenu::CreatePopupMenu.md)|建立一個空的快顯功能表並將其附加至 `CMenu` 物件。|  
|[CMenu::DeleteMenu](../Topic/CMenu::DeleteMenu.md)|從檔案功能表中刪除指定的項目。  如果功能表項目有關聯的快顯功能表，終結控制代碼快顯功能表並釋放它所使用的記憶體。|  
|[CMenu::DeleteTempMap](../Topic/CMenu::DeleteTempMap.md)|刪除 `FromHandle` 成員函式所建立的所有 `CMenu` 暫存物件。|  
|[CMenu::DestroyMenu](../Topic/CMenu::DestroyMenu.md)|終結功能表附加至 `CMenu` 物件並釋放功能表佔用的記憶體。|  
|[CMenu::Detach](../Topic/CMenu::Detach.md)|中斷連結 `CMenu` 物件的視窗功能表控制代碼並將控制代碼傳回。|  
|[CMenu::DrawItem](../Topic/CMenu::DrawItem.md)|呼叫由架構，會在建立主控描繪 \(Owner\-Drawn\) 功能表的視覺外觀變更。|  
|[CMenu::EnableMenuItem](../Topic/CMenu::EnableMenuItem.md)|啟用，停用 \(或暗灰色\) 功能表項目。|  
|[CMenu::FromHandle](../Topic/CMenu::FromHandle.md)|傳回指標設定為指定的物件 `CMenu` 視窗功能表控制代碼。|  
|[CMenu::GetDefaultItem](../Topic/CMenu::GetDefaultItem.md)|決定指定的預設功能表的功能表項目。|  
|[CMenu::GetMenuContextHelpId](../Topic/CMenu::GetMenuContextHelpId.md)|擷取說明主題代碼與功能表。|  
|[CMenu::GetMenuInfo](../Topic/CMenu::GetMenuInfo.md)|擷取有關特定功能表的資訊。|  
|[CMenu::GetMenuItemCount](../Topic/CMenu::GetMenuItemCount.md)|判斷集合中的項目數目快顯或最上層的功能表。|  
|[CMenu::GetMenuItemID](../Topic/CMenu::GetMenuItemID.md)|取得功能表項目的功能表項目識別項所指定的位置。|  
|[CMenu::GetMenuItemInfo](../Topic/CMenu::GetMenuItemInfo.md)|擷取與功能表項目相關的資訊。|  
|[CMenu::GetMenuState](../Topic/CMenu::GetMenuState.md)|傳回指定之功能表項目的狀態或項目數目的快顯功能表的。|  
|[CMenu::GetMenuString](../Topic/CMenu::GetMenuString.md)|擷取指定之功能表項目的標籤 \(Label\)。|  
|[CMenu::GetSafeHmenu](../Topic/CMenu::GetSafeHmenu.md)|傳回這 `CMenu` 物件包裝的 `m_hMenu` 。|  
|[CMenu::GetSubMenu](../Topic/CMenu::GetSubMenu.md)|擷取指標快顯功能表。|  
|[CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)|插入新的功能表項目中的指定位置上，移至功能表項目底下的其他項目。|  
|[CMenu::InsertMenuItem](../Topic/CMenu::InsertMenuItem.md)|插入新的功能表項目在功能表的指定位置。|  
|[CMenu::LoadMenu](../Topic/CMenu::LoadMenu.md)|從可執行檔載入功能表資源並將其附加至 `CMenu` 物件。|  
|[CMenu::LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md)|從  功能表範本載入一個功能表會在記憶體中並將其附加至 `CMenu` 物件。|  
|[CMenu::MeasureItem](../Topic/CMenu::MeasureItem.md)|呼叫由架構判斷功能表維度，當一個主控描繪 \(Owner\-Drawn\) 功能表建立。|  
|[CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)|若要變更現有的功能表項目在指定的位置。|  
|[CMenu::RemoveMenu](../Topic/CMenu::RemoveMenu.md)|刪除具有一個關聯的快顯功能表的功能表項目從指定的功能表。|  
|[CMenu::SetDefaultItem](../Topic/CMenu::SetDefaultItem.md)|設定指定之功能表的預設功能表項目。|  
|[CMenu::SetMenuContextHelpId](../Topic/CMenu::SetMenuContextHelpId.md)|設定與關聯的說明主題代碼與功能表。|  
|[CMenu::SetMenuInfo](../Topic/CMenu::SetMenuInfo.md)|如需設定特定功能表的資訊。|  
|[CMenu::SetMenuItemBitmaps](../Topic/CMenu::SetMenuItemBitmaps.md)|會將指定的核取記號點陣圖與功能表項目產生關聯。|  
|[CMenu::SetMenuItemInfo](../Topic/CMenu::SetMenuItemInfo.md)|變更與功能表項目相關的資訊。|  
|[CMenu::TrackPopupMenu](../Topic/CMenu::TrackPopupMenu.md)|在指定的位置中會顯示一個浮動快顯功能表並追蹤項目的選取範圍在快顯功能表中。|  
|[CMenu::TrackPopupMenuEx](../Topic/CMenu::TrackPopupMenuEx.md)|在指定的位置中會顯示一個浮動快顯功能表並追蹤項目的選取範圍在快顯功能表中。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CMenu::operator HMENU](../Topic/CMenu::operator%20HMENU.md)|擷取功能表物件的控制代碼。|  
|[CMenu::operator \!\=](../Topic/CMenu::operator%20!=.md)|判斷兩個功能表物件是否不相等。|  
|[CMenu::operator \=\=](../Topic/CMenu::operator%20==.md)|判斷兩個功能表物件是否相等。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMenu::m\_hMenu](../Topic/CMenu::m_hMenu.md)|指定控制代碼的視窗功能表附加至 `CMenu` 物件。|  
  
## 備註  
 用以建立，追蹤更新，並終結功能表提供成員函式。  
  
 建立在堆疊框架的 `CMenu` 物件為區域，然後呼叫 `CMenu` 的成員函式來管理新功能表的需要。  接著，呼叫將功能表的 [CWnd::SetMenu](../Topic/CWnd::SetMenu.md) 至視窗，後面緊接著呼叫 `CMenu`[中斷連結](../Topic/CMenu::Detach.md) 物件的成員函式。  `CWnd::SetMenu` 成員函式上設定視窗功能表指向新的  功能表上，讓視窗會重繪以反映功能表變更，也可透過功能表的擁有權至視窗。  對的呼叫 **中斷連結** 中斷連結 `CMenu` 物件的 `HMENU` ，如此一來，當 `CMenu` ，區域變數會超出範圍時，就不會再擁有的 `CMenu` 物件解構函式不會嘗試終結功能表。  功能表，終結時，自動終結視窗。  
  
 您可以使用 [LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md) 成員函式從範本建立的功能表在記憶體，但是，從資源建立的功能表會以呼叫 [LoadMenu](../Topic/CMenu::LoadMenu.md) 更容易維護，，和功能表資源可以功能表編輯器建立和修改。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 CTRLTEST](../../top/visual-cpp-samples.md)   
 [MFC 範例 DYNAMENU](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)