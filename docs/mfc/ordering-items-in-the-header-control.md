---
title: "排序標題控制項中的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DS_DRAGDROP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DS_DRAGDROP 告知"
  - "GetOrderArray 方法"
  - "標題控制項, 排序項目"
  - "OrderToIndex 方法"
  - "序列"
  - "序列, 標題控制項目"
  - "SetOrderArray 方法"
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 排序標題控制項中的項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦您有 [加入項目至標題控制項](../mfc/adding-items-to-the-header-control.md)，您可以操作或取得有關順序的資訊與下列函式：  
  
-   [CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md) 和 [CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)  
  
     擷取和設定標題項目由左至右的順序。  
  
-   [CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md)。  
  
     擷取特定標頭項目的索引值。  
  
 除了先前的成員函式之外， `HDS_DRAGDROP` 模式允許使用者拖放至標題控制項內的標題項目。  如需詳細資訊，請參閱 [提供拖放支援針對標頭項目](../mfc/providing-drag-and-drop-support-for-header-items.md)。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)