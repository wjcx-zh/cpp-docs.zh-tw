---
title: "樹狀目錄控制項標籤編輯 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 編輯標籤"
  - "編輯樹狀目錄控制項標籤"
  - "CTreeCtrl 類別中的標籤編輯"
  - "樹狀目錄控制項, 標籤編輯"
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項標籤編輯
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用者可以直接編輯有 **TVS\_EDITLABELS** 樣式的樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)的項目標籤。  透過按一下具有焦點項目的標籤讓使用者開始編輯功能。  使用 [EditLabel](../Topic/CTreeCtrl::EditLabel.md) 成員函式以使應用程式開始編輯。  當它在開始編輯和被取消或完成時，樹狀目錄控制項會傳送通知。  如果可以，當編輯完成時，您必須負責更新項目的標籤。  
  
 在標籤在開始編輯時，樹狀目錄控制項傳送 [TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) 通知訊息。  藉由處理這個通知，您可以允許編輯某些標籤並防止編輯其他。  傳回 0 允許編輯，傳回非零值防止編輯。  
  
 在標籤編輯遭到取消或完成時，樹狀目錄控制項傳送 [TVN\_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) 通知訊息。  `lParam` 參數為 [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) 結構的位址。  **item** 成員是識別項目並包含編輯文字的 [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) 結構。  如果在驗證編輯字串後為可行，則您要負責更新項目的標籤。  如果已經取消編輯，則 `TV_ITEM` **pszText** 的成員是 0。  
  
 在標籤編輯期間，通常是為了回應 [TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) 通知訊息，您可以使用[GetEditControl](../Topic/CTreeCtrl::GetEditControl.md) 成員函式以得到編輯控制項的指標。  您可以呼叫 Edit 控制項的 [SetLimitText](../Topic/CEdit::SetLimitText.md) 成員函式限制使用者能夠輸入或子類別攔截並捨棄無效字元的編輯控制項中的文字數。  不過，請注意，編輯控制項**TVN\_BEGINLABELEDIT** 只會在傳送*之後* 顯示。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)