---
title: "CPrintInfo Structure | Microsoft Docs"
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
  - "CPrintInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintInfo structure"
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrintInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需列印和預覽列印工作儲存資訊。  
  
## 語法  
  
```  
struct CPrintInfo  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPrintInfo::GetFromPage](../Topic/CPrintInfo::GetFromPage.md)|傳回要列印的第一頁的頁碼。|  
|[CPrintInfo::GetMaxPage](../Topic/CPrintInfo::GetMaxPage.md)|傳回文件的最後一頁的頁碼。|  
|[CPrintInfo::GetMinPage](../Topic/CPrintInfo::GetMinPage.md)|傳回文件的第一頁的頁碼。|  
|[CPrintInfo::GetOffsetPage](../Topic/CPrintInfo::GetOffsetPage.md)|傳回在 DocObject 項目的第一頁之前的頁面數目會在合併的 DocObject 列印工作。|  
|[CPrintInfo::GetToPage](../Topic/CPrintInfo::GetToPage.md)|傳回要列印的最後一頁的頁碼。|  
|[CPrintInfo::SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md)|設定這個文件的最後一頁的頁碼。|  
|[CPrintInfo::SetMinPage](../Topic/CPrintInfo::SetMinPage.md)|設定這個文件的第一頁的頁碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPrintInfo::m\_bContinuePrinting](../Topic/CPrintInfo::m_bContinuePrinting.md)|包含表示架構的旗標是否應該繼續列印迴圈。|  
|[CPrintInfo::m\_bDirect](../Topic/CPrintInfo::m_bDirect.md)|包含指出文件是上的旗標直接列印 \(未顯示列印對話方塊\)。|  
|[CPrintInfo::m\_bDocObject](../Topic/CPrintInfo::m_bDocObject.md)|包含表示列印的文件是否的旗標為 DocObject。|  
|[CPrintInfo::m\_bPreview](../Topic/CPrintInfo::m_bPreview.md)|包含指出文件是上的旗標預覽。|  
|[CPrintInfo::m\_dwFlags](../Topic/CPrintInfo::m_dwFlags.md)|指定 DocObject 列印作業。|  
|[CPrintInfo::m\_lpUserData](../Topic/CPrintInfo::m_lpUserData.md)|含有指向使用者自建結構。|  
|[CPrintInfo::m\_nCurPage](../Topic/CPrintInfo::m_nCurPage.md)|識別目前列印的頁面數目。|  
|[CPrintInfo::m\_nJobNumber](../Topic/CPrintInfo::m_nJobNumber.md)|對於目前的列印工作指定作業系統指派的編號施工|  
|[CPrintInfo::m\_nNumPreviewPages](../Topic/CPrintInfo::m_nNumPreviewPages.md)|識別在預覽視窗中顯示的頁面數目，1 或 2。|  
|[CPrintInfo::m\_nOffsetPage](../Topic/CPrintInfo::m_nOffsetPage.md)|在合併的 DocObject 列印工作指定特定的 DocObject 第一頁的位移。|  
|[CPrintInfo::m\_pPD](../Topic/CPrintInfo::m_pPD.md)|含有指向用於列印對話方塊的 `CPrintDialog` 物件。|  
|[CPrintInfo::m\_rectDraw](../Topic/CPrintInfo::m_rectDraw.md)|指定定義目前可用的頁面區域的矩形。|  
|[CPrintInfo::m\_strPageDesc](../Topic/CPrintInfo::m_strPageDesc.md)|包含頁碼顯示格式的字串。|  
  
## 備註  
 `CPrintInfo` 是結構，而且沒有基底類別。  
  
 架構建立 `CPrintInfo` 物件，每次列印或 \[預覽列印\] 命令會選取和終結它，完成此命令時。  
  
 如需`CPrintInfo` 包含整個列印工作的相關資訊，例如要列印的頁面範圍和列印工作的目前狀態，例如列印目前的頁面。  某些資訊相關聯的 [CPrintDialog](../../mfc/reference/cprintdialog-class.md) 物件儲存，這個物件在列印對話方塊包含使用者輸入的值。  
  
 `CPrintInfo` 物件傳入的架構和您的檢視類別之間在列印處理序期間和用來在兩者之間的資訊。  例如，告知架構檢視類別列印的文件中的哪個頁面可以指派值給 `CPrintInfo`的 `m_nCurPage` 成員;檢視類別擷取值並執行指定的頁面的實際列印。  
  
 另一個範例是文件的長度未知的情況，直到列印。  在這種狀況下，結束的檢視  類別的  中的文件，每次頁面要列印。  在這一端會在到達，則檢視類別設定 `CPrintInfo` 的 `m_bContinuePrinting` 成員至 **否**;這個告知架構停止列印迴圈。  
  
 `CView` 函式清單底下「請參閱成員使用`CPrintInfo` 」。如需 MFC 程式庫提供的列印結構的詳細資訊，請參閱 [框架視窗](../../mfc/frame-windows.md) 和 [文件\/檢視架構](../../mfc/document-view-architecture.md) 和文件 [列印](../../mfc/printing.md) 和 [列印:多頁文件](../../mfc/multipage-documents.md)。  
  
## 繼承階層架構  
 `CPrintInfo`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 DIBLOOK](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)   
 [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)   
 [CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)   
 [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)   
 [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)