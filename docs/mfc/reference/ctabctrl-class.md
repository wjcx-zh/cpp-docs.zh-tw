---
title: "CTabCtrl Class | Microsoft Docs"
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
  - "CTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl class"
  - "CTabCtrl class, 通用控制項"
  - "索引標籤控制項"
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用控制項的功能。  
  
## 語法  
  
```  
class CTabCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTabCtrl::CTabCtrl](../Topic/CTabCtrl::CTabCtrl.md)|建構 `CTabCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTabCtrl::AdjustRect](../Topic/CTabCtrl::AdjustRect.md)|計算指定的索引標籤控制項的顯示區視窗矩形或計算會對應到指定的顯示區域的矩形視窗。|  
|[CTabCtrl::Create](../Topic/CTabCtrl::Create.md)|建立索引標籤控制項並將其附加至 `CTabCtrl` 物件的執行個體。|  
|[CTabCtrl::CreateEx](../Topic/CTabCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的索引標籤控制項並將其附加至 `CTabCtrl` 物件的執行個體。|  
|[CTabCtrl::DeleteAllItems](../Topic/CTabCtrl::DeleteAllItems.md)|從的索引標籤控制項中移除所有項目。|  
|[CTabCtrl::DeleteItem](../Topic/CTabCtrl::DeleteItem.md)|從的索引標籤控制項中移除項目。|  
|[CTabCtrl::DeselectAll](../Topic/CTabCtrl::DeselectAll.md)|如果在索引標籤控制項中的項目，則會清除任何已按下的。|  
|[CTabCtrl::DrawItem](../Topic/CTabCtrl::DrawItem.md)|繪製索引標籤控制項中指定之項目的。|  
|[CTabCtrl::GetCurFocus](../Topic/CTabCtrl::GetCurFocus.md)|擷取與索引標籤控制項的目前焦點的索引標籤。|  
|[CTabCtrl::GetCurSel](../Topic/CTabCtrl::GetCurSel.md)|判斷在索引標籤控制項中目前選取的索引標籤。|  
|[CTabCtrl::GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md)|擷取針對索引標籤控制項是目前使用中的延伸樣式。|  
|[CTabCtrl::GetImageList](../Topic/CTabCtrl::GetImageList.md)|擷取影像清單與索引標籤控制項。|  
|[CTabCtrl::GetItem](../Topic/CTabCtrl::GetItem.md)|擷取與一個索引標籤的資訊在索引標籤控制項。|  
|[CTabCtrl::GetItemCount](../Topic/CTabCtrl::GetItemCount.md)|擷取索引標籤的索引標籤區域中的控制項。|  
|[CTabCtrl::GetItemRect](../Topic/CTabCtrl::GetItemRect.md)|擷取一個索引標籤的週框 \(Bounding Rectangle\) 的索引標籤控制項。|  
|[CTabCtrl::GetItemState](../Topic/CTabCtrl::GetItemState.md)|擷取所指定的索引標籤控制項中項目的狀態。|  
|[CTabCtrl::GetRowCount](../Topic/CTabCtrl::GetRowCount.md)|擷取目前的資料列索引標籤在索引標籤控制項。|  
|[CTabCtrl::GetToolTips](../Topic/CTabCtrl::GetToolTips.md)|擷取工具提示控制項的控制代碼與索引標籤控制項。|  
|[CTabCtrl::HighlightItem](../Topic/CTabCtrl::HighlightItem.md)|將索引標籤項目的焦點狀態。|  
|[CTabCtrl::HitTest](../Topic/CTabCtrl::HitTest.md)|判斷哪個選項，如果有的話，位於指定螢幕位置上的。|  
|[CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md)|在索引標籤控制項插入新的索引標籤。|  
|[CTabCtrl::RemoveImage](../Topic/CTabCtrl::RemoveImage.md)|從的索引標籤控制項的影像清單移除影像。|  
|[CTabCtrl::SetCurFocus](../Topic/CTabCtrl::SetCurFocus.md)|將焦點設定在控制項中指定的索引標籤。|  
|[CTabCtrl::SetCurSel](../Topic/CTabCtrl::SetCurSel.md)|在索引標籤控制項中選取一個選項。|  
|[CTabCtrl::SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md)|設定索引標籤控制項的延伸樣式。|  
|[CTabCtrl::SetImageList](../Topic/CTabCtrl::SetImageList.md)|指定影像清單中的索引標籤控制項。|  
|[CTabCtrl::SetItem](../Topic/CTabCtrl::SetItem.md)|設定部分或所有索引標籤的屬性。|  
|[CTabCtrl::SetItemExtra](../Topic/CTabCtrl::SetItemExtra.md)|將位元組數每個針對索引標籤控制項的應用程式定義的資料保留的索引標籤。|  
|[CTabCtrl::SetItemSize](../Topic/CTabCtrl::SetItemSize.md)|設定項目的寬度和高度。|  
|[CTabCtrl::SetItemState](../Topic/CTabCtrl::SetItemState.md)|設定所指定的索引標籤控制項中項目的狀態。|  
|[CTabCtrl::SetMinTabWidth](../Topic/CTabCtrl::SetMinTabWidth.md)|設定項目的最小寬度在索引標籤控制項。|  
|[CTabCtrl::SetPadding](../Topic/CTabCtrl::SetPadding.md)|在每一索引標籤的圖示和標籤周圍設定空間 \(填補\) 在索引標籤控制項。|  
|[CTabCtrl::SetToolTips](../Topic/CTabCtrl::SetToolTips.md)|指派工具提示控制項的索引標籤控制項。|  
  
## 備註  
 「控制項」是類似於筆記本裡的分隔頁或檔案櫃中的標籤。  藉由使用索引標籤控制項，應用程式可以在視窗或對話方塊的同一個區域定義多個頁面。  每個頁面包含一組資訊或應用程式會顯示一組控制項使用者何時選取此對應的索引標籤。  索引標籤控制項的特殊型別顯示類似於按鈕的索引標籤。  按一下  按鈕應該立即執行命令而不是顯示頁面。  
  
 這個控制項 \(也 `CTabCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用 `CTabCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CTabCtrl](../../mfc/using-ctabctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl Class](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)