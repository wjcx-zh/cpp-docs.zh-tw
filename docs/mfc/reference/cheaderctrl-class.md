---
title: "CHeaderCtrl Class | Microsoft Docs"
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
  - "CHeaderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeaderCtrl class"
  - "header controls, CHeaderCtrl class"
  - "Windows common controls [C++], CHeaderCtrl"
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
caps.latest.revision: 24
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeaderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用標題控制項的功能。  
  
## 語法  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHeaderCtrl::CHeaderCtrl](../Topic/CHeaderCtrl::CHeaderCtrl.md)|建構 `CHeaderCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHeaderCtrl::ClearAllFilters](../Topic/CHeaderCtrl::ClearAllFilters.md)|清除所有標題控制項的篩選條件。|  
|[CHeaderCtrl::ClearFilter](../Topic/CHeaderCtrl::ClearFilter.md)|清除標題控制項的篩選條件。|  
|[CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)|建立標題控制項並將其附加至 `CHeaderCtrl` 物件。|  
|[CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md)|建立項目的影像的透明版本在標題控制項內。|  
|[CHeaderCtrl::CreateEx](../Topic/CHeaderCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的標題控制項並將其附加至 `CListCtrl` 物件。|  
|[CHeaderCtrl::DeleteItem](../Topic/CHeaderCtrl::DeleteItem.md)|刪除標題控制項中的項目。|  
|[CHeaderCtrl::DrawItem](../Topic/CHeaderCtrl::DrawItem.md)|繪製標題控制項的指定項目。|  
|[CHeaderCtrl::EditFilter](../Topic/CHeaderCtrl::EditFilter.md)|編輯標題控制項的指定之篩選條件的開始。|  
|[CHeaderCtrl::GetBitmapMargin](../Topic/CHeaderCtrl::GetBitmapMargin.md)|擷取點陣圖的框線寬度在標題控制項的。|  
|[CHeaderCtrl::GetFocusedItem](../Topic/CHeaderCtrl::GetFocusedItem.md)|取得項目的識別項在具有焦點的目前控制項的標題。|  
|[CHeaderCtrl::GetImageList](../Topic/CHeaderCtrl::GetImageList.md)|擷取用於繪製標題項目使用的影像清單的控制代碼在標題控制項。|  
|[CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md)|擷取關於項目的資訊在標題控制項。|  
|[CHeaderCtrl::GetItemCount](../Topic/CHeaderCtrl::GetItemCount.md)|擷取項目計數\] 標題的控制項。|  
|[CHeaderCtrl::GetItemDropDownRect](../Topic/CHeaderCtrl::GetItemDropDownRect.md)|取得指定的下拉按鈕的週框 \(Bounding Rectangle\) 資訊在標題控制項。|  
|[CHeaderCtrl::GetItemRect](../Topic/CHeaderCtrl::GetItemRect.md)|擷取指定之項目的週框 \(Bounding Rectangle\) 標題控制項。|  
|[CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md)|擷取項目由左至右的順序在標題控制項的。|  
|[CHeaderCtrl::GetOverflowRect](../Topic/CHeaderCtrl::GetOverflowRect.md)|取得溢位按鈕的週框 \(Bounding Rectangle\) 目前標題控制項的。|  
|[CHeaderCtrl::HitTest](../Topic/CHeaderCtrl::HitTest.md)|判斷標題項目，如果有的話，位於指定的點。|  
|[CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md)|將新的項目插入至標題控制項。|  
|[CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md)|擷取標題控制項的大小和位置是在指定的矩形內。|  
|[CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md)|擷取根據其在標題控制項順序之項目的索引值。|  
|[CHeaderCtrl::SetBitmapMargin](../Topic/CHeaderCtrl::SetBitmapMargin.md)|將點陣圖的框線寬度在標題控制項的。|  
|[CHeaderCtrl::SetFilterChangeTimeout](../Topic/CHeaderCtrl::SetFilterChangeTimeout.md)|設定在變更篩選條件屬性和 `HDN_FILTERCHANGE` 告知的回傳發生的時間之間的逾時間隔。|  
|[CHeaderCtrl::SetFocusedItem](../Topic/CHeaderCtrl::SetFocusedItem.md)|將焦點設定在目前標題控制項的指定標題項目。|  
|[CHeaderCtrl::SetHotDivider](../Topic/CHeaderCtrl::SetHotDivider.md)|變更標題項目之間的分割線表示標頭項目中手動拖放。|  
|[CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md)|指派影像清單與標題控制項。|  
|[CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md)|設定指定之項目的屬性在控制項的標題。|  
|[CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)|設定項目由左至右的順序在標題控制項的。|  
  
## 備註  
 標題控制項是一組文字或數值的資料行上通常放置的視窗。  它包含每一個資料行的標題，因此，它可以分割成部分。  使用者可以拖曳分隔部分設定每個資料行的寬度的分割線。  如需標題控制項的說明，請參閱 [標題控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  
  
 這個控制項 \(也 `CHeaderCtrl` 類別\) 給在 Windows 95 和 Windows NT \/98 版本 3.51 和之後的程式才能使用。  
  
 對於 Windows 95\/Internet Explorer 4.0 通用控制項加入的功能包括:  
  
-   標題項目自訂排序。  
  
-   標題項目拖放功能，重新排列的標題項目。  然後，當您建立 `CHeaderCtrl` 物件時，請使用 `HDS_DRAGDROP` 樣式。  
  
-   標題資料行文字通常可檢視資料行調整大小期間。  然後，當您建立 `CHeaderCtrl` 物件時，請使用 `HDS_FULLDRAG` 樣式。  
  
-   標頭的熱追蹤，反白顯示標題項目，當指標停留在其上方。  然後，當您建立 `CHeaderCtrl` 物件時，請使用 `HDS_HOTTRACK` 樣式。  
  
-   影像清單支援。  標題項目可以包含在 `CImageList` 物件或文字儲存的影像。  
  
 如需使用 `CHeaderCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## 需求  
 **標題:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)