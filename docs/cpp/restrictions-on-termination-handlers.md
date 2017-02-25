---
title: "終止處理常式的限制 | Microsoft Docs"
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
  - "限制, 終止處理常式"
  - "終止處理常式, 限制"
  - "try-catch 關鍵字 [C++], 終止處理常式"
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 終止處理常式的限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您無法使用 `goto` 陳述式跳至 `__try` 陳述式區塊或 `__finally` 陳述式區塊內   您必須改為透過一般控制流程進入陳述式區塊。\(不過，您可以跳出 `__try` 陳述式區塊\)。您也無法在 `__finally` 區塊內將例外狀況處理常式或終止處理常式設為巢狀。  
  
 此外，終止處理常式中允許的某些類型程式碼會產生可疑的結果，因此使用這類程式碼時應特別小心 \(如果一定要的話\)。  其中一個就是會跳出 `__finally` 陳述式區塊的 `goto` 陳述式。  如果區塊在正常終止的過程中執行，則不會發生異常狀況。  但是，如果系統回溯堆疊，則該回溯會停止，而且目前函式會取得控制項，就如同從未發生異常終止一般。  
  
 `__finally` 陳述式區塊內的 `return` 陳述式大致上會呈現相同的情況。  控制項會返回包含終止處理常式之函式的立即呼叫者。  如果系統回溯堆疊，這個處理序就會停止，而且程式會繼續執行，就如同從未引發例外狀況一般。  
  
## 請參閱  
 [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)