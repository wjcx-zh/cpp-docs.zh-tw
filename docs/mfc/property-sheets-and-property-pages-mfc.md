---
title: "屬性工作表和屬性頁 (MFC) | Microsoft Docs"
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
  - "CPropertyPage 類別, 屬性工作表和頁面"
  - "CPropertySheet 類別, 屬性工作表和頁面"
  - "MFC 對話方塊, 索引標籤"
  - "屬性頁, 屬性工作表"
  - "屬性工作表, 屬性頁"
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 屬性工作表和屬性頁 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC [對話方塊](../mfc/dialog-boxes.md) 可能採用「選項對話方塊的外觀會結合屬性工作表的屬性頁。  呼叫一個屬性工作表」在 MFC 中，這個對話方塊，類似於 Microsoft Word， Excel 的許多對話方塊，因此， Visual C\+\+，可能包含堆疊定位的工作表，很像堆疊從前面看見資料夾支援或重疊的 Windows 群組。  在前面選項的控制項都是可見的;只有已標記的選項會在之後的選項。  屬性工作表為處理相當工整落在多個群組大量的屬性或設定特別有用。  通常，一個屬性工作表可以取代幾個對話方塊可簡化使用者介面。  
  
 根據 MFC 4.0 版，屬性工作表和屬性頁實作會使用 Windows 95 和 Windows NT 3.51 \(含\) 以後版本的通用控制項。  
  
 屬性工作表實作使用 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 和 [CPropertyPage](../mfc/reference/cpropertypage-class.md) \(說明 *MFC*參考\)。  `CPropertySheet` 會定義整個對話方塊，可以包含以 `CPropertyPage`」的多頁。  
  
 如需建立和使用屬性工作表一起使用的詳細資訊，請參閱 [屬性工作表](../mfc/property-sheets-mfc.md)主題。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [MFC 中的屬性工作表和屬性頁](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [交換資料](../mfc/exchanging-data.md)   
 [建立非強制回應屬性工作表](../mfc/creating-a-modeless-property-sheet.md)   
 [處理套用按鈕](../mfc/handling-the-apply-button.md)