---
title: "拖放矩形和追蹤器 | Microsoft Docs"
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
  - "CRectTracker 類別, 實作追蹤器"
  - "OLE 物件, 選取"
  - "拖放矩形"
  - "追蹤器"
  - "WM_LBUTTONDOWN"
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放矩形和追蹤器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其他功能提供 Tracker 是「橡膠群組列」選取範圍，讓使用者可以透過拖曳縮放矩形選取多個 OLE 項目在要選取的項目附近。  當使用者放開滑鼠左鍵時，在使用者選取的區域中已選取項目可以由使用者操作。  例如，使用者可能會將選取範圍拖曳到另一個容器應用程式。  
  
 實作這項功能需要在應用程式的 `WM_LBUTTONDOWN` 處理常式函式的某個其他程式碼。  
  
 下列程式碼範例實作橡膠群組列選取範圍和其他功能。  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/CPP/rubber-banding-and-trackers_1.cpp)]  
  
 在橡皮行技術時，如果您要讓這個追蹤的繪製方向，您應該呼叫第三個參數集的 [CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md) 到 **TRUE**。  請記得允許還原方向有時候會造成 [CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md) 成為物件的。  您可以對 [CRect::NormalizeRect](../Topic/CRect::NormalizeRect.md)的呼叫修正。  
  
 如需詳細資訊，請參閱 [容器用戶端項目](../mfc/containers-client-items.md) 和 [自訂拖放。](../mfc/drag-and-drop-customizing.md)。  
  
## 請參閱  
 [追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)