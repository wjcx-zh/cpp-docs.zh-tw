---
title: "訊息 | Microsoft Docs"
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
  - "訊息"
  - "訊息, MFC"
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在類別為 `CWinApp` 的 **Run** 成員函式中的訊息迴圈擷取各種事件產生的訊息。  例如，當使用者按一下滑鼠時， Windows 會傳送數個滑鼠相關資訊，例如 `WM_LBUTTONDOWN` 當按下滑鼠左鍵和 `WM_LBUTTONUP` 當放開滑鼠左鍵。  應用程式訊息迴圈架構的實作分派訊息到適當的視窗。  
  
 訊息重要性分類在 [訊息的類別](../mfc/message-categories.md)中說明。  
  
## 請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)