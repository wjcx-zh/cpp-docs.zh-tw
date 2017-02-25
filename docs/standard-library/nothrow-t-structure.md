---
title: "nothrow_t 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "nothrow_t"
  - "std.nothrow_t"
  - "std::nothrow_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nothrow_t 類別"
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# nothrow_t 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

而不會擲回例外狀況，結構用來，當 new 運算子的函式參數指示函式應該傳回 null 指標報告配置失敗。  
  
## 語法  
  
```  
struct std::nothrow_t {};  
```  
  
## 備註  
 結構說明編譯器選取建構函式的正確版本。  [nothrow](../Topic/nothrow%20\(%3Cnew%3E\).md) 是 `std::nothrow_t`型別物件的同義字。  
  
## 範例  
 請參閱 [new 運算子](../Topic/operator%20new%20\(%3Cnew%3E\).md) 和 [new 運算子 &#91;](../Topic/operator%20new\(%3Cnew%3E\).md) 以 `std::nothrow_t` 如何為例做為函式參數。  
  
## 需求  
 新 \<的**Header:** \>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)