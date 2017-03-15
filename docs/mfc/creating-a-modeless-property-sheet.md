---
title: "建立非強制回應屬性工作表 | Microsoft Docs"
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
  - "Create 方法 [C++], 屬性工作表"
  - "非強制回應屬性工作表"
  - "屬性工作表, 非強制回應"
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立非強制回應屬性工作表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，您建立的屬性工作表會強制回應。  當使用強制回應屬性工作表時，使用者必須在使用應用程式的其他部分之前關閉屬性工作表。  本文說明您可以用來建立非強制回應屬性工作表允許使用者保持屬性工作表開啟時，應用程式的其他部分的方法。  
  
 若要顯示屬性工作表為非強制回應對話方塊而非強制回應對話方塊，請呼叫 [CPropertySheet::Create](../Topic/CPropertySheet::Create.md) 取代 [DoModal](../Topic/CPropertySheet::DoModal.md)。  您也必須實作一些額外的工作支援非強制回應的屬性工作表。  
  
 其中一個其他工作是在修改的屬性工作表和外部物件之間交換資料屬性工作表時是開啟的。  這通常是工作與標準非強制回應對話方塊的。  中的這個工作實作通訊通道屬性設定套用至的非強制回應的屬性工作表和外部物件之間。  如果您從非強制回應的屬性工作表中， [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 是從衍生類別的這個實作會比較容易。  本文假設您的話\)。  
  
 通訊的方法在非強制回應的屬性工作表和外部物件 \(例如在檢視中目前選取範圍之間，\) 將定義從屬性工作表的指標到外部物件。  定義函式呼叫 \(類似 `SetMyExternalObject`\) 在 `CPropertySheet`\-變更指標的衍生類別，當焦點從外部物件而變更。  `SetMyExternalObject` 函式需要重設每個屬性頁的設定可以反映最近選取的外部物件。  若要完成這項作業， `SetMyExternalObject` 函式必須能夠存取屬於 `CPropertySheet` 類別中的 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 物件。  
  
 最方便的方式提供對屬性工作表內的屬性頁將內嵌 `CPropertyPage` 物件在 `CPropertySheet`衍生物件。  內嵌的 `CPropertyPage` 中 `CPropertySheet`物件衍生物件與強制回應對話方塊的一般設計不同，屬性工作表擁有者建立 `CPropertyPage` 物件並將其傳遞至屬性工作表透過 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)。  
  
 會決定何時許多使用者介面以選取要套用非強制回應的屬性工作表的設定至外部物件。  替代方式是將目前屬性頁上的設定，每當使用者變更任何值。  另一個替代方式是提供應用程式按鈕，讓使用者在執行前累積在屬性頁中的變更至外部物件。  如需方式處理新應用程式的詳細資訊，請參閱本文件的 [處理應用程式按鈕。](../mfc/handling-the-apply-button.md)。  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)   
 [交換資料](../mfc/exchanging-data.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)