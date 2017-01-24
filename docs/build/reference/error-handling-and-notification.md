---
title: "錯誤處理和告知 | Microsoft Docs"
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
  - "錯誤處理, 和告知"
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 錯誤處理和告知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需錯誤處理和告知的詳細資訊，請參閱[瞭解 Helper 函式](http://msdn.microsoft.com/zh-tw/6279c12c-d908-4967-b0b3-cabfc3e91d3d)。  
  
 如需攔截函式的詳細資訊，請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。  
  
 如果您的程式使用延遲載入 DLL，則它必須強行處理錯誤，因為在程式執行時發生的錯誤會導致未處理的例外狀況。  錯誤處理由兩個部分組成：  
  
 透過攔截 \(Hook\) 復原。  
 如果錯誤發生時，程式碼必須恢復或提供替代的程式庫和 \(或\) 常式，如此一來，能夠將一個攔截常式給可以提供或補救這個情形的 Helper 函式。  該攔截常式必須傳回適當的值才能繼續處理 \(HINSTANCE 或 FARPROC\)，或是傳回 0 以表示應擲回例外狀況。  這個攔截常式也應該擲回本身的例外狀況或是攔截範圍外的 **longjmp**。  因而有告知攔截程序以錯誤攔截程序。  
  
 透過例外狀況報告。  
 如果處理錯誤所需的只是放棄程序，只要使用者程式碼可以處理例外狀況就不需要攔截。  
  
 下列主題討論錯誤處理和告知：  
  
-   [告知攔截](../../build/reference/notification-hooks.md)  
  
-   [錯誤攔截](../../build/reference/failure-hooks.md)  
  
-   [例外狀況](../../build/reference/exceptions-c-cpp.md)  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)