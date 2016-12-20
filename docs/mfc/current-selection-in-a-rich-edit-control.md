---
title: "Rich Edit 控制項中目前的選取範圍 | Microsoft Docs"
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
  - "CRichEditCtrl 類別, 其中目前的選取範圍"
  - "CRichEditCtrls 中目前的選取範圍"
  - "Rich Edit 控制項, 其中目前的選取範圍"
  - "選取範圍, CRichEditCtrl 中目前的"
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控制項中目前的選取範圍
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用者可以選取的 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的文字使用滑鼠或鍵盤，。  目前選取範圍是選取的字元範圍或插入點的位置字元是否未選取。  應用程式可以取得有關目前選取項目的資訊，將目前的選擇，以判斷目前的選取範圍變更時和顯示或隱藏選取範圍反白顯示。  
  
 若要判斷在 Rich Edit 控制項的目前選取範圍，請使用 [GetSel](../Topic/CRichEditCtrl::GetSel.md) 成員函式。  若要設定目前的選取範圍，請使用 [SetSel](../Topic/CRichEditCtrl::SetSel.md) 成員函式。  [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) 結構用來以這些函式指定字元的範圍。  若要擷取目前選取範圍內容的資訊，您可以使用 [GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md) 成員函式。  
  
 根據預設，，則取得和遺失焦點時，的 Rich Edit 控制項顯示和隱藏選取範圍反白顯示。  使用 [HideSelection](../Topic/CRichEditCtrl::HideSelection.md) 成員函式，您可以隨時顯示或隱藏選取範圍反白顯示。  例如，應用程式可能會提供搜尋對話方塊尋找在 Rich Edit 控制項的文字。  應用程式可以選擇符合文字，而不需關閉對話方塊，如果有的話，就必須使用 `HideSelection` 反白顯示選取範圍的情況下。  
  
 若要取得 Rich Edit 控制項中選取的文字，請使用 [GetSelText](../Topic/CRichEditCtrl::GetSelText.md) 成員函式。  文字複製到指定的字元陣列。  您必須確定陣列不夠大保留選取的文字加上結束的 null 字元。  
  
 您可以搜尋在 Rich Edit 控制項的字串使用 [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) 結構搭配此函式指定文字範圍搜尋和字串搜尋的 [FindText](../Topic/CRichEditCtrl::FindText.md) 成員函式。  您也可以指定這個選項與搜尋是否區分大小寫。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)