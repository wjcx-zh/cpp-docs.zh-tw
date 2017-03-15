---
title: "樹狀目錄控制項目資訊 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 項目資訊"
  - "樹狀目錄控制項, 項目資訊"
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 樹狀目錄控制項目資訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 會擷取項目相關資訊在控制項的成員函式。  [GetItem](../Topic/CTreeCtrl::GetItem.md) 成員函式來擷取部分或所有資料與項目。  這項資料可以包含項目的文字、狀態、影像、計數子項目和應用程式定義的 32 位元資料值。  也可以設定某些或所有資料與項目相關聯的 [SetItem](../Topic/CTreeCtrl::SetItem.md) 函式。  
  
 [GetItemState](../Topic/CTreeCtrl::GetItemState.md)、 [GetItemText](../Topic/CTreeCtrl::GetItemText.md)、 [GetItemData](../Topic/CTreeCtrl::GetItemData.md)和 [GetItemImage](../Topic/CTreeCtrl::GetItemImage.md) 成員函式來擷取項目的個別屬性。  這些函式都具有設定項目的屬性有對應的 Set 函式。  
  
 [GetNextItem](../Topic/CTreeCtrl::GetNextItem.md) 成員函式以取得額外負荷對目前項目的指定關聯性的樹狀目錄控制項項目。  這個函式會擷取項目的父代、下一個或上一個可見項目，第一個子項目，依此類推。  也有周遊樹狀結構的成員函式: [GetRootItem](../Topic/CTreeCtrl::GetRootItem.md)、 [GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md)、 [GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md)、 [GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md)、 [GetChildItem](../Topic/CTreeCtrl::GetChildItem.md)、 [GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md)、 [GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md)、 [GetParentItem](../Topic/CTreeCtrl::GetParentItem.md)、 [GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md)和 [GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md)。  
  
 [GetItemRect](../Topic/CTreeCtrl::GetItemRect.md) 成員函式來擷取樹狀目錄控制項項目的週框。  [GetCount](../Topic/CTreeCtrl::GetCount.md) 和 [GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md) 成員函式來分別擷取項目的計數樹狀控制項和目前是顯示在樹狀目錄控制項視窗中的項目計數，。  您可以確保特定項目藉由呼叫 [EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md) 成員函式是可見的。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)