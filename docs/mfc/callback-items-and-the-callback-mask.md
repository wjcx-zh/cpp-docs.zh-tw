---
title: "回呼項目和回呼遮罩 | Microsoft Docs"
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
  - "CListCtrl 類別中的回呼項目"
  - "CListCtrl 類別, 回呼項目和回呼遮罩"
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 回呼項目和回呼遮罩
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於其項目中，清單檢視控制項通常會儲存標籤文字、項目圖示的影像清單索引，和一組位元為項目的狀態旗標。  您可以定義個別項目在回呼項目，如果您的應用程式已經儲存特定項目的資訊的話是有用的。  
  
 您定義了某個項目做為回呼項目藉由指定適當的值給 **LV\_ITEM** 結構的 `pszText` 和 `iImage` 成員 \(請參閱 [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)\)。  如果應用程式維護項目或子項目的文字，指定 **LPSTR\_TEXTCALLBACK** 值作為 `pszText` 成員。  如果應用程式記錄檔項目的圖示，為 `iImage` 成員指定 **I\_IMAGECALLBACK** 值。  
  
 除了定義回呼項目之外，您也可以修改控制項的回呼遮罩。  這個遮罩是一組項目狀態應用程式的位元旗標，而不是控制項會儲存目前資料。  回呼遮罩適用於所有控制項的項目，不同於回呼項目指定，套用至特定項目。  預設回呼遮罩為零，表示控制項正在追蹤所有項目的狀態。  若要變更此預設行為，請使用遮罩設定為下列值的任何組合：  
  
-   `LVIS_CUT` 項目被標記為剪貼作業。  
  
-   `LVIS_DROPHILITED` 項目會反白顯示拖放目標。  
  
-   `LVIS_FOCUSED`這個項目有焦點。  
  
-   `LVIS_SELECTED`這個項目已選取。  
  
-   **LVIS\_OVERLAYMASK** 應用程式儲存目前每一個項目的覆疊影像的影像清單索引。  
  
-   **LVIS\_STATEIMAGEMASK** 應用程式儲存目前每一個項目的狀態影像的影像清單索引。  
  
 如需擷取和設定這個遮罩的詳細資訊，請參閱 [CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md) 和 [CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md)。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)