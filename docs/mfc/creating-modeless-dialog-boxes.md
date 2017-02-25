---
title: "建立非強制回應對話方塊 | Microsoft Docs"
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
  - "MFC 對話方塊, 建立"
  - "MFC 對話方塊, 非強制回應"
  - "非強制回應對話方塊, 建立"
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 建立非強制回應對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於非強制回應對話方塊，您必須提供可在您的對話方塊類別的公用建構函式。  若要建立非強制回應對話方塊，請呼叫自己的公用建構函式接著呼叫對話方塊物件的 [建立](../Topic/CDialog::Create.md) 成員函式載入對話方塊資源。  在建構函式呼叫的期間或之後，您可以呼叫 **Create** 。  如果對話方塊資源有 **WS\_VISIBLE**屬性，則對話方塊會隨即出現。  否則，您必須呼叫它的 [ShowWindow](../Topic/CWnd::ShowWindow.md) 成員函式。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)