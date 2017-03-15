---
title: "覆寫標準命令路由 | Microsoft Docs"
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
  - "命令處理, 傳送命令"
  - "命令傳送, 覆寫"
  - "MFC, 命令傳送"
  - "覆寫, 標準命令路由"
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 覆寫標準命令路由
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候，當您必須實作標準架構路由的一些變化時，您可以覆寫它。  這個概念是變更一個或多個類別的路由可以覆寫這些類別的 `OnCmdMsg` 。  如此:  
  
-   在中斷命令傳遞至非預設的物件的類別。  
  
-   在新的非預設的物件或命令目標它可能會透過命令。  
  
 如果您將一些新的物件至路由，其類別必須是命令目標類別。  `OnCmdMsg`在您的覆寫版本，請確定呼叫版本覆寫。  請參閱 `CCmdTarget` 類別在這種類別 \(如 `CView` 和 **CDocument** 的 [OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md) 成員函式在 *MFC 參考* 和版本中提供的原始程式碼中。  
  
## 請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)