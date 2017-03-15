---
title: "標題控制項中的標題項目 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 其中的標題項目"
  - "控制項 [MFC], 標題"
  - "標題控制項, 其中的標題項目"
  - "標題控制項中的標題項目"
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 標題控制項中的標題項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您有對組成標題控制項的標頭項目的外觀和行為的大量控制權 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\)。  每個標題項目可以有字串、點陣圖影像、從一個關聯的影像清單的影像或與他相關的應用程式定義的 32 位元值。  字串、點陣圖或影像在標頭項目中顯示。  
  
 藉由呼叫 [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md) 建立或修改現有的項目，以及 [CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md) ，加上 [CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md)呼叫，您可以自訂新項目外觀和內容。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [自訂標題項目外觀](../mfc/customizing-the-header-item-s-appearance.md)  
  
-   [排序標題控制項中的項目](../mfc/ordering-items-in-the-header-control.md)  
  
-   [為標題項目提供拖放支援](../mfc/providing-drag-and-drop-support-for-header-items.md)  
  
-   [搭配使用影像清單與標題控制項](../mfc/using-image-lists-with-header-controls.md)  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)