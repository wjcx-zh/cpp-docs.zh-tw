---
title: "檢查記憶體覆寫 | Microsoft Docs"
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
  - "記憶體, 覆寫"
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 檢查記憶體覆寫
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果在呼叫堆積操作函式時發生存取違規，則可能您的程式已損毀堆積。  這種情況常見的徵兆是：  
  
```  
Access Violation in _searchseg  
```  
  
 在偵錯版及發行的組建 \(只限 Windows NT\) 中都可使用 [\_heapchk](../../c-runtime-library/reference/heapchk.md) 函式，用來驗證執行階段程式庫堆積的完整性。  您可以與使用 `AfxCheckMemory` 函式相當類似的方法使用 `_heapchk` 來隔離堆積覆寫，例如：  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 如果這個函式失敗，您必須隔離堆積損毀的地方。  
  
## 請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)