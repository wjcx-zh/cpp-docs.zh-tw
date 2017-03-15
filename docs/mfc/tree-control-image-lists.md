---
title: "樹狀目錄控制項影像清單 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 類別, 影像清單"
  - "影像 [C++], 樹狀目錄控制項中的清單"
  - "樹狀目錄控制項, 影像清單"
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 樹狀目錄控制項影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的每個項目都可以有一組位元對應影像相關聯的。  影像在項目標籤的左邊。  影像會顯示，當項目被選取時，，和其他顯示項目時，沒有選取。  例如，項目可能會顯示一個開啟的資料夾，當選取和已關閉的資料夾時，如果沒有被選取時。  
  
 若要使用項目影像，您必須藉由建構 [CImageList](../mfc/reference/cimagelist-class.md) 物件並使用 [CImageList::Create](../Topic/CImageList::Create.md) 函式建立關聯的影像清單建立影像清單。  使用 [SetImageList](../Topic/CTreeCtrl::SetImageList.md) 成員函式，然後將想要點陣圖到清單，並使清單與樹狀目錄控制項。  根據預設，所有項目顯示在影像清單中的第一個影像的選取或 nonselected 狀態。  您可以指定已選取和 nonselected 影像的索引變更特定項目的預設行為，當將項目加入至樹狀目錄控制項使用 [InsertItem](../Topic/CTreeCtrl::InsertItem.md) 成員函式。  使用 [SetItemImage](../Topic/CTreeCtrl::SetItemImage.md) 成員函式，您可以在加入項目後變更索引。  
  
 樹狀目錄控制項的影像清單也可以包含覆疊影像，在項目影像會重疊。  在位元 8 到 11 的非零值樹狀控制項目狀態指定覆疊影像的以一起始的索引 \(0 表示沒有覆疊影像\)。  由於，以一起始的索引使用 4 位元，覆疊影像必須是在影像清單中的最後 15 個影像中。  如需樹狀控制項目狀態的詳細資訊，請參閱本主題稍早的 [樹狀目錄控制項項目狀態概觀](../mfc/tree-control-item-states-overview.md) 。  
  
 如果狀態影像清單中指定，樹狀目錄控制項中各個項目的圖示左邊為其保留空間的狀態影像。  應用程式可以使用狀態影像，例如已選取或已清除核取方塊，表示應用程式定義的項目狀態。  在位元 12 到 15 的非零的值指定狀態影像的以一起始的索引 \(0 表示沒有狀態影像\)。  
  
 藉由指定而非影像索引的 **I\_IMAGECALLBACK** 值，您可以延遲指定選取的或 nonselected 影像，直到項目會重新繪製。  **I\_IMAGECALLBACK** 指示樹狀控制項傳送 [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) 通知訊息查詢索引的應用程式。  
  
 [GetImageList](../Topic/CTreeCtrl::GetImageList.md) 成員函式來擷取樹狀目錄控制項的影像清單的控制代碼。  如果您需要加入多個影像加入至清單，這個函式會很有用。  如需影像清單的詳細資訊，請參閱 [使用 CImageList](../mfc/using-cimagelist.md)、 [CImageList](../mfc/reference/cimagelist-class.md) 《 *MFC*參考》中的 [影像清單](http://msdn.microsoft.com/library/windows/desktop/bb761389) 和 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)