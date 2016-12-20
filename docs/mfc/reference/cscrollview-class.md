---
title: "CScrollView Class | Microsoft Docs"
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
  - "CScrollView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CScrollView class"
  - "scrolling views"
  - "檢視, 捲動"
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CScrollView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CView](../../mfc/reference/cview-class.md) 提供捲動功能。  
  
## 語法  
  
```  
class CScrollView : public CView  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CScrollView::CScrollView](../Topic/CScrollView::CScrollView.md)|建構 `CScrollView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CScrollView::CheckScrollBars](../Topic/CScrollView::CheckScrollBars.md)|指示捲動檢視是否具有水平和垂直捲軸。|  
|[CScrollView::FillOutsideRect](../Topic/CScrollView::FillOutsideRect.md)|填入一個檢視的區域會在移動區域之外。|  
|[CScrollView::GetDeviceScrollPosition](../Topic/CScrollView::GetDeviceScrollPosition.md)|取得單位的目前捲動位置。|  
|[CScrollView::GetDeviceScrollSizes](../Topic/CScrollView::GetDeviceScrollSizes.md)|取得目前對應模式、總計大小和這個檢視可捲動的線條和頁面大小。  大小 \(以位元組為單位。|  
|[CScrollView::GetScrollPosition](../Topic/CScrollView::GetScrollPosition.md)|取得以邏輯單位的目前捲動位置。|  
|[CScrollView::GetTotalSize](../Topic/CScrollView::GetTotalSize.md)|取得捲動檢視的總大小 \(以邏輯單位計算\)。|  
|[CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)|構成此檢視的大小會要求其架構的大小。|  
|[CScrollView::ScrollToPosition](../Topic/CScrollView::ScrollToPosition.md)|會將檢視捲動至指定的點，指定以邏輯單位。|  
|[CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md)|將檢視捲動到縮放調整模式。|  
|[CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md)|設定捲動檢視的對應方式，總大小，，和水平及垂直捲動總數。|  
  
## 備註  
 您可以處理標準捲動 `CView` 從衍生的任何類別中可以覆寫訊息對應的 [OnHScroll](../Topic/CWnd::OnHScroll.md) 和 [OnVScroll](../Topic/CWnd::OnVScroll.md) 成員函式。  但是， `CScrollView` 將下列功能加入至其 `CView` 功能:  
  
-   它所管理的視窗和檢視區大小和對應模式。  
  
-   它會自動移動捲軸以回應訊息。  
  
-   它會自動移動回應從鍵盤、非捲動滑鼠滾輪或 IntelliMouse 的訊息。  
  
 自動捲動回應從鍵盤訊息，將 WM\_KEYDOWN 訊息和來測試 VK\_DOWN、VK\_PREV 和呼叫 [SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 您可以透過覆寫訊息對應的 [OnMouseWheel](../Topic/CWnd::OnMouseWheel.md) 和 [OnRegisteredMouseWheel](../Topic/CWnd::OnRegisteredMouseWheel.md) 成員處理滑鼠滾輪捲動函式。  當它們是 `CScrollView`，這些成員函式支援 [WM\_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)的建議的行為，轉動滾輪訊息。  
  
 若要利用自動捲動，從 `CScrollView` 衍生您的檢視類別而不是從 `CView`。  在  檢視時，會先建立，如果您想要表示根據紙張大小之可捲動檢視的大小，請呼叫 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 或 [CView::OnUpdate](../Topic/CView::OnUpdate.md)您的覆寫的 `SetScrollSizes` 成員函式。  \(您必須撰寫自己的程式碼會查詢的紙張大小。  如需範例，請參閱 [Scribble 範例](../../top/visual-cpp-samples.md)\)。  
  
 為 `SetScrollSizes` 成員函式的呼叫所設定的對應方式檢視、捲動檢視的總維度和幅度水平和垂直捲動。  任何大小以邏輯單位。  這個檢視的邏輯大小會在文件中儲存的資料通常計算，不過，您可以在其他情況下要指定固定大小。  使用兩種方法的範例，請參閱 [CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md)。  
  
 您在垂直邏輯單位指定數量水平捲動和。  根據預設，在中，如果使用者按一下捲軸的捲動方塊，捲動 `CScrollView` 「Page」。如果使用者按一下捲動箭號的任何一項捲軸的結尾， `CScrollView` 上移一行「」。根據預設，網頁為 1\/10 這個檢視的總大小，線條是 1\/10 頁面大小。  傳入 `SetScrollSizes` 成員函式的自訂大小覆寫這些預設值。  例如，您可以將水平大小為總大小和垂直的大小的寬度的某個分數為一行的高度 \(以目前的字型。  
  
 而非捲動， `CScrollView` 可以自動縮放這個檢視至目前視窗的大小。  在此模式下，這個檢視沒有捲軸，而邏輯檢視自動縮放或壓縮以完全適合視窗的工作區。  若要使用這個縮放調整功能，請呼叫 [CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md)。  \(請 `SetScaleToFitSize` 呼叫或， `SetScrollSizes`，但非兩者\)  
  
 在衍生的檢視類別的 `OnDraw` 呼叫成員函式之前， `CScrollView` 會傳遞至 `OnDraw`的 `CPaintDC` 裝置內容物件自動調整檢視區還原點。  
  
 根據捲動視窗要調整檢視區還原點， `CScrollView` 覆寫 [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)。  這項調整為 `CScrollView` 傳遞至 `OnDraw`的 `CPaintDC` 裝置內容是 Automatic，不過，您必須呼叫 **CScrollView::OnPrepareDC** 您使用的任何其他裝置內容 \(例如， `CClientDC`。  您可以覆寫 **CScrollView::OnPrepareDC** 設定畫筆、背景色彩和其他繪圖屬性，不過，呼叫基底類別 \(Base Class\) 進行縮放。  
  
 如下列範例所示，捲軸的三個位置的外觀，相對於檢視:  
  
-   使用 **WS\_HSCROLL** 和 **WS\_VSCROLL**[視窗樣式](../../mfc/reference/window-styles.md)，標準視窗樣式捲軸可識別檢視設定。  
  
-   架構會轉送 `WM_HSCROLL` 和 `WM_VSCROLL` 訊息從框架視窗加入目前作用中檢視的情況下，捲軸控制項可以加入至包含這個檢視的框架。  
  
-   此架構也轉送來自 `CSplitterWnd` 分隔器控制項的捲動訊息至目前使用中的分割窗格檢視 \(\)。  當位於與共用捲軸的 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) ， `CScrollView` 物件將會使用共用的部分 \(而不是建立它。  
  
 如需使用 `CScrollView`的資訊，請參閱 [文件\/檢視架構](../../mfc/document-view-architecture.md) 和 [衍生的檢視類別適用於 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 DIBLOOK](../../top/visual-cpp-samples.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)