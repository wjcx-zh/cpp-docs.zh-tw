---
title: "拖放：實作置放來源 | Microsoft Docs"
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
  - "拖放, 呼叫 DoDragDrop"
  - "拖放, 置放來源"
  - "拖放, 啟始拖曳作業"
  - "OLE 拖放, 呼叫 DoDragDrop"
  - "OLE 拖放, 置放來源"
  - "OLE 拖放, 啟始拖曳作業"
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放：實作置放來源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何取得應用程式提供資料於拖放作業。  
  
 置放來源的基底實作相當簡單。  第一步是判斷要啟動拖曳作業的事件。  建議的使用者介面方針定義發生在點內拖曳作業以選取資料和 `WM_LBUTTONDOWN` 事件的啟動選取的資料。  MFC OLE遵循這些方針，示範 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 。  
  
 如果您的應用程式是容器，且選取的資料是連接或 `COleClientItem`型別內嵌物件，請呼叫其 `DoDragDrop` 成員函式。  否則，請建構 `COleDataSource` 物件，並使用選取項目，然後呼叫資料來源物件的 `DoDragDrop` 成員函式。  如果您的應用程式是伺服器，請使用 `COleServerItem::DoDragDrop`。  如需自訂標準拖放行為的詳細資訊，請參閱本文件的 [拖放:自訂](../mfc/drag-and-drop-customizing.md)。  
  
 如果 `DoDragDrop` 傳回 `DROPEFFECT_MOVE`，請立即刪除原始程式檔的來源資料。  從 `DoDragDrop` 傳回的其他值對置放來源沒有任何作用。  
  
 如需詳細資訊，請參閱：  
  
-   [實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [自訂拖放](../mfc/drag-and-drop-customizing.md)  
  
-   [建立和終結的 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [管理OLE資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 請參閱  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)   
 [CView::OnDragLeave](../Topic/CView::OnDragLeave.md)