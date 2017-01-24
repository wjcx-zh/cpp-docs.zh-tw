---
title: "建立強制回應對話方塊 | Microsoft Docs"
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
  - "MFC 對話方塊, 建立"
  - "MFC 對話方塊, 強制回應"
  - "強制回應對話方塊, 建立"
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立強制回應對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要建立強制回應對話方塊，請呼叫以 [CDialog](../mfc/reference/cdialog-class.md)宣告的兩個公用建構函式之一。  接著，呼叫對話方塊物件的 [DoModal](../Topic/CDialog::DoModal.md) 成員函式來顯示對話方塊和管理與其互動，直到使用者選擇確定或取消。  由 `DoModal` 的這個管理會讓對話方塊強制回應。  對於強制回應對話方塊， `DoModal` 載入對話方塊資源。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)