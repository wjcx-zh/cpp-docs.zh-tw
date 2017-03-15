---
title: "_WAIT_CHILD、_WAIT_GRANDCHILD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_WAIT_GRANDCHILD"
  - "WAIT_CHILD"
  - "WAIT_GRANDCHILD"
  - "_WAIT_CHILD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_WAIT_CHILD 常數"
  - "_WAIT_GRANDCHILD 常數"
  - "WAIT_CHILD 常數"
  - "WAIT_GRANDCHILD 常數"
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _WAIT_CHILD、_WAIT_GRANDCHILD
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <process.h>  
  
```  
  
## 備註  
 \(如果處理序 ID 知道\)， `_cwait` 函式可以由任何處理序用於其他處理序。  這些動作引數可以是下列其中一項數值：  
  
|常數|意義|  
|--------|--------|  
|`_WAIT_CHILD`|在指定的處理序的呼叫正在等候結束。|  
|`_WAIT_GRANDCHILD`|在指定的處理序的呼叫正在等候並建立新的處理序執行的所有處理序，結束。|  
  
## 請參閱  
 [\_cwait](../c-runtime-library/reference/cwait.md)   
 [全域常數](../c-runtime-library/global-constants.md)