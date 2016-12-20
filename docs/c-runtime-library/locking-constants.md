---
title: "_locking 常數 | Microsoft Docs"
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
  - "_LK_RLCK"
  - "_LK_NBLCK"
  - "_LK_LOCK"
  - "_LK_NBRLCK"
  - "_LK_UNLCK"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_LK_LOCK 常數"
  - "_LK_NBLCK 常數"
  - "_LK_NBRLCK 常數"
  - "_LK_RLCK 常數"
  - "_LK_UNLCK 常數"
  - "LK_LOCK 常數"
  - "LK_NBLCK 常數"
  - "LK_NBRLCK 常數"
  - "LK_RLCK 常數"
  - "LK_UNLCK 常數"
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _locking 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## 備註  
 在呼叫的 *模式* 引數傳遞至 `_locking` 函式指定要執行的鎖定動作。  
  
 *方法* 引數必須是下列資訊清單常數之一。  
  
 `_LK_LOCK`  
 鎖定指定的位元組。  如果位元組無法鎖定，程式會在 1 秒後再試一次。  如果在 10 次嘗試之後，位元組無法被鎖定，此函式回傳一個錯誤。  
  
 `_LK_RLCK`  
 與 `_LK_LOCK` 相同。  
  
 `_LK_NBLCK`  
 鎖定指定的位元組。  如果位元組無法鎖定，函式會傳回錯誤。  
  
 `_LK_NBRLCK`  
 與 `_LK_NBLCK` 相同。  
  
 `_LK_UNLCK`  
 解鎖指定的位元組。\(必須先鎖定位元組\)。  
  
## 請參閱  
 [\_locking](../c-runtime-library/reference/locking.md)   
 [全域常數](../c-runtime-library/global-constants.md)