---
title: "在清單控制項中實作工作區域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "清單控制項, 工作區域"
  - "清單控制項中的工作區域"
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在清單控制項中實作工作區域
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，清單控制項排列所有項目標準格線模式。  不過，另一個方法支援，工作區域，將清單項目置於矩形群組。  如需實作工作區域清單控制項的影像，請參閱 \< 使用清單檢視控制項在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  只有在清單控制項在圖示或小圖示模式時，工作區域為可見的。  不過，所有目前工作區中維持這個值表示這個轉換成報表或 List 模式。  
  
 工作區域可用來顯示空白框線 \(左邊，上方和 \(或\) 正確的項目\)，或是造成水平捲軸，會顯示通常並不是一個。  另一種常見的使用方式是建立項目可以移動或置放的多個工作區。  這個方法，您可以建立具有不同的意義在單一檢視的區域。  使用者可以將它們然後分類項目在不同的區域。  這個範例是具有讀取\/寫入檔案的本機和唯讀檔案的另一個本機檔案系統的檢視。  如果檔案項目將唯讀欄位，它會自動變成唯讀。  將檔案從唯讀區域讀寫區域會讓檔案讀取\/寫入。  
  
 `CListCtrl` 為清單控制項的建立和管理工作區域提供數個成員函式。  [GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md) 和 [SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md) 擷取和設定 `CRect` 物件的陣列 \(或 `RECT` 結構\)，儲存您的清單控制項的目前實作的工作區域。  此外， [GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md) 擷取工作區域目前數目您的清單控制項的 \(根據預設，零\)。  
  
## 項目和工作區域  
 當工作區域建立時，在工作區域之間的項目相容的成員上。  同樣地，如果項目，將工作區域，它符合其移動作業範圍的成員。  如果項目不在任何工作區域之間，它會自動符合第一個 \(索引 0\) 工作區域的成員。  如果您要建立項目並將它放置在特定工作區域內，您將需要建立項目並將它與呼叫所需的工作區域移至 [SetItemPosition](../Topic/CListCtrl::SetItemPosition.md)。  下列第二個範例示範這項技術。  
  
 下列範例會在每個工作區域周圍實作四個工作區域 \(`rcWorkAreas`\)，具有 10 個像素邊界的相等的大小，在清單控制項 \(`m_WorkAreaListCtrl`\)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_1.cpp)]  
  
 對 [ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md) 的呼叫是在本機進行取得要求的整個頁面區域的專案中的所有項目。  此估計值再分成四個區域並用一個 5 像素邊界。  
  
 下面的範例會將現有的清單項目指派給每個群組 \(`rcWorkAreas`\) 和重新整理控制項檢視中 \(`m_``WorkAreaListCtrl`\) 完成這個動作。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_2.cpp)]  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)