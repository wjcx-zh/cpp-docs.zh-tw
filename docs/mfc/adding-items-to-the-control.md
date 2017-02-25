---
title: "將項目加入至控制項 | Microsoft Docs"
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
  - "CListCtrl 類別, 加入項目"
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 將項目加入至控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要在清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 的加入項目，請根據您有的資訊呼叫 [InsertItem](../Topic/CListCtrl::InsertItem.md) 數個版本之一的成員函式。  一個版本會接受您準備的 [LV\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) 結構。  由於 `LV_ITEM` 結構中的成員，您有更大的控制權清單控制項項目的屬性。  
  
 兩個重要成員 \(如需報告檢視\) 的 `LV_ITEM` 結構之 `iItem` 和 `iSubItem` 成員。  `iItem`成員是結構參考項目的以零起始的索引，而 `iSubItem` 成員是子項目的以一起始的索引或是如果結構包含項目的資訊，則是以零為始。  這兩個成員您判斷，每個項目，的子項目資訊的型別和值，會顯示清單控制項在報表檢視中。  如需詳細資訊，請參閱 [CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md)。  
  
 其他成員指定項目的文字、圖示、狀態和項目資料。「項目資料」是應用程式定義的值與清單檢視項目。  如需`LV_ITEM` 結構的詳細資訊，請參閱[CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)。  
  
 `InsertItem` 其他版本使用一個或多個不同值，等於 `LV_ITEM` 結構的成員對應，可讓您使用您要支援的那些成員。  通常，清單控制項處理清單項目的儲存體，不過，您可以在應用程式中儲存某些這項資訊，則會使用「回呼項目」。如需詳細資訊，請參閱 [回呼項目和回呼遮罩](../mfc/callback-items-and-the-callback-mask.md) 和 [回呼項目和在 \<token\>winSDK\<\/token\>中的回呼遮罩](http://msdn.microsoft.com/library/windows/desktop/bb774736) 。  
  
 如需詳細資訊，請參閱 [加入清單檢視項目和子項目](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)