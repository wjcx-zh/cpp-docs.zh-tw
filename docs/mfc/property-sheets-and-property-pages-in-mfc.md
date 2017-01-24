---
title: "MFC 中的屬性工作表和屬性頁 | Microsoft Docs"
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
  - "控制項 [MFC], 屬性工作表"
  - "屬性頁, MFC"
  - "屬性工作表, MFC"
  - "索引標籤對話方塊"
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的屬性工作表和屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性工作表，亦稱為選項對話方塊中，為對話方塊包含屬性頁。  每個屬性頁根據對話方塊樣板資源並包含控制項。  它是置於與一個索引標籤頁的最上方。  這個選項將網頁命名為表示其用途。  使用者按一下屬性工作表中的索引標籤選取一組控制項。  
  
 使用頁面群組在屬性工作表上的控制項型別有意義的集合。  包含屬性工作表通常具有自己的幾個控制項。  這些適用於所有頁面。  
  
 屬性工作表以類別為 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)。  屬性頁根據 [CPropertyPage](../mfc/reference/cpropertypage-class.md)類別。  
  
 屬性工作表是通常用來修改一些外部物件屬性的一種特殊的對話方塊，例如在檢視中目前的選取範圍。  屬性工作表中有三個主要元件:包含的對話方塊、一個或多個屬性頁顯示一個和選項在使用者按一下以選取該網頁的每個頁面頂端。  屬性工作表為您有設定或選項數個相似的群組變更的情況下很有用。  屬性工作表群組資訊以容易了解的方式。  
  
> [!NOTE]
>  使用 `CPropertySheet::DoModal`時，當您嘗試顯示屬性工作表，系統可能產生第一個可能發生的例外狀況。  發生這個例外狀況，因為系統嘗試變更物件的 [視窗樣式](../mfc/reference/window-styles.md) ，在建立物件之前。  如需這個例外狀況的詳細資訊，以及如何使用它或處理，請參閱 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md)。  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)