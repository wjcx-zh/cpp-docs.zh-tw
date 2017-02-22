---
title: "使用熱鍵控制項 | Microsoft Docs"
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
  - "CHotKeyCtrl 類別, 使用"
  - "熱鍵控制項"
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用熱鍵控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

熱鍵控制項的一般使用方式會遵循下列模式:  
  
-   建立控制項。  如果控制項在對話方塊樣板指定，建立是自動的，在對話方塊中建立時。\(您應該會包含熱鍵控制項\) 的對話方塊類別中的 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) 成員。或者，您可以使用 [建立](../Topic/CHotKeyCtrl::Create.md) 成員函式來建立控制項做為子視窗的所有視窗。  
  
-   如果您要將控制項的預設值，請呼叫 [SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md) 成員函式。  如果您要禁止某些傳輸狀態，請呼叫 [SetRules](../Topic/CHotKeyCtrl::SetRules.md)。  對於在對話方塊的控制項，好時機可以在對話方塊的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 函式。  
  
-   使用者與控制項互動傳入的快速鍵組合，當熱鍵控制項取得焦點時。  使用者按一下對話方塊上的按鈕莫名其妙就可以表示工作已完成，或啟用。  
  
-   當您的程式告知時使用者選取了一個快速鍵，則應該使用成員函式 [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) 擷取虛擬按鍵和從熱鍵控制項將狀態值。  
  
-   一旦您知道哪些按鍵使用者選取，您可以設定快速鍵使用 [設定熱鍵](../mfc/setting-a-hot-key.md)中所描述的其中一個方法。  
  
-   如果熱鍵控制項在對話方塊中，將自動終結和 `CHotKeyCtrl` 物件。  否則，您必須確保適當地終結控制項和 `CHotKeyCtrl` 物件。  
  
## 請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)