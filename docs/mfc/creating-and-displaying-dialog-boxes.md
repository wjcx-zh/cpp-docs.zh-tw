---
title: "建立和顯示對話方塊 | Microsoft Docs"
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
  - "MFC 對話方塊, 顯示"
  - "強制回應對話方塊, 建立"
  - "非強制回應對話方塊, 建立"
  - "開啟對話方塊"
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 建立和顯示對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立對話方塊物件是兩個相關作業。  首先，請建構對話方塊物件，然後建立對話方塊視窗。  強制回應和非強制回應對話方塊中所用的處理序不同部分建立並顯示它們。  下表列出強制回應和非強制回應對話方塊如何通常建構及顯示。  
  
### 對話方塊建立  
  
|對話方塊型別|如何建立它|  
|------------|-----------|  
|[Modeless](../mfc/creating-modeless-dialog-boxes.md)|建構 `CDialog`，然後呼叫 **Create** 成員函式。|  
|[強制回應](../mfc/creating-modal-dialog-boxes.md)|建構 `CDialog`，然後呼叫 `DoModal` 成員函式。|  
  
 如果您想的話，您可以建立自己的對話方塊，從[記憶體對話方塊範本](../mfc/using-a-dialog-template-in-memory.md) 的對話方塊，而不是從樣板資源建構。  然而這個進階主題包含：  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)