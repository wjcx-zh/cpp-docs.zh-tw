---
title: "CRectTracker Class | Microsoft Docs"
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
  - "CRectTracker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRectTracker class"
  - "displaying items"
  - "resizing items"
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRectTracker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許項目顯示，移動或調整大小以不同的方式。  
  
## 語法  
  
```  
  
class CRectTracker  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRectTracker::CRectTracker](../Topic/CRectTracker::CRectTracker.md)|建構 `CRectTracker` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRectTracker::AdjustRect](../Topic/CRectTracker::AdjustRect.md)|呼叫，以矩形調整大小。|  
|[CRectTracker::Draw](../Topic/CRectTracker::Draw.md)|呈現矩形。|  
|[CRectTracker::DrawTrackerRect](../Topic/CRectTracker::DrawTrackerRect.md)|呼叫，以區分 `CRectTracker` 物件的框線時。|  
|[CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)|呼叫以取得 `CRectTracker`項目的遮罩的縮放控點。|  
|[CRectTracker::GetTrueRect](../Topic/CRectTracker::GetTrueRect.md)|傳回矩形的寬度和高度，包括調整大小控點。|  
|[CRectTracker::HitTest](../Topic/CRectTracker::HitTest.md)|傳回目前游標位置 `CRectTracker` 與物件產生關聯。|  
|[CRectTracker::NormalizeHit](../Topic/CRectTracker::NormalizeHit.md)|正規化點擊測試程式碼。|  
|[CRectTracker::OnChangedRect](../Topic/CRectTracker::OnChangedRect.md)|呼叫，以矩形調整大小或移動。|  
|[CRectTracker::SetCursor](../Topic/CRectTracker::SetCursor.md)|根據成員在矩形的位置設定游標。|  
|[CRectTracker::Track](../Topic/CRectTracker::Track.md)|允許使用者操作矩形。|  
|[CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md)|提供使用者「需要非群組列」選取範圍。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRectTracker::m\_nHandleSize](../Topic/CRectTracker::m_nHandleSize.md)|判斷大小調整大小控點。|  
|[CRectTracker::m\_nStyle](../Topic/CRectTracker::m_nStyle.md)|TRACKER 的目前樣式。|  
|[CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md)|目前位置 \(以像素為單位\) 矩形。|  
|[CRectTracker::m\_sizeMin](../Topic/CRectTracker::m_sizeMin.md)|決定最小矩形的寬度和高度。|  
  
## 備註  
 `CRectTracker` 不具有基底類別。  
  
 您可以使用一個圖形介面，雖然 `CRectTracker` 類別的設計可讓使用者與 OLE 項目互動時，它的使用並不限於 OLE 啟用應用程式。  可以使用就如同這類的需求。  
  
 `CRectTracker` 邊界可以是實線或虛線。  可寫入項目已規劃的框線或重疊的已規劃的模式表示項目的不同狀態。  您可以將八調整項目的內部或外部框線的控制代碼。  \(如需調整大小控點的說明，請參閱 [GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)\)。最後，在調整大小時， `CRectTracker` 允許您變更項目的方向。  
  
 若要使用 `CRectTracker`，請 `CRectTracker` 建構物件並指定顯示狀態初始化。  您可以使用這個介面提供使用者在 OLE 項目的目前狀態的視覺化回應與 `CRectTracker` 物件。  
  
 如需使用 `CRectTracker`的詳細資訊，請參閱本文 [TRACKER](../../mfc/trackers.md)。  
  
## 繼承階層架構  
 `CRectTracker`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 Tracker](../../top/visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleResizeBar Class](../../mfc/reference/coleresizebar-class.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)