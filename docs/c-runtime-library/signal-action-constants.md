---
title: "signal 動作常數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SIG_IGN"
  - "SIG_DFL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "SIG_DFL 常數"
  - "SIG_IGN 常數"
  - "signal 動作常數"
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# signal 動作常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

採取的動作，以中斷信號時接收取決於 `func`的值。  
  
## 語法  
  
```  
#include <signal.h>  
```  
  
## 備註  
 `func` 引數必須是函式在 SIGNAL.H. 下面清單和定義的位址或其中一個資訊清單常數。  
  
 `SIG_DFL`  
 使用系統預設回應。  如果呼叫端使用資料流 I\/O，並不會清除這個執行階段程式庫建立的緩衝區。  
  
 `SIG_IGN`  
 忽略中斷信號。  因為處理序的浮點狀態未定義，不應該為 `SIGFPE`測量指定的值。  
  
 `SIG_SGE`  
 表示錯誤在訊號中發生錯誤。  
  
 `SIG_ACK`  
 表示通知接收。  
  
 `SIG_ERR`  
 這個錯誤的信號的傳回型別時發生。  
  
## 請參閱  
 [signal](../c-runtime-library/reference/signal.md)   
 [全域常數](../c-runtime-library/global-constants.md)