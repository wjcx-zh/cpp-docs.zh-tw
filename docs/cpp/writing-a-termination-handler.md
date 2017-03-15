---
title: "撰寫終止處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "例外狀況處理, 終止處理常式"
  - "例外狀況, 終止"
  - "處理常式"
  - "處理常式, 終止"
  - "結構化例外狀況處理, 終止處理常式"
  - "終止處理常式"
  - "終止處理常式, 撰寫"
  - "try-catch 關鍵字 [C++], 終止處理常式"
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 撰寫終止處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不同於例外狀況處理常式，無論程式碼保護區塊是否正常終止，都一定會執行終止處理常式。  終止處理常式的唯一用途應該是確保資源 \(例如記憶體、控制代碼和檔案\) 適當地關閉，而不管程式碼區段的執行如何完成。  
  
 終止處理常式會使用 try\-finally 陳述式。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [try\-finally 陳述式](../cpp/try-finally-statement.md)  
  
-   [清除資源](../cpp/cleaning-up-resources.md)  
  
-   [進行例外狀況處理時採取動作的時機](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [終止處理常式的限制](../cpp/restrictions-on-termination-handlers.md)  
  
## 請參閱  
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)